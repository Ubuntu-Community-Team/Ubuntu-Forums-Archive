---
title: "World of Warcraft won't start (10.04) by using ATI."
date: 2010-07-28
forum: Wine
---

### Post by frostig on 2010-07-28
Hi, 

I have a kind of annoying and what it seems like unusual problem while trying to play the game World of Warcraft. I think I have done everything that people have recommended others to try out, have been googling around for some hours now.

My graphic card is: ATI Technologies Inc Radeon HD 4770 [RV740] and I have installed the drivers for it. The funny thing is that my brother uses the exact same graphic card and for him it worked out of the box, we even installed ubuntu from the exact same CD.

Can it be anything else in my hardware maybe that changes from his?

My entire hardware list:

```
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 4770 [RV740]
02:00.1 Audio device: ATI Technologies Inc RV710/730
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```



The output by running Wow.exe is the following:

```
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\enGB\patch-enGB-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x192ee20,0x00000000), stub!
```

And there it stops, it starts a process named Wow.exe and doesn't do anything more. 
```
2382 ?        00:00:02 WoW.exe
```
This is incredible annoying. What follows now is a list of things that I've tried (in no particular order):

- Disabling Compiz
- Changing the xorg.conf
- Enabling openGL mode for wow, and everything else that should contain in the config.wtf to run smoothly.
- Made that regedit fix.
- Crying out loud and get angry
- Updating wine to developer version
- and a lot more I cant remember, even did unplug the ethernet cable.. and now I'm probably going to reinstall the ****ing piece of crap and see if it's gonna work. (I wonder why blizzard didn't release a native linux client (they had one in the beta atleast..)).

This is my xorg-config:


```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual	3200 1080
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

 Section "Device"
   Identifier  "aticonfig-Device[0]"
   Driver      "fglrx"
   Option       "Capabilities" "0x00000800"
   Option       "UseFastTLS" "off"
   Option       "KernelModuleParm" "locked-userpages=0"
 EndSection

```

This is a new clean install of ubuntu and I can't get this working. The thing is everything else works, I run spotify over wine (music streaming application). Althrough steam seems to not be able to update itself everything else seems to work.

I really don't want to run windows and I'm getting really annoyed at these small problems you have every time you want to change system for good. Right now, if I got this to work I would never need a windows system and my world would be saved!

Peace,
Frostig.

---

### Post by frostig on 2010-07-28
Btw, wine flickers for like 1-2 seconds before starting any program. This includes WoW.

---

### Post by frostig on 2010-07-29
New update: HoN doesn't even run thou it's a native client! The screen is just all black and I don't know why. Maybe there is need for some changes to the graphics-config.

---

### Post by asdfoo on 2010-07-29
are you using wine-1.2?
open a terminal and type `wine --version`

also, there was a recent kernel bug affecting Blizzard products due to the copy protection they use.
please also type `uname -a`

---

### Post by frostig on 2010-07-29
> **asdfoo said:**
> are you using wine-1.2?
open a terminal and type `wine --version`

also, there was a recent kernel bug affecting Blizzard products due to the copy protection they use.
please also type `uname -a`

Yes, I use wine 1.2:

```
markus@solaris:~$ wine --version
wine-1.2

```

But I noticed something really strange now, I googled my graphic card and found some report for it under linux and when I did chek my status for it, the GPU load seems to be working really really hard:

```
Default Adapter - ATI Radeon HD 4770
                            Core (MHz)    Memory (MHz)
           Current Clocks :    750           800
             Current Peak :    750           800
  Configurable Peak Range : [500-830]     [800-850]
                 GPU load :    99%

```

I wonder why it sais that my GPU have 99% load since I'm not using anything in particular. I even tried to put my visual effets by compiz back to 'normal' and it still is at 99% load.

Source for the article is availble here: [http://www.phoronix.com/scan.php?page=article&item=amd_hd4770&num=5](http://www.phoronix.com/scan.php?page=article&item=amd_hd4770&num=5)

Maybe this has something to do with it?

EDIT: I am using dual screen btw (I have tried to unplug it..).

EDIT again: I can't even start quadrapassel, it freezes and I have to force it to quit.

---

### Post by frostig on 2010-07-30
New information that I can't understand really. Fail to init opengl32.dll? What does that mean?

^Cerr:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\Wow.exe" failed, status c000013a

---

### Post by srlake314 on 2011-04-05
wondering if anyone has fixed this?  I know I still have disembodied armor and no NPCs.  the sound cracks from time to time, but that is it.  Not even going to get into playing wow on my second screen.  At this point, I'd just like to get wow to work on my new pc.

---

### Post by cwwilson721 on 2011-04-05
A few things to do:
[LIST]
[*]Disable Compiz. (ALWAYS. I use the Compiz Fusion Icon for that)
[*]Only run in opengl mode (add '-opengl' to end of command to launch WoW. After you do this, WoW will add the correct line in config.wtf to always use opengl. But I use the addendum anyway just to make sure))
[*]Uninstall the Ati/AMD drivers, and reinstall them thru System > Administration > Additional Drivers.
[*]Disable sound. (This used to be a major issue. Sometimes sound really messes with the graphics in WoW/wine. Try disabling it to see if that helps)
[/LIST]

Now...

What graphics card/chip are you uising? Is it supported by the latest AMD/Ati drivers? If not...

---

### Post by Dlambert on 2011-04-08
Update drivers and update Wine to 1.3

---

