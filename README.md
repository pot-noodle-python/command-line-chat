# command-line-chat
A simple command line chat app to communicate via the terminal.

- [x] sending messages
- [x] recieving messages
- [x] setting nicknames
- [x] handling client disconnection


## Usage
On the server computer, run `server.py`

This will create a server on the host IP address and on port `6080`

On each client computer, run `client.py`

Then input the IP address printed out by `server.py`, create a nickname and you should be connected to the chat room

## sending messages
To send messages I've created my own little protocol where when the user wants to send a message, two packets are sent: a header and the actual message

- The header contains a padded message of 64 bytes that contains the length of the actual message.
- The actual message contains the actual content and it is efficiently read to the exact number of bytes it contains, not wasting bandwidth

## Recieving messages
When a client sends a message to the server, the server loops through a list of all clients, ignoring the sender. It then sends the original clients message, along with their nickname, to each other client


## Nicknames
The nicknames are stored on the server in a dictionary, where the string of the connection object is the key, and the nickname is the value. By default each nickname is just the address of the client, but it can be changed by sending `!NICK mynickname`