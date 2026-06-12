---
title: "Webmin Cronjob Problem"
date: 2013-01-19
forum: Server Platforms
---

### Post by wydchr on 2013-01-19
I have created a cronjob in Webmin to powerdown my NAS server everyday at 23:50 but it does not execute. The only command I have entered is 'poweroff' (having initially tried 'shutdown -h +0') as a root user, I tried it but nothing happens. Can anyone please help me with this simple (or so I thought) task, thanks in advance.

David

---

### Post by cariboo on 2013-01-20
Moved to Server Platforms.

---

### Post by chrisguk on 2013-01-20
Hi and welcome.

Firslty, Im not a great fan of Webmin.  

My advice is find out what the desired results are using the command line first before messing with Applications to automate the process.

Are you looking for just a power down and reboot?

If so why not just use the already well used Crobtab function.  You can adjust the times and location of the script as you please.

So to enter the cron job just do the following:

```
sudo mkdir /usr/local/sbin/daily.active
```



Next, let's create the daily script (it is very nearly identical to the other two scripts). Type:

```

sudo nano /usr/local/sbin/daily.sh


```

and paste or type in the following:
```

Code:
#!/bin/bash

ACTIVE_SCRIPTS_DIR=/usr/local/sbin/daily.active

for module in `find "$ACTIVE_SCRIPTS_DIR" -maxdepth 1 -mindepth 1 -type f`; do
	if [ -x $module ]; then
		$module
	fi
done


```
save and close the file.

Change its permissions to make it executable:
```

sudo chmod u+x /usr/local/sbin/daily.sh


```

the open crontab:

```
sudo crontab -e
```

place this inside it:

```
30 23 * * * /usr/local/sbin/daily.sh
```

Next lets create a shutdown script:

create this in your home folder first to ensure it works


Test the scripts:

Create a new script in your home directory called reboot.sh:
```

sudo pico ~/reboot.sh
and paste or type the following into it:
Code:
#!/bin/bash

sudo reboot now

echo "system reboot completed" | mail -s "test of the reboot script" youremail@yourdomain.com

#Note: you will want to change the email to actually point to your correct email address.

```

Save and close the file.

change its permissions so that it is executable:

```

sudo chmod u+x ~/reboot.sh

```
and test it by typing:
```

sudo ~/reboot.sh

```

You should receive an email with the subject: test of the reboot scripts

If that worked, move the script into your /usr/local/sbin/daily.active directory:

```

sudo mv ~/reboot.sh /usr/local/sbin/daily.active/reboot.sh

```

---

### Post by wydchr on 2013-01-21
@chrisguk, thanks for the reply.

I went through your instructions and when I entered crontab -e there was my original shutdown instruction - 30 23 * * * shutdown -h now #Daily shutdown. so why was this command was not being executed or am I not understanding the cron philosophy properly. Please excuse my ignorance I am quite new to Linux.

Your script worked fine BTW
cheers, David.

---

### Post by Cheesehead on 2013-01-21
> **wydchr said:**
> I went through your instructions and when I entered crontab -e there was my original shutdown instruction - 30 23 * * * shutdown -h .

That seems like a user-level cron job, not a root cron job.
Users don't have permission to use that command.

---

### Post by wydchr on 2013-01-21
Hmm, but I set it as a root command but maybe you're right as nothing keeps on happening with it whatever it is set as.

---

