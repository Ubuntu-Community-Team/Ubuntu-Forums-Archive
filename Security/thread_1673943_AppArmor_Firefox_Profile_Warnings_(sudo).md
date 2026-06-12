---
title: "AppArmor Firefox Profile Warnings (sudo)"
date: 2011-01-23
forum: Security
---

### Post by funnyelephant on 2011-01-23
Hi,

I've enabled the Firefox apparmor profile shipped with ubuntu a while ago, but I keep getting worrying messages whenever I download a file.

As soon as the download is finished and an application is launched to view the file, I get a notification like seen in the screenshot attached. However the application opens normally and I can view the downloaded file.

Here's are example log messages from /var/log/kern.log:
> 
Jan 23 10:55:07 lim kernel: [34304.735844] type=1400 audit(1295776507.177:1391): apparmor="DENIED" operation="exec" parent=21259 profile="/usr/lib/firefox-3.6.13/firefox-*bin" name="/usr/bin/sudo" pid=23656 comm="firefox-bin" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Jan 23 12:19:39 lim kernel: [39367.848837] type=1400 audit(1295781579.385:1392): apparmor="DENIED" operation="exec" parent=24003 profile="/usr/lib/firefox-3.6.13/firefox-*bin" name="/usr/bin/sudo" pid=25065 comm="firefox-bin" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Jan 23 12:22:21 lim kernel: [39529.656853] type=1400 audit(1295781741.487:1393): apparmor="DENIED" operation="exec" parent=24003 profile="/usr/lib/firefox-3.6.13/firefox-*bin" name="/usr/bin/sudo" pid=25148 comm="firefox-bin" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
Why would firefox want to call sudo? This looks fishy to me.

Please tell me that there's an easy explanation :-)

Funnyelephant

---

### Post by bodhi.zazen on 2011-01-23
firefox has no reason, IMO, to run sudo.

It may be calling sudo if you are using apturl

What are you trying to download ?

---

