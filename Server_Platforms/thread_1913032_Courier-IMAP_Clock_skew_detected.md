---
title: "Courier-IMAP Clock skew detected"
date: 2012-01-21
forum: Server Platforms
---

### Post by NightFoxyarrith on 2012-01-21
So, I installed courier-imap and configured it, but I couldn't connect. I used telnet to troubleshoot, tried logging in and got this:
```
 * BYE Clock skew detected. Check the clock on the file server 
```
I found some info using google, so I tried syncing time with ntp, but except for verifying that a cron job for ntp exists, I couldn't really figure out if and how manual sync is possible. I then tried the following:
```
 date && touch test && stat test 
```
Which gave me this (weird) output:
```
Sun Jan 22 04:30:47 MSK 2012
  File: `test'
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: 1dh/29d	Inode: 5525648     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2012-01-22 03:58:23.000000000 +0400
Modify: 2012-01-22 03:58:23.000000000 +0400
Change: 2012-01-22 03:58:23.000000000 +0400
```
The time from date and the file acces, modify, etc. should be the same, and I think this is causing my imap to fail.
Any help would be appreciated.

---

### Post by NightFoxyarrith on 2012-01-22
I tried the ntpd daemon, but that didn't help, and the logfile doesn't give me any errors. Ntpq gave me this, but I don't know what this means:
```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 91.189.94.4     193.79.237.14    2 u   61   64    7  105.856  -194776   6.956

```

---

### Post by SeijiSensei on 2012-01-23
> **NightFoxyarrith said:**
> I tried the ntpd daemon, but that didn't help, and the logfile doesn't give me any errors.

ntpd won't update if there's too big a mismatch between your machine and the remote server.  Use the command "sudo date --date='12:03' replacing 12:03 with the current clock time.  Then restart ntpd.

You may also need to let traffic on UDP port 123 through your firewall.

---

### Post by NightFoxyarrith on 2012-01-23
Thanks for your reply. I can't set the time manually, I get this error: 
```
date: cannot set date: Operation not permitted
```
I tried sudo, and even tried logging in as root to do this. Is it possible that my VPS provider blocks time changing, and manages time themselves? If so I guess I'll have to send them an e-mail to fix it.

---

### Post by SeijiSensei on 2012-01-23
Actually I mistyped the correct command which is

```
sudo date --set='12:34'
```

I just tested this on my Linode virtual server and was not prohibited from running it.  If you cannot do the same, I guess you need to talk to your provider.

I can see perhaps forbidding you from running the hwclock command, but the date command just sets the system time.  That only applies to your VM and should not interfere with any other VMs on the machine or the host server's hardware clock.

---

