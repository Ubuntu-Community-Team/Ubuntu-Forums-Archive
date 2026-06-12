---
title: "Make ups turn ubuntu off and virtual box save state"
date: 2011-12-04
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2011-12-04
[http://www.amazon.com/gp/product/B0019804U8/ref=oh_o00_s00_i00_details](http://www.amazon.com/gp/product/B0019804U8/ref=oh_o00_s00_i00_details)

So I have one of these, it only lasts for like 2 minutes with my server
q6600 @ 3.4 ghz 8 gigs of ram 12hds

I am not at my server and won't be until like two weeks but whenever poweroutages happen like long ones my virtual machines get corrpted and then chkdsk has to work or fsck.


This is not very comforting.


So I know it has some plug that plugs into usb, but does Ubuntu support this stuff?

If I do get it recognized how would I make the virtual box machines save state and then after say 45 seconds assuming it's done to make the machine turn off?

---

### Post by 2F4U on 2011-12-04
These posts suggest that it works with Linux and Ubuntu in particular:

[http://forums.fedoraforum.org/archive/index.php/t-213529.html](http://forums.fedoraforum.org/archive/index.php/t-213529.html)
[http://www.gavinhollinger.com/2011/08/apcupsd-using-ubuntu-and-be550g-apc.html](http://www.gavinhollinger.com/2011/08/apcupsd-using-ubuntu-and-be550g-apc.html)

---

### Post by JigglyWiggly_ on 2011-12-05
Neat, I'll look into it when Winter break starts. I am not experienced with Linux scripting, so what I plan to do in just a lil java or C++ program is just


So how do I make it so on powerloss it will start a script with apcupsd?

If I can get that done, program will just: 
VBoxManage controlvm <vm> savestate
Then I guess just wait 30 seconds since I don't know how I would poll to check if that VM was still up since there are multiple processes called virtualbox.

Then just sudo halt
and maybe the program can just write my password to the terminal
Though this is like bad security practice (Any better way to  do this?) Because if I wrote it in say java, a person up to no good get a decompiler and look at the String... not that anyone is going to bother to do that to me, but good practice.

I have a question though on that last step how would I make it enter my password or something?

---

### Post by CharlesA on 2011-12-05
What UPS are you using?

I have a startup script that saves the state of any running VMs when the machine shutsdown. I have an APC UPS, so I use apcupsd to control it.

The startup/shutdown script I use is on my site: [http://charlesa.net](http://charlesa.net)

EDIT: I have used both an APC 650VA and another APC UPS which is my current one, but I think it's a 850VA.

---

### Post by JigglyWiggly_ on 2011-12-05
UPS I am using is in the amazon link, lots of description there.
So how do I make apc launch a script?
Because I think your script needs to also be called by apc. Though I must say, your script looks very nicely written, mine woulda been a bit <snip> and written in C++/java depending on my mood.

```
#!/bin/bash

###
### stopvm.sh
### Script to save state of running VMs
### Created by CharlesA
### Updated 1/23/2011
###

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
USR=/usr/bin/

if [[ -n $(${USR}VBoxManage -nologo list runningvms) ]]
  then
    for runningvms in $(${USR}VBoxManage -nologo list runningvms | ${USR}awk -F \" '{ print $2 }')
    do
    echo Saving state of $runningvms && ${USR}VBoxManage -nologo controlvm $runningvms savestate
    done
  else
    echo "No VMs running"
fi
IFS=$SAVEIFS
# eof
```

Just making sure, when it says NO VMs running will it say that after the savestate has been completed or will it just say that after running the above line?

---

### Post by CharlesA on 2011-12-05
> **JigglyWiggly_ said:**
> UPS I am using is in the amazon link, lots of description there.
So how do I make apc launch a script?
Because I think your script needs to also be called by apc. Though I must say, your script looks very nicely written, mine woulda been a bit <snip> and written in C++/java depending on my mood.

The way I have mine set up is that it runs the stop portion of the script at runlevel 0 and 6 (halt and reboot, respectively).

You don't even need to do anything with apcupsd, as it will automatically shut the machine down (and run all shutdown scripts) after the machine has been on battery for a set about of time.

EDIT: The startvm and stopvm scripts are older ones, the one I'm using now is this one:

```
#!/bin/bash

### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv
# Required-Stop:  vboxdrv
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs before/after System shutdown
### END INIT INFO

# Add this script to /etc/init.d/
# Run update-rc.d vmboot defaults as root

# Written to work with VirtualBox 4.x

# User who is running the VMs
VBOXUSER=vboxuser
SU="sudo -H -u $VBOXUSER"
# Path to VBoxManage
VBOXMANAGE="/usr/bin/VBoxManage --nologo"
# Get UUID of All Running VMs
# UUID looks like this: a02b5b54-a84d-48fa-8dac-2a3fad55717e
RUNNINGVMS=$($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/')
# Get UUID of All VMs
ALLVMS=$($SU $VBOXMANAGE list vms | sed -e 's/^".*".*{\(.*\)}/\1/')

# Check to insure $ALLVMS is not null and exit if it is.
if [[ $ALLVMS = "" ]]; then
        echo "No VMs are detected on this host! Did you configure the VBOXUSER variable?"; exit
fi

case $1 in
stop)
if [[ -n $RUNNINGVMS ]]; then
        for v in $RUNNINGVMS; do
        echo -e "Saving state of $($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF-1)}')..." && $SU $VBOXMANAGE controlvm $v savestate
        done; else
        echo "No running VMs to save!"
fi
;;
start)
for v in $ALLVMS; do
        if [[ -n $($SU $VBOXMANAGE showvminfo $v | grep saved) ]]; then
                echo -e "Waiting for VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF -1)}')\" to power on..." && $SU $VBOXMANAGE startvm $v --type headless 1> /dev/null && echo -e  "VM \"$($SU $VBOXMANAGE list vms | grep $v | awk -F\" '{print $(NF-1)}')\" has been successfully started."; else
                echo "No Saved VMs to start!"

        fi
# If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                echo "There was an error starting your VMs! Try starting them manually to see what the problem is."; break
        fi
done
;;
status)
if [[ -n $RUNNINGVMS ]]; then
        echo "List of Running VMs:" && $SU $VBOXMANAGE list runningvms; else
                echo "No VMs Currently Running!"
fi
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop | status"; exit 1
;;
esac
exit 0
# eof
```

You can use my script if you want, or the one that is [here]("http://ubuntuforums.org/showthread.php?t=1844885"). Why remake the wheel? :p

---

### Post by JigglyWiggly_ on 2011-12-05
Thx for the help, very nice.

Though you said it will run all shutdown scripts and then shutdown, how do I tell it that your script is a shutdown script? Like where do I place it?

Nm i just googled
> Put your script in /etc/rc6.d
and make it executable (sudo chmod +x myscript)



I think I will just use the stop script though as I only want it to save them, I have quite a few vms but I only use like half of them. And I can't run them at startup, I mount my RAID 6 array first, and I don't want it being automounted since I might do something first.

Thx for the help btw, much appreciated.

---

### Post by CharlesA on 2011-12-05
> **JigglyWiggly_ said:**
> Thx for the help, very nice.

Though you said it will run all shutdown scripts and then shutdown, how do I tell it that your script is a shutdown script? Like where do I place it?

Nm i just googled

Instructions are in the script. ;)

Put the script into a file named vmboot in /etc/init.d/, then run:

```
sudo update-rc.d vmboot defaults
```

---

### Post by JigglyWiggly_ on 2012-03-19
I just realized why this wasnt working


When it calls the script, it's doing it as root

VBoxManage list runningvms

and nothing shows up

but it needs to be running as my user for the vms to show up, how can I get around this...?

---

### Post by JigglyWiggly_ on 2012-03-19
```
#!/bin/bash

###
### stopvm.sh
### Script to save state of running VMs
### Created by CharlesA
### Updated 1/23/2011
###

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
USR=/usr/bin/

if [[ -n $(${USR}VBoxManage -nologo list runningvms) ]]
  then
    for runningvms in $(${USR}VBoxManage -nologo list runningvms | ${USR}awk -F \" '{ print $2 }')
    do
    echo Saving state of $runningvms && ${USR}VBoxManage -nologo controlvm $runningvms savestate
    done
  else
    echo "No VMs running"
fi
IFS=$SAVEIFS
# eof
```


ok this runs it as administrator
su "administrator" -c "BoxManage -nologo list runningvms"


but how do I change the above to use this


I tried in the if statement(I duno anything about linux scripting)


```
if [[ -n $(su "administrator" -c "VBoxManage -nologo list runningvms"
) ]]
```

but then it says no such file as su in /usr/bin/su no such file or directory

---

### Post by JigglyWiggly_ on 2012-03-19
o wait i got it
gj me

```
#!/bin/bash

###
### stopvm.sh
### Script to save state of running VMs
### Created by CharlesA
### Updated 1/23/2011
###

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
USR=/usr/bin/

if [[ -n $(su "administrator" -c "VBoxManage -nologo list runningvms"
) ]]
  then
    for runningvms in $(su "administrator" -c "VBoxManage -nologo list runningvms" | ${USR}awk -F \" '{ print $2 }')
    do
    echo Saving state of $runningvms && su "administrator" -c "VBoxManage -nologo controlvm $runningvms savestate"
    done
  else
    echo "No VMs running"
fi
IFS=$SAVEIFS
# eof
```

---

### Post by CharlesA on 2012-03-19
Check out [the updated vmboot script]("http://charlesa.net/scripts/linux/vboxscript.php"). The only thing you would have to change would be the VBOXUSER variable.

In any case, it looks like you got it working.

---

### Post by JigglyWiggly_ on 2012-03-25
But I like the old one because it's simpler.
 The new one just has startup scripts which won't work for me since I have to mount my file system first.

however... it's not workign still D:

I even added it to /etc/init.d/halt and when I call halt, it doesn't launch

but if I just launch the script as root it works

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO




SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
USR=/usr/bin/

if [[ -n $(su "administrator" -c "VBoxManage -nologo list runningvms"
) ]]
  then
    for runningvms in $(su "administrator" -c "VBoxManage -nologo list runningvms" | ${USR}awk -F \" '{ print $2 }')
    do
    echo Saving state of $runningvms && su "administrator" -c "VBoxManage -nologo controlvm $runningvms savestate"
    done
  else
    echo "No VMs running"
fi
IFS=$SAVEIFS











NETDOWN=yes

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
	if [ "$INIT_HALT" = "" ]
	then
		case "$HALT" in
		  [Pp]*)
			INIT_HALT=POWEROFF
			;;
		  [Hh]*)
			INIT_HALT=HALT
			;;
		  *)
			INIT_HALT=POWEROFF
			;;
		esac
	fi

	# See if we need to cut the power.
	if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
	then
		/etc/init.d/ups-monitor poweroff
	fi

	# Don't shut down drives if we're using RAID.
	hddown="-h"
	if grep -qs '^md.*active' /proc/mdstat
	then
		hddown=""
	fi

	# If INIT_HALT=HALT don't poweroff.
	poweroff="-p"
	if [ "$INIT_HALT" = "HALT" ]
	then
		poweroff=""
	fi

	# Make it possible to not shut down network interfaces,
	# needed to use wake-on-lan
	netdown="-i"
	if [ "$NETDOWN" = "no" ]; then
		netdown=""
	fi

	log_action_msg "Will now halt"
	halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

:
```

I even put the code in the apcupsd config and still no go.
I don't see why would the new script fix my problem, do you think it's worth a shot?

I'm not entirely sure how apcupsd is doing stuff. I think it calls halt, but I just called halt manually as root and it didn't execute the  code, so I am confused.

---

### Post by CharlesA on 2012-03-25
You can always run a check to make sure something is mounted and have the script run when that file system is mounted.

I've tested both the old script and new script on my Lucid box and it runs as expected. If you run it manually, does it work?

---

### Post by JigglyWiggly_ on 2012-03-25
Works fine if I run it manually, that's why I am really confused lol

(When I run, I run it as root)

---

### Post by CharlesA on 2012-03-25
Take a look at the SU variable in the startup script. It basically does the same thing as su except it uses sudo instead.

EDIT: apcupsd only calls "halt" when triggered, so as long as the script runs before the system halts, it should run, then power off the machine.

---

### Post by JigglyWiggly_ on 2012-03-25
But, I am still confused though, I put the code before halt ran, right? So when halt is called (I mean I am just typing sudo halt)
it should save the vm right? Because when I have a dedicated file for the shutdown and run it, it works fine.

---

### Post by CharlesA on 2012-03-25
I made the startup script so I could just run sudo halt or sudo reboot without having to use an alias to run the save state script before halting/rebooting.

I'm not sure how you set the script up. Did you add it to /etc/init.d/ ?

---

### Post by JigglyWiggly_ on 2012-03-25
yeah what i posted up is the modified /etc/init.d/halt

---

### Post by CharlesA on 2012-03-25
Have the script echo to a log file to see what is causing it to hang.

Add something like this to the end of each line:

```
>> /path/to/some/log 2>&1
```

The way I have mine set up is to add the script to /etc/init.d/ and then run as root or with sudo:

```
update-rc.d vmboot defaults 99 01
```

It should wait for all local file systems to be mounted before running.

---

### Post by JigglyWiggly_ on 2012-03-25
I changed halt to 
```
do
    echo Saving state of $runningvms && su "administrator" -c "VBoxManage -nologo controlvm $runningvms savestate" && echo hello >> /home/administrator/Desktop/lol.txt
```

does this look proper? I added my text at the end (I am not familiar with bash)

Also just to clarify, halt did not hang, it worked, but it seemed to ignore my code completely.

---

### Post by CharlesA on 2012-03-25
To capture the entire output you're going to have to change it to look something like this:

```
{ echo Saving state of $runningvms && su "administrator" -c "VBoxManage -nologo controlvm $runningvms savestate" && echo hello; } >> /home/administrator/Desktop/lol.txt 2>&1
```

That should capture the entire output of the command and let you see what is going on.

---

### Post by JigglyWiggly_ on 2012-03-25
you put a start bracket, should there be one at the end?

---

### Post by CharlesA on 2012-03-25
> **JigglyWiggly_ said:**
> you put a start bracket, should there be one at the end?

It has the closing bracket:

```
[COLOR="Red"]{[/COLOR] echo Saving state of $runningvms && su "administrator" -c "VBoxManage -nologo controlvm $runningvms savestate" && echo hello; [COLOR="Red"]}[/COLOR] >> /home/administrator/Desktop/lol.txt 2>&1
```

---

### Post by JigglyWiggly_ on 2012-03-25
None of what I wrote happens
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO


echo hello >> /home/administrator/Desktop/1st.txt

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
USR=/usr/bin/

if [[ -n $(su "administrator" -c "VBoxManage -nologo list runningvms"
) ]]
  then
    for runningvms in $(su "administrator" -c "VBoxManage -nologo list runningvms" | ${USR}awk -F \" '{ print $2 }')
    do
    { echo Saving state of $runningvms && su "administrator" -c "VBoxManage -nologo controlvm $runningvms savestate" && echo hello; } >> /home/administrator/Desktop/lol.txt 2>&1 


    done
  else
    echo "No VMs running"
fi
IFS=$SAVEIFS











NETDOWN=yes

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
	if [ "$INIT_HALT" = "" ]
	then
		case "$HALT" in
		  [Pp]*)
			INIT_HALT=POWEROFF
			;;
		  [Hh]*)
			INIT_HALT=HALT
			;;
		  *)
			INIT_HALT=POWEROFF
			;;
		esac
	fi

	# See if we need to cut the power.
	if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
	then
		/etc/init.d/ups-monitor poweroff
	fi

	# Don't shut down drives if we're using RAID.
	hddown="-h"
	if grep -qs '^md.*active' /proc/mdstat
	then
		hddown=""
	fi

	# If INIT_HALT=HALT don't poweroff.
	poweroff="-p"
	if [ "$INIT_HALT" = "HALT" ]
	then
		poweroff=""
	fi

	# Make it possible to not shut down network interfaces,
	# needed to use wake-on-lan
	netdown="-i"
	if [ "$NETDOWN" = "no" ]; then
		netdown=""
	fi

	log_action_msg "Will now halt"
	halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

:
```

also side related just reoboted and my raid array is degraded, then I hit attatch in disk utility and it comes back, why do I gotta do that...?
Friggen lunix is being an ******* to me D:

---

### Post by CharlesA on 2012-03-26
D'oh! That's strange that it's degrading. =/

Does the script run as intended?

---

### Post by JigglyWiggly_ on 2012-03-26
Aite i've calmed down ;D
but no the script doesn't work, I mean nothing gets called. Maybe it's not calling this file and doing something else?


Well my raid array is back thankfully as well. I think a hard drive was failing and after all the reboots it got kicked out.


[http://homepage1.nifty.com/Que/plamo/apc-ups/manual/events.html](http://homepage1.nifty.com/Que/plamo/apc-ups/manual/events.html)

also here it says make a file called powerout, I put the script in there (not the halt part) and it doesn't work either. I am pretty confused tbh.

---

### Post by CharlesA on 2012-03-26
Huh. Does the startup script work if you change the VBOXUSER variable and then run it as root?

I know you don't want to use it, but it might help with figuring out why the other script isn't working.

---

### Post by JigglyWiggly_ on 2012-03-26
Alright, update-rc.d vmboot defaults 99 01
your script works when i run it manualyl as root.
chmod +x'd it
and /etc/init.d/vmboot stop works


but i dont think apcupsd even bothers to call anything in rc0.d, just halt.

btw if i havent mentioned already ty for helping so far :>

---

### Post by CharlesA on 2012-03-26
Yeah, I just leave apcupsd alone, it calls halt and that will cause the system to enter runlevel 0, which runs all the scripts and junk in rc0.d.

I've got that script running on my Lucid box and I had a power outage the other day and it ran fine. ;)

If you want to test it, try halting or rebooting the system manually and see if the script runs.

---

### Post by JigglyWiggly_ on 2012-03-26
If I try to reboot through the GUI, it won't let me because virtualbox pops up asking me if I want to save.
Also, halt calls all the things in rc0.d? I though rc0.d is called and then halt runs at the end.

---

### Post by CharlesA on 2012-03-26
I'm not totally sure. I just know it runs things are runlevel0 then halts.

Hrm, the script was written for a headless server, not sure if it will work when the GUI is running. You might need to mess with when it runs so that it runs before the GUI closes out.

---

### Post by JigglyWiggly_ on 2012-03-26
Makes sense, probably when the gui closes, so does virtualbox.

That probably will screw everything up :? I don't think there is a way around this.


EDIT: I have an idea
[http://www.apcupsd.com/manual/manual.html](http://www.apcupsd.com/manual/manual.html)

there is an onbattery thing, perhaps in there I can tell it to save my vms.




In apcupsd folder the onbattery config file
I think this should do the trick, look okay?
```
#!/bin/sh
#
# This shell script if placed in /etc/apcupsd
# will be called by /etc/apcupsd/apccontrol when the UPS
# goes on batteries.
# We send an email message to root to notify him.
#
SYSADMIN=root
APCUPSD_MAIL="mail"

HOSTNAME=`hostname`
MSG="$HOSTNAME Power Failure !!!"
#
(
[COLOR="Red"]**/etc/init.d/vmboot stop **[/COLOR]
   echo "Subject: $MSG"
   echo " "
   echo "$MSG"
   echo " "
   /sbin/apcaccess status
) | $APCUPSD_MAIL -s "$MSG" $SYSADMIN
exit 0
```

---

### Post by CharlesA on 2012-03-26
That might work.

---

### Post by JigglyWiggly_ on 2012-03-26
it worked :) :):) :popcorn:
tyty

