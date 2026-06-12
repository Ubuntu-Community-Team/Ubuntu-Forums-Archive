---
title: "What neat and helpful script do you use?"
date: 2011-09-23
forum: The Cafe
---

### Post by Dragonbite on 2011-09-23
Ubuntu has elevated the Linux desktop to being able to accomplish everything without requiring the command line.  Sometimes, though, the power of scripts just cannot be denied, and can be better than a GUI solution (speed, automated, portable, no-compile)

What useful scripts do you use?  What does it do, and if you don't mind sharing can you post the script?

It doesn't matter if it is in Python, shell, xml or modified config files so long as it does something you want/need.

Or do you need a script?  Make the request and maybe somebody here can whip something up!

For example, I would love to find scripts that...[LIST=1]
[*]automatically saves the packages installed so when I do a clean install upgrade I can run this script and have apt-get/synaptic/whatever isntall all of the programs (and ppa:'s?) that I am using now.
[*]a script to copy modified config files to a location off my home directory (/home/.backups) so when I do an upgrade I can replace these modified (apache, samba, etc.) files easily
[*]a script to automatically create certain users and passwords so I don't have to add them individually again
[*]a script to change everybody's Firefox home page to whatever I specify
[*]a script to set LibreOffice and/or OpenOffice to automatically save in MS Office format (.doc, .xls, .ppt)
[/LIST]

That's just a start.  I am thinking of more but I am hoping that if I can see how to do some of these, it will help me in starting to create my own.

---

### Post by Dragonbite on 2011-09-23
This is what I use to make my webcam work proerly. It is a [[COLOR="Blue"]Microsoft LifeCam NX-6000[/COLOR]]("http://www.amazon.com/Microsoft-94N-00001-LifeCam-NX-6000-Webcam/dp/B000GOUE7Y/ref=sr_1_1?ie=UTF8&s=electronics&qid=1263564640&sr=8-1") and is very hit-or-miss whether it will work or not.  Sometimes it will work in one program (usually Cheese) and not another (like Skype).

So I use the following code to get it to work when it doesn't work on its own, and usually edit the menu item to run it this way so I don't have to manually type it each time.

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese  #to run cheese webcam booth
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype   #to run Skype
```

---

### Post by dave01945 on 2011-09-23
i have a script that i use to disconnect and reconnect a mobile broadband dongle connected to my media server that shares the connection through my router (until the adsl gets connected) i have also created a desktop launcher for the script which isn't using the terminal but does make it alot easier


also another one i didn't make but have found very useful is [sakis3g](www.sakis3g.org) it is used for connecting mobile broadband and has always worked when nothing else will it has everything you need to get connected

any way here is the one i made for connecting and reconnecting on the media server


```
#!/bin/bash
#
set -e
trap "failed" 1 2 3 15 ERR
#
# script to kill wvdial on server
#
#kill wvdial

killwv(){
if zenity --title\="Stop Internet" --question --text\="Do you want to stop WVDial"; then
	(echo "#Now Disconnecting"
	ssh server sudo sakis3gz disconnect &> /dev/null)|
	zenity --progress --title\="Stop Internet" --pulsate --no-cancel --auto-close
	if [ ${PIPESTATUS} = 0 ]; then
		notify-send -i notification-gsm-disconnected "Stop Internet" "WVDial disconnected"
	else
		notify-send -i notification-gsm-disconnected "Stop Internet" "WVDial disconnect failed"
	fi
else
	notify-send -i notification-gsm-disconnected "Stop Internet" "Not disconnecting"
fi
}

# check server is reachable

checknet(){

if ping -w 2 -c 1 192.168.1.254 &> /dev/null; then
	checkwv
else
	notify-send -i notification-network-ethernet-diconnected "Stop Internet" "Server is unreachable"
	if `zenity --title\="Check Network" --question --text\="Would yo like to retry"`; then
		checknet
	else
		exit 1
	fi
fi
}

# check wvdial is connected

checkwv(){
(echo "#Now checking connection"
ssh server sakis3gz status)|
zenity --progress --title="Stop Internet" --no-cancel --auto-close --pulsate
if [ ${PIPESTATUS} = 0 ]; then
	killwv
else
	reconn
fi
}

# ask if wanted to reconnect

reconn(){

if zenity --title\="Start Internet" --question --text\="WVDial Not Connected\nWoild you like to connect"; then
	(echo "#Now Connecting"
	ssh server sudo sakis3gz connect APN=giffgaff.com &> /dev/null)|
	zenity --progress --title\="Start Internet" --pulsate --no-cancel --auto-close
	if [ ${PIPESTATUS} = 0 ]; then
		notify-send -i notification-gsm-full "Start Internet" "Internet is now connected"
	else
		notify-send -i notification-gsm-full "Start Internet" "Connection Failed"
	fi
else
	notify-send -i notification-gsm-disconnected "Start Internet" "Internet not connecting"
fi

}

failed(){

zenity --error --title="Stop Internet" --text="Something went wrong"

}
# this is where it all starts

checknet
exit
```

i have made several more that do similar things like mount nfs shares and to shutdown the server but i wont post them all it will take up alot of space :)

---

### Post by grayraven on 2011-09-23
If you count BASH aliases, I have a series that are a variation on a theme. Started using them at work but they are now on every Linux box I run. Nothing fancy, but effective.

alias up='cd ..'
alias up2='cd ../..'
alias up3='cd ../../..'
alias up4='cd ../../../..'
alias up5='cd ../../../../..'
alias up6='cd ../../../../../..'

Cheers,

James

---

### Post by CharlesA on 2011-09-23
I've got a few that I use to do backups and one that I use to save/start any VMs that I am running on shutdown/startup.

VM Start/stop script:

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

---

