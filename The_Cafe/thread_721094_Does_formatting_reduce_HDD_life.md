---
title: "Does formatting reduce HDD life?"
date: 2008-03-11
forum: The Cafe
---

### Post by LittleLORDevil on 2008-03-11
Here is a question that I have been wondering.  Does formatting a HDD make the life of it decrease?  To me it seems like it wouldn't because it's just a read and write sequence but I have heard that it does from other perspectives.  Any ideas?

---

### Post by thisiam on 2008-03-11
i would think so. its running and could fail at anytime.

---

### Post by LittleLORDevil on 2008-03-11
> **thisiam said:**
> i would think so. its running and could fail at anytime. How would that reduce life? Hardware could fail at any given time. I am talking about normal life.

---

### Post by thisiam on 2008-03-11
well when you are formatting the drive you would be writing to the disks wouldn't you? wear and tear right.

---

### Post by LittleLORDevil on 2008-03-11
> **thisiam said:**
> well when you are formatting the drive you would be writing to the disks wouldn't you? wear and tear right.  Is formatting any more than just a read and write, or is it more intense than that?

---

### Post by thisiam on 2008-03-11
pretty much.
[http://en.wikipedia.org/wiki/File_format](http://en.wikipedia.org/wiki/File_format)

---

### Post by jordanmthomas on 2008-03-11
I don't think it's too hard on a drive.  Formatting takes all of 10 seconds.  
I'm **definitely** no master on the subject, but I believe all formatting is is altering the partition table, setting up special nodes and creating a journal (or a FAT, etc., whatever the filesystem needs).  This seems less strenuous than a lot of things I put my drive through.

---

### Post by Jim! on 2008-03-11
I would doubt it but I guess it's always possibe, if it does reduce HDD life im sure its not much kind of like how they say 1 puff of a cigarette is 5 seconds off your life maybe it's the dame with HDDs, one format is 5 seconds off your HDDs life.. Yea Yea I know stupid right?

---

### Post by pbpersson on 2008-03-11
The more you beat up on a hard drive, the sooner it will fail.

However, a format only takes what......20 minutes at most?  Well.....that is NTFS.....I know EXT3 is way faster.

If you really want to beat up a hard drive, load it up with movies and then sign up subscribers to view your movies - dozens of them simultaneously 24 hours a day.

Maybe then instead of lasting 10 years it will only last 6.

Doing a quick format is less intensive than many other operations.

Now.....if for some reason you setup your system to continuously format the same drive for several years......that would be a problem  ;)

---

### Post by SomeGuyDude on 2008-03-11
I was wondering that myself. I tend to break my system terribly or muck around with Synaptic too much and then do a fresh install because it's easier. Glad to know I'm not hurting it too much.

---

### Post by &amp;)ky#)^ on 2008-03-11
Formatting doesn't hurt the life of a hard drive any more than writing a file to one does.  If you do a complete format that includes wiping or obsucating previous data on the hard drive, that will cause a little more wear on it, but only because there's more writing involved.

---

### Post by blueturtl on 2008-03-11
AFAIK formatting does absolutely nothing whatsoever to the disk in terms of life.

Some have suggested more wear and tear but you have to remember that since all that really changes are the magnetic markers on the disk's surface there really isn't anything that would wear. Maybe the motors of the read/write heads?

Also most common format operations do not actually write the entire disk, they just mark the file table empty without actually touching any of the data on the disk. That's why files can sometimes be succesfully recovered or 'undeleted' after the entire disk has been wiped.

Even if the entire disk is "zeroed" aka the format utility actually does write the disk a time or two there have been studies (I think done by Seagate) that say read/write operations actually prolong disk life because over time the magnetic traces on disk surfaces tend to weaken a bit. Reading/writing rarely used areas of the disk re-enhances the platters magnetic ability. I'd quote a link but I don't have it on me right now.

---

