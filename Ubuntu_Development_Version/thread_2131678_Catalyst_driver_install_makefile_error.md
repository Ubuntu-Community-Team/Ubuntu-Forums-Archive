---
title: "Catalyst driver install makefile error"
date: 2013-04-02
forum: Ubuntu Development Version
---

### Post by Tommy The Cat on 2013-04-02
I'm running Ubuntu Studio 13.04 beta and I'm trying to install the 13.3 beta3 catalyst driver using the binary from AMD's website. Well, actually I already have installed, rebooted, and I've not gotten a black screen of death, but there was this makefile error that has me a bit scared and the testing watermark in the bottom right of my screen has "3D" circled and crossed out (a la the no-smoking signs on airplanes). 

Here's a paste of the install log. 
[http://pastebin.com/wf15gUQn](http://pastebin.com/wf15gUQn)

What's going on here? Does this have anything to do with why steam will not run? It would start just fine before I installed the new driver. 

Thanks much, 
Tom

---

### Post by QIII on 2013-04-02
Moved to U+1

---

### Post by Tommy The Cat on 2013-04-02
Thanks for the move, hopefully this can get some attention. Some updates came in and got installed this evening. Tried to run the installer again to find a different set of errors. These read something like this:

[http://pastebin.com/nQS3iUJ4](http://pastebin.com/nQS3iUJ4)

I was in the linux-ati irc channel earlier and someone (who shall remain nameless) suggested I was missing a kernel source. No idea what that is and how to fix it; and this individual was entirely unhelpful in that regard.

---

### Post by QIII on 2013-04-02
You will need to add linux-headers-generic.

```
sudo apt-get install linux-headers-generic
```

Try again after that and let us know what happens.

I have had no time this cycle to do any testing, so I hope that will get you going.

---

### Post by ManamiVixen on 2013-04-02
QIII, he is on Ubuntu-Studio which has a different Kernel. He needs the real time kernel headers.

---

### Post by Tommy The Cat on 2013-04-03
yeah, the linux-headers-generic package made no difference. I tried to do a little bit of googling to find out more on the subject of the real time kernel. Most references to it were kind of dated (didn't refer to the 3.8 kernel that's currently in use in my distro) so I'm still not exactly sure what it is or how to get it. Clue me in?

---