for anyone else who has this problem in the future

i also have the file powerout modified, not sure if it did anything
```
/etc/init.d/vmboot stop
cd /etc/init.d/
bash vmboot stop
```


my onbattery
```
#!/bin/sh
#
# This shell script if placed in /etc/apcupsd
# will be called by /etc/apcupsd/apccontrol when the UPS
# goes on batteries.
# We send an email message to root to notify him.
#
SYSADMIN=root
APCUPSD_MAIL="mail"

HOSTNAME=`hostname`
MSG="$HOSTNAME Power Failure !!!"
#
(
/etc/init.d/vmboot stop
   echo "Subject: $MSG"
   echo " "
   echo "$MSG"
   echo " "
   /sbin/apcaccess status
) | $APCUPSD_MAIL -s "$MSG" $SYSADMIN
exit 0
```


my apcupsd.conf
```
## apcupsd.conf v1.1 ##
# 
#  for apcupsd release 3.14.6 (16 May 2009) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
#UPSNAME

# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
UPSCABLE usb


# To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB. A blank DEVICE
#                            setting enables autodetection, which is
#                            the best choice for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's 
#                            rfc1628 UPS-MIB. You usually want "APC".
#                            Port is usually 161. Community is usually
#                            "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
# pcnet    ipaddr:username:passphrase
#                            PowerChute Network Shutdown protocol
#                            which can be used as an alternative to SNMP
#                            with AP9617 family of smart slot cards.
#                            ipaddr is the IP address of the UPS mgmt
#                            card. username and passphrase are the
#                            credentials for which the card has been
#                            configured.
#
UPSTYPE usb
DEVICE

# POLLTIME <int>
#   Interval (in seconds) at which apcupsd polls the UPS for status. This
#   setting applies both to directly-attached UPSes (UPSTYPE apcsmart, usb, 
#   dumb) and networked UPSes (UPSTYPE net, snmp). Lowering this setting
#   will improve apcupsd's responsiveness to certain events at the cost of
#   higher CPU utilization. The default of 60 is appropriate for most
#   situations.
#POLLTIME 60

# LOCKFILE <path to lockfile>
#   Path for device lock file. Not used on Win32.
LOCKFILE /var/lock

# SCRIPTDIR <path to script directory>
#   Directory in which apccontrol and event scripts are located.
SCRIPTDIR /etc/apcupsd

# PWRFAILDIR <path to powerfail directory>
#   Directory in which to write the powerfail flag file. This file
#   is created when apcupsd initiates a system shutdown and is
#   checked in the OS halt scripts to determine if a killpower
#   (turning off UPS output power) is required.
PWRFAILDIR /etc/apcupsd

# NOLOGINDIR <path to nologin directory>
#   Directory in which to write the nologin file. The existence
#   of this flag file tells the OS to disallow new logins.
NOLOGINDIR /etc


#
# ======== Configuration parameters used during power failures ==========
#

# The ONBATTERYDELAY is the time in seconds from when a power failure
#   is detected until we react to it with an onbattery event.
#
#   This means that, apccontrol will be called with the powerout argument
#   immediately when a power failure is detected.  However, the
#   onbattery argument is passed to apccontrol only after the 
#   ONBATTERYDELAY time.  If you don't want to be annoyed by short
#   powerfailures, make sure that apccontrol powerout does nothing
#   i.e. comment out the wall.
ONBATTERYDELAY 6

# 
# Note: BATTERYLEVEL, MINUTES, and TIMEOUT work in conjunction, so
# the first that occurs will cause the initation of a shutdown.
#

# If during a power failure, the remaining battery percentage
# (as reported by the UPS) is below or equal to BATTERYLEVEL, 
# apcupsd will initiate a system shutdown.
BATTERYLEVEL 40

# If during a power failure, the remaining runtime in minutes 
# (as calculated internally by the UPS) is below or equal to MINUTES,
# apcupsd, will initiate a system shutdown.
MINUTES 1

# If during a power failure, the UPS has run on batteries for TIMEOUT
# many seconds or longer, apcupsd will initiate a system shutdown.
# A value of 0 disables this timer.
#
#  Note, if you have a Smart UPS, you will most likely want to disable
#    this timer by setting it to zero. That way, you UPS will continue
#    on batteries until either the % charge remaing drops to or below BATTERYLEVEL,
#    or the remaining battery runtime drops to or below MINUTES.  Of course,
#    if you are testing, setting this to 60 causes a quick system shutdown
#    if you pull the power plug.   
#  If you have an older dumb UPS, you will want to set this to less than
#    the time you know you can run on batteries.
TIMEOUT 0

#  Time in seconds between annoying users to signoff prior to
#  system shutdown. 0 disables.
ANNOY 300

# Initial delay after power failure before warning users to get
# off the system.
ANNOYDELAY 60

# The condition which determines when users are prevented from
# logging in during a power failure.
# NOLOGON <string> [ disable | timeout | percent | minutes | always ]
NOLOGON disable

# If KILLDELAY is non-zero, apcupsd will continue running after a
# shutdown has been requested, and after the specified time in
# seconds attempt to kill the power. This is for use on systems
# where apcupsd cannot regain control after a shutdown.
# KILLDELAY <seconds>  0 disables
KILLDELAY 0

#
# ==== Configuration statements for Network Information Server ====
#

# NETSERVER [ on | off ] on enables, off disables the network
#  information server. If netstatus is on, a network information
#  server process will be started for serving the STATUS and
#  EVENT data over the network (used by CGI programs).
NETSERVER on

# NISIP <dotted notation ip address>
#  IP address on which NIS server will listen for incoming connections.
#  This is useful if your server is multi-homed (has more than one
#  network interface and IP address). Default value is 0.0.0.0 which
#  means any incoming request will be serviced. Alternatively, you can
#  configure this setting to any specific IP address of your server and 
#  NIS will listen for connections only on that interface. Use the
#  loopback address (127.0.0.1) to accept connections only from the
#  local machine.
NISIP 127.0.0.1

# NISPORT <port> default is 3551 as registered with the IANA
#  port to use for sending STATUS and EVENTS data over the network.
#  It is not used unless NETSERVER is on. If you change this port,
#  you will need to change the corresponding value in the cgi directory
#  and rebuild the cgi programs.
NISPORT 3551

# If you want the last few EVENTS to be available over the network
# by the network information server, you must define an EVENTSFILE.
EVENTSFILE /var/log/apcupsd.events

# EVENTSFILEMAX <kilobytes>
#  By default, the size of the EVENTSFILE will be not be allowed to exceed
#  10 kilobytes.  When the file grows beyond this limit, older EVENTS will
#  be removed from the beginning of the file (first in first out).  The
#  parameter EVENTSFILEMAX can be set to a different kilobyte value, or set
#  to zero to allow the EVENTSFILE to grow without limit.
EVENTSFILEMAX 10

#
# ========== Configuration statements used if sharing =============
#            a UPS with more than one machine

#
# Remaining items are for ShareUPS (APC expansion card) ONLY
#

# UPSCLASS [ standalone | shareslave | sharemaster ]
#   Normally standalone unless you share an UPS using an APC ShareUPS
#   card.
UPSCLASS standalone

# UPSMODE [ disable | share ]
#   Normally disable unless you share an UPS using an APC ShareUPS card.
UPSMODE disable

#
# ===== Configuration statements to control apcupsd system logging ========
#

# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 0

# Location of STATUS file (written to only if STATTIME is non-zero)
STATFILE /var/log/apcupsd.status

# LOGSTATS [ on | off ] on enables, off disables
# Note! This generates a lot of output, so if         
#       you turn this on, be sure that the
#       file defined in syslog.conf for LOG_NOTICE is a named pipe.
#  You probably do not want this on.
LOGSTATS off

# Time interval in seconds between writing the DATA records to
#   the log file. 0 disables.
DATATIME 0

# FACILITY defines the logging facility (class) for logging to syslog. 
#          If not specified, it defaults to "daemon". This is useful 
#          if you want to separate the data logged by apcupsd from other
#          programs.
#FACILITY DAEMON

#
# ========== Configuration statements used in updating the UPS EPROM =========
#

#
# These statements are used only by apctest when choosing "Set EEPROM with conf
# file values" from the EEPROM menu. THESE STATEMENTS HAVE NO EFFECT ON APCUPSD.
#

# UPS name, max 8 characters 
#UPSNAME UPS_IDEN

# Battery date - 8 characters
#BATTDATE mm/dd/yy

# Sensitivity to line voltage quality (H cause faster transfer to batteries)  
# SENSITIVITY H M L        (default = H)
#SENSITIVITY H

# UPS delay after power return (seconds)
# WAKEUP 000 060 180 300   (default = 0)
#WAKEUP 60

# UPS Grace period after request to power off (seconds)
# SLEEP 020 180 300 600    (default = 20)
#SLEEP 180

# Low line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 106 103 100 097
#    M 177 172 168 182
#    A 092 090 088 086
#    I 208 204 200 196     (default = 0 => not valid)
#LOTRANSFER  208

# High line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 127 130 133 136
#    M 229 234 239 224
#    A 108 110 112 114
#    I 253 257 261 265     (default = 0 => not valid)
#HITRANSFER 253

# Battery charge needed to restore power
# RETURNCHARGE 00 15 50 90 (default = 15)
#RETURNCHARGE 15

# Alarm delay 
# 0 = zero delay after pwr fail, T = power fail + 30 sec, L = low battery, N = never
# BEEPSTATE 0 T L N        (default = 0)
#BEEPSTATE T

# Low battery warning delay in minutes
# LOWBATT 02 05 07 10      (default = 02)
#LOWBATT 2

# UPS Output voltage when running on batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 115
#    M 208
#    A 100
#    I 230 240 220 225     (default = 0 => not valid)
#OUTPUTVOLTS 230

# Self test interval in hours 336=2 weeks, 168=1 week, ON=at power on
# SELFTEST 336 168 ON OFF  (default = 336)
#SELFTEST 336
```


