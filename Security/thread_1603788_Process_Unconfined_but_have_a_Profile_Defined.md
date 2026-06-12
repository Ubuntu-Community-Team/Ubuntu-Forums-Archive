---
title: "Process Unconfined but have a Profile Defined"
date: 2010-10-23
forum: Security
---

### Post by donato roque on 2010-10-23
Hello.
I've tried reboot and the problem persist.  I know that it is known.  But has anyone come up with a solution.  

My Terminal:
donato@donato-desktop:~$ sudo apparmor_status
apparmor module is loaded.
40 profiles are loaded.
36 profiles are in enforce mode.
   /bin/ping
   /sbin/dhclient3
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3-login
   /usr/lib/firefox-3.6.10/firefox.sh//browser_java
   /usr/lib/firefox-3.6.10/firefox.sh//browser_openjdk
   /usr/lib/firefox-3.6.11/firefox.sh
   /usr/lib/firefox-3.6.11/firefox.sh//browser_java
   /usr/lib/firefox-3.6.11/firefox.sh//browser_openjdk
   /usr/sbin/avahi-daemon
   /usr/sbin/cupsd
   /usr/sbin/dnsmasq
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/tcpdump
   /usr/sbin/traceroute
   /usr/share/gdm/guest-session/Xsession
4 profiles are in complain mode.
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/pop3
   /usr/lib/firefox-3.6.10/firefox.sh
   /usr/sbin/dovecot
7 processes have profiles defined.
6 processes are in enforce mode :
   /sbin/dhclient3 (2449) 
   /usr/lib/firefox-3.6.11/firefox.sh (2591) 
   /usr/lib/firefox-3.6.11/firefox.sh (2595) 
   /usr/lib/firefox-3.6.11/firefox.sh (2587) 
   /usr/sbin/avahi-daemon (1112) 
   /usr/sbin/avahi-daemon (1105) 
0 processes are in complain mode.
1 processes are unconfined but have a profile defined.
   /usr/sbin/cupsd (1113) 
donato@donato-desktop:~$ 

Thanks.

---

### Post by donato roque on 2010-10-24
I did this to restart cups.
Code:
user@user-desktop:~$ sudo restart cups

to check if processes are now confined by defined profiles in apparmor:
Code:
user@user-desktop:~$ sudo apparmor_status

9 processes have profiles defined.
9 processes are in enforce mode :
   /sbin/dhclient3 (1244) 
   /usr/bin/evince (4284) 
   /usr/lib/firefox-3.6.11/firefox.sh (3562) 
   /usr/lib/firefox-3.6.11/firefox.sh (3502) 
   /usr/lib/firefox-3.6.11/firefox.sh (3506) 
   /usr/lib/firefox-3.6.11/firefox.sh (3510) 
   /usr/sbin/avahi-daemon (1111) 
   /usr/sbin/avahi-daemon (1115) 
   /usr/sbin/cupsd (4438) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

---

