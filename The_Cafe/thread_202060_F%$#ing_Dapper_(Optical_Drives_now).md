---
title: "F%$#ing Dapper (Optical Drives now?)"
date: 2006-06-22
forum: The Cafe
---

### Post by therunnyman on 2006-06-22
Venting...thanks for indulging me, if you do decide to continue...

So, when I first installed Dapper, I had a number of problems, none of which have been satisfactorily corrected, but have been hacked into submission and are, for the moment, working.  I'll not reiterate my complaint about Dapper's *inablity to enumerate hard disks correctly*, I'm sure you've had enough of that, and the shame that should be draped over every single developer like a pall for a  problem as lethally serious as that doesn't appear to have led to any concern or fix.  Indeed, I'm informed we'll have to wait for Edgy, heh, for our drives to be enumerated properly.

Then I find I have to run gnomebaker as root in order to burn a disc.  And it is spelled "disc," developers; direct your beady little eyes to the tray of any optical device, and you'll find the technology is called "Compact Disc," not "Disk."  Furthernore, you don't "fixate" a session, you "close" a session - that's straight from the Orange Book Standard, guys.  Shame!

Perusing fstab, I find I have 36 optical devices somewhere; I thought I had only two, but lookee! there's cdrom0, cdrom1, cdrom2, cdrom3...all the way on up to cdrom36.  Now you'd think, as a user, I'd be able to burn a disc in at least *one* of these 36 optical drives I've evidently got, but I can't.  Instead I get a hard, grinding, summary crash.  Fortunately, you can run gnomebaker as root with impunity; don't try that with K3B, or you won't be able to log in again until you reconfiogure your ICEAuthority file.

In any event, I'll hack something in a second here to fix the optical drive problem.  A great leap was made moments ago when I erased all but two optical drives in fstab, rebooted, ran gnomebaker as root, and successfully erased, then burned a home-backup CD-RW.

By now, it should come as no surprise to me that Dapper can't handle even the most rudimentary hardware.  It's setting me off now, though: LTS, hah.  That's a good one guys.

Just to keep the user base mollified, I wonder, could the developers at the very least furnish reliable basic hardware support?  I'm hearing - I mean, among the other issues, including hard disk misenumeration - that not even mice are working.  God forbid you have a pen drive, or a USB audio device; then you're really scroohed.

Dapper shouldn't have been released.  Please, for the love of the community, don't pull that kind of crap in the future.  I'm sure we're all willing to wait however long it takes, 6 months, a year, whatever, for a decent upgrade.

Ahhh, I feel much better.  Now I shall smoke my pipe.  I found a delightful aromatic tobacco called "Ivanhoe," close in smoke to your classic Victorian Standard, but a bit more robust.  I'll reccomend that and Breezy to the pipe smokers in the community.

runny

---

### Post by joe_lace on 2006-06-22
I'm brand new, are you saying it would be better for me to just install breazy instead of continuing on with dapper?

---

### Post by therunnyman on 2006-06-22
[QUOTE=joe_lace]I'm brand new, are you saying it would be better for me to just install breazy instead of continuing on with dapper?[/QUOTE]

Unless you want XGL and Compiz - which get a whoopdee-fookin'-doo from me - I'd strongly suggest you install Breezy.  Of course, you can roll the dice with Dapper, give it a whirl, but a lot of people are having really dumb difficulties with it.

---

### Post by joe_lace on 2006-06-22
Since this is my first go with linux I'll might try reverting to breezy.  BTW, I spent a lot of time getting samba configured.  Can I copy my configuration files for samba and caps over to breezy?

---

### Post by therunnyman on 2006-06-22
Now that's an interesting question.  I don't know the answer, but I'm guessing you can, at the very least, configure samba in Breezy pretty much the same way you did it in Dapper, a compare and contrast exercise.

If someone comes back with a definite "yes" to this question, I'm gonna be furious.

runny

---

### Post by teet on 2006-06-22
[QUOTE=joe_lace]I'm brand new, are you saying it would be better for me to just install breazy instead of continuing on with dapper?[/QUOTE]

I would not suggest moving BACK to breezy unless you're having a problem of some sort.

Dapper runs almost perfectly for me.  Gnome is much faster than it was in Breezy and my laptop now has full functioning ACPI support (suspend/hibernate work great).  I have no complaints with Dapper.

-teet

---

### Post by JackSlammer on 2006-06-22
Let me quess, you are installing from some old flight cd and then dist-upgrading, right? That optical drive bug was fixed long time ago.

This forum is full of nonsence about dist-upgrade. Far too many people believes it's some mystical super tool. Upgrading from old flight cd's to dapper final is definetly not supported. Things can go badly wrong.

Sorry if you're indeed installing from dapper final cd or dvd...

---

### Post by joe_lace on 2006-06-22
Well I haven't played with it much yet. I just installed it the night before last and haven't had a chance to test all its functions.  The only reason I have already configured samba is because my wife was hounding me to get the shared printer back online so that was priority 1.

