---
title: "I had fun with a flying ant last night"
date: 2018-08-03
forum: The Cafe
---

### Post by Paddy Landau on 2018-08-03
I walked away from my computer for some minutes. When I returned, I noticed that my browser had been closed and reopened twice (missing all my tabs), along with a couple of other newly-opened windows, and all strangely resized.

Looking at this, puzzled, I noticed a flying ant walking away from my computer. Ah ha! The computer has a touch screen. That's what happened!

No biggie. I brushed away the ant; closed the windows; reopened the browser; resized it; and restored my tabs.

Shortly after, I started my daily backups The backup is incremental, so it backs up only the day's changes (I use [FONT=lucida console]rdiff-backup[/FONT], a great app). It normally takes 1 to 3 minutes depending on how much I've done. Only this time, it took half an hour!

A little investigation showed that this insect had somehow managed to delete all of my audio files and all of my photographs — 17½Gb in all.

(That's the sort of reason why I take daily backups!)

I restored the deleted data from the trash…

… reran the backups…

… and set my touchscreen to be off by default!

---

### Post by TheFu on 2018-08-03
Did a little research.  Is the touch screen infrared?

---

### Post by coffeefiend on 2018-08-03
Well now, that is certainly an interesting event. It is a good example of why having backups is important.

---

### Post by Paddy Landau on 2018-08-03
> **TheFu said:**
> Did a little research.  Is the touch screen infrared?
I have no idea. I've been searching for the computer specifications but found nothing helpful. The closest that I've found to a specification for the monitor is '23" 1920x1080 Full HD Mutli-Touch Display'. The computer is a Packard Bell oneTwo L5861, if that's of any help.

---

### Post by TheFu on 2018-08-03
> **coffeefiend said:**
> Well now, that is certainly an interesting event. It is a good example of why having backups is important.

Not just backups, but automatic, versioned, off-line, backups.

Imagine the storage was CIFS mounted and 1 system got a crypto-locker malware?  rdiff-backup works over ssh and can be "pulled" or "pushed."  Pulling is more secure, since the infected systems can't access the backup storage. I'm assuming they can't mount it - backup storage should use a client/server protocol, not just file sharing over a network. rdiff-backup does this.

Combined with LVM snapshots, rdiff-backup does almost everything we need in a backup tool.  The only thing it doesn't handled internally is encrypting the backups.  If you need that, use LUKS dm-crypt partitions for the storage. ssh provides the network-level encryption for rdiff-backup, so it is only when the backups are at rest this could be a problem.

There are 1001+ uses for versioned backups, at least that many.

---

### Post by Paddy Landau on 2018-08-03
> **TheFu said:**
> Imagine the storage was CIFS mounted and 1 system got a crypto-locker malware?
Oh yes, bad!

> **TheFu said:**
> Combined with LVM snapshots, rdiff-backup does almost everything we need in a backup tool.  The only thing it doesn't handled internally is encrypting the backups.
I have online backups using [SpiderOak]("https://spideroak.com/"), which generally works well. I use rdiff-backup for offline backups (plugged directly into the machine, so no SSH), with everything saved on a LUKS partition. So, all encrypted. I also rotate three external hard drives. I'm probably being paranoid, but I have a lifetime of photos, children's videos, and more.

---

### Post by SantaFe on 2018-08-04
Well, if you had a visit from Ant-Man, was The Wasp far behind?  :D

Shameless Movie Plug! ;)

---

### Post by Perfect Storm on 2018-08-04
And here I thought only cats on keyboards would do such a thing. :popcorn:

---

### Post by TheFu on 2018-08-09
> **Paddy Landau said:**
> 
I have online backups using [SpiderOak]("https://spideroak.com/"), which generally works well. 


Did you see that spideroak's warrant/NSL canary was tripped this week?
[https://boingboing.net/2018/08/06/spideroak-warrant-canary-to-be.html](https://boingboing.net/2018/08/06/spideroak-warrant-canary-to-be.html)
Seems it worked as designed.

---

### Post by #&amp;thj^% on 2018-08-09
> **TheFu said:**
> Did you see that spideroak's warrant/NSL canary was tripped this week?
[https://boingboing.net/2018/08/06/spideroak-warrant-canary-to-be.html](https://boingboing.net/2018/08/06/spideroak-warrant-canary-to-be.html)
Seems it worked as designed.

A Quote:>> "Don't be mad at the company! The canary worked exactly as it was supposed to. "

---

### Post by Paddy Landau on 2018-08-10
> **TheFu said:**
> Did you see that spideroak's warrant/NSL canary was tripped this week?
No, I didn't! A few years ago, I was aware that SpiderOak intended to create a canary report, but I didn't realise that they'd implemented it. Given their zero-knowledge methodology, though, I doubt that the request came to anything.

---

### Post by TheFu on 2018-08-10
I have a simple rule.  Live by the cloud, die by the cloud.  
 
I don't trust every implementation, especially those done in javascript. Everyone has a different level of risk acceptance, I suppose.

---

### Post by Paddy Landau on 2018-08-10
> **TheFu said:**
> Everyone has a different level of risk acceptance, I suppose.
Absolutely! It depends on what you use your computer for. Perfect security (to the extent that such a thing is possible) comes at a cost, so it's always a trade-off.

---

### Post by HermanAB on 2018-08-11
Hmm, I learned my lesson with touch screens, when a pilot accidentally shut down a fuel pump, just by pointing at it.  We avoided a crash thanks to the second fuel pump, but that was the end of our touch screen experiment in avionics.

---

### Post by Paddy Landau on 2018-08-11
> **HermanAB said:**
> Hmm, I learned my lesson with touch screens, when a pilot accidentally shut down a fuel pump, just by pointing at it.  We avoided a crash thanks to the second fuel pump, but that was the end of our touch screen experiment in avionics.
That must have been scary!

On a barely-related note, did you read about this [stolen plane]("https://www.bbc.co.uk/news/world-us-canada-45153535")? The pilot must have been mentally ill or on drugs.

---

### Post by xmoonlight444 on 2018-08-16
hahahha seems like that pesky ant wanted to play some games with you that night!! :)

---

