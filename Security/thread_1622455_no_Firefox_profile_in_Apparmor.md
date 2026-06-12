---
title: "no Firefox profile in Apparmor ?"
date: 2010-11-15
forum: Security
---

### Post by bachor on 2010-11-15
I'm trying to understand the Apparmor and would like to get FF profile from Bodhi.zazen [thank you],but I'm kinda new to Linux.

Did lots of reading but missing one thing:

1.where is FF profile?  I can't see any  usr.lib.firefox-3.6.12

2. how do I do copy FF profile from Bodhi.zazen?

pawel@pawel-Inspiron-6000:/etc/apparmor.d$ sudo /etc/init.d/apparmor status
/usr/sbin/traceroute (complain)
/usr/sbin/tcpdump (enforce)
/usr/sbin/smbd (complain)
/usr/sbin/nscd (complain)
/usr/sbin/nmbd (complain)
/usr/sbin/mdnsd (complain)
/usr/sbin/identd (complain)
/usr/sbin/dovecot (complain)
/usr/sbin/dnsmasq (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/avahi-daemon (complain)
/usr/lib/dovecot/pop3-login (complain)
/usr/lib/dovecot/pop3 (complain)
/usr/lib/dovecot/managesieve-login (complain)
/usr/lib/dovecot/imap-login (complain)
/usr/lib/dovecot/imap (complain)
/usr/lib/dovecot/dovecot-auth (complain)
/usr/lib/dovecot/deliver (complain)
[COLOR="Red"]/usr/lib/firefox-3.6.12/firefox-*bin (enforce)
/usr/lib/firefox-3.6.12/firefox-*bin//browser_openjdk (enforce)
/usr/lib/firefox-3.6.12/firefox-*bin//browser_java (enforce)[/COLOR]
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/chromium-browser/chromium-browser (complain)
/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox (complain)
/usr/lib/chromium-browser/chromium-browser//browser_openjdk (enforce)
/usr/lib/chromium-browser/chromium-browser//browser_java (enforce)
/sbin/syslogd (complain)
/sbin/syslog-ng (complain)
/sbin/klogd (complain)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
/bin/ping (complain)
pawel@pawel-Inspiron-6000:/etc/apparmor.d$



pawel@pawel-Inspiron-6000:/etc/apparmor.d$ ls -l 
total 148
drwxr-xr-x 3 root root 4096 2010-10-07 09:12 abstractions
drwxr-xr-x 2 root root 4096 2010-11-12 08:33 apache2.d
-rw-r--r-- 1 root root  788 2010-09-27 08:30 bin.ping
drwxr-xr-x 2 root root 4096 2010-11-14 17:29 cache
drwxr-xr-x 2 root root 4096 2010-11-14 14:08 disable
drwxr-xr-x 2 root root 4096 2010-08-06 19:48 force-complain
-rw-r--r-- 1 root root  986 2010-09-13 01:07 gdm-guest-session
drwxr-xr-x 2 root root 4096 2010-11-12 08:33 local
drwxr-xr-x 2 root root 4096 2010-11-12 08:33 program-chunks
-rw-r--r-- 1 root root 2052 2010-08-06 19:47 sbin.dhclient3
-rw-r--r-- 1 root root  890 2010-09-27 08:30 sbin.klogd
-rw-r--r-- 1 root root 1190 2010-09-27 08:30 sbin.syslogd
-rw-r--r-- 1 root root 1290 2010-09-27 08:30 sbin.syslog-ng
drwxr-xr-x 3 root root 4096 2010-10-07 09:11 tunables
-rw-r--r-- 1 root root 4511 2010-09-27 08:30 usr.bin.chromium-browser
-rw-r--r-- 1 root root 2052 2010-09-27 15:58 usr.bin.evince
-rw-r--r-- 1 root root 3412 2010-11-14 14:08 usr.bin.firefox
-rw-r--r-- 1 root root  585 2010-09-27 08:30 usr.lib.dovecot.deliver
-rw-r--r-- 1 root root  642 2010-09-27 08:30 usr.lib.dovecot.dovecot-auth
-rw-r--r-- 1 root root  520 2010-09-27 08:30 usr.lib.dovecot.imap
-rw-r--r-- 1 root root  524 2010-09-27 08:30 usr.lib.dovecot.imap-login
-rw-r--r-- 1 root root  562 2010-09-27 08:30 usr.lib.dovecot.managesieve-login
-rw-r--r-- 1 root root  500 2010-09-27 08:30 usr.lib.dovecot.pop3
-rw-r--r-- 1 root root  538 2010-09-27 08:30 usr.lib.dovecot.pop3-login
-rw-r--r-- 1 root root  786 2010-09-27 08:30 usr.sbin.avahi-daemon
-rw-r--r-- 1 root root 4158 2010-10-01 02:45 usr.sbin.cupsd
-rw-r--r-- 1 root root  629 2010-09-27 08:30 usr.sbin.dnsmasq
-rw-r--r-- 1 root root 1006 2010-09-27 08:30 usr.sbin.dovecot
-rw-r--r-- 1 root root  943 2010-09-27 08:30 usr.sbin.identd
-rw-r--r-- 1 root root  932 2010-09-27 08:30 usr.sbin.mdnsd
-rw-r--r-- 1 root root  514 2010-09-27 08:30 usr.sbin.nmbd
-rw-r--r-- 1 root root 1320 2010-09-27 08:30 usr.sbin.nscd
-rw-r--r-- 1 root root 1029 2010-09-27 08:30 usr.sbin.smbd
-rw-r--r-- 1 root root 1172 2010-08-06 10:45 usr.sbin.tcpdump
-rw-r--r-- 1 root root  780 2010-09-27 08:30 usr.sbin.traceroute
pawel@pawel-Inspiron-6000:/etc/apparmor.d$


thank you

---

### Post by uRock on 2010-11-15
**sudo apt-get install apparmor-profiles** should give you the firefox profile.

---

### Post by uRock on 2010-11-15
> **bachor said:**
> I'm trying to understand the Apparmor and would like to get FF profile from Bodhi.zazen [thank you],but I'm kinda new to Linux.

Did lots of reading but missing one thing:

1.where is FF profile?  I can't see any  usr.lib.firefox-3.6.12

2. how do I do copy FF profile from Bodhi.zazen?

```
pawel@pawel-Inspiron-6000:/etc/apparmor.d$ sudo /etc/init.d/apparmor status
/usr/sbin/traceroute (complain)
/usr/sbin/tcpdump (enforce)
/usr/sbin/smbd (complain)
/usr/sbin/nscd (complain)
/usr/sbin/nmbd (complain)
/usr/sbin/mdnsd (complain)
/usr/sbin/identd (complain)
/usr/sbin/dovecot (complain)
/usr/sbin/dnsmasq (complain)
/usr/sbin/cupsd (enforce)
/usr/lib/cups/backend/cups-pdf (enforce)
/usr/sbin/avahi-daemon (complain)
/usr/lib/dovecot/pop3-login (complain)
/usr/lib/dovecot/pop3 (complain)
/usr/lib/dovecot/managesieve-login (complain)
/usr/lib/dovecot/imap-login (complain)
/usr/lib/dovecot/imap (complain)
/usr/lib/dovecot/dovecot-auth (complain)
/usr/lib/dovecot/deliver (complain)
[COLOR="Red"]/usr/lib/firefox-3.6.12/firefox-*bin (enforce)
/usr/lib/firefox-3.6.12/firefox-*bin//browser_openjdk (enforce)
/usr/lib/firefox-3.6.12/firefox-*bin//browser_java (enforce)[/COLOR]
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/usr/lib/chromium-browser/chromium-browser (complain)
/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox (complain)
/usr/lib/chromium-browser/chromium-browser//browser_openjdk (enforce)
/usr/lib/chromium-browser/chromium-browser//browser_java (enforce)
/sbin/syslogd (complain)
/sbin/syslog-ng (complain)
/sbin/klogd (complain)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
/bin/ping (complain)
pawel@pawel-Inspiron-6000:/etc/apparmor.d$



pawel@pawel-Inspiron-6000:/etc/apparmor.d$ ls -l 
total 148
drwxr-xr-x 3 root root 4096 2010-10-07 09:12 abstractions
drwxr-xr-x 2 root root 4096 2010-11-12 08:33 apache2.d
-rw-r--r-- 1 root root  788 2010-09-27 08:30 bin.ping
drwxr-xr-x 2 root root 4096 2010-11-14 17:29 cache
drwxr-xr-x 2 root root 4096 2010-11-14 14:08 disable
drwxr-xr-x 2 root root 4096 2010-08-06 19:48 force-complain
-rw-r--r-- 1 root root  986 2010-09-13 01:07 gdm-guest-session
drwxr-xr-x 2 root root 4096 2010-11-12 08:33 local
drwxr-xr-x 2 root root 4096 2010-11-12 08:33 program-chunks
-rw-r--r-- 1 root root 2052 2010-08-06 19:47 sbin.dhclient3
-rw-r--r-- 1 root root  890 2010-09-27 08:30 sbin.klogd
-rw-r--r-- 1 root root 1190 2010-09-27 08:30 sbin.syslogd
-rw-r--r-- 1 root root 1290 2010-09-27 08:30 sbin.syslog-ng
drwxr-xr-x 3 root root 4096 2010-10-07 09:11 tunables
-rw-r--r-- 1 root root 4511 2010-09-27 08:30 usr.bin.chromium-browser
-rw-r--r-- 1 root root 2052 2010-09-27 15:58 usr.bin.evince
-rw-r--r-- 1 root root 3412 2010-11-14 14:08 usr.bin.firefox
-rw-r--r-- 1 root root  585 2010-09-27 08:30 usr.lib.dovecot.deliver
-rw-r--r-- 1 root root  642 2010-09-27 08:30 usr.lib.dovecot.dovecot-auth
-rw-r--r-- 1 root root  520 2010-09-27 08:30 usr.lib.dovecot.imap
-rw-r--r-- 1 root root  524 2010-09-27 08:30 usr.lib.dovecot.imap-login
-rw-r--r-- 1 root root  562 2010-09-27 08:30 usr.lib.dovecot.managesieve-login
-rw-r--r-- 1 root root  500 2010-09-27 08:30 usr.lib.dovecot.pop3
-rw-r--r-- 1 root root  538 2010-09-27 08:30 usr.lib.dovecot.pop3-login
-rw-r--r-- 1 root root  786 2010-09-27 08:30 usr.sbin.avahi-daemon
-rw-r--r-- 1 root root 4158 2010-10-01 02:45 usr.sbin.cupsd
-rw-r--r-- 1 root root  629 2010-09-27 08:30 usr.sbin.dnsmasq
-rw-r--r-- 1 root root 1006 2010-09-27 08:30 usr.sbin.dovecot
-rw-r--r-- 1 root root  943 2010-09-27 08:30 usr.sbin.identd
-rw-r--r-- 1 root root  932 2010-09-27 08:30 usr.sbin.mdnsd
-rw-r--r-- 1 root root  514 2010-09-27 08:30 usr.sbin.nmbd
-rw-r--r-- 1 root root 1320 2010-09-27 08:30 usr.sbin.nscd
-rw-r--r-- 1 root root 1029 2010-09-27 08:30 usr.sbin.smbd
-rw-r--r-- 1 root root 1172 2010-08-06 10:45 usr.sbin.tcpdump
-rw-r--r-- 1 root root  780 2010-09-27 08:30 usr.sbin.traceroute
pawel@pawel-Inspiron-6000:/etc/apparmor.d$
```


thank you

They are listed in your post. I changed the color of them to red for you.

---

### Post by bachor on 2010-11-15
> **uRock said:**
> They are listed in your post. I changed the color of them to red for you.


thanks uRock,I seems  not to "get it" ](*,). 

So FF profile is there running as STATUS says,but where is the exact location of that profile to edit it? it is not in apparmor.d 

and how do I copy it,just past it with gedit?

sorry I'm kinda new here

thanx :D

---

### Post by cariboo on 2010-11-15
It would probably be easier on you if you open up the profile in a text editor. Press Alt-F2 and type:

```
gksu gedit /etc/apparmor.d/usr.bin.firefox
```

or on the command line:

```
sudo nano /etc/apparmor.d/usr.bin.firefox
```

---

### Post by bachor on 2010-11-15
> **cariboo907 said:**
> It would probably be easier on you if you open up the profile in a text editor. Press Alt-F2 and type:

```
gksu gedit /etc/apparmor.d/usr.bin.firefox
```or on the command line:

```
sudo nano /etc/apparmor.d/usr.bin.firefox
```


 thank you

---

