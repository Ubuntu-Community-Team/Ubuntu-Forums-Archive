---
title: "Where does putty store it's temporary RSA key pair when logging in with username?"
date: 2010-10-01
forum: Security
---

### Post by helloworld1215 on 2010-10-01
When logging into an SSH server with username a client needs to provide a  public key to receive the symmetrically encrypted traffic.
 
Is the key pair stored in memory or in a temporary location on the harddrive?

---

### Post by CharlesA on 2010-10-01
The private key is stored on the hard drive.

You tell putty to use that key when you connect.

---

### Post by bodhi.zazen on 2010-10-01
> **helloworld1215 said:**
> When logging into an SSH server with username a client needs to provide a  public key to receive the symmetrically encrypted traffic.
 
Is the key pair stored in memory or in a temporary location on the harddrive?

The key pair is stored on your HD, although you need only the private key. The bublic key is stored on the server.

ssh agents, such as ssh agent (ssh-add) or seahorse store keys in memory. As far as I know putty does not.

---

### Post by helloworld1215 on 2010-10-01
I dont think u guys took the time to read the question. 

When logging in with a username, ssh needs to establish the RSA connection. In order to do that, it needs to provide the server with a public key so that the server can send RSA encrypted messages to the putty client. 

As you know, you can just type in a username and password and log into a server. In this instance I have not provided Putty with an RSA combination. Where does it store the RSA pair that it uses to complete the connection? Perhaps it's a permenant default key that is generated?

---

### Post by cariboo on 2010-10-01
Have you got ssh setup to use keys only, or do you still allow password logins?

The key pair putty uses is different from what a native ssh client uses.

On my XP system, putty stores the keys in My Documents/private_key.ppk

---

### Post by helloworld1215 on 2010-10-01
This question refers to the scenario of using username to establish connection, not private key and public key on server. 

I am trying to ensure that any temporary private keys putty (or any ssh client when logging in with username) generates are secured in an encrypted container or the like. 

I'm pretty sure putty generates a temporary RSA key pair otherwise how would it establish the RSA connection for a username login? My objective is to find these keys and secure them 

Do you understand the problem?

I checked My Documents and I dont see anything putty related.  Perhaps, puttygen.exe defaults to saving keys My Documents which is why you have your key there.

THis issue revolves around the following logic:

> When logging in with a username, ssh needs to establish the RSA  connection. In order to do that, it needs to provide the server with a  public key so that the server can send RSA encrypted messages to the  putty client. RSA works by encrypted with the recipients public (the client in this scenario) and the senders private key (host in this scenario)

---

### Post by psusi on 2010-10-01
If you are using username/password to log in, then there is no RSA key.

---

### Post by cariboo on 2010-10-01
Putty's private keys are kept in HKCU/Software/SimonTatham/PuTTy/SshHostKey

---

### Post by psusi on 2010-10-01
Now that I read that quote you posted, I see where you are confused.  The quote is wrong.  When you connect, the server gives you ITS public key ( if you don't already have it ) and your client generates a random symetric cipher ( like 128 bit des or aes ) session key and encrypts it using the server's public RSA key.

---

### Post by helloworld1215 on 2010-10-01
client: hello server
servr: hello client here is my RSA public key lets communicate
client: cool, let me generate a RSA private key (and store in memory or harddrive??!?!) so I can send you an encrypted message containing my AES key for which we will encrypt all further messages
server: nice AES key, now we both have the AES key and can symmetrically encrypt all further data

right?

So... once again I am looking for the location, if there is a one of the private key that the client used to encrypt the message back to the server. You are right though that a public RSA key from the client doesn't seem to be required

I'm guessing it's in memory and is destroyed after the AES key is sent

If it's stored on the harddrive my objective is to secure the location of the temporary file

The thing is, I dont think you are correct because the username/password submission is encrypted with RSA and probably the response as well. If there is any encrypted response from the server prior to the AES key being transfered than the clients public key needs to be transfered to the server. 

It's probaby like this:

client: give me public
serv: here
client:rsa encrypted username:password:temp public key
serv:rsa encrypted yes no (possibly server to client traffic aes key!?!?)
client:if yes, rsa encrypted client to server traffic aes key

It's also possible that the server generates the aes key. In fact as you know client to srver and server to client symetric encryption is not off the same key or encryption

---

### Post by psusi on 2010-10-01
> **helloworld1215 said:**
> 
client: cool, let me generate a RSA private key (and store in memory or harddrive??!?!) so I can send you an encrypted message containing my AES key for which we will encrypt all further messages

This is the part that is wrong.  The client uses the server's public key to encrypt the session key.

---

