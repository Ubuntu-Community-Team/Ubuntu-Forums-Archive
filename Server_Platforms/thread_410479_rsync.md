---
title: "rsync"
date: 2007-04-15
forum: Server Platforms
---

### Post by cocotu on 2007-04-15
I want to rsync some directories to an external HD.  This is the problem:

I want to rsync directories;

/dd
/tt
/ss
/pp

But I want to exclude:

/aa
/zz
/ee

I have my exclude file excluding these directories.  But the problem is that directory /dd contains a directory named /aa so I get message: "Excluding /dd because of pattern /aa"  So this means I'm not able to rsync the directory that I want /dd because it contains a directory /aa. how do i solve this problem?? Thanks

---

### Post by motin on 2007-04-15
> **cocotu said:**
> I want to rsync some directories to an external HD.  This is the problem:

I want to rsync directories;

/dd
/tt
/ss
/pp

But I want to exclude:

/aa
/zz
/ee

I have my exclude file excluding these directories.  But the problem is that directory /dd contains a directory named /aa so I get message: "Excluding /dd because of pattern /aa"  So this means I'm not able to rsync the directory that I want /dd because it contains a directory /aa. how do i solve this problem?? Thanks

Tried grsync? It will be easier to configure from there. 

I guess you should use some regular expression that only matches paths beginning with /aa, for example /^\/aa/

---

### Post by cocotu on 2007-04-15
so you are saying if I put  /^\/aa/ it will exclude /aa, but not /dd/aa/?  thanks..

---

### Post by MJN on 2007-04-16
Post the rsync command that you're using as this type of behaviour is often largely dictated by leading/trailing slashes.
 
Mathew

---

### Post by cocotu on 2007-04-16
rsync --exclude-from "/Users/admin/backup-excludes.txt" -avve /usr/bin/ssh /Volumes/DataHD/projects /Volumes/backupdisk/

---

### Post by MJN on 2007-04-16
And your backup-excludes.txt? (that effectively forms part of the rsync command)

Notwithstanding the actual contents of that file, you could use:

```

rsync --exclude-from "/Users/admin/backup-excludes.txt" -avve /usr/bin/ssh /Volumes/DataHD/projects /Volumes/backupdisk/

```with:

```

- /projects/aa

```in backup-excludes.txt.

Are you sure you had leading slashes in your excludes file?

Mathew

---

### Post by cocotu on 2007-04-16
/aa
/zz
/ee

yes leading slashes!

Should I place this: "- /projects/aa" in the exclude file?

---

### Post by MJN on 2007-04-16
I'm surprised anything was excluded! The leading slashes tell rsync to act from the root, and given you didn't/don't have a trailing slash on the source the root doesn't include 'project'.

And yes, put **- /projects/aa** into the excludes file.

If you run rsync with -n set then it'll do a dry run and will show you what would happen whilst you experiment with various slashes etc.

Mathew

---

### Post by cocotu on 2007-04-17
Is the '-' included?

[COLOR="Red"]-[/COLOR]/projects/aa
                  or is it just
/projects/aa

thanks I tested it with a test directory. I will let you know the outcome

---

### Post by MJN on 2007-04-17
The '-' is just shorthand for 'exclude' - I'm not sure if it's required given it's an exclude-from file (i.e. it might be assumed if omitted) but I'd include it for completeness as there are several other prefixes available (see the rsync manpage for those).

Mathew

---

### Post by cocotu on 2007-04-18
Can I do this by file date(creation date)? What I'm doing is backing up many directories, but I want to exclude directories created on the year 2005 and before.  Is this possible? thanks

---

### Post by cocotu on 2007-04-19
I was trying the previous command in a Mac os X server and it worked ok. Now I'm trying it in my Ubuntu machine and I get:

rgm@CheBK:~/testdir$ rsync --exclude-from "/home/rgm/testdir/exclude.txt" -avv /home/rgm/testdir /home/rgm/targetdir
building file list ...
done
delta-transmission disabled for local transfer or --whole-file
testdir/
testdir/exclude.txt
testdir/aa/
testdir/aa/bb/
testdir/bb/
testdir/cc/
testdir/dd/
total: matches=0  tag_hits=0  false_alarms=0 data=15

sent 270 bytes  received 78 bytes  696.00 bytes/sec
total size is 15  speedup is 0.04

Everything get copied! Why?

---

### Post by MJN on 2007-04-20
Again, what does your exclude file look like?

Mathew

---

### Post by cocotu on 2007-04-20
testdir/bb/
testdir/cc/
testdir/dd/
excludet
testing

---

### Post by MJN on 2007-04-20
Try exactly as I wrote:

```

- /testdir/bb
- /testdir/cc
- /testdir/dd

```i.e. '-' to start the line, leading slashes etc

Mathew

---

### Post by cocotu on 2007-04-20
Here at work using this Max os X server it works fine when I use that exclude file.  Very strange.  I will keep you inform. thanks

---

