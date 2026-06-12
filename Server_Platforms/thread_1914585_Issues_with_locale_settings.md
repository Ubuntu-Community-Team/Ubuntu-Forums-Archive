---
title: "Issues with locale settings"
date: 2012-01-24
forum: Server Platforms
---

### Post by Wouter_DS on 2012-01-24
When I try to install or remove something I get always this warnings:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_CTYPE = "UTF-8",
    LANG = (unset)
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```I read a lot of solutions with regenerating and exporting but none of them worked until now. The export settings (eg: export LC_ALL=en_US) are working, but after a reboot there gone.. 

Is there anyone who can help me?

PS: Just upgraded from Ubuntu 10.10 (server edition) to 11.04, but I'm going to upgrade to 11.10.

Regards

---

### Post by fabio.hipolito on 2012-02-05
Hello,

have a look at this other tread in [ubuntuforums]("http://ubuntuforums.org/showthread.php?t=1720356&highlight=file+directory+locale%3A+set+LC_CTYPE+default") it seems the same.

Best regards.

---

