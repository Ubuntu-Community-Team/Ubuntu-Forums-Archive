---
title: "WHat are &quot;deletions&quot; ?"
date: 2010-04-25
forum: Security
---

### Post by MadMax2 on 2010-04-25
n Tue Apr  6 10:12:21 2010 and Tue Apr  6 11:19:32 2010
2 deletion(s) between Fri Apr  9 07:50:23 2010 and Sat Apr 10 06:15:03 2010
1 deletion(s) between Sun Apr 18 21:32:57 2010 and Mon Apr 19 06:10:10 2010
2 deletion(s) between Fri Apr 23 08:59:08 2010 and Fri Apr 23 20:17:51 2010
2 deletion(s) between Sat Apr 24 20:42:49 2010 and Sun Apr 25 05:35:41 2010
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user Max deleted or never logged from lastlog!
----
I log in each session.
==================================================================================
and this:
/usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
===============================
[19:37:57]   Checking running processes for suspicious files [ None found ]
[19:37:57]
[19:37:57] Info: Test 'hidden_procs' disabled at users request.
[19:37:57]
[19:37:57] Info: Test 'suspscan' disabled at users request.

---------------
Checking /dev for suspicious file types         [ Warning ]
[19:38:21] Warning: Suspicious file types found in /dev:
[19:38:21]          /dev/shm/pulse-shm-2904441744: data
[19:38:21]          /dev/shm/pulse-shm-675592893: data
[19:38:21]          /dev/shm/pulse-shm-3486204915: data
[19:38:21]          /dev/shm/pulse-shm-2044683277: data
[19:38:22]   Checking for hidden files and directories       [ Warning ]
[19:38:22] Warning: Hidden directory found: /etc/.java
[19:38:22] Warning: Hidden directory found: /dev/.udev
[19:38:22] Warning: Hidden directory found: /dev/.initramfs
----------



Thanks
[moderator I've asked this again with a catchier title so if no one replies you can delete?]

---

### Post by Rubi1200 on 2010-04-26
I found this thread:
[http://ubuntuforums.org/showthread.php?t=29685](http://ubuntuforums.org/showthread.php?t=29685)
Maybe helps?
From the chkrootkit website:
chklastlog.c: checks for lastlog deletions.
chkwtmp.c: checks for wtmp deletions.
Whether or not you should be concerned is another question that I am not capable of answering.
Good luck!

---

