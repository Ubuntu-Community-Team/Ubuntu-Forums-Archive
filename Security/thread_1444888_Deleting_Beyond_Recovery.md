---
title: "Deleting Beyond Recovery?"
date: 2010-04-01
forum: Security
---

### Post by MasterNetra on 2010-04-01
I was wondering if there are any secure deletion tools for linux? Ones that make multiple deletion passes to prevent even low level data recovery? And perhaps a better formating utility to clear out those partitions that contain personal information. Because no way gparted fully formats partitions beyond recovery.
I ask because I don't want to end up one day selling my computer and have my personal info on there.

---

### Post by mkvnmtr on 2010-04-01
The secure-delete package has four programs that will do what you want and more. If you do not understand man pages you might wish to google a bit to learn to use it.

---

### Post by MasterNetra on 2010-04-01
> **mkvnmtr said:**
> The secure-delete package has four programs that will do what you want and more. If you do not understand man pages you might wish to google a bit to learn to use it.

And my love for linux has grown.

Also just come across DBAN. One way to make sure your computer is safe for resale.

---

### Post by HermanAB on 2010-04-02
The best way is to encrypt your partitions with LUKS and when you need to delete it, just forget the key.

---

### Post by MCVenom on 2010-04-02
I'll give you a tip I picked up when trying to wipe Grub2 off my MBR :)

```
dd if=/dev/zero of=/dev/(hd*/sd*) bs=1MB
```

That command **completely overwrites the selected drive with zeroes and should be run from a LiveCD, of course.** You can then set up new partition tables (which will free the space filled by all those zeroes) and give the drive away/sell it. ;)

---

### Post by cdenley on 2010-04-02
> **BlackOtaku said:**
> I'll give you a tip I picked up when trying to wipe Grub2 off my MBR :)

```
dd if=/dev/zero of=/dev/(hd*/sd*) bs=1MB
```

That command **completely overwrites the selected drive with zeroes and should be run from a LiveCD, of course.** You can then set up new partition tables (which will free the space filled by all those zeroes) and give the drive away/sell it. ;)

That is what I typically use since that makes it impossible to recover data without opening it up and inspecting the platters with some expensive equipment, but it is theoretically possible to determine what data used to be on the disk if you overwrite with all zeros, since all bits which were previously one would be more like .002 and all bits which were previously zero would be more like .001. This is why most tools will use multiple passes of random data. The 27 passes sometimes recommended is overkill for modern drives, though.

---

### Post by MCVenom on 2010-04-02
> **cdenley said:**
> That is what I typically use since that makes it impossible to recover data without opening it up and inspecting the platters with some expensive equipment, but it is theoretically possible to determine what data used to be on the disk if you overwrite with all zeros, since all bits which were previously one would be more like .002 and all bits which were previously zero would be more like .001. This is why most tools will use multiple passes of random data. The 27 passes sometimes recommended is overkill for modern drives, though.
Interesting... then I guess I'd recommend this instead maybe? :p

```
dd if=/dev/random of=/dev/(hd*/sd*) bs=1MB #Repeat as makes you feel comfortable ;)
```

P.S.: Above rules apply, overwrite with random data and should be run from a LiveCD :p

---

### Post by cdenley on 2010-04-02
> **BlackOtaku said:**
> Interesting... then I guess I'd recommend this instead maybe? :p

```
dd if=/dev/random of=/dev/(hd*/sd*) bs=1MB #Repeat as makes you feel comfortable ;)
```

/dev/urandom would be much faster. Or you could just do:
```

sudo shred /dev/(hd*/sd*)

```
This does 3 passes by default.
```

man shred

```

---

### Post by MasterNetra on 2010-04-02
Anything for handling CD-RW/DVD-RW ? & What about Darik's Boot and Nuke? Also I just read that the default method DoD Short is considered medium level secuirty because it makes only 3 passes, but would three rounds of it make up for it and turn it into a high level?

