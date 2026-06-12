---
title: "Long Overdue Update..."
date: 2012-01-21
forum: Server Platforms
---

### Post by The_Dud on 2012-01-21
I'm going to get down to business quick here, but a little bit of background.

A few years back I built a new computer and I installed Apache/PHP/MySQL on the already aging Windows installation. I'd played with Ubuntu on and off since 5.10, so I figured I'd try Ubuntu Server on the old computer. Everything went splendidly, installed 8.10 and really started to tackle shell commands. Months later, 9.04 comes out and the update goes without a hitch...but that's when it stopped.

For the past few months, I've been wanting to update to 11.10, but it's mostly a lazy-type issue now. I've got everything backing up as I type, but no matter how sure I am that I have everything backed up, I feel like I'm going to miss something. 

I'm not terribly worried about anything on it as far as intruders, and it's just this tiny little personal website that isn't even indexed by google. It's mostly about wanting the upgrade to be kinda seamless, and would prefer not to lose anything...but I'll get to that in a second.

So I've got a few questions here.
1. Would it be of any use to shrink the old server partition, install on the new, make sure everything's running smoothly, and then remove the old partition?
2. [s]Is there any way to stream the list of currently installed packages to a text file? I know most of them, but I know there's going to be something I miss.[/s] [Easy enough...I feel derpy...]("http://ubuntuforums.org/showthread.php?t=261366")
3. Is there anything really new about about 11.10 that I'd need to get used to?
Finally, I suppose; 4. Could I just upgrade instead of having to fully reinstall? Should I? Honestly, I'd rather not, but still a thought in the back of my mind.

ANY help is appreciated, thanks.

---

### Post by volkswagner on 2012-01-22
Shrinking the partition can be just as risky as updating.

I suggest backing up your entire /etc and /home folders and any other data locations (/var/www).

Then you can create an image of the system using something like Clonezilla or a dd image.

I would then do a fresh install of 10.04 or 12.04 if you can wail until April.  I suggest the long term support release so upgrades won't need to occur so often.

Do the fresh install and use your config files backed up in /etc to get your services configured the way you had them. Add your content and all should be well.


If things go sour, you can always restore you image from the Clonezilla backup.

---

### Post by The_Dud on 2012-01-22
Much thanks for the reply, Volks. That was another thing I was thinking about, the LTS release. I'm a student at a local university (Software Development) and working at a foundry, so I don't have all of my time to devote to this side-project of mine. If I could put 3 years between upgrades, that'd put a bit of peace on my mind.

I also completely forgot about dd/Clonezilla. I really don't use it enough to think about it, but thanks for the pointer! I'll probably be doing the upgrade tonight at some point and I'll let ya know how it goes.

---

### Post by 2F4U on 2012-01-22
The server edition has 5 years of support, not just 3 years. So if your time is limited, the server lts release is definitely what you want.

---

### Post by bab1 on 2012-01-22
> **2F4U said:**
> The server edition has 5 years of support, not just 3 years. So if your time is limited, the server lts release is definitely what you want.

@The_Dud,

It is worth noting that the next LTS release is 12.04 (this coming April).  I would consider delaying an update (or install) just a little bit longer.  Support for 11.10 lasts only to 2013, while 12.04 will have support until 2017!

All my data is on separate partitions so I can install without losing it.  I have a separate hard drives for the /home and /srv file systems.  I keep backup the /etc file system for future reference.

---

