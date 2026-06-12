---
title: "After Installing Lubuntu - Guide (Things to do &amp; Apps to Install)"
date: 2011-11-13
forum: Tutorials
---

### Post by amjjawad on 2011-11-13
[B][COLOR=Red]Moderators: Please do _not_ move this thread until I finish editing it, thanks :)
[/COLOR][/B]
[CENTER] [IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Lubuntu_logo.svg/320px-Lubuntu_logo.svg.png[/IMG]

[/CENTER]
 
[CENTER] [B][SIZE=4][COLOR=Navy]After Installing Lubuntu
Guide (Things to do & Apps to Install)
[/COLOR][/SIZE][/B][/CENTER]
 

[B][SIZE=4]_Index:_
[/SIZE][/B]
1- [Things you need to do after installing Lubuntu]("http://ubuntuforums.org/showpost.php?p=11453607&postcount=2")

2- [How To Install Applications in Lubuntu?]("http://ubuntuforums.org/showpost.php?p=11453609&postcount=3")
a- Applications in Repo
b- Applications NOT in Repo

3- [Applications You Can Install in Lubuntu]("http://ubuntuforums.org/showpost.php?p=11453612&postcount=4")

4- [Applications You Can Install in Lubuntu with Workaround (not directly)]("http://ubuntuforums.org/showpost.php?p=11453614&postcount=5")

5- [Applications You Can NOT Install in Lubuntu]("http://ubuntuforums.org/showpost.php?p=11453615&postcount=6")

6- [General Notes]("http://ubuntuforums.org/showpost.php?p=11453802&postcount=7")

7- [How To Remove Applications]("http://ubuntuforums.org/showpost.php?p=11453913&postcount=8")

8- [Your Favorite Application in Lubuntu rather than the default ones]("http://ubuntuforums.org/showpost.php?p=11453965&postcount=9")

---

### Post by amjjawad on 2011-11-13
[CENTER][SIZE=4][B]

[COLOR=Navy]Things to do after installing Lubutnu[/COLOR][/B]
[/SIZE][/CENTER]
 

1- You need to be connected to the Internet. Connect to the Wireless Network (You may need to Enter Security Password) OR Connect via Wired Network.

2- Menu > Accessories > LXTerminal

3- ```
sudo apt-get update && sudo apt-get upgrade
```

4- ```
sudo apt-get install lubuntu-restricted-extras
```

5- Some basic Applications/Utilities are not available so you may want to add them:

```
sudo apt-get install numlockx parcellite
```

numlockx = To Turn your Num Lock ON after logging in - there is a workaround to set Num Lock ON before logging in - will be explained later.

parcellite = Clipboard Manager. It's to save whatever you copy and paste. By default, it's not installed. If you close the application/window you are copying from, you will have nothing to paste so this application is very helpful, at least for me :)

---

### Post by amjjawad on 2011-11-13
[CENTER]**[SIZE=4][COLOR=Navy]How To Install Applicaitons in Lubuntu?[/COLOR][/SIZE]**
[LEFT]
[COLOR=Navy][B]A - Applications in Repositories
[/B][/COLOR][/LEFT]
[/CENTER]
[COLOR=Navy][B]B - Applications NOT in Repositories
[/B] [/COLOR]

[LEFT][U][COLOR=Navy][B]A- Applications in Repositories
      [/B][/COLOR][/U][/LEFT]
 There are three (3) simple ways to install ANY Applications from the Official Repositories:

[U][B]1- LXTerminal
[/B][/U]Menu > Accessories > LXTerminal
 
[IMG]http://i40.tinypic.com/2mr5jcl.jpg[/IMG]

For many users, The Terminal is the easiest and the fastest way to install the desired program/application. However, it could be a nightmare for new comers to Linux. PLEASE, do not be afraid, it will never bite you. Once you'll use it as per these instructions, you'll love it and might be addicted to it just like myself.

To install any program/application from the official repositories, please follow the following basic steps:

1- ```
sudo apt-get update
```2- ```
sudo apt-get install <packagename>
```Example:
```
sudo apt-get install vlc
``````
sudo apt-get install firefox
```You could also do this if you know what programs/applications you want to install:

```
sudo apt-get install vlc firefox
```Just leave one space between each package or program.

Sometimes, some programs have dependencies to be installed with them. If you issue the install command just like above, it will ask you whether to install all the dependencies or not. IF YOU KNOW what you are doing, then you can use "-y" at the end so it will not ask you whether you want to install them or not. Example:

```
sudo apt-get install vlc -y
```[SIZE=4][U][B]



2-  Synatpic
[/B][/U][/SIZE]This could be the favorite tool for many users, myself is included even though I tend to use The Terminal more often. Synaptic, which comes by default with Lubuntu, is VERY easy to use and straightforward.

Menu > System Tools > Synaptic Package Manager

You need to type your password so that you can use it.

[IMG]http://i40.tinypic.com/2qwkj6v.jpg[/IMG]


And the main interface of Synaptic will be: 

[IMG]http://i42.tinypic.com/2mqm2b7.jpg[/IMG]


To install any program/application, you need first to Click on "Reload" then Click on the Search Button and Type whatever you are looking for.

[IMG]http://i42.tinypic.com/x0pn9s.jpg[/IMG]


Then

Right Click on the package name and select "Mark for Installation".

[IMG]http://i43.tinypic.com/33oku2t.jpg[/IMG]


In case there are some dependencies to be installed, Mark them too and then Click "Apply" on the main interface of Synaptic.




[SIZE=4][B]_3- Lubuntu Software Center (LSC)_
[/B][/SIZE]Yes indeed. Stephen Smally and others developers are are working so hard on Lubuntu Software Center which hopefully will be included by default with Lubuntu 12.04.

Please check this update regarding LSC:

