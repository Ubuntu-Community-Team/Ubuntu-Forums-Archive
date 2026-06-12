---
title: "VirtualBox WinXP Machine not surfing"
date: 2012-10-22
forum: Virtualisation
---

### Post by duranl on 2012-10-22
I just rebuilt my machine.  I used to have Ubuntu 12.04 with Gnome.  Now, I have Xubuntu 12.10.  I exported my XP virtual machine before the rebuild.  It was working without any problems.  Now that I have imported it to the Xubuntu, the "Internet" is acting funky on it.  I cannot connect to google.com, reddit.com, [www.nytimes.com](www.nytimes.com), nor ubuntuforums.org.  The network connections in XP says that it is connected.  I did a tracert which made it.

> tracert 8.8.8.8

However, when I try

> tracert [www.google.com](www.google.com)

it states that it could not resolve the target system name.

I didn't change the TCP/IP on the windows machine.  It is set to obtain IP address and DNS automatically.

I'm writing this post from the machine in Xubuntu, so the "Internet" is working fine on that.  Also, I installed the VirtualBox extension pack so I could use USB 2.0 on it.

Any suggestions on what I can do to figure this thing out?  This is a huge pain since I need the Office and SPSS installations on the XP to authenticate so I could use them for school/work.

One love

---

### Post by duranl on 2012-10-22
I figured out how to solve it.  I copied the DNS servers from Xubuntu network setup and input them into the Virtual XP machine.

-10/22/12  Nevar forget

---

### Post by coldraven on 2012-10-22
Sorry but I don't have my XP VM installed at the moment but try this:
Go here and click on the image of issue 61 to download it
[http://fullcirclemagazine.org/issue-61/](http://fullcirclemagazine.org/issue-61/)
Then read page 15 about VM networks.

I had the same problem and I think I just changed the setting in Virtualbox >network>Adapter type and it started working again

---

### Post by duranl on 2012-10-28
Thanks!   I switched to a bridged adapter and now it pull DNS servers just fine.

---

### Post by c911darkwolf on 2012-10-30
I use the default NAT option in Virtual box and it picked up my local network fine.  

Did that not work as well ?

---

