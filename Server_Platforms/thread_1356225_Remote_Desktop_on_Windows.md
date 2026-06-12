---
title: "Remote Desktop on Windows"
date: 2009-12-15
forum: Server Platforms
---

### Post by Vegan on 2009-12-15
I was wondering what program could I use to have a virtual Linux desktop on a Windows machine.

I expect something has surfaced, any favorite in the Ubuntu crowd?

---

### Post by BkkBonanza on 2009-12-15
I believe TightVNC is well liked. 
I don't use it but have heard others recommend it.

---

### Post by Vegan on 2009-12-15
Any other candidates? I wanted to review the works to see which one best fits me requirements.

I need to be able get the desktop so that I can gedit *.conf files and quickly deal with problems.

I finally fixed a vexing problem changing Apache from a unorthodox setup to vhosts linked to user accounts with a default www folder.

This way each site can be added as easy as 1, 2, 3. It was hard as I was in terra incognita. But now I have a working system. Now the fun part, making a manual of it so I can refer to it in the future.

Now at least I can rebuild the sites more easily.

The main thrust of the remote desktop is to manage a server from a single machine as though it was a just a machine in some rack buried in some row and column.

---

### Post by BkkBonanza on 2009-12-15
Another completely different way to go is to install an X window client on windows and use X forwarding with ssh. I've heard that works well too. I do a lot of server admin but never bothered with using a remote desktop. Just ssh command line here because I don't really want VNC or X windows on my server.

---

### Post by Vegan on 2009-12-15
My goal is simply to be able to manage the machine, edit config files, reboots etc.

Once I get TELNET issues fixed I can revert to CLI but I am speculating on what Linux can really do for me.

Its hard to learn all that I want to do, but I am forging ahead slowly.

Linux is not alien, but there are a lot of expectations that are hard to implement.

---

### Post by HermanAB on 2009-12-16
MinGW and PuTTY of course.
[http://www.mingw.org/](http://www.mingw.org/)

---

