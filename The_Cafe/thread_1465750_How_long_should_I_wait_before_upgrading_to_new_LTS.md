---
title: "How long should I wait before upgrading to new LTS?"
date: 2010-04-29
forum: The Cafe
---

### Post by cloyd on 2010-04-29
I'm fairly new to Ubuntu and GNU/Linux. (Just since last November)  I am really liking 9.04 on one machine, and 9.10 on my netbook (less the Fisher-Price interface--really don't care for it). Not particularly technically gifted, but just enough to partition a hard drive (well, two of them) successfully and install Ubuntu. I expect to have a problem now and then, and the forum helps. Sometimes, I get some kind of answer or work around before the forum solves it. It is fun, but I really don't want to ask for problems. 
I need my computer for my livelihood, and some people will be somewhat irate with me if I spend all my time fixing my computer and not working.

So my question is this. I like the idea of using a long term support version. How long should I wait before upgrading? 

Also, what are the pro and cons of upgrading vs a fresh install?

Lastly, would the best route be to make a live cd or usb, try it, and if I like it, upgrade (or again, fresh install) ?

---

### Post by TheNerdAL on 2010-04-29
> **cloyd said:**
> 
I need my computer for my livelihood, and some people will be somewhat irate with me if I spend all my time fixing my computer and not working.


Yes, I hate that. I got a huge problem with Beta 2 and I think I spent a whole weekend trying to fix it and not being able to fix it. I had to do a reinstall of Ubuntu 9.10 instead. -.- 

You should wait like a week after a stable release is out because it may still have problems and people who install stable release will post on forums notifying the developers which might fix issues in the Stable Release.

As in The upgrading vs. fresh install debate. I recommend upgrading since it doesn't cost you anything. But you can do a fresh install if you have some extra CD-R's laying around. I heard that it is faster, but I don't know. But I recommend DVD-R's instead.

---

### Post by cloyd on 2010-04-29
I've been kind of peeking at the forums all day today, wondering what problems people were having. See a few. But if these were anywhere close to all the people who likely installing, it doesn't look like there that many problems. 

What bothers me about fresh install is getting my setup like it like, and keeping all my data (though I do have an external hard drive to help me out on this), and getting the applications I want all over again. But . . . they are free.   All they cost is my time. I'll be watching

---

### Post by mick222 on 2010-04-29
If you like 9.04 you can stay with it lucid is nice but you have no rush to upgrade . When you want to upgrade just open update manager by pressing alt +f2 then type update-manager -d
and there will be a button for a distribution upgrade . Make sure you have backed up your home folder first just in case.

---

### Post by Irihapeti on 2010-04-29
You could make either a spare partition or use an extra drive to test the new version. When you feel comfortable that the new version is doing what you want, you can then remove the older one and have the new one take its place.

That way, you still have the tried and true older version available for essential tasks.

I've used this strategy several times and I'm glad that I have. Sometimes, the running in parallel has only been for several hours.

---

### Post by andrewabc on 2010-04-29
Make sure to backup all your important data.

Test 10.04 with liveusb and/or livecd to make sure all the basic hardware/internet works with your computers.

Don't blindingly update to 10.04. Format/install usually works best.

---

### Post by cloyd on 2010-04-29
The comments are appreciated. I am fishing for common wisdom about upgrading among Ubuntu users. 

Backup . . . that seems to be a common subject in any type of computer discussion. (I hate to say it. I know I should have. I was lucky. I did not make backups of anything other than my most very important and personal files before I partitioned my drives. I may not always be so lucky).

At present, I think, I should wait a week or two (maybe a month), then make a live usb, and I am tempted to upgrade rather than fresh install. I wouldn't cry if I made a mistake and my windows partition disappeared, though I wouldn't do it on purpose right now. And I suspect that if anything does go wrong in the upgrade, I would be able to salvage quite a bit with a working live usb. I still need to backup my data. 

I hate  to backup. I've always been pretty good at backing up data, but not programs and the whole system. It has been this way since the old days of IBM XT's.

---

### Post by Bezmotivnik on 2010-04-29
> **cloyd said:**
> 
I need my computer for my livelihood, and some people will be somewhat irate with me if I spend all my time fixing my computer and not working.

Wait, especially if your current install is working OK, and only install LTS releases.

Do a fresh install.

Seriously, I would **never** use desktop Linux on a critical computer in heavy use on which money depended.  Botched update manager routines (servers down, etc.) have totally wrecked my 9.10 install...**TWICE.**  If it wasn't on a third-string hobby box, this would have been bad news.

---

### Post by Rasa1111 on 2010-04-29
well, 

 i have burned 3/ maybe 4 different discs now, 
 2 of them beta 2, one RC, and one LTS....

 and I run into the same problem everytime. 

Karmic installed and runs absolutely perfect on my computer,
but for the life of me.... 
 I cannot get these Live 10.04 CD's to get further than clicking on "try ubuntu 10.04 LST"..
(the screen either goes into power saving mode and turns off, never to do anything else)
                                 or
( the screen goes black, but the top half starts flashing in vertical wihte lines on the black background). 
 and never goes any further...

the the discs are fine, they check out fine, 
i just am not good enough at this stuff to figure it out yet apparently. lol

 I think I will wait at least a month to try again,
but I really do love Karmic, so im ok with it . lol

oh well, 
 it does look beautiful! :lol:
:)

---

### Post by Irihapeti on 2010-04-29
@Rasa1111:
What graphics card/chip do you have?

---

### Post by Rasa1111 on 2010-04-29
> **Irihapeti said:**
> @Rasa1111:
What graphics card/chip do you have?

,  Hey, 
to be honest I really dont even know.. 
I know to type "lspci" into terminal, 
But im not sure what im lookin for in all the info that comes back.

---

### Post by Irihapeti on 2010-04-29
Rasa1111:

Can you type
```
sudo lspci -vv -nn
```

in a terminal. It will ask for your password.

I've just realised, too, that we've hijacked someone else's thread. So, could you please start another thread in one of the technical areas, post the terminal output there, and I'll keep a lookout for it.

---

### Post by Rasa1111 on 2010-04-29
yes, i thought about that to, thank you Irihapeti,
and apologies OP and thread watchers. :)
i just felt bad to start another, with soo many new ones coming in. 
thanks.

edit: here it is man, thanks again
[http://ubuntuforums.org/showthread.php?t=1465883](http://ubuntuforums.org/showthread.php?t=1465883)

---

### Post by cloyd on 2010-04-30
Irihapeti:

quote: "I've just realised, too, that we've hijacked someone else's thread." 

I started the thread, and you are adding the kind of information I am looking for.  I'm new, and I may not have learned the proper good manners for the forum, but I'm interested in the problems others like you have had.

---

### Post by WinterRain on 2010-04-30
> **Bezmotivnik said:**
> 
Do a fresh install.


Quoted for wisdom. Upgrade and take the easy way out, but roll the dice, **OR** take time to backup and clean install with better chance of success. Hmmmmm......... :-k

---

### Post by Irihapeti on 2010-04-30
> **cloyd said:**
> Irihapeti:

quote: "I've just realised, too, that we've hijacked someone else's thread." 

I started the thread, and you are adding the kind of information I am looking for.  I'm new, and I may not have learned the proper good manners for the forum, but I'm interested in the problems others like you have had.

You're most welcome. Here's the thread that Rasa1111 started: [http://ubuntuforums.org/showthread.php?t=1465883](http://ubuntuforums.org/showthread.php?t=1465883)

---

