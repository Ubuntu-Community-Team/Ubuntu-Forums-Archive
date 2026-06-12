---
title: "Workaround for Electricsheep disabling Gnome Power Manager"
date: 2010-07-15
forum: Tutorials
---

### Post by DoritosBR on 2010-07-15
As some of you may have noticed, when running Electricsheep on Ubuntu Lucid (and various others distributions), the monitor never goes off as it should.
You can set any amount of time in "Gnome Power Manager" and the system completely ignores it.

It may be because of mplayer, which prevents monitor going off, and it's the right thing to do as it's an movie player, and nobody wants the monitor shutting off in a middle of a movie.

The Screensaver / Power management system works more or like this way:

After the idle time set in "Screensaver Preferences" the screensaver starts.
Then, after the time set in "Power Management Preferences", it will shut off the monitor.

So, if you have 5 minutes in screensaver and 30 minutes in power management, the monitor will go off after 35 minutes.

And than close the screensaver (no need to draw the screensaver when the monitor is off)

I managed to do an script that monitors the idle time, read the preferences set in Screensaver and Power Management, and after the time set it forces the monitor off. (and then kill the root window electricsheep)

It's a crappy workaround, but it's working quite nicely so far.

You will need first to go on synaptic and install a package named "xprintidle". (or just type in a terminal "sudo apt-get install xprintidle")
I's kind of a dependency. I use it to read the session idle time.

Then you get this script:
[http://www.tirinhas.com/etcetera/shutmonitoroff.sh](http://www.tirinhas.com/etcetera/shutmonitoroff.sh)

And put this script to initialize with your session, under System -> Preferences -> StartUp Applications.
Click Add and browse to the script.
 can edit the script if you wish.
You can easily set the amount of time directly into the script (without reading from gnome).
Or commenting the "kill electricsheep" line (which is a crappy workaround for closing the screensaver).
Doing this will prevent the electricsheep from being killed, and will draw the screensaver even with the monitor off.

It will only shut the monitor off if it finds an electricsheep running on root window (electricsheep running as screensaver)
It will not shut your monitor off if there is no electricsheep as a screensaver running.
(At least, it shouldn't)

So it shouldn't shut off your monitor when watching movies or something.

And it just kills the electricsheep running on root window (generally running on root window means it's running as screensaver)
So it shouldn't kill other instances of electricsheep.
If you have an "no animation" instance running to render / download, it shouldn't kill it.


Script is here:
[http://www.tirinhas.com/etcetera/shutmonitoroff.sh](http://www.tirinhas.com/etcetera/shutmonitoroff.sh)

Put this script to initialize with your session, under System -> Preferences -> StartUp Applications.

Use it at your own risk.
Posts feedback if it worked or not.

---

### Post by dag729 on 2011-09-13
It doesn't seem to work... strange thing is, I encounter the same problem even with the default screensavers: what's the point of having screensavers installed if they won't work (by default)?
Pretty funny!  :tongue:

---

