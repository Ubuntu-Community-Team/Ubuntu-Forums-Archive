---
title: "VBox as a service in Lucid"
date: 2011-09-15
forum: Server Platforms
---

### Post by doas777 on 2011-09-15
I have an ubuntu Desktop server that I run semi-headless and connect to remotely. upon it I have a Virtual box instance, running an ubuntu server edition server (rsyslogd server).
When I reboot I have to login to the box over freenx to start the log server (and to shut it down prior to shutdown).

I would like to run the logserver instance as a service, and I have investigated several init.d scripts to integrate it, but none of them have worked right for me. I notice that this topic has changed a great deal over the years.

Can anyone point me to an autostart tutorial/script for VBox VMs that is sure to work with lucid x64 hosts?

Thanks

---

### Post by CharlesA on 2011-09-15
Hi,

Have you checked my startup/shutdown script [here]("http://charlesa.net/scripts/scripts.php")?

I have it set to run a loop, but if you are starting just one VM, you can modify the script to do that instead.

---

### Post by doas777 on 2011-09-15
> **CharlesA said:**
> Hi,

Have you checked my startup/shutdown script [here]("http://charlesa.net/scripts/scripts.php")?

I have it set to run a loop, but if you are starting just one VM, you can modify the script to do that instead.

Rock On! I'll give em a try!

---

### Post by CharlesA on 2011-09-15
Let me know if you run into any problems. I tested it on my Lucid box with VBox 4 without any problems, but nothing is perfect. ;)

---

### Post by doas777 on 2011-09-15
ok, almost there methinks.

on start the script exits with:
```

Host:/$ sudo service vmboot start
No Saved VMs to start!
Host:/$ sudo service vmboot status
No VMs Currently Running!

```so I started going after the vboxmanage list calls:
```

Host:/$ vboxmanage list vms | sed -e 's/^".*".*{\(.*\)}/\1/'
b1f339e8-6351-45fb-9edd-5c8A84d346cf
Host:/$ v=`vboxmanage list vms | sed -e 's/^".*".*{\(.*\)}/\1/'`; vboxmanage showvminfo $v | grep saved
Host:/$ v=`vboxmanage list vms | sed -e 's/^".*".*{\(.*\)}/\1/'`; vboxmanage showvminfo $v
Name:            LogServer_Lucid32
Guest OS:        Ubuntu
UUID:            b1f339e8-6351-45fb-9edd-5c81b4d346cf
<snip />

```I removed the grep and:
```

Host:/$ sudo service vmboot start
Waiting for VM "LogServer_Lucid32" to power on...
VM "LogServer_Lucid32" has been successfully started.


```so is there any danger to this mod? it seems reasonable, but...

Thanks for your help Charles, 
Franklin

---

### Post by CharlesA on 2011-09-16
Nah no danger. The script was designed to start any vm that was in a saved state, which is why it runs grep.

Were you trying to start a vm from a powered off state?

Also, how were you able to get it to run via service? I recall trying that and it not working.

---

### Post by doas777 on 2011-09-16
yeah, I shut down teh vm before I started playing around with services, just to be on the safe side.

as for installing as a service, I used a varient of your update-rc.d:
```

sudo chmod 755 /etc/init.d/vmboot
sudo update-rc.d vmboot defaults 99 01

```
worked like a charm!

Thanks sir! I'm going to try the shutdown side of it tonight; I'll let you know how it works out.

---

### Post by CharlesA on 2011-09-16
> **doas777 said:**
> yeah, I shut down teh vm before I started playing around with services, just to be on the safe side.

as for installing as a service, I used a varient of your update-rc.d:
```

sudo chmod 755 /etc/init.d/vmboot
sudo update-rc.d vmboot defaults 99 01

```
worked like a charm!

Thanks sir! I'm going to try the shutdown side of it tonight; I'll let you know how it works out.

Thanks for that. I'll try it on my lucid box and see what happens.

As a sidenote: What does the 99 01 do at the end?

EDIT: service worked. Nice - no more typing /etc/init.d/blahblah. :D

---

### Post by doas777 on 2011-09-16
appearently the numbers set the order in which it will he started and killed. from what I understand 99 indicates that it is the last thing to load, and 01 indicates that it is the first thing to unload. 

I remember in the old days, you had to put numbers in front of your init scripts names to control the order in which they execute within each runlevel, but I havent had to do that in like 5 years. I think it changed with upstart, but i am no expert with services. I just found those params while googling around last night, trying to get some of the failed scripts to work.

---

### Post by CharlesA on 2011-09-16
Ah gotcha. Thanks. I just used the defaults and it seemed to work fine for me. If I coded the thing right, it would wait until vboxdrv was loaded before running on boot, but I'm kinda new to the whole init script stuff.

---

### Post by Entilza on 2011-09-16
Did you make the service do stop as well?  (As per your scripts)

---

### Post by CharlesA on 2011-09-16
> **Entilza said:**
> Did you make the service do stop as well?  (As per your scripts)
The script is set to save the state of any running VMs on system shutdown/reboot.

You can also do that manually like so:

```
sudo service vmboot stop
```

---

### Post by Entilza on 2011-09-16
Ah cool, I was looking at the individual start / stop.  You have the combined one as well listed, thanks.

So is this the proper way to shutdown guest machines if the host system goes down? I would probably prefer to shut them down individually?

ie:  Host Ubuntu,  guest: Win7  In order to shutdown win7 fully you would have to send a shutdown signal but I don't think this is possible through vbox?  Atleast without some sort of program listening on the guests and waiting for a shutdown signal..

---

### Post by CharlesA on 2011-09-16
You can send a shutdown signal via vbox. I have been using savestate so I can pick up where I left off instead of having to restart what I was doing on the VM.

---

### Post by doas777 on 2011-09-18
well, I've tried it over a few days and I like it thus far. i am having a problem with the stop however. I added syslogging to the script so i could confirm that it was reacting to the events correctly, and that in itself appears to be working fine, but I am not getting any logs from the shutdown event unless I stop the service manually. 

I've attached my mutant version, in case you see a problem there.
I'm going to try adding a flag file at shutdown to see if I can confirm the event is firing but perhaps after the logging service has stopped. 

