---
title: "Advice recovering Hardware RAID 5"
date: 2012-08-03
forum: Server Platforms
---

### Post by MezzFA0 on 2012-08-03
Hi all,

I'm in a bit of a sticky situation where I've had a hardware RAID controller fail and I'm trying to piece together a 6 disk raid 5 (approx 800GB).

The disks are perfectly fine and I've managed to dd image them without any issues.  I then started stitching the images back together with a few open source tools.

I'm at the point where I can see all the files I want but any files that are bigger than my raids stripe size are corrupted.  For example in some mp3s I get a length of the song, 2 seconds of another song, more of the first song, then another 2 seconds etc etc.

It almost looks as if my assumed disk order is wrong and its piecing in the wrong info.  Heres where I would appreciate advice, how can you tell from say a hexedit where a block ends and then reappears on another disk?

I've read a few guides that all seem to assume you're looking at big text files.  Unfortunately I can't find any sizeable text files to get an accurate guess on the disk order.

Has anyone had the misfortune of dealing with this themselves?  Any advice would be appreciated.

---

### Post by rubylaser on 2012-08-03
Are you unable to purchase the same card and import the array?  That would be the recommended method to recover from a failed hardware RAID controller. Hardware dependence is one of the biggest downsides to hardware RAID.  But, if you can find the same card, importing your current array shouldn't be difficult.

---

### Post by CharlesA on 2012-08-03
> **rubylaser said:**
> Are you unable to purchase the same card and import the array?  That would be the recommended method to recover from a failed hardware RAID controller. Hardware dependence is one of the biggest downsides to hardware RAID.  But, if you can find the same card, importing your current array shouldn't be difficult.
I was going to suggest that. If you can't get the same model of card, try to get the same brand.

I haven't had the misfortune of having my card go out of me yet, but I am very diligent with my backups, so if it does go out, I won't be totally screwed.

---

### Post by Cheesemill on 2012-08-04
I always go for software RAID now for just this reason, I had an old controller die on me and couldn't find a replacement.

It will be a lot easier and quicker for you to just restore from a backup rather than trying to piece together the disks.

---

### Post by MezzFA0 on 2012-08-06
Hi again,

Thanks for the replies.  I've tried a new card without any success.  Its almost as if the card itself didn't fail permanently and neither did the drives (as far as I can tell).

All I know is at the moment the raid cards sees drive 1 and 2 as OK.  Drives 4 and 5 as having foreign config and drives 0 and 3 without anything useful on it.

I've been digging into hexdumps over the weekend and I've finally found a pattern on broken files that corresponds to the number of disks I have.

Basically I get the following:

Start of File
Up to 5 good chunks of 64k (depending on where the file started in the list of chunks)
1 bad chunk
5 good
1 bad 
5 good etc etc
End of File

If I could figure out which disk is dead it would be nice.  I think I'll assume each disk in turn is dead and try and reconstruct one at a time.  6 attempts doesn't seem too bad.

Thanks again for the info so far.

---

### Post by MezzFA0 on 2012-08-19
Hi all,

Managed to solve this in the end.  For anyone in the same situation heres how I did it:

**Pre-reqs:**

