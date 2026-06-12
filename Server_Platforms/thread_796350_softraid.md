---
title: "softraid?"
date: 2008-05-16
forum: Server Platforms
---

### Post by BeastlyKings on 2008-05-16
I have got an old computer set up, installed with ubuntu server 8.04 and all I want it to do is be a simple file server and print server for my home network. But, I would like to set up softraid for the file serving part.
I have three HDDs, 1x 3.5Gb 2x 80Gb.
I installed samba and ubntu-desktop for a gui, now I was wondering if I could get some help setting up softraid? Or at least point me to a howto?
I can't find anything on google..

-Tom

---

### Post by rickyjones on 2008-05-16
> **BeastlyKings said:**
> I have got an old computer set up, installed with ubuntu server 8.04 and all I want it to do is be a simple file server and print server for my home network. But, I would like to set up softraid for the file serving part.
I have three HDDs, 1x 3.5Gb 2x 80Gb.
I installed samba and ubntu-desktop for a gui, now I was wondering if I could get some help setting up softraid? Or at least point me to a howto?
I can't find anything on google..

-Tom

In an article I wrote I included a section for using mdadm to create a simple RAID1 array.

[http://www.rrcomputerconsulting.com/view.php?article_id=3#9](http://www.rrcomputerconsulting.com/view.php?article_id=3#9)

That takes you directly to the section in my article. It should be adaptable to your needs.

Beyond that I would google for "mdadm" - this is the tool that you'll want to use.

Hope this helps!

Sincerely,
Richard

---

### Post by BeastlyKings on 2008-05-16
So, I could configure md0 and md1, each with only one drive, and when I write data to either md0 or md1 then the data is simultanesously written to the other drive as well?

---

### Post by rickyjones on 2008-05-16
> **BeastlyKings said:**
> So, I could configure md0 and md1, each with only one drive, and when I write data to either md0 or md1 then the data is simultanesously written to the other drive as well?

Uh, no, I think you may have misread the little guide that I wrote.

In my guide I created two RAID1 arrays, each with two identical hard drives (four individual hard drives in total).

In your case you would create a single RAID1 array, md0, using your two large hard drives.

This array, md0, would be mounted somewhere and you would write data to it, just like a hard drive. md0 is the virtual array controlled by mdadm. This software will automatically write the data to both physical hard drives (hda and hdb, for example) simultaneously.

Does that make sense?

Sincerely,
Richard

---

### Post by Donb01 on 2008-05-16
Just for my own edification because I'm going to be doing the RAID thing myself soon, I see where you went with your article, but I am in the habit of making separate partitions for things like /var/ftp, /var/www, usr and related stuff so that if anything gets out of control - say someone brute forces themselves into my ftp server and uploads a bunch of crap, that it cannot fill up the drive.  Back in the old days especially, if you ran out of disk space on the root volume the system would get VERY unhappy about it.  I know this could be a pain later if I start putting large files or large quantities of them on a partition, but I usually make them bigger than I expect I'll need and shouldn't have to worry about that.

So, when you say to partition each drive - and imply one partition, would I partition each drive of my mirrored pair into identical sized chunks, mirror them, and then create my EXT3 filtesystems on each mirrored partition, finished by mounting them as /var/www, /usr and the like?

---

### Post by rickyjones on 2008-05-16
> **Donb01 said:**
> Just for my own edification because I'm going to be doing the RAID thing myself soon, I see where you went with your article, but I am in the habit of making separate partitions for things like /var/ftp, /var/www, usr and related stuff so that if anything gets out of control - say someone brute forces themselves into my ftp server and uploads a bunch of crap, that it cannot fill up the drive.  Back in the old days especially, if you ran out of disk space on the root volume the system would get VERY unhappy about it.  I know this could be a pain later if I start putting large files or large quantities of them on a partition, but I usually make them bigger than I expect I'll need and shouldn't have to worry about that.

So, when you say to partition each drive - and imply one partition, would I partition each drive of my mirrored pair into identical sized chunks, mirror them, and then create my EXT3 filtesystems on each mirrored partition, finished by mounting them as /var/www, /usr and the like?

You could do it that way, yes. If that is your preferred way more power to you. Although I feel it could get complicated trying to keep all the different partitions straight. But yes, what your propose would work.

Partition both hard drive into identical chunks. HDA1 corresponds with HDB1 and so on and so forth. Then you can configure a RAID array for each partition.

-Richard

---

### Post by BeastlyKings on 2008-05-16
@rickyjones,
THANKS A TON!
That makes sense, I followed the guide the way you said, with two drives using only md0. And it worked! It all mounts at startup now too.

Much appreciation.

-Tom

---

### Post by rickyjones on 2008-05-16
> **BeastlyKings said:**
> @rickyjones,
THANKS A TON!
That makes sense, I followed the guide the way you said, with two drives using only md0. And it worked! It all mounts at startup now too.

Much appreciation.

-Tom

You're very welcome! Let me know if I can be of any other assistance.

Sincerely,
Richard

---

