---
title: "HOWTO: Set maximum CPU consumption in percentage by any process"
date: 2008-11-25
forum: Tutorials
---

### Post by abcuser on 2008-11-25
**_EDIT_**: Tutorial updated on September 15, 2011. New features added to scripts and some bugs fixed.
**_EDIT_**: 'Attention' info added for properly specifying the variables on January 14, 2014.

**Purpose of cpulimit daemon:**
Daemon runs in background and checks if some process is consuming more then 20% of CPU and if it does then daemon lowers CPU consumption of particular process to maximum of 20%. The goal is to have no single process that consumes more then 20% of CPU power.

Note: If you would like to omit only one process then you don't need this "cpulimit daemon". In this case you only need [cpulimit program](http://cpulimit.sourceforge.net/) to be executed from terminal.

**Tested environment:**
Cpulimit daemon was tested on Ubuntu 8.04 LTS and Ubuntu 10.04 LTS. However it should be running fine on other Ubuntu versions and also on other Linux distributions, because it does not uses any Ubuntu specific code.


[size="4"]1. INSTALL PACKAGES[/size]

1. Install cpulimit package.
```
sudo apt-get install cpulimit
```

2. Install gawk package.
```
sudo apt-get install gawk
```


[size="4"]2. CREATE CPULIMIT DAEMON FILE[/size]

Open text editor with root privileges and save bellow daemon script text to new file /usr/bin/cpulimit_daemon.sh

```

#!/bin/bash
# ==============================================================
# CPU limit daemon - set PID's max. percentage CPU consumptions
# ==============================================================

# Variables
CPU_LIMIT=20       	# Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=3  	# Daemon check interval in seconds
BLACK_PROCESSES_LIST=   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.
WHITE_PROCESSES_LIST=   # Limit all processes except processes defined in this variable. If variable is empty (default) all violating processes are limited.

# Check if one of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST is defined.
if [[ -n "$BLACK_PROCESSES_LIST" &&  -n "$WHITE_PROCESSES_LIST" ]] ; then    # If both variables are defined then error is produced.
   echo "At least one or both of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST must be empty."
   exit 1
elif [[ -n "$BLACK_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | grep -E '$BLACK_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
elif [[ -n "$WHITE_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6' | grep -E -v '$WHITE_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
else
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6 && \$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
fi

# Search and limit violating PIDs
while sleep $DAEMON_INTERVAL
do
   NEW_PIDS=$(eval "$NEW_PIDS_COMMAND")                                                                    # Violating PIDs
   LIMITED_PIDS=$(ps -eo args | gawk '$1=="cpulimit" {print $3}')                                          # Already limited PIDs
   QUEUE_PIDS=$(comm -23 <(echo "$NEW_PIDS" | sort -u) <(echo "$LIMITED_PIDS" | sort -u) | grep -v '^$')   # PIDs in queue

   for i in $QUEUE_PIDS
   do
       cpulimit -p $i -l $CPU_LIMIT -z &   # Limit new violating processes
   done
done

```


[size="4"]3. CHANGE VARIABLES TO YOUR ENVIRONMENT NEEDS[/size]

**CPU_LIMIT**
Change this variable in above script if you would like to omit CPU consumption for every process to any other percentage then 20%. Please read "If using SMP computer" chapter bellow if you have SMP computer (more then 1 CPU or CPU with more then 1 core).

**DAEMON_INTERVAL**
Change this variable in above script if you would like to have more/less regular checking. Interval is in seconds and default is set to 3 seconds.

**BLACK_PROCESS_LIST and WHITE_PROCESSES_LIST**
Variable BLACK_PROCESSES_LIST limits only specified processes. If variable is empty (default) all violating processes are limited.

Variable WHITE_PROCESSES_LIST limits all processes except processes defined in this variable. If variable is empty (default) all violating processes are limited.

One or both of the variables BLACK_PROCESSES_LIST and WHITE_PROCESSES_LIST has to be empty - it is not logical that both variables are defined. 

You can specify multiple processes in one of this two variables using delimiter characters "|" (without double quotes). Sample: if you would like to cpulimit all processes except mysql, firefox and gedit processes set variable: WHITE_PROCESSES_LIST="mysql|firefox|gedit"

**Attention:** Make sure you don't put any spaces in variable, for example WHITE_PROCESS_LIST= "mysql|firefox|gedit" (notice space character after = character) is not going to work correctly. You need to specify the variable without spaces: WHITE_PROCESS_LIST="mysql|firefox|gedit"

[size="4"]4. PROCEDURE TO AUTOMATICALLY START DAEMON AT BOOT TIME[/size]

1.  Set file permissions for root user:
```
sudo chmod 755 /usr/bin/cpulimit_daemon.sh
```

2. Open text editor with root privileges and save bellow script to new file /etc/init.d/cpulimit
```

#!/bin/sh
#
# Script to start CPU limit daemon
#
set -e

case "$1" in
start)
if [ $(ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print $1}' | wc -l) -eq 0 ]; then
    nohup /usr/bin/cpulimit_daemon.sh >/dev/null 2>&1 &
    ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon started successfully"; else print " * cpulimit daemon can not be started" }'
else
    echo " * cpulimit daemon can't be started, because it is already running"
fi
;;
stop)
CPULIMIT_DAEMON=$(ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print $1}' | wc -l)
CPULIMIT_INSTANCE=$(ps -eo pid,args | gawk '$2=="cpulimit" {print $1}' | wc -l)
CPULIMIT_ALL=$((CPULIMIT_DAEMON + CPULIMIT_INSTANCE))
if [ $CPULIMIT_ALL -gt 0 ]; then
    if [ $CPULIMIT_DAEMON -gt 0 ]; then
        ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print $1}' | xargs kill -9   # kill cpulimit daemon
    fi

    if [ $CPULIMIT_INSTANCE -gt 0 ]; then
        ps -eo pid,args | gawk '$2=="cpulimit" {print $1}' | xargs kill -9                    # release cpulimited process to normal priority
    fi
    ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon can not be stopped"; else print " * cpulimit daemon stopped successfully" }'
else
    echo " * cpulimit daemon can't be stopped, because it is not running"
fi
;;
restart)
$0 stop
sleep 3
$0 start
;;
status)
ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon is running"; else print " * cpulimit daemon is not running" }'
;;
esac
exit 0

```

3. Change file's owner to root:
```

sudo chown root:root /etc/init.d/cpulimit
```

4. Change permissions:
```
sudo chmod 755 /etc/init.d/cpulimit
```

5. Add script to boot-up procedure directories:
```
sudo update-rc.d cpulimit defaults
```

6. Reboot to check if script starts cpulimit daemon at boot time:
```
sudo reboot
```


[size="4"]5. MANUALLY CHECK, STOP, START AND RESTART DAEMON[/size]

Note: Daemon and service in this tutorial has equal meaning.

Note: For users using prior to Ubuntu 8.10 (like Ubuntu 8.04 LTS) instead of service command use "sudo /etc/init.d/cpulimit *status/start/stop/restart*" syntax or install sysvconfig package using command: sudo apt-get install sysvconfig

**Check if cpulimit service is running**
Check command returns: "cpulimit daemon is running" if service is running, or "cpulimit daemon is not running" if service is not running.
```
sudo service cpulimit status
```

**Start cpulimit service**
You can manually start cpulimit daemon which will start to omit CPU consumption.
```
sudo service cpulimit start
```

**Stop cpulimit service**
Stop command stops cpulimit daemon (so no new process will be limited) and also sets to all existing limited processes to have full access to CPU, just like it was before cpulimit was not running.
```
sudo service cpulimit stop
```

**Restart cpulimit service**
If you change some variables settings in /usr/bin/cpulimit_daemon.sh like CPU_LIMIT, DAEMON_INTERVAL, BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST, then after changing settings you must restart service.
```
sudo service cpulimit restart
```


[size="4"]6. CHECK CPU CONSUMPTION WITH OR WITHOUT CPULIMIT DAEMON[/size]

**Without daemon**
1. stop cpulimit daemon (sudo service cpulimit stop)
2. execute CPU intensive tasks in background
3. execute command: top and check for %CPU column
Result of %CPU is probably more then 20% for each process.

**With daemon turned on**
1. start cpulimit daemon (sudo service cpulimit start)
2. execute the same CPU intensive tasks in background
3. execute command: top and check for %CPU column
Result of %CPU should be maximum 20% for each process.
Note: Don't forget at beginning %CPU can be more then 20%, because daemon has to catch violating process in interval of 3 seconds (set in script by default)


[size="4"]7. IF USING SMP COMPUTER[/size]

