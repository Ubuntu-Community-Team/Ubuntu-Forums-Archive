---
title: "getting an m-audio 24/96 installed on Ubuntu 10"
date: 2012-02-06
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-02-06
(1)  I have plugged in an m-audio 24/96 card into the PCI slot.

(2)  I have disabled the onboard audio in the BIOS. 

(3)  I have booted up into Ubuntu 10 (with Ubuntu Studio installed). 

(4)  I tried a youtube video: no sound.

(5)  I tried running JACK control, and the new card does not show up, only the RPx400 (still plugged in).

(6)  Not sure what to do next.

I have opened a terminal and tried aplay, arecord -l:

> [HTML]~# aplay -l
**** List of PLAYBACK Hardware Devices *
***
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 # 

 # arecord -l

**** List of CAPTURE Hardware Devices ****
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 ~# [/HTML]

What is the next step?

---

### Post by nazaroo2 on 2012-02-06
Here is a dump from lspci (idea from previous thread):

```
root@unknown:~# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 0a)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 0a)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)
03:02.0 Multimedia audio controller: 
[COLOR=Blue]**VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)**[/COLOR]
root@unknown:~# 

```


Here is the "modules state":

```
~# sudo lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: ioport:cca0(size=32) ioport:cc80(size=16) ioport:cc90(size=16) ioport:ccc0(size=64)
root@unknown:~# 
```

---

### Post by sgx on 2012-02-07
sudo modprobe snd_ice1712

run lsmod command, to see if it is now in the list.

Cheers

---

### Post by nazaroo2 on 2012-02-07
Okay I ran  the command.
Here is the result, it doesn't look good:
```

~# sudo modprobe snd_ice1712
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.added-maudio, it will be ignored in a future release.
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.32-38-generic-pae/updates/alsa/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.32-38-generic-pae/updates/alsa/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1712 (/lib/modules/2.6.32-38-generic-pae/kernel/sound/pci/ice1712/snd-ice1712.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 ~# 
```

results from 
sudo lshw -C multimedia  remain  unchanged.

```
 ~# sudo lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: ioport:cca0(size=32) ioport:cc80(size=16) ioport:cc90(size=16) ioport:ccc0(size=64)
 :~#

```

---

### Post by jejeman on 2012-02-07
Since you are root, you don't need to use "sudo".

---

### Post by nazaroo2 on 2012-02-07
> **jejeman said:**
> Since you are root, you don't need to use "sudo".

I presume using sudo did no harm...?

In any case, do you have any idea why the module didn't load?
Or why there were error/warnings when I tried to load it?

The ***envy24control module*** seems to be installed/working, because it returns a value:

```
# **[COLOR=Blue]envy24control[/COLOR]**
[COLOR=Red]No ICE1712 cards found[/COLOR]


 ~# **[COLOR=Blue]modprobe snd_ice1712[/COLOR]**
[COLOR=Red]**WARNING**: All config files need .conf: /etc/modprobe.d/alsa-base.conf.added-maudio,
 it will be ignored in a future release.

**WARNING**: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.32-38-generic-pae/
updates/alsa/snd-ak4xxx-adda.ko): [B]
Unknown symbol in module[/B], **or unknown parameter** (see dmesg)

**WARNING:** Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.32-38-generic-pae/
updates/alsa/snd-ice17xx-ak4xxx.ko): 
Unknown symbol in module, or unknown parameter (see dmesg)

**FATAL:** Error inserting snd_ice1712 (/lib/modules/2.6.32-38-generic-pae/
kernel/sound/pci/ice1712/snd-ice1712.ko):
 Unknown symbol in module, or unknown parameter (see dmesg)[/COLOR]

[COLOR=Blue] ~#[/COLOR] 
```It looks like some value, reference, or variable / handle has been broken in some version or update of some file that is trying to load or compile.

---

### Post by nazaroo2 on 2012-02-07
In searching over old posts, ***[I found this:]("http://ubuntuforums.org/showthread.php?t=1540891")***

