---
title: "Installing Hydra"
date: 2008-09-23
forum: Security
---

### Post by oneadvent on 2008-09-23
Alright thats it. Is there a deb file for installing xhydra and hydra?

Its just about crazy hard to meet its requirements. 

Thanks anyone!

---

### Post by chronos00 on 2008-09-23
I am having trouble with this installation too. I also started a thread: 
[http://ubuntuforums.org/showthread.php?t=927436]("http://ubuntuforums.org/showthread.php?t=927436")

The only important dependency is libssh-0.11 I guess.
You can download it here:
[http://0xbadc0de.be/libssh/libssh-0.11.tgz]("http://0xbadc0de.be/libssh/libssh-0.11.tgz")

Just extract, ./configure; make; sudo make install

After this, do the same with THC-Hydra's code.
You should get the command line executable.

I got it to recognize lissh, but compilation of hydra throws some weird errors (see the thread I started)

Let me know if this worked for you!

---

### Post by XIIIth on 2009-12-19
I had the same issues while trying to install hydra.
This is what finally worked for me and how!

[http://forum.bec0de.com/linux-unix-f53-installing-hydra-and-hydragtk-xhydra-from-backtrack4-packages-on-ubuntu-t108.html](http://forum.bec0de.com/linux-unix-f53-installing-hydra-and-hydragtk-xhydra-from-backtrack4-packages-on-ubuntu-t108.html)

Hope I helped!..

---

### Post by chronos00 on 2009-12-19
> **XIIIth said:**
> I had the same issues while trying to install hydra.
This is what finally worked for me and how!

[http://forum.bec0de.com/linux-unix-f53-installing-hydra-and-hydragtk-xhydra-from-backtrack4-packages-on-ubuntu-t108.html](http://forum.bec0de.com/linux-unix-f53-installing-hydra-and-hydragtk-xhydra-from-backtrack4-packages-on-ubuntu-t108.html)


It seems those repos are not working any more... a pitty.

Anyone had any success in compiling the source code?

---

### Post by JT9161 on 2009-12-20
Yes, using (for non-x) [http://tuxtraining.com/2009/02/13/howto-install-thc-hydra-54-in-ubuntu-intrepid-ibex](http://tuxtraining.com/2009/02/13/howto-install-thc-hydra-54-in-ubuntu-intrepid-ibex) (Far as I know works on Jaunty, would be a little surprised if it did)

For xhydra I used, at the bottom of the page, third comment, by 'marc', [http://www.hacktoolrepository.com/tool.pl?tid=37](http://www.hacktoolrepository.com/tool.pl?tid=37)

---

### Post by XIIIth on 2009-12-27
> **chronos00 said:**
> It seems those repos are not working any more... a pitty.

Anyone had any success in compiling the source code?

I had to reinstall Ubuntu. (karmic) ,
**Installed hydra again using the link i posted above**. The "sudo apt-get update" shows an err , but the install works...the terminal command for bringing the interface up is  "xhydra".
I am trying to figure out why the error shows up when the update happens.

----xiii.

---

### Post by WittFan on 2010-01-22
> **JT9161 said:**
> Yes, using (for non-x) [http://tuxtraining.com/2009/02/13/howto-install-thc-hydra-54-in-ubuntu-intrepid-ibex](http://tuxtraining.com/2009/02/13/howto-install-thc-hydra-54-in-ubuntu-intrepid-ibex) (Far as I know works on Jaunty, would be a little surprised if it did)

For xhydra I used, at the bottom of the page, third comment, by 'marc', [http://www.hacktoolrepository.com/tool.pl?tid=37](http://www.hacktoolrepository.com/tool.pl?tid=37)

This is exactly what I needed! Thanks for sharing.

---

### Post by zukario on 2010-01-22
> **JT9161 said:**
> Yes, using (for non-x) [http://tuxtraining.com/2009/02/13/howto-install-thc-hydra-54-in-ubuntu-intrepid-ibex](http://tuxtraining.com/2009/02/13/howto-install-thc-hydra-54-in-ubuntu-intrepid-ibex) (Far as I know works on Jaunty, would be a little surprised if it did)

For xhydra I used, at the bottom of the page, third comment, by 'marc', [http://www.hacktoolrepository.com/tool.pl?tid=37](http://www.hacktoolrepository.com/tool.pl?tid=37)

I hope this works in installing hydra.

---

