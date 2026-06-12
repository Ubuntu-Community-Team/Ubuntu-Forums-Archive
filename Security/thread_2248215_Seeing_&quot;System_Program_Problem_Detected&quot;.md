---
title: "Seeing &quot;System Program Problem Detected&quot; on startup"
date: 2014-10-13
forum: Security
---

### Post by jamal5 on 2014-10-13
Since about a week ago, as I login (14.04) I keep getting a message saying "System Program Problem Detected" several times each login, with the option to send an error report to Ubuntu (which I've done to no avail...). It doesn't say any further details as to what the problem is...


At the same time this started happening, I've noticed a few weird new bugs/changes in my system. The volume control which used to be at the top-right of the screen is gone. The System Settings button that used to be on the left bar is gone. Most worrying, when I try to run a Comodo Antivirus scan, it freezes up after about a minute and stays at the same number of objects scanned, uninstalling and reinstalling hasn't helped.

Is this something I should be worried about? Is it possible that my system's been hacked? Does anybody know how to solve this so I stop getting the annoying message? 

Is there a chance that this error message is actually coming from a malicious program that is just trying to get at my root password?

Thanks in advance

---

### Post by ibjsb4 on 2014-10-13
> Does anybody know how to solve this so I stop getting the annoying message? 
Yep, thats apport.
[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

Apport log is located in /var/log/apport.

---

### Post by bashiergui on 2014-10-13
And you can stop the pop-ups by removing the old crash reports ```
sudo rm /var/crash/*
```If you want to disable apport altogether, do this [http://www.binarytides.com/ubuntu-fix-system-program-problem-error/](http://www.binarytides.com/ubuntu-fix-system-program-problem-error/)

---

