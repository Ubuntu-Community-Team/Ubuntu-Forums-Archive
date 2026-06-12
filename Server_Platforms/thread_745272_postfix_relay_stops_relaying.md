---
title: "postfix relay stops relaying"
date: 2008-04-04
forum: Server Platforms
---

### Post by awreneau on 2008-04-04
I have a postfix installation from the default repos 6.06LTS.  The only thing it does is relay mail to a internal exchange server from MFP devices on the network.  

Twice now the SMTP service has stopped responding.  

I can, from command prompt, telnet DNSNAME 25 and never get the 220 prompt for the helo and so on.

I've tried to restart the service /etc/init.d/postfix restart and get the following error:
* Stopping Postfix Mail Transport Agent postfix        [ ok ]
* Starting Postfix Mail Transport Agent postfix 
       rm: cannot remove `etc/localtime': Read-only file system


Bouncing the box is the quickest and sometimes the best method for getting the server back online.  

Any ideas as to what this might be?  
Syslog is pretty quiet prior to the restart.  No errors in the mail.err log that would indicate a hang.

Suggestions?

---

### Post by MJN on 2008-04-04
It sounds like your filesystem is being mounted as read-only in response to a disk problem. Run fsck on your drive, check your logs (if they are held on a different partition to /etc - if they are on the same the log may well not tell you anything as the log won't be updated), and try checking the SMART status/history of the drive.

I'm not sure, but dmesg may well keep a log in memory so next time it happens check it (as if it does do this then it won't matter that messages aren't being written to disk).

If you wish to find out for certain, at the expense of losing data from disk, try removing the **errors=remount-ro** from the relevent line in /etc/fstab - this will stop the read-only remount and hence potentially allow logging to continue.

Mathew

---

### Post by awreneau on 2008-05-09
MJN, thank you for the input, for some reason I didnt get prompted when you posted this reply and googling again turned up my own post.

Anyway, I'll try the things suggested.

A few things have come to the light prior to this post, it would seem that Whats Up Professional got on a rampage and checked SMTP up on the box nearly 9000 times in less than 24 hours and may well have been partially to blame.

Thanks again.

---

### Post by awreneau on 2008-06-08
MJN, I've done some more work on this problem and found the following error:

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/sda1: recovering journal
fsck.ext3: Bad magic number in super-block while trying to re-open /dev/sda1
e2fsck: io manager magic bad!


A reboot is the only way to get the system back online.  What fun!  Suggestions?

---

### Post by MJN on 2008-06-08
Either you got the fsck command wrong or it sounds like your disk is dying.

I'd be inclined to lean towards the latter given the problems that led to this thread. As the price of a new disk is relatively low I'd go for buying a new one rather than giving yourself a headache with the old (and of course running the risk of losing any valuable data).

Mathew

---

### Post by awreneau on 2008-06-08
Funny...  I'm at the office now recovering :-).   Between the time I posted the question and the moment the disk died was about 10 minutes.  HA!

Anyway, this server is running on VMWARE ESX and I had just taken an snapshot prior to upgrading a few packages.  Glad I did. otherwise I'd be toast right now.


I'm building another VM now that will replace this one.  The disks in the SAN, where this server lives, all appear to be OK, so I guess it was local to this installation.

Thanks for the help.  I'll report back my findings.

---

