---
title: "Can I install windows XP dual boot on my vista PC?"
date: 2008-06-09
forum: Windows
---

### Post by Fzang on 2008-06-09
Reason I want to dual boot is mainly because I don't know if everything will work correctly in XP (drivers, apps, etc...) and my dad tends to freak out when something happens to my computer because I wasn't careful enough, messed with some pirated virus haxor software and yada yada...

I've heard something about having to install XP and vista in a specific order, or else one of the OS will overwrite the other or something...

And lastly, can I partition my vista harddisk without having to format/reinstall/stuff?

---

### Post by LaRoza on 2008-06-09
> **Fzang said:**
> 
And lastly, can I partition my vista harddisk without having to format/reinstall/stuff?

The whole thing? No. You can resize the Vista partition to make room though.

I don't know how will that will work, Windows isn't Linux and  Windows is very hard to install.

---

### Post by Joeb454 on 2008-06-09
Windows isn't *that* hard to install, especially if it's the only OS you're installing ;) It's just not as easy as Ubuntu :p

Anyway - you need to install XP first, and then Vista. Though if you have an XP disc, you can free some space using Vista's partitioning tool, and then install XP into that unpartitioned space.

Though note that you need a **FULL** Windows Vista install disc. And the command is different to the XP one (search the Microsoft knowledge base for "fixmbr Vista" it'll come up :))

---

### Post by AndyCee on 2008-06-09
It can be done, this guide has been around for ages:

[http://apcmag.com/howto_category.htm?cid=198](http://apcmag.com/howto_category.htm?cid=198)

As always, backup first. Maybe read all the comments to be aware of issues.

---

### Post by Fzang on 2008-06-10
Oh joy, my vista anytime upgrade CD actually works! :D

Thanks Andy, best link ever

---

### Post by Fzang on 2008-06-10
Argh, tried shrinking my disk volume but it will only let me shrink down **ONE DAM GB!**

Can I partition my disk in another way without deleting the current contents?

---

### Post by fiddledd on 2008-06-10
Assuming you have enough free space to shrink and create a new partition, vista shrinks/creates etc without a problem for me. I had to do it a few times. You can try defragmenting first, that might give you enough contiguous free space. Remember to backup all important stuff first.

---

### Post by Fzang on 2008-06-10
I defragged whole computer few hours ago

I have 95 GB free space out of 150 GB, but vista will only let me shrink 1 GB

:confused:

---

### Post by fiddledd on 2008-06-10
Here's a link with an explanation and some workarounds:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by LaRoza on 2008-06-10
> **Joeb454 said:**
> Windows isn't *that* hard to install, especially if it's the only OS you're installing ;) It's just not as easy as Ubuntu :p

Though note that you need a **FULL** Windows Vista install disc. And the command is different to the XP one (search the Microsoft knowledge base for "fixmbr Vista" it'll come up :))

It isn't the installation itself, which is long, but the next few hours after the mandatory reboots.

Slackware is easier to install than XP. If everyone had to install their own OS, Windows wouldn't be popular (and I'd be rich off those who do want Windows)

---

### Post by Fzang on 2008-06-10
I did everything the guide said, removing page file, cleaning up here and there, defragging

Still not working! :(

---

### Post by Joeb454 on 2008-06-10
I wouldn't recommend it, though you can partition your disc from an Ubuntu Live CD (I did this to get around Vista's partition editing..."issues" ;)

And LaRoza - I totally understand what you mean about Windows installs now you said that ;)

---

### Post by Fzang on 2008-06-11
I know that there's lots of programs that can partition without vista's "shrink volume" but I'm quite afraid of making vista unbootable if I force-partition it :|

---

### Post by swoll1980 on 2008-06-11
> **Fzang said:**
> I know that there's lots of programs that can partition without vista's "shrink volume" but I'm quite afraid of making vista unbootable if I force-partition it :|

back up your data and go balls to the walls if worse comes to worse wipe it and start over

---

### Post by Fzang on 2008-06-11
Well, guess I'll have a go

---

### Post by AndyCee on 2008-06-13
> Argh, tried shrinking my disk volume but it will only let me shrink down ONE DAM GB!

Heh, that's awesome. I mean...sorry...

Can anyone tell me why Windows Vista has a partition editor at all? Perhaps for admin resources or backup...?

Let us know how you go, Fzang.

---

### Post by Joeb454 on 2008-06-13
> **AndyCee said:**
> Can anyone tell me why Windows Vista has a partition editor at all? Perhaps for admin resources or backup...?

I'd imagine it's so you can keep your documents on a separate partition, in the event that you would need to reinstall.

Also it could obviously be used for backup :)

---

### Post by Fzang on 2008-06-13
Well, as I had nothing to lose, I backed up my tiny 4 GB of stuff on a stick and killed vista, then installed XP

However, to my anger, XP doesn't have sufficient drivers for my networking so I only get around 1.5 mbps download speed, whereas vista downloads with 3.8 mbps

So, here I am, with a clean vista install.....

ON THE OTHER HAND, the disk is now clean and I've managed to split my disk in 2, wooh for that:)

---

### Post by AndyCee on 2008-06-22
So you have it working?

---

