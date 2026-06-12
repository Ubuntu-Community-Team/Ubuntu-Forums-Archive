---
title: "Revert the original user for the fs / and recursive"
date: 2010-07-07
forum: Security
---

### Post by braiamp on 2010-07-07
Hello,

I have a real big problem:

Trying to configurate gadmid-bind, I change the user and group of my entire filesystem, I archive some advance getting all back but for now,sudo leave me with a problem about guid, i changed sudoers to root againg, but i don't get all back.

The folders that are owned by root in the current and recursively:

/bin
/sbin
/usr/bin
/usr/sbin
/etc, partialy
/dev
/var

I dosen't have network connection, because nm-applet dosen't start on my user, and when i run on a xserver with root user it give me: The device is not ready.

I dosen't had the change to review for typo, please forgive me for that.  I will user the root user and group to all archives, if some folder or file need to have a special user let me know.

---

### Post by movieman on 2010-07-07
That's pretty much unrecoverable if you didn't have a backup: reinstalling will probably be faster than trying to fix it manually.

---

### Post by braiamp on 2010-07-08
> **movieman said:**
> That's pretty much unrecoverable if you didn't have a backup: reinstalling will probably be faster than trying to fix it manually.

Maybe I'm a hard breaking head, I would like to recover it manualy.

I get that more of the system work. I doesn't worry about a backup, I have my /home on another partition. This is a snapshot:

My /home, recursive are owned by my default user, this leave me login as my user w/out errors, but less funcionality:

[LIST=1]
[*]nm-applet dosen't start when I login as my user, but when I start a xserver as root it start.
[*]The sound system desen't work. I don't kwon much about pulseaudio, alsa or whatever that I use to get sound, even when I'm root.
[*]sudo dosen't work completly. And maybe this is the source of all problems. And this threat will be only for resolve this.
[/LIST]

I'll open a threat about each one of my problems in they respective forums, exept this:

sudo work as expected when I login as root. But when I'm user trying to get su privilegies I get a error that I describes after. I'll paste my auth.log, I see some messages about dbus and gnome-keyring-daemon. I do dpkg-reconfigure to try get to normaly, but doesn't do anything. Maybe pam, but someone should know.

