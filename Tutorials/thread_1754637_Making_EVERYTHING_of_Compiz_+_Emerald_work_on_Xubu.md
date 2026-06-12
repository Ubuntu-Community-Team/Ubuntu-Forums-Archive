---
title: "Making EVERYTHING of Compiz + Emerald work on Xubuntu 11.04"
date: 2011-05-10
forum: Tutorials
---

### Post by 3 frags left on 2011-05-10
**Protip: This tutorial also works on Kubuntu, Lubuntu or whatever Ubuntu distro you want. The only difference will be in the part where it mentions the default window manager of Xubuntu; replace it with the window manager of your distro.**

I heard from many linuxers that one of the main reasons they did not use Xubuntu 11.04 was the impossibility of installing the beautiful, beautiful Compiz interface due to compatibility issues. After a lot of research, I finally did, and this is how I did it.

[COLOR="Magenta"][FONT="Comic Sans MS"]"Meh, Compiz is just eye candy, why would I install it, it's a waste of time!"[/FONT][/COLOR]
Besides the gorgeous eye candy, Compiz makes your system [color=red]much[/color] faster in general. Just check the sidebar @ the screenshots.

[COLOR="Magenta"][FONT="Comic Sans MS"]"INB4 CRASHING SYSTEM"[/FONT][/COLOR]
I guarantee this will work. IF, and only if this doesn't work, you can restore things like they previously were by pressing Alt+F2 and typing *xfwm4 --replace*. This will reset Xubuntu's original windows decorator.

