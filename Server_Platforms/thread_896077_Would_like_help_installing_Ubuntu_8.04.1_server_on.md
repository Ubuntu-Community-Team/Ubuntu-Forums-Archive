---
title: "Would like help installing Ubuntu 8.04.1 server on new system"
date: 2008-08-20
forum: Server Platforms
---

### Post by nashibuntu on 2008-08-20
Hi there.

I am trying to install Ubuntu 8.04.1 server edition on a new computer from a CD-ROM: ASUS M3A-H/HDMI, 4GB RAM, AMD PHENOM X3 8750, 4xSATA, 256MB Radeon 2400 PRO PCI Express. It's not going as smoothly as I would have hoped.

When I select to install it, the kernel loads to 100% and then I get a page of codes (no text that means much to me) followed by

--[ end trace .... ]--
Kernel panic - not syncing: Attempted to kill init!

I have run a memory test and it passed three times. I have also disabled the "Express Gate" bios option that allows connecting to the internet and using Skype etc. without having to launch the operating system in case that is interfering. I have tried using both mem=512M and mem=4096M, but that hasn't helped.

I also happen to have an install CD of Ubuntu Gutsy Desktop edition. I have tried booting from and installing from that, but I get a different error. This one is more descriptive. It says:

Fixing recursive fault but reboot is needed!
BUG: scheduling while atomic: init/0x00000002/880
... a load of codes (do_exit, do_page_fault, etc.) ...
====================
input: AT Translated Set 2 keyboard as /class/input/input1

It freezes there.

I have tried rebooting, but I get the same message. In case this is an issue, I haven't yet formatted or partitioned any of the hard disks. I was hoping that the installer would prompt me to do that. That's right isn't it?

I am guessing that there might be some changes to the BIOS I could make that would help... but there are so many possibilities I wouldn't know where to start. Changing from PCIE to PCI? 

Has anyone else had the same problem? Can anyone suggest where I should go from here? Any help gratefully received.

Thank you.

---

### Post by Sef on 2008-08-20
Moved to Server Platforms.

---

### Post by louieb on 2008-08-20
Sounds like a bad CD. 
Did you check the md5sum of the iso file? 
Also run the check media for defects option.
When I burn an installation CD I use the slowest speed possible. 2x if available.

It just takes a few twisted bits to give bizarre results.

---

### Post by nashibuntu on 2008-08-21
Yes. I did check the md5. I also checked the integrity if the CD when I burnt it. Thanks for the suggestions though.

After experimenting and reading around the forums, I seem to have managed to overcome the problem. I used acpi=off. I have now partitioned my drives and am at the stage of creating user accounts. All seems okay so far. I hope I haven't spoken too soon...

Cheers,

Paul

---

### Post by nashibuntu on 2008-08-21
Sadly, I did speak too soon.

I successfully reached the stage of completing the installation, having the installation CD ejected and rebooting the computer... but the system has rebooted straight back into the original kernel panic screen and halted.

I'm at a loss now. I guess that I need to make a modification somewhere that will enable the system to boot with acpi=off every time, but where and how? Does anyone know how I could do this (without having to reinstall everything preferably)?

Thank you,

Paul

---

### Post by sahwan on 2008-08-21
i think its about grub

& adding this option try search - i don't have experience in that

---

### Post by DemonBob on 2008-08-21
Edit the kernel line adding acpi=off to it to get it to boot, then once booted

Then edit /boot/grub/menu.lst

Look for something this 

```
title		Ubuntu 8.04.1, kernel 2.6.26-5-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=fd9928bb-780f-436a-9677-db1c502b65e6 ro quiet splash
initrd		/boot/initrd.img-2.6.26-5-generic
quiet

```

add acpi=off to the end of the /boot/vmlinuz line.

---

### Post by nashibuntu on 2008-08-21
Great. That works, thank you very much DemonBob.

The only problem I have now is that acpi is set to off... That's fine in the short term. I can now start setting up services etc., but ultimately do I want advanced power management. I want the computer to choose a low power state when it can because it's going to be on all the time and I don't want to waste energy.

Has anyone else here had similar experiences with a similar motherboard before? If someone uses a similar motherboard and has acpi on, then I'd be grateful to know how they have their bios set-up so that I could try to overcome this problem.

Thanks.

---

### Post by DemonBob on 2008-08-21
The best thing to try first, is grab the latest ubuntu updates. I also would recommend checking for BIOS updates also. 

Good thing is to test it out all you have to do is edit the grubline on boot to take apci=off out.

---

### Post by nashibuntu on 2008-08-21
I have upgraded. There was a kernel update too, but it still doesn't work unfortunately.

---

### Post by DemonBob on 2008-08-21
How about BIOS updates to the board itself?

---

### Post by nashibuntu on 2008-08-21
I have just checked the ASUS website for my motherboard ([http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3A-H/HDMI](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3A-H/HDMI)). The latest BIOS version I can find there is 0703 dated 2008/07/18.

The BIOS I have installed claims to be version 0801 dated 2008/07/29. It's strange that I have a newer version installed than is available on their website.

Paul

---

