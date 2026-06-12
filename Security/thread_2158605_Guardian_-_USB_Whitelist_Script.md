---
title: "Guardian - USB Whitelist Script"
date: 2013-06-29
forum: Security
---

### Post by KaosuX on 2013-06-29
[SIZE=4]**Introduction**[/SIZE]
Guardian is a simple script that will contionuously run in the background and notify you of any USB device that is inserted into the machine that is not specified in a whitelist. I initially created this script to detect the presence of specific hardware keyloggers, but it is very useful in different environments for varying purposes. The basic idea is that you maintain a simple list of devices that you trust and those will run nomrally without anything new happening. However, when a device is connected that is not specified in the whitelist you will be notified of the event and it will also be logged to a file in your home directory. When the unauthorized device is unplugged from the system the notifications will stop and everything will resume normally. It is up to the end-user to investigate the notifications to determine if a malicious device was connected or not during the notifications.

The whitelist itself is really simple to maintain. You can add or remove trusted devices at any time by simply modifying the file it uses to store the trusted device ID's. When Guardian is ran for the first time it will automatically generate a new whitelist and trust all connected USB devices which will from then on be your baseline. It is highly recommended to attach all of your devices before you execute Guardian for the first time. As the number of devices you own increase or decrease you will need to modify your whitelist as needed. 

Be aware this is just an informational tool and its effectiveness it up to how each user utilizes it for their specific purposes. This is aimed at users that want to keep a close eye on their systems. Don't treat this as some sort of "scanner" or anything of that nature, because it won't be very effective in that capacity. If anything, I think of Guardian as a lightweight version of Tripwire aimed at specific system resources.

As time goes on I will add support for other resources than just USB devices, which will enable users to create a baseline for all owned peripherals and be notified when anything else is plugged into the machine. This would make identifying malicious hardware devices much easier.

This is not a perfect solution by any means and Guardian won't be particular useful in some environments. However, I feel that it is a good beginning for a useful tool that has a lot of room for improvement.

Right now Guardian uses XFCE4-NOTIFYD to list primary notifications to the user, but it also stores a log file in your home directory as well. If you don't use XFCE4-NOTIFYD or simply need less dependencies, remove the notify-send command(s) and replace them with whatever notification code you wish (SYSLOG, etc.). I made this a simple process with comments in the code.

Guardian was written for and tested on Debian Current-Stable (Wheezy), but should be pretty universal across any distribution aside from the XFCE4-NOTIFYD depenency that is easily removed anyway.

_TODO_:

[LIST]
[*]Add support for email notification. Useful when you want to recieve real-time updates while you're away or for monitoring employees/students in a work/school environment. 
[*]Support for remote logging and for accessing/storing a whitelist stored on a remote server for added security. 
[*]Code optimizations in general 
[*]Ability to allow the administrator to execute specific responses to notification events, such as but not limited to: Ejecting the device, copying contents of the device to a remote location, et cetera. 
[*]Add support for different types of system resources. 
[/LIST]

[SIZE=4]**Recommendations**[/SIZE]
Make sure you store your whitelist in a safe directory with appropriate file permissions. For a home user this would mean storing the whitelist in your home directory with read-only permissions after the list is initially created. An administrator would be better off creating a new user account for Guardian to run as on the system, this would allow you to monitor and enforce peripheral policies on company owned workstations without allowing individual users access to the whitelist so they are forced to comply with whatever standard you wish to enforce upon them.

If you store the whitelist in a location where anyone else has access to it then you are better off not using it. Also, this monitoring tool would be easily defeated by malware that has access to your home directory. I can't say what the best method of storing the whitelist is for everyone's specific purposes, so a little common sense and practical administration knowledge will go a long way here. The two methods suggested above are simply the easiest to implement, but definately not the most secure. 

[SIZE=4]**Code**[/SIZE]

