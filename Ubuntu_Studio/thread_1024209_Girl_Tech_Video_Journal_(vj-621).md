---
title: "Girl Tech Video Journal (vj-621)"
date: 2008-12-28
forum: Ubuntu Studio
---

### Post by xefialtis on 2008-12-28
I searched on Ubuntu Forums to see what I could find...and got bunkus...

What I need to know is how to make my 11 year old girl happy...keep Ubuntu, or go back to Windows...
Since *I* don't wanna go back to Windows, I want to find a way to get this stupid thing working on Ubuntu...

To diagnose this, just tell me what you need...so far...I have this from the syslog...

> 
Dec 28 16:32:38 family-machine kernel: [103417.579917] usb 3-2: new full speed USB device using uhci_hcd and address 5
Dec 28 16:32:39 family-machine NetworkManager: <debug> [1230507159.086558] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_979_227_noserial'). 
Dec 28 16:32:39 family-machine kernel: [103417.764342] usb 3-2: configuration #1 chosen from 1 choice
Dec 28 16:32:39 family-machine NetworkManager: <debug> [1230507159.196226] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_979_227_noserial_if0'). 


---

### Post by Stochastic on 2008-12-29
what's the output of lsusb?

---

### Post by djbushido on 2008-12-29
what are the error messages? the syslog personally doesn't tell me anything unless I have a context. and yes, lsusb will help too.

---

### Post by xefialtis on 2008-12-29
Thank you guys for even taking a look...I can get all the things you ask for, I am not unfamiliar with Linux, but I am unfamiliar with DEBUGGING issues in Linux...

> 
:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0979:0227 Jeilin Technology Corp., Ltd 
Bus 003 Device 002: ID 050d:0805 Belkin Components Nostromo N50 GamePad
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


Thanks!

---

### Post by djbushido on 2008-12-29
Okay, so stupid question: what specifically is the problem?
Also, what error messages show when running the application/interface that is the problem?
Also also, have you tried running the program from terminal? this might also produce valuable debug info.

---

### Post by xefialtis on 2008-12-29
When I try to use any of the applications that allow access to a digital cam, digikam, gphoto, etc...they all say that there is no camera detected.

None of the other methods or programs give any specific error, nothing like "your driver is broken"...just that they cannot find a digital camera.

I found other threads out there that deal with this camera, and I installed every one of the programs they suggested to get a workable driver, and still no luck.

---

### Post by Stochastic on 2008-12-29
Is nautilus (or any other file browser) able to see/browse the camera's memory?  If so, then you just need to find where the photos are stored and copy them to your harddrive.

---

### Post by xefialtis on 2008-12-30
Unfortunately, no, I cannot see or find this device in any of the file browsers...

---

### Post by zika on 2008-12-30
> **xefialtis said:**
> Unfortunately, no, I cannot see or find this device in any of the file browsers...
did You try to get a driver for that device? System->Administration->Hardware drivers ...
(I've never used cameras myself so this is just a shot in the dark)

---

### Post by djbushido on 2008-12-30
okay, i am going to try and diagnose output:
on lsusb, the system isn't recognizing the camera. plain and simple (i assume it is just the jeilin technology entry?). This could be because its memory is inside the actual device. don't know.
also:how have you been trying to access it? have there been error messages, etc.? If so, try doing the same thing only running commands from terminal and post the results.
also also:can you list devices for me?
```
sudo fdisk -l
```

---

### Post by xefialtis on 2008-12-30
I have tried to find drivers via Ubuntu and other resources, there doesn't appear to be one that works.

the output for sudo fdisk -l:
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdc68e12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1221     9807651   83  Linux
/dev/sda2            1222       19457   146480670   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f98432

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1221     9807651   82  Linux swap / Solaris
/dev/sdb2            1222       19457   146480670   fd  Linux raid autodetect

Disk /dev/md0: 149.9 GB, 149996109824 bytes
2 heads, 4 sectors/track, 36620144 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


It isn't recognizing this device at all.

What I think I will do is add a VMWare install of Windows, and show my daughter how to use that...
She would then be able to use her stuff, and this solves this problem without trying to figure out a POS camera. 
My wife bought it for her, and if it were up to me, we would have gotten her a small "real" digital camera...one that, at a minimum, would be recognized by Linux as an external storage device...(or at least, have removable memory card)...

Thanks for the help, but at this point, I think this is a lost cause...unless someone has a break through and finds the answer somewhere...but I did spend a lot of time looking...

No sense in continuing to waste everyone's time on this...

---

### Post by djbushido on 2008-12-30
first of all, use VirtualBox, not VMWare.
```
sudo apt-get install virtualbox-ose
```
second, can you use the other software via wine? ie, try installing product via wine to c:, then run programs etc.
Also-how big is the journal? 149 gb? that's huge for a journal!
Anyway, try the wine solution, but if that doesn't, then _virtualbox_ is probably the way to go.
Sorry for not being able to help much.

---

### Post by thorgal on 2008-12-30
I have not had camera problems for a while but IIRC, cameras I used were not systematically detected and I had to do it by hand. I remember digikam providing the possibility to define a camera if automatic does not work. You plug your cam via USB so there are a few options :

1- it is seen as a storage device, in which case the command dmesg from a terminal should show you something relevant when you hotplug your cam. Type dmesg before you plug it, and after you do it. Post the diff.

2- some USB cameras use something like PTP mode (again, it's from memory, could be different), regardless of their brand/model.

3- digikam should come with a set of drivers (gphoto2 or something like that). Check what's in this list (when you define your cam in digikam, a list of drivers should show up). If it's not in there, if your cam is neither a storage dev nor is a PTP class cam, then I don't know where to go from there.

I forgot one thing: it could well be a permission problem. I think you could use gphoto2 from a terminal to check a few things :

```

gphoto2 --auto-detect

```

does it spit out something ?

that guy ([https://answers.launchpad.net/digikam/+question/6201](https://answers.launchpad.net/digikam/+question/6201)) had a root permission problem, you can maybe get some hint from this msg ?

---

### Post by 4ebees on 2009-01-08
> **xefialtis said:**
> <snip>
She would then be able to use her stuff, and this solves this problem without trying to figure out a POS camera. 
My wife bought it for her, and if it were up to me, we would have gotten her a small "real" digital camera...one that, at a minimum, would be recognized by Linux as an external storage device...(or at least, have removable memory card)...


Maaaaaaaaaaate :)

I think my wife and your wife must have been shopping at the same place :P

I know exactly the camera you're talking about. My wife jumped in a bought this 'device' for our youngest and I'm having exactly the same problems as you.

If I find out anything, I'll certainly let you know.

Best of luck

---

