---
title: "advice requested on cleanup of accumulated one-off backups"
date: 2015-08-15
forum: Server Platforms
---

### Post by MakOwner on 2015-08-15
This is a bit embarrassing to ask, because I *know* better than to do the very thing I have allowed to happen in my own personal space - I have accumulated a number of backups of various bits and pieces of various bits of cruft -- On my working laptops I usually carry around critical stuff, and over the years this has grown. There have been restarts on accumulation of data between employers, etc... so - I have accumulated many GBs of quite a bit of duplicated content, from structures backup up under different host or machine names, and even various points in time of the same data.
(Think large level 0 backups immediately prior to some large evolution -- just in case - but never cleaned up.)  

The one common thing is that at present everything is stored in EXT4 filespace, generally accessible via NFS and I generally only work from linux so file system compatibility isn't an issue for using the same linux server I have the data on now as the destination.
The directory structures that hold the data are setup with /hostame_dateofbackup/ and then another full copy.  

What I want to do is move all of this data into a structure that I can then use rsnapshot to continue backups.

Are there any easy and painless ways to do that?

Any other more painless ways to accomplish the same end?

---

### Post by TheFu on 2015-08-16
> **MakOwner said:**
> 

Are there any easy and painless ways to do that?

Any other more painless ways to accomplish the same end?

No. No. 
It sucks and almost everyone has the same issue. In the end, I decided a $100 for a new HDD to move everything onto was cheaper and more practical than spending months trying to clean up old files. The old HDDs are used as backup storage to the new HDD. After the first time this happened, I quadrupled my efforts to ensure it never happened again by being vigilant in my file storage efforts. I have a system-of-record for things I care about and anything that isn't on those systems and isn't waiting to be processed into the correct location, doesn't matter.  Right now, I have a few thousand photos/videos on the netbook to process into the system-of-record from recent overseas trips.

You can try to clean up duplicate files, if you like. There are tools for it, **fdup** and others and they do find the files. OTOH, selecting which to remove when there are 5 copies is harder. Newer isn't always better. Larger isn't always better and if they are stored on different file systems, sometimes there is slightly different round-off differences in byte counts.

It isn't easy, but I'd rather eat the elephant over years and not be forced to choke on it in a week or two.

And for the last question, probably not.  rsnapshot has some uses. I'm a convert from that to rdiff-backup. The issue with hardlink-based backup versions is that complete file permission versions are not maintained. That metadata could be important.  Backups without versioning aren't really that useful for files that change all the time and for files that never change, a simple rsync mirror is sufficient, IMHO.
 
Regardless, use whatever tool that works for your needs. What works for you isn't necessarily what works for me or anyone else.

Now I need to spend a few hours processing those photos. ;(

---

### Post by tgalati4 on 2015-08-16
As far as data organization, I find the "Rule of 12" helps.  Move your data into no more than 12 folders.  You can create subfolders, but again no more than 12.  With 3 levels of folders, you have 1728 categories or projects.  It makes backups easier because you can add daily backup-scripts to only the folders that have active projects going.

Whatever method you end up choosing, the 3-2-1 strategy also helps.  3 copies of important files on 2 different physical media with 1 copy offsite.

---

