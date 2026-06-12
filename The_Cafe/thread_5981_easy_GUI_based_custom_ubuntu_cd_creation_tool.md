---
title: "easy GUI based custom ubuntu cd creation tool"
date: 2004-11-23
forum: The Cafe
---

### Post by ubuntu_demon on 2004-11-23
Hi,

I think an easy GUI based custom ubuntu cd creation tool would be great for a future release of ubuntu. There are lot's of people who want to add / remove packages and add/edit simple things like :

-cronjobs
-services starting up (like removing cupsys from starting up)

Everyone would be able to easily create their own custom ubuntu cd for giving to friends or installing in their offices.

---

### Post by az on 2004-11-23
Are you working on this for us?

---

### Post by ubuntu_demon on 2004-11-24
Just curious at the moment how much interest there is for this and if anyone is working on something like this.

---

### Post by ubuntu_demon on 2004-12-02
If such a tool was available I could distribute my own customized ubuntu cd to my friends. It could for example contain mp3 and mpeg4 support without ubuntu having to worry about legal claims.

I promise I will be a good user and tell my friends about freedom.

---

### Post by MatthewMetzger on 2004-12-02
Not a bad idea. I suppose it wouldn't be that difficult to accomplish, but I have no idea how as I'm still fairly new to Debian based linux (used to be Fedora Core 2).

---

### Post by Daniel G. Taylor on 2004-12-03
If you can make a list of manual commands that are needed to do these things it will be pretty trivial to make a Python GTK app that does them. I could probably throw something together in a few days.

How does one go about making the custom cd's?

---

