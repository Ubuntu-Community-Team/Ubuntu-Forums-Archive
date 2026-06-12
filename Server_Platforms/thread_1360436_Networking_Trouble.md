---
title: "Networking Trouble"
date: 2009-12-20
forum: Server Platforms
---

### Post by Skidbladniir on 2009-12-20
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 70.114.165.30
gateway 70.114.160.1
netmask 255.255.255.0
network 70.114.160.0
```

sudo /etc/init.d/networking restart

* Reconfiguring network interfaces
SIOCADDRT: NO such process
Failed to bring up eth0

Sorry, probably typos.  I typed that without seeing the screen.  I was looking at my server's screen (One screen - VGA splitter).  Please help.

---

### Post by Skidbladniir on 2009-12-20
Ok, I got it working, (forgot my netmask ends with .224), but now if I try 70.114.165.30, it always gives me a timed out error.

I also tried switching it to port 81 just because I thought my ISP might have blocked incoming port 80s.  Please help.

Also, putty (openSSH) times out also.  Is there anything I can do to fix this?

---

### Post by ephmanjmm on 2009-12-21
I most likely missed something but what do you mean that you switched it to port 81?
Are you trying to run a web server?  From where did you attempt to access this machine and what was the IP address of the machine attempting access?  Is this machine, i.e. 70.114.165.30, behind a firewall and or a router over which you have control?
Have you tried to ping the 70.114.165.30 address from the local network or from itself?

---

### Post by Iowan on 2009-12-21
> **Skidbladniir said:**
> Also, putty (openSSH) times out also.  Is there anything I can do to fix this? By name or IP address? If IP works, but name does not, check */etc/resolv.conf*.
Do you have local DNS server - are you using */etc/hosts* file?

---

