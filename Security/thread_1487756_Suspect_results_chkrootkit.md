---
title: "Suspect results chkrootkit"
date: 2010-05-19
forum: Security
---

### Post by jfa2214 on 2010-05-19
I recently purchased a new laptop and installed Ubuntu 10.04 LS Amd 64 desktop as an additional boot to Windows 7. I installed and ran chkrootkit. It ran clean with the following exception.

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  

```
usr/lib/firefox-3.6.3/.autoreg
 /usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit 
/usr/lib/jvm/.java-6-openjdk.jinfo 
/usr/lib/xulrunner-1.9.2.3/.a
```

Is this a problem or just a false negative?
If it is a problem what should I do to resolve it?:confused:

---

### Post by teh_drizzle on 2010-05-19
I'd say you're fine. :)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549938](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549938)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9318143](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9318143)

(Looks like those are common false-positives.) Try running rkhunter (usually finds more false-positives) to see if there is an overlap.

---

### Post by jfa2214 on 2010-05-19
Tmx teh_drizzle

I ran rkhunter. No indication of the original suspects. Rkhunter ran with no issues. This has been a good learning experience. I now know what I need to run and how to run them. 

Thanks again:P

---

### Post by bodhi.zazen on 2010-05-19
> **jfa2214 said:**
> Tmx teh_drizzle

I ran rkhunter. No indication of the original suspects. Rkhunter ran with no issues. This has been a good learning experience. I now know what I need to run and how to run them. 

Thanks again:P

You probably do not need to run these tools and you missed the most important lesson -

You need to learn to use google to investigate any warnings you get. Warnings mean that, you need to investigate to see if such a file is "normal" for your system.

:popcorn:

---

