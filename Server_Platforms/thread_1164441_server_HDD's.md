---
title: "server HDD's"
date: 2009-05-19
forum: Server Platforms
---

### Post by Hozza on 2009-05-19
I have a Compaq ProLiant DL380 (6 x 18.2GB HDD's) and i have tryed to install ubuntu server 8.10 lts onto it. In the instalation it found 2 partitions an 18GB one and a 54GB one ??? 

it seems to have only installed on one hdd which was expected, but it does not see the others? also there is not the normal things in the /dev/?

what going on and how can i get accses to the other 5 HDD's and how do i find out which on its installed on?

Thanks for any help.

(P.S. i have installed the openbox gui and nautilus)

---

### Post by windependence on 2009-05-19
Looks like the other drives are in RAID, probably RAID 5. This is how most enterprise servers are used. Most likely they used one drive for the OS and the RAID array for the applications and data. A good setup IMHO. You most likely just have to mount the RAID array, and you may need to build a Linux compatible file system on it first. It will be a great setup though with hardware RAID. 

When it boots you will see a screen real quick that will tell you (I think) it's ctl+S to get into the RAID configuration. There, you can view how it's set up and you could even add the other drive to the array because with hardware RAID you can boot off the RAID array. I have drives too if you need them.

-Tim

---

### Post by hictio on 2009-05-19
Find out which is your BIOS utility.
Personally, I have found this guide [PERC 4 BIOS Configuration Utility](http://www.cs.uwaterloo.ca/~brecht/servers/docs/PowerEdge-2600/en/Perc4scdc/UG/bios.htm) when I had to rebuild the RAID array once one of the HDDs died on me.

---

### Post by windependence on 2009-05-19
> **hictio said:**
> Find out which is your BIOS utility.
Personally, I have found this guide [PERC 4 BIOS Configuration Utility]("http://www.cs.uwaterloo.ca/%7Ebrecht/servers/docs/PowerEdge-2600/en/Perc4scdc/UG/bios.htm") when I had to rebuild the RAID array once one of the HDDs died on me.

We have to make it clear to him that we are talking about his RAID BIOS because the config is in there, and NOT the regular BIOS settings. The options go fast on the screen and there are several of them. In fact, now I think I remember, it's F8 to get into the RAID BIOS, F2 for the regular BIOS, and F10 for setup utilities and F12 for PXE boot.

-Tim

---

### Post by Hozza on 2009-05-20
> **windependence said:**
> Looks like the other drives are in RAID, probably RAID 5. This is how most enterprise servers are used. Most likely they used one drive for the OS and the RAID array for the applications and data. A good setup IMHO. You most likely just have to mount the RAID array, and you may need to build a Linux compatible file system on it first. It will be a great setup though with hardware RAID. 

When it boots you will see a screen real quick that will tell you (I think) it's ctl+S to get into the RAID configuration. There, you can view how it's set up and you could even add the other drive to the array because with hardware RAID you can boot off the RAID array. I have drives too if you need them.

-Tim

Thanks so much Tim (why isn't there more people like you in the world :D). you said "you may need to build a Linux compatible file system on it first." do you mean format them to ext3 ??? or something else.

OH!!! i just realised that when the server is running two of the hdd lights are flashing on the front of the server. AND when i installed ubuntu it found 2 partitions a 54GB one and anouther one, i installed on the other one. 

I origionaly thought that i had installed the OS on one hdd, that means the rest were not mounted and probily raided into one hdd. But 5 x 18.2GB HDD's isnt 54GB.

Does this mean i have 4 raided hdds and i have installed on 2 of the hdds or one has failed (a red light on one of the hdd's was on but when i rebooted it said hdd failure then auto repared it.) ???

Someone help please is the suggestion from Tim still valid???

thank you so much for your help.

---

### Post by Hozza on 2009-05-21
:bump: anyone?

---

### Post by Cheesemill on 2009-05-21
You will need to check the RAID BIOS to see how the disks are set up, my guess is you have 2 drives in a RAID1 as your 18GB boot drive plus the other 4 disks in a RAID5 (54GB).

If Ubuntu recognizes both of these logical drives then you should be good to go, you can use them just as if they were 2 normal disks.

Cheesemill

---

