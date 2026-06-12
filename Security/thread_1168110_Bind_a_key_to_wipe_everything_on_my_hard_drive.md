---
title: "Bind a key to wipe everything on my hard drive?"
date: 2009-05-23
forum: Security
---

### Post by Jekshadow on 2009-05-23
Ok, I've setup a fairly secure system with an encrypted home directory and my entire installation is within an encrypted partition. How would I setup a system where if I pressed 'F12' 3 times quickly (while its on, without a live cd), it would completely erase my hard drive and delete the partitions. Please give help and don't just tell me I'm paranoid.

This is why:

[http://en.wikipedia.org/wiki/Carnivore_(FBI](http://en.wikipedia.org/wiki/Carnivore_(FBI))
[http://en.wikipedia.org/wiki/Information_Awareness_Office](http://en.wikipedia.org/wiki/Information_Awareness_Office)
[http://en.wikipedia.org/wiki/Information_Processing_Technology_Office](http://en.wikipedia.org/wiki/Information_Processing_Technology_Office)
[http://en.wikipedia.org/wiki/ADVISE](http://en.wikipedia.org/wiki/ADVISE)

---

### Post by HermanAB on 2009-05-23
That won't work.

What you have to do is encrypt your disk drives using LUKS and when the spooks call, turn the machine off and forget your password.

---

### Post by rookcifer on 2009-05-23
And if you turn the machine off when the spooks call, try to stall them from reaching the machine for a couple of minutes. ;)  There was a paper published a year or two ago discussing how to retrieve encryption keys from RAM, but the RAM needs to be accessed within a few minutes and then immediately cooled in order to store what's left in it.  But it's doable and has been demonstrated.

---

### Post by Jekshadow on 2009-05-23
> **rookcifer said:**
> And if you turn the machine off when the spooks call, try to stall them from reaching the machine for a couple of minutes. ;)  There was a paper published a year or two ago discussing how to retrieve encryption keys from RAM, but the RAM needs to be accessed within a few minutes and then immediately cooled in order to store what's left in it.  But it's doable and has been demonstrated.

I read that, and they cooled it to like -300F and they could retrieve the encryption key for like 5 mins. 

And would it be possible to create a secondary partition with a secondary kernel that would have only a very basic interface (command line, preferable Bourne Again Shell)) and a partitioning tool. So basically when I pressed F12 3 times it would shut down instantly (like when you press and hold the power button for 10 secs) and then I could boot into the secondary kernel and automatically (or with a command) trigger a wipe of my main partition.

Or would it be easier just to have a magnet and a baseball bat nearby?

---

### Post by The Tronyx on 2009-05-23
> **Jekshadow said:**
> I read that, and they cooled it to like -300F and they could retrieve the encryption key for like 5 mins. 

And would it be possible to create a secondary partition with a secondary kernel that would have only a very basic interface (command line, preferable Bourne Again Shell)) and a partitioning tool. So basically when I pressed F12 3 times it would shut down instantly (like when you press and hold the power button for 10 secs) and then I could boot into the secondary kernel and automatically (or with a command) trigger a wipe of my main partition.

Or would it be easier just to have a magnet and a baseball bat nearby?

Sorry, what?

If you give these agencies that much credit, you surely don't think these encryption methods or wiping methods will actually protect your data do you?  I mean, let's say this whole paranoia trip you are onto is legit, what could you possibly have that the government wants so bad that you need to wipe so thoroughly?

Unfortunately I kind of have to lol @ this one.  I would like to help but there really is nothing you can do if this supreme entity is as billy bad *** as you have made them out to be.  It's not like the NSA is going to call you 2 hours before they kick down your door...

Even if you did have a baseball bat a and a magnet, if entities of the U.S. government are after you, if there is data on those plates they are going to get it.  I mean, the fact that you are asking this indicates, to me at least, that you don't really have anything too sensitive other than maybe some pirated movies and music.  If government agencies like that are after you, pirated media is the least of your worries.  If you are looking for the ultimate defense, you may want to pick up a tin foil hat.

---

### Post by koenn on 2009-05-24
> **Jekshadow said:**
> 

And would it be possible to create a secondary partition with a secondary kernel that would have only a very basic interface (command line, preferable Bourne Again Shell)) and a partitioning tool. So basically when I pressed F12 3 times it would shut down instantly (like when you press and hold the power button for 10 secs) and then I could boot into the secondary kernel and automatically (or with a command) trigger a wipe of my main partition.

yes - at least the procedure is feasible. I'm not very good at key bindings, so I'd be thinking a script and a launcher on one of the panels.

But encryption is probably a better idea. 

I wonder what you have on your computer that is so interesting that the "spooks" would come look for it yet you are willing to loose if you accidentally press the wrong keys ...

