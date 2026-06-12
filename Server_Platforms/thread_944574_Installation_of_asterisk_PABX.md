---
title: "Installation of asterisk PABX"
date: 2008-10-11
forum: Server Platforms
---

### Post by stevebeaumont on 2008-10-11
Hi,

I have a problem, I have successfully installed asterisk (PBX) using "sudo apt-get install asterisk". The configuration files for asterisk are contained in the directory "/etc/asterisk". This is OK and as expected, however, when I try changing directory to "/etc/asterisk" I get permission denied. using "sudo cd /etc/asterisk" I get "sudo: cd: command not found".

Any help would be appreciated

Best Regards
Steve B

---

### Post by gpredrag on 2008-10-11
use:
```
sudo -i
```
to run new shell as a root.

---

