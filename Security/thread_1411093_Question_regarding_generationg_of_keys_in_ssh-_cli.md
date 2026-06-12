---
title: "Question regarding generationg of keys in ssh- client?"
date: 2010-02-19
forum: Security
---

### Post by mahela007 on 2010-02-19
EDIT : I've found and answer here: [http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_04.htm#ch03-62629.html](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_04.htm#ch03-62629.html)
Hi.. 
I have ssh server installed on my desktop and the default ssh client on my laptop. The first time I made a remote login, I remember some messages about generating keys. (this happened automatically). Now, I know that both the client and the server must each have two keys. the public key and the private key. I know that the ssh server is capable of generating private and public keys for it's own PC but what generated the keys for the client laptop? Was is the ssh client or the ssh server on the other desktop pc? Where are the keys of the client computer stored? 
(Lately I've been asking a lot of questions about ssh.. but that's because I can't find any of the answers on my own. )

---

### Post by rookcifer on 2010-02-19
You will put the public key on your server machine and the private key on your client machine.  For instance, I use ssh to securely connect to my router, so I generated the keys, pasted the public key into my router's configuration settings and kept the private key on my desktop.

I don't think your assertion that the client and server both need two keys is correct.

---

### Post by bodhi.zazen on 2010-02-19
There are also Host Keys

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

Host keys are generated on the server and use ~/.ssh/known_hosts . These are the keys you saw generated on the server when you installed openssh-server.

The host keys, among other things, ensure you are connecting to the server you think you are.

Then there are client keys. These you generate with ssh-keygen. The private key you keep, typically in ~/.ssh, but you can keep it anywhere.

You transfer the public key to the server.

---

### Post by mahela007 on 2010-02-20
Thanks.. I haven't enabled key based logins. However, I believe the remote (password based) loggins I make are still encrypted with public key encryption. Doesn't that mean that there have to be keys on the client as well?

---

### Post by bodhi.zazen on 2010-02-20
> **mahela007 said:**
> Thanks.. I haven't enabled key based logins. However, I believe the remote (password based) loggins I make are still encrypted with public key encryption. Doesn't that mean that there have to be keys on the client as well?

Not sure what you are asking here.

The ability to use keys to log in does not need to be enabled, you simply make a key on the client and transfer the (public) key to the host with 

ssh-copy-id user@server

ssh traffic is encrypted.

ssh keys and the encryption protocols are different. I suggest you read a few man pages ;)

