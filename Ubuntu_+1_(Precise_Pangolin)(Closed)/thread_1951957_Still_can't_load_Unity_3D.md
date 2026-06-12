---
title: "Still can't load Unity 3D"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-04-03
What the heck? What gives? :confused: I just installed a bunch of compiz updates, but nothing. I try compiz --replace and get the following (just some choice extracts):

> 
(compiz:2713): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed

(compiz:2713): dee-CRITICAL **: dee_model_get_tag: assertion `DEE_IS_MODEL (self)' failed

> WARN  2012-04-03 11:48:05 unity.libindicator <unknown>:0 Desktop file '/home/vtpoet/.local/share/applications/firefox.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-04-03 11:48:05 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/google-chrome.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-04-03 11:48:05 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/thunderbird.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-04-03 11:48:05 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a depracted format for it's actions that will be dropped soon.
WARN  2012-04-03 11:48:05 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window73405583: No such interface `org.ayatana.bamf.view' on object a

---

### Post by neu5eeCh on 2012-04-03
OK. I _finally_ found the bug associated with this problem:

[https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125](https://bugs.launchpad.net/ubuntu/+source/compizconfig-backend-gconf/+bug/932125)

**Edit:** The latest series of updates (as of April 2012) seems to have solved this problem. Marking the thread solved.

---

### Post by mc4man on 2012-04-03
What happens when you log in to ubuntu session (unity 3d

For the heck of it on my older install deleted .gconf/apps/compiz-1 & the .dconf/user file- getting unity back was interesting to say the least

---