> **Jblock312]                                  **Re: Help with M-Audio Delta Audiophile 2496 setup**             
                                                                Like you, I've been trying to get my delta 2496 card working with a recent install of Ubuntu 10.04.
It used to work fine in 9.04.
One of the threads you probably read is:
[https://bugs.launchpad.net/ubuntu/+s...o/+bug/178442/]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/")

go to #30 in the thread, then in your terminal window type:
[COLOR=Blue]gksudo gedit  /usr/share/alsa/cards/ICE1712.conf[/COLOR]
(make sure to leave a space between "gedit" and "/usr")

when the text window comes up, scroll down to "ICE1712.pcm.front.0"
add 2 lines at the bottom, as listed in #30:
[COLOR=Blue]
slave.format S32_LE
slave.channels 10[/COLOR]

save, close and reboot.
Now go to system>preferences>sound, look up the delta and you should now have analog options.

Worked for me. Good luck.
                                                                                                                                    *                                              Last edited by jblock312 said:**
> 

In the same thread later Ruhani04 posted:

[QUOTE]This is in reference to 10.10 beta (maverick meerkat) and audiophile 24/96:
I already filed a bug report but I am pretty sure nothing will come out  of it as this is a known problem for many years with pulseaudio and  nothing has changed.
In 10.04 there has been posted in a previous bug report a workaround. However this seems to no longer work in 10.10.
**In my opinion there are two solutions:**
[COLOR=Blue]*Disable or remove pulseaudio and only use ALSA.*[/COLOR] This has worked for me and all applications are supported with great sound.
[COLOR=Blue]*Or disable or remove pulseaudio and install OSS4.*[/COLOR] Worked for me but not  all applications fully support OSS4. This is definitely a more  complicated approach.
[COLOR=Blue]*I have **no **experience with **Jack **and therefore can't say if this would be a third solution.*[/COLOR]:wink:[B]
Can anyone comment on whether I should try any of these ideas, 
or what ideas from these posts would be helpful here?[/B]

---

### Post by nazaroo2 on 2012-02-07
also, when I do [COLOR=Blue]cat /proc/asound/cards [/COLOR]I get this:

```
:
~#[COLOR=Blue] cat /proc/asound/cards[/COLOR]

[COLOR=Red]--- no soundcards ---[/COLOR]
 ~#

 ~# [COLOR=Blue]aplay -l[/COLOR]

[COLOR=Red]aplay: device_list:223: no soundcards found...[/COLOR]
 ~#


~#[COLOR=Blue] asoundconf list[/COLOR]
[COLOR=Red]asoundconf: command not found[/COLOR]
 ~# 


```

Trying to install the ASOUND program fails:

```

~# [COLOR=Blue]**sudo apt-get install asound**[/COLOR]
[COLOR=Red]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package asound[/COLOR]
 ~# 

```

---

### Post by nazaroo2 on 2012-02-07
I decided to go ahead and try patching ICE1712.conf:

> 
***[COLOR=Blue]gksudo gedit  /usr/share/alsa/cards/ICE1712.conf[/COLOR]***
(make sure to leave a space between "gedit" and "/usr")

when the text window comes up, scroll down to "ICE1712.pcm.front.0"
add 2 lines at the bottom, as listed in #30:
[COLOR=Blue]
slave.format S32_LE
slave.channels 10[/COLOR]

save, close and reboot.
Now go to system>preferences>sound, look up the delta and you should now have analog options.


It now looks like this in the relevant section (lines 29-45):

```


ICE1712.pcm.front.0 {
    @args [ CARD ]
    @args.CARD {
        type string
    }
    type route
    ttable.0.0 1
    ttable.1.1 1
    slave.pcm {
        type hw
        card $CARD
    }
[COLOR=Red]        slave.format S32_LE
        slave.channels 10[/COLOR]
}    


```I will try rebooting as advised....

---

### Post by nazaroo2 on 2012-02-07
The card is definitely recognised by SOME part of the system, because its listed here:

```
:~[COLOR=Blue]**# lspci**[/COLOR]
[COLOR=SeaGreen]
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 0a)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 0a)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)[/COLOR]
[COLOR=Red]**03:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)**[/COLOR]
~# 
```

---

### Post by nazaroo2 on 2012-02-07
After Rebooting, 

```
~#  **[COLOR=Blue]sudo lshw -C multimedia[/COLOR]**
  [COLOR=Blue]*-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product:** ICE1712 [Envy24] PCI Multi-Channel I/O Controller**
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: ioport:cca0(size=32) ioport:cc80(size=16) ioport:cc90(size=16) ioport:ccc0(size=64)[/COLOR]
root@unknown:~#
```So the card is still there, but no drivers.

Going to **[COLOR=Black]System/Preferences/Sound [/COLOR]**

just gives a dialog box:  [COLOR=Blue]"Waiting for sound system to respond..."



Trying to activate the ICE1712 module seems to fail:

```

~# sudo modprobe snd_ice1712
[COLOR=Red]WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.added-maudio, it will be ignored in a future release.
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.32-38-generic-pae/updates/alsa/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.32-38-generic-pae/updates/alsa/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1712 (/lib/modules/2.6.32-38-generic-pae/kernel/sound/pci/ice1712/snd-ice1712.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/COLOR]
 ~#

```
[/COLOR]

---

### Post by nazaroo2 on 2012-02-07
Finally, the envy24control program seems to be installed and working, 
because it returns the same value: (no card found).

```
# [COLOR=Blue]**envy24control**[/COLOR]
[COLOR=Red]No ICE1712 cards found[/COLOR]
 ~# 
```

[B]Given that the card is perfectly recognizable and works in Ubuntu 11.10,
 why can't we get it working here?[/B]

---

### Post by Sylos on 2012-02-07
Im by no means well versed in such things but the error you are getting would appear to suggest that something is missing from the kernel side to allow it to understand the module.

What kernel are you running and what alsa version? Have you installed anything additional (kernel, latest alsa etc)?

Cheers

---

### Post by nazaroo2 on 2012-02-07
> **Sylos said:**
> Im by no means well versed in such things but the error you are getting 
would appear to suggest that something is missing from the kernel side to allow it to understand the module.

What kernel are you running and what alsa version? Have you installed anything additional (kernel, latest alsa etc)?

Cheers


Ok, according to the **System Monitor**, I am running:

[COLOR=Blue][B]Release 10.04 (Lucid)
Kernel Linux 2.6.32-38-generic-pae
GNOME 2.30.2
[/B][/COLOR]
According to the **Synaptic Package Manager**, I am running:

alsa-base ............................. 1.0.22.1+dfsg-0ubuntu3 (= latest version)
alsa-utils ..............................1.0.22-0ubuntu5 (= latest version)
linux-backports-modules-alsa......2.6.3: 2.6.32-38.39 (=latest version)

all other ALSA related pkgs appear to be the latest, at least latest 'stable', according to SPM.

As for third party drivers, like the actual version of **envy24control,** I don't know, 
since it won't load without finding a card.

It is possible that an** alternate kernel **got blended in 
when I installed **Ubuntu Studio** (e.g. a realtime RT kernel),
but I see no sign of this, nor do I know a way to check...

---

### Post by Sylos on 2012-02-07
Hmm. Interesting.

I have US 10.04 installed on my rig and I use an M-audio Delta 66 card using the same ICE1712 chipset and it works fine without issue. For interest it may be helpful to try using the generic kernel that ships with the distro rather than the PAE and see if that makes a difference. You should be able to load it from GRUB if you havent deleted the previous kernel entries.

Also, I would expect that your error about "waiting for sound system..." is related to pulseaudio. It never plays nice in my experience. I just removed pulse completely and use only ALSA for my studio set up. It stops a number of issues that CAN be worked around but I chose not to bother (my studio install is specifically for audio recording so I dont need it).

Cheers

---

### Post by nazaroo2 on 2012-02-07
I went to uninstall the PAE kernel using Synaptic.

I discovered after removing it (it was highlighted red) that it may still be installed.
All the packages are still there.

While browsing in Synaptic for "kernel", I noticed that there are two versions of 
the generic pae  I think:

linux-headers-generic-pae (2.6.32-38.44) and,
linux-headers-2.6.32-38-generic-pae   (2.6.32-38.83) <-- newer.

Maybe I don't understand the meaning here.

There is also a linux-rt (2.6.31.11.13) also 'installed', so I don't even know 
which of the two (or three) is the one running. 

In my GRUB boot, only two choices seem available:

(1) 2.6 .... (i.e., Linux 10.04), and 

(2) 3.0  .....(i.e., Linux 11.10) 

- other than 'recovery' versions, as options on the menu.

How would I go about selecting the different kernels if they are not on the menu,
and how would I put them on the menu if that is required?

Maybe I shouldn't have tried to remove the PAE kernel without a plan...
I haven't closed Synaptic yet, so I'll just leave everything open until you respond..

---

### Post by Sylos on 2012-02-07
Ah - Sorry, my bad - I should have been clearer.

You didnt need to uninstall the PAE kernel - just select a different one from the GRUB menu when you restarted. Hopefully it wont make much of a difference that you have uninstalled it anyway. You can always reinstall again.

I assume you must have installed the PAE kernel after you installed the OS as I dont think it comes on the  ISO image. Correct me if thats wrong. What we want is to try a non-PAE kernel to make sure it isnt anything to do with the PAE version itself. So if the others in the GRUB menu are non-PAE then give them a try. If you want you can install the RT Kernel and give that a shot (I use it). I will advise of the caveat that it isnt an up to date kernel (or wasnt when I installed it) and there is some kind of issue with where other drives are mounted to - something to do with a change from /media to /dev or vice versa. It didnt cause me any issues other than a brief failure note during boot - it then falls back to whatever the fallback is and all drives are present. I mention it because if you have set up other drives through fstab etc it may cause issues with that.

You can install another generic non-pae kernel if need be - just get the latest one. Booting into a different kernel wont cause you any damage (at least not in my experience).

---

### Post by Sylos on 2012-02-07
Just re read your post.

Was that the only 10 kernel you had. If so install one again before you shut down/restart.

EDIT: Make sure to update grub before you shutdown. If you have deleted the only kernel for that version of ubuntu then it will not load unless grub is aware of then new one.

---

### Post by Sylos on 2012-02-07
I have to bail for the night.

I'll check back in the morning.

Cheers

---

### Post by sgx on 2012-02-07
If it works in V11, you are wasting precious time trying to
make it work in V10. Music doesn't care about the version,
nor do those who would listen to it. :popcorn:

---

### Post by jejeman on 2012-02-07
> so I don't even know which of the two (or three) is the one running. Command to check running kernel is
```
uname -r
```

---

### Post by nazaroo2 on 2012-02-07
> **Sylos said:**
> Just re read your post.

Was that the only 10 kernel you had. If so install one again before you shut down/restart.

EDIT: Make sure to update grub before you shutdown. If you have deleted the only kernel for that version of ubuntu then it will not load unless grub is aware of then new one.

Yes; apparently you have assisted me in trashing my system.

And once again you have left behind instructions dangerously and annoyingly vague.

If I must update GRUB before shutting down, kindly*** tell me how.*** [rolls eyes, curses]

But please start first with ***telling me how to re-install my kernel*** if you can.
Preferably by using Synaptic. 

Otherwise I think I will have to write off your posts as worse than useless, and just label them toxic hazards, for other poor souls who happen to wander here.

---

### Post by nazaroo2 on 2012-02-07
> **jejeman said:**
> Command to check running kernel is
```
uname -r
```

Thank you again Jejeman, for posting something useful at least.

```
~# **[COLOR=Blue]uname -r[/COLOR]**
**[COLOR=Red]2.6.32-38-generic-pae[/COLOR]**
 ~# 
```

This looks like the thing I must re-install safely and completely, 
to prevent me losing my entire distro now.

On the other hand, this could also be the thing that is preventing the card from being found.

In any case, I obviously must properly re-install SOME kernel reliably, before shutting down.

Any real and accurate help would be greatly appreciated.
I still have Synaptic open, and a terminal. 

I have no idea how to configure GRUB.
The last time I even heard that name was back in 2004,
when I was trying to install Gentoo as a dual boot with Windoze,
while Microsoft was actively sabotaging any and every dual-boot attempt.
I think I wasted about 6 months of my life on that project destined for failure.

---

### Post by nazaroo2 on 2012-02-07
> **sgx said:**
> **If it works in V11,** [B]
you are wasting precious time trying to
make it work in V10.[/B] 

Music doesn't care about the version,
nor do those who would listen to it. :popcorn:

You're kidding me, right?
Much as I appreciate your help here, given you are one of the more knowlegable and accurate assistors, 
I must point out that this is not logical, nor practical.

Conclusion B simply does not depend upon Premise A. 

the 'music' may not care, but **the user** (me) ***does.***
Lets see why:

(1)  I have spent the last 5 years learning and using Linux, From Gentoo, to Ubuntu.   **I simply can't afford to scrap all my training and work-habits and once again re-learn** yet another totally alien system and orientation, only to adopt the worst piece of pure crap I have ever had the misfortune of having to attempt to make useful [i.e., Ubuntu 11]

(2)  I have in the last five years hit the absolute peak of my productivity in scientific research using these tools, and culminating in at least a 5x increase over the last two years because of dual screens alone.  **I will NEVER take a step backward in productivity ever again.**  If they can't scrap Ubuntu 11 and make a version 12 as productive and useful as 10, Ubuntu and I will have to say goodbye.  **Meanwhile, I must continue to use 10**.

(3)  I am _***not***_ primarily a 'musician' or a sound-engineer.  I will use Ubuntu 11 if I must to record music, but this changes NOTHING.  I MUST HAVE Ubuntu 10 running to do the vast bulk of my productive work, which has nothing to do with music.  And I see no reason NOT to have Ubuntu 10 working with SOUND, using the card I just purchased, whether or not I ever use Ubuntu Studio to record music on my Ubuntu 10 OS.  And since I will be doing most of my daily work in Ubuntu 10, **it is not unreasonable to want sound and music, including youtube videos etc. to be WORKING PROPERLY.**

(4)  Finally, MOST users of 10 will want to keep it and not have to switch to 11.  Therefore, its worthwhile to find out how to make it work in 10, so that all those others (the vast majority of Ubuntu users) can keep 10.

---

### Post by nazaroo2 on 2012-02-07
Machine rebooted OK (thank God), but no sound card is installed, nor apparently drivers.

lspci still shows card sitting there.
aplay says non found.

---

### Post by sgx on 2012-02-07
If you must dual boot a second linux, use AVlinux, the developer
uses 2 mAudio sound cards at once, and has produced a very nice
audio/video distro.

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

---

### Post by sgx on 2012-02-07
> **nazaroo2 said:**
> 
the 'music' may not care, but **the user** (me) ***does.***
Lets see why:

(1)  I have spent the last 5 years learning and using Linux, From Gentoo, to Ubuntu.   **I simply can't afford to scrap all my training and work-habits and once again re-learn** yet another totally alien system and orientation, only to adopt the worst piece of pure crap I have ever had the misfortune of having to attempt to make useful [i.e., Ubuntu 11]

 
The best software and GUIs are easy to install on most linux setups,
so one need not abandon the look and feel they are accustomed to.
I use E17 gui on each linux, different as they may be. Workflow
is much the same.

The reality is that every computer is different, in hardware
or system configuration. Each version of linux has a purpose, and its
authors a mission. Users without 'a match', should move on to different
hardware, improved configuration, or a different linux version.
Sometimes all three.

The resources are not there to support the wide range of hardware,
and newer is often supported last. Every linux has it's share of frustrated users, where some element was a brick wall. So we stick
together and work through the difficulties, and all learn more in the
process.  :)

