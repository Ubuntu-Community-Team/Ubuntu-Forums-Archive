---
title: "The smartest upgrade I ever did."
date: 2012-08-06
forum: The Cafe
---

### Post by irv on 2012-08-06
I have an older laptop and was really thinking about getting a newer one because it was getting so slow. I started reading about SSD's and thought I would give one a try. I started watching for sales and found a 180 gig SSD for $149. I order it, got it, installed it, and did a clean install of 12.04, and I can't believe how fast this old laptop runs. All I can say is WOW!. From a cold boot, it takes about 15 seconds, and things just load super fast.
Thought I would share this simple upgrade with you.

---

### Post by Copper Bezel on 2012-08-06
Yeah, and I think part of the wow factor is just the usual effect of starting off with a clean, new system, too, but the difference with an SSD is amazing. I've upgraded three machines this way, one of them mine and two for friends and family, and it's always a wonderful thing to see an old piece of kit get a new trick.

---

### Post by pqwoerituytrueiwoq on 2012-08-06
be sure to enable trim and AHCI in your bios and use noatime on a ext4 partition
what brand did you get?

This is what i have on my ssd in my fstab
```
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4   discard,noatime,errors=remount-ro 0       1
```

---

### Post by Jakin on 2012-08-06
I can attest to the speed of SSD, my kubuntu boots in 5seconds. 

I remember waiting upto a minute or so to boot with a traditional HDD.. its definatly worth the upgrade, assuming one has the cash, and spends time with their computer alot- i for one never thought it safe to leave a computer on from now til whenever, just so it loads quicker via sleep or hibernation. 
Loading your programs shouldn't have to take another minute or so either, and with SSD it wont.

---

### Post by irv on 2012-08-06
> **pqwoerituytrueiwoq said:**
> be sure to enable trim and AHCI in your bios and use noatime on a ext4 partition
what brand did you get?

This is what i have on my ssd in my fstab
```
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4   discard,noatime,errors=remount-ro 0       1
```

OK, I did an edit on my fstab added the noatime to my ext4 partition. I was wondering what the discard does. I added it also but wasn't sure if I should or not?
Here is my entry in the fstab file.
```
UUID=9c02b696-35d5-4a8b-a8fa-37de6aa8bc85 /               ext4    discard,noatime,errors=remount-ro 0  
```
EDIT: almost forgot, I couldn't find this in my BIOS. "enable trim and AHCI".

---

### Post by Minipalmer on 2012-08-06
Your post interested me enough to go research a little more on the SSD's. I have to say, I'm very impressed with the results many other people have had. 

I'm running an old laptop as well, and this may be just the thing to help me from getting too bogged down with new programs that come out. But my question is: Wouldn't the $100+ spent on a project like this be just as well spent on a new laptop?

Just thinking out loud!

---

### Post by irv on 2012-08-06
> **Minipalmer said:**
> Your post interested me enough to go research a little more on the SSD's. I have to say, I'm very impressed with the results many other people have had. 

I'm running an old laptop as well, and this may be just the thing to help me from getting too bogged down with new programs that come out. But my question is: Wouldn't the $100+ spent on a project like this be just as well spent on a new laptop?

Just thinking out loud!
I was looking at getting a new laptop, but my wife said I should try to make my old one last a little longer. The good thing is if and when I get a new laptop I plan on using this SSD in the new one. If it is still running when I do get a new one I have two other Hard Drive I can put in it when I go to sell. I have a 350 gig and a 500 gig. 
So if you plan on getting a new one down the line, you can use the SSD in the new laptop just like I plan on doing. I looked at it as an investment.

---

### Post by neodirtchief on 2012-08-06
My hdd went bad while deployed and I replaced it with an ssd.  Once loaded with the OS it responded fast. Everyone thought I had purchased a new EEEPC and then thought I left it on all the time due to the fast load speeds.
Well worth the investment.

---

### Post by irv on 2012-08-06
I will never build or buy another computer that does not have a SSD.

---

### Post by pqwoerituytrueiwoq on 2012-08-06
it is in the same place you would go to said up a raid array, the default is usually IDE
discard enables trim, well if you have AHCI enabled

---

### Post by phrak on 2012-08-06
I've been watching SSD's for a little while now... Hopefully I'll be able to pull the trigger on this one myself soon.

---

