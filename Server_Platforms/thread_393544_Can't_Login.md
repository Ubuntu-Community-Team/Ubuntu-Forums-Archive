---
title: "Can't Login"
date: 2007-03-25
forum: Server Platforms
---

### Post by mfmbcpman on 2007-03-25
I installed Ubuntu Server Edition with LAMP. On reboot, I am prompted with host login: _

No matter what I type nothing displays. I try to enter my username and hit enter but nothing happens at all. Just that prompt and the flashing cursor.

---

### Post by mfmbcpman on 2007-03-25
What is supposed to happen at this point? This is my first time using Ubuntu Server.

---

### Post by Mr. C. on 2007-03-25
Try switching terminals with 

Ctrl-Alt-F1, F2, ... F6.

If this fails, boot into the recovery mode, and see if your keyboard input is accepted.

MrC

---

### Post by mfmbcpman on 2007-03-26
> **Mr. C. said:**
> Try switching terminals with 

Ctrl-Alt-F1, F2, ... F6.

If this fails, boot into the recovery mode, and see if your keyboard input is accepted.

MrC

When I tried switching terminals, the screen went black and I couldn't get the terminal back through the F1 through 12.

Recovery mode didn't help either. The keyboard works and is plugged in because I have to punch keys to get into recovery mode. It is a standard 104 key US English keyboard connected by PS/2

---

### Post by mfmbcpman on 2007-03-26
From [http://www.enac.northwestern.edu/~tew/page/2/]("http://www.enac.northwestern.edu/~tew/page/2/")
> Dell Precision Workstation 350 has a problem when running Linux kernels in the 2.6.x series with the keyboard and busmice. If you boot them up without touching a key (say in GRUB, for instance) you&#8217;ll get a message like i8042.c: Can't read CTR while initializing i8042 in your dmesgs.

This makes the keyboard and mouse not respond. If, while trying to debug this problem, you touch a key sometime between POST and when the kernel tries to initialize the i8042, you won&#8217;t have this problem.

One workaround is to touch a key between POST and initialization every time the machine boots. Another workaround is to add acpi=off to your kernel bootup arguments, say in GRUB or LILO. I understand that you could also pass i8042.noacpi=1, according to the linux-kernel mailing list &#8212; but I haven&#8217;t tried this.


I am getting the "Can't Read CTR while initalizing i8042" error message. I'm running a Dell 4300S not a precision workstation. If I press keys, during the bootup, I don't get the error message but the system is still nonresponsive to any input.

---

### Post by dannyboy79 on 2007-03-26
well, try the other solution. when you get the prompt of grub, go to the kernel line you want to boot but this time hit E, which is for editing it. that should bring up your kernel boot line, then go to the way end and add
acpi=off
and then hit the "b" which will boot this kernel entry with that option. if that works we need to edit your /boot/grubmenu.lst file for good. Due to kernel updates and grub-update you'll want to add this to your 
#kopt line within the menu.lst file, this way whenever grub gets autoupdated to boot a new kernel, this will get added no matter what on the end. So look for a line like this:
# kopt=root=/dev/hda1 ro 
Then just add acpi=off at the end of it. so it would be
# kopt=root=/dev/hda1 ro acpi=off
(NOTE: yours may be different as far as waht drive your root is on-ie hda1)

These are the options passed to the linux kernel: 
# kopt=root=/dev/hda1 ro 
Everything after "kopt=" is passed to the kernel as parameters.
Good luck

---

### Post by mfmbcpman on 2007-03-27
I added the acpi=off line, then I was able to boot up and login. However, no matter what I do after a reboot, I cannot type to login.

After I logged in, I gave root a password, ran apt-get update, and installed OpenSSH server.

---

### Post by mfmbcpman on 2007-03-27
Would moving to an older version fix this? Like an older kernel version?

---

### Post by Mr. C. on 2007-03-27
Have you tried swapping keyboards?  I understand that it works during BIOS boot, but it may be a problematic keyboard whose errors are ignored in the BIOS but are not by the Linux keyboard driver.

MC

---

### Post by rt2007 on 2007-04-05
had the exact same problem just there.. switched keyboards and it worked.. new problem was my password didnt work, probably beacuse the old keyboard put it in wrong in setup or something.

Problem keyboard for me was DELL Keyboard Model RT7D00

---

