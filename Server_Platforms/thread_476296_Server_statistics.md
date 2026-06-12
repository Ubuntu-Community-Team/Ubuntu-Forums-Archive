---
title: "Server statistics?"
date: 2007-06-17
forum: Server Platforms
---

### Post by Moonshine on 2007-06-17
Heya,

Are there any scripts available that can show statistics such as:
[LIST]
[*]Uptime
[*]Average Load
[*]Disk space
[*]What computers are accessing the samba share
[*]How many pages have been printed by cups
[*]Network connectivity
[/LIST]

Preferably the script would just be a command that could be typed by SSH, just so I could log in from time to time and take a look.

Thanks!

---

### Post by Gruelius on 2007-06-17
Well for disk space df -h does a great job.

---

### Post by elst on 2007-06-17
Each feature has it's own command-line utility that extracts information from the underlying software, and at the simplest level you can easily write a script that captures the outputs, and either run it interactively, or schedule it and have it send you mails.

For a more sophisticated approach (that takes a bit of time to setup), look into monitoring software.

---

