---
title: "pam-auth-update question"
date: 2010-08-30
forum: Server Platforms
---

### Post by X1R1 on 2010-08-30
Hi, running ubuntu server 10.04 as a file server and integrated with Active Directory (AD users validate to use samba shares with the same credentials).

Long time ago I configured this setup, but something went wrong with pam and since then everytime I type sudo it asks me for the password twice, every single time, very tme consuming and annoying.

Having no other option I leaved the server like that until today fearing that If I changed something users could not be able to access the shares or even root will be unable to login (you can do this kind of things if you mess with pam and dont know what you are doing).

But now I read that ubuntu has pam-auth-update utility which is a simple tool that configures the files automaticaly. So here are my questions:

1- I have manually edited 3 files on the pam.d directory, If I remove them (obv I will have backup) and run pam-auth-update will this re-create the files with a proper setup?

2-Will users still be able to authenticate to samba using the active directory credentials?

3-If something goes wrong, can I just put a live cd in and copy my backup files over to /etc/the pam.d directory and have everything back to normal?

thanks in advance for the help/feedback you can provide :D

---

