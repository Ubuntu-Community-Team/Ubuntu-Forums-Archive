---
title: "Weird boot error &quot;Choose 1-16&quot;"
date: 2009-05-23
forum: Server Platforms
---

### Post by Zuhaib on 2009-05-23
Hi, 
I am having a weird Ubuntu Server 9.04 issue, after booting and starting a few services it stops and prompts me with 

"Choose 1-16 [1]"

This is suppose to be a headless system and did not figure this out till i plugged in a monitor today.  Also odd (and very annoying) is i am getting a IO ACPI (or something) error very early on and causes my keyboard to not work.
Any ideas? Google search on this has not help me, at lest what I am typing in..

---

### Post by Zuhaib on 2009-05-24
Follow up to my initial problem...
First let this be a lesson, always test the simple things first =( it seems i had a bad keyboard which is what stopped me from inputting anything.  It just went bad so gah.

Next, the error seems to have been caused by an Vuze starting script =\  Its the script you get from the CLI Wiki and was working before but it seems some system change makes it now prompt the user for what screen to use during boot, which is why it it asking Choose 1-16?
This is the script
```
 #! /bin/sh
 
 #The user that will run Azureus
 AZ_USER=zuhaib
 
 #Name of the screen-session
 NAME=azureus_screen
 
 #executable files in the following paths that are perhaps needed by the script
 PATH=/bin:/usr/bin:/sbin:/usr/sbin:/home/zuhaib/bin
 
 #your path to the azureus directory, where Azureus2.jar is located
 DIR=/var/azureus/
 
 #Description
 DESC="Azureus screen daemon"
 
 case "$1" in
 start)
    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo "Azureus is already running!"
    else
       echo "Starting $DESC: $NAME"
       su $AZ_USER -c "cd $DIR; screen -dmS $NAME java -jar ./Azureus2.jar --ui=console"
    fi
    ;;
 stop)
#    if [ `su $AZ_USER -c "screen -ls |grep $NAME"` ]
    if [ TRUE ]
       then
       echo "Stopping $DESC: $NAME"
       su $AZ_USER -c "screen -XS $NAME quit"
       echo " ... done."
    else
       echo "Coulnd't find a running $DESC"
    fi
    ;;
 restart)
    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
        then
       echo -n "Stopping $DESC: $NAME"
       su $AZ_USER -c "screen -XS $NAME quit"
       echo " ... done."
    else
       echo "Coulnd't find a running $DESC"
    fi
    echo "Starting $DESC: $NAME"
       su $AZ_USER -c "cd $DIR; screen -dmS $NAME java -jar ./Azureus2.jar --ui=console"
    echo " ... done."
    ;;
 status)
    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo "Azureus is RUNNING"
    else
       echo "Azureus is DOWN"
    fi
    ;;
 *)
    echo "Usage: $0 {start|stop|status|restart}"
    exit 1
    ;;
 esac
 
 exit 0

```
I dont see what is causing it now to prompt for what screen to use, anyone have any idea how to solve this? I might need to move this to an Vuze/Software forums.

---

