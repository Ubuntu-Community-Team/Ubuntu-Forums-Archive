---
title: "How to Recover SSD?"
date: 2017-05-28
forum: Windows
---

### Post by aspartame21 on 2017-05-28
I was using windows 10 that is located on my ssd. Suddenly, windows stopped responding and and powered my laptop off manually. When I tried to start it back, I couldn't run windows. Then I started linux live and tried to recover my ssd using gparted and I couldn't do anything, because I was getting [h=1]Input/output error during read on /dev/sdb[/h]and the actual size of ssd was displayed as 1.97MB instead of 480GB

---

### Post by TheFu on 2017-05-28
Welcome to the forums.

[http://www.makeuseof.com/tag/data-recovered-failed-ssd/](http://www.makeuseof.com/tag/data-recovered-failed-ssd/) says the prognosis isn't good.
Interview with a data forensics expert about SSDs: 
[http://cyberspeak.libsyn.com/cyber-speak-april-5-2011-solid-state-drive-forensics](http://cyberspeak.libsyn.com/cyber-speak-april-5-2011-solid-state-drive-forensics)

Update after seeing oldfred's reply below: It would be helpful to see the output from **sudo parted -l** so we can see all the disks and partitions on the box.  Oldfred is correct, sda is usually where an OS gets placed and sdb would usually be a flash drive or DVD used to boot live-boot media.

However, the point about SSDs is that they fail sometimes and only a backup solves it.

---

### Post by oldfred on 2017-05-28
You show sdb?
Is there an sda?

Often sdb would be your flash drive which might be 2GB?

---

### Post by aspartame21 on 2017-05-28
sdb is the ssd and it fails to be formated. I can't even create a partition table for it

---

### Post by QIII on 2017-05-28
Hello!

My guess is that the controller has gone bad.  But we can always be more optimistic than that!

If you have no data to recover and would like to simply try to get the device working again, you might follow [this advice on the Arch forums]("https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing") to see if you can at least get a usable disk back.

Bear in mind that this will completely, utterly and permanently destroy any information on the device.

---

### Post by howefield on 2017-05-28
Moved to the "*Windows*" forum.

---

### Post by yancek on 2017-05-28
I don't know how Ubuntu or Linux fit into the equation?  When you have a problems with the proprietary windows filesystem, the best way to try to repair it is to use your windows installation DVD with the repair option.  If you don't have the windows DVD,  you might be able to download some windows tool.  There really isn't much any Linux tool can do to fix more than a very minor problems with a windows filesystem and not much incentive for any Linux developers to do so.

Have you tried posting at a windows forum?

---

### Post by aspartame21 on 2017-05-29
Already did. Windows can't even handle it. I had to unplug my ssd in order to run windows recovery.

---

