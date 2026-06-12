---
title: "Quiet a loud hard disk automatically"
date: 2012-06-11
forum: Server Platforms
---

### Post by Master_Taco on 2012-06-11
I'm running the latest copy of Ubuntu Server (12.04 x86) on my server in my house. The server sits right next to me and it has two hard disks. The second hard disk is used only for backup and network shares, so for the most part it needn't be on. This drive also happens to be comparatively loud, so I have been running this command: "sudo hdparm -S60 /dev/sdb" to shut down the hard disk after 5 minutes of being idle. The problem is, if the machine reboots for any reason, it forgets these settings and proceeds to stay spinning for ever and ever. Is there a way to make it so it will remember that I set it to shut up after 5 minutes of inactivity?

---

### Post by LHammonds on 2012-06-12
Run the command in crontab and specify the "@reboot" option so it will run the command after every reboot.

[Crontab How-To]("https://help.ubuntu.com/community/CronHowto")

LHammonds

---

### Post by rubylaser on 2012-06-12
> **LHammonds said:**
> Run the command in crontab and specify the "@reboot" option so it will run the command after every reboot.

[Crontab How-To]("https://help.ubuntu.com/community/CronHowto")

LHammonds

This will work. But, you can, and probably should, use the /etc/hdparm.conf file instead to take care of this for you.

