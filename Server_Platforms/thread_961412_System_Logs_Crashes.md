---
title: "System Logs? Crashes"
date: 2008-10-28
forum: Server Platforms
---

### Post by BassKozz on 2008-10-28
I have a headless system (Hardy 8.04 - Desktop) setup at work, and I woke up this morning and I was unable to ssh into it.  I ended up resetting it and it's now back up and running, but I would like to know why it crashed in the first place...

Are there any system logs I can examine to find out what the problem was, when it happened, and why?
If so where are they located and what should I be looking for?

TiA,
-BassKozz

---

### Post by phidia on 2008-10-28
/var/log has all the logfiles. You could look there at messages, syslog, kern.log, faillog and maybe others.

---

### Post by BassKozz on 2008-10-28
Ok I found the logs in System>Administration>System Log
and I found an odd entry: ```
Oct 28 07:36:50 work-ubuntu-server syslogd 1.5.0#1ubuntu1: restart.
Oct 28 07:36:50 work-ubuntu-server anacron[10408]: Job `cron.daily' terminated
Oct 28 07:36:50 work-ubuntu-server anacron[10408]: Normal exit (1 job run)
```
Also found this from auth.log:```
Oct 28 07:30:01 work-ubuntu-server CRON[10383]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 07:30:01 work-ubuntu-server CRON[10383]: pam_unix(cron:session): session closed for user root
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
```
But I never authorized a reset at that time, what could have caused this?

---

### Post by aeiah on 2008-10-28
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) gives a bit of info on all the different log files. its unusual that your system restarted its self, even after upgrading the kernel without your sayso. have you got your system plugged into a UPS? perhaps there was a power glitch. there should be something in one of the log files that will tell you what was going on around that time.

---

### Post by BassKozz on 2008-10-28
> **aeiah said:**
> [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) gives a bit of info on all the different log files. its unusual that your system restarted its self, even after upgrading the kernel without your sayso. have you got your system plugged into a UPS? perhaps there was a power glitch. there should be something in one of the log files that will tell you what was going on around that time.

Yes the system is plugged into an APC UPS, Where did you see the system "upgrade its kernel" ?

---

### Post by aeiah on 2008-10-28
i didnt, i was just wandering if that was the case. your previous post wasnt as detailed as it is now at the time of my posting. you edited it afterwards to add more detail.

what is in your log before the reset? i can see that a cronjob finished after the reboot command was issued from somewhere, but thats probably expected

---

### Post by BassKozz on 2008-10-28
The cronjobs I have setup are simply daily backups to an archive file, but there aren't any reset commands issued in the cronjobs.

Here is the complete ***auth.log*** from last night:
```

