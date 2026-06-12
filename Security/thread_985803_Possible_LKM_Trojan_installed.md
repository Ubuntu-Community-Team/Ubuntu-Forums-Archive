---
title: "Possible LKM Trojan installed?"
date: 2008-11-18
forum: Security
---

### Post by chunchengch on 2008-11-18
I run command 'sudo chkrootkit' and get thess informations

[COLOR="Red"]...
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/jvm/.java-6-sun.jinfo /usr/lib/jvm/java-6-sun-1.6.0.10/.systemPrefs /usr/lib/Adobe/Reader8/Reader/GlobalPrefs/.config /usr/lib/swiftfox/.autoreg /usr/lib/xulrunner-1.9.0.4/.autoreg /usr/lib/firefox-3.0.4/.autoreg /usr/lib/vmware/bin/.thnumod /lib/init/rw/.ramfs /lib/modules/2.6.27-7-generic/volatile/.mounted
...[/COLOR]

Are these files infected?

[COLOR="Red"]...
Checking `lkm'... You have     3 process hidden for readdir command
You have     3 process hidden for ps command
**chkproc: Warning: Possible LKM Trojan installed**
...[/COLOR]

How can I remove the LKM Trojan virus? thanks a lot.


[ATTACH]93103[/ATTACH]

---

### Post by Gamma746 on 2008-11-18
Just back up your data and reinstall.  If someone's trojanned you, then there's no end to the nasty things that they could have done.  Unless you reinstall, you'll never be sure that you've completely removed the rootkit or any backdoors.

---

### Post by en0f on 2008-11-19
I am perfectly sure your system is pretty safe (i.e., they are common scenarios) although it doesn't necessarily mean its not infected. 

[http://ubuntuforums.org/archive/index.php/t-216827.html](http://ubuntuforums.org/archive/index.php/t-216827.html)

---

### Post by Paul Lonon on 2010-02-21
I got a false positive for the LKM Trojan. I went back into the terminal and before the scan used.

sudo su

Logged into the root did another scan the LKM was gone.

---

### Post by mkvnmtr on 2010-02-21
I like the app Tiger. It does a series of checks and uses chrootkit to deliver a very comprehensive report. There do always seem to be warnings that you should check but an actual root kit would be very rare. I just run stuff like that for fun.

---

### Post by bodhi.zazen on 2010-02-21
> **Gamma746 said:**
> Just back up your data and reinstall.  If someone's trojanned you, then there's no end to the nasty things that they could have done.  Unless you reinstall, you'll never be sure that you've completely removed the rootkit or any backdoors.

That may be good advice if you have been compromised, however that is poor advice when new users run root kit detectors.

> **mkvnmtr said:**
> I like the app Tiger. It does a series of checks and uses chrootkit to deliver a very comprehensive report. There do always seem to be warnings that you should check but an actual root kit would be very rare. I just run stuff like that for fun.

If you use these tools on Linux (Antivirus, root kit detection, snort, ossec, tiger, etc, etc) you need to be willing to INVESTIGATE the "warnings" you recieve.

First , the tools are of no use if you do not know what is "normal". This means running the tools on a fresh install and knowing when something changes.

Second this means using Google to research the warnings.

In my experience the antivirus and rootkit tools are of little to no use as they search only for known problems after you have a problem and have a very high rate of false positives (as does snort and ossec).

Linux is not windows and you can not blindly apply windows virus scanning techniques to Linux.

I strongly suggest you read the stickies at the top of the security section.

---

