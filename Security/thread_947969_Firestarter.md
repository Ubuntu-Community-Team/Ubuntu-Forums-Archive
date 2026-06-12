---
title: "Firestarter"
date: 2008-10-14
forum: Security
---

### Post by SSVegito888 on 2008-10-14
What program does Firestarter use to create the firewall. Eg. ufw, iptables, netfilter, etc.

---

### Post by kevdog on 2008-10-14
All programs down below have to access netfilter -- this is part of the kernel.  I believe firestarter uses iptables rules to interact with netfilter, however you might want to verify this.

---

### Post by SSVegito888 on 2008-10-14
I tried looking briefly at the firestarter website, but couldn't find anything about this.

---

### Post by SSVegito888 on 2008-10-14
The only thing I really need to know is if Firestarter is secure or not.

---

### Post by kevdog on 2008-10-14
I don't know how to answer this since the question really doesn't make that much sense.  netfilter/iptables is definitely secure.  Firestarter is just a frontend to such a program.  Its secure it that configures rules appropriately and correctly, however it does not offer or provide full functionality -- meaning that there are many other ways you can configure your packet routing and blocking capabilities using iptables directly.  Firestarter gives you the most common features that are needed by many "home" users, however if you need to do something fancy, or configure a gateway, etc, you are going to have to use some other type of interface.

---

### Post by SSVegito888 on 2008-10-14
OK. Thanks.


I am a home user, but just for the sake of gaining knoledge, are there any GUIs to do what you mentioned?

---

### Post by kevdog on 2008-10-14
There is the GUI for the UFW, however again I don't believe its fully featured:
[http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html)

To be honest with you -- since this is straightalk -- I don't know what you want to do.  If its anything I would consider advanced with packet routing or advanced filtering, I would suggest either buying a book, or just looking for an iptables tutorial on the internet (frozentux).  Its very hard at first to get your head around, however with time the knowledge comes.  Its nothing you are going to figure out in 5-10 minutes.  Maybe like several months.  The more you configure firewalls and look at other people's examples on the internet, the more you will gain skill.

---

### Post by SSVegito888 on 2008-10-16
Thanks for the info.  I will look into this.




Thanks Again,

SSVegito888

---

