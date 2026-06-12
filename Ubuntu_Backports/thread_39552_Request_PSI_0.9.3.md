---
title: "Request: PSI 0.9.3"
date: 2005-06-05
forum: Ubuntu Backports
---

### Post by buellman on 2005-06-05
hi!

is it possible to backport PSI 0.9.3? <-- jabber-client

thanks. buellman

---

### Post by jdong on 2005-06-08
Sure.

Sorry I overlooked this for so long! :)

---

### Post by buellman on 2005-06-08
[QUOTE=jdong]Sure.

Sorry I overlooked this for so long! :)[/QUOTE]

great and no problem :-)

thanks. buellman

---

### Post by jdong on 2005-06-08
[code]
tdlg.cpp:84: undefined reference to `QCA::Cert::notAfter() const'
.obj/sslcertdlg.o(.text+0xe5e):/home/jdong/ubp-compile-temp/psi-0.9.3/src/sslcertdlg.cpp:85: undefined reference to `QCA::Cert::notBefore() const'
.obj/sslcertdlg.o(.text+0xf0e):/home/jdong/ubp-compile-temp/psi-0.9.3/src/sslcertdlg.cpp:87: undefined reference to `QCA::Cert::notAfter() const'
.obj/sslcertdlg.o(.text+0xfbb):/home/jdong/ubp-compile-temp/psi-0.9.3/src/sslcertdlg.cpp:90: undefined reference to `QCA::Cert::serialNumber() const'
.obj/sslcertdlg.o(.text+0x1048):/home/jdong/ubp-compile-temp/psi-0.9.3/src/sslcertdlg.cpp:94: undefined reference to `QCA::Cert::subject() const'
.obj/sslcertdlg.o(.text+0x1131):/home/jdong/ubp-compile-temp/psi-0.9.3/src/sslcertdlg.cpp:95: undefined reference to `QCA::Cert::issuer() const'
collect2: ld returned 1 exit status
make[2]: *** [psi] Error 1
make[2]: Leaving directory `/home/jdong/ubp-compile-temp/psi-0.9.3/src'
make[1]: *** [sub-src] Error 2
make[1]: Leaving directory `/home/jdong/ubp-compile-temp/psi-0.9.3'
make: *** [build-stamp] Error 2
Traceback (most recent call last):
  File "/usr/local/bin/ubp-build.py", line 270, in ?
    build()
  File "/usr/local/bin/ubp-build.py", line 167, in build
    raise Exception("Build command FAILED")
Exception: Build command FAILED
root@delta:~/ubp#
[/quote]

Sorry, it doesn't build against libqca... :(

---

### Post by buellman on 2005-06-08
[QUOTE=jdong]
Sorry, it doesn't build against libqca... :([/QUOTE]

hmmm... to bad :-/ but thanks for trying it :-)

greets. buellman

---

### Post by tommi on 2005-07-03
can u please test it again ? it would be so great (Breezy has 0.9.3-1) 0.9.3 is 6 months old and not in hoary :(

---

### Post by AnGeLiX on 2005-07-03
[QUOTE=tommi]can u please test it again ? it would be so great (Breezy has 0.9.3-1) 0.9.3 is 6 months old and not in hoary :([/QUOTE]
 I have made a Guide for compiling Psi for Ubuntu. Is very simple and i am currently using V 0.10-CVS . The guide => [http://psi.affinix.com/forums/index.php?act=ST&f=1&t=2633&hl=ubuntu](http://psi.affinix.com/forums/index.php?act=ST&f=1&t=2633&hl=ubuntu)

**jdong** the reason that you can't compile Psi is (i think) that you are using an old version of QCA that it is on the Ubuntu Backports.

---

### Post by TheRealCryss on 2005-07-03
Hi!


When will psi 0.9.3 officially be included in hoary?
What about ssl support? In 0.9.2 it doesen't work. It seems it is compiled without ssl support. :-(

The guide is nice and tnx for it, but I have installed ubuntu over my gentoo because I don't want to compile things by myself anymore. And 0.9.3 is out a while.

Chris

---

### Post by tommi on 2005-07-03
i running 0.9.2 and ssl works. but i dont want install all the -dev packages and sources. then i need extra packages for compile. the directories doesnt equal (usr/bin/ and usr/X11/bin) ...  i will wait for a backport (maybee from the cvs ?, at my last install i compiled from cvs too. but i wont do it again.)

---

### Post by elarochejoubert on 2005-08-03
Hi everybody

I tried this and it worked   \\:D/ :

I've taken debian psi 0.9.3 stable package!

file used (from debian stable  here : [http://ftp.fr.debian.org/debian/pool/main):](http://ftp.fr.debian.org/debian/pool/main):)
- psi_0.9.3-1_i386.deb
- psi-translations_1.8_all.deb
- libqca1_1.0-6_i386.deb (for dependencies)

and finally 'sudo dpkg -i' on each of them (libqca1 first)

hope this help someone.

---

### Post by stoeptegel on 2005-11-05
0.10 is upcoming in the next weeks: [http://psi-im.org/forum/thread/3302](http://psi-im.org/forum/thread/3302)
If there's room in the reposorities of breezy please do so :)

---

### Post by taavi on 2006-01-14
Should made a new topic, but since it mentioned here. 

0.10 is out... 0.10.1 should follow shortly with new graphics, but still... 

[http://www.psi-im.org](http://www.psi-im.org)

Still. I made a .deb with this 400 MHz Celeron. It took 2 hours, but here it is: [psi-0.10_0.10-1_i386.deb](http://jabber.ee/~taavi/asjad/psi-0.10_0.10-1_i386.deb) .

Check it out and let me know, if it works for you... Nice evening.

---

### Post by stoeptegel on 2006-01-15
Thank you taavi :)
I tried to compile myself, but i had an (for me)unresolvable error, so your package came in handy. I only miss the sounds though, but hey it works for me.

---

### Post by Pointwood on 2006-02-14
taavi: That .deb so far works great here, thanks!

---

