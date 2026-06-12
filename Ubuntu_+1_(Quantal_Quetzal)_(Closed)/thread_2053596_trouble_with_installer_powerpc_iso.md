---
title: "trouble with installer powerpc iso"
date: 2012-09-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by 2blue on 2012-09-05
I am testing for lubuntu Quantal powerpc iso. I have the Beta 1 download and are trying to install. During CD boot stage there is a message something is wrong with "b43...". It boots to a coars pixeled desktop image, and installer doesn't launch properly. I can hear cd and laptop work hard, I get the faintest outline of the installer window, and it haults.

Any thoughts or ideas?

---

### Post by cariboo on 2012-09-05
This problem has been discussed several times already. Enable ***nomodeset*** at the initial menu screen, and you should be able to boot with no problems.

To enable ***nomodeset***, press any key when you see the little man and the keyboard, press F5 and use the arrow keys to select ***nomodeset***, then boot as you normally would.

---

### Post by 2blue on 2012-09-05
Thanks for reply. I'm not sure I understand. Iso seems to boot fine, and applications also seem to run fine in live CD, except the installer. However, I shall once more search through relevant posts. I don't get a pre-menu screen other than terminal window at boot up?

Edit; I don't get the booting menu in the powerpc iso I think, it uses yaboot, and there is nothing between yaboot, terminal like windows, lubuntu loading screen and the desktop screen?

---

### Post by cariboo on 2012-09-05
Admittedly, the last PPC install I did was about 3 years ago (Debian stable), and the system is still running with only updates. It could possibly be that there isn't the option to select nomodeset when using yaboot

---

### Post by nm_geo on 2012-09-06
> **2blue said:**
> I am testing for lubuntu Quantal powerpc iso. I have the Beta 1 download and are trying to install. During CD boot stage there is a message something is wrong with "b43...". It boots to a coars pixeled desktop image, and installer doesn't launch properly. I can hear cd and laptop work hard, I get the faintest outline of the installer window, and it haults.

Any thoughts or ideas?

Hey 2blue.. I read through your qa-tracker test and I had the same problem..

When you get to the yaboot line that says>     boot:
Put in the following>                                              live video=ofonly

and let it proceed.

I think that will work when you are using a cut CD.  I however test with USBs that are created with the dd command and I boot from open firmware on my PowerBook G4. Here is a link that might help too.

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

---

### Post by rsavage on 2012-09-06
> **nm_geo said:**
> When you get to the yaboot line that says> boot:
Put in the following> live video=ofonly

