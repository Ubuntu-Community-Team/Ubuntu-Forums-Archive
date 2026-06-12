---
title: "Newbie wanting to setup a Terminal Server"
date: 2010-09-14
forum: Server Platforms
---

### Post by Affrikka on 2010-09-14
Hi all,

My school just bought all new servers, and since their old ones aren't marked or anything, the computer teachers can give them away and not prove that they were ever even at this school. So, I got two servers in my house now, my dad is going to use one for.. something, and i was interested to learn ubuntu server myself. He wants me to learn how to setup and use a terminal server, and learn everything about it and whatnot. I've been an ubuntu user for... years now, but i've never messed much with command line terminal stuff. I can do the basic apt-get things, but that's about it.
My dad had me install webmin, and it seems pretty nice, but can anyone point me in the right direction to start learning more about how to use ubuntu server, and, better yet, setup and learn everything about using terminal servers? that would be awesome.


thanks in advance!


Mathieux

---

### Post by CharlesA on 2010-09-14
I've only really heard the term "terminal" server when refering to Windows Servers using RDP to connect.

I guess you could use FreeNX, but I don't know what you really want to accomplish.

---

### Post by Affrikka on 2010-09-14
from what i can tell (i'm not nearly as computer-whiz as my dad) he wants to setup a server that can host (what my server can support) 30 VMs so that ultimately, an end-user can have a very basic computer with no hard drive that boots from the network, the server gives the end-user the desktop. If that makes any sense. Basically, he wants the server to act as the hard-drives for the end-users computers (but all the machines will be VMs)

EDIT: i'm looking more for something along the lines of LTSP

---

### Post by CharlesA on 2010-09-14
Yeah, that sounds like LTSP. Not sure how to exactly set one up tho.

There's a boatload of documentation [here]("https://help.ubuntu.com/community/UbuntuLTSP").

---

### Post by Baked- on 2010-09-15
> **Affrikka said:**
> from what i can tell (i'm not nearly as computer-whiz as my dad) he wants to setup a server that can host (what my server can support) 30 VMs so that ultimately, an end-user can have a very basic computer with no hard drive that boots from the network, the server gives the end-user the desktop. If that makes any sense. Basically, he wants the server to act as the hard-drives for the end-users computers (but all the machines will be VMs)

EDIT: i'm looking more for something along the lines of LTSP


It may be much easier to setup 3 or 4 more powerful vservers and use neatx
[http://code.google.com/p/neatx/](http://code.google.com/p/neatx/)

---

### Post by Affrikka on 2010-09-15
thanks everyone for the replies! i'll look into it all!

---