### Post by ubuntu_demon on 2004-12-04
The graphical frontend is indeed the easiest part. Any programmer could do that. I could do it myself too (although I've never programmed a graphical app in python I'm sure it wouldn't be too hard).

But the internals have to rock. 

Let's make a list our program has to be able to do

---

### Post by ubuntu_demon on 2004-12-04
these topics might be interesting also :

building ubuntu-based distro?
[http://www.ubuntuforums.org/showthread.php?t=2669](http://www.ubuntuforums.org/showthread.php?t=2669)

ubuntu ready for end-users?
[http://www.ubuntuforums.org/showthread.php?t=6996&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=6996&page=1&pp=10)

---

### Post by ubuntu_demon on 2004-12-04
There will be some tools in the future according to Jeff Waugh. But maybe "our program" will be easier or does things the other tools do not.

I'm not saying we are going to do create this program . But let's explore.

First we have to create the scripts that do the stuff and make sure they work. After that we add a slick GUI and package our program as a deb and try to make it available in universe.

I propose our program (let's invent a name soon) :
- manipulates the cd to add/remove packages but doesn't remove packages from ubuntu-base or ubuntu-desktop
- gives the user additional customization options (mentioned in use cases)
-creates a nice iso file
-burns cd
- installs a script that will be called after the normal ubuntu installation (expert or default or whatever). this script can :
*install a kernel
*install (meta)packages
*copy configuration files/scripts  to target locations
*call update-rc.d to remove/add things starting up (as selected in the customization program)
*change firefox home
*do once again a dist-upgrade

use cases of our program :

- "script dialogs" the installed script that is called right after the installation will present dialogs instead of doing things like : "do you want to change firefox home into introduction.html ?"
- "mount hoary cd-rom and copies it to a location on the harddisk"
- "add / remove packages from the cd" but does't allow to remove packages from ubuntu-base or ubuntu-desktop
- "create meta-packages"
- "select which packages are going to be installed additionally to the installation"
- "edit sources.list"
- "add file" add configuration files and scripts that will be copied on the harddisk at the end of the installation. lets you browse for a file on your harddisk and lets you type in a target location
-"stop services" lets you type in the services you want to stop (uses update-rc.d)
-"add instructions"  changes home of firefox to an ubuntu newbies guide or a html file you add
-"custom kernel selection dialog" adds a kernel selection dialog to the installation 686/386/amd/custom
-"create iso"
-"burn cd"
-"daily upgrades" adds a file into cron.daily with this content :
```

#!/bin/sh
apt-get update
apt-get upgrade -t hoary-security -y
apt-get upgrade --trivial-only
apt-get auto-clean

```

---

### Post by Daniel G. Taylor on 2004-12-04
Hmmm, rather than make "our program" I would recommend we actively let the official developers know that we need to be able to build a GUI around the tools they are making. It could be as easy as making a Python library that we could import and use, or letting us call their scripts and catch the output.

After that, a nice graphical tool would be quite easy to develop and maintain, and would be built on top of official tools as an extra point.

---

### Post by ubuntu_demon on 2004-12-05
I think their tools will have a gui.

We need to wait a little while until they inform us what they are making. (I've read some will be revealed at / around the ubuntu conference)

---

### Post by davidfeldman on 2004-12-06
I think this is a great idea. Ubuntu seems like one of the closest distros to being something a non-technical user could install and use in place of Windows, but there are a few configuration changes that I think would help, such as some changes to Nautilus defaults and a slicker-looking theme; as well as the addition of some mp3 software. A tool like this would make that easy to do.

We might be able to simplify things (particularly the user interaction) as follows: Instead of providing an extensive configuration UI, build the installation CD based on the current system configuration. So to create a new Ubuntu-based distro, you do a fresh Ubuntu install; set things up the way you want them, including user configuration, scripts and apps to run and startup and login, and packages installed. Then you run this tool, perhaps specifying a few additional options. The result is, effectively, an out-of-the-box system configured the way your system was when you ran the tool, with default account settings based on the main user (uid 500, presumably).

Might also be nice to work in the Debian Anaconda port, though I realize Ubuntu doesn't yet use it.

Anyway, I'd be happy to help. I'm a UI designer by profession, so I imagine I'd be most useful in designing the UI.

---

### Post by ubuntu_demon on 2004-12-06
> **davidfeldman]I think this is a great idea. Ubuntu seems like one of the closest distros to being something a non-technical user could install and use in place of Windows, but there are a few configuration changes that I think would help, such as some changes to Nautilus defaults and a slicker-looking theme said:**
> 

 If I understand you correctly. What you are describing is a clone/image tool. That's also very useful but mainly for getting your system quickly back onlne.  Does anyone know if an easy system cloning tool exists ? Maybe we could integrate such a tool with "our program". 

I think creating such a cloning tool is ** at least** as much work as creating "our program".  (think about scanning the system in a good way, what about packages that were installed by source ?, the ubuntu installer needs to be heavily modified or we need to use something else / write our own)

I for myself would like to use "our program"  to create an ubuntu cd that's more suited for the average-desktop-user (instead of optimalizing it for myself).

[QUOTE=davidfeldman]
Might also be nice to work in the Debian Anaconda port, though I realize Ubuntu doesn't yet use it.



I do not think we should work on the installer. Just use the available installer or run a script after their stuff is finished.

[QUOTE=davidfeldman]
Anyway, I'd be happy to help. I'm a UI designer by profession, so I imagine I'd be most useful in designing the UI.[/QUOTE]

That would rock ! 
Have you ever created an UI using python ?

---

### Post by davidfeldman on 2004-12-06
[QUOTE=demon666_nl]If I understand you correctly. What you are describing is a clone/image tool. That's also very useful but mainly for getting your system quickly back onlne.  Does anyone know if an easy system cloning tool exists ? Maybe we could integrate such a tool with "our program". [/QUOTE]

That might save some effort. What I'm suggesting is that instead of creating a whole separate interface by which you specify the configuration for your new Ubuntu-based distro, you tweak a copy of Ubuntu and then use "our program" to create an installation CD for it. I don't know if that's the same as a clone tool or not - the result is  an installable distro. I suggested it primarily because I thought it might be good from a user interface perspective: To create your new distro, install Ubuntu on a scratch partition, customize it as you want your distro to be, and then run "our program."

[QUOTE=demon666_nl]I for myself would like to use "our program"  to create an ubuntu cd that's more suited for the average-desktop-user (instead of optimalizing it for myself).[/QUOTE]

As do I. Again, I didn't mean to propose this as a way to clone a system, so much a distro-creation shortcut. You'd work off a separate, clean Ubuntu install.

[QUOTE=demon666_nl]That would rock ! 
Have you ever created an UI using python ?[/QUOTE]

I haven't. But I have created UIs in a whole bunch of other tools and languages so I could probably work it out :-). It also might make sense for me to do a design (in Photoshop, or perhaps in a good environment for prototyping such as VB...isn't there also a UI-building tool for GNOME?) and have someone else do the development. That may be easier to determine later on though.

---

### Post by ubuntu_demon on 2004-12-06
Creating the GUI is the least amount of programming time. (but obviously it's very important to create a nice and easy GUI)

Let's search and find out what kind of "clone tools" are available.

We have a couple of options. I think these are the import ones :
-adapting the ubuntu installer and generating a custom cd that everyone can download (we would not be creating a custom cd creation tool)
-creating / modifying a clone tool or creating a nice frontend for an existing one
-generating flags/input for a script that is called after installation (my favorite)

This thread is relevant for the script approach :
waih: Warty After Install Helper
[http://www.ubuntuforums.org/showthread.php?t=6708&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=6708&page=1&pp=10)

---

### Post by ubuntu_demon on 2004-12-06
I thought of some options for the "start script after installation approach". I was inspired by your (davidfeldman) posts.

the following options could be added to the GUI :

"current config files" - finds out what files in /etc are modified or created by the user and shows them to the user. The user may select one or more of these files to add to the custom cd.

I'm not sure how to do this. But I think it is possible.

"current installed packages" - finds out what packages are installed on top of ubuntu-base and ubuntu-desktop. only packages from official ubuntu repositories are listed. The user may select one or more to add them to the custom cd.

---

### Post by Daniel G. Taylor on 2004-12-06
[QUOTE=davidfeldman]I haven't. But I have created UIs in a whole bunch of other tools and languages so I could probably work it out :-). It also might make sense for me to do a design (in Photoshop, or perhaps in a good environment for prototyping such as VB...isn't there also a UI-building tool for GNOME?) and have someone else do the development. That may be easier to determine later on though.[/QUOTE]
You probably want to take a look at Glade. It may take a few minutes to get used to creating GTK+ GUIs; it's a bit different than Windows. There are some good tutorials online, here are a few that use Python for the actual application code:

[http://primates.ximian.com/~sandino/python-glade/#01-glade-main.png](http://primates.ximian.com/~sandino/python-glade/#01-glade-main.png)
[http://sjbrown.users.geeky.net/metagame-sector/tutorial.html](http://sjbrown.users.geeky.net/metagame-sector/tutorial.html)

---

### Post by davidfeldman on 2004-12-06
[QUOTE=demon666_nl]-adapting the ubuntu installer and generating a custom cd that everyone can download (we would not be creating a custom cd creation tool)[/QUOTE]

Wait, I'm confused. Isn't that what we're trying to create? A tool whose ultimate product is an install CD for a custom Ubuntu-based distro?

---

### Post by davidfeldman on 2004-12-06
[QUOTE=demon666_nl]"current config files" - finds out what files in /etc are modified or created by the user and shows them to the user. The user may select one or more of these files to add to the custom cd.[/QUOTE]

Yes. Exactly. This should be able to reduce the amount of scripting needed to create a distro.

[QUOTE=demon666_nl]"current installed packages" - finds out what packages are installed on top of ubuntu-base and ubuntu-desktop. only packages from official ubuntu repositories are listed. The user may select one or more to add them to the custom cd.[/QUOTE]

Again, exactly what I was thinking. In addition:

"user configuration" - uses the user's GNOME config, .login, .bashrc, .cshrc, and other files in the home directory as the initial configuration for users of the new distro. (There might be a default set of files to include, with the ability to select or deselect additional ones.) A nice addition to this would be the ability to select a user account to use as this template.

---

### Post by ubuntu_demon on 2004-12-07
[QUOTE=davidfeldman]Wait, I'm confused. Isn't that what we're trying to create? A tool whose ultimate product is an install CD for a custom Ubuntu-based distro?[/QUOTE]
 This option is not about creating a tool but about a custom cd that has a modified installer so that it offers more choices and does some configuring for the users(such a kernel choice and multimedia support). Such a custom cd would be harder for the average-desktop-user to use but saves time when a nerd wants to configure ubuntu for an average-desktop-user. 

I don't like this option because :
- starting a script after the installer is finished is more easy
- I don't want more choices for the average-desktop-user
- creating a tool to create custom cd's is more flexible and makes it possible for a lot of people to create their own custom cd

---

### Post by ubuntu_demon on 2004-12-07
[QUOTE=davidfeldman]Yes. Exactly. This should be able to reduce the amount of scripting needed to create a distro.
[/QUOTE]

I don't think we would safe scripting time. It only makes creating a custom cd a bit faster if you want it closely resemble your own configuration..

This approach introduces some problems like :

suppose a user builds a service/deamon from source. It would create a script in /etc/init.d. "our program" does find a package that could provide this script but when the user having installed the custom cd starts up his custom ubuntu system he discovers the script in /etc/init.d isn't compatible with the package.

I don't think it would be very easy to create a script that finds all the custom files in /etc .

It would do something like this :

```

generate a list of all files in /etc

for each file check if there is a package that provides the filename (at exactly that location)

if there's a package that provides it : check which version of that package is installed, download the package and check whether there are differences between the file in the downloaded package and the file in /etc. if there are differences add the file to the custom files list.

if there isn't a package that provides it : add the file to the custom files list

```

So for this to work you have to download almost all packages on your system again.

Another way is :

user starts "customize now"
```

-lock apt-get so the user can't use it
-create copy op /etc

```

the user may now customize his system
use touch to select a file you want in your customized system
or just modify the files you want

```

-select all files in /etc that differ from the copy
-unlock apt-get

```
[B]
This method is hardly easier for the user I think. The scripting part is easy.
This makes the UI cleaner. I think nerds will like it (I like it).
[/B]
another way is :

```

create copy of /etc and put this on the custom cd
after installation do a dist-upgrade and after that overwrite /etc with /etc on the custom cd

```

This method also sucks because you copy the entire /etc there's a greater risk some scripts/config files won't work anymore.

**Maybe there's another way. But I think it's going to be tricky scripting or isn't very easy for the user. Correct me if I'm wrong.**

[QUOTE=davidfeldman]
> 
"current installed packages" - finds out what packages are installed on top of ubuntu-base and ubuntu-desktop. only packages from official ubuntu repositories are listed. The user may select one or more to add them to the custom cd.

Again, exactly what I was thinking. 
[/QUOTE]

This packaging idea rocks. (no rant here :p)

[QUOTE=davidfeldman]
In addition:
"user configuration" - uses the user's GNOME config, .login, .bashrc, .cshrc, and other files in the home directory as the initial configuration for users of the new distro. (There might be a default set of files to include, with the ability to select or deselect additional ones.) A nice addition to this would be the ability to select a user account to use as this template.[/QUOTE]

this is going to be a lot easier. But I think it's better if a user customizes his own stuff if he needs it. Why would I decide what theme my friends are going to use ? Besides it easily introduces small problems like :

- oops I accidentily installed my bookmarks on the custom cd
- oops I accidentily put my mail on the custom cd
- oops I did it again  (britney  :mrgreen: )
-what if configuration file of a new gaim version isn't compatible with the old one?

---

### Post by randy on 2004-12-07
If you guys do this you should build in support for fully automatic installations.  It looks to me like this is going to be like Redhat Kickstart (which is great for what it does).  I've considered porting to Anaconda in the next couple of weeks in order to do a large scale deployment.

---

### Post by ubuntu_demon on 2004-12-07
> 
If you guys do this you should build in support for fully automatic installations. It looks to me like this is going to be like Redhat Kickstart (which is great for what it does). I've considered porting to Anaconda in the next couple of weeks in order to do a large scale deployment


good idea
you're right. It won't be very hard to do I think (if we have the rest).

1 user with a generated password that he has to change within 24 hours or something ?

---

### Post by randy on 2004-12-07
For my use i wouldn't have any local users on a machine.  I'd be running in a computer lab where all users authenticate via open afs, and mount a network share for there home directory.

---

### Post by ubuntu_demon on 2004-12-07
[QUOTE=randy]For my use i wouldn't have any local users on a machine.  I'd be running in a computer lab where all users authenticate via open afs, and mount a network share for there home directory.[/QUOTE]

does the ubuntu installer support  full automatic installations ?

---

### Post by ubuntu_demon on 2004-12-10
Hi,

I just decided I definetely will start coding on this "easy GUI based custom ubuntu cd creation tool". I'll probably start during my christmas break. Please PM me if you want to help me.

Let's invent a name guys(and girls)!

---

### Post by ubuntu_demon on 2004-12-18
maybe we should do something with kickstart ,debconf or cfengine. I'll look into it when I have more time.

I've read kickstart will be in hoary. I don't know anything about it except :

[http://www.ubuntulinux.org/wiki/KickstartCompatibility](http://www.ubuntulinux.org/wiki/KickstartCompatibility)

---

### Post by shimon on 2004-12-21
[QUOTE=randy]If you guys do this you should build in support for fully automatic installations.  It looks to me like this is going to be like Red hat Kick start (which is great for what it does).  I've considered porting to Anaconda in the next couple of weeks in order to do a large scale deployment.[/QUOTE]
 before you do any porting look at progeny they already did the tough job...

i wound like first to see a GUI for a making a deb package

and this app needs an options of changing default themes for gnome and gdm....

---

### Post by ubuntu_demon on 2004-12-21
[QUOTE=shimon]before you do any porting look at progeny they already did the tough job...[/QUOTE]

 I'm not planning to port anything. kickstart compatibility will be in ubuntu in the future.

[QUOTE=shimon]
i wound like first to see a GUI for a making a deb package
[/QUOTE]


I'll think about it

[QUOTE=shimon]
and this app needs an options of changing default themes for gnome and gdm....[/QUOTE]

yeah that would be nice

I'm going to do some research and some programming this holiday. Just to play with it and see whether it is feasible(is doable in not too much time). I would like to see a nice discussion about the GUI design and internal design here.

---

### Post by jdong on 2004-12-21
As far as design, I suggest a K3b-like approach: a standalone, mastering program.

Nautilus is repeating history by trying XP's failed burn-from-windows-explorer approach. We've seen that this doesn't work, because CD mastering can not be made identical to copying files across filesystems.

---

### Post by shimon on 2004-12-21
[QUOTE=jdong]As far as design, I suggest a K3b-like approach: a standalone, mastering program.

Nautilus is repeating history by trying XP's failed burn-from-windows-explorer approach. We've seen that this doesn't work, because CD mastering can not be made identical to copying files across filesystems.[/QUOTE]
 no no no
please use gtk+ and follow the gnome HIG

---

### Post by ubuntu_demon on 2004-12-22
[QUOTE=shimon]no no no
please use gtk+ and follow the gnome HIG[/QUOTE]
 I was thinking of learning pyGTK

---

### Post by kori.mendocino on 2005-02-09
have you thought of using dfsbuild in your system? just code a gui for customizing it's .conf file and it might work

---

### Post by ubuntu_demon on 2005-02-12
[QUOTE=kori.mendocino]have you thought of using dfsbuild in your system? just code a gui for customizing it's .conf file and it might work[/QUOTE]
 thnx for the tip.  At the moment I'm busy with school. But I'll look into it at some point.

---

### Post by ubuntu_demon on 2005-03-29
[QUOTE=demon666_nl]thnx for the tip.  At the moment I'm busy with school. But I'll look into it at some point.[/QUOTE]
 I haven't spend any time since my post at 12-22 thinking about custom cd creation.

here's a thread about a script created by ubuntu-geek to do your hoary postinstall. Maybe we could use this script/adapt it. :

[http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646)

I got triggered and went looking on the forums if there was any news about custom cd creation.

Let's update this thread with some info about creating custom cd's.

regarding this wiki page [http://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo](http://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo) :

[quote=Matt Zimmerman]
Many of the same customization techniques can be applied to both CDs,
because they share the same infrastructure. There is not yet a document
like the one for the live CD, but it is possible to create one, if someone
takes the time.
[/quote]

here's the post :
[http://www.ubuntuforums.org/showpost.php?p=68531&postcount=6](http://www.ubuntuforums.org/showpost.php?p=68531&postcount=6)

In this post colin watson says something about selecting packages/creating metapackages. But I don't quite get it :

[http://www.ubuntuforums.org/showpost.php?p=35716&postcount=33](http://www.ubuntuforums.org/showpost.php?p=35716&postcount=33)

In this thread colin watson is giving away the program they use to create ubuntu cd's :

[http://www.ubuntuforums.org/showthread.php?t=22124](http://www.ubuntuforums.org/showthread.php?t=22124)

And finally I'm curious about the rumors about cannonical creating something like a cd-customizer.

---

### Post by Roberto Rosselli on 2005-07-03
Hi demon666_nl,
have you tried this program:

[http://ibuild.livecd.net/](http://ibuild.livecd.net/)

They mention Ubuntu in their FAQ, but it is not at all clear (to me :) how to proceed to use ibuild with Ubuntu.

What about the "rumors about cannonical creating something like a cd-customizer"? Any news on that front?

I managed to create a modified version of the Ubuntu Live CD, but if there was a program to simplify the whole process that would be great!

Thanks,

	Roberto

---

### Post by ubuntu_demon on 2005-07-03
[QUOTE=Roberto Rosselli]Hi demon666_nl,
have you tried this program:

[http://ibuild.livecd.net/](http://ibuild.livecd.net/)

They mention Ubuntu in their FAQ, but it is not at all clear (to me :) how to proceed to use ibuild with Ubuntu.

What about the "rumors about cannonical creating something like a cd-customizer"? Any news on that front?

I managed to create a modified version of the Ubuntu Live CD, but if there was a program to simplify the whole process that would be great!

Thanks,

	Roberto[/QUOTE]
 Hi I'm still interested. But it has a low priority to me. I have a couple of other Ubuntu related ideas  I'm working on :).

I'll take a look at the link you gave me. I'll also look at the ubuntulinux.org/wiki regarding this subject. 

Also I'm more interested in modifying an breezy install cd if those things are gonna work like this (this will happen for dvd but I'm not sure if it will happen for cd too)  :

-boot like a live cd
-install with an easy tool after having booted into the livecd (knoppix has something like that)

---

### Post by Roberto Rosselli on 2005-07-03
[QUOTE=demon666_nl]Hi I'm still interested. But it has a low priority to me. I have a couple of other Ubuntu related ideas  I'm working on :).[/QUOTE]

Good luck with them then, can you tell us something about it? (Perhaps in a new thread?)

[QUOTE=demon666_nl]I'll take a look at the link you gave me. I'll also look at the ubuntulinux.org/wiki regarding this subject. [/QUOTE]

Thanks. I'm a non-programmer, non-geek Linux enthusiast trying to produce a Live CD for people working in the Humanities Computing field.

[QUOTE=demon666_nl]Also I'm more interested in modifying an breezy install cd if those things are gonna work like this (this will happen for dvd but I'm not sure if it will happen for cd too)  :

-boot like a live cd
-install with an easy tool after having booted into the livecd (knoppix has something like that)[/QUOTE]

Yes, that ("installing after trying") would be a very nice option for an Ubuntu live CD/DVD. An option I miss from Knoppix is the fast "set your home on the hard disk" option.

I'm looking forward to tools that make it easier to customize a Live CD/DVD, hope those "rumors" are true!

Thanks for your prompt reply.

Ciao

---

### Post by UbuWu on 2005-07-03
[QUOTE=demon666_nl]
Also I'm more interested in modifying an breezy install cd if those things are gonna work like this (this will happen for dvd but I'm not sure if it will happen for cd too)  :

-boot like a live cd
-install with an easy tool after having booted into the livecd (knoppix has something like that)[/QUOTE]

You are lucky, this is one of the high priority goals for breezy:
[http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals](http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals)
[http://udu.wiki.ubuntu.com/UbuntuExpress](http://udu.wiki.ubuntu.com/UbuntuExpress)

---

### Post by UbuWu on 2005-07-03
[QUOTE=Roberto Rosselli] An option I miss from Knoppix is the fast "set your home on the hard disk" option.
[/QUOTE]

Another breezy goal: persistent home directory:
[http://udu.wiki.ubuntu.com/LiveCDFeatures](http://udu.wiki.ubuntu.com/LiveCDFeatures)

---

### Post by ubuntu_demon on 2005-07-03
[QUOTE=Roberto Rosselli]Good luck with them then, can you tell us something about it? (Perhaps in a new thread?)
[/QUOTE]

-I've started a thread about a ubuntu commercial. I'm not an artist but it would be cool if we could get some artists together and create something slick.

-I still have to translate ubuntuguide to dutch

-I'm programming a traffic shaper. It will have easy configuration.

-I've started an Ubuntu europe tc:e clan

---

### Post by ubuntu_demon on 2005-07-03
[QUOTE=UbuWu]You are lucky, this is one of the high priority goals for breezy:
[http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals](http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals)
[http://udu.wiki.ubuntu.com/UbuntuExpress](http://udu.wiki.ubuntu.com/UbuntuExpress)[/QUOTE]
 Yeah I read something about that but I couldn't remember if they would do it for cd too :-P

---

### Post by brentoboy on 2006-04-25
Hey, are thre still people interested in this idea?

is [http://www.ubuntuforums.org/showthread.php?t=2669](http://www.ubuntuforums.org/showthread.php?t=2669) still the best referecen available on how to start?

I was thinking about making a utilty live CD that uses the new liveCD installer wizard, customized to install a server or xubuntu, or kubunutu, or ubuntu, (or "flubuntu" - fluxbox-ubuntu)  install from one CD, where the CD is a recovery CD that knows how to set up apt-get and download whatever else people want if they decide to use it to install it on the local PC.

Is there still a high level of interest in creating a custom CD tool?  I'd be happy to help...  I think that this is the best way to make ubuntu spread even faster. --build your own distro, give it to friends.

---

### Post by nalmeth on 2006-04-25
I am interested in this.
I'm more interested in making custom liveCD's though. Even a liveDVD as I have a DVDburner. All the more crap to throw on it..
My problem is that I don't have any idea how these liveCD making scripts work. 
I have seen these two:
[http://ibuild.livecd.net/](http://ibuild.livecd.net/)
and 
[http://www.linux-live.org/](http://www.linux-live.org/)

they both *sound* like they're easy to use, and hassle free, but the instruction's don't seem that clear to me. 
I want to make a liveDVD that has both gnome and kde 3.5, so probably using dapper. 
It seems that you need only install the system fresh, make the changes / add the packages you want, and run the live scripts.
It sounds too simple to work though.
I'm going to go make a fresh install of dapper beta, and start adding/removing things to my desires. In the meantime, can anyone who has tried / looked into this elaborate on what is really required, and what you need to do to get this going?

The whole system is going to have to be compressed, and decompressed on boot.
It all seems like it must be really complicated.

---

### Post by Roberto Rosselli on 2006-04-26
Hi brentoboy and nalmeth,
I would also be interested in such a tool. At the present moment the best resource is still this wiki page:

[https://wiki.ubuntu.com/LiveCDCustomizationHowTo](https://wiki.ubuntu.com/LiveCDCustomizationHowTo)

but there are a couple of TODOs and unanswered questions inside that document. Another resource is the GNOME Live CD page:

[http://live.gnome.org/GnomeLiveCd](http://live.gnome.org/GnomeLiveCd)

Luis Villa created a set of scripts to make a good deal the work automatic. On a more general level, see also this one:

[http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources](http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources)

Unfortunately I'm not a software developer, so the level of help I can offer is limited (mainly testing, bug reports and the like).

Ciao!

---

### Post by abs on 2006-04-26
I think this tool would be great,

any advances on this, as it seems this project has died in 2005,


--

---

### Post by ubuntu_demon on 2006-04-26
[QUOTE=abs]I think this tool would be great,

any advances on this, as it seems this project has died in 2005,


--[/QUOTE]
AFAIK no advances on this. But I haven't looked into it anymore since july 2005.

---

### Post by Kernel Sanders on 2006-04-26
Would this be something like nlite is for Windows XP? 

If so it would be an excellent idea! :) 

John :)

---

### Post by TeeAhr1 on 2006-04-26
I was discussing something like this with my roommate last week.  I'd like to find a way to make, for instance, an install CD for a high-performance machine, and one for legacy hardware (probably using XCFE).  I'm not looking for a user-customizable installer, just my own custom install CDs, so when I get a piece of old hardware in the house, I can just pop in the custom Xubuntu disc, press enter, have a working install half an hour later that I (or the user) can then customize manually.  So yeah, basically, a cloning tool that compresses the partition into an install CD.  Does anyone know if something like this already exists?

best-
p.daniels

---

### Post by brentoboy on 2006-04-26
I think that the custom live CD option with the new dapper "install from liveCD" wizard that is included on the live cd would do what everyone is talking about here.

What it sounds like the desire is is this:
We want to be able to take one of the existing liveCDs and create our own that has our favorite packages on it.  Maybe even expand it to be a dvd.

Some want it to be just a liveCD and others want it to be able to runt he install wizard that is on the dapper livecd.  BUT, they want the livecd installer wizard to run thier own "script" --in essence they want it to ask custom questions, and offer custom sources to download from.  But, at the same time they dont want to make a new distro, only a new slant on ubuntu.

For instance, I want to make "Brents-Unofficial-Ubunutu-Utility-CD" it boots into OpenBox window manager, has lots of recovery tools, and an install wizard for each of: ubuntu, kubuntu, xubuntu, and "flubuntu" (a fluxbox based ubuntu)  with a server option that asks questions about what services you are going to offer, and then installs the right packages for samba / apache / php / openvpn / thin-client stuff etc.  based on user selection.

We also need the custom-live-cd-maker to let us choose which debs should be included on the cd/dvd so that installing from CD could have the debs for the packages we want to include in a full install of our ubuntu-slant.

Then, ubuntu could remain free-free-free and people could make CDs that install codecs and fonts and things that many people are interested in, and ubuntu would not have to be directly responsible for what we decide to put on our custom live CDs.

---

### Post by mhancoc7 on 2006-07-04
I am really interested in this. What are the odds of something like this getting done? I have tried Linux Live, but I could not get the resulting livecd to boot up. Well it did boot, but it would not load the os.

Jereme

---

### Post by nalmeth on 2006-07-05
I've tried the LiveCD customization howto, but haven't finished yet.

I've chrooted into the system, but can't get apt to do anything...

Anyone actually had success in creating their own customized ubuntu liveCD?

---

### Post by Roberto Rosselli on 2006-07-06
There's now a GUI tool to change the default language + a set of scripts to do more complicated things, look here:

[http://lichota.net/~krzysiek/projects/ubuntu-livecd-customization/](http://lichota.net/~krzysiek/projects/ubuntu-livecd-customization/)

Still have to test it myself, but it looks promising.

Ciao

---

### Post by John.Michael.Kane on 2006-07-06
Theres something called [**MKDISTRO**]("http://www.dreamlinux.com.br/english/saiba-tutor.html") . I don't know if they have made the source available, however it maybe something to look into.

---

### Post by mhancoc7 on 2006-07-07
Thanks, I am going to give MKDISTRO a try. It looks promising.
Jereme

---

### Post by ubuntu_demon on 2006-07-17
I just discovered this great stuff !!! (from digg) :

[http://digg.com/linux_unix/Ubuntu_Customization_Kit](http://digg.com/linux_unix/Ubuntu_Customization_Kit)

> 
About
Ubuntu Customization Kit (UCK) is a set of tools for easy cutomization of Ubuntu Linux distribution (and its derivatives, like Kubuntu).
Currently it allows you to:

    * Create bootable LiveCD with predefined languages based on original Ubuntu/Kubuntu live CD using wizard with GUI.
    * Build live CD with special features using scripts. It is possible to customize root filesystem (for example install/remove packages), ISO contents (add/remove docs, change names) and initrd (add modules to boot, change boot sequence).

Currently UCK is a registered product on Launchpad, so see there for bug reports and other information: [https://launchpad.net/products/uck](https://launchpad.net/products/uck).
Development has moved to SourceForge: project is called uck.


I haven't tried it yet. But I've blogged about it here :
[https://ubuntudemon.wordpress.com/](https://ubuntudemon.wordpress.com/)

---

### Post by mhancoc7 on 2006-07-17
I am trying UCK right now. I saw this a while back, but I didn't understand the scripts. I think I have it figured out now. I will keep you all posted.
Thanks, Jereme

---

### Post by mhancoc7 on 2006-07-17
YES YES YES!!!! This is awesome. I just built my very own customized Ubuntu LiveCD using UCK. It took me a little while to figure out how to work the scripts, but I think I have got the hang of it. My first build was a very simple test. I built a Ubuntu LiveCD that has partimage included so I can use it to back up my system. Now on to bigger and better things.
Jereme

---

### Post by nalmeth on 2006-07-17
mhancoc7, that is excellent news!

I know you just tried it, but have you tried any other alterations? I can't wait to try it when I get home. My other attempts with this pursuit came up with problems.. Hopefully this is a good route

---

### Post by mhancoc7 on 2006-07-17
I have a pretty good handle on using apt-get install and apt-get remove. I have also figured out how to use dpkg to install .deb files not in the repos. I am really excited about this as well. It is really not that hard to do in fact to do basic removal and addition of packages is really simple. Now I want to create a custom LiveCD that uses the gnome setup that I like. Specifically I want it to use a custom icon for the Main Menu on the panel. I know how to do all this in my installation, but I am not sure what files I will need to edit to accomplish this with UCK. I have some ideas, but I haven't tried it yet.
Jereme

---

### Post by ubuntu_demon on 2006-07-24
Here's a relevant wiki page :
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by ehazlett on 2006-08-04
hey all...

i have created a gui tool that is currently in beta...  it is also in English and French and is being translated to a few others...  
 

[http://reconstructor.aperantis.com]("http://reconstructor.aperantis.com")

...written in python/pygtk and is, of course, GPL... ;)

i would love to hear what you all think/suggest...

thanks,

evan

---

### Post by ubuntu_demon on 2006-08-06
Here's the forum thread for reconstructor :

Reconstructor: Ubuntu Live CD creator/customizer
[http://www.ubuntuforums.org/showthread.php?t=229625](http://www.ubuntuforums.org/showthread.php?t=229625)

---

### Post by ubuntu_demon on 2006-08-09
UCK's new webpage :
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

You can find yet another way to create a customized live cd here :
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I blogged about UCK , Reconstructor and the new wiki page here :

Ubuntu CD Customization
[http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/](http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/)

---

### Post by atrus123 on 2006-08-10
> **ehazlett said:**
> hey all...

i have created a gui tool that is currently in beta...  it is also in English and French and is being translated to a few others...  
 

[http://reconstructor.aperantis.com]("http://reconstructor.aperantis.com")

...written in python/pygtk and is, of course, GPL... ;)

i would love to hear what you all think/suggest...

thanks,

evan

This looks pretty useful.  I will be testing it out in the upcoming days.

---

### Post by nalmeth on 2006-08-10
Me too, thanks for taking the plunge Evan, I will let you know if I can get it to work.

---

### Post by mhancoc7 on 2006-08-10
I have tried it with no success so far. I see that they have released the rc1 so I need to give it a go. I have found UCK to be pretty easy once you get the hang of it.
Jereme

---

### Post by Donshyoku on 2006-08-11
I have downloaded and install UCK from their site via .deb file... but how do I launch it?

It is not in any menu and it is not found when entering "uck" from the terminal.  The package, however, is installed according to Synaptic.

Help?

---

### Post by nalmeth on 2006-08-11
> **Donshyoku said:**
> I have downloaded and install UCK from their site via .deb file... but how do I launch it?

It is not in any menu and it is not found when entering "uck" from the terminal.  The package, however, is installed according to Synaptic.

Help?
I saw that .deb too, but just went with the tarball containing the scripts.

Unpack the tarball, and execute 
cd uck
./customize-cd-gui

This will guide you through a GUI, and eventually give you Synaptic to add/remove what you want.

I'm currently trying to get the manual scripts going, because I'd rather just have a terminal.

Perhaps what you've installed is just the customize-cd-gui tool. Try that.

---

### Post by mhancoc7 on 2006-08-11
Hi,
I have been using UCK quite a bit. Here is the basic command that is used to generate the custom live cd. You will need to have your customize scripts in the customize directory. The documentation for UCK is not that good, but this is a really powerful program.
[I]
sudo /usr/bin/remaster-live-cd [/I][I]path-to-iso-file.iso customization-dir/

[/I]Jereme

---

### Post by bakboneuk on 2006-08-14
Hi All..
Cn anyone tell me if any of this liveCD stuff actually works ? and how to install and run it ??

Sounds a bit daft but I downlaoded UCK, Stuck it on a fresh install of Dapper, and so far have found it very Y-UCK as far as "an easy cd remastering tool" goes its far from easy and so far doesn't even work.

The gui.sh script isn't written properly (error messages not written to display on terminal), does not detect Xdialog or gdialog, and I have no idea how to get the gui working ?

does Reconstructor 1.0 RC1 work ? I haven't tried it yet.

I have heard that the CD remastering software is on the liveCD of Ubuntu and can be run from the Cd ? is this correct.

Is CD Re-mastering a big secret that no-one wants to let go of? as I really am drawing a blank on everything I try to lookup on how to get into this subject! I'm not a Linux newbie but I don't know how a LiveCD works / autodetects devices / remasters

anyone able to point me in some sort of walkthroughs that actually explain whats happening?

Anyone know of a remaster tool that actually works?

---

### Post by mhancoc7 on 2006-08-14
> **bakboneuk said:**
> Hi All..
Cn anyone tell me if any of this liveCD stuff actually works ? and how to install and run it ??

Sounds a bit daft but I downlaoded UCK, Stuck it on a fresh install of Dapper, and so far have found it very Y-UCK as far as "an easy cd remastering tool" goes its far from easy and so far doesn't even work.

The gui.sh script isn't written properly (error messages not written to display on terminal), does not detect Xdialog or gdialog, and I have no idea how to get the gui working ?

does Reconstructor 1.0 RC1 work ? I haven't tried it yet.

I have heard that the CD remastering software is on the liveCD of Ubuntu and can be run from the Cd ? is this correct.

Is CD Re-mastering a big secret that no-one wants to let go of? as I really am drawing a blank on everything I try to lookup on how to get into this subject! I'm not a Linux newbie but I don't know how a LiveCD works / autodetects devices / remasters

anyone able to point me in some sort of walkthroughs that actually explain whats happening?

Anyone know of a remaster tool that actually works?

Yes, UCK works. I have used it with great success on my [Ubuntu Christian Edition]("http://www.christianubuntu.com") project.

The documentation is really not that good though. I do not use the GUI to do the re-mastering. I installed the UCK .deb package then I use the following terminal command.
* sudo /usr/bin/remaster-live-cd **path-to-iso-file.iso customization-dir/*

The *customization-dir/* is where your customize scripts go. This is basically a bash script to install/remove software. There are some examples in the UCK download. I have found it to be a bit tricky when messing around with changing graphics, sources.list, and other items that have specific permissions. However it definitely does work. I am hoping to get the chance to put together a How To, but for now I just do not have the time.

I have tried Reconstructor, but it did not work at all for me.

Good Luck, Jereme

---

### Post by H.E. Pennypacker on 2006-08-14
I really like this GUI idea!  Hopefully it will go far.

---

### Post by Yann_K on 2006-08-23
Hello guys, :KS 

I create a personnal Ubuntu "Dapper" CD Live.
But at the Ubuntu start session, I meet the error message below :

"user $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User's $HOME directory must be owned by user and not writable by another users"

I tried to search unsuccessfully the '.dmrc' file on my temporary Ubuntu's custom folder (like specified on [https://help.ubuntu.com/community/LiveCDCustomization/6.06](https://help.ubuntu.com/community/LiveCDCustomization/6.06)) to change file's permission (chmod 644 ~/.dmrc  and   sudo chown my_login /home/my_login/.dmrc   then   chmod 700 /home/my_login )
But this file is present on my local Ubuntu system (HDD).

What can I do ? :?: 

Many thanks !

---

### Post by ubuntu_demon on 2006-08-24
> **Yann_K said:**
> Hello guys, :KS 

I create a personnal Ubuntu "Dapper" CD Live.
But at the Ubuntu start session, I meet the error message below :

"user $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User's $HOME directory must be owned by user and not writable by another users"

I tried to search unsuccessfully the '.dmrc' file on my temporary Ubuntu's custom folder (like specified on [https://help.ubuntu.com/community/LiveCDCustomization/6.06](https://help.ubuntu.com/community/LiveCDCustomization/6.06)) to change file's permission (chmod 644 ~/.dmrc  and   sudo chown my_login /home/my_login/.dmrc   then   chmod 700 /home/my_login )
But this file is present on my local Ubuntu system (HDD).

What can I do ? :?: 

Many thanks !
Here's a bit of information about live cd customization :

[http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/](http://ubuntudemon.wordpress.com/2006/08/09/ubuntu-customization-kit-2/)

Creating a customized Ubuntu cd is on my to-do list and it will be relatively easy thanks to all these great efforts.

I haven't spent time on it yet. This is also not part of my Ubuntu Customization Guide(yet?).

I moved your post to a related thread. Let me know if you want a seperate thread.

---

### Post by jman6495 on 2007-03-24
Everyone Might Get Annoyed With Me @ This But.....
A Tool For Windows!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:confused: :confused: :guitar: 





Don't Hate Windows Hate Mac!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by allforcarrie on 2007-04-12
that is an awesome idea. Apperantly reconstutor doesnt work in feisty.

---

### Post by mhancoc7 on 2007-05-15
> **allforcarrie said:**
> that is an awesome idea. Apperantly reconstutor doesnt work in feisty.

Actually a new version just came out that works on Feisty.

Jereme

---

### Post by smartboyathome on 2007-06-20
> **mhancoc7 said:**
> Actually a new version just came out that works on Feisty.

Jereme

Well, this new version doesn't work for me. Besides, UCK is better for the functionality you get.

---

### Post by mhancoc7 on 2007-06-20
> **smartboyathome said:**
> Well, this new version doesn't work for me. Besides, UCK is better for the functionality you get.

Yes, I agree. I actually use both to build Ubuntu CE. 

Jereme

---

### Post by sandwormblues on 2007-07-29
This would be an awesome tool.  dfsbuild is a pain in the neck.

---