[http://www.linux.com/archive/feature/48092](http://www.linux.com/archive/feature/48092)

Mentions stream at 8 passes is considered a high level wipe but with 3 rounds of DoD Short, I would think it be a high level wipe sense it is essentially doing 9 passes. Am I right or no?

Thoughts or better yet advice?

---

### Post by tubbygweilo on 2010-04-02
You have a trade off between how long it takes for dban to wipe a disk (overnight?) vs what degree of wiping is required vs whoever may wish to reconstitute and read your wiped disk (NSA, CIA, GCHQ, FBI, local police, Tax authorities, local criminal, your partner...). Give it a try to see how long various options take and then decide the correct level of wiping for you.

---

### Post by MasterNetra on 2010-04-02
> **tubbygweilo said:**
> You have a trade off between how long it takes for dban to wipe a disk (overnight?) vs what degree of wiping is required vs whoever may wish to reconstitute and read your wiped disk (NSA, CIA, GCHQ, FBI, local police, Tax authorities, local criminal, your partner...). Give it a try to see how long various options take and then decide the correct level of wiping for you.

Frankly I don't trust the CIA, FBI, Police, etc any more then I would trust a stranger. At any rate Stream (8 passes) 1 round vs DoD Short (3 passes) 3 rounds (9 passes effective?) is unanswered.

---

### Post by NightwishFan on 2010-04-02
I think you can do a 30 pass or so, and overwrite with zeros using shred. It is a pretty great utility.

---

### Post by MasterNetra on 2010-04-02
> **NightwishFan said:**
> I think you can do a 30 pass or so, and overwrite with zeros using shred. It is a pretty great utility.

At this point I'm talking about the method from Boot & Nuke. But apparently zero-ing may not be enough the random letter & number thing suppose to help ensure that nothing is recoverable...nothing usable anyway. I decided to use secure-delete from the repo's when it comes to files and folders.

---

### Post by NightwishFan on 2010-04-02
Zeroing primarily hides the fact that things were shred I think.

---

### Post by MasterNetra on 2010-04-02
> **NightwishFan said:**
> Zeroing primarily hides the fact that things were shred I think.

Perhaps but if nothing is recoverable what does it matter if its shredding is noticeable?

---

### Post by mkvnmtr on 2010-04-02
Rember with thesecure-delet program you can wipe the memory and the swap partition. Also wipe files and all the free space on your disk. I do it all from time to time just for practice. You never know when the CIA will call.

---

### Post by cdenley on 2010-04-02
> **mkvnmtr said:**
> Rember with thesecure-delet program you can wipe the memory and the swap partition. Also wipe files and all the free space on your disk. I do it all from time to time just for practice. You never know when the CIA will call.

I think one pass of zeros would stop the CIA, personally. A few passes of random data would be fine, but I would be more worried about previously used bad sectors which no software can erase, unless it uses ATA commands to trigger the drive's internal secure erase function.

---

### Post by MasterNetra on 2010-04-02
> **mkvnmtr said:**
> Rember with thesecure-delet program you can wipe the memory and the swap partition. Also wipe files and all the free space on your disk. I do it all from time to time just for practice. You never know when the CIA will call.

I know really. I've been clearing my CD-RW's of anything that might seem less then legit. No point on keeping something that's questionable. Which reminds me, anything for CD/DVD's? I know CD-R you would have to phyiscally destroy it, but CD-RW's on the other hand. Would wipe or secure-delete be able to handle optical media? If not any recommendations for a app to do this?

---

### Post by cdenley on 2010-04-02
> **MasterNetra said:**
> I know really. I've been clearing my CD-RW's of anything that might seem less then legit. No point on keeping something that's questionable. Which reminds me, anything for CD/DVD's? I know CD-R you would have to phyiscally destroy it, but CD-RW's on the other hand. Would wipe or secure-delete be able to handle optical media? If not any recommendations for a app to do this?

I never use RW optical media, but I think
```

dvd+rw-format -force=full -blank=full /dev/scd0
wodim dev=/dev/scd0 blank=all -force

```

---

### Post by MasterNetra on 2010-04-02
> **cdenley said:**
> I never use RW optical media, but I think
```

dvd+rw-format -force=full -blank=full /dev/scd0
wodim dev=/dev/scd0 blank=all -force

```

I can only write to CD's atm, planning on getting a USB DVD+RW when I can off of newegg.

---

### Post by cdenley on 2010-04-02
> **MasterNetra said:**
> I can only write to CD's atm, planning on getting a USB DVD+RW when I can off of newegg.

The 2nd one is for CD-RW.

---

### Post by MasterNetra on 2010-04-02
> **cdenley said:**
> The 2nd one is for CD-RW.

oh, my bad

---

### Post by rookcifer on 2010-04-02
> **cdenley said:**
> That is what I typically use since that makes it impossible to recover data without opening it up and inspecting the platters with some expensive equipment, but it is theoretically possible to determine what data used to be on the disk if you overwrite with all zeros, since all bits which were previously one would be more like .002 and all bits which were previously zero would be more like .001. This is why most tools will use multiple passes of random data. The 27 passes sometimes recommended is overkill for modern drives, though.

This is disputed in a recent paper done on this very topic.  From the [abstract:]("http://www.springerlink.com/content/408263ql11460147/")

> One of the chief controversies is that if a head positioning system is not exact enough, new data written to a drive may not be written back to the precise location of the original data. We demonstrate that the controversy surrounding this topic is unfounded. 

They conclude that using MFM's (powerful microscopes) is of no use for recovering data that has been overwritten only one time. 

Also, the NIST has also said that one pass is enough.  From their guidelines on the subject:

> Writing patterns of data on top of the data stored on a magnetic medium. **NSA has researched that one overwrite is good enough to sanitize most drives.** See comments on clear/purge convergence

OP: all you need is one pass with shred or dd or whatever method you wish to use -- they all do the same thing, that is write binary (0 and 1) to the drive.

---

### Post by jflaker on 2010-04-02
> **MasterNetra said:**
> Anything for handling CD-RW/DVD-RW ? & What about Darik's Boot and Nuke? Also I just read that the default method DoD Short is considered medium level secuirty because it makes only 3 passes, but would three rounds of it make up for it and turn it into a high level?

[http://www.linux.com/archive/feature/48092](http://www.linux.com/archive/feature/48092)

Mentions stream at 8 passes is considered a high level wipe but with 3 rounds of DoD Short, I would think it be a high level wipe sense it is essentially doing 9 passes. Am I right or no?

Thoughts or better yet advice?

Freeze the DVD/CD and shatter it........then to make sure no one tries to reassemble the cd.........

Microwaving is also interesting....nice light show results in destroyed foil inside the CD....But use a microwave you don't intend to use for food....Then freeze, shatter, recycle

---

### Post by bukwirm on 2010-04-02
> **MasterNetra said:**
> I was wondering if there are any secure deletion tools for linux?

I suggest a sledgehammer ;)

---

### Post by MasterNetra on 2010-04-02
> **jflaker said:**
> Freeze the DVD/CD and shatter it........then to make sure no one tries to reassemble the cd.........

Microwaving is also interesting....nice light show results in destroyed foil inside the CD....But use a microwave you don't intend to use for food....Then freeze, shatter, recycle

I intend to re-use the CD o.O

---

### Post by MCVenom on 2010-04-02
> **MasterNetra said:**
> I intend to re-use the CD o.O
Well that's no fun :lolflag:

---

### Post by cdenley on 2010-04-03
> **rookcifer said:**
> Writing **patterns of data** on top of the data stored on a magnetic medium. NSA has researched that one overwrite is good enough to sanitize most drives. See comments on clear/purge convergence

Overwriting with patterns of data is very different from overwriting with zeros. A single pass of random data should be enough, but maybe make a few passes for good measure. A single pass of only zeros still leaves the theoretical possibility, though, that you can determine which bits used to be a one before the single pass of zeros were written.

---

### Post by HermanAB on 2010-04-03
"8 passes is considered a high level wipe but with 3 rounds of DoD Short"

On the mythical DoD erase:
The DoD has different data classification levels and the handling for media at those levels are also different.

In general, once media has been used for data of classification Secret or above, the media can never again be re-used for data of a lower classification.  

***So in simple terms, once a disk contained Secret data, it remains Secret forever, no matter how many times you erase it.***

Therefore the reason for the three times overwrite of magnetic media being deemed sufficient, is that the disk will **still** be handled as if it contains Secret data.  Nowadays, the DoD actually requires that all portable media and devices be encrypted with AES256 as well, so one could say that the DoD level of paranoia about magnetic media actually **increased**, not decreased.

---

### Post by rookcifer on 2010-04-03
> **cdenley said:**
> Overwriting with patterns of data is very different from overwriting with zeros. A single pass of random data should be enough, but maybe make a few passes for good measure. A single pass of only zeros still leaves the theoretical possibility, though, that you can determine which bits used to be a one before the single pass of zeros were written.

A drive sector contains nothing but a couple hundred bytes, which themselves are each composed of eight 0's and 1's.  There really is no difference between the 0 and 1 (other than magnetic state).  So, I don't see how overwriting with 1's and 0's is different from overwriting with 0's alone.

---

### Post by cdenley on 2010-04-03
> **rookcifer said:**
> A drive sector contains nothing but a couple hundred bytes, which themselves are each composed of eight 0's and 1's.  There really is no difference between the 0 and 1 (other than magnetic state).  So, I don't see how overwriting with 1's and 0's is different from overwriting with 0's alone.

Because the magnetic state is never absolute one or zero. If you overwrite a disk with all zeros, the bits which were previously one would still be higher than the bits which were previously zero. This may even be true with multiple passes. It can be assumed that half the bits which are closest to absolute zero were zero before the overwrite. After a few passes of random data, it becomes much more difficult, if not impossible, to determine what the value used to be because you don't know what bits it has been overwritten with. Now that I think about it, though, a single pass of random data would only be a little safer, because they would only have to take into account the current state of each individual bit before making an educated guess about what it used to be based on how close it is to absolute one or zero.

---

### Post by MCVenom on 2010-04-03
Hey guys -- I've mean no offense here, but what makes you think people are going to dissect and examine your hard drive bit by bit? Honestly, unless you've committed a felony or are selling it to the CIA, the average comp. user won't be able to recover your old data reasonably after one or two random data passes. And by the time that guy finishes with the drive (for whatever reason) it will either have failed or your data will have been overwritten several times over. Why the suspicion? :p

---

### Post by NightwishFan on 2010-04-03
I agree. Even if you have pirated something, or similar do you think they will care?

---

### Post by rookcifer on 2010-04-03
> **cdenley said:**
> Because the magnetic state is never absolute one or zero. If you overwrite a disk with all zeros, the bits which were previously one would still be higher than the bits which were previously zero. This may even be true with multiple passes. It can be assumed that half the bits which are closest to absolute zero were zero before the overwrite. After a few passes of random data, it becomes much more difficult, if not impossible, to determine what the value used to be because you don't know what bits it has been overwritten with. Now that I think about it, though, a single pass of random data would only be a little safer, because they would only have to take into account the current state of each individual bit before making an educated guess about what it used to be based on how close it is to absolute one or zero.

The guys who wrote the "Great Wiping Controversy" paper dispute this "misaligned drive head" theory in their study of modern ERPML hard drives.  This misaligned head theory started with Gutmann who was writing in the mid '90's before ERPML drives were around.  

There used to be a blog post where one of the authors went into detail about the findings, but it appears to have been deleted.

---

### Post by cdenley on 2010-04-03
> **rookcifer said:**
> The guys who wrote the "Great Wiping Controversy" paper dispute this "misaligned drive head" theory in their study of modern ERPML hard drives.  This misaligned head theory started with Gutmann who was writing in the mid '90's before ERPML drives were around.  

There used to be a blog post where one of the authors went into detail about the findings, but it appears to have been deleted.

I never mentioned anything about misaligned drive heads. That is another issue entirely, and I am aware it is not relevant with modern drives. There being a detectable difference between a bit which used to be one but set to zero and one that was zero but was reset to zero has nothing to do with the alignment of a drive head, unless I misunderstand the issue.

---

### Post by MasterNetra on 2010-04-04
> **NightwishFan said:**
> I agree. Even if you have pirated something, or similar do you think they will care?

> **BlackOtaku said:**
> Hey guys -- I've mean no offense here, but what makes you think people are going to dissect and examine your hard drive bit by bit? Honestly, unless you've committed a felony or are selling it to the CIA, the average comp. user won't be able to recover your old data reasonably after one or two random data passes. And by the time that guy finishes with the drive (for whatever reason) it will either have failed or your data will have been overwritten several times over. Why the suspicion? :p

They will care if they think they may recover personal info such as maybe a credit card number, your social security, etc. Identity theft is on the rise and while most of the crimes may not be from tossed out computers, it still is a unnecessary risk, why give them a chance when you don't need to?

---

### Post by NightwishFan on 2010-04-04
I suppose you are correct but there are much better methods to steal your identity. In either case it seems likely you would have to be targeted by professional criminals. I think a minimal effort would be enough to keep your data safe from passive or even active collection. I recommend:

CD/DVD
```
wodim -force blank=all
```

---

### Post by HermanAB on 2010-04-04
"the average comp. user won't be able to recover your old data"

Exactly - that is why one has to do a Threat and Risk Analysis before doing anything about security.  However, many people who use Linux do so in order to learn and the knowlege gained may be used later in a company or government environment.

---

### Post by jflaker on 2010-04-06
> **HermanAB said:**
> "the average comp. user won't be able to recover your old data"

Exactly - that is why one has to do a Threat and Risk Analysis before doing anything about security.  However, many people who use Linux do so in order to learn and the knowlege gained may be used later in a company or government environment.

You are absolutely correct...but a scenario....
You take your computer to the town's recycling center (and i've seen computers stacked 20 deep and 15 high on one occasion) and someone comes along and wants them...The town will usually "sell" each item for a dollar.  So, great...the computer gets a re-purpose and the town gets a few bucks....or that was the story this person had.

