---
title: "How to make a service to depend on a RAID array?"
date: 2011-03-07
forum: Server Platforms
---

### Post by karakonjul on 2011-03-07
Short story: I have a problem with one of my services (mediatomb) - it  requires an md RAID array to be mounted in order to start, because it  uses files from it. $remote_fs is added by default to the  "Required-Start" line of the init script, so I thought that this should  be enough. However, the mediatomb service fails to start on boot, but  starts just fine when I execute "service mediatomb start" later. The array is entered in /etc/fstab and is automatically mounted on boot.

Long story...

This is my file server (Ubuntu Server 10.10), which has a raid array  created with mdadm (mounted on /z), and the root filesystem is located  on an USB thumb drive. I've installed mediatomb, but I wanted to put its  database files on the raid array instead of the root fs, so I've  symlinked /var/lib/mediatomb (the default path) to /z/mediatomb on the  array. This is because the mediatomb DB is supposed to be updated fairly  often, so I didn't want it to stay on the flash drive.

Problem is, the mediatomb service can't start on boot - in  /var/log/mediatomb.log, it says "2011-03-07 19:22:47   ERROR:  /var/lib/mediatomb : 20 x No such file or directory". As I said, it  works fine when manually started later...

This is the fstab entry for the raid array:
```
/dev/md0 /z xfs defaults,noatime,nobootwait 0 0
```The array md0 is actually 2-level, comprising of 3 separate mirrors (md1, md2, md3) in a linear configuration:
```

md0 : active linear md1[0] md2[1] md3[2]
      4151066624 blocks 256k rounding

md2 : active raid1 sdd1[1] sdc1[0]
      732515648 blocks [2/2] [UU]

md1 : active raid1 sdb1[1] sda1[0]
      1465039488 blocks [2/2] [UU]

md3 : active raid1 sde1[0] sdf1[1]
      1953511936 blocks [2/2] [UU]
```The default init script for mediatomb contains this line:
```
# Required-Start:    $local_fs $network $remote_fs
```in /etc/insserv.conf:
```
$local_fs       +mountall +mountoverflowtmp +umountfs
$remote_fs      $local_fs +mountnfs +mountnfs-bootclean +umountnfs +sendsigs
```

Do I need to change anything in order to ensure that /z is mounted before the mediatomb service starts? I didn't think so, but apparently I'm wrong...

---

### Post by supremedalek on 2011-03-07
I do not know if that helps you but for a mail server I wanted to start mail only if a given encrypted partition was up. So, I disabled all the /etc/rcN.d scripts for the mail-related programs and wrote my own startup script that would only start them if it detected the desired partition was up.

---

