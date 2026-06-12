---
title: "Tripwire - Getting the best out of it..."
date: 2013-08-25
forum: Security
---

### Post by Abaminog on 2013-08-25
Hi!

I have recently installed Ubuntu 13.04 on my laptop (couple days ago) and added the Tripwire package to keep an eye on changes to my file system.

When I installed Tripwire, I ran init to take a snapshot of my system and get it initialised. Over the last day or two I have made a number of changes to my system including downloading and installing new packages, removing some others etc etc. Just now, as I ran Tripwire in the Integrity Check mode, I ended up with a report file of over 500K long with a huge number of changes registered (most of those in the /proc folder). I appreciate that Tripwire simply compared the current file system with the snapshot it made when it was initialised. However, the usefulness of the Tripwire reports is now rather questionable as it would be insane to try and go through the entire report file trying to identify suspicious changes. Hence few questions from me:

1. Is it worthwhile running Tripwire in the Database Update mode every time just after the new report is generated? If so, then the next report will be done based on the updated system snapshot which may already contain some malicious footprints which I skipped.
2. How do I force Tripwire not to scan the /proc folder to avoid generating volumes of meaningless information?  
3. Generally, what is an optimal approach to use Tripwire for regular system monitoring? I.e. should I run it say once a week manually and then look out for some 'red alerts' in the report file? Or maybe add it under cron and then search the report file automatically for some key words?

Please advise.
Thanks!

---

### Post by unspawn on 2013-09-01
> **Abaminog said:**
> Is it worthwhile running Tripwire in the Database Update mode every time just after the new report is generated?
I'd say manually and only after reviewing the report, otherwise it would be as wasted an effort like creating a /etc/apt/apt.conf.d/99tripwire "Post-Invoke" for it to have it run automagically (like you would do for say 'debsums').


> **Abaminog said:**
> How do I force Tripwire not to scan the /proc folder  
Start by reading the documentation? The single line should read something like "!/proc".


> **Abaminog said:**
> Generally, what is an optimal approach to use Tripwire for regular system monitoring? I.e. should I run it say once a week manually and then look out for some 'red alerts' in the report file? Or maybe add it under cron and then search the report file automatically for some key words?
Kind of depends on your security posture and requirements. For instance if you run a SOHO workstation behind a NAT router, for a single human user, with only the applications you need installed, without (publicly) listening services, properly hardened (see the Ubuntu Wiki and maybe the "Securing Debian" manual) and running a combination of auditing tools then due to a reduced attack surface what you audit and how often may be different compared to the requirements for say a public shell server. Back when I ran AIDE (which is OSS and certainly not as License-confused as tripwire) I tended to have different configurations for different areas like system directories, configuration files and such. These days I run Samhain. It doesn't do away with post-upgrade database maintenance but it's way more efficient for running as a daemon process (no need for cron jobs), using inotify (only scan when things change) and much much more...

---