> Ladies and Gentlemen, Lubuntu Software Center 0.0.2 is out!
this is the first stable version, you can grab the tarball at [http://launchpad.net/lubuntu-software-center](http://launchpad.net/lubuntu-software-center)
Now we need your tests, you comments and your hints.

Regards

Stephen Smally

P.S. the PPA is always updated, but is recommended only for test.In the next section, I'll explain how to add it to your Lubuntu Installation.




[COLOR=Navy]**B - Applications NOT in Repositories**[/COLOR]

You can find lots of programs and applications in the official repository. However, some applications are not there by default and you need to add them first then install them.

Usually, the easiest and the fastest way, as always, is The Terminal. However, you can also do that with Synaptic but to be honest, I'm trying to use The Terminal as much as possible whenever possible.

[B][COLOR=Navy]Examples of these applications and How To add each one of them:[/COLOR]

1- Lubuntu Software Center:[/B]

From LXTerminal, please run these commands:
```
sudo apt-add-repository ppa:lubuntu-desktop/ppa
``````
sudo apt-get update
``````
sudo apt-get install lubuntu-software-center
```After installing LSC, you'll find under System Tools Sub-Menu.

You can also download and install LSC from here: [https://launchpad.net/lubuntu-software-center](https://launchpad.net/lubuntu-software-center)


**2- LXScreenshot:**

LXTerminal, please run these commands:
```
sudo apt-add-repository ppa:lubuntu-desktop/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install lxscreenshot
```

LXScreenshot will be found in: Menu > Accessories > LXScreenshot


[B]3- Faenza Icon Theme

[/B] From LXTerminal, please run these commands:

```
sudo add-apt-repository ppa:tiheum/equinox
``````
sudo apt-get update
``````
sudo apt-get install faenza-icon-theme
```

---

### Post by amjjawad on 2011-11-13
[COLOR=Red]_**Note:**_[/COLOR] All installation instructions will be given here based on LXTerminal. To use Synaptic, please refer to [this section]("http://ubuntuforums.org/showpost.php?p=11453609&postcount=3").

Theoretically, any application/program you can install in Ubuntu, you can also install it on Lubuntu. However, that does not mean it's 100% true. Some applications/programs need a workaround while few could not be installed for some reason.

In this section, I'll try to cover most of the applications you can install. If your favorite application is not listed, please don't feel bad :)

[U][B]1- Firefox
[/B][/U]Personally, I can't use any machine if Firefox is not installed. Or to be more specific, both Firefox and Chromium MUST be installed :)
I'm NOT going to talk about Firefox vs Chromium vs Other Browsers - this endless war/debate will never end.

To install Firefox, please run this command from LXTerminal:

```
sudo apt-get update && sudo apt-get install firefox
```[U][B]


2- VLC
[/B][/U]It's my favorite media player. I prefer to use one application for everything and whenever I need to watch or listen to something, I use VLC.

```
 sudo apt-get update && sudo apt-get install vlc
```[U][B][SIZE=4]


3- GNOME Applications[/SIZE]
[/B][/U]
[B]_a- GNOME Screenshot_
[/B]By default, if you press "Print Screen" button on your Keyboard, a Screenshot will be saved on your home folder. You don't really have full control over that. To make life easier, you can install your favorite Screenshot Program. For me, I prefer GNOME Screenshot.

```
sudo apt-get update && sudo apt-get install gnome-screenshot
```Note: some may prefer shutter:
```
sudo apt-get update && sudo apt-get install shutter
```[U][B]

b- GNOME System Monitor:
[/B][/U]LXTask is the default system monitor for Lubuntu. If you don't like it, you can install your favorite.

```
sudo apt-get update && sudo apt-get install gnome-system-monitor
```[U][B]


4- Shotwell:
[/B][/U]I always need a program to do some basic functions like Crop and stuff so I need something else rather than the default installed program.

```
sudo apt-get update && sudo apt-get install shotwell
```[U][B]


5- Libre Office[/B][/U]:
Surprised? don't be. It's true that Lubuntu meant to be used for Low Specifications Hardware but many users with better/new hardware are using it too. As already mentioned above, you can install most if not all of your favorite applications and programs in Lubuntu.

```
sudo apt-get update && sudo apt-get install libreoffice -y
```Note that: If you don't have enough space (HDD) or memory (RAM), better not to install "libreoffice". AbiWord is installed by default.


[U][B]6- Cairo Dock
[/B][/U]OH YES, you can for sure :)

```
sudo apt-get update && sudo apt-get install cairo-dock -y
```

---

### Post by amjjawad on 2011-11-13
Some applications/programs can't be installed directly as explained previously. In this section, I'll try to cover some of these programs which are widely used:

[B]_1- Skype:_
[/B]I have previously updated the [Wiki Pages]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides") and added How To Install Skype. I see no point to re-do that again here so please have a look at [**this link**]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_install_Skype")

---

### Post by amjjawad on 2011-11-13
A List of Applications/Programs that users have reported which don't work with Lubuntu for some reason either for a known bug or other restrictions.

I'll update this list on daily basis either based on Threads here on this forum where users reports problems, Launchpad or if someone posted on this thread stating that Application ABC didn't work.

Thank you!

---

### Post by amjjawad on 2011-11-13
1- Before installing any application or program, you need to refresh and update your Repositories. To do so, please run this command from LXTerminal *OR Click Reload in Synaptic*:

```
sudo apt-get update
```

To understand more about this command, please search on google or [check this]("https://help.ubuntu.com/8.04/serverguide/C/apt-get.html").

---

### Post by amjjawad on 2011-11-13
[CENTER]**[SIZE=4][COLOR=Navy]How To Remove Applications?[/COLOR][/SIZE]**

[LEFT]
[U][B]1- By using LXTerminal:
[/B][/U]To un-install or remove any application/program, please run this command:

```
sudo apt-get remove <packagename>
```For example:
```
sudo apt-get remove vlc
```In order to completely remove an application, please use:

```
sudo apt-get purge <packagename>
```For example:
```
sudo apt-get purge vlc
```You can use the same option like "-y" with the above two commands:
```
sudo apt-get purge vlc -y
```[U][B]


2- By using Synaptic:[/B][/U]
Same as we did before when we wanted to install an application but this time, the process is a little bit different with one simple step.

Type the name of the application you want to remove (use "Search" button), Right Click on the package name and Select "Mark for Removal" or "Mark for Complete Removal". I always use the 2nd option - Complete Removal. After that hit Apply and that's all.

[IMG]http://i44.tinypic.com/amxx1f.jpg[/IMG]
[/LEFT]
 [/CENTER]

---

### Post by amjjawad on 2011-11-13
If you have any favorite application and you would like to inquire about **OR** you want to test it but don't know how, please post here and I'll take care of the rest :)


[COLOR=Red][B]* [U]List Of Users-Favorite Applications in Lubuntu rather than the default:
[/U][/B][/COLOR]

