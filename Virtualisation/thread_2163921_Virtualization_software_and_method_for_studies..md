---
title: "Virtualization software and method for studies."
date: 2013-07-20
forum: Virtualisation
---

### Post by akshay.sulakhe on 2013-07-20
Hey guys, I hope you are doing fine today. I am sorry the subject for my thread doesn't mention much, i was confused as to what exactly i should write. Anyways, I am planning to give RHCE exam in a few months. As i will be playing around the Red Hat system for a longer time, resulting in breakages and all, i thought of using virtualization. Also, with virtualization, once i know i have the base system ready, i would like to copy the image file of the guest OS, so whenever there is a breakage, i can just copy the old image and voila! i can start my work again. I understand this is plausible, i just need to know which virtualization tool would go easy to do all this and which supports auto-detection of images in its folder, something more automated so i don't need to spend more time in messing around with the virtualization software itself. Thank you for your time guys. Have a nice day ahead. :-)

---

### Post by HermanAB on 2013-07-20
Yes, that is exactly how a lot of development and testing is done.  I am mostly working on a Mac, but I usually have VMs running of two other things.

Install Virtualbox, make a VM with a size of about 30GB, install RedHat, install Guest Additions, then quit and make a tar archive of the whole VM directory (or use Virtualbox itself to 'export' a copy).  From then on, when you need a fresh version, just untar (or import) again and you are back to a virgin RedHat.

---

### Post by akshay.sulakhe on 2013-07-20
Thanks @HermanAB That helps... :-)

---

### Post by oldos2er on 2013-07-20
Moved to Virtualisation.

---

