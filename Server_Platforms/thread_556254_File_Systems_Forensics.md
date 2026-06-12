---
title: "File Systems Forensics"
date: 2007-09-21
forum: Server Platforms
---

### Post by Nullack on 2007-09-21
One of the reasons why I am ditching Vista is the transactional NTFS that keeps records of when users have accessed files and so on.

Do any of the Ubuntu file systems keep records of file access that could be used in court or some other dispute situation?

If so, is it possible to wipe this for privacy reasons in a secure fashion?

---

### Post by twistedtwig on 2007-09-21
curious why some one would want to do that

---

### Post by DMills on 2007-09-21
By default all posix file systems keep a couple of time stamps for each file:

mtime - the time the file was last modified.
ctime - the time the file was created.
atime - the last access time. 

You can turn atime updates off for some or all filesystems by adding the noatime option to the options in /etc/fstab (Not do not make a mistake here, you can make the box unbootable easily). 
Google for noatime for details on how to do this.

Turning noatime on does improve FS performance (no need to write for every read), but can break a few things like some mail notifiers and the like (Normally minor). 

There are also fairly extensive system logs under /var/log for all sorts of useful administrivia.

All this is highly configurable. 

HTH.

Regards, Dan.

---

### Post by MJN on 2007-09-21
> **Nullack said:**
> One of the reasons why I am ditching Vista is the transactional NTFS that keeps records of when users have accessed files and so on.

Do any of the Ubuntu file systems keep records of file access that could be used in court or some other dispute situation?

If so, is it possible to wipe this for privacy reasons in a secure fashion?

I think the premise for your question is flawed - I would be very surprised if such access times could be relied upon in the circumstances you describe.

As Dan says, Ubuntu does exactly the same (atime mounts by default), but again it is wide open to plausible deniability. Incidentally, there has been much discussion recently (with Linus Torvalds involved) about the use of atime and the pros, or rather cons of it (from a performance perspective) so you might wish to consider disabling it anyway.

If this is the only reason you're ditching Vista (I can suggest some others if you need them! ;)) then check out [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/fsutil_behavior.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/fsutil_behavior.mspx?mfr=true) (an XP page but applicable to both) where you can find out how to disable this access timestamping - note the caveat (which is relevant for the noatime mount option in Linux) about the potential effect on backup programs which may use it to determine what to do with a file (e.g. archive it if hasn't been accessed for a year). From what I gather, I think it may be disabled by default in Vista anyway...?

Mathew

---

### Post by Nullack on 2007-09-22
Thanks guys - very good responces.

I am ditching Vista for a number of reasons beyond this. I am having alot of problems, but I am so committed I have even gone to the lengths of removing my ati video card and buying an nvidia one (simply was not able to resolve the ati driver failing to load regardless of what I did). I also bought Ubuntu unleashed second edition. Device management seems so much harder as things seem to silently fail and atleast to me (ignortantly) it seems harder to figure out what driver revisions are being used by what and generally diagnose the whole thing.

I suspect Im going to need a better book than this one for more detailed insights into hardening Ubuntu. Im looking forward to Gutsy with apparmor, but I also want to harden my systems from actual physical access as well with encryption and really tighten it all up.

---

### Post by tr333 on 2007-09-23
> **Nullack said:**
> I have even gone to the lengths of removing my ati video card and buying an nvidia one (simply was not able to resolve the ati driver failing to load regardless of what I did).

AMD just recently released the specs to their latest cards, so ATI drivers might even start to outperform NVIDIA drivers in the near future. (note the word "future"; it's not here yet).

---