[Here's how I do it]("http://zackreed.me/articles/60-spin-down-idle-hard-disks").

In your case for a five minute shutdown, you want your /etc/hdparm.conf file to look like this.
```

/dev/sdb {
spindown_time = 60
}

```

---

### Post by Master_Taco on 2012-06-12
> **rubylaser said:**
> This will work. But, you can, and probably should, use the /etc/hdparm.conf file instead to take care of this for you.

[Here's how I do it]("http://zackreed.me/articles/60-spin-down-idle-hard-disks").

In your case for a five minute shutdown, you want your /etc/hdparm.conf file to look like this.
```

/dev/sdb {
spindown_time = 60
}

```
I did a bit of research, and I did do that exact same thing (with the hdparm.conf file), but the problem didn't resolve. It turns out I'm getting some HDD errors in my kernel log. It says that every time the HDD shuts down, it is immediately woken up again. THe console monitor says explicitly that it's waking the drive up, but gives no explicit reason why. Here is an excerpt from my kernel log, maybe it will clue someone who has more intimate knowledge with the OS than I do.

```
-rw-r----- 1 syslog        adm          0 Jan 11 15:06 ufw.log
drwxr-xr-x 2 root          root      4096 Apr  1 06:53 unattended-upgrades
drwxr-xr-x 2 root          root      4096 Jun  3 23:47 upstart
-rw-rw-r-- 1 root          utmp    101376 Jun 12 03:58 wtmp
-rw-rw-r-- 1 root          utmp     44928 Mar 30 00:51 wtmp.1

Tue Jun 12 18:40:45 CDT 2012
/var/log
justin@ubuntu-web-server: pts/1: 79 files b -> vi kern.log
Jun 12 03:16:39 ubuntu-web-server kernel: [   20.536223] type=1400 audit(1339488999.379:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1174 comm="apparmor_parser"
Jun 12 03:16:39 ubuntu-web-server kernel: [   20.536386] type=1400 audit(1339488999.379:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1173 comm="apparmor_parser"
Jun 12 03:16:39 ubuntu-web-server kernel: [   20.537662] type=1400 audit(1339488999.379:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1173 comm="apparmor_parser"
Jun 12 03:16:39 ubuntu-web-server kernel: [   20.537707] type=1400 audit(1339488999.379:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1174 comm="apparmor_parser"
Jun 12 03:16:39 ubuntu-web-server kernel: [   20.538303] type=1400 audit(1339488999.379:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1173 comm="apparmor_parser"
Jun 12 03:16:46 ubuntu-web-server kernel: [   28.496056] eth0: no IPv6 routers present
Jun 12 03:58:21 ubuntu-web-server kernel: [ 2523.432984] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jun 12 03:58:21 ubuntu-web-server kernel: [ 2523.433260] ata1.01: waking up from sleep
Jun 12 03:58:21 ubuntu-web-server kernel: [ 2523.433456] ata1: soft resetting link
Jun 12 03:58:21 ubuntu-web-server kernel: [ 2523.621215] ata1.00: configured for UDMA/100
Jun 12 03:58:21 ubuntu-web-server kernel: [ 2523.636912] ata1.01: configured for UDMA/100
Jun 12 03:58:21 ubuntu-web-server kernel: [ 2523.636961] ata1: EH complete
Jun 12 04:18:49 ubuntu-web-server kernel: [ 3751.754271] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jun 12 04:18:49 ubuntu-web-server kernel: [ 3751.754525] ata1.01: waking up from sleep
Jun 12 04:18:49 ubuntu-web-server kernel: [ 3751.754729] ata1: soft resetting link
Jun 12 04:18:49 ubuntu-web-server kernel: [ 3751.941229] ata1.00: configured for UDMA/100
Jun 12 04:18:49 ubuntu-web-server kernel: [ 3751.956887] ata1.01: configured for UDMA/100
Jun 12 04:18:49 ubuntu-web-server kernel: [ 3751.956938] ata1: EH complete
Jun 12 09:31:08 ubuntu-web-server kernel: [22490.675323] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jun 12 09:31:08 ubuntu-web-server kernel: [22490.675574] ata1.01: waking up from sleep
Jun 12 09:31:08 ubuntu-web-server kernel: [22490.675777] ata1: soft resetting link
Jun 12 09:31:08 ubuntu-web-server kernel: [22490.861227] ata1.00: configured for UDMA/100
Jun 12 09:31:08 ubuntu-web-server kernel: [22490.876913] ata1.01: configured for UDMA/100
Jun 12 09:31:08 ubuntu-web-server kernel: [22490.876966] ata1: EH complete
Jun 12 12:30:09 ubuntu-web-server kernel: [33231.995781] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jun 12 12:30:09 ubuntu-web-server kernel: [33231.996092] ata1.01: waking up from sleep
Jun 12 12:30:09 ubuntu-web-server kernel: [33231.996325] ata1: soft resetting link
Jun 12 12:30:10 ubuntu-web-server kernel: [33232.185227] ata1.00: configured for UDMA/100
Jun 12 12:30:10 ubuntu-web-server kernel: [33232.200885] ata1.01: configured for UDMA/100
Jun 12 12:30:10 ubuntu-web-server kernel: [33232.200935] ata1: EH complete

```

---

### Post by rubylaser on 2012-06-12
There are time gaps in your log ranged from 20 minutes to 3 hours in your log before the disk is woken up.  Are you sure that nothing is accessing it like smartd, hdtemp, etc? Because to my eye (at least from your log here) it doesn't demonstrate it immediately waking up.

Also, Googling your error (I've never seen that before) turns up all sorts of weird causes not related to hdparm.  If it works correctly from the command line, then just do as LHammonds suggested earlier, or add it to /etc/rc.local and be done with it :)

---

### Post by Master_Taco on 2012-06-12
> **rubylaser said:**
> There are time gaps in your log ranged from 20 minutes to 3 hours in your log before the disk is woken up.  Are you sure that nothing is accessing it like smartd, hdtemp, etc? Because to my eye (at least from your log here) it doesn't demonstrate it immediately waking up.

Also, Googling your error (I've never seen that before) turns up all sorts of weird causes not related to hdparm.  If it works correctly from the command line, then just do as LHammonds suggested earlier, or add it to /etc/rc.local and be done with it :)
I re-read what I wrote, and I left out something. The disk is never allowed to actually sleep. When I force it to sleep using the -Y switch, it is woken up almost immediately, and produces that error. Each of the errors you see are from me putting the drive to sleep manually, then it waking up soon thereafter. As far as I'm aware, nothing should be accessing the disk, as backup only occurs at midnight and lasts less than 1 hour. This was never a problem before I updated to 12.04 (I was previously running 11.04). If I put the drive to sleep, or put the command to sleep after 5 minutes of inactivity, it worked just as it is intended.

---

### Post by rubylaser on 2012-06-12
So, does it work when you run this from the command line as you posted earlier?

```
sudo hdparm -S60 /dev/sdb
```

If, so can you try to add it to /etc/rc.local and reboot and see if that works?

```
echo "hdparm -S60 /dev/sdb" >> /etc/rc.local
```

---

### Post by Master_Taco on 2012-06-12
> **rubylaser said:**
> So, does it work when you run this from the command line as you posted earlier?

```
sudo hdparm -S60 /dev/sdb
```If, so can you try to add it to /etc/rc.local and reboot and see if that works?

```
echo "hdparm -S60 /dev/sdb" >> /etc/rc.local
```
It does not anymore. It used to, but won't do it anymore. I can hear the disk attempt to spin down after 5 minutes, but it is interrupted and is forced to spin back up. The interruption is audible. It seems as though there is not a log entry for this, only when I force the drive to sleep.

---

### Post by rubylaser on 2012-06-13
Remove your /etc/hdparm.conf file (empty it) and restart.  Then try again to see if you can successfully run the command.

```
 > /etc/hdparm.conf
```

---

### Post by Master_Taco on 2012-06-13
> **rubylaser said:**
> Remove your /etc/hdparm.conf file (empty it) and restart.  Then try again to see if you can successfully run the command.

```
 > /etc/hdparm.conf
```
That SEEMS to have worked, the disk fell asleep and did not produce a kernel error. But I just tried it a moment ago, I'll keep you posted.

---

### Post by Master_Taco on 2012-06-13
Bah. Turns out it didn't do anything. The drive still wakes up and creates the same error. The only difference now is the drive stays asleep for about 5 minutes, then wakes up again, produces that error, and never shuts down, unless I use the hdparm -Y switch.

---

