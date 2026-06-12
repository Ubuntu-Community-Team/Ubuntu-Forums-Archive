---
title: "Linux Install Not booting"
date: 2010-05-04
forum: Server Platforms
---

### Post by zabijecie on 2010-05-04
First off Hi!

I originally started with a Debian install for a server but that kept giving me errors when loading the OS.

System specs: 2004ish 2.8ghz celeron, 756mb ram, 80gb hd. 128bit pny geforce gfx card.

After 3 attempts at installing Debian through 3 different methods (dvd, cd, netinst) I decided to give ubuntu a try.

Everything installs fine, and upon first boot loading, after selecting one of the two choices in grub loader, the computer stops after end trace and the last display is:
"udevd-event[1081]: run_program: '/sbin/modprobe' abnormal exit."
I get a blinking underscore i can type things in but system is left unresponsive.

Memtest turns out everything is fine. NO Lvm.

I was looking forward to using linux as my webserver hosting, but after 4 failed attempts (probably on my behalf), i'm looking into trying windows 2003, something i'd rather not unless im left without a choice.


Thanks,
-Zabi

---

### Post by Vegan on 2010-05-04
Download the server version and ignore the grub menu when booting after the install

do not worry about grub, ignore its existance

---

### Post by zabijecie on 2010-05-05
Okay i'll start a fresh install without grub loader. I'll let you know how it turns out. Thanks!

---

### Post by zabijecie on 2010-05-06
did not install grub loader. Nothing happens. I am soo lost.

---

### Post by arrrghhh on 2010-05-06
Without any knowledge of what's actually going on, have you tried a LiveCD to ensure Linux or more specifically Ubuntu doesn't have any quips with your hardware?

The server disc doesn't come with a LiveCD, it can't boot from the disc to a fully-functional OS... but that would be interesting, haha.

---

### Post by oldfred on 2010-05-06
You have to have grub in the MBR or else your computer will not boot.

You can install it:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by zabijecie on 2010-05-07
Not sure what you mean by "livecd"... [http://www.livecdlist.com/ubuntu](http://www.livecdlist.com/ubuntu) This site i found for livecd search on google came up with only the same download links.

---

### Post by arrrghhh on 2010-05-07
> **zabijecie said:**
> Not sure what you mean by "livecd"... [http://www.livecdlist.com/ubuntu](http://www.livecdlist.com/ubuntu) This site i found for livecd search on google came up with only the same download links.

If you download the -desktop install & burn it, the LiveCD is included.  The -server install doesn't have a LiveCD.  Although it sounds like perhaps GRUB is messed up, did you try that tutorial oldfred posted?

---

### Post by BobVila on 2010-05-07
Not sure if you're in the same situation that I was in, but I found that 10.04 did NOT like booting with USB devices that it couldn't properly identify plugged in. I've got a hacked up USB cable that draws 5v but passes no data. Had it plugged in while trying to boot 10.04 on two different systems and almost lost my mind out of frustration - seemed to exhibit the same symptoms that you described. For giggles, remove any unnecessary peripherals and give it a go.

---

### Post by zabijecie on 2010-05-07
Yes i tried the grub fix, and grub loader comes on but still same error as before.
I am currently downloading Ubuntu OS. From my understanding i need this in order to run a ubuntu Server? Ony usb device is my mouse. All installations are from a cd.

Thanks for being so helpful guys, i find this forum more user friendly than debian forums in terms of responses!

-Zabi

---

### Post by arrrghhh on 2010-05-07
Well, to run ubuntu-server you just need the ubuntu-server ISO burnt to a CD.

I was suggesting ubuntu-desktop as you can run the full environment from the CD, ensuring that your hardware is compatible.

That may not be the issue, I'm still not entirely clear on what the actual problem is.  Do you have any other output from the failed boots?  I'm also assuming it fails to boot if you select "recovery mode" also?

---

### Post by zabijecie on 2010-05-08
Okay, so i have Ubuntu ISO on a cd, when trying to install the caps lock and scroll lock lights flash on the keyboard and i am unable to do anything.

4.93188 <c058b983> error_code+0x73/0x80

I've hit F6 and did the no-acp thing option but i once i select it i cannot go back into the "install ubuntu" menu it is stuck at the F6 options...

---

### Post by cariboo on 2010-05-09
It sounds like you have a bad burn, at the initial, the one with the man and the keyboard at the bottom, press the any key, you will then have to select your language before seeing a menu. Select test CD for defects using the arrow keys, and let it run. This will tell you if the CD is good to go.

---