I have tested this code on Intel dual-core CPU computer - that behaves like [SMP computer](http://en.wikipedia.org/wiki/Symmetric_multiprocessing). Don't forget that top command and also cpulimit by default behaves in Irix mode, where 20% means 20% of **one** CPU. If there are two CPUs (or dual-core) then total %CPU can be 200%. In top command Irix mode can be turned off with command I (pressing <Shift>+i when top command is running) and Solaris mode is turned on, where total amount of CPU is divided by number of CPUs, so %CPU can be no more then 100% on any number of CPU computer. Please read more info about top command in [top man page](http://www.go2linux.org/top-linux-command-line-to-show-running-processes-in-real-time) (search for I command). Please also read more about how cpulimit is operating on SMP computer in [cpulimit official page.](http://cpulimit.sourceforge.net/)

But how does cpulimit daemon operates on SMP computer? Always in Irix mode. So if you would like to spend 20% of CPU power on 2-CPU computer then 40% should be used for CPU_LIMIT variable in cpulimit daemon script.


[size="4"]8. UNINSTALL CPULIMIT DAEMON AND CPULIMIT PROGRAM[/size]

If you would like to get rid of cpulimit daemon you can clean up your system by removing cpulimit daemon and uninstalling cpulimit program.

1. Stop cpulimit daemon
```
sudo service cpulimit stop             # Stop cpulimit daemon and all cpulimited processes
```      

2. Remove daemon from boot-up procedure
```
sudo update-rc.d -f cpulimit remove    # Remove symbolic links
```

3. Delete boot-up procedure
```
sudo rm /etc/init.d/cpulimit           # Delete cpulimit boot-up script
```

4. Delete cpulimit daemon
```
sudo rm /usr/bin/cpulimit_daemon.sh    # Delete cpulimit daemon script
```

5. Uninstall cpulimit program
```
sudo apt-get remove cpulimit
```

6. Uninstall gawk program
If you don't need this program for any other script, you can remote it.
```
sudo apt-get remove gawk
```


[size="4"]9. NOTE ABOUT AUTHORS[/size]

I have just written **daemon** for cpulimit (bash scripts above). I am not the author of cpulimit project. If you need more info about cpulimit program, please read official cpulimit web page: [http://cpulimit.sourceforge.net/](http://cpulimit.sourceforge.net/).

Regards,
Abcuser

---

### Post by bapoumba on 2008-11-26
Edited thread title :KS

---

### Post by bekirserifoglu on 2009-01-12
a very handy daemon to control the cpu usage in userspace. your instructions are comprehensive but you forgot to include one thing. you have to make the daemon executable. otherwise it will say something like "nohup: cannot run command `/root/cpulimit_daemon.sh': Permission denied".

nice job!

---

### Post by abcuser on 2009-01-16
@bekirserifoglu, thanks I have updated the how-to.

---

### Post by 3rdalbum on 2009-01-17
Hang on a sec... can I just ask for clarification on something? Let's say you're playing a game or transcoding video, where the process uses nearly 100% CPU and you want it that way. Will it then run at 1.5th of the speed with your daemon turned on?

If so, who wants that? I can understand limiting a specified process, but I can't understand limiting every process.

---

### Post by abcuser on 2009-01-17
Hi,
@3rdalbum, thanks for sharing your comment.

Let me explain. On PCs this daemon behaviour is probably not desired. Limiting specific process is more desired, like you described. But I have written this daemon for **server** environment and not every server environment is suitable for this daemon! I have virtual computers server environment.

Lets see a sample. In my case I have an Intel server where I have multiple virtual machines (also Ubuntu and some Windows too) using [VirtualBox](http://www.virtualbox.org/) virtualization tool. On Ubuntu virtual host computer I have several virtual machines. I can omit how much memory can be consumed by each application in VirtualBox GUI, but can't enforce CPU usage. So I have written a daemon to control maximum CPU consumption by each virtual machine. I know I could run every virtual machine with only cpulimit command, but I am not only administrator on this Linux boxes and new virtual machines are added on the fly and others are moved to other Intel computers. So if administrator forgets to set cpulimit command to one new specific virtual machine, this new machine would consume all CPU power and take down other very important virtual machines.

Beside using cpulimit daemon, I can still set that some virtual machine can only use for example 10% of CPU power if desirable by executing cpulimit command by hand. But I can't allow one single process to make all others virtual systems down.
Regards

---

### Post by akoblentz on 2009-03-30
Thank you, your time and effort is much appreciated.

I know how to run a single process through cpulimit,
is there a way to limit a boot service with cpulimit?
I see that there is a way to limit a service, but I want it
limited from startup without me having to type anything...

Thanks

---

### Post by abcuser on 2009-03-31
Hi,
don't know if this is possible, it is strange because boot process starts deamon that handles CPU.

Why would you like to omit CPU to boot process? I always like to boot up as soon as possible.
Regards

---

### Post by akoblentz on 2009-03-31
> **abcuser said:**
> Hi,
don't know if this is possible, it is strange because boot process starts deamon that handles CPU.

Why would you like to omit CPU to boot process? I always like to boot up as soon as possible.
Regards

An example is: Folding@Home, I have it set up to use a service, so at boot it starts working.
I don't want to dedicate a full core to it though.  I can manually cpulimit the PID, however 
I'd like a way to do that automatically.  So, I didn't really mean a "boot process" 
so much as a process that starts on boot.

Thanks.

---

### Post by abcuser on 2009-03-31
Hi,
OK, now I understand. The idea would probably go in this way. At boot time you start some script to start you program and after that some kind of cpulimit daemon has to start and try to catch PID of your desired program and lower the CPU of that program.

I have written this script some time ago, so it should be something like this (instead of cpulimit daemon write this script)
#!/bin/bash
cpulimit -p $( ps -eo pid,args | grep "process name you would like to CPU limit" | grep -v grep | gawk '{print $1}' ) -l 5 -z & 

Note: instead of string "process name you would like to CPU limit" write your process name getting from "ps -eo pid, args" command. Above script assumes you would like to lower CPU to 5% (string: "-l 5" at the end of command), if you would like any other limit change this settings.

After that you have to make sure that your program has to start first and then this new cpulimit script goes second. Assuming you scrip has 20 priority which is by default, run the following script:
update-rc.d cpulimit-daemon defaults 21 19

Note: cpulimit-daemon is your script file name (select appropriate name) to start cpulimit daemon.

Hope this helps,
Regards

---

### Post by akoblentz on 2009-03-31
> **abcuser said:**
> Hi,
OK, now I understand. The idea would probably go in this way. At boot time you start some script to start you program and after that some kind of cpulimit daemon has to start and try to catch PID of your desired program and lower the CPU of that program.

I have written this script some time ago, so it should be something like this (instead of cpulimit daemon write this script)
#!/bin/bash
cpulimit -p $( ps -eo pid,args | grep "process name you would like to CPU limit" | grep -v grep | gawk '{print $1}' ) -l 5 -z & 

Note: instead of string "process name you would like to CPU limit" write your process name getting from "ps -eo pid, args" command. Above script assumes you would like to lower CPU to 5% (string: "-l 5" at the end of command), if you would like any other limit change this settings.

After that you have to make sure that your program has to start first and then this new cpulimit script goes second. Assuming you scrip has 20 priority which is by default, run the following script:
update-rc.d cpulimit-daemon defaults 21 19

Note: cpulimit-daemon is your script file name (select appropriate name) to start cpulimit daemon.

Hope this helps,
Regards

That helps a lot, thank you.  There is an issue with your ps/grep combo...

Here's the output from the ps and grep:

```

 6365 sh -c ./FahCore_a0.exe -dir work/ -suffix 01 -checkpoint 15 -verbose -lifeline 6361 -version 602
 6366 ./FahCore_a0.exe -dir work/ -suffix 01 -checkpoint 15 -verbose -lifeline 6361 -version 602
 6367 ./FahCore_a0.exe -dir work/ -suffix 01 -checkpoint 15 -verbose -lifeline 6361 -version 602
 6368 ./FahCore_a0.exe -dir work/ -suffix 01 -checkpoint 15 -verbose -lifeline 6361 -version 602
 6369 ./FahCore_a0.exe -dir work/ -suffix 01 -checkpoint 15 -verbose -lifeline 6361 -version 602
12331 grep FahCore_a0.exe

```

and the resulting list of ALL of the PIDs gets sent to cpulimit, however, it only acts on the first. The first PID isn't the one that needs limiting.  6368 is, or rather, 6366, 6367, or 6369 would also work. 6365 is the spawning process, however that just hangs out to check for WU updates and the like, it doesn't handle any computations itself.

Any ideas?

Thanks.

---

### Post by abcuser on 2009-04-01
Hi,
I didn't know you have multiple process you would like to limit CPU...
You need to add some loop like for loop to cpu limit all pids.

Try something like:

PIDS=$(ps -eo pid | grep "process name you would like to CPU limit" | grep -v grep | gawk '{print $1}')
for i in $PIDS
do
      cpulimit -p $i -l 5 -z &
done

---

### Post by akoblentz on 2009-04-01
Hey,
I don't really need to cpulimit on multiple PIDs, just one of the last 4 would work.
I'll try your script though, can't hurt to limit all of them.

Thank you very much for all of your help.

---

### Post by akoblentz on 2009-04-01
Hmm, didn't work. When I run it, nothing happens, no output in the term and the process isn't limited, no cpulimits in htop.

Here's the script:
```

#!/bin/bash
PIDS=$(ps -eo pid | grep "FahCore_a0.exe" | grep -v grep | gawk '{print $1}')
for i in $PIDS
do
    cpulimit -p $i -l 5 -z &
done

```

Here's the command I run to limit it currently:
```

% sudo cpulimit -p 6368 -l 20

```

I only need to limit 1 of the 4 processes to limit the whole job I think.

Any ideas?

Thanks

---

### Post by abcuser on 2009-04-01
Hi,
sorry I have forgotten to post "args" argument in ps command. Try this out (instead of PIDS line).
PIDS=$(ps -eo pid,args | grep "FahCore_a0.exe" | grep -v grep | gawk '{print $1}')
Regards

---

### Post by akoblentz on 2009-04-01
Spectacular.  That works perfectly.

Thank you very much.

I keep telling myself that I need to know a shell scripting language, then I get swept up into something else.  
This most recent diversion was Obj-C 2.0.  I'll learn one eventually.

---

### Post by abcuser on 2009-04-02
akoblentz,
thanks for letting me that this solution works for you.
Regards

---

### Post by benji66 on 2009-04-15
Thanks, *abcuser*; this was quite comprehensive.  The only addition I would make is to assure that gawk is installed:
sudo apt-get install gawk
I expect many users already have it, though it wasn't in my upgrade of Ubuntu 8.10 from 8.04.  Thanks again!

---

### Post by abcuser on 2009-04-17
benji66, yes I probably installed gawk before writting this how-to. Now I have updated how-to. Thanks for your note.

---

### Post by Elus1ve on 2009-04-28
hi

would like ask is it possible to limit more processes with the above script you wrote for _akoblentz_ (so not only one application)?

how would such script look like, or does it only need a grep extension?

other option:

to limit everything at anytime except a mysqld process (so basically add exemption)

much appreciated

---

### Post by abcuser on 2009-04-29
Elus1ve, I have written new version of cpulimit daemon. Replace step "2. WRITE CPULIMIT DAEMON FILE" from first post of this how-to with the file bellow. All other steps from how-to remains the same.

UPDATE: ***script deleted because of some bug. Please see script in new post bellow.***

Daemon has two new variables: BLACK_PROCESSES_LIST and WHITE_PROCESSES_LIST.
If you would like only to limit process e.g "firefox" then set:
BLACK_PROCESSES_LIST="firefox"

If you would like to limit all processes except e.g. "firefox" set:
WHITE_PROCESSES_LIST="firefox"

If you would like to limit/exclude multiple processes just use "\|" separator (without quoting marks) between process names. Sample:
BLACK_PROCESSES_LIST="firefox|\gedit\|glchess"
WHITE_PROCESSES_LIST="firefox|\gedit\|glchess"

I haven't tested this new daemon in deep so I haven't changed first post's how-to. I would be very happy if someone out there could test this daemon and post some feed back.
Regards

---

### Post by Elus1ve on 2009-04-29
> **abcuser said:**
> I suggest to extent grep commands with \| which is "OR" conditional in grep.
Sample:
PIDS=$(ps -eo pid,args | grep "FahCore_a0.exe\|second_program\|third_program\|etc_program" | grep -v grep | gawk '{print $1}')

You also can use grep but using "v" switch sample:
PIDS=$(ps -eo pid,args | grep -v "mysqld" | grep -v grep | gawk '{print $1}')

thx for help.

i tried the first method inside your original loop and ended up with almost 1500 instances of cpulimit :S
does the loop need some modification?

gonna try with the invert match hopfully it doesn create that much threads

you know i have a "power hour" in the morning when all perl, logwatch, backup etc process is working and i try to use cpulimit on these processes so that the web surface is still reachable (this is the main goal :P)

okay cheers u modified it while i was writing. i'll go with it then cheers.

---

### Post by abcuser on 2009-04-29
> **Elus1ve said:**
> i tried the first method inside your original loop and ended up with almost 1500 instances of cpulimit :S
does the loop need some modification?

gonna try with the invert match hopfully it doesn create that much threads
Sorry it was probably some kind of bug in code. I didn't test it... But instead I have written new version of daemon. Please see the code in my previous post and test it on test computer. If you would like to test it directly on production computer (not recommended in first place) replace line:
       cpulimit -p $i -l $CPU_LIMIT -z &   # Limit new violating processes
with command:
       echo $i

So instead of cpulimit processes just print PIDs on screen. You can then check if desired PIDs were displayed by using command:
ps aux | grep *PID*

> **Elus1ve said:**
> 
you know i have a "power hour" in the morning when all perl, logwatch, backup etc process is working and i try to use cpulimit on these processes so that the web surface is still reachable (this is the main goal :P)
In this case write all processes you would like to omit a CPU in BLACK_PROCESSES_LIST variable separated by "\|" (without double quotes). See notes in previous post for details.

> **Elus1ve said:**
> 
okay cheers u modified it while i was writing. i'll go with it then cheers.
Yes, sorry... I just got and idea how to extend daemon functionality.

Please try above daemon. For testing purposes you can just copy above text, create file and give execute permissions and then execute from terminal using command:
sudo ./cpulimit_daemon.sh
And pressing <ctrl>+c to stop script.

---

### Post by Elus1ve on 2009-04-29
# ps aux | grep cpu
root      8341  0.0  0.0   1788   556 ?        S<   14:20   0:00 cpulimit -p 11030 -l 5 -z
root      8420  0.0  0.0   1788   556 ?        S<   14:20   0:00 cpulimit -p 11030 -l 5 -z
root      8498  0.0  0.0   1788   560 ?        S<   14:20   0:00 cpulimit -p 11030 -l 5 -z
root      8773  0.0  0.0   1788   560 ?        S<   14:21   0:00 cpulimit -p 11030 -l 5 -z
root      8981  0.0  0.0   1788   556 ?        S<   14:21   0:00 cpulimit -p 11030 -l 5 -z
root      9024  0.0  0.0   1788   560 ?        S<   14:21   0:00 cpulimit -p 11030 -l 5 -z
root      9123  0.0  0.0   1788   556 ?        S<   14:21   0:00 cpulimit -p 11030 -l 5 -z
root      9214  0.0  0.0   1788   556 ?        S<   14:21   0:00 cpulimit -p 11030 -l 5 -z
root     11070  0.0  0.0   1788   556 ?        S<   14:01   0:00 cpulimit -p 11030 -l 5 -z

its running for a few hours wonder why is there so many instance on the same pid :S

# ps -p 11030
  PID TTY          TIME CMD
11030 ?        00:03:34 awstats.pl

---

### Post by abcuser on 2009-04-30
Elus1ve,
it looks the same process was cpu-limited multiple times.

Can you please provide more info.
1. Did you make your own version of the program or did you use my new daemon script? This problem should not happened with my new daemon script because I haven't touched code that is preventing multiple cpu limitation of the same PID.
2. Did you kill all cpulimit processes before running new daemon - you could have some old cpulimit processes running before running a daemon. I suggest you run "killall cpulimit" and then check "ps aux | grep cpulimit" to see if all cpulimit processes are killed. Then start daemon.
3. How did you set variables BLACK_PROCESSES_LIST and WHITE_PROCESSES_LIST?
Regards

---

### Post by Elus1ve on 2009-05-02
> **abcuser said:**
> Elus1ve,
it looks the same process was cpu-limited multiple times.

Can you please provide more info.
1. Did you make your own version of the program or did you use my new daemon script? This problem should not happened with my new daemon script because I haven't touched code that is preventing multiple cpu limitation of the same PID.

using your new version
2. Did you kill all cpulimit processes before running new daemon - you could have some old cpulimit processes running before running a daemon. I suggest you run "killall cpulimit" and then check "ps aux | grep cpulimit" to see if all cpulimit processes are killed. Then start daemon.

yea i looked up that i have killed every cpulimit process
3. How did you set variables BLACK_PROCESSES_LIST and WHITE_PROCESSES_LIST?
Regards

WHITE_PROCESSES_LIST="mysqld\|sc_trans\|httpd"
the black list line is empty else i would get an error :P

---

### Post by abcuser on 2009-05-03
> **Elus1ve said:**
> the black list line is empty else i would get an error :P
I have omitted possibility of having BLACK and WHITE list at the same time, because it is not logical to have both at the same time.

---

### Post by abcuser on 2009-05-03
Elus1ve,
you were correct some processes could be repeated (cpulimited) multiple times, because of bug in QUEUE_PID variable. I used command diff to check the difference between already cpulimited processes (variable LIMITED_PIDS) vs. new processes (NEW_PIDS variable). But I have forgot, that diff can return c-change, d-delete or a-add. Script just assumed that every time c is returned. So this was the reason some processes could be repeated twice or more time. I have now replaced diff command with comm which is more suitable to solve this kind of problem. I have made some other little changes in script as well, so please copy the _whole script_ and change variables values. I have tested this new script in deep and now problem should be solved. Can you please be so kind and test this new script and just write me some feed-back.
Thanks,
Abcuser

UPDATE: **script was deleted. See script on the first post of this thread.**

---

### Post by Elus1ve on 2009-05-04
that was it mate, with the last version you solved it:)

thank you very much for your efforts

\\:D/

---

### Post by abcuser on 2009-05-04
Elus1ve, thanks a lot for testing. I have updated first post with this latest script.

I have also changed start-up script in chapter3 step 2. "Restart" option was simplified.
Regards

---

### Post by krisik28 on 2009-05-15
Is there any way to run the daemon without reboot ?
Regards krisik28

---

### Post by abcuser on 2009-05-15
Hi,
have you read my first post, there is chapter "4. MANUALLY CHECK, STOP, START AND RESTART DAEMON".
Regards

---

### Post by alan_smithee on 2009-09-15
*bump*

hi mate.
first of all, thanks for sharing this script, really handy!
but can you explain a bit more about the blacklist function? 
i couldn't get it working

my intention is to limit a certain php script process, i'm running kloxo as the control panel
so my command goes like this:
```
lxsuexec /path/to/script.php
```it doesn't work with blacklist function, cpulimit just wont run.
but if i let the daemon limit all process, it works fine. 
it just didn't work with blacklist function. i put something like this on the script:
```
CPU_LIMIT=10           # Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=3      # Daemon check interval in seconds
BLACK_PROCESSES_LIST= "lxsuexec /path/to/script.php"  # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.
WHITE_PROCESSES_LIST=   # Limit all processes except processes defined in this variable. If variable is empty (default) all violating processes are 
limited.
```
thanks in advance for any replies :)

---

### Post by abcuser on 2009-09-15
Hi,
I assume your exact command is not displayed by top command or is displayed something else. Try the following.
Run you command from terminal:
```
lxsuexec /path/to/script.php
```
and then run following command in another terminal:
```
top -b -n1 -c
```
and search for your command in the Command column. Do you see "lxsuexec /path/to/script.php" string in Command column? If no, then you have to find a command in Command column that matches your command.

Then write output (or part of output) of your command from Command column in BLACK_PROCESS_LIST variable.

Hope this helps,
Abcuser

---

### Post by alan_smithee on 2009-09-15
hi thanks for replying :)
i ran ```
top -b -n1 -c
```and it was displayed exactly as
```
lxsuexec /path/to/script.php
```i tried to run cpulimit command directly without script, it's working fine the limit applied
```
cpulimit -p $( ps -eo pid,args | grep "lxsuexec /path/to/script.php" | grep -v grep | gawk '{print $1}' ) -l 5 -z &
```





