---
title: "A little advice changing to ubuntu server"
date: 2009-04-29
forum: Server Platforms
---

### Post by X1R1 on 2009-04-29
Hello! im a computer technitian and I have been encouraging for the past week to change our windows 2003 server system at work to an ubuntu server one. This server is only used for proxy and corporate antivirus. 

I have NEVER installed installed ubuntu server before, so I downloaded and printed the ubuntu server guide to give it a read. It doesnt seem complicated to install and switch.

I do have experience in networking though, im Cisco CCNA and just about to finish a degree in networking and telematics, but no server configuration experience.

Current windows 2003 server has microsoft proxy server (the main reason why we want to switch, its completely obsolete and crashes everytime leaving the company without a reliable internet connection) DNS server and corporate antivirus.

So...I want to give ubuntu server a try by installing a test proxy, DNS and antivirus  in it and connect this server to the network with different DNS and proxy address, and configure some machines to go through it. Then if everything goes ok, install ubuntu replacing the windows 2003 server and switch permanently.

So, here are my questions:
-Is this hard to do? 

-Can I install ubuntu server on a decent desktop machine to make this tests? -say a core 2 duo 1Gb of RAM 260 GB hard drive and 100mbps network card (think this would be better 1Gbps card)-

Sorry for the long post but I want to be sure everything is clear, if you need any more info just ask!

Thanks for any advice you could give me! I would really appreciate it!

---

### Post by kerry_s on 2009-04-29
> -Can I install ubuntu server on a decent desktop machine to make this tests? -say a core 2 duo 1Gb of RAM 260 GB hard drive and 100mbps network card (think this would be better 1Gbps card)-

sure you can, it doesn't even need to be that good, i used this 450mhz 256mb laptop to learn way back.

the server is none gui, command line, so you just need to learn your way around and the basic commands. i recommend "mc" file manager if your not use to linux commands.

after you install the server run:
**sudo apt-get install mc**

then just run it with> mc <or> sudo mc <to work as root.

if you don't want to use a file manager look here:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by X1R1 on 2009-04-29
Thanks for your reply.

I think that the guide pretty much describes the commands used to configure it, and I read somewhere that you can install the complete desktop, configure it, and then uninstall it.

I will sure check that file manager you mentioned as soon as I have everything set up.

Thanks!!

any more advice and tips you guys can give me? post post post!!! :lolflag:

---

### Post by bigbearomaha on 2009-04-29
This forum is chock full of server posts.

search search

---

### Post by netztier on 2009-04-29
> **X1R1 said:**
> 
any more advice and tips you guys can give me? post post post!!! :lolflag:


Always: the official [Ubuntu Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html")

regards

Marc

---

### Post by X1R1 on 2009-04-29
> **netztier said:**
> Always: the official [Ubuntu Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html")

regards

Marc

Already had it and reading it

---

### Post by X1R1 on 2009-04-29
> **bigbearomaha said:**
> This forum is chock full of server posts.

search search

I know the forum is full of this type of posts, but I think this is a little different cause its pretty specific

regards

---

