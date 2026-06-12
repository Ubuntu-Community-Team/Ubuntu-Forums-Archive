---
title: "adding Windows"
date: 2016-03-04
forum: Virtualisation
---

### Post by Lloydb39 on 2016-03-04
I've tried to search this but didn't find it. I am running Ubuntu 14.04 on a homebuilt 64-bit AMD machine with 1 TB hard drive and 8 gig RAM. I need to run a couple of Windows programs and don't want to mess with WINE so I'd like to use Virtualbox. I have the deb file downloaded. Is there a step by step for dummies on how to get it installed and then how to install and run Windows with it? Thanks.

---

### Post by Bucky Ball on 2016-03-04
You don't need a .deb file. Virtualbox is in the Software Centre. Advise you use that one. ;)

Install virtualbox, you will then need a Win ISO or DVD or USB. [This link should help]("https://www.virtualbox.org/manual/UserManual.html") with the rest. There is a ton of info online about how to create virtual machines.

---

### Post by howefield on 2016-03-04
Caveat being that it is Virtualbox version 4.3 in the Trusty repositories versus 5.0.14 on later Ubuntu versions and the Virtualbox website.

That's not to say that 4.3 won't work, just a bit behind the times.

---

### Post by Lloydb39 on 2016-03-04
That's the one I have. How do I install it?

---

### Post by QIII on 2016-03-04
The most sure-fire way to do this is to go to virtualbox.org's page [here]("https://www.virtualbox.org/wiki/Linux_Downloads") and add their repo to your sources list.  That will make sure you get regular updates.

Go to the section labeled "**Debian-based Linux distributions**" and add the repo as instructed, then follow the installation instructions.

---

