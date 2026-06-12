---
title: "&quot;No bootable medium found&quot; in virtualbox (and I've google other &quot;solutions&quot;)"
date: 2017-04-09
forum: Virtualisation
---

### Post by david503 on 2017-04-09
I'm using virtualbox to try and create a windows virtual machine, installed from a bootable windows dvd iso files.  Actually, I've tried two- one is windows 8.1, one is windows 7.  In both cases I get  "No bootable medium found!"  I'm doing this:

[http://askubuntu.com/questions/64915/how-do-i-install-ubuntu-on-a-virtualbox-client-from-an-iso-image](http://askubuntu.com/questions/64915/how-do-i-install-ubuntu-on-a-virtualbox-client-from-an-iso-image)

Nothing I've found in my googling works.  Still getting no bootable medium found.  I even tried the ubuntu iso and it won't even boot into that.

I'm running 16.04 TLS, on a pc that's less only a year old, same drive I used with windows, no problems with that. Virtualbox 5.03_ubuntux64

(Oh btw I'm a LAMP developer for 15 years, so get as technical as you want with me)

thanks

---

### Post by deadflowr on 2017-04-09
What's the boot order settings in vbox?

---

### Post by david503 on 2017-04-09
> **deadflowr said:**
> What's the boot order settings in vbox?

That's a great question- so I just changed it to:  

Optical
Hard Disk

Still no go.

Also, when it tries to boot it says "press F12 to select boot device" and when I do that and choose cdrom, I get: "Fatal: Could not read from the boot medium! System halted."

---

### Post by deadflowr on 2017-04-09
I guess the next step would be to try and verify the iso image from Microsoft.
Though, I have no  clue as to how microsoft does this.
(Typically, at least with various linux flavors, you can access the checksum associated with the file and then run the checksum command to see if what you have matches what the image has.
Checksum is part security but more over about integrity as more image problems are likely of the corrupted download variety.)
How it's done on Ubuntu:
[https://www.ubuntu.com/download/how-to-verify]("https://www.ubuntu.com/download/how-to-verify")
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")
at least

Also of note, if the iso is an OEM image, then it more likely is because OEM are set for specific hardware, and if they do not see the correct hardware at start up they will fail.
And vbox hardware specs are different than whatever the machine it is running on.

---

### Post by david503 on 2017-04-09
> **deadflowr said:**
> I guess the next step would be to try and verify the iso image from Microsoft.
Though, I have no  clue as to how microsoft does this.
(Typically, at least with various linux flavors, you can access the checksum associated with the file and then run the checksum command to see if what you have matches what the image has.
Checksum is part security but more over about integrity as more image problems are likely of the corrupted download variety.)
How it's done on Ubuntu:
[https://www.ubuntu.com/download/how-to-verify](https://www.ubuntu.com/download/how-to-verify)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
at least

Also of note, if the iso is an OEM image, then it more likely is because OEM are set for specific hardware, and if they do not see the correct hardware at start up they will fail.
And vbox hardware specs are different than whatever the machine it is running on.

ooohh right, right. Well, but.... it won't even work from the same ubuntu iso that I just used to install ubuntu like 2 weeks ago- (I mentioned that in the op post).  So even when MS is out of the picture I still get the error.   I mean I'm willing to run a checksum if you really want, but... unless it randomly got corrupted inside of two weeks..... unlikely, right.  (Everything else on that drive is fine btw.)

See what I'm saying... so, ubuntu is running great from the same iso (I'm in it right now)... just not in the virtual box.  

ugg

---

### Post by efflandt on 2017-04-09
Typically to add an iso file under Settings > Storage you find Controller: IDE that shows an Empty disk. If you click on that "Empty" disk, there will be a disk with drop down arrow on the far right next to "IDE Secondary Master. If you click on that disk you can either select iso files that you have used before or "Choose Virtual Optical Disk File..." to pick a new file not on the list. Then the name of the iso file you selected should show up where the disk said "Empty" before.

Note that it will only boot that iso once, then the disk will be Empty again unless you check the box for "Live CD/DVD" to keep the iso in the drive.

I have only virtualbox to install from various Ubuntu iso files (because Linux WebEx is a 32-bit only java app), tinycorelinux (to see what that was, used in overpriced all-in-one PC a friend was looking at), and Debian (which someone else had trouble with in vbox, worked fine for me).

---

### Post by david503 on 2017-04-10
Mine only shows Controller:SATA on the list, not IDE.  (See attached)

Y'know- if I could get this to work it would solve all my problems and plus I'd have a second monitor using my laptop: [https://youtu.be/W9gAlqCX5Lw?t=3m2s](https://youtu.be/W9gAlqCX5Lw?t=3m2s)


d

---

### Post by deadflowr on 2017-04-10
You should be able to add an IDE controller just by right clicking in the controller window and selecting add IDE controller.
(or click the add controller icon at the bottom of said window)
If that is where the problem lies.

---

### Post by efflandt on 2017-04-11
I thought it looked like the attached by default, but you can add the IDE: Controller with the diamond+ at the bottom, and with that controller highlighted can add the Empty disc with the floppy+ at the bottom. Then my earlier reply would make more sense to you. Note that if you add the GuestAdditions, that iso would show up as the optical disc.

---

