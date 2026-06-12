---
title: "VMware Server MUI"
date: 2007-03-27
forum: Server Platforms
---

### Post by goliant on 2007-03-27
Does any one have experience with the VMware ServerMUI? When I try to choose the "options" tab beside the status monitor, i get a "not authoirized to modify host configuration options" error message.

I know there is a server console - that does work. 

Any ideas? I am relatively new to the Linux OS.

Thanks for any help or ideas!

---

### Post by bturrie on 2007-07-07
I have a similar problem. It seems to me that I need either to be running with root privileges or modify the permissions associated with some folder to make this work. So far I can only list things that don't work. Here's a couple:

Logging on to the console as root (i didn't think this would work because there is no root password in ubuntu). You can add a root password (I've seen instructions on how to do this somewhere) and that would almost certainly work but I think it's a very bad idea. 

kdesu firefox [http://localhost:8222](http://localhost:8222) does open the console as root but you still need to logon as yourself at which point you get the same failure message

kdesu firefox [https://localhost:8333](https://localhost:8333) logs directly on to the https server but still has the same problem

I'm going to try to find out what permissions i need to change to give my user access. If I find out I'll post it here

---

### Post by arosenau on 2008-01-04
Did you ever find this out?

---

