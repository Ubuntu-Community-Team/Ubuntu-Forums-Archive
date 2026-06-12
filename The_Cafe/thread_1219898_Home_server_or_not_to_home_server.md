---
title: "Home server or not to home server"
date: 2009-07-22
forum: The Cafe
---

### Post by Ian dewhurst on 2009-07-22
I was just after a little advice really.
Recently the company I work for has just purchased a new server and this leaves the old server redundant and doing nothing.
I could have the old one for free and was just wondering if there was any point in using it for a home server.
The specs for the old server are:
40gb HDD hot swapable, RAID capability and space for another 3 HDD
2 LAN cards
1gb RAM
CD drive
Zip drive
Floppy drive
Intel Celeron proccessor (shame really)
It also has Windows server 2000 on it but me thinks this will be removed for obvious reasons.
What I would like it do would be for it to share movies/pictures/videos/music wirelessly between mine 
and the MRS's laptop and backup data locally.
Would this be a reasonable spec server for doing so?

---

### Post by Bölvaður on 2009-07-22
this is pretty good server. You can use it for all sort of stuff. All from using it as additional hard disk space through NFS to something like a team speak server to talk to many people in a irc like voice conference.

---

### Post by Ian dewhurst on 2009-07-22
Pretty good, really? 
I didn't realise it was classed as good as I forced the company to get a new one as it couldn't cope; not enough HDD space, memory and the limited processor really meant lagging performance when more than one employee accessed the main database, never mind reading and writing files lol.
But I suppose I shall be using it differently and the processor could be changed, if neccessary?
Well my next question what OS would deem most suitable for what I would like to do?

---

### Post by aeiah on 2009-07-22
database access requires a lot more CPU than just sharing files and copying them for backup. you should be alright with the power of it. obviously the hard drive space might be an issue but that depends what you use it for. if you need more space it would cost the same amount if you put the HDDs in the server or if you put them in one of your normal computers, obviously.

basically the only negative effect is the electricity bill, but computers dont use too much on the grand scale of things.

---

### Post by aeiah on 2009-07-22
> **Ian dewhurst said:**
> 
Well my next question what OS would deem most suitable for what I would like to do?


just stick ubuntu server on there. you might want to install a desktop environment to start with and then when its up and running you can have it startup just to the CLI to avoid taking up resources needlessly. there'll be loads of tutorials for setting up fileservers and rsync backup servers on ubuntu server on this forum and around the web

---

### Post by Ian dewhurst on 2009-07-22
I shall give it a go then, what have I got to loose it is free.
I did think a couple of HDDs might've been needed as 40gb can filled quite easily.
As for distro wise OSOL looks quite interesting to say the least more so with the implementation of the ZFS filesystem, but more RAM would be needed me thinks.
It looks to have some perks, but I'll have to play around with it first to see if this would be a perfect server distro.

EDIT.
Didn't see the reply above now that makes me question my original decision some more time with google and playing looks fun - oh the wife shall be pleased now she won't see me for days lol.

---

### Post by HermanAB on 2009-07-22
Why do you even ask?  You want to tell me that you haven't got it home with Ubuntu booted and posting to the forum from it already???
;)

---

### Post by gn2 on 2009-07-22
As far as the hardware goes, it will probably be overkill.
My [NSLU2]("http://en.wikipedia.org/wiki/NSLU2") home file server has a 266mhz CPU and 32mb RAM.

---

### Post by benj1 on 2009-07-22
> **gn2 said:**
> As far as the hardware goes, it will probably be overkill.
My [NSLU2]("http://en.wikipedia.org/wiki/NSLU2") home file server has a 266mhz CPU and 32mb RAM.

+1
i was reading a 'post your server spec' thread the other day the most powerful one was a 512mb 500mhz job.

---

