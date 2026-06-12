---
title: "Hi everyone . Weird chromium processes (i don't even have installed it!)"
date: 2016-05-06
forum: Security
---

### Post by deepblue2 on 2016-05-06
Hello everyone. First of all, thank you for your time.
So.. i've just installed a fresh linux
and, with chromium not installed obv, instead iceweasel is by default.
Anyway while im setting up ufw firewall and apparmor
this is what the report shows
a chromium process running, even if chromium is not installed, i can't have install it like a mistake because i  have just started from 0 the entire OS
Sorry for bad english, and thanks for any help.

Apparmor rep

> 38 profiles are loaded.
3 profiles are in enforce mode.
[B]   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/chromium-browser/chromium-browser//sanitized_helper[/B]
35 profiles are in complain mode.
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
[B]   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//lsb_release
   /usr/lib/chromium-browser/chromium-browser//xdgsettings[/B]
   /usr/lib/dovecot/anvil
   /usr/lib/dovecot/auth
   /usr/lib/dovecot/config
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dict
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/dovecot-lda
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/lmtp
   /usr/lib/dovecot/log
   /usr/lib/dovecot/managesieve
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/lib/dovecot/ssl-params
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/smbldap-useradd
   /usr/sbin/smbldap-useradd///etc/init.d/nscd
   /usr/{sbin/traceroute,bin/traceroute.db}
   /{usr/,}bin/ping
2 processes have profiles defined.
0 processes are in enforce mode.
2 processes are in complain mode.
   /usr/sbin/avahi-daemon (722) 
   /usr/sbin/avahi-daemon (739) 
0 processes are unconfined but have a profile defined.

---

### Post by cariboo on 2016-05-07
Those profiles are installed, when you install apparmor profiles. Nothing weird about it

---

### Post by deepblue2 on 2016-05-07
@cariboo thank you very much

---

