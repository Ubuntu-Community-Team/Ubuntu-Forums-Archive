---
title: "Origami loosing work"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by BertN45 on 2012-03-30
folding@home the distributed computing environment from Stanford

I an loosing work using Origami/FahCore_a4.exe. I thought I understood that the work is saved every 3 minutes, so it always can be restarted. After a number of power-fails I noted that the unit, it was working on, disappeared. That unit of work passed the 20% mark, but that disappeared and Origami/FahCore_a4.exe loaded a new unit of work. That new unit of work is now at 0%.

Most of the work takes 1-3 days on my PC and only by exception I have up-times that long. Mostly I have a number of power breaks each day. If Origami/FahCore_a4.exe cannot survive those power-breaks, it is better that I stop, since I only create confusion and loose units of work. I noticed that my old windows XP system did survive and continues with the same unit of work.

Additional Note: I see it happened on both my Ubuntu machines.

ANY SUGGESTIONS?

---

### Post by Bucky Ball on 2012-03-30
Which Ubuntu release are you using???

... and what is this about?

[QUOTE=BertN45]folding@home the distributed computing environment from Stanford
[/QUOTE]

---

### Post by BertN45 on 2012-03-30
I am using 12.04 and the project is called folding@home. It is using the spare cpu time of PCs world wide and through massive simulations the scientists try to understand diseases like Cancer, Alzheimer, Parkinson etc and try to find a cure. If you google for folding@home you get a much better explanation.

---

### Post by Bucky Ball on 2012-03-30
12.04 LTS is not yet released and still 'testing'. You should NOT be using it on a production machine. 

I have asked the mods to move this thread to the 12.04 LTS forum. ;)

---

### Post by BertN45 on 2012-03-30
Giving the whole update process in Ubuntu, the difference between a formal release and a Beta2 is mainly a arbitrary date. Before and after that date bug fixes will be done and continue to be done. Besides I have more confidence in 12.04 as in 11.10. 

Your argument is only a formal argument. The political correct answer, but as often that type of answer has nothing to do with the reality. 

I was already running 12.04 when I detected that folding@home project and I finished 6 work units with 12.04 during a few good days with our energy supply.

_I doubt whether the problem has anything to do with 12.04, I think more in the direction of the use of ext4, probably the default journalling mode is not so reliable as assumed._

---

### Post by jbicha on 2012-03-30
What do you mean by "power-fail"?

ext4 in Ubuntu is reliable.

Origami/FahCore_a4.exe doesn't sound like an Ubuntu app.

---

### Post by BertN45 on 2012-03-31
Well the whole local electricity net goes down and sometimes in a very unpredictable way with spikes and short return of power for a couple of seconds. Ext4 is reliable for the developed world, but here it might  need the "journal mode" instead of the default "ordered mode". There also might be a bug in Origami, so that the script used to start FahCore_a4.exe under some circumstance uses the wrong parameters. Also FahCore_a4.exe might contain a bug.

Well if you read my post you can see it is a Linux program, both are complementary Linux programs / scripts, try Google. It is even discussed in this forum before and that is how I detected it.

The whole technical idea is great and its use in medical science is something, that everybody with his heart in the right place should support.

---

### Post by keithpeter on 2012-03-31
> **BertN45 said:**
> Ext4 is reliable for the developed world, but here it might  need the "journal mode" instead of the default "ordered mode". 

As this is a testing period for 12.04, have you thought of reformatting the hard drive and using a filing system in journal mode to see if it can survive a brief power outage better? Other people might well be interested to know if it does.

In the UK, on the outskirts of a major city, I see a momentary loss of mains power (literally half a second) about every 2 to three months. Always early in the morning.

---

### Post by BertN45 on 2012-03-31
I am thinking about it. I think it is enough if I change the mount options, but I hesitate because it has been said it will double your disk io. True?

I installed a new beta client for folding@home, so it works on its own without origami, eliminating one source of potential issues. Unfortunately that new client has the same problem.

---

