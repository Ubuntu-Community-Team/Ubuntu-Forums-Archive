---
title: "newbie to servers"
date: 2008-11-29
forum: Server Platforms
---

### Post by mastercleric on 2008-11-29
I just acquired at no cost a Dell Poweredge 4400 server.
It was just taken off line and replaced by a more modern blade server and does work.

I understand it to be a Xeon dual cpu with 1 gig of ram
it has 5 harddrives, including the two 'mirror' drives. One of the hotswap mirrors has some sort of problem but all else is functional.

I have zero experience with servers of any kind.
My intent is to use this machine as a learning tool.

I have two main questions. Does the dual cpu mean that I need to use the 64 bit Ubuntu8.04?? Second,where can I go to get information concerning linux server installs, etc.??

Thanks
Mastercleric

---

### Post by CP1256 on 2008-11-29
You should look up information about your CPU to see if it's 32 or 64 bit. 

[http://www.howtoforge.com]("http://www.howtoforge.com") has good tutorials about servers.

---

### Post by cariboo on 2008-11-29
Why not fire it up and see what is on it now? there may be no need  to install a different operating system. This a great opportunity to explore and see what the server can do. Have look here for a command line summary:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

I'm assuming there is linux already installed. The command summary will also work with most of the BSD variants. If it has windows installed. it is up to you, what you want to do.

It won't matter which version you are installing 32bit or 64bit, as they are both generic kernels, meaning that they will run on almost anything.

Jim

---

### Post by tubezninja on 2008-11-29
> **mastercleric said:**
> 
I have two main questions. Does the dual cpu mean that I need to use the 64 bit Ubuntu8.04?? 



Just FYI: The Dell 4400's use 32-bit Xeons, so you actually shouldn't/can't be using a 64-bit OS on it.

---

### Post by andguent on 2008-11-29
Also keep in mind that you can run "server" software on any type of computer, even a laptop. A server of that size is fun to learn on, but expect it to eat a lot of electricity. Have fun installing software and seeing what it can do. 

As a learning experience, one possible setup to play with is VirtualBox/VMWare and see how many different OS's you can get running at once. Then, try to repeat the experiment on a generic desktop PC with 512/1024 meg of mem and see the difference.

FYI - Hardware of that capacity is most likely designed for businesses with 20-50 users, depending on what you run on it. Keep it off of carpet. If it has the fans that I think it does, it will dust your floor for you and suck everything in. Good for the floor, bad for the server.

---

