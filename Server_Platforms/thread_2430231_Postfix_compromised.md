---
title: "Postfix compromised"
date: 2019-10-29
forum: Server Platforms
---

### Post by fernandoch on 2019-10-29
Hello,

It seems that my postfix has been compromised and it is sending SPAM emails.

Here are some logs after blocking port 25:

```
Oct 29 16:44:30 ns388044 postfix/smtp[1402]: 61499148A33: to=<cop4u2wnt@jetty.net>, relay=none, delay=1104, delays=920/124/60/0, dsn=4.4.1, status=deferred (connect to mx2.emailsrvr.com[184.106.54.2]:25: Connection timed out)
Oct 29 16:44:30 ns388044 postfix/smtp[1405]: connect to spam.peak.org[207.55.16.93]:25: Connection timed out
Oct 29 16:44:30 ns388044 postfix/smtp[1346]: connect to publicms1.mail2world.com[216.163.188.54]:25: Connection timed out
Oct 29 16:44:30 ns388044 postfix/smtp[1372]: connect to mx.vgs.untd.com[64.136.52.37]:25: Connection timed out
Oct 29 16:44:30 ns388044 postfix/smtp[1372]: 1A1551473CB: to=<b.evans.7@juno.com>, relay=none, delay=1749, delays=1564/125/60/0, dsn=4.4.1, status=deferred (connect to mx.vgs.untd.com[64.136.52.37]:25: Connection timed out)
Oct 29 16:44:30 ns388044 postfix/smtp[1423]: connect to mx2.beget.ru[185.78.30.48]:25: Connection timed out
Oct 29 16:44:30 ns388044 postfix/smtp[1404]: connect to smtp.glb.shawcable.net[64.59.134.8]:25: Connection timed out
Oct 29 16:44:31 ns388044 postfix/smtp[1427]: connect to awe4one.com[69.73.128.108]:25: Connection timed out
Oct 29 16:44:31 ns388044 postfix/smtp[1427]: D6A99146A5D: to=<jim@awe4one.com>, relay=none, delay=1146, delays=961/155/30/0, dsn=4.4.1, status=deferred (connect to awe4one.com[69.73.128.108]:25: Connection timed out)
Oct 29 16:44:31 ns388044 postfix/smtp[1422]: connect to eu-smtp-inbound-2.mimecast.com[195.130.217.241]:25: Connection timed out
Oct 29 16:44:31 ns388044 postfix/smtp[1422]: ED81214857B: to=<farooq@rasass.com.sa>, relay=none, delay=3997, delays=3812/34/151/0, dsn=4.4.1, status=deferred (connect to eu-smtp-inbound-2.mimecast.com[195.130.217.241]:25: Connection timed out)
Oct 29 16:44:31 ns388044 postfix/smtp[1419]: connect to smtp.glb.shawcable.net[64.59.136.136]:25: Connection timed out
Oct 29 16:44:33 ns388044 postfix/smtp[1363]: connect to mx2.qq.com[203.205.219.58]:25: Connection timed out
Oct 29 16:44:33 ns388044 postfix/smtp[1364]: connect to mail4.ecommodate.com[64.5.100.118]:25: Connection timed out
Oct 29 16:44:33 ns388044 postfix/smtp[1424]: connect to gci-net.com.mx1.dakotacom.rcimx.net[66.181.249.34]:25: Connection timed out
Oct 29 16:44:35 ns388044 postfix/smtp[1420]: connect to frontend2.nts-online.net[216.167.161.218]:25: Connection timed out
Oct 29 16:44:48 ns388044 postfix/smtp[1285]: connect to mx0b-00133a01.pphosted.com[67.231.153.149]:25: Connection timed out
```

Any way to fix this?

Thanks

---

### Post by SeijiSensei on 2019-10-29
First thing I'd check is to see whether you are an [open relay]("https://en.wikipedia.org/wiki/Open_mail_relay"). Unblock port 25, then run this: [https://mxtoolbox.com/diagnostic.aspx](https://mxtoolbox.com/diagnostic.aspx).

Next, are there client machines that send mail through this machine? Perhaps one or more of them have been turned into spambots.  Depending on how public an email server you're running, that could be difficult to track down.  Look in the logs to see the origins of the messages in the listing above. Block any IPs sending suspicious traffic, then deal with their owners.

