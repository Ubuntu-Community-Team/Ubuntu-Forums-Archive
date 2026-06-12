---
title: "Apparmor profiles loaded,what about processes?"
date: 2013-12-02
forum: Security
---

### Post by cogset on 2013-12-02
I'm trying to use Apparmor while understanding what it is doing:the output of **sudo aa-status --verbose** looks like that
```
sudo aa-status --verbose
apparmor module is loaded.
30 profiles are loaded.
12 profiles are in enforce mode.
   /bin/ping
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/avahi-daemon
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
18 profiles are in complain mode.
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
0 processes have profiles defined.
0 processes are in enforce mode :
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```
So,what does that mean? Is Apparmor working as it should?
What does actually mean that 30 profiles are loaded but currently no process has a profile defined?
Do I need to install/generate more profiles ?
Why is the  apparmor directory in /var/log empty,i.e. no apparmor logs at all exist on my system?

---

### Post by bashiergui on 2013-12-02
Have you started any of the programs? This will get you started [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
There's also this [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by cogset on 2013-12-03
Good point,actually the installed profiles are for programs that I almost never use:if I start a program for which *there is* a profile,it says that the program is in enforce mode-so it works.
But I clearly need more profiles for other applications,and I still can't figure out why there are no logs whatsoever,as the /var/log/apparmor directory is empty:do I need to activate the logging for apparmor in some configuration file?

---

### Post by cogset on 2014-01-27
Talking about enabling more profiles,I've discovered that the apparmor profile for Firefox is placed in /etc/apparmor.d but disabled by default,to avoid possible malfunctioning of the browser:I wonder what may be other people's experience with this,i.e. if for someone enabling the profile has resulted in some trouble.

And,come to that,is there a source for updated Firefox-specific apparmor profiles?

---

