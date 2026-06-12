---
title: "chown desaster"
date: 2010-09-07
forum: Server Platforms
---

### Post by horvatj on 2010-09-07
dear forum members,

my situation is *ugly*...

I accidentally chowned -R the /etc subtree to a normal user account...

Is there a way to restore the ownership of a system (like on MacOS X)?

Or (even better): Is there a way to get the ownership of the /etc directory and its subdirectories on a working system, store them to a file and restore them on the f*****-up system?

Best, and thanks in  advence
Johann

---

### Post by BkkBonanza on 2010-09-07
I can suggest how you may fix this but I haven't done it myself. This is just from googling and combining a couple other suggestions...

Disclaimer: this should be safe but if you type something wrong, don't blame me :(

UPDATED:
I checked this on my system and found that ALL files under /etc were owned by root. 
However, this should still work but may be just extra work...
------

You'll need to boot off the LiveCD.

After booting you'll need to mount the original disk to /mnt.

eg. 
**sudo mount /dev/sdaX /mnt** (but be sure to use the correct device here)

Now you'll make a record of the correct permissions like this,

**sudo find /etc -printf "%u:/mnt%p\n" > ~/etc-perms.txt**

This makes a owner/filepath list of all the original files in /etc.

Now run this to redo the ownerships on your mounted version in /mnt/etc

**while IFS=":" read a b; do sudo chown $a $b done < ~/etc-perms.txt**

You may have to fix up some files that were added after installing. You can find them manually with this command, (using the name for the bad user),

**sudo find `/etc -user [B]baduser** -printf "%u:/mnt/%p\n"[/B]

Reboot onto your system. Hopefully that works...

---

