---
title: "rkhunter scan question"
date: 2008-04-26
forum: Security
---

### Post by Lantesh on 2008-04-26
I just ran a scan using rkhunter to look for root kits.  It didn't find any, but I did get two warnings.  Below is a small section from the log file.  Is this anything to be concerned about?  My OS is Linux Mint 4.0


[19:50:43]   Checking for running syslog daemon              [ Warning ]
[19:50:43] Warning: The syslog daemon is not running.
[19:50:43]   Checking for syslog configuration file          [ Found ]
[19:50:43] Info: Found syslog configuration file: /etc/syslog.conf
[19:50:43]   Checking if syslog remote logging is allowed    [ Not allowed ]
[19:50:43]
[19:50:43] Performing filesystem checks
[19:50:43] Info: Starting test name 'filesystem'
[19:50:43] Info: SCAN_MODE_DEV set to 'THOROUGH'
[19:50:57]   Checking /dev for suspicious file types         [ None found ]
[19:50:58]   Checking for hidden files and directories       [ Warning ]
[19:50:58] Warning: Hidden directory found: /etc/.java
[19:50:58] Warning: Hidden directory found: /dev/.static
[19:50:58] Warning: Hidden directory found: /dev/.udev
[19:50:58] Warning: Hidden directory found: /dev/.initramfs
[19:50:58] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)
[19:51:24]

---

### Post by Vinno on 2008-04-27
Nothing to worry about. Its just that its scanning for hidden files in /dev and some files with a dot before there name will be reported.

---

### Post by Lantesh on 2008-04-27
Thanks Vinno.  I appreciate the reply.  I wasn't too worried, but figured I'd ask.

---

