---
title: "Apparmor log files."
date: 2011-07-25
forum: Security
---

### Post by roodypoo on 2011-07-25
I have set profiles using the aa-autodep command for tor and privoxy. When I have the profiles set to enforce neither one works. When I set them to complain, I can't find the log files. 

The folder /var/log/apparmor is empty. Where are the log files stored and once I find them can I post them so that I may get some help with setting up the profiles? Also, is there a list of programs that I should set up profiles for? I've already installed the profiles from the repository.

---

### Post by bodhi.zazen on 2011-07-25
Should log to /var/log/messages

---

### Post by roodypoo on 2011-07-25
I may be an idiot, so go easy.

There are some entries in syslog that have apparmor in them, but nothing that says something would be blocked. They all say allow.

The apparmor folder is empty.

---

### Post by Dave_L on 2011-07-26
By default, apparmor's messages are sent to several existing log files. 

There are some notes in this topic that show how to redirect apparmor messages to a dedicated log file, which makes it *much* easier to work with:

[http://ubuntuforums.org/showthread.php?t=1733231](http://ubuntuforums.org/showthread.php?t=1733231)

---

