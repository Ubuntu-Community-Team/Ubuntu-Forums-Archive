---
title: "cracked?"
date: 2012-05-01
forum: Security
---

### Post by jpdeaton on 2012-05-01
Feels weird man. Someone has been ******* with all my logs and timestamps. The last modified dates for most logs is yesterday when it was too date earlier.

I ran this today (may 1)
```
sudo less /var/log/auth.log
Apr 29 13:17:01 bob-K84L CRON[2825]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 29 13:17:01 bob-K84L CRON[2825]: pam_unix(cron:session): session closed for user root
Apr 29 14:17:01 bob-K84L CRON[3196]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 29 14:17:01 bob-K84L CRON[3196]: pam_unix(cron:session): session closed for user root
Apr 29 15:00:37 bob-K84L gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr 29 15:17:01 bob-K84L CRON[4027]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 29 15:17:01 bob-K84L CRON[4027]: pam_unix(cron:session): session closed for user root
Apr 29 16:17:01 bob-K84L CRON[4591]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 29 16:17:01 bob-K84L CRON[4591]: pam_unix(cron:session): session closed for user root
Apr 29 16:43:00 bob-K84L gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr 29 17:17:01 bob-K84L CRON[4912]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 29 17:17:01 bob-K84L CRON[4912]: pam_unix(cron:session): session closed for user root
Apr 29 18:03:02 bob-K84L gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Apr 29 18:17:01 bob-K84L CRON[5485]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 29 18:17:01 bob-K84L CRON[5485]: pam_unix(cron:session): session closed for user root
Apr 29 19:02:41 bob-K84L gdm-session-worker[1366]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "bob"
Apr 29 19:02:50 bob-K84L gdm-session-worker[1366]: pam_unix(gdm:session): session opened for user bob by (uid=0)
Apr 29 19:02:50 bob-K84L gdm-session-worker[1366]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 29 19:02:56 bob-K84L polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.54 [/usr/bin/gnome-shell], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Apr 29 19:17:01 bob-K84L CRON[1856]: pam_unix(cron:session): session opened for user root by (uid=0)
:
```
also i cant view faillog. Some unknown uid can though.

```
  `/var/log/faillog'
  Size: 24048         Blocks: 16         IO Block: 4096   regular file
Device: 801h/2049d    Inode: 8526742     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2012-05-01 05:10:40.345612278 -0400
Modify: 2012-05-01 02:33:15.949367376 -0400
Change: 2012-05-01 02:33:15.949367376 -0400

bob@bob-K84L:~$ id
uid=1000(bob) gid=1000(bob) groups=1000(bob),4(adm),20(dialout),24(cdrom),46(plugdev),116(lpadmin),118(admin),124(sambashare)
```

---

### Post by unspawn on 2012-05-01
> **jpdeaton said:**
> Someone has been ******* with all my logs and timestamps.
I don't see any evidence in your posted log lines that supports that.


> **jpdeaton said:**
> The last modified dates for most logs is yesterday when it was too date earlier.
Instead of *telling* us about it post the output of running 'date' and running 'stat' on the log file(s). 

*BTW if you emphasized certain log lines to ask questions about them then please post only those lines *and tell us what you think you are seeing*. (But in your case it's not necessary really, as far as I see it all looks OK.)

//Please note the above reply was based on the 2 initial posts by the OP comprising of uncut /var/log/messages and crond output. The OP since has (or moderators since have) edited his posts at least two times.

---

### Post by Ms. Daisy on 2012-05-01
Agree with unspawn.

Also, if you'd like to audit your logs, you can check out the [did I just get owned wiki]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned") for some help on that.  It would also help you to identify the truly suspicious stuff that you should post here to get help on.

---

### Post by CharlesA on 2012-05-02
> **Ms. Daisy said:**
> Agree with unspawn.

Also, if you'd like to audit your logs, you can check out the [did I just get owned wiki]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned") for some help on that.  It would also help you to identify the truly suspicious stuff that you should post here to get help on.
Agreed.

The auth.log looks fine from what I can see.

---

