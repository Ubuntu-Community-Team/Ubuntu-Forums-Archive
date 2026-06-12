---
title: "new server in need of assistance"
date: 2011-06-12
forum: Server Platforms
---

### Post by Python Jedi on 2011-06-12
I'm at a bit of a loss here.  I just recently installed ubuntu 11.04 server on an emachines etower, 400MHz intel celeron, 256MB RAM.  I've tried installing apache2 and python3, but cannot get it to connect to the internet.  while I understand how to work in a command line, I'm not sure what to do to diagnose the problem.  I can list all the packages if it would help. (it's a fresh install so far), as well as the ethernet statuses (two cards for a firewall type setup)

TIA,
Python Jedi

(admins: is this the right place?  move it if need be)

---

### Post by papibe on 2011-06-12
Did you have your server connected to your LAN when you installed? If done that way, the network configuration is set at install time.

Nevertheless, it is possible to do the work editing some files. To start, could you post the result of the following commands ?

```
$ cat /etc/network/interfaces
```
and
```
$ ifconfig
```

Regards.

---

### Post by Python Jedi on 2011-06-22
Sorry about not posting, I got real busy.  As it was a fresh install, I decided to just hook up the cards and reinstall (and it went through the server setup). However, I only selected "print server" for the packages to install (pressed enter instead of space I think), so I need to install those packages (I<3apt-get! add cowsay too).  Any suggestions would be appreciated, I'm more likely to have a rapid response now.:P

And two questions related to the command line, make that three.  

1) ```
sudo shutdown now
``` doesn't turn off the computer, nor does ```
sudo shutdown -P now
``` is this a problem, or normal operations?

2) what command is used to check an IP address on the local network? (what you get from connection information, in the IPv4 section)

3) does anyone know of a guide on how to use a command line environment?  working with settings and common programs?

---

### Post by jmacgowan on 2011-06-22
1.
```
sudo shutdown now
```
Was the right idea, but you need one more step.

This:
```
sudo shutdown -h now
```
will tell your server that you want to shutdown and halt (poweroff).

I believe:
```
sudo poweroff
```
will work too.

2.
As far as checking your IP and the like, use
```
ifconfig
```
It's a little counter-intuitive if you're coming from a Windows environment (ipconfig), but it will give you the data you need.

3.
Start here [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) for the command-line.  It has nice info on getting around and manipulating things.  When you need to change a setting, it's best to look through the documentation for the program in question.  If you need help, search the forums or google it.  I can almost always find how to change this or that from google.

---

### Post by Python Jedi on 2011-06-22
Thanks, I wasn't familiar with the Windows cmd line either, so I'm not at all familiar with what programs are used for what purposes.  I'll check that page out, and I'll continue my quest to create this server.

---

### Post by jmacgowan on 2011-06-22
Don't forget to check out the very well written server guide: [https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)

That guide always points me in the right direction.

If you have any questions or want clarification, feel free to PM me.

---

