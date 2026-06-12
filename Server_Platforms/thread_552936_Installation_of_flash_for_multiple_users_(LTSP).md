---
title: "Installation of flash for multiple users (LTSP)"
date: 2007-09-17
forum: Server Platforms
---

### Post by stephenwalder on 2007-09-17
Hi,
I have a small query that I think somebody will have a simple answer for.

We've setup LTSP in our primary school. I have created user accounts for 40 or so children.

When I log in as a child I am required to setup flash in the web browser. Does this mean that each user would have to individually setup flash for their user profile? It would make much more sense if I could just setup flash for all the users in one fell swoop. Is this possible?

I would be very grateful if somebody could point me in the right direction here.l I can also forsee the same problem happening when I want each user to have Java, Acrobat Reader, etc, etc.

Your kind help would be much appreciated! 

Thanks in advance,

Stephen Walder
Holmfirth Junior, Infant and Nursery School, Huddersfield

---

### Post by koenn on 2007-09-17
have a look here : 
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

you'll notice that for a system-wide install, you just copy files to
/usr/lib/firefox/plugins/

don't know about LTSP but I expect you can do somthing similar (presumably in the ltsp chroot). 

For other system-wide software installs, I suspect there's some way of moving into the chrooted system and do admin tasks there, such as install software, so it will be present on the system the clients get to use. 

I think googling 'chroot' could get you started

---

