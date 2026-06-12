---
title: "potential lemur purchase"
date: 2011-02-01
forum: System76 Support
---

### Post by DNAtsol1 on 2011-02-01
HI, I'm looking for a laptop to use for work (presentations, gradebooks, playing video clips for lectures, etc.) and at home I'd like to be able to stream live events to my HDTV via hdmi as well as the typical browsing, music, really basic photo/video editing (cut, add music track type stuff) etc. 

I'm thinking of getting a lemur with:
4 GB RAM
640 GB HDD
intel wireless card

So, I have three quick questions that need answers before I pull the trigger (hopefully today).

1. Is 4GB RAM sufficient for streaming on wireless-n? Also, when I stream or play video on my current laptop, my cpu starts screaming for mercy before quickly shutting down from overheating - is that likely to happen with a lemur? I figure my current setup is just not optimized for my hardware and I'm not that proficient at hacking this yet)
2. I've been playing with ubuntu since hardy and I've now made sure my /home is on a separate partition for when I do the inevitable (:p) clean install of some newer version. Does system76 partition the drive or is everything in one big block like a standard unbuntu install?
3. Is there a utility to move my /home files and settings from my current to the lemur? 


 err OK 1 more question... I've not used 64-bit versions of ubuntu. Is there a link you can give to help me understand the differences (both in terms of performance and hiccups I might expect using my favorite apps like libreoffice/openoffice, virtualbox, freemind)

Thanks for any help.
DNAtsol
My first plunge into factory installed ubuntu!

---

### Post by isantop on 2011-02-01
> **DNAtsol1 said:**
> 1. Is 4GB RAM sufficient for streaming on wireless-n? Also, when I stream or play video on my current laptop, my cpu starts screaming for mercy before quickly shutting down from overheating - is that likely to happen with a lemur? I figure my current setup is just not optimized for my hardware and I'm not that proficient at hacking this yet)
2. I've been playing with ubuntu since hardy and I've now made sure my /home is on a separate partition for when I do the inevitable (:p) clean install of some newer version. Does system76 partition the drive or is everything in one big block like a standard unbuntu install?
3. Is there a utility to move my /home files and settings from my current to the lemur? 

 err OK 1 more question... I've not used 64-bit versions of ubuntu. Is there a link you can give to help me understand the differences (both in terms of performance and hiccups I might expect using my favorite apps like libreoffice/openoffice, virtualbox, freemind)

Thanks for the questions! 

1. I don't think you're going to have too many problems with 4GB of RAM. I typically recommend getting the best performance you can afford, so if you can go higher I would. But, it shouldn't be required.

2. We used to setup the disk like that, but that setup is slightly less user friendly if you run out of space in either partition, so we now use a more standard single-partition approach. The good news is that you can specify your old root partition to be the new one when you setup Ubuntu, and keep all of your data intact; Ubuntu will only overwrite system files.

3. I think the best way to do that would be to share the files from the old computer to the new one. There are a couple of ways to do this, and the easiest is probably to simply enable sharing of the files by right-clicking them. 

4. 64-bit Ubuntu is very stable and it works great. Due to the way Ubuntu generates packages, there are 64-bit versions of nearly every package in Ubuntu's repository. There may be issues with 3rd-party .deb files, but otherwise everything should go great.

---

### Post by DNAtsol1 on 2011-02-01
thanks for the response. I think I'll take the plunge.

Just one more question regarding the sharing files part. Will this allow me to copy over my evolution emails, google calendar settings and contact as will (ie., does simply copying .evolution folder do the trick or do I import these files once I setup evolution on the 76 machine.

Thanks
DNAtsol

---

### Post by isantop on 2011-02-01
No, this will only grab your files and folders. For getting Evolution over, you'll need to back it up separately (Although when you back it up, the file created can then be shared with the rest of them, and re-imported).

[Here](http://www.ghacks.net/2010/05/31/backup-and-restore-evolution/) is a great tutorial on backing up and restoring Evolution.

---

### Post by DNAtsol1 on 2011-02-01
Thanks. I checked into evolution backups and figured this was the case but I wanted to double check. I want this transition to go as smoothly as possible so getting these questions addressed is really helpful.

---