When your raid goes down the first thing you need to do is get a DD image of each disk.  **Don't faff about trying things** as you'll likely just make things worse (I was quoted between £1,000 - £2,000 for file recovery only on the condition that I hadn't messed with the disks, if I had it was going to be more than 2k).

Make sure you label your disks so that you know what disk slots they came from.  Putting them back in the wrong place can also make things worse if you need to send them off to a recovery company.

If you get errors grabbing the images one or more of your disks are faulty and this method probably won't work (unless its only one disk or as much as your RAID can tolerate before failing on other raid levels).

If you have SAS drives like I did, you'll either need a linux friendly spare server to mount them as a JBOD or buy something like the Rocket RAID 2640.  This works fine under Debian, for some reason even though I could use it on Ubuntu I got access denied errors running the recovery.  I never did figure out why seeing as I was pushed for time.

**Actual recovery steps:**

[LIST=1]
[*]Checkout the following bzr branch:

[https://code.launchpad.net/~eantoranz/+junk/raidpycovery](https://code.launchpad.net/~eantoranz/+junk/raidpycovery)

```
bzr branch lp:~eantoranz/+junk/raidpycovery
```

This is some simple stitching software written in c++ made by a guy from Venezuela ([http://maratux.blogspot.co.uk/2011/11/remember-times-with-i-used-python-for.html](http://maratux.blogspot.co.uk/2011/11/remember-times-with-i-used-python-for.html))

There are various oddities to the translations and other peculiarities such as the software counting in Gigabytes when stitching and resetting to I think -2 as soon as it gets to 2 GB and then loops until finished.  It works despite the strangeness so don't worry about that.


[*]Attempt to stitch your drives back together using the code above (once compiled).

To do this you need to know (or guess the following):

The RAID stripe size, you might be able to find this in your RAID BIOS if not just bet on the default size from any user manual you can find for the RAID card.

In my case it was a 64KB stripe.

Then you need to know how the raid parity is distributed, I couldn't find any info here but the default for most RAIDs is Left distributed, Synchronous (I've seen this mentioned as Symmetric but I couldn't figure out whether synchronous was a mistranslation or not).

Finally you need to know the order of the disks, normally the disk in slot 0 is first followed by slot 1, 2 etc but this doesn't have to be the case so this can catch you out.  Just hope the order is correct otherwise you have 720 combinations on 6 disks which takes forever to sort through.

You can check to see what the first disk is quite easily as if you fdisk the image disk 0 will have a partition table where as the rest won't.

So on with the stitching:

```
./raidrec 5 6 left sync 65536 disk1 disk2 disk3 disk4 disk5 disk6 > final_disk
```

raidrec is the recovery/stitching tool.  The first number is the RAID level (it supports either Raid 4 or 5).  After this is how many disks in the RAID (6 in my case).  Then the parity distribution, left, sync.  Then the stripe size in bytes (64k = 65536), then your disks in the correct order and output to a file.

You'll need enough space for this to complete!

This will take a while, I believe it was about 6 hours on an 870GB ish array.  Recover to a separate disk if you can as it takes even longer reading and writing to the same place.

If you're lucky you can then mount the resulting disk and recover your files.  Unfortunately I wasn't so lucky as nearly every file apart from small ones (under 64kb) were corrupt.


[*]Figuring out the corruption:

To do this I mounted and ran hexedit on one of the larger files.  I found a pattern of 5 good data chunks followed by 1 set of 0s (with offsets of 10000 in HEX which equals 64KB).  So I could tell that one of my disks was dead.  

Its not guaranteed that the data will be nice 0s.  If this is the case, try and find a big text file that you can follow through by reading.  If you get nice readable text then a block of gibberish followed by more readable then you also have one broken disk.

At this point I knew one disk was dead but I had no clue which one it was.  Some people say you can follow the chunks on each disk image but just finding the start of a particular file was a nightmare, good luck to you if you can do that method.  I went the time consuming way:

You can use rmir included with the branch above to recover disk images from other working ones, but you have to change the make file as there is an error which means the rmir executable is actually just a copy of raidrec.  So fix that and recompile.

rmir is quite simple you just run it as follows:

```
./rmir disk1 disk2 disk3 disk4 disk5 > disk6
```

Basically string together your working disks and it will output the missing broken one.  Then restitch the "working" disks in step 2 and remount to see if things are working.

It took I believe an hour or so to reconstitute a broken disk, then with 6 hours to stitch it gave me an 8 hour turn around.

Thankfully, I stumbled across some commercial software that made this process much faster:

Download RStudio from [http://www.r-studio.com/](http://www.r-studio.com/)

There is a Linux version and the Windows version also works fine under Wine.  I then used RStudio to assemble a RAID5 and told it that disk x was missing.   I repeated this step for all the disks until I found some that looked usable.

Using this process I had only two candidates for success, the others produced invalid partition tables.

I ran rmir to recover the two possible faulty disks and then stitched together the two attempts.  The first attempt gave me an even more corrupted set of files (so 16 hours later I was in business).


[*]Getting the original RAID back up and running in the host server:

At this point I had 6 working dd images and a complete image of the RAID but I wanted to see if I could get the original server working as I had no idea where to find an NT4 CD.

So I ran dd in reverse on the disk I recovered using rmir back onto the original disk.

Then I slotted all the disks back into the server and went into the RAID setup.

I then deleted the configuration that the RAID thought it had and manually recreated what should be the working config (basically all the disks as one big pool).

On the controller I had, it asked if I wanted to initialise the array and noted "if you're attempting a recovery, do not perform this step as all data will be erased".

So I skipped the initialisation.  The server rebooted and 2 minutes later the 2 weeks of long hours were over.
[/LIST]
**More info on R-Studio:**

As an aside, if you need to save yourself a lot of time just buy R-Studio.  It can make the raid without having to stitch it together (so 6 hours saved each time there).  I think it can recover broken disks (I used rmir here so I'm not sure) and its also invaluable for trying left sync, async, right sync, stripe sizes etc in case the defaults don't work for you.

Hope this helps someone further down the line.

---

