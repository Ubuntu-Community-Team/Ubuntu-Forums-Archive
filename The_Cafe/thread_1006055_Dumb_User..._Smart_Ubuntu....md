---
title: "Dumb User... Smart Ubuntu..."
date: 2008-12-08
forum: The Cafe
---

### Post by solitaire on 2008-12-08
OK..
Here's a thread where you can post all those little dumb mistakes we make and which Ubuntu works out (or works around.)

Here's my offering......

_**Dumb user bit:**_

Decided to tidy up and wipe my free space. so do the usual 'dd' command with 'urandom' on all my free space (over 2 drives), then i decide to clean out my 2Gb swap-file partition using the same command!! 

So I ran 'Swapoff' and set about running the 'dd' command again on the partition with the swap file.

So after the wipe is finished i decided to reboot.

2 weeks later i noticed that conky is showing my Swap file is running at 68%!! (it's never went above 15% in the past!). Here's me thinking i've got a rouge bug or process or worse a trogen on my system!!

Turns out i've not been using my 2Gb swapfile but a smaller 200Mb swapfile Ubuntu set up when it could not find the UUID of my old (now scrubbed!) swapfile!!

_**Smart Ubuntu bit:**_

The OS ran fine on that 200Mb Swapfile! so much that I never noticed ANY slowdown. If I remember Windows in the same situation (no pagefile) it would scream blue murder at me the second it rebooted!!

Quick edit of 'fstab' with the correct UUID then a reboot and i got my 2Gb swapfile back!

I'm thinking of changing that 2Gb swap partition down to a 500Mb one. leave more room for root :D:D

But wil lwait and see how much swap i use when i upgrade from 755Mb up to 1Gb or ram... :D:D

---

### Post by cardinals_fan on 2008-12-08
You're using swap with 755 MB of RAM?!

---

### Post by WaeV on 2008-12-08
Some people like to use the hibernation feature.
I have 2GB / 300GB as swap with 4GB ram.  Probably too much, but it made all the numbers come out round. :)

A dumb mistake by a friend:
"I wanted to set up a home printer server with an old PC, so I downloaded Ubuntu Server.  Where's the desktop?"

A dumb mistake by me:
See above.  (lol)

---

### Post by sillycheese420 on 2008-12-08
every1 who uses MICRO$HAFT WINDBLOWZ is an idiot and everyone who uses superior Ubuntu is totaly aweomse! over nine thausand lolz!

:confused::confused::confused::KS:KS:KS:popcock:

---

### Post by hardyn on 2008-12-08
<there used to be spam above my post... now that it has been removed my post is somewhat irrelevant>



HAHAHAhahahahaha...

i should not encourage spam, but that was sooooo random...

HAHAHAHAHAahahhaha

---

### Post by WaeV on 2008-12-08
I'm curious as to how the forum shows that sillycheese420 has 0 posts...?

Another dumb mistake I just remembered:
I was following an online tutorial for formatting an extra ext2 partition on my iPod using fdisk.  The guide assumed the hard drive was hda, and that as the the only external drive, the iPod would be sda.  I was following command by command and almost told it to write when I realized my SATA drive is listed as sda...  That would have been a doozy of an error.

---

### Post by chris4585 on 2008-12-09
> **WaeV said:**
> I'm curious as to how the forum shows that sillycheese420 has 0 posts...?


All of his posts are not in any support thread, so 0 support posts

---

### Post by WaeV on 2008-12-09
Oh yeah... (<<Dumb user)

---

### Post by magmon on 2008-12-09
@cheese

***Some*** people have lesser experiance, and are not able to use linux. They're not stupid, just not experianced (=P, For example, people who only use their computer for email/browsing). ***Others*** are old or are familiar with windows, so they use it. (For example, my grandparents. Too old to learn a new OS xD) _No lack of intelligence_. And, *still* others make fun of things they dont use simply because ***they*** are superior, and everything ***_THEY_*** do is better and what they dont do blows. (For example, Cheese)

Also, ***better*** is in the eye of the user. Mocking the other OS's will get you no ground with me, bud.

---

### Post by abhilashm86 on 2008-12-09
> **WaeV said:**
> I'm curious as to how the forum shows that sillycheese420 has 0 posts...?

Another dumb mistake I just remembered:
I was following an online tutorial for formatting an extra ext2 partition on my iPod using fdisk.  The guide assumed the hard drive was hda, and that as the the only external drive, the iPod would be sda.  I was following command by command and almost told it to write when I realized my SATA drive is listed as sda...  That would have been a doozy of an error.

sillycheese420 alwayzzzzzz posts in community cafe!!!!!!so it shows 0 posts!!!!!!!it would be cooler to hear he has got banned,isn't it:lolflag::guitar:

---

