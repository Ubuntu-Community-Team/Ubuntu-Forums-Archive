---
title: "using cron to run .php file on startup"
date: 2008-02-21
forum: Server Platforms
---

### Post by vsiege on 2008-02-21
I don;t wat to keep my server running all day..so i shut it off when not needed... is there a way to have cron run a .php file when the computer is turned on(powered up), without having to first log in?

if there is another app thats better suited for this i would love to know..... everything i see for cron shows scheduling - which wont work for me.

---

### Post by FakeOutdoorsman on 2008-02-21
I recommend anacron.  It's in the repository.

"Unlike cron, it does not assume that the system is running continuously.  It can therefore be used to control the execution of daily, weekly and monthly jobs (or anything with a period of n days), on systems that don't run 24 hours a day."

---

### Post by MJN on 2008-02-22
Cron (and anacron) is a time-based scheduler hence it is not the correct tool for achieving what it an event-driven requirement.
 
Put your startup script (or rather the line to execute it) into /etc/rc.local - this will be executed on boot (on entering any single/multi-user runlevel actually but that's by-the-by for this unless you are changing runlevels regularly[1]). It will not require you to login (indeed it'll be done by the time you get your login prompt anyway).
 
Mathew
 
[1] If you don't want it executing if you change run-level then a better solution would be to call the script from /etc/rcS.d/ as this will only be done on boot (before the runlevel is set). You likely do not need to do this though.

---

### Post by vsiege on 2008-02-27
Thanks for both of your responses... it sounds like /etc/rc.local is the right thing for me...

at the bottom of all the comments (in rc.local) i see:
```
exit 0
```
if my file is located at /home/www/estart.php, where do i put this reference? or rather what should this file's contents look like after i edit it?

---

### Post by Mr. C. on 2008-02-27
```
php /home/www/estart.php

exit 0
```

The final exit 0 ensures a "success" code is returned to the startup scripts.  If your script does not handle or pass an exit status, that above code is fine.

---

### Post by Brazen on 2008-02-27
Putting it in the rc.local is the way to go.

Unless you only wanted it to run once a day or once a week, etc, then you would use anacron.

---

### Post by astrotech226 on 2008-02-27
> **Mr. C. said:**
> ```
php /home/www/estart.php

exit 0
```

The final exit 0 ensures a "success" code is returned to the startup scripts.  If your script does not handle or pass an exit status, that above code is fine.

If this script runs in a loop and never exits, you will need to background it.  Like:

```
php /home/www/estart.php &

exit 0
```

---

### Post by soulresin on 2008-02-27
/etc/rc.local will do the trick.

Just to be complete, you can do this with cron using the time of

@reboot

:)

---

### Post by MJN on 2008-02-28
Ah - I never knew that - thanks!

Mathew

---

### Post by vsiege on 2008-02-28
Wow, so many good tips all in one. 
** MJN  , Mr. C , Brazen** nice and simple, always a good approach. I didnt have a mail server installed and my php failed to send the mail. I looked through the php.ini but there was no space for L[unix] to adjust SMTP only WINS32. I think I have to install **postfix** to see my script work.

**FakeOutdoorsman** def. good to know anacron for the future

** soulresin**@reboot - thanx

---

