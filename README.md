Overview

MyToken is a simple ERC-20-like token contract implemented in Solidity. The contract includes basic functionalities such as minting and burning tokens.

Features

- Token Name: Khaiza
- Token Abbreviation: Alameda
- Total Supply: Dynamic, based on minting and burning activities
- Minting: Ability to create new tokens and assign them to an address
- Burning: Ability to destroy tokens from an address, reducing the total supply

Contract Details

Public Variables

`string public tokenName` - The name of the token.
`string public tokenAbbrv` - The abbreviation of the token.
`uint public totalSupply` - The total supply of the token.
`mapping(address => uint) public balances` - A mapping to store the balance of each address.

Constructor

The constructor initializes the token's name, abbreviation, and sets the total supply to zero.

```solidity
constructor() {
    tokenName = "Khaiza";
    tokenAbbrv = "Alameda";
    totalSupply = 0;
}
```

Functions

Mint

The `mint` function creates new tokens and assigns them to a specified address.

```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

- Parameters:
  `_address`: The address to receive the minted tokens.
  `_value`: The amount of tokens to be minted.

Burn

The `burn` function destroys tokens from a specified address, reducing the total supply.

```solidity
function burn(address _address, uint _value) public {
    require(balances[_address] >= _value, "Insufficient balance");
    totalSupply -= _value;
    balances[_address] -= _value;
}
```

- Parameters:
  `_address`: The address from which the tokens will be burned.
  `_value`: The amount of tokens to be burned.
- Requirements:
  The balance of `_address` must be greater than or equal to `_value`.

License

This project is licensed under the MIT License 