```
Jul  7 01:06:34 braiam-desktop unix_chkpwd[18503]: check pass; user unknown
Jul  7 01:06:34 braiam-desktop unix_chkpwd[18503]: password check failed for user (root)
Jul  7 01:06:34 braiam-desktop su[16824]: pam_unix(su:auth): authentication failure; logname= uid=1000 euid=1000 tty=/dev/pts/1 ruser=braiam rhost=  user=root
Jul  7 01:06:34 braiam-desktop su[16824]: pam_winbind(su:auth): getting password (0x00000388)
Jul  7 01:06:34 braiam-desktop su[16824]: pam_winbind(su:auth): pam_get_item returned a password
Jul  7 01:06:34 braiam-desktop su[16824]: pam_winbind(su:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jul  7 01:06:36 braiam-desktop su[16824]: pam_authenticate: Authentication failure
Jul  7 01:06:36 braiam-desktop su[16824]: FAILED su for root by braiam
Jul  7 01:06:36 braiam-desktop su[16824]: - /dev/pts/1 braiam:root
Jul  7 01:06:52 braiam-desktop unix_chkpwd[23999]: check pass; user unknown
Jul  7 01:06:52 braiam-desktop unix_chkpwd[23999]: password check failed for user (root)
Jul  7 01:06:52 braiam-desktop su[23068]: pam_unix(su:auth): authentication failure; logname= uid=1000 euid=1000 tty=/dev/pts/1 ruser=braiam rhost=  user=root
Jul  7 01:06:52 braiam-desktop su[23068]: pam_winbind(su:auth): getting password (0x00000388)
Jul  7 01:06:52 braiam-desktop su[23068]: pam_winbind(su:auth): pam_get_item returned a password
Jul  7 01:06:52 braiam-desktop su[23068]: pam_winbind(su:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jul  7 01:06:54 braiam-desktop su[23068]: pam_authenticate: Authentication failure
Jul  7 01:06:54 braiam-desktop su[23068]: FAILED su for root by braiam
Jul  7 01:06:54 braiam-desktop su[23068]: - /dev/pts/1 braiam:root
Jul  7 01:07:49 braiam-desktop login[1432]: pam_unix(login:session): session opened for user braiam by LOGIN(uid=0)
Jul  7 01:16:28 braiam-desktop gdm-session-worker[866]: pam_unix(gdm-autologin:session): session closed for user braiam
Jul  7 01:17:01 braiam-desktop CRON[19678]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  7 01:17:01 braiam-desktop CRON[19678]: pam_unix(cron:session): session closed for user root
Jul  8 03:10:05 braiam-desktop gdm-session-worker[913]: pam_unix(gdm-autologin:session): session opened for user braiam by (uid=0)
Jul  8 03:10:05 braiam-desktop gdm-session-worker[913]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Jul  8 03:10:29 braiam-desktop gnome-keyring-daemon[1074]: PROMPT INPUT:#012#012[prompt]#012title=Desbloquear el depósito de inicio#012primary=Introducir la contraseña para desbloquear el depósito#012secondary=El depósito de inicio de sesión no se desbloqueó cuando inició sesión en su equipo.#012window-id=#012#012[visibility]#012name_area=false#012confirm_area=false#012password_area=true#012#012[transport]#012public=689C582B681A9A6CA73110BF89AE61590627AB10A9EA284F5AF172A8994B87A57C7EDB4D35019DFAD99ADC66B81403709AB8B5C557CE09AC8CD967AEDD09755E9E1C9D9461E9CD52C768F9313B044EFBBD08B9AE7CD3598855E6B2CCE04FBDFE127FB25397260DFBAE48C6A2E42A474ACDF2F575F1FA40D9340D42285C78E1D067CDCCF10F89D6A90209C991C71F140F793E487A50B0D7B52963059F2F8E0FC39AB9C0ECC75E347EDDDCE7D4D31F23F83182994A192E11171314FD20E6CDB478#012prime=FFFFFFFFFFFFFFFFC90FDAA22168C234C4C6628B80DC1CD129024E088A67CC74020BBEA63B139B22514A08798E3404DDEF9519B3CD3A431B302B0A6DF25F14374FE1356D6D51C245E485B576625E7EC6F44C42E9A637ED6B0BFF5CB6F406B7EDEE386BFB5A899FA5AE9F24117C4B1FE649286651ECE45B3DC2007CB8A163BF0598DA48361C55D39A69163FA8FD24CF5F83655D23DCA3AD961C62F356208552BB9ED529077096966D670C354E4ABC9804F1746C08CA237327FFFFFFFFFFFFFFFF#012base=02#012
Jul  8 03:12:16 braiam-desktop gnome-keyring-daemon[1074]: PROMPT OUTPUT:#012#012[transport]#012public=AA09E7DB5E32B9F03A10C3493ACEE5F73DC37CA73225244EBA68BA587614A06D2C32AC9A6C727C406964ED47F90656B2D9FC79487A9CD7541E681B7E53F62B9227AF7BAB8546C666EE577B6876563CA14D40888138F863144A77F136B4465157908C7301207891B58273F12EA61A3F423DBDEFE7E57F5DD00641AB00F8F8955A264111C42E0EE703815A8669C5360B80AD1A5B64E9C86F4C72F993FF1B676D9E911E454B0218AE250F92E405F657D73567CEFAC9EDE3BABA784FF6E7B3FF3D38#012#012[password]#012parameter=04E784BC8257AD0F60DA9DEB6939AB1E#012value=880614ADB5153AC1A6B0E0ACB058CB57#012#012[unlock-options]#012unlock-auto=false#012unlock-timeout=0#012unlock-idle=0#012#012[details]#012expanded=false#012#012[prompt]#012response=ok#012
Jul  8 03:12:53 braiam-desktop gdm-session-worker[913]: pam_unix(gdm-autologin:session): session closed for user braiam
Jul  8 04:09:23 braiam-desktop gdm-session-worker[909]: pam_unix(gdm-autologin:session): session opened for user braiam by (uid=0)
Jul  8 04:09:23 braiam-desktop gdm-session-worker[909]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Jul  8 04:10:03 braiam-desktop login[1311]: pam_unix(login:session): session opened for user braiam by LOGIN(uid=0)
Jul  8 04:10:24 braiam-desktop login[1311]: pam_unix(login:session): session closed for user braiam
Jul  8 04:10:42 braiam-desktop login[1435]: pam_unix(login:session): session opened for user braiam by LOGIN(uid=0)
Jul  8 04:11:49 braiam-desktop gnome-keyring-daemon[1564]: unable to create keyring dir: /home/braiam/.gnome2/keyrings
Jul  8 04:12:34 braiam-desktop unix_chkpwd[1687]: check pass; user unknown
Jul  8 04:12:37 braiam-desktop unix_chkpwd[1689]: check pass; user unknown
Jul  8 04:12:37 braiam-desktop unix_chkpwd[1689]: password check failed for user (root)
Jul  8 04:12:37 braiam-desktop su[1686]: pam_unix(su:auth): authentication failure; logname=braiam uid=1000 euid=1000 tty=/dev/tty1 ruser=braiam rhost=  user=root
Jul  8 04:12:37 braiam-desktop su[1686]: pam_winbind(su:auth): getting password (0x00000388)
Jul  8 04:12:37 braiam-desktop su[1686]: pam_winbind(su:auth): pam_get_item returned a password
Jul  8 04:12:37 braiam-desktop su[1686]: pam_winbind(su:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jul  8 04:12:40 braiam-desktop su[1686]: pam_authenticate: Authentication failure
Jul  8 04:12:40 braiam-desktop su[1686]: FAILED su for root by braiam
Jul  8 04:12:40 braiam-desktop su[1686]: - /dev/tty1 braiam:root
Jul  8 04:12:42 braiam-desktop unix_chkpwd[1692]: check pass; user unknown
Jul  8 04:12:43 braiam-desktop unix_chkpwd[1693]: check pass; user unknown
Jul  8 04:12:43 braiam-desktop su[1691]: pam_unix(su:auth): authentication failure; logname=braiam uid=1000 euid=1000 tty=/dev/tty1 ruser=braiam rhost=  user=root
Jul  8 04:12:43 braiam-desktop su[1691]: pam_winbind(su:auth): getting password (0x00000388)
Jul  8 04:12:43 braiam-desktop su[1691]: pam_winbind(su:auth): pam_get_item returned a password
Jul  8 04:12:43 braiam-desktop su[1691]: pam_winbind(su:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jul  8 04:12:45 braiam-desktop su[1691]: pam_authenticate: Authentication failure
Jul  8 04:12:45 braiam-desktop su[1691]: FAILED su for root by braiam
Jul  8 04:12:45 braiam-desktop su[1691]: - /dev/tty1 braiam:root
Jul  8 04:12:46 braiam-desktop unix_chkpwd[1696]: check pass; user unknown
Jul  8 04:12:50 braiam-desktop unix_chkpwd[1697]: check pass; user unknown
Jul  8 04:12:50 braiam-desktop unix_chkpwd[1697]: password check failed for user (root)
Jul  8 04:12:50 braiam-desktop su[1695]: pam_unix(su:auth): authentication failure; logname=braiam uid=1000 euid=1000 tty=/dev/tty1 ruser=braiam rhost=  user=root
Jul  8 04:12:50 braiam-desktop su[1695]: pam_winbind(su:auth): getting password (0x00000388)
Jul  8 04:12:50 braiam-desktop su[1695]: pam_winbind(su:auth): pam_get_item returned a password
Jul  8 04:12:50 braiam-desktop su[1695]: pam_winbind(su:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jul  8 04:12:52 braiam-desktop su[1695]: pam_authenticate: Authentication failure
Jul  8 04:12:52 braiam-desktop su[1695]: FAILED su for root by braiam
Jul  8 04:12:52 braiam-desktop su[1695]: - /dev/tty1 braiam:root
Jul  8 04:16:37 braiam-desktop gdm-session-worker[1181]: pam_unix(gdm-autologin:session): session opened for user braiam by (uid=0)
Jul  8 04:16:37 braiam-desktop gdm-session-worker[1181]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :1
Jul  8 04:17:08 braiam-desktop gnome-keyring-daemon[1258]: unable to create keyring dir: /home/braiam/.gnome2/keyrings
Jul  8 04:22:48 braiam-desktop login[1472]: pam_unix(login:session): session opened for user braiam by LOGIN(uid=0)
Jul  8 04:22:53 braiam-desktop login[1472]: pam_unix(login:session): session closed for user braiam
Jul  8 04:24:06 braiam-desktop gdm-session-worker[998]: pam_unix(gdm-autologin:session): session opened for user braiam by (uid=0)
Jul  8 04:24:06 braiam-desktop gdm-session-worker[998]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :1
Jul  8 04:24:23 braiam-desktop gnome-keyring-daemon[1061]: PROMPT INPUT:#012#012[prompt]#012title=Desbloquear el depósito de inicio#012primary=Introducir la contraseña para desbloquear el depósito#012secondary=El depósito de inicio de sesión no se desbloqueó cuando inició sesión en su equipo.#012window-id=#012#012[visibility]#012name_area=false#012confirm_area=false#012password_area=true#012#012[transport]#012public=056B8BC366D3A17E39888C4A438387222B3BFFFC9375CEB6F5F79F7705EAE4CF134EFB86EB01B1FCBC80515562D13F0C14A9C4BF579285A698F0EF7775B6BED5AF97BE34F2DB41A3E7B35320780433F1FD8C71D2290BF669FD1E8AF284BB13C5636D6A4D02EF4E7FEFE2E3D5366BFE67908F6988168613297A575614AEDC82D784C61101B5B06D52DD70A7858CE3AEC8A71659034EBC499887FD8A348999AAA155A28277588EC7A09E3AFE4BF6E9F83084D3C78C1DC1A337F71CDCDB154F4117#012prime=FFFFFFFFFFFFFFFFC90FDAA22168C234C4C6628B80DC1CD129024E088A67CC74020BBEA63B139B22514A08798E3404DDEF9519B3CD3A431B302B0A6DF25F14374FE1356D6D51C245E485B576625E7EC6F44C42E9A637ED6B0BFF5CB6F406B7EDEE386BFB5A899FA5AE9F24117C4B1FE649286651ECE45B3DC2007CB8A163BF0598DA48361C55D39A69163FA8FD24CF5F83655D23DCA3AD961C62F356208552BB9ED529077096966D670C354E4ABC9804F1746C08CA237327FFFFFFFFFFFFFFFF#012base=02#012
Jul  8 04:24:24 braiam-desktop gnome-keyring-prompt: could not grab keyboard: 3
Jul  8 04:24:24 braiam-desktop gnome-keyring-prompt: could not grab keyboard: 3
Jul  8 04:24:29 braiam-desktop gnome-keyring-daemon[1061]: PROMPT OUTPUT:#012#012[transport]#012public=DF70792284D75CDE9891322CA9DE7BCDFF212F5005A0075857C371549E6824BC3CB4F2B654BCDA92ED41D74716C2440134FBFB1C56D14218D1A9274702D5990CABAEFF4FB7B2E126D5ECEDFA18D8E28B5B7EA1F7B5B178A55C54A6FF45FCB9992D3FE23747C74604A82F80424B88A3B5B6FEBD506EAC49411803A0D119D683233F540DAC016DB166620AA0C8115A51E2EB5F6EC0F447F359038305079A17B1F8722E7403284CAA616503E1A78FCD787D5CADD3961684F64A3E43CCE923ED88BA#012#012[password]#012parameter=0A02757552F694A3AA02B183EC7234D5#012value=8ED13F8B475DFE3EA2B8CFA12349BFBB#012#012[unlock-options]#012unlock-auto=false#012unlock-timeout=0#012unlock-idle=0#012#012[details]#012expanded=false#012#012[prompt]#012response=ok#012
Jul  8 04:36:39 braiam-desktop gnome-keyring-daemon[14803]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:36:39 braiam-desktop gnome-keyring-daemon[14803]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Jul  8 04:36:43 braiam-desktop gnome-keyring-daemon[15530]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:36:43 braiam-desktop gnome-keyring-daemon[15530]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Jul  8 04:36:45 braiam-desktop gnome-keyring-daemon[15778]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:36:45 braiam-desktop gnome-keyring-daemon[15778]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Jul  8 04:37:03 braiam-desktop gnome-keyring-daemon[18770]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:37:03 braiam-desktop gnome-keyring-daemon[18779]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:37:03 braiam-desktop gnome-keyring-daemon[18779]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Jul  8 04:38:00 braiam-desktop gnome-keyring-daemon[27733]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:38:00 braiam-desktop gnome-keyring-daemon[27754]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:38:00 braiam-desktop gnome-keyring-daemon[27754]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed
Jul  8 04:38:12 braiam-desktop gnome-keyring-daemon[29661]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul  8 04:38:12 braiam-desktop gnome-keyring-daemon[29661]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed

```

