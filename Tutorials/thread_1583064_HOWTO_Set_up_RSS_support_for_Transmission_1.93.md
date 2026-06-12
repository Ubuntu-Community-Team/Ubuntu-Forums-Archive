---
title: "HOWTO: Set up RSS support for Transmission 1.93"
date: 2010-09-27
forum: Tutorials
---

### Post by Vu1kan on 2010-09-27
This howto aims to detail the procedure to automatically parse an rss feed for recurring torrent files, i.e. a weekly television program.  This is accomplished through the use of flexget, cron and transmission. Flexget is a multipurpose automation tool for things like torrents, podcasts, comics, ect.  Cron is a daemon used to schedule tasks to run at a specific time.  Each user has a crontab file, there's also a system crontab.  Transmission is a multi-os bittorent program, it has a fairly plain vanilla interface, but gets the job done.  Step **7** is entirely optional, but provides a handy icon in the notification area whenever torrent files are present in your download directory.


**Background**

I migrated from commercial operating systems several years ago-8.04 Hardy Heron was my first foray into the world of linux. I've been quite happy with almost every feature of Ubuntu, but disappointed with the lack of rss feed support in the default torrent client. So, like any self-respecting geek, I ran to google and searched 'transmission rss ubuntu', which returned 'http://theblawblog.com/use-transmission-cli-to-download-from-rss', however that guide was written some time ago, is using the cli version of transmission, and is for linux in general.  I had to adapt parts of it for my system, and I thought there should be a concise, easy to follow guide that's specifically for Ubuntu.  Now, I do realize that there are torrent clients available in the repositories that support rss feeds, without the need for an external program, but I like transmission, it's easy and it's the default client in 10.04.
[I][B]
Note[/B][/I]:  This howto assumes you're running Ubuntu 10.04, using gnome, and all your packages are updated as of 09/26/10.  If your system is not up-to-date:
```
sudo apt-get update && sudo apt-get upgrade
```[B]

Requirements[/B]
Python 2.5.x or higher, easy_install, FlexGet, transmission 1.93, a source for your rss feeds


**Howto**

**1**. Check your installed version of python
```
python -V
```expected output: Python 2.6.5

**1b**. If your version is below 2.5.x:
```
sudo apt-get install python2.6
```**2**. Get the easy_install tool
```
sudo apt-get install python-setuptools
```note that this step takes a bit of time to resolve.


** 3**. Get FlexGet
**3a1**. For Python 2.5.x:
```
sudo easy_install http://download.flexget.com/unstable/FlexGet-1.0r1445-py2.5.egg
```[B]
3a2[/B]. For Python 2.6.x:
```
sudo easy_install http://download.flexget.com/unstable/FlexGet-1.0r1445-py2.6.egg
```note that this step takes a bit of time to resolve.

**3b**. Verify FlexGet install
```
flexget -V
```expected output: FlexGet 1.0r1445

**3c**. Determine location of executable
```
which flexget
```expected output: /usr/local/bin/flexget
As long as the output matches what's expected, no worries.  If it doesn't match, make a note of the output.  When you get to step **5**. refer to step **5b**., rather than **5a**.


**4**. Create FlexGet config
```
mkdir ~/.flexget/ && touch ~/.flexget/config.yml && gedit ~/.flexget/config.yml
```[B]

4a[/B]. Set up FlexGet config
I found this step to be the trickiest to accomplish. A few notes:
1. Always use 2 spaces, never use tab!!
2. If a text value contains any special characters, (i.e. {}[]%:), it must be enclosed in single quotes,' '
3. If a text value contains a number it must be enclosed in single quotes, ' '
4. All plugins are supposed to be indented with exactly the same number of spaces
5. Plugin order doesn't matter.  Neither does feed order, feeds are executed in a random order unless you use the priority plugin(detailed at flexget's wiki).
6. You cannot list a plugin twice in a single feed.

Copy and paste this sample config with dummy data into the gedit window you opened:
```
feeds:
  TV:
    rss: http://some.rss.website/feed/location/
    series:
      hdtv:
        - show 1
        - show 2
    download: ~/tmp/
```Breakdown of dummy config:
Line 1:
feeds:
is a container which may contain any number of feeds under it.

Line 2:
     TV:
