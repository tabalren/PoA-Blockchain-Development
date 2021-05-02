# How To: Create A Private Blockchain Network 

(insert image)

This step-by-step guide can be used to create a Proof of Authority (PoA) algorithm which is typically used for private blockchain networks. A PoA requires pre-approval of, or voting in of, the account addresses that can approve transactions (seal blocks).

## Installation and Environment Setups - for Mac users only

### 1. MyCrypto App
#### An open-source web-based wallet application, MyCrypto lets you manage the plethora of Ethereum-based tokens and make transactions in the blockchain, all while keeping your private keys offline.

Open your browser and navigate to the downloads page at https://download.mycrypto.com/

(insert image)

Choose the appropriate installer for your operating system and once you download the installer, open the file, and follow the installation wizard.

When you've successfully downloaded MyCrypto, you will a tutorial which you can read through. 

(insert gif image)

Important note for Mac users:

The first time you open MyCrypto, you will see a warning message. You can safely click on the "Open" button to start the application.

(insert mac warning image)

## Allowing Permission to Open Apps from Unidentified Developers

Certain applications, like MyCrypto, may be automatically blocked by the Mac OS operating system when attempting to open the "unidentified" application. Therefore, in order to allow the use of the MyCrypto app, you may need to allow it as an exception to your Mac OS security preferences. 

To do so perform the following.

Open the MyCrypto app, it should produce a warning error saying that you cannot open the application due to security reasons. Therefore, we'll need to make a security exception for it.

Look to the top-left of the screen and click on the Apple Logo and navigate to System Preferences > Security & Privacy.

(insert system preferences image)

Click in the General tab and allow your MyCrypto application security access to be opened in the "Allow Apps Downloaded From" section. Your screen should look similar to the image below.

(insert security privacy image)

### 2. GoEthereum App 
#### Go Ethereum is one of the three original implementations of the Ethereum protocol. It is written in Go, fully open-source and licensed under the GNU LGPL v3. We will use Go Ethereum Tools to create our very own blockchain, from the genesis block to mining tokens and making transactions.


To install the Go Ethereum Tools, follow the steps below:


Open your browser and navigate to the Go Ethereum Tools download page at https://geth.ethereum.org/downloads/

Scroll down to the "Stable Releases" section and proceed depending on your operating system.


2.1. Installing in OS X.
Click on the "Geth & Tools 1.9.7" to download the applications bundle archive.

(insert geth gif)

After downloading the tools archive, open your "Downloads" folder, and you will find a file named geth-alltools-darwin-amd64-1.9.7-a718daa6.tar.gz in OS X. 
Note: the last numbers in the filename could vary depending on the last built available.

Decompress the archive in the location of your preference in your computer's hard drive, and rename the containing folder as Blockchain-Tools or any other name you prefer. I recommend using a location that can be easily accessed from the terminal window like the user's home directory.


## Now it's time to start building your own blockchain!

#### The following steps can be followed by Mac users. 

1. Open your Terminal and navidate to a folder Blockchain-Tools. Switch from base to ethereum environment (conda activate ethereum). After, you will generate two new nodes with new account addresses that will serve as our pre-approved sealer addresses.

2. Create accounts for two nodes for the network with a separate datadir for each using geth:

./geth --datadir node1 account new (it will give you 'Public address of the key: 0x7D4247280Fb0090548FC66FD8d51090De4F1b0a4' and 'Path of the secret key file'. Save both in a notebook for your reference. You will need a "Public address" later.)
./geth --datadir node2 account new (it will give you 'Public address of the key': 0x7Bb859b0acAD412c747292d027B7A4659e9191D6 and 'Path of the secret key file'. Save both in a notebook for your reference. You will need a "Public address" later.)

3. Next, generate your genesis block.

 Markup : *  
 
- Run ./puppeth command in your Terminal, name your network (in my case, I named it "renachain3"), and select the option to configure a new genesis block.

- Choose the Clique (Proof of Authority) consensus algorithm.

- Paste both account addresses from the first step one at a time into the list of accounts to seal (see above for the addresses).

- Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.

- You can choose no for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.

- Add a Chain ID. It can be any random number. In my case: 999.

- Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.

- Export genesis configurations. This will fail to create two of the files, but you only need renachain3.json.