also, the links with "reasons' don't explain much : one is a network sniffer that is to be installed at an ISP so you'd never know about it, two others are data mining and analysis systems for enormous amounts of data, not designed towork with indivudual user's data, and finally a project to think u concepts and designs for supercomputers.

I think a tin foil head is actually an excellent idea.

---

### Post by tubbygweilo on 2009-05-24
Jekshadow, I fear that a Sneak and peek warrant followed some time later by a No knock warrant may well trump a tin foil hat but YMMV.

---

### Post by Eviltechie on 2009-05-26
Thermite?

---

### Post by sourchier on 2009-05-27
I could see a rootkit being able to do such things. However the programming and configuration of one is beyond the scope of these forums.

---

### Post by mavis311 on 2009-07-17
I know this is an old thread, but I had to get in on the fun.  I found this thread looking for a disk wiper for a non-paranoid reason: reselling an old HDD.

> **koenn said:**
> I think a tin foil head is actually an excellent idea.

OMGROFLBBQ Definitely a tin foil head?!!  I know it was just a typo, but that is funny stuff.

> **Eviltechie said:**
> Thermite?

Thermite would certainly be the best option

---

### Post by HermanAB on 2009-07-17
This is the best non-destructive way to erase a drive for reselling:

```
sudo hdparm --security-set-pass PWD /dev/sdb

sudo hdparm --security-erase PWD /dev/sdb
```

...but a stick of dynamite will be far more entertaining though will likely ruin the sale.

---

### Post by shaggy999 on 2009-07-18
Anybody who is extremely paranoid about the FBI/CIA/NSA raiding their home and wants to use encryption to protect their data always needs to remember this:

[http://xkcd.com/538/](http://xkcd.com/538/)

As for wiping, most people don't realize just how long it takes to wipe a drive. Suppose you have a modest 80 GB drive and you can write to the drive @ 80 MB/sec. If you're going to do an "unsafe" wipe of only one pass it would still take about 17 minutes to overwrite the entire drive. To perform a DoD-level wipe would take 2 hours.

The reality is that if you need some kind of kill switch like hitting F12 3 times you're better off developing a "bomb-like" device that sets off a stick of thermite that is kept taped to the hard drive.

---

### Post by The Tronyx on 2009-07-18
Old school kids used to use a degausser which utilizes a magnetic...bomb of some kind.

So, get an old OLD CRT monitor, take out the degausser, put it on top of your HD and in the event of a raid, hit the killswitch and send a giant magnetic burst at your drive.

That should take care of your concerns.

---

### Post by TheNosh on 2009-07-18
if you have an internet connection the gov't doesn't really need physical access to your machine

---

### Post by bodhi.zazen on 2009-07-19
**[*Aluminum Foil* Deflector *Beanie*]("http://zapatopi.net/afdb/")**

---

### Post by Whiffle on 2009-07-19
> **The Tronyx said:**
> Old school kids used to use a degausser which utilizes a magnetic...bomb of some kind.

So, get an old OLD CRT monitor, take out the degausser, put it on top of your HD and in the event of a raid, hit the killswitch and send a giant magnetic burst at your drive.

That should take care of your concerns.

And thats probably the best way to do it, honestly.

---

### Post by sailthesea on 2009-07-19
unless you can turn a HDD into a puddle of glass in 30 seconds

---

### Post by tgalati4 on 2009-07-19
Better wrap your keyboard cable in foil as well.  The spooks can read your keystrokes leaking into your house ground circuit.

Ask the gov't for a 2-hour lead time before busting the doors so you can wipe the drive.

Run your computer from a flash drive.  When the underwear patrol comes, take the flash drive and smash it with a hammer.  Swallow the pieces.  Keep a bottle of YooHoo handy to wash it down.

Eat cheeseburgers for the next couple of days to keep things moving.

Tinfoil hat is always a good idea.

---

### Post by bodhi.zazen on 2009-07-19
> **Jekshadow said:**
> Ok, I've setup a fairly secure system with an encrypted home directory and my entire installation is within an encrypted partition. How would I setup a system where if I pressed 'F12' 3 times quickly (while its on, without a live cd), it would completely erase my hard drive and delete the partitions. Please give help and don't just tell me I'm paranoid.

This is why:

[http://en.wikipedia.org/wiki/Carnivore_(FBI]("http://en.wikipedia.org/wiki/Carnivore_%28FBI"))
[http://en.wikipedia.org/wiki/Information_Awareness_Office](http://en.wikipedia.org/wiki/Information_Awareness_Office)
[http://en.wikipedia.org/wiki/Information_Processing_Technology_Office](http://en.wikipedia.org/wiki/Information_Processing_Technology_Office)
[http://en.wikipedia.org/wiki/ADVISE](http://en.wikipedia.org/wiki/ADVISE)

Umm ...

The first link is broken.

You realize the other three have nothing to do with your had drive of course.

To be honest, I think the question has been asked and answered so I am going to close this thread now.

---

