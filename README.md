#SMG: A Multifunctional ERC20 Token Contract
Comprehensive Overview
The SMG contract, crafted in Solidity, adheres to the ERC20 standard, enabling the creation, burning, and transfer of fungible tokens. It inherits the ERC20 and Ownable contracts from OpenZeppelin, providing enhanced functionalities. Additionally, it incorporates a mechanism to redeem NFT accessories using SMG tokens.

#Contract Particulars
Functions
#constructor()
Initialization: Upon deployment, this function sets the contract's name to "Degen" and its symbol to "DGN." It also mints an initial supply of 0 tokens to the contract deployer's address. Furthermore, it stores information about four NFT accessories, including their unique IDs, names, and prices.
Modifiers: None
#storeNftAccessory(uint256 itemId, string memory itemName, uint256 itemPrice)
  NFT Accessory Storage: This function, exclusive to the contract owner, allows the addition of NFT accessories to the contract's storage. Each accessory is associated with a unique ID, a descriptive name, and a price.
  Parameters:   - itemId (uint256): The unique identifier of the NFT accessory.   - itemName (string): The descriptive name of the NFT accessory.   - itemPrice (uint256): The price of the NFT accessory.
  Modifiers:   - onlyOwner: This modifier restricts access to this function to the contract's owner.
  mint(address to, uint256 amount)
  Token Minting: This function empowers the contract owner to mint new SMG tokens and assign them to a specified address.
  Parameters:   - to (address): The address to which the newly minted tokens will be assigned.   - amount (uint256): The quantity of tokens to mint.
  Modifiers:   - onlyOwner: This modifier ensures that only the contract owner can execute this function.
  Emits:   - Mint(address indexed to, uint256 value): This event signifies the successful minting of tokens.
  burn(uint256 amount)
  Token Burning: This function allows any user to burn (destroy) a specified amount of SMG tokens from their own balance.
  Parameters:   - amount (uint256): The quantity of tokens to burn.
  Modifiers: None
  Emits:   - Burn(address indexed from, uint256 value): This event signals the successful burning of tokens.
  transfer(address _to, uint256 _value)
  Enhanced Token Transfer: This function overrides the standard transfer function to introduce additional flexibility and custom functionality.
  Parameters:   - _to (address): The address to which the tokens will be transferred.   - _value (uint256): The amount of tokens to transfer.
  Returns:   - success (bool): Indicates whether the transfer was successfully executed.
  Modifiers: None
  redeem(uint256 accId)
  NFT Accessory Redemption: This function enables users to exchange their SMG tokens for NFT accessories. The cost of redemption is determined by the price of the selected NFT accessory.
  Parameters:   - accId (uint256): The unique identifier of the NFT accessory to redeem.
  Returns:   - itemName (string): The name of the redeemed NFT accessory.
  Revert Conditions:   - Invalid NFT accessory ID: If the specified accId does not correspond to an existing NFT accessory, an error is triggered.   - Insufficient balance: If the user's SMG token balance is insufficient to   cover the cost of redemption, the transaction is reverted.
  Emits:   - Redeem(address indexed from, string itemName): This event signifies the successful redemption of an NFT accessory.
