---
title: "Feedback regarding a recent Windows install"
date: 2007-03-22
forum: The Cafe
---

### Post by prizrak on 2007-03-22
So my father have finally decided to do what I have done for years and ignore what my mother thinks about upgrading computers (she doesn't understand the need to have some execute in less that an hour) and get a new system. Of course the system was going to be built by me out of components I'm comfortable with as I would not trust an OEM with anything more complicated than a toothpick (and they would still manage to jam it into their eye).

So the shiny new components arrive and they work happily together (aside from some weird POST error about the CPU, but it doesn't stop the CPU from working so I assume it's not critical). The system being new and mostly a family computer that gets changed about every 5-6 years I went for not quite top of the line stuff but something closer to the high end. This in turn means SATA II with RAID. OS of choice was to be XP as sadly my mother is 100% against anything that she hasn't sorta learned already and my dad mostly does work and play games on this system and both require Windows. 

So I set up the drives in a nice half TB RAID 0 (purely for speed sake). Pop the XP SP2 CD in and sure enough XP does not recognize the RAID controller and sees no drives. Fine I un RAID the disks and set em as AHCI (native SATA basically) once again XP does not want to see the drives. This is where the trouble starts. I can set the drives in IDE mode but that will basically destroy the whole reason I got SATA II to begin with. So I try hitting F6 to install a 3rd party RAID controller during XP setup. Lo and behold the ONLY place that XP will even attempt to look for a driver is disk A:. For those who aren't old enough to remember disk A: is a floppy disk. There is no frigging floppy in that system, there is no frigging floppy in ANY MOFING MACHINE other than the old computer that is being replaced. That is of course GREAT as the machine is disassembled on the floor (dvd reader was taken out of it and the old HDD is waiting its turn to provide the data to the new system). To make it worse there are no floppies lying around my house as I threw them away about 4 years ago when people STOPPED USING THEM!!!! 

At this point XP was being installed onto the system in IDE mode. My father has MSDN subscription at work that allows him just about any OS MS still supports. So we decide to grab Vista once XP is done installing since the new system of course has a DVD RW drive. (There is no wired ether in the house so the WNIC was taken out of the old machine as well). Now the problem is that there are no blank DVDs lying around the house. To make matters worse it's a 6 hour download on MSDN (it was like 10PM already and we all gotta go to work). This morning when I wake up I find that Vista DL was "Interrupted" (I dunno how the f that happened) at about 90% and had to be resumed. Luckily MS provides a downloader with such a feature and that's what was being used. 

At this point I decide to grab the motherboard CD and bring it to work, go find me floppy and create a driver disk using the desktop I have at work. Then create a RAID and then install XP. No one in my household actually wants Vista and since I don't know what will actually work with it it's a better alternative. So far the disk has been created but I won't be getting there till 9-10PM tonight since I'm going to watch the 300 after work. 

Now I understand that a 6 year old OS (even if SP2 is like 3 years old) cannot possibly include a driver for a SATA II RAID controller that probably haven't been out for more than 2 years but is it too damn much to ask that I get to point the setup to a different location? It can read optical drives (that I have 2 of), USB storage have been around long enough for the installer to have drivers for it. Why the hell could it not ask to provide a location? It does so for drivers you try to install from the GUI so the framework is there. I mean seriously how frigging difficult would it be to implement.

---