That will cause crashes/freezes on a lot of machines (probably 2blue's ibook). It will turn KMS fully on which is still unstable for many radeon cards under PowerPC.
 
To turn off KMS (the nomodeset kernel argument) you just do this at the yaboot prompt:
 
```

live nomodeset

```
In the FAQ it uses radeon.modeset=0 to do the same thing [https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F)
 
> 
I think that will work when you are using a cut CD. I however test with USBs that are created with the dd command and I boot from open firmware on my PowerBook G4. Here is a link that might help too.
 
You may find using grub2 quicker and easier [http://ubuntuforums.org/showthread.php?t=2051337](http://ubuntuforums.org/showthread.php?t=2051337) . No messing around formatting and partitioning afterwards.

---

### Post by 2blue on 2012-09-06
Thanks, it works, graphical manager seems to work better, even if installer haults and freezes entire session.

---

### Post by bytehacker on 2012-09-11
live nomodereset       did not work here
live radeon.modeset=0  did not work here

I have an eMac with an ATI Radeon 9200. 

The only thing that does correct the problem here is the xorg.conf file at the PPC FAQ. My bug report 1044180 refers. There seems to be some debate as to using that file, but here it works, so I will use it.

What perplexes me is that when I first joined the PPC testers just under a month ago, it was all working well.

---

### Post by 2blue on 2012-09-12
I suppose something have changed during copying or builing packages on the Beta 1? I am eager to install the Beta, and hope Beta 2 will soon be out. Did you manager to  install beta 1 and boot fine bytehacker ?

---

### Post by rsavage on 2012-09-13
@2blue, bytehacker, nm_geo, spam_forwards, any other PowerPC testers
 
The yaboot paramaters 
 
```

video=ofonly radeon.agpmode=-1

```
should get you a working display although with lubuntu you will probably have yellow title bars. The yellow title bars are a lubuntu (openbox?) specific problem, so it is up your street to sort out. I raised the problem for 12.04, but the bug got marked as a duplicate of another and was overlooked.
 
For 12.10 you may have to change the kernel config and if you do that then you'll need to change the cd boot message so that people know to use agmode=-1. It's in the FAQ and KnownIssues pages, but as we know, nobody reads them (sigh). 
 
The config setting at the moment (as well as the 'nomodeset' parameter) is causing you to use the fbdev driver in 8 bit mode. You need to work out why this is. If you increase the defaultdepth va an xorg.conf then you get a working display, albeit with no acceleration. Do you have suspend with fbdev?
 
There is unfortunatly no ideal solution at the moment, but it is up to you guys to come up with the best option.
 
@ anybody with a radeon card on a regular architecture
 
If you use the 'nomodeset' boot parameter then do you still use the open source radeon driver or do you fall back to fbdev? You'll have to have a look in /var/log/Xorg.0.log

---

### Post by rsavage on 2012-09-13
> **rsavage said:**
> The config setting at the moment (as well as the 'nomodeset' parameter) is causing you to use the fbdev driver in 8 bit mode. You need to work out why this is. 
 
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyMDI](http://www.phoronix.com/scan.php?page=news_item&px=MTEyMDI)
 
The changelog confirms KMS only:
 
[https://launchpad.net/ubuntu/quantal/+source/xserver-xorg-video-ati/+changelog](https://launchpad.net/ubuntu/quantal/+source/xserver-xorg-video-ati/+changelog)

---

### Post by rsavage on 2012-09-14
> **rsavage said:**
>  Do you have suspend with fbdev?
 
To answer my own question again - yes you have suspend with fbdev.  (FYI you don't currently have suspend with radeon KMS).

Regardless, my own personal opinion is the radeonfb  module (this is what gives suspend) should be nolonger 'built-in' to the kernel (so you don't have to type video=ofonly) and the boot message altered.  KMS is the future and the default config should reflect this.  Currently this is not the best setup for lubuntu (fbdev is) because of the yellow window bars (but that is a lubuntu only problem and should be fixable).  Since you are the guys doing the testing you should decide.

---

### Post by bytehacker on 2012-09-14
None of the yaboot arguements here are working.

the graphics are ATI Radeon 9200

video=ofonly boots a blank screen. Not even possible to do <ctl><alt><F1>

radeon.agpmode=-1 produces a blank screen with a cursor in the centre bacgrounded by horizontal stripes over a small square behind the cursor. It's possible to move the cursor, and sometimes the background disappears. Still there is nothing else on screen.

nomodeset produces same thing.

The only thing that does work is the generic driver fbdev as contained in the xorg.conf file. Trying not to use it, but it's the only thing that works.

As soon as I can figure out how to get the Xorg.0.log file off the machine I'll attach it. In fact there is an Xorg.0.log.old and an Xorg.1.log. All three at the beginning report that:

"No screen section available. Using defaults."

No monitor specified for screen "Default Screen Section".

I'll get the full files as soon as I can figure out how to do it. I have an external modem for the ppc, a D-Link DWA125 which works out of the box, but I need a GUI to set it up. Unless somebody here can give me a hand with the CLI

---

### Post by rsavage on 2012-09-14
> **bytehacker said:**
> 
radeon.agpmode=-1 produces a blank screen with a cursor in the centre bacgrounded by horizontal stripes over a small square behind the cursor. It's possible to move the cursor, and sometimes the background disappears. Still there is nothing else on screen.
Can you confirm you are using this with video=ofonly? You could instead try
```

video=offb:off video=radeonfb:off radeon.agpmode=-1

```

---

### Post by rsavage on 2012-09-14
> **bytehacker said:**
> 
As soon as I can figure out how to get the Xorg.0.log file off the machine I'll attach it. In fact there is an Xorg.0.log.old and an Xorg.1.log. All three at the beginning report that:
 
Those are from previous boots so it makes it quite easy to copy stuff over. When the xorg server starts it renames Xorg.0.log to whatever and generates a new Xorg.0.log.
 
If you are unsure what is what then the easiest thing to do after a failed boot is to just boot back into single user mode:
 
Linux single
 
Then copy /var/log/Xorg.0.log to somewhere like your home partition
 
cp /var/log/Xorg.0.log /home/bytehacker/
 
If you have a usb drive then you can mount and copy it to that
 
mount /dev/sdb1/ /mnt
cp /var/log/Xorg.0.log /mnt
 
You can then restart the xserver
 
start lightdm

---

### Post by bytehacker on 2012-09-17
The commands suggested in #14 produced only a blank screen, and from there I couldn't even do a <cntl-alt-f1> to enter command line. Seems like this eMac of mine doesn't respond to anything like that at all. Wierd!

This time I will try single.

I'll be back!

R

---

### Post by bytehacker on 2012-09-17
command <single> resulted in a slow boot to a command line interface where I did <start lightdm>

got the GUI but with the same colour distortions (bug 1044180).

---

### Post by rsavage on 2012-09-19
For lubuntu PowerPC radeon testers:
 
This is the current situation as far as I can see [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040526/comments/8](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040526/comments/8)

---

### Post by 2blue on 2012-09-20
I still don't get any where using "video=ofonly radeon.agpmode=-1"

It turns out: 

"Please wait, loading kernel...  
video=ofonly:2,/vmlinux: Unable to open file, Invalid device
boot:"

Edit: I have a AMD ATI M11 NV FireGL Mobility T2e rev 80 video card. At least this is what it shows in System Profiler and it worked fine in 12.04.

---

