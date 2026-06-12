---
title: "Truecrypt to encrypt /home. Possible?"
date: 2010-10-29
forum: Security
---

### Post by newboyo on 2010-10-29
Hi all,

I use karmic 64 bit and have installed / and ~ on separate partitions (sda3 and sda5). I'd like to move ~ to an encrypted partition. To do this, I plan to -
1. backup ~ to an external HDD.
2. use truecrypt to encrypt sda5 (using the create a volume/partition option)
3. restore ~ to the (now) encrypted sda5.

Just checking whether or not -
a. the plan is feasible/workable
b. are there any issues that i need guard against
c. will the settings/configurations be restored to the way they were before the exercise is carried out.

Thanks vm



New

---

### Post by HermanAB on 2010-11-08
Yup, you are on the right track, though I would not use TrueCrypt it is well known and generally trusted.  Even Bruce Schneier once admitted to using it.

One problem that you are going to run into is getting the TrueCrypt volume to automount at startup, but I cannot help with that, since I don't know TrueCrypt - only tried it once or twice on a USB stick.

---

