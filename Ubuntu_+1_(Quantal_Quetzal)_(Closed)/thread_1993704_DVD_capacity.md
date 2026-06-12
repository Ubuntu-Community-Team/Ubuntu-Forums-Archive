---
title: "DVD capacity"
date: 2012-06-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by unibroker on 2012-06-02
I made a Live DVD a couple of weeks ago to follow the development progress of Quantal.  Last night I booted into it and tried to apply updates.  There were approximately 270 Mb worth.  After downloading the process failed in trying to write it to the DVD; out of space.  According to the DVD+R packaging the capacity is supposed to be 4.7 Gb.  What am I missing?

---

### Post by rtalcott on 2012-06-02
I thought DVD +R is write once...need RW to be able to add?
rt

---

### Post by unibroker on 2012-06-02
> **rtalcott said:**
> I thought DVD +R is write once...need RW to be able to add?
rt
You are correct.  I just assumed it meant that all of the space was subject to writing once.

---

### Post by rtalcott on 2012-06-02
I do not believe this is so....write once only applying to the written media BUT I could be wrong!!!!
rt

---

### Post by ronacc on 2012-06-02
it depends on if you selected to burn a multisession dvd . the area that has actually been writen to cannot be reused but area not written to can if you select "multisession" , I donn't know if cd/dvd creator or brassero has this option but K3B does .

---

### Post by pressureman on 2012-06-02
DVD+R/-R can store multiple sessions, but only if the disc has not been closed. Most DVD writing software closes the disc after writing a session, ensuring no further writes are possible.

DVD-RW can be written/erased multiple times using disc writing software, but can only be treated like a USB stick or floppy disk if formatted as UDF, and written in packet mode.

---

### Post by unibroker on 2012-06-02
> **ronacc said:**
> it depends on if you selected to burn a multisession dvd . the area that has actually been writen to cannot be reused but area not written to can if you select "multisession" , I donn't know if cd/dvd creator or brassero has this option but K3B does .
Thanks for the response.  I just installed K3B through the Software Center.  I wonder if it will be available to me in Quantal (I downloaded it from Precise).  The Software Center crashes in the version of Quantal that I'm currently trying to update.

Whatever is the default DVD burner in Quantal is the one I used.  I didn't see the option of multisession.  I'll try K3B from Quantal later today and report back.  Hopefully today I'll also mark this thread Solved!

---

### Post by rtalcott on 2012-06-02
Yeah...I never do that BUT that's the way it works...you need to select that option...
rt

---

### Post by unibroker on 2012-06-02
The Update Manager gave me a "Package Operation Failed" again but at least it doesn't appear to be a full DVD problem.  I had K3B opened and the graph at the bottom said 3.7 Gb available.

Initially I had downloaded all the updates (about 300 of them) but got the same full disc message.  I thought maybe it was because K3B wasn't opened.  I opened it and downloaded 5 of the 300 as a test.  That's when I got "Package Operation Failed".  Might be because I didn't download all of the updates and the 5 I did are dependent on the ones I didn't?

I tried to access the K3B manual through the Help menu but was unable.  I don't know if Update Manager is utilizing K3B for burning or what.  It's no biggie and if I want to hassle downloading everything, including K3B, again I might try again tomorrow.  At least I have K3B in Precise!

Thanks for the input.

---

### Post by pressureman on 2012-06-02
Umm... what exactly are you trying to do? I don't think you can simply incrementally apply package updates to a live CD image that has been burned to a disc. When you boot a live CD, you're essentially running from a read-only filesystem, which cannot be updated.

What you probably ought to do is use zsync to periodically download an updated version of the daily .iso (saved to hard disk), and use a DVD-RW to completely erase and re-burn the updated .iso.

Alternatively, if your computer supports booting from a USB stick, use the USB startup disk creator app to write the .iso to a USB stick, as this boots a lot faster than a DVD will.

---

### Post by unibroker on 2012-06-03
> **pressureman said:**
> Umm... what exactly are you trying to do? I don't think you can simply incrementally apply package updates to a live CD image that has been burned to a disc. When you boot a live CD, you're essentially running from a read-only filesystem, which cannot be updated.

