---
title: "Toasted SD Card"
date: 2006-03-23
forum: The Cafe
---

### Post by caspian on 2006-03-23
I copied some files to my SD card (Using a Sd-to-USB adapter -- it mounts the SD card as a usbdisk). Then, I unmounted it by right-clicking the icon on the desktop and clicking "Eject".

Then, Gnome brought up the "Please wait -- Unmounting device" message. It stayed that way for about 10 minutes, so I figured it must have locked up. (I'm using the Dapper beta release) So, I killed the window and pulled out my SD card.

I guess that was a mistake -- I plugged the card into my Palm Pilot and it recognized that I had just inserted an SD card, but it couldn't access it. The same thing happened when I plugged it back into my computer... and the same thing when I plugged it into a Windows machine

Did I just fry my SD card? Is there any way I can recover it (or factory reset it?)

Thanks to anyone who can help me!

---

### Post by stuporglue on 2006-03-23
Can you reformat it? I guess that's what you're looking for.

There's probably a good GUI way to do this, but here's the CLI way, if you like...Take care not to recklessly format stuff. :)

Status: SD card not in computer

$ dmesg
(bunch of output)

Plug in SD card

$ dmesg
(bunch of output)

See what the difference between the two dmesg outputs is. It should tell you that your SD card got connected somewhere, maybe /dev/sda or something similar. 

Create a new partition table:
sudo fdisk /dev/sda  (sda will be replaced with whatever it showed up as!)
Type the letter "o" (lower Oh) and hit enter. This creates a new partition table
Type the letter "n". This will create a new partition. I think if you accept the default values, it'll create one large partition -- which is what you want. You might have to enter a partition number, if you do, put "1"
Type the letter "w". This writes the new partition table to the disk. 

Format the newpartition:
sudo mkfs.vfat /dev/sda1  

Unplug the SD disk, then plug it back in after a moment. Hopefully it works!

---

### Post by caspian on 2006-03-23
Thanks for your reply :D

Ok, I ran dmesg and this is the output I got:

```

...
[4380025.176000] sda: Mode Sense: 02 00 00 00
[4380025.176000] sda: assuming drive cache: write through
[4380025.179000] sda : very big device. try to use READ CAPACITY(16).
[4380025.179000] sda : READ CAPACITY(16) failed.
[4380025.179000] sda : status=0, message=00, host=5, driver=00
[4380025.179000] sda : use 0xffffffff as device size
[4380025.179000] SCSI device sda: 4294967296 512-byte hdwr sectors (2199023 MB)[4380025.181000] sda: Write Protect is off
[4380025.181000] sda: Mode Sense: 02 00 00 00
[4380025.181000] sda: assuming drive cache: write through
[4380025.181000]  sda:<6>usb 4-4: USB disconnect, address 17
[4380025.427000] sd 3:0:0:0: SCSI error: return code = 0x10000
[4380025.427000] end_request: I/O error, dev sda, sector 0
[4380025.427000] Buffer I/O error on device sda, logical block 0
[4380025.429000] sd 3:0:0:0: SCSI error: return code = 0x10000
[4380025.429000] end_request: I/O error, dev sda, sector 0
[4380025.429000] Buffer I/O error on device sda, logical block 0
[4380025.429000]  unable to read partition table
[4380025.430000] sd 3:0:0:0: Attached scsi removable disk sda
[4380025.430000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[4380025.432000] usb-storage: device scan complete
[4380030.000000] usb 4-4: new high speed USB device using ehci_hcd and address 1 9
[4380030.120000] scsi4 : SCSI emulation for USB Mass Storage devices
[4380030.121000] usb-storage: device found at 19
[4380030.121000] usb-storage: waiting for device to settle before scanning

```

Ok, it says "Attached scsi removable disk sda". So, I guess the location is /dev/sda. I also did "ls /dev/s*" and sda is the only one that showed up -- so it's gotta be sda.

I punch in "sudo fdisk /dev/sda" and it just hangs -- as if it's waiting for something. I waited for a while for a prompt to come up... but nothing. So, I went ahead and typed:
```

o
n
--
w

```

And still nothing happened -- the program didn't quit, didn't display any output...

So, I opened a new terinal window and ran "sudo mkfs.vfat /dev/sda1". It said "mkfs.vfat 2.11 (12 Mar 2005)" and then just hung there.

As soon as I pulled out my SD card reader, fdisk outputted "Unable to read /dev/sda" and died. mkfs.vfat outputted "mkfs.vfat: unable to open /dev/sda" and died.

I made sure that the lock switch is off on my SD card -- I'm really not sure what to try next.

Does this mean that my SD card has received its death sentance? ;)

---

### Post by stuporglue on 2006-03-24
> Does this mean that my SD card has received its death sentance? 

Hmm.. that "Waiting for Device to settle before scanning" is interesting...I'm not quite sure what to make of it. I'm guessing that's why you can't fdisk or mkfs it though. 

Here's the two things I'd try before giving up: 

1) How big is the disk? Find a file that's the same size or slightly smaller and try to dd it to the disk. Put the disk in and see where it gets attached, then 

sudo dd if=/path/to/some/file of=/dev/sdFOO

dd takes a while to run, you can use "top" in another terminal to watch that it's still running. 

My idea with this one is that if the device is physicly ok, but the partition tables are messed up just enough to make Ubuntu barf, it'll overwrite the tables. 

2) Try putting it into a Windows (or OSX) computer. And formatting it there
Maybe one of those will say "invalid disk, want to format?"...

After that, I'm out of ideas.

---

### Post by ssam on 2006-03-24
can you reformat it from the palm?

sounds like it died before you ejected it the first time. the message would not go away because it could not write to the card.

---

### Post by mcduck on 2006-03-24
you should turn off automounting of removable devices before you plug it in. You can't repartition a mounted disk (or a disk your system is trying to mount) :)

(System/Preferences/Removable Drives and Media)

After you've done that, plug the card in and try the fdisk again..

---

### Post by caspian on 2006-03-25
Everyone, I really appreciate how you all have tried to help me out with my SD card. Unfortunately, however, I still can't get it to work.

It's really strange -- I can talk to it using "dd", I can transfer files to it, I can zero it out, but I can't seem to format it or repartition it. Hmm... strange. Maybe the card is physically bad.

Nevertheless, I really appreciate how you all have helped me out. Thanks!

---

### Post by caspian on 2006-03-27
Well, As I stated in my above post, I've given up on my SD card :( 

I researched some more, tried some other things... but I just can't seem to bring it back to life.

If any of you gurus want to take a shot at it, I'll send the SD card to you for free (I'll pay of the stamp ;)) -- it's better than me throwing away a SD card that could someday become whole again :D

---

### Post by borris.morris on 2007-11-22
> **caspian said:**
> Well, As I stated in my above post, I've given up on my SD card :( 

I researched some more, tried some other things... but I just can't seem to bring it back to life.

If any of you gurus want to take a shot at it, I'll send the SD card to you for free (I'll pay of the stamp ;)) -- it's better than me throwing away a SD card that could someday become whole again :D

soo... say if we did get it working, we'd send it back to you, right?

---

### Post by caspian on 2007-11-22
Well, I was planning to give it away... but I threw it away after a year ans no one had replied :(. Sorry, I don't have it anymore.

---

