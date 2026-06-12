---
title: "100% percent CPU usage due to Perl?"
date: 2006-12-12
forum: Server Platforms
---

### Post by lubod on 2006-12-12
Hello, I have a Dapper (6.06 LTS) Server set up, and it seems to be doing almost everything I've tried so far. :) So kudos to the developers for a nice, useful piece of software (or actually many pieces of software).

I am however noticing what seems like excessive CPU usage, often 100%, which top attributes to Perl.

Now I should give some background as to what is installed. I began with the LAMP option on the Dapper Server install CD, then added webmin 1.300 from webmin.com, and then used webmin's built in GUI to apt-get to add other things like the ISC DHCP server v.3, etc.

This is an abbreviated copy/paste of what top showed:

top - 16:30:42 up 5 days, 36 min,  1 user,  load average: 1.02, 1.02, 1.00
Tasks:  74 total,   3 running,  71 sleeping,   0 stopped,   0 zombie
Cpu(s): 46.2% us,  4.0% sy,  0.0% ni, 49.8% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   2074604k total,   541696k used,  1532908k free,   164440k buffers
Swap:  3196892k total,        0k used,  3196892k free,   233768k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8148 root      20   0 47148  43m 1572 R   78  2.2   2941:02 perl

Note the 78% CPU, and the load average hovering around 1.0.

Do I have anything to worry about? It still performs its DHCP and IP Forwarding functions with no apparent problem so far.

---

### Post by gnaunited on 2006-12-12
Does the usage continue after a reboot? I have found that when I used it to install packages it locked up for whatever reason and even though the request had ended it continued to try and finish what it started for a while. Try a webmin server restart, then if that doesn't work then try a whole server reboot.

Also - what do you have running that is taking up so much ram? Is this a production server that needs 2 gigs of ram in the first place?

---

### Post by lubod on 2006-12-12
The locking up (not really locking up so much as taking 100% CPU) while installing packages is something I experienced too.

FYI in my case it appears it kept hogging CPU time because while apt-get from a terminal shows when it is stuck waiting for media (like a CD-ROM) to be inserted, the corresponding part of webmin simply keeps trying and trying without notifying you that it needs anything. So inserting the CD it wanted cures that a lot of the time for me, maybe even always.

It has 2GB RAM not so much because it has to, just because it did before I installed Ubuntu. This thing was suffering the blight that is Windows, and so it was configured in the "the more RAM the better" method that most people apply to Windows.

Right now the server is being tested and hooked up only to the company I work for, so for now restarting webmin or the entire server may be a temporary fix, but soon it is expected to be in production, and then restarting anything will be undesirable, to say the least, so I was hoping for a "non-restart" fix.

Maybe I should just kill the offending Perl process? I don't know if it will respawn automatically, short of a restart though.

---

### Post by gnaunited on 2006-12-12
You should be able to kill webmin with no ill effects - it is just for managing the server - it doesn't actually run anything imporant. But if you are also running usermin then it might be an issue.
Does it sky-rocket like that after each restart or will restarting help?

---

### Post by lubod on 2006-12-12
I still don't know that it is Webmin that is the culprit, it may be the culprit but it isn't certain. What is certain is top says "Perl" is the CPU hogging process, and I do think Webmin uses Perl (perhaps it is written in Perl, I think I read this on their site?)

