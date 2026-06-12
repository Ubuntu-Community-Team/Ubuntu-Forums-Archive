---
title: "Daily Email Reports?"
date: 2008-06-13
forum: Security
---

### Post by Phill Kenoyer on 2008-06-13
Hi All,

I've been running FreeBSD for a very long time.  Recently I have retired my servers and T1 at my home and now I have my stuff at managed hosting.  They do not support FreeBSD on their systems so I'm using Ubuntu Linux.

On FreeBSD I would get a daily security report each night from Periodic.  How would I get something similar for Linux?  I've been searching the tubes and haven't found anything that's not overly complicated and bloated.

Below is an example of a report I would be interested in:

```

Removing old temporary files:
 /tmp/sess_347e343e9b074d744c7afbad0709a6b4
 /tmp/sess_49fb2014362960628b52096a8e62fce1
 /tmp/sess_004cc92a4c1396ad47daf7cf238e9178

Removing stale files from /var/preserve:

Cleaning out old system announcements:

Removing stale files from /var/rwho:

Backup passwd and group files:

Verifying group file syntax:
/etc/group is fine

Backing up mail aliases:

Disk status:
Filesystem  1K-blocks    Used    Avail Capacity  Mounted on
/dev/ad0s1a  18798158 5424658 11869648    31%    /
devfs               1       1        0   100%    /dev

Last dump(s) done (Dump '>' file systems):

Network interface status:
Name    Mtu Network       Address              Ipkts Ierrs    Opkts Oerrs  Coll
fxp0   1500 <Link#1>      00:02:55:fa:3b:1e 26068376     0 30196938     0     0 
fxp0   1500 #.#.#/24 www1              24319134     - 30189577     -     - 
fxp1*  1500 <Link#2>      00:02:55:fa:3b:1f        0     0        0     0     0 
lo0   16384 <Link#3>                          539986     0   539986     0     0 
lo0   16384 fe80:3::1     fe80:3::1                0     -        0     -     - 
lo0   16384 localhost     ::1                 409110     -   409110     -     - 
lo0   16384 your-net      localhost           130804     -   131334     -     - 

Local system status:
3:01AM  up 44 days, 18:50, 0 users, load averages: 0.00, 0.00, 0.00

Mail in local queue:
/var/spool/mqueue is empty
		Total requests: 0

Mail in submit queue:
/var/spool/clientmqueue is empty
		Total requests: 0

Security check:
Checking setuid files and devices:

Checking for uids of 0:
root 0

Checking for passwordless accounts:

www2.**********.net login failures:

www2.**********.net refused connections:
Jun 12 03:02:16 www2 sshd[47861]: refused connect from 61.144.122.38 (61.144.122.38)
Jun 12 03:05:01 www2 sshd[48015]: refused connect from 61.144.122.38 (61.144.122.38)
Jun 12 09:29:36 www2 sshd[48797]: refused connect from 58.40.157.78 (58.40.157.78)
Jun 12 16:18:45 www2 sshd[49645]: refused connect from 58.217.255.112 (58.217.255.112)

Checking for rejected mail hosts:

Checking for denied zone transfers (AXFR and IXFR):

-- End of daily output --

```

Thank you very much, in advance.

---

### Post by hyper_ch on 2008-06-13
just write a script that gets all the output you desire and then setup a cronjob that runs that script and emails you the output.

You need to isntall mailx for that.

then make a cron like this:

```

0 2 * * * /path/to/script 2>&1 | mail -s "Nightly Security Check" USER

```

that will email the output of the script to the local systemuser USER. 


```

0 2 * * * /path/to/script 2>&1 | mail -s "Nightly Security Check" user@domain.com

```

That will send it to [email]user@domain.com[/email]

---

### Post by brian_p on 2008-06-13
> **Phill Kenoyer said:**
> On FreeBSD I would get a daily security report each night from Periodic.  How would I get something similar for Linux?  


You are probably looking at installing a combination of packages to get similar functionality. In no particular order: logcheck, tripwire, fam, gamin, fcheck are some of the ones to assess. sec is also sophisicated enough to have the potential do what you want.

---

### Post by Phill Kenoyer on 2008-06-13
Thanks!

Found LogCheck and LogWatch today.  Installed them to see what they do.  I'm also looking at how hard it would be to get Periodic installed from FreeBSD to Linux..or maybe just the cron scripts that compile the report.

---

