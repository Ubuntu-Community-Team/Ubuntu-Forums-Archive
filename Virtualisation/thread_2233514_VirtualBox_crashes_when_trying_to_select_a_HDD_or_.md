---
title: "VirtualBox crashes when trying to select a HDD or CD-DVD (ISO or otherwise)"
date: 2014-07-09
forum: Virtualisation
---

### Post by slooksterpsv on 2014-07-09
When trying to select a CD/DVD to boot from or even change the hard drive on a VM, VirtualBox crashes. I've installed 2 different versions, same thing. I'm not sure where the error is, it doesn't give me an error at all.

This is very frustrating.

---

### Post by hbutt875 on 2014-07-09
Uninstall virtual box by typing in Terminal.

sudo apt-get autoremove virtualbox

Then go to ubuntu software center and install virtualbox.If does not work please reply.

---

### Post by slooksterpsv on 2014-07-09
I did, I figured it out, I had PPA's for the LXQT and a few other PPAs that were using dev versions of Qt which was causing the issue. I used ppa-purge to remove those PPAs and it's working now.

---

### Post by hbutt875 on 2014-07-09
Be happy friend.

---

