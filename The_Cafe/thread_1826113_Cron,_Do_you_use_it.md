---
title: "Cron, Do you use it?"
date: 2011-08-16
forum: The Cafe
---

### Post by amiacamal on 2011-08-16
From Wikipedia: "Cron is a time-based job scheduler in Unix-like computer operating systems."

Im curious, who actually uses cron? I'v heard it mentioned in a few threads. If you do use it, what for? How long are you a linux user? 

I know what it does, but i dunno why one would need to use it..

{edit... im probably not supposed to be posting this here.....}

---

### Post by yetiman64 on 2011-08-16
Yes, occasionally.

I have set up a user cron-tab to play wave files every half hour from 6 am in the morning to 10 pm at night. The files were an artificial voice "announcing" the time with customised messages at certain times. 

This is a pretty trivial use of cron, it could be used for a multitude of system operations, running various scripting automatically etc.

It can be a bit experimental getting commands working in it, but when you work out the syntax and timing etc, you will realize just how usefull it is. 

Linux user on and off (occasional testing) for about 8-9 years, fully onto Linux about 4 years (mostly Ubuntu-now getting onto Debian more often).

---

### Post by amiacamal on 2011-08-16
Hmmm, from what I've read I can at least See how you can do what you've achieved. I can see how it's useful, at least. Seems to me its more use for a system admin, with a system that is "supposed" to be always on, than for an everyday user.

---

### Post by yetiman64 on 2011-08-16
Even as an ordinary user any repetitive time based task is easy to set up from a terminal. 

If you aren't online nothing happens, if you are it does, you don't have to be online constantly to use it (just make sure you are if you have set it up for backups :P).

```
crontab -e
``` add in the timing and command/files, save and the user crontab is inserted to the appropriate location.

If a command has to run as root (for admin purposes like you mention) the command to use is,
```
sudo crontab -e
``` this writes an entry for the user "root".

I have in the past looked at cron gui front ends only to get confused no end. Since I've found out about those 2 commands (user and system) from these forums it's been fairly easy to schedule "stuff" to be done.

---

### Post by amiacamal on 2011-08-16
The System one would run as root without needing to wait for a password to be entered?
Ya know I hadn't even considered that... As of yet i have no reason to use cron, but its another utility thats there if i need it :P

---

### Post by yetiman64 on 2011-08-16
> **amiacamal said:**
> The System one would run as root without needing to wait for a password to be entered?
Ya know I hadn't even considered that... As of yet i have no reason to use cron, but its another utility thats there if i need it :P

That's right as it's working on the fact that you enter the sudo password (give it root permissions) when you write the crontab. Use with care where root access is concerned, a mistake in the system crontab can be costly to you -- practice in the user crontab to get a good feel for the commands/syntax/tricks involved to get it to work smoothly first. :)

---

### Post by amiacamal on 2011-08-16
I understand what you mean, about care where root is concerned.

The biggest advantage to me of ubuntu is that i can pretty much break it, and just reinstall and have it back to where it was in a little over an hour :) 

somehow managed to reduce my system to a state where it couldn't log in a few weeks ago, a quick reinstall later and im good to go :)

---

### Post by Ghost|BTFH on 2011-08-16
Cron is a great little tool.  The best thing to contemplate is:

"What kind of script could I use that would benefit me on a regular basis?"

Then contemplate having it run automatically once per event (second, minute, hour, day, week, month, year, etc.) for you...

And that will give you a small idea on how useful cron is.

It's not just for Sysadmins anymore.

---

### Post by amiacamal on 2011-08-16
You've hit the nail on the head there :) I'm terribly uninventive, need a kick in the right direction :) I dont really DO a lot tho, so i dunno what id need to automate. I can see why its useful tho.

[sidenote] iv started another thread, also related to my uninventiveness, a brainstorming session to help me come up with some ideas, any input is appreciated! -->  

[http://ubuntuforums.org/showthread.php?p=11157377#post11157377](http://ubuntuforums.org/showthread.php?p=11157377#post11157377)

---

### Post by RiceMonster on 2011-08-16
I use it on my minecraft server, yes. I have it do a backup and then restart the minecraft daemon ever night. On the server side, there is countless uses for scheduled jobs.

I can't think of a use for it on a desktop, though.


Edit: oh yeah, I first used Linux 4 years ago.

---

### Post by yetiman64 on 2011-08-16
> Ghost|BTFH +1,

Section 4 examples [[COLOR=Blue]--in this link--[/COLOR]]("http://adminschoice.com/crontab-quick-reference") for setting up the timing in cron fascinate me as to how flexibly it can be programmed. Particularly the use of comma separated multiple values in a single field. Very handy and extremely flexible for anyone.

---

### Post by amiacamal on 2011-08-16
Ahh Minecraft :) This does bring me back to what I said (tried to say, really) earlier. It seems much more useful for server side tasks.

---

### Post by amiacamal on 2011-08-16
It really does seem very well built, I almost feel like i should be using it :P

[edit, double post... oops?]

---

### Post by Paqman on 2011-08-16
Regular cron is of more use on a server or a machine that's on 24/7. For a desktop you'll find anacron more practical, since tasks won't get missed simply because the machine was off at the wrong time. 

