---
title: "New to servers. Help me figure out what I need."
date: 2008-09-16
forum: Server Platforms
---

### Post by Tiersin on 2008-09-16
Hi there. So I just finished building my server. Here are the specs:
ASUS micro ATX mobo
Intel Pentium E2180 Allendale 2.0GHz LGA 775 65W Dual-Core Processor
640 GB WD HDD
2 gigs pqi DDR2 RAM

Anyway, I'm able to find my way around in Linux and I want to set up a versatile home server. Ultimatly, here is what I would like to be able to do with it. (like I said, i'm very new to this so please bear with me.)

1. Have an FTP server so that myself and my roomates can backup and store there files in there own home directory over the network. Eg. they can acess there home directory over the network through Mac/Windows/Linux.
2. Be able to have some sort of remote desktop.
3. Somehow be able to access my files remotely over the internet. 
4. Be able to host websites eventually.

I know this may seem vague. But I'm very new to this. And I have always not been so great with networking. I'm not looking for a list of steps to get stuff don't as much as an explanation of each step. I've looked at things like "The perfect home server" on howtoforge.com and the problem if i have no idea what each step does. Any help in getting me in the right direction would be appreciated. Thanks.

BTW: The server will be running Ubuntu 8.04 and I also have a Windows Vista machine, another Ubuntu machine, My roomate has a Mac, and my other room mate has an XP laptop. I would like for them all to be able to access the server. We have a wireless network running through a Linksys WRT54G router. The server is connected directly, but everything else connects through the wireless network.

---

### Post by lazyart on 2008-09-16
1. vsftp
2. VNC is okay across a lan, but if you're accessing via internet look at nxmachine/nomachine
3. OpenSSH-Server and/or vsftp
4. LAMP stack

You'll have to read up on port forwarding to get connections from the internet to reach your machine.   And you'll need a way to access your server by name-- NoIP or DynDNS are a must here, unless you have a static IP address.

---

### Post by Paul41 on 2008-09-16
> 1. Have an FTP server so that myself and my roomates can backup and store there files in there own home directory over the network. Eg. they can acess there home directory over the network through Mac/Windows/Linux.

You could use samba for this instead of FTP.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by TigerWolf on 2008-09-16
What exactly do you need help with? 

The packages you should install?
A guide on how to set up your server?
or something else.

---

### Post by Tiersin on 2008-09-16
> **TigerWolf said:**
> What exactly do you need help with? 

The packages you should install?
A guide on how to set up your server?
or something else.

I'm looking for more of a point in the right direction. Once I know exactly what I need, I can figure the rest out.

---

### Post by Iowan on 2008-09-16
May I suggest you check some of the "perfect server" articles at [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu").

---

