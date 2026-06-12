---
title: "extras request: Adobe Reader 7.0"
date: 2005-04-14
forum: Ubuntu Backports
---

### Post by thepoch on 2005-04-14
Adobe Reader 7.0. They say it's in marillat, but I just don't want to add marillat and have it conflict with Ubuntu Backports.  :grin:

---

### Post by jdong on 2005-04-14
Ok. Out of curiousity, what kind of License will I be dealing with? ;)

---

### Post by thepoch on 2005-04-14
OK, after some searching, I've found the license at:

[http://www.adobe.com/products/acrobat/acrreula.html](http://www.adobe.com/products/acrobat/acrreula.html)

And for redistribution, you have to fill out a form and accept a distribution version of the license here:

[http://www.adobe.com/products/acrobat/acrrdistribute.html](http://www.adobe.com/products/acrobat/acrrdistribute.html)

after a couple of blinking on the license for distribution, I'm surrounded by somewhat redundant lawyer speak. But it seems you really have to ask for permission before redistribution. And the form doesn't have a "why redistributing?" field to answer this question. But if you submit, they'll email you back, or so it seems.

I guess I should retract my request then. It seems too much trouble for you and doesn't seem worth it. Argh.  :neutral:

---

### Post by oracledarren on 2005-04-14
[QUOTE=jdong]Ok. Out of curiousity, what kind of License will I be dealing with? ;)[/QUOTE]

I dont know about the re-dist licence but they certainly released a linux version of the reader today/yesterday for free download [http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)

---

### Post by jdong on 2005-04-14
Ok, the EULA has a pretty strong clause about repackaging Acrobat Reader in a different format AND about writing a "new installer" for Acrobat Reader. This prevents:

1) Uploading an alien'ed DEB from their RPM
2) Debianizing their tar.gz binaries


It doesn't prevent a download-fetcher mechanism like how Flashplayer/Msttcorefonts install. I've gotta learn how to make those kind of packages. If anyone has good howto's, etc, please enlighten me :)

---

### Post by techn9ne on 2005-04-14
Fortunatley installling it is easy as :

tar zxvf AdobeReader.tar.gz
sudo ./INSTALLER

---

### Post by poofyhairguy on 2005-05-06
Here is the Sarge deb.

Install at ones own perl.

[ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/acroread_7.0-0sarge0.9_i386.deb](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/acroread_7.0-0sarge0.9_i386.deb)

---

### Post by Bob D. on 2005-05-06
[QUOTE=poofyhairguy]Here is the Sarge deb.

Install at ones own perl.

[ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/acroread_7.0-0sarge0.9_i386.deb]("ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/acroread_7.0-0sarge0.9_i386.deb")[/QUOTE] I installed the Sarge .deb from Marillat the other day along with the mozilla-acroread plugin. Works the treat! No problems on Hoary at all.

Bob

---

