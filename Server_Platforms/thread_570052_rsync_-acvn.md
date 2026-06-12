---
title: "rsync -acvn"
date: 2007-10-07
forum: Server Platforms
---

### Post by petiejoe on 2007-10-07
I've been working on setting up a personal file server. I have two physical hard drives and I'm using one as a fully redundant backup of the other. I use "rsync -a /mnt/data/data/ /mnt/back/data" to keep the two in sync with each other, but I want to go a step further and periodically check if one or the other drive is corrupted (I'm particularly nervous about hardware failure). Originally I was going to keep a list of all the md5 or md4 hashes of each file, but I came across the -c (or --checksum) option which I think might do exactly what I'm looking for. The plan would be to run rsync -a on a regular basis (daily or hourly) and then rsync -acvn on a less frequent basis (probably weekly).

A breakdown of why I chose each of the flags:

rsync -a : typical archive rule, backs up everything from one location to another, keeps same privileges, etc.
rsync -c : do full check to make sure the two files are actually the same
rsync -v : I want output if it thinks two files are different (is one v going to be enough? I think that -vv gives me a bit too much info)
rsync -n : I don't actually want to copy any files - I'm doing that with the regular rsync. I just want an alert if something is broken.

So my question is whether "rsync -acvn" will alert me if either drive is corrupted because it will say that a lot of files need to be updated even though they shouldn't. Or if you've found something that works even better, I'm open to suggestions.

Thanks!

---

### Post by HermanAB on 2007-10-07
Well, it will only alert you if you actually sit and look at it.  This is a big problem in any IT system - how to determine whether the system integrity is maintained and there is no easy answer.

I suggest that you intersperse your file set with test files with known MD5 sums, then set up a cron job to check those sums and send you an email if a sum fails.

---

### Post by petiejoe on 2007-10-07
Sending myself an alert will be the next challenge, but it's a challenge I'd have to face if I were to set up test files as well. I'd probably dump the output to a file and just check the contents of the file periodically. Mostly I'm wondering if rsync -acvn will start getting false positives if one of the drives starts failing - it's a really hard thing to test, since I don't particularly want to trash one of my new hard drives just to see what happens.

Of course, this isn't going to be the end of my backup system - I'm also planning on buying a DVD burner and mailing the DVDs to a friend's house (in case of any natural disasters), but losing a month's worth of photos (I do digital photography) is a really painful experience I don't want to repeat.

---

### Post by HermanAB on 2007-10-07
Just mail the DVDs to yourself.  It could easily take a week to get back to you, by which time, you have the next backup and can toss the incoming one away...

---

### Post by gerbman on 2007-10-07
You might also want to use the "--delete" option, which removes files from the destination drive if you delete them from the source drive. Keeps thing tidy.

---

### Post by petiejoe on 2007-10-08
Call me paranoid, but I don't want to automatically delete anything. In fact, because my files should never change (Mostly digital pictures), I added --ignore-existing to the regular sync. Thanks for the suggestion, though - hopefully it's useful for someone else.

FWIW, here's what I think I've decided on. I haven't run any of these from a cron job yet, so if somebody else reads this, be sure to test them for yourself to make sure they work for you.

```
#daily datasync.sh
#don't want to overwrite anything on the backup drive - most of
#my files should not ever be edited. By using --ignore-existing, 
#I protect from the possibility of somebody corrupting my data 
#(e.g. virii). Files that I want to permanently delete 
#(crappy pictures) will have to be deleted from both 
#sources using a separate script.
rsync -a --ignore-existing /mnt/data/data/ /mnt/back/data
```




```
#weekly datacheck.sh
#make sure everything's up-to-date:
datasync.sh
#check if stuff is missing from back drive:
rsync -avn /mnt/data/data/ /mnt/back/data > ~/missingFilesOnBack.output
#check if stuff is missing from data drive:
rsync -avn /mnt/back/data/ /mnt/data/data > ~/missingFilesOnData.output
```


```
#monthly fulldatacheck.sh
#make sure everything's up-to-date:
datacheck.sh
#to check if drives still work:
rsync -acvn /mnt/data/data/ /mnt/back/data > ~/rsync-acvn.output
```

Of course, more suggestions from the masters is always appreciated.

---

### Post by MJN on 2007-10-08
Well, I'm no master but hopefully my 2p is still valid... Besides which, it sounds like you've got it pretty much nailed and understood.
 
Just a few comments:
 
It may be worth you considering the differences between a 'backup' and an 'archive', or at least some of the various interpretations of the terms. Your current 'backup' strategy is effectively giving you a live snapshot of the current system state and this is all well and good but, as you say, if the source corrupts badly then the automated backup procedure could end up replicating the problem into the backup. Hence, an 'archive' representing a known-good historical snapshot is definitely a good idea...
 
You've mentioned DVDs, which is as good a strategy as most, however the one thing I don't like is the mandraulic aspect. If your luck is anything like mine you can bet your *** that the moment you come to rely on it just happens to be the time you didn't burn the discs, or the post went missing, or the media failed etc. It could therefore be worth considering a more automated approach using the tools right in front of you - rsync and the Internet. It works extremely well as as backup tool over a network as not only does it keep the source/destination in sync but it does this by only transferring the files that changed, and indeed only those *parts* of the files that have changed (not to be confused with an incremental backup of course - it's just how it manages to keep the source and destination in sync). Hence it is very bandwidth friendly (at least as well as it can, and it also supports on-the-fly compression if required). It is secure too running over SSH. Find a mate who is in the same boat as you and you're sorted. Of course, depending on your bandwidth (upload especially as it usually asymmetrical) this may not work well - and the first sync with all however-many-GB can take a while! Priming the destination with a manual DVD copy can take the pain out of the first run.
 
