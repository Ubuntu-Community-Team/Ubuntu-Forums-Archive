---
title: "Tor Browser Bundle Whonix AppArmor Profile"
date: 2015-01-18
forum: Security
---

### Post by HardTrickySecurity on 2015-01-18
Hi everyone, english is not my native language.


I found an apparmor profile for Tor Browser Bundle. Its a debian file, in the description sais:


AppArmor profile for The Tor Browser Bundle (TBB)
An AppArmor profile to confine The Tor Browser Bundle (TBB). This profile is developed by the Whonix team. TBB is developed by The Tor Project.
This package is produced independently of, and carries no guarantee from, The Tor Project


I found it here:


[http://download2.polytechnic.edu.na/pub4/sourceforge/w/wh/whonixdevelopermetafiles/internal/pool/main/a/apparmor-profile-torbrowser/](http://download2.polytechnic.edu.na/pub4/sourceforge/w/wh/whonixdevelopermetafiles/internal/pool/main/a/apparmor-profile-torbrowser/)


I just install it in Lubuntu 14.04. But I was wondering:


Where do I have to put my Tor Browser Bundle file?
In wich location, in what folder?
How do I know if is working properly?
From what location I have to start Tor Browser Bundle?


If I do sudo aa-status it show me that the profile is in enforce mode


16 profiles are in enforce mode.
   /home/*/tor-browser_*/Browser/firefox   <---- Is this one, I dont know what the asterisk means
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode.
   /usr/sbin/cupsd (767) 
   /usr/sbin/ntpd (1317) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.










Thanks

---

