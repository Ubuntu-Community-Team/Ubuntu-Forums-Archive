---
title: "sudo chkrootkit - results!"
date: 2010-09-13
forum: Security
---

### Post by Rytron on 2010-09-13
Hi.
I ran this command today

```
sudo chkrootkit
```

Some of the output is below. Does it all look okay? Is my PC safe and clean?


```
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/firefox-3.6.9/.autoreg /usr/lib/xulrunner-1.9.2.9/.autoreg /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path
```

```
Searching for anomalies in shell history files...           Warning: `//home/rytron/.civserver_history' file size is zero
```

Update! I also ran this command below:

```
sudo rkhunter --check --pkgmgr dpkg
```

and this is a part where there were warnings in /var/log/rkhunter.log
```

[18:21:35]   Checking /dev for suspicious file types         [ Warning ]
[18:21:35] Warning: Suspicious file types found in /dev:
[18:21:35]          /dev/shm/pulse-shm-4079446115: data
[18:21:35]          /dev/shm/pulse-shm-2820422919: AmigaOS bitmap font
[18:21:35]          /dev/shm/pulse-shm-1706228885: data
[18:21:35]   Checking for hidden files and directories       [ Warning ]
[18:21:35] Warning: Hidden directory found: /etc/.java
[18:21:35] Warning: Hidden directory found: /dev/.udev
[18:21:35] Warning: Hidden directory found: /dev/.initramfs
```

---

### Post by Rubi1200 on 2010-09-13
Hi,
no disrespect intended, but did you Google for these things before posting?

Next question, again I mean no disrespect, but as an experienced Linux user don't you think you would know what is on your system and whether or not it is "safe and clean"?

Tools like chkrootkit are really quite useless unless run on a clean system and/or you are prepared to do the legwork to investigate results.

And, from my limited experience, I can say the results look quite okay; I do not think you have anything to worry about.

Also take a look here:
[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)

> As with all these tools false positives are common, use Google to search for suspicious results.

[COLOR=navy]**Etiquette: If you are going to run these tools,  please read the documentation  (FAQ / README ) and perform a google  search on the results of alerts or warnings before posting on the  forums.**[/COLOR]

---

