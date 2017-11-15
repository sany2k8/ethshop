# Ethereum Shop

This tutorial is meant for those with a basic knowledge of Ethereum and smart contracts, who have some knowledge of HTML and JavaScript, but who are new to dapps.

# What we'll do

- Setting up the development environment.
- Creating a Truffle project using a Truffle Box.
- Writing the smart contract.
- Migrating the smart contract.
- Creating a user interface to interact with the smart contract.
- Interacting with the dapp in a browser.

### Default config for truffle.js

```
module.exports = {
    networks: {
        development: {
            host: "127.0.0.1",
            port: 8545,
            network_id: "*" // Match any network id
        }
    }
};
```
Window's user rename the **truffle.js** file to **truffle-config.js**

# How to setup

Install **NodeJS** (includes **NPM** 5.5.1) https://nodejs.org/en/download/

**Open terminal and run** 

1. Install Truffle globally ``npm install -g truffle``

2. Clone the project using ``git clone https://github.com/sany2k8/ethshop.git``

3. Install the dependencies from package.json file ``npm install`` 

4. Now, you have **3** choices whether you can use **Truffle develop** or run **TestRpc**

   A. **Using Truffle develop**

    - Run the development console. `truffle develop`

    - Compile the smart contracts. ``compile``
 
    - Migrate the smart contacts. ``migrate``

   B. **Using TestRpc** (That has build-in HD Wallet)

    - Install ``testrpc``, using ``npm install -g ethereumjs-testrpc`` https://github.com/ethereumjs/testrpc

    - Run the testrpc using ``testrpc``

    - Migrate the smart contacts ``truffle migrate``

   C. **Using Geth** 

    - Install ``geth`` on ubuntu by following commands

        ``sudo apt-get install software-properties-common``
    
        ``sudo add-apt-repository -y ppa:ethereum/ethereum``
    
        ``sudo apt-get update``
    
        ``sudo apt-get install geth``

   More info: https://github.com/ethereum/go-ethereum/wiki/Installation-Instructions-for-Ubuntu

    - Install ``geth`` on windows by following step
        
        All versions of Geth are built and available for download at https://geth.ethereum.org/downloads/

        The download page provides an installer as well as a **zip** file. The installer puts geth into your PATH automatically. The zip file contains the command **.exe** files and can be used without installing.

        - Download zip file
        
        - Extract **geth.exe** from zip
        
        - Open a command prompt
        
        - chdir
        
        - open **geth.exe**

   More info: https://github.com/ethereum/go-ethereum/wiki/Installation-instructions-for-Windows
  
    - Migrate the smart contacts `` truffle migrate``
    
# Geth:

        - Create a directory anywhere on your system using e.g ``mkdir geth``
 
        - Change directory ``cd geth``
 
        - Make data directory ``mkdir datadir``
 
        - Create **genesis.json** file with example configuration
 
 ```
    {
        "config": {
            "chainId": 42,
            "homesteadBlock": 0,
            "eip155Block": 0,
            "eip158Block": 0
        },
        "nonce": "0x000000000000002a",
        "difficulty": "0x04000",
        "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "coinbase": "0x0000000000000000000000000000000000000000",
        "timestamp": "0x00",
        "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "extreaData": "0x",
        "gasLimit": "0x47E7C4",
        "alloc": {
                  "f44cf64f2cb6381e260355d6d44c2b09a82c488b": {
                  "balance": "31337000000000000000000000000"
                 },
                  "e2331f931fd65388d6bff717b9aacccf0e400b45": {
                  "balance": "31338000000000000000000000000"
                 },
                  "d0612efd9c7410fb73d5ce3d530a896c5428e31a": {
                  "balance": "31339000000000000000000000000"
                 },
                  "4d60895f05d587df75dcacc74ff598bb93d23830": {
                  "balance": "31336000000000000000000000000"
                 },
                  "7e7034bb21709dd9dba6a19c7549adcb95af8a34": {
                  "balance": "31335000000000000000000000000"
                 }
           }
     }

 ```
    
## Init Geth:

``geth --datadir=./datadir init genesis.json``

## Start Geth:

``geth --port 3500 --networkid 42 --nodiscover --datadir="datadir" --rpc --rpcport 8545 --rpcaddr 0.0.0.0 --rpccorsdomain "*" --rpcapi "eth,net,personal,web3"``

## Attach:

``geth attach ipc:\\.\pipe\geth.ipc`` **Change it as per your ipc path, here I just used mine**

## Example Commands:

personal.newAccount("123456789")

personal.newAccount("987654321")

personal.listAccounts

miner.start(1)

eth.mining

personal.unlockAccount(eth.accounts[0], "123456789", 86400)    
    

5. Run the **liteserver** development server (outside the development console) for front-end hot reloading.

    - Run the DAPP : ``npm run dev``

The DAPP will serve the front-end on http://localhost:3000