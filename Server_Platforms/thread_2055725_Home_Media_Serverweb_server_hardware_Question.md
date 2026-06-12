---
title: "Home Media Server/web server hardware Question"
date: 2012-09-10
forum: Server Platforms
---

### Post by feardotcom on 2012-09-10
Ok, so i'm not sure if im posting in the right spot or not. If not then i'm sorry.

Ok, first I'm looking at building a home media server that also runs a private web server for testing. The media server will be streaming to 5 PC's around the house, I'm looking to back up my entire movie and tv show's collection in full 1080p HD, which is about 10-14gb files for movies. I was going to use XBMC to run on small computers next to the tv's. at the most, 3 systems will be in use at one time. maybe 4 if we have company. I'm looking at a super micro 4u 24 slot hot swappable server case  with 3tb sata II drives x24. 

My question is first, if i get 2- 4x multilane raid cards to connect all 24  HDD's will there be 2 separate raid config's or can i combine all the drives together for one huge raid config even though the hdd's are on 2 separate raid cards? 

Second question is what raid configuration is best? i'm looking at maximizing my storage space but have backups in case of drive failure which i know there will be. i dont want to have it backed up 2 or 3 times and have 72TB and turn it into 24TB with 3 back up's. I know about raid, i have never worked with raid and i understand the concept of raid but i dont fully understand the different configurations.

Third question is what kind of system specs will i be looking at? single 8 core opteron? dual 8 core opteron? quad 8 core opteron?8gb ram, ecc? 16gb ram, ecc? 64gb ram, ecc? Whats going to be best for my situation.

EDIT: Forth question, whats the difference from ubuntu server and ubuntu desktop other than the fancy x windows? Does ubuntu server come with a low end x windows? I would like a low graphic intensity x windows just to be able to drag and drop files or run deb packages with double click. It seems like it would be easier to config setting for network and file sharing with x windows than command line.

---

### Post by feardotcom on 2012-09-15
bump

---

### Post by darkod on 2012-09-15
You need to consider using ubuntu (linux) software raid instead of the raid controllers in the server. In this case, you need to investigate whether the controllers have the option to only act as a connection device, without any raid configuration, just so the system can see all the disks.
Then you do the raid with mdadm. This option will make it possible to keep the raid running and the data safe even if the controller dies.
Using hardware raid controllers for raid is OK if only a disk fails, but what if the controller dies? You would need to use the same model and even then I'm not sure it can pick up the existing array.
With software raid it picks up the array, you only need to connect the disks.

As for raid level, you are probably looking at something like raid5 or raid6. Again, if there are two separate raid controllers, I don't think you can create a single array. It sounds like 12 disks will be connected to one controller and 12 disks on the other. I'm not aware of a procedure to join them together if using the hardware raid.
With software raid, since the controllers will only serve to connect the disks and the system sees 24 separate disks without hardware raid, you can create one huge array of 24 disks.

On the CPU side I guess a single 8 core Opteron would be more than plenty. Dual CPU is way too much. Even the single CPU of that spec is too much I guess. The actual job is done by the disks and the controllers, not the CPU. I don't have experience with such huge arrays but I would say even a more modest CPU would do. But I might be wrong about that, especially if you use the software raid option since the CPU is getting used in softraid.

Ubuntu Desktop will come with all sort of packages that are not needed for a server function. The Server comes with the bare minimum and without any GUI but that gives you a chance to install a lighter GUI, not the full feature Ubuntu Desktop GUI. If you feel it's necessary, you can add a GUI to the Server version. In general the Server wouldn't waste resources on running unneeded packages, so it should work much more optimized.

---

### Post by feardotcom on 2012-09-17
Ok, thank you very much for your reply. 

So the cpu wouldn't matter with XBMC and the 3-4 connections pulling data from the server on top of the test web server i'll be running for software developement? What about the ram? what do you think would be best?

---

### Post by darkod on 2012-09-17
I'm not sure I can assume correctly, but I have HP Microserver with Athlon Neo NL36 and 1GB ram.
Few days ago I did a test for someone, using the mv command to move 370MB folder to another network hdd (not to internal hdd on the same server).
The mv process CPU load was 5% during the move operation. The MEM load was 0.1%.

The NL36 compared to 8 core Opteron is like cpu from 10 years ago. :)

So, even with 3-4 users pulling data over the network, and basic test web server running, I can't really see the Opteron saturating even in the worst scenario.

If you can go with a smaller CPU, the decision is yours, but I think it would handle it too. On the other hand, if you have some sweet combo deal for the Opteron together with the server you want, take it. More power, better. But I doubt it will be really used. :)

---

### Post by feardotcom on 2012-09-18
ok, thank you for you replies. Much appreciated.

---