Have not had a good chance to reboot anything yet, probably after business hours (it's about 3 PM here and business hours end at 6). But if I am to kill a process instead of an outright reboot, which one? Perl itself? I suppose I can copy down what command kills and restarts Webmin and execute those through SSH.

To the best of my knowledge we are not using Usermin for anything much, so that should not be a problem.

---

### Post by gnaunited on 2006-12-12
hmm, normally it will say that webmin is the process name. I am really confused as to why this is happening. Can you post the output of "ps aux"? I am wondering if there is something else that is calling it.

---

### Post by lubod on 2006-12-12
I'm wondering if there is something wrong or what. ps aux shows:

ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1564   528 ?        S    Dec06   0:02 init [2]      
root         2  0.0  0.0      0     0 ?        S    Dec06   0:06 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   Dec06   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    Dec06   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S    Dec06   0:06 [migration/1]
root         6  0.0  0.0      0     0 ?        SN   Dec06   0:00 [ksoftirqd/1]
root         7  0.0  0.0      0     0 ?        S    Dec06   0:00 [watchdog/1]
root         8  0.0  0.0      0     0 ?        S<   Dec06   0:00 [events/0]
root         9  0.0  0.0      0     0 ?        S<   Dec06   0:00 [events/1]
root        10  0.0  0.0      0     0 ?        S<   Dec06   0:00 [khelper]
root        11  0.0  0.0      0     0 ?        S<   Dec06   0:00 [kthread]
root        14  0.0  0.0      0     0 ?        S<   Dec06   0:00 [kblockd/0]
root        15  0.0  0.0      0     0 ?        S<   Dec06   0:00 [kblockd/1]
root        16  0.0  0.0      0     0 ?        S<   Dec06   0:00 [kacpid]
root       120  0.0  0.0      0     0 ?        S    Dec06   0:00 [pdflush]
root       121  0.0  0.0      0     0 ?        S    Dec06   0:00 [pdflush]
root       123  0.0  0.0      0     0 ?        S<   Dec06   0:00 [aio/0]
root       122  0.0  0.0      0     0 ?        S    Dec06   0:00 [kswapd0]
root       124  0.0  0.0      0     0 ?        S<   Dec06   0:00 [aio/1]
root       717  0.0  0.0      0     0 ?        S<   Dec06   0:00 [kseriod]
root       800  0.0  0.0      0     0 ?        S    Dec06   0:00 [kirqd]
root      1766  0.0  0.0      0     0 ?        S<   Dec06   0:00 [ata/0]
root      1767  0.0  0.0      0     0 ?        S<   Dec06   0:00 [ata/1]
root      1768  0.0  0.0      0     0 ?        S<   Dec06   0:00 [ata_hotplug/0]
root      1769  0.0  0.0      0     0 ?        S<   Dec06   0:00 [ata_hotplug/1]
root      1773  0.0  0.0      0     0 ?        S<   Dec06   0:00 [scsi_eh_0]
root      1774  0.0  0.0      0     0 ?        S<   Dec06   0:00 [scsi_eh_1]
root      1842  0.0  0.0      0     0 ?        S<   Dec06   0:00 [khubd]
root      1953  0.0  0.0      0     0 ?        S    Dec06   0:03 [kjournald]
root      2127  0.0  0.0   2108   556 ?        S<s  Dec06   0:00 /sbin/udevd --d
root      2950  0.0  0.0      0     0 ?        S    Dec06   0:00 [shpchpd_event]
root      3136  0.0  0.0      0     0 ?        S<   Dec06   0:00 [hda_codec/0]
root      3137  0.0  0.0      0     0 ?        S<   Dec06   0:00 [hda_codec/1]
root      3789  0.6  0.0   1684   496 ?        Ss   Dec06  54:12 /bin/dd bs 1 if
klog      3791  0.4  0.0   2408  1328 ?        Ss   Dec06  41:20 /sbin/klogd -P
root      3831  0.0  0.0   2644  1316 ?        S    Dec06   0:00 /bin/sh /usr/bi
mysql     3895  0.0  0.8 126444 17100 ?        Sl   Dec06   0:00 /usr/sbin/mysql
root      3896  0.0  0.0   1548   500 ?        S    Dec06   0:00 logger -p daemo
root      3976  0.0  0.0   4768  1056 ?        Ss   Dec06   0:00 /usr/sbin/sshd
root      4011  0.0  0.0   1628   300 ?        Ss   Dec06   0:00 /sbin/mdadm -F
daemon    4056  0.0  0.0   1800   396 ?        Ss   Dec06   0:00 /usr/sbin/atd
root      4066  0.0  0.0   2120   844 ?        Ss   Dec06   0:00 /usr/sbin/cron
root      4121  0.0  0.0   1560   488 tty1     Ss+  Dec06   0:00 /sbin/getty 384
root      4124  0.0  0.0   1560   492 tty2     Ss+  Dec06   0:00 /sbin/getty 384
root      4125  0.0  0.0   1560   488 tty3     Ss+  Dec06   0:00 /sbin/getty 384
root      4126  0.0  0.0   1560   488 tty4     Ss+  Dec06   0:00 /sbin/getty 384
root      4128  0.0  0.0   1564   492 tty5     Ss+  Dec06   0:00 /sbin/getty 384
root      4129  0.0  0.0   1564   492 tty6     Ss+  Dec06   0:00 /sbin/getty 384
root      9157  0.0  0.0   4660  1600 ?        Ss   Dec07   0:00 /usr/lib/postfi
postgres 17234  0.0  0.1  16976  2116 ?        S    Dec07   0:00 /usr/lib/postgr
postgres 17237  0.0  0.0   7776  1796 ?        S    Dec07   0:00 postgres: stats
postgres 17238  0.0  0.0   6916  1008 ?        S    Dec07   0:00 postgres: stats
dhcpd    28819  0.0  0.0   2820  1360 ?        Ss   Dec08   0:00 /usr/sbin/dhcpd
root     31015  0.0  0.0   1720   552 ?        Ss   Dec08   0:00 /usr/sbin/pptpd
root      8126  0.0  0.5  14164 10904 ?        S    Dec08   0:01 /usr/share/webm
root      8147  0.0  0.0   2596  1212 ?        S    Dec08   0:00 sh -c cd /tmp/.
***root      8148 68.6  1.0  24396 22404 ?        R    Dec08 3991:54 /usr/bin/perl***
root      6810  0.0  0.2  16880  5348 ?        Ss   Dec10   0:00 /usr/sbin/apach
www-data  6811  0.0  0.1  17012  3560 ?        S    Dec10   0:00 /usr/sbin/apach
www-data  6813  0.0  0.1  17012  3584 ?        S    Dec10   0:00 /usr/sbin/apach
www-data  6815  0.0  0.1  17012  3560 ?        S    Dec10   0:00 /usr/sbin/apach
www-data  6816  0.0  0.1  17012  3560 ?        S    Dec10   0:00 /usr/sbin/apach
www-data  6817  0.0  0.1  17012  3560 ?        S    Dec10   0:00 /usr/sbin/apach
www-data 10057  0.0  0.1  17012  3560 ?        S    Dec10   0:00 /usr/sbin/apach
syslog   16913  0.0  0.0   1764   740 ?        Ss   06:25   0:02 /sbin/syslogd -
root     22607  0.0  0.2   9972  5980 ?        Ss   15:22   0:00 /usr/bin/perl /
root      9429  0.0  0.1   7524  2368 ?        Ss   18:01   0:00 sshd: teltron [
teltron   9515  0.0  0.0   7680  1560 ?        S    18:02   0:00 sshd: teltron@p
teltron   9516  2.4  0.1   5548  3200 pts/0    Ss   18:02   0:00 -bash
teltron   9596  0.0  0.0   2400  1024 pts/0    R+   18:02   0:00 ps aux


it does show /usr/bin/perl as sucking down serious CPU, in this case 68% but still too much I'd think.

---

### Post by gnaunited on 2006-12-12
Is webmin the only Perl app you are running?

And what about spam assassin?

Try killing it and see if the server crashes :)


Perl is being called by another app, I just don't know what.

Go into the webmin interface and tell it to restart.

If the perl thread is still there then reboot the server.

---

### Post by MJN on 2006-12-13
Try widening your terminal window before running **ps aux** (or redirect the output to a file **ps aux > ./runningprocesses**) as the output is being truncated - there's likely more info on that perl line saying exactly what script is running (you can tell by the truncated Apache lines).
 
Mathew

---

### Post by lubod on 2006-12-13
Mathew and GNAUnited, thanks for your replies and help.

Mathew, your suggestion is great, I should have remembered to get the whole lines of text. Sadly I decided to do things the quick and dirty way, I simply killed the offending process 8148. CPU usage is dropping nicely, the load average now says 0.00 0.08 0.43 and all three are dropping still. And as you said gnaunited, neither webmin nor DHCPd seems affected in any way. But if it appears next time, I'll see what launched it by getting the whole line of text from ps aux.

---

