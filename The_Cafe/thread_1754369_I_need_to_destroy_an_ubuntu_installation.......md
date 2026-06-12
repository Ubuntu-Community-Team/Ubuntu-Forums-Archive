---
title: "I need to destroy an ubuntu installation......"
date: 2011-05-10
forum: The Cafe
---

### Post by Thewhistlingwind on 2011-05-10
In a way that the home directory is obliterated. Any good ideas? I want to simulate a real crash, not just use RM.

---

### Post by madjr on 2011-05-10
wut?! lol

---

### Post by Thewhistlingwind on 2011-05-10
> **madjr said:**
> wut?! lol

Testing disk recovery software.

---

### Post by Hedgehog1 on 2011-05-10
May I suggest copy a large amount of data in the /home directory, and about 1/2 through the copy unplug the PC?

---

### Post by slim_pickins on 2011-05-10
> **Thewhistlingwind said:**
> In a way that the home directory is obliterated. Any good ideas? I want to simulate a real crash, not just use RM.

try doing anything as *root.*  :)

---

### Post by Rasa1111 on 2011-05-10
[http://www.ubuntu-unleashed.com/2008/03/how-to-intentionally-screw-up-and-wipe.html](http://www.ubuntu-unleashed.com/2008/03/how-to-intentionally-screw-up-and-wipe.html)
[http://www.secure-gear.com/linux/How-to-destroy-all-your-data-on-your-Ubuntu-Linux-system-470-1.htm](http://www.secure-gear.com/linux/How-to-destroy-all-your-data-on-your-Ubuntu-Linux-system-470-1.htm)

careful now.

---

### Post by jocko on 2011-05-10
Unplug the power supply while resizing a partition?

---

### Post by VanR on 2011-05-10
Try to install Gnome 3!!!! That should do it.  :popcorn:

---

### Post by Thewhistlingwind on 2011-05-10
> **VanR said:**
> Try to install Gnome 3!!!! That should do it.  :popcorn:

We have a winner! ;)

But really, great ideas people, keep em coming.

---

### Post by Rasa1111 on 2011-05-10
> **VanR said:**
> Try to install Gnome 3!!!! That should do it.  :popcorn:
hahaha! 
that made me laugh. :lol: :KS

---

### Post by Hedgehog1 on 2011-05-10
> **jocko said:**
> Unplug the power supply while resizing a partition?

Fiendishly clever!  ***Bravo!***

---

### Post by nothingspecial on 2011-05-10
[COLOR="Red"]**[SIZE="3"]THE COMMAND IN THIS POST WILL COMPLETELY DESTROY YOUR SYSTEM[/SIZE]**[/COLOR]


Put home on another hard drive, unmount it, then type this

```
dd if=/dev/urandom of=/dev/sd?
```

Change the question mark for the drive in question a,b,c....... etc

That should test your software :P

---

### Post by Paqman on 2011-05-10
Depends what kind of failure you're trying to simulate. Do you want to disrupt the filesystem or just the data?

---

### Post by mips on 2011-05-10
> **nothingspecial said:**
> [COLOR="Red"]**[SIZE="3"]THE COMMAND IN THIS POST WILL COMPLETELY DESTROY YOUR SYSTEM[/SIZE]**[/COLOR]


Put home on another hard drive, unmount it, then type this

```
dd if=/dev/urandom of=/dev/sd?
```

Change the question mark for the drive in question a,b,c....... etc

**That should test your software** :P

No software is gonna recover that.

---

### Post by deconstrained on 2011-05-10
```
man shred
```

---

### Post by Grenage on 2011-05-10
> **mips said:**
> No software is gonna recover that.

Lol, that's a fact.

---

### Post by triceratops on 2011-05-10
Burn up a CD with the [DBAN (Darik's Burn and Nuke)]("http://www.dban.org/") ISO.  Set BIOS for cd-rom bootup, pop in the cd, reboot, watch hdd go bye-bye.  Uses Department of Defense overwrite algorithm.  Will take a long time on 100+ GB drives, so best to shut the monitor off and come back the next day.

I keep a DBAN disk in my toolkit all the time for zeroing out old cheap computers for linux overwrites.

---

### Post by stealth. on 2011-05-10
> **triceratops said:**
> Burn up a CD with the [DBAN (Darik's Burn and Nuke)]("http://www.dban.org/") ISO.  Set BIOS for cd-rom bootup, pop in the cd, reboot, watch hdd go bye-bye.  Uses Department of Defense overwrite algorithm.  Will take a long time on 100+ GB drives, so best to shut the monitor off and come back the next day.

I keep a DBAN disk in my toolkit all the time for zeroing out old cheap computers for linux overwrites.

+1 to DBAN, it took me approx 72 hrs for my 500GB laptop drive with the Gutmann method. 

Also, when I was doing my Arch install I accidentally "dd'ed" my HDD, completely screwed the partition table.

---

### Post by Thewhistlingwind on 2011-05-10
> **Paqman said:**
> Depends what kind of failure you're trying to simulate. Do you want to disrupt the filesystem or just the data?

Preferably both.:P

To the people who suggested Dban (DD, lol. Disk Destroyer......) If your of the belief that ANY software can recover data from a disk after a use of dban (In Esp. if you use something more damaging then DOD short.) then why are you bothering too use it, when the time taken to wipe is SO much longer?

---

### Post by Grenage on 2011-05-10
> **Thewhistlingwind said:**
> Preferably both.:P

To the people who suggested Dban (DD, lol. Disk Destroyer......) If your of the belief that ANY software can recover data from a disk after a use of dban (In Esp. if you use something more damaging then DOD short.) then why are you bothering too use it, when the time taken to wipe is SO much longer?

We don't, and I believe that nothingspecial was probably being playful.  no recovery software is going to got anything back after a random fill.

---

### Post by Thewhistlingwind on 2011-05-10
> **Grenage said:**
> We don't, and I believe that nothingspecial was probably being playful.  no recovery software is going to got anything back after a random fill.

No, I KNOW that on general principal, I wanted to see their responses. My comp science teachers response when I mentioned it was "A peace of mind thing, it doesn't actually work, data deletion is impossible." so I figured the responses would be.....interesting.

EDIT: Though calling him a comp sci teacher may be giving him qualifications he doesn't have.

---

### Post by Paqman on 2011-05-10
> **stealth. said:**
> +1 to DBAN, it took me approx 72 hrs for my 500GB laptop drive with the Gutmann method. 


Sorry to say you probably wasted a lot of time there. There's no need to ever do a full Gutmann wipe, all thirty-something writes. One pass with random data will render your data just as unrecoverable as the Gutmann method.

---

### Post by nothingspecial on 2011-05-10
> **Grenage said:**
> We don't, and I believe that nothingspecial was probably being playful.  

That's what the tongue out smiley is supposed to signify :D

If you are interested in recovering data then format. If you are interested in recovering from bad situations then here is one to try if you have a spare instalation. I'm not going to post the actual command because someone might copy and paste it. So I'll outline the modifications you need to make it work afterwards.

Try getting out of this one.

First you need to move into /usr/bin

```
 x in `ls`; do  -f $x $y; y=?; done
```

Put for at the beginning of the command.

Change the question mark for $x and insert mv inbetween do and -f.

Also run it as root.

That will mix up every file in /usr/bin in that it will swap the names of most of your applications. You will still have bash because bash is in bin, some things like ls will work but most things will not.

Can your software recover from that?

By the way, I have no idea how to recover from it.

---

### Post by Thewhistlingwind on 2011-05-10
> **nothingspecial said:**
> 

If you are interested in recovering from bad situations then here is one to try if you have a spare instalation.......


Data. However, I'd be worried about my sanity if this WASN'T being done on a spare install. (Or moreover, it WAS being done on a production machine.)

Also, that's devious and evil, I love it, gotta try getting out of that later.

> **Paqman said:**
> Sorry to say you probably wasted a lot of time  there. There's no need to ever do a full Gutmann wipe, all  thirty-something writes. One pass with random data will render your data  just as unrecoverable as the Gutmann method.

The point of the gutmann wipe is to make your data irretrievable by having your disk fail halfway through it.:D

---

### Post by nothingspecial on 2011-05-10
You'll get funny error messages like this

```
Uhhuh. NMI received for unknown reason a1 on CPU 0.
You have some hardware problem
Dazed and Confused...................but trying to continue
```

---

### Post by Paqman on 2011-05-10
> **Thewhistlingwind said:**
> 
The point of the gutmann wipe is to make your data irretrievable by having your disk fail halfway through it.:D

Lol. Either that or taking so long that humanity is extinct by the time it finishes, so there's no one left to steal your datas.

---

### Post by Retlol on 2011-05-10
Format the drive.

---

### Post by Rasa1111 on 2011-05-10
lol, i love how such random looking characters can do such disastrous things! :lol: :P

---

