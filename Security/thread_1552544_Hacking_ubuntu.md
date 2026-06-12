---
title: "Hacking ubuntu?"
date: 2010-08-13
forum: Security
---

### Post by binarylife on 2010-08-13
I heard before I've installed ubuntu , that linux system can't be hacked, so is that possible to hack my computer , because I noticed that someone is hacking my ubuntu ? 
thanks !

---

### Post by TheWeakSleep on 2010-08-13
What do you mean you've noticed someone has been hacking your computer?

---

### Post by uRock on 2010-08-13
Any OS can be hacked, but it is not likely.

Are you using a router?

Have you installed any server software?

Have you downloaded and installed anything that was in the Ubuntu Software Center?

[s]What makes you think your system is being hacked?[/s] What symptoms are you seeing that would make you think you are being hacked?

---

### Post by binarylife on 2010-08-13
> **uRock said:**
> Any OS can be hacked, but it is not likely.

Are you using a router?
yes,Siemens

Have you installed any server software?
just ubutnu sources and some other resporites

Have you downloaded and installed anything that was in the Ubuntu Software Center?
I've downloaded pidgin .

[s]What makes you think your system is being hacked?[/s] What symptoms are you seeing that would make you think you are being hacked?

pidgin minimize into the dock by itself and sometimes closes

---

### Post by Zeike on 2010-08-13
That doesn't sound at all diagnostic of hacking to me...

---

### Post by Iowan on 2010-08-13
Moved to Security Discussions...

---

### Post by uRock on 2010-08-13
> **binarylife said:**
> pidgin minimize into the dock by itself and sometimes closes
It is an oddity, but I don't think you have any security issues. Especially if you have a router and you haven't disabled NAT. (Network Address Translation- A security feature within most routers on the market.)

If you feel your system is vulnerable to the INTERNET, then starting the built in firewall will make your system 99.9% invisible to the outside world. To start the firewall open a terminal and enter ```
sudo ufw enable
``` to turn it off simply enter ```
sudo ufw disable
```If you would like GUI application for setting the firewall, then you can go in your menu to Ubuntu Software Center and search for and install GUFW. Once installed you can find and open it through System> Administration> GUFW in the menus.

---

### Post by linux18 on 2010-08-13
it's strange, but your not getting hacked. It could be on an internal timer.

---

### Post by rookcifer on 2010-08-13
> **binarylife said:**
> I heard before I've installed ubuntu , that linux system can't be hacked, so is that possible to hack my computer , because I noticed that someone is hacking my ubuntu ? 
thanks !

You were told wrong.  Linux systems aren't uncrackable.  What they are is more resistant to malware, which means as a desktop user you should be pretty safe from most security issues provided you keep up to date and are careful to only install software from the repositories.

---

### Post by HPD2 on 2010-08-14
Try running pidgin from the terminal, that should tell you whats up. Doesn't sound like some one hacking into your machine.

As rookcifer stated Ubuntu, Linux is not uncrackable. All operating systems have there exploitable flaws. But because of how Linux handles administrator access, normal access is unprivileged meaning your not the administrator, most security threats (Malware) are mitigated.

---

