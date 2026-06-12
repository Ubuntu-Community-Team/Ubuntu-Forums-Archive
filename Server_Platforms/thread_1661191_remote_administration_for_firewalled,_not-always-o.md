---
title: "remote administration for firewalled, not-always-on systems?"
date: 2011-01-06
forum: Server Platforms
---

### Post by bcrowell on 2011-01-06
I have a classroom (a physics lab) with seven Lucid systems that I administer myself. Seven is not a huge number, but even so, I'm finding that it gets pretty time consuming to administer them by hand. I would like to find some way to remotely administer them so that, e.g., I can update a config file on all seven machines from home, without doing any steps seven times. These machines are not always on, and they are behind a firewall, so I can't ssh into them. (No, IT at my school is not going to change the firewall settings for me.)

The basic technique I'm thinking would work would be to have an anacron job that would check a certain URL on a server I run, and if there's a shell script there, execute it as root. The shell scripts would be signed using asymmetic encryption.

I'm thinking of doing this as a DIY software project, but am I reinventing the wheel? Surely I'm not the first person in the world to need to administer a bunch of linux desktop machines remotely, although it probably is unusual for the admin not to be able to ssh in. Googling for remote administration tools turns up a lot of stuff along the lines of either VNC or webmin, neither of which is appropriate for my needs. (And I also hate the clicky-clicky-on-the-mouse stuff.)

It seems like there are some aspects to the design of such a tool that would be difficult to get right, e.g., error handling if the student using the computer shuts it down in the middle of the process. I might just want to leave the computers on when I go home on Friday, scheduling all admin scripts to run on Friday night and then having the machines shut themselves down.

A lot of the operations I'd be doing would be apt-get installs or apt-get updates; how robust are these if the computer gets shut down unexpectedly?

Thanks in advance for any advice!

-Ben

---

### Post by spynappels on 2011-01-06
Could you set up an OpenVPN server at home and connect each machine to it as a client? It is unlikely that traffic coming out is also firewalled, and if it is, you can send it on an open port such as 443 and have your VPN server listen on that port. Youd then be able to SSH in and do whatever you needed to on the VPN tunnel.

---

### Post by bcrowell on 2011-01-06
> **spynappels said:**
> Could you set up an OpenVPN server at home and connect each machine to it as a client? It is unlikely that traffic coming out is also firewalled, and if it is, you can send it on an open port such as 443 and have your VPN server listen on that port. Youd then be able to SSH in and do whatever you needed to on the VPN tunnel.

Aha, thanks, that's very helpful! That would certainly take care of the security and networking part of it.

---

### Post by truant on 2011-01-06
You might want to look into using Puppet to manage configuration of multiple machines.  That way, once they're set up, you only have to change the server and all the clients should update themselves.  IIRC, the server doesn't even have to be in the same network, so as long as each machine can see the outside in some way, you don't need remote access (except for initial install/setup, obviously)

[http://www.puppetlabs.com/](http://www.puppetlabs.com/)

It might be a bit overkill for just 7 machines, but then overkill is the best kind of kill.

---

### Post by samosamo on 2011-01-06
I use puppet too.  It is very advanced but I only use it for the more simple things.  There is no GUI, but I sure would like one.

---

