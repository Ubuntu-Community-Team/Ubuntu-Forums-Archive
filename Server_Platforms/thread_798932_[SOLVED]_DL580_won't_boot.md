---
title: "[SOLVED] DL580 won't boot"
date: 2008-05-18
forum: Server Platforms
---

### Post by NateMan on 2008-05-18
I have a DL580 HP server formerly running ubuntu 7.10. I am using a compaq 5300 scsi card for a raid 5. It formerly contained 3 72.6gig scsi drives, however I destroyed the array and rebuilt it using 4. I then attempted to install ubuntu 8.04 upon the array. This seemed to work, however upon reboot, it failed to boot to my array. I'm not sure what to do to fix this. Any help would be greatly appreciated.

Nathan

---

### Post by barf1 on 2008-05-19
I have an HP LH3000u which was happily running FC7 and I also rebuilt the raid 5 array and installed Ubuntu server 8.04 (Fedora updates to frequently) using the same media that installed succesfuly on a regular PC and mine also fails to boot. I would also appreciate some input. Frankly not impressed that a distro that calls itself 'server edtion' has problems running on a server.

PS it works fine if I reinstall Fedora.

---

### Post by NateMan on 2008-05-19
Well I solved my problem, It was an usb 2.0 card that it didn't like having in while it tried to boot the first time. I had also recently rebuilt the raid 5 and it was running optimization stuff. I took the card out and reinstalled ubuntu 8.04 server, then booted it, shut it down, and reinstalled the card. Now it reboots fine and the card works great. Seems main issue was the usb card. What generation server do you have and what raid card are you using? Also did you wait for the optimization to run? That also seemed to be a problem. I've installed ubuntu 7.10 on 4 different compaq/hp servers with no issues other than this one. In fact, the first time I installed it on the server it worked great, of course I didn't put the card in till later. Maybe you have some sort of hardware conflict. I wouldn't be so quick to judge, as that was the first problem I've ever had with ubuntu server. I also can't find your server on google, what sort of model is it? (processor type, generation, size)

---

### Post by barf1 on 2008-05-20
Good to hear that you have fixed your problem. My server is a HP Netserver LH3000U (google for lh3000). Dual PIII processors, Megaraid card, SCSI drives, triple PSU's, no usb and works just fine with Fedora. I don't recall anything about optimization, when is that supposed to happen?

---

### Post by NateMan on 2008-05-20
It is supposed to happen immediately after the array is created, so if your array has been around for awhile, then that probably isn't the issue. Can you boot a live cd to get a lspci? Are any card installed in your system other than the megaraid? What does the lspci call the megaraid? What cards are included on the motherboard (scsi, etc.)? Have you ran smartstart and configured everything? Also that one seems somewhat old, you may need smartstart 5.5, I've had that problem with two different models. I'm sure it can be worked out.

---

### Post by barf1 on 2008-05-20
Problem solved (sort of). It is booting up it just takes ages and I mean like 10 mins to do it and part way through it blanks the screen so it seems like its frozen.

---

### Post by NateMan on 2008-05-20
ah interesting. What were the specs on the box?

---

### Post by barf1 on 2008-05-21
What specs do you want. Google LH3000 will get loads of info on the server and my specific specs are dual PIII 1GHz cpus, 8 x 18GB scsi drives configured as 5 in a raid 5 array, 2 hotswap and 1 spare. SCSI tape back up, DVD rom and floppy drive.

---

