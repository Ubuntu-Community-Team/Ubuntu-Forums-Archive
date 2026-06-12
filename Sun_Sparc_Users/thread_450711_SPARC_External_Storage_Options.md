---
title: "SPARC External Storage Options"
date: 2007-05-21
forum: Sun Sparc Users
---

### Post by prince_of_hackers on 2007-05-21
Hello everyone, I am wondering if anyone out there has any experience, advice, or recommendations on external storage for Ubuntu on a SPARC platform. 
 
 I have installed Ubuntu 6.06 Dapper on a [Sun Netra t1 105]("http://sunsolve.sun.com/handbook_pub/Systems/Netra_t1_105/Netra_t1_105.html"), all updates installed. I am currently in the process of setting it up as a small network server, providing time, DNS, LDAP, Samba, and intranet web services. No problems so far, however, in order for it to handle the storage capacity I will need, I am looking at the options for using external storage devices. 

 The Netra has a single PCI slot, so I tried installing a USB 2.0 card, which seemed to work fine until I actually connected a device. Then I just got lots of errors in dmesg about the device refusing the number assigned to it or some such. I have had similar problems with USB 2.0 devices on Linux before, my current x86 server is running it's external storage via USB 1.1, since I was never able to figure out the problems I was having using USB 2.0. 
 
 I am considering trying firewire, but I have absolutely no experience with firewire other than hooking up a video camera for my step-father-in-law, so I am unsure about the problems I may run into using it. I am especially unsure about using firewire under Linux, especially with SPARC hardware, which does not seem to have the level of hardware support under Linux that x86 has - especially for third party hardware, such as a USB or firewire card. 

 My question is this: does anyone have any experience or recommendations about using firewire/usb external hard drives under Ubuntu/Linux on a SPARC, and if so, what hardware was used, and what issues were encountered, and what steps were needed to get the devices working?

---

### Post by netztier on 2007-05-21
> **prince_of_hackers said:**
> 
 My question is this: does anyone have any experience or recommendations about using firewire/usb external hard drives under Ubuntu/Linux on a SPARC, and if so, what hardware was used, and what issues were encountered, and what steps were needed to get the devices working?

According to sunsovle.sun.com, the Netra has an external SCSI Port. Sun used to sell external boxes that could hold a single SCSI drive with an 80pin SCA connector, or a SCSI CD or DVD drive, sometimes also a 5.25" DAT drive.

You could daisychain a range of these: [Sun Unipack Hard Drive on ebay]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=120122510293"), but you'll need a lot of 68pin SCSI cables - not cheap either. But they have the advantage that they can take thicker (1.6") drives, which come noticeably cheaper.

Or yo go bold and get something like this: [Sun A1000 Storage Array on ebay]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=160117591586") (see also [Sun A1000 Storage Array on sunsolve.sun.com]("http://sunsolve.sun.com/handbook_private/Systems/A1000/A1000.html")). Here' you'll need the slim 1" drives. You don't have to buy sun-labelled disks; I've been using 80pin SCA drives from Compaq Servers successfully in my Ultra Systems, all you need is a drive bracket to fit it into the drive bay.

The main downside with this kind of external boxes is that they both require 80pin SCA connectors on the SCSI disks. These are available on the aftermarket - but don't actually come cheap and not in large capacities. Filling an A1000 with 72GB disks will cost you an arm and a leg...

[I]Edit: beware.. I am still checking it out.. A1000 has integrated RAID functionality of which I am not sure if it can be configured and used with Linux. The D1000 is sold as "just a bunch of disks" box that holds the SCSI drives - which might be what is better for Linux, anway. I still haven't figured out if it is normal SCSI or Differential-SCSI that uses different electrical signals an requires a special controller...
[/I]

