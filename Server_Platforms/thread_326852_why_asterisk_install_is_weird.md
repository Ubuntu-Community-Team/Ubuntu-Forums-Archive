---
title: "why asterisk install is weird ?"
date: 2006-12-28
forum: Server Platforms
---

### Post by nephish on 2006-12-28
lo there all.

is anyone out there using ubuntu for astersik. I need to set up an IVR system for our company.
i have set up asterisk before on a debian computer, but when i did the apt-get install asterisk, things got weird. 
for example: there is no /usr/share/asterisk/agi-bin directory
neither is there a /var/spool/asterisk/outgoing directory.
do i need to create these by hand ?
did my install go bad ?
does ubuntu do asterisk differently from other distros? 

just need a little advice here.

thanks all

---

### Post by wasburn on 2006-12-28
agi-bin is in /var/lib/asterisk/agi-bin/

---

### Post by nephish on 2006-12-28
ok, so nothing is missing, just laid out a little differently.

cool enough

thanks

---

### Post by nephish on 2007-01-04
um.... it isn't there either

---

### Post by magicfab on 2007-01-29
You may want to contribute to this guide:
[https://wiki.ubuntu.com/AsteriskOnUbuntu](https://wiki.ubuntu.com/AsteriskOnUbuntu)

Be warned, however, that the FreePBX part has not been tested. The document is work in progress.

---

