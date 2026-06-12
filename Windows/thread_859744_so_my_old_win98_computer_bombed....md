---
title: "so my old win98 computer bombed..."
date: 2008-07-14
forum: Windows
---

### Post by themuddaload on 2008-07-14
i gave 2 80 gig hard drives in it, one running win98 (the slave drive) and one running multiple linux distros.

the win98 drive got virused or something, and now it wont work at all. it will boot up, but as soon as my desktop shows up, i get an error message saying that some .dll file is screwed. i click ok, but it wont let me access any of my files. you click any window, for example my computer, and nothing comes up, just an empty window.

my idea:

i disconnected my slave drive and now i am trying to reformat the drive to fat32 using a linux live cd (mint 5)

i cleared the partitions, but i cant get them to totally die.

is there a way to totally reformat a drive to fat32 using the mint 5 live cd?

i'm stuck, someone help me :(

by the way, i will probably download and burn a SAM linux live cd since it plays alot faster on my old slow dinosaur.

---

### Post by LaRoza on 2008-07-15
> **themuddaload said:**
> 
is there a way to totally reformat a drive to fat32 using the mint 5 live cd?


You can use a bootable CD which contains GParted to do that (Ubuntu has it on the live disk, I don't know about Mint)

---

### Post by themuddaload on 2008-07-15
yeah, i was trying to use gparted on the mint live cd, but i didnt see a way to totally wipe all prior partitions and format to fat32.

it shows my hard drive being separated into 3 separate chunks. and mint froze when i told it to delete the swap thing, which is what i think was making my hard drive separated

---

### Post by Bungo Pony on 2008-07-15
Get the Gparted live cd, or even the Parted Magic live cd and use those to format your drive. It should be pretty straight forward on how to delete partitions, create new ones, and format them to any FS you like.

Also, did you try to replace the dll file that was causing problems? Re-formating and re-installing is usually my last resort.

---

