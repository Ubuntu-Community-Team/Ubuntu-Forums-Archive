---
title: "File server recomendations"
date: 2008-04-26
forum: Server Platforms
---

### Post by thecrazy8 on 2008-04-26
Hi,

I am going to setup a file server for my home were we can store all our movies, pictures, music, etc... 

I have read a bit on the subject and from what i gathered up I plan to use mdadm and start with a mirror array and later on i hope to migrate it to raid5 then raid6 as I add drives to accomodate our needs.

For the hardware I have an Athlon xp 2500+ system with 2gb of ram. The whole idea to go with software raid in my case is to save on cost. I was thinking of using the old onboard ide connections for the OS and add up to 4 pci sata cards in the system (4 sata ports each) to connect up to 16 drives to the array (if I ever need it, what i want is to be able to expand).

Is there any problems I may encounter with this setup?
Am i going to have problems with multiple PCI-SATA cards?

Keep in mind that performance isnt a big deal for this system. Worst case scenario 3 users are streaming movies or transfering files at the same time.

Any suggestions on hardware (especialy which brand of pci-sata adpaters work best with ubuntu), software, setup or anything else that you think i overlooked or that i should be aware of before i start will be greatly appreciated.

Thank you everyone!

Fred.

---

### Post by HermanAB on 2008-04-27
If the movies are compressed with MPEG-4 Part 10 then you won't have a need for many disk drives or excessive network speed.  I have run 30 simultaneous movies in Mplayer on a single 1.6GHz Core 2 Duo laptop, before the processor load got to 100%.

---

### Post by thecrazy8 on 2008-04-28
Sounds like network performance wont be an issue, but what really worries me is if ill have any problems with multiple pci-sata cards  of the same brand in the computer.

I remember in the past i had 2 nic cards in the same linux box and the darn thing kept mixing up the two cards... had to redo the config all the time. If something like that happened to a raid array it would get messy.

---

### Post by thecrazy8 on 2008-04-28
/bump

So no recomendation for a multiple pci-sata card setup?

Should i understand by this silence that everything should work just fine ? :confused:

---

