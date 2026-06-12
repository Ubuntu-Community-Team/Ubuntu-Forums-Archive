---
title: "Sun Blade 100 - 6.10 - apt-get dist-upgrade"
date: 2006-10-25
forum: Sun Sparc Users
---

### Post by carlvon on 2006-10-25
I tried to install three different versions of 6.10 on my Blade 100, but they didn't work. They would get to Booting Linux..., try a screen mode switch, and then hang. I was able to get ubuntu installed using the 6.06.1 server cd. It worked great. I did a apt-get install ubuntu-desktop and edited the xorg.conf to add the referenceclock option, and x worked. Ran update manager and got updated. I did the dist-upgrade command and it went fine. Rebooted the box, and it did the same thing as when I tried to install from the 6.10 cd, Booting Linux..., tried to switch screen mode, then nothing. So I rebooted and chose LinuxOLD at the silo prompt. Box came up, but x didn't work. Found out that the xorg-drivers didn't get updated. Installed the new ati driver and now I get this in the Xorg.0.log: xf86MapPciMem Could not mmap PCI memory [base=0x426000,hostbase=0x426000,size=2000] (Inappropriate ioctl for device). Is there a way to undo the dist-upgrade? How can I get X working again? And what is wrong with the new Kernel? I'd post more logs and diag info, but I'm stuck using elinks and apt-get install gpm doesn't find anything.

---

### Post by netztier on 2006-10-25
> **carlvon said:**
> How can I get X working again? And what is wrong with the new Kernel? I'd post more logs and diag info, but I'm stuck using elinks and apt-get install gpm doesn't find anything.

Does it hard-lock when attempting to start X? If you can still get an SSH session up, then use it to re-update the system.

From what I've heard and read, using **aptitude** instead of **apt-get **gives better results, because aptitude's dependency checking is said to be better. Might want to try **[FONT="Courier New"]aptitude update [/FONT]**and **[FONT="Courier New"]aptitude (dist-)upgrade[/FONT]** in a SSH session.

You might be able to extract the Xorg.0.log logfile via a terminal session. If that fails, a serial connection to another PC might give access to the machine. Or booting "rescue" from the installation CD and chrooting into the installed partition can help, too.

regards

Marc

---

### Post by carlvon on 2006-10-25
> **netztier said:**
> Does it hard-lock when attempting to start X? If you can still get an SSH session up, then use it to re-update the system.

From what I've heard and read, using **aptitude** instead of **apt-get **gives better results, because aptitude's dependency checking is said to be better. Might want to try **[FONT="Courier New"]aptitude update [/FONT]**and **[FONT="Courier New"]aptitude (dist-)upgrade[/FONT]** in a SSH session.

You might be able to extract the Xorg.0.log logfile via a terminal session. If that fails, a serial connection to another PC might give access to the machine. Or booting "rescue" from the installation CD and chrooting into the installed partition can help, too.

regards

Marc

When using the new kernel from the 6.10 update, it never gets to the point of trying to start x. The box will lock up when the kernel tries to switch from the black-on-white to white-on-black. I've left it there for 20 mins and tried to see if I could ssh in, but no dice. I think the kernel doesn't support the blade 100. Has anyone been able to run the new kernel that Edgy installs (I'm at work and not sure what version it is but I think its 2.6.17) on a blade 100?

I have since reinstalled Dapper and everything is working fine. I'll skip the upgrade distro for awhile. I'm willing to test the new kernels if someone would like to see if there is a support issue with blade 100s.

---

### Post by carlvon on 2006-10-25
[http://www.nabble.com/forum/ViewPost.jtp?post=6813678&framed=y]("http://www.nabble.com/forum/ViewPost.jtp?post=6813678&framed=y") Talks about 2.6.18 booting on a Blade 100. I'm willing to try kernels with some patching.

---