> **abcuser said:**
> Hi,
I assume your exact command is not displayed by top command or is displayed something else. Try the following.
Run you command from terminal:
```
lxsuexec /path/to/script.php
```and then run following command in another terminal:
```
top -b -n1 -c
```and search for your command in the Command column. Do you see "lxsuexec /path/to/script.php" string in Command column? If no, then you have to find a command in Command column that matches your command.

Then write output (or part of output) of your command from Command column in BLACK_PROCESS_LIST variable.

Hope this helps,
Abcuser

---

### Post by abcuser on 2009-09-16
Hi,
daemon is written for the processes that you don't know when they start-up. If you know when the process starts up, you can manually execute cpulimit command, so no need for daemon.
Regards

---

### Post by alan_smithee on 2009-09-16
actually i don't know when the command will be executed mate, i got some clients who will run this script on my server whenever they'd like to and each client has their own directory with a copy of this script. the script itself is a client-side script to transfer file remotely, so whenever the transfer is done the script then will terminate itself.

the thing is i have some clients who tend to run this script much and it uses huge CPU resource.
so what i'd like to do basically is to put some of these clients on a blacklist for cpulimit.

---

### Post by kut77less on 2009-10-18
when I try to set WHITE_PROCESSES_LIST it does not work.  I try to set it so that it does not limit npviewer.bin (flash). I want to do this because when you limit cpu of flash the videos don't play smoothly. Can you please help me?


thanks

---

### Post by abcuser on 2009-10-21
kut77less, when you run your flash program, try to execute command:
```
top -b -n1 -c
```
Do you see this program in this list of processes? Try to write exactly what you get from top command.

---

### Post by kut77less on 2009-10-22
> **abcuser said:**
> kut77less, when you run your flash program, try to execute command:
```
top -b -n1 -c
```
Do you see this program in this list of processes? Try to write exactly what you get from top command.


When I use that command I can see that it is this command 



> /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/5193-2

But When I put the in the white list it still limits the CPU 


Any suggestions?

Thanks for all your help by the way.

---

### Post by abcuser on 2009-11-20
kut77less,
sorry for late response, I have been very busy. 

It looks "grep" command works differently if "." character is written in variable, don't know why this kind of behaviour. Work-around solution is to to replace the following string in row 19:
```
grep -v '$WHITE_PROCESSES_LIST'
```
with code
```
grep -v "$WHITE_PROCESSES_LIST"
```
So instead of single quotes use double quotes.

This should work.

If you don't like above solution, then just use "npviewer" as WHITE_PROCESS_LIST variable, so without "." character.

Please write back if you solved the problem.
Regards

---

### Post by malyvelky on 2009-11-26
Hi, thank you very much for these instructions! However for me it didn't  work unless I replaced "grep 'black/white list'  with "**grep -E **'black/white list'" in /root/cpulimit_daemon.sh:

```
if [[ -n "$BLACK_PROCESSES_LIST" &&  -n "$WHITE_PROCESSES_LIST" ]] ; then    # If both variables are defined then error is produced.
   echo "At least one or both of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST must be empty."
   exit 1
elif [[ -n "$BLACK_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | grep -E '$BLACK_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
elif [[ -n "$WHITE_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6' | grep -v -E '$WHITE_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT && \$1 != \"PID\" {print \$1}' CPU_LIMIT=$CPU_LIMIT"
else
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6 && \$9>CPU_LIMIT  && \$1 != \"PID\" {print \$1}' CPU_LIMIT=$CPU_LIMIT"
fi
```I suppose that on your system grep is actually linked to egrep, however on my system (Ubuntu 9.04) it's "GNU grep 2.5.3", which doesn't interpret its input as a regular expression by default and we must enforce it by providing the -E option.

Could you please reflect this possible issue somehow in the HOWTO to save other people from the pain to find it out? Thank you!

---

### Post by abcuser on 2009-11-26
> **malyvelky said:**
> I suppose that on your system grep is actually linked to egrep, however on my system (Ubuntu 9.04) it's "GNU grep 2.5.3", which doesn't interpret its input as a regular expression by default and we must enforce it by providing the -E option.
Hi,
I have checked with command "which grep" and it returned /bin/grep and "grep --help" returned "GNU grep 2.5.4". Now I use Ubuntu 9.10, but when this script was last updated on first post of this thread I used Ubuntu 9.04 and it was working fine.

Can you please write what is your string for white or black list that was not excepted by grep command. I need this to check in deep why the exception appeared. And if needed I will update the first post, but I need more info.
Regards

---

### Post by kut77less on 2009-11-29
> **abcuser said:**
> kut77less,
sorry for late response, I have been very busy. 

It looks "grep" command works differently if "." character is written in variable, don't know why this kind of behaviour. Work-around solution is to to replace the following string in row 19:
```
grep -v '$WHITE_PROCESSES_LIST'
```
with code
```
grep -v "$WHITE_PROCESSES_LIST"
```
So instead of single quotes use double quotes.

This should work.

If you don't like above solution, then just use "npviewer" as WHITE_PROCESS_LIST variable, so without "." character.

Please write back if you solved the problem.
Regards

Unfortunately this has not solved my problem. 

Thanks for your efforts.

Any other ideas?

---

### Post by abcuser on 2009-11-30
Hi,
what did you test?
1. double quotes in grep or
2. just use "npviewer" in WHITE_PROCESS_LIST option?

I have checked and both of this solution should work.
What is your Ubuntu version? What does command "which grep" outputs? What does command "grep --version" outputs?
Regards

---

### Post by kut77less on 2009-12-03
> **abcuser said:**
> Hi,
what did you test?
1. double quotes in grep or
2. just use "npviewer" in WHITE_PROCESS_LIST option?

I have checked and both of this solution should work.
What is your Ubuntu version? What does command "which grep" outputs? What does command "grep --version" outputs?
Regards

Thanks for your reply. This is what I have 


> #!/bin/bash
# ==============================================================
# CPU limit daemon - set PID's max. percentage CPU consumptions
# ==============================================================

# Variables
CPU_LIMIT=40       	# Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=3  	# Daemon check interval in seconds
BLACK_PROCESSES_LIST=   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.
WHITE_PROCESSES_LIST=npviewer  # Limit all processes except processes defined in this variable. If variable is empty (default) all violating processes are limited.

# Check if one of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST is defined.
if [[ -n "$BLACK_PROCESSES_LIST" &&  -n "$WHITE_PROCESSES_LIST" ]] ; then    # If both variables are defined then error is produced.
   echo "At least one or both of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST must be empty."
   exit 1
