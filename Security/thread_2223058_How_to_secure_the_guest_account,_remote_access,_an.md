---
title: "How to secure the guest account, remote access, and other logging in options"
date: 2014-05-09
forum: Security
---

### Post by abraham5 on 2014-05-09
Before coming to Ubuntu, I used to be a Windows user and after I learned about the importance of security and privacy I decided to move to Ubuntu. That is actually why I am totally inexperienced.

I happened to notice today, that Ubuntu has a guest account, now that sparked something, if ubuntu has a guest account, does it also happen to have remote login features? So accordingly these are my actual questions for this thread:

1- Should I disable the guest account in my Ubuntu 12.04 desktop installation? How can I do that?
2- Windows had that simple option in system settings for "apparently" disabling remote desktop option, is there a way to disable all kinds of remote access, in Ubuntu as well?
3-If there is such an option for disabling all the remote access features, should I go ahead and disable them all, or I have to think about it first?
4- Is a firewall rule which blocks all incoming traffic enough to block all remote access to the machine in Ubuntu?

---

### Post by sudodus on 2014-05-09
Welcome to the Ubuntu Forums :-)

1. I don't think you have to disable the guest account. It has very limited access.

2,3. By default, there is no server driver for remote access in the Ubuntu desktop flavours. You have to install an ssh or samba server or something similar for remote access.

4. There is a default firewall setting, that should be enough for a normal user (there are no open listening ports).

See this link for more details [BasicSecurity - Ubuntu Wiki]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by abraham5 on 2014-05-09
Thank you [**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021"), for the helpful information.

---

### Post by maglin2 on 2014-05-09
To set firewall to block all incoming:
[I]
sudo ufw enable[/I]

(firewall is not enabled by default - though there are no open listening ports).

---

### Post by bashiergui on 2014-05-10
1. The guest account is a good way to allow others to temporarily use your computer. [https://help.ubuntu.com/community/PasswordlessGuestAccount](https://help.ubuntu.com/community/PasswordlessGuestAccount)


If you don't expect to ever share it then it's rather simple to disable Guest.
[http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html)


2 & 3. Adding some details building on Sudodus' comments: A default installation has some remote connection clients installed, meaning that you could use your Ubuntu machine to connect to someone else's computer. Those don't pose a risk to you. 


There are a bunch of ways to remotely connect to your Ubuntu desktop. They are not installed or enabled by default. 
-vnc
-rdp
-ssh
-ftp
All of these require that you install and configure a server on your computer. It also requires that you allow that service's port to listen to the Internet. If you have a router, then you have to purposely configure the router to expose the listening port to the world.


So in short, if you haven't installed any remote connection servers then you're fine.


4. The Ubuntu firewall is off by default. If you have a router between you and the Internet then there's no reason for Ubuntu to use a firewall. However if you're on a network with other people (like free wifi or a school network) then you definitely want a firewall on your box. Deny all inbound and allow all outbound would suffice.

---

