---
title: "Guest additions for virtualbox using windows 98"
date: 2007-12-29
forum: Virtualisation
---

### Post by IanB2 on 2007-12-29
I've been using Virtualbox for all my Linux VMs and I'm very impressed with the package. I'd like to be able to run windows 98 in a VM but have been unable to alter the screen resolution from the basic 480 x 600 .

It would appear that the usual way of doing this is using 'guest additions', but as I understand there are none for windows 98??

Is there a way around this so I can achieve a modest 600 x 800 screen resolution?

---

### Post by Eck on 2008-01-01
Use Sci-Tech Display Doctor version 7 beta.  Major Geeks has it.  Go to the Sci-Tech website and access their discontinued downloads where you'll be able to download the product keys for the older versions. They're giving them away.  Perfectly legal.   I've read that the same key for the last version 6 that they offer can also be used successfully on the 7 beta.

You install the version 7 beta, restart Windows, and in Device Manager update the standard pci graphics adapter (VGA) to the Sci-Tech one in the list that appears when you choose to install a different driver and scroll through the Display Adapters to the Sci-Tech Corporation drivers.  Reboot again, open up the Sci-tech control panel and you can even use 1024x768 Hi-Color!

The other trick is using the latest Realtek AC97 Audio drivers, the Windows 95 VXD version, and update your Multimedia Audio Controller to it.  Baam!  Sound!

Stuff like this is on the VirtualBox forums.  I'm going to try this eventually on Debian Lenny, as the only Windows I'd want to virtualize is Windows 98SE.  I've got a real drive with Vista on it (by choice, really!)  I've got XP Pro, and used to do a dual-boot 98SE and XP, but figured I might as well have the latest Windows since I bought it.  I actually use the Vista boot loader and BCDEasy to boot grub that is on my 2nd hard drive's Linux partition where Debian is.  I wanted to keep the Vista boot loader so I can muck about with Windows all I want without Grub being effected.  Let Windows destroy things.  I'd just move Grub into the mbr if necessary.  

I want 98 so I can use a few programs that haven't worked on XP since they went to Service Pack 2 and of course won't work on Vista, and not on Wine or Dosbox either.  Stupid things like Star Trek Captains Chair that don't need Direct 3D but won't run on newer Windows versions.  Don't need them, but they're fun as is playing with virtual machine operating systems.

Edit -

Oh, forgot to mention that less video memory allocation is actually better on VirtualBox.  It defaults to 8MB, but changing it to 7MB has eliminated some problems for some folks.  You certainly don't need more than that for what VirtualBox supports for Video anyway.  You won't be playing any Direct 3D games!

---

### Post by freymann on 2008-01-03
> **Eck said:**
> Use Sci-Tech Display Doctor version 7 beta.  Major Geeks has it.  Go to the Sci-Tech website and access their discontinued downloads where you'll be able to download the product keys for the older versions. They're giving them away. 

I have just completed installing Win98SE as a virtual system in ubuntu 7.10 and I got stuck with a crappy 640x480x16 color screen and was hoping your solution may work.

I was able to download the Display Doctor 7 beta exe, but I'm having NO LUCK finding anything about keys at the Sci-Tech website. Any suggestions?

---

### Post by |2eason on 2008-01-03
Bash;
```

VBoxManage setextradata "NameofYourVMHere" "CustomVideoMode1" "1024x768x32"
```
Haven't tried it myself, just spotted it in the manual.

---

### Post by freymann on 2008-01-03
> **|2eason said:**
> Bash;
```

VBoxManage setextradata "NameofYourVMHere" "CustomVideoMode1" "1024x768x32"
```
Haven't tried it myself, just spotted it in the manual.

 Sorry, what is that for??

 I have the Display Doctor 7 Beta installed and I was able to increase my Virtual Machine win98 desktop from 640x480 to 800x600. I didn't try the 1024x768 yet but I see no reason why I can't go that big.

 Display Doctor 7 Beta has a 21 day trial... where do I find the key or whatever it is I need? That's my big question...

---

### Post by |2eason on 2008-01-03
> **freymann said:**
> Sorry, what is that for??
From the manual; > 

9.5 Custom VESA resolutions

Apart from the standard VESA resolutions, the VirtualBox VESA BIOS allows you to add up to 16 custom video modes which will be reported to the guest operating system. When using Windows guests with the VirtualBox Guest Additions, a custom graphics driver will be used instead of the fallback VESA solution so this information does not apply.
  Additional video modes can be configured for each VM using the extra data facility. The extra data key is called CustomVideoMode<x> with x being a number from 1 to 16. Please note that modes will be read from 1 until either the following number is not defined or 16 is reached. The following example adds a video mode that corresponds to the native display resolution of many notebook computers:

VBoxManage setextradata "Windows XP"  "CustomVideoMode1" "1400x1050x16"

Basically, you are in VESA mode because you don't have the proper drivers, this command allows you to config the VESA 'fallback'.

---

### Post by freymann on 2008-01-03
oh heck, it's OK. I managed to make things work here and am happily enjoying running my Windows 98 SE in a "virtual machine"

Very neat!!

Your tip about the Display Doctor was just what I needed though to make it worthwhile. Many thanks!

---

### Post by IanB2 on 2008-01-06
I've managed to find and install the version 7 beta of Display Doctor and can get the correct screen resolution. I have 21 days on the trial version.

I've found the product keys for version 6 on the ftp download site but the version 6 key does not appear to work for me. Has anyone managed to do this?

---

### Post by Eck on 2008-01-06
Heh heh, I even got software 3D working by turning on SciTech Display Doctor's GLDirect thing in compatibility (CAD) mode.  It was fun doing the samples and seeing glxgears, airplanes flying, etc, on Windows 98SE.  It was slow, but familiar as my first computer was a SiS5598 machine with onboard 4MB software Direct3D and was about this same speed.

You know those sites that Windows users are forced to use all the time to get stuff to "generate" "unlocking" things for old software no longer sold, and even new software for poor folks?  That's where you need to search for the SciTech Display Doctor 7 beta thingy to use it more than 21 days.  Hint:  Personal (type in your name), 1 (weird question, but I typed 1 and it continued), Pro.  If you get it you'll understand.  Mine had no nasties embedded, but be careful out there!  Only works on your Windows guest.  He he, I tried it with Wine but had to end the process as it couldn't open the dosbox display to use it.

I did the whole Unofficial Auto-Patcher for Windows 98SE. 98SE2ME, and 98MP10 installations and have a fully updated and ready to have fun with Windows 98SE.  For some reason my Windows 98 Startup floppy couldn't load the cdrom drivers and it froze there, but I substituted an OEM 98 Gold cdrom I had and installed from that fine.  Then I used my 98SE Updates Cd (that $20 thing that upgrades 98 Gold to 98SE from a booted up GUI only), and upgraded to Second Edition.

I used SciTech for the 1024x768 res, software 3D, and used Realtek's latest Windows 95 VXD driver download extracted with WinRAR and Device Manager updated the Audio Controller to it.  Realtek's setup exe doesn't continue on anything but Windows 95 but extracting it gives you the whole thing to direct Device Manager to.  You even get SoundBlaster MS-DOS within Windows sound drivers and a Wavetable midi driver (though midi skips).

I haven't installed Rain20 yet that the Virtualbox user faq recommends to handle processor load, but I'll try that soon.  Maybe it'll help speed it up a bit.

I'll print out that VGA information posted here.  Maybe that would help too, but since I already use the SciTech driver I probably already have that fixed through just using their driver.   Not sure though.  It works so I don't want to fiddle too much with the configuration.

---

### Post by Eck on 2008-01-08
Hmm.  It's kind of too slow to really enjoy.  Rain20 perhaps saves my processor from running at 100%, but didn't speed up anything.  I tried to up the video ram to 16MB from the 6MB I was using but haven't notice any difference from that either.

I fed it 256MB memory right from the start, so that should be fine.  Internet Explorer runs at a snails pace loading web pages, and some streaming Windows Media Player embedded videos were very herky jerky, although sounding fine in between the skips.

I played the pinball game (I get that as part of 98SE2ME) and it correctly received and executed my keyboard entries correctly in real-time, so that's not too bad, but I did need to shoot the ball from the menu as the space bar caused a weird sound to play and didn't execute the plunger.  Activating the midi music played it nicely with just slight skipping unless I went and actually played the game at the same time.  Then it would just hesitate too much to make gameplay possible.  So I turned that off.  (I like that song while playing though!)

Even Windows Explorer isn't all that snappy, but better than browsing the web.

One main thing I like to have 98SE around for is Star Trek Captains Chair.  That uses QuickTime and Shockwave.  Good luck with that, eh?  Flash advertisements work fine in Internet Explorer and the latest Shockwave is installed and working on the Adobe test page, but I just don't see an audio-video intensive application running smoothly based upon what I've tested so far.  Gotta install a few more things before testing that out but I'm not optimistic.

I added Avast to have its protection and it really isn't any slower because of it.  I haven't added a firewall since with NAT networking the Linux firewall does that.

I recall using VMWare Workstation 5.5 a while back, running a 98SE guest on a Windows XP host and the thing was pretty snappy.  It effectively ran videos, games (not 3D of course) very well.  Browsing the web was fine in IE or Firefox.  I haven't even gotten to Firefox yet, but that is even more memory intensive than IE, so again I don't foresee a good experience.

