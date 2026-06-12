---
title: "(Essentially Solved): Virtualbox Error: &quot;No Bootable Media&quot; while using .iso"
date: 2016-01-12
forum: Virtualisation
---

### Post by Saruk_Maktao on 2016-01-12
I saw another thread from a few years back, but the solution seemed to be "Make sure you're booting from the right device."

When I first set up the VM, then start it, it asks for a file or location to boot from, which I then give it the desired .iso file. In this case, Windows XP, a fresh ISO directly from the Microsoft website, and I've even tried a few from other sources, too. No matter what I do, booting from the ISO directly, it doesn't work, and I've even tried burning the ISO to a USB, and trying it on my secondary "testing" computer. Both it, and Virtualbox, report "No bootable media. System halted."

I am booting from the correct source, so that's not the problem. I also do not have the ability to burn a CD, as I do not have a disk drive, disks, or ability to attain either. I'm limited to a USB drive, and .iso files.

What are my options here?


Or, if there is a way to dual-boot Linux and Windows, easily, I'd be willing to give that a go, too. Should I make a second thread for that?

Is there something simple that I'm not seeing here in Virtualbox? It's exactly the same process I've used for years, but suddenly, it doesn't want to work.



EDIT - SOLUTION:
I did two things, which allowed Virtualbox to run.
1: In my host BIOS, I enabled a setting called virtualization, which on my particular version, I'm pretty sure was listed under boot settings, but that may not be true for your own version.
2: I changed to a different ISO file. The existing ISO had continual problems, and even still fails to boot, resulting in the same error, no bootable media. However, that was for Windows XP, which may have other settings. Using a Windows 7 ISO, it worked flawlessly. You may not be able to get the exact OS, but most newer ones should work fine.

I will attempt further testing to see if the ISO which returned the No Bootable Media error can possibly be used using any series of settings or methods.

---

### Post by MAFoElffen on 2016-01-12
> **Saruk_Maktao said:**
> I saw another thread from a few years back, but the solution seemed to be "[COLOR=#008080]Make sure you're booting from the right device.[/COLOR]"

When I first set up the VM, then start it, it asks for a file or location to boot from, which I then give it the desired .iso file. In this case, Windows XP, a fresh ISO directly from the Microsoft website, and I've even tried a few from other sources, too. No matter what I do, booting from the ISO directly, it doesn't work, and I've even tried burning the ISO to a USB, and trying it on my secondary "testing" computer. Both it, and Virtualbox, report "[COLOR=#008080]No bootable media. System halted.[/COLOR]"

I am booting from the correct source, so that's not the problem. I also do not have the ability to burn a CD, as I do not have a disk drive, disks, or ability to attain either. I'm limited to a USB drive, and .iso files.

What are my options here?

Or, if there is a way to dual-boot Linux and Windows, easily, I'd be willing to give that a go, too. Should I make a second thread for that?

Is there something simple that I'm not seeing here in Virtualbox? It's exactly the same process I've used for years, but suddenly, it doesn't want to work.

Wait, you want to dual boot a VM in VirtualBox? That is possible also... So is to a native machine... But first, let's go back to what you are seeing or not seeing. Lets help you work with what you were trying to do.

Please look at my screenshots...
On screenshot #1-- Notice that in the "Settings" windows under the System section, in the middle of the right pane, is the boot order settings. Ensure that cd/dvd is prior to the virtual hard disk in the boot order. In the main window, with that VM powered down, notice where is says under Storage > IDE Controller > CD/DVD > Empty on mine? Yours should have an iso mounted.

On screenshot #3-- Under a VM run window > Devices > CD/DVD Devices > Connect a Virtual CD/DVD ISO file... If yours says empty, like mine does in screen shot #1, then use this menu to connect to your ISO file.

On screen shot #2-- Even if your boot order is wrong, if while booting the VM, if you quickly press <F12> when it is booting, it will bring up a boot menu, where you can change the boot order for that boot sequence.

*** Why am I explaining that as I did??? Because the error message>> "[COLOR=#008080]No bootable media. System halted.[/COLOR]" is the error message VirtualBox displays when it hits a device with no boot loader. If your iso file is good, then maybe it's not attached and it hit the unformated VM HDD first... Right? Possible. I'm human. I make mistakes sometimes. Most of the time, that error is thrown when it hits an unprepared or a corrupted VDisk image.

---

### Post by Saruk_Maktao on 2016-01-13
"Because the error message>> "[COLOR=#008080]No bootable media. System halted.[/COLOR]" is the error message VirtualBox displays when it hits a device with no boot loader."

It's  possible that the ISO doesn't have a bootloader? As I've said, the  process I'm using here, is the exact same as the one I've been using for  years. I can guarantee that all the settings are correct. But, if  there's no bootloader on that ISO, and, apparently every ISO for Windows  XP that I get, perhaps there is a problem with it.... I should try  other ISOs then....

Further testing is required....

---

### Post by MAFoElffen on 2016-01-14
You could check the MD5 CheckSum to see if the iso is corrupted...

---

### Post by Saruk_Maktao on 2016-01-22
Alright, I did two things. I enabled virtualization in my BIOS, and I used a different ISO. It works, and, somewhere, I have a Windows 7 VM waiting for instructions. .... No, sorry, it's actively working. Yay!

So, I think it's the ISO that I was using which is the problem. Now, I just need to see about "burning" a working ISO to a USB drive so I can dual-boot my computer. I really hope that will finally work this time.

---

### Post by MAFoElffen on 2016-01-22
Great. Glad it works for you now.

Please resit this thread > Goto to the "Thread Tools" link > Select "Mark As Solved".

---