### Post by windependence on 2008-08-21
You have some serious hardware compatibilty issues here. I have seen this before. Your system unfortunately will probably never be stable under these conditions. I would pull all your peripheral cards and then try it that way. If it's stable that way, then add each card one by one and try each one until you find the one that give you the problem. Of course, it could be a combination of hardware also. In some cases, I have seen where another distro loads fine on hardware that is a no go on Ubuntu. Try OpenSuSE or CentOS if you can't find the problem.

-Tim

---

### Post by nashibuntu on 2008-08-21
Hmm. That wasn't the answer I was hoping for, but it looks like you're pretty experienced so I should heed your advice. To be honest, I don't want to go pulling out bits of hardware. Firstly, I have never done it before and am liable to break something and secondly, it would probably invalidate my warranty. I have just been running through the list of potential candidates:

* standard keyboard. I don't think that's the problem.
* a 17" CRT monitor. That neither
* the CD/DVD drive. That neither
* the graphics card. I don't think that's the problem because I have already set the bios to use the onboard graphics rather than PCI or PCIE and it doesn't make a difference.

* the USB ports
* the sound card
* the card reader
* the processor cooler?

Is it possible to add boot parameters to tell it to tell the kernel just to ignore these devices rather than having to remove the casing and physically unplug them? It doesn't appear possible to control these things from the bios. If not, then your suggestion of trying a different flavour of linux might be the best option for me.

---

### Post by windependence on 2008-08-21
Don't pull the CPU cooler. :)

You would be surprised it may well be the CDROM. I even had a printer once that when plugged in to the USB hosed my entire system. Rare, but it happens.

-Tim

---

### Post by louieb on 2008-08-21
Just to see what happens. Try the generic kernel. 

```
sudo aptitude install linux-image-generic
```

---

### Post by nashibuntu on 2008-08-21
In reply to windependence: Don't worry. I wouldn't dare go anywhere near the CPU cooler.

louieb: Thanks for the suggestion. I performed the update and when prompted I chose to replace the current boot configuration file with the one from the new package. It looked successful, but on rebooting I got the same kernel panic problem. Once again the problem could be overcome by using acpi=off.

Are there any log files that would help diagnose the problem? Would it be useful if I posted var/log/syslog for example?

Paul

---

### Post by windependence on 2008-08-21
Post your dmesg.

-Tim

---

### Post by nashibuntu on 2008-08-21
Here it is.

Paul

---

### Post by windependence on 2008-08-21
Hmmmm...nothing unusual there. Are you sure that's how the log ends? 

It should probably look something like this:

```
Unable to find volume group “VolGroup00”
Unable to access resume device (/dev/VolGroup00/LogVol01)
Mount: error No such device or address mounting /dev/root on /sysroot as ext3
Setuproot: moving /dev failed: No such file or directory
Setuproot: error mounting /proc: No such file or directory
Setuproot: error mounting /sys: No such file or directory
Switchroot: mount failed: No such file or directory
Kernel panic – not syncing: Attempted to kill init!
```

Check and make sure you got all of the dmesg. the messages in front of the kernel panic are extremely important if we are going to fix it.

-Tim

---

### Post by nashibuntu on 2008-08-21
The file posted was generated once I had booted using acpi=off. It's when I don't use that boot parameter that I get the kernel panic crash. I may be asking a naive question here, but since Ubuntu has crashed at that point and I am forced to reboot, how can I obtain the output of dmesg for the crash case?

Thanks,

Paul

---

### Post by windependence on 2008-08-21
OK Paul I read your post again and I need to ask, you are not even able to get the installer to start? So this is just when you are booting from the CD and are trying to install but the installer never starts?

-Tim

---

### Post by nashibuntu on 2008-08-21
Yes. Without using acpi=off, I cannot even get past the first stage of the installation. To be clear, here's how it works in detail:

When starting a fresh install from the CD, the CD launches and I get to the start page, from where I can choose one of several options, such as perform a memory test. At that stage, if I just select the install ubuntu option, accepting the default boot settings, I get a kernel loading bar. As soon as it has reached 100% I get the screen of death with the trace and kernel panic output and the installation proceeds no further. A reboot is required.

If I select acpi=off while at the welcome screen however, the installation runs smoothly up until the point I have to reboot my computer. When the computer boots it does so with the default boot parameters and so crashes out immediately before the stage at which I would have the opportunity to log in with the same error as it did at the start of the installation. To rescue the situation, I have to reboot, hit Escape while grub is loading and manually edit the boot parameters to include the acpi=off.

Doing this allows me to log in normally. Once logged in I can edit the boot/grub/menu.lst file as you described, including the acpi=off command permanently, thus allowing me to boot normally. Removing the acpi=off means that the computer crashes when it reboots.

---

### Post by nashibuntu on 2008-08-22
I discovered that this is a bug that has been known since September 2006 and has been fixed in many previous releases of the kernel. However, it wasn't marked as requiring fixing for version 2.6.24 and so I have now done so:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/63134](https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/63134)

Thanks for everyone's help. windependence, I'll see if I can find out how to add the 'Thank you' tag for you.

I am keeping my fingers crossed that a patch gets released soon...

---

### Post by windependence on 2008-08-22
Your welcome! Glad you found out what it was. Stuff like that can drive you crazy. FYI the thank you button is the little star in the far right hand corner of every post. ;)

-Tim

---

### Post by Ximbiot on 2008-08-22
Please ignore this post.  I was responding to something several pages back thinking I had hit the end of the post.  :)

---

