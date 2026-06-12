---
title: "Migrate existing windows install to VirtualBox?"
date: 2008-08-06
forum: Virtualisation
---

### Post by helwitch on 2008-08-06
I have an existing windows installation on my laptop, but mainly run kubuntu 8.04. I use windows pretty much only for MS Money. I want to create a virtualbox image of the existing windows install. I read [http://virtualbox.org/wiki/Migrate_Windows](http://virtualbox.org/wiki/Migrate_Windows), but am still confused as to what to do. How do I make the existing install into an image? Do I just make it an .iso image?

---

### Post by bodhi.zazen on 2008-08-06
It is not easy, not for the feint of heart, and not guaranteed to work ...

[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)

---

### Post by BTMark on 2008-08-06
I *just* did this the other day following that exact guide posted above.

It's fairly simple if you just follow the instructions, but the one issue I had with the guide was setting up my Virtual Machine. When he gets to step 11, using his guide, he tells you to choose "Use individual partitions", when I used that, I kept getting GRUB error 14. I went back and blindly chose "Use entire disk", and everything booted as usual. So, if you happen to get GRUB error 14, that may be your issue.


I'll monitor the thread, it took me roughly 12 hours of banging my head off the desk to get it right, so if you need any assistance.

---

