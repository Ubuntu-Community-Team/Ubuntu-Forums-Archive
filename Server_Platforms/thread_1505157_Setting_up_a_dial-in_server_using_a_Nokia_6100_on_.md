---
title: "Setting up a dial-in server using a Nokia 6100 on ubuntu server"
date: 2010-06-08
forum: Server Platforms
---

### Post by the_webspider on 2010-06-08
Hi all,
For a couple of days i've been trying to get this to work, and i've googled every page that might be relevant, but I can't find a solution.

The situation:
I have a computer with Ubuntu Server installed, and connected to that (using a CA-42 --> USB cable) a Nokia 6100 phone.
The nokia 6100 had a built-in modem, and when I plug it in, it shows up as "/dev/ttyUSB0"
.

What I want to achieve:
I want to be able to dial into my server from a different pc, and then be connected to my own LAN (and maybe the internet that my server is connected to).

I found this link on the internet and followed all the steps (but changed details like /dev/ttyS0 --> /dev/ttyUSB0):
[http://ubuntuforums.org/showthread.php?t=150339](http://ubuntuforums.org/showthread.php?t=150339)

But when I use a different pc to call my Nokia phone, it rings, but it doesn't pick up the phone, it just keeps on ringing...

I'm pretty new at using Ubuntu, so I'm stuck right there.
I think that mgetty isn't connecting properly or isnt loaded on boot (in /etc/inittab)
I know that the cable works, and that the phone works, because I've succesfully installed "gammu" which enabled me to send SMS messages from the command line.

What can i do to get the server to pick up the phone and connect the caller to my home-LAN when the phone starts ringing?

Any help would be appreciated,

Webspider

---

