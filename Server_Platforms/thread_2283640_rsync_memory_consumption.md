---
title: "rsync memory consumption"
date: 2015-06-23
forum: Server Platforms
---

### Post by davidricq87 on 2015-06-23
Hi,

I use rsync to backup file from a server.
I just noticed than rsync use more than 10% to backup files. And server runs out of memory.
I use these parameters : "-aHh --stats --compress --delete"

I would like to know if it's possible to "manage" the memory use by rsync to decreased memory usage (actually 4GB).

---

### Post by SeijiSensei on 2015-06-23
Do you need to use --compress?  Try running without compression and see if your usage figures differ.

I find it unlikely that rsync alone is causing your loss of memory on a 4GB machine.  Do you have a swap partition or swap file?  Are you running some other large applications?  I've run rsync on servers with as little as 256M and never had an out-of-memory condition.

---

### Post by papibe on 2015-06-23
Hi davidricq87.

What is the rsync version on both ends? Could you post the output of this command on both the source and destination machines?
```
rsync --version

swapon -s
```
Regards.

---

### Post by davidricq87 on 2015-06-24
Hi,
@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"): I will try to use without --compress. The server is use as web server with several websites. I'm pretty sure that rsync causing this because it begin when rsync start and stop when rsync end, I saw that throught zabbix monitoring tool.

@[**[COLOR=#C61919][B]papibe**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=774785"): Here is the result of rsync --version

```

rsync  version 3.0.9  protocol version 30
Copyright (C) 1996-2011 by Andrew Tridgell, Wayne Davison, and others.
Web site: http://rsync.samba.org/
Capabilities:
    64-bit files, 64-bit inums, 64-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.
```

and swapon -s :

```

Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       46873596        0       -1
```

There is no rsync "destination" because the server mount a remote directory throught cifs.

---

### Post by Habitual on 2015-06-24
I had also noticed rsync (to USB mounts ) to be a memory killer, so  I started using this in my local script.
```
ionice -c 3 rsync -avz  . /media/jj/internal/LM17/ --delete --exclude svn
```

Seems to help immensely here.

---

### Post by davidricq87 on 2015-06-25
Hi Habitual,
Did you see a significant change with ionice ?

---

### Post by papibe on 2015-06-25
Thanks.

As far as I know, the most common reason for rsync reaching an out of memory error is transferring huge number of files. Not the size of the files, but the total number of them. Both -H and --delete are options that increase even more the use of memory.

I would consider the possibility of splitting the rsync command in 2, or 3 commands so that the number of files handled by each new command would be reduced approximately  in half or a third.

By the way, make sure the Windows system behind the cifs supports hard links. I believe only a recent version of Windows would support it.

Hope that helps. Let us know how it goes.
Regards.

---

### Post by Habitual on 2015-06-25
> **davidricq87 said:**
> Hi Habitual,
Did you see a significant change with ionice ?

immensely.

---

### Post by davidricq87 on 2015-06-25
Hi,
Thanks for all the answers.

@[**[COLOR=#C61919][B]papibe**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=774785") Yeah you are right, I didn't think about to split the rsync. I have actually 522000 files transfered.

@[**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341") Another question about ionice ^^. I can imagine that a rsync with ionice is really slower. Did you noticed it ? If yes, how much it take with and without ionice (in your case) ?

---

### Post by Habitual on 2015-06-25
41,449 files.

to /media/jj/Internal rsync w\out ionice:
```
time rsync -avz  . /media/jj/internal/LM17/ --delete --exclude svn
sent 283,078,024 bytes  received 16,201 bytes  8,450,573.88 bytes/sec
total size is 72,251,814,659  speedup is 255.22

real    0m32.867s
```

to /media/jj/external with ionice:
```
time ionice -c 3 rsync -avz  . /media/jj/external/LM17/ --delete --exclude svn
sent 283,068,784 bytes  received 16,170 bytes  5,836,803.18 bytes/sec
total size is 72,251,848,543  speedup is 255.23

real    0m47.775s
```

a little slower.

free -tog showed no difference after using either one.

This may not be conclusive.

---

### Post by davidricq87 on 2015-06-26
Hi,

So, I will use ionice and split my rsync

---

### Post by sudodus on 2015-06-26
I removed your doublet posts.

Good luck with your future rsyncing :-)

---

### Post by davidricq87 on 2015-06-26
Hi sudodus,

Thanks :D

---

