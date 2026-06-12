---
title: "which video driver is better? FGLRX Or X.org"
date: 2014-01-15
forum: Ubuntu, Linux and OS Chat
---

### Post by chkneater on 2014-01-15
I noticed when installing 13.10 I was confronted with the question of whether to use the x.org driver or the proprietary fglrx driver.  I went with the default x.org, but I'd like to know is someone knows the difference and/or advantage of one over the other??

---

### Post by craig10x on 2014-01-16
I believe it's usually preferable to use the open source version as long as it works well for you...usually less problems that way...i am sure others will post with their experiences...

---

### Post by QIII on 2014-01-16
If the open source driver meets your needs, use it.

If you have a laptop, you may run into heat problems with it, though.

What sort of machine are you running and what are the hardware specs?  What do you plan on using the machine for?

---

### Post by chkneater on 2014-01-16
It was formerly a compaq, but now it's an ASUS AMD64 board with 256GCPU and around 3G RAM.  2Ghz or so processor.  I haven't noticed any probs with the x.org driver as of yet, but I know you can't use the AMDCCCLE controls as far as I know without the fglrx driver.

I'm just wondering if it's worth it to have AMD catalyst controls and switch to fglrx driver...  I've used the fglrx driver before.  This is an AMD Radeon 5450HD btw.

---

### Post by QIII on 2014-01-16
The driver will work with the HD 5450.

To make things easier I would suggest just installing it from the repo for now.  

```
 sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

```
sudo amdconfig --initial
```

Reboot.

---

### Post by chkneater on 2014-01-16
thanks a lot Qlll, that helped a bunch... I had been using 'aticonfig --initial -f' which was SORT of close but the amdconfig worked perfectly, checked rendering and driver and even have the Catalyst Control Center now.  Thanks again!!

---

