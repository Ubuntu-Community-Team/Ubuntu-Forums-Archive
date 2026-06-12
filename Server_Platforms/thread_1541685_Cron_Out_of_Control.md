---
title: "Cron Out of Control?"
date: 2010-07-29
forum: Server Platforms
---

### Post by cuddles71 on 2010-07-29
Hi folks. Something is making cron spawn wildly out of control on my system.

Roughly every half hour or so (it's never at an exact time, always between 22 to 37 minutes), the system starts lagging and grinding the drive like crazy. A quick ps shows this:

```
root     25884  0.0  0.2   8324  2164 ?        D    12:54   0:00 /USR/SBIN/CRON
root     25886  0.0  0.2   8324  2164 ?        D    12:54   0:00 /USR/SBIN/CRON
root     25890  0.0  0.2   8324  2164 ?        D    12:54   0:00 /USR/SBIN/CRON
root     25893  0.0  0.2   8324  2164 ?        D    12:54   0:00 /USR/SBIN/CRON
root     25895  0.0  0.2   8324  2164 ?        D    12:54   0:00 /USR/SBIN/CRON
root     25897  0.0  0.2   8324  2164 ?        D    12:54   0:00 /USR/SBIN/CRON
root     25899  0.0  0.1   8324  1936 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25903  0.0  0.1   8324  1936 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25905  0.0  0.1   8324  1936 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25910  0.0  0.1   8324  1936 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25913  0.0  0.1   8324  1936 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25931  0.0  0.2   8324  2164 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25932  0.0  0.2   8324  2164 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25933  0.0  0.2   8324  2164 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25934  0.0  0.2   8324  2164 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25935  0.0  0.2   8324  2164 ?        S    12:54   0:00 /USR/SBIN/CRON
root     25936  0.0  0.2   8324  2164 ?        S    12:54   0:00 /USR/SBIN/CRON
```

After about 2 minutes, everything goes back to normal.

I've checked the crontabs, there's NOTHING scheduled for the specific times, or frequencies that this happens. The above sample is one of the minor ones. Last night I counted 53 instances running.

What's causing this, and more importantly, how can I fix it?

---

### Post by squaregoldfish on 2010-07-29
Cron events tend to be logged in /var/log/syslog. Have a look in there and see if there's anything interesting.

Steve.

---

### Post by cuddles71 on 2010-07-29
You may be onto something there!

I did a cat/grep looking for 12:54 (the time this happened last), and found this:

```
Jul 29 12:54:37 johnnyfever console-kit-daemon[1079]: WARNING: Record was not written to disk (File too large)
Jul 29 12:54:38 johnnyfever last message repeated 5 times
```

So, my next question is, what is console-kit-daemon writing that's so large?

---

### Post by flatline on 2010-07-29
> **cuddles71 said:**
> 
So, my next question is, what is console-kit-daemon writing that's so large?

Looks like this may be an open bug... here are some links for your perusal:

[http://ubuntuforums.org/showthread.php?p=3600578](http://ubuntuforums.org/showthread.php?p=3600578)
[http://ubuntuforums.org/showthread.php?p=8885873](http://ubuntuforums.org/showthread.php?p=8885873)

---

### Post by cuddles71 on 2010-07-29
Thanks for the heads-up.

Finding nothing in /etc/init about it, I renamed the /usr/sbin/console-kit-daemon file, and copied /bin/true over. Let's hope that fixes it!

---

### Post by cuddles71 on 2010-07-29
No joy. It just hit again:

```
root     26845  0.0  0.2   8324  2200 ?        S    14:08   0:00 /USR/SBIN/CRON
root     26851  0.0  0.2   8324  2200 ?        S    14:08   0:00 /USR/SBIN/CRON
root     26852  0.0  0.2   8324  2200 ?        S    14:08   0:00 /USR/SBIN/CRON
root     26860  0.0  0.2   8324  2168 ?        D    14:08   0:00 /USR/SBIN/CRON
root     26865  0.0  0.2   8324  2116 ?        S    14:08   0:00 /USR/SBIN/CRON
root     26866  0.0  0.2   8324  2116 ?        S    14:08   0:00 /USR/SBIN/CRON
root     26867  0.0  0.1   8324  1936 ?        S    14:08   0:00 /USR/SBIN/CRON
root     26868  0.0  0.1   8324  1936 ?        S    14:08   0:00 /USR/SBIN/CRON
```

Last entry in /var/log/syslog is still from 12:54:38, so nothing of interest there.

---

### Post by cuddles71 on 2010-07-29
I will say this. While it IS still happening, it's not as excessive as before. Between 12 and 18 instances now.

---

### Post by P4man on 2010-07-30
I vaguely remember a similar issue that occured when doing upgrades (like from 8.04 -> 8.10 -> 9.04 ->..). Almost each upgrade would add a cron job, not sure for what anymore (something with mlocate and slocate?), and not remove the old one and those would then run concurrently doing basically the same thing, bringing your system to its knees.

---

### Post by cuddles71 on 2010-07-30
I've been over the entire system's cron jobs with a fine tooth comb. NOTHING scheduled for the times when this happens.

Any more suggestions?

---

### Post by P4man on 2010-07-30
perhaps run iotop when it happens?

---

### Post by linux18 on 2010-07-30
[U][B][COLOR=red]Anacron



[/COLOR][/B][/U]

---

### Post by cuddles71 on 2010-07-30
Ok, top 2 tasks are:

2671 syslog         0 B/s    37.8 K/s  0.00 %  0.00 % syslogd -u syslog
3584 root           0 B/s    19.2 K/s  0.00 %  0.00 % rpc.mountd --manage-gids

Everything else is in the list for just a half second or so, butthose two are fairly constant during the grind.

---

### Post by cuddles71 on 2010-08-01
Still getting this. Any new ideas folks?

---

### Post by P4man on 2010-08-01
20 and 40 Kb/s is nothing. Thats not going to slow anything down. Check iotop again. If nothing else is causing IO then I suspect the problem is the drive itself recalibrating or something. Have checked SMART ?

---

### Post by cuddles71 on 2010-08-01
Nope. Enabling SMART now. :)

---

### Post by cuddles71 on 2010-08-01
Ok, SMART is enabled. What should I be looking for?

---

### Post by Vegan on 2010-08-01
If you upgraded from an earlier version of Ubuntu server, you will not be able to solve the problems in any reasonable amount of time.

I installed 9.10 fresh and have had no issues.

---

### Post by cuddles71 on 2010-08-01
I can't exactly do that. This is an active server.

There HAS to be a reason for it doing this.

---

### Post by Sporkman on 2010-08-02
Maybe multiple cron daemons are running?

Try:

ps aux | grep cron

Should only be one line of output I'd think (plus another line for your "grep cron" :) )

---

### Post by cuddles71 on 2010-08-02
Just one running:

root      4135  0.0  0.1   3604  1064 ?        Ss   Aug01   0:03 /usr/sbin/cron

---

### Post by P4man on 2010-08-02
You say its a server. Is it a RAID array?  I still think the problem is closer to the harddisk than cron, or it should show up in iotop or other tools. If its the RAID controller doing its own stuff or a (S)ATA drive recalibrating or dying, then it obviously wont show there.

---

### Post by cuddles71 on 2010-08-02
No RAID array. 120GB Primary, 2TB Secondary, and 4 USB externals.

Whatever's causing it though, it's happening to either the primary or secondary, since it even happens with the externals unhooked.

---

### Post by LightningCrash on 2010-08-03
I do this to hunt stuff like that down:
`dpkg -S console-kit-daemon`
Package name is consolekit
So we run `dpkg -L consolekit`

It has stuff in logrotate.d
Apparently cron.daily and cron.monthly call logrotate.d

Try seeing where consolekit has crap in /etc:
grep -Rni console.*kit /etc|less

---

### Post by cuddles71 on 2010-08-15
Nothing found for console kit. I've completely eradicated it from the system (and went on a business trip).

Any further ideas?

---

### Post by RS_Brooks on 2010-08-15
How about telling the pam_tally security module to audit the cron? If not, there are quite a few other modules in pam (/etc/pam.d or /usr/share/pam-configs/). That would seem like the most efficent route for tracking the issue to me.

---

### Post by RS_Brooks on 2010-08-15
Actually, I was just looking and there appears to be a pam profile for cron.
 
#
# The PAM configuration file for the cron daemon
#
@include common-auth
session       required   pam_env.so
@include common-account
@include common-session-noninteractive
# Sets up user limits, please define limits for cron tasks
# through /etc/security/limits.conf
session    required   pam_limits.so

This might be worth checking into, but I've never actually used that particular PAM profile and I'm not for sure what your proficiency is configuring pam. It's located in the pam.d/cron. At any rate, maybe this will give you and idea of an angle to take on it. Good luck.

---

### Post by cuddles71 on 2010-08-16
Honestly, I don't monkey with pam at all. :)

---

### Post by LightningCrash on 2010-08-16
You could look at what cron has open
```
lsof|grep cron
```

and watch an individual process to see what it's doing (3493 is the PID in this instance)
```
sudo strace -ff -p 3493
```

---

### Post by cuddles71 on 2010-08-18
Ok, here's what it returned:

```
cron       4135       root  cwd       DIR        8,1     4096     295980 /var/spool/cron
cron       4135       root  rtd       DIR        8,1     4096          2 /
cron       4135       root  txt       REG        8,1    35744    2013496 /usr/sbin/cron
cron       4135       root  mem       REG        8,1    42504      90333 /lib/tls/i686/cmov/libnss_files-2.9.so
cron       4135       root  mem       REG        8,1    38444      90335 /lib/tls/i686/cmov/libnss_nis-2.9.so
cron       4135       root  mem       REG        8,1    87804      90330 /lib/tls/i686/cmov/libnsl-2.9.so
cron       4135       root  mem       REG        8,1    30436      90331 /lib/tls/i686/cmov/libnss_compat-2.9.so
cron       4135       root  mem       REG        8,1   256316    2033242 /usr/lib/locale/en_US.utf8/LC_CTYPE
cron       4135       root  mem       REG        8,1   962094    2033245 /usr/lib/locale/en_US.utf8/LC_COLLATE
cron       4135       root  mem       REG        8,1     9676      90326 /lib/tls/i686/cmov/libdl-2.9.so
cron       4135       root  mem       REG        8,1  1442180      90322 /lib/tls/i686/cmov/libc-2.9.so
cron       4135       root  mem       REG        8,1    99972      90171 /lib/libselinux.so.1
cron       4135       root  mem       REG        8,1    42476      90175 /lib/libpam.so.0.81.12
cron       4135       root  mem       REG        8,1       54    2033243 /usr/lib/locale/en_US.utf8/LC_NUMERIC
cron       4135       root  mem       REG        8,1     2454    2033244 /usr/lib/locale/en_US.utf8/LC_TIME
cron       4135       root  mem       REG        8,1      286    2033246 /usr/lib/locale/en_US.utf8/LC_MONETARY
cron       4135       root  mem       REG        8,1       52    2033248 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
cron       4135       root  mem       REG        8,1       34    2033249 /usr/lib/locale/en_US.utf8/LC_PAPER
cron       4135       root  mem       REG        8,1       77    2033250 /usr/lib/locale/en_US.utf8/LC_NAME
cron       4135       root  mem       REG        8,1      155    2033251 /usr/lib/locale/en_US.utf8/LC_ADDRESS
cron       4135       root  mem       REG        8,1       59    2033252 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
cron       4135       root  mem       REG        8,1       23    2033253 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
cron       4135       root  mem       REG        8,1    26048    5890049 /usr/lib/gconv/gconv-modules.cache
cron       4135       root  mem       REG        8,1      373    2033254 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
cron       4135       root  mem       REG        8,1   117348      92406 /lib/ld-2.9.so
cron       4135       root    0r      CHR        1,3                3462 /dev/null
cron       4135       root    1w      CHR        1,3                3462 /dev/null
cron       4135       root    2w      CHR        1,3                3462 /dev/null
cron       4135       root    3u      REG       0,18        5      10839 /var/run/crond.pid
```


And then trying to strace that, gave me this:

```
Process 4135 attached - interrupt to quit
restart_syscall(<... resuming interrupted call ...>
^C <unfinished ...>
Process 4135 detached
```

---

### Post by LightningCrash on 2010-08-19
Were there other cron processes running during that time?
In the beginning you said you counted 53 /usr/sbin/cron processes.... was that happening when you did the above?

---

### Post by cuddles71 on 2010-08-19
After getting rid of console-kit, the number of cron processes has dropped a LOT, but the system still hangs every half hour or so for 20-30 seconds.

---

### Post by LightningCrash on 2010-08-19
> **cuddles71 said:**
> After getting rid of console-kit, the number of cron processes has dropped a LOT, but the system still hangs every half hour or so for 20-30 seconds.

So it is then possible that the number of cron processes and the hang are not related.

I'm going to go back through and scrutinize the thread and see if there is anything else I need to ask before recommending things to check.

---

### Post by LightningCrash on 2010-08-19
> **cuddles71 said:**
> Ok, top 2 tasks are:

2671 syslog         0 B/s    37.8 K/s  0.00 %  0.00 % syslogd -u syslog
3584 root           0 B/s    19.2 K/s  0.00 %  0.00 % rpc.mountd --manage-gids

Everything else is in the list for just a half second or so, butthose two are fairly constant during the grind.

I saw mountd. Do you have any NFS mounts?

If so, are they hard or soft mounted? If you have any kind of network connectivity troubles on a hard mount then your box will be pretty screwy until the mount comes back.
I have a hard mount on my desktop, and when I unplug my network cable I can't even open a new xterm window!

---

### Post by cuddles71 on 2010-08-19
No NFS mounts. All mounts are either internal, or USB.

In fact, here's the current mount list:

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-19-server/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /mnt/music type ext3 (rw,noatime)
/dev/sdc1 on /mnt/vault type ext3 (rw,noatime)
/dev/sdd1 on /mnt/audio type ext3 (rw,noatime)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
```

---

### Post by LightningCrash on 2010-08-19
Well if you're not using NFS then you can remove the NFS kernel server

```

sudo apt-get remove nfs-kernel-server

```

---

### Post by cuddles71 on 2010-08-19
Removed. Still getting the lockup.

---

### Post by LightningCrash on 2010-08-20
> **cuddles71 said:**
> Removed. Still getting the lockup.
At this point I would watch `top` like a hawk until I could catch it in action.

---

### Post by cuddles71 on 2010-08-20
Watching it while we're on the air tonight (it causes the broadcaster to stutter terribly when it happens), but here's what things look like normally:

```
20549 root      20   0  161m 6936 2092 S  6.3  0.7  53:53.08 sc_trans
 3411 root      20   0 10636 1916  520 S  0.7  0.2  59:24.79 lcd4linux
12645 root      20   0  2580 1248  904 R  0.7  0.1   0:00.62 top
    4 root      15  -5     0    0    0 S  0.3  0.0  14:16.62 ksoftirqd/0
 3908 root      20   0  5180 1000  792 S  0.3  0.1   2:12.99 hald-addon-stor
```

---

### Post by cuddles71 on 2010-08-20
Bingo! Caught it right in the middle of a stutter!

```
 6223 nobody    20   0 16724 5076 3400 R  5.3  0.5   0:06.19 smbd
20549 root      20   0  161m 6936 2092 S  4.3  0.7  55:59.91 sc_trans
12249 root      20   0 12532 4404 3532 S  0.3  0.4   0:00.44 sshd
12645 root      20   0  2580 1256  904 R  0.3  0.1   0:09.67 top
13780 www-data  20   0 40020  20m 2632 S  0.3  2.0   0:24.02 python
    1 root      20   0  3084 1776  460 S  0.0  0.2   0:05.69 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0  14:17.99 ksoftirqd/0
```

But now what do I do with it?

Edit: There were a bunch of cron entriles further down, but all of them said 0 0 0 0 for the various columns, and i wasn't able to grab everything at once.

---

### Post by Sporkman on 2010-08-20
smbd = Samba ..?

---

### Post by cuddles71 on 2010-08-20
Yep. That server shares music drives to the LAN.

---

### Post by LightningCrash on 2010-08-20
> **cuddles71 said:**
> Yep. That server shares music drives to the LAN.

The broadcast is the sc_trans, shoutcast transcoder, right?
Is this the only thing that hangs every 30 minutes?


I notice you have it at a priority of 20 (meaning it is at a very, very low priority)... you might try bumping it to -10 as a test.

pgrep sc_trans
that will return the PID of sc_trans
then
renice -n -10 -p 40939

where 40939 is the PID of sc_trans

---

### Post by cuddles71 on 2010-08-20
Actually, the whole system hangs when it happens. But I'll try giving the transcoder a higher priority.

---

### Post by LightningCrash on 2010-08-20
> **cuddles71 said:**
> Actually, the whole system hangs when it happens. But I'll try giving the transcoder a higher priority.

I edited my last post, I had intermixed Priority and Nice (sorry)

The console, samba and shoutcast all display hanging behavior when this happens?

---

### Post by cuddles71 on 2010-08-20
> **LightningCrash said:**
> The broadcast is the sc_trans, shoutcast transcoder, right?
Is this the only thing that hangs every 30 minutes?


I notice you have it at a priority of 20 (meaning it is at a very, very low priority)... you might try bumping it to -10 as a test.

pgrep sc_trans
that will return the PID of sc_trans
then
renice -n -10 -p 40939

where 40939 is the PID of sc_trans

That gave me this:

```
20549: old priority 0, new priority 0
```

---

### Post by LightningCrash on 2010-08-20
> **cuddles71 said:**
> That gave me this:

```
20549: old priority 0, new priority 0
```

I edited my last post, I had intermixed Priority and Nice (sorry)

Next troubleshooting step, if renicing doesn't help, is to stop samba for a while. It could be samba. It could be your USB drives if they're shared out over Samba. I know the fuse-ntfs driver can bog down a good box without much effort.

---

### Post by cuddles71 on 2010-08-20
Well, so far no more hangs... But since the external drives are all ext3, would it really be fuse-ntfs?

Edit: I spoke too soon. Just hung for 12 seconds. Couldn't even get the ssh window to respond so I could run top. :(

---

### Post by LightningCrash on 2010-08-20
are you getting anything in dmesg, syslog, or messages during this time?

---

### Post by cuddles71 on 2010-08-20
Nothing. It's like the system forgets what it's doing for a few seconds.

---

### Post by LightningCrash on 2010-08-21
you might ping it nonstop and see if it stops responding to pings, too

if it's dropping packets, that's a pretty bad hang

---

### Post by cuddles71 on 2010-08-21
Left a ping running all night. No drops, even during the lockups.

---

### Post by LightningCrash on 2010-08-21
> **cuddles71 said:**
> Left a ping running all night. No drops, even during the lockups.

That makes it sound like an errant process on the machine. In my experience when the kernel has been the problem, the box won't respond to ICMP.

ps -ef, prune out any sensitive data, let's walk through and make sure you don't have anything running that you don't need.

---

### Post by cuddles71 on 2010-08-21
Here we go, nothing pruned. :)

```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Aug01 ?        00:00:05 /sbin/init
root         2     0  0 Aug01 ?        00:00:00 [kthreadd]
root         3     2  0 Aug01 ?        00:00:00 [migration/0]
root         4     2  0 Aug01 ?        00:15:09 [ksoftirqd/0]
root         5     2  0 Aug01 ?        00:00:00 [watchdog/0]
root         6     2  0 Aug01 ?        00:00:00 [events/0]
root         7     2  0 Aug01 ?        00:00:00 [khelper]
root         8     2  0 Aug01 ?        00:00:00 [kstop/0]
root         9     2  0 Aug01 ?        00:00:00 [kintegrityd/0]
root        10     2  0 Aug01 ?        00:00:01 [kblockd/0]
root        11     2  0 Aug01 ?        00:00:00 [kacpid]
root        12     2  0 Aug01 ?        00:00:00 [kacpi_notify]
root        13     2  0 Aug01 ?        00:00:00 [cqueue]
root        14     2  0 Aug01 ?        00:00:00 [ata/0]
root        15     2  0 Aug01 ?        00:00:00 [ata_aux]
root        16     2  0 Aug01 ?        00:00:00 [ksuspend_usbd]
root        17     2  0 Aug01 ?        00:00:00 [khubd]
root        18     2  0 Aug01 ?        00:00:00 [kseriod]
root        19     2  0 Aug01 ?        00:00:00 [kmmcd]
root        20     2  0 Aug01 ?        00:00:00 [btaddconn]
root        21     2  0 Aug01 ?        00:00:00 [btdelconn]
root        24     2  0 Aug01 ?        00:01:51 [kswapd0]
root        25     2  0 Aug01 ?        00:00:00 [aio/0]
root        26     2  0 Aug01 ?        00:00:00 [ecryptfs-kthrea]
root        29     2  0 Aug01 ?        00:00:00 [scsi_eh_0]
root        30     2  0 Aug01 ?        00:00:00 [scsi_eh_1]
root        31     2  0 Aug01 ?        00:00:00 [kstriped]
root        32     2  0 Aug01 ?        00:00:00 [kmpathd/0]
root        33     2  0 Aug01 ?        00:00:00 [kmpath_handlerd]
root        34     2  0 Aug01 ?        00:00:00 [ksnapd]
root        35     2  0 Aug01 ?        00:00:00 [kondemand/0]
root        36     2  0 Aug01 ?        00:00:00 [krfcommd]
root       281     2  0 Aug01 ?        00:00:00 [scsi_eh_2]
root       284     2  0 Aug01 ?        00:00:02 [usb-storage]
root       305     2  0 Aug01 ?        00:00:00 [khpsbpkt]
root       334     2  0 Aug01 ?        00:00:00 [knodemgrd_0]
root       552     2  0 Aug01 ?        00:00:00 [scsi_eh_3]
root       558     2  0 Aug01 ?        00:00:57 [usb-storage]
root       757     2  0 Aug01 ?        00:06:32 [kjournald]
root       822     2  0 Aug01 ?        00:00:00 [scsi_eh_4]
root       823     2  0 Aug01 ?        00:00:03 [usb-storage]
root       896     1  0 Aug01 ?        00:00:00 /sbin/udevd --daemon
root      1340     2  0 Aug01 ?        00:00:00 [kpsmoused]
nobody    1734 13151  0 20:41 ?        00:00:00 /usr/sbin/smbd -D
root      2044     1  0 Aug01 ?        00:00:35 /usr/sbin/apache2 -k start
root      2082     2  0 Aug01 ?        00:00:12 [kjournald]
root      2083     2  0 Aug01 ?        00:00:00 [kjournald]
root      2084     2  0 Aug01 ?        00:00:00 [kjournald]
root      2541     1  0 Aug01 tty4     00:00:00 /sbin/getty 38400 tty4
root      2542     1  0 Aug01 tty5     00:00:00 /sbin/getty 38400 tty5
root      2549     1  0 Aug01 tty2     00:00:00 /sbin/getty 38400 tty2
root      2550     1  0 Aug01 tty3     00:00:00 /sbin/getty 38400 tty3
root      2551     1  0 Aug01 tty6     00:00:00 /sbin/getty 38400 tty6
root      2621     1  0 Aug01 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2666     1  0 Aug01 ?        00:03:34 /sbin/syslogd -u syslog
root      2689     1  0 Aug01 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      2691     1  0 Aug01 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
108       2714     1  0 Aug01 ?        00:26:29 /bin/dbus-daemon --system
root      2761     1  0 Aug01 ?        00:00:01 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
bind      2824     1  0 Aug01 ?        00:00:00 /usr/sbin/named -u bind
ntp       2951     1  0 Aug01 ?        00:00:07 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 126:132 -g
root      2998     1  0 Aug01 ?        00:00:13 /usr/sbin/sshd
root      3038     1  0 Aug01 ?        00:00:22 /usr/sbin/lircd --device=/dev/lirc0
root      3081     1  0 Aug01 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     3128  3081  0 Aug01 ?        00:25:15 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
clamav    3295     1  0 Aug01 ?        00:00:20 /usr/bin/freshclam -d --quiet
root      3307     1  0 Aug01 ?        00:00:47 ddclient - sleeping for 60 seconds
root      3411     1  0 Aug01 ?        01:02:42 /usr/sbin/lcd4linux
www-data  3442  2044  0 20:45 ?        00:00:00 /usr/sbin/apache2 -k start
root      3533     2  0 Aug01 ?        00:00:00 [rpciod/0]
root      3668     1  0 Aug01 ?        00:00:00 /usr/lib/postfix/master
postfix   3685  3668  0 Aug01 ?        00:00:00 qmgr -l -t fifo -u
root      3733     1  0 Aug01 ?        00:00:07 /usr/sbin/winbindd
root      3741  3733  0 Aug01 ?        00:00:02 /usr/sbin/winbindd
root      3763     1  0 Aug01 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive -inetd_compat -inetd_ipv6
root      3804     1  0 Aug01 ?        00:00:00 /usr/sbin/dovecot
root      3806  3804  0 Aug01 ?        00:00:00 dovecot-auth
118       3824     1  0 Aug01 ?        00:03:21 /usr/sbin/hald
root      3827  3824  0 Aug01 ?        00:00:00 hald-runner
root      3857  3827  0 Aug01 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3
dovecot   3891  3804  0 Aug01 ?        00:00:00 pop3-login
dovecot   3894  3804  0 Aug01 ?        00:00:00 pop3-login
dovecot   3895  3804  0 Aug01 ?        00:00:00 pop3-login
dovecot   3897  3804  0 Aug01 ?        00:00:00 imap-login
dovecot   3899  3804  0 Aug01 ?        00:00:00 imap-login
dovecot   3902  3804  0 Aug01 ?        00:00:00 imap-login
root      3908  3827  0 Aug01 ?        00:02:20 hald-addon-storage: polling /dev/sr0 (every 2 sec)
118       3920  3827  0 Aug01 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      3957     1  0 Aug01 ?        00:00:03 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
root      3977     1  0 Aug01 ?        00:00:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      3980  3977  0 Aug01 ?        00:00:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      3984  3980  0 Aug01 tty7     00:28:51 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7
root      4012     1  0 Aug01 ?        00:00:05 /usr/sbin/cupsd
root      4034     1  0 Aug01 ?        00:00:00 /usr/bin/system-tools-backends
daemon    4105     1  0 Aug01 ?        00:00:00 /usr/sbin/atd
root      4135     1  0 Aug01 ?        00:01:21 /usr/sbin/cron
root      4144     2  0 Aug02 ?        00:00:00 [cifsoplockd]
root      4147     2  0 Aug02 ?        00:00:00 [cifsdnotifyd]
www-data  4244     1  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
www-data  4277     1  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
www-data  4302     1  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
www-data  4307     1  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
root      4329     1  0 Aug01 ?        00:02:16 /usr/sbin/pwrstatd
www-data  4363  4302  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
www-data  4364  4307  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
www-data  4365  4244  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
www-data  4366  4277  0 Aug01 ?        00:00:00 /usr/bin/php-cgi
root      4395     1  0 Aug01 tty1     00:00:00 /sbin/getty 38400 tty1
root      4407  3827  0 Aug01 ?        00:01:21 hald-addon-hid-ups: listening on /dev/usb/hiddev0
root      4517     1  0 Aug20 ?        00:00:00 /usr/bin/SCREEN.real -D -m centerim -a
root      4519  4517  0 Aug20 pts/1    00:00:07 centerim -a
www-data  4620  2044  0 20:48 ?        00:00:00 /usr/sbin/apache2 -k start
root      4823     1  0 Aug01 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login
root      4826  3980  0 Aug01 ?        00:02:08 x-session-manager
root      4877  4826  0 Aug01 ?        00:00:04 /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session x-session-manager
root      4882     1  0 Aug01 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
root      4883     1  0 Aug01 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
root      4886     1  0 Aug01 ?        00:01:34 /usr/lib/libgconf2-4/gconfd-2
root      4890     1  0 Aug01 ?        00:00:05 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
root      4900  4826  0 Aug01 ?        00:00:08 /usr/bin/metacity --replace
root      4910     1  0 Aug01 ?        00:00:00 /usr/lib/gvfs/gvfsd
root      4930     1  0 Aug01 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /root/.gvfs
root      4965  4826  0 Aug01 ?        00:01:49 gnome-panel
root      4966  4826  0 Aug01 ?        00:00:03 nautilus
root      4968     1  0 Aug01 ?        00:00:27 /usr/lib/gvfs/gvfs-hal-volume-monitor
root      4970     1  0 Aug01 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
root      4972     1  0 Aug01 ?        00:00:28 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
root      4975  4826  0 Aug01 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.8/firefox
root      4985  4975  0 Aug01 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.8/run-mozilla.sh /usr/lib/firefox-3.6.8/firefox-bin
root      4991  4826  0 Aug01 ?        00:00:00 /usr/lib/evolution/2.26/evolution-alarm-notify
root      4993  4985  1 Aug01 ?        05:10:35 /usr/lib/firefox-3.6.8/firefox-bin
root      4996     1  0 Aug01 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
root      5016     1  0 Aug01 ?        00:04:47 gnome-power-manager
root      5023     1  0 Aug01 ?        00:05:55 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/2
root      5026     1  0 Aug01 ?        00:01:50 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=18
root      5029     1  0 Aug01 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=24
root      5032     1  0 Aug01 ?        00:09:16 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=30
root      5416     1  0 Aug01 ?        00:00:39 gnome-screensaver
root      5423     1  0 Aug01 ?        00:38:17 motion
root      5486 12258  0 20:50 pts/0    00:00:00 ps -ef
johnny    5788     1  0 Aug01 ?        00:58:42 eggdrop eggdrop.conf
johnny    6096     1  0 Aug01 ?        00:03:24 eggdrop filebot.conf
root      7124  4135  0 Aug10 ?        00:00:00 /USR/SBIN/CRON
root      7129  4135  0 Aug19 ?        00:00:00 /USR/SBIN/CRON
root      7170  7124  0 Aug10 ?        00:00:00 /bin/sh -c /usr/local/autodj/control/timer/currdj.sh
root      7171  7170  0 Aug10 ?        00:00:00 /bin/bash /usr/local/autodj/control/timer/currdj.sh
root      7197  7129  0 Aug19 ?        00:00:00 /bin/sh -c rdate -s time-a.nist.gov
root      7198  7197  0 Aug19 ?        00:00:00 rdate -s time-a.nist.gov
root      7395  7171  0 Aug10 ?        00:00:00 ftp -i -v -n ftp.kjsr.net
johnny    7562     1  0 Aug01 ?        00:03:17 eggdrop triviabot.conf
johnny    7567     1  0 Aug01 ?        00:03:03 eggdrop tordbot.conf
root      8182  4135  0 Aug10 ?        00:00:00 /USR/SBIN/CRON
root      8252  4135  0 Aug10 ?        00:00:00 /USR/SBIN/CRON
root      8255  4135  0 Aug10 ?        00:00:00 /USR/SBIN/CRON
root      8714     1  0 Aug01 ?        00:00:00 /usr/lib/notify-osd/notify-osd
root      9446  4135  0 Aug10 ?        00:00:00 /USR/SBIN/CRON
root     11776     1  0 Aug17 ?        00:00:00 pure-ftpd (SERVER)                                                                                                                                                                                                    
root     12249  2998  0 Aug20 ?        00:00:26 sshd: root@pts/0 
root     12258 12249  0 Aug20 pts/0    00:00:00 -bash
root     12882  4135  0 06:03 ?        00:00:00 /USR/SBIN/CRON
root     13148     1  0 Aug15 ?        00:00:06 /usr/sbin/nmbd -D
root     13151     1  0 Aug15 ?        00:00:02 /usr/sbin/smbd -D
root     13152 13151  0 Aug15 ?        00:00:00 /usr/sbin/smbd -D
root     13265 12882  0 06:07 ?        00:00:00 [sh] <defunct>
root     15486     1  0 06:07 ?        00:00:00 /bin/bash /bin/jreset
root     15487 15486  6 06:07 ?        00:57:54 ./sc_trans sc_trans.conf
root     15679     2  0 Aug02 ?        00:03:09 [pdflush]
postfix  17679  3668  0 19:59 ?        00:00:00 pickup -l -t fifo -u -c
www-data 21507     1  0 Aug15 ?        00:00:09 /usr/sbin/lighttpd -f /etc/lighttpd/lighttpd.conf
root     22830     1  0 Aug15 ?        00:00:11 /usr/local/services/bin/services
root     28983  3733  0 Aug01 ?        00:00:00 /usr/sbin/winbindd
root     28984  3733  0 Aug01 ?        00:00:02 /usr/sbin/winbindd
root     32321     2  0 20:36 ?        00:00:00 [scsi_eh_5]
root     32323     2  0 20:36 ?        00:00:00 [usb-storage]
root     32605     2  0 Aug02 ?        00:01:49 [pdflush]

```

---

### Post by Sporkman on 2010-08-21
I tried googling these two, nothing came up...

```
root     15486     1  0 06:07 ?        00:00:00 /bin/bash /bin/jreset
root     22830     1  0 Aug15 ?        00:00:11 /usr/local/services/bin/services

```

---

### Post by LightningCrash on 2010-08-21
You're logged into X as root, that would be the first thing I would fix.
If you're not at the physical box you can always /etc/init.d/gdm restart

Firefox is eating up the majority of the CPU there. It's probably running under X and would be killed by the gdm restart.

If you don't need lcd4linux I would remove that as well.
If you don't need motion, that can go too. It look like you're using this box for quite a bit of stuff!

---

### Post by cuddles71 on 2010-08-21
> **Sporkman said:**
> I tried googling these two, nothing came up...

```
root     15486     1  0 06:07 ?        00:00:00 /bin/bash /bin/jreset
root     22830     1  0 Aug15 ?        00:00:11 /usr/local/services/bin/services

```

Both of those are part of the station's transcoder.

---

### Post by cuddles71 on 2010-08-21
> **LightningCrash said:**
> You're logged into X as root, that would be the first thing I would fix.
If you're not at the physical box you can always /etc/init.d/gdm restart

Firefox is eating up the majority of the CPU there. It's probably running under X and would be killed by the gdm restart.

If you don't need lcd4linux I would remove that as well.
If you don't need motion, that can go too. It look like you're using this box for quite a bit of stuff!

We use X (and firefox) for a "tagboard" type display to monitor the station. Same with lcd4linux.

What's motion?

---

### Post by LightningCrash on 2010-08-22
> **cuddles71 said:**
> We use X (and firefox) for a "tagboard" type display to monitor the station. Same with lcd4linux.

What's motion?
motion is a video software that only records when it detects motion.

---