It's very simple to use, just drop your script into the appropriate folder in /etc/cron.whatever and you're done. No faffing about with crontab and cryptic timings required.

The only thing I really have in mine is some rsync scripts to automate backups.

---

### Post by amiacamal on 2011-08-16
> **Paqman said:**
> For a desktop you'll find anacron more practical

Interesting, ill take a look. Might even encourage me to do some backups :P

---

### Post by amauk on 2011-08-16
cronjobs are obviously extremely useful on servers for automating tasks on a regular basis, but I do use it quite a bit on my desktop as well

On my desktop at the moment are the following cronjobs:
- daily grabbing the latest comic strip from various sites (dilbert, xkcd, cyanide & happiness, etc.)
- monthly check of music archive to flag up any duplicate tracks, obviously wrong metadata, etc.
- hourly check to see if VPN connection is still active, if not restart
- A half-hourly check for a flag-file on a shared storage device, if present pause all bittorrent transfers

---

### Post by amiacamal on 2011-08-16
> **amauk said:**
> 
- daily grabbing the latest comic strip from various sites (dilbert, xkcd, cyanide & happiness, etc.)
- monthly check of music archive to flag up any duplicate tracks, obviously wrong metadata, etc.


What are you doing with these comics? :) this interests me...

And metadata... the bane of a large music collection :P

---

### Post by amauk on 2011-08-16
> **amiacamal said:**
> What are you doing with these comics? :) this interests me...
Reading them
It's just more convenient than manually visiting websites

---

### Post by amiacamal on 2011-08-16
I mean are you saving them to your own machine somehow? or displaying them on the desktop?

---

### Post by Grenage on 2011-08-16
On our work servers, yes; I've got a lot of cron jobs running scripts.  On my linux desktops, none.

---

### Post by amauk on 2011-08-16
> **amiacamal said:**
> I mean are you saving them to your own machine somehow? or displaying them on the desktop?

Grabbing them off the net, saving the images locally (and occasionally twiddling them)

This is the script I use for getting dilbert comics, and because they tend to be a tad small, it uses imagemagick to resize the images to 200%

```
#! /bin/bash

if [ -n "$1" ];
then
	DIL_YEAR=$1
else
	DIL_YEAR=$(date +%Y)
fi

if [ -n "$2" ];
then
        DIL_MONTH=$2
else
        DIL_MONTH=$(date +%m)
fi

if [ -n "$3" ];
then
        DIL_DAY=$3
else
        DIL_DAY=$(date +%d)
fi

if [ ! -f "/media/raid5/tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH/$DIL_YEAR-$DIL_MONTH-$DIL_DAY.gif" ];
then

	HTML=`wget -q -O - "http://www.dilbert.com/fast/$DIL_YEAR-$DIL_MONTH-$DIL_DAY/index.html" | grep '.gif' | sed 's|src=\"\(/[^\"]*strip[^\"]*gif\)\"|\nhttp://www.dilbert.com\1\n|g' | grep 'http://www.dilbert.com'`

	if [ "$HTML" != "http://www.dilbert.com/dyn/str_strip/default_th.gif" ];
	then
		if [ ! -d /media/raid5/tony/Webcomics/dilbert/$DIL_YEAR ];
		then
			mkdir /media/raid5/tony/Webcomics/dilbert/$DIL_YEAR
		fi
		if [ ! -d /media/raid5/tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH ];
		then
			mkdir /media/raid5/tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH
		fi
		wget -q -O /media/raid5/tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH/$DIL_YEAR-$DIL_MONTH-$DIL_DAY.gif $HTML
		mogrify -resize 200% /media/raid5/tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH/$DIL_YEAR-$DIL_MONTH-$DIL_DAY.gif
		rm -f /tmp/magick-*
	fi
fi
```

---

### Post by markp1989 on 2011-08-16
I use cron to run a few things:

flexget, for auto downloading .torrent files. 

custom script for getting information about the lines I use from the [http://tubeupdates.com/](http://tubeupdates.com/) API and sending any changes to my phone using the [http://nma.usk.bz/](http://nma.usk.bz/) API.
using cron, its run every 15minutes between 6am and 6pm on weekdays, if its between september and december or january and may. This matches my uni time table, so I don't get notified when I am not needing the information 

I also have it run the following commands at 1am to keep my xbmc library up to date. 
/usr/bin/xbmc-send -a "UpdateLibrary(video)"
/usr/bin/xbmc-send -a "CleanLibrary(video)" 

lots of people use it to run back up programs such as rsync.

---

### Post by GWBouge on 2011-08-16
Yes, to change my desktop background every 20 minutes, and daily rsync backups.

---

### Post by urukrama on 2011-08-16
I use it to remind me to pause for prayer and meditation at noon and in the evening: [http://urukrama.wordpress.com/2010/11/27/making-linux-remind-me-to-meditate/](http://urukrama.wordpress.com/2010/11/27/making-linux-remind-me-to-meditate/)

---

### Post by ilovelinux33467 on 2011-08-16
yes, I use it for rsync

---

### Post by kjohri on 2011-09-10
Yes, it is useful in automating backups and synchronizing my desktop with the server. 

[Using cron]("http://www.softprayog.in/tutorials/using-cron")

---