Guardian.sh
*[Note: The code tag used on these forums hates my formatting, so ignore any weird styling. The code was recently tested and works.*]
```
#!/bin/bash
###################################
#     Guardian [Version 0.99]     #
###################################
# Author: Kaosu                   #
#                                 #
# Guardian will notify you of USB #
# devices that are not specified  #
# in your whitelist. This may aid #
# with detecting hostile devices. #
#                                 #
# I currently use xfce4-notifyd   #
# to notify the user. Replace the #
# notify-send command(s) if you   #
# are not using XFCE4 or would    #
# like less dependencies.         #
#                                 #
# The first time Guardian is ran  #
# it will generate your whitelist #
# so make sure you connect all of #
# your trusted devices the first  #
# time you execute the script.    #
#                                 #
# You can also add a device to    #
# to your whitelist at any time   #
# by adding its device ID into    #
# safe.cfg. To get the device ID  #
# of your device use lsusb.       #
###################################

#[Configuration]
TMPLIST="/tmp/idlist.cfg" # Temporary list of connected device ID's.
SAFELIST="/home/kaosu/safe.cfg" # Your whitelist. Keep in a private directory.
SECONDS="1" #Define how many seconds the script should wait to execute again.
#[ERROR HANDLING]
# If safe.cfg does not exist then Guardian will generate a new whitelist
# for you. Keep in mind that any connected device will automatically be
# added to this list of trusted devices, so verify only devices you trust
# are connected the first time you run Guardian.
#
# For security purposes ensure safe.cfg is in your home directory and you
# are the only person with access to modify its contents.
if [ ! -f $SAFELIST ]; then
   lsusb >> $SAFELIST
fi

while :; do
#[Main]
lsusb >> $TMPLIST

RES=`grep -F -v -f $SAFELIST $TMPLIST` #Compare connected ID's to safe.cfg

if [ -n "$RES" ]; then #If grep returns text on STDIN then a new device was located
    ID=`lsusb | grep "$RES"` #Identify unauthorized USB ID's
    #[BEGIN DELETE HERE IF YOU WISH TO REMOVE XFCE4-NOTIFYD DEPENDENCIES]
    notify-send --app-name=Guardian --icon=error --category=Security \
    "The following unauthorized USB device(s) have been detected:" "$ID"
    #[END DELETE HERE IF YOU WISH TO REMOVE XFCE4-NOTIFYD DEPENDENCIES]
    echo "ERROR: Guardian detected the following unauthorized USB device(s):" >> ~/guardian.log
    echo "$ID" >> ~/guardian.log
fi

#[Remove temporary files]
if [ -f $TMPLIST ]; then
      rm -f $TMPLIST
fi
sleep $SECONDS
done

```

[SIZE=4]**Feedback**[/SIZE]
Constructive critisism and general feedback is more than welcome as long as it is mature and civil. I am limiting all feedback to this thread, so reply here and please don't PM me.

[SIZE=4]**Edits**[/SIZE]
Changed a lot of the script. It now verifies the entire state of lsusb constantly, quickly identifying unauthorized devices and inspecting them completely. Now two identical devices are correctly separated instead of blindly being ignored due to matching ID's. I also simplified the NOTIFYD messages so they would automatically maintain themselves to make things easier on myself. Simple is good and everything works much better for me now. Let me know if there are any major problems, I have not been using the modification for too long.

---

### Post by Azdour on 2013-07-01
Hi,

Did you ever look at using a udev rule rather than running always in a loop?  Just interested to see what you thought of udev.

---

### Post by KaosuX on 2013-07-01
> **Azdour said:**
> Hi,  Did you ever look at using a udev rule rather than running always in a loop?  Just interested to see what you thought of udev.

  I have recently started this project from scratch because I was unhappy with several aspects of the script and felt it was lacking. The newest version I am working on uses udev, which provides me with several advantages in terms of performance, expansion of future feature-set, and the ability to effectively harden this tool against more than 10  different evasion techniques that allowed me to attach my hardware keyloggers without setting off an alarm. The tool is now far more efficient, reliable and has some interesting new features for administrators.

  When I feel like the script is stable then I will begin porting the project to Python. The script was always just my prototype to get a quick-and-dirty concept going that I could build upon. There is also a native Windows version written in C, but the Windows version won't be maintained that well since I rarely use it.  Feel free to ask me anything else, and I look forward to sharing the new version with everyone.

---

