---
title: "ubuntu server 12.04 network will not start"
date: 2013-10-03
forum: Server Platforms
---

### Post by scottie4442 on 2013-10-03
Ok I tried to find this in the forums and no go so far.  I just setup an Ubuntu Server 12.04 using ubuntu server 12.04.3 32-bit iso.  when I rebooted everything seemed to work, but when I went in tried to update got a bunch of errors.  long story short, I checked and networking will not start, it shows stop.waiting when I do sudo service networking start, even though I can do sudo ifconfig eth0 up (same for eth1). I can ping the gateway and other systems outside of this server, but networking still will not start.  This is the 32 bit version, I had the 64 bit version and though that might be the problem, but still no change. I have looked around and tried to find a log file to check for network errors, but no luck so far.  I have checked out lshw, ifconfig, lspci (every command I can think of) and the network cards show up fine and they are being activated fine, also they look like they work ok, ifconfig and ping prove this. Not sure what to try now, this is driving me crazy.  I have used Linux for years so I am not new to the game, just never seen this before, I have setup dozens of Linux servers before and never had this problem.  Any help at this time would be appreciated.

---

### Post by scottie4442 on 2013-10-03
Ok progress. I have the network interfaces up but still sudo service networking start shows stop/waiting. seems to be working so far so will continue from here.

---

### Post by scottie4442 on 2013-10-04
The pain with this issue is that after a reboot I have to manually start the interfaces and run ip forwarding command and add a route by hand, I have these defined in the interfaces file and in sysctl but they will not start because of the networking issue. I am still researching how to fix this but I will make a script to start everything by hand if necessary.

---

### Post by spynappels on 2013-10-05
I presume you are happy with your /etc/network/interfaces file and have attempted to use ```
/etc/init.d/networking restart
``` to bring the interfaces up?

Does the network stack work ok using only the loopback interface?

---

### Post by scottie4442 on 2013-10-05
Haven't tried the loopback only, but if I hand type everything the network works fine, I setup IP_forwarding and a static route to another machine, just networking will not start. Yes I did try the init.d method and the service method as well, no good.

---

