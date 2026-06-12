---
title: "PSA to people new to server hardware"
date: 2020-05-07
forum: The Cafe
---

### Post by Tadaen_Sylvermane on 2020-05-07
I recently picked up an older model Intel server with a Xeon E3 1225. The machine works great. But I didn't know some things about how servers handle boot processes. Today I decided to reboot because no one was here, and while everything was working just fine I didn't know if it would come right up like it was supposed to. Suffice it to say it did not. I spent an hour chasing the issue, at first thinking network issues, changed cables, all sorts of things. What made this odd was it worked fine when I brought it to my living room tv and tested there. As soon as I put back in the guest room headless though, nothing.

Ultimately I landed on boot order and it wanting to boot from usb. As I have 2 usb 3.0 drives for my snapraid parity it seems that it was getting stuck on trying to boot from them, and never finishing the boot process. I disabled all usb boot options, cleared the boot priority list of all but the drive i have for my os and network booting. A couple full reboot tests later and all is well. I've never seen an issue deciding which device to boot when usb is concerned. I'm guessing something is different about server specific gear, in this case the way it boots itself. This problem may or may not happen to you. 

TLDR: If you are new to actual server hardware, make sure to read up on it before assuming you know what it's gonna do. I did not, and it cost me over an hour of chasing this issue when it could have been solved in less than a minute when I first set this machine up.

---

### Post by mastablasta on 2020-05-08
same here on HP ProLiant N40L. the thing boots from any USB. i have OS on internal USB (USB stick is plugged in it) which is actually meant for magnetic tape. the rack has WD Red HDD. the stupid thing is this server has 4 USB plugs at the front and two more at the back and you can't plug any USB disk in them because it tries to boot from it. i haven't noticed a specific BIOS setting that would allow me to choose a specific the boot port. though this would be very hand indeed.

if i add external USB drive it would sometimes try to boot from internal stick and other times from external drive. it seems completely random. 

all this is kind of silly, because the space for tape can be easily converted to hold 4 x 2.5" drives that can actually be added. so the server could in theory hold 4 x 3,5" HDD drives in drive enclosure, 4 x 2,5" drives in tape enclosue , 6x USB external drives and an e-sata drive=15 drives+ USB for OS. and the server box is very small. but because of this USB boot, it is all a bit annoying to effectively setup.  maybe one day, when i grow up, i will buy a HDD for OS.

---

