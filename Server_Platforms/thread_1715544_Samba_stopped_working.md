---
title: "Samba stopped working?"
date: 2011-03-27
forum: Server Platforms
---

### Post by G1ZmO65 on 2011-03-27
Hiya,

Got a wee issue this morning.

History:
Boot HDD failure last week. (Ubuntu 8.04 server)
Fortunately 95% of data was on the other HDDs (with the exception of MY home folder lol)
Rebuilt server and put 10.10 server on a new drive.
Connected the old data drives and confirmed they were ok
Backed up all data (again)
Set up fstab, interfaces, ssh, samba
All seemed fine last night. Could access via ssh and samba shares from both ubuntu desktop and XP

This morning I installed mediawiki successfully 

Noticed that I couldnt access the samba shares from ubuntu desktop nor from XP

Any idea what might have happened?

Thanks

Paul

---

### Post by falko on 2011-03-27
Are there any errors in your logs?

---

### Post by G1ZmO65 on 2011-03-27
Actually I can access the shares via the IP address but not the servername

From XP \\192.168.1.10\paul does work but \\callisto\paul does not

I'm assuming something during the mediawiki setup has changed something but can't see it yet...

---

### Post by G1ZmO65 on 2011-03-27
```
[2011/03/27 09:56:54.506227,  1] smbd/service.c:1251(close_cnum)
  xw8200 (192.168.1.100) closed connection to service 200a
[2011/03/27 09:56:54.509661,  1] smbd/service.c:1251(close_cnum)
  xw8200 (192.168.1.100) closed connection to service 250a
[2011/03/27 09:56:54.513662,  1] smbd/service.c:1251(close_cnum)
  xw8200 (192.168.1.100) closed connection to service 250b
[2011/03/27 11:04:29.586597,  1] smbd/service.c:1070(make_connection_snum)
  xw8200 (192.168.1.100) connect to service paul initially as user paul (uid=1000, gid=1000) (pid 1187)
```

from the samba log for this workstation

Thanks

tbh I'm not sure which error logs I should be looking at :P
The ones on the server or on this machine?

---

### Post by SeijiSensei on 2011-03-27
That sounds like a name service problem, not a Samba problem.  Do you have a DNS server or use hosts files?  If the latter, check to make sure there's an entry for callisto in them.  If you have an internal DNS server, check the client's /etc/resolv.conf files to make sure it's being used.

---

### Post by G1ZmO65 on 2011-03-27
No, I'm not running a DNS server.

Nor have I used hosts files before. It was working the other night and the only thing I've installed since then was the mediawiki. Wondering if that incorporates some DNS settings.... tbh I dont know how to check

---

### Post by G1ZmO65 on 2011-03-27
hmmm. I restarted the server. No change.

I disabled the networking service and re-enabled it.

voila! it's working again.

Not happy about that "fix" as I still don't know the cause though I have a possible work around.

Any further ideas would be appreciated.

Thanks

Paul

---

### Post by G1ZmO65 on 2011-03-29
Further to this

The server seemed stable enough for a while after reboot but is now crashing out occasionally.

Samba stops, as does SSH and I'm unable to ping it either.

Any suggestions?


```
paul@callisto:~$ dmesg | tail
[   10.239712] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   10.239906] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   10.330133] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   10.686788] type=1400 audit(1301426940.902:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=687 comm="apparmor_parser"
[   10.687374] type=1400 audit(1301426940.902:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=687 comm="apparmor_parser"
[   10.687710] type=1400 audit(1301426940.902:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=687 comm="apparmor_parser"
[   10.698539] type=1400 audit(1301426940.914:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=688 comm="apparmor_parser"
[   10.705040] type=1400 audit(1301426940.922:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=689 comm="apparmor_parser"
[   11.249310] type=1400 audit(1301426941.466:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=789 comm="apparmor_parser"
[   20.080052] eth0: no IPv6 routers present

```

---

### Post by G1ZmO65 on 2011-03-29
tbh I'm not really sure this is even an error message.

Could someone point me in the right direction of where to look?

I'm assuming it should be in /var/log/

The recent files there are: 

```
paul@callisto:/var/log$ ls -l -t
total 7464
-rw-r----- 1 syslog adm  1856740 2011-03-29 21:40 auth.log
-rw-r----- 1 syslog adm   356726 2011-03-29 21:40 syslog
-rw-rw-r-- 1 root   utmp  293168 2011-03-29 20:29 lastlog
-rw-rw-r-- 1 root   utmp  128640 2011-03-29 20:29 wtmp
-rw-r----- 1 syslog adm    63156 2011-03-29 20:29 debug
-rw-r----- 1 syslog adm   324207 2011-03-29 20:29 kern.log
-rw-r----- 1 syslog adm    10572 2011-03-29 20:29 daemon.log
-rw-r--r-- 1 root   root     772 2011-03-29 20:29 boot.log
-rw-r----- 1 syslog adm   262133 2011-03-29 20:29 messages
-rw-r----- 1 root   adm    35300 2011-03-29 20:29 dmesg
-rw-r--r-- 1 root   root  178973 2011-03-29 20:29 udev
-rw-r----- 1 root   adm    35318 2011-03-29 18:31 dmesg.0

```

```
paul@callisto:/var/log$ cat syslog | tail
Mar 29 20:29:02 callisto /etc/mysql/debian-start[866]: Checking for insecure root accounts.
Mar 29 20:29:02 callisto /etc/mysql/debian-start[870]: Triggering myisam-recover for all MyISAM tables
Mar 29 20:29:10 callisto kernel: [   20.080052] eth0: no IPv6 routers present
Mar 29 20:39:01 callisto CRON[1097]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 29 21:09:02 callisto CRON[1290]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 29 21:17:02 callisto CRON[1306]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 29 21:39:01 callisto CRON[1324]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 29 21:40:01 callisto CRON[1333]: (root) CMD (sudo ./mnt/200a/paul/Server\ Backups/backupservfiles.sh)
Mar 29 21:40:02 callisto CRON[1332]: (CRON) error (grandchild #1333 failed with exit status 1)
Mar 29 21:40:02 callisto CRON[1332]: (CRON) info (No MTA installed, discarding output)
```
```

paul@callisto:/var/log$ cat debug | tail
Mar 29 20:29:00 callisto kernel: [    2.926751] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 131087
Mar 29 20:29:00 callisto kernel: [    2.926844] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 131086
Mar 29 20:29:00 callisto kernel: [    2.926860] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 131085
Mar 29 20:29:00 callisto kernel: [    2.926875] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 131084
Mar 29 20:29:00 callisto kernel: [    2.926890] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 131083
Mar 29 20:29:00 callisto kernel: [    9.405183] irda_init()
Mar 29 20:29:00 callisto kernel: [   10.239689]   alloc irq_desc for 22 on node -1
Mar 29 20:29:00 callisto kernel: [   10.239693]   alloc kstat_irqs on node -1
Mar 29 20:29:00 callisto kernel: [   10.239906] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
Mar 29 20:29:10 callisto kernel: [   20.080052] eth0: no IPv6 routers present
```

---