---

### Post by therunnyman on 2006-06-22
[QUOTE=JackSlammer]Let me quess, you are installing from some old flight cd and then dist-upgrading, right? That optical drive bug was fixed long time ago.

This forum is full of nonsence about dist-upgrade. Far too many people believes it's some mystical super tool. Upgrading from old flight cd's to dapper final is definetly no supported. Things can go badly wrong.

Sorry if you're indeed installing from dapper final cd or dvd...[/QUOTE]

Clean - and when I say clean, I mean clean - installs from both the Live and "Alternate" (hah!) CDs result in this BS.

---

### Post by therunnyman on 2006-06-22
[QUOTE=joe_lace]Well I haven't played with it much yet. I just installed it the night before last and haven't had a chance to test all its functions.  The only reason I have already configured samba is because my wife was hounding me to get the shared printer back online so that was priority 1.[/QUOTE]

In Breezy, I plugged about 17 different printers - USB, parallel, hot, even - into my machine, and all worked just fine.

---

### Post by JackSlammer on 2006-06-22
Clean? So you mean you have dapper final install cd? Because this was known bug and it was fixed before dapper beta release. I honestly don't believe you're using final cd.

---

### Post by therunnyman on 2006-06-22
[QUOTE=JackSlammer]Clean? So you mean you have dapper final install cd? Because this was known bug and it was fixed before dapper beta release. I honestly don't believe you're you are using final cd.[/QUOTE]

It's true, I say, with tears in my eyes.  I'll email you the .isos if you want 'em.  Heckfire, I'll even FedEx overnight my CDs.

The thing of it is, they've either claimed to have fixed these bugs over at launchpad/malone, or they're saying, we know, it's a big problem, but, uh, sorry, you'll have to wait until Edgy.

Check out #6367, for example.

---

### Post by prizrak on 2006-06-23
That's weird, other than the Gnomebaker I have no issues that you are talking about. Gnomebaker IS the dumbest issue ever it didn't have to be root in Breezy why change that? Though I'm using Nautilus for burning and it works great, I actually haven't found Gnomebaker to have any functionality over Nautilus as soon as I learned that I STILL need a separate program for Audio CD's I dropped Baker. 

P.S. You misspelled "disc" in your sig. (Just ironic that you pointed it out ;) )

---

### Post by BoyOfDestiny on 2006-06-23
[QUOTE=prizrak]
P.S. You misspelled "disc" in your sig. (Just ironic that you pointed it out ;) )[/QUOTE]

Actually disk is correct there...

c : a round flat plate coated with a magnetic substance on which data for a computer is stored

[http://www.m-w.com/dictionary/disk](http://www.m-w.com/dictionary/disk)

also for floppy disks it's correct, or floppy diskette...

For things like CD's, DVD's, and frisbees, it's disc.

To stay somewhat on topic, if Dapper works for you, I'd say stick with it.

---

### Post by prizrak on 2006-06-23
[QUOTE=BoyOfDestiny]Actually disk is correct there...

c : a round flat plate coated with a magnetic substance on which data for a computer is stored

[http://www.m-w.com/dictionary/disk](http://www.m-w.com/dictionary/disk)

also for floppy disks it's correct, or floppy diskette...

For things like CD's, DVD's, and frisbees, it's disc.

To stay somewhat on topic, if Dapper works for you, I'd say stick with it.[/QUOTE]
If that is not confusing I don't know what is. Dapper does work for me cept tht for some reason alot of admin stuff takes forever to load but as the system is running well I don't need to admin stuff normally. I guess everyone's mileage will vary but it is weird that something that works in Breezy wouldn't in Dapper.

---

### Post by therunnyman on 2006-06-23
A fine point indeed - disc v disk, I mean - and one I wouldn't ordinarily bring up; every bit of vitriol I had stored up for the developers came out in the initial post, and that was a corner of the vat.

I fought the NYT over "Disc" one day.  Their style guide insisted the technology was spelled "Disk;" I asked them to look at their machines, and spell what the faceplate on their optical drives read back to me.  They conceded.  They changed the style guide.  I won.

This was a great triumph for me back in 1999, when I was counted a star in the optical storage authority constellation.  Anymore, eh, whatever.  If James Joyce had paid attention to spelling, we'd be a century behind in the arts.

Magnetic storage: disk.  Optical, PD, MO, etc.: disc.

---

### Post by prizrak on 2006-06-23
On the topic of Dapper, I have noticed that most people who have issues with it have them on desktops but not laptops (of course I could be wrong I didn't make a scientific analysis of it) even my desktop that had no problems with Breezy and Automatix crashes on flash install for some reason in Dapper using Automatix. The laptop however has full ACPI and wireless support. I think that developers spent more time polishing laptop components for Dapper since those are the ones people were concentrating their complaints on. As a result some desktop stuff got overlooked. I'm starting to agree with some people who say that 6 month development cycle is too fast maybe they should change it to 8 or something.

---

