---
title: "Ubuntu Server Help!"
date: 2007-05-27
forum: Sun Sparc Users
---

### Post by dillbertdabomb on 2007-05-27
I would like to know what the best guide to ubuntu server 7.04 (sparc) is.
 
And I thought working with these things was easy!
 
Also I would like to know how to connect two computers togater without internet (sun ultra 5 and a HP pavilion) using the ethernet ports.
 
Thnaks for any help!

---

### Post by prince_of_hackers on 2007-05-29
I can't answer your question about the guide, for my use of Ubuntu on a server, I have consulted numerous Linux books and websites, and of course, these forums.

As far as connecting two computers using the ethernet ports, if you don't want to connect anything other than these two computers up, you can use a crossover ethernet cable. (Note that this will usually work at 100mbps, however, the official standard recommends against it) However, this will only establish a physical connection - you will still need to configure your network settings and you will need to configure the appropriate servers and clients on each computer depending on what purpose you are wanting to connect the computer together for. If you tell me what your intended purpose in connecting the computers together, maybe I can help you more.

Also, what operating systems are you running on each system? I assume Ubuntu on the Ultra 5, but what about the HP?

---

### Post by didijeeeke on 2007-05-30
> **dillbertdabomb said:**
> I would like to know what the best guide to ubuntu server 7.04 (sparc) is.
 
And I thought working with these things was easy!
 
Also I would like to know how to connect two computers togater without internet (sun ultra 5 and a HP pavilion) using the ethernet ports.
 
Thnaks for any help!
 Just make sure you use for both machines the same subnet 

192.168.1.*

You don't need a gateway or dns server just leave those empty. 

Like the prev. poster said you can use a crossover cable 
Or  just put both computers into a switch or huib. 
Putting a normal cable between those computers wil not work. 

If you want to file share between windows and ubuntu.

Samba is the keyword you need
.> Note that this will usually work at 100mbps, however, the official standard recommends against it) 
I keep learning every day :) did not know the standart does not like cross

---

### Post by prince_of_hackers on 2007-05-30
To make a little more clear what didijeeeke said, you will need to set up both machines to use static IP addresses on the same private subnet - for example:

HP) IP: 192.168.1.1, subnet mask: 255.255.255.0
U5) IP: 192.168.1.2, subnet mask: 255.255.255.0

Of course, as didijeeeke said, you can use any IP address for the machines starting with 192.168.1.x, as long as each machine has a different IP. After configuring the machines this way, you will have established physical and transport layer communications between the two machines, and you will just need to install the appropriate server(s) and client(s) to share data between the machines. I will assume that you are wanting to share files, however, what servers you want to use will depend on what operating systems you are using on each machine. If the HP is running Windows, didijeeeke is correct, the best bet will be to install Samba and SWAT (Samba Web Administration Tool) on the Linux box to allow it to share files like a Windows file server. However, if both machines are running Linux, it would be quicker and easier to use NFS to share files. I believe in Ubuntu you need to install the nfs-kernel-server package. ```
sudo apt-get install nfs-kernel-server
``` You will need to edit the /etc/exports file to share directories - see the man page for the exports file to find out how to do this. Then you will be able to mount directories shared from the server machine on the client machine.

> [QUOTE]Note that this will usually work at 100mbps, however, the official standard recommends against it)

I keep learning every day did not know the standart does not like cross[/QUOTE]

I think I read that in the installation manual for an Intel hub that I bought - it indicated that the 802.3u (100Base-TX) standard did not allow you to use a crossover cable like the 802.3i (10Base-T) standard did. However, most equipment apparently supports it, as I use crossover cables on 100mbps ethernet on a regular basis, and have not yet encounted a problem with it. ;)

---

