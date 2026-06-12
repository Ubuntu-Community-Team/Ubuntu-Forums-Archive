---
title: "Setting up &amp; securing a remote VPS"
date: 2010-12-03
forum: Server Platforms
---

### Post by craigbert on 2010-12-03
Hello All,

I am in the process of trying to setup a hosted VPS (virtual private server) and I am trying to figure the best high level steps to go about making it secure.

The main purpose of this VPS is for me and some friends of mine to play around with some web development tools.

So I will need Apache and sftp running.  I will also need MySQL and perhaps PostgreSQL running.  Apache will have PHP5 and fastCGI modules installed and most likely a few others.  I will also need a simple mail server as I am sure we will need to test sending and receiving e-mail with the tools we plan to play with.

I will be the only one with shell access and that thru SSH.  

No one has access to the server yet so I can fiddle around as much as I like until I have it the way I want it.

When I am not actually on the server working I keep it shutdown.  

Here is the order in which I plan to go about securing it:

1) Disable root access to SSH, but make sure my user id is part of the admin or root group.
2) Setup a simple and secure secure DNS server (needed for the VPN and to the authoritative DNS for my domain.)
3) Get a VPN up and running for an added layer of security.
4) Install and run Bastille
5) Install and set up Tripwire
6) Remove any programs / compilers that are not absolutely needed.

My resources include the Ubuntu Hardening Guide posted [here]("http://ubuntuforums.org/showthread.php?t=1002167") on the forums; The [Ubuntu OpenVPN]("https://help.ubuntu.com/community/OpenVPN") help doc; The [Ubuntu Bastille]("https://help.ubuntu.com/community/BastilleLinux") help doc; and a copy of Michael Bauer's _Linux Server Security_, 2nd Edition.

I feel like I have all the information I need, but I need someone who has actual experience to say "do this instead of that" or "you are on the right track, just switch steps x & y around" or "you also need to do...."

I have never taken the time to actually harden a server so I am looking forward to this wonderful learning experience and learning from some wiser folks than me here on the forums.

Thanks,

Craigbert

---

