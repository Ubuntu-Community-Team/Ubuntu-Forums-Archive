---
title: "clients dont connect to the internet"
date: 2008-10-21
forum: Server Platforms
---

### Post by machinakias on 2008-10-21
hi all! i'm trying to set up an ubuntu server like this:
etho 192.168.0.10 (gateway 192.168.0.1 - from a modem router)
eth1 192.168.0.20 for connecting a switch to my clients

the thing is that i cant get internet to my clients whatever i do...tried many configurations but no luck...my cards work fine,but after installing some stuff (updates or webmin etc) i cant connect to the internet...what is wrong? any ideas? please,i'm trying since  august...to set up this thing!

---

### Post by neilengineer on 2008-10-21
Can it be possible something is wrong with the firewall(after update? Or I don't know if Ubuntu Server has SELinux, if does, maybe SELinux will matter.

---

### Post by machinakias on 2008-10-22
> **neilengineer said:**
> Can it be possible something is wrong with the firewall(after update? Or I don't know if Ubuntu Server has SELinux, if does, maybe SELinux will matter.


well,there's apparmor which i have uninstalled...tried many tutorials,many configurations but still no clue what's wrong...any one?

---

### Post by Iowan on 2008-10-22
I'm probably off-base, but I don't know if the system will like having both devices in the same subnet - plays havoc with routing. Do clients have static addresses, too - or are they DHCP via server? Could you move clients and eth1 to 192.168.1.x subnet - then you'd need to do [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

---

### Post by lykwydchykyn on 2008-10-22
I'm going to second Iowan.  If you are using your Ubuntu server as a gateway for the clients, you are going to have to put the two NICs on different subnets.  You can't route to the same subnet.  You'll also need to make sure your clients are getting IP's somehow as well as a default gateway (eth1's IP), and DNS settings.

Apart from that you'll need IP forwarding working between the two interfaces.

---

### Post by machinakias on 2008-10-24
well folks the idea is this: set up theserver as a dhcp server fo my clients,and also as a gate to the internet.so you think that i must set eth0 to 192.168.0.x and eth1 to 192.168.1.x ? if so,what next? i'm not sure if the clients can get to the internet...but i'll give it a try...so,thank you and i'll be back when i try it...see ya!:)

---

### Post by machinakias on 2008-11-02
hello all...back again with the same problem...tried different things but still no luck....got any ideas???

---

### Post by lykwydchykyn on 2008-11-02
Have a look over this:
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Seems like you may have forgotten a few steps.

---

### Post by Iowan on 2008-11-03
Oops, I just noticed that my [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") link didn't go anywhere - actually linked to this thread... I fixed it, and included it again.

---