[I]Edit II: just spoke to the Sun Onsite Engineer here at work. Both A1000 and D1000 are **Differential-SCSI** boxes (HVD, High Voltage Differential SCSI), so you'll need a special controller to connect them that would also have to be supported by the Linux kernel. Sorry for misleading you here. 
Same difficulty with StorEdge T3 and the likes: these are FC-AL units and you'll need ad additional FC-AL controller for the Netra; some FC-AL controllers are supported in Linux, but you'll have to figure out which ones. This will make it even more expensive...
[/I]

*Edit III: Here's what's less cumbersome in the SCSI context: [Sun SPARCstorage Multipack on ebay](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=150101448682) and on [sunsolve.sun.com]("http://sunsolve.sun.com/handbook_private/Devices/Disk_Options/DISKOPT_StorEdge_MultiPk_18GB.html"). Holds up to six 80pin SCA disks with standard Sun brackets, and takes 1.6" drives (but should be happy with 1" drives too). *

best regards

Marc

---

### Post by prince_of_hackers on 2007-05-25
Thanks for the info. Sounds like SCSI is the way to go. However, I am afraid I do not have a very good working knowledge of SCSI - I have read about it, but found it very confusing. The only way I managed to get the right disks for the Netra was by ordering the same part number as the unit originally shipped with. 
 
 My next question then would be this: what kind of external SCSI does the Netra actually have? The Sun System Handbook just says 40-MB/sec, 68-pin, UltraSCSI (SCSI-3). I imagine more information would be available from Sunsolve, but I don't have an account for that.

---

### Post by netztier on 2007-05-28
> **prince_of_hackers said:**
>  My next question then would be this: what kind of external SCSI does the Netra actually have? The Sun System Handbook just says 40-MB/sec, 68-pin, UltraSCSI (SCSI-3). I imagine more information would be available from Sunsolve, but I don't have an account for that.

Well, that's pretty much all there is to say: UltraSCSI, with an 68pin connector (HD 68 mini). A sunsolve account is free, you just need to register - thats at least how I got mine (don't know if/when/how subscription policies might have changed) without actually having any support contract of any kind.

SCSI (see [Wikipedia on SCSI]("http://en.wikipedia.org/wiki/SCSI")) is not that difficult; it is a bus system with a daisychain of cables from first to last device - either the device has only one connector and you connect it to a flat ribbon cable (typically internal), or a device has two connectors, most often labelled "in" and "out" (typipcall external devices). Ultra SCSI with 16bit bus width (sometimes also called UltraWideSCSI) has a throughput of 40MBytes/s. 

Each device must have  a unique ID from 0-7 for "normal" SCSI and from 0-15 on so-called "Wide SCSI" - which is what we have here. The sequence of the devices on the daisychain is irrelevant - it's the ID that matters.

On some devices, you have to set the ID with jumpers (typically seen on CD or tape drives) or you have some dial to configure the ID on external harddisk enclosures. If you use harddisks with 80pin SCA connectors as you find them in most "Youngtimer" Sun systems, you don't have to worry about IDs - it's the slot number that determines the SCSI ID. 

Generally, first Harddisk is ID 0, second is ID1, CD-ROM is ID 6 and the SCSI Controller s ID 7. If on a common PC, a SCSI controller is detected, IDs 0 and 1 are mapped to the same addresses as the first two harddisks on the ATA controller - and therefore the PC will recognise them as devices that it can boot from.

It's very important to have proper termination at *both* the SCSI Bus' ends - either by setting a jumper on *only* the last device or by adding a small box to the last open connector of the cables (called a "SCSI Terminator"). Again, internal SCSI on a SUN has already taken care of this, there should be a terminater connected to the end of the flat ribbon cable.

The external connector is automatically terminated by the controller, unless you connect some device to it - then you must make sure that bus termination is activated - or connect an external SCSI terminator to the "out" port of the (last) external device.

best regards

Marc

---

