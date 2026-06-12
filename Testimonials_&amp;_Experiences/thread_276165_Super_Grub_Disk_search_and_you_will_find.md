---
title: "Super Grub Disk search and you will find"
date: 2006-10-12
forum: Testimonials &amp; Experiences
---

### Post by dddouglas on 2006-10-12
I have been experimenting with Ubuntu since April. My adventure started with frustration with having to purchase Windows for a machine that I had built. Back then, some 5 years ago, I tried Mandrake and spun my wheels, same thing with Red Hat. So in the eventually I purchased an OEM Windows disk and went on my merry way. 
Then other propriety problems that required more money to be dump into the black box sitting under my desk popped up.  I started looking at Linux again. 
A friend suggested I try a Live CD of Linux so in my search I stumbled across Ubuntu and it seem to be the top of the heap. Before I did anything I read daily on the forum, the wiki  and then I found the holy grail [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)  which gave me step by step instructions to successfully set up my dual boot (dual boot necessary for those who have stuff in bill’s world). With printed copies in hand I performed this task on my laptop to evaluate and eventually do our desktop. I needed to reassure my wife that this would not be a significant road block for her.  After updating to Dapper and working out some wrinkles with wifi. I felt I could do the other box. 
Since I had done two laptops successfully, one for a friend and experimented with various desktops (I prefer KDE :KS ) I decided to do the desktop. However my wife kind of freaked out on the prospect of something new and balked. In my desperation to please her I set GRUB to default to Windows (thinking of bringing her along slowly). But somehow Windows had a hissy fit and required a restore. Naturally it rewrites the MBR.  I knew from reading that all was not lost so I set out find the fix. Super Grub Disk [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)  is much easier than I expected. Hallelujah. 
My Ubuntu has been characterized by search and find. I am always amazed at the amount of post asking the same thing over and over. I realize much of this is juveniles that have no patience for searching, reading first or just wanting to be heard but in the end the pay off of being able to kick Microsoft to curb is priceless. Unless you are Beta testing most questions have been asked and if you do ask don’t leave the community hanging. Let us know if it worked. 
AYSIU has an excellent recourse also [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  
IMHO

Doug :KS

---

### Post by K.Mandla on 2006-10-13
Thanks for the Super Grub Disk link! That could be very useful. I'm going to give it a shot later, if I can convince Windows to break ... which shouldn't be too tough. :)

---

### Post by dddouglas on 2006-10-13
I am just looking for the day when my MBR get written over and GRUB is restored and windows ain't on it.

---

### Post by argie on 2006-10-14
Haha dddouglas. Thanks for the Super Grub disk link too. I'm sure it'll be useful. (younger brother still uses windows, alas)

---

### Post by bulldog on 2006-10-15
> **dddouglas said:**
> I am just looking for the day when my MBR get written over and GRUB is restored and windows ain't on it.

Can help you with that though :D :D 

```
gksudo gedit /boot/grub/menu.lst
```

Delete the windows part save the file and your done!:cool:

---

### Post by dddouglas on 2006-10-15
Still got hold of some apron strings I guess. Likely will cut them in a couple months.

---