is the actual name of the feed, it must be indented by two spaces since it belongs to feeds:.

Line 3:
         rss: [http://some.rss.website/feed/location/](http://some.rss.website/feed/location/)
is a Plugin used to retrieve a rss feed from the web. It must be indented by four spaces since it belongs to TV:.
(note that is not an actual rss url, you must replace it with your rss feed source)

Line 4:
         series:
is a Plugin used to intelligently parse a list of shows.  It will automatically increment-meaning it will download a torrent for S0XE01, then S0XE02.  It must be indented by four spaces since it belongs to TV:.

Line 5:
      hdtv:
is a group name, and also a quality setting.  It ensures that only torrents tagged with hdtv or better are downloaded.  It must be indented by six spaces since it belongs to series:.

Line 6:
                - show 1
is a placeholder for the name of the show that you want to download a torrent for.  Note the "- ", this must preface each of the shows in the list.  It must be indented by eight spaces since it belongs to hdtv:.

Line 7:
        - show 2
is the same as Line 6, replace 'show 2' with the name of the program you want a torrent for, preserving the "- "...so if you wanted the torrent for south park, you'd change this line to read"        - south park".  It must be indented by eight spaces since it belongs to hdtv:.
To add more shows to the list, simply indent the line by eight spaces, and preface the show name with "- ".

Line 8:
    download: ~/tmp/
is the third and final Plugin used in my sample config, it specifies where to save the parsed .torrent files.  It must be indented by four spaces since it belongs to TV:.

This should be enough to get FlexGet off the ground, however FlexGet supports quite a few more options than I've detailed here, for more information refer to:
[http://flexget.com/wiki/Configuration](http://flexget.com/wiki/Configuration)

**4b**. Save config.yml, then check your syntax:
```
flexget --check
```expected output: Feed 'TV' passed


**5**. Set up cron via terminal(note that step **5. Alternate** details a method to add cron jobs via gui)
If you haven't used cron before, follow these steps:

**5a1**. ```
crontab -e
```It will ask which editor you'd prefer to use, I've written this howto for option 2, nano.  If you choose one of the other options, disregard the keyboard commands I've specified.
**5a2**. add this line:
```
@hourly /usr/local/bin/flexget --cron

```Press ctrl+o, enter, to save changes, ctrl+x to exit.  You must include a newline *after* the final job, or cron will not run the job, and no errors will be reported at edit or runtime.(This is a bug with vixiecron, a fix is in the works; if you're interested [here]("https://bugs.launchpad.net/ubuntu/+source/cron/+bug/118168")'s the bug report @ launchpad)

**5b**. If your output in step **3c**. did not match the expected, modify the line to add to crontab thusly: ```
@hourly [insert output from **3c**.] --cron
```[B]
5c[/B]. check /var/log/syslog after the top of the hour to verify the job is running, you should see a line similar to this one:
Sep 27 07:00:03 %HOST% CRON[2966]: (%USER%) CMD (/usr/local/bin/flexget --cron)
the %HOST% replaced with your hostname; the %USER% replaced with your username.

If you have used cron before, simply add the line from **5a2**. or **5b**.(**3c**) to your existing crontab.


**5. Alternate**
If you'd rather accomplish this step via gui:
**5Aa**. Get the gnome scheduled tasks program:
```
sudo apt-get install gnome-schedule
```**5Ab**. Applications>System Tools>Scheduled tasks
**5Ac**. Click 'New'
**5Ad**. Click 'A task that launches recurrently'.
**5Ae**. Put whatever you like in the 'Description' box.
**5Af**. Put the code from **5a2**. ("/usr/local/bin/flexget --cron") or **5b**.(**3c**) ("[insert output from **3c**.] --cron")in the 'Command' box.
**5Ag**. Click 'Add'.

Your task should look like this:
[IMG]http://i54.tinypic.com/4ryjk0.png[/IMG]


**6**. Set up transmission
**6a**. Edit>Preferences>Torrents tab
Check box for 'Automatically add torrents from:', point towards ~/tmp/
**6b**. Check box for 'Start when added'
**6c**. Uncheck box for 'Show options dialog'
Optional, but recommended:
**6d**. Check box for 'Seed torrent until its ratio reaches:', set to 1.00

Your Transmission Preferences should look like this:
[IMG]http://i54.tinypic.com/15cf4i0.png[/IMG]


**7**. Optional(but handy) zenity notification for new torrents
Note: for this to function correctly, you must have transmission set to "Move .torrent file to the trash"(which I've forgotten to include in my screenshot above XD )
**7a1**. CLI Method: Open a terminal
```
crontab -e
```**7a2**. Add this line to your crontab(replacing %USER% with your username):
```
1 * * * * ! pgrep zenity && ls /home/%USER%/tmp/* && DISPLAY=:0 zenity --notification --text="New Torrents"
```Press ctrl+o, enter, to save changes, ctrl+x to exit.  You must include a newline *after* the final job.

**7b**. GUI Method: Open gnome scheduled tasks(Applications>System Tools>Scheduled tasks)
**7b1**. Click 'New'
**7b2**. Click 'A task that launches recurrently'.
**7b3**. Put whatever you like in the 'Description' box.
**7b4**. Put the following code in the 'Command' box:
```
! pgrep zenity && ls /home/%USER%/tmp/* && DISPLAY=:0 zenity --notification --text="New Torrents"
```**7b5**. Click the 'Advanced' bullet point, input a 1 in the 'Minute' box.
**7b6**. Click 'Add'.

**Explanation**:
"! pgrep zenity" determines whether an instance of zenity is already in your tray; "ls /home/%USER%/tmp/*" checks your incoming torrent folder to see if any files exist there; "DISPLAY=:0" sets an environment variable that cron ignores; "zenity..." generates the tray icon itself.
As an alternate to launching a zenity notification icon, you could just launch transmission itself.  If you'd like this, modify the code in step **7a2**. or **7b4**. as follows:
Replace "zenity" with "transmission", Replace "DISPLAY=:0 zenity --notification --text="New Torrents"" with "/usr/bin/transmission".  Your modified line would look like this:
```
! pgrep transmission && ls /home/%USER%/tmp/* && /usr/bin/transmission
```
Your task should look like this:
[IMG]http://i54.tinypic.com/2q9xe9w.png[/IMG]


** Procedure to revert the changes in this Howto**

Step **1**.
No revert required.

Step **2**.
```
sudo apt-get remove python-setuptools
```Step **3**.
I'm not sure how to revert this, but i would imagine that you only need to delete the output of **3c**.
```
sudo rm /usr/local/bin/flexget
```Step **4**.
```
sudo rm -r ~/.flexget/
```Step **5**.
```
sudo crontab -e
```delete the "@hourly /usr/local/bin/flexget" line, ctrl+o, enter to save, ctrl+x to exit.

Step **5A**. 
```
sudo apt-get remove gnome-schedule
```Step **6**.
Uncheck all boxes you'd checked in this step.

Step **7**.
```
sudo crontab -e
```delete the "1 * * * *! pgrep zenity && ls /home/%USER%/tmp/* && DISPLAY=:0 zenity --notification --text="New Torrents" " line, ctrl+o, enter to save, ctrl+x to exit.

Sources:
[http://theblawblog.com/use-transmission-cli-to-download-from-rss](http://theblawblog.com/use-transmission-cli-to-download-from-rss)
[https://help.ubuntu.com/community/CronHowto#Enable%20User%20Level%20Cron](https://help.ubuntu.com/community/CronHowto#Enable%20User%20Level%20Cron)
[https://bugs.launchpad.net/ubuntu/+source/cron/+bug/118168](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/118168)
[http://flexget.com/wiki/Configuration](http://flexget.com/wiki/Configuration)
And a resounding thank you to the folks in #bash on irc.freenode.net, step 7 had eluded me for about three months...they solved it in two hours.

---

### Post by fooey on 2010-09-30
aww..nice post. i tried to get this working with flex a while back, but i didn't have any luck. going to try your write up now. thanks! :P

---

### Post by Vu1kan on 2010-10-30
Well, one month and 500+ views later, I've a few questions for anybody that feels like responding.  Firstly, is step one even required in a "fresh out of the box" lucid install?  What parts of my guide are difficult to follow, and how would you recommend revising them?  Has anybody come across another, simpler method to accomplish broadcatching using transmission?  And lastly, how about reporting any successes/failures?  If you're unable to get flexget working, I'm perfectly willing to try to help hammer out the problem.

p.s. #2 google result when searching 'transmission rss ubuntu' woot!

---

### Post by erissiva on 2010-11-02
It's fantastic! I just followed it, and had no trouble adding a couple things I needed to get right. There was a crazy error with permissions of the flexget folder, however. Wasn't writable.

I would love to find out if there was some way to get these torrents added to Transmission with no options dialog. Because I would still love to use the options dialog for things I add myself...but not for the things automatically added by FlexGet. So I have it disabled right now so that it works for FlexGet, but still want to have it pop up for me. :(
As far as I know, there is no way to do this - since Transmission relies on the same options for both the folder watching AND manual adding.

---

### Post by Vu1kan on 2010-11-02
@erissiva: I may have a workaround concerning the options dialog: If you're comfortable w/cli, you could get the command line version of transmission(it's in the repo's), and have your FlexGet output folder monitored by that...I'm pretty sure this method wouldn't add your flexgot(hehe) torrents to the gui of transmission.  Otherwise, I seem to recall that transmission will start downloading a file whether or not the options dialog is open...I can't be sure though, my options still match the screenshot i included in the howto.
Also, I wonder if your error with the folder was due to the fact that the directory was created and accessed with essentially the same command?  When I was muddling through the somewhat dated guide I based this on, I created the directory with one command, made the .yml with a second, and opened my gedit with a third...I'll install a lucid virtual machine tomorrow and do some testing.

---

### Post by proteusmoteus on 2010-11-09
@[erissiva]("http://ubuntuforums.org/member.php?u=138089")
The "crazy error with permissions of the flexget folder" is bc step 4 shouldn't be using sudo.

Running that step w/ the "sudo"s creates a directory and config file owned by root. It is a personal config file that is being created and thus should be owned by whatever account you login as.

Corrected line would be:

mkdir ~/.flexget/ && touch ~/.flexget/config.yml && gedit ~/.flexget/config.yml

---

### Post by Vu1kan on 2010-11-09
I didn't realize the command shouldn't be sudo'ed...as i mentioned, i did that step in three parts...i've corrected the howto, thanks for pointing that out, proteusmoteus.

---

### Post by jstapels on 2010-11-16
You might want to add a step that runs "flexget --test" to verify the config.yml file. Otherwise, great little guide, thanks.

---

### Post by Vu1kan on 2010-11-16
@jstapels see step 4b..."flexget --check" will go through the .yml file and report any irregularities...whereas "flexget --test" just does a 'dry run', in other words, it runs flexget, but doesn't write any fetched torrent files to disk.

---

### Post by Vu1kan on 2011-01-09
Three months and 1500+ views later...wow, theres a disproportionate amount of replies to views ratio; I'm going to assume it's because people are looking at the howto and determining that it's not for them, or they're following the howto and not having problems.  Either way, it's all groovy.
My post this evening is to denote what I hope will be the final large update to the howto.  I've accomplished everything I set out to do, and until the zenity developers implement right-click actions for notification icons, I don't foresee any major changes.
Also, I wanted to let people know that I'm subscribed to the thread, and still just as curious for answers to my previous questions.  As well as still willing to provide support, if anybody needs it.  I would prefer you just make a new reply to the thread, so that we could help other people that may be experiencing your issues.

---

### Post by sjhupp on 2011-01-19
Just came across this, and mildly excited someone else is using transmission with flexget!!  Nice guide too.
I have issues with transmission, and flexget integration :confused:

I had flexget working with deluged (daemon) on my headless 10.04 64bit server, and it (flexget) passed torrents directly to deluge, which would download them, and nicely sort them into folders (say TV/show/season/episode.avi). Wonderful.
BUT, deluged was painfully slow downloading (maybe 200KB if I was lucky, usually much less), even after following wiki and posts to optimise it, so I wanted to try transmission.  I then installed transmission-daemon and it chugs down at my capped 1500KB rate smoothly by default! So really want to stick to it, but I have issues:
- cannot use the transmissionrpc plugin for flexget. I easy_install it, seems fine, but always get 'unknown plugin' for it. Tried 5 different ways to config it from wiki, cookbook and other user posts, which all supposedly work.  Wrong path?
- transmission won't move completed downloads to the download folder. I set it up to use temp folder, it does, then leave 100% files there, even after seeding to ratio. Enabled in config. Have seen a commend to remove them, but need to know how to work it in nicely.
- some downloaded files complete and then just pause (???)
- transmission won't remove torrent files from watch directory  if just put in there by nautilus, or flexget etc.  Will remove if added from the GUI though (I have a basic gnome desktop on my server to VNC in to). Config error?
- not sure if removewhendone is an option for 1.93. The below tvnamer script can move files out, but they're left in the GUI to be manually deleted. That's crap.

Anyway, and advice on any issue would be much appreciated!!

Also, recommend looking at tvnamer as an addon to rename files. Works a treat! And cam copy to another drive also, and file in appropriate structure. Not perfect script yet, but damn nice start. I used webmin to set up cron jobs for flexget & tvnamer regularly.

Please help me get flexget & transmission working properly!! :P
Ta.

---

### Post by paranoidi on 2011-01-20
> **sjhupp said:**
> 
I have issues with transmission, and flexget integration :confused:

- cannot use the transmissionrpc plugin for flexget. I easy_install it, seems fine, but always get 'unknown plugin' for it. Tried 5 different ways to config it from wiki, cookbook and other user posts, which all supposedly work.  Wrong path?


The "Unknown plugin" error was from FlexGet? Maybe you tried to use transmission plugin with old name (transmissionrpc). It was renamed from "transmissionrpc" to "transmission" to better match naming convention. It quite possible that the old name is still used in some places ...

---

### Post by sjhupp on 2011-01-20
Yep, flexget error.  I did try both transmission and transmissionrpc, but neither work for me.
May have to go back to deluge, and try and work out how to get reasonable speeds with it. :?

---

### Post by sjhupp on 2011-01-20
PC had a problem and triple posted, sorry

---

### Post by sjhupp on 2011-01-20
PC had a problem and triple posted, sorry

---

### Post by paranoidi on 2011-01-21
> **sjhupp said:**
> Yep, flexget error.  I did try both transmission and transmissionrpc, but neither work for me.
May have to go back to deluge, and try and work out how to get reasonable speeds with it. :?

Sounds a bit odd. We're happy to help you to resolve the issue in IRC (freenode #FlexGet) or alternatively you can create a help ticket in [http://flexget.com](http://flexget.com).

---

### Post by sjhupp on 2011-01-24
> **paranoidi said:**
> Sounds a bit odd. We're happy to help you to resolve the issue in IRC (freenode #FlexGet) or alternatively you can create a help ticket in [http://flexget.com](http://flexget.com).

Thanks paranoidi, your help was much appreciated, very happy to have things appearing to work now! :D

Quick update for anyone reading:

Plugin seems happy now after I easy_install --upgrade flexget to the latest version (r1889) and deleted the database file.  I will set a few transmission options and try on some files that match, and add any followup relevant.
I love flexget!

---

### Post by xhaos on 2012-03-08
First of all, let me thank you for you excellent how to:popcorn:

only thing missing for me at least is a final-useful version of the config.yml so I'm going to post one:

```

presets:
  tv:
    download: yes
    exists_series: /...path.../Series/
    series:
      hdtv:
      - Pioneer One
      - Foo1
      - Foo2
      720p:
      - Foo3
      - Foo4

    set:
      path: /...path.../Series/{{series_name}}/
    transmission:
      host: localhost
      port: 9091
      username: xxxxxx
      password: xxxxxx
      addpaused: No

feeds:
  ezRSS:
    rss: http://ezrss.it/feed/
    preset: tv

  BT-Chat:
    rss: http://rss.bt-chat.com/?group=3&cat=9/
    preset: tv

  The Pirate Bay - TV shows:
    rss: http://rss.thepiratebay.se/205
    preset: tv

```

Just copy - paste this code to your config.yml and mind while you edit not to put any TABs and keep double spaces.

Keep on rocking!  :guitar:

---

### Post by Fredrik_b on 2012-08-17
xhaos, grate I have 2 questions

a) will it or is it possible to de episodes to series_season catalog?

b) Have anyone tried using "thetvdb_favorites" instead of Series?

Edit, I seam to have a more basic problem. GetRss is saying that it is downloading but no files get pased to transmission.

---

