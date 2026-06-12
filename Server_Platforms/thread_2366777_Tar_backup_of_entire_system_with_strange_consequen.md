---
title: "Tar backup of entire system with strange consequences"
date: 2017-07-21
forum: Server Platforms
---

### Post by electricjelly on 2017-07-21
Hello,

I recently tried to create a gzip tarball of my entire system using command
```
tar -zcfv /external/drive/foo.tar.gz --exclude=/external_drive /
```
This command seemed to take forever and after 24hrs of not completing, I killed the process, which deleted to tarball as well. Furthermore, it created a very large file 6GB+, simply named "v" in the parent directory of the external drive which when I cat into the file produced what seemed to be the same looking output as /dev/urandom but I'm only guessing it was the same. Furthermore, I started the tarball process on screen and that screen absolutely refuses to end, whether I use ```
pkill -f -SIGKILL screen
``` or  some other one none works. 

My question is, was all this created simply because i tried to backup a system onto a external drive instead of making it locally and them moving the created tarball or is there something I am not seeing, and is there a way to kill the screen process, that just refuses to end, or will i simply need a full system restart. also why was this "v" file created.

Thanks for taking the time to read this

---

### Post by TheFu on 2017-07-21
TL;DR - tar shouldn't be used for any data over about 500MB in size there are a number of reasons for this.  The tar you used will never complete because it included special files that generate output, unlimited.

[B]sudo tar -zvcf /external/drive/foo.tar.gz
[/B]
is closer - see how the 'f' is the last argument?  The next entry will be used as the output file. The command will still fail because it will include those device files that create output forever.  If you try to backup /dev/urandom .. you will get pseudo-random numbers forever.

In short, don't use tar (or any similar command like gtar, star, etc).  Use a modern backup tool for better results.  

If you want a write-once, image-like, backup, look at clonezilla or partimage.  If you want versioned backups (and you should), look to duplicity or rdiff-backup.  Of course, there are 50 other choices too.  Each has good points and bad points.  I've tried most backup tools and settled on rdiff-backup about 7 yrs ago.  Have needed to restore a few times over the years.  Last time was about 3 months ago when a 4TB disk failed in my media server. The failed disk was also holding the OS which made it a little more difficult.  Once the replacement disk arrived, I had a working system in about 30 minutes.  It took another 26 hrs to get all the data back because I was determined to start with the failing disk first, not just go to a backup.  

Generally, for my servers without much data, restores take about 30-45 minutes.

---

### Post by electricjelly on 2017-07-25
Thank you for your help, after what you said, i looked into the tag --one-file-system, which fixed the issue. However, looking into clonezilla and you other suggestions, led me to follow that the best way was to move away from Tarring and into duplicity, now i just need to look into how to automate those things and have it replace rsync backups possibly.

Thanks again

---

### Post by TheFu on 2017-07-25
Glad it helped.

Please mark the thread as "SOLVED" so help the community.

---

