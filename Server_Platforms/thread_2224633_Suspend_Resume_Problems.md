---
title: "Suspend Resume Problems"
date: 2014-05-17
forum: Server Platforms
---

### Post by Satia_Herfert on 2014-05-17
Hey,

I've set up a small home server and I am experiencing issues with suspend and/or resume. I am using an auto-suspend script that calls '**sudo pm-suspend**' after inactivity. The server is woken up via Wake-On-LAN. This works great 90 % of the time.

At certain times the server just won't suspend properly, stays up but irresponsive. When I connect a monitor, it stays black. Then I have to press the physical power button and then it just starts up normally (not resume).

Here's an extract from '**/var/log/pm-suspend.log**' that shows a successful suspend output (there's a lot of output before that, mostly running hooks, I don't know what you need there):
```

+ log Thu May 15 23:30:02 CEST 2014: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Thu May 15 23:30:02 CEST 2014: performing suspend = -n ]
+ printf %s\n Thu May 15 23:30:02 CEST 2014: performing suspend
Thu May 15 23:30:02 CEST 2014: performing suspend
+ sync
+ do_suspend
+ uswsusp_get_quirks
+ OPTS=
+ ACPI_SLEEP=0
+ continue
+ [ 0 -ne 0 ]
+ [  = true ]
+ s2ram --force
KMS graphics driver is in use, skipping quirks.

```
A whole successful suspend/resume is even to big to attach as txt with 78 KB log data.

An unsuccessful attempt is almost identical, just the last line ("KMS graphics driver is in use, skipping quirks.") is missing. Thus, he never gets to that point, I assume.

System information:
OS: Ubuntu server 13.10 x86
Mainboard: AS-Rock E350M1

Please tell me if you need more information and what - I am not quite familiar with the subject.

I appreciate your help! If anything about the way I post is wrong please let me know. As you can see this is my first post on this forum.
Thanks!

---

