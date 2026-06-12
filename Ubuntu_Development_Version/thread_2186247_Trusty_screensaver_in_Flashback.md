---
title: "Trusty screensaver in Flashback"
date: 2013-11-06
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-11-06
I'm surprised that there are not more people wanting to login to Gnome Flashback and have a working screensaver. You cannot unistall gnome-screensaver because it is a dependency for gnome-session-flashback.
This was the common practice after the initial install of other Ubuntu versions: uninstall gnome-screensaver, install xscreensaver and add it to your startup applications.

This problem was introduced with Saucy and persists in Trusty.

If you want a working screensaver in flashback add your name to this [_bug_]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074").

Here is what you need in Trusty:
1) Add this to a text file:
[PHP]#!/bin/bash
sleep 180
killall gnome-screensaver [/PHP]
2) Then save it in your home directory as **/home/cavsfan/killscreensaver.sh** (of course substituting your username with cavsfan).
3) Enter **sudo chmod +x /home/cavsfan/killscreensaver.sh** to make it executable.
4) Enter **sudo chown root:root /home/cavsfan/killscreensaver.sh** to make it owned by root.
5) Add **/home/cavsfan/killscreensaver.sh** to your startup programs.

6) Add this to another text file:
[PHP]#!/bin/bash
sleep 240
xscreensaver -no-splash [/PHP]
7) Then save it in your home directory as **/home/cavsfan/xscreensaver-start.sh** (of course substituting your username with cavsfan).
* this script must not be owned by root or the screensaver will not start.
8) Add **/home/cavsfan/xscreensaver-start.sh** to your startup programs.
9) Make gnome-screensaver unexecutable with this command **sudo chmod -x /usr/bin/gnome-screensaver** just to make double sure.

I've tried many combinations and many did not work but the above appears to work OK.
I even entered sudo killall gnome-screensaver in terminal and it killed it but it _re-spawned_ back to life somehow.
It is set to kill gnome-screensaver after 3 minutes because it doesn't start for a while and anything less will not work.
Then it starts xscreensaver after 4 minutes and it cannot be started before gnome-screensaver is killed or it will not start.
I logged out and back in and this worked. Haven't tried rebooting but, that should do.

---

### Post by Cavsfan on 2014-01-02
Received an email this morning that this dependency will be fixed and will be in the next upload. :guitar:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074)

---

### Post by Cavsfan on 2014-01-02
Now I noticed that the email was about Saucy. Have to wait and see if it gets to Trusty but I imagine it will.

---

### Post by kansasnoob on 2014-01-02
I subscribed, me too'ed, and added the trusty tag along with a comment.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074/comments/7](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074/comments/7)

---

### Post by Hazzabin on 2014-01-02
There probably would be more people trying, if they are like me I still have NOT been successful in getting 'Flashback' with or without whatever

---

### Post by kansasnoob on 2014-01-02
> **Hazzabin said:**
> There probably would be more people trying, if they are like me I still have NOT been successful in getting 'Flashback' with or without whatever

But you're talking about Flashback w/compiz:

[http://ubuntuforums.org/showthread.php?t=2184682&page=23&p=12887102#post12887102](http://ubuntuforums.org/showthread.php?t=2184682&page=23&p=12887102#post12887102)

It's been discussed that we should drop "flashback" for compiz although no decision has been made.

What's needed by Edubuntu for it's LTSP installs is only flashback w/metacity ;)

---

### Post by Cavsfan on 2014-01-02
> **kansasnoob said:**
> I subscribed, me too'ed, and added the trusty tag along with a comment.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074/comments/7](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074/comments/7)

I got into Saucy and the update wasn't there. Guess maybe tomorrow. I had added that it affects Trusty already but didn't tag it so that is good.
I had also added my workaround. A script that killed gnome-screensaver which let Xscreensaver work. If gnome-screensaver was still running Xscreensaver could not work.
Xscreensaver is the only one I am aware of that is being kept up to date and is also in the regular repositories. I'm happy with it as there are many choices. 
I have mine set to Piecewise which I like. ;)

> **Hazzabin said:**
> There probably would be more people trying, if they are like me I still have NOT been successful in getting 'Flashback' with or without whatever
I have only been in Lunity long enough to install the necessary components gnome-session-flashback needs and then I got into Flashback.
Only after I heard Kansasnoob mention flashback with compiz and flashback with metacity did I notice they had changed.

I only use flashback with compiz and it's been running smooth as silk for a long time now. 

I am working from an ISO that was created a while back.

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Nov 24 10:51

