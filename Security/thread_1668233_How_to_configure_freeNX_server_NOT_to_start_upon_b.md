---
title: "How to configure freeNX server NOT to start upon boot?"
date: 2011-01-16
forum: Security
---

### Post by latgarf on 2011-01-16
*By default*, upon booting an Ubuntu machine (I use Maverick), freeNX server is *running*.
This can be checked by
```
$ sudo /usr/NX/bin/nxserver --status
```
The server can be manually stopped by
```
$ sudo /usr/NX/bin/nxserver --stop
```
But it's annoying to stop the server manually on every restart of the machine, if nxserver is rarely needed. If nxserver just left running, it adds to security risks, right?
Is there any way to configure freeNX server NOT to start upon machine's boot-up?

Thanks for any ideas/advice!

---

### Post by ajgreeny on 2011-01-16
Try adding the manual command that you use, minus the sudo, just above the **exit 0** line in /etc/rc.local, ie
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/NX/bin/nxserver --stop
[COLOR=Red]service ssh stop[/COLOR]

exit 0

```As an example I have left in a line that I use, [COLOR=Red]shown in red above[/COLOR], to stop the ssh server from running as I need it only very seldom, and like you prefer to not have it run all the time for increased security.

---

### Post by sj1410 on 2011-01-16
a better way is rcconf

rcconf is a handy Debian utility for configuring which services get started up at boot-time. It's really a front-end for the update-rc.d command.


> sudo apt-get install rcconf
sudo rcconf

unselect the services than you dont want to start at boot time. thats it.

---

### Post by latgarf on 2011-01-16
Guys, your suggestions look spot-on... but neither solution worked :confused:

rcconf shows nxserver unchecked (even after poweroff-> restart), but 
nxserver --status 
still shows "running".

I also edited /etc/rc.local to include both nxserver --stop and ssh stop, but nxserver --status is "running" and I could nx-connect seamlessly. Also after complete poweroff->restart of the nxserver machine. 
Am I missing something?

---

### Post by bodhi.zazen on 2011-01-16
rc.local probably runs too early, you can add a sleep 10 to the top

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
**sleep 10**
/usr/NX/bin/nxserver --stop
service ssh stop

exit 0
```

Better either disable freenx from starting or edit the init script.

I am not familiar with the init script, is it in /etc/init ? If so set the service to stop on all runlevels.

---