I have no idea whether the slowness is due to Virtualbox running an unsupported Windows or due to this being done on Linux rather than a Windows host.  I'd think Windows would slow it down more.  But I don't see how the Guest Additions would be any speedier than this since I'd really only be getting a video driver and SciTech Display Doctor takes care of that essentially the same way, I think.

I'd be interested to hear anyone's experience with 98SE in Virtualbox on Linux regarding running it and getting acceptable performance.  This thing is just too slow.

Specs are an AthlonXP 3200+, Crucial 2x512MB PC3200 DDR-SDRAM, NVidia GeForce 6600GT, Audigy 2 ZS Platinum on an Epox EP-8KRAIPRO board.

Maybe a newer generation motherboard, processor, memory would make the diffference?  Or is it just Virtualbox?

I have no problems running Dosbox on Linux, or several programs using Wine.  Plenty of speed.

---

### Post by loeppel on 2008-01-30
Hi there, i'm trying to find the "Display Doctor 7 beta" but with no success.
Can anyone upload the software (as its freeware now) or post a download link here? 
I tested the "SciTech Display Doctor 6.53" from [http://www.scitechsoft.com/ftp/sdd/](http://www.scitechsoft.com/ftp/sdd/) but with NO success. It doesn't find a DisplayDriver for the VirtualBox Graphics Card!

Please Help!

greets,
loeppel

---

### Post by freymann on 2008-01-30
> **loeppel said:**
> Hi there, i'm trying to find the "Display Doctor 7 beta" but with no success.

 If you go to virtualbox's web site and poke around, you find this:

[http://virtualbox.org/wiki/User_FAQ]("http://virtualbox.org/wiki/User_FAQ")

 At the bottom of the page is this paragraph:

```

Poor graphical output in Windows 98

    * Unlike more modern systems, Windows 98 does not come with a driver which will work with the VirtualBox graphics card, so it falls back to using it as a 16 color VGA card. While innotek do not provide Guest Additions for Windows 98, the Display Doctor suite by the company SciTech does contain a driver which will allow you to use higher color and resolution graphics modes. Please note that neither innotek nor SciTech support nor accept liability for the use of this program. 

    You can download the installation program for Display Doctor here and the activation codes here.
```

 Of course, that link is for 6.53...

 And the other links gives you registration codes for it.

 I forget what version I downloaded...I think I found 7.3.4.000 somewhere.. just by searching in google. It's 10MB's. If you're absolutely stuck I'm sure I could get you a web url to download it with...

---

### Post by jon_herr on 2008-02-18
About SciTech Display Drivers:

Beta Version is here:
[http://www.majorgeeks.com/download382.html](http://www.majorgeeks.com/download382.html)

regcodes and everything from oem is here:
[ftp://ftp.scitechsoft.com/sdd/](ftp://ftp.scitechsoft.com/sdd/)


These tricks also work for Windows 95.

---

### Post by aBitLater on 2008-02-24
what's the trick here?

I can't get the reg codes mentioned from the previous post to work with the 7 beta download (link in the previous post).  Anyone else get them to work?  I tried the "windows and dos" codes for version 6.53 and version 5.3a, neither worked with the version 7 beta, as was mentioned on the first page of this thread.

so I downloaded version 6.53, and it won't recognize the virtual box graphics adapter.  I'm using a win98 SE guest OS on linux


```

SciTech UNIVBE 6.7
Supports DOS.
No Code Required
  	 
SciTech Display Doctor 6.53
Supports: Windows and DOS.
Free Version Code
Reg Code: 	00000-173D626E-02002
Full Name: 	6.x Free Edition

SciTech Display Doctor 6.53-d
DOS ONLY
Free Version Code
Reg Code: 	00000-173D626E-02002
Full Name: 	6.x Free Edition
	
SciTech Display Doctor 5.3a
Supports: Windows and DOS.
Free Version Code
Reg Code: 	00000-816EAD30-20020
Full Name: 	5.x Free Edition

SciTech Display Doctor 5.3a-d
DOS ONLY
Free Version Code
Reg Code: 	00000-816EAD30-20020
Full Name: 	5.x Free Edition

```

---

### Post by HermanAB on 2008-02-25
Hmm, Virtualbox is based on Qemu and it mainly supports WinXP.  So using other versions of Windows is bound to be somewhat traumatic.

---

### Post by aBitLater on 2008-02-26
my vb guest os win98se runs really slow.  It's usable, but barely.  I've considered removing the scitech display doctor, assuming that may be part of the cause for the slow-down.

---

### Post by davmk on 2008-03-26
Well, Windows 98 is some real sh*t which uses MS-DOS for most common things. That MS-DOS layer is emulated with the 16bit virtual mode manager in x86, but, as one process cannot be both run 32bit AND under 16bit VMM, all 16-bit code must be emulated which causes the system to go really slow. The system was faster when i installed unofficial service pack v2.1a.

If you look for a not too slow system, think about Win95 OSR2 (it is actually faster than Win98SE on my system). Think also disabling ACPI, IO-APIC or any high-tech thing that Win98 have hard time to support.

Finally, make sure you install 32-bit drivers. 16bit drivers in Windows 98 are common but painfully slow.

---

### Post by Wake Rider on 2008-05-01
> **Eck said:**
> Heh heh, I even got software 3D working by turning on SciTech Display Doctor's GLDirect thing in compatibility (CAD) mode.  It was fun doing the samples and seeing glxgears, airplanes flying, etc, on Windows 98SE.  It was slow, but familiar as my first computer was a SiS5598 machine with onboard 4MB software Direct3D and was about this same speed.

You know those sites that Windows users are forced to use all the time to get stuff to "generate" "unlocking" things for old software no longer sold, and even new software for poor folks?  That's where you need to search for the SciTech Display Doctor 7 beta thingy to use it more than 21 days.  Hint:  Personal (type in your name), 1 (weird question, but I typed 1 and it continued), Pro.  If you get it you'll understand.  Mine had no nasties embedded, but be careful out there!  Only works on your Windows guest.  He he, I tried it with Wine but had to end the process as it couldn't open the dosbox display to use it.

I did the whole Unofficial Auto-Patcher for Windows 98SE. 98SE2ME, and 98MP10 installations and have a fully updated and ready to have fun with Windows 98SE.  For some reason my Windows 98 Startup floppy couldn't load the cdrom drivers and it froze there, but I substituted an OEM 98 Gold cdrom I had and installed from that fine.  Then I used my 98SE Updates Cd (that $20 thing that upgrades 98 Gold to 98SE from a booted up GUI only), and upgraded to Second Edition.

I used SciTech for the 1024x768 res, software 3D, and used **Realtek's latest Windows 95 VXD driver download extracted with WinRAR and Device Manager updated the Audio Controller to it.**  Realtek's setup exe doesn't continue on anything but Windows 95 but extracting it gives you the whole thing to direct Device Manager to.  You even get SoundBlaster MS-DOS within Windows sound drivers and a Wavetable midi driver (though midi skips).

I haven't installed Rain20 yet that the Virtualbox user faq recommends to handle processor load, but I'll try that soon.  Maybe it'll help speed it up a bit.

I'll print out that VGA information posted here.  Maybe that would help too, but since I already use the SciTech driver I probably already have that fixed through just using their driver.   Not sure though.  It works so I don't want to fiddle too much with the configuration.

Which one did you use? I am struggling to get sound on Windows 98 in VirtualBox!

---

### Post by xfree07 on 2008-09-21
You know, I honestly didn't want to use Microsoft's VirtualPC 2007 to run Windows 98, but I was forced to.  I tried it in VirtualBox, but I couldn't get the Display Doctor 7 driver to work, nor the VESA drivers they listed on that Geocities page.  The VM would just hang on startup, and never go into Windows.  To make matters worse the CPU load was always fairly high, even with RAIN 2.0.  

It works great with VirtualPC though, as one would expect.  It works about the same as Ubuntu or Debian work under VirtualBox with a Windows host OS - Great!  All the drivers work right out of the box, and there are guest tools as well.

I would be interested to see if it is possible to run VirtualPC on Wine... Has anyone tried this???

I was trying to set up a MyEnTunnel solution, because AutoSSh wasn't accomplishing my goals (remote ports stay open?):
[http://freshme.at/index.php?page=articles&op=readArticle&id=8&title=Cant-access-remote-desktop-via-SSh-remote-port--Use-a-Windows-98-VM]("http://freshme.at/index.php?page=articles&op=readArticle&id=8&title=Cant-access-remote-desktop-via-SSh-remote-port--Use-a-Windows-98-VM")

---

### Post by col48 on 2009-05-24
Came across this thread when looking for a way to get >16 colours on guest Windows95 in VirtualBox under Ubuntu Hardy.

Is Display Doctor still the recommendation for this?

_**SVGA resolution 800x600 without Display Doctor**_

I have managed to get SVGA 800x600 rather than 600x480 which was all the VM originally offered.  When searching the net for a solution I came across [http://kb2.adobe.com/cps/312/312726.html](http://kb2.adobe.com/cps/312/312726.html) (as at 14 May 2009) which gave me the vital clue, although I was not able to follow the instructions to the letter in the VM.

The essence is to run (in DOS mode on the guest)

Extract  Win95_04.cab  xx\framebuf.drv  /L  c:\windows\system

where xx points to where the cab file is (perhaps on the Windows95 installation CD).

This then opens up SVGA as an option in the Control Panel to allow 800x600.

---

