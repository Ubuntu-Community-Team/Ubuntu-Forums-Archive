---
title: "bugs at launchpad now marked invalid"
date: 2014-06-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-06-28
Apport poked me to do three bug reports and they are all now marked invalid.

Any ideas what I did wrong or am not doing right?

---

### Post by mc4man on 2014-06-28
a link (or 3) would be helpful

---

### Post by mc4man on 2014-06-28
I see one now (unity-control-center
Could be 2 things -
If you are not fully updated with related (to crash) packages then apport shouldn't allow you to file the crash bug in  the first place, apparently it did.
It could also be that all the needed debug sources aren't available atm in Launchpad so a retrace would fail.

In general - update your install
remove all prior crash files from /var/crash
```
sudo rm /var/crash/*.*
```

re-trigger or attempt to your crashes & refile

As far as the unity-control-center hold off on for a bit, I filed from fully updated install  to see if the retrace fails.

Edit: the retrace worked so your issue was you weren't fully updated prior to getting & filing the crash & apport allowed you to file 
anyway (possible bug in apport itself
[https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1335438](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1335438)

---

### Post by ventrical on 2014-06-28
But I have been updating.  I did remove  those files as you suggested but I also had to uncomment a line in powerd.conf as was suggested by the link.

> 
Please  report any bugs you find with powerd. If you have issues, you need to  enable debug messages, which as of July 11 are disabled by default. In  order to do that you need to edit /etc/init/powerd.conf and remove the  comment (the # character) on the line that says "env POWERD_DEBUG=1".  After doing that you can reboot the phone and reproduce your issue. Once  the issue comes back, please attach the contents of /var/log/syslog to  the bug. If you want you can filter that log to only have powerd entries  using grep. 




[https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1335449](https://bugs.launchpad.net/ubuntu/+source/powerd/+bug/1335449)

---

### Post by ventrical on 2014-06-28
> **mc4man said:**
> I see one now (unity-control-center
Could be 2 things -
If you are not fully updated with related (to crash) packages then apport shouldn't allow you to file the crash bug in  the first place, apparently it did.
It could also be that all the needed debug sources aren't available atm in Launchpad so a retrace would fail.

In general - update your install
remove all prior crash files from /var/crash
```
sudo rm /var/crash/*.*
```

re-trigger or attempt to your crashes & refile

As far as the unity-control-center hold off on for a bit, I filed from fully updated install  to see if the retrace fails.

Edit: the retrace worked so your issue was you weren't fully updated prior to getting & filing the crash & apport allowed you to file 
anyway (possible bug in apport itself
[https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1335438](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1335438)


Thanks much ;)

---

### Post by Cavsfan on 2014-06-28
> **mc4man said:**
> 
In general - update your install
remove all prior crash files from /var/crash
```
sudo rm /var/crash/*.*
```

That is a very good command to have on hand.
I saved it. 
Thanks :)

---

### Post by Cavsfan on 2014-06-28
Earlier today when I seen this thread I entered this to clear everything out: ```
sudo rm /var/crash/*.*
```

This I get this bug which I have gotten before: **notify-osd crashed with signal 5 in _XReply()** which does not appear on the first page listed; only really old bugs show on that page. 
So I open **bugs** at the top in another tab and enter the error. Four bugs appeared #404271 (Ubuntu 9.10), #922129 (Ubuntu 12.04), #1206754 (Ubuntu 13.10) and then the correct one being last.
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524) 

I had originally reported that bug and just enter in the comments that I got this error again when something happened.

Previously I added myself to the 1st one #404271 (Ubuntu 9.10) because it is triaged and has the highest number by the fire symbol; it also has a little road sign that says "Branch exists".

Am I doing this right? Because this is a bit confusing. :-|

---

### Post by mc4man on 2014-06-28
Well the "notify-osd crashed with signal 5 in _XReply()' has been going on for 5 yrs. so likelihood of being addressed isn't that good.
you could go to [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524)
click on the little yellow circle on the Tags: line & add utopic, save, (button with green checkmark), & don't hold breath awaiting a fix

(as far as the 9.10 bug, nobody cares anymore as 9.10 is long dead

---

### Post by Cavsfan on 2014-06-28
> **mc4man said:**
> Well the "notify-osd crashed with signal 5 in _XReply()' has been going on for 5 yrs. so likelihood of being addressed isn't that good.
you could go to [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524)
click on the little yellow circle on the Tags: line & add utopic, save, (button with green checkmark), & don't hold breath awaiting a fix

(as far as the 9.10 bug, nobody cares anymore as 9.10 is long dead

OK will do. Yeah I know 9.10 Karmic Koala is long dead that's why I thought it was weird. I guess many people get that error if it's been going on that long. 
They just don't see it with apport reporting bugs turned off.
I added utopic to it. I won't hold my breath for sure. :lol:

---

### Post by Cavsfan on 2014-09-15
> **mc4man said:**
> Well the "notify-osd crashed with signal 5 in _XReply()' has been going on for 5 yrs. so likelihood of being addressed isn't that good.
you could go to [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524)
click on the little yellow circle on the Tags: line & add utopic, save, (button with green checkmark), & don't hold breath awaiting a fix

(as far as the 9.10 bug, nobody cares anymore as 9.10 is long dead

I got the same bug *again*. This time I found this bug that I had reported in Precise. :p [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1275524)

I added utopic and systemd-boot to it and no I'm not holding my breath. :)

---

