---
title: "Is there a file size limit for upload"
date: 2010-05-11
forum: Ubuntu One (CLOSED)
---

### Post by laoshi on 2010-05-11
I have a large file (deflated size: 602191947)that is not saved in my Ubuntu One account. On sync'ing the file is being uploaded, and eventually reaches 602191947 - and then nothing more happens to this file - but sync'ing the following files in the queue goes on with success.
I have tried manual upload with the same result.
The file is still being marked as 'uploading' even after several tries and log ins/log outs, and reboots.
So I was just wondering whether there is a file size limit - can't seem to find information regarding this.

---

### Post by scc4fun on 2010-05-11
> **laoshi said:**
> I have a large file (deflated size: 602191947)that is not saved in my Ubuntu One account. On sync'ing the file is being uploaded, and eventually reaches 602191947 - and then nothing more happens to this file - but sync'ing the following files in the queue goes on with success.
I have tried manual upload with the same result.
The file is still being marked as 'uploading' even after several tries and log ins/log outs, and reboots.
So I was just wondering whether there is a file size limit - can't seem to find information regarding this.

I do not know what the file size limit is, but the total storage limit is 2GB for the free version or 50GB for the paid version. It seems your file is well over both of those at just under 600GB (read: GiB). To my knowledge there are not any other plans that support larger files or total storage.

---

### Post by dearingj on 2010-05-11
> **scc4fun said:**
> I do not know what the file size limit is, but the total storage limit is 2GB for the free version or 50GB for the paid version. It seems your file is well over both of those at just under 600GB (read: GiB). To my knowledge there are not any other plans that support larger files or total storage.

I think you might have miscalculated that 600GB size. Using Google's convert function, and assuming the original number is in bytes, I get 574.294993 mebibytes - well under the 2 GB total storage limit.

---

### Post by laoshi on 2010-05-11
Yes - the size is about 600 MB, and I have a paid 50 GB account.
The strange thing is that I get no warnings, the file uploads, and I can follow it using u1sdtool --current-transfers until everything seems uploaded - calculated size and uploaded size is identical. But the file just doesn't show up in my files storage on Ubuntu One.

---

### Post by joshuahoover on 2010-05-11
> **laoshi said:**
> Yes - the size is about 600 MB, and I have a paid 50 GB account.
The strange thing is that I get no warnings, the file uploads, and I can follow it using u1sdtool --current-transfers until everything seems uploaded - calculated size and uploaded size is identical. But the file just doesn't show up in my files storage on Ubuntu One.

Hi, This file is definitely small enough. We cannot support files bigger than 5 GB currently. In order to figure out what is causing this problem (not syncing to the server), can you do the following?

[LIST=1]
[*]Open (or create if it doesn't exist):  ~/.config/ubuntuone/syncdaemon.conf 
[*]Add the following 2 lines to this file and save: 
[main] 
 log_level = DEBUG 
 
[*]Run the following commands from a terminal session: u1sdtool -d; u1sdtool -q; u1sdtool --start; u1sdtool -c;
[*]Try to sync the file
[*]File a new bug here:  [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)
[*]In a terminal session run (replacing ###### with the bug number from the previous step): apport-collect -p ubuntuone-client ######
[*]Attach  ~/.cache/ubuntuone/log/syncdaemon.log to the bug report
[/LIST]
Thank you,

Joshua

---

### Post by laoshi on 2010-05-12
Hi Joshua.
Thank you for your guidance.
Before I saw your latest post I had removed the file from the directory selected for synchronization, and replaced it with a tar.gz compressed version.
I then put the original file back and followed your counsel.
After sync'ing started, the tar.gz file was synced without problems.
The original file did not sync. But the greyed out 'uploading' disappeared from the server - and on my pc the file was marked as synchronized!
No faults in the log.
But there seems to have been faulty calculation of the file size.
u1sdtool persistently reported the file as being 602191947 bytes - but on inspection in nautilus it is reported as being 784512000 bytes.
Anyway - sync'ing is proceeding full scale now.

---

