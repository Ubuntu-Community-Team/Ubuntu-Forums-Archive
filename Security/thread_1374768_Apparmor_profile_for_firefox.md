---
title: "Apparmor profile for firefox"
date: 2010-01-07
forum: Security
---

### Post by dogdo on 2010-01-07
Hi

Ive disabled the apparmor profile for firefox 3.5.6. but i still have the default firefox profile as enforced. When i run sudo this is what i get: 

shinji@shinji-laptop:~$ sudo /etc/init.d/apparmor status
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
/usr/sbin/avahi-daemon (enforce)
/usr/lib/firefox-3.5.6/firefox.sh (complain)
/usr/lib/firefox-3.5.6/firefox.sh//null-27 (complain)
/usr/lib/dovecot/pop3-login (complain)
/usr/lib/dovecot/pop3 (complain)
/usr/lib/dovecot/managesieve-login (complain)
/usr/lib/dovecot/imap-login (complain)
/usr/lib/dovecot/imap (complain)
/usr/lib/dovecot/dovecot-auth (complain)
/usr/lib/dovecot/deliver (complain)
/usr/lib/firefox-3.5.*/firefox (enforce)
/usr/bin/evince-thumbnailer (enforce)
/usr/bin/evince-previewer (enforce)
/usr/bin/evince (enforce)
/sbin/syslogd (complain)
/sbin/syslog-ng (complain)
/sbin/klogd (complain)
/usr/lib/connman/scripts/dhclient-script (enforce)
/usr/lib/NetworkManager/nm-dhcp-client.action (enforce)
/sbin/dhclient3 (enforce)
/usr/share/gdm/guest-session/Xsession (enforce)
/bin/which (complain)
/bin/ping (complain)
shinji@shinji-laptop:~$ 

Does this mean that apparmor is still keeping firefox in check? bear in mind i have tried to train the firefox profile 3.5.6 but i found it really hard-firefox not loading up, multiples instances of firefox, firefox crashing and going grey-is it possible to be safe with the firefox profile set to default?

---

### Post by running_rabbit07 on 2010-01-07
[FONT=Times New Roman][FONT=Arial][SIZE=2]_"complain_ - In complain mode AA monitors applications and logs violations to your profile without restricting or confining the application. I think of this as "Testing" mode."[/SIZE][/FONT][FONT=Arial]

[/FONT]  [FONT=Arial][SIZE=2]As long as it is set to complain mode, you are not protected.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Why would you disable it? Was it giving you problems?[/SIZE][/FONT]
[/FONT]

---

### Post by dogdo on 2010-01-07
Yeh i tried to configure firefox profile 3.5.6 to my own needs but i always end up with a malfunctioning firefox :( I still have the general firefox profile set to enforce-wont this provide some protection? 

When i first ran apparmor i noticed that a lot of the default profiles were already set to enforced-does anyone know what specifically these default profiles do?

---

### Post by running_rabbit07 on 2010-01-07
> **dogdo said:**
> Yeh i tried to configure firefox profile 3.5.6 to my own needs but i always end up with a malfunctioning firefox :( I still have the general firefox profile set to enforce-wont this provide some protection? 

When i first ran apparmor i noticed that a lot of the default profiles were already set to enforced-does anyone know what specifically these default profiles do?

For the best explanation, check out Bodhi's AppArmor thread in the link in my signature. The factory profile covers quite a bit. It is the one I am using. The only ones I have imported so far are the ones that did not exist at all from the repositories or needed beefing up.

---