That person spent $80 for a truck load of computers for the sole purpose of running forensics on the hard disks to glean as much personal information as possible.  Now, this formatted drive contains the remnants of your data from your financial software (business or personal) and other data that was just found and there is enough available information to steal your identity.......

There are people who have nothing but time and run automated programs on drives....The person doesn't even need to do anything except kick off programs to search several connected drives and this can happen unattended....

Will the average person do this?  Highly unlikely...but you never know what happens to your electronics after you toss them.  I would rather be overly cautious than to find out someone found data and was able to steal my identity.

---

### Post by cdenley on 2010-04-06
> **jflaker said:**
> You are absolutely correct...but a scenario....
You take your computer to the town's recycling center (and i've seen computers stacked 20 deep and 15 high on one occasion) and someone comes along and wants them...The town will usually "sell" each item for a dollar.  So, great...the computer gets a re-purpose and the town gets a few bucks....or that was the story this person had.

That person spent $80 for a truck load of computers for the sole purpose of running forensics on the hard disks to glean as much personal information as possible.  Now, this formatted drive contains the remnants of your data from your financial software (business or personal) and other data that was just found and there is enough available information to steal your identity.......

There are people who have nothing but time and run automated programs on drives....The person doesn't even need to do anything except kick off programs to search several connected drives and this can happen unattended....

