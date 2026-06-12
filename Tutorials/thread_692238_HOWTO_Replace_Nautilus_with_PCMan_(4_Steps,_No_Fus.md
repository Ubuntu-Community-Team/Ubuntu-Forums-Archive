---
title: "HOWTO: Replace Nautilus with PCMan (4 Steps, No Fuss)."
date: 2008-02-09
forum: Tutorials
---

### Post by SilverWave on 2008-02-09
_________________________________________________

**PCMan works great as a drop in replacement for Nautilus.**

[B][I]PCMan works well with GNOME and has options to "Open Current Folder as root" and also "Open Terminal" .
Its fast, uncluttered and has tabs![/I][/B]

[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)
Features:

    * Extremly fast and lightweight
    * Can be started in one second on normal machine
    * Tabbed browsing (Similiar to Firefox)

Original idea from: [http://lifehacker.com/software/linux-tip/change-gnome-menus-to-use-pcman-file-manager-288616.php](http://lifehacker.com/software/linux-tip/change-gnome-menus-to-use-pcman-file-manager-288616.php)

OS: Ubuntu 7.10
Architecture: 64bit.
_________________________________________________

1. 
Install pcmanfm from the package manager.
> Applications > System Tools > PCMan File Manager

2.
If you find that you like PCMan and want to have "Places" use it instead of nautilus do the following:
Start the PCMan File Manager and go to:
> /usr/share/applications

In PCMan "Open Current Folder as root"
> Tools > Open Current Folder as root.

3.
Make a backup copy of the files below (copy and paste and add  "_bak" on the end of the file name.

> /usr/share/applications/nautilus-computer.desktop
/usr/share/applications/nautilus-folder-handler.desktop

4.
Change the line in each with starts with Exec=
e.g

> For nautilus-computer.desktop: Exec=pcmanfm /
For nautilus-folder-handler.desktop: Exec=pcmanfm %U

Done :)

_________________________________________________
Note: You can go quite a bit further in replacing nautilus if you wish (see gsiliceo's post below) but the steps I have detailed above give the most change for the least effort. ;)
_________________________________________________

[B][UPDATE]
[Old tip - See this post for latest NEWS]("http://ubuntuforums.org/showpost.php?p=7060049&amp;postcount=76")[/B]

---

### Post by gsiliceo on 2008-03-02
To completly replace nautilus follow this steps, they all are reversable and not harmful at all, as long as you make the backups.
[COLOR="DimGray"]
First we need to backup some files[/COLOR]
> sudo cp /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus.desktop.backup
sudo cp /usr/share/applications/nautilus-folder-handler.desktop /usr/share/applications/nautilus-folder-handler.desktop.backup
[COLOR="DimGray"]Then open these files[/COLOR]
> sudo gedit /usr/share/applications/nautilus-folder-handler.desktop 
sudo gedit /usr/share/applications/nautilus.desktop
and replace every nautilus word with pcmanfm (delete the arguments after the word pcmanfm since some are not supported)
And save
[COLOR="DimGray"]
And these changes are for gnome session manager[/COLOR](so ubuntu stops trying to load nautilus)
Backup this file 
> sudo cp /usr/share/gnome/default.session /usr/share/gnome/default.session.backup
Then we need to delete a few lines an change some numbers
> sudo gedit /usr/share/gnome/default.session
[COLOR="DimGray"]Then open it and delete the lines that have at the beggining the same number as the nautilus line
something like this[/COLOR]:
> **2**,id=default2
**2**,Priority=40
**2**,RestartCommand=nautilus --no-default-window --sm-client-id default2
[COLOR="DimGray"]Then rename the other lines so the numbers dont jump from 1 to 3[/COLOR]. 
[COLOR="DimGray"]And from the line[/COLOR]
> num_clients=X
[COLOR="DimGray"]Change the number to the new number of process you just changed.
And save[/COLOR]

If you don't understand i added my file to this post as an attachment so you can compare.

[COLOR="DimGray"]And the most important step to kill nautilis you need to do this[/COLOR] :
> sudo cp /usr/bin/nautilus /usr/bin/nautilus.backup
sudo rm /usr/bin/nautilus
sudo ln -s /usr/bin/pcmanfm /usr/bin/nautilus

Finally, you need to open a PCMan window and go to *edit*, *preferences,* *desktop,* to configure the desktop.
And dont forget to restart the session doing ctrl+alt+backspace

Doing this ubuntu wont ever load nautilus, saving the precious ram and reducing boot time.
I wish you could just uninstall it, but the package is tied to many other important packages.

---

### Post by SilverWave on 2008-03-04
> **gsiliceo said:**
> Your forgot a few files that you ...

I was about to make a how to my self, but i don't like duplicate posts, so i hope you can update yours =D

Updated the howto pointing to your post for the advanced stuff :)

If you get a chance add in a couple of screen shots to your original post.

---

### Post by tad1073 on 2008-03-04
I followed the steps in the first post but nautilus is still opening computer and home from the desktop icons

---

### Post by gsiliceo on 2008-03-04
you have to follow the second post instructions to get rid of nautilus.

---

### Post by tad1073 on 2008-03-04
> **gsiliceo said:**
> you have to follow the second post instructions to get rid of nautilus.
I don't want to remove nautilus until I get pcman opening everything that nautilus opens.

---

### Post by gsiliceo on 2008-03-04
You dont actually delete nautilus you just delete the binary, and you keep a backup, and then you replace all calls to nautilus to pcman, there are just too many files that need to be edited so stuff gets opened with pcman and not nautilus, so this is an ugly but effective and secure solution.

---

### Post by tad1073 on 2008-03-04
can i do the same with thunar, for some reason pcman was causing 100% processor usage while i was editing the files that were posted

---

### Post by gsiliceo on 2008-03-04
I recommend upgrading to the latest version, first uninstall the one you currently have.
> sudo apt-get remove pcmanfm
And get the latest tarball from here:
[http://www.gnomefiles.org/app.php/PCMan_File_Manager]("http://www.gnomefiles.org/app.php/PCMan_File_Manager")
This app has being getting better and better with every upgrade and since the one in the repositories is old you are missing a lot.
And once you have the new tarball:
> sudo apt-get build-dep pcmanfm
Extract the tarball and open the terminal in the extracted folder
> ./configure
make
sudo make install
And there you go.

---

### Post by tad1073 on 2008-03-04
I followed the instructions and when I go to places>computer, i get an error saying file doesn't exist.---I got this problem fixed, but the error message pops up everytime I open computer. 

What do i need to do to get desktop icons and have pcman open the location. such as, computer, sdc1, home, network etc...

---

### Post by tad1073 on 2008-03-05
bump...

---

### Post by gsiliceo on 2008-03-05
Sorry, i made a mistake in one of the commands, you have to do this.
sudo ln -s /usr/bin/pcmanfm /usr/bin/nautilus
I forgot the sudo part and its important =P
Tell me how it goes, and recheck the steps please you might have forgotten something.

---

### Post by BIGtrouble77 on 2008-03-05
Couple of things to note...
The bad:
- PCMan does not support mime types nearly as well as nautilus, so no image or video previews.
- PCMan had weird behavior when launching from the Places location in the Gnome panel.  Loading new instances opened under my current window.  May be an issue with compiz fusion.
- Desktop mode is very under developed.  Basically only works as an ordered folder.  
- Could not connect to network through PCMan so it basically makes your network option in Places broken.

The Good:
- Has tabs support!!!!
- Looks almost exactly like Nautilus.
- Has tabs support!!!!

In the end I REALLY like PCMan, but it really makes me appreciate how good Nautilus is.  I have no speed improvements on my Macbook, but the Tabs feature makes it worth having alone.  Still needs more development, but very promising.  This is a GREAT file manager for xfce, far better than thunar.  I highly recommend just installing pcman and not having it take over nautilus... If you want light weight then use xfce with pcman.  

Thanks for the howto.

-bt

---

### Post by gsiliceo on 2008-03-06
In the latest version it does support image previews but not video.

Yeah its a focus problem, changes with metacity recently have made a number of apps fail like this.

The next unstable version does a better job in the desktop, it looks much much better.

I miss network support too, but i use a stand alone samba browser(in the repositories).

I like it because its so fast, i dual boot and the file explorer in windows is super fast(when my windows is virus free) and i missed that in ubuntu, now i have it :D

---

### Post by quina on 2008-03-13
**gsiliceo** you make a small mistake:
>  sudo cp /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus.desktop.backup
sudo cp /usr/share/applications/nautilus-folder-handler.desktop /usr/share/applications/nautilus-folder-handler.desktop

should be:
>    sudo cp /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus.desktop.backup
sudo cp /usr/share/applications/nautilus-folder-handler.desktop /usr/share/applications/nautilus-folder-handler.desktop**.backup**

Luckily, I've made backups using commands from **SilverWave**'s post, so have no problems, when returning to nautlius.
A few things, which annoing me most, are:
-no posibility to arrange icons(they are organised automaticaly, from left to right, top to bottom etc)
-problems with HAL(?!)(my phone card was mounted as read only:/)
-doesn't support drag&drop(beetwen aplications, eg. Totem)
-can't using RBM(right mouse button, *is this correct form?*), elsewhere than on icons...
But, i've been realy suprised how fast is PCManFM!!!
If someone would like to return to nautilus from PCManFM, should do(in terminal of course;):
> 
sudo cp /usr/share/applications/nautilus.desktop.backup /usr/share/applications/nautilus.desktop
sudo cp /usr/share/applications/nautilus-folder-handler.desktop.backup /usr/share/applications/nautilus-folder-handler.desktop
sudo cp /usr/share/gnome/default.session.backup /usr/share/gnome/default.session
sudo cp /usr/bin/nautilus.backup /usr/bin/nautilus
Then alt+ctrl+backspace
Hope, it will be helpful for some newbie;)

---

### Post by gsiliceo on 2008-03-13
Thanks man for the errata, i fixed it, and about those things you mention, i hate the lack of drag and drop support to copy/move files.

---

### Post by newb1e on 2008-04-20
I followed the instructions of the second post, everything is fine. 
But the weird thing is, I can't see the nautilus.desktop and nautilus-folder-handler.desktop in the /usr/share/applications folder (I can see the backup file).
I can see and open them with gedit in the terminal.
When I try to rename nautilus.desktop.backup to nautilus.desktop, I got the error the file already existed, so pcman knows the .desktop files are there:confused:
[IMG]http://img175.imageshack.us/img175/1524/27840541zl4.png[/IMG]

And when I use the shortcut "Super L", I got the error "Couldn't execute command: nautilus", so where can I change it:(

---

### Post by gsiliceo on 2008-04-21
Those files a probably hidden, click view hidden files in pcman. About the second problem i don't know where to change that.
Is it the default shortcut to open nautilis un gutsy?

---

### Post by subru77 on 2008-04-27
I followed the steps mentioned and had 2 problems. 

1) Places > Computer throws "File does not exist" error
2) The deskop wallpaper is missing and does appear when I run PCmanfm. So should I add PCmanfm to the startup ? Is there any other way? 

Thanks

---

### Post by gsiliceo on 2008-04-27
Yes, you need to add it to start up, but don't worry all it will do is load your desktop. And yes, the computer/network places links are broken, but the developer might fix them soon, it's being a while since he released a new version after releasing many in a row. I guess he will come back soon with fixes.
The official webpage here.
[http://pcmanfm.sourceforge.net/]("http://pcmanfm.sourceforge.net/")
You might want to help filing a bug here
[http://sourceforge.net/tracker/?group_id=156956&atid=801864]("http://sourceforge.net/tracker/?group_id=156956&atid=801864")

---

### Post by Alucard-sama on 2008-04-28
I can't find the *.desktop files? :S

EDIT: Nevermind they were simply labeled as "File Browser" and "File Management" for some reason.
Dunno if this is a Hardy thing or something to do with my version of PCManFM or what.

EDIT 2: Lol actually it seems the two are just combined now under "nautilus.desktop" which will come up as "File Manager" in the GUI.

---

### Post by gsiliceo on 2008-04-28
Im sorry i havent tried it this with Hardy only gutsy thats why i didnt answered.

---

### Post by Alucard-sama on 2008-04-28
It's cool
.
Anyways I tried it by editing this file and it worked perfectly so no biggy just took a tiny bit of detective work.

---

### Post by JoskeTobben on 2008-05-09
Running the pcman from the repositories. Followed the steps of the first and second post.

Pcman works just fine, though my desktop seems rather crippled. I can't really do anything with it, I can't make icons since it doesn't respond to a right-click. It just sits there, empty. It also doesn't show my conky.

Did I do something wrong or is this to be expected?

---

### Post by eriqjaffe on 2008-05-09
> **JoskeTobben said:**
> Running the pcman from the repositories. Followed the steps of the first and second post.

Pcman works just fine, though my desktop seems rather crippled. I can't really do anything with it, I can't make icons since it doesn't respond to a right-click. It just sits there, empty. It also doesn't show my conky.

Did I do something wrong or is this to be expected?There should be an option in PCMan to allow it to manage the desktop.

---

### Post by JoskeTobben on 2008-05-10
It's fixed in the latest version.

---

### Post by shreaded_teddy on 2008-05-11
i'm not exactly sure what to change.  can someone edit my default.session and post it back here?

# This is the default session that is launched if the user doesn't
# already have a session.
# The RestartCommand specifies the command to run from the $PATH.
# The Priority determines the order in which the commands are started
# (with Priority = 0 first) and defaults to 50.
# The id provides a name that is unique within this file and passed to the
# app as the client id which it must use to register with gnome-session.
# The clients must be numbered from 0 to the value of num_clients - 1.

[Default]
num_clients=4
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3

---

### Post by takmsdsm on 2008-05-12
PCMan doesnt play nice with conky. Everything works fine til i run PCman. Then conky loses its transperancy. Is there a fix for that? Otherwise, I am just going to switch back.

---

### Post by El_Belgicano on 2008-05-12
Disable the function "draw icons on desktop" in the preferences of pcmanfm. This should do it...

---

### Post by gsiliceo on 2008-05-12
[Default]
num_clients=4
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
#2,id=default2
#2,Priority=40
#2,RestartCommand=nautilus --no-default-window --sm-client-id default2
2,id=default3
2,Priority=60
2,RestartCommand=gnome-cups-icon --sm-client-id default3

There, make sure you run the latest version!

---

### Post by mkendall on 2008-05-21
> **gsiliceo said:**
> I recommend upgrading to the latest version, first uninstall the one you currently have.
```
sudo apt-get remove pcmanfm
```
And get the latest tarball from here:

[http://www.gnomefiles.org/app.php/PCMan_File_Manager]("http://www.gnomefiles.org/app.php/PCMan_File_Manager")

This app has being getting better and better with every upgrade and since the one in the repositories is old you are missing a lot.
And once you have the new tarball:
```
sudo apt-get build-deb pcmanfm
```
Extract the tarball and open the terminal in the extracted folder
```
./configure
make
sudo make install
```
And there you go.

I would really like to give this a try, but when I run
```
sudo apt-get build-deb pcmanfm
```
I get:
```
E: Invalid operation build-deb
```
Furthermore, ./configure yields:
```
checking for SN... configure: error: Package requirements (libstartup-notification-1.0) were not met:

No package 'libstartup-notification-1.0' found
```

Looking in Synaptic, I see that I have **libstartup-notification0**, but 1.0 doesn't exist.

---

### Post by gsiliceo on 2008-05-21
Are you using gutsy gibbon?
And i think what you really need is the -dev package of that library.

---

### Post by eriqjaffe on 2008-05-21
> **mkendall said:**
> I would really like to give this a try, but when I run
```
sudo apt-get build-deb pcmanfm
```
I get:
```
E: Invalid operation build-deb
```It should be **build-dep**.

---

### Post by gsiliceo on 2008-05-21
Didnt noticed that mistake, fixing it.

---

### Post by mkendall on 2008-05-21
> **eriqjaffe said:**
> It should be **build-dep**.

That fixed it.

---

### Post by BobSongs on 2008-05-23
I think I found a bug. I'm not sure, but I'm going to give it a test run. Here's what I'm talking about.

**gsiliceo**'s attachment looks like this:

> [Default]
num_clients=5
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
######  this symbol# tells the system not to read this lines######
#####2,id=default2
#####2,Priority=40
#####2,RestartCommand=nautilus --no-default-window --sm-client-id default2
#####  as you can see i've changed the file to comment## the nautilus part of the file numbers included and renumbered the other ones
2,id=default3
2,Priority=60
2,RestartCommand=gnome-cups-icon --sm-client-id default3
3,id=default4
3,Priority=40
3,RestartCommand=gnome-volume-manager --sm-client-id default4
4,id=default5
4,Priority=50
4,RestartCommand=vino-session --sm-client-id default5Now I'm no pro, but I believe I see an error in there.

Shouldn't[INDENT]**2,id=default3**
[/INDENT]actually be[INDENT]**2,id=default[COLOR=Red]2[/COLOR]?**
[/INDENT]And[INDENT]**2,RestartCommand=gnome-cups-icon --sm-client-id default3**
[/INDENT]should be[INDENT]**2,RestartCommand=gnome-cups-icon --sm-client-id default[COLOR=Red]2[/COLOR]**
[/INDENT]???

And so on throughout the piece? I'm getting a slightly wonky system and while I cannot guarantee it... it may be related to this bug.

I've corrected my own sheet and I'll give it a try and post the results.

---

### Post by BobSongs on 2008-05-23
[FONT=Verdana]Well I made the changes and I don't see much in the way of difference.

Here's what I've noticed that works all weird on me now that I've followed the tutorial:
[/FONT]
[LIST]
[*][FONT=Verdana]When booting into my account the **Nautilus** desktop wallpaper appears.[/FONT]
[*][FONT=Verdana]There are no signs of any desktop icons (files, folders or shortcuts).
[/FONT]
[*][FONT=Verdana]Clicking Places > My Computer results in a wallpaper switch (from the Nautilus wallpaper to the PCMan wallpaper) and the icons appear (albeit along the top rather than the side - but they're back).[/FONT]
[*][FONT=Verdana]The TrashCan/RecycleBin in my bottom panel returns this error: "File doesn't exist" with an OK button.[/FONT]
[*][FONT=Verdana]When changing appearances (System > Preferences > Appearance) and applying a theme with a desktop background, the background does not function (but I figured this would happen beforehand - not really an issue, but noteworthy for the brave of heart that wonder if this is true across the board).[/FONT]
[*][FONT=Verdana]PCMan doesn't appear to have a method of getting to the RecycleBin/TrashCan. But that's a PCMan problem.
[/FONT]
[/LIST]
[FONT=Verdana]I think I'll restore Nautilus as my desktop manager and use PCMan as my file browser.

I'll keep an eye on this thread and wait for updates.
[/FONT]

---

### Post by gsiliceo on 2008-05-24
You need to open pcmanfm and then go to edit / preferences / desktop / show icons, choose what you need :D

---

### Post by BobSongs on 2008-05-25
> **gsiliceo said:**
> You need to open pcmanfm and then go to edit / preferences / desktop / show icons, choose what you need :D
Thanks. But ... "been there, done that".

That setting was indeed set. The sequence then was:

[LIST]
[*]Log in
[*]Nautilus desktop wallpaper displayed and no desktop icons
[*]From the upper panel click **Place > Desktop** and boom: all the icons appear and the PCMan wallpaper shows up
[/LIST]
Hence the **show icons** option was set, but it did not appear to work when I signed in.

PCMan is a fast little file browser. But I don't believe it has everything a true Nautilus replacement requires, such as a way to manage things in the Trash. Deleting a file/folder in PCMan is permanent as opposed to sending things to a trash folder... unless I've missed something.

Personally I think the tips and tricks offered in the many posts that follow a tutorial should be gleaned and added to the main post and shown as options and choices, along with an uninstall/undo method should a new user wish to "back out" and return his/her desktop to default settings. I do this with [my own tutorial]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=352460").

---

### Post by gsiliceo on 2008-05-25
Yeah its a work in progress, this post is for people who like to experiment with the latest, i think what you may be missing is nautilus trying to load the wallpaper, you can change that in gconf editor, but i'm probably wrong.

---

### Post by MetalheadGautham on 2008-06-02
As far as I am concerned, I don´t need to replace Nautilus.

What I am doing is creating an alternative environment, with PCMan, IceWM(true curve theme), icewm-gnome-support, xchat, xterm, totem and kazehakase/skipstone.

I intend to use this ¨lighter¨ environment for CPU intensive activities.

so is PCMan really that great ? I intend to install either kaze or skippy as browser. Which shall I take ?

PS: Waiting for GTK2+ ports of EmelFM and Dillo

---

### Post by The Recorder on 2008-06-03
How do I uninstall PCMan?  Reset the shortcuts, but PCMan still opens locations from the "Places" menu.  I want PCMan to be available, but not a default app.  Can't figure out how to do this, so I want to uninstall it.  Was a tarball install of 0.4.1.1, so I can't uninstall through Synaptic.  And, I'm afraid that if I do uninstall it, my "Places" menu items won't work (since they are defaulted to it).

Any help would be appreciated.

Thanks,

Art

---

### Post by DesiDishoom on 2008-06-16
> **The Recorder said:**
> How do I uninstall PCMan?  Reset the shortcuts, but PCMan still opens locations from the "Places" menu.  I want PCMan to be available, but not a default app.  Can't figure out how to do this, so I want to uninstall it.  Was a tarball install of 0.4.1.1, so I can't uninstall through Synaptic.  **And, I'm afraid that if I do uninstall it, my "Places" menu items won't work (since they are defaulted to it).**

Any help would be appreciated.

Thanks,

Art

You're right about that part...I tried uninstalling PCMan from the terminal, and it broke all my places links. I even restored all the backups that we had made. So right now i use PCMan to open my places, but nautilus is still default for everything else. This works pretty well since PCMan is really fast, but I have Nautilus rendering the desktop and for conky.

---

### Post by tad1073 on 2008-06-19
I get this error when trying to ./configure pcmanfm-0.4.3. Can someone walk me through on how to set the variables.

```
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.6.0              
gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by gsiliceo on 2008-06-21
I suggest you install the .deb you can get in [www.getdeb.net](www.getdeb.net)

---

### Post by ShirishAg75 on 2008-06-21
Hi all, 
 I tried doing the same on Intrepid and while it works, there are some issues . I know Intrepid is in development so things may get broken and I'm not looking for a fix. Although it would be nice to also have a way to go back to nautilus described in the 1st or 2nd post itself as well. Specifically with the linking which was done there. 

The issue I'm facing atm is the wallpaper doesn't stand on its own . Also pcmanfm doesn't have a pcmanfm --version thing. 

Here's another thing which shows up when I run pcmanfm on the CLI. 

```

shirish@Mugglewille:~$ pcmanfm
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/mime-type.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/mime-action.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/mime-cache.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-file-monitor.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-mime-type.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-file-info.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-dir.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-app-desktop.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-file-task.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-volume-hal.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-volume-hal-options.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-execute.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-async-task.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-thumbnail-loader.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/vfs-utils.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/md5.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-browser.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-list.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-path-entry.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-text-renderer.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-icon-renderer.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-utils.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-dir-tree-view.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-dir-tree.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-location-view.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-bookmarks.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-input-dialog.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-task.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-archiver.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-console-output.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-clipboard.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-menu.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-misc.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-file-properties.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-app-chooser.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-ui-xml.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/ptk-xml-tree.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/exo-icon-view.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/exo-private.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/exo-string.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/exo-marshal.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/desktop-window.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/working-area.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/desktop.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/main.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/main-window.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/settings.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/pref-dialog.gcda:Skip
profiling:/build:Cannot create directory
profiling:/build/buildd/pcmanfm-0.4.3/src/edit-bookmarks.gcda:Skip

```

This I guess is to be expected.

---

### Post by Alucard-sama on 2008-07-02
Since following this guide I now have a hella annoying Icon on my Desktop called "My Documents" that links to my home directory.
I want it gone but I can't get rid of it.
Anybody know how to get rid of it?

---

### Post by altonbr on 2008-07-03
Awesome, works well with Hardy, thanks!

I wish it would do this automatically however :(

---

### Post by gsiliceo on 2008-07-03
I think it will eventually happen, but right now is not a complete nautilus replacement, some functions are not implemented but are on their way.
I've followed the development of this app and its going great, really moving forward.

---

### Post by EnigMattic on 2008-07-14
Hello

I've tried this and really like using PCMan as my main file manager, but would prefer to keep nautilus managing my desktop.

So, my question is this: Is it possible to have PCMan open folders from 'Places', open when i browse a drive/folder etc (i.e. act as the default file manager), but not override nautilus as desktop manager?

Thanks!

---

### Post by Truedream on 2008-07-14
> **Alucard-sama said:**
> Since following this guide I now have a hella annoying Icon on my Desktop called "My Documents" that links to my home directory.
I want it gone but I can't get rid of it.
Anybody know how to get rid of it?


same here. if someone knows how to get rid of that icon please share it.

---

### Post by PCMan on 2008-07-18
> **Truedream said:**
> same here. if someone knows how to get rid of that icon please share it.

I'll try to provide an option to turn it off in the next major release.

---

### Post by gsiliceo on 2008-07-18
Yay the pcman itself spoke to us =P by the way the latest version totally rocks i've been following closely the development and that one is the best.

---

### Post by altonbr on 2008-07-19
> **PCMan said:**
> I'll try to provide an option to turn it off in the next major release.

PCMan, have you thought about maintaining the Ubuntu packages? They always seem to be out of date.

PS: I sent you an e-mail directly on adding 'Ctrl + Shift +  N' for creating a new folder in PCManFM (similar to Nautilus). Have you received it or are you thinking of adding it in the near future?

---

### Post by EnigMattic on 2008-07-22
Would anyone be interested in helping me write a patch to add a dual pane option to PCMan?

---

### Post by jcrabapple on 2008-07-25
A suggestion for getting the Empty Trash button to work when you replace Nautilus with PCMan: create your own!

Just put a launcher on your panel that executes the following command:

rm -rf ~/.Trash/*

If you're deleting things through PCMan it doesn't go to trash anyway, just gets deleted.

---

### Post by iamBevan on 2008-08-07
Thankyou very much posts #1 + #2 - both worked perfectly, and i'm enjoying PCMan way more than Nautilus

---

### Post by Just-trevor on 2008-08-08
I want to change back...
how is this achieved?

---

### Post by gsiliceo on 2008-08-09
Restore your backups, overwritting. And dont forget the binary.

---

### Post by Just-trevor on 2008-08-09
oh.. i should have been clearer... what is the code to do that, i meant

---

### Post by Bruce M. on 2008-08-19
Hi Folks,

I'm running Ubuntu 64bit v8.04.1 and this works GREAT!

I only followed Post #1, not the rest, PCMan is great stuff.

Have a nice day
Bruce

**EDIT:** Thank you, SilverWave

---

### Post by yosemite610 on 2008-11-26
Am really loving the increase in speed, but when I use the 'Places' menu, pcmanfm can't open files (dbl-click on a text file and it doesn't open in Text Editor).

However, if I start pcmanfm from the command line, it seems to open files ok.

---

### Post by noahTHEpurdy on 2008-11-29
Hey all.

I'm looking to replace nautilus completely with pcmanfm on 8.10. This is on a netbook, so I want the lightest of light, and I want to rid myself of the bloat. 

My end goal is the complete removal of nautilus, however the process seems a bit different on Ibex.

Anyone have any ideas?

---

### Post by Bruce M. on 2008-11-30
> **noahTHEpurdy said:**
> Hey all.

I'm looking to replace nautilus completely with pcmanfm on 8.10. This is on a netbook, so I want the lightest of light, and I want to rid myself of the bloat. 

My end goal is the complete removal of nautilus, however the process seems a bit different on Ibex.

Anyone have any ideas?

{shhhhhhhh don't tell anyone I said this...}
Try Xubuntu.  :)

---

### Post by Izek on 2008-12-14
I find it annoying that I can't make launchers in PCMan.

Dragging a folder to the desktop copies/moves it. I want to create shortcuts.

Why do I want to create a shortcut? Because when I insert a CDRom, it doesn't show on the desktop!

Also created a new bug: [Click Here](http://sourceforge.net/tracker/index.php?func=detail&atid=801864&aid=2430211&group_id=156956)

---

### Post by TheMyself on 2009-01-03
I followed the steps in the second post and now when I double click on a file (pdf, jpg, etc.) the corresponding application is not launched. In fact the icon for the program appears in the panel but shortly after, it disappears. This wasn't the case (in PCmanfm) before. 

Another oddity was that the file /usr/share/gnome/default.session was empty (from the beginning).

Please help.

---

### Post by TheMyself on 2009-01-03
problem was resolved after I restarted the computer.

---

### Post by w1zard on 2009-01-11
Yep, can confirm that /usr/share/gnome/default.session does not exist in my install of Intrepid either.

Not sure how to proceed with the instructions for complete replacement of nautilus in this case?

---

### Post by TheMyself on 2009-01-12
I want to mention some caveats.

1-When I delete a file in PCmanFM, it doesn't go to the bin, it just gets deleted forever.

2-Nautilus is still running as a process. If I kill it, things go wrong and I have to restart the session.

3-When I want to save a file in Firefox, the dialogue which appears looks entirely like Nautilus and is as slow.

---

### Post by edyeeh on 2009-02-13
> **w1zard said:**
> Yep, can confirm that /usr/share/gnome/default.session does not exist in my install of Intrepid either.

Not sure how to proceed with the instructions for complete replacement of nautilus in this case?

same here

---

### Post by cb951303 on 2009-02-13
> **SilverWave said:**
> _________________________________________________

**PCMan works great as a drop in replacement for Nautilus.**

[B][I]PCMan works well with GNOME and has options to "Open Current Folder as root" and also "Open Terminal" .
Its fast, uncluttered and has tabs![/I][/B]


Nautilus has "Open Current Folder as root"
Nautilus has "Open Terminal"
Nautilus has tabs

just look for plugins in synaptic for the first 2(I don't remember the names :/) :popcorn:

EDIT: oops it's an old thread. anyway I'm gonna keep this post just in case :)

---

### Post by krazyman on 2009-02-15
As others have mentioned, with Intrepid, default.session does not exist anywhere in the file system!

The main reason I like PCManFM over nautilus is that it allows you to 'lassoo' files to select them. Konqueror does, but it's well heavy.

---

### Post by RueHabergeon on 2009-02-24
I did everything as instructed here to replace nautilus, but I don't like it anymore...

How do you revert to nautilus?

---

### Post by fooey on 2009-04-09
Revert back to the backups you made from Post #1 ;)

---

### Post by Twitch6000 on 2009-04-11
I have tried PCMan for a few days manually and I love the speed...

However I tried this guide and the location for the nautilus file is there,but nautilus is not...

I really want to make PCMan the default,but it seems the guide is a bit outdated or something...

---

### Post by SilverWave on 2009-04-12
Hi guys nice to see that this was useful to some people :)

Things have moved on a lot from when I first posted this tip so here is a note.

Nautilus now comes with tabs, Nautilus extensions allow root and open-terminal use.
_____________________

nautilus-gksu - privilege granting extension for nautilus using gksu - Open as Administrator

nautilus-open-terminal - nautilus plugin for opening terminals in arbitrary local paths

"gconf-editor" /apps/nautilus/preferences/show_advanced_permissions
(Show advanced permissions in the file property dialogue).

gTweakUI - dialogs with settings for Nautilus, the Session and Menus

_____________________

I still install PCMan after Ubuntu as a backup file manager but I find now that Nautilus is fine 99% of the time. Permissions is one area that I sometimes find easier in PCMan.

[UPDATE] But you can tweak the setting via "gconf-editor" /apps/nautilus/preferences/show_advanced_permissions

You may want to have a look at xfe as well.

I have no reason to now wish to replace Nautilus with PCMan.

Cheers!

---

### Post by Pili36 on 2009-05-15
> **Twitch6000 said:**
> I have tried PCMan for a few days manually and I love the speed...

However I tried this guide and the location for the nautilus file is there,but nautilus is not...

I really want to make PCMan the default,but it seems the guide is a bit outdated or something...

Hi,

To replace nautilus by pcmanfm, i just do that:

Install the pcmanfm package
After press Alt + F2 and type gconf-editor
   Go to Desktop -> Gnome -> Session -> required_components and next to "filemanager', replace nautilus by pcmanfm.


-------------------------------------

OS : Ubuntu Jaunty 9.04

---

### Post by kevinguillorytraining on 2009-10-09
I followed the instructions and I got the results.

---

### Post by airtonix on 2010-03-30
> **krazyman said:**
> 
The main reason I like PCManFM over nautilus is that it allows you to 'lassoo' files to select them. Konqueror does, but it's well heavy.

Nautilus does this as well, but not in detailed list view if there is no white space at the bottom of the list... so if your list of files extends all the way to the bottom then you cant "lasso" a file selection...

You can however do this in the other two views and have been able to for as long as i can remember.

The one thing pcmanfm has over nautilus is speed. pure and utter speed.

---

### Post by alainpannetier on 2010-05-18
Hello everyone,

Is there any nautilus plugin to filter a right hand side pane on file names (I'm not talking about CTRL-s here which only highlights entries and is a many clicks operation). Many OS have this but I can't seem to find it on Linux.  The closest I could come up with is dolphin but it's really weird to use.

For winwoes you can use custom toolbars like StExBar (google it).  For Nautilus: nothing !
It can't be that hard ! can it ?

Alain Pannetier

---

### Post by JohnnyC35 on 2010-05-18
using Thunar right now to replace nautilus. am able to do mass rename and moving GB's of data doesn't kill my CPU cycles. up to 65% CPU transferring files from USB external to RAID5 is not cool. Thunar does it and doesn't go over 15%. Would like it if Thunar had tabs tho, and have a rough MB/s listing when moving files.

---

### Post by Zenmij on 2010-05-21
Hi, real simple question.

I have the thumbnail limit set to the default 1024kb but I am not seeing any.

I can't find any info on this particular problem.

Thanks.

---

### Post by Devi 710 on 2010-08-28
Any update on this for Lucid 10.04? There is no "default.session" on my system at all, so I can't follow all the steps in the second post.

Or should I just go to the Configuration Editor -> Desktop -> Gnome -> Session -> required_components -> and change 'nautilus' to 'pcmanfm' ?

Devi

---

### Post by gsiliceo on 2010-08-29
Also requesting changes needed to make this tutorial work with Lucid.

---

### Post by Devi 710 on 2010-08-29
> **gsiliceo said:**
> Also requesting changes needed to make this tutorial work with Lucid.

Well you want to start by getting the latest version of PCManFM. The one in the Lucid Repos is something like 0.5. The newest one is 0.9.7 which has been rewritten and is way better.

You can do this by adding the Lubuntu repository: [https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

You could just use the terminal and type:
```

sudo add-apt-repository ppa:lubuntu-desktop/ppa

sudo apt-get update
```

Next, install PCManFM2 from Synaptic. This will delete the old version as well.

Then follow the first to posts here (as much as you can). And that will get you pretty close to full replacement.

---

### Post by fooey on 2010-08-31
> **Devi 710 said:**
> Well you want to start by getting the latest version of PCManFM. The one in the Lucid Repos is something like 0.5. The newest one is 0.9.7 which has been rewritten and is way better.

You can do this by adding the Lubuntu repository: [https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

You could just use the terminal and type:
```

sudo add-apt-repository ppa:lubuntu-desktop/ppa

sudo apt-get update
```

Next, install PCManFM2 from Synaptic. This will delete the old version as well.

Then follow the first to posts here (as much as you can). And that will get you pretty close to full replacement.

aww..very nice. thanks. they have REALLY improved that since last time i used pcmanfm. thanks for the heads up :P

---

### Post by Devi 710 on 2010-08-31
> **fooey said:**
> aww..very nice. thanks. they have REALLY improved that since last time i used pcmanfm. thanks for the heads up :P

No problem. Now to figure out how to completely remove nautilus and get pcmanfm to write the desktop and mount drives to the desktop...

---

### Post by asrail on 2010-09-05
> **Devi 710 said:**
> No problem. Now to figure out how to completely remove nautilus and get pcmanfm to write the desktop and mount drives to the desktop...

I don't use pacmanfm myself, but I'll help per your request.
I've made a post about how to make some program be the default file manager, including when opening something inside Firefox (which doesn't use the system default file manager): 
[http://my.opera.com/Asrail/blog/opening-dolphin-from-firefox-and-other-gtk-applications-on-ubuntu](http://my.opera.com/Asrail/blog/opening-dolphin-from-firefox-and-other-gtk-applications-on-ubuntu)

the key is you can always use another desktop entry instead of changing the nautilus's desktop entries or using an symbolic linc. Making it using the mimeinfo.cache, which can be edited on a per user basis, will allow to some user replace nautilus with pacmanfm while another user uses nautilus.

You can try that approach, but that won't help in cases nautilus is called directly from another program.

---

### Post by Devi 710 on 2010-09-05
> **asrail said:**
> I don't use pacmanfm myself, but I'll help per your request.
I've made a post about how to make some program be the default file manager, including when opening something inside Firefox (which doesn't use the system default file manager): 
[http://my.opera.com/Asrail/blog/opening-dolphin-from-firefox-and-other-gtk-applications-on-ubuntu](http://my.opera.com/Asrail/blog/opening-dolphin-from-firefox-and-other-gtk-applications-on-ubuntu)

the key is you can always use another desktop entry instead of changing the nautilus's desktop entries or using an symbolic linc. Making it using the mimeinfo.cache, which can be edited on a per user basis, will allow to some user replace nautilus with pacmanfm while another user uses nautilus.

You can try that approach, but that won't help in cases nautilus is called directly from another program.

Thanks for the info. Any help is great. 

Though I am not sure how to proceed.There is a file called pcmanfm.desktop, but it's in /usr/share/app-install/desktop, nowhere else. Should I copy it into /usr/share/applications/ and change the MimeType line?

---

### Post by Ravi5kumar on 2012-09-25
What about 12.04?

---

### Post by Elfy on 2012-09-25
Try a support thread in a normal forum - this is an old tutorial that's not been posted in for 2 years and is 4 years old.

---

