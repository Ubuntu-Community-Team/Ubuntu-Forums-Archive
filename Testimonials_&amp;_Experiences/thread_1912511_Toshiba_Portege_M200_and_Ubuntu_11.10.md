---
title: "Toshiba Portege M200 and Ubuntu 11.10"
date: 2012-01-20
forum: Testimonials &amp; Experiences
---

### Post by tpinkfloyd on 2012-01-20
So I recently fixed a Portege M200 up for a friend and cause windows didn't want to install properly I went with Ubuntu 11.10. Some things to know about the M200:

**No optical drive**
This comes with a major problem sometimes cause you have to install a OS somehow.

**No USB Boot**
Again another major issue some of you understand.

**Specific optical drives only**
The system only allows a selection of about 5 USB optical drives to be used in booting an OS. Most these drives are rare and cost ~$30 and when you are low on cash that is an issue.

**Bootable through floppy**
When I say bootable through floppy what this actually means is you can use the SD card reader as a floppy drive. Upside of this is you can boot windows if you have a large enough card. Downside of this is that by large enough card that means nothing over 1GB and definitively no SDHC cards 

The M200 is a tablet that actually has a nice setup though it does get quite hot at times. The configuration on it is:

Intel Pentium M Processor 1500MHz L2 cache - 1.0 MB
Intel 855PM Chipset
512 PC2700 DDR 333MHz SDRAM
nVIDIA® GeForceTM Go 5200 32M 4X AGP
Intel PRO/Wireless Network Connection 2200BG 
Wacom Penabled technology for the Tablet 
1400 x 1050 native display

When I installed Ubuntu the lack of an optical drive and USB boot caused big issues. I ended up putting the HDD in an old IBM T20 I had laying around my house that had very minimal specs but worked perfect for install. After install finished (took almost 3 hours) I transferred the drive back over to the M200. I turned on the M200 and it booted to where it was reading the HDD but this was taking a long time and I couldn't figure out why. It also showed nothing onscreen short of the small cursor blinking at the top left hand corner. I thought maybe 11.10 just isn't working on it, so I pulled the HDD out and installed 10.04 instead.

As I went through the process of installing 10.04 I searched the forum for any and all information I could find on the M200. Most were the same problems with different outcomes. So I prepared myself for any and all issues that might come about.

10.04 got finished and I put the HDD back in the M200, but the same problem of slow boot happened. I started searching for an answer to the issue but was coming up empty handed. Then I came across a post about SpeedStep being turned off and how to get it working. By now the system had booted but was so laggy that you couldn't use it. I decided to try what the post had said but to do that had to turn it off again. Worried that this might not work I searched around a little more first and found no other answer. I turned off the system and entered the BIOS. Inside the BIOS was an area named OTHERS. There were 3 options in this area: CPU cache, Dynamic CPU Frequency Mode, and Auto Power On. CPU Cache was disabled so I looked it up to see what it was. This was the SpeedStep section that was talked about in the post. So I enabled the cache and a new option came up, Level 2 Cache. It was also disabled so I enabled it too. 

I rebooted hoping for the best. As it got to reading the HDD it lagged for about 30 seconds and then the screen went blank and about 2 minutes later Ubuntu started. I was relieved and logged in. Hearing the login sound and straight to the desktop. Naturally I went to updates and started updating the system but it was taking a long time and I still had to upgrade to 11.10 if I could. 

I searched to see if others had and then got on my way to upgrading but though why wait when I could just install 11.10 from disc. So I pulled the HDD and started over again. 11.10 installed without a hitch and started to boot on the system. I got a white screen that I had never seen before and then the login screen. I didn't think anything of it at first then it appeared after the login screen and I got no desktop. I looked around and found my issue. Apparently the Nvidia driver that boots with the system didn't work with the Nvidia card in the system. The Fix to this was simple. Boot into ubuntu 2D and enter additional drivers and get a different version of the driver. I used version 96, not the post-release updates version and then rebooted. 

Everything was working great then I ran into a different problem I have yet to solve. The M200 went into hibernate and wouldn't come out. I had to reboot. I searched and found nothing that would work so I just turned off hibernate. So far the only other issues are getting the buttons on the tablet working and the SD card reader doesn't work. From what I understand the SD reader is an issue with the company not releasing how to make a driver for it.

I hope this helps someone so they don't run into all the problems I had and if anyone can help me with the issues I have run into it would be nice to fix them.

Also for people that are having an issue with screen rotation I haven't tested it but this [post]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") may be of some use

---

### Post by Favux on 2012-01-20
Hi tpinkfloyd,

Welcome to Ubuntu forums!

I don't think anyone has greeted you yet, so I will.  Unless you count getting yelled at by a mod a greeting?  :)

Often suspend/resume problems are cause by the i8042 keyboard controller chip not being reset.  Just try adding to the kernel boot commandline *i8042.reset*:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset"
```
and see if that does the trick.

---

### Post by tpinkfloyd on 2012-01-20
Any way you could walk me through how to do that. The last time I even touched linux was Red Hat Shrike way back in '03. I have forgotten a lot of how to do things though I am picking it up slowly again. Also I linked your post hope you don't mind. I still haven't tried it though.

---

### Post by Favux on 2012-01-20
Of course I don't mind you linking to the Rotation HOW TO, that's what it is there for.  I don't know if any of the bezel button stuff in appendix 2 will be of use to you, but you might want to have a look if you haven't already.

Grub2 now uses the grub file in /etc/default.  So:
```
gksudo gedit /etc/default/grub
```
make the edit and Save.  Then like it says at the top of the grub file run:
```
sudo update-grub
```

---

### Post by tpinkfloyd on 2012-01-20
I did it and it came up with the following:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done

Going to test now just wanted this posted if something happened so you could see

[Edit]
Ok so it went in to hibernate and after it did I hit the space first and it kicked back on to the login. Right after it did this the screen went white and then turned off. Everything was still running it just wouldn't come back on

---

### Post by Favux on 2012-01-20
Bummer.

I can't tell.  Is this an "improvement" in behavior?

Because I think I also vaguely remember someone posting how to add the i8042.reset to the resume scripts instead. Perhaps that route would work better.

---

### Post by tpinkfloyd on 2012-01-20
It is better than hibernating and not coming back on like it was. But still had to reboot the computer after the black out. I will look around and see if I can find the post you are talking about.

---

### Post by Favux on 2012-01-21
Apparently there can be multiple causes which makes it hard to debug.  A module (such as a wireless one), a video driver, more that one CPU core not being handled correctly, etc.

Are you suspending to RAM (sleep) or disk (hibernate)?  If RAM make sure your swap file is larger than your RAM.  They talk about say 1.5 x RAM size.

---

### Post by tpinkfloyd on 2012-01-21
The HDD. I haven't tried suspend yet. 

It may be the video driver there have been problems with the nVidia GeForce FX Go5200 and Linux. Not 100 sure how to fix it though. Some say the xorg nv files work while others say that it makes things worse

---

### Post by tpinkfloyd on 2012-01-21
Ok quick update on the matter. Suspend worked fine. After it is in suspend all I had to do is a quick slide of the power button and let go and it kicked out of suspend. Tried the same with hibernate but it took it all the way back to boot and then when it got to where it was supposed to show you login the screen just turned off.

---

