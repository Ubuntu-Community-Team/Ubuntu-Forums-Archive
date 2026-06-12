---
title: "Erasing the data before giving away a hard disk"
date: 2010-05-03
forum: The Cafe
---

### Post by Viva on 2010-05-03
I'm thinking about giving away my old hard disk, but I had some very important data stored on it before. I don't want somebody getting hold of my personal data using a data recovery software. Is the disk utility software enough for the purpose?

---

### Post by kaldor on 2010-05-03
Run this from a LiveCD but note this is a DANGEROUS command that will make it impossible to recover data: 

```

dd if=/dev/zero of=/dev/sda

```

Run it as root, but be careful to back up everything.

---

### Post by Chrysantine on 2010-05-03
No, just wiping it via partitioning utilities won't do the job - you can still easily recover data even after a format or a dd. 

Use a program called **shred** - you can do it via a LiveCD or existing installation and have it do multiple random data write runs.

An example;
[http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)

100 may be a little excessive - even for the paranoid :-)

---

### Post by insane_alien on 2010-05-03
just fill it with zeros and it'll be sufficient. 

dd if=/dev/zero of=/dev/sdX

where sdX is the drive you want to wipe.

if you're really paranoid you can write random numbers over it several times as well but really, this will be a waste of time. anyone with the resources available to get the data off it after writing all zeros  isn't going to be buying drives of ebay or whatever and they also won't really care unless your a secret agent for another government or terrorist organisation.

---

### Post by MacUntu on 2010-05-03
> **Chrysantine said:**
> you can still easily recover data even after a [...] dd.

Prove it. :)

---

### Post by K.Mandla on 2010-05-03
> **MacUntu said:**
> Prove it. :)
I'd be interested in seeing that too. It was my understanding that dd has never been proven recoverable. I could be wrong though.

dban is good stuff too.

