---
title: "[EC2] : what is the way to change / set system date and time by cmd line ?"
date: 2016-12-13
forum: Ubuntu Cloud and Juju
---

### Post by hmachefer on 2016-12-13
I keep trying to "manually" set system date and time by CLI once ssh-connected to my EC2 (Ubuntu-16) instance, for example:[INDENT][COLOR=#000080][FONT=courier new]sudo date -s '2016-12-12 17:10:30'[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#000080][FONT=courier new]sudo date --set "12 DEC 2016 5:10:30 PM"[/FONT][/COLOR][/INDENT]
but always unsuccessfully, that is to say invoking next command as query:[INDENT][FONT=courier new]date[/FONT][/INDENT]
always returns current date & time, regardless of earlier attempts to apply predetermined one as 2016-12-12 [FONT=&quot]17:10 [/FONT]...

I have read this *[http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/set-time.html](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/set-time.html)* (not my purpose) and that *[https://ubuntuforums.org/showthread.php?t=1172252](https://ubuntuforums.org/showthread.php?t=1172252)* however the solution never applies to me, meaning:[INDENT][COLOR=#000080][FONT=courier new]ubuntu@ip-172-31-31-101:~$ echo 1 > /proc/sys/xen/independent_wallclock[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#000080][FONT=courier new]-bash: [/FONT][/COLOR][COLOR=#ff0000][FONT=courier new]/proc/sys/xen/independent_wallclock**: No such file or directory**[/FONT][/COLOR][/INDENT]

So is it possible to modify / **set **current (system) **date** after all and what is the magic trick to get it changed eventually ?

---

