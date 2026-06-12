---
title: "Limit time usage for my kids"
date: 2009-10-01
forum: Security
---

### Post by giambolo on 2009-10-01
Hi there. I'm a father with two kids who use their PC at home. Too often, in my opinion. Can someone give suggestions on how to limit the time that a user can be connected. I'd like to be able to say something like "This week, you're allowed no more than xx hours of use". Just limiting the access time, say Lu-Su 16:00-17:30 has drawbacks. I think that a solution which could allow for issuing a voucher for some time, would permit to use more hours in a day, if needed.

Well, hope you've understood the needing.

Thanks

---

### Post by bruno9779 on 2009-10-01
I have been googling for quite a while before stumbling on this:

[http://www.91courtstreet.net/wordpress/2008/02/03/how-to-limit-daily-desktop-usage-in-ubuntu/](http://www.91courtstreet.net/wordpress/2008/02/03/how-to-limit-daily-desktop-usage-in-ubuntu/)

I haven't tried it, my kid is still only 6 months old, so feedback if it works, so i will save the tutorial for future reference....

PS: also timeoutd in repos

---

### Post by giambolo on 2009-10-01
Thanks Bruno. HAd a look at the url you gave. I'll be trying it soon and report here my considerations. Thanks again.

---

### Post by ghostborg on 2009-10-01
I believe most routers have this feature but I think that would require fixed IP addresses.:](*,)

---

### Post by xpod on 2009-10-01
> **giambolo said:**
> Hi there. I'm a father with two kids who use their PC at home. Too often, in my opinion. Can someone give suggestions on how to limit the time that a user can be connected. I'd like to be able to say something like "This week, you're allowed no more than xx hours of use". Just limiting the access time, say Lu-Su 16:00-17:30 has drawbacks. I think that a solution which could allow for issuing a voucher for some time, would permit to use more hours in a day, if needed.

Well, hope you've understood the needing.

Thanks

I just go with the "if you abuse it then you shall loose it" philosophy.It works a treat.It must do anyway as i`ve never had to "take" anyones Internet away in the three and a half years we`ve had the computers & Internet connections.Our youngest 2 share a laptop in the main sitting room but the other three all have their own machines.I filter the muck i dont want our young girls seeing with OpenDNS but apart from that i dont use any restrictions now-a-days, certainly not time based ones.I dont really need to to be perfectly honest as i`m probably the only one here that needs his Internet time controlled in any way. :-\"
I`ve had to have words about the amount of time being spent on MSN & Facebook with certain parties in the past but as long as the computers/Internet are being used for the educational as well as the recreational then theres really no need for me to intervene i feel.
I had a few preconceived ideas about the Internet prior to ever using it and as a consequence i spent my first year or two using computers trying more blocking, filtering & restriction methods than i care to even remember.The reality is that education & trust have been far better weapons.The only thing i really do now is monitor.

---

### Post by jluber on 2009-10-01
I was faced with the same problem with my 3 younger children.  My solution was/is the following script which I placed in the.kde/Autostart directory in their home directories.  It allows them each 60 minutes per day and provides warnings to logoff before time expires.  The 60 minutes can be overridden by placing a different number of minutes in a textfile called myMax within the .kde directory.

				

#!/bin/bash
today=`date +"%F"`
me=`whoami`

#
#  Read user's maximum time limit
#

if test -a ~/.kde/myMax
then
  my_max=`cat ~/.kde/myMax`
else
  my_max=60
fi
#echo $my_max

#
#  Read how much time is left for the user today
#

if test -a ~/.kde/$today
then
  time_left=`cat ~/.kde/$today`
else
  echo $my_max > ~/.kde/$today
  time_left=60
fi
#echo $time_left

#
# Check if the user's time has been suspended
#

if [ $my_max -eq 0 ]
then
  kdialog --title "TIME SUSPENDED" --passivepopup "Your computer privileges are suspended!!!" 10

  #
  #  TIME SUSPENDED; FORCE THEM OFF
  #

  # Uncomment for testing
  #kdialog --title "THIS IS A TEST" --error "You will be automatically logged off!" &
  # Uncomment for KDE3
  #dcop ksmserver ksmserver logout 0 0 0
  # Uncomment for KDE4
  dbus-send --session --dest=org.kde.ksmserver --type=method_call --print-reply /KSMServer org.kde.KSMServerInterface.logout int32:0 int32:0 int32:0
  echo "timelimit.sh: User time was suspended; code: 3" > ~/.kde/$today.err
  exit 3
fi


#
# Check if the user's time limit has been reached
#

if [ $time_left -le 0 ]  
then
  kdialog --title "TIME LIMIT EXCEEDED" --passivepopup "You've already used your minutes today!!!" 10
  
  #
  #  TIME IS EXPIRED; FORCE THEM OFF
  #

  # Uncomment for testing
  #kdialog --title "THIS IS A TEST" --error "You will be automatically logged off!" &
  # Uncomment for KDE3
  #dcop ksmserver ksmserver logout 0 0 0
  # Uncomment for KDE4
  dbus-send --session --dest=org.kde.ksmserver --type=method_call --print-reply /KSMServer org.kde.KSMServerInterface.logout int32:0 int32:0 int32:0
  echo "timelimit.sh: User was forced off; code: 1" > ~/.kde/$today.err
  exit 1
fi

# 
#  TIME IS NOT EXPIRED; LET THEM PLAY
#

kdialog --title "Welcome" --passivepopup "You have $time_left minutes left today."  10

while test $time_left -gt 0
do
  who | grep $me
  if test $? -ne 0
  then
    echo "timelimit.sh: User has logged off; code: 2" > ~/.kde/$today.err
    exit 2
  fi
  echo "sleep 1"
  #sleep 1
  sleep 60
  time_left=`expr $time_left - 1`
  echo $time_left > ~/.kde/$today
  #echo $time_left