---

### Post by braiamp on 2010-07-08
Note: I have access to all my system as read-only. Any log that could be reviewed I can copy-paste them.

---

### Post by cariboo on 2010-07-08
If it was a matter of only root, or your user owning everything, it would be fairly simple to fix the problem, but what about all the other users on your system? I have the following users on my system:

```
cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:107::/var/run/dbus:/bin/false
avahi-autoipd:x:103:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
speech-dispatcher:x:106:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
usbmux:x:107:46:usbmux daemon,,,:/home/usbmux:/bin/false
haldaemon:x:108:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:117:RealtimeKit,,,:/proc:/bin/false
saned:x:112:118::/home/saned:/bin/false
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:114:120:Gnome Display Manager:/var/lib/gdm:/bin/false
me:x:1000:1000:me,,,:/home/me:/bin/bash
statd:x:115:65534::/var/lib/nfs:/bin/false
sshd:x:116:65534::/var/run/sshd:/usr/sbin/nologin
```

---

### Post by bodhi.zazen on 2010-07-08
> **braiamp said:**
> Maybe I'm a hard breaking head, I would like to recover it manualy.

You would need to manually go through every file and directory in / and set the proper permissions.

To do so, you would need to reference to a known good install with the same configuration as your system.

So while it can be done, it will take you some time.

You can boot a live CD, mount your install in a chroot, and start looking at permissions on the live CD and start restoring them in the chroot.

Knock yourself out.

---

### Post by sisco311 on 2010-07-08
> **braiamp said:**
> 
sudo dosen't work completly. And maybe this is the source of all problems. And this threat will be only for resolve this.


sudo must be setuid root. chown clears the setuid and setgid flags. 