```

About the only thing that works in the indicator-applet-complete (the top right button on the top panel) is suspend, but it works very well. :)
I have Cairo Dock running along with the cube and the whole nine yards. Even got Emerald window decorator installed.

Have to use Cairo Dock to logout, restart, etc. but I don't mind. It's just like Saucy was/is.

[[IMG]http://en.zimagez.com/miniature/1screenshotfrom2014-01-02165516.png[/IMG]]("http://en.zimagez.com/zimage/1screenshotfrom2014-01-02165516.php")

---

### Post by PJs Ronin on 2014-01-02
> **Hazzabin said:**
> There probably would be more people trying, if they are like me I still have NOT been successful in getting 'Flashback' with or without whatever

I can 'me too' this comment.   I can't get Gnome Flashback working with either compiz or metacity so the discussion about screensavers is, for me, moot.   I do have Gnome Shell working so I may fiddle with the screensaver in that and see how I go.

---

### Post by kansasnoob on 2014-01-02
> **Cavsfan said:**
> I got into Saucy and the update wasn't there. Guess maybe tomorrow. I had added that it affects Trusty already but didn't tag it so that is good.
I had also added my workaround. A script that killed gnome-screensaver which let Xscreensaver work. If gnome-screensaver was still running Xscreensaver could not work.
Xscreensaver is the only one I am aware of that is being kept up to date and is also in the regular repositories. I'm happy with it as there are many choices. 
I have mine set to Piecewise which I like. ;)


I have only been in **[COLOR="#FF0000"]Lunity[/COLOR]** long enough to install the necessary components gnome-session-flashback needs and then I got into Flashback.
Only after I heard Kansasnoob mention flashback with compiz and flashback with metacity did I notice they had changed.

I only use flashback with compiz and it's been running smooth as silk for a long time now. 

I am working from an ISO that was created a while back.

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Nov 24 10:51

```

About the only thing that works in the indicator-applet-complete (the top right button on the top panel) is suspend, but it works very well. :)
I have Cairo Dock running along with the cube and the whole nine yards. Even got Emerald window decorator installed.

Have to use Cairo Dock to logout, restart, etc. but I don't mind. It's just like Saucy was/is.

[[IMG]http://en.zimagez.com/miniature/1screenshotfrom2014-01-02165516.png[/IMG]]("http://en.zimagez.com/zimage/1screenshotfrom2014-01-02165516.php")

You really shouldn't expect anyone to take you serious using blurbs like highlighted above.

Of course you won't see the upcoming change until it's marked "fix released"!

Patience is a virtue ;)

---

### Post by kansasnoob on 2014-01-02
> **PJs Ronin said:**
> I can 'me too' this comment.   I can't get Gnome Flashback working with either compiz or metacity so the discussion about screensavers is, for me, moot.   I do have Gnome Shell working so I may fiddle with the screensaver in that and see how I go.

I've had very little trouble with Flashback w/Metacity so you must be doing something wrong.

---

### Post by PJs Ronin on 2014-01-02
> **kansasnoob said:**
> I've had very little trouble with Flashback w/Metacity so you must be doing something wrong.
Agreed.   But when you're as noob as I it is difficult to know what you're doing wrong.   Nonetheless, I shall persevere.

---

### Post by kansasnoob on 2014-01-03
> **PJs Ronin said:**
> Agreed.   But when you're as noob as I it is difficult to know what you're doing wrong.   Nonetheless, I shall persevere.

I'm having to learn some new tricks myself:

[http://ubuntuforums.org/showthread.php?t=2184682&page=23&p=12890035#post12890035](http://ubuntuforums.org/showthread.php?t=2184682&page=23&p=12890035#post12890035)

---

### Post by Cavsfan on 2014-01-03
> **PJs Ronin said:**
> I can 'me too' this comment.   I can't get Gnome Flashback working with either compiz or metacity so the discussion about screensavers is, for me, moot.   I do have Gnome Shell working so I may fiddle with the screensaver in that and see how I go.

I guess messing with screensavers would be moot for you as well. The bug is about Flashback when installed has a dependency of gnome-screensaver. 
So as in previous Ubuntu versions many places recommend as one of the first things you do is to purge gnome-screensaver, 
which is not actually a screensaver and is no longer maintained and install Xscreensaver, which is a nice screensaver with many options and is being maintained.
The ability to use Flashback and have a working screensaver was taken away with Saucy and has been carried on into Trusty. 

So, when I seen that it is going to be fixed I was thrilled. 

> **kansasnoob said:**
> You really shouldn't expect anyone to take you serious using blurbs like highlighted above.

Of course you won't see the upcoming change until it's marked "fix released"!

Patience is a virtue ;)