**[COLOR=Sienna]* [/COLOR]**[U][B][COLOR=Sienna]List Of Users' Applications TO BE TESTED in Lubuntu:

[/COLOR][/B][/U][COLOR=Sienna][COLOR=Black]

[COLOR=DarkGreen]***These two list will be updated as per users input**[/COLOR]

[/COLOR][/COLOR]

---

### Post by amjjawad on 2011-11-13
Please note that this guide will be updated on daily basis ;)

Thank you for reading!

---

### Post by MG&amp;TL on 2011-11-14
Very good guide for beginners; boookmarked. Sorry it took me so long to find it. Minor pointers:

1-LXTerminl --> 1-LXTerminal (typo)

Perhaps you could do a 'preferred ways' of getting apps installed;  repos, deb downloads, rpm downloads, make/make install apps. (in that order)

You've got a 2) somewhere with no instructions. 

Is it really necessary to have apt-get update before every single apt-get install firefox/libreoffice etc?

Also might be worth pointing out that the Lubuntu software-center, while available and potentially very good, is quite buggy at the mo.

Also if you're suggesting firefox and libreoffice, why not suggest software-center, as in the ubuntu one?

Just trying to help, Michael

Great idea though. Although perhaps needs converting to a wiki page? I can do that if necessary...ill, so nothing else to do.

---

### Post by KBD47 on 2011-11-14
Nice thread. It might also be useful to have a thread dedicated to suggested programs to install. I know when I first came to Linux I spent tons of time trying to figure out the names of programs I needed for things like music, paint, to handle photos, etc. Just a suggestion.
Good work!
KBD47

---

### Post by ArtWeatherbee on 2011-11-17
Thank you for this guide! Impressive work and extremely helpful. Just switched to the Lubuntu world and I love it!

---

### Post by amjjawad on 2011-11-25
> **MG&TL said:**
> Very good guide for beginners; boookmarked.
Thanks :) 

> Sorry it took me so long to find it. 

It's ok.

> 1-LXTerminl --> 1-LXTerminal (typo)

Done, thanks :)

> Perhaps you could do a 'preferred ways' of getting apps installed;  repos, deb downloads, rpm downloads, make/make install apps. (in that order)
My job is to explain ALL the available methods to install an application and the user is free to use whatever he/she likes :)
However, I add my personal opinion to each way.

>  You've got a 2) somewhere with no instructions. 
Yes, I know and I didn't have time to add more. I'll try to add something else beside Skype.

> Is it really necessary to have ```
apt-get update
``` before every single apt-get install firefox/libreoffice etc?
To get the latest version of that application so Yes.

> Also might be worth pointing out that the Lubuntu software-center, while available and potentially very good, is quite buggy at the mo.
I have mentioned that already when I wrote this guide :)

> Also if you're suggesting firefox and libreoffice, why not suggest software-center, as in the ubuntu one?
You mean Ubuntu Software Center? I never tried it on Lubuntu and I don't think I'll. LSC should be ready with 12.04 beside I'm not a fan of Software Centers :D

> Great idea though. Although perhaps needs converting to a wiki page? I can do that if necessary...ill, so nothing else to do.
Thanks again :)
To be honest, I'm not interested in updating or adding any Wiki Page any more. I enjoy here on Ubuntu Forum more so I'll do what I enjoy the most.

---

### Post by amjjawad on 2011-11-25
> **KBD47 said:**
> Nice thread.
Thanks a lot, KBD47 :) 

> It might also be useful to have a thread dedicated to suggested programs to install. I know when I first came to Linux I spent tons of time trying to figure out the names of programs I needed for things like music, paint, to handle photos, etc. Just a suggestion.

I know what you mean and I've been there too except I didn't spend much time on searching because I was searching ONLY for the applications I needed to do something. I tend to use less Programs to keep the list as short as possible. No point to install 3-4 programs which do the same function (Music) IMHO.
Your suggestion is great actually and to be honest, that is one of the reasons why I created this thread :)

Thank you!

---

### Post by amjjawad on 2011-11-25
> **ArtWeatherbee said:**
> Thank you for this guide! Impressive work and extremely helpful. Just switched to the Lubuntu world and I love it!

Appreciate that, thanks :)

Welcome to Lubuntu World ... please enjoy and have fun :)

---

### Post by Adrianzo on 2011-12-02
how can I update audacious to the lastest version and why I don't already have it... is it really resource-hungry? or what?

thanks..!

PS: similar doubt with VLC and gnome mplayer... the second one is already shipped but not working properly... (moving files along differents harddrives while watching a movie and the gnome mplayer kept on dropping frames... switched to vlc and got a normal view of 30 fps)

---

### Post by amjjawad on 2011-12-02
Hi,

> **Adrianzo said:**
> how can I update audacious to the lastest version

```
sudo apt-get update && sudo apt-get upgrade -y
```Should take care of this.

Or, as always, you can do it via Synaptic Package Manager:

[IMG]http://i56.tinypic.com/2rw3w47.jpg[/IMG]

1- Write the program/application name on the Search Box.
2- Right Click on the name.
3- Select "Mark for upgrade".
4- Apply.
5- Done.

> why I don't already have it... is it really resource-hungry? or what?It's the **default application in Lubuntu** so I have no idea why you don't have it?! it should be there.

What OS are you using? how did you install it?


> PS: similar doubt with VLC and gnome mplayer... the second one is already shipped but not working properly... (moving files along differents harddrives while watching a movie and the gnome mplayer kept on dropping frames... switched to vlc and got a normal view of 30 fps)
I'm a VLC fan. I always install it and use it every time I install any Linux Distribution.
As for GNOME MPlayer, I haven't watched a movie and at the same time was transferring some files from one HDD to another but usually, it's a common issue (if I'm not mistaken) specially with low RAM and it also depends on the size of the files you are moving. I have noticed moving/copying files take almost all the resources and make the system slower regardless what OS I'm using. Well, that at least what is happening with me, my system is a bit old and I'm using IDE HDD so that explains why. However, I have 2GB RAM on this PC but the other one has less than 512MB so copying files is a headache while doing something else.
I might be wrong but this is what I do have.

Thank you :)

---

### Post by Kril on 2011-12-02
Hi, I'm a new Ubuntu user. I installed 10.04 Lynx x64 version of Ubuntu.
I wonder if I can use these useful things on my Ubuntu too or not.
Thanks for reply from now ^_^