---

### Post by Sylos on 2012-02-08
> **nazaroo2 said:**
> Yes; apparently you have assisted me in trashing my system.

And once again you have left behind instructions dangerously and annoyingly vague.

If I must update GRUB before shutting down, kindly*** tell me how.*** [rolls eyes, curses]

But please start first with ***telling me how to re-install my kernel*** if you can.
Preferably by using Synaptic. 

Otherwise I think I will have to write off your posts as worse than useless, and just label them toxic hazards, for other poor souls who happen to wander here.


Ok, first off I will apologise if attempting to follow my advice has lead you into some trouble. BUT.... I did not tell you to delete your kernel in the first place. If you were unsure of what I meant then you should have asked before deleting it. You have been posting quite a lot of code output and discussing installing varying items so I assumed (incorecctly it would seem) that you had a fairly basic knowledge of how to select the kernel to boot into and how to uninstall/install packages from synaptic. You even said yourself that you have uninstalled the kernel through synaptic so its reasonable to assume that you can do the reverse procedure and reinstall it using synaptic.

I tagged on the caveat about updating grub  for the following reason: Grub would normally but auto updated when a new kernl is installed but having removed what maybe your only kernel I wanted to make sure that you did a manually update of grub to be sure you didnt loose your only access into the system (not that it would have been an unresolvable problem if you had but why make more problems).