My bad. Ventrical used Lunity one time referring to Unity and it just stuck. I kind of like that term. ;)

BTW, for all of you who do not use Cairo Dock, how do you get the notification when a system restart is required after a software update?
My logout icon in Cairo Dock puts out a message that a system restart is required.

Usually it's after I see update-initramfs but not always. Sometimes a restart is required and sometimes it is not. So, I rely on Cairo Dock to tell me.

---

### Post by kansasnoob on 2014-01-03
> **Cavsfan said:**
> I guess messing with screensavers would be moot for you as well. The bug is about Flashback when installed has a dependency of gnome-screensaver. 
So as in previous Ubuntu versions many places recommend as one of the first things you do is to purge gnome-screensaver, 
which is not actually a screensaver and is no longer maintained and install Xscreensaver, which is a nice screensaver with many options and is being maintained.
The ability to use Flashback and have a working screensaver was taken away with Saucy and has been carried on into Trusty. 

So, when I seen that it is going to be fixed I was thrilled. 



My bad. Ventrical used Lunity one time referring to Unity and it just stuck. I kind of like that term. ;)

BTW, for all of you who do not use Cairo Dock, how do you get the notification when a system restart is required after a software update?
My logout icon in Cairo Dock puts out a message that a system restart is required.

Usually it's after I see update-initramfs but not always. Sometimes a restart is required and sometimes it is not. So, I rely on Cairo Dock to tell me.

AFAIK update-notifications and restart-notifications are handled the same as Saucy:

[http://ubuntuforums.org/attachment.php?attachmentid=248080&d=1385371191](http://ubuntuforums.org/attachment.php?attachmentid=248080&d=1385371191)

[http://ubuntuforums.org/attachment.php?attachmentid=248081&d=1385371191](http://ubuntuforums.org/attachment.php?attachmentid=248081&d=1385371191)

But I can't be certain because I've been using synaptic which I think breaks that.

---

### Post by cariboo on 2014-01-04
> **kansasnoob said:**
> AFAIK update-notifications and restart-notifications are handled the same as Saucy:

But I can't be certain because I've been using synaptic which I think breaks that.

Synaptic does break the notification no matter what DE you are using. On the other hand, if you are using synaptic, instead of the Software Centre, or Software Updater, you are more than likely aware of when your system needs a restart.

---

### Post by Cavsfan on 2014-01-04
I like how Cairo Dock does the job of notifying me when I need to restart as it is always very clear. :)

Even after you see the words pop up saying you must restart after the updates, you can hover your mouse over the logout icon in Cairo Dock and it will tell you to restart.
No wondering needed.

---

### Post by QDR06VV9 on 2014-01-04
> **Cavsfan said:**
> I like how Cairo Dock does the job of notifying me when I need to restart as it is always very clear. :)

I also find that helpful, But I really dislike the notifications about newly installed apps:mad:(Open this new application)
But I must like the dock because I keep using it.;) Just my 2 cents worth.LOL

---

### Post by Hazzabin on 2014-01-04
> **runrickus said:**
> I also find that helpful, But I really dislike the notifications about newly installed apps:mad:(Open this new application)
But I must like the dock because I keep using it.;) Just my 2 cents worth.LOL


Ditto from me too, and yes that notification thingie can get quite annoying

---

### Post by Cavsfan on 2014-01-04
> **runrickus said:**
> I also find that helpful, But I really dislike the notifications about newly installed apps:mad:(Open this new application)
But I must like the dock because I keep using it.;) Just my 2 cents worth.LOL

> **Hazzabin said:**
> Ditto from me too, and yes that notification thingie can get quite annoying

That is indeed annoying especially when you install a bunch of new updates. It asks so many times do you want to open this, blah blah blah? 
I just let it go until it's finished updating and then click the x to make it go away.
I searched for a way to disable these notifications but could not find anything worthwhile.

That would be nice to turn off those notifications.

I seen something about using **notify-send** to do it but, didn't see a clear explanation of how.

---

### Post by jerrylamos on 2014-01-04
To really "save" my screen it goes to black after the set time period.  If you have something running, you're not "saving" the screen.

Now if you just want to have a pretty picture there should be a 14.04 ability to do that after a set time period of inactivity.  Displaying something might be pleasing but it's not saving the screen.

Does the "inactivity" just mean no keyboard activity?

---

