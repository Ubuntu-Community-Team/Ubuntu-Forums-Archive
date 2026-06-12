---
title: "Initial disappointment having to look for fixes"
date: 2008-10-31
forum: Testimonials &amp; Experiences
---

### Post by wishy77 on 2008-10-31
Senior cit here
I have been using Ubuntu as a distribution of choice since Breezy.
Normally dual booted with windows, also run multi boot system with etch4, and have tried many linux distros over the years.
I accept a few install problems as the norm but was most disappointed to have the install of 8.10(which was flawless with Hardy) stall with an intramfs error.
Having to find "fixes" will be a multiple frustration for new users.
Found the fix but new users wouldn't have the confidence editing files.
Final decision pending.
Later found unable to read dvd r-w  not mounted.
Tried mounting to no avail
Am giving one last chance by upgrading Hardy to 8-10, if this is not satisfactory will consign Intrepid to the "other distros" fun but no thanks.

---

### Post by delanov on 2008-11-01
> **wishy77 said:**
> Senior cit here
I have been using Ubuntu as a distribution of choice since Breezy.
Normally dual booted with windows, also run multi boot system with etch4, and have tried many linux distros over the years.
I accept a few install problems as the norm but was most disappointed to have the install of 8.10(which was flawless with Hardy) stall with an intramfs error.
Having to find "fixes" will be a multiple frustration for new users.
Found the fix but new users wouldn't have the confidence editing files.
Final decision pending

I'm running 8.04 and as you stated no problem with its install.  My machine is an old hp 500Mb/1300Mhz.  I have not read of other posters having this problem; have you?  I think I'll try an install 8.1 on different machine before desturbing 8.04.

---

### Post by wishy77 on 2008-11-01
The boot went to a shell with an initramfs
Fix found below
the system will drop to a busybox initramfs shell with a 
"Gave up waiting for root device." error.
 ..... exit the initramfs shell by typing 'exit'.
You may have to do this several times then....
 Booting should proceed normally. 
 Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel."
Did this fix, rebooted and now booting fine.

---

### Post by cardinals_fan on 2008-11-01
Users who want an OS that "just works" will buy preinstalled.

---

### Post by wishy77 on 2008-11-01
Quote:"Users who want an OS that "just works" will buy preinstalled."
Didn't expect a reply like this.
One of the best things about most of the Ubuntu versions I have used has been that "most" things just worked.
Apart from a few codecs everything else was stable and worked well.
Just for info I have installed and used Etch4,Mandriva, Suse,Mandrake,Fedora , Foresight and dabbled with various others...so hardly fall into the "preinstalled" needed., and having worked and installed programs and operating systems since 1988 regard your comment as rubbish.
Incidentally the "upgrade" from Hardy to Intrepid also was not a success and Hardy is now reinstalled and Intrepid consigned to the "others" collection.

---

### Post by cardinals_fan on 2008-11-02
> **wishy77 said:**
> Quote:"Users who want an OS that "just works" will buy preinstalled."
Didn't expect a reply like this.
One of the best things about most of the Ubuntu versions I have used has been that "most" things just worked.
Apart from a few codecs everything else was stable and worked well.
Just for info I have installed and used Etch4,Mandriva, Suse,Mandrake,Fedora , Foresight and dabbled with various others...so hardly fall into the "preinstalled" needed., and having worked and installed programs and operating systems since 1988 regard your comment as rubbish.
Incidentally the "upgrade" from Hardy to Intrepid also was not a success and Hardy is now reinstalled and Intrepid consigned to the "others" collection.
Installing an OS is never an exact, flawless process - unless the machine is designed for that OS.  Linux has done great things with out-of-the-box hardware compatibility, but "just works"-type experiences are only consistent on preinstalled machines.

---

### Post by Tamlynmac on 2008-11-02
> cardinals_fan
Installing an OS is never an exact, flawless process - unless the machine is designed for that OS. Linux has done great things with out-of-the-box hardware compatibility, but "just works"-type experiences are only consistent on preinstalled machines.

I must agree whole heartedly with cardinals_fan. What I don't understand is why everyone's in such a hurry to upgrade if their already using a fully functional OS. The only reason I even considered upgrading one of our 5 systems was to evaluate 8.1 and it's updates prior to installing on our other systems. Any time one considers installing a new OS, it should be investigated for compatibility and improved functionality - or whats the expectations / purpose. As cardinals_fan states if you want assurance that it will work OOTB, then it's best to buy it preinstalled.

---

### Post by vikramaditya on 2008-11-03
> **Tamlynmac said:**
> Any time one considers installing a new OS, it should be investigated for compatibility and improved functionality
+1...ain't broke = don't fix.

---

### Post by appier on 2008-11-03
> **wishy77 said:**
> 
One of the best things about most of the Ubuntu versions I have used has been that "most" things just worked.


For me, this has been a major "plus" for the Ubuntu family of distributions.  Most of the time, they do "just work".  Unless one is purchasing from Dell or some other more obscure manufacturers, "pre-installed" is just not much of an option so trying to make the install and upgrade process as glitch-free as possible would seem to me to be a worthy objective.

---