Again I apologise if you have ended up somewhere you did not want to be but to label my advice as 'toxic' to users is going way too far here.

If you really want to pursue the possibility of whether the kernel is the problem (and it may not be) you should boot up and do the following:

1. ```
uname -r
```

2. If you are still running the pae kernel (as shown from the output of the above command) Open Synaptic and install another kernel. For the sake of this testing I would pick the latest generic kernel that does NOT have pae after it (Im not at my ubuntu machine right now so I cant give you an example from my system - if in doubt, ask). dont remove the existing kernel - you will be able to choose from grub which to boot into.

3. Reboot into the new kernel.

4. Attempt to input the relevant module for the card.

5. Post whatever output you get back here in the forum.

As a final note I would have to agree with sgx - if you have it working on another distro why bother fiddling with this one trying to get it to play ball. You could be spending time making music.

---

### Post by nazaroo2 on 2012-02-08
Thanks for making the effort to give the additional details.

I also have something remarkable to report, although I haven't fully check this out yet.

Previously, I had run JACK using the onboard sound card in Ubuntu 10.

I had not fully appreciated just what was built into this box.

The Dell Optiplex 330, and probably the whole line of boxes, 

has an Integrated ADI 1984 High Definition Audio system built onto the motherboard.

I just got the tech specs on this Audio system:

