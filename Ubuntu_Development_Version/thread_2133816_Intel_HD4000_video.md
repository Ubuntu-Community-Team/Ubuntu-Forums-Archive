---
title: "Intel HD4000 video"
date: 2013-04-09
forum: Ubuntu Development Version
---

### Post by canadianwriterman on 2013-04-09
Has anyone tried installing Ringtail on a machine with Intel HD4000 graphics. I haven't been able to use the last two releases on my machine and get a desktop without annoying workarounds. Hopefull the issue has been solved so I can can back to using Ubuntu!

---

### Post by Gompa on 2013-04-09
i dunno if it is the same problem.
but i get this when starting ubuntu 13.04 on my intel i3 3220 on a h67 motherboard.

[ATTACH=CONFIG]241152[/ATTACH]

ps debian wheezy works fine with the 3.2 kernel but if i compile the 3.8/3.9 series the same thing happens so i think it is a kernel bug ?

---

### Post by chrisle on 2013-04-09
No problems here on a Lenovo Thinkpad L430. Only thing that doesn't work for me is brightness keys regression  [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1156477](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1156477)

Why not try booting and testing from a usb stick?

---

### Post by canadianwriterman on 2013-04-09
Chrisle: The weird thing is that the live version always worked for me. This failure to load the desktop only happened after installing on the hard drive.

---

### Post by chrisle on 2013-04-09
Are you sure you don't have nvidia or amd plus intel graphics card installed?

Do you have reported this bug?

Are you using the latest bios for your Dell maybe a bios issue?

---

### Post by oldfred on 2013-04-09
It must work for some, but he uses some of the very newest drivers.

 Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics Jan 2013 with 13.04
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)

---

### Post by Gyokuro on 2013-04-09
> **oldfred said:**
> It must work for some, but he uses some of the very newest drivers.

 Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics Jan 2013 with 13.04
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)

That's the missing part - he was using for the published benchmark Mesa 9.1-devel (mesa git trunk) and maybe this is helpful ([http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)).

---

