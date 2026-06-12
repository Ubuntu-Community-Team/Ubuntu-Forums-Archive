---
title: "installer tutorials"
date: 2009-09-13
forum: The Cafe
---

### Post by chris200x9 on 2009-09-13
I was wondering if anmyone could point me in the direction of any programming tutorials for writing a linux installer. I do not care how basic of an installer the tutorial outlines. Thank you.

---

### Post by &#32 Greg on 2009-09-13
What do you mean by an installer? A .deb? A shell script to compile from source? A way of installing a distro?

---

### Post by chris200x9 on 2009-09-13
> **  Greg said:**
> What do you mean by an installer? A .deb? A shell script to compile from source? A way of installing a distro?

for a distro

---

### Post by &#32 Greg on 2009-09-13
For that, I'd say your best bet is probably looking at Linux from Scratch, and also taking a look at the source code of programs like remastersys to see how they're doing it, as well as how the system is made that you'd need to be putting together.

---

### Post by chris200x9 on 2009-09-13
> **  Greg said:**
> For that, I'd say your best bet is probably looking at Linux from Scratch, and also taking a look at the source code of programs like remastersys to see how they're doing it, as well as how the system is made that you'd need to be putting together.

thanks! :)

---

### Post by Frak on 2009-09-13
Take a look at Anaconda([http://fedoraproject.org/wiki/Anaconda](http://fedoraproject.org/wiki/Anaconda)). Somebody wanted to post that here, but they don't have an account, and hey, I'm just the kind of guy to do it.

> Posted by **The Dude**
A lot of ugly Python in it, but, it's a pretty sound installer and would certainly serve as a good starting point towards something else.

Hope it helps!

---

### Post by mdmarmer on 2009-09-14
I looked at this -- actually the installer is probably the most difficult part of building a new distro.

Remastersys is fairly simple and general purpose. It's available for both Debian and Ubuntu. Anaconda is more complex and set up for Fedora/RedHat type distro. There are installers for caos and sidux.  I couldn't find the source code for caos, and I have not explored sidux.  The BOSS distribution is tailored for Indian users -- they have ported Anaconda to Debian for use with BOSS. I didn't explore that too far.  There is the Mepis installer and the Acritox installer (used for kanotix).

Source code for Mepis installer [ftp://ftp.mepis.com/mepis/pool/main/m/](ftp://ftp.mepis.com/mepis/pool/main/m/)


Acritox installer  [http://kanotix.com/files/excalibur/kanotix/contrib/acritoxinstaller/](http://kanotix.com/files/excalibur/kanotix/contrib/acritoxinstaller/)

Look at Remastersys first.  If you want an Ubuntu based howto that's fairly easy to understand look here CAPINK's Transforming your Installation Manually into a Live DVD/CD Howto   
[http://www.geekconnection.org/remastersys/capink.html](http://www.geekconnection.org/remastersys/capink.html)

Remastersys has forum -- u can ask questions there.

Mike

---