High Def Stereo Support : YES
Number of channels : 2
Number of BITS / Audio Resolution:  **16, 20, [COLOR=Red]and 24 BITs[/COLOR]**
Sampling Rate (for record/playback):  [COLOR=Red]**up to 192 kHz**[/COLOR]
Signal to Noise Ratio:......................[COLOR=Black]** 96 db**[/COLOR]
Analog Audio : YES
Microphone:  1k-2k ohm
Line In: > 10K ohm
Line Out: > 10K ohm
Headphone:  16-500 ohm 

The microphone and line in use the same mini-jack on the back of box.

These specs look about as good as I can find on any PCI plug-in card.
[B]
The reason I missed this was, I always buy bargain-bin used computers.[/B]
These boxes were marketed for corporation/office use,
 and when they were traded in, the small-time vendors reselling them 
just assumed they were office junk and priced them at $100-200 per box.
It is true they come with a minimal graphics card onboard, that doesn't do dual screens. 
So people probably thought these would require buying a graphics card,
only to make them into a mediocre game-box. 
I got them for the price, and bought an old nVidia card for dual screens,
without even checking how good they were.

**But for music, these are real 'sleepers'! **
You have the built-in 24/192 kHz soundcard,
and fast SATA drive support, along with dual processors 
and the ability to run a 64-bit operating system!
The physical box is extremely quiet, and well designed.