### Post by Cavsfan on 2014-01-05
> **jerrylamos said:**
> To really "save" my screen it goes to black after the set time period.  If you have something running, you're not "saving" the screen.

Now if you just want to have a pretty picture there should be a 14.04 ability to do that after a set time period of inactivity.  Displaying something might be pleasing but it's not saving the screen.

Does the "inactivity" just mean no keyboard activity?

Not really sure what you are asking. Read the bug mentioned in the first post. It should explain what the whole issue is about.

Inactivity would mean no keyboard/mouse activity for a certain period of time. The gnome-session-screensaver that is a dependency of gnome-session-flashback is not a screensaver but a lock that does not totally black out the screen. It just shows a black screen with date/time and some other stuff displayed at the top of the screen forever till the cows come home.

---

### Post by Cavsfan on 2014-01-10
If anyone is interested in having xscreensaver working with Trusty, I just updated the 1st post with what I found will work.
I had been battling this for a while and could not get it to work but all is good now. ;)

---

### Post by kansasnoob on 2014-01-10
> **Cavsfan said:**
> If anyone is interested in having xscreensaver working with Trusty, I just updated the 1st post with what I found will work.
I had been battling this for a while and could not get it to work but all is good now. ;)

I'm interested :D

---

### Post by Cavsfan on 2014-01-11
> **kansasnoob said:**
> I'm interested :D

Good deal! :D I thought you said you didn't like screensavers.

One more thing I forgot to add was I made gnome-screensaver unexecutable with this command **sudo chmod -x /usr/bin/gnome-screensaver** just to make double sure because it respawns on it's own.
This might make the 1st script moot but, I'm leaving it in there because I want to make double sure that gnome-screensaver is indeed not alive when xscreensaver starts. :)

I'll add this to the first post.

---

### Post by Cavsfan on 2014-01-11
Forgot to mention that upon bootup this morning this method (in post 1) did work. If you boot up and do not touch any key or move the mouse for 10 minutes xscreensaver will kick in.

---

### Post by kansasnoob on 2014-01-11
> **Cavsfan said:**
> Good deal! :D I thought you said you didn't like screensavers.

One more thing I forgot to add was I made gnome-screensaver unexecutable with this command **sudo chmod -x /usr/bin/gnome-screensaver** just to make double sure because it respawns on it's own.
This might make the 1st script moot but, I'm leaving it in there because I want to make double sure that gnome-screensaver is indeed not alive when xscreensaver starts. :)

I'll add this to the first post.

Well, I maintain an ever larger number of computers and some of the most recent users still have old CRT monitors :(

I'll certainly be trying to get them upgraded but I'm not sitting on a gold mine ;)

So it should be easy to switch from gnome-screensaver to xscreensaver if the user wishes to.

---

### Post by Cavsfan on 2014-01-11
> **kansasnoob said:**
> Well, I maintain an ever larger number of computers and some of the most recent users still have old CRT monitors :(

I'll certainly be trying to get them upgraded but I'm not sitting on a gold mine ;)

So it should be easy to switch from gnome-screensaver to xscreensaver if the user wishes to.

Good deal. I have an LCD monitor and I still like a good screensaver to kick in after say 10 minutes. ;)

---

### Post by Cavsfan on 2014-01-11
> **filter1102 said:**
> [COLOR=#000000]Received an email  [/COLOR]
[https://bugs.launchpad.net/ubuntu/+s...l/+bug/1199074]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1199074")

Thanks but, that email was previously noted. We're waiting on one that says "final release" I believe. But, that will be good when it happens! :)

---

### Post by muktupavels on 2014-01-11
There is new gnome-panel version which will allow to remove gnome-screensaver without removing gnome-flashback-session, but for now I would suggest to keep it installed. New version is missing one more fix, without that fix gnome flashback session will fail to start without gnome-screensaver.

---

### Post by Cavsfan on 2014-01-11
> **albertsmuktupavels said:**
> There is new gnome-panel version which will allow to remove gnome-screensaver without removing gnome-flashback-session, but for now I would suggest to keep it installed. New version is missing one more fix, without that fix gnome flashback session will fail to start without gnome-screensaver.

Thanks for the reply Alberts! I seen that in the change log that gnome-screensaver was moved to from Depends to Recommends. Sweet! :)

But, like you mention I'll leave it installed until I hear back that is OK to uninstall. And I'll leave my work around in place.

---

### Post by kansasnoob on 2014-01-12
> **Cavsfan said:**
> Thanks for the reply Albert! I seen that in the change log that gnome-screensaver was moved to from Depends to Recommends. Sweet! :)

