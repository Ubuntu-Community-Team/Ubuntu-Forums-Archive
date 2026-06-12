---
title: "chkrootkit- what does this mean?"
date: 2010-01-28
forum: Security
---

### Post by Silvertones on 2010-01-28
Checking `z2'...                                            user **** deleted or never logged from lastlog!
user root deleted or never logged from lastlog!

I replaced my loggin name for this post with ****

I also show this:
Checking `aliens'...                                        
/dev/shm/pulse-shm-1152339957 /dev/shm/pulse-shm-4292147515

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/pymodules/python2.6/.path /usr/lib/firefox-3.5.7/.autoreg /usr/lib/xulrunner-1.9.1.7/.autoreg

Do I have a problem?

Thanks

---

### Post by adam814 on 2010-01-28
Probably not, I get similar messages running chkrootkit.  It's less paranoid than rkhunter, but it still gives a good deal of false positives.

---

### Post by Silvertones on 2010-01-28
Thanks. Is there a good program to use or should I just drop this Windows mindset?

---

### Post by adam814 on 2010-01-28
Both chkrootkit and rkhunter have their advantages and disadvantages.  Both warn for some things that don't necessarily indicate a problem.

It's safe to let the Windows mindset mostly go.  You won't get a drive-by rootkit on Linux.  At worst you may be tricked into installing one yourself.  So be conscious of Linux security issues (i.e. don't run anything you don't need to as root, make sure to set proper file permissions/ACLs as needed, use strong passwords, use a firewall, set up AppArmor, etc).

You shouldn't have to worry too much about rootkits as long as you're only installing software from trusted sources (what constitutes a trusted source depends on your level of paranoia).  I've never heard of trojans in files from the official Ubuntu repositories and in fact I've seen lengthy explanations as to why this is all but impossible.  With other sources YMMV.

---