The only disadvantage is the relatively 'poor' S/N ratio (96 db),
presumably because it is 'onboard',  
But now I'm going to see if JACK can use the 'record' function,
and also if I can set the sample rate to either 96 or 192 kHz.

Maybe I don't need a Soundcard at all.....!!!

---

### Post by sgx on 2012-02-09
Only a bat would benefit from 192khz, and the processor
that would handle 24/192 on multiple tracks, would not be cheap.

The A/D  D/A convertors are crucial to quality sound, and not cheap to put on a motherboard, so they usually wind up on soundcards.

Britney was furious to discover that the 64 bit studio
she demanded and paid for, still produced 16 bit music, that iTunes turned into cheap cardboard replicas.
Life is hard sometimes ;)

If the motherboard audio meets your needs, any other assets can be
liquidated. :)

---

### Post by nazaroo2 on 2012-02-09
***Updated Report:***

After discovering that my ONBOARD sound was probably as good a quality as any outboard card (24/192 kHz, -96 db noise floor), 
I tried to see if the RECORD inputs to the ONBOARD were working,
even with the m-audio plugged in, by re-enabling the onboard sound in the BIOS.

(1) The onboard sound system seems to work fine,  I am able to record / monitor whatever is plugged into it, using JACK (using **Ubuntu 11**  <--).

