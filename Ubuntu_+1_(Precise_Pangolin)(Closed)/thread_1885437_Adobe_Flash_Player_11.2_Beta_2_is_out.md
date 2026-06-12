---
title: "Adobe Flash Player 11.2 Beta 2 is out"
date: 2011-11-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2011-11-23
[http://labs.adobe.com/downloads/flashplayer11-2.html](http://labs.adobe.com/downloads/flashplayer11-2.html)

Won't be able to try it until later. I hope it works better than 11.2 Beta 1 - I found the constant crashes too annoying in the end and reverted to an earlier version.

---

### Post by ajgreeny on 2011-11-23
I have not managed to get the beta version that Flash-aid add-on gives by default to work at all on my system, but the Shockwave Flash 11.1 r102 that Flash-aid downloads from the ubuntu repos works fine.

I presume this is a hardware incompatibility in my case.

---

### Post by portis on 2011-11-23
It still crashes, just like 11.2 beta 1.

> **paul_in_london said:**
> [http://labs.adobe.com/downloads/flashplayer11-2.html](http://labs.adobe.com/downloads/flashplayer11-2.html)

Won't be able to try it until later. I hope it works better than 11.2 Beta 1 - I found the constant crashes too annoying in the end and reverted to an earlier version.

---

### Post by effenberg0x0 on 2011-11-23
> **portis said:**
> It still crashes, just like 11.2 beta 1.

@portis
1. You're using nvidia?
2. Does "**LD_PRELOAD=/usr/lib/libGL.so.1 $(whereis firefox)&**" reduces the number of crashes on flash sites?

---

### Post by ubupirate on 2011-11-23
Tried this last night on my Lucid install, and it was horrible.

There was this line of I think small small text at the very lower right corner of flash videos which was annoying, and videos were extremely choppy.

Went back to stable, all works 100% now. :popcorn:

---

### Post by xebian on 2011-11-23
Looks ok here with NV 290.10 64-bit.

---

### Post by portis on 2011-11-23
1. yes, I use nvidia.
2. I don't have this file /usr/lib/libGL.so.1, instead I have a file:
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1

I use LD_PRELOAD=/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 firefox to launch firefox.
After some tests, flash still crashes and give me these error messages:

[xcb] Unknown sequence number while processing queue
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
plugin-container: ../../src/xcb_io.c:273: poll_for_event: Assertion `!xcb_xlib_threads_sequence_lost' failed.
WARNING: pipe error (87): Connection reset by peer: file /build/buildd/firefox-9.0~b2+build1/build-tree/mozilla/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 419

Some people said that flashplugin has some bugs in multithreading xcb.

> **effenberg0x0 said:**
> @portis
1. You're using nvidia?
2. Does "**LD_PRELOAD=/usr/lib/libGL.so.1 $(whereis firefox)&**" reduces the number of crashes on flash sites?

---

### Post by effenberg0x0 on 2011-11-23
> **portis said:**
> 1. yes, I use nvidia.
2. I don't have this file /usr/lib/libGL.so.1, instead I have a file:
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1

I use LD_PRELOAD=/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 firefox to launch firefox.
After some tests, flash still crashes and give me these error messages:

[xcb] Unknown sequence number while processing queue
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
plugin-container: ../../src/xcb_io.c:273: poll_for_event: Assertion `!xcb_xlib_threads_sequence_lost' failed.
WARNING: pipe error (87): Connection reset by peer: file /build/buildd/firefox-9.0~b2+build1/build-tree/mozilla/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 419

Some people said that flashplugin has some bugs in multithreading xcb.

libGL.so.1 should be a soft-link to libGL.so.290.10 from Nvidia. It doesn't look ok to me.

If I were you, I would go to Nvidia Linux Drivers download page, or use the FTP link I posted here, save the file in your HOME directory, sudo service lightdm stop, sudo chmod +x /home/you/NV* and sudo ./NV* to run the install.

During install, NVidia-proprietary installer fixes missing / wrong libs and references. You just have to say yes to all questions. Then sudo service lightdm start and test again.

---

### Post by Harry33 on 2011-11-23
> **xebian said:**
> Looks ok here with NV 290.10 64-bit.

Working here too, Nvidia-current_290.10, 64-bit setup.

---

### Post by portis on 2011-11-23
Ok, I also have /usr/lib/nvidia-current-updates/libGL.so.1,
but LD_PRELOAD=/usr/lib/nvidia-current-updates/libGL.so.1 firefox
just gave me the same error messages.

nvidia driver 290.10 

> **effenberg0x0 said:**
> libGL.so.1 should be a soft-link to libGL.so.290.10 from Nvidia. It doesn't look ok to me.

If I were you, I would go to Nvidia Linux Drivers download page, or use the FTP link I posted here, save the file in your HOME directory, sudo service lightdm stop, sudo chmod +x /home/you/NV* and sudo ./NV* to run the install.

During install, NVidia-proprietary installer fixes missing / wrong libs and references. You just have to say yes to all questions. Then sudo service lightdm start and test again.

---

### Post by effenberg0x0 on 2011-11-23
I already gave you my advice (to download and use the proprietary driver from Nvidia website and run its installer).

---

### Post by portis on 2011-11-23
I download the proprietary driver and I packaged it into debs.
Do you think there's really a difference if I run the installer instead of install the debian package?

---

### Post by Jordanwb on 2011-11-25
So where does it go? I put it in ~/.mozilla/plugin/ but firefox doesn't load it.

> **cariboo907 said:**
> The standard location has always been /usr/lib/mozilla/plugins

thanks

---

### Post by cariboo on 2011-11-25
> **Jordanwb said:**
> So where does it go? I put it in ~/.mozilla/plugin/ but firefox doesn't load it.

The standard location has always been /usr/lib/mozilla/plugins

---

### Post by effenberg0x0 on 2011-11-25
You can put it there, but it must have proper ownership/permissions.

I usually put it in /usr/lib/adobe-flashplugin/<version>/libflashplayer.so
Then I create a link from to it at /etc/alternatives/mozilla-flashplugin
And /usr/lib/mozilla/plugins/flashplugin-alternative.so is a link to /etc/alternatives/mozilla-flashplugin

There are a number of ways, of course.
In any case, you have have proper ownership/permissions. 

If you're gonna put the file inside .mozilla/plugins, it should be owned by you.
sudo chown $USER:$USER && sudo chmod 775 libflashplayer.so

---

### Post by Harry33 on 2011-11-26
> **effenberg0x0 said:**
> You can put it there, but it must have proper ownership/permissions.

I usually put it in /usr/lib/adobe-flashplugin/<version>/libflashplayer.so
Then I create a link from to it at /etc/alternatives/mozilla-flashplugin
And /usr/lib/mozilla/plugins/flashplugin-alternative.so is a link to /etc/alternatives/mozilla-flashplugin

There are a number of ways, of course.
In any case, you have have proper ownership/permissions. 

If you're gonna put the file inside .mozilla/plugins, it should be owned by you.
sudo chown $USER:$USER && sudo chmod 775 libflashplayer.so

It is generally considered that the method effenberg described, is the safest way.
Adobe recommends simply putting the file libflashplayer.so into folder /usr/lib/mozilla/plugins/
Then it is of course a universal installation.
Using home folder .mozilla/plugins/ makes it user specific.

---

### Post by zika on 2011-11-26
> **Harry33 said:**
> It is generally considered that the method effenberg described, is the safest way.
Adobe recommends simply putting the file libflashplayer.so into folder /usr/lib/mozilla/plugins/
Then it is of course a universal installation.
Using home folder .mozilla/plugins/ makes it user specific.I always think we want to make it user-specific... ;) At least for „security“ purposes...

---

### Post by effenberg0x0 on 2011-11-26
The method I use allow for having different versions of the plugin, for all users. So, when it starts to crash, I can just set the soft link of /etc/alternatives to a previous version, etc. 

I use the "alternatives" stuff because I had issues with some versions of flash && specific versions of NVidia libGL. And, even though I'm not updating it from repos, I wanted to keep a structure similar to what the default on Ubuntu is (although Ubuntu doesn't keep the old version, like I do). 

