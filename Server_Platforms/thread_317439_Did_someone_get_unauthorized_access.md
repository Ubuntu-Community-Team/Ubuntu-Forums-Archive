---
title: "Did someone get unauthorized access?"
date: 2006-12-12
forum: Server Platforms
---

### Post by JELO on 2006-12-12
Hello all,
I'm currently running a Ubuntu 6.06 server on a DMZ via IPCOP.  I check my logs periodically, every few days.  Mainly the auth.log found in /var/logs.  Since I don't actually have a webpage up right now.  Anywho, I do have an ssh server setup on this box.  I've been finding several attempts looking like bots or scripts running trying several different user names.  However, I found something suspicious in my log today.  I'm still pretty new to this but it seems odd, like someone got in.  Usually when I find a script looking deal I add the IP address in the hosts.deny file.  I guess there's probably a better way to do this though?  Anywho on to business, here's they odd thing I found.

uid=0)
Dec 11 06:25:02 ubuntu su[22453]: + ??? root:nobody
Dec 11 06:25:02 ubuntu su[22453]: (pam_unix) session opened for user nobody by (uid=0)
Dec 11 06:25:02 ubuntu su[22453]: (pam_unix) session closed for user nobody
Dec 11 06:25:02 ubuntu su[22457]: + ??? root:nobody
Dec 11 06:25:02 ubuntu su[22457]: (pam_unix) session opened for user nobody by (uid=0)
Dec 11 06:25:02 ubuntu su[22457]: (pam_unix) session closed for user nobody
Dec 11 06:25:02 ubuntu su[22459]: + ??? root:nobody
Dec 11 06:25:02 ubuntu su[22459]: (pam_unix) session opened for user nobody by (uid=0)

last and lastlog commands show nothing strange.  However, it seems that finger and whois commands have been uninstalled.  It is a server install but I would think they would be installed.  Also, there is this odd cron job running every hour it seems.  Here's just a couple of examples

Dec 11 09:17:02 ubuntu CRON[22530]: (pam_unix) session closed for user root
Dec 11 10:17:01 ubuntu CRON[22532]: (pam_unix) session opened for user root by (uid=0)
Dec 11 10:17:01 ubuntu CRON[22532]: (pam_unix) session closed for user root
Dec 11 11:17:01 ubuntu CRON[22534]: (pam_unix) session opened for user root by (uid=0)

Thanks

---

### Post by bswilson on 2006-12-12
> **JELO said:**
> I'm still pretty new to this but it seems odd, like someone got in. 

Not really.  The log is showing you PAM authentication by the user 'nobody' and 'root'.  These 2 users are running server services like at, cron, syslog,  X11, etc. and must authenticate themselves from time to time.

---

### Post by tturrisi on 2006-12-12
And I believe whois is not installed by default, at least in Debian it is not installed.  One needs to do:
apt-get install whois libidn11

---

### Post by JELO on 2006-12-12
Ah I see now.
Thanks.
I got all this from /etc/passwd
I'm wondering can I delete most of these and be ok?
Is there a tutorial or anything on what users I should leave?
I see that all are disabled except my main user?

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
..
..

---

### Post by technodigifreak on 2006-12-12
> **JELO said:**
> Ah I see now.
Thanks.
I got all this from /etc/passwd
I'm wondering can I delete most of these and be ok?
Is there a tutorial or anything on what users I should leave?
I see that all are disabled except my main user?

[B]root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh[/B]
..
..

I've never tried deleting these,  I tell you what, make a full backup of your system beforehand, and then delete them.  Let us know what happens :twisted:

---

### Post by MJN on 2006-12-13
Leave them in!
 
First rule of Linux... don't start pulling things apart unless you understand what they do! (okay, so I made that up but it's sound advice regardless)
 
If the user ID is <1000 then it's likely you didn't put them in (the system, or a package, did)... hence you shouldn't be pulling them out again either.
 
Mathew

---

