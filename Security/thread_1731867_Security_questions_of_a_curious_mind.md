---
title: "Security questions of a curious mind"
date: 2011-04-17
forum: Security
---

### Post by debd on 2011-04-17
Before you start reading this thread, I request you to be a little patient to read through this- a bit long post.

Till this date I have not been concerned at all for my Ubuntu system; until I read a post in the Ubuntu Forums, and became curious to know how my system fares in terms of overall security. So, I went by the post and installed ntop (network monitoring tool), tiger(system security audit and intrusion detection utility), john(a password cracker), and chkrootkit(root-kit detection tool).

Now I want some info about some situations I got, and need to clear some doubts. Any reply related to these situations, suggesting external links or any other help would be of great guide to me.

1. While installing ntop, I get this info:

```
adduser: Warning: The home directory `/var/lib/ntop' does not belong to the user you are currently creating.

```
I checked that that folder belongs to the user 'ntop'- apparently craeted while installing ntop(I checked auth.log) .I'm just curious..: then why does it say - it does'nt belong to user 'ntop' ?

2.When trying to run ntop, I get this following error:

```
Sun Apr 17 14:57:04 2011  NOTE: Interface merge enabled by default
Sun Apr 17 14:57:04 2011  Initializing gdbm databases
Sun Apr 17 14:57:04 2011  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Sun Apr 17 14:57:04 2011  Possible solution: please use '-P <directory>'
Sun Apr 17 14:57:04 2011  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Sun Apr 17 14:57:04 2011  CLEANUP[t3077978048]: ntop caught signal 2
Sun Apr 17 14:57:04 2011  THREADMGMT[t3077978048]: ntop RUNSTATE: SHUTDOWN(7)
Sun Apr 17 14:57:04 2011  CLEANUP[t3077978048] catching thread is unknown
Sun Apr 17 14:57:04 2011  CLEANUP: Running threads
Sun Apr 17 14:57:04 2011  CLEANUP: Locking purge mutex (may block for a little while)
Sun Apr 17 14:57:04 2011  CLEANUP: Locked purge mutex, continuing shutdown
Sun Apr 17 14:57:04 2011  CLEANUP: Continues
Sun Apr 17 14:57:04 2011  PLUGIN_TERM: Unloading plugins (if any)
Sun Apr 17 14:57:04 2011  CLEANUP: Clean up complete
Sun Apr 17 14:57:04 2011  THREADMGMT[t3077978048]: ntop RUNSTATE: TERM(8)
Sun Apr 17 14:57:04 2011  ===================================
Sun Apr 17 14:57:04 2011          ntop is shutdown...        
Sun Apr 17 14:57:04 2011  ===================================

```
what is the error about? Do I have to install some more packages for it to work?

3. While installing tiger, john and chkrootkit, a package 'sendmail' was installed along with some other extra packages.
I googled to know about this 'sendmail' package. What am still not sure about is- is sendmail a mailserver that should rather be on a server than a desktop computer? or is it good to have it installed, and if so-- why?

Now am in similar confusion with this 'sendmail' thing. :)
While installing sendmail, it gave the folloing msgs:

```
adduser: Warning: The home directory `/var/lib/sendmail' does not belong to the user you are currently creating.
adduser: Warning: The home directory `/var/lib/sendmail' does not belong to the user you are currently creating.
```

I checked the owner of /var/lib/sendmail is 'smmta- Mail Transfer Agent', while, in the /var/log/auth/log file, it's like this:

```
Apr 17 15:12:00 debubu groupadd[15013]: group added to /etc/group: name=smmta, GID=130
Apr 17 15:12:00 debubu groupadd[15013]: group added to /etc/gshadow: name=smmta
Apr 17 15:12:00 debubu groupadd[15013]: new group: name=smmta, GID=130
Apr 17 15:12:00 debubu useradd[15019]: new user: name=smmta, UID=119, GID=130, home=/var/lib/sendmail, shell=/bin/false
Apr 17 15:12:00 debubu usermod[15024]: change user 'smmta' password
Apr 17 15:12:01 debubu chage[15029]: changed password expiry for smmta
Apr 17 15:12:01 debubu chfn[15032]: changed user 'smmta' information
Apr 17 15:12:01 debubu groupadd[15040]: group added to /etc/group: name=smmsp, GID=131
Apr 17 15:12:01 debubu groupadd[15040]: group added to /etc/gshadow: name=smmsp
Apr 17 15:12:01 debubu groupadd[15040]: new group: name=smmsp, GID=131
Apr 17 15:12:01 debubu useradd[15046]: new user: name=smmsp, UID=120, GID=131, home=/var/lib/sendmail, shell=/bin/false
```

So, apperently, 'smmta' was created by 'sendmail' itself and is owned by it. So, why the 'adduser' warning? 

Whereas tiger -H which creates a detailed security audit warns me (!!:)) that "`/etc/mail' is not owned by root (owned by smmta)." 

It also complains:

"Login ID mail's home directory (/var/mail) has group `mail' and world write access. "

what does that mean?

some other warnings by the audit-results of my concern are like:
```

FAIL [lin005f]Installed file `/usr/share/liferea/pixmaps/available.png' checksum differs from installed package 'liferea-data'.
FAIL [lin005f]Installed file `/usr/share/liferea/pixmaps/available_offline.png' checksum differs from installed package 'liferea-data'. 

FAIL [lin016f]The system permits source routing from incoming packets
WARN [lin017w]The system is not configured to log suspicious (martian) packets

WARN [perm001w]The owner of /usr/bin/at should be root (owned by daemon).
WARN [perm002w]The group owner of /usr/bin/at should be root. 
```

What should be the defaults/safer for these last three cases?

Well, if you have hold your patience till now, I ought to give you a big thank, which I do :)

**Thank you.**

 Am looking forward to your replies.

---

### Post by Doug S on 2011-04-17
For the ntop part:
I tried ntop just a few days ago, and out of interest from another thread.
I got the exact same as you when I used this command:
```
 
ntop -w 3000 -W 0

```So, I did this instead:
```
 
sudo ntop -w 3000 -W 0

```
And it worked fine. I do have to still read more and such, and I havent't gotten back to it yet.

---

### Post by debd on 2011-04-17
```
sudo ntop -w 3000 -W 0
```

this was very helpful...the way ntop shows all the infos in a html format is really good.

---