I do more or less the same with java: I have java-6-sun (u1), java-6-oracle, java-7-oracle and open-jdk*. It's a little more complicated because these 4 jvm directories get copied to a RAM disk using a init.d script and there are only links to /tmp/ramdisk/java<something> on lib (and some programs use specific machines, like eclipse, etc).

But I understand it all is overkill for the average user that just wants to get the damn thing to work.

---

### Post by zika on 2011-11-26
[img]http://gifs.gifbin.com/sw7yu34948sw.gif[/img]

---

### Post by effenberg0x0 on 2011-11-26
> **zika said:**
> [IMG]http://gifs.gifbin.com/sw7yu34948sw.gif[/IMG]

/me wonders what the gif was about :)

---

### Post by zika on 2011-11-26
> **effenberg0x0 said:**
> /me wonders what the gif was about :smile:
My message should have looked like this:
> **effenberg0x0 said:**
> The method I use allow for having different versions of the plugin, for all users. So, when it starts to crash, I can just set the soft link of /etc/alternatives to a previous version, etc. 

I use the "alternatives" stuff because I had issues with some versions of flash && specific versions of NVidia libGL. And, even though I'm not updating it from repos, I wanted to keep a structure similar to what the default on Ubuntu is (although Ubuntu doesn't keep the old version, like I do). 

