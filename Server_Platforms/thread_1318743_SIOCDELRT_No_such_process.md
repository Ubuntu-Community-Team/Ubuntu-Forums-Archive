---
title: "SIOCDELRT: No such process    ?"
date: 2009-11-07
forum: Server Platforms
---

### Post by darksideforge on 2009-11-07
I just edited /etc/network/interfaces to give myself a static IP and then I did
```
sudo /etc/init.d/networking restart
```
and i received the following error:
```
SIOCDELRT: No such process
```

What am I doing wrong?

---

### Post by darksideforge on 2009-11-07
I still don't know where the error came from, but my static IP is up and running.  I won't mark this as "SOLVED" for another day or so to see if anyone has any answers on what a SIOCDELRT is.

---

### Post by Iowan on 2009-11-08
Sounds like "delete route". [Here]("http://www.howtoforge.com/forums/showthread.php?t=7949") is a similar problem - it also seemed to work, despite the error messages.

---

### Post by darksideforge on 2009-11-09
> **Iowan said:**
> Sounds like "delete route". [Here]("http://www.howtoforge.com/forums/showthread.php?t=7949") is a similar problem - it also seemed to work, despite the error messages.

Thanks!!

---

### Post by Distortedgamer on 2010-05-25
I am having a similar issue. I setup static IPs in /etc/network/interfaces and then when I restart it, I get that error. The static IPs work for the most part, but every once in a while I will run an ifconfig and they switch to DHCP. Then I restart the networking, get that error, then they go back to static. 

Any ideas on how to keep them static all the time?

---

### Post by fdelval on 2010-06-29
Bump for help...

---

### Post by oldschoolDebian on 2010-07-31
> **darksideforge said:**
> I just edited /etc/network/interfaces to give myself a static IP and then I did
```
sudo /etc/init.d/networking restart
```and i received the following error:
```
SIOCDELRT: No such process
```What am I doing wrong?


first off you need to edit your /etc/hosts file * use vi,  nano, gedit * what ever flavor  txt editor you like```
sudo nano -w /etc/hosts
```add your ip address and your name at line three 

```
127.0.0.1    localhost    linux
#127.0.1.1    linux.WorkGroup    linux
192.168.20.20    linux.mydomain.com linux # <------ add your ip and name 


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```then restart your network and the error is fixed, the edited /etc/host file is also need for the static changes you made

---

### Post by ammofreak on 2012-04-20
TY oldschoolDebian:D

---