elif [[ -n "$BLACK_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | grep '$BLACK_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
elif [[ -n "$WHITE_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6' | grep -v '$WHITE_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
else
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6 && \$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
fi

# Search and limit violating PIDs
while sleep $DAEMON_INTERVAL
do
   NEW_PIDS=$(eval "$NEW_PIDS_COMMAND")                                                                    # Violating PIDs
   LIMITED_PIDS=$(ps -eo args | gawk '$1=="cpulimit" {print $3}')                                          # Already limited PIDs
   QUEUE_PIDS=$(comm -23 <(echo "$NEW_PIDS" | sort -u) <(echo "$LIMITED_PIDS" | sort -u) | grep -v '^$')   # PIDs in queue

   for i in $QUEUE_PIDS
   do
       cpulimit -p $i -l $CPU_LIMIT -z &   # Limit new violating processes
   done
done

 




The commands you told me to input said this 

> /bin/grep

and 

> GNU grep 2.5.4  

I use Ubuntu Karmic Koala 

Thanks for all your help

---

### Post by abcuser on 2009-12-14
kut77less, you are using the same system as I, so it is strange you get different result.
Can you please run you program and check what you get for output of the following command:
```
top -b -n1 -c | gawk 'NR>6' | grep -v "npviewer"
```

---

### Post by doxola on 2009-12-28
I have Hardy (8.04) and have installed the daemon.  Good work. (I also added sysvconfig per your instructions).

The only thing that doesn't work quite right on my system is as follows:

When issuing the ***sudo service cpulimit restart*** command, I receive the following output:

```
doxola@athena:~$ sudo service cpulimit restart
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
doxola@athena:~$
```

Not sure why this is, as the other commands work as they should, e.g.:

```
doxola@athena:~$ sudo service cpulimit status
 * cpulimit daemon is running
doxola@athena:~$ 
```

This is a minor issue by all accounts, as the daemon runs as its supposed to otherwise. Instead of performing the restart command, I just stop and start the daemon using the other available commands.

Again, good work!

:)

---

### Post by abcuser on 2009-12-29
> **doxola said:**
> When issuing the ***sudo service cpulimit restart*** command, I receive the following output:

```
doxola@athena:~$ sudo service cpulimit restart
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
doxola@athena:~$
```

Not sure why this is, as the other commands work as they should, 
The script tries to find cpu_daemon and execute kill command. In your sample above kill command does not get any argument, process to kill, so kill syntax help is displayed. This is actually not such a big problem, it just can't stop the daemon that is already stopped. After this command is run then start command is executed which should not produce any error.

Just to make sure if this my assumption is correct I am wondering how did you execute commands? Just wondering if you have done in the following sequence:
```
sudo service cpulimit stop
sudo service cpulimit restart
sudo service cpulimit status
```
if so, then first command (stop) killed the cpu_daemon and the second (restart) tried to kill the daemon again, but daemon was not running because it was already killed by stop command execute before this restart command. In this case this "kill syntax help error" is displayed. Then restart command also executes start, so status command correctly showed that daemon is running. So daemon couldn't be stopped because it was already stopped and was just started. Actually this is what you want.

To make it sure, please test in the following way:
```
sudo service cpulimit start
sudo service cpulimit restart
```
and then see if restart command is returning any error, it should not return the error.

If you would like to test if restart is working correctly. Then test:
1. open /etc/init.d/cpulimit file with text editor and increase sleep time from 5 to 60 seconds, so change code:
```

restart)
$0 stop
sleep 5
$0 start

```
to:
```

restart)
$0 stop
sleep **60**
$0 start

```
this will allow you to have one minute to test what is happening (after this test is over you can set it back to 5 seconds).
2. Open terminal and execute:
```

sudo service cpulimit stop

```
to stop the daemon.
3. Execute:
```

sudo service cpulimit restart

```
to restart daemon. This should print "kill syntax help error", which is just a info, not something to be doing wrong.
4. Open another terminal and check if daemon is running (don't forget you have only 60 seconds to do this, if you are slow writer, then increase to more then 60 seconds):
```

sudo service cpulimit status

```
it should report that daemon is not running, which is ok, because in step 2 you have stopped the daemon.
5. After 60 seconds start command will be executed because restart executes stop and after 60 seconds executes start.
6. Check again if cpulimit is running:
```

sudo service cpulimit status

```
and it should report that it is running.

If this is the case, then the only problem is that when restarting daemon, daemon can't be stopped because it was already stopped by "stop" command and so can't be stopped one more time, so just warning is put out "kill syntax help error", nothing to be worried about, daemon it is working fine.

If above is not working then try the following:
1. Change the code:
```

restart)
$0 stop
sleep 5
$0 start

```
to:
```

restart)
ps -eo pid,args | gawk '$3=="/root/cpulimit_daemon.sh"  {print $1}' | xargs kill -9   # kill cpulimit daemon
ps -eo pid,args | gawk '$2=="cpulimit" {print $1}' | xargs kill -9       # release cpulimited process to normal priority
sleep 5
nohup /root/cpulimit_daemon.sh &

```
So instead of stop and start aliases just use full commands from stop and restart.

Please report if this is work-around for you system.

I am at my holiday vacations and will not be using Ubuntu 8.04 until early stage of January 2010, to test this out. I would be very happy if you could test this out and report if daemon is executing as I have described in this post.

When I will have some time I will check if this error message can be avoided. So to check first if daemon is not running and to not try to kill the process that is not running. This can probably be done with some if checking but as I wrote above, I have to find some time to fix this. But it would help me much if you could test above scenario and write how restart is behaving.

Thank you very much to test this daemon and report problem you have.

---

### Post by abcuser on 2010-01-04
doxola,
I have tested the code. The problem is in "sudo service cpulimit stop". If this command is executed two times in a role then second time the error is displayed that there is no process to kill (which is correct). This is actually not a big problem, just some confusing info users are confused about.

Because "sudo service cpulimit restart" calls stop command (and then start command) the problem also appears in "restart" command, just like you have reported. It is also just annoying info, but script is working correctly.

Today I have added some if logic to check if process is stopped and if it is the script will not try to stop the process (and so reporting error), but instead it will report info, that process can't be stopped, because it is already stopped.

I have also added some additional checks in "start" command, to prevent multiple starts of the script if "sudo service cpulimit start" is executed twice or multiple times. Now scripts checks if the process is started and if it is, then it reports info, that process can't be started, because it is already running.

I have also added additional checks for start/stop/restart right after command is executed, to check if start/stop/restart was successfully executed or not and then report info of success or failure.

Doxola, thanks a lot for reporting this problem. I hope I have fixed all the problems related to this reported issue. I have changed script on the first post of this thread.
Regards

---

### Post by abcuser on 2010-01-04
malyvelky,
I have tested and I have changed the code according to your suggestion (instead of grep I have used "grep -E"), to make code working on all of Ubuntu versions. I have changed daemon and publish changes in the first post of this thread.
Thanks for testing and reporting problems.
Regards

---

### Post by abcuser on 2010-01-05
Hi,
today I have added some major changes to boot-up script, with additional checkings, which makes script more stable if manually using start/stop/restart service commands.

I have also rewritten tutorial to add new info and remove as much confusion as possible.

I would be very happy if you could test this daemon script and report, if it is working for you. Also post here if you would like to have any additional functionality.
Regards

---

### Post by pranaynewton on 2010-07-04
Hi,

I don't know if this is the appropriate thread for this question but here goes..

I am running ubuntu on an embedded board( gumstix overo fire) which has an ARM cortex-A8 600Mhz. I am using it to run an algorithm which is initiated every 100ms as new data comes in from a sensor.

My algorithm takes about 30ms-50ms to run. When i ran top i noticed that it is using only 30% cpu resources. Is there anyway to make the code utilize cpu more effectively?

I have tried using nice -20. Or is it showing 30% as the code is running only for 30ms every 100ms and hence is utilizing CPU effectively?

Any help would be appreciated.

Pranay

---

### Post by ebrajoh on 2010-08-18
I just wanted to say that could not get the startup script to work on centos 5.3 without removeing the following line:
. /lib/lsb/init-functionsing

---

### Post by abcuser on 2010-08-19
@ebrajoh, you are most probably right. I have just copied the following header:
```
#!/bin/sh
#
# Script to start CPU limit daemon
#
set -e
. /lib/lsb/init-functions

```
from some other script and didn't really check if they are really needed.

---

### Post by abcuser on 2010-08-20
pranaynewton, you should probably open new thread because this thread if for making limitation on CPU using and you would like to do vise-versa.

It looks like in your case the bottleneck is not a CPU. So you can't use more then 30% CPU if there is no need to use it more.

---

### Post by abcuser on 2010-08-20
> **ebrajoh said:**
> I just wanted to say that could not get the startup script to work on centos 5.3 without removeing the following line:
. /lib/lsb/init-functionsing
@ebrajoh, I have just copied this line from some other script and now I have tested the script **without** this line on Ubuntu 8.04 LTS and Ubuntu 10.04 LTS and it is working fine. So I have updated the first post in this thread (deleted the line from script). Thanks a lot for posting this issue. Now it should also work on centos.

I have also made some minor changes in tutorial, to make it more clear. E.g. scripts must be saved with root privileges otherwise system will report "no privileges to save a file".

If you find some bugs in scripts or tutorial please post it on this forum. Also post a note if you have some suggestion how to improve tutorial/scripts.

---

### Post by quequotion on 2010-09-18
On 10.04 i can't get the daemon to start...
```
$ sudo service cpulimit start
 * cpulimit daemon can not be started
$
```

I've changed one part, and put the script in /usr/local/sbin (where I keep all user scripts), but I made sure to make the appropriate changes to /etc/init.d/cpulimit.... other than that I followed the guide.

---

### Post by abcuser on 2010-09-19
@quequotion, can you please do the following:
1. Check if the file is in this path and what are permissions on file:
```
ls -l /usr/local/sbin/cpulimit_daemon.sh
```
2. Before starting a cpulimit daemon please execute the following command to list if daemon is already started.
```
ps -eo pid,args | gawk '/cpulimit_daemon/'
```
3. Please also execute this command to check if some process of cpulimit is already running:
```
ps aux | grep cpulimit | grep -v grep
```
4. Try to manually start a cpulimit daemon:
```
sudo service cpulimit start
```
(this will most probably produce the error in your case)
5. Now execute the command from step 2 again.
6. Now execute the command from step 3 again.
Please post the output of all 6 steps.

Can you please also post the script from /etc/init.d/cpulimit to see if you made a proper changes.

---

### Post by piter.cr on 2010-12-04
great tip

works quite good
thanks

---

### Post by onemyndseye on 2010-12-17
Thanks for this. It was most helpful for my home media server ...

I had to make some changes for my needs though as your method for polling for limited PIDs was always returning null...  I ended up rewriting abit but the key change was the line:


```

 LIMITED_PIDS=$(ps -eo args | gawk '$1=="cpulimit" {print $3}')
## changed to (more explaination below) ##
 LIMITED_PIDS=$(ps -eo args | grep cpulimited-bin |grep -v grep |awk '{print $3}')

```


I needed a version with start/stop built in and also wanted logging.. So my finial code which is still being tested is:

cpulimited.sh
```

#!/bin/bash
# ==============================================================
# CPU limit daemon - set PID's max. percentage CPU consumptions
# ==============================================================
# Variables
CPU_LIMIT=25                   # Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=3              # Daemon check interval in seconds
LOG=/var/log/cuplimited.log
CPULIMITED_TMPDIR=/tmp/cpulimited
CONFIG=/etc/cpulimited/cpulimited.conf

BLACKLIST=0
WHITELIST=0
PROCESSES_LIST=

do_help() {
cat <<EOF
Usage:  $0 <options> start|stop
                     -f   ::  Run in foreground
       -c <config file>   ::  Use specified config file

EOF
exit 0
}
do_cpuwatcher() {

# Search and limit violating PIDs
while [ -z "$EXIT" ]; do
   sleep $DAEMON_INTERVAL
   # Check for exit
   DCMD=$(cat "$CONTROL_FILE" |tail -n 1)
   if [ "$DCMD" = "exit" ]; then
     echo "Shutdown requested..."
     PIDS="$(ps ax |grep cpulimited-bin |awk '{print $1}')"
     echo "Removing CPU limits ..."
     kill -9 $PIDS >/dev/null 2>&1
     sleep 1
     cd /tmp
     echo "Cleaning up ..."
     rm -rfd $CPULIMITED_TMPDIR
     echo "Goodbye"
     EXIT=1
     exit 0
   fi
   NEW_PIDS=$(eval "$NEW_PIDS_COMMAND")
   LIMITED_PIDS=$(ps -eo args | grep cpulimited-bin |grep -v grep |awk '{print $3}')
   QUEUE_PIDS=$(comm -23 <(echo "$NEW_PIDS" | sort -u) <(echo "$LIMITED_PIDS" | sort -u) | grep -v '^$')
   if [ -n "$QUEUE_PIDS" ]; then
     echo "These PIDs are already limited: $LIMITED_PIDS"
     echo "These PIDs are now entering the queue: $QUEUE_PIDS"
   fi
   for i in $QUEUE_PIDS; do
        echo "Setting limits for PID: $i"
        if [ -z "$FOREGROUND" ]; then
           ./cpulimited-bin -p $i -l $CPU_LIMIT -z >>$LOG 2>&1 &
        else
           ./cpulimited-bin -p $i -l $CPU_LIMIT -z &
        fi
   done
done
exit 0
}


# Init
##  Process commandline options
while [ "$1" ]; do
   case "$1" in
     -f)
         FOREGROUND=1
         shift 1
      ;;
     -c)
         CONFIG=$2
         shift 2
      ;;
  start)
         CMD=start
         shift 1
         break
       ;;
   stop)
         CMD=stop
         shift 1
         break
      ;;
      *)
       do_help
       break
   esac
done
if [ -z "$CMD" ]; then
  do_help
  exit 0
fi


[ -f $CONFIG ] && . $CONFIG
if [ $BLACKLIST = 1 -a $WHITELIST = 1 ]; then
   echo "Cannot use both whitelist AND blacklist.  Please check your config"
   exit 1
else
   if [ "$BLACKLIST" = "yes" ]; then
     MODE=blacklist
     NEW_PIDS_COMMAND="top -b -n1 -c | grep -E '$BLACK_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
   fi
   if [ "$WHITELIST" = "yes" ]; then
     MODE=whitelist
     NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6' | grep -E -v '$WHITE_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
   fi
   if [ -z "$MODE" ]; then
     MODE=supervisor
     NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6 && \$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
   fi
fi

##########  END Init ############


case "$CMD" in
   start)
       echo "Starting up in $MODE mode ..."
       if [ -d $CPULIMITED_TMPDIR ]; then
         echo "Already running or stale tmp directory detected. Aborting ..."
         exit 23
       else
         mkdir -p $CPULIMITED_TMPDIR
         CONTROL_FILE="${CPULIMITED_TMPDIR}/control"
         chown -R root:root $CPULIMITED_TMPDIR
         chmod 700 $CPULIMITED_TMPDIR
         cd $CPULIMITED_TMPDIR
         CPULIMIT=$(which cpulimit)
         ln -s $CPULIMIT cpulimited-bin
         touch $CONTROL_FILE
         if [ -n "$FOREGROUND" ]; then
           # Do not fork
           do_cpuwatcher
         else
           # Fork into the background
           do_cpuwatcher >>$LOG &
         fi
       fi
       ;;
    stop)
        echo "Sending stop signal ..."
        CONTROL_FILE="${CPULIMITED_TMPDIR}/control"
        echo "exit" >$CONTROL_FILE
      ;;
esac

```

I set a temp directory up for the script and symlinked /usr/bin/cpulimit to ./cpulimited-bin to ease in grep'ing for cpulimit processes spawned by this script. I also added the ability to set changes from a config file.  The other change is that BLACKLIST/WHITELIST is a mode toggle (0/1) and PROCESS_LIST would contain the strings to act on...   Most all other changes were simply stylistic.

Thanks again! :)

---

### Post by Cammer Pants on 2011-05-28
First, I want to thank you for this information. Second, I'd like to confess that for the life of me, I cannot figure out how to make cpulimit work properly with a multi-core processor.

I see numerous posts both on these forums and elsewhere claiming that the limit can be a multiple of 100% based on the number of processors the machine has. I have four processors (phenom II 840 @3.2 ghz), and yet, cpulimit will not allow me to set any limit higher than 100%.

I see this error when I try: 

"Error: limit must be in the range 0-100"

Additionally, the help message states:

"percentage of cpu allowed from 0 to 100 (mandatory)"

I thought maybe I would be clever and run the top command followed by <shift> i to switch the irix mode. This did not work either. If I input 90& in cpulimit, top then displays that I am using 22% of processing time.

In other words, I cannot figure out how to make it believe that I have a multi-core processor.

---

### Post by abcuser on 2011-05-30
Hi,
can you please check the number of CPUs (cores) on you computer with command:
```
cat /proc/cpuinfo | grep processor | wc -l
```
Thanks

---

### Post by Cammer Pants on 2011-06-01
> **abcuser said:**
> Hi,
can you please check the number of CPUs (cores) on you computer with command:
```
cat /proc/cpuinfo | grep processor | wc -l
```
Thanks

Yes, the command gives me "2" on my laptop. I am away from my desktop as I am currently traveling, but I can assure you that the desktop is 4. 

The laptop is a core 2 duo t7500 @ 2.2 gz and the desktop is a phenom 2 840 X4 @ 3.2 gz. 

This issue occurs on both systems. If it makes a difference, I installed cpulimit from the ubuntu repos in both maverick (on the laptop) and natty on the desktop. Thank you.

---

### Post by abcuser on 2011-06-05
> **Cammer Pants said:**
> This issue occurs on both systems. If it makes a difference, I installed cpulimit from the ubuntu repos in both maverick (on the laptop) and natty on the desktop.
I see the main problem is not with my script but with cpulimit in the first place. I suggest to open a bug report with command in Terminal:
```
ubuntu-bug cpulimit
```
You have to register in Launcphad. See more info: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by MaxBux on 2011-09-15
Thanks for the scripts abcuser. 

I was having processor issues on Amazon EC2 (Ubuntu 10.04.3 LTS 64bit server) and this has really helped me out.

However, I had to change 

```
sudo chmod 700 /usr/bin/cpulimit_daemon.sh
```

to 

```
sudo chmod 755 /usr/bin/cpulimit_daemon.sh
```

for the daemon wouldn’t start

```
* cpulimit daemon can not be started
```

Thanks again
MaxBux

---

### Post by abcuser on 2011-09-15
MaxBux, maybe you opened file with different user then specified in documentation and so you get other owner then you should.

Anyway I have updated instruction in my first post with your recommendation (755 instead 0f 700), just to avoid someone else having the same problem.

Thanks for reporting this issue.

---

### Post by davidparks21 on 2011-10-31
Thanks for all the effort of putting up this script and helping us out with it, it's exactly what I need. 

I have been running it for about a week and found my system overrun by about 400+ cpulimit processes running (count as of today).

The phenomenon appears to be cpulimit limiting itself (I have it set to limit anything over 3%).

Here is one example of the 400, every PID I took from the -p argument was a cpulimit process its self (I check 4 or 5 examples)

```
root      6114 20975  0 Oct29 ?        00:02:30 cpulimit -p 1061 -l 3 -z
root     13470 20975  0 Oct30 ?        00:02:18 cpulimit -p 6114 -l 3 -z
```

Here are my varilables in cpulimit_daemon.sh, I installed the script as suggested in this thread:


```
# Variables
CPU_LIMIT=3             # Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=2       # Daemon check interval in seconds
BLACK_PROCESSES_LIST=   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.
WHITE_PROCESSES_LIST="openvpn|squid|log_helper|url_rewrite_helper|ssh|nrpe"   # Limit all processes except processes defined in this variable. If variable is empty (default) all violat$
```

I'm going to try fixing this by whitelisting cpulimit.  :D

But even if that's the solution it's worth a report here.

---

### Post by El_Belgicano on 2011-10-31
Whitelisting cpulimit should be good, but IMHO setting everything to be limited at 3% is kind of low, don't you start to notice everything going slower?
I tend to think the other way round, and i got a few processes in my blacklist, the rest can go on... No noticeable unwanted slowdowns... For example I got mencoder limited at 40%: everything else stays (most of the time) within reasonable boundaries, so no need to slow them down...

---

### Post by davidparks21 on 2011-10-31
I figured someone would comment on 3%. :)  It's on an AWS micro box. Sustained CPU over about 5% will cause AWS to trigger a near shutdown of the box (98% stolen cpu). Unless the process bursts up and down (such as is the case with the limited whitelisted processes). Anything else *must* be limited to avoid triggering the AWS limiter. Typically cron jobs trigger the AWS limiter when I'm not looking. 

Basically the whitelisted processes are the only ones I care about and and have tested, the rest should mozy on through life at an easy pace.

---

### Post by El_Belgicano on 2011-11-01
What an interesting box you have there... ;-)

---

### Post by abcuser on 2011-11-01
@El_Belgicano: If you execute mencoder randomly then daemon can be useful, but if you would like to omit only single process and doing this ones per some time, then you do not need cpu_limit daemon script. You can just execute the cpulimit command with process id for mencoder.

@davidparks21: Thanks for bringing this issue out. Limiting processes to 3% is actually very specific problem. In this case it can easily happen that cpulimit program is caught in a 3% cpu limit by deamon. In this case I suggest to whitelist the cpulimit process.

---

### Post by El_Belgicano on 2011-11-01
> **abcuser said:**
> @El_Belgicano: If you execute mencoder randomly then daemon can be useful, but if you would like to omit only single process and doing this ones per some time, then you do not need cpu_limit daemon script. You can just execute the cpulimit command with process id for mencoder.

Mostly i run mencoder through a script, thus if i follow your thinking, i could change my script from:```
...
mencoder [...] &
...
```
to:```
...
mencoder [...] &
cpulimit -e mencoder -l 40 & (exact parameters to be investigated...)
...
```
and this instance (assuming there are never two mencoders running at the same time) would be limited to 40% cpu without the daemon part having to remind the process it is limited...?

Could be good for the pc, i'm looking to trim it's idling ram at a minimum, i'm stuck at 45MB atm... i could save a few more MB's without the daemon...

Thanks for the input...

---

### Post by abcuser on 2011-11-03
> **El_Belgicano said:**
> Mostly i run mencoder through a script, thus if i follow your thinking, i could change my script 
In you case I would create a bash file line on destkop or something and then just double click on it to run mencoder.
The code could be something like:
```
#!/bin/bash
mencoder... 
PID=$(ps -eo pid | grep "mencoder..." | grep -v grep | gawk '{print $1}')
cpulimit -p $PID -l 40 -z
```

> **El_Belgicano said:**
> 
Could be good for the pc, i'm looking to trim it's idling ram at a minimum, i'm stuck at 45MB atm... i could save a few more MB's without the daemon...
I am sceptical about this statement. I don't think you will preserve much of RAM, specially not mega bytes. But you can test the code and I would be happy to see the results how many RAM you have spare.

---

### Post by El_Belgicano on 2011-11-03
> **abcuser said:**
> In you case I would create a bash file line on destkop or something and then just double click on it to run mencoder.
The code could be something like:
```
#!/bin/bash
mencoder... 
PID=$(ps -eo pid | grep "mencoder..." | grep -v grep | gawk '{print $1}')
cpulimit -p $PID -l 40 -z
```

For now i modified my script to:
```
cpulimit -e mencoder -l 25 &
mencoder [...]
killall cpulimit &
```
Now i have two questions:
- What if i put two mencoder lines instead of one, would they both respect the speed limit?
- Any idea on how to be more "elegant" than killall? I feel like a butcher now...

> **abcuser said:**
> I am sceptical about this statement. I don't think you will preserve much of RAM, specially not mega bytes. But you can test the code and I would be happy to see the results how many RAM you have spare.

Well, without the daemon running i can spare a MB or two while idle... since no unexpected process has to be limited, starting cpulimit when needed sounds lighter...

---

### Post by abcuser on 2011-11-05
> **El_Belgicano said:**
> 
- What if i put two mencoder lines instead of one, would they both respect the speed limit?
In this case then I suggest to use code already discussed on post #14, but in your case use mencoder, like bellow.
```

#!/bin/bash
PIDS=$(ps -eo pid | grep "mencoder" | grep -v grep | gawk '{print $1}')
for i in $PIDS
do
    cpulimit -p $i -l 40 -z &
done

```

> **El_Belgicano said:**
> 
- Any idea on how to be more "elegant" than killall? I feel like a butcher now...

Killing is never elegant. :) I don't see any point of changing this command if it is working fine.

