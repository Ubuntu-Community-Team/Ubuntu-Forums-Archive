---
title: "Is AppArmor too restrictive, or is it stopping a real problem?"
date: 2010-10-23
forum: Security
---

### Post by Brian Vaughan on 2010-10-23
I'm using Ubuntu 10.10, with apparmor and apparmor-profiles installed, as well as apparmor-notify (which is informative); I've executed "sudo enforce firefox". 

Today, I was trying to follow instructions from an employer for "connecting to the VPN", apparently through a Java applet in a Web browser. It didn't seem to work, and I got a lot of warning messages from apparmor_notify.

Here are a couple of typical messages from /var/log/kern.log:
```
Oct 23 18:47:17 brian-desktop kernel: [35178.402280] type=1400 audit(1287884837.585:251): apparmor="DENIED" operation="exec" parent=6721 profile="/usr/lib/firefox-3.6.11/firefox-*bin//browser_openjdk" name="/bin/dash" pid=6722 comm="java" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Oct 23 18:47:17 brian-desktop kernel: [35178.418710] type=1400 audit(1287884837.601:252): apparmor="DENIED" operation="exec" parent=6723 profile="/usr/lib/firefox-3.6.11/firefox-*bin//browser_openjdk" name="/bin/dash" pid=6724 comm="java" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Oct 23 18:47:19 brian-desktop kernel: [35180.446478] type=1400 audit(1287884839.628:253): apparmor="DENIED" operation="exec" parent=6726 profile="/usr/lib/firefox-3.6.11/firefox-*bin//browser_openjdk" name="/bin/dash" pid=6727 comm="java" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Oct 23 18:47:19 brian-desktop kernel: [35180.457808] type=1400 audit(1287884839.640:254): apparmor="DENIED" operation="exec" parent=6728 profile="/usr/lib/firefox-3.6.11/firefox-*bin//browser_openjdk" name="/bin/dash" pid=6729 comm="java" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Oct 23 18:47:21 brian-desktop kernel: [35182.473602] type=1400 audit(1287884841.656:255): apparmor="DENIED" operation="exec" parent=6730 profile="/usr/lib/firefox-3.6.11/firefox-*bin//browser_openjdk" name="/bin/dash" pid=6731 comm="java" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Oct 23 18:47:21 brian-desktop kernel: [35182.495287] type=1400 audit(1287884841.676:256): apparmor="DENIED" operation="exec" parent=6732 profile="/usr/lib/firefox-3.6.11/firefox-*bin//browser_openjdk" name="/bin/dash" pid=6733 comm="java" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
```

I'm able to execute Java applets, such as the one at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml), without difficulty.

So, the question is whether AppArmor is set to be too restrictive, or whether this applet is really trying to do something it shouldn't be doing. I'd like to get my facts in order before I complain.

---

