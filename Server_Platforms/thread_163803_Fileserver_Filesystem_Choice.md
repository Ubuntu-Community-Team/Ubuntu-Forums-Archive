---
title: "Fileserver Filesystem Choice"
date: 2006-04-21
forum: Server Platforms
---

### Post by hachre on 2006-04-21
I'm planning to built a filesserver with SATA2 Disks, doing Linux Software Raid5 on 8 Disks spanning more than 2TB.

Now my question to you guys is: Which Filesytem would you prefer?

I need my new array to be stable. Also it needs to recover quickly and with no filesystem corruptions from an improper shutdown. It should handle "big" files well (2MB+, 600MB+, sometimes 2GB+). It doesn't really need to be efficient with small files (<2MB) (not space, nor performance).

Which filesystem do you think is up for the job?

- XFS
- Reiser4
- ReiserFS
- ext3

I meanwhile learned that for some JFS is the fs of choice... I can't add it to the poll, sorry - so please just post if you'd like to vote for JFS

---

### Post by colo on 2006-04-21
ext3 - stable, sturdy, tried & true. Tuneable for larger files (-T largefile for example, manpage for more examples of preset block-sizes), hashed dir indexes if you like to have them.

I'm regaulry using reiser3 for filesystems filles to the brim with rather unimportant data in many small files (mind the notail-option), /usr/portage in Gentoo, for example.

---

### Post by brentoboy on 2006-04-21
I agree.
There is a reason it is default.  People trust it.
My server uses ext3

---

### Post by hachre on 2006-04-22
I can't really afford the lengthy filechecks ext3 likes to do every 20 mounts or 30 days... On a 2TB+ disk they take more than 30 hours afaik.

---

### Post by fdoving on 2006-04-22
I've used XFS with success on big fileservers. I've only had good experience with it.

- Frode

---

### Post by Keidash on 2006-04-23
This article might be interesting for you.

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

---

### Post by colo on 2006-04-23
[QUOTE=hachre]I can't really afford the lengthy filechecks ext3 likes to do every 20 mounts or 30 days... On a 2TB+ disk they take more than 30 hours afaik.[/QUOTE]


You can use tune2fs to fine-tune and adapt the filesystem's options to better fit your needs. Of course, you can also choose not to run "mandatory" fscks on your fs based on time or mountcount at all.

I've read the benchmark-article on debian-administration.org earlier today, and would not give too much about it, since nothing has been done to optimize the filesystem's characteristics for the task needed - which is very well possible in reality. There's also been a comparison on the web I've seen a few months ago (I'm to lazy to google for it right now, sorry) where ext3 beats the pants off of all its competitors, including, but not limited to reiser4.

I still starkly suggest ext3.

---

### Post by hachre on 2006-04-23
[QUOTE=Keidash]This article might be interesting for you.

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)[/QUOTE]

Thanks!

---

### Post by hachre on 2006-04-23
[QUOTE=colo]You can use tune2fs to fine-tune and adapt the filesystem's options to better fit your needs. Of course, you can also choose not to run "mandatory" fscks on your fs based on time or mountcount at all.

I've read the benchmark-article on debian-administration.org earlier today, and would not give too much about it, since nothing has been done to optimize the filesystem's characteristics for the task needed - which is very well possible in reality. There's also been a comparison on the web I've seen a few months ago (I'm to lazy to google for it right now, sorry) where ext3 beats the pants off of all its competitors, including, but not limited to reiser4.

I still starkly suggest ext3.[/QUOTE]

I'm not confident that ext3 can survive for a long time when you disable it's filesystem checks... I've had alot of problems with ext3 in the past and I ended up checking the filesystem for hours and hours... A few times I lost all data - just because I had a corrupted filesystem after mount and changed it too much before the next fsck...

---

### Post by LordHunter317 on 2006-04-23
[QUOTE=hachre]just because I had a corrupted filesystem after mount and changed it too much before the next fsck...[/QUOTE]That umm, makes no sense.

Ext3 has had some minor bugs where the journal replayes wouldn't yield a 100% consistent filesystem in the past, but I believe they're all fixed now.  None of them were ever truly serious.

---

### Post by colo on 2006-04-23
The only reason for this to happen is defective hardware.

---

### Post by LordHunter317 on 2006-04-23
No, bugs in the EXT3 journaling driver will cause an inconsistent filesystem on replay.  Such bugs have existed in the past.

---

### Post by hachre on 2006-04-24
[QUOTE=LordHunter317]No, bugs in the EXT3 journaling driver will cause an inconsistent filesystem on replay.  Such bugs have existed in the past.[/QUOTE]

I guess this was what had happened to me back then...

---

### Post by ronzo on 2008-02-29
I've XFS up'n'runnin on a 1.5 TB fileserver for approx. 2 years now without a single problem...

---

### Post by astrotech226 on 2008-02-29
I use ext3 now.  I've used xfs in the past and have great luck and bad luck.  Great luck on servers.  But it has done some really weird stuff to me on personal systems that are rebooted on a regular basis.

I wouldn't have much of a problem using xfs on a system that is built and designed to run for hundreds of days on end.  I mean redundant power supplies, clean power, etc...  But I have that now and still chose ext3 :)

---

### Post by Brazen on 2008-02-29
> **Keidash said:**
> This article might be interesting for you.

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

It left out the "maintainer is in jail" benchmark.

---

