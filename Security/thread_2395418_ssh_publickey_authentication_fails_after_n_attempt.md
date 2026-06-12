---
title: "ssh publickey authentication fails after n attempts"
date: 2018-07-02
forum: Security
---

### Post by kedvsk on 2018-07-02
Hello,

I'm using ssh library in a c program.
It connects about every minute for a view seconds using public key authentication to several linux systems (Ubuntu 16.04 LTS, Raspbian Stretch, Mint, Libreelec, ... )
After a while login on the ubuntu 16.04 LTS system is denied with following message:

**ssh_userauth_publickey: Access denied. Authentication that can continue: publickey,password**

If I login once using username/password the program runs well again.

This happens only on the Ubuntu 16.04 LTS system. On Ubuntu 12.04 LTS this didn't happen.
The sshd_config is exactly the same as on the Mint system.

Any ideas?

Best regards ...

---

### Post by TheFu on 2018-07-02
There's no way for anyone here to know what your C program does.
If the normal ssh client connection works, then it is an issue in how your code does it.  You can look in the code for ssh-client to see how that has changed.  You can turn up the debugging on the client and server to see which messages happen as they work, which might also provide hints for who to modify your program.  

Over the years, things change. Some ciphers are found to be too weak to continue supporting, so those have been removed. Also, new attack vectors have been found, so the servers take steps to prevent them. And server admins have learned to prevent connections that appear to be attacks in the firewalls. Attempted connections that don't complete would appear to be an attack to many firewalls and monitoring programs.

---