Thanks!

---

### Post by CharlesA on 2011-09-18
Have you tried adding $local_fs and $syslog  to the requires areas?

[http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)

I'm not even sure I wrote that part correctly, but it *looks* right.

---

### Post by doas777 on 2011-09-18
interesting. 

ok,I've added those items start/stop dependency list, but I'm still not getting log messages on the stop, unless I stop the service manually from the shell. service start works as expected.

per the LSB init specs, I added restart and force-reload clauses as well just in case. I've been removing and resetting the service with update-rc.d on each change before testing.

my latest version is attached. see anything amiss?

---

### Post by CharlesA on 2011-09-18
Looks fine to me.

It sounds like the system logger is being stopped during shutdown before the commands are being run. or something. I'm not sure how to fix that.

BTW: Nice mod with the functions. :)

---

### Post by doas777 on 2011-09-18
> **CharlesA said:**
> 
It sounds like the system logger is being stopped during shutdown before the commands are being run. or something. I'm not sure how to fix that.

looks like that is exactly the case. I had it touch a file in /var/log after it stops the vm without error, and that file does get created on reboot, so I guess all is in working order. as long as its working, I'm not so worried about the logging.

Thanks for all your help with this. I've enjoyed working with you and learning about service configuration.
cya 'round

---

### Post by CharlesA on 2011-09-19
No problem, glad you (sorta) got it figured out. :)

---

### Post by CharlesA on 2011-09-20
*pokes thread*

I was thinking.. maybe try using the full path to logger and see what happens. If it works when run as your normal user, but not on shutdown, perhaps the path is not found.

---

### Post by doas777 on 2011-09-22
sure, i'll give it a try. I found the logger executable, but there has to be a way to get direct access to the log. since a touch works, a file write should as well.

---

### Post by CharlesA on 2011-09-22
touch is an internal command, isn't it?

---

### Post by doas777 on 2011-09-23
indeed it is, as is >> or so it would appear. I was able to manually write to the syslog file on shutdown, so looks like that will work. I need to clean it up a little to better integrate the logging, as well as get it to echo to stdout, but here is my working copy.

a quick question on savestate. I did some poking around and it seems like there is no cli way to gracefully shutdown the guest. do virtual filesystems suffer from the write-in-progress danger that physical disks carry with them? is it safe to simply reset them?

I'm also having a problem with network services in the guest when resuming from saved state. I think I can handle that though.

```

#!/bin/bash

### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv $local_fs $syslog
# Required-Stop:  vboxdrv $local_fs $syslog
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs before/after System shutdown
### END INIT INFO

# Add this script to /etc/init.d/
# Run update-rc.d vmboot defaults as root

# Written to work with VirtualBox 4.x

# User who is running the VMs
VBOXUSER=CONFIGURE_ME
SU="sudo -H -u $VBOXUSER"

#en/disable syslogging 1|0
EnableLogging="1"
echocmd="echo -e"
loggercmd="logger -s -f /var/log/syslog"
logdate=$(echo -e $(date +"%b %d %H:%M:%S"))
loggermsg="$(echo -e $logdate `hostname` vmboot: %s)\n"

# Path to VBoxManage
VBOXMANAGE="/usr/bin/VBoxManage --nologo"

# Get UUID of All Running VMs
# UUID looks like this: a02b5b54-a84d-48fa-8dac-2a3fad55717e
RUNNINGVMS=$($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/')
# Get UUID of All VMs
ALLVMS=$($SU $VBOXMANAGE list vms | sed -e 's/^".*".*{\(.*\)}/\1/')

#set logging
if [[ "$EnableLogging" -eq "1" ]]; then
    echocmd=$loggercmd
fi

# Check to insure $ALLVMS is not null and exit if it is.
if [[ $ALLVMS = "" ]]; then
        $echocmd  "No VMs are detected on this host! Did you configure the VBOXUSER variable?"; exit
fi

function logMsg(){
    if [[ "$EnableLogging" -eq "1" ]]; then
        printf "$loggermsg" "$1" >> /var/log/syslog >> /dev/stdout;
    fi
}

function stopService(){
    if [[ -n $RUNNINGVMS ]]; then
        for v in $RUNNINGVMS; do
        $echocmd "Saving state of $($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF-1)}')..." && $SU $VBOXMANAGE controlvm $v savestate
        done; else
        $echocmd "No running VMs to save!"
    fi
    # If the previous loop has an error, the loops exits and returns an error.
    if [[ $? -ne 0 ]]; then
            $echocmd  "There was an error stopping your VMs!"; else
            echo -e "$(touch /var/log/vmboot-shutdown-`date +%Y%m%d%H%M%S`)";
            logMsg "VMBoot has saved all VMs";
    fi
    
}

function startService(){
    for v in $ALLVMS; do
        if [[ -n $($SU $VBOXMANAGE showvminfo $v) ]]; then
                $echocmd  "Waiting for VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF -1)}')\" to power on..." && $SU $VBOXMANAGE startvm $v --type headless 1> /dev/null && logger -s "VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF-1)}')\" has been successfully started."; else
                $echocmd  "No Saved VMs to start!"

        fi
        # If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                $echocmd  "There was an error starting your VMs! Try starting them manually to see what the problem is."; break
        fi
    done
}

function restartService(){
    stopService
    startService
}

function serviceStatus(){
    if [[ -n $RUNNINGVMS ]]; then
        $echocmd "List of Running VMs:" && $SU $VBOXMANAGE list runningvms; else
                $echocmd "No VMs Currently Running!"
    fi
}

case $1 in
stop)
    stopService
;;
start)
    startService
;;
restart)
    restartService
;;
status)
    serviceStatus
;;
force-reload)
    #not really sure what to do here other than restart
    restartService
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop | status | restart | force-reload"; exit 1
;;
esac
exit 0
# eof

```

---

### Post by CharlesA on 2011-09-23
From what I read, just powering off the guest may cause problems and/or data corruption on the virtual hdd.

I did see that you can send these two signals to the guest via cli:

```
 acpipowerbutton
```

I think that might be what you are looking for, tho I have not used it. Just replace savestate with that.

