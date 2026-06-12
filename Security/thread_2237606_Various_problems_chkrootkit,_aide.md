---
title: "Various problems: chkrootkit, aide"
date: 2014-08-02
forum: Security
---

### Post by dunbrokin on 2014-08-02
1) chkrootkit is not producing a log?!

This is the line from my crontab However, the log never gets sent to me..and when I check the log it is empty. I have tried Chkrootkit from the terminal and it runs OK. What am I missing?

30 09 * * * root /usr/sbin/chkrootkit && cat /var/log/chkrootkit/log.today | mail -s "chkrootkit log for $(date)" [email]xxx@gmail.com[/email]

I am using 14.04.

2) this is my crontab for aide...it runs no problem....but not sure how meaningful the output is. Should I be running it with a different switch?

15 09 * * * root /usr/bin/aide/aide.conf --check && head -n 20 /var/log/aide/aide.log | mail -s "Aide log for $(date)" [email]xxxx@gmail.com[/email]

aide run on pj-selxxuild started at 2014-08-02 08:37:38.
AIDE returned with exit code 7. Added, removed and changed entries detected!
AIDE produced no errors.
AIDE output (292772 lines):
lstat() failed for /run/user/1000/gvfs:Permission denied
lstat() failed for /run/user/1001/gvfs:Permission denied
Entry /home/pj/.gvfs in databases has different attributes: 1a00200fbd 800000fbd
Entry /root/.gvfs in databases has different attributes: 800000fbd 1a00200fbd
Entry /usr/sbin/sendmail in databases has different attributes: 1ac027cfbd a00000fbf
Entry /usr/share/applications/defaults.list in databases has different attributes: a00000fbf 1ac027cfbd
AIDE 0.16a2-19-g16ed855 found differences between database and filesystem!!
New AIDE database written to /var/lib/aide/aide.db.new
Start timestamp: 2014-08-02 08:37:38 +1200
Verbose level: 6

Summary:
  Total number of entries:	408490
  Added entries:		106371
  Removed entries:		64054
  Changed entries:		13662

---------------------------------------------------
Added entries:
-------------------------------------

---

### Post by unspawn on 2014-08-03
> **dunbrokin said:**
> chkrootkit is not producing a log?! IIRC Chkrootkit sends output to stdout, meaning you have to send it to whatever destination yourself.   > **dunbrokin said:**
> the log never gets sent to me If that's due to what I wrote about above then try '/usr/sbin/chkrootkit > /var/log/chkrootkit/log.today 2>&1;' or send via email directly: '/usr/sbin/chkrootkit 2>&1| mail -s "chkrootkit log for $(date)" some@address;'. If it's not that then also check your /var/log mail log, because if your IP address is in a range for residential use and you don't use your ISPs MTA then Google may block it.   > **dunbrokin said:**
> lstat() failed for /run/user/1000/gvfs:Permission denied lstat() failed for /run/user/1001/gvfs:Permission denied No idea what subsystem actually uses /run/ (systemd? udev? ^whatever.*kit?) but these are volatile files just like the ones in /proc/.  Unless there's a distinct reason these files and directories should be watched for changes I suggest you exclude them from the database.   > **dunbrokin said:**
> Entry /home/pj/.gvfs in databases has different attributes: 1a00200fbd 800000fbd AFAIK that's a GNOME Virtual File System mount point. Unless you weaken it with mount options I suggest you exclude it from the database.   > **dunbrokin said:**
> Entry /root/.gvfs in databases has different attributes: 800000fbd 1a00200fbd Same here except root should have nothing to do with any runlevel 5 graphical utilities so this shouldn't exist in the first place IMHO.   > **dunbrokin said:**
> Entry /usr/sbin/sendmail in databases has different attributes: 1ac027cfbd a00000fbf Check which attributes changed when, try to correlate the change with running prelink of system updates, else see 'man debsums'.   > **dunbrokin said:**
> Entry /usr/share/applications/defaults.list in databases has different attributes: a00000fbf 1ac027cfbd Same as with the sendmail binary.

---

### Post by dunbrokin on 2014-08-03
Thank you for that, I very much appreciate your help. I will try them out and report back on how it goes.

---

### Post by dunbrokin on 2014-08-07
Thanks your suggestion for chkrootkit worked perfectly.

---

