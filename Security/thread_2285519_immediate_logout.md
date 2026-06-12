---
title: "immediate logout"
date: 2015-07-06
forum: Security
---

### Post by b49P23TIvg on 2015-07-06
$ cat /etc/issue
Ubuntu 15.04 \n \l

------------------
I update almost daily.  My main account logs me out immediately following login.
I moved ~/.Xauthority to ~/old.Xauthority,
stuck skip-authentication into /etc/pam.conf,
rebooted.
I use the computer daily.  This file didn't change:
```
-rw-r--r-- 1 lambertdw lambertdw 6174 Jun 27 08:46 /home/lambertdw/.bashrc

pam_kwallet.so, whatever that is, failed.  Here are some lines from my /var/log/auth.log file

Jul  6 13:00:27 dwl sudo: lambertdw : TTY=pts/1 ; PWD=/home/t500 ; USER=root ; COMMAND=/bin/cat /var/log/auth.log
Jul  6 13:00:27 dwl sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Jul  6 13:00:28 dwl sudo: pam_unix(sudo:session): session closed for user root
Jul  6 13:01:31 dwl dbus[880]: [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.34" (uid=0 pid=1384 comm="/usr/sbin/lightdm ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.162" (uid=1001 pid=3087 comm="/usr/lib/x86_64-linux-gnu/indicator-session/indica")
Jul  6 13:01:31 dwl lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  6 13:01:31 dwl lightdm: PAM adding faulty module: pam_kwallet.so
Jul  6 13:01:31 dwl lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lambertdw"
Jul  6 13:01:31 dwl lightdm: pam_unix(lightdm:auth): conversation failed
Jul  6 13:01:31 dwl lightdm: pam_unix(lightdm:auth): auth could not identify password for [lambertdw]
Jul  6 13:01:33 dwl lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  6 13:01:33 dwl lightdm: PAM adding faulty module: pam_kwallet.so
Jul  6 13:01:33 dwl lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jul  6 13:01:33 dwl systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Jul  6 13:01:33 dwl systemd-logind[822]: New session c7 of user lightdm.
Jul  6 13:01:33 dwl lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  6 13:01:33 dwl lightdm: PAM adding faulty module: pam_kwallet.so
Jul  6 13:01:33 dwl lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lambertdw"
Jul  6 13:01:40 dwl lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Jul  6 13:01:40 dwl lightdm: pam_unix(lightdm:session): session opened for user lambertdw by (uid=0)
Jul  6 13:01:40 dwl systemd-logind[822]: New session c8 of user lambertdw.
Jul  6 13:01:40 dwl systemd: pam_unix(systemd-user:session): session opened for user lambertdw by (uid=0)
Jul  6 13:01:42 dwl lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  6 13:01:42 dwl lightdm: PAM adding faulty module: pam_kwallet.so
Jul  6 13:01:42 dwl lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jul  6 13:01:42 dwl systemd-logind[822]: New session c9 of user lightdm.
Jul  6 13:01:42 dwl lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  6 13:01:42 dwl lightdm: PAM adding faulty module: pam_kwallet.so
Jul  6 13:01:42 dwl lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "lambertdw"
Jul  6 13:01:45 dwl lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  6 13:01:45 dwl lightdm: PAM adding faulty module: pam_kwallet.so
Jul  6 13:01:45 dwl lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dwl"
Jul  6 13:01:52 dwl lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Jul  6 13:01:59 dwl sudo: lambertdw : TTY=pts/1 ; PWD=/home/t500 ; USER=root ; COMMAND=/bin/cat /var/log/auth.log
Jul  6 13:01:59 dwl sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Jul  6 13:01:59 dwl sudo: pam_unix(sudo:session): session closed for user root
Jul  6 13:02:51 dwl sudo: lambertdw : TTY=pts/1 ; PWD=/home/t500 ; USER=root ; COMMAND=/bin/cat /var/log/auth.log
Jul  6 13:02:51 dwl sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
```


Please advise, I'd like to log in to my normal account!
Thanks.  David Lambert

ps:
```
$ sudo updatedb
$ locate wallet
/home/lambertdw/.config/google-chrome/Default/Local Storage/http_rs.gwallet.com_0.localstorage
/home/lambertdw/.config/google-chrome/Default/Local Storage/http_rs.gwallet.com_0.localstorage-journal
/usr/lib/python2.7/dist-packages/keyring/backends/kwallet.py
/usr/lib/python2.7/dist-packages/keyring/backends/kwallet.pyc
/usr/lib/python2.7/dist-packages/keyring/tests/backends/test_kwallet.py
/usr/lib/python2.7/dist-packages/keyring/tests/backends/test_kwallet.pyc
/usr/share/app-install/desktop/kwalletmanager:kde4__kwalletmanager.desktop
/usr/share/app-install/icons/kwalletmanager.png
```

---

### Post by NoWayWin8 on 2015-07-06
Something is incorrectly owned by root instead of yourself. At the greeter/login screen drop to terminal login with ctrl+alt+F1, login to it then look at the owner of files in your Home directory.
```
ls -al
```
See what the offending item is (probably .Xauthority) and fix it with **chown**.

---

### Post by b49P23TIvg on 2015-07-07
Thank you, and whoops!  ls -l ~/.. showed that I wasn't owner of my account.  I over-zealously changed owners of files in my account from another computer from me to new account name.  This mistake was more easily recovered than when with privilege I recursively deleted files from, yes, / .  That was in the early '90s.

---

