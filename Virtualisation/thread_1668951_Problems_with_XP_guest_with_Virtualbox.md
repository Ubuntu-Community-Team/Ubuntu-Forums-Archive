---
title: "Problems with XP guest with Virtualbox"
date: 2011-01-17
forum: Virtualisation
---

### Post by Kevin_j76 on 2011-01-17
I recently installed Ubuntu 10.10 on my new Compaq laptop, I've been running Ubuntu for a while now on my desktop and just prefer it. However i do use my laptop a lot for netflix, so i decided to setup xp in virtual box since netflix doesn't work in Ubuntu. The first time i installed xp it worked fine but while installing guest additions it crashed and i had to power off the VM and it stopped working after that. So i decided to delete that install and try agian, which is where my problems begin. Now every time i try to install xp it tells me
   "Setup cannot load the keyboard layout file KBDUS.DLL.
    Setup cannot continue. Shut down or restart your computer"
and i have no idea where to go from here... I've tried uninstalling and reinstalling Virtualbox and deleting the .vdi's but its not getting me anywhere.. any help would be greatly appreciated...

---

### Post by vidtek on 2011-01-17
> **Kevin_j76 said:**
> I recently installed Ubuntu 10.10 on my new Compaq laptop, I've been running Ubuntu for a while now on my desktop and just prefer it. However i do use my laptop a lot for netflix, so i decided to setup xp in virtual box since netflix doesn't work in Ubuntu. The first time i installed xp it worked fine but while installing guest additions it crashed and i had to power off the VM and it stopped working after that. So i decided to delete that install and try agian, which is where my problems begin. Now every time i try to install xp it tells me
   "Setup cannot load the keyboard layout file KBDUS.DLL.
    Setup cannot continue. Shut down or restart your computer"
and i have no idea where to go from here... I've tried uninstalling and reinstalling Virtualbox and deleting the .vdi's but its not getting me anywhere.. any help would be greatly appreciated...

Kevin-

Firstly we need to know a bit about your system.  
How are you installing Virtualbox, from the repositories (OSE) or the PEUL version from the website.  32 0r 64-bit etc etc.

My recommendation is to completely uninstall Virtualbox then get the PEUL version from the Virtualbox website.  Make sure you get the right version, 32 or 64-bit.
Then you need to install the operating system from the original windows disc (or an .iso of the disc).  
Install the Virtualbox extensions and additions.

Tony.

---

### Post by wilee-nilee on 2011-01-17
So is this the Ose version or the Puel.

Did you install the guest from the software center or synaptic.

---

### Post by vidtek on 2011-01-17
> **wilee-nilee said:**
> So is this the Ose version or the Puel.

Did you install the guest from the software center or synaptic.


Neither- As a file d/l
Virtualbox make it hard to find the additions as a separate file download, they sort of hide it, no idea why oracle are so coy about it.  

Somewhere here on this forum there is a link posted, but I can't find it now.  From memory it was something like [http://www.virtualbox.org/wiki/Downloads/guestadditions](http://www.virtualbox.org/wiki/Downloads/guestadditions)

but don't quote me on it!

Tony.

---

### Post by Kevin_j76 on 2011-01-17
System spec's are here... [http://www.gadgets-freak.biz/compaq-presario-cq56-115dx-review/]("http://www.gadgets-freak.biz/compaq-presario-cq56-115dx-review/")
and i'm running puel 64bit installed from a .deb i downloaded from the oracle site, which I learned from installing it on my desktop is what i need for usb, and i'm installing xp off of a cd.  I've tried compeletly uninstalling and reinstalling and it did not solve my problem.

---

### Post by vidtek on 2011-01-17
> **Kevin_j76 said:**
> I recently installed Ubuntu 10.10 on my new Compaq laptop, I've been running Ubuntu for a while now on my desktop and just prefer it. However i do use my laptop a lot for netflix, so i decided to setup xp in virtual box since netflix doesn't work in Ubuntu. The first time i installed xp it worked fine but while installing guest additions it crashed and i had to power off the VM and it stopped working after that. So i decided to delete that install and try agian, which is where my problems begin. Now every time i try to install xp it tells me
  [B][I] "Setup cannot load the keyboard layout file KBDUS.DLL.
    Setup cannot continue.[/I][/B] Shut down or restart your computer"
and i have no idea where to go from here... I've tried uninstalling and reinstalling Virtualbox and deleting the .vdi's but its not getting me anywhere.. any help would be greatly appreciated...

Kevin-
Just a thought-
Maybe the install is having a problem with the laptop keyboard/touchpad hardware. Try using an external usb keyboard.

Tony.

---

### Post by Kevin_j76 on 2011-01-18
Fixed it... From what i was reading the error happens when trying to install xp over some other windows os's, or in this case i guess it happened with my first xp install that crashed so i just grabbed a Fedora disc set up vm like i was going to install xp then installed fedora on it, then installed xp over fedora and it worked...

---

### Post by vidtek on 2011-01-18
> **Kevin_j76 said:**
> Fixed it... From what i was reading the error happens when trying to install xp over some other windows os's, or in this case i guess it happened with my first xp install that crashed so i just grabbed a Fedora disc set up vm like i was going to install xp then installed fedora on it, then installed xp over fedora and it worked...

Well done Kevin, bit of lateral thinking there, don't forget to mark this thread as solved.

Tony.

---

