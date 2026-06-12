---
title: "Server with 1 HD with Ubuntu 2 other with Raid"
date: 2010-03-26
forum: Server Platforms
---

### Post by Bauer17 on 2010-03-26
I am new to Ubuntu and trying to figure out how to set up the following:

I have 1 HD that will run Ubuntu server

then 2 hard drives that will run a raid 1 configuration as a file server so we can share files at home.

How would I set this configuration up? I know how to set up the raid drives but what would the mount points be if I have the HD with Ubuntu installed set as / (from my understanding you can only have 1 drive with the mount set as / )

Then how do I access the raid from a command prompt to make sure it is working?, and does it mount automatically?

I hope I explained this well enough.  If not please follow up with questions.

Thanks!

---

### Post by GrumbleNZ on 2010-03-27
I have a similar setup but want to use hardware raid. Both volumes show as a raid array in raid bios, I have setup a mount point and tried to configure fstab but the drives don't seem to have 'linked' to the mountpoint, so I suspect they may need to be setup as a logical drive and then point that at the mountpoint although NO idea how to do that!. Running 9.04 ws + server components. Only started this a week ago and getting nowhere. All help appreciated.Thanx

---

### Post by trundlenut on 2010-03-27
Are you using software or hardware raid?
Will you have all the drives installed in the machine before you install Ubuntu?

I have a similar setup (with hardware raid) but I only had the first drive in when I installed Ubuntu and then added the additional drives later which made it a bit more complicated.  

Basically I have the additional drives (set up as Raid 5) mounted as /storage.

---

### Post by Bauer17 on 2010-03-27
> **trundlenut said:**
> Are you using software or hardware raid?
Will you have all the drives installed in the machine before you install Ubuntu?

I have a similar setup (with hardware raid) but I only had the first drive in when I installed Ubuntu and then added the additional drives later which made it a bit more complicated.  

Basically I have the additional drives (set up as Raid 5) mounted as /storage.


Yes all the drives are installed and I would like to set it up as a RIAD 1 array.  It would be a software raid since the intel version that comes with motherboard is not supported with Ubuntu.

---

### Post by whoop on 2010-03-27
You want to put the single hd on /, and the software raid 1 array on /home.
You usually set this up during the install, but it is possible to do it after you have installed ubuntu on the single hd (/).
I did the latter once, I described it here:
[http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328)

That is if I understand you correctly <-- ubuntu is installed on the single disk, all user generated files (user accounts) are on the raid array...

---

### Post by Bauer17 on 2010-03-27
> **whoop said:**
> You want to put the single hd on /, and the software raid 1 array on /home.
You usually set this up during the install, but it is possible to do it after you have installed ubuntu on the single hd (/).
I did the latter once, I described it here:
[http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328)

That is if I understand you correctly <-- ubuntu is installed on the single disk, all user generated files (user accounts) are on the raid array...


Basically I was looking to keep all the ubuntu files on the main hard drive (including /home files ect) then all storage files (mp3's, documents, movies ect) on a separate drive(s)/Raid controller but I did not know what the mount point for the raid controller/secondary hard drives would be?

---

### Post by whoop on 2010-03-27
> **Bauer17 said:**
> Basically I was looking to keep all the ubuntu files on the main hard drive (including /home files ect) then all storage files (mp3's, documents, movies ect) on a separate drive(s)/Raid controller but I did not know what the mount point for the raid controller/secondary hard drives would be?

Ahh, well you define that yourself... mount it anyway you want it..
Setup the hard-drive(s) using tools like fdisk, mdadm, and you probably want to auto mount the raid array at startup so you need to edit /etc/fstab and add a mount point (any mountpoint, example: /thisisvalid) to the raid array.

In my personal opinion having everything raided is the most logical (if a drive breaks, just replace it and your (just about) done), having just home raided is the next best thing (if the ubuntu drive breaks, just replace the drive, reinstall and mount /home, all files and user settings are preserved), but what you want to do works, if it works it's not wrong :)

---

### Post by trundlenut on 2010-03-28
> **whoop said:**
> Ahh, well you define that yourself... mount it anyway you want it..
Setup the hard-drive(s) using tools like fdisk, mdadm, and you probably want to auto mount the raid array at startup so you need to edit /etc/fstab and add a mount point (any mountpoint, example: /thisisvalid) to the raid array.

In my personal opinion having everything raided is the most logical (if a drive breaks, just replace it and your (just about) done), having just home raided is the next best thing (if the ubuntu drive breaks, just replace the drive, reinstall and mount /home, all files and user settings are preserved), but what you want to do works, if it works it's not wrong :)

Yeh, what he said.

That's what I did but hardware raid made it easier.

---

