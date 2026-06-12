---
title: "Audacious 1.5.1 Released!"
date: 2008-05-27
forum: The Cafe
---

### Post by Kosimo on 2008-05-27
Hey Guys, audacious team has just released a new version 1.5.1

Here the changelogs: 

Audacious 1.5.1 (2008-05-23)
============================

> Enhancements
------------
* New Cairo-based playlist widget, which should be somewhat faster.
* Volume setting is now saved between sessions.
* Session management is now optional and can be disabled via
  a configure option.
* Added an option to enable loading of broken skins (use with care.)
* "Remote" handling of Audacious via commandline is now faster.

Bugfixes
--------
* Headless support should work now again.
* Compiling without DBUS support works, but you should note that we DO NOT
  SUPPORT builds compiled without DBUS! Several features of Audacious are
  disabled if built without DBUS!
* Memory leak fixed in eggsm (session management).
* Documentation updates and fixes.
* GCC 4.3 compilation fixes.
* Fixed a crash when eggsm couldn't find audacious.desktop file.
* Cleaned up and refactored configure and various buildsystem fixes.
* Removed references to some options that are not available anymore.
* A Dbus-related crash when using remote playlist adding functions was fixed.
* Few potential lock-up situations have been fixed.
* "Reload Plugins" button was removed, because it did not work properly
  and often caused segfaults due to broken plugins.




Audacious-plugins 1.5.1 (2008-05-23)
====================================

> Enhancements
------------
* Some ModPlug playback engine fixes integrated from Schism Tracker.
* ModPlug archive support "works" now again, but only on local files.
* cdaudio-ng now has a rescan option.
* Various enhancements in Audacious-SID plugin synchronized from
  XMMS-SID.

Bugfixes
--------
* ModPlug starting to play from incorrect pattern order was fixed.
* Some unaligned access and other nasty bugs fixed in MADPlug.
* Code cleanups made in various plugins (not nearly enough, though.)
* Cleaned up and refactored configure and various buildsystem fixes.
* ProjectM compatibility fixes.
* demac plugin skips leading junk in APE files.
* Some sndfile plugin problems, including a filehandle leak, were fixed.
* Several crash fixes in the Neon HTTP/HTTPS transport plugin.



Does anyone made a .deb compiled in Hardy?

Thank you!!

---

### Post by Kosimo on 2008-05-28
Does anyone know any "Third Party" Repository with this latest Audacious version?

---

### Post by bigbrovar on 2008-05-28
can u please post a link were i can download the source code .. . BTW i dont know why pple are always scared to compile from source .. its not that hard especially for a something like audacity which is available in the repos .. just run [PHP]sudo apt-get build-dep audacious[/PHP] .. this would install all the dependencies for u ... extract the folder into ur desktop ( or where ever) and enter the folder thru terminal .. (u can install nautilus-terminal its makes that very easy and its in the repo) run [PHP]./configure[/PHP]   then run [PHP]make[/PHP] and lastly run [PHP]make install[/PHP] ... just give it a try .. its fun .. i tell u :)

---

### Post by rhauff on 2008-06-19
Well, maybe compiling is great, but this one says it requires libmcs >= 0.7, which is not is the repositories.  And the atheme site it says to get it from appears dead.

---

### Post by JPorter on 2008-06-22
> **rhauff said:**
> Well, maybe compiling is great, but this one says it requires libmcs >= 0.7, which is not is the repositories.  And the atheme site it says to get it from appears dead.