Oct 28 00:17:01 work-ubuntu-server CRON[10280]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 00:17:01 work-ubuntu-server CRON[10280]: pam_unix(cron:session): session closed for user root
Oct 28 01:01:01 work-ubuntu-server CRON[10288]: pam_unix(cron:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 01:17:01 work-ubuntu-server CRON[10296]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 01:17:01 work-ubuntu-server CRON[10296]: pam_unix(cron:session): session closed for user root
Oct 28 02:17:01 work-ubuntu-server CRON[10307]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 02:17:01 work-ubuntu-server CRON[10307]: pam_unix(cron:session): session closed for user root
Oct 28 03:17:01 work-ubuntu-server CRON[10334]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 03:17:01 work-ubuntu-server CRON[10334]: pam_unix(cron:session): session closed for user root
Oct 28 04:17:01 work-ubuntu-server CRON[10345]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 04:17:01 work-ubuntu-server CRON[10345]: pam_unix(cron:session): session closed for user root
Oct 28 05:17:01 work-ubuntu-server CRON[10354]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 05:17:01 work-ubuntu-server CRON[10354]: pam_unix(cron:session): session closed for user root
Oct 28 06:17:01 work-ubuntu-server CRON[10365]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 06:17:01 work-ubuntu-server CRON[10365]: pam_unix(cron:session): session closed for user root
Oct 28 06:25:01 work-ubuntu-server CRON[10370]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 06:25:01 work-ubuntu-server CRON[10370]: pam_unix(cron:session): session closed for user root
Oct 28 07:17:01 work-ubuntu-server CRON[10377]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 07:17:01 work-ubuntu-server CRON[10377]: pam_unix(cron:session): session closed for user root
Oct 28 07:30:01 work-ubuntu-server CRON[10383]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 28 07:30:01 work-ubuntu-server CRON[10383]: pam_unix(cron:session): session closed for user root
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE

```
and ***messages***:
```

Oct 28 00:13:22 work-ubuntu-server -- MARK --
Oct 28 00:33:22 work-ubuntu-server -- MARK --
Oct 28 00:53:22 work-ubuntu-server -- MARK --
Oct 28 01:13:22 work-ubuntu-server -- MARK --
Oct 28 01:33:22 work-ubuntu-server -- MARK --
Oct 28 01:53:22 work-ubuntu-server -- MARK --
Oct 28 02:13:22 work-ubuntu-server -- MARK --
Oct 28 02:33:22 work-ubuntu-server -- MARK --
Oct 28 02:53:22 work-ubuntu-server -- MARK --
Oct 28 03:13:22 work-ubuntu-server -- MARK --
Oct 28 03:33:22 work-ubuntu-server -- MARK --
Oct 28 03:53:22 work-ubuntu-server -- MARK --
Oct 28 04:13:22 work-ubuntu-server -- MARK --
Oct 28 04:33:22 work-ubuntu-server -- MARK --
Oct 28 04:53:22 work-ubuntu-server -- MARK --
Oct 28 05:13:22 work-ubuntu-server -- MARK --
Oct 28 05:33:22 work-ubuntu-server -- MARK --
Oct 28 05:53:22 work-ubuntu-server -- MARK --
Oct 28 06:13:22 work-ubuntu-server -- MARK --
Oct 28 06:33:22 work-ubuntu-server -- MARK --
Oct 28 06:53:22 work-ubuntu-server -- MARK --
Oct 28 07:13:22 work-ubuntu-server -- MARK --
Oct 28 07:33:22 work-ubuntu-server -- MARK --
Oct 28 07:36:50 work-ubuntu-server syslogd 1.5.0#1ubuntu1: restart.

```
***syslog***:
```

Oct 28 07:36:50 work-ubuntu-server syslogd 1.5.0#1ubuntu1: restart.
Oct 28 07:36:50 work-ubuntu-server anacron[10408]: Job `cron.daily' terminated
Oct 28 07:36:50 work-ubuntu-server anacron[10408]: Normal exit (1 job run)

```

---

### Post by BassKozz on 2008-10-28
:bump: :confused:

---

### Post by bswanboat on 2008-10-28
Did I see amd 64? I was able to get 8.04 up and running after about 7 crashes. Then I used the envyny-qt to get the graphics working. It envyng-at did much better than the other methods I tried. 

But it still crashes. The motherboard is a M3N78 Pro with a 500 watt power supply. Could it be that the chip set drivers for the motherboard need to be updated?

I will stay tuned to see if someone comes up with a solution.

---

### Post by BassKozz on 2008-10-28
Well, my only lead that I have to go on is that I recently installed [JungleDisk]("http://jungledisk.com/") to do nightly backups on this machine (but the backups weren't/aren't scheduled for 7:30am, they run at 3am), and I've already had 5 to 6 successful nights in a row w/out any issues...

I recently rebooted this machine again and it crashed again...
I am leaning more & more towards jungledisk being the culprit.

Before I give my final ruling on this, are there any other logs I can post to get some more feedback?
Thanks for the help everyone.

---

### Post by BassKozz on 2008-11-24
It happened again on the 21st :(,
***Auth.log***
```
Nov 21 08:17:01 work-ubuntu-server CRON[26749]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 08:17:01 work-ubuntu-server CRON[26749]: pam_unix(cron:session): session closed for user root
Nov 21 09:17:01 work-ubuntu-server CRON[27480]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 09:17:01 work-ubuntu-server CRON[27480]: pam_unix(cron:session): session closed for user root
Nov 21 10:17:01 work-ubuntu-server CRON[28211]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 10:17:01 work-ubuntu-server CRON[28211]: pam_unix(cron:session): session closed for user root
Nov 21 11:17:01 work-ubuntu-server CRON[28944]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 11:17:01 work-ubuntu-server CRON[28944]: pam_unix(cron:session): session closed for user root
Nov 21 12:17:01 work-ubuntu-server CRON[29676]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 12:17:01 work-ubuntu-server CRON[29676]: pam_unix(cron:session): session closed for user root
Nov 21 13:17:01 work-ubuntu-server CRON[30410]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 13:17:01 work-ubuntu-server CRON[30410]: pam_unix(cron:session): session closed for user root
Nov 21 14:17:01 work-ubuntu-server CRON[31158]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 14:17:01 work-ubuntu-server CRON[31158]: pam_unix(cron:session): session closed for user root
Nov 21 15:17:01 work-ubuntu-server CRON[31892]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 15:17:01 work-ubuntu-server CRON[31892]: pam_unix(cron:session): session closed for user root
Nov 21 16:17:01 work-ubuntu-server CRON[32626]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 16:17:01 work-ubuntu-server CRON[32626]: pam_unix(cron:session): session closed for user root
Nov 21 17:17:01 work-ubuntu-server CRON[891]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 17:17:01 work-ubuntu-server CRON[891]: pam_unix(cron:session): session closed for user root
Nov 21 18:17:01 work-ubuntu-server CRON[1631]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 18:17:01 work-ubuntu-server CRON[1631]: pam_unix(cron:session): session closed for user root
Nov 21 19:17:01 work-ubuntu-server CRON[2365]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 19:17:01 work-ubuntu-server CRON[2365]: pam_unix(cron:session): session closed for user root
Nov 21 20:17:01 work-ubuntu-server CRON[3100]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 20:17:01 work-ubuntu-server CRON[3100]: pam_unix(cron:session): session closed for user root
Nov 21 21:17:01 work-ubuntu-server CRON[3832]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 21:17:01 work-ubuntu-server CRON[3832]: pam_unix(cron:session): session closed for user root
Nov 21 22:17:01 work-ubuntu-server CRON[4568]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 22:17:01 work-ubuntu-server CRON[4568]: pam_unix(cron:session): session closed for user root
Nov 21 23:17:01 work-ubuntu-server CRON[5395]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 23:17:01 work-ubuntu-server CRON[5395]: pam_unix(cron:session): session closed for user root

```
Looks like CRON is bugging-out ? 
I don't have a cronjob in place to run every hour on the 17th minute :confused:

---

### Post by dmizer on 2008-11-27
> **BassKozz said:**
> Looks like CRON is bugging-out ? 
I don't have a cronjob in place to run every hour on the 17th minute :confused:

Nope, those are perfectly normal looking cron logs. open the session, do what it needs to do (normally simple log rotation), and close session.

This looks like someone tried to access your box with a script, and your messages log indicates your server performed a restart shortly after that:
```
Oct 28 07:30:01 work-ubuntu-server CRON[10383]: pam_unix(cron:session): session closed for user root
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
```

Moving this to servers.

---

### Post by MJN on 2008-11-27
Guys, you are all getting confused as to the log entries and their meaning.
 
> **dmizer said:**
> This looks like someone tried to access your box with a script, and your messages log indicates your server performed a restart shortly after that
 
> **BassKozz said:**
> ```
Oct 28 07:36:50 work-ubuntu-server syslogd 1.5.0#1ubuntu1: restart.
```
But I never authorized a reset at that time, what could have caused this?
 
It wasn't a reset. Or at least nothing in that log snippet suggests it was. The 'restart' is referring to **syslog** restarting. This is perfectly normal and necessary in order for the log to be freed up for rotation (and archiving as appropriate).
 
> **BassKozz said:**
> ```
Nov 21 08:17:01 work-ubuntu-server CRON[26749]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 08:17:01 work-ubuntu-server CRON[26749]: pam_unix(cron:session): session closed for user root
Nov 21 09:17:01 work-ubuntu-server CRON[27480]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 21 09:17:01 work-ubuntu-server CRON[27480]: pam_unix(cron:session): session closed for user root
```
Looks like CRON is bugging-out ? 
I don't have a cronjob in place to run every hour on the 17th minute :confused:
 
Again this is perfectly normal. Look in /etc/crontab and you will likely find that your hourly cronjobs (as contained in /etc/cron.hourly/) are set to fire at 17 minutes past the hour...
 
Mathew

---

### Post by change_mode on 2008-12-26
> **dmizer said:**
> 
This looks like someone tried to access your box with a script, and your messages log indicates your server performed a restart shortly after that:
```
Oct 28 07:30:01 work-ubuntu-server CRON[10383]: pam_unix(cron:session): session closed for user root
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
Oct 28 07:35:01 work-ubuntu-server sudo:     root : TTY=unknown ; PWD=/ ; USER=USERNAME_HERE ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session opened for user USERNAME_HERE by (uid=0)
Oct 28 07:35:01 work-ubuntu-server sudo: pam_unix(sudo:session): session closed for user USERNAME_HERE
```

Moving this to servers.

Sorry for digging this up, but I saw the same thing in my log (ubuntu desktop pc) and found that it seems to be something the cron.daily/apt script does, so I guess it's harmless? :confused:

---

### Post by BassKozz on 2008-12-26
> **change_mode said:**
> Sorry for digging this up, but I saw the same thing in my log (ubuntu desktop pc) and found that it seems to be something the cron.daily/apt script does, so I guess it's harmless? :confused:

Thanks for letting me know, 
dmizer scarred me when he said someone was trying to access my box :eek:
I think I've cleared up the issue, for some reason when I ran JungleDisk as root (sudo mysecurebackupmonitor) it caused these random reboots.  So I am now running it as user and I haven't seen the issue since.

---

### Post by MJN on 2008-12-27
> **change_mode said:**
> so I guess it's harmless? :confused:Yes - just user confusion at what the logs are saying.

Post your full syslog if you are at all unsure as to what's happening in your particular case.

Mathew

---

