---
title: "change telnet password"
date: 2014-09-27
forum: Server Platforms
---

### Post by Black_Project on 2014-09-27
I am new in ubuntu and have been currently reading certain topics about it. I have a problem with my modem specifically a greenpacket modem (DV235t)

Is there a way to change my modem's telnet password? I have recently been attacked by remote telnet connection. Unfortunately the admin username and password for my modem is generally all the telnet's admin account for that specific modem. I have been trying to open the shadow file on my modem's telnet but unfortunately i cant seem to open it.

Any help would be greatly appreciated. Thank you.

---

### Post by TheFu on 2014-09-28
telnet shouldn't be used anymore - anywhere.
If you own the modem, follow the instructions from the vendor's documentation to chnage the password, disable WAN access and use a more secure access method, like ssh.

BTW - this really isn't a Linux question - better to ask this on the greenpacket support site.  Or am I completely misunderstanding the issue?

---

### Post by nerdtron on 2014-09-28
> Is there a way to change my modem's telnet password? I have recently been attacked by remote telnet connection.

So I guess this is not an Ubuntu question but rather a modem question. Although you may say it is similar to Ubuntu command line there can still be differences. 

Hhhhhmmmm I remember my old modem was a greenpacket too and I can telnet to it (but can't login because I don't know the user/password). How are you sure that you were attacked by remote telnet connection?

By default on home modems like this, all common ports, Web GUI (port 90), SSH (port 22) and Telnet (port 21) are all restricted when the connection is made from the remote (internet) side. Meaning only users in your internal network will be able to telnet, ssh or web gui on your modem. They also need the user/password to login.

---

