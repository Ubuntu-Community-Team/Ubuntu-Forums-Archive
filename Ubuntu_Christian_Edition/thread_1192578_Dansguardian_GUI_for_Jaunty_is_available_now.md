---
title: "Dansguardian GUI for Jaunty is available now"
date: 2009-06-20
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-06-20
I have managed to make a deb package of Dansguardian GUI, it will help you to do as follow:

1. Automatically configure dansguardian, firehol and tinyproxy
2. Manage dansguardian including filter level ( young children, old children, or young adult)
3. Lock and unlock firefox proxy, it will auto detect your firefox version.
4. It also show status of dansguardian, filter and firefox proxy on title box.

Just download dansguardian gui from this website:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/](http://ubuntuce.com/repos/Ubuntu_CE/binary/)

and install it. 


Launch the script from System > Administration > Dansguardian GUI, and follow the instruction there.

You will need to key in your password in terminal.

Hopefully it works for you.

DK

---

### Post by david_kt on 2009-06-24
I have improved and added new feature to the dansguardian-gui:

1. filter setting now include a slide bar, to choose from 50 (strict) to 160 (less strict). You could pick any number in between.
2. Added advance setting, to edit blacklist and whitelist.

Recently I found websctrict, which is dansguardian GUI for Ubuntu ME. The comparison of websctrict and dansguardian-gui are as follow:

websctrict advantage:
1. Very beautiful user interface
2. Easily ported (based on java)

Webstrict disadvantage:
1. bloated (pull more than 100 MB of software package, installed size should much more than that).
2. Not suitable for older machine, as it based on java (resource hungry).

dansguardian-gui advantage:
1. Small (only 18.5 kb !!!)
2. Could do all things that webstrict could do.
3. Include auto configuration for beginners, no need to configure anything, all work out of the box.
4. Mostlikely will survive any upgrade as it just based on zenity and perl. 

dansguardian-gui disadvantage:
1. the gui not so beautiful
2. It will pull more software (zenity) if run on kde or other desktop environment.

DK

---

### Post by mnavasuk on 2009-07-03
Just been directed from post 7555432.
Thanks you for this work. I'll give it a try in Ubuntu later and post results.

---

### Post by mnavasuk on 2009-07-05
I should have mentioned that after installation, I did do:
 "Autoconfigure/reset Firehol Dansguardian Tinyproxy". I just done it again and the output is:
mkdir: cannot create directory `/home/<mylogin>/.cache': File exists
[sudo] password for <mylogin>:
grep: /usr/lib/firefox-3.0.11/firefox.cfg: No such file or directory
* Stopping DansGuardian dansguardian [ OK ]
* Stopping Firewall firehol

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana.sh script to generate this file.

[ OK ]
Stopping tinyproxy: tinyproxy.
Starting tinyproxy: tinyproxy.
* Starting Firewall firehol

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana.sh script to generate this file.

[ OK ]
* Starting DansGuardian dansguardian Error connecting to parent proxy
[fail]
grep: /usr/lib/firefox-3.0.11/firefox.cfg: No such file or directory

Still no internet, but internet is back if I stop Firehol.
Now the curious thing is that from my previous attempt to install the webcontent control script (which failed), it left on the menu an entry for "Webcontent control" under applications > system tools. I can launch it, and shows that Firehol is on, Tinyproxy is off and Dansguardian is off.
If I attempt to turn Tinyproxy on from it by clicking on the tinyproxy button, the output stops at "Starting tinyproxy, tinyproxy"
I'll keep looking, any ideas would be great.
Thanks.

---

### Post by david_kt on 2009-07-05
[QUOTE=mnavasuk;7566631
If I attempt to turn Tinyproxy on from it by clicking on the tinyproxy button, the output stops at "Starting tinyproxy, tinyproxy"
I'll keep looking, any ideas would be great.
Thanks.[/QUOTE]

For some reason tinyproxy could not start. Could you attached below file:

/etc/tinyproxy/tinyproxy.conf
and
/etc/init.d/tinyproxy

But maybe you would not able to find /etc/init.d/tinyproxy as I suspect webcontentcontrol or previous dansguardian gui remove/edited /etc/init.d/tinyproxy so that it could not start.

DK

---

### Post by mnavasuk on 2009-07-06
Thanks for your help david_kt.
I'll do just that later when I'm home.

---

### Post by mnavasuk on 2009-07-06
> **david_kt said:**
> For some reason tinyproxy could not start. Could you attached below file:

/etc/tinyproxy/tinyproxy.conf
and
/etc/init.d/tinyproxy

But maybe you would not able to find /etc/init.d/tinyproxy as I suspect webcontentcontrol or previous dansguardian gui remove/edited /etc/init.d/tinyproxy so that it could not start.

DK
I can't upload the files. I'll have to paste the contents.
Let me know what you think.

---

### Post by mnavasuk on 2009-07-06
Contents of /etc/init.d/tinyproxy:
#! /bin/sh
#
# Tinyproxy init.d script
# Ed Boraas 1999
# 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/tinyproxy
NAME=tinyproxy
DESC=tinyproxy
FLAGS=
if [ -r /etc/default/tinyproxy ]
then
    . /etc/default/tinyproxy
fi

test -f $DAEMON || exit 0

set -e

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start-stop-daemon --start --quiet -o --exec $DAEMON -- $FLAGS
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop --quiet -o --exec $DAEMON
	echo "$NAME."
	;;
  reload|force-reload)
	 echo "Reloading $DESC configuration files."
	 start-stop-daemon --stop --signal 1 --quiet -o --exec $DAEMON
	;;
  restart)
	echo -n "Restarting $DESC: "
	start-stop-daemon --stop --quiet -o --exec $DAEMON
	sleep 1
	start-stop-daemon --start --quiet -o --exec $DAEMON -- $FLAGS
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	exit 1
	;;
esac

exit 0

---

### Post by mnavasuk on 2009-07-06
Contents of /etc/tinyproxy/tinyproxy.conf:
##
## tinyproxy.conf -- tinyproxy daemon configuration file
##

#
# Name of the user the tinyproxy daemon should switch to after the port
# has been bound.
#
User root
Group root

#
# Port to listen on.
#
Port 3128

#
# If you have multiple interfaces this allows you to bind to only one. If
# this is commented out, tinyproxy will bind to all interfaces present.
#
#Listen 192.168.0.1

#
# The Bind directive allows you to bind the outgoing connections to a
# particular IP address.
#
#Bind 192.168.0.1

#
# Timeout: The number of seconds of inactivity a connection is allowed to
# have before it closed by tinyproxy.
#
Timeout 600

#
# ErrorFile: Defines the HTML file to send when a given HTTP error
# occurs.  You will probably need to customize the location to your
# particular install.  The usual locations to check are:
#   /usr/local/share/tinyproxy
#   /usr/share/tinyproxy
#   /etc/tinyproxy
#
# ErrorFile 404 "/usr/share/tinyproxy/404.html"
# ErrorFile 400 "/usr/share/tinyproxy/400.html"
# ErrorFile 503 "/usr/share/tinyproxy/503.html"
# ErrorFile 403 "/usr/share/tinyproxy/403.html"
# ErrorFile 408 "/usr/share/tinyproxy/408.html"

# 
# DefaultErrorFile: The HTML file that gets sent if there is no
# HTML file defined with an ErrorFile keyword for the HTTP error
# that has occured.
#
DefaultErrorFile "/usr/share/tinyproxy/default.html"

#
# StatFile: The HTML file that gets sent when a request is made
# for the stathost.  If this file doesn't exist a basic page is
# hardcoded in tinyproxy.
#
StatFile "/usr/share/tinyproxy/stats.html"

#
# Where to log the information. Either LogFile or Syslog should be set,
# but not both.
#
Logfile "/var/log/tinyproxy.log"
# Syslog On

#
# Set the logging level. Allowed settings are:
#	Critical	(least verbose)
#	Error
#	Warning
#	Notice
#	Connect		(to log connections without Info's noise)
#	Info		(most verbose)
# The LogLevel logs from the set level and above. For example, if the LogLevel
# was set to Warning, than all log messages from Warning to Critical would be
# output, but Notice and below would be suppressed.
#
LogLevel Info

#
# PidFile: Write the PID of the main tinyproxy thread to this file so it
# can be used for signalling purposes.
#
PidFile "/var/run/tinyproxy/tinyproxy.pid"

#
# Include the X-Tinyproxy header, which has the client's IP address when
# connecting to the sites listed.
#
#XTinyproxy mydomain.com

#
# Turns on upstream proxy support.
#
# The upstream rules allow you to selectively route upstream connections
# based on the host/domain of the site being accessed.
#
# For example:
#  # connection to test domain goes through testproxy
#  upstream testproxy:8008 ".test.domain.invalid"
#  upstream testproxy:8008 ".our_testbed.example.com"
#  upstream testproxy:8008 "192.168.128.0/255.255.254.0"
#
#  # no upstream proxy for internal websites and unqualified hosts
#  no upstream ".internal.example.com"
#  no upstream "www.example.com"
#  no upstream "10.0.0.0/8"
#  no upstream "192.168.0.0/255.255.254.0"
#  no upstream "."
#
#  # connection to these boxes go through their DMZ firewalls
#  upstream cust1_firewall:8008 "testbed_for_cust1"
#  upstream cust2_firewall:8008 "testbed_for_cust2"
#
#  # default upstream is internet firewall
#  upstream firewall.internal.example.com:80
#
# The LAST matching rule wins the route decision.  As you can see, you
# can use a host, or a domain:
#  name     matches host exactly
#  .name    matches any host in domain "name"
#  .        matches any host with no domain (in 'empty' domain)
#  IP/bits  matches network/mask
#  IP/mask  matches network/mask
#
#Upstream some.remote.proxy:port

#
# This is the absolute highest number of threads which will be created. In
# other words, only MaxClients number of clients can be connected at the
# same time.
#
MaxClients 100

#
# These settings set the upper and lower limit for the number of
# spare servers which should be available. If the number of spare servers
# falls below MinSpareServers then new ones will be created. If the number
# of servers exceeds MaxSpareServers then the extras will be killed off.
#
MinSpareServers 5
MaxSpareServers 20

#
# Number of servers to start initially.
#
StartServers 10

#
# MaxRequestsPerChild is the number of connections a thread will handle
# before it is killed. In practise this should be set to 0, which disables
# thread reaping. If you do notice problems with memory leakage, then set
# this to something like 10000
#
MaxRequestsPerChild 0

#
# The following is the authorization controls. If there are any access
# control keywords then the default action is to DENY. Otherwise, the
# default action is ALLOW.
#
# Also the order of the controls are important. The incoming connections
# are tested against the controls based on order.
#
Allow 127.0.0.1
#Allow 192.168.0.0/16
#Allow 172.16.0.0/12
#Allow 10.0.0.0/8

#
# The "Via" header is required by the HTTP RFC, but using the real host name
# is a security concern.  If the following directive is enabled, the string
# supplied will be used as the host name in the Via header; otherwise, the
# server's host name will be used.
#
ViaProxyName "tinyproxy"

#
# The location of the filter file.
#
#Filter "/etc/tinyproxy/filter"

#
# Filter based on URLs rather than domains.
#
#FilterURLs On

#
# Use POSIX Extended regular expressions rather than basic.
#
#FilterExtended On

#
# Use case sensitive regular expressions.
#                                                                         
#FilterCaseSensitive On     

#
# Change the default policy of the filtering system.  If this directive is
# commented out, or is set to "No" then the default policy is to allow
# everything which is not specifically denied by the filter file.
#
# However, by setting this directive to "Yes" the default policy becomes to
# deny everything which is _not_ specifically allowed by the filter file.
#
#FilterDefaultDeny Yes

#
# If an Anonymous keyword is present, then anonymous proxying is enabled.
# The headers listed are allowed through, while all others are denied. If
# no Anonymous keyword is present, then all header are allowed through.
# You must include quotes around the headers.
#
#Anonymous "Host"
#Anonymous "Authorization"

#
# This is a list of ports allowed by tinyproxy when the CONNECT method
# is used.  To disable the CONNECT method altogether, set the value to 0.
# If no ConnectPort line is found, all ports are allowed (which is not
# very secure.)
#
# The following two ports are used by SSL.
#
ConnectPort 443
ConnectPort 563

---

### Post by david_kt on 2009-07-06
> **mnavasuk said:**
> Contents of /etc/init.d/tinyproxy:
#! /bin/sh
#
# Tinyproxy init.d script
# Ed Boraas 1999
# 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/tinyproxy
NAME=tinyproxy
DESC=tinyproxy
FLAGS=
if [ -r /etc/default/tinyproxy ]
then
    . /etc/default/tinyproxy
fi

test -f $DAEMON || exit 0

set -e

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start-stop-daemon --start --quiet -o --exec $DAEMON -- $FLAGS
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop --quiet -o --exec $DAEMON
	echo "$NAME."
	;;
  reload|force-reload)
	 echo "Reloading $DESC configuration files."
	 start-stop-daemon --stop --signal 1 --quiet -o --exec $DAEMON
	;;
  restart)
	echo -n "Restarting $DESC: "
	start-stop-daemon --stop --quiet -o --exec $DAEMON
	sleep 1
	start-stop-daemon --start --quiet -o --exec $DAEMON -- $FLAGS
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	exit 1
	;;
esac

exit 0

Replace /etc/init.d/tinyproxy with below:

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          tinyproxy
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Tinyproxy HTTP proxy
# Description:       Start, stop or reload tinyproxy.
### END INIT INFO
#
# Tinyproxy init.d script
# Ed Boraas 1999
# 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
CONFIG=/etc/tinyproxy/tinyproxy.conf
DAEMON=/usr/sbin/tinyproxy
DESC=tinyproxy
FLAGS=
NAME=tinyproxy

if [ -r /etc/default/tinyproxy ]; then
    . /etc/default/tinyproxy
fi

test -f $DAEMON || exit 0

set -e

# assert pidfile directory and permissions
if [ "$1" != "stop" ] ; then
    USER=$(grep    -i '^User[[:space:]]'    "$CONFIG" | awk '{print $2}')
    GROUP=$(grep   -i '^Group[[:space:]]'   "$CONFIG" | awk '{print $2}')
    PIDFILE=$(grep -i '^PidFile[[:space:]]' "$CONFIG" | awk '{print $2}' | \
      sed -e 's/"//g')
    PIDDIR=`dirname "$PIDFILE"`
    if [ "$PIDDIR" -a "$PIDDIR" != "/var/run" ] ; then
	if [ ! -d "$PIDDIR" ] ; then
	    mkdir "$PIDDIR"
	fi
	if [ "$USER" ] ; then
	    chown "$USER" "$PIDDIR"
	fi
	if [ "$GROUP" ] ; then
	    chgrp "$GROUP" "$PIDDIR"
	fi
    fi
fi

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start-stop-daemon --start --quiet -o --exec $DAEMON -- $FLAGS
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop --quiet -o --exec $DAEMON
	echo "$NAME."
	;;
  reload|force-reload)
	 echo "Reloading $DESC configuration files."
	 start-stop-daemon --stop --signal 1 --quiet -o --exec $DAEMON
	;;
  restart)
	echo -n "Restarting $DESC: "
	start-stop-daemon --stop --quiet -o --exec $DAEMON
	sleep 1
	start-stop-daemon --start --quiet -o --exec $DAEMON -- $FLAGS
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	exit 1
	;;
esac

exit 0
```

And then open dansguardian gui and start dansguardian. If successfull, you will see the status of dansguardian on the title box as "dansguardian enable". Otherwise it will inform you as dansguardian disable".

DK

---

### Post by mnavasuk on 2009-07-07
Hi DK.
I've just replaced the tinyproxy.conf file (after backing up) and restarted dansguardian as suggested.
Got this:
Starting tinyproxy: Errors in configuration file:
	/etc/tinyproxy/tinyproxy.conf:16: syntax error
 * Starting Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana.sh script to generate this file.

                                                                         [ OK ]
 * Starting DansGuardian dansguardian                                           Error connecting to parent proxy
                                                                         [fail]
grep: /usr/lib/firefox-3.0.11/firefox.cfg: No such file or directory

I'm having a look at line 16, see if I can spot the problem.

---

### Post by mnavasuk on 2009-07-07
by the way, after replacing the file, I also changed owner and group to root, just in case was necessary.
And I can't tell what the syntax error is. My bash programming knowledge is nil.
I'll keep looking...
Thanks.

---

### Post by david_kt on 2009-07-07
> **mnavasuk said:**
> 
Starting tinyproxy: Errors in configuration file:
	/etc/tinyproxy/tinyproxy.conf:16: syntax error


I could not spot the problem as well. What you could do is:

1. sudo apt-get purge tinyproxy (dansguardia gui would be remove as well)
2. sudo rm /etc/init.d/tinyproxy (to make sure it is removed)
3. re-install dansguardian gui.
4. Launch dansguardian gui and choose autoconfigure.

Hopefully that would solve this issue.

Another method to install dansguardian-gui:
1. Add below repository to your sources.list:
deb [http://david-kt.atbhost.net/Ubuntu_CE/](http://david-kt.atbhost.net/Ubuntu_CE/) binary/
2. sudo apt-get update
3. sudo apt-get install dansguardian-gui

By the way, what ubuntu release you are using to test dansguardian now? Is it Jaunty?

DK

---

### Post by mnavasuk on 2009-07-08
thanks for all your help dk. I've purged tinyproxy and had to do apt-get update after. Then reinstalled danguardian gui with your script again, and did autoconfigure, like advised. I still get "could not connect to parent proxy"
I'm using hardy by the way. Maybe that's the problem. I'll try rebooting now, who knows.

---

### Post by david_kt on 2009-07-09
> **mnavasuk said:**
> thanks for all your help dk. I've purged tinyproxy and had to do apt-get update after. Then reinstalled danguardian gui with your script again, and did autoconfigure, like advised. I still get "could not connect to parent proxy"
I'm using hardy by the way. Maybe that's the problem. I'll try rebooting now, who knows.

I tried using hardy, face the same issue. Right now I do not have time to troubleshoot yet as I am preparing the iso file for next ubuntu release (Jaunty). Once I complete it I will continue troubleshooting dansguardian for Hardy.

DK

---

### Post by mnavasuk on 2009-07-09
ok, fair enough. Thanks.

---

### Post by david_kt on 2009-07-11
> **mnavasuk said:**
> ok, fair enough. Thanks.

as I promise, I will take a look into this matter after I completed iso file for ubuntu ce v5 (jaunty).

The problem is the pid file for Hardy has different location. Temporary just do this:

gksudo gedit /etc/ tinyproxy/tinyproxy.conf

And search for:

PidFile "/var/run/tinyproxy/tinyproxy.pid"

Change it to 

PidFile "/var/run/tinyproxy.pid"

After that you could use dansguardian gui to manage dansguardian, but DO NOT autoconfigure as it will override that setting again.

I will improve dansguardian gui to cater for this differences, and also to prevent similar occurance in case of next release they move again the file location.

Thanks for the feedback.
DK

---

### Post by mnavasuk on 2009-07-12
thanks again.
I look forward to your renewed efforts. In the meantime, I've followed the latest advise, after removing all the packages, re-installed by running: "dansguardian-gui_1.1_all.deb". Opened /etc/tinyproxy/tinyproxy.conf and the line found is:
# PidFile: Write the PID of the main tinyproxy thread to this file so it
# can be used for signalling purposes.
#
PidFile "/var/run/tinyproxy.pid"

Now, when I opened dansguardian-gui, I didn't do autoconfigure, mind you =, I haven't changed anything as there wasn't any need.
When I did, start dansguardian, the console output is:
Starting tinyproxy: tinyproxy.
 * Firewall disabled via /etc/default/firehol
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun this script.
grep: /usr/lib/firefox-3.0.11/firefox.cfg: No such file or directory


More head scratching..
I mention just in case the pid issue is a red herring.
Thanks
mnavasuk

---

### Post by david_kt on 2009-07-12
> **mnavasuk said:**
> thanks again.
I look forward to your renewed efforts. In the meantime, I've followed the latest advise, after removing all the packages, re-installed by running: "dansguardian-gui_1.1_all.deb". Opened /etc/tinyproxy/tinyproxy.conf and the line found is:
# PidFile: Write the PID of the main tinyproxy thread to this file so it
# can be used for signalling purposes.
#
PidFile "/var/run/tinyproxy.pid"

Now, when I opened dansguardian-gui, I didn't do autoconfigure, mind you =, I haven't changed anything as there wasn't any need.
When I did, start dansguardian, the console output is:
Starting tinyproxy: tinyproxy.
 * Firewall disabled via /etc/default/firehol
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun this script.
grep: /usr/lib/firefox-3.0.11/firefox.cfg: No such file or directory


More head scratching..
I mention just in case the pid issue is a red herring.
Thanks
mnavasuk

Nope, sorry my instruction is not clear.
It is not necessary to remove/reinstall packages. OK, now is the whole steps:

1. Install everything using dansguardian gui (you have done this, is not not necessary to reinstall).
2. Autoconfigure using dansguardian gui.
3. Edit PidFile from
PidFile "/var/run/tinyproxy/tinyproxy.pid"
to
PidFile "/var/run/tinyproxy.pid"

4. Start dansguardian using danguardian gui

DK

---

### Post by mainiacjoe on 2009-07-12
Thanks, I'm very new to Linux (sick of Windows and my HD died so I figured I'd switch) and this helped a great deal--it's working now.  

I must say I've been quite frustrated trying to find documentation for beginners on DansGuardian.  The things I'd like to be able to do are have a different password on the GUI instead of root and have multiple filter settings for different I've found the wiki documentation but what I've seen assumes too much familiarity with the software.  Is there a DansGuardian for Dummies site you could recommend?

---

### Post by mnavasuk on 2009-07-13
DK you were spot on. Done the changes as you suggested in the last post and now I'm writing this from a Virtual Machine protected by Dansguardian. Now is time for me to do the tweaking and ideally put the webcontentcontrol graphical interface on top of it.
Just in time for the school holidays, so I can have peace of mind!
Thanks for your help.

@mainiacjoe:
You're not the only one trying to get different filter levels for different users. From all I've read about it, it's a difficult task since involves some way of user authentication being done external to dansguardian. May I suggest do something similar to what I'm doing, create a virtual machine to work with, so you can make any changes you want without breaking your current "live" installation.

---

### Post by david_kt on 2009-07-13
> **mnavasuk said:**
>  Now is time for me to do the tweaking and ideally put the webcontentcontrol graphical interface on top of it.


Would you please let me know what are the function in webcontentcontrol that is not available in dansguardian gui so as you need to put webcontentcontrol on top of it?

DK

---

### Post by david_kt on 2009-07-14
> **mainiacjoe said:**
> The things I'd like to be able to do are have a different password on the GUI instead of root and have multiple filter settings for different I've found the wiki documentation but what I've seen assumes too much familiarity with the software.  Is there a DansGuardian for Dummies site you could recommend?

1. Any user with admin right would be able to edit dansguardian.
2. I will try to add Multiple setting for different user to the GUI, but may be not so soon.
3. So far I have not found such documentation yet (DansGuardian for Dummies), I am also interested in there is such thing.

DK

---