> **El_Belgicano said:**
> 
Well, without the daemon running i can spare a MB or two while idle... since no unexpected process has to be limited, starting cpulimit when needed sounds lighter...
Interesting findings, thanks for sharing the info. Sparing RAM is very important on netbooks. I have never thought of RAM usage because of having several GB of RAM on PC and I can spare one or two MB.

---

### Post by El_Belgicano on 2011-11-05
> **abcuser said:**
> In this case then I suggest to use code already discussed on post #14, but in your case use mencoder, like bellow.
```

#!/bin/bash
PIDS=$(ps -eo pid | grep "mencoder" | grep -v grep | gawk '{print $1}')
for i in $PIDS
do
    cpulimit -p $i -l 40 -z &
done

```

Is there any hidden advantage to prefer "-p" over "-e"?
Right now i'm using:```
function encode()
{
	mencoder [...] (first pass)
	mencoder [...] (second pass)
}
cpulimit -e mencoder -l 20 &
encode [args1]
encode [args2]
killall cpulimit &
```
It's looking like the 20% is being respected for all "mencoder" lines in the speed limited zone... Not done testing though, the script is running right now...

> **abcuser said:**
> Killing is never elegant. :) I don't see any point of changing this command if it is working fine.
Then i'll keep feeling like a butcher...

> **abcuser said:**
> Interesting findings, thanks for sharing the info. Sparing RAM is very important on netbooks. I have never thought of RAM usage because of having several GB of RAM on PC and I can spare one or two MB.

I got 512MB of RAM on that laptop, but for some time now i've been looking to make it as light as possible while idle... Where i'm now, even going from a colored root window to using an image as wallpaper means a change from 42-43 to 45-47 MB (with X, ssh, mpd -paused- and a conky)

---

### Post by abcuser on 2011-11-07
> **El_Belgicano said:**
> Is there any hidden advantage to prefer "-p" over "-e"?

In this case it is not. But in my script in #1 post there is easier to track which PIDs are already cpulimited and which are not by using uniq process ID.

---

### Post by davidparks21 on 2011-11-07
Well, I'm no longer having cpulimit its self, but when I checked on cpulimit again today (after running a few days) I see that I have cpulimit processes on 2 of the whitelist processes. I'm perplexed.

I tried taking the base command: 

```
top -b -n1 -c | gawk 'NR>6' | grep -E -v 'my|whitelist|processes'
```

And it does indeed exclude the processes that I see limited.

Before I run off and hack up the script with a ton of debug statements and painfully monitor it for the next few days I thought I'd see if this perks anyones ears.

My configuration on the cpulimit_daemon.sh is below, everything else is out-of-the-box as is laid out in this post.


```
#!/bin/bash
# ==============================================================
# CPU limit daemon - set PID's max. percentage CPU consumptions
# ==============================================================

# Variables
CPU_LIMIT=3             # Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=2       # Daemon check interval in seconds
BLACK_PROCESSES_LIST=   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.
WHITE_PROCESSES_LIST="openvpn|squid|log_helper|url_rewrite_helper|ssh|nrpe|cpulimit|statusreader"   # Limit all processes except processes defined in this variable. If variable is empty (default) all violating processes are limited.

