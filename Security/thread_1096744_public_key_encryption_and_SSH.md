---
title: "public key encryption and SSH"
date: 2009-03-15
forum: Security
---

### Post by Sojurner on 2009-03-15
I recently installed ssh so i cold have a secure way of communicating with my pc when i was away. I read that just using your password wasnt the safest of ways to go about this so i set up a public/private key. Im not quite sure tho if it was enabled. i just  created the key but did  not go any further.

I was also able to connect to my computer via my Blackberry and a little ssh program for it. Now all of a sudden i can not connect. I know the problem lies with the computer itself because nothing changed on my phone.

Any help......

---

### Post by victorbrca on 2009-03-15
Do you have any other computer that you can use to try and connect via ssh?

One other option would be to ssh to localhost (ssh 127.0.0.1), and see if that works.


Vic.

---

### Post by lovinglinux on 2009-03-15
First some links to help you:

1 - [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
2 - [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
3 - [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

I use ssh to log into a notebook on my local network using key authentication. Sometimes it doesn't work and keeps giving me errors about no route to the remote machine, until I reboot it. I don't know why, but maybe this is what is happening to you. Nevertheless, it seems that you haven't configured the key authentication properly.

Here is a simple tutorial that explains how to setup the key authentication.

[http://www.linuxjournal.com/article/8904](http://www.linuxjournal.com/article/8904)

The tutorial is actually about SSHFS, but skip to the section "**Automating the Connection**" to find the key authentication setup instructions.

---

