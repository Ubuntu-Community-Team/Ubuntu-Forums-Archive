---
title: "Ubuntu One Nukes Files... Eep."
date: 2009-11-24
forum: Ubuntu One (CLOSED)
---

### Post by Mr_Pag on 2009-11-24
Lesson Learned Today...

Just had to spend this evening re-writing an essay because Ubuntu One decided to delete my local Ubuntu One directory following a bodged sync (I think, my wireless is shaky at best but I'm not reproducing this one any time soon, the cloud is getting banned from my drive til 10.04)

My stupid fault of course for putting my only copy in the sync folder. But for Gawd's sakes peoples, do yourself a favour and keep a copy elsewhere, and certainly don't rely on a beta service as your only backup.

The more you know :KS

---

### Post by joshuahoover on 2009-11-25
> **Mr_Pag said:**
> Lesson Learned Today...

Just had to spend this evening re-writing an essay because Ubuntu One decided to delete my local Ubuntu One directory following a bodged sync (I think, my wireless is shaky at best but I'm not reproducing this one any time soon, the cloud is getting banned from my drive til 10.04)

My stupid fault of course for putting my only copy in the sync folder. But for Gawd's sakes peoples, do yourself a favour and keep a copy elsewhere, and certainly don't rely on a beta service as your only backup.

The more you know :KS

Yikes! My apologies for the serious inconvenience Ubuntu One has caused you. This is a VERY serious bug and we need to address it ASAP. If you can submit a bug report along with any ~/.cache/ubuntuone/log/syncdaemon.log files you have, we'll take a look right away. Please put DATA LOSS at the beginning of the bug title so that it gets our attention right away.

Thank you,

Joshua

---

### Post by Nicolas Raoul on 2010-01-13
The same bug happens to me quite often.
I can easily reproduce it if anyone wants.
I posted the bug on Launchpad but nobody seems to care:
[https://bugs.launchpad.net/ubuntuone-client/+bug/503751](https://bugs.launchpad.net/ubuntuone-client/+bug/503751)

Hopefully, I have not lost any data yet, because somehow when Ubuntu One decides to delete essay.txt then I can find the latest version of it in essay.txt.u1conflict.x where "x" is the highest number you can find in the same directory. For instance:

BEFORE:

essay.txt
essay.txt.u1conflict
essay.txt.u1conflict.1
essay.txt.u1conflict.2

AFTER:

essay.txt.u1conflict
essay.txt.u1conflict.1
essay.txt.u1conflict.2
essay.txt.u1conflict.3

TRY THIS TO RECOVER YOUR FILE:

mv essay.txt.u1conflict.3 essay.txt

---

### Post by joshuahoover on 2010-01-15
> **Nicolas Raoul said:**
> The same bug happens to me quite often.
I can easily reproduce it if anyone wants.
I posted the bug on Launchpad but nobody seems to care:
[https://bugs.launchpad.net/ubuntuone-client/+bug/503751](https://bugs.launchpad.net/ubuntuone-client/+bug/503751)

Hopefully, I have not lost any data yet, because somehow when Ubuntu One decides to delete essay.txt then I can find the latest version of it in essay.txt.u1conflict.x where "x" is the highest number you can find in the same directory. For instance:

BEFORE:

essay.txt
essay.txt.u1conflict
essay.txt.u1conflict.1
essay.txt.u1conflict.2

AFTER:

essay.txt.u1conflict
essay.txt.u1conflict.1
essay.txt.u1conflict.2
essay.txt.u1conflict.3

TRY THIS TO RECOVER YOUR FILE:

mv essay.txt.u1conflict.3 essay.txt

My apologies for the lack of a response. I will be looking into your bug today. I do want to clarify one point though. There is a big difference between files being deleted and files being marked as conflicts. Files being deleted means they are no longer available. Files being marked as conflicts means they are still available, but Ubuntu One thinks they conflict for some reason and marks them as such. I will be looking into why you get the conflict files but I wanted to make sure that others who read this post know that there is a difference between conflicts and files being deleted. :-)

Thank you,

Joshua

---

### Post by venik212 on 2010-01-17
How do I start the ubuntuone-client?  I have installed ubuntuone, created an account, but I cannot run it from the command line.  When I type: ubuntuone-client I am told: command not found.

---

### Post by dominant on 2010-01-18
My problem is that sometimes ubuntu one replicates files with 0bytes, and then on the other computer where the original files were stored it rewrites it to empty files. I lost hundreds documents like that few weeks ago. After this little misfortune I never store only copy of files in ubuntu one. This problem persists when both pcs are online.

---

### Post by teknico on 2010-01-18
venik212: the command is "ubuntuone-client-applet".

dominant: did you see that behavior recently? If so, can you please file a bug, doing the following to try and reproduce it? 

1. Open (or create if it doesn't exist): ~/.config/ubuntuone/syncdaemon.conf
 
2. Add the following 2 lines to this file and save:

[__main__]
log_level = DEBUG
 
3. Restart the Ubuntu One client
 
4. Try to reproduce the behavior you've been seeing and then attach the following log file: ~/.cache/ubuntuone/log/syncdaemon.log
 
Please file the bug here: [https://bugs.launchpad.net/ubuntuone-client/+filebug](https://bugs.launchpad.net/ubuntuone-client/+filebug)

This will provide us with a lot more detail and help the developers get to the root cause of the problem. Thank you.

---

### Post by dsfitzpat on 2010-11-05
I also experiences problems with file loss today; fortunately, I copied my documents folder to an external drive before it happened.  I'm running Ubuntu on my desktop and on a netbook.  I finally got around to organising my documents folder on my desktop, after which I synced it to Ubuntu One.

When I turned on my netbook I saw that it now also had its documents folder selected for syncronisation.  I wanted to make sure there were no files on the netbook that I didn't already have on my PC, so I disconnected the netbook from Ubuntu One, and did a manual check of the files to confirm they were already on my desktop.

Then, since I wanted my netbook to have the same documents as my desktop, and since I'd just reorganised the desktop, I emptied the documents folder on the netbook, and then reconnected to Ubuntu One.  For the most part, this did what I wanted - the netbook began to download files from Ubuntu One.  

Unfortunately, during the synchronisation a handful of files were removed from the cloud image (about 15Mb of 365Mb): for some reason syncing the netbook caused most of the files to be downloaded, but caused others to be deleted from the server.  No idea why.  Then, when my desktop connected to Ubuntu One, it saw that some of the files it had put there yesterday were gone, and promptly removed them from my computer!

Shouldn't the default behaviour be to upload local files that are not on Ubuntu One, rather than deleting them?  What if I create a new file?  Is my computer going to see that it's not on the cloud and then remove it?

I'd like to use Ubuntu One to keep my two computers in snyc, but clearly, I'm doing it wrong!  Any hints?

---

