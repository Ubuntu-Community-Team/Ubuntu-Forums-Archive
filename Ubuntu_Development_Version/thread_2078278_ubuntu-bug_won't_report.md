---
title: "ubuntu-bug won't report"
date: 2012-10-30
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2012-10-30
initramfs screwed up and left a crash report in /var/crash

In trying to report it with ubuntu-bug I keep getting:

```
jerry@Aspire1:~$ ubuntu-bug initramfs
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 588, in <module>
    app.run_argv()
  File "/usr/lib/python3/dist-packages/apport/ui.py", line 637, in run_argv
    return self.run_report_bug()
  File "/usr/lib/python3/dist-packages/apport/ui.py", line 439, in run_report_bug
    self.collect_info(symptom_script)
  File "/usr/lib/python3/dist-packages/apport/ui.py", line 975, in collect_info
    hookui, symptom_script, ignore_uninstalled))
  File "/usr/lib/python3/dist-packages/apport/REThread.py", line 22, in __init__
    threading.Thread.__init__(self, group, target, name, args, kwargs, verbose)
TypeError: __init__() takes from 1 to 6 positional arguments but 7 were given

```

I presume I'm not able to report the crash to launchpad?

-rw------- 1 root  whoopsie 262646 Oct 30 13:49 initramfs-tools.0.crash

Any hints or just wait and keep updating....

Thanks, Jerry

p.s. temporary workaround as in mc4man's suggestion,
sudo gedit /usr/lib/python3/dist-packages/apport/REThread.py
and remove last argument, "verbose"
ubuntu-bug then ran.  I don't know if anything useful to the bug shooters was dropped off.

---

### Post by mc4man on 2012-10-30
Not too far down this forum page
[http://ubuntuforums.org/showthread.php?t=2077634](http://ubuntuforums.org/showthread.php?t=2077634)

---

### Post by ventrical on 2012-10-30
I got this today also..

---

### Post by ronacc on 2012-10-30
I got the same error as ventrical when I tried to send in a bug report on gparted . I'm also getting random mouse lockups and have to alt>sysreq>b to restart .

---

### Post by thotz on 2012-10-31
I can confirm this. Hopefully we see a fix soon :)

---

