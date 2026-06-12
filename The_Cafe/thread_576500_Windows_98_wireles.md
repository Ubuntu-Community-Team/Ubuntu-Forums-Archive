---
title: "Windows 98 wireles???"
date: 2007-10-15
forum: The Cafe
---

### Post by jgrabham on 2007-10-15
OK, long story short, one of my laptops needs to run 98 (SE).

It is an IBM thinkpad 600 with a 300Mhx P2 and 224 MB RAM.

So  have everything working (even USB pen drives!!!) exept the internet.  I installed the software for my Linksys wpc54g wfi card, shoved it in, told it my WEP key, and... It doesnt work.  Apparantly its connected to the router, but the routers not connected to the net.  I know this isnt true, because Im talking to you from another PC on the wireless network.  Network neighbourhood etc have appeard, so in theory Im on the network... But Im not.  My router says there are 2 PCs on the network, but there should be 3.


Please help me, Im close to jumping out of the window.

EDIT: It says the IP is 169.254.114.218   Im sure it should be 10.0.0.x.   :/  Downloading newer software from lynksys atm, will get back to you.

---

### Post by Dr. C on 2007-10-15
I would open an MS DOS box (Windows Terminal) and type ```
ipconfig /all
```This should tell you what is going on, IP,  DNS servers, gateway, etc. If you are getting an IP address but not on you router are you connecting to the correct wireless network?

---

### Post by jrusso2 on 2007-10-15
in windows 98 its winipcfg not ipconfig.

You don't have a valid IP set. Does your network run DHCP?

If so its not getting the DHCP.  You can try setting it manually.




If so and your have an IP, DNS and gateway configured.  Try running it open.  See if its a WEP problem.

---

### Post by SunburnedCactus on 2007-10-15
A 169.blahblah IP address usually means a problem with the wireless key yeah, the computer hasn't been able to reach the DHCP server.

---

### Post by mthakur2006 on 2007-10-15
oh i have been thru this so many times....it seems that the sun, earth and the moon have to line up for it work properly.
What I would suggest doing is try with No encryption and static IP addresses with the firewall turned off first off all, then switch one thing on and see what causes the problem and take it from there.
Another thing, on windows, an IP address of 169.xxx.xxx.xxx usually means that it has failed to make a connection.

On another note, if you don't mind sharing, could you tell us why the laptop needs to run windows? you could easily run xubuntu or arch or any linux distro on it, even a lightweight gnome (do a forum search, i have seen a guide on how to do it :))

mrinal

---

### Post by jgrabham on 2007-10-15
> **mthakur2006 said:**
> 
On another note, if you don't mind sharing, could you tell us why the laptop needs to run windows? you could easily run xubuntu or arch or any linux distro on it, even a lightweight gnome (do a forum search, i have seen a guide on how to do it :))



I need to use 98, because 2000/xp just runs like a dog, and there are no graphics or sound drivers for linux, Ive spent hours trying to make linux work with various distros, it just doesnt want to play.

---

### Post by jgrabham on 2007-10-15
CHanged  WEP from open to shared - now it works.

thanks anyway.

---

