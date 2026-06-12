---
title: "ssh encrypted login"
date: 2010-01-31
forum: Security
---

### Post by noway2 on 2010-01-31
There was a recent thread in this forum regarding capturing of SSH passwords via the use of wireshark.  The thread subject was closed, which is a decision that I both agree with as well as agree with the reasoning behind.  The thread, however, raised a point of curiosity and concern that I would like to ask about.  

Quoting from a the book, SSH, The definitive guide, > The client authenticates you to the remote computer's SSH server using an encrypted connection, meaning that your username and password are encrypted before they leave the local machine. The SSH server then logs you in, and your entire login session is encrypted as it travels between client and server. Because the encryption is transparent, you won't notice any differences between telnet and the telnet-like SSH client. 

I was under the impression that SSH was impervious to this type of eavesdropping, and quite frankly I take great comfort in that idea. I personally, only allow RSA keys for SSH access and (hopefully) avoid this problem (?) as a result.

Does SSH really have a vulnerability in that the authentication is sent via plain text?

Note, please keep responses along the lines of how to ensure the security of SSH and not on anything that could be considered a how to 'crack' it.

---

### Post by DGortze380 on 2010-01-31
> **noway2 said:**
> 

Does SSH really have a vulnerability in that the authentication is sent via plain text?


No.

SSH (Secure Shell) utilizes encryption during authentication as well as during session communications.

Cracking that encryption is a whole other topic entirely.

---

### Post by Sporkman on 2010-01-31
SSH is secure, and assumes the communications may be eavesdropped on.

FTP, on the other hand, does indeed send authentication over plaintext is my understanding, and is therefore insecure.

---

### Post by BkkBonanza on 2010-02-01
It is possible for a MITM attack to be used against SSH. However, for that to be done you would have to be sloppy in your use. All security requires that you be careful about how you use the tools. 

In the case of SSH it will tell you if the machine it is connecting with is not the expected machine and doesn't have the expected key signature. If you get a warning that the machine is "not in your known hosts file" then you need to think carefully about whether there is a valid reason for that and decide if you should continue. If not then you could have been intercepted by another machine. At that point all deals are off as you don't know what or who you're connecting to.

So - pay attention to details and you should be ok. Same whn using SSL web sites - pay attention to the protocol https and the url you are connecting to, not just the little padlock.

---

### Post by bodhi.zazen on 2010-02-01
> **noway2 said:**
> There was a recent thread in this forum regarding capturing of SSH passwords via the use of wireshark.  The thread subject was closed, which is a decision that I both agree with as well as agree with the reasoning behind.  The thread, however, raised a point of curiosity and concern that I would like to ask about.  

Quoting from a the book, SSH, The definitive guide, 

I was under the impression that SSH was impervious to this type of eavesdropping, and quite frankly I take great comfort in that idea. I personally, only allow RSA keys for SSH access and (hopefully) avoid this problem (?) as a result.

Does SSH really have a vulnerability in that the authentication is sent via plain text?

Note, please keep responses along the lines of how to ensure the security of SSH and not on anything that could be considered a how to 'crack' it.

I know the thread you are asking about ;)

SSH encrypts all traffic, including passwords. The encryption can potentially, in theory at lease, be cracked if enough packets are sampled and the cracker is skilled.

Personally, I am not sure the OP in  the closed thread gave us sufficient information and the information may have been incomplete or false. I would certainly not jump to the conclusion that ssh is insecure because of the closed thread.

I find with security questions it is best to read the source documentation.

[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch01_04.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch01_04.htm)

> The client authenticates you to the remote  computer's SSH server using an encrypted connection, meaning that your username and password are encrypted before they leave the local machine. The SSH server then logs you in, and your entire login session is encrypted as it travels between client and server.

Keep reading the link if you are interested =)

---

### Post by DZ* on 2010-02-01
> **bodhi.zazen said:**
> 
[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch01_04.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch01_04.htm)

Keep reading the link if you are interested =)

Are any of these books really free?
([http://docstore.mik.ua/orelly/](http://docstore.mik.ua/orelly/))

---

### Post by noway2 on 2010-02-01
Thank you for the replies everybody.  It is good to read that there isn't some sort of gaping hole that I was blindly not aware of.

I think bodhi.zazen is correct, that there was some information missing or just plain wrong in that post.

---

