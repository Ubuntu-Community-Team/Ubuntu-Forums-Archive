---
title: "CRONTAB - Date in to log file"
date: 2022-09-14
forum: Server Platforms
---

### Post by paweltech on 2022-09-14
Write date to log file Hi, I run a command through the crontab, which then writes a log file Is it possible to insert the date and time in the log file, when it is run?
Thank you

---

### Post by TheFu on 2022-09-14
Sure.
Just add an echo statement in the script with the date in the format you like. An example would be:
```
echo date "+%F-%R"
```

If the log file is created by the program being run, look for options in that software to include timestamps.  Logs without timestamps are fairly worthless, so if the program doesn't do that for every line, complain to the project team about it. Open a bug.

---

