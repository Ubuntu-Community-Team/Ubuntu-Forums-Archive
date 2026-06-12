---
title: "update-notifier like script for servers"
date: 2006-06-22
forum: Server Platforms
---

### Post by mariuss on 2006-06-22
Is there a "update-notifier" like script for servers?

Ideally the script would be run periodically through cron and it will:
- run apt-get update
- check if there are any upgredable packages
- optionally will only download (no install) these upgredable packages
- send out an email if there is anything to be upgraded

Marius

---

### Post by jrattner on 2006-06-22
Here is a little script I use for my server.

```

#!/bin/bash
apt-get update
apt-get upgrade -y
apt-get autoclean
reboot

```

I have this in a file called WeeklyUpdate in my /etc/cron.weekly

NOTE: This downloads AND installs the packages.  I added the reboot line so if something like a new kernel is installed that there won't be issues.

On completion I recieve an E-mail showing the success of the cron job and its output.

---

### Post by mariuss on 2006-06-22
[QUOTE=jrattner]
NOTE: This downloads AND installs the packages.  I added the reboot line so if something like a new kernel is installed that there won't be issues.[/QUOTE]
This is something I want to avoid, I would like to be only notified. Automatic installs and reboots are kind of dangerous IMHO.

> On completion I recieve an E-mail showing the success of the cron job and its output.
Who is sending the email? I could not figure that from your script.

Thanks,
Marius

---

### Post by jrattner on 2006-06-22
[QUOTE=mariuss]This is something I want to avoid, I would like to be only notified. Automatic installs and reboots are kind of dangerous IMHO.


Who is sending the email? I could not figure that from your script.

Thanks,
Marius[/QUOTE]


The e-mail is sent by cron to the root account on the box.  What I do is place a .foward in root's home and have it fowarded to my real e-mail address so I get the report weekly.

---