---

### Post by doas777 on 2011-09-24
ok, It took a little fiddling, but I got the ACPI button to work. the guest had not installed acpid by default so I had to:
```
sudo apt-get acpid
```but after that, the guest responded correctly to the shutdown request. very nice.

I will be testing the guest network services on startup and shutdown tonight and tomorrow (server reboots are a little bit of a pain during the day). if all goes well, I'll clean up the script and pass it back if you are interested. I'm a .net/java programmer by trade, so I am used to somewhat cleaner code that shell usually provides. I am always struck by how insanely flexible, yet bizarrely arcane shell is.

after that, all I need to look at running transmission as a service (on the host) and I am golden.

---

### Post by CharlesA on 2011-09-24
Glad you got it figured out. Good luck with getting the network issues resolves and transmission to run as a service. :)

I'd love a copy of the script once you get it up and running.

---

### Post by doas777 on 2011-09-25
I think I have everything running to my taste now, so here you go. I hope its of use.
New\Notable:
   documentation expanded
   added a spin-wait to let the vms actually shutdown before exit
   new behavoir for force-reload. attempts to gracefully stop, and resets guest if it cannot.

Thanks again, and have fun,
Franklin

---

### Post by CharlesA on 2011-09-25
Looks good. Nice job!

---

### Post by pildrmar on 2012-05-03
Thank you guys! Those scripts helped me out bigtime! You have done a great job here:guitar:):P

---

### Post by babanimfomana on 2012-07-22
The script starts all the virtual machines, i don't want that, can i make a list with what machine i want to be up at startup ?

---

### Post by CharlesA on 2012-07-22
> **babanimfomana said:**
> The script starts all the virtual machines, i don't want that, can i make a list with what machine i want to be up at startup ?
That is what it was designed to do, which is why it runs in a loop.

If you have a single VM you want to start, you can specify the name instead of $v.

---

### Post by Fauskin on 2012-09-16
> **CharlesA said:**
> That is what it was designed to do, which is why it runs in a loop.

If you have a single VM you want to start, you can specify the name instead of $v.

Been using this script for quite some time, and would like to autostart only one VM, but would like all the VM's to be nicely shut down.

Should I replace every $v with my VM's name, or should I only replace $v 's in the function Startservice?

---

### Post by CharlesA on 2012-09-16
> **Fauskin said:**
> Been using this script for quite some time, and would like to autostart only one VM, but would like all the VM's to be nicely shut down.

Should I replace every $v with my VM's name, or should I only replace $v 's in the function Startservice?

Just replace $v with the name of the VM you want to start up.

---

### Post by Fauskin on 2012-09-17
> **CharlesA said:**
> Just replace $v with the name of the VM you want to start up.

Well, yeah, I got that part..;)

The question was should I replace ALL the occurrences of $v in the whole script? You see that there are several $v 's and for a newb this is a quite advanced script to mess with.

Anyway I found it out, and it's enough to replace $v in the following line inside function Startservice
```
$echocmd  "Waiting for VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF -1)}')\" to power on..." && $SU $VBOXMANAGE startvm VWNAME --type headless..
```

---

### Post by JKyleOKC on 2012-09-17
You could also make a small change in the startservice loop, to read the VM names from a file in /etc such as /etc/vmboot.conf, that contains only the names of the machines you want to start automatically. Then, of course, create that file and populate it. That would give you the flexibility to start more than one, but not all, of the VMs at boot time.

This is taken from the way another automatic start/stop tool, called vboxtool, works. Originally written for vbox version 3, vboxtool quit working when vbox moved to version 4 and that (as I recall) was part of the reason Charles developed his own script. Eventually vboxtool got fixed, and I'm using it -- but I definitely like parts of Charles' script better and will probably switch one of these days. I haven't tested the suggested change in any way, but it ought to be fairly simple to implement...

---

### Post by CharlesA on 2012-09-17
> **Fauskin said:**
> Well, yeah, I got that part..;)

The question was should I replace ALL the occurrences of $v in the whole script? You see that there are several $v 's and for a newb this is a quite advanced script to mess with.

Anyway I found it out, and it's enough to replace $v in the following line inside function Startservice
```
$echocmd  "Waiting for VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF -1)}')\" to power on..." && $SU $VBOXMANAGE startvm VWNAME --type headless..
```

Gotcha. Sorry for the misunderstanding.  Even my script confuses me sometimes and I am the one who wrote it! :p

> **JKyleOKC said:**
> You could also make a small change in the startservice loop, to read the VM names from a file in /etc such as /etc/vmboot.conf, that contains only the names of the machines you want to start automatically. Then, of course, create that file and populate it. That would give you the flexibility to start more than one, but not all, of the VMs at boot time.

This is taken from the way another automatic start/stop tool, called vboxtool, works. Originally written for vbox version 3, vboxtool quit working when vbox moved to version 4 and that (as I recall) was part of the reason Charles developed his own script. Eventually vboxtool got fixed, and I'm using it -- but I definitely like parts of Charles' script better and will probably switch one of these days. I haven't tested the suggested change in any way, but it ought to be fairly simple to implement...

There is also another script that the creator of phpvirtualbox wrote up, it seems to be leaner than mine, but I still like mine. ;)

