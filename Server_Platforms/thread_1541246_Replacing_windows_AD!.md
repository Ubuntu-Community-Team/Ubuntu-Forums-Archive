---
title: "Replacing windows AD!"
date: 2010-07-28
forum: Server Platforms
---

### Post by lloyd_987 on 2010-07-28
Hi all. I have been using Windows Server 2003 R2 for a long time to manage user login's and allowing the user to access ONLY THERE information from whatever PC they are on in the house (i.e a typical school set-up without the heavy restrictions). 

However now I have had to replace the server and for some unknown BLOODY reason STUPID windows is not detecting my hard drive in the install, then only tells me to exit, THANKS!! 

I have been shown a linux server with a collection of programs that allow windows machines to connect (and log in) to the server and access user files, as it would be if it were a windows server. 

So basically I want to be able to replicate Windows Active Directories and sharing user files (WITH ONLY THE LOGGED IN USER!!) Anyone know how this is done?

Thanks all =]

---

### Post by CharlesA on 2010-07-28
It's not possible to directly replace an AD DC in Samba 3. Samba 4 is supposed to have that capability, but it's not officially released yet.

As for why Windows 2K3 isn't detecting the hard drive. You probably need the SATA drivers for the motherboard or switch it to use IDE mode instead of ACHI.

The users would need to authenticate to a separate DC then have the same password in Samba, which would be a pain in the butt to keep synchronized.

---

### Post by lloyd_987 on 2010-07-28
Do you think it would be okay to use even though its alpha stages or not stable enough yet?? I believe that is why too, I have a hdama rev g motherboard Dual 2.4ghz AMD Opteron, 4GB RAM and 500GB SATA drive. I have looked all over the internet for the driver but can find nothing!! Really need this running soon!!

---

### Post by CharlesA on 2010-07-28
I wouldn't use it tbh. I don't know how stable it is, but if it's still in alpha, it's not ready for production.

Check here: [http://www.rioworks.com/server/Product/ViewDownload.asp?View=HDAMA%20rev.G](http://www.rioworks.com/server/Product/ViewDownload.asp?View=HDAMA%20rev.G)

The driver you probably need is the one listed under: Silicon Image's Serial ATA driver for Windows 98/ME, NT4.0, 2000, XP, 2003

I could be wrong, but given the info you gave, that is the most likely driver.

---

### Post by lloyd_987 on 2010-07-28
I will leave it for now then.. will keep trying on this! However... (sounding thick here!!) how do i install the drivers if I have no OS. Do I write them to CD then boot from that? 

If so which file(s)/folder(s) do I burn?

---

### Post by CharlesA on 2010-07-28
You can use nlite to create an integrated install cd or use a floppy disk to install the driver during setup.

I prefer the [nlite]("http://www.nliteos.com/") approach since the machines I have don't have floppy drives (and Server 2K3 only accepts 3rd party drivers from floppy, not usb)

Depending on if it's a 32-bit or 64-bit install, it will either be the win32 or 64-bit driver.

It's easier to just integrate the driver on the install media tho.

---

### Post by lloyd_987 on 2010-07-28
> **CharlesA said:**
> You can use nlite to create an integrated install cd or use a floppy disk to install the driver during setup.

I prefer the [nlite]("http://www.nliteos.com/") approach since the machines I have don't have floppy drives (and Server 2K3 only accepts 3rd party drivers from floppy, not usb)

I tried that program earlier and it didnt seem to work... all i am able to use on this server is a CD/DVD or USB. Anyway I have just downloaded the drivers and in the readme.txt it says:

--------------------------------------------------------
1) Windows XP or Windows Server 2003 Fresh Installation
--------------------------------------------------------
Follow the instructions in this section if you are performing a new
installation of Windows XP or Windows 2000/XP, and you wish to
boot from a device attached to the SiI 3114 controller.


1. Power off the system.  Connect the hard drives to the SiI 3114
   controller and insert the controller into a PCI slot. Power up
   the system.

2. Put your Windows XP or Windows Server 2003 CD into the CD-ROM/DVD drive.

3. Press F6 for third party SCSI or driver installation at the beginning
   of text mode installation.  Press 's' when setup asks if you want to
   specify an additional device, and insert the diskette labeled
   'Silicon Image SiI 3114 SATARaid Driver Installation Disk'.
   Press 'Enter'. From the menu presented next, select 
   'Silicon Image SiI 3114 SATARaid Controller'

4. Press 'Enter' again when prompted to continue on with text mode setup.

5. Follow the setup instructions to select your choice for
   partition and file system.

6. After setup examines your disks, it will copy files to 
   Windows installation folders and restart the system.  
   The setup program will continue and finish the installation
   after restart.

7. Wait until Windows finishes installing devices, regional
   settings, networking settings, components, and final set of 
   tasks, reboot the system if it is required.  

8. See instructions in section 4 to verify controller was installed
   correctly.

So by the looks of things it will install the OS then ask for the files that come in the download :S... ill give it a go tomorrow as it is now 4am and need to be up at 7am =]

---

### Post by CharlesA on 2010-07-28
You will still need a floppy disk to put the drivers on, Win 2003 server won't see anything else.

Where did you have problems with nlite?

---

### Post by kevinthecomputerguy on 2010-07-29
Keep hitting the "F6" key on your keyboard as the windows cd is booting, you will eventually be asked for a floppy, then follow what CharlesA said. A USB external floppy drive will work too. Your after the hard drive controller driver, thats what needs to be on the floppy. CharlesA talks about this is step #3 above. A quick rule of thumb when looking for the driver, if its larger than 1.4MB, its the wrong driver.
-Kev

---

### Post by HermanAB on 2010-07-29
Howdy,

Win2003 runs beautifully in a VMware Player and Virtualbox VM.  I never ever install Windows servers on the bare metal anymore.  The Microsoft device driver support is just way too crappy and backing up and copying VMs is so much easier.

---

### Post by CharlesA on 2010-07-29
> **HermanAB said:**
> Howdy,

Win2003 runs beautifully in a VMware Player and Virtualbox VM.  I never ever install Windows servers on the bare metal anymore.  The Microsoft device driver support is just way too crappy and backing up and copying VMs is so much easier.

Didn't even think about that, that's a really good idea.

---

