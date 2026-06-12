---
title: "Active Directory Replacement"
date: 2007-01-14
forum: Windows
---

### Post by geekender on 2007-01-14
Anyone know of a Linux based solution to replace Active Directory?  I have seen OpenLDAP for authentication but I am looking for something that can push out policies and software, etc and run it on a Linux machine.  I guess I could run Server 2003 in a VM, but I was hoping there was a native solution.  

Thanks in advance.

---

### Post by Hendrixski on 2007-01-14
Hey, hope that it's not too late for you to get an answer on this, but the reason that there is no separate software in Linux for the kind of stuff that Active Directory does is because it's inherent in the operating system, so you don't need a program to do it.  This has been the case ever since UNIX came out, and Windows didn't come out with a way of managind directory services untill 2003.  That's why they're so behind on the server market.

So yes, there is an active directory replacement, and it's virus free.  It IS Linux.

---

### Post by geekender on 2007-01-15
I really appreciate your reply.  However, being a Microsoft person, how can I get more information on how to do this?  I mean, if I want to push firefox with options to every desktop, do I set it up on one machine and have all workstations use that as their X server?  It seems that way though there would be no redundancy if the main server failed.  I am not sure the procedure for doing this on the workstations.

---