[http://www.dban.org/](http://www.dban.org/)

I've used the free version of Killdisk in the past, and it works well.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by Drenriza on 2010-05-03
> **insane_alien said:**
> just fill it with zeros and it'll be sufficient. 
 
dd if=/dev/zero of=/dev/sdX
 
where sdX is the drive you want to wipe.
 
if you're really paranoid you can write random numbers over it several times as well but really, this will be a waste of time. anyone with the resources available to get the data off it after writing all zeros isn't going to be buying drives of ebay or whatever and they also won't really care unless your a secret agent for another government or terrorist organisation.
 
Wrong.
download hirens boot cd. go to google.com and type
download hirens boot cd. download it, burn it, and start the system up on it.
 
Use the utility kill disk. This will wipe your drive multiple times. By writing the hexidecimal value if FF to the drive and then wiping it again.
 
It will take time. But filling your drive with 0 is an insanely un-professional way of doing things. It would take me 2mins to recover data from such a drive.

---

### Post by MacUntu on 2010-05-03
> **K.Mandla said:**
> I'd be interested in seeing that too. It was my understanding that dd has never been proven recoverable. I could be wrong though.

Maybe, just maybe, government agencies with advanced electron microscopes can recover something... but that's not my understanding of "easily recover data". :D

---

### Post by spupy on 2010-05-03
Well, I'm not worried about government agencies. For my purpose several dd's of /dev/zero and /dev/random will be perfectly sufficient.

---

### Post by MacUntu on 2010-05-03
> **spupy said:**
> Well, I'm not worried about government agencies. For my purpose several dd's of /dev/zero and /dev/random will be perfectly sufficient.

Good luck with /dev/random:

>  When read, the /dev/random device will only return random bytes  within the estimated number of bits of noise in the entropy pool.  /dev/random should be suitable for uses that need very high quality randomness such as  one-time  pad  or  key generation.  When the entropy pool is empty, reads from /dev/random will block until additional environmental  noise is gathered.

Use /dev/urandom instead (less random but won't take you days), or better use /dev/zero as I've seen exactly the same number of recovered devices for all three sources (after one run): 0.

---

### Post by 3rdalbum on 2010-05-03
DD is certainly good enough. If you're really paranoid, run it a couple of times, get the disk heads to park (like, by turning off the hard disk), start it back up again and run dd a couple more times, etc.

If you're super-paranoid, you could use one of those little devices that generates quantum random numbers, and use the output of that instead of /dev/zero.

With /dev/zero, if the data recovery expert knows how many times you ran dd, they can potentially recover data through studying exactly how "zero" a zero is on the magnetic platter of the disk. With random numbers, or even pseudo random numbers, it should be much more difficult.

---

### Post by NMFTM on 2010-05-03
Why do it half assed though? Even if it takes a long to write over your HD 100 times with pesudorandom numbers, all you have to do is set it to start and than leave it alone until it's done.

---

### Post by ssam on 2010-05-03
if you set a bit to zero, then disk drive will always read it back as zero (unless there is some secret interface, that lets you get the analog reading for each bit). so the only way to recover is to dismantle the drive and read the bits with some fancy machine.

if someone wants to know whats on your disk that badly they would probably find it cheaper/easier to arrest, kidnap, rendition, etc you.

personally i run a destructive read+write badblocks test over the drive. has the bonus of also checking that the drives is in good condition.

```

badblocks -w -o bb.log -s /dev/sdX

```
then check no block numbers were writen to bb.log

---

### Post by dragos240 on 2010-05-03
Zero the HDD out. Zero it out many times, like 5. Just to make sure.

---

### Post by CharlesA on 2010-05-03
I just use DBAN. Why make it overly complicated?

---

### Post by Viva on 2010-05-03
I forgot to mention that this disk is slightly damaged. The disk utility says there are a few bad sectors.

---

### Post by Viva on 2010-05-03
> **Chrysantine said:**
> No, just wiping it via partitioning utilities won't do the job - you can still easily recover data even after a format or a dd. 

Use a program called **shred** - you can do it via a LiveCD or existing installation and have it do multiple random data write runs.

An example;
[http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)

**100 may be a little excessive - even for the paranoid** :-)

How many should I use then?

---

### Post by wojox on 2010-05-03
I think DoD uses 3 passes.

---

### Post by Tristam Green on 2010-05-03
> **dragos240 said:**
> Zero the HDD out. Zero it out many times, like 5. Just to make sure.

If all else fails, nuke it from orbit.  It's the only way to be sure.

> **Viva said:**
> How many should I use then?

I believe that 8 passes of zeros or random characters is sufficient for US Department of Defense record retention and destruction policies.  Use that as a high-end standard :|

---

### Post by Viva on 2010-05-03
Cheers. Is there any way I can do it without using a live cd? The disk is currently connected to my computer, but I don't have any data on it.

---

### Post by swoll1980 on 2010-05-03
The data has to be overwritten in order for it to be unrecoverable. Fill it with zeros as someone else said.

---

### Post by ve4cib on 2010-05-03
Assuming the disk isn't mounted then you won't need a live CD.

As for the /dev/random vs /dev/urandom question, it's pretty pointless for this application; you're not cryptographically changing the data; you're overwriting it with garbage to make the old data unrecoverable.  If writing a fixed value (like 0xFF or 0x00) to the disk repeatedly is good enough, then pseudo-random values (which are more cryptographically secure than fixed values) should be random enough.

There is also a command-like tool called wipe that you might want to look into.  It's on the repos, and does essentially the same thing as shred.

```
$ wipe /dev/sdaX
```

That will wipe the entire partition.  Obviously replace "sdaX" with the actual partition though.

---

### Post by jetsam on 2010-05-03
Overwrite it between one and three times and you're covered, unless you're related to Dr. Evil or aspire to be Darth Vader, then you should pulverize it it with a sledgehammer.  If this is the case, please post video on YouTube.

---

### Post by swoll1980 on 2010-05-03
> **jetsam said:**
> Overwrite it between one and three times and you're covered, unless you're related to Dr. Evil or aspire to be Darth Vader, then you should pulverize it it with a sledgehammer.  If this is the case, please post video on YouTube.

Once is more than enough, unless the guy your giving the computer to is a forensic data recovery specialist for the FBI or something.

---

### Post by Viva on 2010-05-03
How long will it take? I've used dd if=/dev/zero of=/dev/sda and it is a 80gb disk.

---

### Post by mmix on 2010-05-03
[http://degausser.com/](http://degausser.com/)

---

### Post by swoll1980 on 2010-05-03
> **Viva said:**
> How long will it take? I've used dd if=/dev/zero of=/dev/sda and it is a 80gb disk.

I would guess around 25 minutes. It would depend on alot of things.

---

### Post by Viva on 2010-05-03
Thanks. Can I cancel the operating using Ctrl+C and redo it later?

---

### Post by swoll1980 on 2010-05-03
> **Viva said:**
> Thanks. Can I cancel the operating using Ctrl+C and redo it later?

You could. You would have to start over again though.

---

### Post by J V on 2010-05-03
Dude, whats with the DD? Just "sudo shred /dev/sda"...

---

### Post by barney385 on 2010-05-03
> **mmix said:**
> [http://degausser.com/](http://degausser.com/)

**+1**

---

### Post by NCLI on 2010-05-03
> **mmix said:**
> [http://degausser.com/](http://degausser.com/)

Not a good idea:
> Can Computer Tape and Hard Drives be Reused After Degaussing?
Many types of magnetic media can be reused after being run through a degausser, such as analog and digital video cartridges, DLT, 3480 and 3490. However, certain forms of media employ the use of servo tracks, which tell the computer how to interface with the media so that it can be read. Using a degausser to erase these not only erases the data on the media but also erases the servo tracks, so that the computer or tape drive will not be able to engage with the media after erasure. Hard disk drives and LTO and 3590 tape employ servo tracks and cannot be reused after being degaussed unless they are reformatted by the manufacturer and the servo tracks are rewritten.

---

### Post by Viva on 2010-05-03
I used sudo dcfldd if=/dev/zero of=/dev/sdb statusinterval=10 bs=10M conv=notrunc in the end. It has taken 40 minutes for wiping the entire drive. I guess it would've taken hours with the default options. Is using a larger block size a problem?

---

