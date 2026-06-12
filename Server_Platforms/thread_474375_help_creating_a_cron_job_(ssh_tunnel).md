---
title: "help creating a cron job (ssh tunnel)"
date: 2007-06-15
forum: Server Platforms
---

### Post by dmizer on 2007-06-15
i need to establish and keep alive a reverse ssh tunnel.  but i only want to do this over the weekend.  i need to establish the connection late friday night, and terminate the connection late sunday night.

here is the script i'm using to establish the connection:
```

#!/bin/sh

# $REMOTE_HOST is the name of the remote system
REMOTE_HOST=my.home.system

# $REMOTE_PORT is the remote port number that will be used to tunnel
# back to this system
REMOTE_PORT=5000

# $COMMAND is the command used to create the reverse ssh tunnel
COMMAND="ssh -N -R $REMOTE_PORT:localhost:22 $REMOTE_HOST"

# Is the tunnel up? Perform two tests:

# 1. Check for relevant process ($COMMAND)
pgrep -f -x "$COMMAND" || $COMMAND

# 2. Test tunnel by looking at "netstat" output on $REMOTE_HOST
ssh $REMOTE_HOST netstat -an | egrep "tcp.*:$REMOTE_PORT.*LISTEN" \
   > /dev/null 2>&1
if [ $? -ne 0 ] ; then
   pkill -f -x "$COMMAND"
   $COMMAND
fi
```
pulled from this page: [http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

now, what i need help with is how to configure cron to make this both activate and terminate during the times when i need.

---

### Post by Mr. C. on 2007-06-15
You can either have the script run at midnight Friday, and kill itself in 48 hours (sleep, followed by kill), or you can have a start script and a stop script where the start script runs Friday, the stop script runs late Sunday (early monday am).  The later is easier to generalize and control:

A crontab entry might look like:

$ crontab -l
# start at 11:30pm Friday
30 23   * * 5    startsshtunnel > /dev/null 2>&1
# stop at 2am Monday
0 2       * * 0    stopsshtunnel > /dev/null 2>&1

You mention maintaining the connection.  You will need something to watch for the connection being dropped, and to reestablish it if it fails.

Be careful of the pkill, immediately followed by starting the job again.  pkill just sends a signal, and the pkill program can return *before the signal is delivered*.  This means that your command could fail, due to the network socket still being in use.

MrC

---

### Post by dmizer on 2007-06-15
well ... my problem now is how to stop it.  it seems that if i terminate the script, the tunnel is still active.

---

### Post by Mr. C. on 2007-06-15
Right, you need to kill the SSH server **instance** that is managing the connection, or its child shell.

MrC

---

### Post by dmizer on 2007-06-22
okay ... i still need some help with this.  scripting is far out of my reach at this point.

1) how can i terminate the connection?
2) how can i monitor the connection and reestablish if it gets disconnected?

edit:
okay ... i figured out how to start it and terminate it at the desired times.  now i just need to figure out how to monitor the connection.

---

### Post by gaten on 2007-06-22
> now i just need to figure out how to monitor the connection.

The only thing I could think of would be to monitor the output of maybe tcpdump (which obviously watches the port in question). Once data stops going through it, restart the process. 

Or perhaps you could just do a periodic nmap scan of the host, and if port xx isn't open, then the process stopped etc..

Just an idea

---

### Post by dmizer on 2007-06-23
well ... my problem is not with determining if the connection is active or not.  the above posted script does that.

my problem is how to manage the script or monitor the connection only during weekends, and not during weekdays.

---

### Post by gaten on 2007-06-23
OK, maybe I'm confused but can't that be done with a cron job?

---

### Post by dmizer on 2007-06-23
i suspect i will have to make use of crontab, but i really don't know how to apply it.

using crontab ... how can i make a script start on saturday at 3am, then repeatedly execute every 30 minutes or hour or so, and terminate on monday morning 3am?

---

### Post by gaten on 2007-06-23
> 
using crontab ... how can i make a script start on saturday at 3am, then repeatedly execute every 30 minutes or hour or so, and terminate on monday morning 3am?

I'm no expert on cron, so I'm thinking you'll be needing 3 scripts. Something like this:

Script 1: Your "startssh" script. This would start the script and make sure its working and such. Run this on Sat at 3am.

Script 2: Your "monitor" script. Checks to make sure the tunnel is up and whatnot. Run this every 30 mins on Sat + Sun.

Script 3: You "stopall" script. Kills the tunnel and the monitor script. 
Run this Mon at 3am.

So, crontab might look like this:

```

# m h dom mon dow user  command
* 3 * * Sat   ssh    sh script1
30 * * * Sat,Sun   ssh    sh script2
* 3 * * Mon   ssh    sh script3

```


Although, with that it won't be monitored for 3 hours on monday morning. You might want to create another crontab entry for that. 

I know it's messy, but its the best I can do with 15 minutes of thought ;)

Hope that helps.

---

### Post by dmizer on 2007-06-23
wouldn't this line:
```
30 * * * Sat,Sun   ssh    sh script2
```
only run the script twice ... once at 0:30 on saturday, and once at 0:30 on sunday?

---

### Post by gaten on 2007-06-23
No, look at the /etc/crontab entry for the hourly run, only the minute field is set, the rest are *. 

> only run the script twice ... once at 0:30 on saturday, and once at 0:30 on sunday?

Then entry for that would look like
```
30 0 * * Sat,Sun   ssh    sh script2
```

I think ;)

---

### Post by dmizer on 2007-06-23
well, i had to play quite a bit ... but here's the functional line:
```
0,30 * * * 0,6 ssh sshtunnel.sh
```

not exactly what i had in mind because it only gives me access between midnight friday night/saturday morning until midnight sunday night/monday morning but it's better than nothing, and it will do.

---

### Post by gaten on 2007-06-23
```
0,30 * * * 0,6 ssh sshtunnel.sh
```

Isn't 0,6 Monday and Saturday only? Sunday is 7, I don't know if something like 6-0 will work (Sat - Mon), but crontab DOES support ranges. But glad you have an acceptable solution.

---

### Post by dmizer on 2007-06-23
well, the documentation i read indicated that 0 is sunday and 6 would be saturday, and it appears to be working correctly on the correct days.

i tried 6-0 at one point, but it didn't seem to work.

also, if i don't make use of the tunnel, it seems to time out after about 10 minutes, so i had to increase the increments.

i can't figure out any way to include only part of a day, so at least for the time being this will have to be satisfactory.

---

### Post by gaten on 2007-06-23
> well, the documentation i read indicated that 0 is sunday and 6 would be saturday, and it appears to be working correctly on the correct days.

Yep you were right, my bad. I didn't see that 0 AND 7 are Sunday.

> i tried 6-0 at one point, but it didn't seem to work.
Meh.

> also, if i don't make use of the tunnel, it seems to time out after about 10 minutes, so i had to increase the increments.
Did you read the ssh docs for a --timeout option or something similar? There is a **ConnectionTimeout** option is /etc/ssh/ssh_config.

> i can't figure out any way to include only part of a day, so at least for the time being this will have to be satisfactory.

Except for adding an entry specifically for monday:
```
* 0-3 * * 1 ssh sshtunnel.sh
```

I can;t think of anything either.

---

### Post by dmizer on 2007-06-24
thank you so much for your help.  i've entered the additional line as you've suggested, and i should be able to test it tonight.

according to the docs (which i did look at), the ConnectTimeout option is for the initial connection attempt, and is only used in cases when the server is down.

the only other option i can see that would effect this would be on the server side in sshd_conf under the option "KeepAlive" ... but it is already set to "yes" as per default.

anyway ... the problem was easily solved by increasing the frequency of the script.

---

### Post by gaten on 2007-06-24
No problem, glad I could help. Hope everything works out for ya, good luck.

---

### Post by dmizer on 2007-06-24
the additional line:
```
* 0-3 * * 1 ssh sshtunnel.sh
```
did nothing.  i'm going in to the client location today, and i'll post any errors if i see them.

any other ideas?

---

### Post by gaten on 2007-06-24
> the additional line:
 	Code:
 	* 0-3 * * 1 ssh sshtunnel.sh 
did nothing.  i'm going in to the client location today, and i'll post any errors if i see them.

any other ideas?

It should, assuming that there IS an ssh user, and you've included the path to sshtunnel.sh. You might also try
```
sh /path/to/sshtunnel.sh
```

Also, look in /var/log/syslog for errors from cron
```
cat /var/log/syslog|grep -i cron
```

Also, those lines I specified were for the system crontab, NOT individual user crontabs (the system one is the only crontab with the user field), so just making sure.

---

### Post by Mr. C. on 2007-06-24
If you edited the crontab file manually, you will have to restart cron.  If you used crontab -e, no need to restart cron.

MrC

---

### Post by dmizer on 2007-06-24
> **Mr. C. said:**
> If you edited the crontab file manually, you will have to restart cron. 
doh ...

you know, by now i should really know better than that.

---

