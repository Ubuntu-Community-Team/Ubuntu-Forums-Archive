---
title: "LVM: Risks/alternatives?"
date: 2005-07-24
forum: Server Platforms
---

### Post by XoloX on 2005-07-24
Hi all! I've recently set-up a server for our LAN, primarily to serve files via Samba. Right now it's running Debian Sarge, but after my recent experiences with Ubuntu I'm seriously considering installing that. The reason I'm asking this question now is that I want to know where I stand *before* I install Ubuntu. Here's my current (problematic) setup regarding harddisks:```
hda1 -> 20GB, Contains OS, apps & libs
hdb1 -> 80GB, Main fileshare:
  Audio/
  Games/
  Software/
  Video -> Symlink to hdc1/Video
hdc1 -> 80GB, Video:
  Video/
    Movies/
    Comedy/
    Documentaries/
    Video-clips/
    Anime -> Symlink to hdd1/Anime
hdd1 -> 80 GB, Anime
  Anime/
    and/
    so/
    on/
```See my problem? If not: This setup is far from flexible. If I ever run out of space on on of the three 80GB disks, I'll have to create more directories and set-up symlinks from the main fileshare so the directories are accessible. After a while, I'm going to find myself in a 'symlink farm'. Coming from Windows land, these symlinks can be real live savers. However, their not exactly favorable to a clean disk/directory/file organisation.

Now I know about LVM, that it's suppost to solve this exact problem. I also know about RAID, which could solve it aswell. But what I also know is that I do not want to lose ALL of my data when one of the three disks fails.

I may have misunderstood LVM's method, but far as I've understood, it creates *n* MB blocks (4MB on default I think) and spreads your files over those blocks. It might not mean one corrupt disk ruins everything, but this stil seems like a risk to me.

Am I correct here, or simply worrying to much?

If I am correct and it is indeed a risk, does anyone know of a technology that transparently shows the three disks as one, or at least let's me use it as such, without fragmenting the files?

Thanks in advance for your time!

 - Peter Odding

---

### Post by dataw0lf on 2005-07-26
Sounds like you'd be happy with a RAID.  If you've got the money, an external IDE to SCSI RAID cage might be just the thing you want.  I just purchased one for my personal use : [http://www.pc-pitstop.com/das/arenadfII.asp](http://www.pc-pitstop.com/das/arenadfII.asp) and it's pretty damn cool.  I got 8 250 gig drives in there, and it's incredibly easy to setup in *nix (just mount it as SCSI).

---

### Post by LordHunter317 on 2005-07-26
[QUOTE=XoloX]Now I know about LVM, that it's suppost to solve this exact problem.[/quote]It can, yes.

> But what I also know is that I do not want to lose ALL of my data when one of the three disks fails.Then you want RAID.  LVM doesn't guarantee redundancy.  

> I may have misunderstood LVM's method, but far as I've understood, it creates *n* MB blocks (4MB on default I think) and spreads your files over those blocks.Well, no, not quite.  LVM stores data in phsyical extents (or blocks, or stripes) 4MB large.  Just like your disk stores data in units no smaller than 512 bytes, and your filesystem generally works in blocks no smaller than 2048 or 4096 byes.  Aside: the extent side can be changed.

You are correct in that normally, you're not assured where these blocks ends up on the physical volumes in a volume group.  So if I have two physical volumes that hold my logical volume.  Block 1 could end up on the first disk, and block 2 on the second.

You can force certain allocation policies, though the support isn't totally mature.  The most important one you can enforce right now is continuous: which esentially makes a logical volume like a traditional disk partition: it occupies a fixed space on a fixed disk.  But that wouldn't solve your problem.

In realitly, LVM uses a concept called spanning:  it uses the first volume until it's full, then the second, then the third.

> It might not mean one corrupt disk ruins everything, but this stil seems like a risk to me.It means yes, if you lose one disk, you lose everything in whatever volume groups that disk was particpating in.

> If I am correct and it is indeed a risk, does anyone know of a technology that transparently shows the three disks as one, or at least let's me use it as such, without fragmenting the files?You could use RAID, software or hardware.

Note that you can run LVM on top of a RAID array, and getthe useful benefits of LVM and the data integrity of RAID.

---

### Post by XoloX on 2005-07-27
Thanks for your replies. I've been doing some reading on RAID myself, and have come to the conclusion that RAID 5 is probably my best option: I want to 'merge' several physical disks, but am worried about one of the disks failing and me losing all of my data. *If* I've read [the Wikipedia article](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks) correctly, RAID 5 will spread the data across all disks while distributing the parity blocks/data (whatever they're called), and when one disk fails, it can rebuild that disk from the parity blocks (as long as *one disk* failed, oh well, can't have everything :)). It also gives me the benefit of higher performance on read operations. Which suits me fine, since the RAID will be used as network storage, which means it will be dealing with read operations mostly. So ehm, RAID 5 it is? Or did I miss something?

> Note that you can run LVM on top of a RAID array, and getthe useful benefits of LVM and the data integrity of RAID.
The most important benefit of LVM, to me, would be that it's possible to add storage later-on. But RAID, far as I know, doesn't allow this. So do you mean I can use LVM to 'merge' several RAID's? Because I'm certain it won't come to that, I don't have the money :).

And about layering several of these solutions (RAID, LVM): Won't this slow down the system?

One last thing, I've read that software RAID actually has some benefits. Like outperforming a hardware based RAID :-k? Also, from the Wikipedia article:

> In rare cases hardware controllers have become faulty, which can result in data loss. This implies software RAID is a slightly more reliable and safer option.
Not that I'm particularly worried about a hardware RAID controller failing on me anymore than my RAM or CPU failing me, but still. However, the article leaves the conclusion up to the reader ("implies"). What do you guys think about this?

Thanks for your help/time so far!

- Peter

---

### Post by LordHunter317 on 2005-07-27
> **XoloX] So ehm, RAID 5 it is? Or did I miss something?[/quote]Nothing but implementation details  said:**
> The most important benefit of LVM, to me, would be that it's possible to add storage later-on.It also supports dynamic growing of existing volumes.  So if you only allocate 2GB to / and need more, you can add more space to / as long as you have physical space free.

>  But RAID, far as I know, doesn't allow this.HW RAID controllers allow  for this.  Linux MD (Software) RAID can do it, but the support is very experimental.  I wouldn't do it without taking a full backup and being prepared to rebuild the array from scratch.

>  So do you mean I can use LVM to 'merge' several RAID's? Because I'm certain it won't come to that, I don't have the money :).Yes, but it has the same issues that LVM on a span of single disks has: if one of the arrays has an unrecoverable failure (e.g., two disks die), you'll lose everything.

> And about layering several of these solutions (RAID, LVM): Won't this slow down the system?Not really.  LVM doesn't add significant overhead for regular I/O operations.  It just sits in between the VFS and the physical disks, directing where the blocks go.  Which isn't a lot of overhead.

> One last thing, I've read that software RAID actually has some benefits. Like outperforming a hardware based RAID :-k?It's very rare software RAID actually outperforms HW RAID.

>  Also, from the Wikipedia article:That's just plain wrong, think about it.  The software RAID code could have a bug too, and you can still have hardware failures that will kill the array outright.

> However, the article leaves the conclusion up to the reader ("implies"). What do you guys think about this?They're spreading misinformation, though I don't think it's on purpose.

---

### Post by XoloX on 2005-07-27
> **LordHunter317]Nothing but implementation details  said:**
> 
I'm not planning on running / from RAID just yet. It's a nice option regarding redundancy, but I'm new to RAID and have already found a sh*tload of threads about problems with running / from RAID. Also, I plan on running software RAID since ATM I don't have the money for a hardware RAID controller. About partitioning each disk individually: Is there any FS that works specifically well with RAID? Or is it just a matter of opinion & situation?
> It also supports dynamic growing of existing volumes.  So if you only allocate 2GB to / and need more, you can add more space to / as long as you have physical space free.
Hmm, that does allow for a great deal of flexibility. But I think for now I'll go for a RAID only solution.
[quote]Not really.  LVM doesn't add significant overhead for regular I/O operations.  It just sits in between the VFS and the physical disks, directing where the blocks go.  Which isn't a lot of overhead.
Good to know :)
> It's very rare software RAID actually outperforms HW RAID.
That's what I thought. Seemed illogical that a software solution would outperform a hardware solution. ATM I can't find the source, but I'm sure someone, somewhere, mentioned it.
> 
That's just plain wrong, think about it.  The software RAID code could have a bug too, and you can still have hardware failures that will kill the array outright.
I know, that's why I named it. The only reason I didn't dismiss it in a second is because it was from Wikipedia, and they generally have good quality articles.

Thanks for your help, it's greatly appreciated :)

---

