---
title: "Broken cups installation"
date: 2010-12-06
forum: Server Platforms
---

### Post by mangecelle on 2010-12-06
Hi, 

I am having trouble with an cups installation. It seems to be in a broken state. When i try to reinstall it it stalls, the same if i try to remove it completely.

I am running the server version 64 bit of Ubuntu 10.10 with kernel
Linux version 2.6.35-22-server.

I have tried to remove it with the following command

*sudo apt-get purge cups*

It finally stalls with the following message

[I]Removing cups ...
[/I]
After that nothing happens. 

The process tree for the apt-get command looks like this. 

 1404  1404  1404 ?        00:00:00   sshd
26495 26495 26495 ?        00:00:00     sshd
26581 26495 26495 ?        00:00:00       sshd
26582 26582 26582 pts/4    00:00:00         bash
27158 27158 26582 pts/4    00:00:00           apt-get
27172 27172 27172 pts/2    00:00:00             dpkg
27176 27172 27172 pts/2    00:00:00               cups.prerm
27178 27172 27172 pts/2    00:00:00                 stop

I have tried to leave the process running for a while to see if i get any error messages but without success.

Would be grateful for any suggestion.

---

