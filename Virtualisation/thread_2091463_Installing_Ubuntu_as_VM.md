---
title: "Installing Ubuntu as VM"
date: 2012-12-05
forum: Virtualisation
---

### Post by BradleyAtkins on 2012-12-05
Hi

Not sure this is the right forum but here goes -

I have installed Ubuntu DT as a VM in Virtual Box running on my work laptop.

I'm having a frustrating time trying to up the screen resolution and to get the Guest Additions to work.

At one point I had a large enough screen but then found I couldn't get cut and paste to work between my host (Win 7) and guest.

I reinstalled guest additions and now have a tiny screen again and still no cut and paste.

Can anyone walk me through how to resolve these issues?

Screen 

```
brad@brad-VirtualBox:~$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0d.0 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
```

```
brad@brad-VirtualBox:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0 
```

I did have about two resolutions higher than this at one point but wasn't too sure how I got them as I just kept trying different things that turned up on Google searches until they appeared.

It would be nice if someone could spell out a more systematic approach for me...

Thaks in advance for any help

Brad

---

### Post by markbl on 2012-12-05
What is Ubuntu DT?

---

### Post by BradleyAtkins on 2012-12-05
Desk Top

---

### Post by Habitual on 2012-12-05
Make sure the clipboard is set to bidirectional.

---

### Post by BradleyAtkins on 2012-12-05
Hi

Thanks. 

Yes it is set to bidirectional but doesn't work in either direction.

I notice that my mouse scroll wheel doesn't work either, which makes me think that the problem could be with the Guest Additions package for Linux. I have an XP VM running as well and Guest Additions works fine for that.

Any ideas on how to get around this?

Brad

---

### Post by markbl on 2012-12-05
You don't tell us the version of Virtualbox, nor the version of Ubuntu guest OS.

If you are trying to run the current Ubuntu 12.10 then make sure you are using the current Virtualbox version 4.2.4. Note that 3D acceleration in current VirtualBox does not work which makes it unbearable to use because Ubuntu 12.10 does not have 2D fallback. Oracle have said an update to fix this is due soon.

---