### Post by White Rasta on 2013-04-10
It's been workin for me lately
I was getting some low graphics boots but after a reboot it would be OK
a message would pop up that there was a problem detected after logging on
I choose the "not sure" option on the bug report (cause I'm an idiot)
it came back with a sudgestion to upgrade 4 packages which i did in synaptic (I don't remember which ones)
and we're all happy and stable now
I got a lenovo thinkpad 230 w/o the centrino wireless

---

### Post by canadianwriterman on 2013-04-10
Interesting replies. When I read them, I'm not sure if the problem has been fixed or not. My machine has an Ivy Bridge processor and Intel HD4000 graphics (no AMD or nVidia) and the last two versions of Ubuntu would simply bring up a blank, black screen on bootup, although the Live versions worked fine. It was a common problem and received many postings on the forum at the time. There were lots of suggested workarounds, but they were awkward and annoying and really didn't "fix" the issue. 

It SEEMS like there has been work done in the kernel to make things better, but when I read White Rasta's reply, I'm not sure it has been fixed. Since Ivy Bridge and Intel HDXXXX graphics are becoming more common in newer machines, I am praying that Ringtail will install and boot up to a desktop so that I can, once again, enjoy the benefits of Ubuntu. When the final release comes out, I'll be trying it again.

---

### Post by Gyokuro on 2013-04-10
> **canadianwriterman said:**
> Interesting replies. When I read them, I'm not sure if the problem has been fixed or not. My machine has an Ivy Bridge processor and Intel HD4000 graphics (no AMD or nVidia) and the last two versions of Ubuntu would simply bring up a blank, black screen on bootup, although the Live versions worked fine. It was a common problem and received many postings on the forum at the time. There were lots of suggested workarounds, but they were awkward and annoying and really didn't "fix" the issue. 

It SEEMS like there has been work done in the kernel to make things better, but when I read White Rasta's reply, I'm not sure it has been fixed. Since Ivy Bridge and Intel HDXXXX graphics are becoming more common in newer machines, I am praying that Ringtail will install and boot up to a desktop so that I can, once again, enjoy the benefits of Ubuntu. When the final release comes out, I'll be trying it again.

Hi

If I'm not totally wrong it seems that you are using Ubuntu 12.10 - is it possible for you to boot a Raring live cd/usb and post your /var/log/Xorg.0.log and a top output of a live session?? As you have the hardware in which developers are interested your feedback should be welcome and here is the concerning thread [http://ubuntuforums.org/showthread.php?t=2133979](http://ubuntuforums.org/showthread.php?t=2133979) 
I would do this test myself but I do not have hardware with Intel HD4000 GPU and Mesa 9.1 bring in support for your Intel GPU.

---

### Post by pqwoerituytrueiwoq on 2013-04-10
> **Gompa said:**
> i dunno if it is the same problem.
but i get this when starting ubuntu 13.04 on my intel i3 3220 on a h67 motherboard.

[ATTACH=CONFIG]241152[/ATTACH]

ps debian wheezy works fine with the 3.2 kernel but if i compile the 3.8/3.9 series the same thing happens so i think it is a kernel bug ?

that looks like what happened to me on super mario bros 3 (nes game) from time to time and i had to blow the cartridge
that said can you get to a tty to make a xorg.conf file (i would use nano)?
/etc/X11/xorg.conf
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
```
this will revert a thing that is supposed to be a major improvement for intel gpus
if it fails just delete the file

iirc raring uses sna and quantal uses uxa by default
so this probably will not work, but worth a try

---

### Post by Gyokuro on 2013-04-11
> **pqwoerituytrueiwoq said:**
> that looks like what happened to me on super mario bros 3 (nes game) from time to time and i had to blow the cartridge
that said can you get to a tty to make a xorg.conf file (i would use nano)?
/etc/X11/xorg.conf
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
```
this will revert a thing that is supposed to be a major improvement for intel gpus
if it fails just delete the file

iirc raring uses sna and quantal uses uxa by default
so this probably will not work, but worth a try

Thanks for your comments - so it seems there is a problem with Ubuntu's graphic stack as in Debian wheezy "SNA" for Intel GPU's isn't the default setting - "UXA" get used and kernel is 3.2.XX, mesa 8.0.5. Most of this is identical to Ubuntu Precise 12.04.2 (without LTSEnablementStack) - the real LTS :-) (kernel 3.2.XX and mesa 8.0.5). So only neweer kernels and graphic stacks must be tested.

---

### Post by northar on 2013-04-14
I have a Intel 4000 in my machine, and running raring i get:
:Sometimes a black screen on loging screen (but can login anyway, typing in the dark so to say
:Strange graphic glitches in Firefox.

I wonder if this has been reported, the release date is drawing nearer, and i guess a lot of people have intel 4000 by now.

---

### Post by Gyokuro on 2013-04-14
> **northar said:**
> I have a Intel 4000 in my machine, and running raring i get:
:Sometimes a black screen on loging screen (but can login anyway, typing in the dark so to say
:Strange graphic glitches in Firefox.

I wonder if this has been reported, the release date is drawing nearer, and i guess a lot of people have intel 4000 by now.

Hi

Is this the same problem as the one reported here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1162349](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1162349)

---

### Post by ewlinux on 2013-04-28
I can confirm this issue. Ivy Bridge and HD4000(Lenovo G580) 

I`ve just upgraded from 12.10 to 13.04 and I am welcomed by a big nice blackscreen. 12.10 worked OOTB for me. I`m also running lots of Debian distros, and I have the same issues with 3.7 and 3.8 kernels there. 3.5 and 3.6 works OOTB. For my Debian distros I`ve found a fix that lets me use 3.8 kernels. The fix is to add this to the kernel line: ""acpi_osi=\Linux\ acpi_backlight=vendor" ,  and add "setpci -s 00:02.0 F4.B=80" to etc/rc.local . This fix works for me in Debian, but it didn`t work with Ubuntu 13.04... At least it didn`t when i tried it yesterday on a clean install. Today I reinstalled 12.10 and tried the upgrade route instead, hoping that would bring me better luck, but sadly not. But I`ll keep hacking on with those kernel parameters, and see if I get it to work. It`s quite annoying to have these kind of issues on what is the new default hardware in most computers.

---

### Post by ewlinux on 2013-04-28
Just in case my fix will work for others with Ivy Bridge and Intel HD4000 Graphics, (Lenovo G580), I`m posting what worked for me. Don`t know why, but it works for me.

1. Edit the kernel line in /etc/default/grub - and add "acpi_osi=Linux", so that it looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"

2. Update grub and reboot...... Works for me.

---

### Post by simple_2k3 on 2013-04-28
This worked for my Lenovo Y580 and was a much better than using "nomodeset" from the grub menu.  Also "lshw -c display" no longer shows "display UNCLAIMED" for the Intel HD4000 Graphics.  I'm thinking something ACPI related prevented the intel graphics driver/module from being loaded.

---

### Post by Paper Bag on 2013-10-18
**13:10:**

Anyone else feeling that some Compiz things feel sluggish compared to 13.04? For example:

- desktop wall sliding
- expo zoom in/out

Not laggy, but visibly jerky/sluggish, a bit like V-sync sometimes makes things sluggish. I noticed the difference immediately when I upgraded to 13.10, so I don't think it is placebo.

Interestingly some other things feel faster, e.g. the way some windows get drawn on the screen, but this might be just general Unity/Ubuntu/Gnome speed improvements.

```
compiz:
Installed: 1:0.9.10+13.10.20131011-0ubuntu1
Candidate: 1:0.9.10+13.10.20131011-0ubuntu1
```
```
xserver-xorg-video-intel:
Installed: 2:2.99.904-0ubuntu2
Candidate: 2:2.99.904-0ubuntu2
```
I have tried playing around with the V-sync and refresh rate settings in CCSM, but no change.

I am thinking it has to be something in Compiz, because on another account on this computer, it feels as if the above things were slightly smoother.

---

### Post by Elfy on 2013-10-19
This sub forum is for the discussion/troubleshooting of development versions.

    Finding threads in here and then using them for support once a version has been released won't work.

    Please start a new support thread in a suitable sub-forum.

    Closed.

---

