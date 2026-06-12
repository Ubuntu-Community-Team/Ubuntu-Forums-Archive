---
title: "Ubuntu 10.04 LTS - mysql fills up / with invisible files"
date: 2010-07-23
forum: Server Platforms
---

### Post by luigi6699 on 2010-07-23
I'm having the oddest problem.  I use Ubuntu 10 LTS on 3 Amazon EC2 "large" instances, for Drupal hosting.  All three servers are seeing the same issue, where root gradually fills up with files that I cannot see by any means.  ls -a , du , nothing seems to see these files except for df.  And when the drive gets full (after about a week), the server behaves as if the disk is full... so I believe that df is correct here.  The moment I restart mysql, all that invisible data disappears, and everything is fine again.

The MySQL datadir is on a separate device (600GB EBS mounted at /ebs ), so it's definitely not MySQL data.  And /tmp doesn't have anything visible going on; certainly not something that would take up 9gb. 

I suspect that something is causing the kernel to not release file handlers correctly.  For all I know this could be happening with all programs, but MySQL is the only thing running that would use enough temp space to be noticed.  Each server has some applications that happen on it uniquely, but since it's happening on all of them I figure it's the common elements that count.  The servers are a clean install, running Apache2 (PHP 5.3), MySQL, and SSHD.  All three servers were installed from the official AMI.

---

### Post by luigi6699 on 2010-07-29
I found the culprit!  

lsof -s +L1 on /var shows me that mysql is not closing logfiles after deletion... so the logfile continues occupying disk space.  

I'm just going to disable the mysql general query log... I only had it on for debug purposes anyway.  That should render the problem moot.  But in case anyone really logs a lot of mysql traffic, you should know: mysql log rotation is broken.

---

