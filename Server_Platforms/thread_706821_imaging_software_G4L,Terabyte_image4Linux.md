---
title: "imaging software G4L,Terabyte image4Linux"
date: 2008-02-24
forum: Server Platforms
---

### Post by ttallos on 2008-02-24
is this imaging software: G4L worth loading and using? I tried it once but it was so sloooooowww. I was wanting to make a server with just a few features and was considering what imaging software I could use just for linux. I have heard of Terabyte image4Linux but I dont want to pay if I dont have to.

---

### Post by wirelessmonkey on 2008-02-25
I use partimage, it works wonderfully. At work, we use partitionmagic.

---

### Post by MJN on 2008-02-25
I've used G4L a little in the past and never found it slow - indeed I seemed to recall it ran practically as fast as my disks would allow. That said, it's an old tool with some 'interesting' history - if I was looking for a solution now I'd be more inclined to go with an alternative with more weight behind it like Partimage that wirelessmonkey recommended.

Mathew

---

### Post by crush304 on 2008-02-25
dd?

[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by ttallos on 2008-02-28
Using G4L on a bigger drive 160GB seemed to be slow compared to norton Ghost. Partimg seems to work but for some reason hangs on my machine it does finish after a while. DD I have used in the past this may be the way to go I will have to test it further. I would like to see what is the best of the three.....

---

### Post by MJN on 2008-02-28
Well, if it helps, dd will copy the entire drive/partition regardless of whether there is data stored in all the sectors or not so it should be the slowest (and biggest backup size).

I'm not saying it's necessarily a bad choice, but it's something you should be aware of.

Mathew

---

### Post by ttallos on 2008-02-28
Sure.... I am aware I used DD with the frount end AIR have you ever heard of it? it lets you create .gz compression. It still copies sector by sector though but the images are small. I think terabyteunlimited.com might have the cheapest software out of norton or acronis that can clone linux also for an inexpensive price the pay versions are usually better.

---

### Post by ttallos on 2008-03-02
I found through much experemintation that partimage is the best....Before I was using the boot disk. I loaded a ubuntu test machine and laoaded it on that machine and was successful at backing up a 6.5GB partition in 35min 26sec to an image file. Then to restore the machine took only 20min 53sec to another HDD as a test. Then I restored the partition tables and the master boot record and wallaa presto the whole thing worked like a champ. I was using a windows disk cause that was what I will need to backup the most at work....Long Live Ubuntu!

---

