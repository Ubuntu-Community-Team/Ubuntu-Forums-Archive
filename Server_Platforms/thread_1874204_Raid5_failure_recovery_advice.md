---
title: "Raid5 failure: recovery advice"
date: 2011-11-02
forum: Server Platforms
---

### Post by daniel.pool on 2011-11-02
Hi,

As the title says my raid 5 array failed last week. I have an Adaptec 3805 h/w raid solution with 8x 1.5TB disks. One disk was mounted as a dedicated hot spare and the rest were set up for a Raid 5.

The rough sequence for the failure is as follows:
[LIST]
[*]The alarm on the adaptec goes off late at night signalling a disk error, the hot spare automatically joins the array and it begins rebuilding. As it is late at night and for some reason I can't log into the adaptec storage manager, I shut down the server instead.
[*]A few days later I finally have to opportunity to boot the server to investigate, it appears one of the disks reached a threshold for medium errors and was taken out of the array. Unable to do anything more I shut the server down again resolving to buy a few new disks.
[*]Wanting to investigate how much of the disk space I am using for certain types of media, I turn the machine back on. The array shows as failed and Ubuntu server fails to boot because it is unable to mount the drive (note, this isn't a boot disk, but it is mounted in the fstab).
[/LIST]

So, my array is now showing as failed. At this point I would cunningly rebuild the array and restore from a backup ... except. Yes, I was in the middle of changing a backup strategy and haven't backed up recently (typical I know).

From what I have read it is possible to use the dd command to make a bit level copy of each drive and use that to reconstruct the array (either with some home grown software or using some commercial tools). All very well except for the fact that dd images the entire disk, and I haven't got anywhere big enough to store these files. Having done a bit of investigating I have some questions:

[LIST=1]
[*]Though the array was some 6.8TB, I had only used around 1.6TB of its capacity. If I zero out the empty blocks of the disk and compress the image will I be preventing myself from reconstructing the array as a file?
[*]I note that CloneZilla will make images of only the used space, can I then convert these images to a more conventional file format used be the raid recovery tools out there.
[*]Does anyone know of any other FOSS tools that will help in this situation?
[/LIST]

Thanks in advance,
~Dan

---

### Post by darkod on 2011-11-02
I'm slightly confused. You shut off the server while the hot spare was still syncing?

Why didn't you just let it sync and you end up with a working server with 7/7 disks working, while the one failed was replaced automatically by the hot spare?

---

### Post by daniel.pool on 2011-11-02
Yea, I know not the best of choices. Honestly though, it's because it was 1 something am and when the disk failed the alarm on the Adaptec card started going off ... it was quite loud and since I live in a small London flat and the server lives quite close to my baby girl's room shutting down became the best choice. I'd initially tried to get into the Adaptec Management software to check the status of the array and turn the alarm off, but this wouldn't connect to the card for some reason. Because of that I didn't know what had happened with the array (or even if the hot swap had worked). Instead I opted to shut the machine off as fixing software issues and dealing with an angry wife and screaming daughter aren't things I wanted to deal with.

It wasn't until a few days later that I was able to the time to turn things on again and figure out why I couldn't log in ... it turns out the host service wasn't running as it's not set to run by default in level of userland I had running (level 3 ... I'm hoping I have the term right, it's late and I'm running off memory not research). Having logged into the manager I was able to see that the disk was rebuilding and the array was running in a degraded state ... unfortunately the alarm was still going off and refusing to turn off with the silence alarm command and 3 hours later when my wife and daughter came home it was still going off. At this point the array was only 30% rebuilt ... at which point I shut the server off again rather than deal with things thinking that I could figure it out later.

---

### Post by darkod on 2011-11-02
This might be more Adaptec then Ubuntu thing. Since you are not using software raid but instead a dedicated raid adapter with it's own management, the research about restoring the array to a working state is probably better to go Adaptec way.

One thing still confusing me though. OK, you shut the server because you had a reason. If I got it right, originally you had one spare disk and a RAID5 array of 7 disks. If one fails, even if the spare doesn't kick in, a RAID5 array is still good with one failed disk.

Not sure how shutting it during a rebuild affects it, but doesn't common sense says this: with the server off, remove both the failed disk and the hot spare. Get a new, third disk and install it instead of the failed one.

Turn the server on and enter the raid management console. With 6/7 disks of RAID5 still operational, shouldn't it start rebuilding again using the new disk as seventh?

---

### Post by daniel.pool on 2011-11-03
Hey Darkod,

Thanks for your help.

My problem is that the array is no longer showing up as degraded, it is now marked by the adaptec console as failed with each seperate disks of the array showing as optimal. I now wonder if the console thinks that it should be done rebuilding the disk and because it doesn't have all the information it's freaking out (I'd actually just assumed that I'd been really unlucky and had two disk with too many URE failures).

I'd originally found a blog where someone had had a similar issue and they solved it by going down the 'dd' command and turn the array into a single file route; hence my questions.

I'll certainly try removing the disks, perhaps that'll put the array back into a degraded state. In which case I'd be able to restore conventionally rather than worrying about copying things.

Even though it isn't an Ubuntu thing I'll report back here as I go.

Thanks,
~Dan

----

Just wanted to report on progress. By removing the old hot spare I was able to force the array back on-line in a degraded state (I had to use the Advanced Options and Force on-line without a consistency check). I've since taken a full backup of the array, though I have yet to verify that there has been no data loss. It looks like the Adaptec Manager did consider the hot spare fully rebuilt and hence the array reporting as failed since the disk was only 30% rebuilt (it takes around 2 days to rebuild).

---

