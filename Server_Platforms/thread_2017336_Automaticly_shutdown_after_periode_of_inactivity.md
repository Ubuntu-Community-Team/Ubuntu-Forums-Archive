---
title: "Automaticly shutdown after periode of inactivity"
date: 2012-07-05
forum: Server Platforms
---

### Post by Scripting22 on 2012-07-05
Hello,

I recently installed a Ubuntu server (12.04). I want this server to power off after a periode of inactivity.

I found already that the package pm-utils can be of some help, but couldn't find any good tutorial on how to configure it.

What I want is that the server shuts down after an hour of idle state. Does any1 know how to accomplish this?

Thanks in advance.

---

### Post by rubylaser on 2012-07-05
Here's a [thread]("http://ubuntuforums.org/showthread.php?t=530973") that covers a few working examples of a shutdown after a period of inactivity.

---

### Post by Scripting22 on 2012-07-05
Thanks for the reply. I tried the script which I found in the thread, but it doesn't work for me.

The inactivity in that script is based on user activity and my server almost always runs without any user logged in.

The second script is based on network activity. It measeures incoming and outgoing packet and I find this a uncertain way of measuring whether a server is used or not.

Would be much helped with another script which is based on some kind of system proces (tty input for example?). If someone knows how to do this or where I can find how to do this, it would be much appreciated.

---

### Post by rubylaser on 2012-07-05
> **Scripting22 said:**
> Thanks for the reply. I tried the script which I found in the thread, but it doesn't work for me.

The inactivity in that script is based on user activity and my server almost always runs without any user logged in.

The second script is based on network activity. It measeures incoming and outgoing packet and I find this a uncertain way of measuring whether a server is used or not.

Would be much helped with another script which is based on some kind of system proces (tty input for example?). If someone knows how to do this or where I can find how to do this, it would be much appreciated.

I'm not sure how you would base it on a daemon.  Those are intended to run constantly, and do have an "inactive" state.  They are either running or not.  What functions does your machine perform?  Maybe I can help you build a script around that.

Person based or network activity are about the two easiest and most obvious ways to do this, but if those aren't effective for you, you'll have to figure out a process you want to monitor.

---

### Post by Scripting22 on 2012-07-05
> **rubylaser said:**
> I'm not sure how you would base it on a daemon.  Those are intended to run constantly, and do have an "inactive" state.  They are either running or not.  What functions does your machine perform?  Maybe I can help you build a script around that.

Person based or network activity are about the two easiest and most obvious ways to do this, but if those aren't effective for you, you'll have to figure out a process you want to monitor.

Well, after some thinking I think I want to use the script based on network activity. The best thing to do would be to alter the script from the thread.

I will give it a try tonight or tomorrow morning. If you could give feedback on it, it would be great.

---

### Post by Scripting22 on 2012-07-05
Okay, here's the script with some alterations. I've changed the location where the log will be created, the treshold to 100 packets, and the end command from suspend to RAM, to shutdown. Corresponding echo messages I've changed also.

If I run this script every 30 minutes through CRON, will it shut down the system when it should be? The network activity exists merely of one ssh connection. When this connection isn't used, are there more than 100 packets per half an hour generated?

Edit: I tested it and after some changes in the paths it works good. Issuing a command through ssh connection generates about 5 to 10 packets, so if I'm actively using the ssh connection the server won't shut down.

Edit 2: Well, it works on an hourly bases now. Because it does not run when i put it in /etc/crontab. I think this is because in crontab I've to specify a user who runs the job (for the permissions), but no one is logged in, so the the job isn't executed at all?

Edit 3: The cronjob isn't working at all. When I just execute the command everything works fine. When I add the command to the crontab of root, nothing happens? There's even no output written to the logfile?

```
#!/bin/bash                                                                                                         
#                                                                                                                   
# This script is scheduled in CRON.  It will run every 30 minutes
# and check for network inactivity.  It compares the RX and TX packets
# from 30 minutes ago to detect if they significantly increased.
# If they haven't, it will force the system to shut down.
#

log=/home/wouter/scripts/poweroff_log

# Extract the RX/TX
rx=`/sbin/ifconfig eth0 | grep -m 1 RX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`
tx=`/sbin/ifconfig eth0 | grep -m 1 TX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`

#Write Date to log
date >> $log
echo "Current Values" >> $log
echo "rx: "$rx >> $log
echo "tx: "$tx >> $log

# Check if RX/TX Files Exist
if [ -f ~/Scripts/idle/rx ] || [ -f ~Scripts/idle/tx ]; then
        p_rx=`cat ~/Scripts/idle/rx`  ## store previous rx value in p_rx
        p_tx=`cat ~/Scripts/idle/tx`  ## store previous tx value in p_tx

        echo "Previous Values" >> $log
        echo "p_rx: "$p_rx >> $log
        echo "t_rx: "$p_tx >> $log

        echo $rx > ~/Scripts/idle/rx    ## Write packets to RX file
        echo $tx > ~/Scripts/idle/tx    ## Write packets to TX file

        # Calculate threshold limit
        t_rx=`expr $p_rx + 100`
        t_tx=`expr $p_tx + 100`

        echo "Threshold Values" >> $log
        echo "t_rx: "$t_rx >> $log
        echo "t_tx: "$t_tx >> $log
        echo " " >> $log

        if [ $rx -le $t_rx ] || [ $tx -le $t_tx ]; then  ## If network packets have not changed that much
                echo "Powering off ..." >> $log
                echo " " >> $log
                rm ~/Scripts/idle/rx
                rm ~/Scripts/idle/tx
                sudo /sbin/shutdown -h now  ## Shut down system
        fi

#Check if RX/TX Files Doesn't Exist
else
        echo $rx > ~/Scripts/idle/rx ## Write packets to file
        echo $tx > ~/Scripts/idle/tx
        echo " " >> $log
fi
```

---

