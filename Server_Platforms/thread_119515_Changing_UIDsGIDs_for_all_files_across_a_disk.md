---
title: "Changing UIDs/GIDs for all files across a disk?"
date: 2006-01-19
forum: Server Platforms
---

### Post by MJN on 2006-01-19
Not sure if this is the right sub-forum, but I am talking about a backup disk residing in my server... ;)

My problem is this: I recently migrated my server from Red Hat to Kubuntu and have an issue regarding the consequences of these distros using different strategies for user UIDs/GIDs. In Red Hat these start at 500, whereas ofcourse in (K)ubuntu (asper Debian policy) they start at 1000.

I have a second hdd - with an ext3 filesystem - which serves simply as a backup disc. When this is mounted under (K)ubuntu the file/directory ownerhips are being displayed numerically (i.e. 500, 501 ...) because there is no mapping for these in my passwd/group files. The consequence of this is that the users cannot access 'their' files on the backup disc because of this mismatch.

Of course, I could change the 'new' UIDs/GIDs to be the same as the old ones however I don't know what the effect of this on current files will be and don't really want to stray from the Debian stategy with regards to numbering.

My question is thus is it possible for me to 'batch convert' the ownership of the backup files to align with the new numbering e.g. change 501 to 1002, 502 to 1006 etc?

Mathew

---

### Post by lcg on 2006-01-19
[QUOTE=MJN][...]

My question is thus is it possible for me to 'batch convert' the ownership of the backup files to align with the new numbering e.g. change 501 to 1002, 502 to 1006 etc?[/QUOTE]
Yes, it is:
```
cd <mount point of your backup>
find -user 501 -exec ls -l "{}" ";"
```

Verify if these are in fact the files of user 1002, then:
```
find -user 501 -exec chown 1002 "{}" ";"
```

Then the same for user 502:
```
find -user 502 -exec chown 1006 "{}" ";"
```

And so on.

But beware of problems in the above code; I have not tried it! ;)

HTH,
Lars

---

### Post by MJN on 2006-01-20
That's great Lars - I'll look into that and give it a go.

I'm relatively new to Linux and am still being amazed how the concatenation and piping of simple commands can achieve pretty much anything you want to do... Unfortunately I'm not quite in tune with putting this theory into practice though!

Thanks again,

Mathew

---

### Post by MJN on 2006-01-20
Update...

Worked superbly, many thanks Lars.

I must say however, I almost passed out from holding my breath whilst waiting for it to trawl the 65GB worth of backups... ;) 

Thanks again,

Mathew

---

### Post by LordHunter317 on 2006-01-20
It would have gone significantly faster if you had done:```
find -user 501 -print0 | xargs -0 chown user
```-exec to find should only be used when you need something xargs cannot provide.  For most operations, that's not the case.

---

### Post by MJN on 2006-01-20
Now you tell me! ;) 

Thanks for that though - will remember for next time.

Mathew

---