### Post by netztier on 2007-06-27
> **netztier said:**
> 
*Edit III: Here's what's less cumbersome in the SCSI context: [Sun SPARCstorage Multipack on ebay](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=150101448682) and on [sunsolve.sun.com]("http://sunsolve.sun.com/handbook_private/Devices/Disk_Options/DISKOPT_StorEdge_MultiPk_18GB.html"). Holds up to six 80pin SCA disks with standard Sun brackets, and takes 1.6" drives (but should be happy with 1" drives too). *


After two weeks on searching on ebay for one of these, I remembered that my brother still had one down in the basement somewhere... DUH!

Then I talked six Compaq-labelled 36Gig 80pin-SCA disks (actually made by Fujitsu-Siemens) out of the buddy from the Server Team @ work, and grabbed some Sun disk brackets out of my Suns and voilà: 6x 36 Gig in a handy case. Runs fine on my PC-based server as well as with my Sun Ultra 60, both with Ubuntu. SCSI termination is easy; no external terminators, no switches; the box takes care of it itself :-)

Sun's original Part Number: 599-2231

best regards

Marc

---

### Post by prince_of_hackers on 2007-06-27
I researched the enclosures on Sunsolve, and Ebay, thanks for the tip about Sunsolve accounts being available at no cost now. It looks like this solution should work great for the project it was intended for, however, it may be awhile before I can implement it, due to the IT budget getting cut way back.

 One final question on the SCSI issue: Does the type of SCSI drive have to match the SCSI on the Netra, or does the box take care of that too? The manuals on Sunsolve didn't really say, but it seemed like as long as the drive type used the same number of pins, the box didn't really have much to do with it other than termination.

---

### Post by netztier on 2007-06-28
> **prince_of_hackers said:**
> 
One final question on the SCSI issue: Does the type of SCSI drive have to match the SCSI on the Netra, or does the box take care of that too? The manuals on Sunsolve didn't really say, but it seemed like as long as the drive type used the same number of pins, the box didn't really have much to do with it other than termination.

SCSI Disks are backward compatible - i.e. you can put a current Ultra320-SCSI Disk onto a UltraWide Bus (as we have here) and it will run - at slower speeds of course, but it will run. Serial-attached-SCSI (SAS) drives of the latest generation however won't work - different connectors, different signalling, different speeds.

The box takes care of termination, unless you connect more external SCSI devices behind the box - then you'll have to take care of it yourself. And it does take care of **SCSI ID assignment**. 

I haven't really seen many, but of those I have seen, all hardware implementations of SCSI with 80pin SCA connectors assign SCSI IDs based on the slot number you put the disk in.

The box has 6 slots and assigns 6 IDs; it has an external switch where you select if these should be SCSI ID 1-6 or 9-14, Given that you probably have internal SCSI disk(s) in the Netra with IDs 0-1, you'd better choose 9-14 here.

best regards

Marc, just ran out of disk brackets for my suns :-/

---

### Post by prince_of_hackers on 2008-05-22
OK, been awhile since I started this thread, but I finally picked up a Sun 711 Multipack hard drive enclosure, put six Seagate Cheetah 73GB hard drives in it, and hooked it up in my UltraSPARC server with a sym53c876 SCSI controller card. (the only cheap one I could find that had a driver for SPARC) One of the drives was bad, when I first turned it on, it sounded like an A10 at full throttle! Anyhow, after replacing the faulty drive, the Linux driver module recognized the sym53c876 (sym53c8xx driver) just fine, but it reported an error, "0x108, expected 0x100," and printed a message about checking cables and termination. The autoterm lights on the multipack enclosure are lit, and the SCSI card is supposed to autoterminate as well, although I am not sure how to check and verify that. I tried a different cable, tried the box with no drives to make sure it wasn't a drive problem, tried different ports on the SCSI card, and tried setting the termination on the card manually using the optional jumpers - the only change was with the jumpers, the driver error went from 0x108 to 0x20128 or 0x128, depending on how I set the termination and what connector I used. Anyhow, any ideas on what I might be doing wrong?

---

