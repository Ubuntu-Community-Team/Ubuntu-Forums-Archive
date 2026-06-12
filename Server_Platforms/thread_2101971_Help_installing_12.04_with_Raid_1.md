---
title: "Help installing 12.04 with Raid 1"
date: 2013-01-05
forum: Server Platforms
---

### Post by Fxkrait on 2013-01-05
So my dad recently upgraded his business computers from P4's to I7's and now i have a server in my possession. The specs are: P4 3.2ghz, 1.5gb DDR 400, 120gb SATA raid 1, windows server 2003 :frown:.

The install works fine until I have to partition the hard drives and install it. It tells me that it has detected a raid, and if i want to "activate" the sata drives, i have tried selecting both yes and no to this  but it keeps failing in the next step.

Then it brings me to the partition manager. I select the first option and let it do it automatically, leaving me with around 118 gb EXT4 and 1.5 gb SWAP. I get the same error whether i selected "no" or yes": Failed to add Partition 1 (no such device or address) and i also get creation of the swap (Partition 5) has failed

Any help would be greatly appreciated, Thanks!

---

### Post by sandyd on 2013-01-06
Is this a fakeraid RAID1 configuration?
If it is, it is better to turn off FakeRaid in the BIOS, and follow [this guide]("http://ubuntuforums.org/showthread.php?t=408461") to setup software raid instead. (I know, it says Ubuntu 6, just download Ubuntu 12.04 LTS).

You can also disable RAID in the BIOS, and simply install without RAID.

---

### Post by Fxkrait on 2013-01-07
Thanks for your response, and with the mention of 'Fake Raid' i did a little research on the hardware i'm dealing with. I have determined i have a entry level server motherboard from Intel: the SE7210TP1-E, and here is the PDF manual [Link1].

I found this article [Link 2], which made me sceptical if i really have a "true" raid and not a "fake" one, as this is an "entry" level board. The raid controller is built in, which gives me another bad feeling.

On the second link, one of the comments said look for the phrase** 'Host Raid'**, and 90% of the time that basically means fake raid. I have found such horrible words in the PDF, and I am starting to think the worst :(. **Can anyone confirm if I truly have fake raid or am I one of the lucky 10%? **

Link 2: [http://serverfault.com/questions/9244/how-do-i-differentiate-fake-raid-from-real-raid](http://serverfault.com/questions/9244/how-do-i-differentiate-fake-raid-from-real-raid)

Link 1:[http://www.intel.com/support/motherboards/server/se7210tp1-e/sb/cs-008319.htm](http://www.intel.com/support/motherboards/server/se7210tp1-e/sb/cs-008319.htm)

And  again thanks a lot for any help given! I really appreciate it! :D P.S. I really  want to get the raid 1 working so i can store family pictures and other  documents in a redundant environment running 24/7, so no raid is not really an option.

[IMG]http://s7.postimage.org/bz134dejf/Server.png[/IMG]

---

### Post by spynappels on 2013-01-08
Do you have 2 x 120GB HDDs in the server? If you do, and you want to continue using them in a RAID 1 array, you can do that very easily at the install stage.

Turn off RAID in BIOS as already said.
You will need to choose "Manual Partitioning" during the install, this will show you a screen with the 2 HDDs listed, with or without partitions already on them. Remove all existing partitions, and create a new partition on each disk as a Physical Volume for RAID.

Then select the "Setup RAID" option, select RAID 1 and check both drives. Carry on and create the array.

The last step is creating some partitions on the newly created array. The simplest set up would be a 200MB ext2 partition at the start of the drive for /boot, a 2GB swap partition at the end of the drive, with all the space in the middle as an ext4 partition for / although this single partition could be split as many ways as you want with a different partition used for /var, /home etc.

After this, the install carries on as normal and you have a fully functioning Ubuntu Server on a RAID1 array.

---

