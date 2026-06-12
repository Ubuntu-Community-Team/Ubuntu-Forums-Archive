---
title: "how to use /etc/cron.d?"
date: 2011-03-17
forum: Server Platforms
---

### Post by nbv4 on 2011-03-17
I have this symlinked into my /etc/cron.d folder:

```

*/5 * * * * python /srv/bidsite/manage.py send_mail
  * * * * * echo `date` >> /home/bidsite/what.txt

```

but it does nothing. Anyone know why? What I really want to happen is the first line. The second line is just for testing.

---

### Post by BkkBonanza on 2011-03-17
The sub-directories cron.* linked to cron.d and are for putting scripts to run at hourly, daily, weekly, monthly intervals. You can put links to scripts in there.

But what you have posted is not a script. It is cron lines that should not be used this way. These lines need to be entered into a crontab file. You do this by using the special edit command,

crontab -e

Then paste in the lines to the editor that starts up.
Then save. Now the lines are active. You can list your current crontab using,

crontab -l

Note that this crontab is user specific so if you do as above then cron will run them as YOUR user. If you need them to run as root then you need to put sudo in front of the crontab command.

---

### Post by nbv4 on 2011-03-17
> **BkkBonanza said:**
> The sub-directories cron.* linked to cron.d and are for putting scripts to run at hourly, daily, weekly, monthly intervals. You can put links to scripts in there.

But what you have posted is not a script. It is cron lines that should not be used this way. These lines need to be entered into a crontab file. You do this by using the special edit command,

crontab -e

Then paste in the lines to the editor that starts up.
Then save. Now the lines are active. You can list your current crontab using,

crontab -l

Note that this crontab is user specific so if you do as above then cron will run them as YOUR user. If you need them to run as root then you need to put sudo in front of the crontab command.

Oh I see. The problem is that the above file is in a git repository, and it needs to be symlinked into cron, so we can update the repo and have the changes cascade. Is that possible with cron?

---

### Post by BkkBonanza on 2011-03-17
If you don't want to cut/paste the contents then you can use the form,

crontab /path/to/the/file

This will copy that file into the /var/spool/cron/crontabs/ directory with the username as filename. 

It is probably possible to place a file directly in there but it's not recommended as the crontab program does syntax checking and controls permissions and other settings to ensure correct operation. If you just copied it in you could end up with problems.

Even if you could directly symlink the python script to cron.d there is no way to set 5 minute intervals as that you have in the crontab. If the script is updated from a repo then it's changes will be used, but if the cron interval (5 minutes) were changed that would need to be updated with crontab.

You can read all about this with **man crontab**.

---