My brother and I use rsync to backup our machines to each other (talk about 'offsite' - we're in different countries!) and as it's automated it runs every night quite happilly as a cron job and mails out a report for future reference. I still run a local backup (call me paranoid but I actually do two - one to an internal drive for immediate recovery and the other to a hidden external USB drive which also stores my security camera footage - after all if a burglar breaks in it's probably my PC that will be first to go!). Our remote backup is more trimmed down to the most important stuff (photos, docs, config files, and not the system as a whole).
 
The other comment was regarding your checksum comparison check (remember rsync always checksums a file after the transfer, but I know this isn't what you're after). I think you might be being over-paranoid, particularly given hard disk reliability and a suitable archive mechanism in place. However, that's not for me to say, but what I do suggest you looking at taking advantage of cron's automated mailing of any output from a cronjob. I see your current 'datacheck' cronjob redirects the output to a file - don't. Just leave it be (without the redirect, and you might need to drop the -v) and cron will mail it you. No output therefore no mail, hence no differences/problems!
 
Damn, does this post get me the prize for length without substance? I ought to get back to work... ;)
 
Mathew

---

### Post by gerbman on 2007-10-08
> **petiejoe said:**
> FWIW, here's what I think I've decided on. I haven't run any of these from a cron job yet, so if somebody else reads this, be sure to test them for yourself to make sure they work for you.

```
#daily datasync.sh
#don't want to overwrite anything on the backup drive - most of
#my files should not ever be edited. By using --ignore-existing, 
#I protect from the possibility of somebody corrupting my data 
#(e.g. virii). Files that I want to permanently delete 
#(crappy pictures) will have to be deleted from both 
#sources using a separate script.
rsync -a --ignore-existing /mnt/data/data/ /mnt/back/data
```

```
#weekly datacheck.sh
#make sure everything's up-to-date:
datasync.sh
#check if stuff is missing from back drive:
rsync -avn /mnt/data/data/ /mnt/back/data > ~/missingFilesOnBack.output
#check if stuff is missing from data drive:
rsync -avn /mnt/back/data/ /mnt/data/data > ~/missingFilesOnData.output
```


```
#monthly fulldatacheck.sh
#make sure everything's up-to-date:
datacheck.sh
#to check if drives still work:
rsync -acvn /mnt/data/data/ /mnt/back/data > ~/rsync-acvn.output
```Keep in mind that Cron does not set up the PATH environment variable. So, while these scripts might run fine from the terminal (where the PATH has already been set up), they won't run from Cron because rsync won't be found. You either need to specify the full path to rsync (e.g., /usr/bin/rsync) each time, or set up the PATH variable at the beginning of your Cron table.

---

### Post by MJN on 2007-10-08
The default PATH variable set by cron is /usr/bin:/bin so it should be okay (in this case at least - does no harm to explicitly set it).
 
The PATH variable is enhanced even further by /etc/crontab for those crontabs that use it (e.g. cron.hourly|daily|weekyl|monthly but notably not cron.d/).
 
Mathew

---

### Post by gerbman on 2007-10-08
> **MJN said:**
> The default PATH variable set by cron is /usr/bin:/bin so it should be okay (in this case at least - does no harm to explicitly set it).
Can you point me to where you found this info? The last time I worked with Cron (a couple Ubuntu distributions ago) this was not the case.

---

### Post by MJN on 2007-10-08
It was more from experience (drop a cronjob of echo $PATH into /etc/cron.d/) but man 5 crontab refers to it (I'm sure there must be a more direct reference, but I haven't found it):

```
Several environment variables are set up automatically by  the  cron(8) daemon.
SHELL is set to /bin/sh, and LOGNAME and HOME are set from the /etc/passwd  line
of the crontab's owner.  PATH is   set to "/usr/bin:/bin".   HOME,  SHELL, and PATH
may be overridden by settings in the crontab; LOGNAME is the user that the job is
running from, and may not be changed.
```Mathew

---

### Post by petiejoe on 2007-10-09
> **MJN said:**
>  Last edited by MJN : 20 Hours Ago at 04:05 AM. Reason: Removed the most rambling bits (yep, what's left is the 'concise' stuff!)

:D

I appreciate everybody's comments. Perhaps I'll drop the monthly super-paranoid check and replace it with a good automated offshore push. I think I'll prime the pump by mailing a spare hard drive to my friend with 70 gigs of data and then set up a nightly sync (hopefully Comcast doesn't hate me too much). About 98% of my data (probably more) simply does not change - it's just the curse of having a high resolution camera. I'll post again in a few days when I actually have everything in cronjobs.

---

