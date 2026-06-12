---
title: "Offsite Backups"
date: 2006-05-11
forum: Server Platforms
---

### Post by dk_pa on 2006-05-11
I have been playing around with some off-site backups with RSYNC.  I really like it so far and I'm probably going to use a script and setup a Cronjob for a couple weeks to test how it does.  Anyway...

Right now I'm usiing rsync with SSH and was wondering if the encryption SSH offers is good enough for something like this.  I know SSH is really widespread but I'm not a security guru.  

Any suggestions/advice etc is appreciated.

---

### Post by MJN on 2006-05-12
Sure - it's the defacto standard and can be safely relied upon (v2 at least).
 
I too use rsync in this way - as you've likely found it does exactly what it says on the tin, and very well too.
 
Mathew

---

### Post by dk_pa on 2006-05-12
Thanks for the reply.  

And yeah... I definitely like rsync a lot.  It just sits there and does it thing, can't really ask for me at this point.

---

### Post by Socratez on 2006-05-13
I am looking to do a similar thing however I want to set it up as ONSITE backup. I have a desktop with a directory I want to keep in Sync with my NAS machine. I don't want to have to copy the entiredirectory each time just update the changes like an incremental backup ... Can Rsync and ssh do this as well? 



Soc

---

### Post by MJN on 2006-05-13
That depends on the capabilities of your NAS - it would need an SSH server and rsync installing on it. Rsync essentially works by having an instance of rsync running at either end (i.e. source and destination) and they discuss between themselves what files they've got then work out the differences (using the timestamps by default) and transfer the portions of files that need updating. It sounds like it'd take forever but it's done lightning quick. SSH is used in this instance to encrypt the traffic between the rsync's. Note that it goes beyond the more conventional 'incremental update' whereby only changed files are transferred, in this case it even limits the transfers to only the *parts* of the file that have changed.

Incidentally, you can run rsync at either end in a 'daemon mode' and forego the SSH tunnel however to discuss that in this context will only confuse the issue.

Does that answer your query?

Mathew

---

### Post by Socratez on 2006-05-13
Yes it does ... I will have to see if I can get the rsync to work .. I just have a cheap ol NSLU2 appliance from Linksys and I haven't hacked it or opened it up to run on a more robust linux kernel. Looks like I have a weekend project ... 


Thanks a Mill


Soc

---