(2) However, even though JACK says its aware of the m-audio PCI card, it can't use it while the Onboard is enabled in the BIOS.  No sounds go in or out.

That looks like the size of it for Dell Optiplex users.  They can use their onboard sound if they want to, 
but extra sound-cards plugged in will not work properly as long as the onboard sound is enabled in the BIOS.

You may be able to avoid buying a sound card: 
but if you do buy one and install it, 
you'll have to disable the onboard one in the Dell BIOS.

Fo[COLOR=Red]***r Ubuntu 10 ***[/COLOR]users however, the news is sad and ironic.

(1)  Although the onboard card "works",  It seems to 'hardware' itself  to its own output, even when disconnected from it in Patchage.   Thus  you can't turn off sound being sent into the ONBOARD system, or re-route  it into Ardour for instance, and control it. 

(2)  As with Ubuntu 11, **Ubuntu 10** users won't be able to access  an m-audio PCI card either, whether or not the OS or JACK thinks it sees  it.  This could be a combination of not having working drivers  available, and/or the OS being unable to initialize the card(s)  properly. 

Bottom line: I couldn't get the onboard system to work with JACK properly** in Ubuntu 10**, at least with another card plugged into a PCI slot, although it can be made to work in Ubuntu 11.

These are mainly issues for dual-boot users, and/or those who don't want to upgrade to Ubuntu 11.
The Patchage patchbay seems to work properly generally in Ubuntu 11,  (i.e., disconnecting sound through-put when System Input is re-routed),  although you can't access both onboard and outboard systems at once.


The verdict concerning the** Dell Optiplex 330 **etc. is still the same however: great!
Its an awesome box, well-suited to audio purposes, if you choose a working OS and install software/hardware properly.

---

### Post by sgx on 2012-02-09
> **nazaroo2 said:**
> 
(2) However, even though JACK says its aware of the m-audio PCI card, it can't use it while the Onboard is enabled in the BIOS.  No sounds go in or out.

You can create a textfile called blacklist, in /etc/modpobe.d
It blocks kernel modules that support undesired components.
My motherboard sound gets in the way, so my blacklist file
contains 1 line

blacklist snd_intel8x0

Sometimes one may want a device in one linux, but not another,
this way, the bios can be left alone. There is a way to use
more than 1 soundcard at once for input devices, but it's classified
top secret information. Unless google can't keep a secret. :)
Cheers

---

