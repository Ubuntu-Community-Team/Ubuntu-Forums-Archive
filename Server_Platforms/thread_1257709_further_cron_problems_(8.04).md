---
title: "further cron problems (8.04)"
date: 2009-09-04
forum: Server Platforms
---

### Post by Gorlist on 2009-09-04
Since installing Ubuntu 8.04 LTS ive been having some extensive cron problems.

If I disable the root account crontab -e fails to run (user no longer exists).

None of the cron folders appear to function what so ever, I have one reference in the syslog pointing to cron.hourly.

At the moment to run the nightly backup which is in cron.daily im having to login and sudo it by hand.

No idea what the problem is, ive searched the forums and tried various suggestions over the last few months.

Any help would be most appreciated.

---

### Post by DaithiF on 2009-09-04
Hi,
(I can only speak for 9.04 here, so some of this may not be applicable to 8.04).
Firstly, a nightly backup isn't a good candidate for running from cron.daily.  cron.daily is a good choice for jobs you want to run approx once a day, when the exact time they run at isn't important.  Also, entries in cron.daily get run by anacron rather than by cron so theres another link in the chain to investigate when something isn't working.

On my system, something in cron.daily would get run by this mechanism.
1. /etc/crontab contains:
```
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```
so, at 6:25, test if anacron exists & is executable (it is), and if so, do nothing
2. /etc/cron.d/anacron contains:
```
30 7    * * *   root    test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null

```
so, at 7:30, crond again checks for the anacron binary, and now runs anacron
3. /etc/anacrontab contains:
```
1   5   cron.daily   nice run-parts --report /etc/cron.daily

```
which (finally) tells anacron to run whatever is in cron.daily

Instead of all this, to give yourself precise control over when your backup job runs, just put an entry in /etc/crontab, something like:
```
30 1 * * * root /path/to/your/backupcommand > /path/to/some/logfile 2>&1
```
so at 1:30, run the backup job, capture stdout & stderr output to a logfile somewhere.

---

### Post by Gorlist on 2009-09-04
Thanks for the reply DaithiF and suggestions. Will dig around further and double check on anacron.

---

### Post by Gorlist on 2009-09-21
right, im still not convinced anacron is running correctly - it is installed :) and their is an entry in cron.d:

```

# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

30 7    * * *   root    test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null

```

However going of a second post a gentlemen also has this following within anacron:

```

# m h dom mon dow user command
14 * * * * root cd / && run-parts --report /etc/cron.hourly
33 0 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
55 2 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
29 1 19 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```

Which is correct? and does anyone have an example of their anacron. 

Best Regards

---

### Post by DaithiF on 2009-09-21
Hi, its not a question of one or other of those being correct or incorrect, they are are separate things, and actually neither of them is the anacron config. file :) 

For anacrons config file, see
```
/etc/anacrontab
```

on jaunty desktop its default contents are:
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1       5       cron.daily       nice run-parts --report /etc/cron.daily
7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly

```

The two files you posted are:
1. /etc/cron.d/anacron -- this is a cron job whose purpose is to start anacron once per day, and in turn then allow anacron to do whatever processing it is configured to do (as defined in the /etc/anacrontab file).
2. /etc/crontab -- system-wide cron job, the references you see to anacron in the last 3 commands there are only saying: IF anacron isn't installed, then have cron execute these jobs -- since anacron IS installed, these have no effect.

---

### Post by Gorlist on 2009-09-21
Right! well everything checks out then in regards to anacron and the config as well as cron.d - more importantly I now understand your first reply :)

So, if anacron appears fine, then I wonder if its user related. When the root account is disabled then crontab/cron doesn't appear to be running (or atleast the root user crontab). Now I can manually run cron from sudo: 

```
run-parts -v /etc/cron.daily
```

Thanks, will carry on digging :)

---

