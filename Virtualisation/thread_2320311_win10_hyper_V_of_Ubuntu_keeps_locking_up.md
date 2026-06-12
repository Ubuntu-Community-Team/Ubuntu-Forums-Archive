---
title: "win10 hyper V of Ubuntu keeps locking up"
date: 2016-04-12
forum: Virtualisation
---

### Post by Jeffrey_Becker on 2016-04-12
Every day or three my virtual guest will completely lock up (I can still see the login screen) and I have to 'Turn Off' the VM.
Before I turn it off it shows the RAM is around 30-60% usually around 4-6GB of ram allocated to the machine (it's auto allocated)

I'm curious if I should be looking in the windows logs or in the Ubuntu logs since periodically I'll get different problems with the Ubuntu machine.
It once told me it was in low graphics mode and another time it went to a console with logging info even though my servers were still up I couldn't interface with the machine at all except through webmin.

I'd love to provide more information but I'm not exactly sure WHEN it is locking up or what to look for.

---

### Post by MAFoElffen on 2016-04-13
Usually if you are trying to track down a process that is eating up memory, in Windows you would turn on audting in the performance monitor. In Lunix you write a script that is triggered by cron (the scheduler) that will write the top 5 processes to a file that you can review (later).

If you do a quick search of the server section, there are a gazillon examples of that, for instance, run a coomand, such as this, tailor it to  the output you need, then redirect the output to a file, then add it to a script that can be reused... (execute with elevated privileges, which cron will do normally):
```

ps -eo pcpu,pid,user,args | sort -r | head -5 >> /var/logs/audit.log

```
After tweaking it to get the ouptut you need, and adding it to a script... then figure out the frequency you want it to check, then add the script execution as a cron job.

One caution- This appends to a file without checking other elements... Does not check the size of that file, does not rotate to different versions of that files... So if you forgot it... It could eventually, potentially create a large enough file to fill a disk. Remember to remove the job when you are through using it.

---

