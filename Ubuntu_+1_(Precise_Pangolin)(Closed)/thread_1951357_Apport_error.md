---
title: "Apport error"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wgarcia on 2012-04-02
In one of my systems fully updated to 12.04 any of the commands "ubuntu-bug", "apport-cli" or "apport-collect" is crashing apport and producing the following error:

```
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 506, in <module>
    app.run_argv()
  File "/usr/lib/python2.7/dist-packages/apport/ui.py", line 543, in run_argv
    return self.run_report_bug()
  File "/usr/lib/python2.7/dist-packages/apport/ui.py", line 348, in run_report_bug
    self.collect_info(symptom_script)
  File "/usr/lib/python2.7/dist-packages/apport/ui.py", line 912, in collect_info
    anonymize_thread.exc_raise()
  File "/usr/lib/python2.7/dist-packages/apport/REThread.py", line 34, in run
    self._retval = self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 1297, in anonymize
    replacements.append((re.compile('\\b%s\\b' % s), 'User Name'))
  File "/usr/lib/python2.7/re.py", line 190, in compile
    return _compile(pattern, flags)
  File "/usr/lib/python2.7/re.py", line 242, in _compile
    raise error, v # invalid expression
sre_constants.error: nothing to repeat

```

This stops me from reporting any bugs. Fortunately I could report this bug itself:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/971497](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/971497)

I've tried to clean apport by "remove purging" it and reinstalling, removing the files in /var/log/crash, recreating /var/log/dpkg/available, restarting the system and apport, but I always get this error now.

I don't see this error in any of my other systems with updated 12.04, so I suspect this comes from a misconfigured file or something. Does anybody know of any other places that I could clean files created or used by apport?

---

### Post by dino99 on 2012-04-02
dupe oops

---

### Post by dino99 on 2012-04-02
Got a similar one while using apport-collect:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/969950](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/969950)

seems related to python2.7

---

### Post by wgarcia on 2012-04-02
If you get a workaround please tell, because in the affected system I cannot use any bug-reporting method.

---

### Post by wgarcia on 2012-04-03
I'm still having this problem. In the meantime I have figured out that it only happens with my main user (I can for instance run "ubuntu-bug" from the guest account). I have tried everything to clean my user account but I still get this error. 

I also noticed that the error does not pop up if I run apport with "sudo", that is for instance "sudo ubuntu-bug <package>", but no matter what I do "ubuntu-bug <package>" produces the above error.

---

