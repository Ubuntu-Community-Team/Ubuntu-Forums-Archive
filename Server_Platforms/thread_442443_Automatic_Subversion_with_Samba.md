---
title: "Automatic Subversion with Samba"
date: 2007-05-13
forum: Server Platforms
---

### Post by cryptohash on 2007-05-13
I am currently setting up a RAID 50 NAS (which is no problem), but I figure, for even more protection from data loss, why not setup subversion for use with samba?  If it's possible.

What I am talking about is transparently using subversion for when users access the samba shares.  So when they resave something to the network share, subversion is automatically version controlling it.  I don't want the user to fool around with repositories and merging and all that sort of stuff.  I want it to be entirely transparent.

Any ideas?

---

### Post by Frosty Cold Drink on 2007-05-13
Oddly I just wrote something that shows one method to accomplish this.

[http://askcolddrink.blogspot.com/2007/05/silhouette-clone-part-1.html](http://askcolddrink.blogspot.com/2007/05/silhouette-clone-part-1.html)

Make sure you check for parts 2 and 3 as well. My own personal scritps are a bit better but not published (yet).

---

### Post by craigp84 on 2007-05-14
There's faster and easier ways to do this. There's a few reason's i wouldn't use this SVN approach in production, but highest among those is "what happens when it fails?" - this could cock up majorly and do it quietly, you'd really need to consider some serious sanity checking and alerting around that cron job.

How do you restore files from this? You'll need to login, figure out the version you want to restore (not easy since the user will have to be involved to find the right version; can they read a (binary) diff of a powerpoint presentation? can you?), restore it (multiple times in search of the correct version), then faff around with the versioning @ next commit.

As above, now this is the killer, you have to be involved in any restores. What if i'm not around and my user needs the file restored *now* - i don't fancy handholding someone through this procedure over the phone.

Save yourself some grief, "sudo apt-get install rsnapshot" then export the (read-only) snapshots via samba. This is p1ss easy to explain to a user, and they can access their own backups.

Long term the rsnapshot approach requires *way* less hands on admin (it's fire and forget really), and also space requirements don't grow with time.

I know where my money goes on the real world practicality stakes.

Hope this helps,

-c

---

### Post by Frosty Cold Drink on 2007-05-14
First, I would never recomend using those scripts as-is. They are for illustration only. (Mine are much better :)

If you poke through parts 2 and 3, timestamped directories are saved, so users can browse the data as it looked at a certian point in time and copy out the files themselves.

Either way, I really wouldn't recoomend that solution unless there is something about an RCS that you need (I do, most don't.) It would seem to me that it would be a little though to "pick up" an rsnapshot backup and drop it in a new location if you felt like it. rdiff-backup was recomended as another alternative.

---

### Post by elst on 2007-05-14
IIRC, the (free) Subversion book talks about how to use Subversion as a store for WebDAV shared directories, with automatic commits triggered when users save changes to files, but I'm not sure that I'd trust the WebDAV clients in Windows enough to actually try to implement it.

---

### Post by Frosty Cold Drink on 2007-05-14
> **elst said:**
> IIRC, the (free) Subversion book talks about how to use Subversion as a store for WebDAV shared directories, with automatic commits triggered when users save changes to files, but I'm not sure that I'd trust the WebDAV clients in Windows enough to actually try to implement it.

The problem with this is that when overwriting a file many applications will move the existing file, write the new file, then delete the old one. The problem with this is that Subversion recognizes the file when written as a new file, and doesn't store things efficiently. At least this was the case when I last checked.

---

### Post by elst on 2007-05-14
> **Frosty Cold Drink said:**
> The problem with this is that when overwriting a file many applications will move the existing file, write the new file, then delete the old one. The problem with this is that Subversion recognizes the file when written as a new file, and doesn't store things efficiently. At least this was the case when I last checked.

Hmm, I just read your blog entry and looked at some Microsoft documentation on Volume Shadow Copy. We need smarter software.

---

### Post by craigp84 on 2007-05-14
Volume shadow copy is not very good at all. You are quite correct that they need better software.

Thankfully in linux / ubuntu there are better options - you just have to ignore all this subversion / cvs repo jibber jabber plaguing the forums right now.

-c

---

### Post by Frosty Cold Drink on 2007-05-14
> **elst said:**
> Hmm, I just read your blog entry and looked at some Microsoft documentation on Volume Shadow Copy. We need smarter software.

Really I just want to see how this goes: [http://www.ext3cow.com/](http://www.ext3cow.com/)

---

### Post by cprofitt on 2007-07-02
> **craigp84 said:**
> Volume shadow copy is not very good at all. You are quite correct that they need better software.

Thankfully in linux / ubuntu there are better options - you just have to ignore all this subversion / cvs repo jibber jabber plaguing the forums right now.

-c

Heh? Volume Shadow Copy not that good?

What are the better options in Linux?

---

### Post by Brazen on 2007-07-02
Shadow Copy is a much better solution to this.  Check out the shadow_vol module in Samba and then use the Previous Versions client on your Windows clients.  You'll have to set up LVM and write scripts to create snapshots and then link them to the correct place for Samba to use.  It's really pretty easy and there is documentation out on the web and examples of scripts for the snapshots.  These are time based snapshots, so we take snapshots hourly, daily, weekly, and monthly, for instance.

As someone else said, a version-based setup is just not a good idea for this.  For instance, it's easy for a user to say "the file was good last wednesday" and then restore a time based snapshot just before last wednesday than it is for a user to say "my file was good before the 257th time I saved it" and restore to the 256th version.

With the Previous Versions client users can even restore their files on their own.  We have educated the users a few times on how to do this, but we still get calls to restore files because people forget.  It's it incredibly easy though.  A few clicks through an incredibily easy interface and their file or folder is back immediately.  Much, much better than having to bring in our offsite backup tapes and restore from those.

---

### Post by craigp84 on 2007-07-02
> You'll have to set up LVM and write scripts to create snapshots and then link them to the correct place for Samba to use.

> It's really pretty easy

Sounds it. ;-)

```
apt-get install rsnapshot
```

Job done. What's better than the buggy volume shadow copy client? Not having to install a client! What's better than volume shadow copy? Lots, but see apt-cache show rsnapshot for starters.

-c

---

### Post by Frosty Cold Drink on 2007-07-02
Correct me if I'm wrong, but since rsnapshot relies heavily on hard links, versioned backups are pretty much stuck on the initial target filesystem. That sucks. It is *really* nice to take 100% of my backup data and move it elsewhere just my moving a directory.

rdiff-backup shouldn't have this problem, since it does straight copies and stores backwards diffs.

I'm curious as to how many of you RCS for backup haters have tried it. I don't mean fudging around for a bit, I mean attemption to provide a solid and complete backup system with the foolproof point-in-time access to data novice users need. I've done it, and my backup setup is pretty damn solid...

```
tachikoma:~ chris$ svn list `cat ~/Backup/repository`/
head/
snapshots/
tachikoma:~ chris$ svn list `cat ~/Backup/repository`/snapshots/
2007-05-09 16:48:13/
2007-05-22 21:20:01/
2007-05-27 02:40:01/
2007-06-03 00:00:09/
2007-06-10 00:00:00/
2007-06-17 01:20:01/
2007-06-24 23:20:03/
2007-07-01 00:40:00/

```

---

### Post by cprofitt on 2007-07-02
> **craigp84 said:**
> Sounds it. ;-)

```
apt-get install rsnapshot
```

Job done. What's better than the buggy volume shadow copy client? Not having to install a client! What's better than volume shadow copy? Lots, but see apt-cache show rsnapshot for starters.

-c


I have not had issues with the Shadow Volume client... what issues have you had?

---

