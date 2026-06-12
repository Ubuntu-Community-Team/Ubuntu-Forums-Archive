---
title: "Thunderbird and Firebird segfaulting on startup"
date: 2014-02-25
forum: Ubuntu Development Version
---

### Post by ubucatz on 2014-02-25
Hi, 

there are several bug reports about this, but I would like to ask if there is any quick fix, as it is really a problem not being able to use thunderbird to check mail accounts. Setting any env var did not helped (like described).

Since the last 14.04 glibc update a few days ago Thunderbird and Firebird segfault at startup:

```
ubucatz@ubuntu:~$ firefox


(process:3489): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(firefox:3489): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(firefox:3489): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(firefox:3489): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(firefox:3489): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Segmentation fault (core dumped)

ubucatz@ubuntu:~$ thunderbird


(process:3503): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(thunderbird:3503): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(thunderbird:3503): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(thunderbird:3503): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(thunderbird:3503): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
Segmentation fault (core dumped)
```




Thanks for your attention,
Ubucatz

---

### Post by 23dornot23d on 2014-02-25
I see its in the following bug report and you have added a comment at the end 
so they should deal with it ......... seems its been open for some time now.

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1160569](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1160569)

Its down as Critical at the top ...... of the report and seems to affect multiple platforms.

---

