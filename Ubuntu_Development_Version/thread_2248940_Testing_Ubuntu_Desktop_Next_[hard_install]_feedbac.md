---
title: "Testing Ubuntu Desktop Next [hard install] feedback"
date: 2014-10-18
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-10-18
Updates rolling in , log on becoming even smoother and some apps now loading readily. Even an Ubuntu Feedback app directly to NickSkaggs :)

[https://www.youtube.com/watch?v=1UyQLLpXt6s](https://www.youtube.com/watch?v=1UyQLLpXt6s)

---

### Post by grahammechanical on 2014-10-18
I installed the daily image of the 16th and it now runs on Nouveau, which my updated version did not. I installed using the US keyboard and I can now type numbers and the full stop. So, I can login in to the forums. Browser works well. Click packages install.

I would like to find a way of importing audio files to test out the music app. I thought of copying and pasting from another Ubuntu install into the music folder of desktop next but there is no music folder. There is a home folder and in it a username folder which is empty apart from some hidden folders and files. Where does this version store user documents and files? In the cloud?

I tried using Browser to play a BBC radio station. The web site said I needed to install an app from the Android app store.  And the link to it is of course broken. I doubt if the app would have worked anyway.

I was able to play some music using GroveShark in Browser. Each app runs on it own "surface." Slide the surface off screen and the app gives up system resources. With Groveshark the music stopped playing. So, that bit works.

Some of the Touch apps that we experimented with a few months back are not present and some of the apps that are present have been redesigned.  The ability to slide apps off and on screen as we need them might do away with the need for workspaces.

Edit: Just a thought. Mir seems to have the potential for fancy effects.

Regards.

---

### Post by ventrical on 2014-10-18
Some of the old mir commands work in terminal.

```

ps aux | grep unity-system-compositor

```

 I installed mc (midnightcommander) and that works from terminal showing the directory structure and then I installed gnome-terminal and razorqt but as fate would have it, it will not work on mir but will auto roll to xorg. This is where I have to be careful because I do not want to break the unity-ubuntu-desktop next.

 If you install razorqt and load gnome-terminal you can type  unity8  and it will load up but soon as you try something , a swipe or gester on the iPhone and it will crash  but will not hurt the unity8 install.

Then .. just for fun .. if you type in ' gnome-terminal' at the cli after Ctrl+Alt+F1 it will give a very odd 'mir' report as if it is waiting for somthing.


So...

1. Installing gnome-terminal will not break ubuntu-next
2. Installing razorqt will not break ubuntu-next
3. Entering 'gnome-terminal' at cli gives a very odd or new report about what mir is doing
4. ps aux | grep unity-system-compositor  will still give report that "mir" is running .. etc.. 
5. mc reports directory structure from cli or gnome-terminal when run on razorqt


Regards..

---

### Post by grahammechanical on 2014-10-18
What terminal is that? I get network error when I ty to install the terminal app in the app store. Ctrl+Alt+T does not work. Ctrl+Alt+F2 gets me to a terminal but Ctrl+Alt+F7 get me to a blackscreen. Did you use recovery mode to install an MC? Regards

---

### Post by ventrical on 2014-10-18
*edit* This may or may not break your break your ubuntu-desktop-next.

 I logged on via unity greeter.  I have to log on twice. Once in unity-greeter and then once in unity8. To get to Ctrl+Alt+F1 terminal you can do it either after  you log on from greeter or after you log in to unity8.

 It should give you terminal;

Then

```

sudo apt-get install mc

sudo apt-get install gnome-terminal

sudo apt-get install razorqt

sudo apt-get install htop

```

Mir is running in the background. To verify enter at the cli (command line interface)

```

ps aux | grep ubuntu-system-compositor

```

you will get verbose report (I could not capture it but is similar to reports that we have been been getting with early adopter.

Now , when I type in :

```
 
gnome-terminal


```

I get results:

```

gdk_mir_display_open
Failed to connect to Mir:Failed to send message to server: Broken pipe.
Failed to parse arguments:Cannot open display:

```

 but ubuntu-desktop-next is still working.

  I know this is  not a relevant experiement. I was just trying to  experiment and see what was happening . It may or may not eventually break install so I don't want others to break their installs.

The Failed to connect, Failed to parse are new messages after my last reboot. Perhaps this happened after I chose razorqt desktop, logged on and opened gnome-terminal and ran 

```

unity8

```

I am just curious to see whats going on behind the scenes.  The terminal app from the developers section of unity8 will not install correctly .. so it's kind of like we are working in the dark so to speak. So I am trying other things to see if I can see what mir is up to :)

Regards..

---

### Post by ventrical on 2014-10-18
ok... what happened here is that when I use Ctrl+Alt+F1 after logging on to unity8, unity8 session gets bounced to VT-8 (Ctrl+Alt+F8) and the other 7 terminals are all working so you can run commands at the terminal (but you have to log in to each terminal seperately).. ie; I have mc on one terminal, htop on F4 etc... and I am now downloading xmonad to see if I can start that from one of the terminals .. so there is lots of activity going on here with mir and unity8 .. especially multiple  VTs working simultaneously.

Regards..

---

### Post by grahammechanical on 2014-10-18
Remember the devel software sources we were mucking about with some months ago? Well, there is a devel channel for updating ubuntu touch. Desktop Next is on the standard utopic sources list of any Utopic install. I am going to try moving one of my two desktop next installs on to devel and see what happens. I will be in touch.

Regards.

---

### Post by ventrical on 2014-10-18
> **grahammechanical said:**
> Remember the devel software sources we were mucking about with some months ago? Well, there is a devel channel for updating ubuntu touch. Desktop Next is on the standard utopic sources list of any Utopic install. I am going to try moving one of my to desktop next installs on to devel and see what happens. I will be in touch.

Regards.

@graham That is going to be interesting Good luck !

 Ok .. getting late here. Just wonder if you recall off hand those commands that we had to enter into terminal when testing unity8 from gnome terminal. I just plumb forget :)  It was an environ setting of some sort.

  I'll search it later

Regads..

---

### Post by grahammechanical on 2014-10-18
It failed. 101 network unreachable. That repository is not longer around, apparently. Back to the drawing board.

Regards.

---

### Post by ventrical on 2014-10-21
> **grahammechanical said:**
> It failed. 101 network unreachable. That repository is not longer around, apparently. Back to the drawing board.

Regards.

 I changed my sources.list on one utopic install to /vivid/ to no ill effect so far.

Regards..

---

### Post by zika on 2014-10-22
> **ventrical said:**
> I changed my sources.list on one utopic install to /vivid/ to no ill effect so far.
Regards..Did You check if there is anything available in that branch of that tree?
For example: [http://archive.ubuntu.com/ubuntu/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/) ...

---

### Post by grahammechanical on 2014-10-22
> [COLOR=#000000]Did You check if there is anything available in that branch of that tree?[/COLOR]

I was wondering the same thing but then I reasoned that there is nothing say a new cycle repository can only be set up after the old cycle is completed. Do these new URLs bring in updates? There will not be much going on with Vivid right now anyway. But that does not necessarily mean that developers not directly involved with getting Utoptic out the door get a couple of weeks of doing nothing.

Regards.

---

### Post by ventrical on 2014-10-22
> **zika said:**
> Did You check if there is anything available in that branch of that tree?
For example: [http://archive.ubuntu.com/ubuntu/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/) ...

No . There is nothing except /devel/proposed .. but that is not the point. I just wanted an extra hdd set up and ready for when the toolchain  is uploaded .

Regards..

---

### Post by ventrical on 2014-10-22
> **grahammechanical said:**
>  But that does not necessarily mean that developers not directly involved with getting Utoptic out the door get a couple of weeks of doing nothing.

Regards.

 That is basically my point.  I have so much extra hardware - so  I just like to have an hdd ready for when that branch does open up .. and who knows .. it may come  sooner than we expect.

---

### Post by zika on 2014-10-22
Have fun. Whatever.

---

### Post by jerrylamos on 2014-10-22
Kind of running.  Usual mixup trying to get password to sign in.  Using USB because next has exactly the same iso name as utopic so booting off the hard drive won't work no way to distinguish them.  So far Next, Utopic Unity, and Lubuntu all use the same iso name.

---

### Post by jerrylamos on 2014-10-22
Browser is up full screen.  How do I reduce the window size to get another window open?

---

### Post by jerrylamos on 2014-10-22
For that matter, how to close the browser?

I guess the best part Next even ran, browser anyway to do these postings.  Some time ago I couldn't get anywhere with MIR.

All of August and beginning of September Utopic Unity/compiz crashed trying to start the desktop on this Intel Core 2 Duo 3 gHz.  Finally the bug bothered one of the key canonical people so Unity got fixed and compiz didn't crash.

---

### Post by grahammechanical on 2014-10-22
> [COLOR=#000000]Browser is up full screen. How do I reduce the window size to get another window open?[/COLOR]

We don't. I am not using Desktop Next at the moment. So, this is coming from memory. At the top right of the application window there is an icon of three horizontal lines. That has a menu which will let us open a new tab or show all our open tabs. That is how we switch tabs in Browser. I think.

I have yet to find a way of closing any application. I do not think that we do. We slide from the right to see a vertical stack of "surfaces", each with an application on it. We then select an already loaded application. I understand that once a surface is off screen the application on it gives up system resources.

Regards.

---

### Post by ventrical on 2014-10-22
> **zika said:**
> Have fun. Whatever.


Don't worry. I will. :)

---

### Post by Mateusz Stachowski on 2014-10-22
> **jerrylamos said:**
> Browser is up full screen.  How do I reduce the window size to get another window open?

 At this stage of development Unity 8 doesn't do windows at all so the applications will open fullscreen and in sidestage (apps opened on the right edge).

You can close applications by sliding from the right edge to get vertical stack of surfaces (which grahammechanical already mentioned) and then you just slide the app down or up both will result in closing it.

Here is a video showing app closing on phones but it works exactly the same in Unity 8 desktop session. Note that apps aren't rendered in realtime (they are suspended).

[https://www.youtube.com/watch?v=n0qvKnGvCiA](https://www.youtube.com/watch?v=n0qvKnGvCiA)

---

### Post by grahammechanical on 2014-10-22
Now, that is a real neat way to close an app. Thank you

---

### Post by jerrylamos on 2014-10-23
> **grahammechanical said:**
> Now, that is a real neat way to close an app. Thank you

We've been on pc's since 1982 we can do what we want to.
On phones we just do communication so we're pretty ignorant on the myriad quirks nnumerable apps use.  
My view the developers have to do absolute handsprings to accommodate the very limited physical size & capabilities of the phones. 
I'm not at all sure how ubuntu and microsoft will do on forcing these quirks onto the high function pc's.

So I'm keeping an eye on Next to see whether I can make any comfortable use out of it.

---

### Post by ventrical on 2014-10-23
> **jerrylamos said:**
> We've been on pc's since 1982 we can do what we want to.
On phones we just do communication so we're pretty ignorant on the myriad quirks nnumerable apps use.  
My view the developers have to do absolute handsprings to accommodate the very limited physical size & capabilities of the phones. 
I'm not at all sure how ubuntu and microsoft will do on forcing these quirks onto the high function pc's.

So I'm keeping an eye on Next to see whether I can make any comfortable use out of it.

+1

  I think if apps like gnome-system-monitor and gnome-terminal  and gedit and other  conventional ubuntu apps were intergrated with unity8 then it could be very useful on the desktop - but I think the plan is to sneak in a 'mode' switcher and just give the option of  unity8 phone_emulator or unity-desktop emulator.

  All through  this unity8 fanfare  I have found a neat little desktop experience called razorqt which does everything and is very low on resources. But that's another topic.  This then leads  me to  ask the question of whether  'mir' will exclude all the other DEs and only include the unity8 DE, meaning to say that the other DEs will have convergence option for an xmir type mode switcher ? If this is the case .. then I guess I really don't get the whole idea of  convergence at present.

Regards..

---

### Post by grahammechanical on 2014-10-23
The developers have said that 16.04 will default to Unity8 but with a Unity7 option. So, although the flavours do not use Unity the Xserver and lightDM code will still be in the Ubuntu 16.04 archives, surely.

Which reminded me of unity8-desktop-session-mir. I have just installed it to see if things are any better. I am on Nouveau and all I get is black screen. It is a pity. This could be a useful way to get users familiar with Unity 8 and avoid them getting a shock when they install 16.04. But as it stands session Unity8 is not worth the hard disk space.

I guess the developers of the flavours will have to make some hard choices over the next 12 - 18 months. Stay with Xserver. Go on Mir. Go with a Wayland compositor. This is the work that Gnome is doing. So, I guess we know which direction Ubuntu Gnome has to go in. But when to make the switch?

[https://wiki.gnome.org/ThreePointEleven/Features/WaylandSupport](https://wiki.gnome.org/ThreePointEleven/Features/WaylandSupport)

[http://blogs.gnome.org/mclasen/2014/09/16/a-wayland-status-update/](http://blogs.gnome.org/mclasen/2014/09/16/a-wayland-status-update/)

Either way it all has to be tested.

Regards.

---

### Post by ventrical on 2014-10-23
> **grahammechanical said:**
> The developers have said that 16.04 will default to Unity8 but with a Unity7 option. So, although the flavours do not use Unity the Xserver and lightDM code will still be in the Ubuntu 16.04 archives, surely.

Which reminded me of unity8-desktop-session-mir. I have just installed it to see if things are any better. I am on Nouveau and all I get is black screen. It is a pity. This could be a useful way to get users familiar with Unity 8 and avoid them getting a shock when they install 16.04. But as it stands session Unity8 is not worth the hard disk space.

I guess the developers of the flavours will have to make some hard choices over the next 12 - 18 months. Stay with Xserver. Go on Mir. Go with a Wayland compositor. This is the work that Gnome is doing. So, I guess we know which direction Ubuntu Gnome has to go in. But when to make the switch?

[https://wiki.gnome.org/ThreePointEleven/Features/WaylandSupport](https://wiki.gnome.org/ThreePointEleven/Features/WaylandSupport)

[http://blogs.gnome.org/mclasen/2014/09/16/a-wayland-status-update/](http://blogs.gnome.org/mclasen/2014/09/16/a-wayland-status-update/)

Either way it all has to be tested.

Regards.

 Thanks for the clear up here. For some reason I had the impression that 'mir'  would be able to be used as a sort of virtual machine without having to actually load a virtual machine SW program on top of an Xmir , or even Mir for that matter. So unity7 and gnome-session-fallback  could all take advantage of what Mir has to offer.

Oy.


 "I'm just sitting here watching the wheels go round and round . I really love to watch them roll."

JL

Regards..

---

### Post by ventrical on 2014-10-23
> **grahammechanical said:**
> The developers have said that 16.04 will default to Unity8 but with a Unity7 option. So, although the flavours do not use Unity the Xserver and lightDM code will still be in the Ubuntu 16.04 archives, surely.

Which reminded me of unity8-desktop-session-mir. 

Funny you mentioned that.

```

Done
The following packages have been kept back:
  unity8-desktop-session-mir
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
ventrical@ventrical-MS-7798:~$ 

```

---

### Post by ventrical on 2014-10-24
> **ventrical said:**
> That is basically my point.  I have so much extra hardware - so  I just like to have an hdd ready for when that branch does open up .. and who knows .. it may come  sooner than we expect.


:)

---

### Post by grahammechanical on 2014-10-29
29 October Update to my experiments with Desktop Next.

1) When at the phone UI then Ctrl+Alt +F2 will get us to a Linux command line and Mir will still be running.
2) Ctrl+Alt+F8 will get us back to the phone UI. Thanks ventrical for finding that out.
3) The terminal in the app store does not install and the app store does not have a file manager. But there is a way around this.
4) We can install the PPA of the Touch core apps and that includes the original set of core apps, which are still being actively worked on and they include a terminal and a file manager.

Here is how. Install the PPA

```
sudo add-apt-repository ppa:ubuntu-touch-coreapps-drivers/daily
```

But there is not a core apps PPA for vivid. Not yet. So we need to edit the sources list and change "vivid" to "utopic" The sources list for the PPA is found at

/etc/apt/sources.list.d/ubuntu-touch-coreapps-drivers-ubuntu-daily-vivid.list

Change 

> deb [http://ppa.launchpad.net/ubuntu-touch-coreapps-drivers/daily/ubuntu](http://ppa.launchpad.net/ubuntu-touch-coreapps-drivers/daily/ubuntu) vivid main

to

> deb [http://ppa.launchpad.net/ubuntu-touch-coreapps-drivers/daily/ubuntu](http://ppa.launchpad.net/ubuntu-touch-coreapps-drivers/daily/ubuntu) utopic main

Now we can update/upgrade and run

```
sudo apt-get install ubuntu-filemanager-app
```

It will appear in the phone UI not not in the app store. And it may take a re-start for this to take effect. Maybe not. When I could not find File Manager I restarted and then I found it. Maybe I did not look hard enough. We can find the package names for all these touch core apps here.

[https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/ubuntu/daily](https://launchpad.net/~ubuntu-touch-coreapps-drivers/+archive/ubuntu/daily)

You will notice that there trusty versions and utopic versions of the apps but as yet no vivid versions.

More fun to come.

Edit Update: File Manager works but it can only access the partition Desktop Next is installed on. Terminal gives a vivid purple screen and nothing else. Docviewer crashes.

Regards.

---

### Post by ventrical on 2014-10-30
Thanks grahammechanical. ummmm .I'll be back.. eheheh :)

---

### Post by grahammechanical on 2014-10-30
During yesterday's Ubuntu Engineering team Ubuntu On air session it was said that Terminal (Touch core app) is being completely re-built. So, that is why we cannot download it from the app store and if we do what I have done we get just a purple screen. Ubuntu Touch for devices has not yet moved on to vivid, if I am remembering correctly. Problems with their automatic test system, apparently.

The file manager will let us create folders and I am going to run this test;

1) create a Music folder in /home/user/
2) from another install of Ubuntu copy an audio file to the Music folder
3) see if the Music app detects and plays the audio file.

It is proving impossible to import any file into Desktop Next from other partitions. Of course, none of this is necessary for a phone OS but running on a desktop machine brings in different user needs. And I get the feeling that the developers are looking to these apps as possible replacements for existing utilities.

If I had patience, I would not be a U+1 tester.

Regards.

---

### Post by ventrical on 2014-10-30
@graham

Ok .. I am going to try the procedure that you laid out and see if I can dupe it.

Regards...

Onwards and Upwards..

---

### Post by ventrical on 2014-10-30
It worked here. I had to 'unlock' the filemanager at the lower-middle of the screen but before I did this I moved some pictures into Home/Pictures using the DE razorqt with nautilus, then logged off and log-on to unity8 and was able to get my pics up in the gallery!!  Browser/network is not working again also.  Movies will move into /videos/ directory but Unity8 media player complains  about Unity Scopes and to hook up your iPhone/tablet (er whatever) . Ok .. so I will .. got plenty of pics there:)

  I did get the sources list you referenced :

```

/etc/apt/sources.list.d/ubuntu-touch-coreapps-drivers-ubuntu-daily-vivid.list

```

but the utopic  was already there. So I did not insert:

```

deb [http://ppa.launchpad.net/ubuntu-touc...s/daily/ubuntu]("http://ppa.launchpad.net/ubuntu-touch-coreapps-drivers/daily/ubuntu") utopic main                      

```

It is really looking up!

 Edit:It also recognizes USB dongles and displays those folders but you cannot transfer anything atm..

---

### Post by ventrical on 2014-10-30
Ok . about to test/hookup my Nokia (as it requests phone) and see how the file transfer goes.

Regards..

Edit:

 There are a lot of features behinds the scenes, but it is all about learning the right 'mouse' gestures to get it going. ie; that little notch in the lower bottom of mid screen. Some times you have to hold it a bit longer and then move it to get the different scopes to come up. Even though I transfered a bunch of files from my phone , nothing came up as far as pics or movies that I had recorded but I think they (devs) are hot on this.

Regards..

---

### Post by ventrical on 2014-10-30
Here is a way to have mutiple desktops running in different consoles concurrently. I have it running Ubuntu-desktop and fvwm-crystal but I am going to try gnome - then unity8 on my Core 2 Quad.

[http://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization](http://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization)

---

### Post by grahammechanical on 2014-10-30
@ventrical

there is something i am not clear about. The test where you put some images in the Pictures folder and they were picked up by the Gallery. Is this being done on Ubuntu Desktop Next and did you create that folder? I asked because my test failed. I was able to creae a Music folder in /home/graham and copy an image into it from another install of Ubuntu but the image did not appear in the Music app that I installed from the app store.

I have read that post. It is useful for Xserver systems. Here is something that I do not understand

> [COLOR=#333333][FONT=Helvetica Neue]Once you get past F6, you&#8217;re in X&#8217;s territory. Much like the virtual terminals, each screen starting with F7 is a separate instance of X, which can have its own programs running, independent of the other screens.[/FONT][/COLOR]

In normal Ubuntu the desktop runs in tty7 (Ctrl+Alt+F7). In Desktop Next it runs in tty8 (Crtl+Alt+F8) and it is running on Mir not Xserver. Should we be trying to get an alternative desktop running on tty9 (Ctrl+Alt+F9)? But how? Startx will not work. Or it should not work.

Regards.

---

### Post by ventrical on 2014-10-31
> **grahammechanical said:**
> @ventrical

there is something i am not clear about. The test where you put some images in the Pictures folder and they were picked up by the Gallery. Is this being done on Ubuntu Desktop Next and did you create that folder? I asked because my test failed. I was able to creae a Music folder in /home/graham and copy an image into it from another install of Ubuntu but the image did not appear in the Music app that I installed from the app store.

Basically l what I did was that I had to log off from Unity8  (Desktop-Next) and log on to razorqt. I had installed nautilus earlier and used nautilus to bring up the file directories.  Once there I stuck in a USB with pics and movies and music on it.  I them  dragged 'n dropped pics to the Pictures directory, movies to the Video directory and music to the music directory.  Then I logged off razorqt and logged back om to unity8 Desktop Next.  Once on Desktop Next choose gallery (the video and music scopes are not working) and you can view your pics but the video and music files will not play and those scopes are not working yet.

Also you have to unlock the directory-tool using the bottom/middle little  icon (after you have opened the directory) It will ask you for a password. When I was moving pic files while I was in razorqt session I had to choose /computer/ then home directory  then user_name and then put the pics/videos/music in those directories.
> 


I have read that post. It is useful for Xserver systems. Here is something that I do not understand



In normal Ubuntu the desktop runs in tty7 (Ctrl+Alt+F7). In Desktop Next it runs in tty8 (Crtl+Alt+F8) and it is running on Mir not Xserver. Should we be trying to get an alternative desktop running on tty9 (Ctrl+Alt+F9)? But how? Startx will not work. Or it should not work.

Regards.

  I am about to try that now on Desktop Next and see what happenes. One has to download xinit to be able to use startx and , of course , edit the xinitrc file.  I left a report somewhere here or in another thread that htop reported to me that unity-system-compositor and xorg were running simutaneously. This during my experiment with mc , htop and unity8 all running on different consoles.

Ready to try that today.

Regards..

---

### Post by ventrical on 2014-10-31
Amazing. Unity8 and wmaker running concurrently! When you run gnome-terminal/htop while in wmaker and then switch to unity8 console and then back again real fast you can see X authority and unity-system-compositor both running simultaneously. I guess this is the way to look under the hood of mir and unity8 :)

Regards..

---

### Post by ventrical on 2014-10-31
Using razorqt (much more configurable with gnome programs) and unity8 running concurrently on same install of Desktop Next.

---

### Post by ventrical on 2014-10-31
Here is htop pic. See that unity8 , unity-system-compositor and gnome system-monitor are running .. X is in the backgorund during this shot but it will pop in and out as you move the mouse around.

Regards...

---

### Post by ventrical on 2014-10-31
I am now using the browser in unity8 Desktop Next. It is working just fine. So I am able use firefox between the two desktops, razorqt and unity8 desktop next without any hinderances. Also I can run multiple instances of wmaker on X (only if not running unity8). Of course there would be a memory issue eventually and it would crash. So far .. this razorqt/unity8 concurrent session running 3 hours with no gltiches.

 I just thought I would put up this caveat. When unity8 Desktop Next is running you can only run one other DE in console (which will end up as tty7) but other programs can be run from the other terminals such as mc and htop.

Regards.

---

### Post by ventrical on 2014-10-31
Also this process is hardly using any resources.

```

ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.13 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:       +3.30 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.14 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.04 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      2057 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed: 2481 RPM  (min =  600 RPM, max = 7200 RPM)
POWER FAN Speed:     763 RPM  (min =  600 RPM, max = 7200 RPM)
CPU Temperature:     +25.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +28.0°C  (high = +45.0°C, crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +30.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +30.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +28.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +28.0°C  (high = +84.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +31.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +2.0°C)
                       (emerg = +110.0°C, hyst = +10.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2014-10-31
If you decide to use razorqt as  a DE then  you need to edit your .xinitrc file to:

```

exec razor-session

```

for wmaker

```

exec wmaker

```


I haven't tried with gnome-session yet. Lightdm will not work as it is 'mir' oriented so there is a different command. I'll have to look that up also.

---

### Post by ventrical on 2014-11-01
Yesterdays updates , boot up thismorning equals no Unity8 desktop.

---

### Post by ventrical on 2014-11-01
Fresh install  on same machine -update/upgrade/no ppas .. no unity8.

---

### Post by grahammechanical on 2014-11-11
You may not have noticed but Desktop Next (installed) was broken by an update a few days ago. The switch from LightDM to Mir did not load the UI. But updates over the last few days have fixed that. And I have noticed some improvements.

1) The vertically stacked surfaces of opened apps that a swipe from the left reveals no longer have jagged vertical edges. Big visual improvement.

2) System Settings>Updates actually finds updates to apps. I have yet to test if updating the phone does the same as apt-get. That would indeed be something. 

Regards.

---

### Post by ventrical on 2014-11-12
Yes, I had noticed.  I've been working gnome-desktop iso  bit.  Got some work on xubuntu too. Will certainly check out unity8 updates today.

Regards..

---

### Post by ventrical on 2014-11-12
> **grahammechanical said:**
> You may not have noticed but Desktop Next (installed) was broken by an update a few days ago. The switch from LightDM to Mir did not load the UI. But updates over the last few days have fixed that. And I have noticed some improvements.

1) The vertically stacked surfaces of opened apps that a swipe from the left reveals no longer have jagged vertical edges. Big visual improvement.

2) System Settings>Updates actually finds updates to apps. I have yet to test if updating the phone does the same as apt-get. That would indeed be something. 

Regards.

Yes indeed. back online here.
Edit:

The Feedback app certainly did update when invoked from the settings panel.

Regards..

---

### Post by jerrylamos on 2014-11-13
I'm a bit behind the rest of you folks.

zsync'd the image as of 2013, used Disks to restore image to a USB stick.  Easy and relatively safe.

Booted better - a bit dark so I had to guess where the password window was.  No funny business with password required.

No way to set screen resolution that I could see.  This screen defaults to 1920x1080 very small and hard to read - just fine with 1360x768 I use with vivid.

Web browser ran O.K.  Couldn't find settings such as Synch.

Stay away from the disks icon - it wants to format my hard drives.

Layout still very much for a limited function vertical phone instead of a high function desktop.  

Anyway nice Next worked.  I've had fits with Unity 7 on utopic telling compiz to do things that crashed.

---

### Post by grahammechanical on 2014-11-14
Installed today's daily (14 November). Seen improvements. It now runs off Nouveau as well as Nvidia. And the English UK keyboard bug where pressing Shift would disable numeric and punctuation keys has been fixed. But I have the idea that they fixed it by setting up English US keyboard even though I selected English UK during install process.

I noticed an app in the app store by Nicolas Skaggs (QA team leader) that allows the user to send feedback. No need for a bug report reference. Just the sort of message an uninformed user of the phone could use to give feedback. Nothing to stop us using it either.

From a session in the Ubuntu Online Summit I got the impression that we may be able to use the default desktop applications by next spring. It was something about having a rootless X session running on Mir by then. It does not sem to be top priority at the moment. Too busy with other things. Something to look forward to.

EDIT: @ventrical. I just noticed your earlier post where you got in first with the Feedback app. Never invite feed back or questions. You just might get more than you wanted. :)

Regards.

---

### Post by ventrical on 2014-11-15
> **grahammechanical said:**
> Installed today's daily (14 November). Seen improvements. It now runs off Nouveau as well as Nvidia. And the English UK keyboard bug where pressing Shift would disable numeric and punctuation keys has been fixed. But I have the idea that they fixed it by setting up English US keyboard even though I selected English UK during install process.

I noticed an app in the app store by Nicolas Skaggs (QA team leader) that allows the user to send feedback. No need for a bug report reference. Just the sort of message an uninformed user of the phone could use to give feedback. Nothing to stop us using it either.

From a session in the Ubuntu Online Summit I got the impression that we may be able to use the default desktop applications by next spring. It was something about having a rootless X session running on Mir by then. It does not sem to be top priority at the moment. Too busy with other things. Something to look forward to.

EDIT: @ventrical. I just noticed your earlier post where you got in first with the Feedback app. Never invite feed back or questions. You just might get more than you wanted. :)

Regards.

ehehe .. I was just about to post  to that  :)  ... lol .. actually it was one of the first apps I installed about 2  1/2 weeks ago. I posted it somewhere in here.  It worked from the very start. One of the few that do.  I never got a reply back though after I used the app and sent Mick some feedback .. so perhaps still in template stage I presume.

Regards.

---

### Post by grahammechanical on 2014-11-15
> [COLOR=#000000] never got a reply back though [/COLOR]

I hope they cannot reply. For that would mean they know where we are. That would be a bit scary without voluntarily giving an email address or phone number. Maybe the app is a con. Just giving the pretence of giving us feed back. Now, I am really getting distrustful.

Yes, nurse, I know it is time for my tablets. :)

Regards.

---

### Post by ventrical on 2014-11-15
I actually logged in with SSO!

I need some tablets too. :) lol

I think I'll try again.  Thing is I can't see what's happening behind the scenes. There are no real tools like a gnome-terminal, screenshot or system monitor... we always have to sqwatch out to another console.

sqwatch . (new word) meaning .. I have no idea .. but it just sounded good :)

  We do have a sasqwatch in Canada. Actually my feet are so big that I often refer to myself as a sasqwatch :) lol ... 

Oy .. vey :) .. med time :)



Regards..

---

### Post by ventrical on 2014-11-19
To all concerned.. todays updates -

```

The following packages have been kept back:
  unity8-desktop-session-mir

```

---

### Post by installshield on 2014-11-19
[https://www.youtube.com/watch?v=MXHulRlq10s](https://www.youtube.com/watch?v=MXHulRlq10s)


Here you all go. Have fun...:p

---

### Post by ventrical on 2014-12-14
Recent updates give a new 'Setup' option which leads to a complete fail of the Unity8 desktop. A small screen appears that cannot be managed and if you click the browser it too will pop up as a small screen that cannot be managed in any way.

The Unity side panel appears (as does settings dash .. etc but they are useless in current state.

---

### Post by grahammechanical on 2014-12-15
Try grabbing the application window by a corner and dragging. I have not logged into a Desktop Next hard disk install for a few days but I see the same thing in Unity8 in LXC which I have been trying out and grabbing the corners is the way to resize the application window.

Regards.

---

### Post by ventrical on 2014-12-15
> **grahammechanical said:**
> Try grabbing the application window by a corner and dragging. I have not logged into a Desktop Next hard disk install for a few days but I see the same thing in Unity8 in LXC which I have been trying out and grabbing the corners is the way to resize the application window.

Regards.

Ok.. those same winows (desktop) appears to have trancended  down to the actual unity8 Desktop-next project.  The way to resize windows is very touchy. You have to hold the left mouse key just outside of the window border and jiggle it a bit and then it will grab and resize.  If you click the middle radio button on the current window it will knock back to the hidden unity-panel (like unity7 does) and then when you swipe the left hand side of the screen the panel will come up and then you click the browser and find that you browser session is still live and zoom the browser back open with a click. I'll leave a comment in your other thread you have created.Regards..

---

### Post by ventrical on 2014-12-15
Ubuntu store (apps) now produces nothing.

Regards..

---

### Post by ventrical on 2015-01-13
Latest update will not show systemd in GRub . Also video is 400X600.  Unity8 will appear it is loading through hdd activity LED but nothing happens .. Can get to terminal, recovery ok.

Regards..

---

### Post by grahammechanical on 2015-01-13
Updated my desktop next installs and they got Grub 2.02~beta2-20 with systemd as an advanced option but both installs are now broken after the lightdm login screen. White cursor - black screen. Nothing else.

Regards.

---

### Post by ventrical on 2015-01-14
Thanks for the report-in graham. I'll keep having at it . :)

Regards..

---

### Post by ventrical on 2015-01-14
I rolled back to the 3.16.x-x kernel, updated, got the 3.18.x-9 kernel (would not work with 3.18.x-8) and so systemd option is there and unity8 is working somewhat - no browser but some  action..

Regards..

---

### Post by grahammechanical on 2015-01-14
I used dist-upgrade to bring down some held back stuff. Got the 3.18.x9 kernel and some mir stuff. The switch from lightdm to mir+unity8 UI results in a black screen. This is on an Nvidia driver. Yet to try it on Nouveau. I may put in a new install of the latest daily image.

Regards

---

### Post by ventrical on 2015-01-14
Ok...  I am replying from  the browser in Unity8 Desktop Next.It is the mir default. Systemd is the culprit for unity8 not working.  There have been some large enhancements it appears.  I am using nouveau driver on same nVidia card you have. I am just scouting about here. I am using ff web browser. There is the 'radio button' option which will give you full screen and then also option to hide over in panel to left. <Enter key will not work in editor <as I am doing now>.

---

### Post by grahammechanical on 2015-01-14
I am back in to Unity8 on my install with Nouveau. I used dist-upgrade to bring in the held back stuff including kernel 3.18x9 and unity-system-compositor and other mir stuff. The teminal has improved. We can now use apt-get from inside Unity8 without gioing into a tty. There is a developer mode I am not sure what to do with it.

---

### Post by ventrical on 2015-01-15
> **grahammechanical said:**
> I am back in to Unity8 on my install with Nouveau. I used dist-upgrade to bring in the held back stuff including kernel 3.18x9 and unity-system-compositor and other mir stuff. The teminal has improved. We can now use apt-get from inside Unity8 without gioing into a tty. There is a developer mode I am not sure what to do with it.

Thats news to me. I got to try that. The App store is very limited here on this machine.

Regards.

---

### Post by grahammechanical on 2015-01-15
For weeks I have not had a usable app store. It was like the repository did not exist. Or the internet was out. Perhaps it was being updated. Anyway, the redesigned terminal is called terminal reboot. I had seen developers praising the new terminal but could not get it until a few hours ago.

When I install I do not usually install third party software as I want to run on Nouveau. So, using terminal reboot I installed ubuntu-restricted-extras. What a lot of extras! But it makes Browser much more useful for playing audio and video from a web site. Such as mp3 or mp4 files.

There is a problem when downloading an audio file and getting it to play. Apparently the download happens and Music app is available to play it but there is the error message about being unable to transfer the file.

Unity 8 is still very much a UI for online/cloud storage.

Regards.

---

### Post by pixelro on 2015-01-15
you can change from Desktop mode to Tablet mode on the fly :>> with some QML hacks 

[https://www.youtube.com/watch?v=z1NZr2fQCp0](https://www.youtube.com/watch?v=z1NZr2fQCp0)

---

### Post by grahammechanical on 2015-01-16
I have seen that video from one of the developers on discourse.ubuntu

[http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986](http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986)

I have yet to get the code upgrade on my Desktop Next installs. I suspect that what we are seeing is experimental code that is yet to be approved for merging in the code branch even though the code branch is itself experimental code. I expect things to change over time as different approaches are tried until decisions are made as to which approach gives the desired effect.

I would make Desktop Next my daily work driver if

1) I could run Libreoffice in an Xmir session as shown in the video.
2) Get read and write access to documents and files on other partitions.

I would accept the need to authenticate accessing another partition. In Unity 8 AppArmor profiles lock apps tightly into their containers. That is good security.

Regards.

---

### Post by Mateusz Stachowski on 2015-01-16
> **grahammechanical said:**
> I have seen that video from one of the developers on discourse.ubuntu

[http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986](http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986)

I have yet to get the code upgrade on my Desktop Next installs. I suspect that what we are seeing is experimental code that is yet to be approved for merging in the code branch even though the code branch is itself experimental code. I expect things to change over time as different approaches are tried until decisions are made as to which approach gives the desired effect.

That switching from desktop to tablet mode wasn't done by any of the developers. It's only a QML hack by a curious user which made other such modifications before.

For example this one: [Ubuntu NEXT 15.04 transparency rotation test]("https://www.youtube.com/watch?v=jmSrjTPjs4I").

---

### Post by grahammechanical on 2015-01-16
> [COLOR=#000000]It's only a QML hack by a curious user [/COLOR]

Then what is the point of posting a video of it? Other than saying: "Look what I can do." I think that it is good that someone is curious about what can be done with Mir and Unity 8. I imagine that research like this can lead on to someone writing a Mir/Unity8 tweak tool. I have noticed that with Ubuntu there is plenty of room for community developers to provide added value.

At the moment these videos like a magician's performance. I want to know how to do the magic. They do show that Mir is capable of "eye candy." And that holds promise for the future.

Regards.

---

### Post by ventrical on 2015-01-16
:) Thanks for the migraine  :) lol

---

### Post by Alan F on 2015-01-16
> **grahammechanical said:**
> Then what is the point of posting a video of it? Other than saying: "Look what I can do." 

Isn't that the entire reason that YouTube exists?

---

### Post by ventrical on 2015-03-19
and so on ...

```

The following packages have been kept back:
  unity8-desktop-session-mir

```

---

### Post by zika on 2015-03-19
> **ventrical said:**
> and so on ...

```

The following packages have been kept back:
  unity8-desktop-session-mir

```Just curious: did You see any reason why it is being kept back? (apt and its dist-upgrade, aptitude and its full-upgrade etc.)

---

### Post by ventrical on 2015-03-19
> **zika said:**
> Just curious: did You see any reason why it is being kept back? (apt and its dist-upgrade, aptitude and its full-upgrade etc.)

I used dist-upgrade and it was the only file that was being kept back.  I upgraded this one particular system for another reason (systemD) which I will leave  a comment in appropiate forum.

btw .. I had been checking on unity8 from time to time and it is just a mess (on SandyBridge) ...(is  which machine I got the message from).

Regards..

---

### Post by grahammechanical on 2015-03-19
For several days now I have found Unity8 Desktop Next broken in different ways. The other day I put in a fresh install of a daily image and applications snap out of existence before they load.

The same happened with a fresh install of unity8 in LXC. And I get login screen bounce back when trying unity8-desktop-session-mir. I would like to blame those Redhat developers and their systemd but I cannot. :)

I am now thinking of building a branch of unity8 from the trunk. It is more advanced code but I have to study up on it first.

Regards.

---

### Post by ventrical on 2015-03-19
Thanks for comments..

It's sad because it was working really well there for a while ... but I think in all honesty that most of the ubuntu braintrust and brainstorming is going into systemD ironworks atm because mid Ape-ril  (Bwahahahah .. no pun intended) :)lol, release day is fast approaching and there is some major nVidia breakage and nouveau on nVida adapters also.

---

### Post by cariboo on 2015-03-19
> **ventrical said:**
> Thanks for comments..

It's sad because it was working really well there for a while ... but I think in all honesty that most of the ubuntu braintrust and brainstorming is going into systemD ironworks atm because mid Ape-ril  (Bwahahahah .. no pun intended) :)lol, release day is fast approaching and there is some major nVidia breakage and nouveau on nVida adapters also.

This pretty normal for a development release, we've all been spoiled with the way this testing cycle has gone. For the most part there haven't been any big show stoppers, I have great faith in the devs, they will get things fixed before the final release. :)

---

### Post by grahammechanical on 2015-03-19
Just think, in about 7 weeks we will be converting to <wcodename>. It does not matter to me if things are not quite fixed.

---

### Post by ventrical on 2015-03-19
> **cariboo907 said:**
> This pretty normal for a development release, we've all been spoiled with the way this testing cycle has gone. For the most part there haven't been any big show stoppers, I have great faith in the devs, they will get things fixed before the final release. :)

+1 :)

---

### Post by ventrical on 2015-03-19
> **grahammechanical said:**
> Just think, in about 7 weeks we will be converting to <wcodename>. It does not matter to me if things are not quite fixed.

:)

 Whimsical Wallaby:)

---

### Post by ventrical on 2015-04-09
> **ventrical said:**
> Here is a way to have mutiple desktops running in different consoles concurrently. I have it running Ubuntu-desktop and fvwm-crystal but I am going to try gnome - then unity8 on my Core 2 Quad.

[http://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization](http://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization)

I just wanted to bump this up as the method used will allow you to use another desktop(s) to run concurrently on a single processor using the Ctrl+Alt + F terminal keys. So in a way you can have a virtual 'sidekick' reference desktop if you are doing a research project, excellent for development version and very simple to use.

 So each tty(n) can act as a virtual container , however, the performance may vary from PC to PC.

I am currently running Mate Desktop and Unity Desktop and have had Desktop Next working at one time also. 
Regards..

---

### Post by wukeshi on 2015-04-13
hey,guys,I need your help
I Download a ubuntu 15.04 from [http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)
I know It's unity8
When I install the system and restart it
there is a demo first
slide from the left edge,then slide from the right edge.
BUT I CAN'T DO THAT,THE SYSTEM CAN'T GET THE ACTIVITY
I cant't skip the DEMO,please tell me how to do,
THANK YOU VERY MUCH!:lolflag:

---

### Post by wukeshi on 2015-04-13
[COLOR=#000000]I Download a ubuntu 15.04 from [/COLOR][http://cdimage.ubuntu.com/ubuntu-des...-live/current/]("http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/")
[COLOR=#000000]I know It's unity8[/COLOR]
[COLOR=#000000]When I install the system and restart it[/COLOR]
[COLOR=#000000]there is a demo first[/COLOR]
[COLOR=#000000]slide from the left edge,then slide from the right edge.[/COLOR]
[COLOR=#000000]BUT I CAN'T DO THAT,THE SYSTEM CAN'T GET THE ACTIVITY[/COLOR]
[COLOR=#000000]I cant't skip the DEMO,please tell me how to do,[/COLOR]
[COLOR=#000000]THANK YOU VERY MUCH![/COLOR]:lolflag:

---

### Post by grahammechanical on 2015-04-13
> **wukeshi said:**
> [COLOR=#000000]I Download a ubuntu 15.04 from [/COLOR][http://cdimage.ubuntu.com/ubuntu-des...-live/current/]("http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/")
[COLOR=#000000]I know It's unity8[/COLOR]
[COLOR=#000000]When I install the system and restart it[/COLOR]
[COLOR=#000000]there is a demo first[/COLOR]
[COLOR=#000000]slide from the left edge,then slide from the right edge.[/COLOR]
[COLOR=#000000]BUT I CAN'T DO THAT,THE SYSTEM CAN'T GET THE ACTIVITY[/COLOR]
[COLOR=#000000]I cant't skip the DEMO,please tell me how to do,[/COLOR]
[COLOR=#000000]THANK YOU VERY MUCH![/COLOR]:lolflag:

I have found the same problem on a recent install of Ubuntu Desktop Next. I can usually succeed in the swipe from the left screen edge but just cannot succeed with the swipe from the right screen edge and hence we cannot go beyond this demo into the desktop.

I do not know any solution. Sometimes all we can do wait until problems like this are fixed in later ISO images. You might want to try using Recovery Mode to update/upgrade. Or downloading a newer ISO image to see it is fixed.

Regards.

---

### Post by cariboo on 2015-04-13
Merged two similar threads.

---

### Post by Mateusz Stachowski on 2015-04-13
The devs have a fix ready for that since beginning of April but who knows when it actually lands. There are multiple other approved branches waiting to be merged in Unity 8.

[https://code.launchpad.net/~mterry/unity8/skip-spread-tutorial-on-desktop/+merge/253866](https://code.launchpad.net/~mterry/unity8/skip-spread-tutorial-on-desktop/+merge/253866)

[https://code.launchpad.net/unity8/+activereviews](https://code.launchpad.net/unity8/+activereviews)

---

### Post by wukeshi on 2015-04-13
I got,I will update and upgrade to try again~  Thank you very much

---

### Post by Mateusz Stachowski on 2015-04-14
The updated Unity 8 containing fix for the tutorial among many other fixes and enhancements was released 19 hours ago (according to launchpad) and it is already on todays daily ISO image of Ubuntu Desktop Next and of course in Vivid archives.

[https://launchpad.net/ubuntu/+source/unity8/8.02+15.04.20150409.1-0ubuntu1](https://launchpad.net/ubuntu/+source/unity8/8.02+15.04.20150409.1-0ubuntu1)

---

### Post by QDR06VV9 on 2015-04-15
Tried 4/14/2015 and could not even swipe from Left to right let alone right to left.
Oh well I will try today's iso from [http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)
Later tonight.

---

### Post by Mateusz Stachowski on 2015-04-15
Strange I also tried the 4/14/2015 and didn't have any problems completing tutorial. Also now the tutorial on desktop is just swipe from left edge.

I have other problem with Unity 8 for about a month or maybe more all the texts have a black background or something like that so they are hardly readable. This is with Nouveau.

---

### Post by QDR06VV9 on 2015-04-15
Got bored so today's iso brings
This install was on Acer Laptop.
**Welcome to your New Phone**[-o<
Browser just keeps crashing:-\" but other than that it was interesting.
Scopes worked pretty good(still incomplete)
Import Contacts (Worked):cool:
I am suddenly **excited** to see this on one of my Tablets.(When Complete)
I shot some pics with my tablet no screenshot app yet. Some were a little shaky.(Due to Old fart behind the Camera) Sorry
After maximizing windows it would not close or un-maximize, Navigation with arrow keys.
Boy the mouse is very touchy, non factor on touch device.
But Coming along Oh this won't duel boot with windows on another partition.(At least I could never get to install)
Regards

---

### Post by grahammechanical on 2015-04-15
I have 2 installs of Ubuntu DEsktop Next and I updated both of them in the early hours of this morning. The one running on Nvidia allowed me to get to the desktop. The apps fail to load. That has been a problems for more than a couple of weeks.

The second install runs of Nouveau and is an install from the 8 March with the swipe bug not allowing to get beyond the introduction. I do not know if the update fixed things because it loads to a kernel panic. I will try a new daily image a bit later.

Oh, well, such is life.

Regards.

---

### Post by lgd on 2015-05-09
> **ventrical said:**
> Thanks for the clear up here. For some reason I had the impression that 'mir'  would be able to be used as a sort of virtual machine without having to actually load a virtual machine SW program on top of an Xmir , or even Mir for that matter. So unity7 and gnome-session-fallback  could all take advantage of what Mir has to offer.

Oy.


 "I'm just sitting here watching the wheels go round and round . I really love to watch them roll."

JL

Regards..
Maybe some of you are interested in some information to Xmir on Ubuntu Phone, too. I don't know if it is possible to try the Xmir script and desktop file from the phone on the desktop next on a pc too but you can do some search (maybe in [mir IRC logs like this and older]("http://irclogs.ubuntu.com/2015/05/08/%23ubuntu-mir.html") and experiment a little bit with it:

**[SIZE=2][Re: Currently sold Ubuntu phones: how desktop-like are they really? ]("http://ubuntuforums.org/showthread.php?t=2270341&p=13282294#post13282294")[/SIZE]**


Greetings, lgd

---

