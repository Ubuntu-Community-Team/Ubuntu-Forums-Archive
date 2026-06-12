---
title: "ATA disk timing issue - results in 30 second freeze"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by Doug S on 2012-11-23
The issue herein is carried forward from late in the 12.04 release cycle. The issue persists with the server 13.04 development system. I have made progress on the issue to the point of isolating it down to [udev revision 2760 ]("http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu/precise/udev/ubuntu/revision/2760/debian/patches/builtin-block-polling.patch")
 
What am I looking for? Someone else with the same issue.
 
The issue: On a very pathetic computer with an old style ATA type disk and under intensive disk I/O, occasionally the system will lock up for 30 seconds. Example kern.log entry:```
Nov 20 15:31:10 test-smy kernel: [ 7493.285721] ata1: lost interrupt (Status 0x58)
Nov 20 15:31:10 test-smy kernel: [ 7493.289578] ata1: drained 65536 bytes to clear DRQ
Nov 20 15:31:10 test-smy kernel: [ 7493.292936] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov 20 15:31:10 test-smy kernel: [ 7493.295863] ata1.00: failed command: READ DMA
Nov 20 15:31:10 test-smy kernel: [ 7493.297694] ata1.00: cmd c8/00:20:48:86:7c/00:00:00:00:00/e0 tag 0 dma 16384 in
Nov 20 15:31:10 test-smy kernel: [ 7493.297694]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Nov 20 15:31:10 test-smy kernel: [ 7493.304284] ata1.00: status: { DRDY }
Nov 20 15:31:10 test-smy kernel: [ 7493.308525] ata1: soft resetting link
Nov 20 15:31:10 test-smy kernel: [ 7493.478162] ata1.00: configured for MWDMA2
Nov 20 15:31:10 test-smy kernel: [ 7493.478243] ata1.00: device reported invalid CHS sector 0
Nov 20 15:31:10 test-smy kernel: [ 7493.478365] sd 0:0:0:0: [sda]
Nov 20 15:31:10 test-smy kernel: [ 7493.478394] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 20 15:31:10 test-smy kernel: [ 7493.478428] sd 0:0:0:0: [sda]
Nov 20 15:31:10 test-smy kernel: [ 7493.478451] Sense Key : Aborted Command [current] [descriptor]
Nov 20 15:31:10 test-smy kernel: [ 7493.478493] Descriptor sense data with sense descriptors (in hex):
Nov 20 15:31:10 test-smy kernel: [ 7493.478514]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
Nov 20 15:31:10 test-smy kernel: [ 7493.478633]         00 00 00 00
Nov 20 15:31:10 test-smy kernel: [ 7493.478693] sd 0:0:0:0: [sda]
Nov 20 15:31:10 test-smy kernel: [ 7493.478724] Add. Sense: No additional sense information
Nov 20 15:31:10 test-smy kernel: [ 7493.478762] sd 0:0:0:0: [sda] CDB:
Nov 20 15:31:10 test-smy kernel: [ 7493.478782] Read(10): 28 00 00 7c 86 48 00 00 20 00
Nov 20 15:31:10 test-smy kernel: [ 7493.478890] end_request: I/O error, dev sda, sector 8160840
Nov 20 15:31:10 test-smy kernel: [ 7493.483030] ata1: EH complete
```I realize that typically these types of errors indicate a failing disk. Such is not the case here, the issue has been repeated with multiple disks, cd-rom drives, and cabling. I can also create or eliminate the issue with udev compiled with / without the revision 2760 (or 2761) change (well, I did that for 12.04, but not yet for 13.04).
 
Disclaimer: The problem computer is underpowered, and that might be the root issue. I have not been able to repeat the issue on any of my other computers.
 
References:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654)
[http://www.smythies.com/~doug/network/hd_race/index.html](http://www.smythies.com/~doug/network/hd_race/index.html)
[http://ubuntuforums.org/showthread.php?t=1958838](http://ubuntuforums.org/showthread.php?t=1958838)

---

### Post by ventrical on 2012-11-23
> **Doug S said:**
> 
Disclaimer: The problem computer is underpowered, and that might be the root issue. I have not been able to repeat the issue on any of my other computers.
 

Sounds like a good call.

  I am just curious as to your hardware config info. I have had older machines cough when I have too many hdds attatched. Also 4500rpm drives could stall.. old Maxtors.. even 7200rpms.WDs  Some hdds really draw a lot of power after time.

---

### Post by Doug S on 2012-11-23
Sorry, I should have said "only 200Mhz CPU" when I said "underpowered". As far as I know the power supply is fine.
 
[The hardware config.]("http://www.smythies.com/~doug/network/s06_profile/hardwareprofile.html")  (note: the memory information is actually incorrect in that lshw -html listing. see also [here.)]("http://www.smythies.com/~doug/network/s06_profile/index.html")
 
I probably should just give up and toss the computer. However I liked contributing via minimum requirements testing with it. My thinking was always that if testing passes with this computer, then we know for sure one that actually meets the minimum requirements (300Mhz) will be O.K. However, conversely, we know nothing if mine fails testing, as it started to really late in the 12.04 cycle.

---

### Post by ventrical on 2012-11-23
Yepper .. the traffic cops are going WAIT, WAIT, WAIT.

---

### Post by zika on 2012-11-23
I would try to look in [http://ubuntuforums.org/showthread.php?t=2086325](http://ubuntuforums.org/showthread.php?t=2086325) and try to see if there is a solution of Your problem also. Since I do not have HW to test it I'll leave i to You... File mentioned there is a good place to start in my opinion and I'm very confidnt since I was looking for a solution for quite a long time...

---

### Post by ventrical on 2012-11-23
Thats an Ultra ATA so  there may be a conflict with your 33MHz IDE bus and 133Mhz hdd clock?. I am not sure if it would help to put an 80strand/40pin cable on that but you could try ... or if there is a clock setting for UltraATA in your BIOS .. I know some of the older machines would have that option in the BIOS.

EDIT: or you can check to see if that PC supports UDMA , choose 4, or if PIO, then 3 or 4.

---

### Post by Doug S on 2012-11-23
@zika: Thanks for [that reference]("http://paulphilippov.blogspot.co.uk/2011/07/how-to-fix-slow-boot-with-ata-errors.html") . I am so dense. Previously when I tried to revert the single line rule change of udev rev 2760, I did NOT do:```
sudo update-initramfs -u
``` and so I thought that quicker than complete re-compile method did not work. I am re-testing it now.
 
@ventical: another HD I have tried is ATA-100. I have done tests with multple different 80 pin cables and ... I'll look at bios settings after above tests are done (usually about 4 hours is enough to know for sure).
 
Summary of the issue introduced by udev [rev 2760 ]("http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu/precise/udev/ubuntu/revision/2760/debian/patches/builtin-block-polling.patch")(and the same line was modified again in [rev 2761]("http://bazaar.launchpad.net/~ubuntu-core-dev/ubuntu/precise/udev/ubuntu/revision/2761/debian/patches/builtin-block-polling.patch")): The issue can be eliminated be reverting the single line rules change of /lib/udev/rules.d/60-persistent-storage.rules to the rev 2759 and prior state.
Specifically change this:```
ACTION=="add", ATTR{removable}=="1", ATTR{events_poll_msecs}=="-1", ATTR{events_poll_msecs}="2000"
```Back to this:```
ACTION=="add", KERNEL=="sr*", ATTR{events_poll_msecs}=="0", ATTR{events_poll_msecs}="2000"
```And yes, those rules are with respect to removeable storage, yet the issue is with non-removeable storage. The other workaround I have found is to unplug the CD-ROM drive, if I don't need it.
 
It took me quite a lot of time (months) to get this issue isolated down to this single line rule change. 
 
So, I am questioning if the rule change should have been made in the first place, as it broke my system. Yes, there is a workaround, but I try do this work from the perspective of a inexperienced user that just wants to install Ubuntu server edition and it works.

---

### Post by ventrical on 2012-11-23
> **Doug S said:**
> @zika: Thanks for [that reference]("http://paulphilippov.blogspot.co.uk/2011/07/how-to-fix-slow-boot-with-ata-errors.html") . I am so dense. Previously when I tried to revert the single line rule change of udev rev 2760, I did NOT do:```
sudo update-initramfs -u
``` and so I thought that quicker than complete re-compile method did not work. I am re-testing it now.
 
 
So, I am questioning if the rule change should have been made in the first place, as it broke my system. Yes, there is a workaround, but I try do this work from the perspective of a inexperienced user that just wants to install Ubuntu server edition and it works.

If you're dense , then I'm denser hehehaha .. hey .. Dense and Denser .. new theme for a cyber movie .. no jk... but yes.. some times the linux command line interface is all new to me, even after 2 years of it. 25 years of Microsoft really took it's toll on me. :)

  I am pretty well a novice Ubuntu user but I have lots of hardware experience and my instincts always lead me there.

---

### Post by dino99 on 2012-11-24
its a good idea to start with this test:

[http://support.asus.com/powersupply.aspx](http://support.asus.com/powersupply.aspx)

(even if there is no Asus hardware)

---

### Post by Doug S on 2012-11-24
O.K. so now I have tested on 13.04 with: That one rule reverted back to rev 2759 state, works fine; Rule restored to rev 2761 state, has problems; Rule reverted back to rev 2759 state, works fine; Rule restored to rev 2761 state, has problems; Rules changed as per the link that zika gave, has problems.
 
I also checked my bois for the settings ventrical suggested, and they don't exist in my bios.
 
I remain convinced that there is a subtle timing issue or race condition introduced by udev rev 2760 (and 2761), perhaps worsed on my computer because it is so pathetic, but still a failure window.
 
I am looking for anyone else that has experienced this issue. The problem was introduced with that one line rule change in udev 175-0ubuntu7 somewhere around late March or early April 2012, and continues today with udev 175-0ubuntu13.

---

### Post by Doug S on 2013-01-23
Solved!!! (or more correctly, issue understood. Finally, and after almost 10 months).
 
**_Summary: _**The single udev rule change that "*introduced*" this issue, actually just created a new, and more probable, way to demonstrate a pre-existing issue.
 
**_Conclusion:_** I can continue to try to contribute via using the pathetic old computer as a (less than) minimum requirements server test platform.
 
**_Details:_** 
 
The keys to finally unlocking this mystery were: Some article somewhere (sorry, I can not recall where, so can not provide a due credit reference) that mentioned to monitor the interrupts; And secondly, the constant nagging question as to how a single udev rule change related to removable devices, i.e. a CD_ROM drive, resulted in a problem with the non-removable hard drive.
 
The motherboard has two IDE controllers, the primary uses interrupt 14 and the secondary uses interrupt 15. It turns out that those two interrupts do not co-habitat well, and perhaps never did. The single line udev rule change that started this whole saga, also created a steady stream of interrupt 15's, even if the CD-ROM drive was not being used. The hard drive was on the primary IDE controller, using interrupt 14. The CD-ROM drive was on the secondary IDE controller using interrupt 15. Before, the single line udev rule change, there was never an interrupt 15 if the CD-ROM drive was not being used.
 
Verification experiment 1: If it is true that the issue is due to some issue where certain timing of interrupt 15 occurring can cause a missed interrupt 14, then one should be able to increase the number of occurrences per unit time of the lost interrupt 30 second freeze by increasing the number of interrupt 15's per unit time. The udev rule:```
ACTION=="add", ATTR{removable}=="1", ATTR{events_poll_msecs}=="-1", ATTR{events_poll_msecs}="[COLOR=red]2000[/COLOR]"
```was changed to```
ACTION=="add", ATTR{removable}=="1", ATTR{events_poll_msecs}=="-1", ATTR{events_poll_msecs}="[COLOR=red]500[/COLOR]"
```for about 4 times the interrupt 15 rate. My random disk read test program was run. Previously the lost interrupt 30 second freeze rate averaged about one per hour, but now it averaged about 4 per hour.
 
Verification experiment 2: O.K., using the original, pre revision 2760 udev rule can the lost interrupt 30 second freeze still be made to occur via using the CD-ROM drive at the same time, thus creating interrupt 15's? A DVD was created, with one big 4 gigabyte file. These commands were entered (for my own memory and future reference):```
doug@test-smy:~$ sudo mount /dev/sr0 /media/cdrom
[sudo] password for doug:
mount: block device /dev/sr0 is write-protected, mounting read-only
doug@test-smy:~$ cd /media/cdrom
doug@test-smy:/media/cdrom$ cp big /dev/null
```A high rate of interrupt 15s were observed. Meanwhile the random disk read test program was run. The lost interrupt 30 second freeze occurred occasionally.
 
Verification experiment 3: If the CD-ROM drive is moved to be the second, slave, device on the primary IDE interface, thus eliminating interrupt 15, does the issue not occur? The udev rule used was the higher interrupt rate one from above. Otherwise, the experiment execution was as per experiment 2 above. There was never a lost interrupt 30 second freeze. Interrupts, for reference:```
doug@test-smy:/lib/udev/rules.d$ cat /proc/interrupts
           CPU0
  0:    6154057    XT-PIC-XT-PIC    timer
  1:        369    XT-PIC-XT-PIC    i8042
  2:          0    XT-PIC-XT-PIC    cascade
  8:          0    XT-PIC-XT-PIC    rtc0
 10:      13152    XT-PIC-XT-PIC    eth0
 [COLOR=red]14:     441848    XT-PIC-XT-PIC    ata_piix[/COLOR]
[COLOR=red]15:          0    XT-PIC-XT-PIC    ata_piix[/COLOR]
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
IWI:          0   IRQ work interrupts
RTR:          0   APIC ICR read retries
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         83   Machine check polls
ERR:          0
MIS:          0
```**_Notes:_**
 
The interrupt 15 rate never made any sense, nor correlated exactly with the [COLOR=black][FONT=Tahoma]events_poll_msecs time. However it did, roughly scale, with the setting. Also it would change by 2 always. i.e. if I set a longer time of 5 seconds, the interrupt counter would not change for about 6 or 7 seconds, then increase by 2. This will be an investigation for another time.[/FONT][/COLOR]
 
Edit: Two other computers behave the same. For very long events_poll_msecs, the times don't correlate exactly, for more typical settings and shorter, they do, once one divides by 2. No need for future investigation.
 
[COLOR=black][FONT=Tahoma]Performance is greatly hampered by having the CD-ROM drive and HDD on the same IDE cable/interface. Seeks rates dropped as low as 6 per second while the CD-ROM was also copying the big file to /dev/null. On separate IDE interfaces, the seek rate stayed as high as 84 seeks per second. The seek rate was typically 89 seeks per second with nothing else going on at the same time. With the CD-ROM drive on the same cable, but doing nothing the HDD seek rate was typically 84 seeks per second. I only use the CD-ROM drive to install a new ISO, so it will just take longer. It already took several hours on this old pathetic computer anyhow.[/FONT][/COLOR]
 
**_Thanks:_** If you actually got this far, thanks to all that helped on this thread and the one I had previously during the 12.04 cycle.

---

### Post by ventrical on 2013-01-24
> **Doug S said:**
> The issue herein is carried forward from late in the 12.04 release cycle. The issue persists with the server 13.04 development system. I have made progress on the issue to the point of isolating it down to [udev revision 2760 ]("http://bazaar.launchpad.net/%7Eubuntu-core-dev/ubuntu/precise/udev/ubuntu/revision/2760/debian/patches/builtin-block-polling.patch")
 
What am I looking for? Someone else with the same issue.
 
The issue: On a very pathetic computer with an old style ATA type disk and under intensive disk I/O, occasionally the system will lock up for 30 seconds. Example kern.log entry:```
Nov 20 15:31:10 test-smy kernel: [ 7493.285721] ata1: lost interrupt (Status 0x58)
Nov 20 15:31:10 test-smy kernel: [ 7493.289578] ata1: drained 65536 bytes to clear DRQ
Nov 20 15:31:10 test-smy kernel: [ 7493.292936] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov 20 15:31:10 test-smy kernel: [ 7493.295863] ata1.00: failed command: READ DMA
Nov 20 15:31:10 test-smy kernel: [ 7493.297694] ata1.00: cmd c8/00:20:48:86:7c/00:00:00:00:00/e0 tag 0 dma 16384 in
Nov 20 15:31:10 test-smy kernel: [ 7493.297694]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Nov 20 15:31:10 test-smy kernel: [ 7493.304284] ata1.00: status: { DRDY }
Nov 20 15:31:10 test-smy kernel: [ 7493.308525] ata1: soft resetting link
Nov 20 15:31:10 test-smy kernel: [ 7493.478162] ata1.00: configured for MWDMA2
Nov 20 15:31:10 test-smy kernel: [ 7493.478243] ata1.00: device reported invalid CHS sector 0
Nov 20 15:31:10 test-smy kernel: [ 7493.478365] sd 0:0:0:0: [sda]
Nov 20 15:31:10 test-smy kernel: [ 7493.478394] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 20 15:31:10 test-smy kernel: [ 7493.478428] sd 0:0:0:0: [sda]
Nov 20 15:31:10 test-smy kernel: [ 7493.478451] Sense Key : Aborted Command [current] [descriptor]
Nov 20 15:31:10 test-smy kernel: [ 7493.478493] Descriptor sense data with sense descriptors (in hex):
Nov 20 15:31:10 test-smy kernel: [ 7493.478514]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
Nov 20 15:31:10 test-smy kernel: [ 7493.478633]         00 00 00 00
Nov 20 15:31:10 test-smy kernel: [ 7493.478693] sd 0:0:0:0: [sda]
Nov 20 15:31:10 test-smy kernel: [ 7493.478724] Add. Sense: No additional sense information
Nov 20 15:31:10 test-smy kernel: [ 7493.478762] sd 0:0:0:0: [sda] CDB:
Nov 20 15:31:10 test-smy kernel: [ 7493.478782] Read(10): 28 00 00 7c 86 48 00 00 20 00
Nov 20 15:31:10 test-smy kernel: [ 7493.478890] end_request: I/O error, dev sda, sector 8160840
Nov 20 15:31:10 test-smy kernel: [ 7493.483030] ata1: EH complete
```I realize that typically these types of errors indicate a failing disk. Such is not the case here, the issue has been repeated with multiple disks, cd-rom drives, and cabling. I can also create or eliminate the issue with udev compiled with / without the revision 2760 (or 2761) change (well, I did that for 12.04, but not yet for 13.04).
 
Disclaimer: The problem computer is underpowered, and that might be the root issue. I have not been able to repeat the issue on any of my other computers.
 
References:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654)
[http://www.smythies.com/~doug/network/hd_race/index.html]("http://www.smythies.com/%7Edoug/network/hd_race/index.html")
[http://ubuntuforums.org/showthread.php?t=1958838](http://ubuntuforums.org/showthread.php?t=1958838)


 Doug S,

Thanks for bringing this up again. I had a complete fail after a BIOS upgrade and got the exact same errors as you had posted in this thread.!! Please see:

[http://ubuntuforums.org/showthread.php?t=2105242](http://ubuntuforums.org/showthread.php?t=2105242)

 I was doing an experiment with trying to enable a 3.0 USB PCI-e card  on an Intel Motherboard.  It gave me boot option prioritys of USB, HDD or bootable add-in cards in BIOS.

  Before I upgraded the BIOS I enabled Plug 'n Pray to see if the card would work. No Go. Then ( me dummy) I enabled LBA. Nothing went wrong at first. All was still working well with the excpetion that  I could not get the 3.0 USB PCI-e card to work (although it was recognized with lspci command.)

  I then proceeded to upgrade the BIOS verison and then, everything went south and I started getting the bootup errors ( that you have posted.)  I could only get raring to boot from GRUB recovery option witht the 3.5.x-x kernel set . 3.7.0-0 and anything above would just lock up. I then decided to install the raring daily (about 2 days ago) over the borked install  and it came up like it was running in molasses (after still producing those errors which you have posted). I then decided to try a stable release of Precise and by default that April 2012 release install an earlier version of GRUB. It seemed that this process had completely rectified the problem. I did back up some of my files and folders from that install before I Installed 12.04. I thought at first that  is was the BIOS  upgrade but it was not (as proved out by  the fine working 12.04 install) .

  It is just my opinion that at current time , raring was not able to handle the BIOS upgrade and the current  dailys are really not installing very well at all. With Lucid and Maveric I could swap a USB install (or HDD) to any PC and it would just work.  Now, it seems that Ubuntu has become more pernickity with graphic hardwiring and hence trying to swap a drive out to another PC will not auto jockey reset (as did Lucid and Maveric.

  ** Note: I use  the term auto-jockey-reset as it appeared that those two versions would use a generic graphic detect algorithm that would not bork a crossover.

  Hope this is of some help.

---

### Post by Doug S on 2013-01-25
Hi Ventrical,
Thanks for your reply and details about your issue. I also followed your link, and the links from there. Furthermore, I spent several hours yesterday trying to find any more information on historical issues with interrupts 14 and 15, as they are just so very basic to IDE based systems. There are some notes in the ata_piix.c source code header about IDE deadlock under high load. I also found an interesting note (which, of course, I can not find again) about one interrupt incorrectly clobbering the other. My own log book notes for the problem computer from 2003 mention IDE issues and swapping devices around until it finally worked with windows me. I should have just listened to my own log book note dated 2003.12.26: "Preparing to retire this computer as the main family use computer. The computer has done well, but just cann't keep up with the compute demands of these days." ... 2.5 years years later I revived it and it became the main Ubuntu server computer for several years. Now, I just do minimum requirments testing on it, but I think I'll re-consider to just turf it. It certainly doesn't owe me anything.

---