I do more or less the same with java: I have java-6-sun (u1), java-6-oracle, java-7-oracle and open-jdk*. It's a little more complicated because these 4 jvm directories get copied to a RAM disk using a init.d script and there are only links to /tmp/ramdisk/java<something> on lib (and some programs use specific machines, like eclipse, etc).

But I understand it all is overkill for the average user that just wants to get the damn thing to work.
[IMG]http://gifs.gifbin.com/sw7yu34948sw.gif[/IMG]
... ;)

Or, simply, I agree  with You...

---

### Post by effenberg0x0 on 2011-11-26
> **zika said:**
> My message should have looked like this:

[IMG]http://gifs.gifbin.com/sw7yu34948sw.gif[/IMG]
... ;)

Or, simply, I agree  with You...
Oh ok... I asked cause instead of the gif, all I see is this:
[ATTACH]208015[/ATTACH]
There must be some sort of Geo-IP thing blocking download from IPs in Brazil...
(or are you trying to mess with my mind lol)

---

### Post by effenberg0x0 on 2011-11-26
Anyway, one thing that I thought I should clarify for the beginner that eventually reads this while trying to get flash to work. 

There's a perception that usually Linux users are divided between those that adopt a KISS principle in one end and those that praise autotools and kernel hacking in the other. Beginners stay in the KISS end for years before trying to venture in the other end, if ever. IMO, beginners that choose the KISS end can use Linux for years by following cake recipes in forums, blogs, etc and eventually learn nothing.

Regarding this particular topic (installing flash): The /etc/alternatives method is commonly regarded as complex by beginners. Although it sure is more complex than saving a lib in a target plugins directory, I find it one of the smartest things we can play with and of the simplest. There's inherent true beauty in it: It's a simple, rock-solid, structured in the very basics of the shell (links), way to change the behavior of many things in the system in runtime. For those that love shell and shell scripting, like me, it's gold. If I could advise a beginner to invest 20 minutes of his life learning something about Ubuntu and Linux, I think "alternatives" is a nice way to learn the basic about libs, links, permissions and ownership of files and directories and some bash.

---

### Post by paul_in_london on 2011-11-26
11.2 Beta 2 crashes more than I would like, but I'm still using it.

I don't usually mess around with the sym links, I just extract the .tar.bz2 into /usr/lib/adobe-flashplugin/ (if installing manually) and keep a stable version in that directory that I can fall back on if it all gets too annoying.

---

### Post by zika on 2011-11-26
> **effenberg0x0 said:**
> Oh ok... I asked cause instead of the gif, all I see is this:
[ATTACH]208015[/ATTACH]
There must be some sort of Geo-IP thing blocking download from IPs in Brazil...
(or are you trying to mess with my mind lol)Oh, I'm sorry. No, I did not want to make any inappropriate joke. Old people are clumsy making jokes... ;)

---

### Post by zika on 2011-11-26
> **paul_in_london said:**
> 11.2 Beta 2 crashes more than I would like, but I'm still using it.

