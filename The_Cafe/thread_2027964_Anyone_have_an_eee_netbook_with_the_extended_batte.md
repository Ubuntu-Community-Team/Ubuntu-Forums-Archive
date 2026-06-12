---
title: "Anyone have an eee netbook with the extended battery?"
date: 2012-07-17
forum: The Cafe
---

### Post by mr-woof on 2012-07-17
Hi,

as per title, does anyone have an eee netbook with the extended battery? If yes, how long is it lasting etc?

I've got a eee 900 and I'm thinking about buying one, my current 4400 battery only lasts around an hour or so which isn't ideal.

:)

---

### Post by Nytram on 2012-07-17
My eee 1005 has the 6 cell battery, it lasts for around 6-7 hours on Linux, and 7-8 on Windows. I did a search on ebay for batteries a while back and noticed there are longer lasting ones available, 9 cell and above I believe, going for a reasonable price.

---

### Post by mr-woof on 2012-07-17
thanks, the big battery is only around 30 pound. I'm just wondering how many hours I'll get out of it.

You say 6 cell, any ideas what that is in mah? My current battery is 4400mah

---

### Post by Paqman on 2012-07-18
> **mr-woof said:**
> my current 4400 battery only lasts around an hour or so which isn't ideal.


It's probably just thrashed out. I've got a 4400mAh and I get at least about 5h out of it.

I've looked at one the massive batts, but you give up a lot of the portability of the netbook, which is the whole point of having one.

---

### Post by Nytram on 2012-07-18
Just checked it and mine is the same at 4400 mah, I think the 9 cell is supposed to give around 12 hours.. not certain but I looked into it a couple years back when I was considering getting one. Something else I read was that some of the batteries are low quality and don't last very long.. so it might be worth looking at some user reviews of the one you're after before buying.

---

### Post by coldraven on 2012-12-16
I've just been given a 900 with the bigger battery. It's a no-name but just says Type: P701H. Rating: 77Wh.
I don't know how long it lasts, I will post back later.
I just flashed the BIOS to the newest version which I read has better fan control and should make the battery last longer.
I should make a how-to because it took hours when it can be done in minutes if you know what you're doing :(

---

### Post by Lars Noodén on 2012-12-16
What was the easy way to update the BIOS?

---

### Post by coldraven on 2012-12-17
> **Lars Noodén said:**
> What was the easy way to update the BIOS?
I wasted hours on this so I can say that I'm now an expert :)
Download 900-ASUS-1006.ROM from the Asus site
Rename it to 900.ROM
You need to make/have a USB stick with maximum 512MB formatted to FAT16
I only have a 8GB stick so I used gparted to do the following:
Delete the existing partition.
Create a new one, I chose 256MB to be on the safe side.
Format the partition to FAT16
Leave the rest as "Unallocated"
When gparted has finished, remove and replace the stick so that the file manager detects it.
Copy 900.ROM to the stick
**Make sure that the power lead is connected**
Boot your eeepc with the stick in holding  Alt+F2 during the POST messages.
(no need to alter the BIOS boot settings)
After a few seconds of black screen you should see the EZflash utility which will automatically flash the BIOS in about three minutes.
If it gets stuck on "Reading file 900.ROM" then switch it off, something is not working.

I think the fan is running a lot less with this upgrade.
I've not yet had the time to test it with a DVD/video playback to check the battery life.

Don't forget to re-format you stick back to it's original state, mine was NTFS.

---

### Post by 3rdalbum on 2012-12-18
I got a 9 cell battery for my Aspire One. From eBay. It still works, unlike my genuine 3-cell batteries. My netbook is still acceptably portable and the bigger battery helps lift the keyboard and allow more airflow.

---

