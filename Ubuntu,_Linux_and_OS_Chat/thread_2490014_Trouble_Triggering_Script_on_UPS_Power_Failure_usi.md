---
title: "Trouble Triggering Script on UPS Power Failure using NUT"
date: 2023-08-18
forum: Ubuntu, Linux and OS Chat
---

### Post by free.dragon on 2023-08-18
I'm currently facing an issue with configuring NUT (Network UPS Tools) to trigger a script when my UPS goes on battery power (ONBATT event). Despite trying various configurations and troubleshooting steps, I haven't been able to get the script to execute when the power failure occurs.


Here's an overview of what I've tried so far:


**1. Configuration Files and Script**


I have added the following lines to my upsmon.conf file:


NOTIFYFLAG ONBATT SYSLOG+WALL+EXEC
NOTIFYCMD /home/nut/batt.sh


The batt.sh script is located at /home/nut/batt.sh and has the execute permission set (chmod +x batt.sh).
The script is simple and logs message to a file (/home/nut/log.txt). Scripts runs on manual execution.



**2. Troubleshooting Steps Taken**


I've checked system logs (/var/log/syslog) for NUT-related messages but haven't found any relevant entries indicating script execution.
The DEBUGLEVEL option doesn't seem to be available in upsmon.conf for increasing debug output.
I've restarted the NUT service after making changes to configuration files.
The NOTIFYFLAG and NOTIFYCMD settings appear to be correctly defined in upsmon.conf.

NOTIFYFLAG ONLINE	SYSLOG+WALL+EXEC
NOTIFYFLAG ONBATT	SYSLOG+WALL+EXEC



**4. Permissions and Ownership**


I've given user nut sufficient permissions to execute the script. Even made home directory for nut user.
The batt.sh script is owned by nut user and has the execute permission set.
I've checked that there are no typos or syntax errors in the configuration files.


Has anyone else encountered a similar issue with NUT? Are there any suggestions or insights you can provide to help me resolve this issue?

---

### Post by #&amp;thj^% on 2023-08-18
Without seeing your script I've have missed this part:
```
NOTIFYMSG ONBATT "Someone pulled the plug on %s"
```
It won't work with spaces, they need to be wrapped with quote tags.
Just a passing thought.

---

### Post by free.dragon on 2023-08-19
NOTIFYMSG was commented out

I added

```
NOTIFYMSG ONBATT    "UPS %s on battery"
```

but nothing changed. I restart nut-server service between each change and this time even restarted the whole system.

Script in batt.sh is:
```
[COLOR=#000000][FONT=Menlo]#!/bin/bash
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]current_datetime=$(date +"%Y-%m-%d %H:%M:%S")[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]echo "Running on battery power at $current_datetime" >> /home/nut/battery_log.txt[/FONT][/COLOR]
```

I do not pass any arguments into the script.

---

### Post by #&amp;thj^% on 2023-08-20
Here are some good thoughts and ideas: [https://technotim.live/posts/NUT-server-guide/](https://technotim.live/posts/NUT-server-guide/)

---

