---
title: "Cron-ing some scripts doesn't work"
date: 2011-07-21
forum: Server Platforms
---

### Post by Italic_Rendezvous on 2011-07-21
Sorry for the monster post; it got out of the "brief" stage very quickly. I'll leave my other help topic for another thread.

Greetings, 

I'm relatively new to Linux, but over the last couple weeks I have learned much more than I had ever thought possible using Ubuntu Server 11.04 to create a game and web server.

One of my issues: I have created a multitude of scripts to update and start a dedicated game serve at startup and to reboot the server at midnight for it to update. However, not all of these scripts can be started by cron, while others will. That which can be run is: 
```
#!/bin/sh
echo "Starting Team Fortress 2"
echo ""
echo ""
/home/lvflag/srcds_l/orangebox/srcds_run -console -game tf -hostname "LV Flag" -hostport 27015 +maxplayers 12 +map ctf_2fort
```

I can launch this at startup using cron just fine, but what confuses me is the one that WON'T start with cron:
```
#!/bin/sh
echo "Updating Team Fortress 2"
echo ""
echo ""
/home/lvflag/srcds_l/steam -command update -game tf -dir /home/lvflag/srcds_l/
``` I can also use "-dir ." for the directory variable, but this gives it a definite destination, which I have had problems with earlier.

I can run each of these scripts with no issues manually. Both are executable by the user "lvflag" - neither are executed using root for any reason due to the game server's certain security flaws. 

Because I couldn't get the latter script to run with cron, I made a third script that executed both of them consecutively: 
```
#!/bin/sh
echo ""
/home/lvflag/scripts/update.sh&&/home/lvflag/scripts/start.sh
```
This is also perfectly executable manually, but when it comes to cron, it just won't do it. I try to use "crontab -e" to add these scripts at startup, but it won't run anything including the update script. Out of curiosity, I ran the update script as root once at startup, but also to no avail. I also thought it could be caused by the "-dir ." variable, but even after I changed it to a definite path, it still wouldn't start. 

Is there any reason cron shouldn't be executing said script at startup? Is the target of the script restricting it? Why would cron be selective of which scripts it runs? 

(If there are error logs, where can I find those? They might also point me in the right direction.)

Thank you all for providing such great forums. They have helped me get this far. -Italic

---

### Post by dethorpe on 2011-07-21
Not sure cron is the right thing, if you want stuff to run at startup then you should add an initd script or the users startup apps if you want them when the user logs on.
 
Cron is for running jobs on a reguler basis e.g. every min, hour, day or certain time of day.
 
If it is cron you want to use then the main gotcha that can cause this is that cron does not source the users login profile when it runs a job, unlike when you run it from a terminal. If your script needs this then source it specificly in the cron job or your script by adding ". ~/.bashrc" to run the contents of your bashrc file.
 
e.g for the cron job command
 
```
. ~/.bashrc; scriptname.sh
```
 
Cron by default norally emails the job output to the user, but can only do that if you have an email server setup (e.g. sendmail). So instead to capture the output and stderr redirect the script to a log file in the cron job command e.g.
 
```
 
scriptname.sh >> /home/lvflag/cron.log 2>&1 

```

---

### Post by ruffEdgz on 2011-07-21
I believe doing this during a cron startup should be ok but knowing more about your cronjobs can only help you and anyone else trying to help.

lets make sure you have cron logs running:
```

sudo <editor here> /etc/rsyslog.d/50-default.conf

```
You should see a line that looks like so:
```

cron.*                          /var/log/cron.log

```
Make sure its not commented out and save the file. Once saved, lets restart the rsyslog service:
```

sudo service rsyslog restart

```
Once complete, you should see a new file called /var/log/cron.log. You will have to wait until your machine restarts to grab additional information.

The additional suggestions from **dethorpe** can also help depending on if the commands need environment variables or if your want a personal log to go into your home dir.

---

### Post by CharlesA on 2011-07-21
I've got a script that starts tf2 via cronjob:

```
#!/bin/bash

echo "Starting TF2 Dedicated Server..."
$HOME/hlds/orangebox/srcds_run -game tf +map cp_badlands -autoupdate

```

In your case, you'd change hlds to srcds_1

That one is set to auto-update.

---

### Post by Italic_Rendezvous on 2011-07-21
Thank you to all of you for your quick responses; they're all very much appreciated. As for CharlesA: 
```
$HOME/hlds/orangebox/srcds_run -game tf +map cp_badlands -autoupdate
```

When does your script autoupdate it? Will it only update on startup, or will it automatically query the update servers, shut down, update and restart the server when Valve releases an update? If it auto-updates when the database is updated, I can takeout my daily midnight reboot and possibly save my box a bit of trouble. I didn't know about this startup variable, so this may be the most useful of all. I will try it and come back if it worked or not. 

As for those regarding cron itself, I will implement all that I can, whether I use it now or in the future. 

Again, thanks for being so quick on the subject; I've never seen forum users get back so quickly.

---

### Post by CharlesA on 2011-07-22
It updates when the script is run from what I've seen. I don't have the server running all the time so I'm not sure if it'll update on the fly or not.

EDIT: Found [something]("http://forums.steampowered.com/forums/showthread.php?t=877000") mentioning that it'll update during a mapchange, but I haven't tested it myself.

---

### Post by Italic_Rendezvous on 2011-07-24
Seems everything is working just as it should. It starts and updates at system boot, and I have it set to reboot the server at midnight for updating. I don't think it will update at mapchange, but I'm ok with it updating only once a day. Thanks for the input, everybody!

---

### Post by CharlesA on 2011-07-24
Glad it worked out for you. :)

---

