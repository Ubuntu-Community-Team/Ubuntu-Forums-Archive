---
title: "Initial ramdisk error"
date: 2006-07-20
forum: Sun Sparc Users
---

### Post by soapyfish on 2006-07-20
Hi I have a sun ultra 2 enterprise. After a bit of research and reading other sparc related posts I though I would give ubuntu a try on my sun. I downloaded the dapper iso version 20060616.5. (version number from welcome screen) I start the boot process and this is the output

Allocated 8 Megs of memory at 0x40000000 for kernal
Loaded kernal version 2.6.15
loading initial ramdisk (4821666 bytesat 0x40000000 phys, 0x40C00000 virt)...
Illegal instruction
{0} ok   

I recieve the same problem with a rescue boot. The system currently has solaris 10 installed and that seems to work fine  so I am not sure its actually a hardware problem ?  I cannot alt f2 or anything like that but the open boot still works

---

### Post by RaggedJack on 2006-07-21
I am also experiencing this exact same problem.  I read in a much earlier post about someone removing memory from there machine and being able to complete the install.  

I am using an Ultra 2 Enterprise as well.  Anyone have any insight.   It has been running Solaris 9 for a while with no issues.  Is there anything I can do to help to assist someone with diagnosing the problem?  Thanks in advance

---

### Post by chansiuming on 2006-07-22
> **soapyfish said:**
> Hi I have a sun ultra 2 enterprise. After a bit of research and reading other sparc related posts I though I would give ubuntu a try on my sun. I downloaded the dapper iso version 20060616.5. (version number from welcome screen) I start the boot process and this is the output

Allocated 8 Megs of memory at 0x40000000 for kernal
Loaded kernal version 2.6.15
loading initial ramdisk (4821666 bytesat 0x40000000 phys, 0x40C00000 virt)...
Illegal instruction
{0} ok   

I recieve the same problem with a rescue boot. The system currently has solaris 10 installed and that seems to work fine  so I am not sure its actually a hardware problem ?  I cannot alt f2 or anything like that but the open boot still works

Since the ubuntu kernel for sparc is 64-bit, have you checked that your box is up-to-date (PROM) enough to run 64-bit stuff?
[http://developers.sun.com/solaris/articles/64_bit_booting.html]("http://developers.sun.com/solaris/articles/64_bit_booting.html")

---

### Post by soapyfish on 2006-07-22
Yes When I got the box I updated the OBP  to the last and current version I will give removing some of the RAM and try and post back thanks for the suggestion :-)

---

### Post by soapyfish on 2006-07-22
I have removed various memory configurations  and still no joy :-(   I DO how ever recall that I had a problem like this installing Debian sarge onto an HP Visualize B2000 station  and on that machine with the debian discs I was allowed to edit the boot options  Inc the size of the RAM disk and that allowed me to sucessfully install debain sarge hppa  maybe that will shed some light on it... I will alos try the debain sparc and see if that sheds any light

---

### Post by gavinj44 on 2006-07-22
Do you have more than a gig of memory in this machine ?

---

### Post by soapyfish on 2006-07-24
The Machine Specs are as follows  2x 296mhz Ultra sparc IIe 1gb of RAM all sun branded with  4 x 128 and 8x 64  2x 9.1  GB scsi disks  Scsi CDROM sun keyboard mouse and non sun monitor I have it plugged into a UPA graphics card although an SBus card is also in the machine. The Machine does have the lstest OBP.

---

### Post by chansiuming on 2006-07-24
> **soapyfish said:**
> The Machine Specs are as follows  2x 296mhz Ultra sparc IIe 1gb of RAM all sun branded with  4 x 128 and 8x 64  2x 9.1  GB scsi disks  Scsi CDROM sun keyboard mouse and non sun monitor I have it plugged into a UPA graphics card although an SBus card is also in the machine. The Machine does have the lstest OBP.

Have you tried the debian install cds? If debian happens to work, you could quite easily just change the apt repos and "dist-upgrade" to ubuntu. The error sounds as if you either had (1) a bad cd or cd drive (tried cd-r's instead of rw's already?) (2) wrong architecture cd, which I hope, is less likely ;)

---

### Post by soapyfish on 2006-07-24
I am going to try the debian disks tonight. I am sure I have the correct arch disks ;-) I am already using CD-R's rather than CD-RW's  I only have that one scsi CDROM drive so I cannot try another. I will try again tonight to write the CD-R at 1x with the debian ISO and let you all know how I get on.  Thankyou for all the advice   :-)

---

