---
title: "Kernel 3.2-rc2 has arrived"
date: 2011-11-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2011-11-15
Just installed it from ppa kernel mainline:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc2-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc2-oneiric/)

Working nicely so far...

---

### Post by Hedgehog1 on 2011-11-16
Well, my Intel Atom based netbook likes the new kernel fine.

So I guess I will try it on my i7 based laptop next.  I get 40 minutes of battery on that system (very early i7 with short battery life when it had windows, too).  

***[I]The Hedge*[/I]**

:KS

---

### Post by Hedgehog1 on 2011-11-16
Well, the nVidia video card has stopped me from getting the 3.2 kernel successfully installed ***and*** booted on the HP laptop.  

Just when I think I have the basics down, I get put into my place.

At least I knew how to revert to the old kernel, so there is some hope for me (I guess).

***The Hedge***

:KS

---

### Post by effenberg0x0 on 2011-11-16
> **Hedgehog1 said:**
> Well, the nVidia video card has stopped me from getting the 3.2 kernel successfully installed ***and*** booted on the HP laptop.  

Just when I think I have the basics down, I get put into my place.

At least I knew how to revert to the old kernel, so there is some hope for me (I guess).

***The Hedge***

:KS

Using the proprietary NVidia driver (From NVidia website), sometimes dkms don't work on a Kernel Update and I have to manually run the NVidia installer with the -k option (compile kernel module). After that I can sudo service lightdm start, no need to reboot as it loads the module. It's fast. From console screen to usable system takes 20 seconds to fix.

---

### Post by paul_in_london on 2011-11-16
> **effenberg0x0 said:**
> Using the proprietary NVidia driver (From NVidia website), sometimes dkms don't work on a Kernel Update and I have to manually run the NVidia installer with the -k option (compile kernel module). After that I can sudo service lightdm start, no need to reboot as it loads the module. It's fast. From console screen to usable system takes 20 seconds to fix.

At the moment I'm using the 290.06 nvidia driver from xorg-edgers. I didn't need to reinstall it when I installed the 3.2-rc2 kernel. On other occasions after a kernel update, reinstalling nvidia-current using aptitude has done the trick for me.

---

### Post by Hedgehog1 on 2011-11-16
Thanks ***effenberg0x0*** and ***paul_in_london***!

You can guess what I will be doing tonight on the HP laptop!


***The Hedge***

:KS

---

