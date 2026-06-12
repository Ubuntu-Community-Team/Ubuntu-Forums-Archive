---
title: "Need help debugging my first backup script!"
date: 2011-09-20
forum: Tutorials
---

### Post by scytherswings on 2011-09-20
So I just made my first attempt at a .sh backup script this morning. The idea is to check if the minecraft server is running and if so, backup. I plan to run this script through cron. Here's my attempt so far.
p.s. The ps grep statement is intended to make sure the script only backs up when the server is run, which has an argument -Xincgc in the command args line of ps.
Thanks much!


#!/bin/sh
######################################
# Check if Minecraft Server is running
# In order to prevent needless backups
######################################

RUNSTAT="$ps -C java -o pid=PID -o comm=CMD,args | grep -q Xincgc"

if [$RUNSTAT==0]; then
	echo "Starting Backup" && tar -vzcf /home/******/backup/minecraft.$(date +\%Y,\%m,\%d-\%H:\%M:\%S).tar.gz /home/******/Minecraft && echo "Backup Completed Successfully"
else
	echo "Server is Offline"
fi

---