```


**ps -ef | grep cpulimit**
```
root      5833 32058  0 21:06 ?        00:00:01 cpulimit -p 5774 -l 3 -z
root     13439 32058  0 Nov03 ?        00:07:04 cpulimit -p 951 -l 3 -z
root     14018 32058  0 Oct31 ?        00:10:18 cpulimit -p 5655 -l 3 -z
root     15825 32058  0 Nov01 ?        00:10:07 cpulimit -p 614 -l 3 -z
root     20063 32058  0 Nov01 ?        00:09:43 cpulimit -p 1 -l 3 -z
root     32657 32058  0 Nov03 ?        00:06:09 cpulimit -p 501 -l 3 -z
```

**Those PIDs**
```
1001      5774  5772  0 21:06 pts/0    00:00:01 -bash
[COLOR="red"]root       951     1  0 Oct24 ?        00:05:54 /bin/bash /opt/openvpn/bin/statusreader[/COLOR]
[COLOR="Red"]root      5655     1  0 Oct24 ?        00:11:31 /bin/bash /opt/squid/bin/log_helper[/COLOR]
root       614     1  0 Oct24 ?        00:05:21 /usr/sbin/vnstatd -d
root         1     0  0 Oct24 ?        00:36:17 /sbin/init
syslog     501     1  0 Oct24 ?        00:06:35 rsyslogd -c5
```

---

### Post by abcuser on 2011-11-08
This is strange problem, I never faced the problem of this kind. Did you change some WHITE_PROCESSES_LIST variable like adding "openvpn" string to the variable and forgot to restart daemon?

=== From first post of this thread ===
**Restart cpulimit service**
If you change some variables settings in /usr/bin/cpulimit_daemon.sh like CPU_LIMIT, DAEMON_INTERVAL, BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST, then after changing settings you must restart service.
```
sudo service cpulimit restart
```

---

### Post by davidparks21 on 2011-11-08
I'm 99% sure I stopped it and verified the processes, but that 1% uncertainty has a nasty tendency to assert its self. I've stopped/started and verified no cpulimit/cpulimit_daemon.sh processes. 

I'll post again after I look into it further in the next few days.

Thanks!
Dave

---

### Post by davidparks21 on 2011-11-09
No luck, restarted and verified all cpulimit processes were gone, today I see it limiting 2 processes in the whitelist. Odd, I'll add some debug statements and will report back.

---

### Post by abcuser on 2011-11-11
David,
why do you execute program like this:
/bin/bash /opt/openvpn/bin/statusreader
/bin/bash /opt/squid/bin/log_helper

Are this bash scripts? If you open this two files what is the first statement in the file? Is it #!/bin/bash if yes, then you don't need to execute it like /bin/bash some_program, just execute it /opt/openvpn/bin/statusreader
If #!/bin/bash is not added, can you manually add this line at firt line position and execute the program with /opt/openvpn/bin/statusreader

I am not 100% sure, but space in the process name can cause some problems. I haven't test this, but it is possible that "openvpn" is searched in "/bin/bash" column, where nothing is found out.
Regards

---

### Post by hg088 on 2011-12-15
hi!

i have an i7 2600k which has 4 cores (8 with ht)

i was trying to limit the folding@home process to about 50% of the total cpu, because on full load the cpu gets really hot (been saving to buy a good heat sink)

so, the problem is that when i try to set --limit=400 (cause the max is 800), cpulimit wont actually limit, not even if i set it to 100 or any other number above 100

but, if i set --limit=99 cpu overall usage goes to 14% on conky, and 99% on top

anyway i was hoping some here would help me to get cpu limit to actually limit a process to 50% of my cpu (400% on top)

---

### Post by edanny191 on 2012-08-18
Hi, 
Thank you for the great job,
I'm trying to use your scrip on Fedora with a few changes.
In /etc/init.d/cpulimit scrip I added
```
#!/bin/sh
#
# Script to start CPU limit daemon
#
# chkconfig: 2345 99 99
#
# description: Starts cpulimit processes for all
``` 

And instead of
```
update-rc.d cpulimit defaults
```
I did
```
chkconfig --add cpulimit
```

All looks good
```
service cpulimit status
*cpulimit daemon is running
```
But in services shows that "This unit has finished."
```
system-config-services
```

My question is, Is this unit should keep running? If yes, How can I change it to the unit is running? 

Thanks in advance.
Cheers
Danny

---

### Post by abcuser on 2012-08-19
@edanny191, maybe "system-config-services" requires something more from daemon to do, to be recognized as "running service". Program "system-config-services" is Fedora specific (not available on Ubuntu - or if it is, it's not there by default), so I am probably not be able to help you out with this problem, because I am not a Fedora user. You should probably ask on Fedora forum, something like:
Bash script is executed in while-do infinite loop using "chkconfig --add" command and bash process resists in memory and working fine, but "system-config-services" reports "This unit has finished". Is there some additional requirement to be done by bash script to be fully recognized as 'running service'?


On the other hand, just for explanation "service cpulimit status" executes the code I have written, with 'ps' command it just checks if process /usr/bin/cpulimit_daemon.sh is still running and if it is it outputs "*cpulimit daemon is running". Bellow is full code if it helps:

```

ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon is running"; else print " * cpulimit daemon is not running" }'

