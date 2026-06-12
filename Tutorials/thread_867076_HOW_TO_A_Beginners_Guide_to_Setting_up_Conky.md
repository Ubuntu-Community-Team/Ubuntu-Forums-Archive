---
title: "HOW TO: A Beginners Guide to Setting up Conky"
date: 2008-07-22
forum: Tutorials
---

### Post by Bruce M. on 2008-07-22
The information in this thread has been moved to [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012428](http://ubuntuforums.org/showthread.php?t=2012428)


Thread closed.


Hi Folks

**Preamble:**

First and foremost this thread isn't meant to be a place to display your screeshots of conky or to discuss the inner workings of the conky configuration itself.  There are a couple of really good threads that will give you help in those areas:
[LIST=1]
[*][Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")
[*][Howto: Get a beautiful Conky 1.4.2 setup]("http://ubuntuforums.org/showthread.php?t=205865")
[*][Howto: setup Conky in Hardy and Ibex]("http://ubuntuforums.org/showthread.php?t=1010741")
[/LIST]

While this topic is discussed in those threads above, trying to find the information is difficult as it's spaced out over hundreds of pages and thousands of posts.

Here's some further reading to help you "configure" your conky if you are interested:
[LIST=1]
[*][~.conkyrc settings]("http://conky.sourceforge.net/config_settings.html")
[*][Conky Variables]("http://conky.sourceforge.net/variables.html")
[*][Conky Manual]("http://conky.sourceforge.net/docs.html")
[/LIST]

Fact is, I'm hoping that his will be a 1 post thread to keep it "uncomplicated". If you see and error, have an addition, please PM me and I'll pop it in here giving due credit.

So lets move on to: **A Beginners Guide to Setting up Conky**

[B][COLOR="Blue"][CENTER]CHAPTER I
Setting Up A Conky[/CENTER][/COLOR][/B]

**CONKY** - Conky is a system monitor for X originally based on the torsmo code.

Since its original conception, Conky has changed a fair bit from its predecessor. Conky can display just about anything, either on your root desktop or in its own window. Conky has many built-in objects, as well as the ability to execute programs and scripts, then display the output from stdout.

First you need the file "conky" and I'd suggest you look at curl, lm-sensors and hddtemp as well, described below. You may as well get them now, I'll bet you will in the future if you don't:
```
sudo aptitude install conky
```
**CURL** - Get a file from an HTTP, HTTPS or FTP server 

curl is a client to get files from servers using any of the supported protocols. The command is designed to work without user interaction or any kind of interactivity.

curl offers a busload of useful tricks like proxy support, user authentication, ftp upload, HTTP post, file transfer resume and more.

**LM-SENSORS** - utilities to read temperature/voltage/fan sensors 

Lm-sensors is a hardware health monitoring package for Linux. It allows you to access information from temperature, voltage, and fan speed sensors. It works with most newer systems.

This package contains programs to help you set up and read data from lm-sensors.

Homepage: [http://www.lm-sensors.org](http://www.lm-sensors.org)

**hddtemp** - hard drive temperature monitoring utility

The hddtemp program monitors and reports the temperature of PATA, SATA
or SCSI hard drives by reading Self-Monitoring Analysis and Reporting
Technology (S.M.A.R.T.) information on drives that support this feature.

If you want all four, it's easy:
```
sudo aptitude install conky curl lm-sensors hddtemp
```
OK, so you have the file(s).

Now to use conky, open a terminal and type:
```
conky
```
and you'll see a little window open and display a basic conky. That's the default conky found in: /etc/conky/conky.conf

But you want it on your desktop all the time and customized for your system, not in a pop-up window.

I'm going to be using gedit, you may have mousepad or kate. I use Xfce, but have gedit installed because I open multiple files in a tabbed environment. I'm also suggesting a directory and file names, one is hidden, use whatever you like, I'm using my setup here as an example only.

**STEP 1 - Create a conky**

[LIST]
[*]Create a directory in /home called /Conky
[*]Create an empty file called; conkymain:
```
gedit ~/Conky/conkymain
```
[*]Paste a conky file from one of the posts in the threads above that you like into that empty file and save it.
[/LIST]

Believe it or not that's it, you now have a working (maybe not configured correctly) conky.

In terminal type (the **-c** is telling conky to load and run the file that follows):
```
conky -c ~/Conky/conkymain
```
and you'll see it, it may not be perfect for your setup, that's why I suggest you go to the threads mentioned above or even the default file: /etc/conky/conky.conf

The point is, you now have a working conky

**STEP 2 - Setting up conky to autostart on boot.**
[LIST]
[*]Create a hidden file **~/.startconky**
```
gedit ~/.startconky
```
[*]In this empty file paste the following:
[/LIST]
```
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```

If you are using GNOME or KDE you'll need to change sleep 0 to sleep 20 or better, depending on your system. This gives your desktop (Metacity, Compiz, etc.) time to load itself and not over write an existing conky. The start conky command will be delayed by that time and not start until after your desktop is running.

I left two extra lines in there (commented out) for future reference if you ever want to run more than one conky. That's why I'm suggesting the ~/.startconky here. Once you start with conky, in my opinion, it's addictive and you may want more than one running. This way you are prepared.

Now you must make **~/.startconky** executable.  There are two methods:

**Terminal:**
```
chmod a+x ~/.startconky
```

**File Manager:**
Right click on *~/.startconky* > Properties > Permissions > check the box necessary to make it executable.

OK, so now you have conkymain working and a way to start it and a second one for future reference inside your ~/.startconky file.

Getting Ubuntu to **Autostart** conky.

**In Ubuntu:**
[LIST=1]
[*]System -> Preferences -> Sessions -> Startup Programs
[*]Click on the ADD button:
[/LIST]
**In Xubuntu:**
[LIST=1]
[*]Applications > Settings > Settings Manager > Autostarted Apps
[*]Click on the ADD button:
**Continuing in Ubuntu and Xubuntu:**
[*]Name: Conky <<-- anything you want
[*]Description: <<--- anything you want (mine is blank)
[*]Command: <<-- see the "Open Icon" click on that. When your home folder shows, right click to show hidden files if not visible ... and find the hidden file: .startconky. Highlight it and click [ OK ].
[*]Close
[*]Now: [Ctrl]+[Alt]+[Backspace] to restart your session and conky will start in xx seconds, depending on your sleep command.
[/LIST]

**In Kubuntu**

I am NOT a KDE user and have never seen it but I found this at the bottom of; [http://ubuntuforums.org/archive/index.php/t-19154.html](http://ubuntuforums.org/archive/index.php/t-19154.html) from 2006. Crinos512 has come up with an easy way to do this in KDE:

> **Crinos512 said:**
> As I promised I have come by to help out on autostarting conky in KDE 4.

it actually is just as easy as under Gnome, make your startconky script and make it executable.... as before. 

Then in the Kick Off panel, click the big blue **[COLOR="Blue"]K[/COLOR]**, select the Computer tab and then System Settings.

In the system settings App select the Advanced Tab and then AutoStart in the top section.

Click "Add Script" and browse to your startconky script.

Close system settings, you are done.

Well, that looks easy, **Thank you Crinos512**

Having a problem with a transparent conky in KDE 4, Crinos512 has a fix for you in [Post #24]("http://ubuntuforums.org/showpost.php?p=6676822&postcount=24")

Don't forget to thank him if you need it.

Here's another one for KDE users by **Ng Oon-Ee**, [Post #29]("http://ubuntuforums.org/showpost.php?p=6809184&postcount=29") for those times when:
> **Ng Oon-Ee said:**
> 1. if login time takes unusually long somehow (increased startup programs or low battery situation) the time may not be enough
2. When relogging-in without shutdown, the delay is much much longer than needed.

Again, Thank you Ng Oon-Ee for your support, and if you find it useful, don't forget to thank him.

[B][COLOR="Blue"][CENTER]CHAPTER II
A Multiple Conky Setup[/CENTER][/COLOR][/B]

Ok, you have your conky set up, you've configured it the way you want it's working properly for your system.

Now you want to put a second conky on your desktop, for example: weather.  If you followed the example above you have a **~/.startconky** file with a second entry commented out, called *conkyforecast*. Uncomment those lines and you are ready to create an run a second conky.

Create that file the same way you created *conkymain*. When you get the blank file up I "suggest" copying your "conkymain" file into it and deleting everything **[COLOR="Red"]below[/COLOR] TEXT** and change the "alignment" line for example:
```
alignment top_right  # top_right, top_left, bottom_left, bottom_right
```
to:
```
alignment bottom_left  # top_right, top_left, bottom_left, bottom_right
```
so they don't overlap each other.

Add what ever you want conky to display below TEXT, save it. Then edit the **~/.startconky** file **removing the # before the last two lines** and make sure the last line points to your second file:

```
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &
sleep 0 &&
conky -c ~/Conky/conkyforecast &
```
Now:
```
killall conky
conky -c ~/.startconky
```
to see the results.

**More on conky:**
[LIST=1]
[*]**ARCHIVED & LOCKED:** [Conky Weather Python Script]("http://ubuntuforums.org/showthread.php?t=760527"): Can be configured to use English (default), Spanish or French. [COLOR="Red"](Good for historical purposes ONLY)[/COLOR]
[*]**The New one:** [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328") - Same script in a new thread so we can post suggestions and requests.
[*][Conky Google Calendar Python Script]("http://ubuntuforums.org/showthread.php?t=837385")
[*][Conky SSL Email Python Script]("http://ubuntuforums.org/showthread.php?t=869771")
[*][conkyDeluge]("http://ubuntuforums.org/showthread.php?t=946664")
[*][conkyExaile]("http://ubuntuforums.org/showthread.php?t=926041")
[*][conkyPidgin]("http://ubuntuforums.org/showthread.php?p=6099901")
[*][conkyRhythmbox]("http://ubuntuforums.org/showthread.php?t=928168")
[*][Conky Gmail Revisited]("http://ubuntuforums.org/showthread.php?t=680265")
[*][How To: Configuring Conky]("http://lusule.wordpress.com/2008/08/07/how-to-4/") - Thank you Sealbhach
[*][HTML Color Names]("http://www.w3schools.com/HTML/html_colornames.asp") - Thank you Sealbhach
[/LIST]

OK that will get you started, now comes the fun part ... configuring it to your own personal tastes and machine.

Have a Nice day
Bruce

**PS:** If you see errors or have other conky resources that you feel might be helpful here please PM me.

-----
Dedicated to all the wonderful people that helped me with conky, you know who you are. **Thank you !**

**EDITS:**
[LIST]
[*]31 Jul 08 - Corrected ~/.startconky
[*]01 Aug 08 - Added: Conky Gmail Revisited
[*]15 Aug 08 - Added: "Getting Ubuntu to Autostart conky" section title.
[*]06 Nov 08 - Added more scripts to the list
[*]26 Nov 08 - Added info for running two or more scripts.
[*]27 Nov 08 - Added links, better late than never. *Thanks Sealbhach*
[*]28 Nov 08 - Added hddtemp. *Thanks Crinos512*
[*]02 Jan 09 - Added Link to: Howto: setup Conky in Hardy and Ibex
[*]04 Feb 09 - *Thanks to Crinos512*, an easy way to autostart in KDE
[*]04 Feb 09 - Fix for a transparent conky in KDE 4 *Thanks Crinos512*
[*]27 Feb 09 - Added Link to Ng Oon-Ee's post #29 *Thanks Ng Oon-Ee*
[/list]

---

### Post by jjgomera on 2008-07-22
good work

how to in [how to]("http://ubuntuforums.org/forumdisplay.php?f=100"), isnt it? :D

More in conky: really all you can obtain in a terminal, all dbus program, all dcop program, all daemon, infinite posibilities...

---

### Post by Dr Small on 2008-07-22
Em, maybe I am missing something here, but what is the point of the ~/.startconky, and 'sleep 0 &' eh?

---

### Post by bodhi.zazen on 2008-07-22
Nice write up, moved to tips and tutorials.

---

### Post by Bruce M. on 2008-07-22
> **Dr Small said:**
> Em, maybe I am missing something here, but what is the point of the ~/.startconky, and 'sleep 0 &' eh?

Edited to reflect your questions.

Thank you.
Bruce

---

### Post by Bruce M. on 2008-07-22
> **jjgomera said:**
> good work

how to in [how to]("http://ubuntuforums.org/forumdisplay.php?f=100"), isnt it? :D

More in conky: really all you can obtain in a terminal, all dbus program, all dcop program, all daemon, infinite posibilities...

It's been moved to Tips and Tutorials.  :)

I'm happy.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-07-22
> **bodhi.zazen said:**
> Nice write up, moved to tips and tutorials.

Thank you for this.

CHIMO!
Bruce

---

### Post by Dr Small on 2008-07-22
> **Bruce M. said:**
> Edited to reflect your questions.

Thank you.
Bruce
Oh. Ok, Thanks. It didn't make sense, since I don't use Gnome / Metacity ;)

---

### Post by monjope on 2008-08-12
Good work!! 

Thank you.

---

### Post by Bruce M. on 2008-08-12
> **monjope said:**
> Good work!! 

Thank you.

You're welcome and *Thank you.*
Enjoy.
Bruce

---

### Post by Sealbhach on 2008-08-14
I was puzzled about finding a list of colours until I looked at this guide

[How To: Configuring Conky]("http://lusule.wordpress.com/2008/08/07/how-to-4/")

which explained that you can use the HTML colour set. A list of Colour Names with hex equivalents can be found here:

[HTML Color Names]("http://www.w3schools.com/HTML/html_colornames.asp")


Hope this helps other n00bs like me!:)


.

---

### Post by Bruce M. on 2008-08-14
> **Sealbhach said:**
> I was puzzled about finding a list of colours until I looked at this guide

[How To: Configuring Conky]("http://lusule.wordpress.com/2008/08/07/how-to-4/")

which explained that you can use the HTML colour set. A list of Colour Names with hex equivalents can be found here:

[HTML Color Names]("http://www.w3schools.com/HTML/html_colornames.asp")


Hope this helps other n00bs like me!:)


.

Nice stuff and would fit better in the threads mentioned in my first post. As the idea here is not how to configure conky but how to set it up for the first time.

HOWEVER, having said that. It is a nice addition here as this is obviously a place new conky users will look, and this comes after the setup.

So, Thank you for the post.
Bruce

---

### Post by e2k on 2008-08-17
I want to thank you too, this thread kickstarted my conky configuration! After an hour of messing around with it, I now have the perfect conkymain to suit my needs. Much appreciated.. =D>

---

### Post by rbarbe on 2008-08-26
Excellent How To!!!

It's one of the best.

Thank you

---

### Post by negatifo on 2008-10-04
Hi everyone I'm new in Ubuntu and Linux too :). I got some problem with conky, when I try to start it it gives me 

```
Conky: can't open display:
```

I try to reinstall but it didn't  workout.

Thanks in Advance !

Negatifo

---

### Post by Bruce M. on 2008-10-04
> **negatifo said:**
> Hi everyone I'm new in Ubuntu and Linux too :). I got some problem with conky, when I try to start it it gives me 

```
Conky: can't open display:
```

I try to reinstall but it didn't  workout.

Thanks in Advance !

Hi Negatifo

Welcome to Ubuntu, you are going to love it.

No to be disrespectful or a bad guy but can you repost your question in one of the following threads. There are a lot of people there that will be helping you and quite a few know more about conky than I do.

> **Bruce M. said:**
> First and foremost this thread isn't meant to be a place to display your screeshots of conky or to discuss the inner workings of the conky configuration itself.  There are a couple of really good threads that will give you help in those areas:
[LIST=1]
[*][Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")
[*][Howto: Get a beautiful Conky 1.4.2 setup]("http://ubuntuforums.org/showthread.php?t=205865")
[/LIST]

Have a nice day.
Bruce

---

### Post by NewJack on 2008-10-09
I just wanted to thank Bruce for this simple, yet great HowTo.  Got me running in no time.

Joe

---

### Post by thraxy on 2009-01-02
Cheers mate! Exactly what I was looking for today :)

---

### Post by Bruce M. on 2009-01-02
> **NewJack said:**
> I just wanted to thank Bruce for this simple, yet great HowTo.  Got me running in no time.

Joe

Hi Joe, Glad to hear that.

> **thraxy said:**
> Cheers mate! Exactly what I was looking for today :)

Hi thraxy, Glad to have helped.

Show us a screenshot at: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")

Have a nice day.
Bruce

---

### Post by Messyhair42 on 2009-01-31
edit: got the conky running but when i get to this part of the instructions: 

Terminal:Code:

chmod a+x ~/.startconky

File Manager:
Right click on ~/.startconky > Properties > Permissions > check the box necessary to make it executable.


I dont know where to find ~/.startconky after running the terminal code

also i'm not getting any temperatures from my cpu, motherboard or hdd

---

### Post by Bruce M. on 2009-01-31
> **Messyhair42 said:**
> edit: got the conky running but when i get to this part of the instructions: 

Terminal:Code:

chmod a+x ~/.startconky

File Manager:
Right click on ~/.startconky > Properties > Permissions > check the box necessary to make it executable.


I dont know where to find ~/.startconky after running the terminal code

also i'm not getting any temperatures from my cpu, motherboard or hdd

Hi Messyhair42

That file is "hidden" in your **/home** directory (it starts with a **[SIZE="6"].[/SIZE]**)

If you read the first post there is a section for "Auto Starting" conky that you need to set up.  I'll re-quote it here if you have Ubuntu or Xubuntu. If you have KDE that information is also in the first post:

> Getting Ubuntu to Autostart conky.

In Ubuntu:

   1. System -> Preferences -> Sessions -> Startup Programs
   2. Click on the ADD button:

In Xubuntu:

   1. Applications > Settings > Settings Manager > Autostarted Apps
   2. Click on the ADD button:

      Continuing in Ubuntu and Xubuntu:

   3. Name: Conky <<-- anything you want
   4. Description: <<--- anything you want (mine is blank)
   5. Command: <<-- see the "Open Icon" click on that. When your home folder shows, right click to show hidden files if not visible ... and find the hidden file: .startconky. Highlight it and click [ OK ].
   6. Close
   7. Now: [Ctrl]+[Alt]+[Backspace] to restart your session and conky will start in xx seconds, depending on your sleep command.

Once you do that conky will start when you start your computer or a new session - New Session: [Ctrl]+[Alt]+[Backspace]

For temperatures, the first post tells you that you need hddtemp and lm-sensors installed, but it is beyond the scope of this tutorial on how to do that. You can post your questions for that in one of these threads (I'm in all of them):
[LIST=1]
[*][Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865")
[*][Howto: Get a beautiful Conky 1.4.2 setup]("http://ubuntuforums.org/showthread.php?t=205865")
[*][Howto: setup Conky in Hardy and Ibex]("http://ubuntuforums.org/showthread.php?t=1010741")
[/LIST]

Have a nice day.
Bruce

---

### Post by Crinos512 on 2009-02-03
Chimo Bruce!

As I promised I have come by to help out on autostarting conky in KDE 4.

it actually is just as easy as under Gnome, make your startconky script and make it executable.... as before. 

Then in the Kick Off panel, click the big blue **[COLOR="Blue"]K[/COLOR]**, select the Computer tab and then System Settings.

In the system settings App select the Advanced Tab and then AutoStart in the top section.

Click "Add Script" and browse to your startconky script.

Close system settings, you are done.

---

### Post by Bruce M. on 2009-02-04
> **Crinos512 said:**
> Chimo Bruce!

As I promised I have come by to help out on autostarting conky in KDE 4.

it actually is just as easy as under Gnome, make your startconky script and make it executable.... as before. 

Then in the Kick Off panel, click the big blue **[COLOR="Blue"]K[/COLOR]**, select the Computer tab and then System Settings.

In the system settings App select the Advanced Tab and then AutoStart in the top section.

Click "Add Script" and browse to your startconky script.

Close system settings, you are done.

Thank you!

You are now quoted in the first post!  :)
CHIMO!
Bruce

---

### Post by Crinos512 on 2009-02-04
FYI: there is an issue with using KDE 4 with a transparent conky... the wallpaper used by Plasma does not "show through".

the simple fix for this is to install feh ( [COLOR="Blue"]sudo apt-get install feh[/COLOR] )

then append this to the end of your .conkyrc 
[COLOR="#0000ff"]${texeci 1000 feh --bg-scale "`grep 'wallpaper=' ~/.kde/share/config/plasmarc | tail --bytes=+11`"}[/COLOR]

---

### Post by Bruce M. on 2009-02-04
> **Crinos512 said:**
> FYI: there is an issue with using KDE 4 with a transparent conky... the wallpaper used by Plasma does not "show through".

Hmmm, No "Thank You" Button here. :frown: so ----

[CENTER]**[COLOR="DarkRed"][SIZE="5"]Thank You![/SIZE][/COLOR]**[/CENTER]

Will pop a link to this into the first post

CHIMO!
Bruce

---

### Post by kodiakmax on 2009-02-06
KDE3.5 no compiz

I am trying to get conky to be transparent with twinview enabled for 2 monitors.  Each monitor has a seperate wallpaper.  Normally with just one monitor/wallpaper transparency works fine with the following command.

```
${texeci 60 feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`}
```

I am not sure weather the problem lies with feh or dcop.  If I go to kde control center --> desktop --> behavior and then toggle the show icons off and on.  Then conky "transparency" works.  I realize that what this does is copy the current wallpaper to the root wallpaper.  If I could get dcop to do the same thing that would be great. Or failing to find the correct dcop command, perhaps just get feh to only scale for one monitor (bg-seamless, bg-tile, and bg-center don't work).  Any ideas would be helpful.

---

### Post by Bruce M. on 2009-02-07
> **kodiakmax said:**
> KDE3.5 no compiz

I'm sorry I cannot help you, I'm not a KDE user and your request is beyond the scope of this little HowTo.

I would suggest that you re-post your post here: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865"). There are KDE users there, Crinos512 being one of them, that I'm sure will be glad to help.

Sorry for the inconvenience.
Have a nice day.
Bruce

---

### Post by kodiakmax on 2009-02-07
Thanks for your reply I'll give the other thread a shot then :)

---

### Post by Ng Oon-Ee on 2009-02-27
Hi, I've been searching around for auto-start info for conky on compiz (specifically Ubuntu, though a general compiz-related issue I believe). Of course, most people use the sleep function as you've shown here, but there's two problems with that:-
1. if login time takes unusually long somehow (increased startup programs or low battery situation) the time may not be enough
2. When relogging-in without shutdown, the delay is much much longer than needed.

So, I set about looking for a way to check whether compiz was actually running. At first I saw checks for whether pidof compiz or compiz.real returned a PID, but even if a PID was available it didn't mean compiz had actually started taking control of the desktop, hence the conky window may be drawn before compiz starts.

Finaly solution, using the dbus plugin in compiz, which returns an error if compiz is not fully functional yet (initial help came from [the compiz forums]("http://forum.compiz-fusion.org/showthread.php?p=71409")). So, here's how my startconky looks like:-

```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
		DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
		DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```

I have three conkys, so of course those lines need to be modified based on your setup. Please note that the dbus plugin for compiz must be enabled, and that if you're not using compiz, this code would mean your conky would never start from this script. If you're not using compiz, you don't need to worry about checking for it, of course =).

So, think this is useful enough for addition to the HOWTO? Or is it too technical and niche? Anyhow, I can just post it up elsewhere if you figure its not suitable here.

---

### Post by Bruce M. on 2009-02-27
> **Ng Oon-Ee said:**
> So, think this is useful enough for addition to the HOWTO? Or is it too technical and niche? Anyhow, I can just post it up elsewhere if you figure its not suitable here.

Hi Ng Oon-Ee,

Hey, that looks great.
I'll link to your post in the first post.

Thanks for the support.
Bruce

---

### Post by Ng Oon-Ee on 2009-02-27
You're welcome :P. Thanks for the great guide, its been helpful.

---

### Post by nyarnon on 2009-03-12
> **Ng Oon-Ee said:**
> 

Finaly solution, using the dbus plugin in compiz, which returns an error if compiz is not fully functional yet (initial help came from [the compiz forums]("http://forum.compiz-fusion.org/showthread.php?p=71409")).

Thanks that found it's way into my ~/bin very usefull indeed.

---

### Post by Ng Oon-Ee on 2009-03-12
> **nyarnon said:**
> Thanks that found it's way into my ~/bin very usefull indeed.
You're welcome. Dbus is such an amazing tool.

---

### Post by FerociousTwig on 2009-05-03
So I'm having trouble with this... whenever I restart conky I do the following. 

sudo killall conky
sudo conky

Then I get about 50 error messages every 1/2 second or so that read:

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Then sometimes it will eventually work. Othertimes I get too frustrated and just give up. Any ideas?

(complete noob, sorry)

---

### Post by Bruce M. on 2009-05-04
> **FerociousTwig said:**
> So I'm having trouble with this... whenever I restart conky I do the following. 

sudo killall conky
sudo conky

Then I get about 50 error messages every 1/2 second or so that read:

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Then sometimes it will eventually work. Othertimes I get too frustrated and just give up. Any ideas?

(complete noob, sorry)

Hi FerociousTwig,

Welcome to conky, soon you will be addicted like most of us.

Well, we were all new to conky at one time. Don't apologize for it. I doubt very much you are a [noob]("http://www.urbandictionary.com/define.php?term=noob") either, due to the fact you are trying and asking for help. I really do dislike that term.  :)

It sounds like you copied a conky from someone else and you have calls that you don't need with you system.

Anyway since the guide come with no real conky setup, it's difficult to answer your questions here. So before you get to frustrated there are a lot of recourses available to you, two of which are:

[Conky Hardcore!]("http://conky.linux-hardcore.com/") - a conky reference site with some setups although more complicated. There is [a simple conky]("http://conky.linux-hardcore.com/?page_id=173") there to get you started, and

The mega thread here: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") where you can post the conky you have and ask your questions. *If I don't answer you there, it will be because someone beat me to it.* There is a lot of people in that thread helping others from the very simple "I'm new to this" questions to the more complex ones.

Just don't give up, and you'll surprise yourself how easy it is when you have the answers. Like I tell people, *"If I can do it, anyone can."*

Have a nice day.
Bruce

---

### Post by neo.patrix on 2009-06-17
I found Conky when searching for some cool desktop stuff. I have started with [Conky-Colors]("http://www.gnome-look.org/content/sh...?content=92328"). It is very addictive as fore warned. I spent nearlly three hours with colors & some icon customization, most of trying  to decipher commands in ".conkyrc" how & where to make changes. Next I am going to modify ".conkyrc" to get system-logs.

Here my desktop with customized theme for ConkyColors

[[IMG]http://img196.imageshack.us/img196/1390/patrixlaptop.th.png[/IMG]](http://img196.imageshack.us/i/patrixlaptop.png/)

".conkyrc" was generated with command

> 
./conky-colors --theme=human --unit=C --cpu=2 --powerb --updates=apt-get --proc=3 --calendar --banshee --network --wlan=0


---

### Post by coffee-n-cream on 2009-07-31
hey guys great writeup.I manage to get conky working but the displayed time does not update itself.how do i fix this? thx

---

### Post by Bruce M. on 2009-07-31
> **coffee-n-cream said:**
> hey guys great writeup.I manage to get conky working but the displayed time does not update itself.how do i fix this? thx

Hi coffee-n-cream

The mega thread here: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") is where you can post the conky you have and ask your questions. *If I don't answer you there, it will be because someone beat me to it.* There is a lot of people in that thread helping others from the very simple "I'm new to this" questions to the more complex ones.

This is a HowTo and I'd rather not duplicate the above thread.  It is so helpful that people using other dustro's come here to ask conky questions.  :)

Have a nice day.
Bruce

---

### Post by theGlitch on 2009-07-31
very helpful how-to! thanks! 

Is there anyway to edit the width of the Conky window?

---

### Post by Cardale on 2009-08-04
Great! this helped a lot.

---

### Post by dreadkit.kat on 2009-08-31
please help me  cant figure out what is wrong since i followe deach and everystep.i dont get the CPU temp and the MB temperature and the HDD temperature right.It is always set to 0 c

i```
ndranil@indranil-desktop:~$ conky -c ~/conky/conkymainConky: /home/indranil/conky/conkymain: 30: no such configuration: 'on_bottom'
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: /home/indranil/conky/conkymain: 94: no such configuration: 'xmms_player'
Conky: statfs '/media/data': No such file or directory
Conky: desktop window (14000a7) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found
Conky: statfs '/media/data': No such file or directory
sh: /home/indranil/.bin/hddconky: not found

```

---

### Post by Bruce M. on 2009-08-31
> **dreadkit.kat said:**
> please help me  cant figure out what is wrong since i followe deach and everystep.i dont get the CPU temp and the MB temperature and the HDD temperature right.It is always set to 0 c


I think you copied someones conky file and expected it to work, but their computer is different to yours. Like it says in the first post:

> In terminal type (the -c is telling conky to load and run the file that follows):

```
conky -c ~/Conky/conkymain
```

and you'll see it, it may not be perfect for your setup, that's why I suggest you go to the threads mentioned above or even the default file: /etc/conky/conky.conf

Head over to: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") and ask questions there.

Have a nice day.
Bruce

---

### Post by mesuhas_sit on 2010-05-14
Bruce... Thank you very much for this thread and howto... very usefull... and fun...
 
 
For all you Ubuntu beginers... Go through this and have fun... 
It has all the elements of having fun with ubuntu right from getting stuff... using the terminal... modifying and customizing..... and you can see the fun looking at your friends face who look at your desktop...
 
 
I started modifying my ubuntu with CONKY... Have fun...
 
Bruce you :guitar:

---

### Post by emma00 on 2010-07-02
Paste a conky file from one of the posts in the threads above that you  like into that empty file and save it


I did not get this from which thread do i have to paste the lines i did from some of the posts but its giving some errors.

---

### Post by ankit singh on 2010-07-06
Conky threads are always long so i will give a concise conlusion of what people should do(this note is not in detail,forgive me) 
Conclusion(only For Lucid Lynx):
------------------------------------------------------------------------------------

install conky

```
sudo apt-get install conky-all
```-------------------------------------------------------------------------------------
and Download this script(i giving here my script,just click on it and firefox will pop some option.Hit the "save" option).This script will create a .conkyrc file and will also write everything.No tension here.Just do what i said

[ATTACH]162594[/ATTACH]
-------------------------------------------------------------------------------------
Now do the following steps:
1)Download this script in your home directory
2)Right click ->Permissions-> mark [COLOR=#000000][FONT=arial][***executable***]("http://ubuntuforums.org/search?hl=en&&sa=X&ei=VC0zTPydMcK0rAfC_q3HBA&ved=0CAYQvwUoAQ&q=executable&spell=1")[/FONT][/COLOR]
3)Double click on the script and click "run"
---------------------------------------------------------------------------------------
Now we need to create a script

now create a new file in any directory you want and name it "conky.sh"
Paste the following code in it
```

#!/bin/bash
sleep 30
conky &
exit 0

```Close the file and make it [COLOR=#000000][FONT=arial][***executable***]("http://ubuntuforums.org/search?hl=en&&sa=X&ei=VC0zTPydMcK0rAfC_q3HBA&ved=0CAYQvwUoAQ&q=executable&spell=1")[/FONT][/COLOR] (Right click ->properties->Permissions)
-----------------------------------------------------------------------------------------
Now go to System -> Startup applications and click "add" and after that put "Conky" as name and in place of location,you should put your script directory(conky.sh)
I m giving the screenshots
[ATTACH]162596[/ATTACH]
-----------------------------------------------------------------------------------------
Note if in the above step u see that there is already a conky added to start up then you should edit the location.(Once again in location you should write out the location of your script i.e conky.sh)
------------------------------------------------------------------------------------------
After all this simple nooby steps,You will find magic on your desktop(Reboot may be required)
Look at this screenshot
[ATTACH]162597[/ATTACH]
------------------------------------------------------------------------------------------


:popcorn:

---

### Post by martinblunn on 2010-07-22
Hi Guys,

 Just a quick question.
I want to use an animated wallpaper using XWinWrap. I know that doing so covers any desktop icons, but I cant find whether it also prevents Conky's from working. Does anyone have any experience or knowledge about this.

Martin

---

### Post by corrytonapple on 2010-08-03
Thank you Bruce for this Guide. I spoke about Conky a bit in a How-To and I linked it to here. Thanks again.

---

### Post by biltong on 2010-08-19
Hi everyone, I've been using conky for a while now and moved on to a laptop.  Everything works fine except the upspeed and downspeed of wlan0, there is simply no activity. My ifconfig only gives me only eth0 & wlan0.

UP: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 BEBEBE BEBEBE}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 BEBEBE BEBEBE}

The funny thing is that the signal strength does get displayed.
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}

Got any ideas.

---

### Post by baraka607 on 2010-10-10
hi friends, i have managed to create some scripts so that some of you can use them in their conky, just try it and let me know what do you think.

the codes are:

    background yes
    use_xft yes
    xftfont HandelGotD:size=8
    xftalpha 0.5
    update_interval 4.0
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 200 5
    maximum_width 220
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color grey
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 12
    gap_y 48
    no_buffers yes
    uppercase no
    cpu_avg_samples 2
    override_utf8_locale no

    TEXT
    $sysname $kernel on $machine

    Uptime $alignr $uptime
    Load $alignr $loadavg
    Temp: ${alignr}${acpitemp}C

    Hostname $alignr $nodename
    wlan0 $alignr ${addr wlan0}

    Inbound $alignr ${downspeed wlan0} kb/s
    ${downspeedgraph wlan0}
    Outbound $alignr ${upspeed wlan0} kb/s
    ${upspeedgraph wlan0}

    $processes processes ($running_processes running)

    CPU $alignr ${cpu cpu0}%
    ${cpubar cpu0}

    MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    / $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
    ${fs_bar /}

    /home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}

    swap $alignc $swap / $swapmax $alignr $swapperc%
    ${swapbar}

${color white}NETWORK ${hr 1}${color}

Down ${downspeed ppp0} k/s ${alignr}Up ${upspeed ppp0} k/s
${downspeedgraph ppp0 25,107} ${alignr}${upspeedgraph ppp0 25,107}
Total ${totaldown ppp0} ${alignr}Total ${totalup ppp0}


    NAME $alignr PID    CPU
    ${top name 1} $alignr ${top pid 1} ${top cpu 1}
    ${top name 2} $alignr ${top pid 2} ${top cpu 2}
    ${top name 3} $alignr ${top pid 3} ${top cpu 3}
    ${top name 4} $alignr ${top pid 4} ${top cpu 4}
    ${top name 5} $alignr ${top pid 5} ${top cpu 5}

---

### Post by Gotit on 2010-10-31
I have conky running on 2 different machines without problem.  However, I get a behavior on one of the machines I would like to have on the other, but can't figure out how to make it happen.

The behavior is that when I modify my .conkyrc file and save it, conky automatically reloads with the new settings.  I really like this feature as I don't need to do a
```
killall conky && conky
``` 

Here's what I see in the terminal window when I save my modified .conkyrc file
> Conky: '/home/gotit/.conkyrc' modified, reloading...
Conky: desktop window (14000a5) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x2400002)
Conky: drawing to double buffer


Does anyone know how to make conky monitor the .conkyrc file and reload when it gets modified?

---

### Post by firewall_03 on 2010-12-23
I followed your directions to the letter and am getting an error.
Any ideas?

```
rob@rob-netbook:/$ cd Conky/
rob@rob-netbook:/Conky$ cd gedit conkymain
bash: cd: gedit: No such file or directory
rob@rob-netbook:/Conky$ sudo gedit conkymain
rob@rob-netbook:/Conky$ conky -c ~/Conky/conkymain
Conky: invalid configuration file '/home/rob/Conky/conkymain'

Conky: desktop window (1c00003) is subwindow of root window (aa)
Conky: window type - desktop
Conky: drawing to created window (0x5a00001)
Conky: drawing to single buffer
^Z
[1]+  Stopped                 conky -c ~/Conky/conkymain
rob@rob-netbook:/Conky$
```

My conky file
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

---

### Post by Gotit on 2010-12-24
firewall_03
> Conky: invalid configuration file '/home/rob/Conky/conkymain'

If this is the problem you are referring to, it could be that Conky looks for a specific config file (.conkyrc) as a hidden file in your home directory.  In your case the path looks like it should be:
```
/home/rob/.conkyrc
```

---

### Post by firewall_03 on 2010-12-24
> **Gotit said:**
> firewall_03

If this is the problem you are referring to, it could be that Conky looks for a specific config file (.conkyrc) as a hidden file in your home directory.  In your case the path looks like it should be:
```
/home/rob/.conkyrc
```

I was just following the directions from the tutorial on the first post or so

---

### Post by Gotit on 2010-12-24
Oh, I see...
Guess I'm running a little more "vanilla" than that.  Basically, installed conky from the repos and put my config file in my home directory as .conkyrc for tweaking per the manual.

You might want to try that and then in the terminal run:
```
~$ killall conky
~$ conky
```
to see if it picks up your configurations and runs it.

---

### Post by firewall_03 on 2010-12-24
thats what it is doing now and conky doesn't start, or at least I can't see it

```
rob@rob-shop:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: /home/rob/.conkyrc: 44: no such configuration: 'border_margin'
Conky: statfs '/mnt/slack': No such file or directory
Conky: desktop window (20000a9) is subwindow of root window (72)
Conky: window type - normal
Conky: drawing to created window (0x6200001)
Conky: drawing to double buffer
Conky: statfs '/mnt/slack': No such file or directory
Conky: statfs '/mnt/slack': No such file or directory

```

---

### Post by Gotit on 2010-12-24
firewall_03
Good news is that I copied your Conky file into my /home/gotit/.conkyrc file restarted conky and it displays fine (with the same errors you show).
> gotit@Home-Linux:~$ Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: /home/gotit/.conkyrc: 44: no such configuration: 'border_margin'
Conky: statfs '/mnt/slack': No such file or directory
Conky: desktop window (18000a5) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x1a00001)
Conky: drawing to double buffer
Conky: statfs '/mnt/slack': No such file or directory
Conky: statfs '/mnt/slack': No such file or directory
Conky: statfs '/mnt/slack': No such file or directory

I can't say why it isn't displaying for you right now. :(

---

### Post by firewall_03 on 2010-12-24
Well now its working I had to comment out the slackware lines

---

### Post by Gotit on 2010-12-24
GREAT!
My next suggestion was to try a very basic .conkyrc and see if that worked and tweak it to what you wanted.

---

### Post by firewall_03 on 2010-12-24
How hard is to add the .conkyforecast script to it?

---

### Post by Kognit on 2010-12-26
Hi

I have Ubuntu 10.04 and i found out that because of conky dbus-daemon eats a lot of RAM. From the beginning dbus-daemon have only 1 MB of RAM and after few hours dbus-daemon have 200 MB od RAM. Is there any way to fix this issue with dbus-daemon because i really like conky?

Thx for help

---

### Post by WarrenSH on 2010-12-26
Wicked tutorial mate! 

Can you please update this posting with pictures so that some of our new Ubuntu/Linux members can understand this better?

Thanks ;) love it <3

---

### Post by jermza on 2011-07-15
Is this guide still relevant, now being 2011?  I see this was written in 2008.  I'm asking because I've tried and failed to install Conky (largely due to my noob status).

---

### Post by Gotit on 2011-07-16
> **jermza said:**
> Is this guide still relevant, now being 2011?  I see this was written in 2008.  I'm asking because I've tried and failed to install Conky (largely due to my noob status).

Did you try installing from Synaptic or Applications > Ubuntu Software Center?  That should give you Conky and a basic config file at etc/conky/conky.conf

Copy that file (conky.conf) and paste it in you home directory as 
```
.conkyrc
```
Logout/in and conky should be running.  

For current Conky information you can see here too [http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

---

### Post by Sector11 on 2011-07-23
> **jermza said:**
> Is this guide still relevant, now being 2011?  I see this was written in 2008.  I'm asking because I've tried and failed to install Conky (largely due to my noob status).

Yes, it is.

> **Gotit said:**
> Did you try installing from Synaptic or Applications > Ubuntu Software Center?  That should give you Conky and a basic config file at etc/conky/conky.conf

Copy that file (conky.conf) and paste it in you home directory as 
```
.conkyrc
```
Logout/in and conky should be running.  

For current Conky information you can see here too [http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

Don't even have to copy it over if ~/.conkyrc doesn't exit conky will default to using /etc/conky/conky.conf

But it is nice to have your own in ~/  :D

---

### Post by Denver79 on 2011-07-25
Thank you very much, good work!!

---

### Post by spraitukas on 2011-12-25
Is there a newer tt like this? Im new to ubuntu and its really confusing to find workarounds for nearly every step mentioned here since its almost 2012 and ubuntu has changed A LOT ](*,)

---

### Post by bodhi.zazen on 2011-12-25
Three options:

1. Copy a working .conky from someone else.

2. conkywizard - a graphical configuration tool

[http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html](http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html)

3. Read the man page

[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

[http://wiki.conky.be/index.php?title=Conky_Wiki](http://wiki.conky.be/index.php?title=Conky_Wiki)

---

### Post by Borunco on 2012-01-12
```
**STEP 1 - Create a conky**

[LIST]
[*]Create a directory in /home called /Conky
[*]Create an empty file called; conkymain:
     Code:
     gedit ~/Conky/conkymain
[/LIST]

```Hi, I'm trying to get conky to work, the problem that i'm having is I don,t know how to (Create a directory in /home called /Conky). I have done the code that you did above put when i copy/paste a conky to the gedit file and try to save it, tells me that cant find home folder. I also have used the conky wizard and on both I get working conkys when I turn them on, dont understand why can get the copy/paste one to save. Just to let you know I a BIG TIME NOOB. I have tried it on Lubuntu 11.04, Ubuntu 10.04-3, Ubuntu 11.04 and all do the same thing , so I know it,s me. can any body help me and explain it to a NOOB. thank you.
Love Ubuntu:D
Ps I get (could not find /home/jose/conky/conkymain)

---

### Post by Gotit on 2012-01-12
@Borunco

Easiest way to create a folder in your home directory is to open your home folder by going to Places > Home Folder

This will open your home folder in a Nautilus window.

Then select File > Create Folder
A new folder will be created and highlighted waiting for you to name it.  In your case it looks like the name will be Conky.  Just type it in and press Enter.

---

### Post by Borunco on 2012-01-13
> **Gotit said:**
> @Borunco

Easiest way to create a folder in your home directory is to open your home folder by going to Places > Home Folder

This will open your home folder in a Nautilus window.

Then select File > Create Folder
A new folder will be created and highlighted waiting for you to name it.  In your case it looks like the name will be Conky.  Just type it in and press Enter.
Thanks for the help Gotit. I did was you instructed and every thing worked, the problem I'm having now, I can't get the conky to auto start. I have followed the instructions given here and on the conky wizard site and can't get ether one of them to come on ,only manually. any help would be greatly appreciated. I have spent a lot of time on this and yet I think the problem is right in front of me and may not know what I'm looking at, just trying to figure things out.
Thanks for any and all help
borunco

---

### Post by Gotit on 2012-01-13
I've had some problems with getting Conky to start when I boot too.  But, I got it resolved thanks to other posts in the forums.  Here's what I ended up with

Create a new text file and add these lines:
```
#!/bin/bash
sleep 8 && conky
```
Save the file in your home directory as something.sh  I used: 
> .conky_start.sh
This will add a short (8 sec) delay to starting Conky.
Once saved navigate to the newly saved file, right click and select Properties.  
On the Permissions tab, check the "Allow executing file as program" check box and close the properties dialogue.

Go to: 
Systems > Preferences > Startup Applications
Click Add
In the dialogue box give a name (I used Conky)
In the command box enter
```
/home/your_home_folder_name/.conky_start.sh
```
and click OK to save.  You should now have a new Conky entry in the Startup Applications Preferences list.
Make sure the check box next to Conky is checked in the Startup Applications Preferences.
Log out/in from Gnome and Conky should start automatically.

---

### Post by Borunco on 2012-01-13
> **Gotit said:**
> I've had some problems with getting Conky to start when I boot too.  But, I got it resolved thanks to other posts in the forums.  Here's what I ended up with

Create a new text file and add these lines:
```
#!/bin/bash
sleep 8 && conky
```Save the file in your home directory as something.sh  I used: 

This will add a short (8 sec) delay to starting Conky.
Once saved navigate to the newly saved file, right click and select Properties.  
On the Permissions tab, check the "Allow executing file as program" check box and close the properties dialogue.

Go to: 
Systems > Preferences > Startup Applications
Click Add
In the dialogue box give a name (I used Conky)
In the command box enter
```
/home/your_home_folder_name/.conky_start.sh
```and click OK to save.  You should now have a new Conky entry in the Startup Applications Preferences list.
Make sure the check box next to Conky is checked in the Startup Applications Preferences.
Log out/in from Gnome and Conky should start automatically.
Hi gotit, I looked at what you posted and I was doing all that you said except the (/home/name/) part at the command box in the startup app section. Did that and my conky started after reboot. YEAH BABY you made my day. ( sorry didn't mean to call you baby). Now I can move on start playing with it.
 thank you.
[COLOR=Red]**Just a note to this tutorial, some things that are taken for granted, like living that part of the code out, for NOOBS like me we some times don't understand, and can be copying/pasting all day long and things will not work. So in conclusion in a tutorial things need to be explained, like the person on the other side has never done a code structure before. For those more experienced it would be boring at first, but for the beginners is a total rush, and there would be faster growth.**[/COLOR]
Thank again Gotit
borunco:popcorn:

---

### Post by Sector11 on 2012-01-21
If you were reading this guide, the way to start conky (be it one or more) is described in the first post:

**STEP 2 - Setting up conky to autostart on boot.**

What it does not say is "~/" is equal to /home/your_name/

Want to see what yours is?  In a terminal:

```
  14:05:12 ~
         $ $HOME
bash: /home/sector11: Is a directory

  14:05:18 ~
         $ 

```

so you can use (in my case):
```
/home/sector11/

~/

$HOME/
```

The script on the first page can be (original):
```
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &
# sleep 0 &&
# conky -c ~/Conky/another_conky &
```

**[COLOR="DarkRed"]OR[/COLOR]**
```
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c /home/sector11/Conky/conkymain &
# sleep 0 &&
# conky -c /home/sector11/Conky/another_conky &
```
**[COLOR="DarkRed"]OR[/COLOR]**
```
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c $HOME/Conky/conkymain &
# sleep 0 &&
# conky -c $HOME/Conky/another_conky &
```

With "some" newer versions of conky if you edit them most times you need to kill then and restart them or they don't "resize"

Nice script for that is [Start/Stop Conky]("http://conky.pitstop.free.fr/wiki/index.php5?title=Start/Stop_Conky_%28en%29")

In keeping with the example above:

```
   #!/bin/sh
   # Name: ssc.sh
   # click to start, click to stop, click again to start
    
   if pidof conky | grep [0-9] > /dev/null
   then
   exec killall conky
   else
   #sleep 3  # sleep may not be required on startup
   conky -c ~/Conky/conky &
   # conky -c ~/Conky/conky2 &  ## 2nd or 3rd conky
   # conky -c ~/Conky/another3 &  ## uncomment to use
   exit
   fi
```

Since conky is NOT running when you boot up you can use this script as an auto start script as well.  How you do that is explained in the first post of this thread as well.  Since it is old YMMV (your mileage may vary).

---

### Post by Borunco on 2012-01-22
Thank you, sector11 for explaining that. although when I was trying to do the ~/conky/conkymain I was not getting a file in file manager with the conkymain name. I have a working conky now on my desktop and it's coming on at start, thanks to you guys help. I will try again on my net-book this week and see if all goes well, but for sure it is a great learning experience, and it's AWESOME to have people like you that know what to do and are willing to help us noobs.
Thank you
borunco  :D

---

### Post by Sector11 on 2012-01-22
> **Borunco said:**
> Thank you, sector11 for explaining that. although when I was trying to do the ~/conky/conkymain I was not getting a file in file manager with the conkymain name. I have a working conky now on my desktop and it's coming on at start, thanks to you guys help. I will try again on my net-book this week and see if all goes well, but for sure it is a great learning experience, and it's AWESOME to have people like you that know what to do and are willing to help us noobs.
Thank you
borunco  :D

I'm a noob about many things Linux.  But I was taught about conky by some patient people that stuck with me through thick and thin even thought I asked the same question a couple of times.  Now I help because I know the frustration of trying and the "WHY DOESN'T THIS WORK FOR ME! Grrrrrrrrr!!!"

"conky" is a program, it uses a normal "text file" to get it's output from.

When you install the program conky there is NO "~/.conkyrc" in your home directory and typing ```
conky
``` starts up the default ugly conky file found in */etc/conky/conky.conf*.

However "conky" is designed to read and use *~/.conkyrc* if it is there in your home directory.  Many Linux Distros are now including conky in the install process with a default conky in ~/.conkyrc.

My Distro default conky is still intact:
[[IMG]http://thumbnails55.imagebam.com/17114/0a5d16171130890.jpg[/IMG]](http://www.imagebam.com/image/0a5d16171130890)
I've never touched it, but I have a look-a-like I modified.

In the first post it says to:
[LIST=1]
[*]Create a directory in /home called /Conky
[*]Create an empty file called; conkymain:
```
gedit ~/Conky/conkymain
```
[*]**Paste a conky file from one of the posts in the threads above that you like into that empty file and save it.**[/LIST]

don't forget #3 - *you need to create the file*,  Also pasting a conky into that open file will not guarantee it will work correctly, but it will get you started.

**conky --help**
```
  12:50:51 ~
         $ conky --help
Usage: conky [OPTION]...
Conky is a system monitor that renders text on desktop or to own transparent
window. Command line options will override configurations defined in config
file.
   -v, --version             version
   -q, --quiet               quiet mode
   -D, --debug               increase debugging output, ie. -DD for more debugging
   -c, --config=FILE         config file to load
   -C, --print-config        print the builtin default config to stdout
                             e.g. 'conky -C > ~/.conkyrc' will create a new default config
   -d, --daemonize           daemonize, fork to background
   -h, --help                help
   -a, --alignment=ALIGNMENT text alignment on screen, {top,bottom,middle}_{left,right,middle}
   -f, --font=FONT           font to use
   -X, --display=DISPLAY     X11 display to use
   -o, --own-window          create own window to draw
   -b, --double-buffer       double buffer (prevents flickering)
   -w, --window-id=WIN_ID    window id to draw
   -x X                      x position
   -y Y                      y position
   -t, --text=TEXT           text to render, remember single quotes, like -t '$uptime'
   -u, --interval=SECS       update interval
   -i COUNT                  number of times to update Conky (and quit)
   -p, --pause=SECS          pause for SECS seconds at startup before doing anything

  12:50:56 ~
         $ 

```
tells is that you can use:
```
conky -c /path_to/conkyfile
```
or if you choose, you can use:
```
conky -c ~/conky/my_first_conky_by_borunco.txt
```
if you want to ... for example my current start-up script:

```
#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
   then
      exec killall conky
   else
      sleep 3
      conky -c ~/Conky/OB_Cal-br &
      conky -c ~/Conky/OB_V_right &
      conky -c ~/Conky/OB_VR2 &
      (sleep 3s && wmctrl -s 2 && conky -c ~/Conky/OB_Win_remind-cal) &
   exit
fi
```

Which is also assigned to my tint2 clock and OpenBox menu.

The first three are "sticky" on all desktops, the last one is not and only runs on my third desktop (wmctrl -s 2)

---

### Post by Borunco on 2012-01-22
```
 	Code:
 	gedit ~/Conky/conkymain 

```
Thank you for all that info.
My stupid question is, when you put that code in terminal, is it so post to make the directory and file in the home. because if it is, I don't get that even when I look at the hidden files.
I get the empty gedit script page with the conkymain name, when i copy/paste a script to it, then hit save. It always tells me that can,t find /home/jose/conkymain.:?:

---

### Post by Sector11 on 2012-01-22
> **Borunco said:**
> ```
 	Code:
 	gedit ~/Conky/conkymain 

```
Thank you for all that info.
My stupid question is, when you put that code in terminal, is it so post to make the directory and file in the home. because if it is, I don't get that even when I look at the hidden files.
I get the empty gedit script page with the conkymain name, when i copy/paste a script to it, then hit save. It always tells me that can,t find /home/jose/conkymain.:?:

OK I see your problem... the directory does not exist.

do this in a terminal (copy and paste from here)
```
mkdir ~/Conky && gedit ~/Conky/conkymain
```

If you do not know somethings questions are not stupid.
Questions should be encouraged.

A question; is Spanish your first language?
S11

---

### Post by Borunco on 2012-01-23
```
A question; is Spanish your first language?
S11
```
Well to answer that would be yes 41 years ago, so I would have to say no, I just suck at typing ;). I tried the code you posted and I was able to save the script, as soon as I have some time today I will continue with it, and get back with my progress.
Thank you for all your help
borunco

---

### Post by Sector11 on 2012-01-23
> **Borunco said:**
> ```
A question; is Spanish your first language?
S11
```
Well to answer that would be yes 41 years ago, so I would have to say no, I just suck at typing ;). I tried the code you posted and I was able to save the script, as soon as I have some time today I will continue with it, and get back with my progress.
Thank you for all your help
borunco

Lets see, 41 years ago - yes, I was bilingual then: English and Profanity!

OK, I'm a four and a half finger typist (thumb on the space bar) tell people what I do:

> I do not make typos, the keys on my keyboard move around to confuse me.

Enjoy!

---

### Post by Borunco on 2012-01-23
Lol, That must be my problem. I knew that there was something weird about my keys.
Thanks

---

### Post by KyleEvans on 2012-05-07
I solve most of the errors by deleting calls for second cpus, the weather from an http address, my battery status, etc but can't solve the last one which says "glibc detected *** conky: double free or corruption" 

I reckon this is a big problem and so I'm best to just give up.  Just wondering though if there is a simple solution.

---

### Post by mmesantos1 on 2012-05-07
Very helpful how to, thank you for posting. :)

---

### Post by Prescilla on 2012-05-08
Just a few questions.
What is the difference between the conky.conf in the /etc/conky/ directory and the .conkyrc to be created on the /home/user/conky/ directory?

Is it recommended to directly modify the conky.conf file?
I created a .conkyrc in my home directory, but when i run conky from the terminal the default conky appeared on the desktop not the created conkyrc.

---

### Post by Sector11 on 2012-06-12
> **Prescilla said:**
> Just a few questions.
What is the difference between the /etc/conky/ in the /etc/conky/ directory and the .conkyrc to be created on the /home/user/conky/ directory?

Is it recommended to directly modify the conky.conf file?
I created a .conkyrc in my home directory, but when i run conky from the terminal the default conky appeared on the desktop not the created conkyrc.

When you install conky it installs /etc/conky/etc/conky/ as it's primary default conky IF ~/.conkyrc does not exist.

You must create ~/.conkyrc yourself and after that a terminal command of:
```
conky
```
will start the new ~/.conkyrc by default.

---

### Post by Sector11 on 2012-06-12
> **KyleEvans said:**
> I solve most of the errors by deleting calls for second cpus, the weather from an http address, my battery status, etc but can't solve the last one which says "glibc detected *** conky: double free or corruption" 

I reckon this is a big problem and so I'm best to just give up.  Just wondering though if there is a simple solution.

I don't use a battery, maybe someone in the [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") can help.  20062 posts in that thread prove it is popular!

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012428](http://ubuntuforums.org/showthread.php?t=2012428)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

