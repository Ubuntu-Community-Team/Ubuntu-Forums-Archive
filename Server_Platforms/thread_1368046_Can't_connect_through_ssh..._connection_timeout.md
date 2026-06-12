---
title: "Can't connect through ssh... connection timeout"
date: 2009-12-30
forum: Server Platforms
---

### Post by roomy on 2009-12-30
Hi

I just setup my ubuntu server on amazon EC2 and I can connect through ssh using elastic fox plugin. But when I try to connect from any other computer using putty. I just get the connection timeout error.

Strange thing is Elastic fox also uses putty to connect to server and the only thing it asks for is private key. It works absolutely perfect.

I have created username and password for other users and I have also enabled the password authentication in openssh but they can't connect using ip address or domain name.

I will appreciate if anyone can help in rather simple language as I am very new to ubuntu.

Thanks

---

### Post by Alex4108 on 2009-12-30
You said your SSH client asks for a key.  It depends on what SSH Daemon your using.  Some completely deny connections if they don't get a key.  Others will let you in but say that you don't have a key.

In PuTTY, try this. 

In the left side, go Connection > SSH > Auth.

In the top of that area it asks to locate a key file.  

Note: If your Daemon is configured for Private Key - Clear.  Password - Clear. Welcome Jane Doe.  Then you either don't know what your doing.  Or your taking extra measures to secure your server.  

Anyway, in the Auth section, put in the private key file and everything should work.  

If this doesn't work, lets try one other thing.  Make sure your connecting on the right port, as some servers purposely throw themselves off the default port to avoid being spammed or crashed

---