### Post by cariboo on 2012-03-31
I would think, that with the crummy power system you have to deal with, that a UPS would solve many problems, as it will safely shut down the system when mains power is lost.

---

### Post by BertN45 on 2012-04-01
True, but I hesitate since I already invested in:
- 24 Volt inverter of 2.5 KW and 4 batteries.
- Surge protector

On the other hand, I am convinced there is a bug somewhere or in ext4 journal or in the check pointing of the FAHCore_a4 client.

I have set check pointing of FAH... to 5 minutes, that is 300 seconds. Say it takes 100 msec to write a checkpoint. So there should be a chance of 1 in 3000 that something goes wrong with that checkpoint. In reality the chance seems closer 1 in 2. That difference is too big, there must be a bug somewhere.

Another reason to assume a bug, is that normally if the last checkpoint is corrupted, I would expect that the previous checkpoint is used instead by FAH...

Ext is run as mode=ordered by default and it is updating its journal each 5 seconds. So I assume it saves the state of the FAH checkpoint file each 5 seconds if needed. If we also assume 100 msec to write the journal, the chance that it goes wrong would be 1 in 50. Both happening at the same time should be not noticeable for me. My PC should be scrapped on average before that could happen even with 30 power breaks per week and my oldest PC being 12 years.

Another reason I think about a bug:
- I have the problem on two Ubuntu 12.04 systems
- My old Windows XP system does not have any problem with an  older version of the same FAH... program.

ANY IDEA HOW TO FIND THE CULPRIT (ext4 or FAH..)?

---

### Post by BertN45 on 2012-04-02
OK it is an ext4 problem. They favored speed over data security, too many speed junkies in Linux. Especially if files are written and then renamed, there is a large chance that data is lost, since the allocation of disk space can be delayed by default for 30 seconds. 

For most application designers the rename seems like a good idea, you write the file and if the system crashes you still have the old version. This approach seems only vulnerable during the rename and that looks like a very short moment in time. 

Unfortunately in ext4 the rename is executed and journalled, while the data still might be partly or completely in the cache in memory and it can take 30-60 seconds before that is written to disk, Hence the high chance of corrupted files. On a crash the new file seems to be there, but its content is corrupt. So with ext4 you can create corrupted files, but you can do it very fast :D   

see:
[http://lwn.net/Articles/322823/](http://lwn.net/Articles/322823/) 

The next changes should make the ext4 file system more secure for your data and the behavior should be almost equal to ext3. I have adapted my ext4 settings as follows, 

changing the journalling file structure on disk.

sudo tune2fs -ojournal_data /dev/sda1

and add the bold part to the entry in /etc/fstab as follows,

# / was on /dev/sda1 during installation
UUID=af8c719f-9a9c-473f-881e-d9aad93d6765 / ext4 **data=journal,**errors=remount-ro 0 1

Now my previous calculation should be true again and the chance that I loose data should be better than the remaining life time of my PCs. I think I can buy a BIG disk and some crates of beer for the money earmarked for the UPS. Of course I will use ext3 on that new drive, since ext4 is the typical geek idea of a file system :)

---

### Post by jbicha on 2012-04-02
I'll admit I don't know much in depth about file systems, but that lwn link you posted is from 3 years ago. Are you sure that article talks about your problem?

---

### Post by BertN45 on 2012-04-02
Yes, because it is considered according to the POSIX standard and as such it is considered a feature and not a bug. There are solutions, but that means changing the defaults of ext4.

I think it is not smart to reduce the reliability of your file system, if you introduce a major new release. I think in countries like this you might loose data and it will take a long time before you realize, what is going on. I remember that removed a lot of music mp3 and wma files that had zero length and that makes me angry. Music that I have lost forever, because by now also my back-up has been corrupted.

**So if you have system crashes or power breaks, be aware that ext4 by default will corrupt your files.**

---

### Post by cariboo on 2012-04-02
Due to your power situation, there are only two things I can suggest, run fsck after every power failure, or store your data on a partition with a more robust file system.

I have XFS partitions on my server, the only power failures I've suffered are owner induced, but I haven't lost any data due to them.

---

