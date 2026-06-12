---
title: "Firefox confined profile with AppArmor Ubuntu's default. What's your experience?"
date: 2016-02-14
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2016-02-14
I just enabled it. I won't say how. My VPN loads and works, I can log into the forums, access my encrypted web-mail service, broke precedence and opened a YouTube video of reviewing Ubuntu 15.04, so far everything is working.

What is your experience having with this? Anything you can't access with it?

```
apparmor module is loaded.
20 profiles are loaded.
20 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
4 processes have profiles defined.
4 processes are in enforce mode.
   /sbin/dhclient (954) 
   /usr/bin/freshclam (1337) 
   /usr/sbin/cups-browsed (1117) 
   /usr/sbin/cupsd (2226) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

---

### Post by lisati on 2016-02-14
Duplicate of [http://ubuntuforums.org/showthread.php?t=2313669](http://ubuntuforums.org/showthread.php?t=2313669) closed.

---