---

### Post by amjjawad on 2011-12-02
> **Kril said:**
> Hi, I'm a new Ubuntu user. I installed 10.04 Lynx x64 version of Ubuntu.
I wonder if I can use these useful things on my Ubuntu too or not.
Thanks for reply from now ^_^

Hello and Welcome to Ubuntu Forum :)

Ubuntu and Lubuntu, both share the same repositories and same core system, it's just the default applications and the desktop (DE) which is different.

&#1613;So, to answer your question, YES, you can. Same approach/concept but the packages or applications may be different. For example, for Ubuntu, you need to install:

```
ubuntu-restricted-extras
```instead of:

```
lubuntu-restricted-extras
```So, to install the above package for Ubuntu, you need to issue this command from Terminal:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras -y
```Hope that will help :)

As a new user, my advice to you is keep reading and searching :) this is what I have done when I first joined this forum and started to use Linux. Perhaps it seems hard at the beginning but believe me, it's very easy :)

Good Luck!

Useful Links:

[www.googlubuntu.com]("http://www.googlubuntu.com")

[SIZE=1][Dual-Booting Windows & Ubuntu From A-Z]("http://ubuntuforums.org/showthread.php?t=1649050")

[/SIZE][SIZE=1][HOW TO Avoid Wubi & Install Ubuntu on USB Drive]("http://ubuntuforums.org/showthread.php?t=1650699")[/SIZE]

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by wjbite on 2011-12-07
Need to find an application or tool that will allow me to modify the default settings for the touchpad on my Viao laptop. The included KEYBOARD/MOUSE  tool will not give the ability to turn off the tap = left click. It thinks I am using a low level mouse instead of a touchpad.

Thanks - good thread.

---

### Post by amjjawad on 2011-12-08
> **wjbite said:**
> Need to find an application or tool that will allow me to modify the default settings for the touchpad on my Viao laptop. The included KEYBOARD/MOUSE  tool will not give the ability to turn off the tap = left click. It thinks I am using a low level mouse instead of a touchpad.

Thanks - good thread.

Hello and Welcome to Ubuntu Forum :)

Kindly have a look at: [http://ubuntuforums.org/showthread.php?t=1875683](http://ubuntuforums.org/showthread.php?t=1875683)

---

### Post by anewguy on 2011-12-18
Nice work you've been doing here!  I do plan to try Lubuntu soon as I am a little tired of unity, flash problems, etc., that I have in 11.10.

To that end I wanted to ask - is Synaptic Package Manager included in the default install?  I know in 11.10 you actually have to use the command line and apt-get it.

Thanks, and again, great work!

Dave ;)

---

### Post by amjjawad on 2011-12-18
> **anewguy said:**
> Nice work you've been doing here!
Thank you, my friend :)  

> I do plan to try Lubuntu soon as I am a little tired of unity, flash problems, etc., that I have in 11.10.
Please do and I'm here if you need anything :)

As for Flash, we had our little conversation lately ... I'm not sure how well Flash will work on Lubuntu? and I told you about what happened with me :) I had a discussion the other day with [lovinglinux]("http://ubuntuforums.org/member.php?u=649167") regarding flash but our discussion did not lead to any successful solution actually. I'm thinking to do some search or start a new thread to understand what is going on with me regarding flash but since everything is working perfectly except that game on facebook, it's not an urgent or top priority :)
As for other stuff, not sure if Lubuntu will be better for you than Ubuntu but if you are like me (like simple stuff), then you'll like it :)

> To that end I wanted to ask - is Synaptic Package Manager included in the default install?  I know in 11.10 you actually have to use the command line and apt-get it.

With Lubuntu 11.10, Synaptic is installed by default.
We also have this: [https://launchpad.net/lubuntu-software-center](https://launchpad.net/lubuntu-software-center)

> Ladies and Gentlemen, Lubuntu Software Center 0.0.2 is out!
this is the first stable version, you can grab the tarball at [http://launchpad.net/lubuntu-software-center](http://launchpad.net/lubuntu-software-center)
Now we need your tests, you comments and your hints.

Regards

Stephen Smally

P.S. the PPA is always updated, but is recommended only for test.



> Thanks, and again, great work!

Most welcome my friend, I appreciate that and if you need anything, you know how to find me :)

---

### Post by KalithDemoren on 2011-12-20
Hi,

I switched from Ubuntu to Lubuntu quite recently, and I have a few hints to share.

1) I use a laptop with a touchpad, and horizontal scrolling was not enabled by default. In Ubuntu I guess there is a GUI for it in Preference -> Mouse, but not in Lubuntu. To make it work, I had to input the following in the terminal :
```
synclient HorizEdgeScroll=1
```But it was way too slow for me. So I tweaked the speed a little with :
```
synclient HorizScrollDelta=100
```These two commands only last for the current session. To run these automatically at startup, you have to open ~/.config/lxsession/Lubuntu/autostart, copy the two commands inside the file, and save it.
I think it's a very useful feature and it's too bad that it cannot be enabled straightforwardly in lubuntu (that and the automatic num-lock).

2) I was missing the "quick filter" search box in synaptic package manager. To enable it, you have to install an additional package :
```
sudo apt-get install apt-xapian-index
```(source : [click]("https://sites.google.com/a/gillhouse.net/support/Home/tips-and-fixes/lubuntusynapticdoesnthavethequicksearchworking"))
It will consume some CPU to index all the packages during a few seconds, then the filter will be functional.

I hope you'll find these useful ;)
Finding informations on Lubuntu is quite hard I think, so it's a good initiative you have there.

---

### Post by amjjawad on 2011-12-22
> **KalithDemoren said:**
> Hi,

I switched from Ubuntu to Lubuntu quite recently, and I have a few hints to share.

1) I use a laptop with a touchpad, and horizontal scrolling was not enabled by default. In Ubuntu I guess there is a GUI for it in Preference -> Mouse, but not in Lubuntu. To make it work, I had to input the following in the terminal :
```
synclient HorizEdgeScroll=1
```But it was way too slow for me. So I tweaked the speed a little with :
```
synclient HorizScrollDelta=100
```These two commands only last for the current session. To run these automatically at startup, you have to open ~/.config/lxsession/Lubuntu/autostart, copy the two commands inside the file, and save it.
I think it's a very useful feature and it's too bad that it cannot be enabled straightforwardly in lubuntu (that and the automatic num-lock).

2) I was missing the "quick filter" search box in synaptic package manager. To enable it, you have to install an additional package :
```
sudo apt-get install apt-xapian-index
```(source : [click]("https://sites.google.com/a/gillhouse.net/support/Home/tips-and-fixes/lubuntusynapticdoesnthavethequicksearchworking"))
It will consume some CPU to index all the packages during a few seconds, then the filter will be functional.

I hope you'll find these useful ;)


Hello and Welcome to Ubuntu Forum :)

Thanks a lot for sharing this with us, I appreciate that. I'll test that on a laptop and will add that to Users' Contributions on Lubuntu One Stop Thread :)

> Finding informations on Lubuntu is quite hard I think, so it's a good initiative you have there.
Agreed, that's why I created some threads here but sadly some users don't really understand what I'm trying to do.

Lubuntu needs MORE care and MORE resources.

Thank you and welcome to Lubuntu :)

---

### Post by locojets54 on 2011-12-27
Hi,

First of all, thanks for putting in all the hard work it must have taken to assemble this awesome lubuntu thread.

I use ubuntu on my desktop and have recently started using lubuntu on my netbook. I use the Tracker search tool extensively on my desktop, and I have tried to get it up and running on lubuntu, but with no luck. The gui returns no search results even after I set up the indexing preferences. Any advice? Thanks in advance.

---

### Post by KalithDemoren on 2011-12-27
> **amjjawad said:**
> Lubuntu needs MORE care and MORE resources.
Yes, and a dedicated forum too...

Right now I'm in trouble with the F11 key. It toggles full screen mode in ALL applications (removes window decorations and sets window size to maximum), even those who actually use the F11 key for other purposes (for example : CodeBlocks uses it to toggle between .cpp files and .h files). I can't find anything on google to disable it, so if you have an idea... ;)

**Edit** : Fixed ! You have to edit ~/.config/openbox/lubuntu-rc.xml then search for "F11". You should see an entry with "ToggleFullScreen". Then you have two options : either completely remove this xml entry, or change the associated key. For example, changing "F11" to "A-F11" will change the key to Alt+F11 (source : [click](http://www.pclinuxos.com/forum/index.php?topic=71985.0)).

**Edit** : Ok maybe that was a little off topic. Let me correct this and give another piece of advice (coming from there : [click]("http://awesometoast.com/xfce4-power-manager-icon-missing/")).
By default, there is no power management item in the Preferences menu. To enable it, you have to run :
gksudo leafpad /usr/share/applications/xfce4-power-manager-settings.desktop
... and change (almost at the end of the file) :
OnlyShowIn=XFCE;
... to :
OnlyShowIn=XFCE;LXDE;

And there it is. I wonder why it's not enabled by default : that's a very important place to go. You can actually reach it by right-clicking the battery icon in the system tray... but only if you do have a battery in the first place.

---

### Post by amjjawad on 2011-12-29
> **locojets54 said:**
> Hi,

First of all, thanks for putting in all the hard work it must have taken to assemble this awesome lubuntu thread.

Hello and Welcome to Ubuntu Forum :)
Thanks for choosing and using Lubuntu ... you made the right choice ;)

Appreciate your nice words. I hope this thread will be helpful for you and everyone else.

> I use ubuntu on my desktop and have recently started using lubuntu on my netbook. I use the Tracker search tool extensively on my desktop, and I have tried to get it up and running on lubuntu, but with no luck. The gui returns no search results even after I set up the indexing preferences. Any advice? Thanks in advance.

I'm really sorry but I have no idea what you mean? sorry!
More information/explanation is highly appreciated :)

---

### Post by amjjawad on 2011-12-29
> **KalithDemoren said:**
> Yes, and a dedicated forum too...

Right now I'm in trouble with the F11 key. It toggles full screen mode in ALL applications (removes window decorations and sets window size to maximum), even those who actually use the F11 key for other purposes (for example : CodeBlocks uses it to toggle between .cpp files and .h files). I can't find anything on google to disable it, so if you have an idea... ;)

**Edit** : Ok maybe that was a little off topic. Let me correct this and give another piece of advice (coming from there : [click]("http://awesometoast.com/xfce4-power-manager-icon-missing/")).
By default, there is no power management item in the Preferences menu. To enable it, you have to run :
gksudo leafpad /usr/share/applications/xfce4-power-manager-settings.desktop
... and change (almost at the end of the file) :
OnlyShowIn=XFCE;
... to :
OnlyShowIn=XFCE;LXDE;

And there it is. I wonder why it's not enabled by default : that's a very important place to go. You can actually reach it by right-clicking the battery icon in the system tray... but only if you do have a battery in the first place.

This is totally off-topic so kindly start a new thread if you need that. Thank you :)

---

### Post by locojets54 on 2011-12-29
> **amjjawad said:**
> 
I'm really sorry but I have no idea what you mean? sorry!
More information/explanation is highly appreciated :)

I'm referring to the awesome desktop search tool, Tracker:

[http://projects.gnome.org/tracker/]("http://projects.gnome.org/tracker/")

I used to use Google Desktop until it was discontinued. I have found Tracker to be the next-best alternative. I have installed Catfish on Lubuntu for now, but it lacks the instant results aspect of Tracker. But, like I said, Tracker does not seem to be working right. I understand that it is completely possible that Tracker could be GNOME-exclusive, but I think people have gotten it to work on KDE, etc. If you have any ideas about getting it to work on Lubuntu, I'd really appreciate it. However, if you think it is going to be too resource-intensive and slow down my system (it is only a netbook, after all), I could live without it. Thanks again!

---

### Post by amjjawad on 2011-12-29
> **locojets54 said:**
> I'm referring to the awesome desktop search tool, Tracker:

[http://projects.gnome.org/tracker/](http://projects.gnome.org/tracker/)

I used to use Google Desktop until it was discontinued. I have found Tracker to be the next-best alternative. I have installed Catfish on Lubuntu for now, but it lacks the instant results aspect of Tracker. But, like I said, Tracker does not seem to be working right. I understand that it is completely possible that Tracker could be GNOME-exclusive, but I think people have gotten it to work on KDE, etc. If you have any ideas about getting it to work on Lubuntu, I'd really appreciate it. However, if you think it is going to be too resource-intensive and slow down my system (it is only a netbook, after all), I could live without it. Thanks again!

Never heard about that and never used it. I usually do some search and help the poster for set everything up but I'm actually still sick and recovering slowly ... I have logged in today because I'm tired of being on my bed :)

Perhaps it's because of PCManFM? I have no idea, sorry again.

As for your system being slow or not, it depends on your usage. If you have a decent CPU and RAM, that shouldn't be a problem. If you have low end hardware, then yes, you need to think twice but IMHO, the ONLY way to tell is to install and check ... in case any application will add any extra load, then you need to find another alternative.

---

### Post by arguson on 2011-12-30
If you used Google Desktop i'd recommend [Synapse]("http://www.omgubuntu.co.uk/2011/09/semantic-launcher-synapse-sees-release/"). Themes don't work properly in LXDE but its lightning fast and powerful. I use it as a search tool, launcher, command line, etc...

---

### Post by locojets54 on 2011-12-31
> **arguson said:**
> If you used Google Desktop i'd recommend [Synapse]("http://www.omgubuntu.co.uk/2011/09/semantic-launcher-synapse-sees-release/"). Themes don't work properly in LXDE but its lightning fast and powerful. I use it as a search tool, launcher, command line, etc...

wow, after trying this, i'm really impressed with the speed. i really like this, but i have a few questions:

1.) is there a way to see a list of the results without having to arrow down?

2.) more importantly, is there a way to control which directories are included in the search and which are excluded?

thanks for introducing me to this great new tool!

---

### Post by arguson on 2011-12-31
1. Change the theme to Vergilio, it displays the results as soon as you start typing
2. as far as i know, no. maybe you can set it in zeitgeist which synapse uses as an indexer but i never bothered with blocking directories from search results

---

### Post by locojets54 on 2011-12-31
> **arguson said:**
> 1. Change the theme to Vergilio, it displays the results as soon as you start typing
2. as far as i know, no. maybe you can set it in zeitgeist which synapse uses as an indexer but i never bothered with blocking directories from search results

thanks, the virgilio theme is perfect for me. and honestly, this thing is so stellar that i'm willing to live without being able to choose which directories show up. thanks so much.

---

### Post by ConchX on 2012-02-07
This is an amazing guide! Thank you for posting this :)
I have a problem though, in Lubuntu. When I download files that are archived, like tar, zip, rar etc.
I'm forced to select the file and click "Extract to" and then choose my folder. If I drag and drop the file into a folder, X completely freezes up & gives me an error saying that I don't have permission to drag and drop into the folder. I can't Alt+F2 to kill the archive manager, and I can't even kill X with Ctrl+Alt+Bckspace or Alt+PrntScrn+K
I'm forced to shutdown the computer with the power button and start it up again, which I hate to do :( 

Is there any way around this?

Thanks :)

---

### Post by KalithDemoren on 2012-02-07
> **ConchX said:**
> This is an amazing guide! Thank you for posting this :)
I have a problem though, in Lubuntu. When I download files that are archived, like tar, zip, rar etc.
I'm forced to select the file and click "Extract to" and then choose my folder. If I drag and drop the file into a folder, X completely freezes up & gives me an error saying that I don't have permission to drag and drop into the folder. I can't Alt+F2 to kill the archive manager, and I can't even kill X with Ctrl+Alt+Bckspace or Alt+PrntScrn+K
I'm forced to shutdown the computer with the power button and start it up again, which I hate to do :( 

Is there any way around this?

Thanks :)

Same problem here. The "solution" I found to regain control after this bug is to Ctrl+Alt+F1, login, "top", and kill (k) file-roller (use the > or < keys to find "file-roller" in the list and get its PID).

**Edit** : this is a confirmed bug :
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/884503](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/884503)
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/878993](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/878993)

The last bug report provides a possible solution : install the latest file-roler from source. I haven't tried it, but the user reporting it seems to have solved his problem that way.

**Edit 2** : I tried (with file-roller 3.3.3) and it didn't change a thing.

---

### Post by Rodney9 on 2012-02-07
> **ConchX said:**
> This is an amazing guide! Thank you for posting this :)
I have a problem though, in Lubuntu. When I download files that are archived, like tar, zip, rar etc.
I'm forced to select the file and click "Extract to" and then choose my folder. If I drag and drop the file into a folder, X completely freezes up & gives me an error saying that I don't have permission to drag and drop into the folder. I can't Alt+F2 to kill the archive manager, and I can't even kill X with Ctrl+Alt+Bckspace or Alt+PrntScrn+K
I'm forced to shutdown the computer with the power button and start it up again, which I hate to do :( 

Is there any way around this?

Thanks :)

Yes , don't try to drag and drop, just hit 'Extract'

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by amjjawad on 2012-02-07
> **ConchX said:**
> This is an amazing guide! Thank you for posting this :)
I have a problem though, in Lubuntu. When I download files that are archived, like tar, zip, rar etc.
I'm forced to select the file and click "Extract to" and then choose my folder. If I drag and drop the file into a folder, X completely freezes up & gives me an error saying that I don't have permission to drag and drop into the folder. I can't Alt+F2 to kill the archive manager, and I can't even kill X with Ctrl+Alt+Bckspace or Alt+PrntScrn+K
I'm forced to shutdown the computer with the power button and start it up again, which I hate to do :( 

Is there any way around this?

Thanks :)

You welcome and I'm glad you like it :)

I'm not aware of this issue as I don't do that. Things are running so crazy here and I need a miracle to test that and get back to you :(
I can't promise but will see what I can do.

We can't call an error a bug unless it can be re-produce. However, sometimes, it's so hard to re-produce an issue which is eventually called a bug.

---

### Post by seppalta on 2012-02-26
Thank you, Amjjawad, for a very nice guide.  Guides like this are invaluable to beginners.  They save enormous amounts of *search* time.  Wished I had had one when I started.      For anyone interested, I have constructed a "Beginners Guide" for LXDE in general:  [http://douwil7.100webspace.net/linux/Tuning.html](http://douwil7.100webspace.net/linux/Tuning.html)
All my computers run either Lubuntu or Mint LXDE.

---

### Post by Neosano on 2012-04-02
Kupfer is very useful too. I'm surprised that it's not included in this guide.

---

### Post by amjjawad on 2012-04-02
> **Neosano said:**
> Kupfer is very useful too. I'm surprised that it's not included in this guide.

I have never heard about it :)
There are millions of applications and there is no time or space to mention all that. 

This guide should be a general basic steps that will help anyone to deal with Lubuntu "after" installing it.

---

### Post by amjjawad on 2012-04-02
> **seppalta said:**
> Thank you, Amjjawad, for a very nice guide.  Guides like this are invaluable to beginners.  They save enormous amounts of *search* time.  Wished I had had one when I started.      For anyone interested, I have constructed a "Beginners Guide" for LXDE in general:  [http://douwil7.100webspace.net/linux/Tuning.html](http://douwil7.100webspace.net/linux/Tuning.html)
All my computers run either Lubuntu or Mint LXDE.

At your service :)
That is exactly why I wrote this guide. I've been there and I know how hard and tough that could be for a new comer. I don't like to use "beginner" because we are all here beginners :) we keep learning and learning until we die. We think we know everything but that is not even close.

Never too late. You can do the same, you can take this guide and make it even better, etc etc. Lots of ways to help the community :) you can help new comers by directing them to such guides, etc.

I have lots of ideas in mind but being involved with Lubuntu Team has left me with no time to do what I really want.

My time and efforts are both dedicated to Lubuntu and its team :)

Take care and I'm looking forward to work together as long as we have the same interest ;)

---

### Post by BlueKite on 2012-04-08
> **amjjawad said:**
> [CENTER]**[SIZE=4][COLOR=navy]How To Remove Applications?[/COLOR][/SIZE]**[/CENTER]

 

 
 
Hi, and thank for providing this informative thread!
 
I have a question regarding the removal of software.
 
I have been using Lubuntu for the past couple of days, and having found that I didn't like the Chromium browser, I decided to replace it with Midori which I have enjoyed using for the past 2 years.
This was easily done with Synaptic Package Manager, but there was a hitch when I tried to remove Chromium.
 
It seems that when you try to remove Chromium, Synaptic will automatically install Firefox and a few other things. This is despite the fact that I have already installed Midori and made it my preferred browser.
 
So my question is: How can I remove Chromium without having to install Firefox?
 
I haven't tried using the terminal to remove it yet - I'm asssuming the same thing would happen?
 
Any help would be appreciated.
 
Thank you muchly,
 
BlueKite.:)

---

### Post by Herpythebrony on 2012-04-09
I cannot change wm's or de's in it.

---

### Post by Herpythebrony on 2012-04-09
sudo apt-get install numlockx parcellite fixed it. Nice guide dude!

---

### Post by amjjawad on 2012-04-11
> **BlueKite said:**
> Hi, and thank for providing this informative thread!
 
I have a question regarding the removal of software.
 
I have been using Lubuntu for the past couple of days, and having found that I didn't like the Chromium browser, I decided to replace it with Midori which I have enjoyed using for the past 2 years.
This was easily done with Synaptic Package Manager, but there was a hitch when I tried to remove Chromium.
 
It seems that when you try to remove Chromium, Synaptic will automatically install Firefox and a few other things. This is despite the fact that I have already installed Midori and made it my preferred browser.
 
So my question is: How can I remove Chromium without having to install Firefox?
 
I haven't tried using the terminal to remove it yet - I'm asssuming the same thing would happen?
 
Any help would be appreciated.
 
Thank you muchly,
 
BlueKite.:)

BlueKite,

Hello and Welcome to Ubuntu Forum and Thanks for choosing and using Lubuntu :)

AFAIK (As Far As I know), removing Chromium has nothing to do with Installing Firefox. Honestly, I have never ever tried that at all despite the fact that I've been installing and using Ubuntu and/or Lubuntu for 2+ years now. If I'm the one who must answer that Q then I must do it myself and test it on a fresh new installation because I always install Firefox the first thing after any fresh installation for Lubuntu :) except for testing and that is Lubuntu 12.04 which is still on Beta2 phase.

Have you installed Lubuntu 11.10?

Why to remove Chromium on the first place? sorry for asking but if you ask me, I would strongly recommend to always keep another browser in any system as Plan B in case something may go wrong :) maybe I'm too caution? :D

Have you searched on Google? not sure if someone else has had the same issue of yours?!

---

### Post by amjjawad on 2012-04-11
> **Herpythebrony said:**
> I cannot change wm's or de's in it.
Sorry, what do you mean?

> **Herpythebrony said:**
> sudo apt-get install numlockx parcellite fixed it. Nice guide dude!

Glad it helped :)

---

### Post by BlueKite on 2012-04-11
> **amjjawad said:**
> BlueKite,
 
Have you installed Lubuntu 11.10?
 
Why to remove Chromium on the first place? sorry for asking but if you ask me, I would strongly recommend to always keep another browser in any system as Plan B in case something may go wrong :) maybe I'm too caution? :D
 
Have you searched on Google? not sure if someone else has had the same issue of yours?!
 
Hi, thanks for replying!
 
Yes, I have installed Lubuntu 11.10.
 
I tried Chrome a while back and never liked it, got rid of it fairly quickly. I did try Chromium briefly but felt it was just as bad as Chrome, and I've been very happy with Midori.
Having another browser available can be a good idea but as I've never had a problem with Midori I don't really see the point in keeping it.
 
I've just had a quick look on google and although other people mention removing it, there doesn't seem to be any discussion on how.
 
Maybe it's not the hassle I think it is....:confused:
 
Regards,
 
BlueKite.

---

### Post by amjjawad on 2012-04-12
> **BlueKite said:**
> Hi, thanks for replying!
 
Yes, I have installed Lubuntu 11.10.
 
I tried Chrome a while back and never liked it, got rid of it fairly quickly. I did try Chromium briefly but felt it was just as bad as Chrome, and I've been very happy with Midori.
Having another browser available can be a good idea but as I've never had a problem with Midori I don't really see the point in keeping it.
 
I've just had a quick look on google and although other people mention removing it, there doesn't seem to be any discussion on how.
 
Maybe it's not the hassle I think it is....:confused:
 
Regards,
 
BlueKite.

Hi again,

Looks like it's a known issue because when I searched on Google, I found some threads on Ubuntu Forum, here is one:

[http://ubuntuforums.org/showthread.php?t=1832162](http://ubuntuforums.org/showthread.php?t=1832162)

I put this on google and searched: > removing chromium will install firefox

I have NO clue WHY exactly Firefox will be installed when you remove Chromium? maybe somehow it's a default action when a user wants to remove the browser so the system will always have one. Firefox is the default browser in Ubuntu Systems and because Lubuntu is just another variant of Ubuntu, same will apply to it.
I need to ask someone with more experience about such behavior.

I'd suggest NOT to remove anything on the first place. Install your favorite application and keep the default one. 

I tried on Lubuntu 12.04 and it says the same and it doesn't matter whether you remove it from LXTerminal or Synaptic, both are the same except the front end (Synaptic is the GUI front-end of the terminal - both should do the same job).

I'm sitting now with 5 machines, 3 laptops and 2 PCs and I have tired that on two machines, one with Lubuntu 11.10 32-bit and the other is Lubuntu 12.04 32-bit and I can do the same with Lubuntu 11.10 64-bit but it's pointless, I'm sure it will do the same (install Firefox after removing Chromium).

If I will have a logical answer about this, I will post it here :)

Thanks!

---

### Post by BlueKite on 2012-04-12
Hi,
 
Thanks for checking on this.
 
It seems a shame to take up space with an unwanted program, but I'm happy to let it sit there if that's best. And as you say, it might be useful if anything should go wrong with Midori.
 
Thanks again for your help,
 
Regards,
 
BlueKite.):P

---

### Post by amjjawad on 2012-04-13
> **BlueKite said:**
> Hi,
 
Thanks for checking on this.
 
It seems a shame to take up space with an unwanted program, but I'm happy to let it sit there if that's best. And as you say, it might be useful if anything should go wrong with Midori.
 
Thanks again for your help,
 
Regards,
 
BlueKite.):P

Hi,

You most welcome and as promised, once I'll find a logical answer for installing Firefox upon Chromium removal, I will let everyone knows by posting here :)

As for space, if you have 4GB SSD HDD then I can understand why you want that (not sure how many MB Chromium needs) but if you have more space, then don't bother :) this is what I would do if I were you ;)
> Unused Space is Wasted Space = Unused RAM is Wasted RAM = nice theory :D

I've read somewhere that Midori is getting better but for me, I'm more into Chromium and Firefox. However, I think I need Midori here on this: [http://ubuntuforums.org/showpost.php?p=11832431&postcount=152](http://ubuntuforums.org/showpost.php?p=11832431&postcount=152)

By the way, there are different approaches when it comes to install Linux. Some prefer to go for "install everything as it is" path while some other prefer to go for "build it myself" path.
The 2nd path is a bit advanced for new users to Linux who are very new to Linux but it is NOT so hard to do.

If you are interested, you can follow [**this thread **]("http://ubuntuforums.org/showpost.php?p=11832431")or wait for me until I write a new guide for that :)

Why I'm telling you all that? because those who are always like to remove the default programs/applications and install their own may not be aware they can build their system as per their needs which is sometimes better than installing some packages then remove them.

---

### Post by HotForLinux on 2012-04-13
I was waiting for a guide like this. Excellent!!

In a Lubuntu forum once I posted a question about using a common brand USB headphones (I think it was Logitech) in a somewhat old PC, but never received a concrete answer. Maybe you could post some info about how to solve that kind of issues.

---

### Post by jola on 2012-04-13
Thanks a bunch for this guide. 
I'm new at all this -I installed Lubuntu last night- & would like to learn to use the terminal as much as possible, so thanks a lot. -jola

---

### Post by pdlethbridge on 2012-04-27
I all ways see info on what to add to lubunt but what can safely be removed from ubuntu to make it more like lubuntu

---

### Post by km3952 on 2012-04-28
This post has got separated from the question...re midori
@[B]BlueKite
@[/B][amjjawad]("http://ubuntuforums.org/member.php?u=941822")

It appears to be down to /etc/alternatives, see man update-alternatives; somewhat complex, but it looks like you can have midori installed & then remove chromium.

DO CHECK for yourself, I will accept no responsibility for your actions.  :)

---

### Post by amjjawad on 2012-04-28
> **pdlethbridge said:**
> but what can safely be removed from ubuntu to make it more like lubuntu

IMHO, the best approach is to download Lubuntu ISO, create a LiveCD or LiveUSB and install it rather than removing stuff from Ubuntu to make it more like Lubuntu :)

[https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu)

The Philosophy is different and the aim behind each system is different too. The time that you will need to change Ubuntu to make it look more like Lubuntu, IMHO, is more than just installing Lubuntu (remember, you can always Dual-Boot).

That is what I would do if I were you :)

There is another approach that some users prefer which is installing another DE so at the longin manager, you can choose whether to login to Lubuntu Desktop or Ubuntu Desktop.

If you still insist to remove stuff from Ubuntu to make it look more like Lubuntu than that is different story that I didn't even think to go through and honestly not sure what exactly you need to do to achieve that :)

---

### Post by pdlethbridge on 2012-04-28
About all I've taken put is Open Offic and Unity using synaptic and I've had no problems

---

### Post by amjjawad on 2012-04-29
> **pdlethbridge said:**
> About all I've taken put is Open Offic and Unity using synaptic and I've had no problems

Changing the default programs by removing them and install other programs will NOT give you something similar to Lubuntu, period. We are talking about **[COLOR=Red]System A[/COLOR]** **VS** **[COLOR=Blue]System B [/COLOR]**and there are many things that makes the real difference between each system. Lubuntu would have never been exist if it's "just" about the default apps :)

To be more accurate, I'm talking about "performance" and "design". If all what you want to achieve is using same apps of Lubuntu and have same look, that is totally a different story :)

---

### Post by MarceloG on 2012-05-11
Hi, help needed. Newbie here, installed Lubuntu 12.04 alternate install, trying to install flash. When I do:

```
sudo apt-get install lubuntu-restricted-extras
```

the terminal stops at the screen "TrueType core fonts for the Web EULA", which apparently awaits my confirmation, but I don't find how to confirm I accept the EULA terms. Same happens in Synaptic.

How to solve this?

---

### Post by howefield on 2012-05-11
Try pressing the tab key to activate the OK button and enter to proceed.

---

### Post by MarceloG on 2012-05-11
> **howefield said:**
> Try pressing the tab key to activate the OK button and enter to proceed.

That worked :)

Still, the flashplugin is installed... but not working. But that goes to another thread.

---

