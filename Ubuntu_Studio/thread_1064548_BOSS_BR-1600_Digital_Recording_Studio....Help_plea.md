---
title: "BOSS BR-1600 Digital Recording Studio....Help please?"
date: 2009-02-08
forum: Ubuntu Studio
---

### Post by BHermus on 2009-02-08
I own a BOSS BR-1600 Digital Recording Studio and I am having problems trying to export my completed songs to my laptop running Ubuntu Studio 8.10.  The laptop is a Dell Inspiron 1420.

In a nutshell I suppose I'm asking how to accomplish the task at hand.

Here's what happens:  On my device (the br-1600) I select the USB function. From there I select EXPORT and then I select the tracks I would like to export to my laptop (ex Tracks 9/10 - 2 ...my completed and mastered song).  At that point my device writes the file and prepares it for the transfer as a WAV file.  It then attempts to connect to the computer through USB.

What is supposed to happen at that point is similar to adding a thumb drive or an external usb drive... I am supposed to be able to navigate and find the correct folder and file to copy over to the laptop from the device.

What actually happens is an error on my device and no changes on the laptop.

Is there anyone out there who can help me? I will be greatly appreciative!

Thank you in advance!

---

### Post by sgx on 2009-02-09
> **BHermus said:**
> I own a BOSS BR-1600 Digital Recording Studio and I am having problems trying to export my completed songs to my laptop running Ubuntu Studio 8.10.  The laptop is a Dell Inspiron 1420.

In a nutshell I suppose I'm asking how to accomplish the task at hand.

Here's what happens:  On my device (the br-1600) I select the USB function. From there I select EXPORT and then I select the tracks I would like to export to my laptop (ex Tracks 9/10 - 2 ...my completed and mastered song).  At that point my device writes the file and prepares it for the transfer as a WAV file.  It then attempts to connect to the computer through USB.

What is supposed to happen at that point is similar to adding a thumb drive or an external usb drive... I am supposed to be able to navigate and find the correct folder and file to copy over to the laptop from the device.

What actually happens is an error on my device and no changes on the laptop.

Is there anyone out there who can help me? I will be greatly appreciative!

Thank you in advance!
First, 8.10 is a bit buggy, 8.04 is the better choice. For now, you may want to play the song on the 1600, and simply record it by cables on your ubuntu system while it plays, and in 24bit if possible, giving some extra headroom for further processing. Use ardour or audacity to record the line-level output from the BR. I have done this with output from Tascam box-studios, no problems.
The Roland usb transfer may require windows, so a wubi install of 8.04 may simplify things, with a usb-stick as go-between, or use ntfs tools to transfer your mastered .wav files to Ubuntu.
A more traditional dual-boot using xp, with a shared fat32 partition for file sharing is a workable option also. 
An M-Audio usb Transit device has digital i/o for $70, and may work well for quiet digital transfers between your setups.
Good luck!

---

### Post by liamnixon on 2009-02-09
I feel your pain.  I'm having the same problem, though I'm running Fedora and haven't tried it on that distro yet.  Maybe I should.

---

### Post by BHermus on 2009-02-18
I dropped more money on my BR-1600 than I normally like to spend at once and I stopped using M-Audio Devices five years ago to move away from computer recording.... all I want is to get my music from my BR-1600 to my computer for archiving and backup purposes through USB -- *without using windoze or spending more money*

---

### Post by laughzilla on 2009-02-22
is there a solution to this yet? 

i am having the same problem with my boss br-1600 connecting via usb to my ubuntu 8.04 box. similarly, this mixer connects fine to windows boxes. i just need it to connect to ubuntu in this case.

---

### Post by steveneddy on 2009-02-22
Can you use a Flash drive for this task?

You know, until you get it figured out?

EDIT:

or maybe a large USB powered external hard drive?

---

### Post by laughzilla on 2009-02-22
thanks, steveneddy :)

i actually do have a usb external drive that has enough space on it. in order to try that very slow method, i will have to get one of those cables that connects those two ends, since it's not a standard usb cable that would fit from the squareish end to the small trapezoid end.

any other ideas / solutions about this? :)

---