Will the average person do this?  Highly unlikely...but you never know what happens to your electronics after you toss them.  I would rather be overly cautious than to find out someone found data and was able to steal my identity.

We are still talking about a 2-pass random data overwrite, correct? This would make it impossible to recover anything without physically opening the drive and removing the platters. Even then, the possibility is purely theoretical, and requires expensive equipment and complex equations. I doubt even the NSA would be able to recover any data off the drive unless it was written to a sector later marked as bad and unusable. I think your identity theft scenario is impossible.

---

### Post by NightwishFan on 2010-04-06
I concur. Perhaps theoretically possible, but much more expensive to implement than what they would gain from it.

---

### Post by HermanAB on 2010-04-07
A serious issue with relying on deletion of data occurs when the drive electronics fail. In that case it is impossible to delete the data. If a knowledgeable person gets this drive in the trash, then he can buy a similar drive on Ebay and swap the electronics, then read all the data with no trouble at all.

The best practical way to protect against the above failure mode is to encrypt your data with LUKS.

---

### Post by jflaker on 2010-04-07
I wish I would have remembered this....

Here is a sure fire way to make sure your data can never be recovered....

[http://www.youtube.com/user/Blendtec](http://www.youtube.com/user/Blendtec)

:lolflag:

---

### Post by EJeanmaire on 2010-04-08
> **HermanAB said:**
> A serious issue with relying on deletion of data occurs when the drive electronics fail. In that case it is impossible to delete the data. If a knowledgeable person gets this drive in the trash, then he can buy a similar drive on Ebay and swap the electronics, then read all the data with no trouble at all.

The best practical way to protect against the above failure mode is to encrypt your data with LUKS.

Or own a degausser ;-)

---

