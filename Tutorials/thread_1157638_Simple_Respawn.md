---
title: "Simple Respawn"
date: 2009-05-12
forum: Tutorials
---

### Post by josefnpat on 2009-05-12
So when a service goes down, like apache2, etc, we want it to restart. So we use monit etc. But what happens when you simply want to respawn some GUI app when it closes, like conky or linuxdcpp?

I googled. googled and googled. Nada, zip. Wrote this script, hope it helps anyone that needs a simple solution to a simple problem.

For those of you running gnome:
[System]->[Prefrences]->[Sessions]->
Startup Programs (Tab), Add (button), and under your command:

sh /path/to/script/respawn.sh [program name] [sleeptime]

so maybe:

~/scripts/respawn.sh conky 10

And now for the code.

respawn.sh:
```
#!/bin/bash

# This script is a simple respawn deamon for those of us who dont want
# to deal with the /etc/event.d, monit etc...
# Usage: sh respawn.sh [program] [sleep time]

while [ true ]
do
	sleep $2
	if ps ax | grep -v grep | $1 > /dev/null
	then
		echo $1": Stopped. Restarting in "$2" seconds."
	else
		$1 &
	fi
done

```

---

### Post by jpeddicord on 2009-05-13
Approved. Thank you for your tutorials & tips submission.

---

### Post by petesimon on 2013-01-06
Thanks! :p I needed a way to respawn a service which is normally started by a debian style script in /etc/init.d during boot because I think there is no builtin way to respawn processes ... unless I convert the script to an Ubuntu upstart job but that's too much hassle. I changed and added some things to your script to suite my tastes.

**By the way, _is there_ a clause or directive I can put into a debian script such as /etc/init.d/vncserver to poll the running process and restart it if it stops?**

```

#!/bin/bash
# This script is a simple respawn daemon for those of us who dont want
# to deal with the /etc/event.d, monit etc...
#
# file: respawn.sh
# usage: /path/respawn.sh [program name] [sleeptime] 
#
# the next example will start and respawn a text
# editor after a 5 seconds delay when it closes
# example: /path/respawn.sh gnome-text-editor 5
#
# when the program closes, logger will display a message in a terminal
# and log the message including the programs PID to the syslog service
# (see file /var/log/syslog)


if [ "$1" == "" ] || [ "$2" == "" ]; then
  echo error: not enough parameters given.
  echo usage: respawn.sh [program name] [sleep time]
  exit 1
fi

PNAME=$1
STIME=$2

while [ true ]

do
	sleep $STIME
	if ps ax | grep -v grep | $PNAME > /dev/null
	then
		logger -i -s -t respawn.sh "$PNAME stopped. Restarting in $STIME seconds."
	else
		$PNAME &
	fi
done

```

---

