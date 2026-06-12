---
title: "Older file over written local newer file"
date: 2010-02-16
forum: Ubuntu One (CLOSED)
---

### Post by mickcalcara on 2010-02-16
Hi. I have had relatively good success with Ubuntu One over the last several months. However, today I had an issue with a file being replaced with an older version from the Ubuntu One server. Basically, I have been editing an Open Office Calc spreadsheet that is located in the Ubuntu One folder. I have been making frequent updates over the last few days. Suddenly today it was replaced with a version from about 3 days ago. 

This file is not shared and is only edited from one workstation.

Is it not a good idea to make file edits directly into the Ubuntu One folder?  Could frequently updating a file cause an issue ( syncs not keeping up with changes etc? )?

Has this happen to anyone else? 


Thanks for any feedback

---

### Post by Marran77 on 2010-02-17
I have experienced something similar. See this post:[http://http://ubuntuforums.org/showthread.php?t=1398122]("http://http://ubuntuforums.org/showthread.php?t=1398122")
but I didn't get an satisfying answer. But I would like to know though

---

### Post by joshuahoover on 2010-02-18
> **mickcalcara said:**
> Hi. I have had relatively good success with Ubuntu One over the last several months. However, today I had an issue with a file being replaced with an older version from the Ubuntu One server. Basically, I have been editing an Open Office Calc spreadsheet that is located in the Ubuntu One folder. I have been making frequent updates over the last few days. Suddenly today it was replaced with a version from about 3 days ago. 

This file is not shared and is only edited from one workstation.

Is it not a good idea to make file edits directly into the Ubuntu One folder?  Could frequently updating a file cause an issue ( syncs not keeping up with changes etc? )?

Has this happen to anyone else? 


Thanks for any feedback

This should definitely not be happening and is a serious problem. Can you do the following to help provide as much information as possible about what may be causing this to happen?


[LIST=1]
[*]Quit the Ubuntu One client
[*]Open (or create if it doesn't exist): ~/.config/ubuntuone/syncdaemon.conf
[*]Add the following 2 lines to this file and save
[main]
log_level = DEBUG
[*]Open the Ubuntu One client
[*]Try to reproduce the problem you're experiencing
[*]File a new bug by right-clicking on the Ubuntu One client and select "Report a Problem"
[*]Attach ~/.cache/ubuntuone/log/syncdaemon.log to the bug report
[/LIST]
Thank you,

Joshua

---

### Post by joshuahoover on 2010-02-18
> **Marran77 said:**
> I have experienced something similar. See this post:[http://http://ubuntuforums.org/showthread.php?t=1398122](http://http://ubuntuforums.org/showthread.php?t=1398122)
but I didn't get an satisfying answer. But I would like to know though

My apologies for missing your original message/thread. If you are still experiencing this problem you can follow the steps I posted above. You can also hop on #ubuntuone on Freenode IRC to get real time help. I'm joshuahoover on there and am normally there Monday-Friday, 14:00 UTC - 22:00 UTC. 

Thank you,

Joshua

---

