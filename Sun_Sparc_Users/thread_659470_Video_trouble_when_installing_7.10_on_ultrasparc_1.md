---
title: "Video trouble when installing 7.10 on ultrasparc 10"
date: 2008-01-05
forum: Sun Sparc Users
---

### Post by CorporateTool on 2008-01-05
Hi there,

I've been trying unsuccessfully for about a week to install Ubuntu 7.10 on my UltraSparc 10.  After typing "install" or hitting enter at the SILO prompt, the kernel starts to boot.  Immediately following the message "Booting Linux" my video goes blank and my monitor says "out of range".  This particular box has an onboard Mach64-based ATI video chip.  It does not have any other video card.

I understand this has been a problem in the past and I read the gentoo documentation which told me to do the following in the PROM:

setenv output-device screen:r1024x768x60
reset

Then, when booting from the install cd I'm typing:

install video=atyfb:1024x768@60

I've also tried:

install append="video=atyfb:1024x768@60"

In both cases I continue to get the out of range error.  I've confirmed my TFT can handle that res and refresh rate and I've tried an old CRT just to be certain.  I've tried other modes (1024x768@70, 1280x1024, etc).  I've also tried to install the latest Debian Sparc build and I'm seeing the same result.

As a last resort I reset my NVRAM (holding stop-n for 5 seconds) but no luck there either.  

This thread:  [http://lists.debian.org/debian-sparc/2005/02/msg00073.html](http://lists.debian.org/debian-sparc/2005/02/msg00073.html)
 details a problem that sounds the same and it required a patch to the atyfb driver, though I'm not sure if that's relevant at this point.

Thanks in advance for any help you may be able to offer.

---

### Post by zanderred on 2008-01-06
Hi, you get the banner and the ok prompt, so things seem to be working, you could try, when initilizig memory press stop-a, (befor it finished) at ok prompt, set-defults, (this will set env default), ok reset, when initilizing stop-a, at ok boot cdrom.

---

### Post by TehCamel on 2008-01-26
sounds like maybe silo is trying to display an image (this is what mine did)
check a few of my other posts, and i may have posted what I've done... i can't recall ottomh

---

### Post by cclub on 2008-01-26
What version of OBP are you running? Inorder to install Ubuntu I had to netboot. I also installed 7.04. I also had to remove the add-in videocard. Untill i removed the video card, installation would stop at "booting linux"

---

### Post by arfonzo on 2008-02-01
Hi, 

Do you actually need your monitor?

If not, you should be able to install in headless mode using a null modem cable (check out another thread I've posted to about it [here]("http://ubuntuforums.org/showthread.php?t=664854")). The process is relatively painless, and you don't need a keyboard and monitor plugged into the ultra 10 at all.

BTW - I have installed off a nightly hardy iso--you might have better luck with a hardy media set.

Hope this helps,
- Art

---