### Post by soapyfish on 2006-07-24
Just been doing some reading and I found this snippet in the debian sparc how to [http://www.debian.org/releases/stable/sparc/ch02s01.html.en](http://www.debian.org/releases/stable/sparc/ch02s01.html.en)

section 

"2.1.2.2. Graphics Configuration
Especially in the case of older Sun workstations, it is very common for there to be an onboard framebuffer which has been superseded (for example the bwtwo on a sun IPC), and an SBUS card containing a later probably accelerated buffer is then plugged in to an SBUS slot. Under Solaris/SunOS this causes no problems because both cards are initialized. 

However with Linux this can cause a problem, in that the boot PROM monitor may display its output on this additional card; however the linux kernel boot messages may then be directed to the original on board framebuffer, leaving no error messages on the screen, with the machine apparently stuck loading the RAMdisk. 

To avoid this problem, connect the monitor (if required) to the video card in the lowest numbered SBUS slot (on motherboard card counts as below external slots). Alternatively it is possible to use a serial console."


Maybe this  is the problem after all I do have two different video cards the machine a UPA based card and a SBus card I will check this out tonight as well and let you all know

---

### Post by gavinj44 on 2006-07-24
I seem to remember having to pass mem=512 to the installer to work properly, this was on an older sparc linux install for Debian. 

Once it was installed it would boot fine, it was just something with the installer that had issues with over 512Mb of RAM.

All my sun boxes are installed over a serial line using cisco plugs and straight cat 5.

Let me know how it goes.

Regards,
Gavin

---

### Post by RaggedJack on 2006-07-24
I was experiencing the same issue.  I am not sure what kind of configuration you are looking to use.  When using the generic install from the boot menu installation would fail.  However since I was building a lamp-server anyhow I chose this and the install finished completely and rebooted and came up correctly.  Hope this helps.  Thanks to whoever mentioned the tabbed key to select boot options.

---

### Post by soapyfish on 2006-07-25
Ok So last nite I fiddled about with RAM chips again and removed 512 of the total 1024  swapped the monitor to the SBus card and removed the UPA card and I got past the initial error about the RAM drive  :) ........I have done some reading and was aware I would have a problem with the Ultra 2's SCSI CD-ROm drive so I press the Alt + F2 to get and activate a new terminal type the modprobe esp and go back to the first terminal to carry on the installer but the machine still refuses to see the CD-ROM drive :-(  I need to spend some more time looking into this but  thats the current state of play  :)

---

### Post by simion on 2006-08-04
Wow, the memory thing worked.  I've got the exact same error as this on a Sunfire V100 with a gig of ram.  I opened the case, pulled 512mb and rebooted.  It worked.  Weirdness.  Post install I popped the rest of the memory back in and its happy.

Spooky.

---

### Post by MakubeX on 2006-08-07
In my experience, it is weird.

I don't remember passing memory value arguments, sometimes it just works, sometimes it doesn't. What I usually do - upon booting the SPARC machine, I make the prompt go to "ok" mode before it starts to initialize the memory.

---

### Post by arkham on 2006-08-15
It seems that the problem relates to how many slots you have full - any more than 2 gave me an error.  2 by themselves were just fine - like you said very weird.......

---

### Post by hakankarakas on 2006-08-16
I resolved the same problem as many of you suggested by removing the 512MB RAM form the Ultra 10. 
It passed the initil ramdisk error. I stuck with the partitioning. Mu Ultra 10 has 20GB IDE drive. Auto partitioning prepares 100MB Of boot 19.4 MB of root rest for the swap space. However after wrting partitions to the disk and formating them it return an error saying that it connot mount the root file system. 

I tried manual partitioning on the shell with the parted command however when I returned to installation it returns to partitionin section and does the same! Does ext3 fs supported on Sun disk? Has any one had a problem on partitioning?

Hakan

---

### Post by tabweb on 2006-08-21
I have a Netra t1 105 and had this problem with same dapper version. Since I have no vga on system, I was going through serial port. I found a post somewhere that mentioned I needed to do a powerdown at the LOM and then poweron, send break to get to boot prom before system comes up (i'm using minicom) and that worked. If I let system boot and did a reboot cdrom or did a break after system was up(it had solaris on it) and did a boot cdrom it would fail. 

Quickest way should be to boot this way and you shouldn't have to remove memory. Hope this helps.

---

### Post by tabweb on 2006-08-21
> **hakankarakas said:**
> 
I tried manual partitioning on the shell with the parted command however when I returned to installation it returns to partitionin section and does the same! Does ext3 fs supported on Sun disk? Has any one had a problem on partitioning?

Hakan

I had an intial problem too. I have two 36gb scsi drives in netra t1. I finally did guided partition and let the finish, then I went back to detect disks and went through the process again and chose manual partition and it worked fine.

---

### Post by kairu0 on 2007-05-17
I had this problem on Debian Etch and just got past it by removing one of my two 256MB chips. I didn't have to pass any argument to the kernel.

---

