---
title: "Lock Screen won't unlock with correct password, tried other posts already."
date: 2015-09-29
forum: Security
---

### Post by ahears on 2015-09-29
I just cloned my Hdd to a new drive but left the old swap behind and created a new one. FYI. That being said...

Lock Screen won't unlock with correct password, and I own everything in my home folder:

```

[COLOR=#008000]sudo chown user:user -R /home/user/*[/COLOR][COLOR=#008000]
sudo chown root:shadow /etc/gshadow
sudo chown root:shadow /etc/gshadow-
sudo chown root:shadow /etc/shadow
sudo chown root:shadow /etc/shadow-
sudo chown root:shadow /sbin/unix_chkpwd
sudo chmod 2755 /sbin/unix_chkpwd
mv .bashrc bashrc_old
mv .profile profile_old[/COLOR]

```


Here is the "auth.log" file from the events:

> Sep 28 21:59:01 Linux-PC compiz: gkr-pam: unlocked login keyring
Sep 28 21:59:05 Linux-PC lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Sep 28 21:59:05 Linux-PC lightdm: PAM adding faulty module: pam_kwallet.so
Sep 28 21:59:05 Linux-PC lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Sep 28 21:59:05 Linux-PC lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :1
Sep 28 21:59:05 Linux-PC lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Sep 28 21:59:05 Linux-PC lightdm: PAM adding faulty module: pam_kwallet.so
Sep 28 21:59:05 Linux-PC lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "BADASSUSER"
Sep 28 21:59:08 Linux-PC lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Sep 28 21:59:08 Linux-PC lightdm: PAM adding faulty module: pam_kwallet.so
Sep 28 21:59:08 Linux-PC lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "TESTUSER"
Sep 28 21:59:08 Linux-PC lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Sep 28 21:59:08 Linux-PC lightdm: PAM adding faulty module: pam_kwallet.so
Sep 28 21:59:08 Linux-PC lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "BADASSUSER"
Sep 28 21:59:18 Linux-PC lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Sep 28 22:00:01 Linux-PC CRON[15875]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 28 22:00:01 Linux-PC CRON[15876]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 28 22:00:01 Linux-PC CRON[15875]: pam_unix(cron:session): session closed for user root
Sep 28 22:00:01 Linux-PC CRON[15876]: pam_unix(cron:session): session closed for user root



Ok, now when I run with my Yubikey inserted everything unlocks just fine

```

[COLOR=#008000]/usr/bin/dm-tool lock
[/COLOR]
```

However, when I use** "ctrl+alt+l"** the screen [COLOR=#ff0000]will not unlock with the correct password.

[/COLOR][COLOR=#000000]Also, when I create a new TESTUSER the **ctrl+alt+l **lock screen works fine.

Login works fine with all users. Everything works with my [/COLOR][COLOR=#006400]Yubikey[/COLOR][COLOR=#000000]: login/logout - it's just the [/COLOR][COLOR=#ff0000]Unity Lock screen[/COLOR][COLOR=#000000] that won't unlock.

I also uninstalled and re-installed '[/COLOR][COLOR=#006400]xscreensaver[/COLOR][COLOR=#000000]'... no progress..

Any help is _greatly_ appreciated, Thank you:)
[/COLOR]

---