Here is a list of setuid and setgid files and directories installed on my system:
```
find / -perm +6000 -exec ls -aldh '{}' + 2> /dev/null 
-rwsr-xr-x  1 root        root        31K 2010-01-27 00:28 /bin/fusermount
-rwsr-xr-x  1 root        root        81K 2010-03-22 17:57 /bin/mount
-rwsr-xr-x  1 root        root        35K 2010-06-19 19:47 /bin/ping
-rwsr-xr-x  1 root        root        40K 2010-06-19 19:47 /bin/ping6
-rwsr-xr-x  1 root        root        36K 2010-01-26 17:09 /bin/su
-rwsr-xr-x  1 root        root        56K 2010-03-22 17:57 /bin/umount
drwxr-s---  2 root        dip        4.0K 2010-05-04 18:34 /etc/chatscripts
drwxr-s---  2 root        dip        4.0K 2010-05-04 18:34 /etc/ppp/peers
-rwsr-xr-x  1 root        root        70K 2010-07-06 11:18 /home/sisco/pinger-0.32d/deb/data/usr/bin/pinger
-rwsr-xr--  1 root        messagebus  47K 2010-03-30 18:43 /lib/dbus-1.0/dbus-daemon-launch-helper
-rwxr-sr-x  1 root        shadow      35K 2010-07-07 23:25 /sbin/unix_chkpwd
drwxrwsr-x  3 root        src        4.0K 2010-06-29 11:33 /srv/cvs
drwxrwsr-x  3 root        src        4.0K 2010-06-29 11:33 /srv/cvs/CVSROOT
drwxrwsr-x  2 root        src        4.0K 2010-06-29 11:33 /srv/cvs/CVSROOT/Emptydir
-rwsr-xr-x  1 root        root        19K 2010-06-19 19:47 /usr/bin/arping
-rwsr-sr-x  1 daemon      daemon      51K 2010-06-27 19:38 /usr/bin/at
-rwxr-sr-x  1 root        tty         15K 2010-05-27 09:28 /usr/bin/bsd-write
-rwxr-sr-x  1 root        shadow      58K 2010-01-26 17:09 /usr/bin/chage
-rwsr-xr-x  1 root        root        41K 2010-01-26 17:09 /usr/bin/chfn
-rwsr-xr-x  1 root        root        37K 2010-01-26 17:09 /usr/bin/chsh
-rwxr-sr-x  1 root        crontab     37K 2010-06-25 22:13 /usr/bin/crontab
-rwxr-sr-x  1 root        mail        15K 2010-05-18 15:03 /usr/bin/dotlockfile
-rwxr-sr-x  1 root        shadow      23K 2010-01-26 17:09 /usr/bin/expiry
-rwsr-xr-x  1 root        root        63K 2010-01-26 17:09 /usr/bin/gpasswd
-rwsr-xr-x  1 root        lpadmin     14K 2010-06-29 18:16 /usr/bin/lppasswd
-rwxr-sr-x  3 root        mail        15K 2010-06-22 18:27 /usr/bin/mail-lock
-rwxr-sr-x  3 root        mail        15K 2010-06-22 18:27 /usr/bin/mail-touchlock
-rwxr-sr-x  3 root        mail        15K 2010-06-22 18:27 /usr/bin/mail-unlock
-rwxr-sr-x  1 root        mlocate     35K 2010-03-24 12:35 /usr/bin/mlocate
-rwxr-sr-x  1 root        mail        11K 2010-02-11 02:47 /usr/bin/mlock
-rwsr-xr-x  1 root        root        61K 2010-03-07 03:56 /usr/bin/mtr
-rwsr-xr-x  1 root        root        32K 2010-01-26 17:09 /usr/bin/newgrp
-rwsr-xr-x  1 root        root        42K 2010-01-26 17:09 /usr/bin/passwd
-rwsr-xr-x  1 root        root        19K 2010-04-09 14:47 /usr/bin/pkexec
-rwxr-sr-x  1 root        utmp       368K 2010-06-18 21:13 /usr/bin/screen
-rwxr-sr-x  1 root        ssh        107K 2010-05-27 10:00 /usr/bin/ssh-agent
-rwsr-xr-x  2 root        root       145K 2010-07-06 22:22 /usr/bin/sudo
-rwsr-xr-x  2 root        root       145K 2010-07-06 22:22 /usr/bin/sudoedit
-rwsr-xr-x  1 root        root        19K 2010-06-19 19:47 /usr/bin/traceroute6.iputils
-rwxr-sr-x  1 root        tty         15K 2010-03-22 17:57 /usr/bin/wall
-rwsr-sr-x  1 root        root        11K 2010-04-09 02:07 /usr/bin/X
-rwxr-sr-x  1 root        utmp       413K 2010-06-11 03:46 /usr/bin/xterm
-r-xr-sr-x  1 root        games      159K 2010-07-06 05:58 /usr/games/gnomine
-r-xr-sr-x  1 root        games      125K 2010-07-06 05:58 /usr/games/mahjongg
-r-xr-sr-x  1 root        games      141K 2010-07-06 05:58 /usr/games/quadrapassel
-rwsr-xr-x  1 root        root        11K 2009-11-10 08:07 /usr/lib/eject/dmcrypt-get-device
-rwxr-sr-x  1 root        mail        15K 2010-06-28 17:24 /usr/lib/evolution/camel-lock-helper-1.2
-rwsr-xr-x  1 root        root        11K 2009-11-21 09:45 /usr/lib/kde4/libexec/fileshareset
-rwxr-sr-x  1 root        nogroup     56K 2010-06-28 11:09 /usr/lib/kde4/libexec/kdesud
-rwxr-sr-x  1 root        utmp        15K 2010-05-27 10:17 /usr/lib/libvte9/gnome-pty-helper
-rwsr-xr-x  1 root        root       208K 2010-05-27 10:00 /usr/lib/openssh/ssh-keysign
-rwsr-xr-x  1 root        root        15K 2010-04-09 14:47 /usr/lib/policykit-1/polkit-agent-helper-1
-rwsr-xr-x  1 root        root        11K 2010-06-28 00:45 /usr/lib/pt_chown
drwxrwsr-x  4 root        staff      4.0K 2010-07-06 22:26 /usr/local/lib/python2.6
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:11 /usr/local/lib/python2.6/dist-packages
drwxrwsr-x  2 root        staff      4.0K 2010-07-06 22:26 /usr/local/lib/python2.6/site-packages
drwxrwsr-x  2 root        staff      4.0K 2010-07-01 10:54 /usr/local/lib/site_ruby/1.8/x86_64-linux
drwxrwsr-x  2 root        staff      4.0K 2010-07-05 15:50 /usr/local/share/asterisk/sounds
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:15 /usr/local/share/ca-certificates
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 18:02 /usr/local/share/fonts
drwxrwsr-x  2 root        staff      4.0K 2010-07-05 15:10 /usr/local/share/ppd
drwxrwsr-x  7 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/declaration
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/dtd
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/entities
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/misc
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/stylesheet
drwxrwsr-x  2 root        staff      4.0K 2010-06-26 16:03 /usr/local/share/texmf
drwxrwsr-x  6 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/declaration
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/entities
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/misc
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/schema
drwxrwsr-x  2 root        staff      4.0K 2010-05-28 14:27 /usr/local/share/zsh/site-functions
-rwsr-xr-x  1 root        root        32K 2010-05-12 23:10 /usr/sbin/hddtemp
-rwsr-xr--  1 root        dip        315K 2010-03-07 05:37 /usr/sbin/pppd
-rwsr-sr-x  1 libuuid     libuuid     19K 2010-03-22 17:57 /usr/sbin/uuidd
-rws--x--x  1 root        root        31K 2008-06-19 13:28 /usr/sbin/vlock-main
drwxrwsr-t  2 root        lpadmin    4.0K 2010-04-09 17:03 /usr/share/ppd/custom
drwxrwsr-x 25 root        src        4.0K 2010-07-08 15:25 /usr/src
drwxrwsr-t  2 root        admin      4.0K 2010-05-04 20:02 /var/cache/jockey
drwxr-sr-x 39 man         root       4.0K 2010-07-08 15:25 /var/cache/man
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ca
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/ca/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-25 14:32 /var/cache/man/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat2
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat3
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat4
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat6
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat7
drwxr-sr-x  2 man         root       4.0K 2010-06-25 11:38 /var/cache/man/cat8
drwxr-sr-x  6 man         root       4.0K 2010-07-08 15:25 /var/cache/man/cs
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/da
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/da/cat1
drwxr-sr-x  7 man         root       4.0K 2010-07-08 15:25 /var/cache/man/de
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat3
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/de.UTF-8
drwxr-sr-x  2 man         root       4.0K 2010-06-29 14:00 /var/cache/man/de.UTF-8/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/es
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/es/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/es/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/es/cat8
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fi
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fi/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fi/cat8
drwxr-sr-x  7 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fr
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat3
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat8
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fr.ISO8859-1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.ISO8859-1/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.ISO8859-1/cat8
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fr.UTF-8
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.UTF-8/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.UTF-8/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/gl
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/gl/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/hr
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/hr/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/hu
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/hu/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/hu/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/hu/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/id
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/id/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/id/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/id/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/it
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/it/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/it/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/it/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ja
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/ja/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/ja/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/ja/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ko
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ko/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ko/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ko/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/nl
drwxr-sr-x  2 man         root       4.0K 2010-05-04 20:00 /var/cache/man/nl/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/pl
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pl/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pl/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pl/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/pt
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/pt_BR
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pt_BR/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pt_BR/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pt_BR/cat8
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/pt/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ru
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ru/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ru/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ru/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/sv
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/sv/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/sv/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/sv/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/tr
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/tr/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/tr/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/tr/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ug
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/ug/cat1
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/vi
drwxr-sr-x  2 man         root       4.0K 2010-06-29 11:32 /var/cache/man/vi/cat1
drwxr-sr-x  2 man         root       4.0K 2010-06-29 11:32 /var/cache/man/vi/cat7
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/zh
drwxr-sr-x  2 man         root       4.0K 2010-06-26 16:21 /var/cache/man/zh/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/zh_CN
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_CN/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_CN/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_CN/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/zh_TW
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_TW/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_TW/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_TW/cat8
drwxrwsr-x  2 libuuid     libuuid    4.0K 2010-05-04 17:11 /var/lib/libuuid
drwxrwsr-x  2 root        staff      4.0K 2010-04-23 10:23 /var/local
drwxr-s---  2 Debian-exim adm        4.0K 2010-06-26 13:34 /var/log/exim4
drwxr-s---  2 mysql       adm        4.0K 2010-07-06 04:47 /var/log/mysql
drwxrwsr-x  2 root        mail       4.0K 2010-05-04 17:04 /var/mail

```