done

#
#  FIRST WARNING; TIME TO LOGOFF
#

kdialog --title "WARNING:  TIME EXPIRED!!!" --passivepopup "You have 2 minutes to log off" 10
sleep 60

#
#  SECOND WARNING; NOW WE'RE SERIOUS
#

kdialog --title "WARNING:  TIME EXPIRED!!!" --passivepopup "Time to log off; You have just 1 minute left to log off" 10
sleep 60

#
#  OK; PUSH THEM OFF AND SET time_left to 0
#

echo "timelimit.sh: User was forced off; code: 1" > ~/.kde/$today.err
echo 0 > ~/.kde/$today
# Uncomment for testing
#kdialog --title "THIS IS A TEST" --error "You will be automatically logged off!" &
# Uncomment for KDE3
#dcop ksmserver ksmserver logout 0 0 0
# Uncomment for KDE4
dbus-send --session --dest=org.kde.ksmserver --type=method_call --print-reply /KSMServer org.kde.KSMServerInterface.logout int32:0 int32:0 int32:0
exit 1

---

### Post by juliaallen on 2010-07-30
I've  copied this script and I'm looking for that directory to put it into, but I can't find .kde/Autostart directory in their home directories. I can't find it anywhere. Am I supposed to create it? When you say their home directories, do you mean the one with their name? I have three kids, and they fight over computer time, so I need something to do this. My son misled me into believing Ubuntu would do this automatically, but I don't see any features to do this, and I'm about ready to uninstall it  and go with Windows 7 like I'd originally planned.

---

### Post by fargle on 2010-07-30
This appears to be a script for KUbuntu, you're likely using standard Ubuntu.

You'd need to modify this to autostart under Gnome (in the startup applications preferences panel perhaps?), store things in another hidden directory, and use "/usr/bin/gnome-session-save --kill" to do the logout, I think.

---

### Post by kerry_s on 2010-07-30
[http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)

---

### Post by shane2peru on 2011-04-08
This is a bit old, but still a relevant thread.  There was a nice package being developed for a while timekpr which worked perfectly and was easy to setup and use.  I too am looking for a new replacement for this as it is no longer being developed.

Shane

PS  I like the script posted here, and think it would be easy to modify for gnome.

---

### Post by ollelille on 2011-04-10
I found the script from jluber quite ok. I gave it a try on my xubuntu 10.04. My kids (3 and 5) use gnome. So this is my gnome-tweak:

```

#!/bin/sh
today=`date +"%F"`
me=`whoami`

#
# Read user's maximum time limit
#

if test -r ~/.config/myMax
then
my_max=`cat ~/.config/myMax`
else
my_max=30
fi
#echo $my_max

#
# Read how much time is left for the user today
#

if test -e ~/.config/$today
then
time_left=`cat ~/.config/$today`
else
echo $my_max > ~/.config/$today
time_left=30
fi
#echo $time_left

#
# Check if the user's time has been suspended
# 

if [ $my_max -eq 0 ]
then
# No time admitted (myMax) - signal  logout
zenity --warning --title "**** TID" --text "Du loggas ut!!!" --timeout=10

#
# TIME SUSPENDED; FORCE THEM OFF
#

gnome-session-save --force-logout
echo "timelimit.sh: User time was suspended; code: 3" > ~/.config/$today.err
exit 3
fi


#
# Check if the user's time limit has been reached
#

if [ $time_left -le 0 ]
then
# Time is out - signal logout
zenity --warning --title "TID ****" --text "Din skärmtid är ****!!!" --timeout=10

#
# TIME IS EXPIRED; FORCE THEM OFF
#

gnome-session-save --force-logout
echo "timelimit.sh: User was forced off; code: 1" > ~/.config/$today.err
exit 1
fi

#
# TIME IS NOT EXPIRED; LET THEM PLAY
#

# Welcome user - display remaining time
zenity --info --title "Välkommen" --text "Du har $time_left minuter kvar." --timeout=10

while test $time_left -gt 0
do
who | grep $me
if test $? -ne 0
then
echo "timelimit.sh: User has logged off; code: 2" > ~/.config/$today.err
exit 2
fi
echo "sleep 1"
#sleep 1
sleep 60
time_left=`expr $time_left - 1`
echo $time_left > ~/.config/$today
#echo $time_left
done

#
# FIRST WARNING; TIME TO LOGOFF
#
# Two min to logout

zenity --warning --title "VARNING: TID ****!!!" --text "Du har 2 minuter att logga ut" --timeout=10
sleep 60

#
# SECOND WARNING; NOW WE'RE SERIOUS
#
# One min to logout
zenity --warning --title "VARNING: TID ****!!!" --text "Dax att sluta; 1 till avstängning" --timeout10
sleep 60

#
# OK; PUSH THEM OFF AND SET time_left to 0
#

echo "timelimit.sh: User was forced off; code: 1" > ~/.config/$today.err
echo 0 > ~/.config/$today
gnome-session-save --force-logout
exit 1

```

I am not a good dash script programmer so it might not be the most optimal adjustments.


Autostart in Gnome:
In ~/.config/autostart/
I have a file named time_control.sh.desktop 
I guess the name is unimportant.
I contains:
```

[Desktop Entry]
Type=Application
Exec=/bin/sh -c ~/.config/autostart/time_control.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[sv_SE]=timer
Name=timer
Comment[sv_SE]=skarmtid
Comment=skarmtid

```

That file is generated automatically if you use System -> Preferences -> Sessions -> Startup Programs -> Add

---

