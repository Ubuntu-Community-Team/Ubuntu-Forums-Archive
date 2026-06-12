---
title: "Can't access encrypted /home"
date: 2009-06-29
forum: Security
---

### Post by makksjuh on 2009-06-29
.

---

### Post by bodhi.zazen on 2009-06-29
Is this on a live CD or after re-booting the system ?

---

### Post by makksjuh on 2009-06-30
.

---

### Post by bodhi.zazen on 2009-06-30
Is your home directory encrypted with LUKS, or my guess is ecryptfs ?

If you pulled your data and are re-installing I guess it does not matter, but I hope your understand the difference between LUKS and ecryptfs.

---

### Post by makksjuh on 2009-06-30
.

---

### Post by HermanAB on 2009-07-01
Howdy,

If you are using encryption, then it is extremely important to backup your data to another encrypted disk.  A single bit error can cause the loss of all your data.

See this for some wizards that you can use to make encrypted USB disks:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