> **bodhi.zazen said:**
> 
Knock yourself out.

LOL

---

### Post by braiamp on 2010-07-11
> **sisco311 said:**
> sudo must be setuid root. chown clears the setuid and setgid flags. 

Here is a list of setuid and setgid files and directories installed on my system:
```
find / -perm +6000 -exec ls -aldh '{}' + 2> /dev/null 
-rwsr-xr-x  1 root        root        31K 2010-01-27 00:28 /bin/fusermount
-rwsr-xr-x  1 root        root        81K 2010-03-22 17:57 /bin/mount
-rwsr-xr-x  1 root        root        35K 2010-06-19 19:47 /bin/ping
-rwsr-xr-x  1 root        root        40K 2010-06-19 19:47 /bin/ping6
-rwsr-xr-x  1 root        root        36K 2010-01-26 17:09 /bin/su
-rwsr-xr-x  1 root        root        56K 2010-03-22 17:57 /bin/umount
drwxr-s---  2 root        dip        4.0K 2010-05-04 18:34 /etc/chatscripts
drwxr-s---  2 root        dip        4.0K 2010-05-04 18:34 /etc/ppp/peers
-rwsr-xr-x  1 root        root        70K 2010-07-06 11:18 /home/sisco/pinger-0.32d/deb/data/usr/bin/pinger
-rwsr-xr--  1 root        messagebus  47K 2010-03-30 18:43 /lib/dbus-1.0/dbus-daemon-launch-helper
-rwxr-sr-x  1 root        shadow      35K 2010-07-07 23:25 /sbin/unix_chkpwd
drwxrwsr-x  3 root        src        4.0K 2010-06-29 11:33 /srv/cvs
drwxrwsr-x  3 root        src        4.0K 2010-06-29 11:33 /srv/cvs/CVSROOT
drwxrwsr-x  2 root        src        4.0K 2010-06-29 11:33 /srv/cvs/CVSROOT/Emptydir
-rwsr-xr-x  1 root        root        19K 2010-06-19 19:47 /usr/bin/arping
-rwsr-sr-x  1 daemon      daemon      51K 2010-06-27 19:38 /usr/bin/at
-rwxr-sr-x  1 root        tty         15K 2010-05-27 09:28 /usr/bin/bsd-write
-rwxr-sr-x  1 root        shadow      58K 2010-01-26 17:09 /usr/bin/chage
-rwsr-xr-x  1 root        root        41K 2010-01-26 17:09 /usr/bin/chfn
-rwsr-xr-x  1 root        root        37K 2010-01-26 17:09 /usr/bin/chsh
-rwxr-sr-x  1 root        crontab     37K 2010-06-25 22:13 /usr/bin/crontab
-rwxr-sr-x  1 root        mail        15K 2010-05-18 15:03 /usr/bin/dotlockfile
-rwxr-sr-x  1 root        shadow      23K 2010-01-26 17:09 /usr/bin/expiry
-rwsr-xr-x  1 root        root        63K 2010-01-26 17:09 /usr/bin/gpasswd
-rwsr-xr-x  1 root        lpadmin     14K 2010-06-29 18:16 /usr/bin/lppasswd
-rwxr-sr-x  3 root        mail        15K 2010-06-22 18:27 /usr/bin/mail-lock
-rwxr-sr-x  3 root        mail        15K 2010-06-22 18:27 /usr/bin/mail-touchlock
-rwxr-sr-x  3 root        mail        15K 2010-06-22 18:27 /usr/bin/mail-unlock
-rwxr-sr-x  1 root        mlocate     35K 2010-03-24 12:35 /usr/bin/mlocate
-rwxr-sr-x  1 root        mail        11K 2010-02-11 02:47 /usr/bin/mlock
-rwsr-xr-x  1 root        root        61K 2010-03-07 03:56 /usr/bin/mtr
-rwsr-xr-x  1 root        root        32K 2010-01-26 17:09 /usr/bin/newgrp
-rwsr-xr-x  1 root        root        42K 2010-01-26 17:09 /usr/bin/passwd
-rwsr-xr-x  1 root        root        19K 2010-04-09 14:47 /usr/bin/pkexec
-rwxr-sr-x  1 root        utmp       368K 2010-06-18 21:13 /usr/bin/screen
-rwxr-sr-x  1 root        ssh        107K 2010-05-27 10:00 /usr/bin/ssh-agent
-rwsr-xr-x  2 root        root       145K 2010-07-06 22:22 /usr/bin/sudo
-rwsr-xr-x  2 root        root       145K 2010-07-06 22:22 /usr/bin/sudoedit
-rwsr-xr-x  1 root        root        19K 2010-06-19 19:47 /usr/bin/traceroute6.iputils
-rwxr-sr-x  1 root        tty         15K 2010-03-22 17:57 /usr/bin/wall
-rwsr-sr-x  1 root        root        11K 2010-04-09 02:07 /usr/bin/X
-rwxr-sr-x  1 root        utmp       413K 2010-06-11 03:46 /usr/bin/xterm
-r-xr-sr-x  1 root        games      159K 2010-07-06 05:58 /usr/games/gnomine
-r-xr-sr-x  1 root        games      125K 2010-07-06 05:58 /usr/games/mahjongg
-r-xr-sr-x  1 root        games      141K 2010-07-06 05:58 /usr/games/quadrapassel
-rwsr-xr-x  1 root        root        11K 2009-11-10 08:07 /usr/lib/eject/dmcrypt-get-device
-rwxr-sr-x  1 root        mail        15K 2010-06-28 17:24 /usr/lib/evolution/camel-lock-helper-1.2
-rwsr-xr-x  1 root        root        11K 2009-11-21 09:45 /usr/lib/kde4/libexec/fileshareset
-rwxr-sr-x  1 root        nogroup     56K 2010-06-28 11:09 /usr/lib/kde4/libexec/kdesud
-rwxr-sr-x  1 root        utmp        15K 2010-05-27 10:17 /usr/lib/libvte9/gnome-pty-helper
-rwsr-xr-x  1 root        root       208K 2010-05-27 10:00 /usr/lib/openssh/ssh-keysign
-rwsr-xr-x  1 root        root        15K 2010-04-09 14:47 /usr/lib/policykit-1/polkit-agent-helper-1
-rwsr-xr-x  1 root        root        11K 2010-06-28 00:45 /usr/lib/pt_chown
drwxrwsr-x  4 root        staff      4.0K 2010-07-06 22:26 /usr/local/lib/python2.6
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:11 /usr/local/lib/python2.6/dist-packages
drwxrwsr-x  2 root        staff      4.0K 2010-07-06 22:26 /usr/local/lib/python2.6/site-packages
drwxrwsr-x  2 root        staff      4.0K 2010-07-01 10:54 /usr/local/lib/site_ruby/1.8/x86_64-linux
drwxrwsr-x  2 root        staff      4.0K 2010-07-05 15:50 /usr/local/share/asterisk/sounds
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:15 /usr/local/share/ca-certificates
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 18:02 /usr/local/share/fonts
drwxrwsr-x  2 root        staff      4.0K 2010-07-05 15:10 /usr/local/share/ppd
drwxrwsr-x  7 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/declaration
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/dtd
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/entities
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/misc
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/sgml/stylesheet
drwxrwsr-x  2 root        staff      4.0K 2010-06-26 16:03 /usr/local/share/texmf
drwxrwsr-x  6 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/declaration
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/entities
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/misc
drwxrwsr-x  2 root        staff      4.0K 2010-05-04 17:52 /usr/local/share/xml/schema
drwxrwsr-x  2 root        staff      4.0K 2010-05-28 14:27 /usr/local/share/zsh/site-functions
-rwsr-xr-x  1 root        root        32K 2010-05-12 23:10 /usr/sbin/hddtemp
-rwsr-xr--  1 root        dip        315K 2010-03-07 05:37 /usr/sbin/pppd
-rwsr-sr-x  1 libuuid     libuuid     19K 2010-03-22 17:57 /usr/sbin/uuidd
-rws--x--x  1 root        root        31K 2008-06-19 13:28 /usr/sbin/vlock-main
drwxrwsr-t  2 root        lpadmin    4.0K 2010-04-09 17:03 /usr/share/ppd/custom
drwxrwsr-x 25 root        src        4.0K 2010-07-08 15:25 /usr/src
drwxrwsr-t  2 root        admin      4.0K 2010-05-04 20:02 /var/cache/jockey
drwxr-sr-x 39 man         root       4.0K 2010-07-08 15:25 /var/cache/man
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ca
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/ca/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-25 14:32 /var/cache/man/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat2
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat3
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat4
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat6
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/cat7
drwxr-sr-x  2 man         root       4.0K 2010-06-25 11:38 /var/cache/man/cat8
drwxr-sr-x  6 man         root       4.0K 2010-07-08 15:25 /var/cache/man/cs
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/cs/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/da
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/da/cat1
drwxr-sr-x  7 man         root       4.0K 2010-07-08 15:25 /var/cache/man/de
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat3
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/de/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/de.UTF-8
drwxr-sr-x  2 man         root       4.0K 2010-06-29 14:00 /var/cache/man/de.UTF-8/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/es
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/es/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/es/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/es/cat8
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fi
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fi/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fi/cat8
drwxr-sr-x  7 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fr
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat3
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr/cat8
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fr.ISO8859-1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.ISO8859-1/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.ISO8859-1/cat8
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/fr.UTF-8
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.UTF-8/cat7
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/fr.UTF-8/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/gl
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/gl/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/hr
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/hr/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/hu
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/hu/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/hu/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/hu/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/id
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/id/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/id/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/id/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/it
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/it/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/it/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/it/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ja
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/ja/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/ja/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/ja/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ko
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ko/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ko/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ko/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/nl
drwxr-sr-x  2 man         root       4.0K 2010-05-04 20:00 /var/cache/man/nl/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/pl
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pl/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pl/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pl/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/pt
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/pt_BR
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pt_BR/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pt_BR/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:34 /var/cache/man/pt_BR/cat8
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/pt/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ru
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ru/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ru/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/ru/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/sv
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/sv/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/sv/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/sv/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/tr
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/tr/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/tr/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/tr/cat8
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/ug
drwxr-sr-x  2 man         root       4.0K 2010-06-17 23:39 /var/cache/man/ug/cat1
drwxr-sr-x  4 man         root       4.0K 2010-07-08 15:25 /var/cache/man/vi
drwxr-sr-x  2 man         root       4.0K 2010-06-29 11:32 /var/cache/man/vi/cat1
drwxr-sr-x  2 man         root       4.0K 2010-06-29 11:32 /var/cache/man/vi/cat7
drwxr-sr-x  3 man         root       4.0K 2010-07-08 15:25 /var/cache/man/zh
drwxr-sr-x  2 man         root       4.0K 2010-06-26 16:21 /var/cache/man/zh/cat1
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/zh_CN
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_CN/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_CN/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_CN/cat8
drwxr-sr-x  5 man         root       4.0K 2010-07-08 15:25 /var/cache/man/zh_TW
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_TW/cat1
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_TW/cat5
drwxr-sr-x  2 man         root       4.0K 2010-05-04 18:33 /var/cache/man/zh_TW/cat8
drwxrwsr-x  2 libuuid     libuuid    4.0K 2010-05-04 17:11 /var/lib/libuuid
drwxrwsr-x  2 root        staff      4.0K 2010-04-23 10:23 /var/local
drwxr-s---  2 Debian-exim adm        4.0K 2010-06-26 13:34 /var/log/exim4
drwxr-s---  2 mysql       adm        4.0K 2010-07-06 04:47 /var/log/mysql
drwxrwsr-x  2 root        mail       4.0K 2010-05-04 17:04 /var/mail

```

