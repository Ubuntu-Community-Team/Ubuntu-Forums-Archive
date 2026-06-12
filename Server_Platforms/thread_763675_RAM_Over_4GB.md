---
title: "RAM Over 4GB"
date: 2008-04-23
forum: Server Platforms
---

### Post by Deathrend on 2008-04-23
So I just picked up two servers with over 4GB of RAM.  I'm currently trying to decide how to use it.  To start off, 64bit is out of the question, just not possible.  They have Quad PIII Xeons.

I know with Windows Server, I can use Enterprise to use either 8, and 16, or I can use /PAE in the boot script to bring it well over 4gb in a 32bit OS.  My question, how can I do this using linux? More specificly, non-guit linux.  I plan to use this for VMWare Server, and that's it.

I really like Ubuntu Server, so I wanted to stick with it, but if it's not possible, then I'll have to go with Windows Server :(

---

### Post by Deathrend on 2008-04-23
Well, I've never been a big Red Hat fan, atleast not in years, however I'm now finding this [http://www.cyberciti.biz/tips/redhat-enterprise-linux-4gb-plus-ram-support.html](http://www.cyberciti.biz/tips/redhat-enterprise-linux-4gb-plus-ram-support.html) 

Anyone know of something like this for Ubuntu?

---

### Post by chefweb on 2008-04-23
just install ubuntu-image-server and the restricted-modules

 sudo aptitude install linux-image-server linux-restricted-modules-2.6.24-16-server 

the server kernel supports PAE

---

### Post by vpsville on 2008-04-23
The 32bit server version of Ubuntu supports > 4GB of ram via PAE.  You don't have to do anything, it will just work.

---

### Post by honeydew on 2008-04-23
all of our servers are running ubuntu 32bit and they do not encounter issues with 4GB of ram.

---

### Post by Deathrend on 2008-04-23
My problem isn't 4gb however, I'm using around 8.6 Gigs in one, and over 16 in the other.

The server with 8 gigs loaded Ubuntu-server ok, just kind of hung the first time around.  It also had a problem seeing the disk arraay.  It doesn't however see over 4Gigs, only not the full 8+, instead it seems to only see 7.6 Gigs.  This seems like a small price to pay for that much however.  Probbably a bit overkill for quad PIII Xeons anyway..

---

