---
title: "Setup ssh access with ppk"
date: 2013-07-19
forum: Security
---

### Post by virgygky on 2013-07-19
hi,
I'd like to setup my home-made server in order to access on it useing a ppk key.

I've Ubuntu 13.04 installed
I've installed putty-tools

but I'm not able to understand how the keys stuff, works.

What's the right procedure to generate the 2 keys (pub and pvt)?
Anyone is able to help me with an easy tutorial?

Thank you for support

Virginia

---

### Post by Lars Noodén on 2013-07-19
Here are two on the topic:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Authentication_Keys#Basics_of_Public_Key_Authentication](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Authentication_Keys#Basics_of_Public_Key_Authentication)

Look around in the search engines using the words 'ssh keys ubuntu' and you'll find many different ones, some of which will be useful for you.  

The basic steps are:

1. create a key pair using ssh-keygen
2. put the public key on the server

---

### Post by virgygky on 2013-07-19
> **Lars Noodén said:**
> Here are two on the topic:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Authentication_Keys#Basics_of_Public_Key_Authentication](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Authentication_Keys#Basics_of_Public_Key_Authentication)

Look around in the search engines using the words 'ssh keys ubuntu' and you'll find many different ones, some of which will be useful for you.  

The basic steps are:

1. create a key pair using ssh-keygen
2. put the public key on the server

Thank you

I've found the trouble...
I got a problem with puttygen, now all works fine.
Thank you

---

