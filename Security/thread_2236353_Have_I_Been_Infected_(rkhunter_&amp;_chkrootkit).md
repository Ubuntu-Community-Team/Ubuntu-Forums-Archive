---
title: "Have I Been Infected (rkhunter &amp; chkrootkit)"
date: 2014-07-26
forum: Security
---

### Post by StackSmasher on 2014-07-26
[B]Hello!
[/B]
Some general info about my system first:

I am running Ubuntu 14.04 LTS with a kernel version of 3.13.0-32-generic.
It is a relatively fresh install (not even 2 months old).
It is not a server, nor any p2p apps are being run.

So, the problem is the following:

I recently run chkrookit and a warning popped up (/sbin/init INFECTED). After some googling, i found out that
it is most likely a false positive.

However, after running rkhunter, it, too warned me about /sbin/init. I have to admit, that got me worried...

```

[01:04:27]   /sbin/init                                      [ Warning ]
[01:04:27] Warning: The file properties have changed:
[01:04:27]          File: /sbin/init
[B][01:04:27]          Current hash: f8318fbf9490e34035d35494f99842cb1f57192e
[01:04:27]          Stored hash : a3f4886df912c0550f4e32cec1814e7f92e0218b[/B]
[01:04:27]          Current inode: 2752577    Stored inode: 2752579
[01:04:27]          Current file modification time: 1405676811 (18-July-2014 12:46:51)
[01:04:27]          Stored file modification time : 1397253526 (12-April-2014 00:58:46)

```

Googling the *"Stored Hash"* checksum, revealed some relationship with /sbin/init. However, searching for the *"Current Hash" *returns nothing.

I do understand that rootkits are **extremely rare** for home users who, don't run a server.
However, I am still worried...

My primary question is:
*Under what conditions the /sbin/init file would change? Would something other than an infection account for the warnings?*

*(According to apt's logs, no updates were run on this day...)*

**Any help would be greatly appreciated!** :)

Thanks a lot.

---

### Post by wyliecoyoteuk on 2014-07-26
Probably a false positive.
if you have not rebooted since the last updates were run, the hash may be mismatched.

rkhunter and chrootkit use different methods for scanning, init has a history of FPs from chrootkit.
rkhunter needs 
 rkhunter --propupd 
running after any updates, to bring its data up to date.

---

### Post by mooreted on 2014-07-26
Just checked, mine says the same thing. I doubt that all of us have a root kit. Looks like a false positive to me.

---

### Post by StackSmasher on 2014-07-26
Yes, I guess so... Thanks for the replies.

I initially wondered, because I couldn't find an update entry on apt's logs, for that day.

So, I used a 14.04 live CD I had lying around.
It's /sbin/init's sum matched with "Stored Hash".

**After upgrading, the new hash match the current one stored in my system.**

Thanks for your help!

---

