---
title: "Repository Speed"
date: 2007-01-05
forum: Repositories &amp; Backports
---

### Post by Buickman on 2007-01-05
Is anyone else having speed issues with the main, universe, and multiverse repositories? I'm on broadband, and I''ve only been getting about 4k - 24k. In the past it's been at least 100k. This has been going on at least since last weekend when I did a reinstall.

---

### Post by scrooge_74 on 2007-01-05
It could be related to the problems do to the earthquake in Taiwan

[http://news.bbc.co.uk/2/hi/asia-pacific/6211451.stm](http://news.bbc.co.uk/2/hi/asia-pacific/6211451.stm)

---

### Post by Buickman on 2007-01-05
Wow. I guess that's what I get for sleeping under a rock. So I assume that's where the repositories are physically located?

---

### Post by scrooge_74 on 2007-01-05
I deal with suppliers from China and I did not occur to me they were having troubles with that until one of them called me and told me about it, and that until further notice we had to work the old fashion way: fax and phone

:D

---

### Post by chr1831 on 2007-01-06
> **Buickman said:**
> Is anyone else having speed issues with the main, universe, and multiverse repositories? I'm on broadband, and I''ve only been getting about 4k - 24k. In the past it's been at least 100k. This has been going on at least since last weekend when I did a reinstall.

i can download from ubuntu in 2hours, firefox to install from the repo's 4hours :/, anyclue when the problem will be fixed?, this speed is driving me CRAZY!!!


are there mirriors for the repo's?

---

### Post by scrooge_74 on 2007-01-06
It all depends where you are and which severs you are using for upates.  Try to use severs close to you.  If the problems in Asia are affecting you this is going to take a few weeks.

They have to take ships out there, then they have to repair the damage, and everything has to be done out at sea

---

### Post by jawknee530 on 2007-01-06
I am having the same problem but i dont think that mine is due to the quakes because yesterday my repos were downloading fine and now they are crazy slow.

---

### Post by chr1831 on 2007-01-06
> **scrooge_74 said:**
> It all depends where you are and which severs you are using for upates.  Try to use severs close to you.  If the problems in Asia are affecting you this is going to take a few weeks.

They have to take ships out there, then they have to repair the damage, and everything has to be done out at sea

ucsb is close to me, can i use them? (with apt)

is there a list of repo mirrors?

---

### Post by JPMaximilian on 2007-01-06
I did an reinstall (lousy time I guess) I'm getting between 24 and 2 KB/s.  Painful is right.

---

### Post by quartzy on 2007-01-06
There are lots of mirrors, I can't find the list of prefixes though :\

You use them by making the lines in your sources.list (or using the gui version) look like:

```
deb http://nz.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

```

where nz stands for New Zealand in my case.

---

### Post by chr1831 on 2007-01-06
im on the us ones...., i would love a prefix list :D

---

### Post by quartzy on 2007-01-06
I didn't find a list however I found [this]("http://www.ubuntu-nl.org/source-o-matic/"), which will do the job of telling you what the prefix is :)

---

### Post by chr1831 on 2007-01-06
im updating at 81kb WOOT!!!!!!!!!!! Thanks A Lot :D, how did you find it?, im so glad im not downloading at 3xxxK/s anymore it took so long to install firefox it was so sad :'(

---

### Post by quartzy on 2007-01-06
> **chr1831 said:**
> Thanks A Lot :D
No Problem :) 

> how did you find it?

I googled '"nz.archive" ubuntu' or something and there was a link to that page within another page, flukey.. :-k

---

### Post by JPMaximilian on 2007-01-06
So should if I'm in the US and I add the Canadian sources list will it look at both and choose the fastest?  Or just the first one it comes across?

---

### Post by scrooge_74 on 2007-01-06
> **JPMaximilian said:**
> So should if I'm in the US and I add the Canadian sources list will it look at both and choose the fastest?  Or just the first one it comes across?

Not sure how it is done, I think it will update the information from all the servers and then choose those that are faster, unless a package you are getting is only on an specific server

---

### Post by Elvish Legion on 2007-01-06
Ok well even using the US servers I'm getting horrid speeds, I contacted ISP and they reset my modem and said if it doesn't clear up then its either

1) Mirror issue
2) Contact again and try more steps...

I'm getting like 6469 bps dls.

---

### Post by quartzy on 2007-01-06
Is it just the updates or is it the internet in general?

---

### Post by Elvish Legion on 2007-01-06
As far as I can tell just the updates, surf speed and downloads from the net are going at full speed...

So far I've tested

Automatix: Slow
Updates: Slow
Installing from repos: Slow

---

### Post by quartzy on 2007-01-06
They all use the same thing underneth it all ;) 

Have you tried a mirror close to you? 

If it's not that then I really don't know sorry, maybe a firewall? Although that seems unlikely..

---

### Post by Elvish Legion on 2007-01-06
I used the source o matic to generate a source.list of US sources.

I don't think its a firewall, as this is the first time  I've ever had this problem and nothing about my network setup has changed..

---

### Post by quartzy on 2007-01-07
Try the canadian mirror maybe?

---

### Post by acerbix on 2007-01-07
Canadian mirrors are marginally better... getting ~ 15 kbps... 

Any other mirrors working faster?

---

### Post by Elvish Legion on 2007-01-07
That seems to have sped it up a bit, still not where I'm used to but now at least 50 kbs avg....better than I could get even hard wired

---

### Post by quartzy on 2007-01-07
Try other closeish servers? Mexico (mx). Maybe some european ones.. Pompyland (gb)?

Edit: [this]("http://ubuntuforums.org/showthread.php?t=333124") thread suggested removing the prefix entirely.

---

### Post by acerbix on 2007-01-07
Try Australia... I'm getting ~ 150 kbps :-)

---

### Post by acerbix on 2007-01-07
I started off with not having mirrors in the source.list file... didn't help me any... I guess the non-local addresses do some location resolution and point you to the closest mirrors... which works most times, except when US mirror have problems :-)

[EDIT:]   I copied my original sources.list back after reading the other thread... I am now getting high speed connections. So it appears that not having country prefixes is the way to go!

---

### Post by Elvish Legion on 2007-01-07
So it would just be archive.ubuntu instead of ca.archive or us.archive?

---

### Post by acerbix on 2007-01-07
That's correct: e.g 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted

---

### Post by Elvish Legion on 2007-01-07
Wow that really helped, now I'm back up to speed, thanks crew, yet one more reason I stay with ubuntu

---

### Post by orb9220 on 2007-01-07
Yep I changed to main server in synaptic and I went from 8906B/s-10KB/s to 80KB/s -150KB/s 

come on US upgrade please.

---