What you probably ought to do is use zsync to periodically download an updated version of the daily .iso (saved to hard disk), and use a DVD-RW to completely erase and re-burn the updated .iso.

Alternatively, if your computer supports booting from a USB stick, use the USB startup disk creator app to write the .iso to a USB stick, as this boots a lot faster than a DVD will.
What I'm reading this morning is that an iso file is compressed so I would probably have to extract it, append the new update and then re-burn the new file which would not be allowed with my DVD+R.

I was just trying to make use of media that I had previously purchased (bought 6+ years ago when I bought my computer). I'll just wait until we get further in the Quantal development and just replace Precise.  I did the same with Precise and enjoyed seeing things improve as I downloaded updates.

Thanks to all for the responses.

---

### Post by jerrylamos on 2012-06-03
USB sticks are getting very reasonable, example 16 GB for $6 from Amazon or 8 gb for less than $3 hardly worth my time with DVD's....

Jerry

---

### Post by unibroker on 2012-06-03
> **jerrylamos said:**
> USB sticks are getting very reasonable, example 16 GB for $6 from Amazon or 8 gb for less than $3 hardly worth my time with DVD's....

Jerry
It's not a cost issue.  I have disposed of technology in the past that had more computing power than what it took to land on the moon.  Now that I've discovered open source platforms and the forums (this one being among the best) they spawn I try to look at what I have already accumulated to solve present needs.

---

### Post by pressureman on 2012-06-03
> **unibroker said:**
> What I'm reading this morning is that an iso file is compressed so I would probably have to extract it, append the new update and then re-burn the new file which would not be allowed with my DVD+R

ISO files are not compressed - they're more like an (uncompressed) tar image of a directory tree. ISO 9660 (aka CDFS) is by design a read-only filesystem. To add even a single new file, you either need to re-master the entire ISO image (and burn to a new disc, or erase and rewrite a RW media), or ensure that you enabled support for multisession when you burned the first session to the disc. In the latter case, burning additional sessions lays down an entirely new ToC (Table of Contents), which is like a FAT for ISO 9660. There is no way to alter existing content on a disc, however existing files can be "virtually" deleted or overwritten, by the means of the updated ToC pointing to new content on the disc.

In short, I think you are making things much harder for yourself than they need to be.

---

### Post by jerrylamos on 2012-06-03
> **pressureman said:**
> ISO files are not compressed - they're more like an (uncompressed) tar image of a directory tree. ISO 9660 (aka CDFS) is by design a read-only filesystem. To add even a single new file,... There's another way.  With "persistent" in the linux line and a casper-rw partition, I add files, make changes, updates, ...  Now the persistent casper-rw partition is on my USB in this case, however previously I've even had it on a hard drive.

With the .iso loaded on one partition and casper-rw on another, I make changes, copy files, ... reboot, everything's there, even take the usb flash to another pc (like right now) and it boots with all the added changes I did.  

Now admittedly not as fast as running on the hard disk, but sure is convenient for seeing if today's daily build runs on different pc's.  I'm using 3 test pc's at the moment.  I do miss the frequent install errors which I'll look for when Alpha 1 comes out this week.

Another way is a USB hard disk (left over 2.5" laptop drive in a $10 case) install on one pc and take to the other two.  A little longer than just doing the "persistent" USB drive.

Have fun,

Jerry

---

### Post by pressureman on 2012-06-03
> **jerrylamos said:**
> There's another way.  With "persistent" in the linux line and a casper-rw partition, I add files, make changes, updates, ...  Now the persistent casper-rw partition is on my USB in this case, however previously I've even had it on a hard drive.

With the .iso loaded on one partition and casper-rw on another, I make changes, copy files, ... reboot, everything's there, even take the usb flash to another pc (like right now) and it boots with all the added changes I did.

That's UnionFS at work there, which allows you to merge two or more mixed read-only/read-write filesystems into a single virtual RW filesystem. UnionFS automatically substitutes updated copies of files from an underlying RO-filesystem with their counterpart from a RW filesystem member of the UnionFS mount.

---

