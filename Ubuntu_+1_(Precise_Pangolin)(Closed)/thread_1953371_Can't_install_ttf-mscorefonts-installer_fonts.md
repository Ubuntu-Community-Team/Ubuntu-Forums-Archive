---
title: "Can't install ttf-mscorefonts-installer fonts"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by napsy on 2012-04-06
Hello. I have troubles installing microsoft fonts using ttf-mscorefonts-installer ... it hangs when trying to download the fonts. No URL works just hangs in 'HTTP request sent, waiting for response..."

Any ideas?

---

### Post by Linuxisfast on 2012-04-06
Installed fine on my Ubuntu 12.04 beta 2 on a Quad core PC.

---

### Post by dino99 on 2012-04-06
the package fonts-liberation contains free variants of the Times,
Arial and Courier fonts. It's better to use those instead unless you
specifically need one of the other fonts from this package.

---

### Post by napsy on 2012-04-06
I need pixel-perfect fonts that are rendered well in 1-bit displays (black-white). Arial was displayed very good on ubuntu 10.04 but now I upgraded to 12.04 and arial with bold weight is really ugly.

I got arial TTF file from a page but want to test the font from the official package.

---

### Post by Abandon on 2012-04-06
Have you tried to switch to another (download) server? Using the Main Server gives the best results.

---

### Post by jbicha on 2012-04-06
I don't think encouraging people to use the main server is a very good idea. Ubuntu has dozens of mirrors around the world to spread out the load.

---

### Post by kurt18947 on 2012-04-06
Just a thought -- did you see and agree to the license?  They won't install without that.  I suspect that to have *any* chance of having .doc & docx files import and export properly,  I'd need MS fonts installed.

---

### Post by Abandon on 2012-04-06
> **jbicha said:**
> I don't think encouraging people to use the main server is a very good idea. Ubuntu has dozens of mirrors around the world to spread out the load.

Ok...change to another mirror instead. :p

---

### Post by napsy on 2012-04-06
If I killall -9 wget while apt-get is running, another server is chosen but still the same. Yes I've agreed to the license.

---

### Post by Abandon on 2012-04-06
Try downloading from here and see if that one works with sudo dpkg -i ttf-mscorefonts-installer_3.3ubuntu4_all.deb

[http://packages.ubuntu.com/oneiric/ttf-mscorefonts-installer](http://packages.ubuntu.com/oneiric/ttf-mscorefonts-installer)

---

### Post by napsy on 2012-04-06
Doesn't work either. There's probably some problem with my ISP.

---

