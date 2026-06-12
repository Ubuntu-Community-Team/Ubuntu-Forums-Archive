---
title: "Ext4: How do you feel?"
date: 2010-01-27
forum: The Cafe
---

### Post by k64 on 2010-01-27
How do you like Ext4 currently? Of course, it's the default in Ubuntu 9.10 and 10.04 LTS Alpha. Do you guys think it's a very good file system, and how much of a performance increase are you guys having? Please explain your votes.

---

### Post by Dark Aspect on 2010-01-27
> **k64 said:**
> How do you like Ext4 currently? Of course, it's the default in Ubuntu 9.10 and 10.04 LTS Alpha. Do you guys think it's a very good file system, and how much of a performance increase are you guys having? Please explain your votes.

Never had problem with it on Arch, But I sadly didn't use it with Ubuntu.

---

### Post by yester64 on 2010-01-27
Can't really compare. I used ext4 previously and i haven't noticed either a drop or gain in performance.
I feel ok.

---

### Post by FuturePilot on 2010-01-27
I don't trust it. Never had an issue with Ext3; have had issues with Ext4.

---

### Post by Mike'sHardLinux on 2010-01-27
For me there is no difference, unless it is responsible for the faster boot and shutdown times.

---

### Post by jrusso2 on 2010-01-27
I don't trust any of the ext based file systems and have not used them since I have lost data on both ext2 and ext3.

---

### Post by juancarlospaco on 2010-01-27
Rock solid, never failed.

---

### Post by baddog144 on 2010-01-27
I haven't really noticed that I'm using it. So I'm happy with it. :D

---

### Post by CharlesA on 2010-01-27
Does that problem where large files become corrupted still exist in EXT4?

---

### Post by FuturePilot on 2010-01-27
> **CharlesA said:**
> Does that problem where large files become corrupted still exist in EXT4?

Apparently so.

---

### Post by CharlesA on 2010-01-27
> **FuturePilot said:**
> Apparently so.

I shall stick to EXT3 then.

---

### Post by dragos240 on 2010-01-27
I like it. WorksForMe.

---

### Post by nmccrina on 2010-01-27
I haven't noticed any difference, so I said "kind of good".

---

### Post by Grifulkin on 2010-01-27
No, other option.  I don't use it, I use XFS.

---

### Post by dmizer on 2010-01-27
> **FuturePilot said:**
> Apparently so.

Where's the evidence for this?

---

### Post by k64 on 2010-01-27
There is one key difference between Ext3 and Ext4: 64-bit. That's why I prefer Ext4, because it is 64-bit optimized. Not to mention it has support for up to an exabyte of hard drive space (in the form of mounted volumes, of course) so it is perfect for large-scale server deployments.

---

### Post by Grifulkin on 2010-01-27
> **k64 said:**
> There is one key difference between Ext3 and Ext4: 64-bit. That's why I prefer Ext4, because it is 64-bit optimized. Not to mention it has support for up to an exabyte of hard drive space (in the form of mounted volumes, of course) so it is perfect for large-scale server deployments.

Who is ever going to need an exabyte of space?

---

### Post by thatguruguy on 2010-01-27
That's a LOT of pirated movies and tunes.

---

### Post by dmizer on 2010-01-27
> **Grifulkin said:**
> Who is ever going to need an exabyte of space?

> **k64 said:**
> large-scale server deployments.

For example, ext4 handles large file sizes much better than ext3. For that reason, I'm using ext4 for my virtualization server where single files can reach 30+ gig. If you've got a central virtual datacenter, you're looking at giant storage needs.

---

### Post by Grifulkin on 2010-01-27
> **dmizer said:**
> For example, ext4 handles large file sizes much better than ext3. For that reason, I'm using ext4 for my virtualization server where single files can reach 30+ gig. If you've got a central virtual datacenter, you're looking at giant storage needs.

Can I ask why you use ext4 over say xfs that has a reputation with working with large files better then others?

---

### Post by dmizer on 2010-01-27
> **Grifulkin said:**
> Can I ask why you use ext4 over say xfs that has a reputation with working with large files better then others?

Pretty simple really. I have no experience with XFS, while all the ext3 tricks and knowledge I have also works in ext4.

---

### Post by Grifulkin on 2010-01-27
> **dmizer said:**
> Pretty simple really. I have no experience with XFS, while all the ext3 tricks and knowledge I have also works in ext4.

That definitely works, experience is always a good thing.

---

### Post by JDShu on 2010-01-27
It worked as well a Ext3 did.. really didn't notice anything. I suspect that I won't notice a change when btrfs goes mainstream either.

---

### Post by Queue29 on 2010-01-27
> **dmizer said:**
> Where's the evidence for this?

[IMG]http://i.imgur.com/v4K6S.png[/IMG]

---

