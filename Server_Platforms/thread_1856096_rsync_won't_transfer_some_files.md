---
title: "rsync won't transfer some files"
date: 2011-10-07
forum: Server Platforms
---

### Post by jhuhmann on 2011-10-07
I'm doing an rsync -aHK from one 8.04 server to another 8.04 server as root over ssh, transferring about 60 gb.  I've found that it isn't transferring everything though. 

If I do a diff of the two folders I find that I'm missing 18000 files. 

Am I using the wrong arguments on rsync? Will files with certain permissions not transfer over rsync with ssh? 

The full scenario is I have an email server running zimbra.  I do an rsync of the live directory while email is up. Shut down zimbra, do a second rsync to get the changes and then start it back up. That one works fine. I get a functional backup with all the appropriate files intact.  The problem is happening when I do an rsync of the backup to a second server. I'm at a loss.  

Anyone have ideas of what I can look for?

---

### Post by jhuhmann on 2011-10-08
Did I post this thread in the wrong spot for it to be seen by the right people?

---

### Post by papibe on 2011-10-08
A few questions:

Are the machines' clocks well set?
The last rsync is from ext4 to ext4? or there's NTFS mixed in there?

Could you post the actual commands you are using?

Regards.

---

### Post by HermanAB on 2011-10-09
Howdy,

Try -v and -n to see what is going on.

Also try unison.

---

### Post by jhuhmann on 2011-10-10
I checked the time on both servers.  They are both set correctly. Both servers are using ext3, there is no ntfs anywhere in transfer.

The exact command I ran from within the directory I want to transfer is:

 rsync -aKH ./* [email]root@server.name.com[/email]:/opt/zimbra/

I don't know if doing a transfer with -v will be useful. It looks like there are about 700,000 files in the source folder. 

A thought I just had, probably wrong, but could I be causing the problem by using ./* instead of putting in a full path?

---

### Post by SeijiSensei on 2011-10-10
> **jhuhmann said:**
> rsync -aKH ./* [email]root@server.name.com[/email]:/opt/zimbra/

Try using just "." instead of "./*".

I find just using -a is sufficient.  Do you actually have hard links (-H)?  What purpose does (-K) serve?  It isn't especially clear from the rsync man page.

---

### Post by jhuhmann on 2011-10-10
I'm in the midst of trying another rsync will the full path instead of ./*  

Is using ./* redundant? Does it mean something different than . does?

---

### Post by a2j on 2011-10-10
I use this to backup entire proxy box
```
rsync -avz --progress /  hostname@lan.ip.address.here:~
```
it works great.

---

### Post by SeijiSensei on 2011-10-10
> **jhuhmann said:**
> I'm in the midst of trying another rsync will the full path instead of ./*  

Is using ./* redundant? Does it mean something different than . does?

Typing "ls ." shows me the current directory.  Typing "ls ./*" recurses through the subdirectories.  Since the "-a" switch to rsync invokes recursion automatically, I'm not sure that ./* adds anything.

Try running "rsync -avn ." and "rsync -avn ./*" from the same directory.  You'll see a list of the files that would be transferred.  Do they differ?

---

### Post by jhuhmann on 2011-10-10
> **SeijiSensei said:**
> 

I find just using -a is sufficient.  Do you actually have hard links (-H)?  What purpose does (-K) serve?  It isn't especially clear from the rsync man page.

I'm not doing -aHK because I have any particular insight into what it does, or a great deal of knowledge about what I'm doing.  I'm doing it mostly because the zimbra open source forums have almost everyone doing the same thing.  I'm operating loosely from [this]("http://wiki.zimbra.com/wiki/Open_Source_Edition_Backup_Procedure").  I can only assume that Zimbra is using hard links in however they do their setup.

---

### Post by jazzon on 2011-10-10
been studying mail servers myself all day.  Most use hard links ONLY WHILE UP, and do this instead of mv commands to reloacte mail between folders as it is processed.

As in get a mail,
save a mail,
execute a process on a mail that would end with it being moved,
hard link the mail in new location,
unlink the original mail.

These steps are used to avoid data loss and duplication during processing since with a copy command their are two isolated copies in existence for a brief moment, and if a usewr checks their mail at that moment, it gets moved again.  Now there are three copies, and only one will be deleted by the interrupted process.

So,
If your not running rsync while the server is in operation, no hard  link references exist.

Part of the mail protocol (don't remember which mail protocol though)

---

### Post by koenn on 2011-10-10
> **jhuhmann said:**
> 
Is using ./* redundant? Does it mean something different than . does?
couple of things

1-
with *, the *shell* will expand that to subdirs of and files in /, before rsync sees the options, so it differs from "." or "./". 
A trailing slash in the src is also relevant to rsync, so  "." and "./" are not identical.
Since they're fifferent commands, they might cause a different behaviour, although I don't know if that could account for 18000 files missing

You probably want  ./  


2-
are you sure your diff is accuratie ?

3- 
rsync has specific default behaviour and options for symlinks and extra mounted filesystems
If the "current dir" you work with has mount points for 'other file systems' such as extra disks or partitions, these defaults will come into play. 
Don't remember the details, but it's worth looking into.

4-
+1 to Herman's suggestion to run verbose and see what files get skipped (and what rsync complains about).
You 'll probably need to grep [Ee]rror or something if you're dealing wat that many files/.



-----
Edit
I might be wrong about 3- in that the default behaviour would be the scan files on extra filesystems and you'd need to specify an option to restrict rsync to 'one filesystem". 
Still, it's somthing to be aware of.

---

### Post by jhuhmann on 2011-10-10
Thank you for all the replies.  I ran it with the full path for the source directory doing away with ./* and using /storage/backup/sync/zimbra/ and it correctly transferred everything.  

Consider this solved!

---

### Post by jhuhmann on 2011-10-10
> **jazzon said:**
> been studying mail servers myself all day.  Most use hard links ONLY WHILE UP, and do this instead of mv commands to reloacte mail between folders as it is processed.

As in get a mail,
save a mail,
execute a process on a mail that would end with it being moved,
hard link the mail in new location,
unlink the original mail.

These steps are used to avoid data loss and duplication during processing since with a copy command their are two isolated copies in existence for a brief moment, and if a usewr checks their mail at that moment, it gets moved again.  Now there are three copies, and only one will be deleted by the interrupted process.

So,
If your not running rsync while the server is in operation, no hard  link references exist.

Part of the mail protocol (don't remember which mail protocol though)

This makes complete sense.  The scripts I was looking at are doing the initial backup while the server is active and then stopping it and rsyncing the changes.  I probably just need rsync -a.

Thanks!

---

