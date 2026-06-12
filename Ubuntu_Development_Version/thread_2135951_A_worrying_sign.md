---
title: "A worrying sign"
date: 2013-04-16
forum: Ubuntu Development Version
---

### Post by iamkuriouspurpleoranj on 2013-04-16
[[img]http://ompldr.org/taTQybA[/img]](http://ompldr.org/vaTQybA/Capture du 2013-04-16 06:41:53.png)

Hadn't done anything except boot my machine. There is one window before this one but the bug happened without me doing anything.

Not a good sign.

---

### Post by serdotlinecho on 2013-04-16
It's not a worrying sign. It's [apport]("https://wiki.ubuntu.com/Apport") doing its job. You can disable it anyway. And you're using the beta version of Ubuntu.  ;)
If you want to disable it from startup, comment out(#) start on runlevel:

```
sudo -i
gedit /etc/init/apport.conf
```

```
# apport - automatic crash report generation
#
# While this job is active, core dumps will captured by apport and
# used to generate automatic crash reports.

description    "automatic crash report generation"

#start on runlevel [2345]
stop on runlevel [!2345]
```

---

### Post by iamkuriouspurpleoranj on 2013-04-16
Yes but it never crashed. So where does it come from?

---

### Post by deadflowr on 2013-04-16
> **iamkuriouspurpleoranj said:**
> Yes but it never crashed. So where does it come from?

What does the little details box tell you?

Click on that box and eventually it'll show you the generated crash report, which will include at the top the program that crashed.

---

