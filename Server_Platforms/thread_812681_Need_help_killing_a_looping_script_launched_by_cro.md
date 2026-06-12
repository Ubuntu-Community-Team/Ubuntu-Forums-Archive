---
title: "Need help killing a looping script launched by cron"
date: 2008-05-30
forum: Server Platforms
---

### Post by b166er on 2008-05-30
Hi
I'm currently writing a Bash script that is designed to loop every 9 seconds. The task it's doing is basicly linking all files in one directory named a specific thing into another directory. But occationally I want to kill the script process to "upgrade" its wildcards to another word. How can I find its PID so i can kill it? will I find it with the "ps" command? I haven't dared testing it in cron yet since i can't afford a reboot.

---

### Post by Aearenda on 2008-05-30
```
ps aux
```will show you the list...
```
pgrep script-name
``` will find the pid for you...
But ```
killall script-name
``` sounds like what you are really looking for.

Why does the script need to loop so often?

---

### Post by b166er on 2008-05-30
Thanks, I allready knew about the "ps aux" command but wasn't sure if I could see the script name in there if it was launched by cron.

The reason for the fast looping is because the first folder is the output folder from a program that creates uncompressed video files.
the script then filters out all the files in there called something like "to_mpeg_encoder" or "to_xvid_encoder" to seperate folders. then another application which is set to encode all the videos in a specific folder to a specific codec takes over. and that program scans each folder every 10 seconds. And time is allways of the essance.
Hope youre glad you asked :)

---

### Post by Aearenda on 2008-05-30
Yep, I'm glad I asked! 

I wonder if there might be a more efficient way to do this, based on filesystem change notification. But I'm not a programmer any more, so I'll leave that to others for comment.

---

