---
title: "TCP &amp; UDP requests to port 29974?!"
date: 2009-06-05
forum: Security
---

### Post by IceRayn on 2009-06-05
After booting into Ubuntu, I went to disable my firewall, as I usually do, and just to check, I checked the Events tab, seeing 1 request to port 29974, I figured it was someone using the wrong IP, I waited, and started to see a bombardment of 29974 TCP and UDP connections being attempted from many source IP's. I'd really like to know what the h*** is trying to use my port 29974, and what that port is used for. It is opened on my router because I host a Quake 3 server, so I opened 29000-30000. I also have 80, 5900, and others open, and am now scared. What is the communities advice? Restart my modem for a new IP?

Thank You,
IceRayn

PS: From Firestarter: Source:79.111.115.238 Destination:192.168.1.148 Length:48 TOS:0x00 Protocol:TCP Service:Unknown

---

### Post by movieman on 2009-06-05
If your ISP gives you a dynamic IP, it's quite likely that someone was previously using a P2P program on that IP address and various machines out in the world still expect it to be running on that port.

As you suggested, restart the ISP connection to get a new IP address and check that the connections stop.

---

### Post by lovinglinux on 2009-06-05
> **movieman said:**
> If your ISP gives you a dynamic IP, it's quite likely that someone was previously using a P2P program on that IP address and various machines out in the world still expect it to be running on that port.

As you suggested, restart the ISP connection to get a new IP address and check that the connections stop.

+1

They are called ghost packets.

---

### Post by cdenley on 2009-06-05
> **IceRayn said:**
> 
I also have 80, 5900, and others open, and am now scared.


Are you running a VNC server on port 5900? I don't think VNC is considered secure, and you shouldn't allow remote connections unless it is tunneled through an encrypted tunnel such as SSH.

---

### Post by IceRayn on 2009-06-05
Yes, I think that it was the P2P explanation. I was running uTorrent in WinBl0ws before I booted into Ubuntu. I'm assuming that it was leachers still looking for my seeding? Thank you for your help, and a restart of my modem helped. No more 29974. 

Thank You,
IceRayn

---

### Post by lovinglinux on 2009-06-05
> **IceRayn said:**
> Yes, I think that it was the P2P explanation. I was running uTorrent in WinBl0ws before I booted into Ubuntu. I'm assuming that it was leachers still looking for my seeding? Thank you for your help, and a restart of my modem helped. No more 29974. 

Yes, [exactly](http://ubuntuforums.org/showpost.php?p=7391948&postcount=3). Restarting the modem solves the problem because the ISP reassigns an new IP for you. Your previous IP will be assigned to someone else, who will then post a new thread complaining about lots of hits on port 29974 :)

---