### Post by FuturePilot on 2010-01-27
> **dmizer said:**
> Where's the evidence for this?

Still not fixed [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579]("https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579")

---

### Post by dmizer on 2010-01-27
> **FuturePilot said:**
> Still not fixed [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579]("https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579")
Thanks.

---

### Post by /ext4 on 2010-01-28
> Ext4: How do you feel?


I feel pretty good, thanks. Yourself?

---

### Post by schauerlich on 2010-01-28
> **/ext4 said:**
> I feel pretty good, thanks. Yourself?

In before banned for dupe account. I lol'd though, so, totally worth it.

---

### Post by Dark Aspect on 2010-01-28
> **FuturePilot said:**
> Still not fixed [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579]("https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/453579")

[That problem is fixed in Kernel 2.6.3*2*]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.32.1").

---

### Post by chessnerd on 2010-01-28
I didn't vote.

I don't feel that ext4 had any *major* performance increase for me, nor do I blame it for Karmic's issues. Those faults belong to the OS and applications, not the underlying file system. 

At the same time, it's also not just "kind of good." I think it's plenty solid. It survived a few hard-boots without data loss and seems a *bit* faster than ext3.

From about 3.5 months of use, I can say that I am satisfied as a user and will be using it for my Linux installs for the foreseeable future.

---

### Post by cronos on 2010-01-28
I don't really have enough experience with ext3, so I don't know if ext4 is better.  But, ext4 used to freeze a lot when I was using Ubuntu 9.04..  However, ext4 on Ubuntu 9.10 seems very stable.

I did not know that there is a possibility of losing data for files larger than 512mb.  Scary!  I have a lot of movies on my HD.  As far as I know, I don't have any corrupted files.

---

### Post by 5dolla on 2010-01-28
it feels solid.

---

### Post by Zoot7 on 2010-01-28
I'm still on the fence about it, and I most certainly wouldn't go trusting a lot of data to it.
That said, the root partition on most of my Linux installs is Ext4, but my home and data partitions are going to stay Ext3 for a long time to come yet.

---

### Post by ukripper on 2010-01-28
It is excellent FS! Using it since jaunty beta days and never looked back. Though my servers are still running ext3.

---

### Post by JohnFH on 2010-01-28
I used it for quite a while (6 months to a year), and it was faster than ext3 but I encountered 'that' bug and lost some data.  Now I'm back to ext3.  I would strongly advise against using it unless you are running kernel 2.6.32 or above.  It may work for you now, like it did for me for a while, but that data loss risk is a definite risk.

---

### Post by llawwehttam on 2010-01-28
I am running 64 bit ubuntu 2.6.31-17-generic on ext4 and have noticed it is faster. Also I have several large dvd iso's ( ie about 8GB) as I back up my favorite movies and I have never had corruption. Besides I thought that problem was fixed a while back.

EDIT: I don't know how long it will be till ext is abandoned for Btrfs anyway.

---

### Post by ukripper on 2010-01-28
> **JohnFH said:**
> I used it for quite a while (6 months to a year), and it was faster than ext3 but I encountered 'that' bug and lost some data.  Now I'm back to ext3.  I would strongly advise against using it unless you are running kernel 2.6.32 or above.  It may work for you now, like it did for me for a while, but that data loss risk is a definite risk.

That is why backup is always advised in any case ext3 or ext4 irrespective. 

"No-backup makes man to lose data, not the filesystem."

---

### Post by whiskeylover on 2010-01-28
Why are multiple choices selectable in this poll? Its not like it made my apps crash and thats why I love it.

Besides, where is the option for "neutral"?

---

### Post by k64 on 2010-01-28
Considering I have downloaded a CD image of Ubuntu 10.04 LTS Alpha 2 on a Karmic installation with Ext4 and the .ISO image didn't get corrupted, I haven't gotten any large file corruption on Ext4, 3, or 2.

I also have downloaded the Foresight image (though I haven't used it) on Linpus Lite, and haven't gotten any corruption of the image.

Also: The Foresight image is larger than the Ubuntu 10.04 image.

---

### Post by nrs on 2010-01-28
It's fine, I enjoy it. I'm sceptical of people going "OMG PERFORMANCE@". It is faster, but filesystem performance isn't generally something people running desktop machines will notice.

---

### Post by Jackelope on 2010-01-28
i just clean installed 9.10 with ext3 because i read that the modifications to ext4 to improve reliability pretty much made it slower than ext3. So far, I'm having less stability issues than I did on ext4. Gnome-do would crash constantly, for example. Since I've only had the new install a day, it's too soon to tell if ext3 is really helping, but it sure seems better. However, boot is a tad slower. 

Anyone know if the recent fix for ext4 really makes it slower than ext3? I'd really like to go back to ext4 if I know its solid.

---