LOL

This would be realty helpfull, but by the way I can't print right know, but what command get that the setuid and setgid change to the ones you especify? chown do it, if not can you tell me.

---

### Post by braiamp on 2010-07-11
Maybe I will ran the command I post the results. Give me about 15 min if you are online to get it.

---

### Post by braiamp on 2010-07-11
By the way, I'm posting from my system, using the root user, and don't tell me that is a bad idea, I know!! Following the path I get that my [wireless work again]("http://ubuntuforums.org/showthread.php?t=1526536"), my f[ilesystems show up the Places menu]("http://ubuntuforums.org/showthread.php?p=9575522#post9575522"), with some investigation, and run a simple command:popcorn:: dpkg-reconfigure. So the main problem.

I use the recovery mode to get root session, because my users doesn't have su access, I start x server using startx, and looking how I mount my NTFS filesystem, I hit with the answer.

I start firefox as fast that I could and search for the command you run because I made a typo on the paper that won't get it work, and for least the output:```


root@braiam-desktop:~# find / -perm +6000 -exec ls -aldh '{}' + 2> /dev/null 
drwxr-sr-x  2 root                bind                4.0K 2010-07-01 22:13 /etc/bind
drwxr-s---  2 root                root                4.0K 2010-06-25 04:09 /etc/chatscripts
drwxr-s---  2 root                root                4.0K 2010-04-29 08:26 /etc/ppp/peers
drwxrwsr-x  2 root                debian-transmission 4.0K 2010-07-10 16:24 /etc/transmission-daemon
-rwsr-xr--  1 root                messagebus           42K 2010-03-30 11:07 /lib/dbus-1.0/dbus-daemon-launch-helper
drwxrwsr-x  3 root                root                4.0K 2010-06-15 16:30 /srv/cvs
drwxrwsr-x  3 root                root                4.0K 2010-06-15 16:30 /srv/cvs/CVSROOT
drwxrwsr-x  2 root                root                4.0K 2010-06-15 16:30 /srv/cvs/CVSROOT/Emptydir
drwxrwsr-x  4 root                root                4.0K 2010-04-29 08:18 /usr/local/lib/python2.6
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:18 /usr/local/lib/python2.6/dist-packages
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:18 /usr/local/lib/python2.6/site-packages
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:18 /usr/local/share/ca-certificates
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:21 /usr/local/share/fonts
drwxrwsr-x  2 root                root                4.0K 2010-06-25 12:39 /usr/local/share/ppd
drwxrwsr-x  7 root                root                4.0K 2010-04-29 08:19 /usr/local/share/sgml
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/sgml/declaration
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/sgml/dtd
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/sgml/entities
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/sgml/misc
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/sgml/stylesheet
drwxrwsr-x  6 root                root                4.0K 2010-04-29 08:19 /usr/local/share/xml
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/xml/declaration
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/xml/entities
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/xml/misc
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:19 /usr/local/share/xml/schema
drwxrwsr-t  2 root                lpadmin             4.0K 2010-04-09 11:10 /usr/share/ppd/custom
drwxrwsr-x 10 root                root                4.0K 2010-07-01 10:50 /usr/src
drwxr-sr-x  4 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack
d-----S---  8 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/manpages
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/packages
d-----S---  3 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/patches
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/patches/old
d-----S---  4 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts
d-----S---  5 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airgraph-ng
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airgraph-ng/lib
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airgraph-ng/man
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airgraph-ng/test
d-----S---  4 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript
d-----S---  3 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/doc
d-----S---  3 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/doc/html
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/doc/html/images
d-----S---  6 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/src
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/src/airosperl
d-----S---  3 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/src/i10n
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/src/i10n/po
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/src/patches
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/scripts/airoscript/src/themes
d-----S---  4 root                root                4.0K 2010-06-24 15:54 /usr/src/aircrack/aircrack-ng-1.0-rc3/src
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/src/include
d-----S---  3 root                root                4.0K 2010-06-24 15:54 /usr/src/aircrack/aircrack-ng-1.0-rc3/src/osdep
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/src/osdep/tap-win32
d-----S---  2 root                root                4.0K 2010-06-23 17:11 /usr/src/aircrack/aircrack-ng-1.0-rc3/test
drwx--S---  8 root                root                4.0K 2010-06-25 04:57 /usr/src/aircrack/aircrack-ng-1.1
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/manpages
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/packages
drwx--S---  3 root                root                4.0K 2010-06-25 15:56 /usr/src/aircrack/aircrack-ng-1.1/patches
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/patches/old
drwx--S---  4 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts
drwx--S---  6 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airdrop-ng
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airdrop-ng/docs
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airdrop-ng/lib
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airdrop-ng/logs
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airdrop-ng/support
drwx--S---  5 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airgraph-ng
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airgraph-ng/lib
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airgraph-ng/man
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/scripts/airgraph-ng/test
drwx--S---  4 root                root                4.0K 2010-06-25 04:19 /usr/src/aircrack/aircrack-ng-1.1/src
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/src/include
drwx--S---  4 root                root                4.0K 2010-06-23 17:02 /usr/src/aircrack/aircrack-ng-1.1/src/osdep
drwx--S---  2 root                root                4.0K 2010-06-23 17:02 /usr/src/aircrack/aircrack-ng-1.1/src/osdep/radiotap
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/src/osdep/tap-win32
drwx--S---  2 root                root                4.0K 2010-06-23 17:01 /usr/src/aircrack/aircrack-ng-1.1/test
drwxr-sr-x 16 root                root                 12K 2010-06-25 12:18 /usr/src/kismet
drwxrwsr-t  2 root                root                4.0K 2010-05-03 12:32 /var/cache/jockey
drwxr-sr-x 36 man                 root                4.0K 2010-07-11 07:21 /var/cache/man
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/ca
drwxr-sr-x  2 man                 root                4.0K 2010-07-04 08:17 /var/cache/man/ca/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-07-04 08:17 /var/cache/man/ca/cat3
drwxr-sr-x  2 man                 root                4.0K 2010-07-04 08:17 /var/cache/man/ca/cat7
drwxr-sr-x  2 man                 root                4.0K 2010-07-01 09:37 /var/cache/man/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cat2
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cat3
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cat4
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cat6
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cat7
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cat8
drwxr-sr-x  6 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/cs
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cs/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cs/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cs/cat7
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/cs/cat8
drwxr-sr-x  7 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/de
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/de/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/de/cat3
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/de/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/de/cat7
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/de/cat8
drwxr-sr-x  3 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/de.UTF-8
drwxr-sr-x  2 man                 root                4.0K 2010-05-03 13:15 /var/cache/man/de.UTF-8/cat1
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/es
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/es/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/es/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/es/cat8
drwxr-sr-x  4 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/fi
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fi/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fi/cat8
drwxr-sr-x  7 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/fr
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr/cat3
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr/cat7
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr/cat8
drwxr-sr-x  4 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/fr.ISO8859-1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr.ISO8859-1/cat7
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr.ISO8859-1/cat8
drwxr-sr-x  4 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/fr.UTF-8
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr.UTF-8/cat7
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/fr.UTF-8/cat8
drwxr-sr-x  3 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/gl
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/gl/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/hu
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/hu/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/hu/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/hu/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/id
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/id/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/id/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/id/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/it
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/it/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/it/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/it/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/ja
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ja/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ja/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ja/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/ko
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ko/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ko/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ko/cat8
drwxr-sr-x  4 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/local
drwxr-sr-x  2 man                 root                4.0K 2010-07-04 07:35 /var/cache/man/local/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-06-25 04:10 /var/cache/man/local/cat5
drwxr-sr-x  3 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/nl
drwxr-sr-x  2 man                 root                4.0K 2010-06-15 16:29 /var/cache/man/nl/cat1
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/pl
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/pl/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/pl/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/pl/cat8
drwxr-sr-x  4 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/pt
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/pt_BR
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/pt_BR/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/pt_BR/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/pt_BR/cat8
drwxr-sr-x  2 man                 root                4.0K 2010-07-01 14:37 /var/cache/man/pt/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-07-01 14:37 /var/cache/man/pt/cat7
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/ru
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ru/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ru/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/ru/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/sv
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/sv/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/sv/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/sv/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/tr
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/tr/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/tr/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/tr/cat8
drwxr-sr-x  4 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/vi
drwxr-sr-x  2 man                 root                4.0K 2010-07-01 14:37 /var/cache/man/vi/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-07-01 14:37 /var/cache/man/vi/cat7
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/zh_CN
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/zh_CN/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/zh_CN/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/zh_CN/cat8
drwxr-sr-x  5 man                 root                4.0K 2010-07-11 07:21 /var/cache/man/zh_TW
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/zh_TW/cat1
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/zh_TW/cat5
drwxr-sr-x  2 man                 root                4.0K 2010-04-29 08:26 /var/cache/man/zh_TW/cat8
drwxrwsr-x  2 root                root                4.0K 2010-04-29 08:18 /var/lib/libuuid
drwsrwxr-x  2 debian-transmission debian-transmission 4.0K 2010-06-18 05:21 /var/lib/transmission-daemon/downloads
drwsr-x---  5 debian-transmission debian-transmission 4.0K 2010-07-06 03:51 /var/lib/transmission-daemon/info
drwxrwsr-x  2 root                root                4.0K 2010-04-23 06:11 /var/local
drwxrwsr-x  2 root                root                4.0K 2010-07-06 23:49 /var/mail
drwx--s---  2 root                root                4.0K 2010-07-06 22:25 /var/spool/postfix/public
root@braiam-desktop:~# 
```

As i see, it seems parted equals as yours but with su* shadow* and this stuff doesn't seems right. Again, if someone else know how revert all this, please leave me know:D.

---

### Post by braiamp on 2010-07-13
Well, I've reconfigure and reinstalled sudo and gksu but the inssue still here. Should I purge sudo and gksu and try to get it aging? If not, what are the packages that maybe are getting the inssue, or maybe purge and reinstall my whole system as apt-build does?

I should add the shadow file. Please, if somebody know about a list of all installed packages that needs special fileaccess permissions, no doubted post it.

---

### Post by braiamp on 2010-07-13
I kocked out myself. Some googling of "set setuid root" give me the pages [How to ser SUID under Linux?]("http://www.networkdictionary.com/software/Linux329.php") and using your output as reference I'll have all runing as desired. Thanks a lot for all the help that you ofered to a hard breaking head linux user. I someday write on the Hints forums all m experiences about all the problems that I have and the way that I resolve the inssue.

---

### Post by bodhi.zazen on 2010-07-13
> **braiamp said:**
> I kocked out myself. Some googling of "set setuid root" give me the pages [How to ser SUID under Linux?]("http://www.networkdictionary.com/software/Linux329.php") and using your output as reference I'll have all runing as desired. Thanks a lot for all the help that you ofered to a hard breaking head linux user. I someday write on the Hints forums all m experiences about all the problems that I have and the way that I resolve the inssue.

Glad you learned something, that is probably the most important point. As a side note, it took you 6 days when backing up your data and re-installing would have been much faster >:)

My general rule is , if it takes longer to fix then reinstall, I usually give myself a day or two and if at that point I am not making progress, reinstall. 

If I really like, I will make an image of the broken system and toy with it in Virtualbox/KVM.

---

