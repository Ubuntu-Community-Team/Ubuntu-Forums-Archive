---
title: "Found warnings in rkhunter.log (rootkit hunter)"
date: 2014-01-18
forum: Security
---

### Post by bc.haynes on 2014-01-18
There were warnings in my rootkit hunter log:
Excerpt:
[16:12:18] Info: Starting test name 'passwd_changes'
[COLOR=#ff0000][16:12:18]   Checking for passwd file changes                [ Warning ]
[16:12:19] Warning: User 'postfix' has been added to the passwd file.[/COLOR]
[16:12:19]
[16:12:19] Info: Starting test name 'group_changes'
[COLOR=#ff0000][16:12:19]   Checking for group file changes                 [ Warning ]
[16:12:19] Warning: Group 'postfix' has been added to the group file.
[16:12:19] Warning: Group 'postdrop' has been added to the group file[/COLOR].
[16:12:19]   Checking root account shell history files       [ None found ]
[16:12:19]
[16:12:19] Info: Starting test name 'system_configs'
[16:12:19] Performing system configuration file checks
[16:12:19]   Checking for SSH configuration file             [ Not found ]
[16:12:19]   Checking for running syslog daemon              [ Found ]
[16:12:19] Info: Found rsyslog configuration file: /etc/rsyslog.conf
[16:12:19]   Checking for syslog configuration file          [ Found ]
[16:12:19]   Checking if syslog remote logging is allowed    [ Not allowed ]
[16:12:19]
[16:12:19] Info: Starting test name 'filesystem'
[16:12:19] Performing filesystem checks
[16:12:19] Info: SCAN_MODE_DEV set to 'THOROUGH'
[16:12:19]   Checking /dev for suspicious file types         [ None found ]
[COLOR=#ff0000][16:12:19]   Checking for hidden files and directories       [ Warning ]
[16:12:19] Warning: Hidden directory found: /dev/.udev
[16:12:19] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'[/COLOR]
[16:12:25]

Do I need to worry/act?:confused:

I am very visually impaired.  Ben

---

### Post by Iowan on 2014-01-18
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. [COLOR="#FF0000"]Please use the default font color and properties[/COLOR] unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

---

### Post by cariboo on 2014-01-18
Those are normal warnings, that you get if you don't update the rkhunter database before running it. I'd suggest running: 

```
fkhunter --propupd
```

then run rkhunter again.

---

### Post by morty71 on 2014-01-19
Nothing to be worried about...

---

