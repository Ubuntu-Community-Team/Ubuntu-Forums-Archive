---
title: "Cannot enforce Firefox 4.0 Apparmor profile"
date: 2011-04-29
forum: Security
---

### Post by Foxter on 2011-04-29
Hello

Since Ubuntu 9.10 I used:

"sudo apt-get install apparmor-profiles

 sudo enforce firefox"

However in Lubuntu 11.04 the "sudo enforce firefox" command does no longer work. It looks like the enforce command is no longer recognised. Does anybody know why ?

Thank you and sorry for my bad english.

---

### Post by Soul-Sing on 2011-04-29
> **Foxter said:**
> Hello

Since Ubuntu 9.10 I used:

"sudo apt-get install apparmor-profiles

 sudo enforce firefox"

However in Lubuntu 11.04 the "sudo enforce firefox" command does no longer work. It looks like the enforce command is no longer recognised. Does anybody know why ?

Thank you and sorry for my bad english.

```
sudo aa-enforce firefox
```

---

### Post by uRock on 2011-04-29
Can you show us the output of sudo apparmor_status? It should look like the following.```
apparmor module is loaded.
42 profiles are loaded.
16 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
[COLOR="Red"]   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}//browser_openjdk[/COLOR]
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
26 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//null-28
   /usr/lib/chromium-browser/chromium-browser//null-29
   /usr/lib/chromium-browser/chromium-browser//null-2a
   /usr/lib/chromium-browser/chromium-browser//null-2b
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
12 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (1877) 
   /usr/sbin/cupsd (1312) 
8 processes are in complain mode.
   /usr/lib/chromium-browser/chromium-browser (2173) 
   /usr/lib/chromium-browser/chromium-browser (2019) 
   /usr/lib/chromium-browser/chromium-browser (2017) 
   /usr/lib/chromium-browser/chromium-browser (2089) 
   /usr/lib/chromium-browser/chromium-browser (2015) 
   /usr/sbin/avahi-daemon (1206) 
   /usr/sbin/avahi-daemon (1208) 
   /usr/sbin/nmbd (1955) 
2 processes are unconfined but have a profile defined.
   /usr/sbin/smbd (1298) 
   /usr/sbin/smbd (1162) 
```

---

### Post by Foxter on 2011-04-29
@**uRock**
Here is the output before following  **leoquant** advice:

apparmor module is loaded.
34 profiles are loaded.
12 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
22 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
3 processes have profiles defined.
3 processes are in enforce mode :
   /sbin/dhclient (861) 
   /usr/sbin/cupsd (811) 
   /usr/sbin/ntpd (1337) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.


After following  **leoquant** advice:

apparmor module is loaded.
37 profiles are loaded.
15 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}//browser_openjdk
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
22 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
4 processes have profiles defined.
4 processes are in enforce mode :
   /sbin/dhclient (861) 
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]} (1664) 
   /usr/sbin/cupsd (811) 
   /usr/sbin/ntpd (1337) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.





@**leoquant**
Thank you, that worked !

---

### Post by uRock on 2011-04-29
I don't see Firefox listed at all in your output.

---

### Post by Foxter on 2011-04-29
I edited my previous post with new output that came after the "sudo aa-enforce firefox" command.

---

### Post by uRock on 2011-04-29
Awesome!

---

