---
title: "Ubuntu 9.04: chkrootkit Suspicious File Help"
date: 2011-02-15
forum: Security
---

### Post by SexySara on 2011-02-15
I ran a search and these are the results... are they false positives? I think the sniffer may be from Wireshark. the Java and Firefox files seem to be false positives, but what about the xulrunner and the "z2" thing?

```
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.0.19/.autoreg 
/usr/lib/jvm/.java-6-sun.jinfo 
/usr/lib/jvm/.java-6-openjdk.jinfo 
/usr/lib/jvm/java-6-sun-1.6.0.22/.systemPrefs 
/usr/lib/firefox-3.6.11/.autoreg /lib/modules/2.6.28-19-generic/volatile/.mounted /lib/init/rw/.ramfs


Checking `sniffer'... wlan0: PF_PACKET(/sbin/wpa_supplicant, /sbin/dhclient3)
Checking `z2'... user soultravel369 deleted or never logged from lastlog!
```

---

### Post by sydbat on 2011-02-15
> **SexySara said:**
> I ran a search and these are the results... are they false positives? I think the sniffer may be from Wireshark. the Java and Firefox files seem to be false positives, but what about the xulrunner and the "z2" thing?

```
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.0.19/.autoreg 
/usr/lib/jvm/.java-6-sun.jinfo 
/usr/lib/jvm/.java-6-openjdk.jinfo 
/usr/lib/jvm/java-6-sun-1.6.0.22/.systemPrefs 
/usr/lib/firefox-3.6.11/.autoreg /lib/modules/2.6.28-19-generic/volatile/.mounted /lib/init/rw/.ramfs


Checking `sniffer'... wlan0: PF_PACKET(/sbin/wpa_supplicant, /sbin/dhclient3)
Checking `z2'... user soultravel369 deleted or never logged from lastlog!
```Both chkrootkit and rkhunter find a few "false positives". Most can be checked out via Google and are generally well known.

As for the "user soultravel369 deleted or never logged from lastlog!", I imagine that your username is soultravel369? If not, and not another user you have set up on your system, then I would be suspicious.

Otherwise, if you can account for the above items (like the Wireshark thingy), then don't worry too much.

---

### Post by Rubi1200 on 2011-02-15
[xulrunner]("http://en.wikipedia.org/wiki/XULRunner"): not something to be concerned about.

As sydbat pointed out, you need to check up on the user name.

Other than that, results seem normal.

These tools produce a lot of false positives and are, in some respects, quite useless.

Read the security sticky by bodhi.zazen for more about security on Ubuntu:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by SexySara on 2011-02-15
Thank you both for the help, everything makes sense now :)

---

### Post by Rubi1200 on 2011-02-15
You are more than welcome :-)

---

