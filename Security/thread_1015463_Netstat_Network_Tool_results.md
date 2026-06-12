---
title: "Netstat Network Tool results"
date: 2008-12-18
forum: Security
---

### Post by Red Rebel on 2008-12-18
Netstat Network Tools is showing these active network services. (sorry I could not show screen

protocol   ip source port/service  state
  
  tcp      127.0.0.1    631         listen
  udp      0.0.0.0      59669
  udp      0.0.0.0      68         
  udp      0.0.0.0      5353

by the way, uder "Events", on the Firestarter Firewall Configuration Application, these do not come up? Can someone tell me what these active network services are, and are the normal? Any help would be greatly appreciated.

---

### Post by slowth5 on 2008-12-18
Hi Red Rebel,

sudo netstat -pantu

This will give you the program for the tcp and udp connections, without all of the sockets.  My netstat output mirrors yours, so I'm assuming it's normal.

---

### Post by jerome1232 on 2008-12-20
Port 631 on 127.0.0.1

That is the cups daemon listening on for local connections only (so no remote computer can even attempt exploiting it the connections will just get dropped) cups is the linux printing service.

port 68 is dhcpd, it is necessary for the automatic allocation of ip addresses on your local network.

Port 5353 is Avahi

Avahi is a system which facilitates service discovery on a local network. This means that you can plug your laptop or computer into a network and instantly be able to view other people who you can chat with, find printers to print to or find files being shared.

port 59669 I'm actually not sure what that is it's not running on my system...

---

### Post by Red Rebel on 2008-12-21
port 59669 I'm actually not sure what that is it's not running on my system...

thanks for the info. I will try to research port 59669 further....

---

### Post by Red Rebel on 2008-12-21
Well, I checked netstat tools again, and port 59669 is gone, instead, 33333 appeared in its place. Ran sudo netstat -pantu and it shows: udp        0      0 0.0.0.0:33333           0.0.0.0:*                           4542/avahi-daemon:

---

### Post by slowth5 on 2008-12-21
It searches random ports because it's a local network discovery tool. I've looked into avahi-daemon a bit more, and I don't require the service it provides, so I deleted it.

---

