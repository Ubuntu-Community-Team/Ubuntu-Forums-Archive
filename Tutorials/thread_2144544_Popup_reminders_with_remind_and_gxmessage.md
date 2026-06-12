---
title: "Popup reminders with remind and gxmessage"
date: 2013-05-12
forum: Tutorials
---

### Post by GrouchyGaijin on 2013-05-12
Pop-up Reminders: The Fun Way 
Programs needed: remind, gxmessage


I am a bit obsessive about remembering when things are going to happen or more precisely, about remembering when I have to do something.

I also love to tinker with my computer.

What could be better for a guy like me than remind.  Remind is an ultra geeky calendar, reminder program that is probably on your system or in the repository if it is not.

Remind is a sophisticated calendar and alarm program. It includes the following features:

[LIST]
[*]A sophisticated scripting language and intelligent handling of exceptions and holidays.
[/LIST]

[LIST]
[*]Plain-text, PostScript and HTML output.
[/LIST]

[LIST]
[*]Timed reminders and pop-up alarms.
[/LIST]

[LIST]
[*]A friendly graphical front-end for people who don't want to learn the scripting language.
[/LIST]

[LIST]
[*]Facilities for both the Gregorian and Hebrew calendars.
[/LIST]

[LIST]
[*]Support for 12 different languages.
[/LIST]


This How-To deals with just a couple of these features.
I use remind in two ways:
1. For general reminders I want to see when I start the computer as well as from time to time throughout the day.
2. Things I want to be reminded of at a particular time. (To pick the kids up from school &#8211; leave NOW)


All of remind's commands are kept in aptly named reminder files, which are plain-text files.  The default is ~/.reminders  I chose to keep mine in ~/Reminder-files/
I have three files:
1. reminders-general for things I want to see when I start the computer and from time to time over the course of the day.
2. timedreminders &#8211; for things like remembering to leave at a specific time to pick up my kids.
3. remindersholidays &#8211; a list of holidays, so that I receive an alert in the week leading up to Ground Hog day 


The Anatomy of a Reminder:
Reminders are written with a special syntax.  You can learn more than you ever want to know about this syntax at [http://www.roaringpenguin.com/products/remind](http://www.roaringpenguin.com/products/remind).  They also have a mailing list for Remind-Fans.  Below is an example of a reminder I have in my reminders-general file:

At the top of the reminders file I have:
INCLUDE /home/grouchygaijin/Reminder-files/remindershollidays - this tells remind to include my list of holidays

INCLUDE /home/grouchygaijin/.ical2rem - this is a script that pulls Google calendar events and converts them into remind format

FSET _days(x) iif(x>1, x + " days", x==1, "1 day", "") 
FSET _hrs(x)  iif(x>1, x + " hours", x==1, "1 hour", "") 
FSET _mins(x) iif(x>1, x + " minutes", x==1, "1 minute", "") 
FSET _smush(x, y) iif(x != "" && y != "", x + " and " + y, x + y) 
FSET _countdown(x) _smush(_smush(_days(x/1440), _hrs((x - 1440*(x/1440))/60)), _mins(x%60))  - I don't know exactly what this does, but without it, things don't work very well.


REM 11 April 2013 +30 AT 08:00 MSG Teknik Dalarna %b (in [_countdown(trigdatetime()-current())])
The most important things here are:
1. REM &#8211; this tells remind that what comes next is for you.
2. 11 April 2013 &#8211; or any date you want to be reminded of
3. +30 &#8211; How many days in advance you want to be reminded.  30 days in this case
4. AT followed by the time the reminder should remind you
5. MSG followed by the message you want to see when you are reminded.
6. End with a % or if you want to know how much time is left before an event end with 
%b (in [_countdown(trigdatetime()-current())])
Timed reminders look similar:


REM 26 Sept 2011 AT 11:59 MSG Pizza! - in this case on September 26 at 11:59 AM I wanted to be reminded that I should take the pizza out of the oven.  I don't end with a percent because I don't care about having anything appear after the message text.  This is a reminder to tell me to do something right when it pops up.

The Pop-Up

To get these reminders to pop-up I have a script that runs at startup and another that I run via a cron job.  The start up script is called startRemind and basically it tells remind to start in demon mode and what to do with timed reminders, when their time comes.

```
StartRemind:
#!/bin/bash 
remind -z /home/grouchygaijin/Reminder-files/remindersgeneral & 
remind -z '-kgmessage -buttons "OK:1" -default "OK" -center -font "serif 16" -fg "#46f" -bg white -wrap -title "Hey!" %s &' ~/Reminder-files/timedreminders 
```

The remind -z starts the demon followed by the path to the reminder file.
The second part of the script is for the timed reminders. The '-kgmessage -buttons "OK:1" -default "OK" -center -font "serif 16" -fg "#46f" -bg white -wrap -title "Hey!" %s &' defines the pop-up box that will appear when the time is right and /home/grouchygaijin/Reminder-files/timedreminders is the path to the file containing the timed reminders.

Adding Reminders:

Now, you could simply open the appropriate file each time you want to add a reminder, but that gets to be a hassle.  I  threw together a couple of scripts that make the task a bit easier:


This script asks me a series of questions then takes that information and adds it to my file for general reminders.
```

#!/bin/bash
read -p "What is the trigger date of the reminder?:" triggerdate
read -p "Hpw many days in advance should this appear?" daysadvance
read -p "What is the trigger time of the reminder?:" triggertime
read -p "What will the reminder say?:" message


echo "REM $triggerdate +$daysadvance AT $triggertime MSG $message %b (in [_countdown(trigdatetime()-current())])" >> ~/Reminder-files/reminders-general 
```


This script does the same thing, but for timed reminders.
```

#!/bin/bash


read -p "What is the trigger date of the reminder?:" triggerdate
read -p "What is the trigger time of the reminder?:" triggertime
read -p "What will the reminder say?:" message

echo "REM $triggerdate AT $triggertime MSG $message" >> ~/Reminder-files/timedreminders

```

In order to be reminded of my general reminders throughout the day I run this as a cron job every 3 hours:
```

#!/bin/bash
remind -q /home/grouchygaijin/Reminder-files/reminders-general | gxmessage -buttons "Close:1" -default "Close" -center -font "serif 16" -fg "#46f" -bg white -wrap -title "Remember" -file -

```

---

