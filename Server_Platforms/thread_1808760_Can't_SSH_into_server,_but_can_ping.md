---
title: "Can't SSH into server, but can ping"
date: 2011-07-20
forum: Server Platforms
---

### Post by OzuYatamutsu on 2011-07-20
Ah sorry, ignore the title, I can't ping the server after all...

Hi, I'm having a bit of a problem. After changing something with update-rc.d (I probably screwed something up, I know :(), I can no longer ssh into the server or ping to it. Connecting a monitor to the server just gives me the message "Nonsupport video mode". However, I can still access the shell (with a monitor) via rescue mode on a startup disk. 

I'm running Ubuntu 11.04 Server. Any help you can give me would be appreciated!

---

### Post by karlson on 2011-07-20
> **OzuYatamutsu said:**
> Ah sorry, ignore the title, I can't ping the server after all...

Hi, I'm having a bit of a problem. After changing something with update-rc.d (I probably screwed something up, I know :(), I can no longer ssh into the server or ping to it. Connecting a monitor to the server just gives me the message "Nonsupport video mode". However, I can still access the shell (with a monitor) via rescue mode on a startup disk. 

I'm running Ubuntu 11.04 Server. Any help you can give me would be appreciated!

Check:

/etc/network/interfaces
file

Also check what happens if you do:

```

/usr/sbin/service networking start

```

This should give you ping capability.  If that doesn't then you more then likely have a hardware problem.

---

### Post by OzuYatamutsu on 2011-07-21
Thanks for the reply. I can't get to the server right now (and when I do, I'll certainly try your suggestion) but I don't think it is a networking problem or a problem with the hardware, as all was working well until I used "sudo update-rc.d" to run something at startup.

I did remember setting a static IP in /etc/network/interfaces and it working correctly, though, but that was a while ago, and I haven't changed it since then.

---

### Post by Wayne_V on 2011-07-21
when you get the 'nonsupported video mode' message try <ctrl><alt>F1 to switch to a text mode login.  should save you the trouble of booting in rescue mode.

---

### Post by OzuYatamutsu on 2011-07-21
# /usr/sbin/service networking start
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

My /etc/network/interfaces is:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

...however, I remember when I booted into rescue mode, it said something about DHCP succeeding and it got the time from a 'network time server' or something...

Wayne_V: See, that's the weird thing. The 'nonsupported video mode' comes from a text login. I don't have a desktop environment installed. :\

---

### Post by OzuYatamutsu on 2011-07-21
Nevermind, I ended up just backing everything up and reinstalling. 

Thanks for trying, though

---