your vmboot 
for others
once you put it in init.d don't forget to chmod +x vmboot

in my case using user administrator
so chance his script accordingly
```
#!/bin/bash

### BEGIN INIT INFO
# Provides:       vmboot
# Required-Start: vboxdrv $local_fs
# Required-Stop:  vboxdrv $local_fs
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Stop/Start VMs before/after System shutdown
### END INIT INFO

# Updated 12/05/2011

# Add this script to /etc/init.d/
# Run "update-rc.d vmboot defaults 99 01" as root

# Written to work with VirtualBox 4.x
# This script will save the state of any running virtual machines.

# User who is running the VMs (Change this!)
[COLOR="Red"]VBOXUSER=administrator
[/COLOR]
# Environmental Variables (Do Not Modify!)
SU="sudo -H -u $VBOXUSER"
VBOXMANAGE="/usr/bin/VBoxManage --nologo"
# Get UUID of All Running VMs
# UUID looks like this: a02b5b54-a84d-48fa-8dac-2a3fad55717e
RUNNINGVMS=$($SU $VBOXMANAGE list runningvms | sed -e 's/^".*".*{\(.*\)}/\1/')
# Get UUID of All VMs
ALLVMS=$($SU $VBOXMANAGE list vms | sed -e 's/^".*".*{\(.*\)}/\1/')

# Functions
function getVMName()
{ echo $($SU $VBOXMANAGE list vms | grep "$1" | awk -F\" '{print $(NF -1)}'); }

# Check to ensure $ALLVMS is not null and exit if it is.
if [[ $ALLVMS = "" ]]; then
        echo "No VMs are detected on this host! Did you configure the VBOXUSER variable?"; exit
fi

case $1 in
stop)
if [[ -n $RUNNINGVMS ]]; then
        for v in $RUNNINGVMS; do
        echo -e "Saving state of \"$(getVMName $v)\"..." && $SU $VBOXMANAGE controlvm $v savestate
        done; else
        echo "No running VMs to save!"
fi
;;
start)
for v in $ALLVMS; do
        if [[ -n $($SU $VBOXMANAGE showvminfo $v | grep saved) ]]; then
                echo -e "Waiting for VM \"$(getVMName $v)\" to power on..." && $SU $VBOXMANAGE startvm $v --type headless 1> /dev/null; else
                echo "No Saved VMs to start!"; exit 0

        fi
# If the previous loop has an error, the loops exits and returns an error.
        if [[ $? -ne 0 ]]; then
                echo "There was an error starting $(getVMName $v)! Try starting it manually to see what the problem is."; break; else
		echo "VM \"$(getVMName $v)\" started successfully!"
        fi
done
;;
status)
if [[ -n $RUNNINGVMS ]]; then
        echo "List of Running VMs:" && $SU $VBOXMANAGE list runningvms; else
                echo "No VMs Currently Running!"
fi
;;
*)
echo "Usage: /etc/init.d/vmboot start | stop | status"; exit 1
;;
esac
exit 0
# eof
```

and then
```
update-rc.d vmboot defaults 99 01

```

ty again (>

---

### Post by CharlesA on 2012-03-26
Awesome. Glad you got it working.

Don't forget to mark the thread as solved from thread tools. ;)

---

