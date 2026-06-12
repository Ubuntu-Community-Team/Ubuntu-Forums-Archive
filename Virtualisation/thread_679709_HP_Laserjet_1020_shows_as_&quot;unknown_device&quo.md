---
title: "HP Laserjet 1020 shows as &quot;unknown device&quot; in device manager (VM-XP)"
date: 2008-01-27
forum: Virtualisation
---

### Post by diablo75 on 2008-01-27
Someone I know has a HP Laserjet 1020, and it prints just fine from Ubuntu.  But from VMware, after install the software and then connect the USB cable as well as check-off (enable) the device in the Removable Device menu, Device Manager shows it to be an Unknown USB device.

I've done some looking around, some forums on the web seem to indicate this problem has to do with the cable that came with the printer, or that the 2.0 needs to be disabled and set to function as a 1.1 port.  I've not yet tried a new cable out, but hopefully that will work so nothing in the bios or in the device manager has to be disabled...

But I was wondering if anybody has any other ideas about what might cause this problem?

---

### Post by fjgaude on 2008-01-27
You are doing this in VMware, in Windows guest? If so, you likely need to use the  Windows install disk for the printer.

---

### Post by diablo75 on 2008-01-27
I've tried using both the original software CD that came with the printer, as well as the latest available drivers from HP's website.  No go.

---

### Post by fjgaude on 2008-01-27
Did the original driver load without errors?

---

### Post by diablo75 on 2008-01-28
I'm not entirely sure.  I did get this in an e-mail from him, discussing this problem:

>  I had gotten the error message in xp that only a 1.0 usb was available.
If I remember correctly, that is a vmware thing with the free version.  Did plug in a new cable.  Device is still not recognized.

I'm not sure what to try now.

Is there a way to share the printer into Windows using Cups or something?  I've set up LPR/LPD printing in a windows VM before, but it seemed to have mixed success.

---

### Post by fjgaude on 2008-01-28
Printers don't need anything more than USB 1.0; mine work fine and my Canon i9100 is about as fast as printers get. It works fine here, no slow ups.

I don't know of a way to use CUPS, but there likely is... could you google your printer and get the latest driver from HP or wherever?

---

### Post by diablo75 on 2008-01-28
Yeah, I downloaded the latest drivers from HP's website.  Good old windows.  This problem, to me, feels like something that'll get fixed after I uninstall the "unknown device", unplug the device (or rather, uncheck it in removable devices), then reinstall the drivers, then re-attach the printer.

Perhaps the whole reason this madness is going on is because he plugged the printer in before installing the drivers.  I'm not sure.  I'm just glad that it works in a truely plug-n-play fashion in Ubuntu as God had intended ;)

I'll keep fiddling around with it...

---