[http://www.openbsd.org/cgi-bin/man.cgi?query=ssh-keygen](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh-keygen)

[http://www.openbsd.org/cgi-bin/man.cgi?query=sshd&sektion=8&arch=&apropos=0&manpath=OpenBSD+Current](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd&sektion=8&arch=&apropos=0&manpath=OpenBSD+Current)

This page also reviews some of the technical details as well :

[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch07_04.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch07_04.htm)

---

### Post by mahela007 on 2010-02-20
hm... Let's start at the beginning. 
This is my understanding of ssh (largely based on the 'How it works' section in the  wikipedia article on public key encryption)
There are two components of an ssh 'network'. The ssh client and the ssh server. 
Now, the ssh server encrypts everything it sends over the network using the public key of the client. The client is then able to decrypt the message using it's own private key. 
Now, in a default installation of the ssh-server on Ubuntu, an ssh connection is established and the client computer sends the username and password of a particular user on the server to the server.
I assume that this exchange and everything after that is encrypted using public key encryption. If that is so shouldn't the client have it's own public and private keys? (which will be used to decrypt the messages sent by the server)

EDIT: As I said in previous posts, I only saw the keys on my ssh server. I haven't been able to find any keys on my client machine (assuming that they should be there) and yet I am able to establish ssh connections..

---

### Post by cariboo on 2010-02-20
In order for you to log on to the sever without having to enter a password you generate a private/public key on the client, you then copy that key to the server, which allows you to access the server without having to enter a password. Have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for a better explanation and howto.

---

### Post by mahela007 on 2010-02-20
Thanks.. but that's how key based login works. 
At the moment I use an ordinary 'password based' login [on my LAN]. The client doesn't seem to have any keys. According to what I've read, the client must have keys in order for the server to encrypt any information that is transferred. So if there are no keys on my client, how does ssh even work for password based logins?

---

### Post by rookcifer on 2010-02-20
> **mahela007 said:**
> Thanks.. but that's how key based login works. 
At the moment I use an ordinary 'password based' login [on my LAN]. The client doesn't seem to have any keys. According to what I've read, the client must have keys in order for the server to encrypt any information that is transferred. So if there are no keys on my client, how does ssh even work for password based logins?

Just like we explained already.  In public key cryptography there are two keys -- one public (for authentication) and one private (for encryption).  When you generate a key, you are actually generating two: both a public and private key.  You can think of these as two sides of the same coin -- one is worthless without the other.  

As was said, you need to transfer the public key to the server and the private key will stay behind on the client.  If you are connecting to a server that you did not generate the keys for, you will have to copy it's public key to your "keyring."  Then you will have to make sure the server operator has allowed your client's (public) key access to the server (that is, you will need to make sure the server has given you permission to connect via key authentication).  

Basically, the server will add your public key to his keyring and you will have his on yours, thus the ability for authentication and encryption between the two of you.

---

### Post by bodhi.zazen on 2010-02-21
> **mahela007 said:**
> Thanks.. but that's how key based login works. 
At the moment I use an ordinary 'password based' login [on my LAN]. The client doesn't seem to have any keys. According to what I've read, the client must have keys in order for the server to encrypt any information that is transferred. So if there are no keys on my client, how does ssh even work for password based logins?

You do not have the correct understanding of how ssh works. 

There are 3 things, and other then that they all involve encryption, they are otherwise unrelated.

1. Host keys - These are used to identify the host (server).

2. User or Clinet keys. These are used to identify the client.

3. Encryption of the ssh data itself.

Did you read the links I gave you ?

[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch07_04.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch07_04.htm)

section 7.4.2. User Identity Explains Client keys.

section          7.4.3. Host Keys and Known-Hosts  Databases Explains Host keys.

And this link

[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch05_04.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch05_04.htm)

Section 5.4.5. Encryption Algorithms explains the encryption algorithms. This is the section that applies to the encryption of the data. 

And yet another link explaining "Identity"

[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch06_01.htm#ch06-60666.html](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch06_01.htm#ch06-60666.html)

---

### Post by mahela007 on 2010-02-21
> **rookcifer said:**
> Just like we explained already.  In public key  cryptography there are two keys -- one public (for authentication) and  one private (for encryption).  When you generate a key, you are actually  generating two: both a public and private key.  You can think of these  as two sides of the same coin -- one is worthless without the other.  

As was said, you need to transfer the public key to the server and the  private key will stay behind on the client.  If you are connecting to a  server that you did not generate the keys for, you will have to copy  it's public key to your "keyring."  Then you will have to make sure the  server operator has allowed your client's (public) key access to the  server (that is, you will need to make sure the server has given you  permission to connect via key authentication).  

Basically, the server will add your public key to his keyring and you  will have his on yours, thus the ability for authentication and  encryption between the two of you.
I didn't have to do any of that.. I didn't have to copy keys to my ssh host... All I did was install the server and use the ssh command from my client PC.
Thanks for all the links bodhi.zazen. I did try reading the man pages you sent me before.. however, they are much too complicated for me to understand. Looks like I'll give the other website a try. I'll post back when I get my head around this thing and am able to ask some sensible questions ;-) :-)

---

### Post by mahela007 on 2010-02-28
Ok.. I've got it after some reading and forum-posting. 
SSH uses both public key encryption [aka asymmetric encryption] and symmetric encryption. 
Check this out: [http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_04.htm#ch03-62629.html](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_04.htm#ch03-62629.html)

---

### Post by ushills on 2010-03-01
> **mahela007 said:**
> I didn't have to do any of that.. I didn't have to copy keys to my ssh host... All I did was install the server and use the ssh command from my client PC.
Thanks for all the links bodhi.zazen. I did try reading the man pages you sent me before.. however, they are much too complicated for me to understand. Looks like I'll give the other website a try. I'll post back when I get my head around this thing and am able to ask some sensible questions ;-) :-)


If you did not copy you public key to the server then you are using passphrase login for SSH, this is not very secure over the net due to the high number of brute force attacks that take place on port 22.  Consider installing additional security such as fail2ban or denyhosts or move solely to key based ssh logins and remove the facility to login via passphrase.

I wrote a brief guide to securing SSH here.

[http://www.ushills.co.uk/2009/03/ssh-securely-with-keys.html]("http://www.ushills.co.uk/2009/03/ssh-securely-with-keys.html")

---