I don't usually mess around with the sym links, I just extract the .tar.bz2 into /usr/lib/adobe-flashplugin/ (if installing manually) and keep a stable version in that directory that I can fall back on if it all gets too annoying.I keep Flash (and other) plugin(s) in a separate sub-directory of Home that I keep up-to date and I make symbolic links in appropriate directory, pointing to those above. My symlinks are, usually, in ~/.mozilla/plugins but, because of Opera, I, sometimes, make a symlink also in /usr/lib/mozilla/plugins...
Just to be as precise as I can... In accordance with our current testing version...

---

### Post by effenberg0x0 on 2011-11-26
> **zika said:**
> I keep Flash (and other) plugin(s) in a separate sub-directory of Home that I keep up-to date and I make symbolic links in appropriate directory, pointing to those above. My symlinks are, usually, in ~/.mozilla/plugins but, because of Opera, I, sometimes, make a symlink also in /usr/lib/mozilla/plugins...
Just to be as precise as I can... In accordance with our current testing version...

That's a nice way too... When you mention the "accordance to testing version": It's a real important thing. Sometimes I'm finding it hard to not use the old-habits and tweaks in the testing systems, so I can get a real feel of what the default install is. Sometimes I do old-habit tweaks/changes automatically, without thinking at all that it may produce very different behaviors than what an average user would experience...

---

### Post by zika on 2011-11-26
> **effenberg0x0 said:**
> That's a nice way too... When you mention the "accordance to testing version": It's a real important thing. Sometimes I'm finding it hard to not use the old-habits and tweaks in the testing systems, so I can get a real feel of what the default install is. Sometimes I do old-habit tweaks/changes automatically, without thinking at all that it may produce very different behaviors than what an average user would experience...Accordance was a joke because I tried to be precise, and the name of version we are testing is also: precise...
If I put libflashplayer.so in /usr/lib/mozilla/plugins, directly, as a file, FF tends to crash. Java is yet another even more difficult story, even though alternatives are set accordingly... If I put symbolic links everything works perfectly. FF reads ~/.mozilla/plugins and it is happy with that, Opera demand usage of /usr/lib/mozilla/plugins. Yes it can be tweaked to use ~/.mozilla/plugins,but, I am not in a tweak mode always...
Yes I carry a lot of stuff from the time 64-bit plugins had to be &#8222;installed&#8220; in a non-standard way. Nowadays it is easier... But, old horse, as I am, is a bit slow in learning new paths...

---

### Post by effenberg0x0 on 2011-11-26
> **zika said:**
> Accordance was a joke because I tried to be precise, and the name of version we are testing is also: precise...

Non-native English speakers like me are terrible at identifying subtle humor :P

> **zika said:**
> 
If I put libflashplayer.so in /usr/lib/mozilla/plugins, directly, as a file, FF tends to crash.

It's weird. Only time I've seen that was when there was more than one occurrence of libflashplayer.so in the system. But FF actually does do some strange things...

---

### Post by zika on 2011-11-26
> **effenberg0x0 said:**
> Non-native English speakers like me are terrible at identifying subtle humor :PDitto:
Non-native English speakers like me are terrible at identifying subtle humor :razz:
or should I say:
Non-native English speakers like we are terrible at identifying subtle humor :razz:
> **effenberg0x0 said:**
>  It's weird. Only time I've seen that was when there was more than one occurrence of libflashplayer.so in the system. But FF actually does do some strange things...Exactly. That is why I have only one: in aforementioned folder. Opera and FF like it in different places and that is the nice way to make them cohabit happily... Yes I could put it in /usr/lib/mozilla/plugins, but FF... I said that, already...

I think we'll get banned for this (long) conversation... ;)

---

### Post by effenberg0x0 on 2011-11-26
> **zika said:**
> Ditto:
I think we'll get banned for this (long) conversation... ;)

Cariboo must be taking a weekend nap :)

---

### Post by Elfy on 2011-11-27
Cariboo is not the only one that wanders these halls ... 

I just hardly ever post in here :P

---

### Post by zika on 2011-11-27
> **forestpiskie said:**
> Cariboo is not the only one that wanders these halls ... 

I just hardly ever post in here :PBe merciful to us... ;)

---

### Post by Elfy on 2011-11-27
I might ... :p

---

