---
title: "Placing a CD image on a jumpdrive, and using GRUB on said drive to boot it"
date: 2009-06-20
forum: Ubuntu Dev Link Forum
---

### Post by necromantula on 2009-06-20
This isnt so much of a help or such topic, but more of a journal of my aspirations towards such a goal.
some grub binaries seem to have a bootfrom= flag, but it seems unreliable at best, so I'm working towards not using it. What inspired me towards this was thinking about the U3 drives, and how they work. 
I decided they are most likely a iso9660 filesystem for the u3 partition, and decided to try my own hand at playing with such a game

So far, i have in my possession
a 1gb jumpdrive, known to be bootable friendly (i dunno if all can, I've just used this one before)
1.iso (an iso with a set of tools useful to me I put together)
2.iso (Hirems Boot Disc, a common utility CD)
an ubuntu linux computer
high speed internet

my work thus far
Using fdisk, I created 3 partitions, all fat32, all primary partitions, on the drive. the first, is going to have grub installed on it, and is 100mb. The second will contain 1.iso, about 700mb. The third will contain Hirems, which is about 90mb

i'm using dd to write the isos to their respective partitions as we speak. Any ideas on how to configure grub for this? I'm planning on trying some stuff with chainloader so far

---