### Post by prince_of_hackers on 2008-05-26
> **prince_of_hackers said:**
> OK, been awhile since I started this thread, but I finally picked up a Sun 711 Multipack hard drive enclosure, put six Seagate Cheetah 73GB hard drives in it, and hooked it up in my UltraSPARC server with a sym53c876 SCSI controller card. (the only cheap one I could find that had a driver for SPARC) One of the drives was bad, when I first turned it on, it sounded like an A10 at full throttle! Anyhow, after replacing the faulty drive, the Linux driver module recognized the sym53c876 (sym53c8xx driver) just fine, but it reported an error, "0x108, expected 0x100," and printed a message about checking cables and termination. The autoterm lights on the multipack enclosure are lit, and the SCSI card is supposed to autoterminate as well, although I am not sure how to check and verify that. I tried a different cable, tried the box with no drives to make sure it wasn't a drive problem, tried different ports on the SCSI card, and tried setting the termination on the card manually using the optional jumpers - the only change was with the jumpers, the driver error went from 0x108 to 0x20128 or 0x128, depending on how I set the termination and what connector I used. Anyhow, any ideas on what I might be doing wrong?

OK, I think I might have this one figured out - I accidentally purchased the differential controller card instead of the single-ended version. (X6541A instead of an X6540A) In any case, I have now ordered the correct card, hopefully that will resolve the problem.

---

### Post by prince_of_hackers on 2008-06-08
OK, I have not had the chance yet to get out to install the new single-ended card in the SPARC. However, I did try hooking it up to an Adaptec aic7xxx single-ended card in a PC. The card doesn't have any pre-compiled drivers under Ubuntu SPARC, which is why I went with the sym53c8xx card, which does have built in drivers. In any case, the multipack and drives worked great, so that took care of my biggest worries, that the pack or cables weren't going to work. However, I did encounter a Linux kernel driver bug with the Adaptec card I have seen mentioned on a number of forums - the driver will not negotiate a speed any higher than 20mbps, even though the card and drives support up to 40mbps. Hopefully the Symbios card and driver do not share the same problem. I will post again once I try the new card with the SPARC drivers.

Relating to my original post in this thread, I recently acquired a Firewire external hard drive. I am thinking about borrowing a Firewire PCI card and trying it in either the Netra or the Ultra5, and see how it does - if I can get it working, Firewire external drives would be a much cheaper solution for using an old SPARC system as a small business file server.

---

### Post by bkortleven on 2008-06-25
If you still need an external SCSI box, I have a few lying around... unused.
You can choose which one you want ;)
Just PM or email me!

---

### Post by prince_of_hackers on 2008-06-28
OK, another update - I have not yet installed the new SCSI adapter, but I did try setting up a RAID array on the Multipack using the external SCSI connector on my Netra. The Netra uses a chipset very similar to the card I purchased, the 875 model instead of the 876. Anyhow, I should have seen this problem coming, but accessing all six drives across a 40mb/s bus has some seriously crappy performance issues.

---

### Post by prince_of_hackers on 2008-07-19
OK, more trouble with the software disk array. I installed the new SCSI card in the Ultra 5, hooked up all the drives, and everything seemed to be working fine. I erased each of the drives, and partitioned each one with a Sun disklabel and a single Linux raid partition. I then used mdadm to create a RAID 5 array, it took about 5 hours to rebuild the array. I formatted the new array with an ext3 filesystem, and then mounted it. I created an mdadm.conf listing the devices and arrays, and made sure the system startup was set to assemble the array on bootup. I also made an entry in the fstab file to mount the array. I was able to copy files to the array with no problem, however, the problem occurs when I reboot - some startup task apparently decides to rebuild the array on every reboot!!! At first, I thought I had tracked it down to evms (enterprise volume management system) which is installed on Ubuntu by default and apparently is an alternative to mdadm. However, I modified the configuration file for evms to tell it to ignore all drives, and that seemed to fix it for one reboot, but now it is doing it again! Does anyone have any idea what the problem might be here?

---

