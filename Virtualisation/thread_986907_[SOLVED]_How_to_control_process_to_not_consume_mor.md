---
title: "[SOLVED] How to control process to not consume more then 20% of CPU?"
date: 2008-11-19
forum: Virtualisation
---

### Post by abcuser on 2008-11-19
Hi,
using Ubuntu 8.10 I have installed VirtualBox to have multiple virtual machines. In VirtualBox tool I can set max memory consumption, but can't set max CPU consumption. I have 5 virtual computers on my physical computer and I would like to set that each virtual computer should not take more then 20% of CPU power.

Is there any way on Linux that I could control the maximum CPU consumption by each Linux process?
Regards

---

### Post by aurelieng on 2008-11-19
[http://cpulimit.sourceforge.net/](http://cpulimit.sourceforge.net/)

:)

---

### Post by abcuser on 2008-11-19
Hi,
I have installed program:
```
sudo apt-get install cpulimit
```
and read man pages:
man cpulimit

This is nice tool. But it is not exactly what I would like to have. I need somekind of deamon that will control all of the processes and if some process (for example starting new virtual computer) try to consume more then 20% of CPU then this process is limited to use no more then 20%.

Cpulimit is nice tool for known existing processes, but I would also like to have some limitation for new processes. Any idea?

---

### Post by aurelieng on 2008-11-19
The CPU usage balance between all processes running on your machine can be adjusted by changing their "nice" value. Perhaps you should go this way ?

---

### Post by abcuser on 2008-11-19
@aurelieng, I know there is nice/renice command, but the main problem is I have to do this manually. What I would like to have is somekind of deamon that will monitor system and nice/renice (or cpulimit) the system dynamically without human intervention.

---

### Post by abcuser on 2008-11-20
Hi,
I have written bash script which behaves like a deamon. I gave it a name cpu_control.sh

**EDIT:** I have removed the script from this post, changed the script (repair bugs) and posted it few posts bellow.

Regards,
Absuser

---

### Post by abcuser on 2008-11-20
Hi,
I have run the above script with root privileges with nohup command, so I can safely close terminal and command will not terminate.

Run cpu_control in background:
```

sudo nohup ./cpu_control.sh &

```

Terminate cpu_control process:
```

ps aux | grep cpu_control   ==> get pid of this command
sudo kill -9 *pid_from_previous_command*

```

Terminate all cpulimit processes (if desired):
```

ps aux | grep cpulimit   ==> get pid of this command
sudo kill -9 *pid_from_previous_command*

```

I would be very happy if someone out there can test this script (deamon) and would be very happy if some writes some tips how to improve it.

Regards,
Abcuser

---

### Post by abcuser on 2008-11-21
Hi,
I have changed the code. The process can still occupy more then 20% of cpu if cpulimited to 20% in the interval of daemon is sleeping, so that is why I have changed the code. I have also add variables to adjust script to any other limit.

```

#!/bin/bash
# ==============================================================
# CPU limit daemon - set PID's max. percentage CPU consumptions
# ==============================================================

# Variables
CPU_LIMIT=20        # Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=3   # Daemon check interval

while sleep $DAEMON_INTERVAL
do
   NEW_PIDS=$(top -b -n1 | gawk 'NR>6 && $9>CPU_LIMIT {print $1}' CPU_LIMIT=$CPU_LIMIT)         # Violating PIDs
   LIMITED_PIDS=$(ps -eo args | gawk '$1=="cpulimit" {print $3}')                               # Already limited PIDs
   QUEUE_PIDS=$(diff <(echo "$NEW_PIDS") <(echo "$LIMITED_PIDS") | grep '^<' | sed 's/< //g')   # PIDs in queue

   for i in $QUEUE_PIDS
   do
      cpulimit -p $i -l $CPU_LIMIT -z &   # Limit new violating processes
   done
done

```

Now a question: how to boot up this script at start time. I have included (modified) script in /etc/init.d and executed update-rc.d command. At boot time Ubuntu freezes - it looks it hangs in while...do loop. OK, I have rescue my Ubuntu with recovery mode, but I am wondering how to write boot up script that will work without hanging. Any idea?
Regards,
Abcuser

---

### Post by abcuser on 2008-11-24
Hi,
I have managed to write boot-up script.

1. copy daemon script from above post to /root/cpulimit_daemon.sh file

2. with text editor save the following commands to file /etc/init.d/cpulimit
```

#!/bin/sh
#
# Script to start CPU limit daemon
#
set -e
. /lib/lsb/init-functions
case "$1" in
start)
nohup /root/cpulimit_daemon.sh &
;;
stop)
ps -eo pid,args | gawk '$3=="/root/cpulimit_daemon.sh"  {print $1}' | xargs kill -9   # kill cpulimit daemon
ps -eo pid,args | gawk '$2=="cpulimit" {print $1}' | xargs kill -9       # release cpulimited process to normal priority
;;
restart)
ps -eo pid,args | gawk '$3=="/root/cpulimit_daemon.sh"  {print $1}' | xargs kill -9   # kill cpulimit daemon
ps -eo pid,args | gawk '$2=="cpulimit" {print $1}' | xargs kill -9       # release cpulimited process to normal priority
sleep 5
/root/cpulimit_daemon.sh &
;;
status)
ps -eo pid,args | gawk '$3=="/root/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon is running"; else print " * cpulimit daemon is not running" }'
;;
esac
exit 0

```

3. change file's owner to root:
```

cd /etc/init.d/
sudo chown root:root cpulimit
```

4. change permissions:
```
sudo chmod 755 cpulimit
```

5. add script to boot-up procedure directories:
```
sudo update-rc.d cpulimit defaults
```

6. reboot
```
sudo reboot
```

After reboot check:
```
sudo service cpulimit status
```
it should return: "cpulimit daemon is running" or "cpulimit daemon is not running".

Note: For users using prior to Ubuntu 8.10 instead of service command use "sudo /etc/init.d/cpulimit status" syntax or install sysvconfig package using command: sudo apt-get install sysvconfig

To stop cpulimit service:
```
sudo service cpulimit stop
```

To start cpulimit service:
```
sudo service cpulimit start
```

If you change some settings in /root/cpulimit_daemon.sh for example CPU limit to something else then 20% or daemon interval to something else then 3 seconds, then after changing settings you can restart service:
```
sudo service cpulimit restart
```

Hope this helps to someone out there.
Regards,
Abcuser

---

### Post by lex1 on 2008-11-24
thankyou very much it will be very useful.

lex1:KS

---

