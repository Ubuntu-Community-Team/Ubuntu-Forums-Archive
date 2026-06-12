---
title: "Anti theft / PC tracking / Remote mobile control solutions"
date: 2009-02-09
forum: Security
---

### Post by regstraton on 2009-02-09
I have recently set up my new ASUS Eee PC 901 Netbook with the EasyPeasy variant of Ubuntu 8.10. It all works brilliantly, and am loving it. I'm new to using linux as a desktop but already Ubuntu is my desktop OS of choice (never tied mac though).

One concern with these little portable devices is that their likelihood of being stolen is possibly even more than that for laptop computers. So apart from a good insurance, or acceptance that someday it'll no longer be yours, what can be done to improve the situation if/when such an event occurs:

[LIST=1]
[*]A way of tracking the NetBook.
[*]A way to remotely issue commands the NetBook - even if behind a NAT.
[*]Possibly use the built in webcam/mic to record the current user. 
[*]Some sort of emergency/self destruct script that runs if "something" hasn't happened within the past X days?? - though this is rather extreme and is likely to catch you out.
[/LIST]
So far I have a reasonable solution for 1) by using dynamic DNS. Below I detail how I setup *inadyn* to run as a deamon and continuously update the internet facing IP address of my NetBook. The reason why I chose to run it as a deamon rather than as a session is that it will then run whether or not a user is logged in.

Install inadyn:
```
sudo apt-get install inadyn
```

Create a init deamon init script called **/etc/init.d/inadyn** :
```

#!/bin/sh
#
# My little attempt at turning 'inadyn' DynDNS client into a daemon
#

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/inadyn
NAME=inadyn
DESC="Dynamic DNS Client (inadyn)"

INADYN_INPUT_FILE=/root/inadyn.conf

NO_START=0

set -e

cancel() { echo "$1" >&2; exit 0; };
test ! -r /etc/default/inadyn || . /etc/default/inadyn
test "$NO_START" = "0" || cancel 'NO_START is not set to zero.'
test -x "$DAEMON" || cancel "$DAEMON does not exist or is not executable."
test ! -h /var/service/inadyn || \
  cancel '/var/service/inadyn exists, service is controlled through runit.'

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start-stop-daemon --start --quiet --exec "$DAEMON" \
          -- --input_file $INADYN_INPUT_FILE --background --log_file /dev/null
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop --quiet --oknodo --exec "$DAEMON"
	echo "$NAME."
	;;
  restart|force-reload)
	echo -n "Restarting $DESC: "
	start-stop-daemon --stop --quiet --oknodo --exec "$DAEMON"
	sleep 1
	start-stop-daemon --start --quiet --exec "$DAEMON" \
          -- --input_file $INADYN_INPUT_FILE --background --log_file /dev/null
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|force-reload}" >&2
	exit 1
	;;
esac

exit 0
``` 

Setup a dynamic DNS account with a service provider such as [DynDNS]("http://www.dyndns.com/") and register a suitable URL, eg: *youralias.dyndns.info*


Create a config file for inadyn **/root/inadyn.conf** :
```

username 		yourusername
password 		yourpassword
alias			youralias.dyndns.info
update_period_sec 	300
```

Make the config file less readable:
```

$ sudo chmod 0700 /root/inadyn.conf
```


Setup the inadyn deamon:
```

$ sudo update-rc.d inadyn defaults 98 02
```

Start the inadyn deamon with:
```

$ sudo /etc/init.d/inadyn start
```

Now if your NetBook ever grows legs you can see where it is if is connected to the internet with:
```

$ nslookup youralias.dyndns.info
```

Potentially you can then pass this IP address and your NetBook's MAC address on to the authorities.

Further I am still mulling over ideas to achieve 2 and 3. Possibly one could place an empty command script out there on the internet. And then in the event that your NetBook is stolen the script could be updated to excecute something - though this would potentialy have to be run as root - which is a fairly large security hole. So perhaps just a flag to run a existing script.

I'd be interested to hear what other people have been thinking on this issue in general.

---

### Post by hyper_ch on 2009-02-09
if you're worried about the data, fully encrypt the system... I doubt that tracking will help get the notebook back.

---

