---
title: "Can I run a shell script in the background?"
date: 2008-08-05
forum: Server Platforms
---

### Post by PryGuy on 2008-08-05
Hello there and sorry for the lame question, but I have the following problem, I got a VPN script that runs on my server and I have to make something to check periodically whether the the connection is still up and invoke the script if it's not. So the question is, is that possible to write a script that would run as a daemon in the background? Sorry for the silly question again.

---

### Post by cdenley on 2008-08-05
This isn't really the correct way to do it, but I usually just start it in /etc/rc.local
```

/path/to/myscript&
exit 0

```

---

### Post by spin2cool on 2008-08-05
Here's a simple bash script that will work.  Insert the name of the vpn command you need to run and change the 'sleep' line to set the number of seconds it will wait before checking again.

```

#!/bin/bash
#
# takes one argument - name of running process
# (example 'emacs' or 'trackerd')

while true
do    
    if [ -z $(pgrep "$1") ]
    then
        <insert script to run here>
    fi
    sleep 5
done

```

Alternately, remove the while loop/sleep statements and just set cron to run the script every so often.

---

### Post by finer recliner on 2008-08-05
make your script run periodically using cron (scheduler)

---

### Post by c2olen on 2008-08-05
What exactly will be the purpose of this script?

If you are using openVPN, the daemon can reconnect by itself automatically, in case this would be the purpose of the script.

Otherwise, you could do

```

nohup pathtoscript > /logfile_somewhere 2>&1 &

```

nohup is actually "No Hangup". This will make sure the script keeps running, even if you close your session. The ampersand (&) at the end, will start it in the background.
Next, it makes sense to log it somewhere for troubleshooting or accounting purposes.

---

### Post by cdtech on 2008-08-05
Sure, you could write a script to check whatever it is you want to check, maybe using the "if &{myvariable} != &{myothervariable}; then" and use cron to run the script however often you want......

---

### Post by PryGuy on 2008-08-05
Hmmm, I'm really confused... So many answers... Thank you, people! Will give thanks to all of ya! ;)

---

### Post by c2olen on 2008-08-05
> **PryGuy said:**
> Hmmm, I'm really confused... So many answers... Thank you, people! Will give thanks to all of ya! ;)


Thank you for that, but did you solve your problem?

---

