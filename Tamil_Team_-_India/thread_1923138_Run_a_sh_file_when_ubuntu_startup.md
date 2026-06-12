---
title: "Run a sh file when ubuntu startup"
date: 2012-02-10
forum: Tamil Team - India
---

### Post by shivashiva on 2012-02-10
Hi Friends,
            I need to run a sh file when the ubuntu 9.04 startup.Please help me how to do. Thanks.

---

### Post by jayshomebrew on 2012-02-10
goto
system/preferences/startup applicatoins
click the add button and add your .sh script.


[IMG]http://lh6.ggpht.com/_FJH0hYZmVtc/Son1CMwQbhI/AAAAAAAACD0/r3F-Hwh5QsA/Ubuntu%209.04%20Jaunty%20Jackalope%20-%20Gnome%20-%20Startup%20Applications%20Preferences%5B4%5D.png[/IMG]

alternatively, you can add it to cron:
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

ie,
```
crontab -e
@reboot /home/jayshomebrew/bin/mycoolscript.sh
```

---

