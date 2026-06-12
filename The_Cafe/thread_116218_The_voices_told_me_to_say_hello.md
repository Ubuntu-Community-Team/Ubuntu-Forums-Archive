---
title: "The voices told me to say hello"
date: 2006-01-12
forum: The Cafe
---

### Post by YoungJules on 2006-01-12
So here I am, hopefully making my first post today by saying hello to the Community Chat forum :-)

I'm a programmer of many year's experience, having started in the wonderful world of Honeywell and Cobol 68.  I know something of 'nix, having had to use it now and then for my work but have been mostly working on Windoze as mandated by our corporate bean-counters and white-hatters...

I'm currently using my Ubuntu 5.10 distro on a headless dual-cpu (don't get too excited, they're only 400MHz PIIs!) machine.  I use the machine for developing home-automation solutions using the K8055 USB-interface board and a home-brewed parallel-port interface (so far only at the prototyping stage).

I'd seen the Ubuntu forums before, but having answered yet another of my dumb questions (how to use Synaptic through our company firewall), I thought it was time I bit the bullet and actually joined up.

I'm sure I will ask some VERY dumb questions now and then but am willing to learn and share what I know.

Thanks for a great forum :cool:

---

### Post by stimpack on 2006-01-12
Welcome to Ubuntu!. We all ask silly questions, but the day you first answer somebody else's question is a great day indeed.

---

### Post by earobinson on 2006-01-12
Welcome

---

### Post by oliverb on 2006-08-18
Hi, I was looking for info on the k8055 board as I downloaded a linux "driver" for it but I cannot get it to compile, as there seems to be a problem with usb.h. Are you using the board under linux? If so who's driver are you using?

---

### Post by jISh on 2006-08-18
Welcome to the forums.

---

### Post by hentaidan on 2006-09-14
> **oliverb said:**
> Hi, I was looking for info on the k8055 board as I downloaded a linux "driver" for it but I cannot get it to compile, as there seems to be a problem with usb.h. Are you using the board under linux? If so who's driver are you using?

(I assume you are trying to use the one from [http://linuxk8055.free.fr/](http://linuxk8055.free.fr/))

In case you are still having trouble..:)

> 1) change line 31 in src/k8055.cpp to #include <usb.h>
2) change line 96 of src/Makefile to LIBS = -lusb

---

### Post by DoctorMO on 2006-09-14
hentaidan do you know how to produce a patch?

*** See Dumb questions all the time ***

---

### Post by Autotropics on 2006-09-20
Hi 

I have just joined the forum.
I have a reasonable amount of Linux/Windows knowledge and also a strong interest in automation ( I have a number of private greenhouses that I want to automate, monitor and remotely control) as well as other things

I intend using a linux distro (Ubuntu) to drive my automation projects due to the stability and small footprint of Linux as opposed to doing this in a windows environment with all the issues and cost associated with this

I noted that has been a few posts regarding the use of the K8055 USB-interface board with Linux and I would love to get in touch with you guys to learn from what you have achieved so far and to hopefully exchange ideas, etc...

Initially I looked at using PIC circuitry for overall control but the complexity of cost, effort and limitations as opposed to using a standard PC with linux, K8055 USB-interface board , and other discrete modules made up my mind to go for the PC linux solution as a more practical way forward. I still plan to use PIC circuitry/code to develop discreet modules that I cannot easily/cheaply source and/or to supplement and interface the components for which there are no easy work arounds.

Hopefully there would be sufficient interest in this to devote a whole thread to this in the forums, but I thought I would just dip my toes in the water in this forum thread first

I noted that YoungJules and Hentaidan had content content in these posts relating to K8055 USB-interface board that I would like to discuss with them, so hopefully you guys are still around

I look forward to hearing from you

---

### Post by hentaidan on 2006-09-22
> **DoctorMO said:**
> hentaidan do you know how to produce a patch?

*** See Dumb questions all the time ***

Not really :) What for?

I *believe* I am using the driver from [http://libk8055.sourceforge.net/](http://libk8055.sourceforge.net/) now, and that seems to be working ok, (although I had to fiddle with the location to which it installs the driver).

I have written a simple glade program which emulates the test program from velleman (inputs/outputs/counters etc.):

[http://yet-to.be/software/](http://yet-to.be/software/) : needs libk8055, run as root. Still in beta, work in progress, no warranty, gpl, etc. etc. 

@ Autotropics, everything that the windows based software can do (and is mentioned in the manuals), I believe the linux version(s) can do as well.

Any questions, feel free to ask or drop me a mail @ hentaidan (at) gmail.com, as I dont frequent these forums too often anymore.

---

### Post by jeremy on 2006-09-22
remember, the only silly question is the one you didn't ask!

---

