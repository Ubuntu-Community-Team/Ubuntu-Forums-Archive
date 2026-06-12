---
title: "Personal Firewall"
date: 2006-08-20
forum: Server Platforms
---

### Post by blocky on 2006-08-20
I've been running my Ubuntu box for a couple of years on my internal network at my house, protected by a debian-based firewall/router. In a few weeks I am  moving into a dorm at a university, and will be connected directly to their LAN. I am wondering what the best option for creating a convient and secure firewall solution is. Should I try to hack something together with iptables, or install a premade package like firestarter? Would it be a bad idea to keep SAMBA sharing enabled with some restrictions? thanks in advance

---

### Post by meng on 2006-08-20
Firestarter provides a convenient way to configure iptables, and is my personal choice.

---

### Post by Klaidas on 2006-08-20
Agreed. Firestarter \o/ !

It has an easy interface and is powerfull too ;)

---

### Post by Gouki on 2006-08-20
I also recommend FireStarter.

---

### Post by jinx099 on 2006-08-21
I'm looking for a software firewall for my server which is on LAN behind a dedicated firewall.  I have used firestarter and it works great... if you only have 1 interface.  Is there a similar program that will allow me to define rules like firestarter, for each interface?

---

### Post by sno on 2006-08-21
^ my problem as well. 
          
-----------\/-----------

Found my solution, and its called shorewall :D

---