If you're not accepting any inbound SMTP traffic, the messages displayed above must be in your queue.  Run the command "sudo mailq" to see what's there. You can also delete the queued messages by following the instructions here: [https://www.wirehive.com/thoughts/5-top-tips-reviewing-postfix-mail-queue/](https://www.wirehive.com/thoughts/5-top-tips-reviewing-postfix-mail-queue/)

---

### Post by TheFu on 2019-10-29
Never run an open relay.  That will get your IP banned and getting off a banned list is weeks of effort, if possible at all.  One ISP banned one of my servers for 5 yrs. Nothing I did worked.  Fortunately, they were only a minor, regional, ISP.  I ended up blocking them to prevent their clients from emailing and believing we'd ever receive those emails.

---

### Post by fernandoch on 2019-10-29
I think these smpt processes might be the problem...

```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 16:40 ?        00:00:03 /sbin/init
root         2     0  0 16:40 ?        00:00:00 [kthreadd]
root         3     2  0 16:40 ?        00:00:01 [ksoftirqd/0]
root         5     2  0 16:40 ?        00:00:00 [kworker/0:0H]
root         7     2  0 16:40 ?        00:00:17 [rcu_sched]
root         8     2  0 16:40 ?        00:00:00 [rcu_bh]
root         9     2  0 16:40 ?        00:00:00 [migration/0]
root        10     2  0 16:40 ?        00:00:00 [migration/1]
root        11     2  0 16:40 ?        00:00:01 [ksoftirqd/1]
root        13     2  0 16:40 ?        00:00:00 [kworker/1:0H]
root        14     2  0 16:40 ?        00:00:00 [migration/2]
root        15     2  0 16:40 ?        00:00:01 [ksoftirqd/2]
root        17     2  0 16:40 ?        00:00:00 [kworker/2:0H]
root        18     2  0 16:40 ?        00:00:00 [migration/3]
root        19     2  0 16:40 ?        00:00:01 [ksoftirqd/3]
root        21     2  0 16:40 ?        00:00:00 [kworker/3:0H]
root        22     2  0 16:40 ?        00:00:00 [khelper]
root        23     2  0 16:40 ?        00:00:00 [kdevtmpfs]
root        24     2  0 16:40 ?        00:00:00 [netns]
root        25     2  0 16:40 ?        00:00:00 [writeback]
root        26     2  0 16:40 ?        00:00:00 [ksmd]
root        27     2  0 16:40 ?        00:00:00 [kintegrityd]
root        28     2  0 16:40 ?        00:00:00 [bioset]
root        29     2  0 16:40 ?        00:00:00 [crypto]
root        30     2  0 16:40 ?        00:00:00 [kblockd]
root        31     2  0 16:40 ?        00:00:00 [ata_sff]
root        32     2  0 16:40 ?        00:00:00 [khubd]
root        33     2  0 16:40 ?        00:00:00 [md]
root        34     2  0 16:40 ?        00:00:00 [edac-poller]
root        35     2  0 16:40 ?        00:00:00 [rpciod]
root        54     2  0 16:40 ?        00:00:00 [kswapd0]
root        55     2  0 16:40 ?        00:00:00 [fsnotify_mark]
root        56     2  0 16:40 ?        00:00:00 [kworker/3:1]
root        57     2  0 16:40 ?        00:00:00 [nfsiod]
root        58     2  0 16:40 ?        00:00:00 [cifsiod]
root        59     2  0 16:40 ?        00:00:00 [jfsIO]
root        60     2  0 16:40 ?        00:00:00 [jfsCommit]
root        61     2  0 16:40 ?        00:00:00 [jfsCommit]
root        62     2  0 16:40 ?        00:00:00 [jfsCommit]
root        63     2  0 16:40 ?        00:00:00 [jfsCommit]
root        64     2  0 16:40 ?        00:00:00 [jfsSync]
root        65     2  0 16:40 ?        00:00:00 [xfsalloc]
root        66     2  0 16:40 ?        00:00:00 [xfs_mru_cache]
root        67     2  0 16:40 ?        00:00:00 [xfslogd]
root        68     2  0 16:40 ?        00:00:00 [ocfs2_wq]
root        69     2  0 16:40 ?        00:00:00 [user_dlm]
root        70     2  0 16:40 ?        00:00:00 [glock_workqueue]
root        71     2  0 16:40 ?        00:00:00 [delete_workqueu]
root        72     2  0 16:40 ?        00:00:00 [gfs_recovery]
root       103     2  0 16:40 ?        00:00:00 [kthrotld]
root       104     2  0 16:40 ?        00:00:16 [kworker/0:1]
root       105     2  0 16:40 ?        00:00:12 [kworker/1:1]
root       107     2  0 16:40 ?        00:00:00 [nvme]
root       108     2  0 16:40 ?        00:00:00 [nvme]
root       109     2  0 16:40 ?        00:00:00 [bioset]
root       111     2  0 16:40 ?        00:00:00 [drbd-reissue]
root       112     2  0 16:40 ?        00:00:00 [iscsi_eh]
root       113     2  0 16:40 ?        00:00:00 [scsi_eh_0]
root       114     2  0 16:40 ?        00:00:00 [scsi_tmf_0]
root       115     2  0 16:40 ?        00:00:00 [scsi_eh_1]
root       116     2  0 16:40 ?        00:00:00 [scsi_tmf_1]
root       117     2  0 16:40 ?        00:00:00 [scsi_eh_2]
root       118     2  0 16:40 ?        00:00:00 [scsi_tmf_2]
root       119     2  0 16:40 ?        00:00:00 [scsi_eh_3]
root       120     2  0 16:40 ?        00:00:00 [scsi_tmf_3]
root       122     2  0 16:40 ?        00:00:02 [kworker/u8:4]
root       124     2  0 16:40 ?        00:00:00 [bond0]
root       125     2  0 16:40 ?        00:00:00 [bnx2x]
root       126     2  0 16:40 ?        00:00:00 [ixgbe]
root       127     2  0 16:40 ?        00:00:00 [mlx4]
root       128     2  0 16:40 ?        00:00:00 [vfio-irqfd-clea]
root       131     2  0 16:40 ?        00:00:00 [kpsmoused]
root       132     2  0 16:40 ?        00:00:00 [kworker/1:2]
root       133     2  0 16:40 ?        00:00:00 [raid5wq]
root       134     2  0 16:40 ?        00:00:00 [bcache]
root       135     2  0 16:40 ?        00:00:00 [bch_btree_io]
root       136     2  0 16:40 ?        00:00:00 [dm_bufio_cache]
root       137     2  0 16:40 ?        00:00:00 [kmpathd]
root       138     2  0 16:40 ?        00:00:00 [kmpath_handlerd]
root       139     2  0 16:40 ?        00:00:00 [ipv6_addrconf]
root       140     2  0 16:40 ?        00:00:00 [ceph-msgr]
root       141     2  0 16:40 ?        00:00:00 [bioset]
root       142     2  0 16:40 ?        00:00:00 [deferwq]
root       143     2  0 16:40 ?        00:00:47 [jbd2/sda1-8]
root       144     2  0 16:40 ?        00:00:00 [ext4-rsv-conver]
root       167     1  1 16:40 ?        00:02:37 /lib/systemd/systemd-journald
root       186     2  0 16:40 ?        00:00:00 [kworker/2:1H]
root       202     1  0 16:40 ?        00:00:00 /sbin/lvmetad -f
root       205     1  0 16:41 ?        00:00:00 /lib/systemd/systemd-udevd
root       229     2  0 16:41 ?        00:00:01 [kworker/2:3]
root       268     2  0 16:41 ?        00:00:12 [kworker/3:2]
root       424     2  0 16:41 ?        00:00:08 [kworker/1:1H]
root       456     2  0 16:41 ?        00:00:00 [jbd2/sda2-8]
root       459     2  0 16:41 ?        00:00:00 [ext4-rsv-conver]
systemd+   518     1  0 16:41 ?        00:00:00 /lib/systemd/systemd-timesyncd
root       616     1  0 16:41 ?        00:00:12 /usr/lib/accountsservice/accounts-daemon
root       618     1  0 16:41 ?        00:00:00 /usr/sbin/smartd -n
message+   619     1  0 16:41 ?        00:00:00 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --syst
root       632     1  0 16:41 ?        00:00:00 /usr/sbin/acpid
syslog     637     1  0 16:41 ?        00:00:56 /usr/sbin/rsyslogd -n
root       641     2  0 16:41 ?        00:00:00 [kworker/3:1H]
root       642     1  0 16:41 ?        00:00:00 /usr/sbin/cron -f
root       643     1  0 16:41 ?        00:00:00 /lib/systemd/systemd-logind
root       688     1  0 16:41 ?        00:00:00 /sbin/mdadm --monitor --pid-file /run/mdadm/monitor.pid --daemonise --scan -
root       726     1  0 16:41 ?        00:00:01 /usr/sbin/irqbalance --pid=/var/run/irqbalance.pid
root       730     1  0 16:41 ?        00:00:00 /usr/lib/policykit-1/polkitd --no-debug
root       733     2  0 16:41 ?        00:00:00 [kworker/0:1H]
root       984     1  0 16:41 ?        00:00:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown
beamium    989     1  0 16:41 ?        00:00:12 /usr/bin/beamium --config=/etc/beamium/config.yaml
bind       991     1  1 16:41 ?        00:02:33 /usr/sbin/named -f -u bind
root      1013     1  0 16:41 ?        00:00:00 /usr/sbin/sshd -D
mysql     1014     1  1 16:41 ?        00:02:23 /usr/sbin/mysqld
root      1053     1  0 16:41 ?        00:00:00 /lib/systemd/systemd --user
opendkim  1054     1  1 16:41 ?        00:01:35 /usr/sbin/opendkim -x /etc/opendkim.conf -u opendkim -P /var/run/opendkim/op
root      1058  1053  0 16:41 ?        00:00:00 (sd-pam)
root      1067     1  0 16:41 tty1     00:00:00 /sbin/agetty --noclear tty1 linux
root      1085     1  0 16:41 ?        00:00:01 /usr/bin/noderig
root      1118     1  0 16:41 ?        00:00:00 /usr/sbin/apache2 -k start
root      1136     1  4 16:41 ?        00:05:47 /usr/bin/python3 /usr/bin/fail2ban-server -s /var/run/fail2ban/fail2ban.sock
www-data  1137  1118  1 16:41 ?        00:01:38 /usr/sbin/apache2 -k start
www-data  1138  1118  1 16:41 ?        00:02:09 /usr/sbin/apache2 -k start
www-data  1139  1118  0 16:41 ?        00:00:59 /usr/sbin/apache2 -k start
www-data  1140  1118  1 16:41 ?        00:01:41 /usr/sbin/apache2 -k start
www-data  1242  1118  0 16:41 ?        00:01:16 /usr/sbin/apache2 -k start
www-data  1277  1118  1 16:41 ?        00:01:39 /usr/sbin/apache2 -k start
www-data  1278  1118  0 16:41 ?        00:01:04 /usr/sbin/apache2 -k start
www-data  1286  1118  1 16:41 ?        00:01:42 /usr/sbin/apache2 -k start
www-data  1288  1118  0 16:41 ?        00:01:17 /usr/sbin/apache2 -k start
www-data  1289  1118  0 16:41 ?        00:01:19 /usr/sbin/apache2 -k start
www-data  1290  1118  0 16:41 ?        00:00:58 /usr/sbin/apache2 -k start
www-data  1318  1118  0 16:41 ?        00:01:17 /usr/sbin/apache2 -k start
www-data  1319  1118  1 16:41 ?        00:01:42 /usr/sbin/apache2 -k start
www-data  1320  1118  1 16:41 ?        00:01:56 /usr/sbin/apache2 -k start
www-data  1321  1118  1 16:41 ?        00:01:20 /usr/sbin/apache2 -k start
www-data  1322  1118  0 16:41 ?        00:01:14 /usr/sbin/apache2 -k start
www-data  1323  1118  1 16:41 ?        00:01:20 /usr/sbin/apache2 -k start
www-data  1324  1118  1 16:41 ?        00:01:22 /usr/sbin/apache2 -k start
www-data  1325  1118  0 16:41 ?        00:01:18 /usr/sbin/apache2 -k start
www-data  1352  1118  0 16:41 ?        00:01:17 /usr/sbin/apache2 -k start
www-data  1353  1118  1 16:41 ?        00:01:30 /usr/sbin/apache2 -k start
www-data  1355  1118  1 16:41 ?        00:01:29 /usr/sbin/apache2 -k start
www-data  1356  1118  1 16:41 ?        00:01:26 /usr/sbin/apache2 -k start
www-data  1357  1118  0 16:41 ?        00:01:09 /usr/sbin/apache2 -k start
root      2176     2  0 16:56 ?        00:00:14 [kworker/2:1]
root      3815     2  0 18:16 ?        00:00:00 [kworker/u8:1]
root     14309     2  0 17:43 ?        00:00:00 [kworker/0:0]
root     23805  1013  0 18:45 ?        00:00:00 sshd: root@pts/0
root     23948 23805  0 18:45 pts/0    00:00:00 -bash
root     28697     2  0 18:50 ?        00:00:00 [kworker/3:0]
root     30192     2  0 18:52 ?        00:00:00 [kworker/u8:0]
root     30910  1013  0 18:53 ?        00:00:00 sshd: root [priv]
sshd     30914 30910  0 18:53 ?        00:00:00 sshd: root [net]
root     31078     1  4 18:53 ?        00:00:00 /usr/lib/postfix/sbin/master
postfix  31079 31078  1 18:53 ?        00:00:00 pickup -l -t unix -u -c
postfix  31080 31078 61 18:53 ?        00:00:01 qmgr -l -t unix -u
postfix  31081 31078  3 18:53 ?        00:00:00 cleanup -z -t unix -u -c
postfix  31086 31078 10 18:53 ?        00:00:00 trivial-rewrite -n rewrite -t unix -u -c
postfix  31087 31078  4 18:53 ?        00:00:00 cleanup -z -t unix -u -c
postfix  31088 31078  1 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31089 31078  2 18:53 ?        00:00:00 tlsmgr -l -t unix -u -c
postfix  31090 31078  3 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31091 31078  3 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31092 31078  3 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31093 31078  3 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31094 31078  3 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31095 31078  2 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31096 31078  2 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31097 31078  2 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31098 31078  2 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31099 31078  2 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31100 31078  3 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31101 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31102 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31103 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31104 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31105 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31106 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31107 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31108 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31109 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31110 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31111 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31112 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31113 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
postfix  31115 31078  0 18:53 ?        00:00:00 smtp -t unix -u -c
root     31117 23948  0 18:53 pts/0    00:00:00 ps -ef
```

What do you suggest?

---

### Post by TheFu on 2019-10-29
Do you really run apache on an email server?  Srsly?!!!

A process list isn't really helpful. What can anyone tell from a list of smtp processes buried 4 pgs down in the list?

 Run the open relay tests and report back.  
When it comes to solving any problems, simplify and test.  Keep doing that until the only thing left is causing the issue, then delve into the configuration of that remaining item.

---

### Post by fernandoch on 2019-10-29
This is not a mail server, this is a LAMP.

I am just using Postfix to send emails from Wordpress to the admins...

---

### Post by fernandoch on 2019-10-29
I get this error when using the tool [https://mxtoolbox.com/diagnostic.aspx](https://mxtoolbox.com/diagnostic.aspx)

[https://www.screencast.com/t/gvcgMTj6sB](https://www.screencast.com/t/gvcgMTj6sB)

---

### Post by fernandoch on 2019-10-29
How did they exploit Postfix?

Does that mean they have the root password? Or can they do it without root?

---

### Post by TheFu on 2019-10-29
> **fernandoch said:**
> This is not a mail server, this is a LAMP.

I am just using Postfix to send emails from Wordpress to the admins...
That changes everything. 

They didn't exploit postfix.  They hacked your website(s).

Can't help with wordpress or php security. Sorry.  We don't use php for anything on the internet.  Have you disabled postfix yet?  Need to block all outbound emails immediately.  If the system is still under their control, likely, then they will enable postfix again and start going.  You can lock postfix down so only emails to specific userids are allowed, but that takes longer and doesn't solve the root issue.

If you have backups, can you check for changes day by day to see when something funky was added?  This is one of the main reasons to have 
[LIST]
[*]daily
[*]automatic
[*]versioned
[*]"pulled"
[*]backups
[/LIST]
By "pulling" the data, the bad guys can't corrupt the backups or the data it contains.  With the versioned backup data, we can see what they did, where the scripts were placed, and what those actually do beyond just spamming the world.  It is likely they have modified the php to be a phishing site too.

Google found this: [https://www.malcare.com/blog/how-to-remove-phishing/](https://www.malcare.com/blog/how-to-remove-phishing/)  I don't know anything about it. 

Lacking that, I'd wipe the server and start over, paying closer attention to all security considerations.

If they did get in and got a shell, they can can setup an outbound reverse shell to specific places that happens for 3 minutes every few days.  Those are nearly impossible to find, unless you happen to be watching when they are open. With a reverse shell, they will have shell access back into the server. This is why wiping the server and starting over is really the only method if you don't have versioned backups that could not have been corrupted from at least some time before they got in.

---

### Post by kevdog on 2019-10-29
I'm not sure how you figure his webserver was compromised.

---

### Post by TheFu on 2019-10-30
> **kevdog said:**
> I'm not sure how you figure his webserver was compromised.

How?

Postfix accepts local mail traffic on the machine (based on the logs).

Postfix is not accepting any connections from the internet email *open relay *testing tools.

The OP has a LAMP server and is running Wordpress.  That means that wordpress and php are both loaded, which are highly likely to be compromised.  OP also claims that emails should be going only to WP admins.

To me, that all adds up to a hacked webserver.  Is there some other explanation?

---

### Post by fernandoch on 2019-10-30
Wiping the server?

My wordpress sites have all data, not to easy to wipe it out.

---

### Post by fernandoch on 2019-10-30
These are the files

```
root@ns3XXX5:/var/www/woXXX.com/public_html# ls
4rr1su1v.php  index.php                 wp-comments-post.php  wp-load.php
azl5r89j.php  license.txt               wp-config.php         wp-login.php
ck1ymks5.php  readme.html               wp-config-sample.php  wp-mail.php
cy.php        **seo_script.php.suspected**  wp-content            wp-settings.php
fnog1zfm.php  wp-activate.php           wp-cron.php           wp-signup.php
ftzk7jbh.php  wp-admin                  wp-includes           wp-trackback.php
hko9oxxe.php  wp-blog-header.php        wp-links-opml.php     xmlrpc.php
```

---

### Post by fernandoch on 2019-10-30
Gonna try ISPProtect, it seems to be the best one right now in the market.

---

### Post by TheFu on 2019-10-30
> **fernandoch said:**
> Wiping the server?

My wordpress sites have all data, not to easy to wipe it out.

Wiping a server is really easy.

Do you think that your data isn't already corrupted?
A compromised server can NEVER be trusted again.  Wipe and start over is the only viable answer.

If there are backups from before the compromise, starting with the data from those would be reasonable.  Otherwise, until all the data is proven to be reasonable, not compromised, then it cannot be trusted.

---

### Post by fernandoch on 2019-10-30
How do you wipe a server if all your Wordpress files are compromised?

I think first you need to fix them...

---

### Post by Skaperen on 2019-10-30
> **fernandoch said:**
> Wiping the server?

My wordpress sites have all data, not to easy to wipe it out.

where are your backups?

---

### Post by Skaperen on 2019-10-30
> **fernandoch said:**
> How do you wipe a server if all your Wordpress files are compromised?

I think first you need to fix them...

there is no reliable way to fix a compromised server.  even the kernel binary can be compromised.  start over by erasing the partition table and install the latest Ubuntu server.

anything and everything you think you want to save could be compromised.

boot from media that has never been attached to that server or is read-only media.

---

### Post by LHammonds on 2019-10-31
When you do re-install, don't setup the server the exact same way you did before...or it will happen again.

If done right, not even wordpress can update itself.  I use two accounts for wordpress.  One is production mode and has just enough rights to function but cannot update itself.  Another account is an installer account that I will switch to when wordpress or plugins need to be updated.

If the website does not need users registering and logging in, be sure to disable registration too.

LHammonds

---

### Post by SeijiSensei on 2019-10-31
I set the permissions in WordPress to block the server from doing anything to the installation. That means that the software cannot update itself automatically, but it also blocks lots of attacks on WordPress itself.  I simply wrote two little scripts to manage the permissions:

Run before the update

cd /path/to/wordpress

```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```
The Apache pseudo-user, www-data on Ubuntu, is in the group that owns the WordPress installation.

After I perform the update I run this script
```

#!/bin/sh
chmod u+rwx,g+rx wp-admin wp-includes wp-content -R
chmod g-w *
echo "Permissions reset!"

```
In my case, the owner of the wordpress directory is not the www-data user, but another user I set up to own all the websites.

---

### Post by fernandoch on 2019-11-03
All good ideas, thanks.

But now what can I do with the compromised Wordpress?

I have like 10 of them...

I also had a phpBB on that server.

---

### Post by fernandoch on 2019-11-03
> **SeijiSensei said:**
> I set the permissions in WordPress to block the server from doing anything to the installation. That means that the software cannot update itself automatically, but it also blocks lots of attacks on WordPress itself.  I simply wrote two little scripts to manage the permissions:

Run before the update

cd /path/to/wordpress

```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```
The Apache pseudo-user, www-data on Ubuntu, is in the group that owns the WordPress installation.

After I perform the update I run this script
```

#!/bin/sh
chmod u+rwx,g+rx wp-admin wp-includes wp-content -R
chmod g-w *
echo "Permissions reset!"

```
The owner of the wordpress directory is not the www-data user, but another user I set up to own all the websites.

I like this option.

How would you adapt it if instead of just one wordpress installation I had like 10...

Would you recommend doing that to the public_html folder?

---

### Post by TheFu on 2019-11-03
You cannot trust the server.  It needs to be wiped.  The entire OS.  Everything that was installed.  
If it is a VPS, create a new VPS and delete the old one.  
If it is a physical server, format the HDD, and randomly fill the /dev/sda device, then do a fresh install.

We understand this is painful.
 
You can pay people who will claim they can clean it.  They aren't telling the truth.  That server install can never be known to be safe ever again.  It hasn't been safe since before you noticed. It cannot be trusted.

What you get from this experience is how to do better next time, but not the binary data or OS or any non-text files. Hopefully, you will setup the next server better, keep it maintained better, and have daily, automatic, versioned, off-machine, backups.  

If you are an expert at WP DBs, you could dump that DB, then manually check every field for corruption.  It will take weeks.
For any text files, you can grab those too, then manually validate each one.  Or use diff to compare to source files from other known-good places.  
I don't know how to validate that binary files haven't been altered, except by having backups PRIOR to the attack.  All binary files need to be wiped. When in doubt, wipe it.

---

### Post by fernandoch on 2019-11-03
Sure, and how do you pass the data from one server to another?

---

### Post by LHammonds on 2019-11-03
> **fernandoch said:**
> How would you adapt it if instead of just one wordpress installation I had like 10...

Would you recommend doing that to the public_html folder?

He showed you the basic solution which is a bash script.  You just adapt the command how you would do them for each sites folder.

Since there are repetitive tasks, I would put the tasks into a function and call the function for each different scenario (different folder in this case).  But if each site has different permission requirements, you might have to just repeat the permission-setting lines for the unique sites or make unique functions if multiple sites share the same permission settings.

I would also include full paths to all programs called to avoid path issues when run via crontab schedule.  If your paths do not match what I have in the example script, you can find out the correct path for your server by using the "which" command.  Example: which chmod

I would also include a log file so you can check the history of when the script was run and what wordpress sites were processed when it did run.

Keep in mind that one persons solution may not fit what you need.  A default install with no plugins or themes will have different permissions if it is production mode verses developer mode.  As plugins and such are added, they might require specific permissions to be tailored for that site.  Be sure to read WordPress' article about this before continuing any further.  [https://wordpress.org/support/article/changing-file-permissions/](https://wordpress.org/support/article/changing-file-permissions/)

Example of how I would do it (but again, could be different for your site so adapt as needed):

Also note this has not been tested to be free of syntax errors, code was copy/pasted and typed from scratch to try an fit this particular post and should not be considered "best practice for a default site."

wordpress-update-mode.sh
```

#!/bin/sh
LogFile="/var/log/wordpress-update-mode.log"
WebUser="www-data"
WebGroup="www-data"

function f_update_mode()
{
  ## Parameter $1 = Root path of wordpress site.
  SitePath=$1
  ## Add log entry for which path is being modified.
  /bin/echo "`date +%Y-%m-%d_%H:%M:%S` -- Path modified = ${SitePath}" >> ${LogFile}
  if [ ! -d ${SitePath} ]; then
    /bin/echo "`date +%Y-%m-%d_%H:%M:%S` ---- ERROR: Path does not exist - ${SitePath}" >> ${LogFile}
    return 1
  fi
  ## Set expected ownership on all files.
  /bin/chown --recursive ${WebUser}:${WebGroup} ${SitePath}/*
  ## Add group write permissions to all folders
  /usr/bin/find ${SitePath} -type d -exec /bin/chmod g+w {} \;
  ## Add group write permissions to all files
  /usr/bin/find ${SitePath} -type f -exec /bin/chmod g+w {} \;
} ## f_update_mode

/bin/echo "`date +%Y-%m-%d_%H:%M:%S` Wordpress update mode started." >> ${LogFile}
f_update_mode "/var/www/wordpress1"
f_update_mode "/var/www/wordpress2"
f_update_mode "/var/www/wordpress3"
f_update_mode "/var/www/wordpress4"
/bin/echo "`date +%Y-%m-%d_%H:%M:%S` Wordpress update mode finished." >> ${LogFile}

```

wordpress-safe-mode.sh
```

#!/bin/sh
LogFile="/var/log/wordpress-safe-mode.log"
WebUser="www-data"
WebGroup="www-data"

function f_safe_mode()
{
  ## Parameter $1 = Root path of wordpress site.
  SitePath=$1
  ## Add log entry for which path is being modified.
  /bin/echo "`date +%Y-%m-%d_%H:%M:%S` -- Path modified = ${SitePath}" >> ${LogFile}
  if [ ! -d ${SitePath} ]; then
    /bin/echo "`date +%Y-%m-%d_%H:%M:%S` ---- ERROR: Path does not exist - ${SitePath}" >> ${LogFile}
    return 1
  fi
  ## Reset ownership on all files.
  /bin/chown --recursive ${WebUser}:${WebGroup} ${SitePath}/*
  ## Reset root folder permission
  /bin/chmod u+rwx,g+rx-w,o+rx-w ${SitePath}
  ## Set the setgid sticky bit so all created files inherit group ID from parent
  /bin/chmod g+s ${SitePath}
  ## Reset directory permissions to standard default.
  /usr/bin/find ${SitePath} -type d -exec /bin/chmod u+rwx,g+rx-w,o-rxw {} \;
  ## Reset file permissions to standard default.
  /usr/bin/find ${SitePath} -type f -exec /bin/chmod u+rw-x,g+r-wx,o-rwx {} \;
  ## Lock down .htaccess
  /usr/bin/find ${SitePath} -type f -name ".htaccess" -exec /bin/chmod u+rw-x,g+rw-x,o-rwx {} \;
  ## Lock down config file.
  /bin/chmod u+r-wx,g+r-wx,o-rwx ${SitePath}/wp-config.php
  ## Relax permissions on content folders.
  /usr/bin/find ${SitePath}/wp-content -type d -exec /bin/chmod u+rwx,g+rwx,o-rwx {} \;
  /usr/bin/find ${SitePath}/wp-content -type f -exec /bin/chmod u+rw-x,g+rw-x,o-rwx {} \;
  ## Set default permissions for new files/folders.
  /usr/bin/setfacl -d -m g::rwx ${SitePath}/wp-content
} ## f_safe_mode

/bin/echo "`date +%Y-%m-%d_%H:%M:%S` Wordpress safe mode started." >> ${LogFile}
f_safe_mode "/var/www/wordpress1"
f_safe_mode "/var/www/wordpress2"
f_safe_mode "/var/www/wordpress3"
f_safe_mode "/var/www/wordpress4"
/bin/echo "`date +%Y-%m-%d_%H:%M:%S` Wordpress safe mode finished." >> ${LogFile}

```

I would configure crontab to run the "wordpress-safe-mode.sh" on a daily basis just in case you or someone else "forgot" to disable update mode but do NOT rely on the automation to restrict it.  You want to lock down Wordpress AS SOON AS the update is done so it is vulnerable to attack in the least amount of time...or disable public access while the site is being updated to ensure nobody can mess with it while in "update mode."

> **fernandoch said:**
> Sure, and how do you pass the data from one server to another?
If you are talking about dumping the SQL data, .php code and whatnot, I would use WinSCP to transfer the files to my PC.  Then I would use WinSCP again to transfer the files from my PC to a different server.  I would NEVER let the new and infected server communicate directly to each other in any way.  It sounds like you are determined to salvage the data but as TheFu has mentioned, that data can never be trusted even if a so-called professional says he scrubbed it and finds it to be clean.

If you have no way of determining WHEN the site was compromised, you cannot trust any prior backup you have made.  And if the backups exist only on the same server that has been compromised, those cannot be trusted either.  And if the infected server has access to the offsite backups, those cannot be trusted either.

The only code you can trust is the original install files for that version of wordpress straight from wordpress.org (as a fresh download on a different server)

LHammonds

---

### Post by fernandoch on 2019-11-03
Thanks for all that.

But with winscp you will copy the compromised files... confused about this option.

---

### Post by LHammonds on 2019-11-03
> **fernandoch said:**
> But with winscp you will copy the compromised files... confused about this option.Well, I was confused about your question.  I assumed you were talking about trying to salvage the compromised files from the old server.  What were you talking about when you asked "pass data from one server to another?"

---

### Post by SeijiSensei on 2019-11-03
> 
```
root@ns3XXX5:/var/www/woXXX.com/public_html# ls
4rr1su1v.php  index.php                 wp-comments-post.php  wp-load.php
azl5r89j.php  license.txt               wp-config.php         wp-login.php
ck1ymks5.php  readme.html               wp-config-sample.php  wp-mail.php
cy.php        **seo_script.php.suspected**  wp-content            wp-settings.php
fnog1zfm.php  wp-activate.php           wp-cron.php           wp-signup.php
ftzk7jbh.php  wp-admin                  wp-includes           wp-trackback.php
hko9oxxe.php  wp-blog-header.php        wp-links-opml.php     xmlrpc.php
```

All those files with gobbedly-gook names are very suspicious. They're certainly not part of any legitimate WP installation. Have you examined any of them with an editor?  Other than index.php and xmlrpc.php, the only legitimate files are the ones that begin with "wp-".  Who owns the suspicious files?  I'm guessing they are owned by www-data, the Apache pseudouser, and were placed there when the miscreants gained some type of shell access to this directory.  

Not allowing the Apache user to write into the website directory is the first line of defense.

If the compromised software resides in the Wordpress installation, and not in the content itself, then you can try using mysqldump to create a text-based backup of the MySQL database, then read it back in after a fresh installation.  I can't guarantee this won't replicate the compromise, though, since we have so little information on how the exploit took place.  But most of these compromises attack the WP installation, not the database.

Some resources:
[https://www.getastra.com/blog/911/wordpress-hacked-sending-spam/](https://www.getastra.com/blog/911/wordpress-hacked-sending-spam/)
[https://www.wordfence.com/docs/how-to-clean-a-hacked-wordpress-site-using-wordfence/](https://www.wordfence.com/docs/how-to-clean-a-hacked-wordpress-site-using-wordfence/)

---

### Post by fernandoch on 2019-11-03
> **LHammonds said:**
> Well, I was confused about your question.  I assumed you were talking about trying to salvage the compromised files from the old server.  What were you talking about when you asked "pass data from one server to another?"

I mean to copy all the content we have in our wordpress sites to the new server.

I think the files have to be cleaned before copying to a new server.

---

### Post by fernandoch on 2019-11-03
> **SeijiSensei said:**
> All those files with gobbedly-gook names are very suspicious. They're certainly not part of any legitimate WP installation. Have you examined any of them with an editor?  Other than index.php and xmlrpc.php, the only legitimate files are the ones that begin with "wp-".  Who owns the suspicious files?  I'm guessing they are owned by www-data, the Apache pseudouser, and were placed there when the miscreants gained some type of shell access to this directory.  

Not allowing the Apache user to write into the website directory is the first line of defense.

If the compromised software resides in the Wordpress installation, and not in the content itself, then you can try using mysqldump to create a text-based backup of the MySQL database, then read it back in after a fresh installation.  I can't guarantee this won't replicate the compromise, though, since we have so little information on how the exploit took place.  But most of these compromises attack the WP installation, not the database.

Some resources:
[https://www.getastra.com/blog/911/wordpress-hacked-sending-spam/](https://www.getastra.com/blog/911/wordpress-hacked-sending-spam/)
[https://www.wordfence.com/docs/how-to-clean-a-hacked-wordpress-site-using-wordfence/](https://www.wordfence.com/docs/how-to-clean-a-hacked-wordpress-site-using-wordfence/)

Of course I have checked them all. All of them had hex code owned by www-data.

I ran ISPProtect and it detected all the infected files. It can also scan the database.

From what I've seen it is a very robust scanner, but I only get 1 trial scan. Soon I will buy more scans.

I don't think we can block apache from writing to disk. For example caching plugins do write files to disk, like w3 total cache. And probably other plugins need that too.

And I was thinking that most probably if I block apache from writing to disk, those hackers will queue their attacks and as soon as I enable the editing on disk, their scripts will also write to disk.

The compromised files had all different dates. Some from February, others from March and others from October.

So my guess is that they attack with intervals or something like that.

---

### Post by fernandoch on 2019-11-03
And the thing is that I have ufw enabled with fail2ban... All pretty well configured.

But most probably it was some php file that was not well coded or maybe a plugin... Although all my wordpress sites are always updated.

---

### Post by SeijiSensei on 2019-11-04
> **fernandoch said:**
> I don't think we can block apache from writing to disk. For example caching plugins do write files to disk, like w3 total cache. And probably other plugins need that too.

And I was thinking that most probably if I block apache from writing to disk, those hackers will queue their attacks and as soon as I enable the editing on disk, their scripts will also write to disk.

If the Apache user cannot write to the directory, there won't be any place to put those scripts so there shouldn't be any queued attacks.

Maybe you should consider if you really need caching plugins? Does performance degrade visibly if you disable them?

I'm very wary of adding more than a few plugins to WordPress.  I use a few that control the format of blogs, like WP Hide Post, and ones like Classic Editor and GDPR Cookie Compliance. None of these need write-permissions to function.

---

