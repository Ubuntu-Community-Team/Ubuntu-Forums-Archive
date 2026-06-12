---
title: "Apparmor default profiles"
date: 2011-03-19
forum: Security
---

### Post by needhelppeeps on 2011-03-19
I was tinkering with the apparmor default profiles and jacked up the firefox one a bit and wanted to go back to the defaults so I deleted it. I cannot get the thing to reload it. I've purged, removed, installed apparmor utils and profiles numerous times. What do I have to do, somehow it remembers I deleted the file apparently.

NOTE: I did find the original apparmor profile in the firefox deb file which is in var/apt/archives. Mine was gone so I just did an apt-get for firefox to bring it back down.

---

### Post by ptn107 on 2011-03-20
The apparmor profile '/etc/apparmor.d/usr.bin.firefox' does not come from any apparmor* packages.  It's included in the firefox package.  You can get the original profile from here for the moment:

[_/etc/apparmor.d/usr.bin.firefox_]("http://www.filedropper.com/usrbin")*

Click the link then 'Download this file'.  Just throw it in /etc/apparmor.d/ and restart apparmor:
```
sudo service apparmor restart
```

Make sure apparmor, apparmor-utils, and firefox are already installed.

*There is no difference between the 32/64-bit profiles, fyi.

---

### Post by judderwocky on 2011-06-21
sorry to reply to this... but is there a current location for that file? I seem to have made the same mistake as the original poster but the link does not open for me. 

thanks

---

