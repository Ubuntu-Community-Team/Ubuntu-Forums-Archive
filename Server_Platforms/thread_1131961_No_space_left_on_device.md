---
title: "No space left on device"
date: 2009-04-21
forum: Server Platforms
---

### Post by Adi_T on 2009-04-21
My email server says that has no space left. 
I cannot install anything. Even when i try to see me email account is says

Warning: session_write_close() [function.session-write-close]: open(/var/lib/php5/sess_6af737004e239834c011eacd7c62752f, O_RDWR) failed: No space left on device (28) in /usr/share/squirrelmail/src/redirect.php on line 171

this is th output when i run df -h


root@nesmark:/etc# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   14G   21G  40% /
varrun                248M  988K  247M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   32K  247M   1% /dev
devshm                248M     0  248M   0% /dev/shm
root@nesmark:/etc# 

Thanks in advance
Adi

---

### Post by BkkBonanza on 2009-04-21
That looks a little odd. Can you check a couple things - just stuff that may be detective work.

Check that session file it was opening/closing 
/var/lib/php5/sess_6af737004e239834c011eacd7c62752f

Is it still there and how big is it? If it's gone then it may have been that is was caused to grow too big and then released after it consumed all space. No idea why that would be though. Are there other sess_* files there and are they big?

Check your /var/logs to see if any of your logs have grown huge. That can happen and cause trouble.

It looks like your /var directory is mounted normally in / - so it's use should show up there in df output. Perhaps something went wrong and caused massive space allocation and upon closing that space was released. 

Also look in your /tmp directory and see if anything big is happening there.

Just ideas that I think I would look at if I saw this.

---

