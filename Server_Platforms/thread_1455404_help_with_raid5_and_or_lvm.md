---
title: "help with raid5 and or lvm"
date: 2010-04-15
forum: Server Platforms
---

### Post by speed32219 on 2010-04-15
Here is what I have and what I want to do.

3 new 1.5TB HD.
1 used 1.5TB hd with 980MB of data.

I want to set up a raid 5 with a hot spare.  I have music, pictures, videos, and movies (About 2.8TB worth).  I have had a mismatch of drives previously, 250GB, 2 320GB, 500GB, 2 1TB and now a 1.5TB all with data.  I have removed the one 250 and 2 320s and put the data on the 1.5TB that is currently installed.

What I would like to do is create a raid5 with the three new 1.5TB HD's, copy the data over from the currently installed 1.5TB and then grow or add that drive as a hot spare. Or just add it and then add another 1.5TB down the road as a hot spare  don't know for sure.

In addition since I have 2 1 TB drives, I could add 2 more (Good deals on 1 TB drives right now) and have a total of 4 1TB drives.  Could I have 2 raid5's (4-1TB's and 4-1.5TB's)in two separate arrays?  I really do not know if that makes sense or not but here comes LVM.  I am tired of managing my HD space and since i have multiple folders (Movies, music, pictures, videos) and within the movies folder I have R, G & PG folders for the ratings of the movies.  (Pwd protect the R so the kids can't get to it) So with LVM installed with the Raid5 I should be able to create my folders and just keep adding data and not worry about moving folders around when I grow the storage by adding new drives.  Is that correct?  Maybe someone could point me to a how to.

Also, if I create 2 arrays (And I need to know so I can order the 2 additional 1TB drives), then I could put all the music, G and PG content on the one array and all the R and spicy stuff on the other and password protect it.   

Any help or guidance would be appreciated. This can get confusing.

---

### Post by kenada on 2010-04-15
Hey,

All that is doable.

You can have multiple raid 5 arrays.
Expect it to take some time though :)

mdadm is what you'll need.

I don't have a lot of LVM experience, hopefully someone else can chime in and give you some advise :)


Just out of curiosity what you building this in? a rack or a tower?

---

### Post by speed32219 on 2010-04-15
A Rack 19 x 7 x 20 inch, istarusa.com model dAGE410U40TL-PM is what I am looking at.  It holds 10 3.5" hot swappable drives and can expand to 15 total and comes with the bays, cabing and port multipliers already installed. (Adding an additional 5-3.5" drive cage to replace the existing 3-5.25" external drive bays plus adding a port multiplier would be easy).

I am starting out with my current tower that can support 12 3.5" drives but only 5 can be hot swap.  Plus I want to get everything in a rack to clean up the mess, noise and heat.

---

### Post by kenada on 2010-04-16
Awesome, i've been entertaining a rack for a while now. Pricey bastards though.

Wonder what the noise is like?

---

### Post by speed32219 on 2010-04-16
Yeah, pricey, but if you price out individually the hot swap bays, 2 ea  port multipliers, power supply, cabling, etc. and even a tower case, it would cost  more than 499. IF they would just drop the price about 100. :)

That unit comes with one 120MM fan, so should be just about silent.
My main system has two 120MM fans and no cpu fan (AMD 5050e dual core) and you can't hear them, I have to put my hand up to the exhaust area to feel if they are on. I'm with you, looking for near silent if not silent operation. I would like to get the case  without power supply, and add a 120W DC-DC internal power supply with an external brick AC-DC, or a AC-DC 150W Power Board without fans.

Been checking the power consumption on the drives during start-up and I think it will work.  If I could just sequence the power on the two arrays.
Anyhow going to start the build today of the first Raid5, ordered the two additional 1 TB drives after your response last night. More than likely I will be back asking questions, my first Raid5 with LVM2.

---

