---
title: "Restricted user privilages"
date: 2008-11-30
forum: Security
---

### Post by lavinog on 2008-11-30
I installed Intrepid a couple of weeks ago.
Today I was trying to sync up my mp3 player. Normally this is a chore because it is a mtp-device and requires editing /etc/udev/libmtp8.rules to add it since it is too new of a device.
What was odd was that it wasn't enough this time...My user was not part of the audio group which was preventing me from accessing my mp3 player.
even more odd is that when I look at my User Privileges, I noticed that some things were not checked off: 
[I]Capture video from TV or Webcams, and use 3d acceleration
Connect to wireless and ethernet networks
Use audio devices
Use scanners
Use tape drives[/I]
I am the only one on this machine, and I find it weird that these are unchecked by default.

Is this normal?
If so, why would this be normal?
I think that I am not the only one experiencing this because I have come across a couple of posts where users are being told to use sudo to access their devices...the users seem content with that solution, but I don't think that users should be using sudo for everyday activities

---

### Post by cariboo on 2008-12-01
I just checked and my user had several things unchecked, including what you mentioned, but because I am part of the admin and adm groups

Those groups are there so you can give other users permission to use those features. If they aren't members of adm and admin they need permission to use the specified devices.

Jim

---