```

The simpliest way of checking if daemon is working fine is to execute some CPU intensive task and check with 'top' command if CPU consumption is omitted or not. See "6. CHECK CPU CONSUMPTION WITH OR WITHOUT CPULIMIT DAEMON" chapter in HowTo for details.

P.S. Please report on this forum if you found out the solution.
Regards

---

### Post by El_Belgicano on 2012-08-19
Thanks for the script, very useful!
I just did a few modifications for my specific use, but one of them could be useful to more people:
```
start)
if [ $(ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print $1}' | wc -l) -eq 0 ]; then
    nohup /usr/bin/cpulimit_daemon.sh >/dev/null 2>&1 &
    [COLOR="DarkOrange"]sleep 1[/COLOR]
    ps -eo pid,args | gawk '$3=="/usr/bin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon started successfully"; else print " * cpulimit daemon can not be started" }'
else
    echo " * cpulimit daemon can't be started, because it is already running"
fi
;;
```
This is because when issuing "sudo service start" it would tell me "daemon not started" but doing "sudo service status" right after would tell me it is actually running, sleep 1 fixes this...

---

### Post by edanny191 on 2012-08-19
Thank you,
I made few changes again and the problem solved,
Here you are:
```
[root@pc ~]# gedit /usr/local/sbin/cpulimit_daemon.sh
```
```
#!/bin/bash
# ==============================================================
# CPU limit daemon - set PID's max. percentage CPU consumptions
# ==============================================================
#
ADDR=root@localhost
#
# Variables
CPU_LIMIT=20       	# Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=3  	# Daemon check interval in seconds
BLACK_PROCESSES_LIST=   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.
WHITE_PROCESSES_LIST=   # Limit all processes except processes defined in this variable. If variable is empty (default) all violating processes are limited.

# Check if one of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST is defined.
if [[ -n "$BLACK_PROCESSES_LIST" &&  -n "$WHITE_PROCESSES_LIST" ]] ; then    # If both variables are defined then error is produced.
   echo "At least one or both of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST must be empty."
   exit 1
elif [[ -n "$BLACK_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | grep -E '$BLACK_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
elif [[ -n "$WHITE_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6' | grep -E -v '$WHITE_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
else
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6 && \$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
fi

# Search and limit violating PIDs
while sleep $DAEMON_INTERVAL
do
   NEW_PIDS=$(eval "$NEW_PIDS_COMMAND")                                                                    # Violating PIDs
   LIMITED_PIDS=$(ps -eo args | gawk '$1=="cpulimit" {print $3}')                                          # Already limited PIDs
   QUEUE_PIDS=$(comm -23 <(echo "$NEW_PIDS" | sort -u) <(echo "$LIMITED_PIDS" | sort -u) | grep -v '^$')   # PIDs in queue

   for i in $QUEUE_PIDS
   do
       cpulimit -p $i -l $CPU_LIMIT -z &   # Limit new violating processes
   done
done
```
```
[root@pc ~]# chmod 755 /usr/local/sbin/cpulimit_daemon.sh
```
```
[root@pc ~]# gedit /etc/rc.d/init.d/cpulimit
```
```
#!/bin/sh
#
# Script to start CPU limit daemon
#
#chkconfig:     35 99 01
#
# Source function library.
. /etc/rc.d/init.d/functions
[ -f /usr/local/sbin/cpulimit_daemon.sh ] || exit 0
set -e

case "$1" in
start)
if [ $(ps -eo pid,args | gawk '$3=="/usr/local/sbin/cpulimit_daemon.sh"  {print $1}' | wc -l) -eq 0 ]; then
    nohup /usr/local/sbin/cpulimit_daemon.sh >/dev/null 2>&1 &
    ps -eo pid,args | gawk '$3=="/usr/local/sbin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon started successfully"; else print " * cpulimit daemon can not be started" }'
else
    echo " * cpulimit daemon can't be started, because it is already running"
fi
;;
stop)
CPULIMIT_DAEMON=$(ps -eo pid,args | gawk '$3=="/usr/local/sbin/cpulimit_daemon.sh"  {print $1}' | wc -l)
CPULIMIT_INSTANCE=$(ps -eo pid,args | gawk '$2=="cpulimit" {print $1}' | wc -l)
CPULIMIT_ALL=$((CPULIMIT_DAEMON + CPULIMIT_INSTANCE))
if [ $CPULIMIT_ALL -gt 0 ]; then
    if [ $CPULIMIT_DAEMON -gt 0 ]; then
        ps -eo pid,args | gawk '$3=="/usr/local/sbin/cpulimit_daemon.sh"  {print $1}' | xargs kill -9   # kill cpulimit daemon
    fi

    if [ $CPULIMIT_INSTANCE -gt 0 ]; then
        ps -eo pid,args | gawk '$2=="cpulimit" {print $1}' | xargs kill -9                    # release cpulimited process to normal priority
    fi
    ps -eo pid,args | gawk '$3=="/usr/local/sbin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon can not be stopped"; else print " * cpulimit daemon stopped successfully" }'
else
    echo " * cpulimit daemon can't be stopped, because it is not running"
fi
;;
restart)
$0 stop
sleep 3
$0 start
;;
status)
ps -eo pid,args | gawk '$3=="/usr/local/sbin/cpulimit_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * cpulimit daemon is running"; else print " * cpulimit daemon is not running" }'
;;
esac
exit 0
```
```
[root@pc ~]# chown root:root /etc/rc.d/init.d/cpulimit
```
```
[root@pc ~]# chmod 755 /etc/rc.d/init.d/cpulimit
```
```
[root@pc ~]# chkconfig --add cpulimit
```
```
[root@pc ~]# service cpulimit status
 * cpulimit daemon is not running
```
```
[root@pc ~]# service cpulimit restart
Restarting cpulimit (via systemctl):                       [  OK  ]
```
```
[root@pc ~]# service cpulimit status
 * cpulimit daemon is running
```
And in system-config-services shows, This unit is running.
I'll check it for bugs and hope other help me too.

Thanks again,
Cheers
Danny

---

### Post by brettgavin on 2012-10-04
Hi,
 
Thank you for your work on these topic! It has helped me a ton so far.
 
I am trying to limit the Plex Transcoder process so that I can run multiple video streams. I can successfully limit it manually, over and over for each process instance, without issue. When I use the scripts that you've built, it does indeed work for me, but I have to use the more generic command title "plex" 
```
BLACK_PROCESSES_LIST="plex" 
```
 
The actual command title is "Plex Transcoder". 
 
When I use "plex" it seems to interfere with the streaming service or something causing all streams, even if it's just one, to pause or buffer about every minute or so.
 
 
If I set the blacklist to 
```
BLACK_PROCESSES_LIST="'/usr/lib/plexmediaserver/Resources/Plex Transcoder'" 
``` 
then, I receive the output 
```
$sudo cpulimit_daemon.sh
grep: Transcoder: No such file or directory
```

If I use
```
BLACK_PROCESSES_LIST="`/usr/lib/plexmediaserver/Resources/Plex\ Transcoder`" 
``` 
it seems to work, but the output reads:
```
/usr/lib/plexmediaserver/Resources/Plex Transcoder: error while loading shared libraries: libass.so.4: cannot open shared library object file: No such file or directory
```

 
If I use
```
BLACK_PROCESSES_LIST="'/usr/lib/plexmediaserver/Resources/Plex\ Transcoder'" 
``` 
or 
```
BLACK_PROCESSES_LIST="Plex\ Transcoder"
```
I don't receive an error, but it does not effect the instance(s) of Plex Transcoder.
 
here is the output from "top -b -n1 -c"
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3421 plex      15  -5 1179m 213m 4896 R  362  5.4   7:02.50 /usr/lib/plexmediaserver/Resources/Plex Transcoder transcode [http://127.0.0.1:32400/library/parts/657/file.mkv](http://127.0.0.1:32400/library/parts/657/file.mkv) /tmp/plex-transcode-EADFE28A-3CE5-41A9-9EAE-9E04DC167EC7-331029a38c1ce49d4241869aac9baa11243701a3/media 7 4 27 1 nil 2 yes UTF-8
```
 
 
Is it possible to blacklist a process with a _space_ in its name?
 
Am I using the wrong variable for the blacklist?
 
 
Thanks in advance!

---

### Post by abcuser on 2012-10-05
@brettgavin, I investigated this problem and it looks like if there is a space in process name then script does not work, error is produced by "grep -E" command.

According to the grep documentation syntax for BLACK_PROCESS_LIST variable should be:
```

BLACK_PROCESSES_LIST='Plex[[:blank:]]Transcoder'

```

Please report back if this solves the problem.

P.S. Still don't understand why programs in Linux use spaces in file name - this just produces problems...
Thanks

---

### Post by brettgavin on 2012-10-05
@abcuser, 
 
Thank you for looking into this a little further. I'm can't wait to get this working!
 
I have tried the following combinations:
 
1:
```
BLACK_PROCESSES_LIST='Plex[[:blank:]]Transcoder'
```
 
2:
```
BLACK_PROCESSES_LIST="Plex[[:blank:]]Transcoder"
```
 
3:
```
BLACK_PROCESSES_LIST='/usr/lib/plexmediaserver/Resources/Plex[[:blank:]]Transcoder'
```
 
4:
```
BLACK_PROCESSES_LIST="/usr/lib/plexmediaserver/Resources/Plex[[:blank:]]Transcoder"
```
 
5:
```
BLACK_PROCESSES_LIST="`/usr/lib/plexmediaserver/Resources/Plex[[:blank:]]Transcoder`"
```
 
I know you said last night that your script is not designed to accept direct paths, #3, 4, and 5, and while #3 and #4 do not work, #5 does work. The only thing is that it still kicks out the libass.so.4 error. I posted a question in the Plex forums about this file, but haven't had a response, yet.
 
==============
 
 
While writing this, I just tried this on a whim:
 
```
BLACK_PROCESSES_LIST="`Plex\ Transcoder`"
```
 
When manually starting the daemon, it immediately outputs:
 
```
/usr/bin/cpulimit_daemon.sh: line 9: Plex Transcoder: command not found
```
 
I thought this was a sign of it not working. It turns out, it seems, that it may simply be a notification that the process command name is not found in the currently running processes. As soon as I start and/or stop a video, as expected, the output reads
```
Process XXXX detected
Process XXXX dead!
``` 
 
If the "command not found" is an acceptable output from your script, this may work just fine for me. I'm going to test it out with multiple streams in a little bit. I have a meeting to go to right now.
 
 
Thank you for your time!

---

### Post by abcuser on 2012-10-05
> **brettgavin said:**
> 
5:
```
BLACK_PROCESSES_LIST="`/usr/lib/plexmediaserver/Resources/Plex[[:blank:]]Transcoder`"
```
 
I know you said last night that your script is not designed to accept direct paths, #3, 4, and 5, and while #3 and #4 do not work, #5 does work. The only thing is that it still kicks out the libass.so.4 error.

Using above command with "`" character it means EXECUTE program in quotes and set output to variable BLACK_PROCESS_LIST. I don't think this is going to be working correctly, because executing a program in my humble opinion will not output a program name. I would be really surprised if this works out.

---

### Post by brettgavin on 2012-10-05
Please forgive my limited understanding of scripting. I took some classes many years ago, but I dont remember a ton of it. 
 
I understand what you're saying about the backticks actually executing a program. Do you think it works because the program name and the command name appear to be identical?
 
 
----
 
Using this:
 
```
BLACK_PROCESSES_LIST="`Plex\ Transcoder`"
```
 
I set the daemon interval to 60 to give the transcoder a chance to process enough video at the beginning to avoid unnecessary buffering.
 
It seems to work fine, even with that simple output message about the command not being found (this only appears when running the script manually; does not appear on boot).
 
Here are a couple screenshots:
 
before 60s check
[IMG]http://i.imgur.com/cjbVH.png[/IMG]
 
after 60s check
[IMG]http://i.imgur.com/u1m86.png[/IMG]
 
----
 
If this does continue to work well, I have one more idea that I could use your help with. 
 
I would like to be able to set the daemon to check every x seconds (like you have it setup) but upon finding the blacklisted command, wait one additional interval cycle before enacting the cpulimit function. Do you have an idea of how to go about this?

---

### Post by brettgavin on 2012-10-05
@abcuser Here is a link to my post and setup instructions that you helped me get working:
 
[http://brettgavin.wordpress.com/](http://brettgavin.wordpress.com/)
 
Here is the Plex forum post about it as well:
 
[http://forums.plexapp.com/index.php/topic/48265-howto-plex-setup-for-many-simultaneous-streams/](http://forums.plexapp.com/index.php/topic/48265-howto-plex-setup-for-many-simultaneous-streams/)

---

### Post by david.rahrer on 2012-11-11
I have set up the version of this script from Sept 2010 as [found here]("http://maketecheasier.com/limit-cpu-usage-of-any-process-in-linux/2010/09/22").  While it seems to work fine in general, I have an issue that I don't see mentioned anywhere in this thread.

I placed "mysqldump" in the blacklist, as we run a backup script which uses this as part of the archiving.  Mysqldump is limited, but all the instances of mysql are as well.  I tried adding the -w option to grep in cpulimit_daemon.sh (matches exact word only) with no change.

I'm a little fuzzy with regex and I'm not sure exactly what's going on in the script so I'm stuck.  Apparently it matches anything, in whole or in part, to the strings delimited in the blacklist.  Can anyone verify and/or offer a solution to make it work only on mysqldump and not mysql as well?

Thanks.

---

### Post by abcuser on 2012-11-11
@David,
1. What is the output of command:
top -b -n1 -c

2. What is the output of command:
top -b -n1 -c | grep -E 'mysqldump'

Does this command also list the mysql process?

3. What is exact BLACKLIST variable?
4. What is your CPU_LIMIT variable?

---

### Post by david.rahrer on 2012-11-11
Answer to #1 is attached file.  

Answer to #2 is:
```
root@localhost:~# top -b -n1 -c | grep -E 'mysqldump'
30159 root      20   0 11684  912  784 S    0  0.0   0:00.00 grep --color=auto -E mysqldump   
```                     

Answer to #3 is:
```
BLACK_PROCESSES_LIST= "rdiff-backup|mysqldump"
```

Answer to #4 is:
```
CPU_LIMIT=20
```

Strangely enough, I removed the "mysqldump" portion of the blacklist and restarted and it still cut off at 20%.  Is it possible this is acting like everything is subject to limiting?  Is my blacklist variable format correct?

I should mention that these results are with the cpulimit stopped as the server quickly fails (due to mysql cutting off in so many threads) when it is on.

Thanks for your help.

---

### Post by abcuser on 2012-11-12
> **david.rahrer said:**
> 
Answer to #2 is:
```
root@localhost:~# top -b -n1 -c | grep -E 'mysqldump'
30159 root      20   0 11684  912  784 S    0  0.0   0:00.00 grep --color=auto -E mysqldump   
```                     

from #2 I see there is no "mysqldump" program running and so it can't be cpu-limited if it does not exists. Was program mysqldump really running when you executed the #2 command?

> **david.rahrer said:**
> 
Strangely enough, I removed the "mysqldump" portion of the blacklist and restarted and it still cut off at 20%.  Is it possible this is acting like everything is subject to limiting?  Is my blacklist variable format correct?

BLACKLIST only limits processes listed except if this variable is empty then it limits all of the processes (as described in first post of this thread).

Stop or restart also kills all of the cpulimit processes so everything that was limited is getting full CPU access again.

---

### Post by david.rahrer on 2012-11-12
The following is the response from #2 when the mysqldump script is running.

```
root@WSN005:~# top -b -n1 -c | grep -E 'mysqldump'
19923 root      20   0 99012 3092 1312 S    4  0.1   0:03.16 /usr/bin/mysqldump -Q --single
19930 root      20   0  9384  880  760 S    0  0.0   0:00.00 grep --color=auto -E mysqldump
```

---

### Post by abcuser on 2012-11-17
@david.rahrer, this looks good to me. Don't know what the problem is. I don't use mysql, so maybe there is something else that is wrong...

---

### Post by gagginaspinnata on 2012-12-03
Is there any way to run it on mac osx? I know that cpulimit works fine on osx

---

### Post by abcuser on 2012-12-04
@gagginaspinnata, I don't know, I don't have a mac, but osx is a unix like system, so it may work. You will need to test it to see how it is working - most probably the start-up scripts will not work, but cpulimit deamon could.

---

### Post by staple22 on 2013-01-17
Hi,

I have two processes on my server with the same name and using your scripts it only traps one of them.

So for example is you ran this commend twice to generate fake load.
dd if=/dev/zero of=/dev/null &
And then in the blacklist you set the variable equal to dd
it would only trap the first instance of the process name. Can you let me know how I can trap all processes with this name on the server rather than just the first one. 

P.S. abcuser - u provided an awesome script. :D

---

### Post by liju.g.chacko on 2013-02-10
Don't limit root processes. When I tried to limit Xorg process via
gnome-terminal, system hanged(ubuntu 12.04).
Please add "root" to white list as below
> WHITE_PROCESSES_LIST="root"

---

### Post by Olav on 2013-10-11
I realise this thread is a few years old already, but I found it only today and I can confirm the script is still very useful. It works and it is very clever. Thank you, Abcuser, if you are still reading this.

There is one small change I had to make, which was to insert ```
export LANG=C
``` as the second line (after #!/bin/bash of course). Since the script uses the output of top and other commands, this line makes sure this output conforms to the default locale.

For instance, the CPU usage column in top is shown with a comma as the decimal seperator in LANG=nl_NL.UTF-8, which is my system locale, but the script expects a decimal point.

It makes sense to always use LANG=C in every script you write. Or at least, if you are going to publish them on an international web forum...

---

### Post by abcuser on 2013-10-12
@Olav, thanks for your info. I can't edit first post in this thread anymore. I can't do it for years... some forum policy that old post can't be changed.

There was also another decision that tutorials are moved to some wiki or something... don't know in my humble opinion bad decision, because in forum you can always get feedback as author of tutorial and end-users can report bugs, ideas etc. So double way communication, collaboration etc.

---

### Post by likudio on 2014-01-13
Hi.

I have an issue with this daemon.
I'm using it on Debian GNU/Linux 7.3 .

The problem is that it keeps crashing the MySQL server.
If I stop the daemon, MySQL works normally.

To debug this, I tried running "*/usr/bin/cpulimit_daemon.sh*" in console.
And this is what I get:

```

root@hsh:~# /usr/bin/cpulimit_daemon.sh
/usr/bin/cpulimit_daemon.sh: line 9: tar|zip: command not found

```

while the script is still waiting.
After a short period of time, I get this: 

```
Process 20913 detected
Process 20913 dead!

```

And this is the moment I get MySQL crashed. The MySQL crash is confirmed by */var/log/syslog* also:

```

Jan 13 10:12:07 hsh mysqld_safe: Number of processes running now: 1
Jan 13 10:12:07 hsh mysqld_safe: mysqld process hanging, pid 20913 - killed
Jan 13 10:12:07 hsh mysqld_safe: mysqld restarted

```
If I let the script running, it keeps crashing MySQL on and on.

In */usr/bin/cpulimit_daemon.sh* at line 9, i have the following code:

```
BLACK_PROCESSES_LIST= "tar|zip"   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.

```

tar and zip are the proccesses I'm watching for not to override my limit.
No matter if I write any process in the black list or not, I keep getting MySQL crashed.

Does anyone have any clue about this?
Thanks.

---

### Post by abcuser on 2014-01-13
It looks to me that NEW_PIDS_COMMAND also gets into MySQL process. Maybe NEW_PIDS_COMMAND variable is not correctly assined by deamon.

In terminal can you please execute command:
```
top -b -n1 -c | grep -E 'tar|zip'
```
Please look at the last column of above output. Is there any of MySQL process involved? Please post the output to this forum.
 
Grep command above looks for regular expression pattern!!! For example if process name (from top command) returns e.g. mysqltar (notice tar in the name of the process) then this process is going to be assigned to NEW_PIDS_COMMAND. It looks to me that at least one of MySQL process has 'tar' or 'zip' in its name.

So for example if above command returns the: "mysqltar" and you would like to limit only "tar" you can use a regular expression to properly filter out only "tar". So try this out or one of its variations (with or without ^  OR  with or without $)
```
BLACK_PROCESSES_LIST= "^tar$|^zip$"
```
Note: ^ - is a special character that tells grep that string has to be the FIRST character in the line.
Note: $ - the same as above but LAST.

Hope this helps. If not then please reply to this forum the output of first command above.

---

### Post by likudio on 2014-01-13
Nope, that doesn't seem to be the issue.
Here's the only output of your command:

```

root@hsh:~# top -b -n1 -c | grep -E 'tar|zip'
24753 root      20   0  7780  880  768 S    0  0.0   0:00.00 grep -E tar|zip

```

No MySQL process involved in the grep pattern.
I even tried to delete all the string from the blacklist line and still crashes MySQL, even without having any text in the pattern string.
Line 9 looks like this now:
```

BLACK_PROCESSES_LIST= ""   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.

```

...and the result:

```

root@hsh:~# /usr/bin/cpulimit_daemon.sh
/usr/bin/cpulimit_daemon.sh: line 9: : command not found
Process 23990 detected
Process 23990 dead!
^C

```

Confirmed by */var/log/syslog*:

```

Jan 13 14:42:00 hsh mysqld_safe: Number of processes running now: 1
Jan 13 14:42:00 hsh mysqld_safe: mysqld process hanging, pid 23990 - killed
Jan 13 14:42:00 hsh mysqld_safe: mysqld restarted

```

So the issue still remains.
But, as a side question... if the purpose of the daemon is to limit the CPU usage, why does it crash?
It has to do with mysql_safe which thinks that the proccess is hanging and tries to restart it, right?

Anyway, this was just a side question.
Still can't figure it out why does it try to limit the MySQL process (and crashes it also)...

---

### Post by likudio on 2014-01-13
As a (PHP) developer, I started to debug the code.

I have put the following echos in the if lines to see which block gets execute.
It's pretty hard for me as I don't know exactly the bash syntax... but I hope I'll figure it out. (any help is appreciated).

So:

```

# Check if one of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST is defined.
if [[ -n "$BLACK_PROCESSES_LIST" &&  -n "$WHITE_PROCESSES_LIST" ]] ; then    # If both variables are defined then error is produced.
   echo "At least one or both of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST must be empty."
        echo 10;
   exit 1
elif [[ -n "$BLACK_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | grep -E '$BLACK_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
        echo 20;
elif [[ -n "$WHITE_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6' | grep -E -v '$WHITE_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
        echo 30;
else
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6 && \$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
        echo 40;
fi

```

And I get 40 all the time, no matter what I put in variables.
So... the last if block gets executed and that's the reason why I get MySQL crashed.

1. I'll let you know as soon as I get any more information... I don't know why the first if blocks don't get executed.
2. Anyway... the script purpose it's to limit the cpu usage, but MySQL crashes. How to avoid that? I still think that mysqld_safe thinks that the server is hanging and it restarts it... I have to find a way to avoid that.

---

### Post by abcuser on 2014-01-14
Hi,
first for all I don't know why MySQL is crashing. According to your post it looks like regardless of variable you put in, ALL of the processes gets into limiting state (echo 40) and so this affects MySQL processes in some way - maybe MySQL recognizes that something has changed with its process and it crashes.

When you change the code and run it one more time are you sure you have STOPPED previously executed daemon? You see in the code is endless while loop, so you have to kill existing running application (= daemon) before running another instance of it. Before running daemon again search if there is an already running process by:
```
ps -eo pid,args | grep "cpulimit_daemon.sh"
```
If you get some output then there is already a daemon running and you have to kill it first before running another instance of daemon.

The next thing you can do is to add "echos" into after all of the lines that some variable is specified and echo the variable content. I have prepared debugging code see bellow. Try to run this code (but make sure you don't have a daemon already running).

```

#!/bin/bash
# ==============================================================
# CPU limit daemon - set PID's max. percentage CPU consumptions
# ==============================================================

# Variables
CPU_LIMIT=20       	# Maximum percentage CPU consumption by each PID
DAEMON_INTERVAL=3  	# Daemon check interval in seconds
BLACK_PROCESSES_LIST=   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.
WHITE_PROCESSES_LIST=   # Limit all processes except processes defined in this variable. If variable is empty (default) all violating processes are limited.

# Check if one of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST is defined.
if [[ -n "$BLACK_PROCESSES_LIST" &&  -n "$WHITE_PROCESSES_LIST" ]] ; then    # If both variables are defined then error is produced.
   echo "At least one or both of the variables BLACK_PROCESSES_LIST or WHITE_PROCESSES_LIST must be empty."
   echo "1. BLACK_PROCESSES_LIST: " $BLACK_PROCESSES_LIST
   echo "2. WHITE_PROCESSES_LIST: " $WHITE_PROCESSES_LIST
   exit 1
elif [[ -n "$BLACK_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | grep -E '$BLACK_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
   echo "3. CPU_LIMI: " $CPU_LIMIT
   echo "4. BLACK_PROCESSES_LIST: " $BLACK_PROCESSES_LIST
   echo "5. NEW_PIDS_COMMAND: " $NEW_PIDS_COMMAND
elif [[ -n "$WHITE_PROCESSES_LIST" ]] ; then                                 # If this variable is non-empty then set NEW_PIDS_COMMAND variable to bellow command
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6' | grep -E -v '$WHITE_PROCESSES_LIST' | gawk '\$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
   echo "6. CPU_LIMI: " $CPU_LIMIT
   echo "7. WHITE_PROCESSES_LIST: " $WHITE_PROCESSES_LIST
   echo "8. NEW_PIDS_COMMAND: " $NEW_PIDS_COMMAND
else
   NEW_PIDS_COMMAND="top -b -n1 -c | gawk 'NR>6 && \$9>CPU_LIMIT {print \$1}' CPU_LIMIT=$CPU_LIMIT"
   echo "9. CPU_LIMI: " $CPU_LIMIT
   echo "10. NEW_PIDS_COMMAND: " $NEW_PIDS_COMMAND
fi

# Search and limit violating PIDs
while sleep $DAEMON_INTERVAL
do
   NEW_PIDS=$(eval "$NEW_PIDS_COMMAND")                                                                    # Violating PIDs
   LIMITED_PIDS=$(ps -eo args | gawk '$1=="cpulimit" {print $3}')                                          # Already limited PIDs
   QUEUE_PIDS=$(comm -23 <(echo "$NEW_PIDS" | sort -u) <(echo "$LIMITED_PIDS" | sort -u) | grep -v '^$')   # PIDs in queue

   echo "11. DAEMON_INTERVAL: " $DAEMON_INTERVAL
   echo "12. CPU_LIMI: " $CPU_LIMIT
   echo "13. NEW_PIDS: " $NEW_PIDS
   echo "14. LIMITED_PIDS: " $LIMITED_PIDS
   echo "15. QUEUE_PIDS: " $QUEUE_PIDS

   for i in $QUEUE_PIDS
   do
       cpulimit -p $i -l $CPU_LIMIT -z &   # Limit new violating processes
   done
done

```

Please post the outputs of echos to the forum.

There is also possible that Debian has something different then Ubuntu. This code was tested on Ubuntu 10.04 (= April 2010) few years back. It is possible that Debian uses some never version of one of the programs and e.g. outputs something that script does not expects. For example there are "gawk" commands with searches the data in one of the columns, if some output has changed then script is not going to be working fine.

One more thing to discuss is are you sure you need a cpulimit_daemon? How do you run tar and zip commands? Are they executed manually from shell by you or some other way? You see from my tutorial there is a note at the top of the tutorial: "Note: If you would like to omit only one process then you don't need this "cpulimit daemon". In this case you only need cpulimit program to be executed from terminal."

So if you execute the code from shell manually then you can:
1. Execute the 'tar' or 'zip' command.
2. Check the process_pid: ps -eo pid,args | grep tar
3. Limit process manually: cpulimit -p process_pid -l cpu_limit -z &
Note: process_pid is from command 2, cpu_limit is for example 20 for 20%.

Regards

---

### Post by abcuser on 2014-01-14
> **likudio said:**
> 
```

BLACK_PROCESSES_LIST= ""   # Limit only processes defined in this variable. If variable is empty (default) all violating processes are limited.

```

...and the result:

```

root@hsh:~# /usr/bin/cpulimit_daemon.sh
/usr/bin/cpulimit_daemon.sh: line 9: : command not found
Process 23990 detected
Process 23990 dead!

```

There is a problem you didn't specify the variable in correct way! The variable should be empty, but you have defined it to have an empty string, but executing it in double quotes. See variable black_list should be defined as:
```
BLACK_PROCESSES_LIST=
```
but you have defined it as:
```
BLACK_PROCESSES_LIST= ""
```
Remove the double quotes from variable value. See my first post in this thread for original code.

Also make sure there are no ADDITIONAL spaces in you code. For example if you add or remove some of the space in if statement then command can have completely different meaning and it will not work as designed or not work at all. Spaces are very important!!!

Also how did you define black_process_list variable?
Did you write:
```
BLACK_PROCESSES_LIST= "tar|zip"
```
Note: So space after "=" character? If yes, then you code is not going to work correctly. In this case instead of defining a variable value you gonna execute tar command and pass the output into zip command... Strange thing can happen if you add additional space.
```
BLACK_PROCESSES_LIST="tar|zip"
```
Note: You see there is no space after "=" character.

Hope this helps.

---

### Post by abcuser on 2014-01-14
It looks like old posts can be edited again. This was a limitation the last time I have looked at editing them. So in first post I have added the 'Attention' note on how to properly specify variables.

---

### Post by likudio on 2014-01-17
Sorry for the late answer, I didn't have time until now to dig the problem.

> **abcuser said:**
>  Spaces are very important!!!

Unbelievable, but you were so right.
That space before the equal sign was all the issue.
After removing it, it finally goes in the right "if" section.
And it limits processes as it should.

On the other hand, for MySQL I have to say that it has the same behavior, but somehow can be explained.
In Debian (perhaps in other distros too), if you install MySQL with aptitude, it comes with a monitoring package named "mysqld_safe" which constantly monitors the mysqld process. For some reason, when it sees it struggling (limited by cpulimit) it kills it and restarts it.

To avoid that, you must disable mysqld_safe, but I wouldn't recommend that as it does some other things too in order to keep mysql up and running.
For batch jobs like backups and so on, simply limit mysqldump or gzip (considering you export to a gzip archive) or so on.

Anyway, thank you once again for your help, I wouldn't think in ages that those spaces can be the issue.

Best regards,

---

### Post by abcuser on 2014-01-18
> **likudio said:**
> 
For some reason, when it sees it struggling (limited by cpulimit) it kills it and restarts it.

Are you still having problem with MySQL? Can you try using the debug code from [http://ubuntuforums.org/showthread.php?t=992706&p=12899891#post12899891](http://ubuntuforums.org/showthread.php?t=992706&p=12899891#post12899891) and see if some of the mysql process gets limited? If yes then you should change the variable BLACK_PROCESSES_LIST to meet you requirements.
> **likudio said:**
> 
To avoid that, you must disable mysqld_safe, but I wouldn't recommend that as it does some other things too in order to keep mysql up and running.
For batch jobs like backups and so on, simply limit mysqldump or gzip (considering you export to a gzip archive) or so on.

This is probably work around, but I can't suggest anything like this, because I am not an MySQL expert. Like written before, I suggest to trace down the process that gets limited and appropriatly change BLACK_PROCESSES_LIST variable.

---

### Post by bobmarley2021 on 2014-01-20
Hi abcuser, thank you for this daemon - I am finding it incredibly useful. I have found others that added the following to beginning of the cpulimit daemon:

#!/bin/bash
### BEGIN INIT INFO
# Provides:          cpulimitd
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Script to start CPU limit daemon
# Description:
#
### END INIT INFO

Or Debian complains (insserv).

I just need some input on a couple of things....

I am running this on a Debian Wheezy system which for the most part seems to be working well. The only problem is that when the daemon is running, sometimes bash will background an apt-get process while it is running an apt-get update or install etc. and the output "[1]+  Stopped                 apt-get update" will be displayed... if I stop the cpulimit daemon, this problem goes away... 

Is this an issue that you have run into? I know you have posted this for Ubuntu and not Debian, but any help/adjustments you can offer would be very much appreciated.

---

### Post by abcuser on 2014-01-21
> **bobmarley2021 said:**
> The only problem is that when the daemon is running, sometimes bash will background an apt-get process while it is running an apt-get update or install etc.
Daemon searches for pattern in process names including the whole string it uses when run. When using update/install some of the processes that meets pattern! can be caught by daemon.

Did you specify a BLACK_PROCESS_LIST or WHITE_PROCESSES_LIST variable? I suggest to define one of them and use proper regular expression to specify processes you need as exactly as you can. For example if you would like to limit only Gedit program, then run Gedit and monitor what is outputted by command:
```

top -b -n1 -c | grep -E 'gedit'

```
Then try to add regular expressions like "^" for beginning of the command and "$" for end of the command. So example:
```

top -b -n1 -c | grep -E '^gedit$'

```
Above command will most probably avoid the problem at apt-get update/install, because it will not contain any spaces that apt-get update/install produces. So in this case use:
```

BLACK_PROCESS_LIST="^gedit$"

```



The other work-around is maybe you can stop limit daemon when updating the system. For example if you are updating your system at night when most probably system is not occupied too much, so you can write script:
```

[code to stop limit daemon]
apt-get update...
[code to start limit daemon]

```
Hope this helps

---

### Post by bobmarley2021 on 2014-01-21
Thank you for your reply. After considering the options I have decided to add the list of offending processes to the black list, instead of white-listing apt-get etc and this has solved the issue. Thanks again for this great daemon.

---

### Post by Votlon on 2014-02-07
What are the benefits of controlling your cpu to such a lower % rather than just letting it run free? 0.0

---

### Post by abcuser on 2014-02-07
@dale2, if you are asking this kind of question, then you don't need this daemon. :)

The whole point is that one or more processes do not occupy whole your CPU and makes your computer unusable. For example you decided to compile some program that will take 30 minutes to compile, but when you execute this compile you can't work with your computer, because it is 100% CPU occupied. With this kind of restriction that daemon gives you are able to work normally like browsing the web, typing some text in office suite and similar while a background process does the compile work for you.

---

### Post by Votlon on 2014-02-07
@abcuser Didn't mean to offend :) but thank you for the info now i understand why people would want to use it. I apologize for still being new to Ubuntu and in depth computing, i'll venture back to the absolute beginners section :3

---

### Post by abcuser on 2014-02-08
@dalen2, I was not offended. I was just surprised... that is why I wrote smiley at the end of first sentence. I am glad you are a new Ubuntu user and trying out the new things and trying to understand computing. Apology is not needed if you are curious. Don't just go back to beginner section if you are interested in understanding some topic. We are all in the same position of being in dark in multiple topics, but asking questions is the way out to light, to knowledge.

---