But, like you mention I'll leave it installed until I hear back that is OK to uninstall. And I'll leave my work around in place.

I see Alberts beat me to the punch but here's the changelog:

> gnome-panel (1:3.8.0-1ubuntu2) trusty; urgency=low

  [ Dmitry Shachnev ]
  * Backport upstream patches to:
    - fix building with gweather 3.9.2 and newer versions.
    - fix problem when panel size was not updated.
  * Drop obsolete breaks on historic versions of gnome-session and
    gnome-power-manager.
  * Drop ‘with’ word from sessions names to make them shorter.

 [B] [ Alberts Muktup&#257;vels ]
  * Move gnome-screensaver from Depends to Recommends.
[/B]
 -- Dmitry Shachnev <mitya57@ubuntu.com>  Sat, 11 Jan 2014 14:56:20 +0400


Thanks Alberts :D

---

### Post by Cavsfan on 2014-02-07
> **albertsmuktupavels said:**
> There is new gnome-panel version which will allow to remove gnome-screensaver without removing gnome-flashback-session, but for now I would suggest to keep it installed. New version is missing one more fix, without that fix gnome flashback session will fail to start without gnome-screensaver.

Alberts, I guess this still has not been resolved? Do you think it will be?

Thanks

---

### Post by muktupavels on 2014-02-07
It should be fixed now.

[https://launchpad.net/ubuntu/+source/gnome-panel/1:3.8.0-1ubuntu3](https://launchpad.net/ubuntu/+source/gnome-panel/1:3.8.0-1ubuntu3)

---

### Post by Cavsfan on 2014-02-07
> **albertsmuktupavels said:**
> It should be fixed now.

[https://launchpad.net/ubuntu/+source/gnome-panel/1:3.8.0-1ubuntu3](https://launchpad.net/ubuntu/+source/gnome-panel/1:3.8.0-1ubuntu3)

Fantastic! I think I seen these in the updates recently. I'll resolve this thread and get rid of gnome-screensaver finally.

Thank you for the update. :)

---

### Post by Cavsfan on 2014-02-07
I don't think this is resolved just yet.

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge gnome-screensaver
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome* gnome-core* gnome-screensaver*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 535 kB disk space will be freed.
Do you want to continue? [Y/n]
```

---

### Post by kansasnoob on 2014-02-07
> **Cavsfan said:**
> I don't think this is resolved just yet.

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge gnome-screensaver
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome* gnome-core* gnome-screensaver*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 535 kB disk space will be freed.
Do you want to continue? [Y/n]
```

I'm surprised the meta-package 'gnome' is even installed and even 'gnome-core' is part of the upstream 'gnome' meta-package:

> This is the GNOME Desktop environment, an intuitive and attractive
desktop, with extra components.

This meta-package depends on the standard distribution of the GNOME
desktop environment, plus a complete range of plugins and other
applications integrating with GNOME and Debian, providing the best
possible environment to date.

> These are the core components of the GNOME Desktop environment, an
intuitive and attractive desktop.

This meta-package depends on a basic set of programs, including a file
manager, an image viewer, a web browser, a video player and other
tools.

It contains the official “core” modules of the GNOME desktop.

---

### Post by muktupavels on 2014-02-08
> **Cavsfan said:**
> I don't think this is resolved just yet.

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge gnome-screensaver
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome* gnome-core* gnome-screensaver*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 535 kB disk space will be freed.
Do you want to continue? [Y/n]
```

gnome-flashback-session is not going to be removed, so problem is solved. You can use flashback session without gnome-screensaver if you want so. :)

---

### Post by Cavsfan on 2014-02-08
Thanks! It worked well. I'm almost embarrassed to say that I did not know that a meta-package is like a transitional package. :redface:
I guess if you don't learn something fairly often you aren't doing anything :)

I removed the kill screensaver script and changed the startup command for xscreensaver to the usual **xscreensaver -no-splash** and all is well.

This is resolved. :popcorn:

---

### Post by Cavsfan on 2014-02-08
This doesn't seem quite right. When checking for updates after I removed gnome-screensaver I get this:

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  argyll browser-plugin-gnash caribou caribou-antler dconf-tools finger fonts-cantarell gdebi gdebi-core gir1.2-gtop-2.0 gir1.2-rest-0.7 gir1.2-tracker-0.16 gir1.2-zpj-0.0 gnash gnash-common gnome-backgrounds
  gnome-color-manager gnome-dictionary gnome-documents gnome-games gnome-icon-theme-extras gnome-nettool gnome-online-accounts gnome-packagekit gnome-packagekit-data gnome-packagekit-session
  gnome-shell-extensions gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gtk2-engines hamster-applet hamster-indicator inkscape libbonoboui2-0 libbonoboui2-common libboost-program-options1.54.0
  libboost-thread1.54.0 libcaribou-gtk-module libcaribou-gtk3-module libcdaudio1 libcolord-gtk1 libdirac-encoder0 libdiscid0 libdmapsharing-3.0-2 libgdict-1.0-6 libgdict-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgsf-1-114 libgsf-1-common libgsl0ldbl libgstreamer-plugins-bad0.10-0 libgtkmm-2.4-1c2a libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libicc2 libimdi0
  libiptcdata0 libjemalloc1 librygel-core-2.0-1 librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1 libslv2-9 libsofia-sip-ua-glib3 libsofia-sip-ua0 libtracker-extract-0.16-0
  libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libzapojit-0.0-0 libzvbi-common libzvbi0 perlmagick python-appindicator python-gnome2 python-pyatspi python-pyorbit python-uniconvertor python-wnck
  python3-mako python3-markupsafe rhythmbox-plugins rygel rygel-playbin rygel-preferences sound-juicer telepathy-rakia tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils unoconv
Use 'apt-get autoremove' to remove them.

```

Maybe this is not fixed. Did any one test this by removing gnome-screensaver?

---

### Post by mc4man on 2014-02-08
Works fine on an Ubuntu + gnome-panel install.
All of those packages listed were automatically installed when *you* installed those 2 metapackages. Now that gnome & gnome-core have been removed any of those automatically installed packages that don't have anything else depending on are marked for autoremove.

If you actually use any of them then mark them as manually installed & they won't show in the autoremove list..

---

### Post by Cavsfan on 2014-02-09
> **mc4man said:**
> Works fine on an Ubuntu + gnome-panel install.
All of those packages listed were automatically installed when *you* installed those 2 metapackages. Now that gnome & gnome-core have been removed any of those automatically installed packages that don't have anything else depending on are marked for autoremove.

If you actually use any of them then mark them as manually installed & they won't show in the autoremove list..

*rolls up sleeves* *prepares for the plunge* *here we gooooooo*

Thanks for the information, I'll see if I can make this work.

---

### Post by Cavsfan on 2014-02-09
@mc4man, I saved a list of what was removed and just let it happen. Took out the stuff I had added and put it back like it should be normally like **xscreensaver -no-splash** in startup commands.
Then rebooted. Everything seems to be good to go. I do recall a bunch of stuff being installed when I installed something gnome* 

Man, I guess you can't learn enough about how this stuff all works together.

Thanks

---

### Post by kansasnoob on 2014-02-09
> **Cavsfan said:**
> @mc4man, I saved a list of what was removed and just let it happen. Took out the stuff I had added and put it back like it should be normally like **xscreensaver -no-splash** in startup commands.
Then rebooted. Everything seems to be good to go. I do recall a bunch of stuff being installed when I installed something gnome* 

Man, I guess you can't learn enough about how this stuff all works together.

Thanks

Installing the meta-package 'gnome' is NOT the right way to get a "flashback" session.

I'm using "flashback w/metacity" in Ubuntu Trusty as I type this having only installed 'gnome-panel' which installs the proper dependencies and when I try to install the meta-package 'gnome' I get all of this cruft:

```
lance@lance-desktop:~$ sudo apt-get install gnome
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  content-hub libcontent-hub0 libgcrypt20 liblivemedia15
  linux-headers-3.13.0-5 linux-headers-3.13.0-5-generic linux-headers-3.13.0-6
  linux-headers-3.13.0-6-generic linux-image-3.13.0-5-generic
  linux-image-3.13.0-6-generic linux-image-extra-3.13.0-5-generic
  linux-image-extra-3.13.0-6-generic qtdeclarative5-accounts-plugin
  qtdeclarative5-ubuntu-content0.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  argyll binfmt-support browser-plugin-gnash caribou caribou-antler cli-common
  evolution evolution-common evolution-indicator evolution-plugins finger
  five-or-more fonts-cantarell four-in-a-row gawk gdebi gdebi-core gdm
  gedit-plugins gimp gimp-data gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-gucharmap-2.90 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-rest-0.7 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-tracker-0.16 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gir1.2-zeitgeist-2.0 gir1.2-zpj-0.0 gjs gksu gnash
  gnash-common gnome-backgrounds gnome-chess gnome-color-manager gnome-core
  gnome-dictionary gnome-documents gnome-games gnome-icon-theme-extras
  gnome-klotski gnome-nettool gnome-nibbles gnome-online-accounts
  gnome-packagekit gnome-packagekit-data gnome-packagekit-session gnome-robots
  gnome-shell gnome-shell-extensions gnome-sushi gnome-tetravex gnuchess
  gnuchess-book gtk2-engines hamster-applet hamster-indicator iagno
  imagemagick imagemagick-common inkscape libamd2.3.1 libappindicator0.1-cil
  libappindicator1 libavahi-ui-gtk3-0 libavresample1 libbabl-0.1-0 libblas3
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libboost-iostreams1.54.0 libboost-program-options1.54.0
  libboost-thread1.54.0 libcamd2.3.1 libcaribou-common libcaribou-gtk-module
  libcaribou-gtk3-module libcaribou0 libccolamd2.8.0 libcholmod2.1.2
  libcolord-gtk1 libdbus-glib2.0-cil libdbus2.0-cil libdiscid0
  libdmapsharing-3.0-2 libencode-locale-perl liberror-perl libevolution
  libfile-listing-perl libfont-afm-perl libgconf2.0-cil libgdict-1.0-6
  libgdict-common libgdiplus libgdm1 libgegl-0.2-0 libgfortran3 libgif4
  libgimp2.0 libgjs0d libgksu2-0 libglade2-0 libglib2.0-cil libgmime2.6-cil
  libgnome2-0 libgnome2-bin libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgpod-common libgpod4 libgsl0ldbl
  libgtk-vnc-2.0-0 libgtk2.0-cil libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell0 libgupnp-av-1.0-2 libgupnp-dlna-2.0-3
  libgvnc-1.0-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libicc2 libidl-common libidl0 libimdi0 libindicator7
  libio-html-perl libiptcdata0 libjavascriptcoregtk-1.0-0 libjemalloc1
  liblapack3 liblinear-tools liblinear1 liblqr-1-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmagick++5 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmail-spf-perl libmng2 libmono-addins-gui0.2-cil
  libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.0-cil
  libmono-corlib4.5-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmozjs-17.0-0
  libmusicbrainz5-0 libmutter0c libnet-http-perl libnetaddr-ip-perl
  libnetpbm10 liborbit-2-0 liborbit2 libpst4 librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1
  libsgutils2-2 libsigsegv2 libsofia-sip-ua-glib3 libsofia-sip-ua0
  libsys-hostname-long-perl libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libumfpack5.6.2 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwmf-bin libwww-perl libwww-robotrules-perl
  libxcb-xf86dri0 libytnef0 libzapojit-0.0-0 lightsoff mono-4.0-gac mono-gac
  mono-runtime mono-runtime-common mono-runtime-sgen mutter-common netpbm nmap
  perlmagick python-appindicator python-gnome2 python-numpy python-pyatspi
  python-pyorbit python-wnck python3-mako python3-markupsafe quadrapassel re2c
  rhythmbox-plugins rygel rygel-playbin rygel-preferences sound-juicer
  spamassassin spamc swell-foop tali telepathy-rakia tomboy tracker
  tracker-gui tracker-utils transfig unoconv vinagre whois xserver-xephyr
Suggested packages:
  browser-plugin-lightspark evolution-ews evolution-plugins-experimental
  gawk-doc gimp-help-en gimp-help gimp-data-extras dia-gnome gnome-boxes
  gnucash libreoffice-evolution planner gnome-hearts gnome-system-tools
  gnome-packagekit-tools xboard eboard scid python-evolution imagemagick-doc
  autotrace curl enscript gnuplot grads hp2xx html2ps mplayer povray radiance
  texlive-base-bin ufraw-batch pstoedit libsvg-perl libxml-xql-perl
  python-uniconvertor ruby libbonobo2-bin libdiscid0-dbg monodoc-gtk2.0-manual
  libgnomevfs2-bin gamin fam gnome-mime-data gsl-ref-psdoc gsl-doc-pdf
  gsl-doc-info gsl-ref-html libdata-dump-perl libsvm-tools liblinear-dev
  libcrypt-ssleay-perl libmono-i18n4.0-all libgamin0 sg3-utils sofia-sip-doc
  libauthen-ntlm-perl python-gnome2-doc gfortran python-dev python-nose
  python-numpy-dbg python-numpy-doc python-pyorbit-dbg python3-beaker
  python-mako-doc rygel-tracker rygel-mediathek tumbler gstreamer1.0-lame
  gstreamer1.0-plugins-really-bad razor libnet-ident-perl libdbi-perl pyzor
  libmail-dkim-perl tasque xfig
Recommended packages:
  gstreamer0.10-ffmpeg tracker-miner-fs
[B]The following NEW packages will be installed:
  argyll binfmt-support browser-plugin-gnash caribou caribou-antler cli-common
  evolution evolution-common evolution-indicator evolution-plugins finger
  five-or-more fonts-cantarell four-in-a-row gawk gdebi gdebi-core gdm
  gedit-plugins gimp gimp-data gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-gucharmap-2.90 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-rest-0.7 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-tracker-0.16 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gir1.2-zeitgeist-2.0 gir1.2-zpj-0.0 gjs gksu gnash
  gnash-common gnome gnome-backgrounds gnome-chess gnome-color-manager
  gnome-core gnome-dictionary gnome-documents gnome-games
  gnome-icon-theme-extras gnome-klotski gnome-nettool gnome-nibbles
  gnome-online-accounts gnome-packagekit gnome-packagekit-data
  gnome-packagekit-session gnome-robots gnome-shell gnome-shell-extensions
  gnome-sushi gnome-tetravex gnuchess gnuchess-book gtk2-engines
  hamster-applet hamster-indicator iagno imagemagick imagemagick-common
  inkscape libamd2.3.1 libappindicator0.1-cil libappindicator1
  libavahi-ui-gtk3-0 libavresample1 libbabl-0.1-0 libblas3 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libboost-iostreams1.54.0 libboost-program-options1.54.0
  libboost-thread1.54.0 libcamd2.3.1 libcaribou-common libcaribou-gtk-module
  libcaribou-gtk3-module libcaribou0 libccolamd2.8.0 libcholmod2.1.2
  libcolord-gtk1 libdbus-glib2.0-cil libdbus2.0-cil libdiscid0
  libdmapsharing-3.0-2 libencode-locale-perl liberror-perl libevolution
  libfile-listing-perl libfont-afm-perl libgconf2.0-cil libgdict-1.0-6
  libgdict-common libgdiplus libgdm1 libgegl-0.2-0 libgfortran3 libgif4
  libgimp2.0 libgjs0d libgksu2-0 libglade2-0 libglib2.0-cil libgmime2.6-cil
  libgnome2-0 libgnome2-bin libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgpod-common libgpod4 libgsl0ldbl
  libgtk-vnc-2.0-0 libgtk2.0-cil libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell0 libgupnp-av-1.0-2 libgupnp-dlna-2.0-3
  libgvnc-1.0-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libicc2 libidl-common libidl0 libimdi0 libindicator7
  libio-html-perl libiptcdata0 libjavascriptcoregtk-1.0-0 libjemalloc1
  liblapack3 liblinear-tools liblinear1 liblqr-1-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmagick++5 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmail-spf-perl libmng2 libmono-addins-gui0.2-cil
  libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.0-cil
  libmono-corlib4.5-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmozjs-17.0-0
  libmusicbrainz5-0 libmutter0c libnet-http-perl libnetaddr-ip-perl
  libnetpbm10 liborbit-2-0 liborbit2 libpst4 librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1
  libsgutils2-2 libsigsegv2 libsofia-sip-ua-glib3 libsofia-sip-ua0
  libsys-hostname-long-perl libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libumfpack5.6.2 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwmf-bin libwww-perl libwww-robotrules-perl
  libxcb-xf86dri0 libytnef0 libzapojit-0.0-0 lightsoff mono-4.0-gac mono-gac
  mono-runtime mono-runtime-common mono-runtime-sgen mutter-common netpbm nmap
  perlmagick python-appindicator python-gnome2 python-numpy python-pyatspi
  python-pyorbit python-wnck python3-mako python3-markupsafe quadrapassel re2c
  rhythmbox-plugins rygel rygel-playbin rygel-preferences sound-juicer
  spamassassin spamc swell-foop tali telepathy-rakia tomboy tracker
  tracker-gui tracker-utils transfig unoconv vinagre whois xserver-xephyr
0 upgraded, 264 newly installed, 0 to remove and 0 not upgraded.
Need to get 120 MB of archives.
[COLOR="#FF0000"]After this operation, 510 MB of additional disk space will be used.[/COLOR][/B]
Do you want to continue? [Y/n] n

```

---

### Post by Cavsfan on 2014-02-10
Guess I should have asked you before hand.

I'm pretty sure that thought was already implied by mc4man. :p

---

