---
title: "New install partition/drive setup?"
date: 2010-11-27
forum: Ubuntu Studio
---

### Post by garyed on 2010-11-27
I'm getting ready to do a new install of U-studio 10.04 amd64.
Just looking for recommendations for partitions & drives. 
Any info or ideas appreciated. 
I'm coming from XP using Cakewalk Sonar Home Studio XL where I always used a separate drive for audio than for the OS. Does anyone do it like that here? I've actually got U-Studio 7.10 working pretty good but every version since then I've had problems with over runs & latency so I've stuck with XP to do any serious music. I really want to go Linux all the way for my DAW so I'm curious how others set up their systems. I'm assuming that I'll get Jack working with no problem for now but if not that would be another thread.

---

### Post by JC Cheloven on 2010-12-21
Hi, your setup is quite similar to mine. Also used sonar, and audition and sibelius. Switched almost totally to linux also for audio&music though (ardour, traverso, musescore). Quite happy.

I used (and in fact use) a second internal HD for audio and video edition and data storage. It's ntfs, for the sake of sharing with win2. The first internal HD is for the operating systems, currently XP, UbuntuStudio Karmic and UbuntuStudio Lucid. I like this one to be fast (7200 rpm).

Side note: 7.10 was gutsy gibbon, wasn't it? He he, somehow old. If for some reason you don't get well with ubuntu but want to use linux, you could consider using an alternative, something as [avlinux]("http://www.bandshed.net/AVLinux.html") . It even can run live ;) 

Cheers

---

### Post by sgx on 2010-12-21
> **garyed said:**
> I'm getting ready to do a new install of U-studio 10.04 amd64.
Just looking for recommendations for partitions & drives. 
Any info or ideas appreciated. 
I'm coming from XP using Cakewalk Sonar Home Studio XL where I always used a separate drive for audio than for the OS. Does anyone do it like that here? I've actually got U-Studio 7.10 working pretty good but every version since then I've had problems with over runs & latency so I've stuck with XP to do any serious music. I really want to go Linux all the way for my DAW so I'm curious how others set up their systems. I'm assuming that I'll get Jack working with no problem for now but if not that would be another thread.
Hi, separate drives for separate tasks are the norm for recording musicians.
In addition, a separate /home partition is needed so you can reinstall linux without reconfiguring your net accounts and gui choices, and the .wine folder can be preserved with a complex vst setup intact. Saves
many hours per year.
Cheers

---

