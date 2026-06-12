---
title: "Recover HDD data by freezing it."
date: 2009-12-23
forum: The Cafe
---

### Post by spydeyrch on 2009-12-23
Hey guys, thought I would post something that might be helpful to others and seeing as it deals with windows, I felt like it would be more appropriate here than in the general help threads or hardware threads but feel free to move it if needs be.
 
My story:
 
I have a friend who's family has been good friends with mine. I built them a new computer a few years back and got them out of the confines of a pre-built, manufatured controlled system. Needless to say, they loved it! It wasn't a huge gamers system but it wasn't low end either. they could play crysis at 1024x768 in medium details. they loved it.
 
Well about a year into owing the computer, the HDD started to go bad. I would recover it with check disk and make sure everything was good on it. A few times I had to reinstall the entire system but I was always able to get access to it via a second computer and therefore able to backup their files prior to a fresh reinstall.
 
This last time though, it was a huge problem. the computer just crashed one day and when they tryed to turn on the computer, it would hang at POST. I took out the drive and put it in my system, the bios would hang at POST too, at the same tie it was trying to access the HDD that was going bad. I tried everything!!! I tried hot swapping it while windows was up, I tried hot swapping it with ubuntu, which was installed as my second os. I tried mounting it by using a live cd (both *buntu & knoppix). Nothing would get this drive to get detected. Everything woudl hang. I even got as desperate as doing a platter swap and seeing if I could do that. But i held off and stored the drive for about 7 months. 
 
Then last night, it hit me!! I had recently read an article about freezing a HDD to possibly get access to the files. So I pulled it out of storage and threw it in the freezer. After which I started to read how to do it. Should have read how to do it before doing it. I was supposed to put it in a plastic bag and THEN into the freezer. Too late!!! but I had another great idea. After about 4 hours of chilling, I pulled the HDD and put it into a container of uncooked rice!!
 
