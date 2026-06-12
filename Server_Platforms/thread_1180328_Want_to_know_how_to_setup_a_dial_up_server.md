---
title: "Want to know how to setup a dial up server"
date: 2009-06-06
forum: Server Platforms
---

### Post by kustomjs on 2009-06-06
Hi Guys
I just wanted to know how can I setup a dial up server on ubuntu?

here is how my internet is setup:

FTTH connection from outside ----> to smoothwall ----> ? (like to dial up server)

---

### Post by kustomjs on 2009-06-07
after 20 views and still no reply?

---

### Post by volkswagner on 2009-06-07
Do you want to setup a dial-in server?

[http://howtoforge.com/linux_dialin_server](http://howtoforge.com/linux_dialin_server)

---

### Post by kustomjs on 2009-06-07
is it going to work? because basically why I want to build one is because I am getting ready go down to TN and only thing they have down there is dial up and I want to be able to dial in to my network and use my network to access the internet.

---

### Post by volkswagner on 2009-06-09
> **kustomjs said:**
> is it going to work? because basically why I want to build one is because I am getting ready go down to TN and only thing they have down there is dial up and I want to be able to dial in to my network and use my network to access the internet.


I have yet to try it myself, but it should work.

Before you go through the trouble, check with your provider.  My ISP (TimeWarner Cable) provides free dial up accounts to the high speed customers.  The downside is, their software only works with MS Windows and maybe Mac.

---

### Post by kustomjs on 2009-06-09
I am going to find out since my ISP isnt that big of telco to see if they do and if they dont I will setup my own dial up server.

---

### Post by lensman3 on 2009-06-09
Do a google on "ppp dialup faq linux".  This one has everything you need. [http://www.yolinux.com/TUTORIALS/LinuxTutorialPPP-Dial-in.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialPPP-Dial-in.html) .  Dailup and Dialin were state-of-the-art about 15 years ago.

The trick is this line in /etc/inittab

S1:2345:respawn:/sbin/uugetty ttyS1 115200 vt100


The respawn and uugetty which starts a terminal on the serial interface ttyS1.  Unfortunately, Ubuntu has screwed up inittab really bad and you now have to go to /etc/event.d and muck around in the files there.  I would suggest that you get use to running on a command line, because a GUI across a dialup is very slow approaching glacial.

Look for faq's from about 10 to 15 years ago.

---

### Post by kustomjs on 2009-06-10
well I got my 56k modem installed and the location it said it was installed as ttySHSF0  so where do I put in that at?

and I was trying to follow this guide: [http://www.howtoforge.com/linux_dialin_server](http://www.howtoforge.com/linux_dialin_server)

but I dont see any file under:   /etc/inittab

so what should I do?

---

### Post by n00biwan_ken00bi on 2009-07-11
^Bump

Im trying to set up my pc as a dial in server to share my ethernet with a 56k modem limited device following the directions here [http://howtoforge.com/linux_dialin_server](http://howtoforge.com/linux_dialin_server) and am facing the same "no inittab" file problem. Does anyone know how to workaround this?

Regards

---

