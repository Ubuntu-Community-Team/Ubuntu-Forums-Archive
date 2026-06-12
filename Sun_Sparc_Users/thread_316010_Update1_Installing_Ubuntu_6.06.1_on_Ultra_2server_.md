---
title: "Update1: Installing Ubuntu 6.06.1 on Ultra 2server: stalls after ALT+F2 modprobe esp"
date: 2006-12-10
forum: Sun Sparc Users
---

### Post by sandpiper on 2006-12-10
Hello,
Last week I explained my SPARC Ultra 2 Enterprise server was hanging after typing the ALT +F2 and modprobe esp command into a second window. I was attempting to complete the Ubuntu install boot process as described in previous threads. 

I have tried to diagnose what is causing the problem and have investigated the perhaps obvious (showdevs command ) (I have very limited computer experence). I have determined the CDROM is connected to the fast bus adapter  ie the device path is /sbus@1f,0/SUNW,Fas@e,8500000. Now this first device path is used in the CDROM device alias. The Boot CDROM command does wortk ok. Ie I can get as far as the selecting the keyboard layout and scanning for hardware progress screen 
There is also another device path:  /Sbus@1f,0/dma@3,81000/esp@3,8000

Now my question is: Does the Ubuntu esp driver support the fas adapter since I see the CDROM is actually (from the above device path definition) connected internally to the FAS host adapter "not" the ESP host adapter. Does this explain why I will never be able to install Ubuntu unless I get the correct FAS driver?. can anyone help me out here please? I am little lost here to know what to do.

Chris

---

### Post by netztier on 2006-12-16
> **sandpiper said:**
> Hello,
Last week I explained my SPARC Ultra 2 Enterprise server was hanging after typing the ALT +F2 and modprobe esp command into a second window. I was attempting to complete the Ubuntu install boot process as described in previous threads. 


Well, in the Dapper Beta and Dapper 6.06 days, manually loading the **esp** module definitely was necessary. Having finally found a bit of spare time, I grabbed a 6.06.1 SPARC ISO-image and booted my Ultra2 from it. 

In the first attempt to boot from CD and start the installation process, it got stuck in the first "Detecting Hardware" phase with the message: ```
Loading module 'esp' for 'FAS-336 ESP SCSI'
```

I Stop+A'd out of there and issued another **boot cdrom** command at the **ok>** prompt. This time it worked and I could've continued to install. Since the machine already has 6.10 with xubuntu on it, I stopped there.

> **sandpiper said:**
> 
Now my question is: Does the Ubuntu esp driver support the fas adapter since I see the CDROM is actually (from the above device path definition) connected internally to the FAS host adapter "not" the ESP host adapter. Does this explain why I will never be able to install Ubuntu unless I get the correct FAS driver?

Judging from the message I saw, I'd say that the esp module is the right one for the "FAS" thing - and that the manual loading of the esp module is no longer necessary with 6.06.1. Edgy 6.10 has it built-in, too. Ever tried installing *without* manually loading **esp**?


best regards

Marc

---

### Post by sandpiper on 2006-12-18
Hello Marc

Really appreciate you taking the time to assist

> **netztier said:**
>  In the first attempt to boot from CD and start the installation process, it got stuck in the first "Detecting Hardware" phase with the message: ```
Loading module 'esp' for 'FAS-336 ESP SCSI'
```

I Stop+A'd out of there and issued another **boot cdrom** command at the **ok>** prompt. This time it worked and I could've continued to install. Since the machine already has 6.10 with xubuntu on it, I stopped there.

Marc

Followed your suggestion... My ultra 2 simply performs a reset and I return to the SILO install prompt. I return to the same "hanging state"  Yes I have tried without Modprobe but the Ultra just sits there cycling the CDROM drive. Presumably if I had a faulty CDROM image there would at least be an error message

FYI: Since I posted my last update I have also got hold of a second SCSI CDROM and set it up as Target 4 on the external SCSI bus to test the drive path. Loads the image ok by issung boot "the physical path statement" and loads the ISO image ok but still hangs at the "loading module "esp" for FAS-336" message.  Just wondering what steps to take to diagnose... Regards Chris

---

### Post by netztier on 2006-12-18
> **sandpiper said:**
> Just wondering what steps to take to diagnose...

Might be worth checking **[FONT="Courier New"]/var/log/syslog[/FONT]** and dmesg's output in another console, i.e. press **ALT+F3** and run **[B][FONT="Courier New"]dmesg[/FONT]**[/B] every so often during Setup and hardware (re)discovery.
AFAICR, the esp modules and the ones that depend on it give their output to dmesg, especially the list of SCSI devices they find.

best regards

Marc

---

### Post by sandpiper on 2006-12-20
Hello Marc

> **netztier said:**
> Might be worth checking **[FONT="Courier New"]/var/log/syslog[/FONT]** and dmesg's output in another console, i.e. press **ALT+F3** and run **[B][FONT="Courier New"]dmesg[/FONT]**[/B] every so often during Setup and hardware (re)discovery.
AFAICR, the esp modules and the ones that depend on it give their output to dmesg, especially the list of SCSI devices they find.

best regards

Marc

Your advice was right on the button!.  Typed dmesg and discovered the install process stuck at SCSI device target 0.... the first SCSI disc drive. Message was DMA error. Just cycled in a loop. Removed the offending drive and "Modprobe esp worked.  (ie yes I still needed to type "Modprobe esp".)

For a person like myself who has limited experience of Linux and in particular Ubuntu, I was loosing hope of ever using the Ultra 2. Your advice has "opened the door".  Thanks so much for your time and I hope this report will help someone someday.. Merry Christmas Chris

---

