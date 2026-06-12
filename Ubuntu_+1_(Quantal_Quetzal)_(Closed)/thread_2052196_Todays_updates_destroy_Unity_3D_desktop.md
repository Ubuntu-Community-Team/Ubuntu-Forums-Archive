---
title: "Todays updates destroy Unity 3D desktop"
date: 2012-09-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-09-02
Just updated an install that took me two weeks to fix with nvidia/neywork problems. Got that all fixed , then , updated just now, and now Unity 3D is gone. LightDm only and background wallpaper with compiz-errors to report but apport will not report , why , because no desktop.! etc..

```

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:03.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
d

```

---

### Post by fjgaude on 2012-09-02
Lots of bugs, but Thursday the first Beta comes out... I'm sure much will happen between now and then.

---

### Post by kansasnoob on 2012-09-02
Not surprising :(

For quite some time now they've started "early" iso-testing on the Friday prior to the next milestone, but NOT this time.

Based on bits of chatter here and there I think some last minute kernel and xorg updates are in the works.

The box I usually use for testing installation options is a total no-go ATM:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625)

Lots of fun ahead :lolflag:

---

### Post by ventrical on 2012-09-02
> **kansasnoob said:**
> Not surprising :(

For quite some time now they've started "early" iso-testing on the Friday prior to the next milestone, but NOT this time.

Based on bits of chatter here and there I think some last minute kernel and xorg updates are in the works.

The box I usually use for testing installation options is a total no-go ATM:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625)

Lots of fun ahead :lolflag:

Thats probably it. Thanks.

---

### Post by ventrical on 2012-09-03
Apport finally coughed up a xorg/nvidia bug report.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1045197](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1045197)

---

### Post by ventrical on 2012-09-03
btw .. just adding on here ... it was the compiz  updates which did the worst I think.  I am writing this from fvwm-crystal DE which seems to be the only one to work right now. ( A real trustworthy workhorse indeed.)

 All compiz settings were wiped out from CCSM. Trying to set them manually did not fix the problem .. but it did bring back  that olde bug form PRecise days when we were  getting those distorted screens just after logging in from lighdm.

---

### Post by jerrylamos on 2012-09-03
> **ventrical said:**
> btw .. just adding on here ... it was the compiz  updates which did the worst I think.  I am writing this from fvwm-crystal DE which seems to be the only one to work right now. ( A real trustworthy workhorse indeed.).Oops.  I'm set to log on automatically which has been working fine.  If Unity/Compiz is dead can't log out/log in to a working desktop LXDE in my case.  I don't know fvwm-crystal DE?  

So quick switch to mandatory log in before doing update/upgrade so I can switch desktops before disaster.  

Thanks for the hint!

Jerry

---

### Post by ventrical on 2012-09-03
> **jerrylamos said:**
> Oops.  I'm set to log on automatically which has been working fine.  If Unity/Compiz is dead can't log out/log in to a working desktop LXDE in my case.  I don't know fvwm-crystal DE?  

So quick switch to mandatory log in before doing update/upgrade so I can switch desktops before disaster.  

Thanks for the hint!

Jerry

fvwm-crystal can be found in the repos synaptic. It is a really light DE. *fvwm* has been around for a long time.. even before Gnome I think. Iv'e tested it quite a bit. It removes cleanly .. but is always able to login when the breakage hits the fan :)

**Yes.. LXDE works awesomely in several cases when Unity/Gnome will not work.

fvwm-crystal does not depend on compiz either.

---

### Post by grahammechanical on 2012-09-03
@ventrical

Thanks for mentioning fvwm-crystal. I have just tried it out on one of my quantal installs.

I have been looking for an alternate DE to log into when the Unity desktop breaks. I tried LXDE and XFCE. There are fine. I have no wish downgrade the work being done there but for my purpose I think they bring in to much other stuff.

All I want is to get to a desktop to run updates, that might or might not fix the problem, or some some of those sudo codes of yours.

Thanks again.

Regards.

---

### Post by ventrical on 2012-09-03
> **grahammechanical said:**
> @ventrical

Thanks for mentioning fvwm-crystal. I have just tried it out on one of my quantal installs.

I have been looking for an alternate DE to log into when the Unity desktop breaks. I tried LXDE and XFCE. There are fine. I have no wish downgrade the work being done there but for my purpose I think they bring in to much other stuff.

All I want is to get to a desktop to run updates, that might or might not fix the problem, or some some of those sudo codes of yours.

Thanks again.

Regards.

 Thanks for bringing this up.  From my own experience  LDXE and XFCE have a tendency to break lighdm and corrupt the transition process from from login to Unity DE. Honestly, Iv'e tried and tried but there is always this breakage with those two DEs , even with LTS !!

   Yes.. as a tester DE, fvwm-crystal will work when gnome(no-effects) will not. I try to load it on all my installs because when breakage happens I can always log in to fvwm, get to synaptic and terminal at least, and firefox also. Saves a lot of brain work from terminal :)

---

### Post by scradock on 2012-09-03
Just looked at installing fvwm-crystal. It tries to bring in a whole bunch of other stuff - audacious, for what? If I'm adding in a window manager just to be able to close down when lightdm breaks I surely don't need someone else's favorite audio player....

---

### Post by mc4man on 2012-09-03
Didn't see any issue when upgrading compiz/unity here the other day from proposed
 - other then a few custom compiz settings where lost as was the run history. (gsettings & ccsm don't always seem to communicate well..

Do get a kick out of your bug report which now has been duped to a 2 week old bug marked 'incomplete' & was on an intel display adapter

---

### Post by ventrical on 2012-09-03
> **mc4man said:**
> Didn't see any issue when upgrading compiz/unity here the other day from proposed
 - other then a few custom compiz settings where lost as was the run history. (gsettings & ccsm don't always seem to communicate well..

Do get a kick out of your bug report which now has been duped to a 2 week old bug marked 'incomplete' & was on an intel display adapter

Yes .. thats it exactly .. settings were lost. Perhaps I over-reacted.  I want to believe that apport is making authentic reports - so I am just really going with the flow.

---

