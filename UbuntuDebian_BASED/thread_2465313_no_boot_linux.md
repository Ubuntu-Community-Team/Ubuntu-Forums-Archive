---
title: "no boot linux"
date: 2021-07-29
forum: Ubuntu/Debian BASED
---

### Post by fishingsunrise on 2021-07-29
hi there,
first time here so here goes, not able to boot into my Linux at all, have re-installed grub but to no avail, I have tried boot repair and can see the report, it failed to repair the boot, I have a black screen that flashes 7 times then just stays black, how do I upload the report to get help from the community, many thanks and kind regards to you all...

---

### Post by tea for one on 2021-07-29
If you have already created a boot-repair report, then paste the URL link in this thread.

Here is some more info [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by yancek on 2021-07-29
You should run boot repair with the Create BootInfo Summary option then post the link you get when it finishes.  When you open a thread, you should always post what you are using and the version such as Ubuntu 20.04, Kubuntu `18.04.  Also indicate if it is the only OS or if you have a dual or multiboot system, which other OS's do you have.  All this info should be in the boot repair output so the suggestion to post that link is the best option.

---

### Post by fishingsunrise on 2021-07-29
ok heres the link 
[http://paste.ubuntu.com/p/C328tv76Vp/](http://paste.ubuntu.com/p/C328tv76Vp/)

---

### Post by fishingsunrise on 2021-07-29
ok heres the link 
[http://paste.ubuntu.com/p/C328tv76Vp/](http://paste.ubuntu.com/p/C328tv76Vp/)

---

### Post by Impavidus on 2021-07-29
You've got Zorin OS 15.3, which is not Ubuntu, but still based on Ubuntu 20.04. The kernel is a little behind, at 5.4.0-77, whilst Ubuntu 20.04 is at 5.4.0-80.

As the screen flashes several times, then stays black, my guess is that the system boots, but has some graphics driver problem, causing a black screen. I don't know how Zorin OS handles graphics drivers. Maybe somebody around here knows. In any case, telling us a bit more about your graphics hardware may help.

---

### Post by TheFu on 2021-07-29
> Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!
Does this not work?

Did the system ever work?

---

### Post by fishingsunrise on 2021-07-29
many thanks for the reply ;
HP laptop with AMD Ryzen 5 and Radeon Vega graphics AMD

---

### Post by fishingsunrise on 2021-07-29
hi there TheFu, the system was all working about a week ago then it just went to a black screen, how do I make my BIOS boot on sda1/EFI... I can get into options ok with esc and then go to BIOS with F10, then how do I proceed, thanks for your patience....

---

### Post by fishingsunrise on 2021-07-29
AMD Raven Graphics

---

### Post by coffeecat on 2021-07-29
*Thread moved to **Ubuntu/Debian based** sub-forum, and [Zorin] prefix added.*

---

### Post by fishingsunrise on 2021-07-29
repost from boot repair URL
[http://paste.ubuntu.com/p/C328tv76Vp/](http://paste.ubuntu.com/p/C328tv76Vp/)
some mentioned this could be graphics related as the screen is black, AMD Raven graphics, the report tells me to make BIOS boot on sda1/EFI/ubuntu/shimx64.efi file, I can access options with esc and BIOS settings, then I don't know what to do ? many thanks to you all..

---

### Post by coffeecat on 2021-07-29
@fishingsunrise, your latest post was in the form of a single-post new thread. I've merged it into the thread it belongs to.

---

### Post by TheFu on 2021-07-29
> **fishingsunrise said:**
> hi there TheFu, the system was all working about a week ago then it just went to a black screen, how do I make my BIOS boot on sda1/EFI... I can get into options ok with esc and then go to BIOS with F10, then how do I proceed, thanks for your patience....

Sorry. I don't know. My Ryzen isn't setup to use UEFI booting, nor does it have an AMD GPU.
Doesn't UEFI have a tool that allows selection of the boot init file to be used?  efi-manager?  Something like that?

A google for "ubuntu uefi" should find a lengthy article somewhere under *.ubuntu.com just about UEFI and how it works under Ubuntu. Because it used to work, I'm guessing that something about the most recent kernel update failed.  All my systems got new kernels on Saturday, but I didn't see issues related to booting or graphics. My working systems use nvidia GPUs or Intel iGPUs.  The only systems I have here with AMD GPUs are from 2010-2012 and neither uses UEFI, sorry.

The top link returned by the search: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Some EFI boot managers: [https://wiki.ubuntu.com/EFIBootLoaders](https://wiki.ubuntu.com/EFIBootLoaders)
The ones I've heard about are grub2 and rEFind. The default on Ubuntu has to be grub2.

---

### Post by ajgreeny on 2021-07-29
I am very much no expert in UEFi but for those users who are more knowledgable than me, the terminal output of command ```
efibootmgr -v
``` might be extremely helpful so copy back the output you get back here.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by fishingsunrise on 2021-07-29
```
zorin@zorin:~$ efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,2002,3000,2001,2004
Boot0000* ubuntu    HD(1,GPT,ad3fec2f-998f-42a0-a48b-be289081c320,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* USB Hard Drive (UEFI) - SanDisk (SanDisk)    PciRoot(0x0)/Pci(0x8,0x1)/Pci(0x0,0x3)/USB(4,0)/HD(1,MBR,0x5ccbc8ad,0x1d0,0x1d00)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
zorin@zorin:~$ 
```

efibootmgr -v returned the above into the terminal window

---

### Post by ajgreeny on 2021-07-30
That output sho**ws that you are at present, of course, running from a live system of zorin running from a USB.

It may also help us to see exactly what hardware you have so again from a live system run command **inxi -Fzx** and copy back the output you get.
Please use code tags this time for terminal output; as I mentioned last time, it makes it much easier to read and understand that output.

---

