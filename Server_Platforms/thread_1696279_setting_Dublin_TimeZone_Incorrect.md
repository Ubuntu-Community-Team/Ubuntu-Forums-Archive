---
title: "setting Dublin TimeZone Incorrect"
date: 2011-02-27
forum: Server Platforms
---

### Post by stafforg on 2011-02-27
Hi

Using Ubuntu Server 10.04.2 LTS
This is what happens when I try to set my timezone to Dublin.
1 dpkg-reconfigure tzdata
2 Then select Europe -> Dublin.

But the time is incorrect, it should be an hour ahead of the time stated.
[B]Current default time zone: 'Europe/Dublin'
Local time is now:      Sun Feb 27 11:20:03 GMT 2011.
Universal Time is now:  Sun Feb 27 11:20:03 UTC 2011.[/B]

Any ideas? thanks

Befow is a screen printout of what happens

:/# dpkg-reconfigure tzdata
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = ".UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_CTYPE to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_MESSAGES to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory

Current default time zone: 'Europe/Dublin'
Local time is now:      Sun Feb 27 11:20:03 GMT 2011.
Universal Time is now:  Sun Feb 27 11:20:03 UTC 2011.

---

