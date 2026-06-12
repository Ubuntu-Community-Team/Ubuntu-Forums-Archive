---
title: "Ubuntu server 7.04 - all ports open by default?!"
date: 2007-07-16
forum: Server Platforms
---

### Post by codmate on 2007-07-16
Hi all.

I'm new to Ubuntu, if not totally new to Linux.

I just installed a server with no default server software (no DNS or LAMP etc). I just need it to run Slimserver, Samba, MusicMagic Ip Mixer and rTorrent.

I noticed that iptables is running by default and have a few questions about this implementation.

Firstly I was able to SSH into the box with no problems - until I accidently blocked myself out by changing iptables policy!  :)

This is contrary to what it says here:
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)
"The Ubuntu Server has no open ports after the installation"

According to my expereince - *all* the ports were open directly after installation!

I then went through and made some rules (just for Samba, rTorrent, SlimServer, www and SSH really), which I then tested, as well as changing poilcy to always drop for everything I don't need.

All seems OK now - but is my experience atypical?
If not, the documentation on the above page should be changed as it is very misleading if I'm right!

Two other quick questions...
How do I turn iptables on and off?
There doesn't appear to be anything in /etc/init.d/
Right now I just
>sudo iptables -F
..to 'stop' it...
...and then use a script to re-add all the rules to 'start' it up again.

Also...
What port does apt-get need?
It seems to be working ok regardless...

---

### Post by adam_kimber on 2007-07-16
I am also currently struggling with my iptables installation, however from my reading around, what i gather is that the way iptables works is that all ports are closed by default unless a recognised service has explicitly asked for a port. Then it opens that port unless the rules prohibit is from doing so. 

Check out this thread as it has some further info about iptables implementation in Ubuntu. 

[http://ubuntuforums.org/showthread.php?t=31663]("http://ubuntuforums.org/showthread.php?t=31663")

---

### Post by ZephyrXero on 2007-07-16
I think what they mean by no ports open, is that there are no services/daemons running on any ports, thus there's nothing to exploit ;)

---