So, let's get started, shall we?
First of all, if you have attempted to install emerald, **remove it.** For some reason, the package in the repository does not work. I'm pretty sure they are doing their best to solve this, but meanwhile we will have to use another way. Remove purge emerald and its dependencies.
```
sudo apt-get remove --purge emerald libdecoration-0dev
```
Good. Now, using a fix I borrowed from [this blog](http://demonic.cc/?p=50), we'll install a few packages we need, as well as using git repositories. You might save this as a script if you wish, or copy & paste everything. [color=#990000]PROTIP: To paste a line in a terminal session, use Ctrl+Shift+V.[/color]
```
sudo apt-get -y install libtool build-essential intltool libdecoration0-dev libglib2.0-dev libgtk2.0-dev libwnck-dev
#Install git and autoconf too if you don't have it
sudo apt-get install git autoconf
cd ~
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald
git checkout -b compiz++ origin/compiz++
./autogen.sh
make
make install
cd ~
rm -rf emerald
```
Once this is done, Emerald THeme Manager should be at your menu. Go check it under Settings.

Now it's Compiz's turn. You can get it with no trouble through regular means.
```
sudo apt-get install compiz compiz-plugins-extra compiz-plugins-main compizconfig-settings-manager
```
Once that's done, now it's time to go to CompizConfig Settings Manager in Settings menu. Before starting Compiz up, set emerald as Compiz's default window manager. Select the Effects category, enable Window Decorator and get into its options. In the *command*, place *emerald --replace*.

Now onto the testing part! Press Alt+F2 and type *compiz --replace*. Emerald will automatically take the scene. Oh, do I need to remind you that first you need to install a theme to manage it? Get some [here](www.compiz-themes.org). I personally recommend Gallygan, it's the one I'm using at the screenshots.

Bang! Compiz oughta be working, so now we must add it to startup, right? Go to *Settings > Settings Manager > Session and Startup[i]. Select [i]Application Autostart* tab and click *Add* button. Name it *Compiz Startup*, and type *compiz --replace* in the command line.

[COLOR="Magenta"][FONT="Comic Sans MS"]"What about the cube?"[/FONT][/COLOR]
11.04 has decided to be nasty with this conflict between Desktop Wall and the Cube. [OMG! Ubuntu made a pretty good post about it](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/), follow it to the letter and it will work properly.

[SIZE="4"]Check out a few screenshots of my PC with the ultimate eye candy:[/SIZE]
[[IMG]http://img818.imageshack.us/img818/7402/compiz01.th.png[/IMG]](http://img818.imageshack.us/i/compiz01.png/)
[[IMG]http://img863.imageshack.us/img863/1723/ubuntu02.th.png[/IMG]](http://img863.imageshack.us/i/ubuntu02.png/)
[[IMG]http://img109.imageshack.us/img109/297/compiz03.th.png[/IMG]](http://img109.imageshack.us/i/compiz03.png/)

Credits:
[www.demonoid.cc](www.demonoid.cc)
[www.omgubuntu.com.uk](www.omgubuntu.com.uk)

[COLOR="Silver"]***Edit**: [dballanc](http://ubuntuforums.org/member.php?u=719299) reminded me of something I forgot... you must add the packages [i]libglib2.0-dev libgtk2.0-dev libwnck-dev* if you are installing Xubuntu from scratch. Otherwise, it won't configure. Thanks, bud!
**Edit 2**: Another typo fixed... sorry for that! Thanks [jclmusic](http://ubuntuforums.org/member.php?u=132186)! Typos happen...[/COLOR][/i]

---

### Post by dballanc on 2011-05-15
The above steps were not enough coming from a default xubuntu 11.04 install.  There were a couple of other dev packs to install before the autogen.sh script would complete without errors:

sudo apt-get install libglib2.0-dev libgtk2.0-dev libwnck-dev


After that everything worked perfectly.  Thanks!  I think this really improves the appeal of xfce.

---

### Post by 3 frags left on 2011-05-16
Oh, I forgot that little detail! I'm editing that into the tutorial right away. Thank you!

---

### Post by jclmusic on 2011-05-16
Small thing, but shouldn't that last code block be:

```
 sudo apt-get **install** ... 
```

---

### Post by 3 frags left on 2011-05-16
Whoops! What a lack of attention of mine! Thank you and sorry for that.

---

### Post by geazzy on 2011-05-16
great tips..
but I use unity :D

---

### Post by Deadmode on 2011-05-18
bleehhhhh... I decided not to go with emerald + compiz after I went through this, but I can't get rid of emerald theme manager out of my system > preferences menu. ```
sudo apt-get remove emerald
``` gives me ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emerald is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 94 not upgraded.

```

What do I need to do to just remove all traces of emerald?

---

### Post by 3 frags left on 2011-05-18
> **Deadmode said:**
> bleehhhhh... I decided not to go with emerald + compiz after I went through this, but I can't get rid of emerald theme manager out of my system > preferences menu. ```
sudo apt-get remove emerald
``` gives me ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emerald is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 94 not upgraded.

```

What do I need to do to just remove all traces of emerald?
Since you did not use the PPA Repo version, you must uninstall it from the same folder you installed it. Go to the *emerald* folder with all the files you downloaded and type *sudo make uninstall*. That should do the trick.

But I don't get it, didn't you like the result? What happened?

---

### Post by Deadmode on 2011-05-18
> **3 frags left said:**
> Since you did not use the PPA Repo version, you must uninstall it from the same folder you installed it. Go to the *emerald* folder with all the files you downloaded and type *sudo make uninstall*. That should do the trick.

But I don't get it, didn't you like the result? What happened?

Thanks, I figured it was probably something like this.

---

### Post by helicase on 2011-05-18
Thanks! I've got it working now, although emerald complained at first about not finding libemeraldengine.so.0 Linking to /usr/local/lib/libemeraldengine.so.0 from /usr/lib solved the problem.

---

### Post by jclmusic on 2011-05-21
I can't get compiz to start :(

When I type **compiz --replace** in a terminal, this is what I get:

```

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Support for non power of two textures missing
Compiz (bailer) - Info: Ensuring a shell for your session

```

Anyone got any ideas?

---

### Post by Neobuntu on 2011-05-23
OK friends, here's what I did to get this to work:

I am using 11.04 Natty; from an upgrade(risky, so do a clean install), and I used the win2-7, script-installed, theme; not Unity. Just because. I chose a non-Windows branded Win 7 look (today); just because I can. Unity's not that bad, but I don't like it better. I also, do not like Windows.

I removed Unity. ```
sudo apt-get remove unity 
```Note: DRI seems to be working with my Nvidia driver (in, System > Administration > Additional Drivers), set as "Version 173"; not "current".

1. I found I needed to do this logged in with Ubuntu, and not Ubuntu classic. I guess I'm doing this, in the place of Unity.

2. This fine thread worked for me; when I added **sudo**, before the **make install** command. If you're using the Compiz icon (panel setting), found, and started from: Application > System Tools, (see the win2-7 help text, for how to install it.) It will not give an option for Emerald, nor its theme manger, until this complied version is working (makes sense).

3. You may need to log out, (and remember set "Ubuntu", not Classic) and log back in.

With Ubuntu: **System > Preferences > Startup applications**, and add the **Compiz -replace** as instructed, to make it reappear, after restarting.

Now; finally, I see Emerald themes changing, before my eyes, and I've turned on Wobbly Windows (Checking [http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/) ). Plus, I see a gradient blur (follow Win2-7 directions), through the Emerald windows boarders.

For my best results, I loaded the Included "Win2-7" Compiz profile; and then "Exported As" Win2-7_final, after setting the blur Windows, as Win2-7 suggests, and to my liking. I decided to just stay with the thing where if you drag windows halfway out of the screen, it will light up half the screen, so that when you release the click, it fill that half of your screen, with that windows, as resized. You can pop up a left, and right, window this way; which is useful. I'll mess with the other stuff when the bugs are fixed. Let sleeping dogs lie. You can play with fire writing and all, but click th wrong option and it will crash, so be ready to load up you custom/set profile again, to fix it.

---

### Post by redthor on 2011-05-25
Should the instructions say:

sudo make install 

? 
Just got a permissions error on that line.

Thanks v much for the instructions.

---

### Post by aoniumo on 2011-05-26
This might be a stupid question, but how do I apply a theme?

I downloaded a theme and I was able to open it with Emerald Themer.  Now what?

---

### Post by Neobuntu on 2011-05-31
I downloaded an emerald theme, just to test, and it, being just the windows boarder, works. I use the win2-7 emerald boarders (various colors) though.

One could just use Metacity boarders, with it's composting; for see through boarders.  

I used the Compiz Icon to select Emerald, over the regular Gnome Metacity, windows boarders.

The in-window controls, are under the usual: ```
Preferences > Appearance > Custom
```

So are Icon sets.

...Hope that helps.

---

### Post by Krydahl on 2011-06-02
An easy solution is to use a different window-decorater. 

If you install compiz and ccsm from the repos open ccsm, go into the Window Decoration plugin and type, "gtk-window-decorator" where it says Command, it pretty much works without any effort.

---

### Post by RallyDarkstrike on 2011-06-04
Hiya folks,

Forgive me for being a Linux n00bie, but I was curious; I just installed Xubuntu and wanted to get Compiz back up and running, however, I do not want to use Emerald as my window manager and just want to use the default window manager that Xubuntu has with Compiz?

I assume this is possible considering I read this ("**The only difference will be in the part where it mentions the default  window manager of Xubuntu; replace it with the window manager of your  distro."** in your tutorial, but please for forgive me as I don't quite understand the steps required to do so.

If I want to use Xubuntu's default window manager in 11.04 with Compiz, ARE there additional steps or do I just install those Compiz packages, or...?

I appreciate any help anybody is kind enough to give me :)

Cheers and thanks!

---

### Post by mexicanseaf00d on 2011-06-12
Basically it works, thank you for the tutorial, but there is a problem: ```
sudo make install
``` bypasses the package manager, therefore synaptic/apt wants to install the repo-emerald as a dependency whenever I fetch emerald themes from some ppa (webup8 for example).

I used ```
sudo checkinstall
```, added a .1 to the version number (0.9.4 I believe is in ubuntu repository, I changed the above posted git version to 0.9.4.1) and also changed option "13" in checkinstall to replace package 'emerald'.

So far it seems to work, but I can't be sure of course, because I am a horrible noob in these matters :D

---

### Post by yetiman64 on 2011-06-13
@RallyDarkstrike, Yes you can skip the install of emerald, and install compiz with Xubuntu. I suggest you install fusion-icon as well and create a startup up entry for it. It is an easy means of reloading the Window Manager when things get hung while changing settings etc, or for generally managing compiz.

With it I have the choice of Xfwm4 or compiz for Windows managers and the windows decorator is the gtk window decorator. Compiz is installed here and fully working without the use of emerald at all, that is the cube and related effects, the expo wall, wobbly windows etc, the full install of effects basically.

You can set up some interesting effects with Xfwm4 and gtk windows decorator and then set up compiz with gtk windows decorator. Then by using fusion icon you can choose between the 2 different set of effects easily. Matching the settings for the expo wall in compiz and the workspace switcher in Xfwm4 gets weird when you have 36 desktops in a 6 X 6 grid ;), it can be made to work :mrgreen:.

Please note though my install is built up from a 22 MB minimal image NOT the standard installer. I plan to do a standard install with the very setup you want in the next week or so, hope it goes as well as this is performing.

Cheers, yetiman64.

---

### Post by RallyDarkstrike on 2011-06-13
Thanks yetiman64, I'll take a look later tonight if I have time, and if not, tomorrow! :)

---

### Post by beew on 2011-06-13
> **yetiman64 said:**
>  I suggest you install fusion-icon as well and create a startup up entry for it. It is an easy means of reloading the Window Manager when things get hung while changing settings etc, or for generally managing compiz.
.


I am afraid the fusion-icon is broken for Compiz 0.9.

---

### Post by yetiman64 on 2011-06-14
> **beew said:**
> I am afraid the fusion-icon is broken for Compiz 0.9.
What do you mean by "broken" (dependencies etc ?) and do you have a link to any info for what you are saying beew ?

I have Compiz "installed version 1:0.9.4+bzr20110415-0ubuntu2: + Fusion-icon "installed version 0.1.0-2ubuntu1" here. 
This is with a Natty minimal install (22 MB - 64 bit) and the command,
```
sudo apt-get install xubuntu-desktop
``` to set up the system. **Edit:** just a note, the minimal cd was for a command line only installation of Natty.

I installed all the drivers (nvidia) /codecs and such for a multimedia system then installed compiz and fusion icon and both are working fine. Fusion icon let me seemlessly switch between compiz and Xfwm4 (set up first), this was using the GTK Window Decorator for both WMs.

Obviously this is not a standard means of installing and I noted that to RallyDarkstrike earlier, I have only just finished burning the standard Xubuntu live cd (64 bit) and am about to reinstall a more standard setup. Will let you know how it goes. Please link some info if you can :), I won't be too surprised if i hit a ](*,)that way. Regards from yetiman64.

---

### Post by beew on 2011-06-15
> **yetiman64 said:**
> What do you mean by "broken" (dependencies etc ?) and do you have a link to any info for what you are saying beew ?

I have Compiz "installed version 1:0.9.4+bzr20110415-0ubuntu2: + Fusion-icon "installed version 0.1.0-2ubuntu1" here. 
This is with a Natty minimal install (22 MB - 64 bit) and the command,
```
sudo apt-get install xubuntu-desktop
``` to set up the system. **Edit:** just a note, the minimal cd was for a command line only installation of Natty.

I installed all the drivers (nvidia) /codecs and such for a multimedia system then installed compiz and fusion icon and both are working fine. Fusion icon let me seemlessly switch between compiz and Xfwm4 (set up first), this was using the GTK Window Decorator for both WMs.

Obviously this is not a standard means of installing and I noted that to RallyDarkstrike earlier, I have only just finished burning the standard Xubuntu live cd (64 bit) and am about to reinstall a more standard setup. Will let you know how it goes. Please link some info if you can :), I won't be too surprised if i hit a ](*,)that way. Regards from yetiman64.

I read a while ago that the fusion icon was broken in Compiz 0.9 but I haven't tried it myself, so maybe they fixed it or I was just getting wrong info. Glad it is working for you. 

Anyway, I installed Compiz 0.86 using the ppa in this link (It is for Ubuntu but everything works in Xubuntu as expected) 

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

The instruction is unnecessarily complicated. Don't need to remove Compiz, just add the ppa and do a normal update in Synaptic would do , since the 0.86 packages in the ppa were renamed to 2.086  which is a higher version than 0.9 in Natty (1.09), so updating will override the default version.

Since there is no Unity in xubuntu anyway there is no catch in using 0.86 (in Ubuntu that would remove Unity) but I can installed other experimental plugins that no longer work in 0.9 
[http://www.techdrivein.com/2010/11/script-to-install-incredible-compiz.html](http://www.techdrivein.com/2010/11/script-to-install-incredible-compiz.html)

The fusion icon would likely work too, though I haven't installed it since I probably don't need it.

---

### Post by yetiman64 on 2011-06-15
Ok I understand the situation now, thanks :). I've done a full install now from the live cd and got compiz and fusion icon working fine. Am noting some strangeness with the panel workplace switcher from xfwm4 when used at the same time as the compiz viewport switcher. They like to fight and things can disappear and magically reappear later when least expected :lol:. Everything else works fine.

I tried the emerald instructions here with no luck at all, then tried the repo version as well and failed, I've given up on emerald unfortunately. Couldn't get any windows decorations to work with it so will stay with the gtk decorator.

Will look into those links, particularly the experi**mental** ones later on. I'm working on a few things that are likely to break this install as is, so won't push my luck too far at the moment ;).

Cheers, yetiman64.

---

### Post by beew on 2011-06-15
> **yetiman64 said:**
> 
I tried the emerald instructions here with no luck at all, then tried the repo version as well and failed, I've given up on emerald unfortunately. Couldn't get any windows decorations to work with it so will stay with the gtk decorator.



I haven't looked at the instructions here, but I have been able to install emerald in Natty (Unity) since beta with the help of the forum (special thanks to mc4man)

[http://ubuntuforums.org/showthread.php?t=1702253](http://ubuntuforums.org/showthread.php?t=1702253)

It should work in Xubuntu as well, but haven't tried it yet.

EDITED: And oh, the experimental plugins work, at least for those that I have tried. :)

---

### Post by beew on 2011-06-18
BTW, for those who are still interested, this is a simplified tutorial.

If you downgrade Compiz as I said in post#23 you don't need to build emerald yourself. It will work if you just install from the repository because Compiz 0.9 is what breaks it. There is no harm downgrading Compiz in Xubuntu because the only side effect is that it will get rid of Unity but Unity doesn't run in Xubuntu anyway.

so in summary: 

> sudo add-apt-repository ppa:guido-iodice/compiz-0.8.6-natty
sudo apt-get update 
 then install Compiz and the related packages (or upgrade Compiz and related packages--which is actually downgrading,--if  they are already installed, no need to remove the already installed packages like in my Webupd8 link) Then install emerald, that's it. No need to build emerald from source at all.

To make Compiz auto start go to Settings > Setting manager > Session And Startup > Applications Autostart and add an entry for Compiz. The command should simply be "/usr/bin/compiz" (without quotations) instead of "compiz --replace". "compiz --replace" loads another default window manager and then switch to Compiz. There is no point in loading another window manager since you are using Compiz anyway.

---

### Post by chosen1920 on 2011-06-25
thanks this thread is very useful

---

### Post by charliewhizbeez on 2011-07-06
> **3 frags left said:**
> [b]  
[COLOR="Magenta"][FONT="Comic Sans MS"]"What about the cube?"[/FONT][/COLOR]
11.04 has decided to be nasty with this conflict between Desktop Wall and the Cube. [OMG! Ubuntu made a pretty good post about it](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/), follow it to the letter and it will work properly.

[SIZE="4"]Check out a few screenshots of my PC with the ultimate eye candy:[/SIZE]
[[IMG]http://img818.imageshack.us/img818/7402/compiz01.th.png[/IMG]](http://img818.imageshack.us/i/compiz01.png/)
[[IMG]http://img863.imageshack.us/img863/1723/ubuntu02.th.png[/IMG]](http://img863.imageshack.us/i/ubuntu02.png/)
[[IMG]http://img109.imageshack.us/img109/297/compiz03.th.png[/IMG]](http://img109.imageshack.us/i/compiz03.png/)


When looking at your screenshots I realized that the desktop changing taskbar applet was still working.  Even with the cube! How did you do that? Because whenever I try that in ubuntu classic it becomes one desktop and stops working (the applet).

---

### Post by cty on 2011-07-08
I followed and instruction from the beginning and I'm able to compile (make and make install) emerald, however, I do NOT see emerald theme manager under settings. Can you give me some hints? Many thanks in advance...

---

### Post by charliewhizbeez on 2011-07-08
You may have to install compiz-fusion-icon (as described in the original post).

---

### Post by piotrv on 2011-08-31
[SIZE="3"]great tutorial!

compiz + cairo where the only issues stopping me to move away (in time) from GNOME (I don't even spend a word on Unity)

Now this tutorial saved me heaps of time.
Compiz is even working fine (why not) on Xubuntu running just from the LIVE_CD USB stick without rebooting  :) 

XFCE might safe us from more Ubuntu DE disasters..[/SIZE]

---

### Post by Nymn on 2011-10-27
I tried this on 11.10 but when I run the make and make install commands I get:

nymn@nymn-System-Product-Name:~/emerald$ make
make: *** No targets specified and no makefile found.  Stop.
nymn@nymn-System-Product-Name:~/emerald$ make install
make: *** No rule to make target `install'.  Stop.

:confused:

---

### Post by beew on 2011-10-27
> **Nymn said:**
> I tried this on 11.10 but when I run the make and make install commands I get:

nymn@nymn-System-Product-Name:~/emerald$ make
make: *** No targets specified and no makefile found.  Stop.
nymn@nymn-System-Product-Name:~/emerald$ make install
make: *** No rule to make target `install'.  Stop.

:confused:

Download and install the .deb packages from here.

[https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1/+build/2545504](https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1/+build/2545504)

It works for 11.10. I tried.

---

### Post by razaz03 on 2011-10-28
Last post gave 32bit packages and that's no good for me, have stable 64bit ones been released?

Second to last post had trouble with 11.10, so I assume unless the instructions are updated and the right emerald packages included, I don't wanna risk trying it as I've already tweaked and failed with it once (under ubuntu gnome but still)

Any help would be great

---

### Post by beew on 2011-10-29
These are all that I could find

[https://launchpad.net/ubuntu/oneiric/+source/emerald/+builds](https://launchpad.net/ubuntu/oneiric/+source/emerald/+builds)

---

### Post by antoinethewiz on 2011-10-29
The make and make install runs into a bunch of compilation errors on Xubuntu 11.10. As a result, the theme manager does not show in the settings menu.

---

### Post by Nymn on 2011-11-06
> **beew said:**
> Download and install the .deb packages from here.

[https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1/+build/2545504](https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1/+build/2545504)

It works for 11.10. I tried.

I was only able to install the libemeraldengine0_0.8.8-0ubuntu1_i386.deb one, as the other two were checked off as installed. Compiz still not working, though.:confused:

---

### Post by Cresho on 2011-11-10
#sudo apt-get install compiz compiz-plugins-extra compiz-plugins-main compizconfig-settings-manager gnome-themes

[https://launchpad.net/~malteworld/+archive/compiz/+packages](https://launchpad.net/~malteworld/+archive/compiz/+packages)

install libemeraldengine and emerald.  both debs work on my 32bit system.  dont use the dev since you dont need it.

then

applications menu->settings->settings manager->session and startup->application autostart

make new "add" from bottom

1st

name:compiz
command: compiz --replace ccp



name:emerald
command: emerald --replace


under applications menu->settings->settings manager->session and startup->application, remove checkmark under "automatically save session on logout"
when you log out, be sure to remove "save sessions for future log ins" checkmark so
 it can boot up clean.

for a real clean boot, delete all files in your /usernmane/.cache/sessions so delete all files.  not necessery but it helps in some cases.

---

### Post by Nixarter on 2011-11-13
When it gets to the part about installing compiz, I get this...

```
ubuntu@ubuntu:~$ sudo apt-get install compiz compiz-plugins-extra compiz-plugins-main compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compizconfig-settings-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package compiz-plugins-extra
E: Package 'compizconfig-settings-manager' has no installation candidate
ubuntu@ubuntu:~$ 
```

Any ideas?  I'm testing on a Kubuntu usb.

---

### Post by Cresho on 2011-11-14
> **Nixarter said:**
> 

Any ideas?  I'm testing on a Kubuntu usb.

well, this is specific to xubuntu.

---

### Post by Nixarter on 2011-11-18
> **Cresho said:**
> well, this is specific to xubuntu.

Yes, but he says it is the same for all, just change the part that mentions the default xubuntu window manager.  Apparently I did that wrong.  any ideas?

---

### Post by JustinGordon on 2011-11-25
> **3 frags left said:**
> **Protip: This tutorial also works on Kubuntu, Lubuntu or whatever Ubuntu distro you want. The only difference will be in the part where it mentions the default window manager of Xubuntu; replace it with the window manager of your distro.**
Good. Now, using a fix I borrowed from [this blog](http://demonic.cc/?p=50), we'll install a few packages we need, as well as using git repositories. You might save this as a script if you wish, or copy & paste everything. [color=#990000]PROTIP: To paste a line in a terminal session, use Ctrl+Shift+V.[/color]
```
sudo apt-get -y install libtool build-essential intltool libdecoration0-dev libglib2.0-dev libgtk2.0-dev libwnck-dev
#Install git and autoconf too if you don't have it
sudo apt-get install git autoconf
cd ~
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald
git checkout -b compiz++ origin/compiz++
./autogen.sh
make
make install
cd ~
rm -rf emerald
```
Once this is done, Emerald THeme Manager should be at your menu. Go check it under Settings.




I'm trying the instructions on 11.10, and I get the following errors when I try to make:

> make[2]: Entering directory `/home/justin/github/emerald/libengine'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/justin/github/emerald/libengine'
Making all in src
make[2]: Entering directory `/home/justin/github/emerald/src'
gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz   -I../include -DLOCALEDIR="\"/usr/local/share/locale"\" -DENGINE_DIR=\"/usr/local/lib/emerald/engines\"    -g -O2 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz   -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c: In function ‘decor_update_window_property’:
main.c:507:7: warning: assignment makes pointer from integer without a cast [enabled by default]
main.c:511:8: warning: passing argument 3 of ‘decor_quads_to_property’ makes pointer from integer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘struct decor_extents_t *’ but argument is of type ‘XID’
main.c:511:8: warning: passing argument 7 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_extents_t *’
main.c:511:8: warning: passing argument 10 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_quad_t *’
main.c:511:8: error: too many arguments to function ‘decor_quads_to_property’
/usr/include/compiz/decoration.h:189:1: note: declared here
main.c:518:7: error: ‘PROP_HEADER_SIZE’ undeclared (first use in this function)
main.c:518:7: note: each undeclared identifier is reported only once for each function it appears in
main.c: In function ‘decor_update_switcher_property’:
main.c:1944:7: warning: assignment makes pointer from integer without a cast [enabled by default]
main.c:1948:8: warning: passing argument 3 of ‘decor_quads_to_property’ makes pointer from integer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘struct decor_extents_t *’ but argument is of type ‘XID’
main.c:1948:8: warning: passing argument 7 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_extents_t *’
main.c:1948:8: warning: passing argument 10 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_quad_t *’
main.c:1948:8: error: too many arguments to function ‘decor_quads_to_property’
/usr/include/compiz/decoration.h:189:1: note: declared here
main.c:1962:7: error: ‘PROP_HEADER_SIZE’ undeclared (first use in this function)
main.c: In function ‘update_default_decorations’:
main.c:2375:7: warning: assignment makes pointer from integer without a cast [enabled by default]
main.c:2379:5: warning: passing argument 3 of ‘decor_quads_to_property’ makes pointer from integer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘struct decor_extents_t *’ but argument is of type ‘XID’
main.c:2379:5: warning: passing argument 7 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_extents_t *’
main.c:2379:5: warning: passing argument 10 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_quad_t *’
main.c:2379:5: error: too many arguments to function ‘decor_quads_to_property’
/usr/include/compiz/decoration.h:189:1: note: declared here
main.c:2385:4: error: ‘PROP_HEADER_SIZE’ undeclared (first use in this function)
main.c:2439:5: warning: passing argument 3 of ‘decor_quads_to_property’ makes pointer from integer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘struct decor_extents_t *’ but argument is of type ‘XID’
main.c:2439:5: warning: passing argument 7 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_extents_t *’
main.c:2439:5: warning: passing argument 10 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_quad_t *’
main.c:2439:5: error: too many arguments to function ‘decor_quads_to_property’
/usr/include/compiz/decoration.h:189:1: note: declared here
main.c:2443:5: warning: passing argument 3 of ‘decor_quads_to_property’ makes pointer from integer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘struct decor_extents_t *’ but argument is of type ‘XID’
main.c:2443:5: warning: passing argument 7 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_extents_t *’
main.c:2443:5: warning: passing argument 10 of ‘decor_quads_to_property’ makes integer from pointer without a cast [enabled by default]
/usr/include/compiz/decoration.h:189:1: note: expected ‘int’ but argument is of type ‘struct decor_quad_t *’
main.c:2443:5: error: too many arguments to function ‘decor_quads_to_property’
/usr/include/compiz/decoration.h:189:1: note: declared here
main.c: In function ‘update_window_decoration_size’:
main.c:3054:11: warning: assignment makes pointer from integer without a cast [enabled by default]
main.c: In function ‘update_switcher_window’:
main.c:3252:9: warning: assignment makes pointer from integer without a cast [enabled by default]
main.c:3301:11: warning: assignment makes pointer from integer without a cast [enabled by default]
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/justin/github/emerald/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/justin/github/emerald'
make: *** [all] Error 2


---

### Post by overmind81 on 2011-12-03
I have the same problem on Kubuntu 11.10

error: too many arguments to function ‘decor_quads_to_property’
error: ‘PROP_HEADER_SIZE’ undeclared (first use in this function)

---

### Post by tintinboss on 2012-04-11
Awesomely cool and after waiting like forever, I finally got it working!!! And thats also in Kubuntu 12.04 Precise Pangolin. Works without an issue!

Thanks a lot mate!!!

For anyone confused : IT WORKS.
Please Purge all Compiz and Emerald related packages from muon before you start! :)

---