It is included in the phpvirtualbox zip.
[http://code.google.com/p/phpvirtualbox/](http://code.google.com/p/phpvirtualbox/)

---

### Post by sparticle2000 on 2012-12-19
CharlesA and Doas777

Firstly let me say a HUGE THANK YOU FOR THE WORK ON THIS SCRIPT. After weeks of trying to get autostart to work with 4.2 on Ubuntu 12.04.1 I gave up and then found your scripts. The acpipowerbutton method is great as it allows my servers etc. to shutdown properly. 

 I also get an error every time the script tries to write to the log I tried adding $SU to the front of the commnad sequence but that did nothing see below.

/etc/init.d/myvmboot.sh: line 140: break: only meaningful in a `for', `while', or `until' loop
/etc/init.d/myvmboot.sh: line 66: /var/log/syslog: Permission denied
Waiting for VM "xxx.xxx.xxx" to power on...
/etc/init.d/myvmboot.sh: line 66: /var/log/syslog: Permission denied
VM "xxx.xxx.xxx" has been successfully started.


I am not a programmer so most of it is double dutch to me. Ideally I  need to start a number of machines (ever changing) and would like to have a simple text file with a VM machine name per line that I can edit that your script could use to start the machines in function startService(). 

Also is there a way to list machine names against the UIID;s one per line as all I get when I use 'service myvmboot.sh status' is a list of UUID;s on one line. Not the easiest of outputs to read.

This is my first post so please be gentle. [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

Any help appreciated 

Many thanks

Spart

---

### Post by CharlesA on 2012-12-19
Which script are you using?

I don't use the logging utility, so I'm not sure what the problem with that is, but could you post the entire script?

---

### Post by sparticle2000 on 2012-12-19
> **CharlesA said:**
> Which script are you using?

I don't use the logging utility, so I'm not sure what the problem with that is, but could you post the entire script?

Sorry don't now how to make this look like the script doas777 embedded in his post so this is it longhand. it seems to have removed all the indenting. As you can see my amendments are not very elegant :redface:

Many thanks for your response. 

Cheers
Spart

sparticle@TWHGCS23VPS0:~$ sudo cat /etc/init.d/myvmboot.sh
```
#!/bin/bash

### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv $local_fs $syslog
# Required-Stop:  vboxdrv $local_fs $syslog
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs before/after System shutdown
### END INIT INFO

#---------- VMBoot ----------------------------------------------------#
# An LSB-Compliant Init script for VirtualBox 4.x guests on Ubuntu systems.
#
# Valid Parameter values:
#  start            Starts all VMs owned by VBOXUSER.
#  stop                Stops all VMs owned by VOXUSER. Stop behavoir is controled by SHUTDOWNMODE.
#  status            Prints a status message indicating running VMs.
#  restart            Stops and then starts all VMs. Stop behavoir is controled by SHUTDOWNMODE.
#  force-reload        Stops and then starts all VMs, resetting any that do not stop gracefully. Stop behavoir is controled by SHUTDOWNMODE.
#
# To Install:
#  Add this script to /etc/init.d/
#  Make the script executable with 'chmod +x /path/to/this/script' as root
#  Run update-rc.d vmboot defaults 99 01 as root
#
# To Configure:
#  Set VBOXUSER below adding the username of the user who created the VM. This is important because the VM config will reside in /home/$VBOXUSER/VirtualBox VMs/<Virtual Machine Name>/
#  Set SHUTDOWNMODE to your preference. valid values are: "acpipowerbutton", "savestate", "reset". reset can damage your virtual disks so don't use it.
#  Set ENABLELOGGING to enable or disable logging to the systemlog. when logging is enabled messages will be written to the syslog using the pattern contained in LOGGERMSG
#
# To Use:
#  Once Installed and configured, VMBoot works automatically on system boot and shutdown, like any other service.
#  You may manually control VMBoot, by calling the init script itself (as root), or by using the Service interface.
#        ex.     sudo /etc/init.d/vmboot start
#    OR
#        ex.     sudo service vmboot stop
#

#---------- User Settings ---------------------------------------------#
VBOXUSER="sparticle";                    #User who owns the VMs.
SHUTDOWNMODE="acpipowerbutton";        #shutdown or save state. acpipowerbutton|savestate
ENABLELOGGING="1";                    #en/disable syslogging. 1|0

#---------- Environment settings --------------------------------------# 
#Do not modify these values unless absolutely necessary.
VBOXMANAGE="/usr/bin/VBoxManage --nologo";
SU="sudo -H -u $VBOXUSER";
ECHOCMD="echo -e";
LOGGERMSG="$(echo -e `date "+%b %d %H:%M:%S"` `hostname` "$0": %s)\n";

#---------- Script -------------#

RUNNINGVMS=$($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/'); #UUID of All Running VMs. UUID looks like this: a02b5b54-a84d-48fa-8dac-2a3fad55717e
ALLVMS=$($SU $VBOXMANAGE list vms | sed -e 's/^".*".*{\(.*\)}/\1/');        #UUID of All VMs

# Check to insure $ALLVMS is not null and exit if it is.
if [[ $ALLVMS = "" ]]; then
    output  "No VMs are detected on this host! Did you configure the VBOXUSER variable?"; 
    exit;
fi

#outputs messages to the screen and log if logging is enabled
function output(){
    if [[ "$ENABLELOGGING" -eq "1" ]]; then
        $SU $ECHOCMD "$(printf "$LOGGERMSG" "$1")" >> /var/log/syslog;
        echo "$1"
    else
        $ECHOCMD "$1";
    fi
}

#return a given machines human readable name by UUID
function getVMName(){
    echo $($SU $VBOXMANAGE list vms | grep "$1" | awk -F\" '{print $(NF -1)}');
}

#return the list of currently running VMs. never gets stale.
function getRunningVMs(){
    echo $($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/');
}

function stopService(){
    if [[ -n $RUNNINGVMS ]]; then
    
        #set message based on SHUTDOWNMODE
        modemsg="Shutting Down";
        if [[ $SHUTDOWNMODE == "savestate" ]]; then
            modemsg="Saving state of";
        elif [[ $SHUTDOWNMODE == "reset" ]]; then
            modemsg="Aborting"
        fi
        
        #shutdown or save all running vms
        for v in $RUNNINGVMS; do
            name=$(getVMName $v)
            output "$modemsg $name...";
            $SU $VBOXMANAGE controlvm $v $SHUTDOWNMODE;
            
            # If this loop has an error, the loops exits and returns an error.
            if [[ $? -ne 0 ]]; then
                output  "There was an error $modemsg $name."; 
            else
                output "VMBoot has stopped $name.";
            fi
        done; 
        
        #wait for VMs to shutdown, if they haven't already.
        c=90;
        while [[ (-n $(getRunningVMs)) && ("$c" -gt "0") ]]; do
            sleep 1;
            c=$(($c - 1));
        done
        
        #if waited for specified number of seconds, log and exit.
        if [[ "$c" -eq "0" ]]; then
            output "Warning: One or more VMs failed to stop!";
        else
            output "VMBoot stopped all running VMs."
        fi
    else
        output "No running VMs to save!";
    fi
}

function startService(){
    name=""
#    for v in $ALLVMS; do
        if [[ -n $($SU $VBOXMANAGE showvminfo bid4work.twhg.home) ]]; then
            name=$(getVMName bid4work.twhg.home)
            output "Waiting for VM \"$name\" to power on..." 
            $SU $VBOXMANAGE startvm bid4work.twhg.home --type headless 1> /dev/null;
        else
            output  "No Saved VMs to start!";
        fi

        # If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
            output  "There was an error starting \"$name\"! Try starting it manually to see what the problem is."; 
            exit;
        else
            output "VM \"$name\" has been successfully started.";
        fi

        if [[ -n $($SU $VBOXMANAGE showvminfo zimbra.twhg.home) ]]; then
                        name=$(getVMName zimbra.twhg.home)
                        output "Waiting for VM \"$name\" to power on..." 
                        $SU $VBOXMANAGE startvm zimbra.twhg.home --type headless 1> /dev/null;
                else
                        output  "No Saved VMs to start!";
        fi

                # If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                        output  "There was an error starting \"$name\"! Try starting it manually to see what the problem is."; 
                        exit;
                else
                        output "VM \"$name\" has been successfully started.";
        fi
#    done
}

function restartService(){
    stopService;
    startService;
}

function force-reloadService(){
    stopService  #attempt to gracefully shutdown guests.
    
    #if any VMs are still up, forcibly reset them.
    if [[ !(-n getRunningVMs) ]]; then
        sdm=$SHUTDOWNMODE
        SHUTDOWNMODE="reset"
        
        stopService
        
        SHUTDOWNMODE=$sdm
    fi
    
    restartService
}

function serviceStatus(){
    logging=$ENABLELOGGING
    ENABLELOGGING="0" #disable logging if it is on
    
    if [[ -n $RUNNINGVMS ]]; then
        output "List of Running VMs:\n $(getRunningVMs)" ;
    else
        $ECHOCMD "No VMs Currently Running!";
    fi
    
    ENABLELOGGING=$logging
}

case $1 in
stop)
    stopService
;;
start)
    startService
;;
restart)
    restartService
;;
force-reload)
    force-reloadService
;;
status)
    serviceStatus
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop | status | restart | force-reload"; exit 1
;;
esac
exit 0
# eof
```

---

### Post by sparticle2000 on 2012-12-19
> **CharlesA said:**
> Which script are you using?

I don't use the logging utility, so I'm not sure what the problem with that is, but could you post the entire script?

Tried again with the code tags. 

```

sparticle@TWHGCS23VPS0:~$ sudo cat /etc/init.d/myvmboot.sh
#!/bin/bash

### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv $local_fs $syslog
# Required-Stop:  vboxdrv $local_fs $syslog
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs before/after System shutdown
### END INIT INFO

#---------- VMBoot ----------------------------------------------------#
# An LSB-Compliant Init script for VirtualBox 4.x guests on Ubuntu systems.
#
# Valid Parameter values:
#  start            Starts all VMs owned by VBOXUSER.
#  stop                Stops all VMs owned by VOXUSER. Stop behavoir is controled by SHUTDOWNMODE.
#  status            Prints a status message indicating running VMs.
#  restart            Stops and then starts all VMs. Stop behavoir is controled by SHUTDOWNMODE.
#  force-reload        Stops and then starts all VMs, resetting any that do not stop gracefully. Stop behavoir is controled by SHUTDOWNMODE.
#
# To Install:
#  Add this script to /etc/init.d/
#  Make the script executable with 'chmod +x /path/to/this/script' as root
#  Run update-rc.d vmboot defaults 99 01 as root
#
# To Configure:
#  Set VBOXUSER below adding the username of the user who created the VM. This is important because the VM config will reside in /home/$VBOXUSER/VirtualBox VMs/<Virtual Machine Name>/
#  Set SHUTDOWNMODE to your preference. valid values are: "acpipowerbutton", "savestate", "reset". reset can damage your virtual disks so don't use it.
#  Set ENABLELOGGING to enable or disable logging to the systemlog. when logging is enabled messages will be written to the syslog using the pattern contained in LOGGERMSG
#
# To Use:
#  Once Installed and configured, VMBoot works automatically on system boot and shutdown, like any other service.
#  You may manually control VMBoot, by calling the init script itself (as root), or by using the Service interface.
#        ex.     sudo /etc/init.d/vmboot start
#    OR
#        ex.     sudo service vmboot stop
#

#---------- User Settings ---------------------------------------------#
VBOXUSER="sparticle";                    #User who owns the VMs.
SHUTDOWNMODE="acpipowerbutton";        #shutdown or save state. acpipowerbutton|savestate
ENABLELOGGING="1";                    #en/disable syslogging. 1|0

#---------- Environment settings --------------------------------------# 
#Do not modify these values unless absolutely necessary.
VBOXMANAGE="/usr/bin/VBoxManage --nologo";
SU="sudo -H -u $VBOXUSER";
ECHOCMD="echo -e";
LOGGERMSG="$(echo -e `date "+%b %d %H:%M:%S"` `hostname` "$0": %s)\n";

#---------- Script -------------#

RUNNINGVMS=$($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/'); #UUID of All Running VMs. UUID looks like this: a02b5b54-a84d-48fa-8dac-2a3fad55717e
ALLVMS=$($SU $VBOXMANAGE list vms | sed -e 's/^".*".*{\(.*\)}/\1/');        #UUID of All VMs

# Check to insure $ALLVMS is not null and exit if it is.
if [[ $ALLVMS = "" ]]; then
    output  "No VMs are detected on this host! Did you configure the VBOXUSER variable?"; 
    exit;
fi

#outputs messages to the screen and log if logging is enabled
function output(){
    if [[ "$ENABLELOGGING" -eq "1" ]]; then
        $SU $ECHOCMD "$(printf "$LOGGERMSG" "$1")" >> /var/log/syslog;
        echo "$1"
    else
        $ECHOCMD "$1";
    fi
}

#return a given machines human readable name by UUID
function getVMName(){
    echo $($SU $VBOXMANAGE list vms | grep "$1" | awk -F\" '{print $(NF -1)}');
}

#return the list of currently running VMs. never gets stale.
function getRunningVMs(){
    echo $($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/');
}

function stopService(){
    if [[ -n $RUNNINGVMS ]]; then
    
        #set message based on SHUTDOWNMODE
        modemsg="Shutting Down";
        if [[ $SHUTDOWNMODE == "savestate" ]]; then
            modemsg="Saving state of";
        elif [[ $SHUTDOWNMODE == "reset" ]]; then
            modemsg="Aborting"
        fi
        
        #shutdown or save all running vms
        for v in $RUNNINGVMS; do
            name=$(getVMName $v)
            output "$modemsg $name...";
            $SU $VBOXMANAGE controlvm $v $SHUTDOWNMODE;
            
            # If this loop has an error, the loops exits and returns an error.
            if [[ $? -ne 0 ]]; then
                output  "There was an error $modemsg $name."; 
            else
                output "VMBoot has stopped $name.";
            fi
        done; 
        
        #wait for VMs to shutdown, if they haven't already.
        c=90;
        while [[ (-n $(getRunningVMs)) && ("$c" -gt "0") ]]; do
            sleep 1;
            c=$(($c - 1));
        done
        
        #if waited for specified number of seconds, log and exit.
        if [[ "$c" -eq "0" ]]; then
            output "Warning: One or more VMs failed to stop!";
        else
            output "VMBoot stopped all running VMs."
        fi
    else
        output "No running VMs to save!";
    fi
}

function startService(){
    name=""
#    for v in $ALLVMS; do
        if [[ -n $($SU $VBOXMANAGE showvminfo bid4work.twhg.home) ]]; then
            name=$(getVMName bid4work.twhg.home)
            output "Waiting for VM \"$name\" to power on..." 
            $SU $VBOXMANAGE startvm bid4work.twhg.home --type headless 1> /dev/null;
        else
            output  "No Saved VMs to start!";
        fi

        # If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
            output  "There was an error starting \"$name\"! Try starting it manually to see what the problem is."; 
            exit;
        else
            output "VM \"$name\" has been successfully started.";
        fi

        if [[ -n $($SU $VBOXMANAGE showvminfo zimbra.twhg.home) ]]; then
                        name=$(getVMName zimbra.twhg.home)
                        output "Waiting for VM \"$name\" to power on..." 
                        $SU $VBOXMANAGE startvm zimbra.twhg.home --type headless 1> /dev/null;
                else
                        output  "No Saved VMs to start!";
        fi

                # If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                        output  "There was an error starting \"$name\"! Try starting it manually to see what the problem is."; 
                        exit;
                else
                        output "VM \"$name\" has been successfully started.";
        fi
#    done
}

function restartService(){
    stopService;
    startService;
}

function force-reloadService(){
    stopService  #attempt to gracefully shutdown guests.
    
    #if any VMs are still up, forcibly reset them.
    if [[ !(-n getRunningVMs) ]]; then
        sdm=$SHUTDOWNMODE
        SHUTDOWNMODE="reset"
        
        stopService
        
        SHUTDOWNMODE=$sdm
    fi
    
    restartService
}

function serviceStatus(){
    logging=$ENABLELOGGING
    ENABLELOGGING="0" #disable logging if it is on
    
    if [[ -n $RUNNINGVMS ]]; then
        output "List of Running VMs:\n $(getRunningVMs)" ;
    else
        $ECHOCMD "No VMs Currently Running!";
    fi
    
    ENABLELOGGING=$logging
}

case $1 in
stop)
    stopService
;;
start)
    startService
;;
restart)
    restartService
;;
force-reload)
    force-reloadService
;;
status)
    serviceStatus
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop | status | restart | force-reload"; exit 1
;;
esac
exit 0
# eof



```

---

### Post by CharlesA on 2012-12-19
OK, the script it meant to be run via sudo, so that would get rid of the permission denied messages for the syslog.

It looks like you fixed the error on line 140, by changing break to exit.

I am not sure what "zimbra.twhg.home" or "bid4work.twhg.home" are, but I am going to assume they are the VMs you wish to power on.

I'm not sure how you can do that outside of adding them directly to the script itself.

---

### Post by sparticle2000 on 2012-12-19
Yes they are VM's. I don't really know if exit was the right answer. Does that exit the if/fi or the entire script?

Is $ALLVMS an array that gets populated from the list command?

If so, could I populate it from a file somehow by reading each line into the $ALLVMS array element? in much the same way. If this can be done then the original script would need no modification to the start and stop functions. It is really only the list of VM's to start that I need to figure out. 

Any help appreciated. BASH scripting is like Russian crossed with reverse nor to me!

Cheers
Spart

---

### Post by CharlesA on 2012-12-19
If you only want a certain number of VMs to power on automatically, you can rewrite the entire start function into something like this:

```

VMNAME="test testing testo"

for v in $VMNAME; do
        echo $SU $VBOXMANAGE startvm $v --type headless;
done
```

Note: This is just a quick example. There is no error checking.

I used echo to check the commands without running them (as the box I tested it on doesn't have Vbox installed)

This is what the output looked like:

```
sudo -H -u sparticle /usr/bin/VBoxManage --nologo startvm test --type headless
sudo -H -u sparticle /usr/bin/VBoxManage --nologo startvm testing --type headless
sudo -H -u sparticle /usr/bin/VBoxManage --nologo startvm testo --type headless

```

EDIT: Not sure how that will work with spaces, but it's a start. :)

As far as the exit command - I am not sure. It will either exit the script entirely or not do anything. I had break in there because it was running a loop and that would allow the loop to end if there was an error.

In any case, I looked at your script and it looks like every line is ending with ";" which is unnecessary.

If you want a semi-better script, you can check out the one I have updated over time here:
[http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php](http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php)

It is different from the one doas777 did, but his script is based off my original one. ;)

---

### Post by sparticle2000 on 2012-12-19
Hey thanks for this. Looks like I need to learn at least some basic scripting. I will work on it tomorrow it is now 04:40 and I am bleary eyed. 

Thank you so much.

Cheers
Spart

---

### Post by CharlesA on 2012-12-19
Good luck! It takes some time to figure out how different logic works but it'll be worth it in the end.

---

### Post by sparticle2000 on 2012-12-20
> **CharlesA said:**
> Good luck! It takes some time to figure out how different logic works but it'll be worth it in the end.

OK here is the latest version running on my test VM host machine. I can't figure out how to make  function getRunningVMs() to output the names and UUIDs one per line [IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]

```

sparticle@TWHGCS23VPS0:~$ cat /etc/init.d/myvmboot.sh
#!/bin/bash
### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv $local_fs $syslog
# Required-Stop:  vboxdrv $local_fs $syslog
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs before/after System shutdown
# script originally by CharlesA and modified by Doas777 from Ubuntu forums
# hacked by noob sparticle2000 from Ubuntu forums to enable selective list of machines to start
### END INIT INFO

#---------- VMBoot ----------------------------------------------------#
# An LSB-Compliant Init script for VirtualBox 4.x guests on Ubuntu systems.
#
# Valid Parameter values:
#  start            Starts all VMs owned by VBOXUSER.
#  stop                Stops all VMs owned by VOXUSER. Stop behavoir is controled by SHUTDOWNMODE.
#  status            Prints a status message indicating running VMs.
#  restart            Stops and then starts all VMs. Stop behavoir is controled by SHUTDOWNMODE.
#  force-reload        Stops and then starts all VMs, resetting any that do not stop gracefully. Stop behavoir is controled by SHUTDOWNMODE.
#
# To Install:
#  Add this script to /etc/init.d/
#  Make the script executable with 'chmod +x /path/to/this/script' as root
#  Run update-rc.d vmboot defaults 99 01 as root
#
# To Configure:
#  Set VBOXUSER below adding the username of the user who created the VM. This is important because the VM config will reside in /home/$VBOXUSER/VirtualBox VMs/<Virtual Machine Name>/
#  Set SHUTDOWNMODE to your preference. valid values are: "acpipowerbutton", "savestate", "reset". reset can damage your virtual disks so don't use it.
#  Set ENABLELOGGING to enable or disable logging to the systemlog. when logging is enabled messages will be written to the syslog using the pattern contained in LOGGERMSG
#
# To Use:
#  Once Installed and configured, VMBoot works automatically on system boot and shutdown, like any other service.
#  You may manually control VMBoot, by calling the init script itself (as root), or by using the Service interface.
#        ex.     sudo /etc/init.d/vmboot start
#    OR
#        ex.     sudo service vmboot stop
#

#---------- User Settings ---------------------------------------------#
VBOXUSER="sparticle";                       #User who owns the VMs.
SHUTDOWNMODE="acpipowerbutton";                           #shutdown or save state. acpipowerbutton|savestate
ENABLELOGGING="1";                       #en/disable syslogging. 1|0
VMSTOSTART="bid4work.twhg.home zimbra.twhg.home";          #Insert list of your VM Names to start. Alternatively 
                                                           #change $VMSTOSTART to $ALLVMS in function startService()
                                                           #to start all VM's owned by $VBOXUSER
#---------- Environment settings --------------------------------------# 
#Do not modify these values unless absolutely necessary.
VBOXMANAGE="/usr/bin/VBoxManage --nologo";
SU="sudo -H -u $VBOXUSER";
ECHOCMD="echo -e";
LOGGERMSG="$(echo -e `date "+%b %d %H:%M:%S"` `hostname` "$0": %s)\n";

#---------- Script -------------#

RUNNINGVMS=$($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/'); #UUID of All Running VMs. UUID looks like this: a02b5b54-a84d-48fa-8dac-2a3fad55717e
ALLVMS=$($SU $VBOXMANAGE list vms | sed -e 's/^".*".*{\(.*\)}/\1/');        #UUID of All VMs

# Check to ensure $ALLVMS is not null and exit if it is.
if [[ $ALLVMS = "" ]]; then
    output  "No VMs are detected on this host! Did you configure the VBOXUSER variable?"; 
    exit;
fi

#outputs messages to the screen and log if logging is enabled
function output(){
    if [[ "$ENABLELOGGING" -eq "1" ]]; then
        $SU $ECHOCMD "$(printf "$LOGGERMSG" "$1")" >> /var/log/syslog;
        echo "$1"
    else
        $ECHOCMD "$1";
    fi
}

#return a given machines human readable name by UUID
function getVMName(){
    echo $($SU $VBOXMANAGE list vms | grep "$1" | awk -F\" '{print $(NF -1)}');
}

#return the list of currently running VM's when 'service myvmboot.sh status' is used. Never gets stale.
function getRunningVMs(){
#    echo $($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/'); #This prints just the UUId's
        echo $($SU $VBOXMANAGE list runningvms | awk -F\" '{print $(NF -1)}' );   #Changed to print just the machine names
#       echo $($SU $VBOXMANAGE list runningvms);                                  #Changed to print the machine names and UUID's
#
#       **** Cannot figure out how to output each machine name on a newline. The normal 'VBoxManage list runningvms' command ****
#       **** lists the machine name and UUID for each machine on a newline. With the above everything is just on one line    ****
#       **** probably smething that SED can do but all hieroglyphics to me at present :)                                     ****                   
}

function stopService(){
    if [[ -n $RUNNINGVMS ]]; then
    
        #set message based on SHUTDOWNMODE
        modemsg="Shutting Down";
        if [[ $SHUTDOWNMODE == "savestate" ]]; then
            modemsg="Saving state of";
        elif [[ $SHUTDOWNMODE == "reset" ]]; then
            modemsg="Aborting"
        fi
        
        #shutdown or save all running vms
        for v in $RUNNINGVMS; do
            name=$(getVMName $v)
            output "$modemsg $name...";
            $SU $VBOXMANAGE controlvm $v $SHUTDOWNMODE;
            
            # If this loop has an error, the loops exits and returns an error.
            if [[ $? -ne 0 ]]; then
                output  "There was an error $modemsg $name."; 
            else
                output "VMBoot has stopped $name.";
            fi
        done; 
        
        #wait for VMs to shutdown, if they haven't already.
        c=90; # I use 90 seconds as the mail servers tend to take a while to shutdown
        while [[ (-n $(getRunningVMs)) && ("$c" -gt "0") ]]; do
            sleep 1;
            c=$(($c - 1));
        done
        
        #if waited for specified number of seconds, log and exit.
        if [[ "$c" -eq "0" ]]; then
            output "Warning: One or more VMs failed to stop!";
        else
            output "VMBoot stopped all running VMs."
        fi
    else
        output "No running VMs to save!";
    fi
}

function startService(){
    name=""
    for v in $VMSTOSTART; do                                #Replace $VMSTOSTART with $ALLVMS to start all VM's owned by $VBOXUSER
        if [[ -n $($SU $VBOXMANAGE showvminfo $v) ]]; then
            name=$(getVMName $v)
            output "Waiting for VM \"$name\" to power on..." 
            $SU $VBOXMANAGE startvm $v --type headless 1> /dev/null;
        else
            output  "No Saved VMs to start!";
        fi

        # If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
            output  "There was an error starting \"$name\"! Try starting it manually to see what the problem is."; 
            break;
        else
            output "VM \"$name\" has been successfully started.";
        fi

    done
}

function restartService(){
    stopService;
    startService;
}

function force-reloadService(){
    stopService  #attempt to gracefully shutdown guests.
    
    #if any VMs are still up, forcibly reset them.
    if [[ !(-n getRunningVMs) ]]; then
        sdm=$SHUTDOWNMODE
        SHUTDOWNMODE="reset"
        
        stopService
        
        SHUTDOWNMODE=$sdm
    fi
    
    restartService
}

function serviceStatus(){
    logging=$ENABLELOGGING
    ENABLELOGGING="0" #disable logging if it is on
    
    if [[ -n $RUNNINGVMS ]]; then
        output "List of Running VMs:\n $(getRunningVMs)" ;
    else
        $ECHOCMD "No VMs Currently Running!";
    fi
    
    ENABLELOGGING=$logging
}

case $1 in
stop)
    stopService
;;
start)
    startService
;;
restart)
    restartService
;;
force-reload)
    force-reloadService
;;
status)
    serviceStatus
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop | status | restart | force-reload"; exit 1
;;
esac
exit 0
# eof


```

Cheers
Spart

---

### Post by CharlesA on 2012-12-20
If you do not care about extra spaces you can use this:

```
echo "List of running VMs:" && $SU $VBOXMANAGE list runningvms | awk -F \" '{ print $2 }'
```

---

### Post by sparticle2000 on 2012-12-20
> **CharlesA said:**
> If you do not care about extra spaces you can use this:

```
echo "List of running VMs:" && $SU $VBOXMANAGE list runningvms | awk -F \" '{ print $2 }'
```


Settled on this: 

```

        echo && $SU $VBOXMANAGE list runningvms | awk -F \" '{ print $2, $3 }';


```

Just what I wanted. Many thanks again for your help. The syntax of awk and sed is a nightmare for the uninitiated.

Cheers
Spart

---

### Post by sparticle2000 on 2012-12-20
This is now working brilliantly, tested with 20 VM's linux and windows on manual start, stop, status and on reboot and powerup of the server. It is simple and intuitive and the service interface makes it seem very polished to use.

Awesome stuff thank you. I really hope this helps others as this was a nightmare to try and get working using the VirtualBox autostart and docs.

Don't forget to install the acpid utility if using acpipowerbutton mode of shutdown. 

Everything is logged into syslog for posterity, you can also see what is going on with 'tail -f -v  /var/log/syslog'

Cheers
Spart

---

### Post by CharlesA on 2012-12-20
Awesome. Glad you got it working!

---

### Post by jizzner on 2013-05-10
i cant seem to make it work please help me.. what vbox user am i looking for?  iv tried several user but cant make it work.. please help

---

### Post by CharlesA on 2013-05-10
You need to tell it to run as whatever user you have those VMs running as. I have mine running under vboxuser.

---

### Post by JKyleOKC on 2013-05-10
The user in these scripts should be the one that owns the VMs. The default installation of vbox puts the VM directories under $HOME of the user who's installing the package, which normally is your own home directory. In that case, VBOXUSER in the scripts should be set to your user name.

Hope this helps...

EDIT: I see that Charles runs his VMs under a different user name, but that may be a bit advanced for you if you're having problems getting the scripts to work. Use a search utility such as find or catfish to locate your *.vdi files, which will be in a subdirectory of some user's home directory. That user will be the one to use.

---

### Post by CharlesA on 2013-05-10
> **JKyleOKC said:**
> The user in these scripts should be the one that owns the VMs. The default installation of vbox puts the VM directories under $HOME of the user who's installing the package, which normally is your own home directory. In that case, VBOXUSER in the scripts should be set to your user name.

Hope this helps...

EDIT: I see that Charles runs his VMs under a different user name, but that may be a bit advanced for you if you're having problems getting the scripts to work. Use a search utility such as find or catfish to locate your *.vdi files, which will be in a subdirectory of some user's home directory. That user will be the one to use.

This pretty much covers it.

If there is only one user on the machine, the VMs would be run under that user's account.

---

### Post by jizzner on 2013-05-10
im still trying to understand the script. could you help me understand ? i was wondering if i will only shutdown my ubuntu server without shuting down the VMs will the script safely shutdown the running VMs?

---

### Post by CharlesA on 2013-05-10
Yes. You can test it by running it manually:
```
/etc/init.d/***scriptname*** stop
```

---

### Post by jizzner on 2013-05-10
i have tried the script. but i was afraid maybe my VMs would get corrupted? is there a possibility that this would occur? thank you for your response.

---

### Post by CharlesA on 2013-05-10
That is unlikely to occur. The script calls the functions VirtualBox uses when shutting down or saving the state of the VM. Unless your machine is powered off unexpectedly, you should be fine as long as the script is working.

Have you tested it already?

---

### Post by jizzner on 2013-05-10
yes sir i have tried the script and it works thank you sir

---