### Post by DigitalTreant on 2009-02-23
The BR1600 is a pretty good portable recorder.  I too have tried connecting it to my computer running Ubuntu, simply to have the recorder lock up.  thing is, if ubuntu can mount my NTFS windows disk and read every file, I don't see how it can't communicate with the BR1600.  I think it must be how the software in the BR1600 is written.  I have the latest updates from Boss too and still no dice.  The only thing I could think to do is export t9/10 to a CD in a raw format and get it into Ubuntu that way.  Or from my Windows disk:(

---

### Post by liamnixon on 2009-03-04
The BR-1600 may have it's own file system.  It seems like I read of another recorder that had a file system (like reiserfs or ext3) unique to the device.  :?:  I'll have to look into it some more.

---

### Post by kayosiii on 2009-03-05
run the command dmesg (from terminal) after connecting up the BR-1600 and post the last page or so of output here....

---

### Post by robhank on 2009-03-05
I have hooked up an external hard drive to my Boss recorder. What are the steps on the recorder so I can record to the external hard drive? I cannot figure it out
Thanks

---

### Post by liamnixon on 2009-03-05
Here is the dmesg output on my computer (don't know why I didn't think about that).  Bear in mind, though, that I'm not on Ubuntu.  I'm using Slackware

```
usb 7-1: new low speed USB device using uhci_hcd and address 2
usb 7-1: configuration #1 chosen from 1 choice
input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/input/input8
input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.2-1
usb 7-1: New USB device found, idVendor=046d, idProduct=c50e
usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 7-1: Product: USB RECEIVER
usb 7-1: Manufacturer: Logitech
usb 7-1: USB disconnect, address 2
usb 7-1: new full speed USB device using uhci_hcd and address 3
usb 7-1: configuration #1 chosen from 1 choice
scsi5 : SCSI emulation for USB Mass Storage devices
usb 7-1: New USB device found, idVendor=0582, idProduct=0068
usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 7-1: Product: BR-1600CD USB function
usb 7-1: Manufacturer: BOSS Corp.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
scsi 5:0:0:0: Direct-Access     BOSS     BR-1600CD        1.00 PQ: 0 ANSI: 0
sd 5:0:0:0: [sdb] Attached SCSI removable disk
sd 5:0:0:0: Attached scsi generic sg1 type 0
usb-storage: device scan complete
sd 5:0:0:0: [sdb] 78165361 512-byte hardware sectors (40021 MB)
sd 5:0:0:0: [sdb] Write Protect is on
sd 5:0:0:0: [sdb] Mode Sense: 40 00 80 00
sd 5:0:0:0: [sdb] Assuming drive cache: write through
sd 5:0:0:0: [sdb] 78165361 512-byte hardware sectors (40021 MB)
sd 5:0:0:0: [sdb] Write Protect is on
sd 5:0:0:0: [sdb] Mode Sense: 40 00 80 00
sd 5:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1

```

It appears to recognise the device, but it hangs for some reason.  I tried mounting it manually, but no go.

EDIT: Sadly this is the only reason I still have a Windows partition. ;)

---

### Post by liamnixon on 2009-03-13
Bump?

---

### Post by radi0j0hn on 2009-03-13
Hope you have it fixed by now!  I have a Tascam Portastudio and it took me a long time to wrap my head around similar functions.  On my machine, "Export" does not move the file to the PC.  It saves the track as a WAV file separate from the mix.  THEN you activate the USB command and find the folder that appears on your PC.

So I am wondering if you have the steps out of order regarding the "export" function.  Have you mixed down the song?

---

### Post by kayosiii on 2009-03-13
ok the device seems to be showing up correctly
What error message does it give when you try to mount it manually (try both /dev/sdb and /dev/sdb1 to mount)
What file system does this device use? you may need to specify it manually... eg

sudo mkdir /media/br-1600
mount -t vfat /dev/sdb1 /media/br-1600

---

### Post by soldanovht@yahoo.com on 2009-08-18
hi,i  have the br 1600cd i shut the unit down as i always have but this time when i turned it on  half of my marked songs were  gone.   can some one help.   i hope     thx.    [EMAIL="soldanovht@yahoo.com"]soldanovht@yahoo.com[/EMAIL]

---

### Post by FULLARMOUR on 2009-12-17
I wonder why rolandcorp  does not have a program for the computer that would intergrate with the boss br1600 ?  or possibly open the boss files up and read them .
i hate waiting all day for the files to load on my computer only to find out that they are usless unless they are in the recorder or am i missing something??????:guitar:

---

### Post by sgx on 2009-12-18
> **FULLARMOUR said:**
> I wonder why rolandcorp  does not have a program for the computer that would intergrate with the boss br1600 ?  or possibly open the boss files up and read them .
i hate waiting all day for the files to load on my computer only to find out that they are usless unless they are in the recorder or am i missing something??????:guitar:
A lot of external recorders use proprietary formats, requiring their own procedure to export through a cable. If you can play the file on the BR1600, connect its line-out into your soundcard line-in and record it at high resolution.
Cheers

---

### Post by wwweeeee on 2010-05-03
[SIZE=3]HEY EVERYBODY .. [SIZE=2]I THINK I HAVE A SOLUTION ...

GO TO TOP SOUND PRODUCTIONS ... THEY SELL A PROGRAM CALLED A WAV-MAKER-1600 ... IT WORKS WELL WITH SONAR 8 ...
TRANSFERING FILES FROM THE BR TO YOUR COMPUTOR IS FAST ..
CHECK IT OUT 
PS ... I HAVE NO AFFILIATION WITH THEM ... JUST A FAN ..


WWWEEEEE:popcorn:
[/SIZE][/SIZE]

---

