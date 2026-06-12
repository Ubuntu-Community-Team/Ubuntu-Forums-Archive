---
title: "Ubuntu Server 20.04 Installation Problems"
date: 2021-08-22
forum: Server Platforms
---

### Post by sawesome1018 on 2021-08-22
I'm trying to install the 20.04 lts on a custom built computer that has an Athlon x4 750k processor, 10gb of ram (1 of 8gb and 1 of 2gb). I am using Rufus 3.14 to create a bootable drive out of the iso, and it's crashing either on the stage where I have to choose an archive mirror, or when it tries to scan for hard drives. I've installed the regular 20.04 version of ubuntu on the computer before with no issues 
If you have any suggestions, I'll be happy to take them

---

### Post by mastablasta on 2021-08-23
1.make sure image is good (md5sum or SHA hash check)
2. use another "burn to USB" app (balena etcher for example or some other app to remove it as possible culprit)

-- is the install BIOS or UEFI ?

server installer is a bit different than desktop. i am not sure why there is a difference other than it being text only. but there are differences and sometimes they interfere with install.

---

### Post by MAFoElffen on 2021-08-23
What is the motherboard so I can look up the specs on the storage controller, NIC's and other related hardware...

Right at the moment, the Desktop Edition and the Server Edition ISO's have completely different installers. Desktop has the older debian-installer and the new Live Installer on Server is ubiquity... But for 21.10, is supposed to be the same for both.

I know by experience, that if the new Live Installer starts crashing at random places in the install, like you are describing... check the md5sum to ensure you have a good image to install from. That is what that is leaning towards.

---

