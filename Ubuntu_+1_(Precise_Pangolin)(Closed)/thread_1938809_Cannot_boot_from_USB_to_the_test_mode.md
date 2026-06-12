---
title: "Cannot boot from USB to the test mode?"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hakermania on 2012-03-10
All other ubuntu releases had a test mode which allows you to run Ubuntu in GUI mode loaded in memory, through the live USB.

This one doesn't provide me with such an option.

The only option I get is 'Install Ubuntu' and 3 others that are for fixing the system.

Also, the 'Install Ubuntu' begins the installation of Ubuntu in non-GUI (terminal-like-installation).

Am I missing something?

---

### Post by disabled20191128 on 2012-03-10
[LEFT]hi,

i think that you are running the alternate installation cd
[/LEFT]

---

### Post by disabled20191128 on 2012-03-10
there are 2 types of cds:
the live cd version that allows you to test, install and even fix a system 
and the alternate version which does the same things (except testing the system)

---

### Post by hakermania on 2012-03-10
Thanks Dennisgre, that seems about right :)

I got it now :)

---

### Post by disabled20191128 on 2012-03-10
You are welcome

---

### Post by hakermania on 2012-03-10
Actually, it's not OK, I just tested it again. Yes, I had downloaded the alternate installation iso image, but even with this one: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) (first link: PC (Intel x86) desktop CD) I get the same options.

There's nowhere an option for testing...

---

### Post by disabled20191128 on 2012-03-10
Well that's weird maybe live cd isn't yet supported in precise pangolin (because it's a beta)

---

### Post by mc4man on 2012-03-10
Asumming that image is a live image (should be, haven't downloaded, use the dailies here), if you are using the Startup Disk Creator then make sure you delete or move your previous image (the alt. one

The Startup Disk Creator has this poor habit of sometimes  using a prior image even if your tell it differently

---

### Post by cariboo on 2012-03-10
I always use the erase drive option first before creating a new usb drive using the Startup Disk Creator.

Maybe I'm reading your post wrong, but tha alternative iso is text based only, you have to use :

[http://releases.ubuntu.com/precise/ubuntu-12.04-beta1-desktop-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04-beta1-desktop-amd64.iso)

or

[http://releases.ubuntu.com/precise/ubuntu-12.04-beta1-desktop-i386.iso](http://releases.ubuntu.com/precise/ubuntu-12.04-beta1-desktop-i386.iso)

in order to be able to boot to a live desktop.

---

