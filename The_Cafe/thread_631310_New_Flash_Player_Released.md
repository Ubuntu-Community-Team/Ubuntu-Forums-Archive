---
title: "New Flash Player Released"
date: 2007-12-04
forum: The Cafe
---

### Post by bpny on 2007-12-04
A new version of the Adobe flash player came out today. Any Opera users try it yet? This new XEmbed-enabled plugin should work with Opera now.[http://blogs.adobe.com/penguin.swf/]("http://blogs.adobe.com/penguin.swf/")

---

### Post by ForzaItalia250 on 2007-12-04
I've just installed it, and it doesn't seem to fully work. It displays images that were formerly not visible, but videos and animations don't work.

I might have installed it wrong though because I have no idea what I'm doing :P

..I guess I'll still need Firefox to watch youtube videos until they get it right :confused:

EDIT: Actually everything is just a gray box instead of something that says I need to install flash player

---

### Post by Polygon on 2007-12-04
> 
A new version of the Flash Player is available. To be specific, this is Adobe Flash Player 9 Update 3, version identifier 9,0,115,0. It is simultaneously available for Linux, Mac, and Windows. The Linux version, as with previous Linux versions, is presently x86_32 only.

This version includes the new Flash support for the standard H.264 and AAC codecs as well as hardware-accelerated fullscreen support (where supported by video hardware and drivers, and specified by a site's SWF). This is also the first official Linux release to support the new XEmbed browser protocol which simply allows a browser plugin on Unix to behave better in a modern desktop environment.

Improvement over the string of beta releases: This new XEmbed-enabled plugin should work with Opera now.


i believe this version also has full screen support. I like :D 

trying it now

works like a charm, fullscreen mode works and now when you right click a flash video, you get a nice gtk+ dropdown list instead of the ugly window's 95 -esque one :D

im happy.

---

### Post by boast on 2007-12-04
no deb :(

see! too many packages for linux

---

### Post by bash on 2007-12-04
You should be able to just alien the .rpm. But more importantly still no 64bit version. :(

---

### Post by Polygon on 2007-12-04
just download the tar.gz file from the adobe website

extract it to desktop

in terminal

cd Desktop

cd install_flash_player_9_linux

./flashplayer-installer

answer the questions, make sure firefox is closed when you install it, and then at the end question say no for no more installations and then your done ;)

---

### Post by boast on 2007-12-04
dang, I still have the same issues as the RC. full screen just opens a small window on the bottom left

---

### Post by FuturePilot on 2007-12-04
I see the freezing issue hasn't been fixed, neither has the wmode transparency problem (Flash overlays Java script). Even worse it's tearing everything to death and it doesn't work in Konqueror  Hmpf [-(

---

### Post by matthewcraig on 2007-12-04
And still no 64-bit support.  Abobe is one of the largest software companies in the world.  For their 64-bit Flash Player, they have been "working on it" for over a year.  So, can we safely say that they are just yanking our chain, yet?  Is there a industry-wide rule-of-thumb where one can say some PR-spin is actually not really being worked on?  Or do we keep our hopes up?  Anyone still hoping for the release of Duke Nukem Forever?  You know, they said it will have support for Ubuntu.  64-bit Ubuntu, too!

---

### Post by mrbungle on 2007-12-04
yeah still no 64bit and still get tons of freezing.  adobe you suck!!! :mad: 

bring back macromedia!!!

---

### Post by hanzomon4 on 2007-12-05
Current flash works in opera for me...

---

### Post by erfahren on 2007-12-05
All I got was grey boxes in Opera with this version. Seems like a step backward. The older Flash 9 version was just buggy for me in Opera. 

Guess I'll go back to using Flash 7 in Opera and Flash 9 in Firefox. That seems to be working best for me.

Edit: I tested out Firefox a little with it and and firefox crashed twice on me. I was on youtube and hit the back button while a video was playing. It didn't with the older version.

---

### Post by chronusdark on 2007-12-07
i was using this on hulu and videos play fine untill you fullscreen them controls become very slow to respond and right click menu stops working also video framrate drops and you get LOTS of video tearing we need vsync or something

---

### Post by master_kernel on 2007-12-07
Will this make it into the Gutsy repos or just Hardy?

---

### Post by artelsj on 2007-12-07
Fullscreen (on YouTube) shows video in a small window, is this a Compiz-related issue? Does a solution exist?

---

### Post by FuturePilot on 2007-12-07
> **chronusdark said:**
> i was using this on hulu and videos play fine untill you fullscreen them controls become very slow to respond and right click menu stops working also video framrate drops and you get LOTS of video tearing we need vsync or something

Yes. I see tearing too. I contacted Adobe about this but they said they couldn't reproduce it.:mad:

---

### Post by daradib on 2007-12-08
This is not a good thing for Ubuntu in many ways, since it will make the installation via flashplugin-nonfree fail due to a md5 mismatch (the package downloads flash player installer from Adobe's website, which has changed).

See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix (and of course an upgrade to the current flash player), do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

Thus you can see that Ubuntu HAS to update the repositories, else Flash won't work at all.

---

### Post by boast on 2007-12-08
> **artelsj said:**
> Fullscreen (on YouTube) shows video in a small window, is this a Compiz-related issue? Does a solution exist?

the solution is to use compiz zoom desktop

:(

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by Polygon on 2007-12-11
> **artelsj said:**
> Fullscreen (on YouTube) shows video in a small window, is this a Compiz-related issue? Does a solution exist?

fullscreen flash videos work, ive tested it, and youtube fullscreen works as well

must be a compiz issue or something else

and ive noticed significantly less crashes with this version then the last one, i think its good overall, and its nice that adobe is getting in the habit of releasing flash for all three platforms at the same time

now all they need to do is get 64 bit working and they will be gold ;)

---

### Post by daradib on 2007-12-11
I do think this new plugin is good, but I think there are certain problems.

> **daradib said:**
> The new version of flash is incompatible with Konqueror because it requires XEmbed ([Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")). 9.0.48.0 is the last version of flash to support Konqueror in its current state. That could cause problems for an update through the repositories. Some sites, including disney.com and nick.com do not load properly. It would be great if someone tests these sites with an older flash plugin and with Windows Flash Update 3.

---

### Post by mstephens on 2007-12-13
Can I use  Flash 9.0.115 with Ubuntu 7.04 ?

The BBC website is now using a Flash version of iPlayer  and it will only do full screen using the latest version (according to the message which pops up when you click on the full screen icon)

I tried using the tar.gz from the Adobe site and their installation instructions but Firefox just keeps crashing when I try to play video. Re-installing  the .48 version using the package manager gets everything working again but of course means back to no full screen.

Having had a bit of a read round the forums I see 9.0.115 is causing various problems and obviously package manager does not know about the new release . So can I actually use it with 7.04 and how do I go about installing it ?

Thanks

---

### Post by daradib on 2007-12-13
> **mstephens said:**
> Can I use  Flash 9.0.115 with Ubuntu 7.05 ?

Yes, you can. See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by minisori on 2007-12-13
This new version is too slow with full screen videos in youtube for example.

---

### Post by daradib on 2007-12-13
> **minisori said:**
> This new version is too slow with full screen videos in youtube for example.

That's odd. I don't have any of those problems. I liked this flash plugin release because full screen YouTube finally works.

---

### Post by jrusso2 on 2007-12-13
Every time I go to a flash site it crashed firefox so I had to go back to the old flash.

---

### Post by hkgonra on 2007-12-13
well the flash I have now is working like crap. 
Should I try to upgrade or not ?

---

### Post by Incense on 2007-12-13
> **hkgonra said:**
> well the flash I have now is working like crap. 
Should I try to upgrade or not ?

If it's working so badly, then what do you have to lose by upgrading? I upgraded on openSUSE and it's working great.

---

### Post by mstephens on 2007-12-14
Ooops. I installed the .115 version properly and it still crashes every time I try to play anything. I assume that it might be something to do with hardware acceleration and the fact I have an ATI Radeon 7500 card using the radeon driver. The problem now is that I don't seem to be able to get back to the  original .48 version. Even reinstalling the package completely doesn't work. Synaptics package manager says it is installed but Firefox still uses the .115 version. I deleted the libflashplayer.so file in the .mozilla/plugins directory but all that happens then is that Firefox sees that flashplayer isn't installed and I end up being pointed back to the adobe site which only lets me install the .115 version again. How do I get back to .48 (or alternatively, is there a way of configuring .115 to behave like .48 )

Edited to add: I've already tried turning off hardware acceleration but it still crashes.

---

### Post by sr20ve on 2007-12-14
> **erfahren said:**
> All I got was grey boxes in Opera with this version. Seems like a step backward. The older Flash 9 version was just buggy for me in Opera. 


All I get are grey boxes in opera with this version and the last one. Flash works fine in firefox, but I like opera better, I just wish I could get the flash to work.

---

### Post by boast on 2007-12-14
are u using the opera 9.5 beta?

---

### Post by erfahren on 2007-12-14
> **sr20ve said:**
> All I get are grey boxes in opera with this version and the last one. Flash works fine in firefox, but I like opera better, I just wish I could get the flash to work.
Flash 7 is much more stable in Opera.  I've actually been experimenting with using Flash 7 in Opera and Flash 9 in Firefox (for the sites that require it). It seems to be working pretty well. Opera doesn't crash on me like it did using Flash 9.

I can tell you how I set that up if you want.

---

### Post by mstephens on 2007-12-15
> **mstephens said:**
> Ooops. I installed the .115 version properly and it still crashes every time I try to play anything. I assume that it might be something to do with hardware acceleration and the fact I have an ATI Radeon 7500 card using the radeon driver. The problem now is that I don't seem to be able to get back to the  original .48 version. Even reinstalling the package completely doesn't work. Synaptics package manager says it is installed but Firefox still uses the .115 version. I deleted the libflashplayer.so file in the .mozilla/plugins directory but all that happens then is that Firefox sees that flashplayer isn't installed and I end up being pointed back to the adobe site which only lets me install the .115 version again. How do I get back to .48 (or alternatively, is there a way of configuring .115 to behave like .48 )

Edited to add: I've already tried turning off hardware acceleration but it still crashes.

Curiously the problem doesn't occur with Youtube (which will also switch to fullscreen) but still nothing works with BBC iPlayer.

Managed to get back to 9.0.48.0 by downloading the full v9 archive from Adobe and manually installing it. For some reason although the package manager says that the9.0.48 has been installed, I couldn't actually find the flashplayer.xpt and libflashplayer.so files anywhere.

---

### Post by sr20ve on 2007-12-15
> **erfahren said:**
> Flash 7 is much more stable in Opera.  I've actually been experimenting with using Flash 7 in Opera and Flash 9 in Firefox (for the sites that require it). It seems to be working pretty well. Opera doesn't crash on me like it did using Flash 9.

I can tell you how I set that up if you want.

Yes, how do you setup flash 7? I checked adobe's download site, but couldn't seem to find the older versions.

---

### Post by erfahren on 2007-12-15
> **sr20ve said:**
> Yes, how do you setup flash 7? I checked adobe's download site, but couldn't seem to find the older versions.
you can get Adobe's Flash 7 installers [from here](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2) (the download is about 32 megs, and includes all versions of Flash 7 for all the OSs. I'd just attach the Linux one here but probably shouldn't since it's nonfree). -- apparently Flash 8 is there too, but someone else suggested Flash 7 so that's what I went with.

Anyway, after downloading the archive to your home or ~/Desktop directory, double-click on the archive to open it in Archive Manager and extract the latest one for Linux (r70). Then extract the libflashplayer.so and flashplayer.xpt from that archive.

at this point all you really need to do is open Nautilus (file browser) with root permissions
```

sudo nautilus

```
and browse to "/usr/lib/opera/plugins" and cut & paste the libflashplayer.so and flashplayer.xpt that were extracted into the opera plugins directory. You can then restart Opera and go to [Adobe's test page](http://www.adobe.com/software/flash/about/) to verify it.

(It may also work if you just create a "plugins" directory in your ~/.opera and put them in there. I've never tried that though.)


**I do it a little differently:**
First let me explain that when the flashplayer-nonfree (Flash 9) package is installed through Synaptic it creates the directory "/usr/lib/flashplayer-nonfree" and puts the libflashplayer.so and flashplayer.xpt (if it has it) in there. It then creates symbolic links to those files in "/usr/lib/firefox/plugins"

When Adobe's installer is used it puts those files directly into "/usr/lib/firefox/plugins" (and "/usr/lib/opera/plugins" if you go through that step with its installer).

[COLOR="DarkRed"]So what I do is this (it seems less "hackish"):[/COLOR]
I first uninstall the flashplayer-nonfree package through Synaptic and make sure the "/usr/lib/flashplayer-nonfree" directory and the symbolic links are gone. 

I then make the directories:
```

sudo mkdir /usr/lib/flashplugin-nonfree-7

```
```

sudo mkdir /usr/lib/flashplugin-nonfree-9 

```
and put the Flash 7 and Flash 9 files in their respective directories (copy & paste using sudo nautilus works for that)
...then create the symbolic links to the files in the corresponding plugins directories
```

sudo ln -s /usr/lib/flashplugin-nonfree-7/libflashplayer.so /usr/lib/opera/plugins

```
```

sudo ln -s /usr/lib/flashplugin-nonfree-7/flashplayer.xpt /usr/lib/opera/plugins

```
```

sudo ln -s /usr/lib/flashplugin-nonfree-9/libflashplayer.so /usr/lib/firefox/plugins

```
(the newest version of Flash 9 doesn't have the flashplayer.xpt )

anyway, that's what I do. 

NOTE: you can put a button in Opera's toolbar to open the current page in Firefox. That comes in handy with that setup when a site requires a newer version of Flash. I've had instructions to do that written out already but haven't posted them. I think I'll do that. I'll post a link here after I do.

---

### Post by imaca on 2007-12-15
> **sr20ve said:**
> All I get are grey boxes in opera with this version and the last one. Flash works fine in firefox, but I like opera better, I just wish I could get the flash to work.

Same problem here, flash used to work (mostly) in Opera but now just grey boxes.
I wish Firefox could zoom pages the way Opera does,- this is the main reason I still use opera and adds huge functionality - especially for people with poor eyesight

---

### Post by daradib on 2007-12-15
> **imaca said:**
> I wish Firefox could zoom pages the way Opera does,- this is the main reason I still use opera and adds huge functionality - especially for people with poor eyesight

Do you mean that it magnifies the whole page, including images and not just increasing font size. If that is so, then you would probably like Firefox 3 (in beta), which has a similar zoom function to that of Internet Explorer (7?).

---

### Post by sr20ve on 2007-12-15
thanks erfahren, works great now.:)

---

### Post by cookies on 2007-12-16
Adobe says that this release makes Fullscreen work, but Fullscreen always worked for me no matter what in both Flash 7 and 9. So, am I missing something, or very lucky?

---

### Post by FuturePilot on 2007-12-16
> **cookies said:**
> Adobe says that this release makes Fullscreen work, but Fullscreen always worked for me no matter what in both Flash 7 and 9. So, am I missing something, or very lucky?

Yeah, I don't know, but full screen works for me with r48 :confused:

---

### Post by cookies on 2007-12-16
I see what they mean now. True fullscreen works now, where there are no window borders or taskbars.

---

### Post by Mateo on 2007-12-16
ohh really,  that's cool.

---

### Post by gaspard.leon on 2008-01-06
ok... I just went to youtube with r48 flash player installed... and clicking full screen button causes a pop-up, which is annoying.

So I went to the adobe site to get the latest version since it reported there is a new one: r115

I installed r115 and it works fine, and I went to youtube and it does fullscreen properly now... (instantly and with no popup)

however... it's so bloody slow it's painful, CPU pegs at 100% and frames are choppy about 4 to 10 FPS and torn and everything...

very annoying.. with a normal youtube-sized video window it's at 66% and video plays smoothly if you don't do anything else...

So who else has tried it, and what are your hardware specifications?

My setup is:
[LIST]
[*]Ubuntu 7.10 with kernel v2.6.23.12 (used KernelCheck to compile it)
[*]Firefox version 3.0b2 (downloaded from mozilla and installed to /opt/firefox)
[*]AthlonXP 2500+ (1.8Ghz) with 2GB of memory, and Geforce 5900XT with 128MB...
[/LIST]

---

### Post by gaspard.leon on 2008-01-06
ok looks like it's a case of DirectX only?

> 
**Will hardware-accelerated scaling work on all computers?**

For hardware-accelerated scaling to work, you need Microsoft® DirectX 9 with VRAM 128 MB on Windows® 2000 Service Pack 4 or higher; for Apple® Macintosh®, OS X v10.2 or higher. There might be compatibility issues with older hardware and drivers such as those with Windows 98. (See Flash Player system requirements.) With older versions of Flash Player, you should not see dramatic changes as the player reverts from hardware-accelerated scaling back to software scaling.


From: [http://www.macromedia.com/support/documentation/en/flashplayer/help/help01.html#117111](http://www.macromedia.com/support/documentation/en/flashplayer/help/help01.html#117111)

---

### Post by vatbier on 2008-04-15
I experience choppy video with youtube videos with Flash Player 9.0.124. 
I had to reinstall 9.0.48 to get decent video play back.
I made a bug report at adobe's new 
 "Adobe Flash Player Bug and Issue Management System": 
 [https://bugs.adobe.com/jira/browse/FP-83](https://bugs.adobe.com/jira/browse/FP-83) 
 "linux Flash Player 9.0.124 plays video with very low frame rates"
 Please vote for this bug (you have to register first).

---

