---
title: "How to install systemd in raring?"
date: 2013-02-26
forum: Ubuntu Development Version
---

### Post by Mr.JJ on 2013-02-26
How can I install systemd in ubuntu raring?

I saw this page here: [https://wiki.ubuntu.com/systemd](https://wiki.ubuntu.com/systemd) 
which is quite old (2010) and is not updated. I saw couple of other blogs/tutorials which says they can only be used in specific ubuntu versions.

Any help is appreciated, thanks!!

By the way, I heard wonderful improvements in bootup with systemd (reduced as much as upto 50%).

---

### Post by dino99 on 2013-02-26
out of ubuntu radar ;)

---

### Post by Stinger on 2013-02-26
> **dino99 said:**
> out of ubuntu radar ;)

How do I install 'ubuntu radar'? :biggrin:

---

### Post by dext on 2013-02-26
hopefully Mark Shuttleworth dont see this thread, he might blow a Gasket :p 

but isnt there any tutorials updated ones on the systemd website or in maybe Archlinux forum or wiki? or what about the Debian wesite wiki as they have systemd in 7.0, should have some tutorials over there

---

### Post by grahammechanical on 2013-02-26
last edited 2012-09-10 21:38:04 by dileks)

Not so old.

---

### Post by castrojo on 2013-02-26
> **Mr.JJ said:**
> How can I install systemd in ubuntu raring?

Ubuntu uses Upstart, not systemd:

Old, but still applies: [http://undacuvabrutha.wordpress.com/2011/04/29/why-ubuntu-should-continue-with-upstart-for-11-10/](http://undacuvabrutha.wordpress.com/2011/04/29/why-ubuntu-should-continue-with-upstart-for-11-10/)

Though some parts are used in Raring: 

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-ubuntu-system-services](https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-ubuntu-system-services)

Though if someone were to do the work it could probably be done, just not by the core team. 

> By the way, I heard wonderful improvements in bootup with systemd (reduced as much as up to 50%).

Upstart is pretty optimized for boot as well, I doubt you'd see such a drastic impact across the board, (I'd love to see some numbers to be proven wrong though!)

---

### Post by jbicha on 2013-02-26
There's now a systemd-services package which I believe the Foundations Team is working on to replace ubuntu-system-services. The systemd-services didn't work right for me (with gnome-control-center) when I tried. Until Ubuntu switches over, if you want to get things back to the Ubuntu default, I think you'll need to do a reinstall of ubuntu-system-service after uninstalling systemd-services.

[https://launchpad.net/ubuntu/+source/systemd](https://launchpad.net/ubuntu/+source/systemd)

---

### Post by Mr.JJ on 2013-02-26
> **castrojo said:**
> Ubuntu uses Upstart, not systemd:
 Old, but still applies: [http://undacuvabrutha.wordpress.com/2011/04/29/why-ubuntu-should-continue-with-upstart-for-11-10/](http://undacuvabrutha.wordpress.com/2011/04/29/why-ubuntu-should-continue-with-upstart-for-11-10/)

If ubuntu was using systemd, there won't be any point in this thread :smile:
That guy basically tells since an LTS is coming soon ubuntu should wait and after 12.04 LTS, move to systemd could be discussed. This is the second release after 12.04, so I don't know how relevant that is.
Nyways I am more interested in the 'how's than the 'why's.

> **castrojo said:**
> Upstart is pretty optimized for boot as well, I doubt you'd see such a drastic impact across the board, (I'd love to see some numbers to be proven wrong though!)
This person says his boot went from 9 to 5 seconds (in 12.04): [how-to-use-systemd-in-ubuntu-1204]("http://nomoreterminals.blogspot.in/2012/05/how-to-use-systemd-in-ubuntu-1204.html")

---

### Post by Mr.JJ on 2013-02-26
> **jbicha said:**
> There's now a systemd-services package .........Until Ubuntu switches over......
If I understand correctly, for the time being, ubuntu-system-service will work with systemd, right?

Lubuntu ppa has systemd but it comes with all other apps etc. and Martin Pitt ppa is not updated for almost an year. What next??

Does the instructions on the ubuntu wiki valid still (though it talks only about 12.04)? Anyone has any idea?

---

### Post by dino99 on 2013-02-26
you can already write your whish list for SS (aka 13.10) to be ready for the next UDS  ):P

---

### Post by Starks on 2013-02-26
Biggest problem with systemd is that you can't cancel an fsck

---

### Post by dext on 2013-02-26
> **Starks said:**
> Biggest problem with systemd is that you can't cancel an fsck

why would you wanna cancel a FSCK in the first place?

---

### Post by arpanaut on 2013-02-26
Sometimes when I am in a hurry to get my system up I will cancel out of fsck.
Most of the time, not a problem.

---

### Post by EgoGratis on 2013-02-26
The problem i see here is changing this needs somebody that knows what he is doing and what to do when it will brake and how to "fine tune" and i doubt OP is willing to educate himself for this task? 

Probably the point is to test if boot time will really be 50% less time compared to default Ubuntu? To test this the easiest solution would be to test one or two Linux distributions that uses systemd and measure boot time on the same hardware you use Ubuntu on and problem solved because probably you will not achieve 50% less boot time. ;)

---

### Post by jbicha on 2013-02-26
> **Mr.JJ said:**
> 
Lubuntu ppa has systemd but it comes with all other apps etc.


Excuse me…which PPA?

---

### Post by Mr.JJ on 2013-02-27
> **jbicha said:**
> Excuse me…which PPA?

This one: [https://launchpad.net/~mati75/+archive/lubuntu](https://launchpad.net/~mati75/+archive/lubuntu)

Isn't that the official version?

---