The rice sucks up any condensation. I hooked it up to my system, and it got threw POST, loaded up windows, installed the drivers for the drive. I opened my computer and there it was, but it didn't show the drive space remaing/used. It gave the drives name and then showed NTFS under the name. I tried to open it but got an error message saying I didn't have permission to do so. So I opened up the properties and security details. I took ownership of the drive. It took about 15 mins to change ownership on the drive. After which I tried to access the drive again. Still same error. so I restarted and booted in to my ubuntu system. it recognized the drive but when I tried to mount it through the places menu, it gave me an error message of basically (I don't remember the exact words): "unable to mount /dev/sdb to /media/..... must mount as root" So I opened up a terminal and tried to mount it as root, but got the same message, kind of strange.
 
So after I tried to do the same thing on a live cd of knoppix, I kind of gave up a little. until I decided to run check disk again. I ran check disk for about 3 hours. After which I tried to get access to the drive via windows and ubuntu, both which gave me the "do not have permissions" and "need to be root" messages. the wierd thing was that if I tried to save a file to them, say one that I downloaded from the internet, it would allow me to browse through the file contents of the drive using the "save file" window. I could see all the folders and files and I could save to it but I couldn't get to the folders/files through normal folder/file explorer/file manager. Also, every file and folder icon had a padlock sign on it, so I knew that it was locked. But i had previously taken ownership of the entire drive sot hat shouldn't matter anymore. It was very frustrating!!!
 
So I threw the drive back into the freezer at about 1am this morning and went to bed, with thoughts of solutions floating in my mind as I slept. I woke up bright and early this morning and decided to try one more time. I took out the drive, put it in the rice, and then connected it to my computer. I booted up windows 7 and then took a look at the drive, it still showed the NTFS under the drive name and still said that I didn't have permission to access the drive. I checked the ownerhsip of the drive and it still showed that I was the owner. Not just the admin group but my actual user in the admin group was the owner.
 
I started to look through the permissions settings and noticed that even though I was set as the owner, I did not have a permissions level granted to me on the drive. Really it shouldn't matter as far as I remember but I decided to give it a go. I gave myself permissions to read, write, change, full, etc. to the drive and it's contents. Then I tried to open the drive. 
 
BAM!!! All the files were present in front of me!! I started to copy them ASAP to a folder on my system drive. I couldn't believe it. It had actually worked!! Freezing it allowed me to get it past post and into the system. After which just some settings tweaks and I was good to go!!
 
I got almost all the files before the drive died on me again. So I threw it back into the freezer with the hopes that it will last 20 more mins for me to get the remaining files off of it.
 
My friend thought that she had lost ALL her pics of her children growing up and family. Basically her whole digital lifebook was recovered. What a great Christmas gift for her!!! I have pressed EXTENSIVELY the need to do weekly backups.
 
I would like to know if anyoe else has tried this method of freezing a HDD and if it worked. Also, what other ways have you used to get data recovered. Enjoy!!
 
-Spydey :guitar:

---

### Post by cariboo on 2009-12-23
I've done it several times to recover data from defective drives. Where I live condensation isn't a big problem most of the time as there isn't enough moisture in the air.

The best defense though is to have good backups. For some reason most Windows users seem to think it is to much hassle to back up, but if you set something up that does it automagically, you're golden.

---

### Post by HeadHunter00 on 2009-12-23
I have tried doing that, but nothing happens.

---

### Post by cascade9 on 2009-12-23
Voted "[I]Yes, it worked like a miracle!!"

[/I]I've done the freezer trick several times. Sometimes its worked, sometimes it hasnt. Depends on whats caused the issue in the 1st place IMO (freezing your hdd is never going to help if the controller chip or other stuff has caught fire LOL)

[IMG]http://www.capsicumgroup.com/images/stories/data_recovery/fire_damaged_hdd.JPG[/IMG]

Edit- I've also found that dry ice on the hdd can work as well. Only done it once when they drive got rather toasty within seconds of starting,a nd it was easier to use dry ice than to try to run an ide and power cable into my freezer.

---

### Post by Gizenshya on 2009-12-23
you need more poll options...

Yes, it didn't work, but didn't kill it.

Yes, it didn't work, and killed it.

Yes, it may have helped get it to work, but unsure.

I've heard of all of these 3 scenarios... and I've experienced the first and third ones myself.

I My experience with the first scenario was a bit strange, though.  I shocked the PCB, so it wasn't a mechanical issue.  It didn't work (but I didn't expect it to), but it didn't hurt either.

I had a hard drive that wouldn't load no matter how many times I tried.  I usually have them in external cases so I can just flip the switch off and on whenever they hang, to try again.  It is MUCH faster this way.  And  it is the only way to get some to recover (the ones that only stay running for a few seconds at a time).  This isn't enough time to boot, but it is enough time to get files off.  Well, anyway, that drive was screwed, I thought.  But, I kept it.  I finally resorted to freezing it.  I took the rechargeable silica gel pack from the gun safe and put it and the hard drive in a 1-gallon plastic bag for a couple hours, then I put them in the freezer.  I had the wires hooked up to the drive through the bag, and glued around them.

Froze it and tried, and it didn't work.  BUT, after a while, I tried it again, and it worked long enough to get my files off.  I don't know if the freezing had anything to do with it, but it wouldn't work at all before it was frozen.

---

### Post by spydeyrch on 2009-12-23
> **Gizenshya said:**
> you need more poll options...
 
Yes, it didn't work, but didn't kill it.
 
Yes, it didn't work, and killed it.
 
Yes, it may have helped get it to work, but unsure.
 
I've heard of all of these 3 scenarios... and I've experienced the first and third ones myself.
 

 
i will go in and add the more options that you suggested, thanks for them. :KS
 
EDIT: Hey guys, excuse the totally rediculous question, but how do I edit my poll? I am having a n00b moment right now (no offense to any n00bs out there, we have all been there). I can't seem to remember hwo to edit my poll. I hate it when I can't access part of my memory partition ..... I mean my brain... :confused:
 
-Spydey :guitar:

---

### Post by dragos240 on 2009-12-23
Never heard of it. And I've never had a bad HD.

---

### Post by Firestem4 on 2009-12-23
> **cascade9 said:**
> Voted "[I]
Edit- I've also found that dry ice on the hdd can work as well. Only done it once when they drive got rather toasty within seconds of starting,a nd it was easier to use dry ice than to try to run an ide and power cable into my freezer.

You don't leave the HDD in the freezer lol. You freeze it for a while and then you take it out right before you put it into your machine.

---

### Post by hessiess on 2009-12-23
Never needed to, as a minimum always have AT LEAST two hard drives in a computer and RAID them;)

Also check that the drive isn't getting too hot.

---

### Post by cascade9 on 2009-12-23
> **Gizenshya said:**
> Yes, it didn't work, and killed it.

If its not dead, you shouldnt be freezering it anyway. Unless you mean 'its semi-dead' (i.e. it will appear in BIOS, but not initialize)

> **Firestem4 said:**
> You don't leave the HDD in the freezer lol. You freeze it for a while and then you take it out right before you put it into your machine.

Err.....it was a heat issue (which is one of the things that the freezer trick works for, it will never fix mechanical problems....and may make them worse). So the drive would appear in BIOS, initialize, spin up, get part way though moving a file and then opps, not working- and really really hot. 

So I had 3 options- 
1- Throw the thing away without getting data off it. Not cool. LOL 
2- Try to keep it in the freezer so it would stay cool longer. 
3- Cool it outside the freezer. 

I took 3. It worked. 

BTW, I know of other people who have had similar issues to me and run the drive in the freezer. I just couldn't be bothered finding my long IDE cable, power extension cable and just happened to have some dry ice around.

---

### Post by foldingstock on 2009-12-23
I only tried this trick once on an older IDE drive and it did not work for me. Most likely the board on the drive had failed. I ended up setting up a make shift "clean room" and physically moving the platters from the bad drive to a good drive (same model). This worked well enough for me to get the data off the drive. No idea how long it would have lasted, I didn't want to trust it longer than I had to.

---