libmcs 0.7.1 is in the Intrepid repositories, but not in Hardy.  You can download the Intrepid package directly from:  [http://packages.ubuntu.com/intrepid/libmcs1](http://packages.ubuntu.com/intrepid/libmcs1)  Use at your own risk, of course.

Also, there are Audacious 1.5.1 packages for Hardy built by Dean on the Audacious forums, you can see the discussion here:  [http://boards.nenolod.net/viewtopic.php?f=4&t=3](http://boards.nenolod.net/viewtopic.php?f=4&t=3)  Note that there is also a custom crossfade plugin that may work better than the one that has been previously packaged under Ubuntu.


[edit]  **AUDACIOUS 1.5.1 HOW-TO ADDED BELOW IN POST #7**

---

### Post by FranMichaels on 2008-06-22
> **rhauff said:**
> Well, maybe compiling is great, but this one says it requires libmcs >= 0.7, which is not is the repositories.  And the atheme site it says to get it from appears dead.

You can get the mercurial version. I've been building automatically off that for several months. :)

Quick intro for audacious and main plugins

[http://audacious-media-player.org/index.php?title=Mercurial_Information](http://audacious-media-player.org/index.php?title=Mercurial_Information)

[http://hg.atheme.org/](http://hg.atheme.org/)

Notice libmcs at the bottom of this page.

Building from the mercurial repos is pretty fun, smaller downloads (hg pull), combined with bleeding edge fun, and it's easy to roll back...

---

### Post by JPorter on 2008-06-22
I just tested with the new [FONT="Courier New"][COLOR="DimGray"]libmcs1[/COLOR][/FONT] (0.7.1) and the Audacious 1.5.1 Hardy packages made by Dean that I linked to in post #5.  It works great.



[INDENT]**NOTE TO FOLKS UPGRADING MANUALLY:**

[INDENT]Dean has packaged the files a little differently from the default Ubuntu installation of Audacious 1.5.0. Rather than separate packages such as [FONT="Courier New"][COLOR="DimGray"]libaudclient1[/COLOR][/FONT] and [FONT="Courier New"][COLOR="DimGray"]audacious-plugins-extra[/COLOR][/FONT], he has packaged everything together in the main [FONT="Courier New"][COLOR="DimGray"]audacious[/COLOR][/FONT] and [FONT="Courier New"][COLOR="DimGray"]audacious-plugins[/COLOR][/FONT] debs.  Oh, and his embedded package descriptions happen to be in Spanish, but it doesn't make any difference for our purposes.

*You should uninstall all of the current Ubuntu packages related to Audacious 1.5.0 prior to installing Dean's 1.5.1 Hardy packages.*[/INDENT]



**HOW-TO:**


[list=1][*]I installed the new [FONT="Courier New"][COLOR="DimGray"]libmcs1[/COLOR][/FONT] manually from the Intrepid package I mentioned earlier.  

Link:  [FONT="Courier New"][libmcs1_0.7.1-1_i386.deb]("http://packages.ubuntu.com/intrepid/libmcs1")[/FONT]



[*]I then **un**installed all of the following Audacious 1.5.0 packages via Synaptic:

[FONT="Courier New"][COLOR="DimGray"]audacious
audacious-plugins 
audacious-plugins-extra 
libaudclient1 
libaudid3tag1[/COLOR][/FONT]



[*]I then installed dean's Audacious 1.5.1 .deb packages manually, which are linked:

[FONT="Courier New"][audacious_1_5_1-1_i386.deb]("http://www.divshare.com/download/4606507-72f")
[audacious-plugins_1_5_1-1_i386.deb]("http://www.divshare.com/download/4606508-54a")[/FONT]



[*]I also installed his recommended [_Audacious Crossfade 0.3.14_]("http://www.divshare.com/download/4606509-21f") but have not yet tested it.[/list][/INDENT]



Best of luck, and use at your own risk.

Thanks,
Porter

---

### Post by Kosimo on 2008-06-28
That worked perfectly dude.
Thank you!!



> **JPorter said:**
> I just tested with the new [FONT="Courier New"][COLOR="DimGray"]libmcs1[/COLOR][/FONT] (0.7.1) and the Audacious 1.5.1 Hardy packages made by Dean that I linked to in post #5.  It works great.



[INDENT]**NOTE TO FOLKS UPGRADING MANUALLY:**

[INDENT]Dean has packaged the files a little differently from the default Ubuntu installation of Audacious 1.5.0. Rather than separate packages such as [FONT="Century Gothic"][COLOR="DimGray"]libaudclient1[/COLOR][/FONT] and [FONT="Courier New"][COLOR="DimGray"]audacious-plugins-extra[/COLOR][/FONT], he has packaged everything together in the main [FONT="Courier New"][COLOR="DimGray"]audacious[/COLOR][/FONT] and [FONT="Courier New"][COLOR="DimGray"]audacious-plugins[/COLOR][/FONT] debs.  Oh, and his embedded package descriptions happen to be in Spanish, but it doesn't make any difference for our purposes.

*You should uninstall all of the current Ubuntu packages related to Audacious 1.5.0 prior to installing Dean's 1.5.1 Hardy packages.*[/INDENT]



**HOW-TO:**


[list=1][*]I installed the new [FONT="Courier New"][COLOR="DimGray"]libmcs1[/COLOR][/FONT] manually from the Intrepid package I mentioned earlier.  

Link:  [FONT="Courier New"][libmcs1_0.7.1-1_i386.deb]("http://packages.ubuntu.com/intrepid/libmcs1")[/FONT]



[*]I then **un**installed all of the following Audacious 1.5.0 packages via Synaptic:

[FONT="Courier New"][COLOR="DimGray"]audacious
audacious-plugins 
audacious-plugins-extra 
libaudclient1 
libaudid3tag1[/COLOR][/FONT]



[*]I then installed dean's Audacious 1.5.1 .deb packages manually, which are linked:

[FONT="Courier New"][audacious_1_5_1-1_i386.deb]("http://www.divshare.com/download/4606507-72f")
[audacious-plugins_1_5_1-1_i386.deb]("http://www.divshare.com/download/4606508-54a")[/FONT]



[*]I also installed his recommended [_Audacious Crossfade 0.3.14_]("http://www.divshare.com/download/4606509-21f") but have not yet tested it.[/list][/INDENT]



Best of luck, and use at your own risk.

Thanks,
Porter

---

### Post by Kosimo on 2008-06-29
I'm having a strange issue using Audacious 1.5.1: 
I'm wondering if anyone else have this particular bug:  When Audacious is closed and I double click to any music file audacious starts playing the last played file that was playing before closing it... Wired...
this forces me to double click again to the same file once audacious is open

---

### Post by JPorter on 2008-06-30
> **Kosimo said:**
> I'm having a strange issue using Audacious 1.5.1: 
I'm wondering if anyone else have this particular bug:  When Audacious is closed and I double click to any music file audacious starts playing the last played file that was playing before closing it... Wired...
this forces me to double click again to the same file once audacious is open
Kosimo,

I have the same behavior. No clue why this happens. It works normally once Audacious is running, so it's not a global change in command line parsing for the app... pretty odd.  Luckily it doesn't affect the performance, so it's not much of an issue for me.  

I suppose this is the sort of thing that will (should?) be ironed out prior to final inclusion in the Ubuntu repositories.

---

### Post by Kosimo on 2008-07-01
> **JPorter said:**
> Kosimo,

I have the same behavior. No clue why this happens. It works normally once Audacious is running, so it's not a global change in command line parsing for the app... pretty odd.  Luckily it doesn't affect the performance, so it's not much of an issue for me.  

I suppose this is the sort of thing that will (should?) be ironed out prior to final inclusion in the Ubuntu repositories.

Yeps... Looks like, even if I doubt that this issue can be solved by adding 1.5.1 to Ubuntu official respository. I guess that on Intrepid Ibex release we'll have at least a 1.5.2 where this bug it'll be fixed.

---

### Post by NoVista on 2008-08-18
I have been without Audacious for quite a while.
It always ran fine for me until it mysteriously broke months ago, (link below), and I put off trying again to fix it for a later date.

I currently have it installed from here:
[http://howto.landure.fr/gnu-linux/ubuntu-gutsy-gibbon/audacious-media-player-1-4-for-ubuntu-7-10-gutsy-gibbon](http://howto.landure.fr/gnu-linux/ubuntu-gutsy-gibbon/audacious-media-player-1-4-for-ubuntu-7-10-gutsy-gibbon)

But mo matter what version of Audacious I install, from any repo, the same thing happens when I start the program:
Segmentation fault (core dumped)

None of the fixes on this page work for me:
[http://ubuntuforums.org/showthread.php?t=706497](http://ubuntuforums.org/showthread.php?t=706497)

I really miss this program.
I still see others having this problem.
Anyone with the same symptoms ever find a fix?

---

### Post by qstraza on 2008-08-19
hej guys ;)

can anyone reupload those 2 .deb files from previous page:
audacious_1_5_1-1_i386.deb
audacious-plugins_1_5_1-1_i386.deb

Becouse link doesnt work anymore :(

Im having trouble with current version (from the repos, hardy) it uses like 80 % of my cpu, which sucks a lot, i compiled xmms so i dont mealt in the room cuz of the cpu temp:p

---

### Post by RiceMonster on 2008-08-19
Hmmm, the arch repos still have 1.5.0. The only bug I've been experiencing is sometimes when I bring it back from the tray the playlist window is cut off at the edge and I have to alt-right click resize to to fix it. Doesn't appear to be fixed yet.

---

### Post by qstraza on 2008-08-19
well i have 20.000 tracks in my playlist, saved playlist, all trackes are synched (have full name and track lenght)

when i rerun audacious it takes up to 80 % of cpu usage and keeps eating it for like 30mins.

I read some threat that if you quit audacious and remove one track from the playlist, audacious starts eating the cpu (when runned again ofcourse).

message reads something like "name_of_the_track giving up"... this floods your screen, if runned from terminal.

try it and tell us if it does the same for you ;)

anyway, i would be very happy if someone could provide me a 1.5.1 version, deb package 

peace

---

### Post by RiceMonster on 2008-08-19
20,000? That's a lot. I have 6600 songs in my library, but I don't keep them all in one giant audacious playlist, because I don't like having them in one big list and I know XMMS style players have a history of not agreeing with large playlists like that. I just add whatever album I want to listen to and then clear the playlist later. It's fine because I have my music neatly organized.

I heard one of the devs say on the forums they're going to be doing work to improve the playlist on audacious 2. 

Edit: [here](http://boards.nenolod.net/viewtopic.php?f=4&t=66)

---

### Post by qstraza on 2008-08-19
Yea looking forward to version 2.
I have one big playlist where all of my tracks are, and then few smaller, but i usually play the big one ;)

I dont know what u mean by XMMS style-like. I used XMMS like for 5 years i think, and even now i am, cuz of that cpu thing, and it works flawlessly, but i want changes;) xmms is old... I was using amarok for a day or two, and with so many songs search took a while, in audacious search (ctrl+j) work faster than amarok's, but xmms's search is realy fast.

I have to start using smaller playlist... ;)

---

### Post by RiceMonster on 2008-08-19
By XMMS-like, I just mean players that are similar, or related to XMMS. I'm talking about of course, XMMS, BMP and Audacious.

I stopped using Amarok because I don't like Qt and I found Audacious had better sound quality (equalizer, etc).

Edit: Oh, and regards to your problem, I think i experienced it, but that was because I closed it with songs from my external harddrive, then tried to play the same songs again with my external harddrive off. It did start eating up cpu.

---

### Post by foresto on 2008-08-22
A backport for Hardy has been requested.  Here's hoping it gets done soon.

[https://bugs.launchpad.net/hardy-backports/+bug/242161](https://bugs.launchpad.net/hardy-backports/+bug/242161)

---

### Post by ENigma885 on 2008-09-13
[SIZE="5"]_**The Packages**_ [/SIZE]

I compiled Audacious and Audacious plugins 1.5.1 from source and packed them in deb packages under Hardy... to install them u have to:

**1.** Download and install the *_libmcs1 0.7.1_* package from Ubuntu Intrepid repository [[COLOR="Red"]**HERE**[/COLOR]]("http://yu.archive.ubuntu.com/ubuntu/pool/universe/m/mcs/libmcs1_0.7.1-1_i386.deb").
it doesn't conflict with other packages at least for me under Hardy.

**2.** Then *_Audacious 1.5.1_* (audacious_1.5.1-1_i386.deb) from [[COLOR="Red"]**HERE**[/COLOR]]("http://rapidshare.com/files/145084729/audacious_1.5.1-1_i386.deb.html").

**3. ** Lastly *_Audacious Plugins 1.5.1_* (audacious-plugins_1.5.1-1_i386.deb) from [[COLOR="Red"]**HERE**[/COLOR]]("http://rapidshare.com/files/145086235/audacious-plugins_1.5.1-1_i386.deb.html").

I uploaded Audacious debian packages on Rapidshare..if some ppl have problems with it. i can upload them elsewhere.

**_**HOW TO use Rapidshare**_

(Click the link >> Select Free User >> Wait the timer, if any, >> The download button will appear >> Click download)

---

### Post by mustang on 2008-09-21
> **ENigma885 said:**
> [SIZE="5"]_**The Packages**_ [/SIZE]

I compiled Audacious and Audacious plugins 1.5.1 from source and packed them in deb packages under Hardy... to install them u have to:

**1.** Download and install the *_libmcs1 0.7.1_* package from Ubuntu Intrepid repository [[COLOR="Red"]**HERE**[/COLOR]]("http://yu.archive.ubuntu.com/ubuntu/pool/universe/m/mcs/libmcs1_0.7.1-1_i386.deb").
it doesn't conflict with other packages at least for me under Hardy.

**2.** Then *_Audacious 1.5.1_* (audacious_1.5.1-1_i386.deb) from [[COLOR="Red"]**HERE**[/COLOR]]("http://rapidshare.com/files/145084729/audacious_1.5.1-1_i386.deb.html").

**3. ** Lastly *_Audacious Plugins 1.5.1_* (audacious-plugins_1.5.1-1_i386.deb) from [[COLOR="Red"]**HERE**[/COLOR]]("http://rapidshare.com/files/145086235/audacious-plugins_1.5.1-1_i386.deb.html").

I uploaded Audacious debian packages on Rapidshare..if some ppl have problems with it. i can upload them elsewhere.

**_**HOW TO use Rapidshare**_

(Click the link >> Select Free User >> Wait the timer, if any, >> The download button will appear >> Click download)

Thank you ENigma885. After trying to figure out doing this on my own for a long time, these instructions worked on the first try.

---

### Post by Kosimo on 2008-09-24
Getdeb is also offering fresh audacious 1.5.1 .deb compilations for 32 and 64 bits.

[http://www.getdeb.net/app/Audacious](http://www.getdeb.net/app/Audacious)

---

### Post by ENigma885 on 2008-09-24
> **Kosimo said:**
> Getdeb is also offering fresh audacious 1.5.1 .deb compilations for 32 and 64 bits.

[http://www.getdeb.net/app/Audacious](http://www.getdeb.net/app/Audacious)

The GetDeb Audacious Plugins package is **not** complete ...it lacks many plugins included in the original Audacious Plugins source code.

I provided a debianized package of the original Audacious Plugins *(see my previous post)*

---

### Post by Kosimo on 2008-09-24
> **ENigma885 said:**
> The GetDeb Audacious Plugins package is **not** complete ...it lacks many plugins included in the original Audacious Plugins source code.

I provided a debianized package of the original Audacious Plugins *(see my previous post)*

I didn't know that (as I couldn't install it yet) Strange, as usually getdeb offers good compilations. 
Thanks for the information.

---

### Post by ENigma885 on 2008-09-25
> **Kosimo said:**
> I didn't know that (as I couldn't install it yet) Strange, as usually getdeb offers good compilations. 
Thanks for the information.

The problem is that Ubuntu splits the plugins package into two packages :
plugins and extra plugins..

At the time i posted the previous reply they provided only the plugins package and not the extra one. But now they fixed that and both of the packages are available there.

---

### Post by Technoviking on 2008-09-25
> **ENigma885 said:**
> 
**1.** Download and install the *_libmcs1 0.7.1_* package from Ubuntu Intrepid repository [[COLOR="Red"]**HERE**[/COLOR]]("http://yu.archive.ubuntu.com/ubuntu/pool/universe/m/mcs/libmcs1_0.7.1-1_i386.deb").
it doesn't conflict with other packages at least for me under Hardy.


Mixing packages from different version of Ubuntu can be dangerous. I would suggest asking the Ubuntu Backport team to backport this version into Ubuntu 8.04.

---

### Post by ENigma885 on 2008-09-26
HEY Guys 
i've just made a mini-guide to Equalize ur music with Audacious 
If u wanna take alook =)

[[COLOR="Red"]**[SIZE="3"]_*HOW TO: Equalize Your Music*_[/SIZE]**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5857956#post5857956")

if u have other thoughts plz let me know

---

### Post by Nerdriot on 2009-01-10
So I've tried installing libmcs, which installed fine, but when I run ./configure on the source for Audacious 1.5.1, it complains:

```
configure: error:
Cannot find libmcs! If you are using binary packages based system, check that you
have the corresponding -dev/devel packages installed.

```

I suppose I need the libmcs-dev package, but I can't find it (bleh).

Also, when I try to install it from GetDeb, it says:

> Error: Dependency is not satisfiable: audacious-plugins

Any idea what that means? :O

---

### Post by Kosimo on 2009-01-10
> **Nerdriot said:**
> So I've tried installing libmcs, which installed fine, but when I run ./configure on the source for Audacious 1.5.1, it complains:

```
configure: error:
Cannot find libmcs! If you are using binary packages based system, check that you
have the corresponding -dev/devel packages installed.

```

I suppose I need the libmcs-dev package, but I can't find it (bleh).

Also, when I try to install it from GetDeb, it says:



Any idea what that means? :O

If you're using Intrepid (8.10) You can get audacious 1.5.1 from official repos. Open a terminal and type: ```
sudo apt-get install audacious
```

---

### Post by Nerdriot on 2009-01-10
I'm using Hardy right now. I probably should update, but I've put it off.

---

### Post by flapane on 2009-01-30
I succesfully compiled it on 7.10 i386
I would put the deb packages here, but I won't until I solve this bug, to understand if I have to recompile it:
Mp3 files can't play if you double click it
[https://answers.launchpad.net/ubuntu/+source/audacious/+question/49545](https://answers.launchpad.net/ubuntu/+source/audacious/+question/49545)

---

### Post by krieggegenpaz on 2009-02-22
I am running Intrepid and I have the version from the official repositories installed. But if I go look into the visualization plugins (which are supposed to include ProjectM according to the Audacious site), ProjectM is not there. I also pulled down the source and when I run ./configure, it gives me this as part of its output:

```
  Visualization
  -------------
  Blur Scope:                             yes
  Spectrum Analyzer:                      yes
  Paranormal Visualization Library:       yes
  projectM 0.x (GL milkdrop):             no
  projectM 1.x (GL milkdrop):             no
  RootVis plugin:                         yes
```

I really, really want to get ProjectM up and running and I was wondering if there is anyone out there that has it working with Audacious, or even some other media player on Ubuntu. I'm not picky, I just want to see this visualization plugin to see how it compares to Milkdrop.

---

### Post by Kosimo on 2009-03-02
Guys... Is Audacious Dead?
It's been almost one year without any new version, and I'm wondering if they are still working on Audacious 2.x using mercurial.

Anyone has any info?

---

### Post by andrewabc on 2009-03-02
Does look inactive

[http://redmine.atheme.org/](http://redmine.atheme.org/)

---

### Post by ibabob on 2009-03-02
I'm also wondering if audacious is still active because the removed several pages from their website and I remember they used to have a news post on there saying that 1.5.1 was the final release and will no long be supported to work on 2.0 instead.

But no updates since...

I hope its still alive cause I love this player but with each new version of Ubuntu, its gets more unsatble for me !

---

### Post by BoyOfDestiny on 2009-03-02
> **Kosimo said:**
> Guys... Is Audacious Dead?
It's been almost one year without any new version, and I'm wondering if they are still working on Audacious 2.x using mercurial.

Anyone has any info?

The mercurial version is being updated, as of writing this post, it's been an average of 10 days without an update (hardly a dead project...) 

[http://atheme.org/](http://atheme.org/)

It's worth dropping in their irc channel, if you like to see what's up.

---

### Post by flapane on 2009-03-12
ah great, I'm glad to see that Audacious isn't dead.
So is that sort of svn (redmine) centered on version 2?

---

### Post by nenolod on 2009-04-16
2.0 alpha1 is out on the website, if anyone cares. I released it a few hours ago.

Apologies on the length of time this has taken, but we wanted to be sure that a lot of design flaws from the XMMS days (which caused significant performance issues) were squashed entirely.

---

### Post by Kosimo on 2009-04-17
> **nenolod said:**
> 2.0 alpha1 is out on the website, if anyone cares. I released it a few hours ago.

Apologies on the length of time this has taken, but we wanted to be sure that a lot of design flaws from the XMMS days (which caused significant performance issues) were squashed entirely.

Auauuuu!!!!

Finally!!!   Gonna try it right now!!!

Thanks for the heads up!

---

### Post by Kosimo on 2009-04-17
> **nenolod said:**
> 2.0 alpha1 is out on the website, if anyone cares. I released it a few hours ago.

Apologies on the length of time this has taken, but we wanted to be sure that a lot of design flaws from the XMMS days (which caused significant performance issues) were squashed entirely.

Installed, but can't run it

```
Desktop/audacious/audacious-2.0-alpha1$ audacious2
Warning: no hook found for "playlist create"
audacious2: unable to launch selected interface skinned
cosimo@none:~/Desktop/audacious/audacious-2.0-alpha1$ 

```

---

### Post by Twitch6000 on 2009-04-17
> **nenolod said:**
> 2.0 alpha1 is out on the website, if anyone cares. I released it a few hours ago.

Apologies on the length of time this has taken, but we wanted to be sure that a lot of design flaws from the XMMS days (which caused significant performance issues) were squashed entirely.

OH YEAH BABY =D.
Time to test this.

---

### Post by flapane on 2009-04-17
Just compiled and debianized the 2.0 alpha and its plugins on hardy i386 (it is supposed to work on newer versions) at [nix.flapane.com]("http://nix.flapane.com") in Ubuntu folder.
edit: detailed post, translation on the left sidebar: [link]("http://www.flapane.com/blog/2009/04/audacious-20-alpha1-appena-rilasciato-e-compilato-il-deb-per-ubuntu/")

---

### Post by flapane on 2009-05-10
Just compiled at the same post above the audacious 2.0 beta version, released yesterday.

---

### Post by Kosimo on 2009-05-10
> **flapane said:**
> Just compiled at the same post above the audacious 2.0 beta version, released yesterday.

Thanks for the job! :)

Does this includes all extra plugins as well?

---

### Post by flapane on 2009-05-10
Hi, yes except last.fm for which I needed a lot of libs and I didn't have enough space. It will probably be included when the stable version will come out.

---

### Post by LightB on 2009-05-10
I kind of miss highlyadvanced plugin, doesn't seem to be supported in the new alpha.

---

### Post by infoseeker on 2009-05-10
Just installed it (from the repos, 1.5.1).  I got no sound from pulse audio, but OSS and ALSA both work fine.  I didn't try any of the other options.

I enabled the mixer and thought it wasn't working and screwed up the volume....I thought people in the states possibly heard my music.  There is a bit of a delay  :)  Dire Straits/Brothers in arms sounds pretty good on it.

---

### Post by nenolod on 2009-05-11
> **LightB said:**
> I kind of miss highlyadvanced plugin, doesn't seem to be supported in the new alpha.

HighlyAdvanced plugin is supported, but it has never shipped with Audacious itself due to being horrible code. You need to pull it from my HG repository (hg clone [http://hg.atheme.org/users/nenolod/highlyadvanced/](http://hg.atheme.org/users/nenolod/highlyadvanced/) highlyadvanced), and rebuild it. Then Audacious2 will pick it up.

---

### Post by The Bright Side on 2009-05-23
Hey, this is the first time I compile any program myself, and I've made it pretty far... Audacious 2.0.1 is actually installed, but I cannot run it. Here's what I get:

/home/thebrightside/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
audacious2: unable to launch selected interface skinned


Also, the plugins don't have their own readme for installation, and when I try ./configure in the plugins directory, I get the following:

[...]
checking for DBUS... no
configure: error: Cannot find dbus-glib >= 0.60


Any ideas for a beginner?
Thanks!

---

### Post by The Bright Side on 2009-05-24
Meh. All this compiling from source is really frustrating... I had to post for help and some great guys walked me through it, installed about 100 MB of libraries just to be able to compile and install that 8 MB program from source, I got tons of error messages in the process and ended up with a player that loaded, but didn't accept my music files or playlists. I spent several hours on this during my day. I just gave up and re-installed 1.5.1 through Synaptic.

Is compiling from source always such a hassle?

---

### Post by BoyOfDestiny on 2009-05-24
[QUOTE=The Bright Side]
Is compiling from source always such a hassle?[/QUOTE]

No, once you have all the libraries etc installed, it is usually nothing more than

./autogen.sh
./configure
make
sudo make install

This can be automated via a bash script or cut n' pasted.

If you still want help with 2.0.1, just post. 

You can have 1.51 and 2.0.1 installed at the same time btw.
the latter being run with the bin "audacious2"

---

### Post by The Bright Side on 2009-05-24
Thanks! Yeah, but I had some trouble finding out which libraries I need, it seems I need lots more than the readme file says (plus, the plugins don't even have their own readme). When I ran ./configure, I got a bunch of messages during the very long process, but I couldn't make sense of all of them. Right now, my problem is removing the half-broken installation of Audacious 2 I have on my system so I can start again. Or should I just try installing it again over the broken one?

Which libraries did you use to get it running with all plugins?

Thanks!

---

### Post by BoyOfDestiny on 2009-05-24
I've had them installed for a while. For sure you want the latest libmowgli and libmcs.
You can definitely install on top without problems.
Here are some off that I remember (if you already have some of these, don't worry it won't need to re-download or reinstall)

```
sudo apt-get install mercurial build-essential automake autoconf libresid-builder-dev libdbus-1-dev libbinio-dev libgtk2.0-dev libsamplerate0-dev

```

After that, these will create 2 directories and pull the code straight from the repositores.

```
hg clone http://hg.atheme.org/libmcs/ libmcs
hg clone http://hg.atheme.org/libmowgli/ libmowgli
```

Do the regular thing, 
```
cd libmcs
./autogen.sh
./configure
make
sudo make install
```

and that whole deal, install, and do the same for the libmowgli directory

Now try to build and install audacious, then go for the audacious-plugins,

as nenolod said in a previous post,

```
hg clone http://hg.atheme.org/users/nenolod/highlyadvanced/ highlyadvanced
```

If you want that plugin (for gameboy advanced music rips)

If everything build and installs without error, but doesn't run
```
sudo ldconfig
```
Should do the trick.

Good luck. 
BTW, if any errors like that dbus not found, search synaptic for libdbus and -dev. So to invent an example here, let's say "whatever" was missing. Search for "whatever" or "libwhatever", and grab one suffixed -dev. Then try configure again.

---

### Post by a.sarkar on 2009-08-02
Hi all. Using audacious 1.5.1 version on hardy downloaded from 
[http://www.getdeb.net/app/Audacious](http://www.getdeb.net/app/Audacious)

As Kosimo has pointed out, if this version of audacious is closed and opened again, it starts playing the old playlist. I have found a work around this. This post is about that.

*) First the installation how-to. 
Download all the dependencies:

```
sudo apt-get install ladcca2 libbinio1c2 libcddb2 libfluidsynth1 libjack0.100.0-0 libmcs1 libmowgli1 libneon27-gnutls libresid-builder0c2a libsidplay2
```Then download the debs from the above website. Open a terminal where you have saved them and run the command 

```
sudo dpkg -i audacious_1.5.1-1~getdeb1_i386.deb audacious-plugins_1.5.1-1~getdeb1_i386.deb audacious-plugins-extra_1.5.1-1~getdeb1_i386.deb libaudclient1_1.5.1-1~getdeb1_i386.deb libaudid3tag1_1.5.1-1~getdeb1_i386.deb
```*) Solving the bug.
So audacious 1.5.1 is installed. Now to solve the above mentioned bug. Copy the code below in a file and name it "kaudacious". (I am using konqueror as file manager. Hence the "k".)

```
#!/bin/bash

## For Audacious 1.5.1
Version=$(audacious -v | awk '{print $2}')
if [ "$Version" != "1.5.1" ];then
    echo "Kaudacious: Support for audacious 1.5.1 version only."
    exit 1
fi

ScriptName=$(basename $0)
## Check whether audacious is already running or not
CheckAudacious=$(ps -A | grep audacious | grep -v "$ScriptName")

if [ -n "$CheckAudacious" ] ; then
#   Audacious is running

    Status=$(audtool playback-status)
    if [ "$Status" = "playing" ];then
#       Audacious is already playing music; Append
        audacious -e "$@"
    else
#       Audacious is paused/stopped; Append and play
        audacious -p -e "$@"
    fi

else
#   Audacious is not running
    rm -f ~/.config/audacious/playlist.xspf
    audacious &
    sleep 2s
    audacious -p "$@"
fi

```Save the file and exit. Make it executable and move it to your bin directory.

```
chmod +x kaudacious
mv kaudacious ~/bin/

```Now use kaudacious to open your audio files or playlist. Should work. Comments and suggestions welcome.

P.S. If you are using konqueror as file manager then you can create another file
"kaudacious.desktop" with the following code.

```
[Desktop Entry]
Name=Kaudacious
Comment=Wrapper script for audacious player version 1.5.1
Exec=kaudacious %U
Icon=audacious
InitialPreference=1
MimeType=application/x-ogg;audio/mp3;audio/mpeg;audio/mpegurl;audio/prs.sid;audio/x-flac;audio/x-it;audio/x-mod;audio/x-mp3;audio/x-mpeg;audio/x-mpegurl;audio/x-ms-wma;audio/x-musepack;audio/x-s3m;audio/x-scpls;audio/x-stm;audio/x-wav;audio/x-xm;application/ogg;audio/x-vorbis+ogg
Terminal=false
Type=Application
```Now save this file and move it to ~/.local/share/applications/ folder. This will link your audio files to kaudacious. Use konqueror to make it the default for audio.

That should do it. Happily using audacious.:D

---

### Post by flapane on 2009-09-21
Just waiting for 2.2 to be stable in order to compile it...

---

### Post by flapane on 2009-11-12
2.2beta2 compiled as usual
[LINK]("http://www.flapane.com/blog/2009/04/audacious-20-stable-appena-rilasciato-e-compilato-il-deb-per-ubuntu/")

---

### Post by oomingmak on 2009-11-12
> **flapane said:**
> 2.2beta2 compiled as usual
[LINK]("http://www.flapane.com/blog/2009/04/audacious-20-stable-appena-rilasciato-e-compilato-il-deb-per-ubuntu/")
Thanks.

Does this have all the dependencies?

---

### Post by flapane on 2009-11-12
Too lazy to do it, atm, sorry :)

---

### Post by Kosimo on 2009-11-15
> **JPorter said:**
> Kosimo,

I have the same behavior. No clue why this happens. It works normally once Audacious is running, so it's not a global change in command line parsing for the app... pretty odd.  Luckily it doesn't affect the performance, so it's not much of an issue for me.  

I suppose this is the sort of thing that will (should?) be ironed out prior to final inclusion in the Ubuntu repositories.

Hi

This issue was solved to me by using official ubuntu repos (and some update as well). 

What version of ubuntu are you using?

---

### Post by flapane on 2009-11-26
Audacious 2.2 stable has just been compiled and uploaded in my repo

---

