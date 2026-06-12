---
title: "Things you discovered you could do in Ubuntu that not many knew about"
date: 2011-03-13
forum: The Cafe
---

### Post by marl30 on 2011-03-13
I expect this to be a great thread, as perhaps someone will share some secret tips I never knew was possible in Ubuntu.

Anyhow, here are mine:

Grouping similar running task/windows. I just found this out a few weeks ago that this is possible in Gnome just like in KDE and Windows.  All you have to do is right click on the little separation icon beside the show-desktop icon on the bottom toolbar, then click preferences. Under Window grouping select always group windows.   

Task preview window. This is a similar feature to that of KDE and Windows in Gnome. This can be done through Compiz settings. Go to Extras then enable Window preview. 

Tabs in Gedit and nautilus. 

There are probably more, but those were the ones that came to memory. 

Let's hear yours.

---

### Post by Paqman on 2011-03-13
[Reinstall all your packages in one go.]("http://ubuntuforums.org/showthread.php?t=261366") Massive time-saver.

---

### Post by TriBlox6432 on 2011-03-13
Download vids from the internet without any additional plugins or anything.  Wait for a video (such as youtube) to buffer completely, and it's in your /tmp folder.  Just rename it and drag it to wherever you want.  ;)

---

### Post by sandyd on 2011-03-13
Use GDDR4 as part of your computer's RAM :D. VERY VERY FAST.

---

### Post by leviathan8 on 2011-03-13
```
ffmpeg -i video.extension music.extension
```

Easy way of converting music and video.

---

### Post by Alan D on 2011-03-13
Place your web browser cache into ram. You have a ram disk at /dev/shm which grows dynamically up to half the size of your ram.

---

### Post by marl30 on 2011-03-13
> **Paqman said:**
> [Reinstall all your packages in one go.]("http://ubuntuforums.org/showthread.php?t=261366") Massive time-saver.

Hmmm, this seems useful.

> **TriBlox6432 said:**
> Download vids from the internet without any additional plugins or anything.  Wait for a video (such as youtube) to buffer completely, and it's in your /tmp folder.  Just rename it and drag it to wherever you want.  ;)

Thanks for this one. I knew the videos get stored temporarily in cache, but never thought I could use them.  

> **sandyd said:**
> Use GDDR4 as part of your computer's RAM :D. VERY VERY FAST.

What is GDDR4?

---

### Post by Alan D on 2011-03-13
> **marl30 said:**
> 
What is GDDR4?

I think Sandyd means DDR4, a type of memory. My new computer is going to have DDR3. and GDDR is whats used in a graphics card.

---

### Post by pi3.1415926535... on 2011-03-13
> TriBlox6432	
Re: Things you discovered you could do in Ubuntu that not many knew about
Download vids from the internet without any additional plugins or anything. Wait for a video (such as youtube) to buffer completely, and it's in your /tmp folder. Just rename it and drag it to wherever you want. 

Unfortunately this no longer works for me, it is most likely because I have upgraded to Chrome and Chromium 9, though I have tried other browsers and they do not seem to work either.

---

### Post by Alan D on 2011-03-13
> **pi3.1415926535... said:**
> Unfortunately this no longer works for me, it is most likely because I have upgraded to Chrome and Chromium 9, though I have tried other browsers and they do not seem to work either.

Youtube made changes and they actually push the load indicator behind the actual load point. Then they delete it from your cache when its actually finished. You can try to catch it before that, or use one of the downloaders.

---

### Post by tjeremiah on 2011-03-13
> **Paqman said:**
> [Reinstall all your packages in one go.]("http://ubuntuforums.org/showthread.php?t=261366") Massive time-saver.

wow, thanks. I was thinking about doing a fresh install after 11.04 alpha. This really helps.

---

### Post by sandyd on 2011-03-13
> **Alan D said:**
> I think Sandyd means DDR4, a type of memory. My new computer is going to have DDR3. and GDDR is whats used in a graphics card.
and you can use that GDDR4 as RAM: [https://wiki.archlinux.org/index.php/Swap_on_video_ram](https://wiki.archlinux.org/index.php/Swap_on_video_ram)

Its called swap, but it just swaps to the GDDR4

---

### Post by weasel fierce on 2011-03-13
> **Alan D said:**
> Youtube made changes and they actually push the load indicator behind the actual load point. Then they delete it from your cache when its actually finished. You can try to catch it before that, or use one of the downloaders.

Is this a recent thing? I tried it a few weeks ago and it worked fine.

---

### Post by cguy on 2011-03-14
HOW TO SELECT TEXT:
You don't have to keep the left-button of your mouse pressed and move the pointer to the ending of your desired selection. (you could even outrun the desired ending in this way)

INSTEAD:
1. Click at the beginning of the selection.
2. Scroll (if necessary) to whereever the end of your selection is.
3. Press shift and keep it pressed.
4. Click where you want to end your selection.
5. Release all the buttons.

Voila! The text is selected without any troubles.

It works in text editors (ie: editable text fields) and browsers (ie: read-only text fields) alike.

---

### Post by sffvba[e0rt on 2011-03-14
> **cguy said:**
> HOW TO SELECT TEXT:
You don't have to keep the left-button of your mouse pressed and move the pointer to the ending of your desired selection. (you could even outrun the desired ending in this way)

INSTEAD:
1. Click at the beginning of the selection.
2. Scroll (if necessary) to whereever the end of your selection is.
3. Press shift and keep it pressed.
4. Click where you want to end your selection.
5. Release all the buttons.

Voila! The text is selected without any troubles.

It works in text editors (ie: editable text fields) and browsers (ie: read-only text fields) alike.

lol... You will be amazed about all the nifty things that can be done with shift and control when it comes to text editing etc. :)

One of my favorite finds of a while back was pressing F3 in Nautilus... give it a go :)


404

---

### Post by hotrod6657 on 2011-03-14
> **cguy said:**
> HOW TO SELECT TEXT:
You don't have to keep the left-button of your mouse pressed and move the pointer to the ending of your desired selection. (you could even outrun the desired ending in this way)

INSTEAD:
1. Click at the beginning of the selection.
2. Scroll (if necessary) to whereever the end of your selection is.
3. Press shift and keep it pressed.
4. Click where you want to end your selection.
5. Release all the buttons.

Voila! The text is selected without any troubles.

It works in text editors (ie: editable text fields) and browsers (ie: read-only text fields) alike.

This is not just a Ubuntu discovery.  Works in Windows too (at least in 7 it does).

---

### Post by Copper Bezel on 2011-03-14
Yep, it's in just about everything, like Ctrl+F. Relatedly, most applications will select the whole sentence (or often the paragraph) if you double-click it.

I thought I was the only one using Maximize Vertically, and it came up in Desktop Environments lately, with a lot of folks seeming fairly excited about it.

I liked finding out that the default application for folders can be changed - I still need Nautilus, but Thunar is a lot lighter if I just need to pull up a folder from Places. Search and Run in the Gnome Menu, too (I use Tracker and XFRun4.)

---

### Post by Random_Dude on 2011-03-14
> **not found said:**
> 
One of my favorite finds of a while back was pressing F3 in Nautilus... give it a go :)


Interesting.
On Nautilus I like it when it just plays an audio file by putting your mouse cursor over it. The Ctrl+H option for seeing hidden files and folders is also very useful. :)

Cheers :cool:

---

### Post by Ender985 on 2011-03-14
Great thread!

My contribution: you can set a number of applications to autostart whenever your computer is turned on, just by adding their command-line call to Preferences -> Startup Applications (for instance the call to launch chromium is "chromium-browser")

If you are willing to spend some time reading DevilsPie documentations, you can even set them to open to a specific workspace at a specific position!

---

### Post by Alan D on 2011-03-14
> **sandyd said:**
> and you can use that GDDR4 as RAM: [https://wiki.archlinux.org/index.php/Swap_on_video_ram](https://wiki.archlinux.org/index.php/Swap_on_video_ram)

Its called swap, but it just swaps to the GDDR4


Thanks, that is awesome.

---

### Post by BHEJU on 2011-03-14
I use small screen laptop. So the screen space is very important for me. And I found out that you can remove the bottom panel and add all the buttons from bottom panel and add them to top panel and end-up with one panel without missing any buttons. And joining that with grouping of icons.. great.

Cheers,

---

### Post by hotrod6657 on 2011-03-14
> **Ender985 said:**
> Great thread!

My contribution: you can set a number of applications to autostart whenever your computer is turned on, just by adding their command-line call to Preferences -> Startup Applications (for instance the call to launch chromium is "chromium-browser")

If you are willing to spend some time reading DevilsPie documentations, you can even set them to open to a specific workspace at a specific position!

My favorite for this is going to the options tab in Startup Applications, under Preferences, and selecting "remember currently running application" once I have everything open and positioned where I want it.

Still amazes me how quickly the OS loads even when I ask for a bunch of other applications to be launched compared to even old basic XP installs...

---

### Post by Old_Grey_Wolf on 2011-03-14
This is not strictly an Ubuntu capability. It will work on several Distros.

Using cssh (ClusterSSH) to control a number of xterm windows via a single graphical console window. It allows commands to be interactively run on multiple servers over an ssh connection.

It saves time when you have multiple identically configured computers and you need to update them. You just enter the command once and they all get the command.

I don't remember for sure but I think it has to be installed from the repositories.

---

### Post by Old_Grey_Wolf on 2011-03-14
This is not strictly an Ubuntu capability. It will work on several Distros.

If you have ever been remotely logged into a server and while running a process; such as, compiling a program you lost your connection to the server then you may want to investigate the "screen" command. When you loose your connection to a server the process terminates. Screen lets the process continue to run even when the connection is lost.

Here is a tutorial on "screen" that I found through Google [http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

---

### Post by NightwishFan on 2011-03-14
Well this is well known to power users, but I love apt-get source - dpkg-buildpackage (set my dpkg-buildflags to use -Os) and I can modify the source code of packages and rebuild them the way I want easy as pie. I managed to customise gmountiso, wine and etc the way I want. :D

---

### Post by Alan D on 2011-03-15
> **NightwishFan said:**
> Well this is well known to power users, but I love apt-get source - dpkg-buildpackage (set my dpkg-buildflags to use -Os) and I can modify the source code of packages and rebuild them the way I want easy as pie. I managed to customise gmountiso, wine and etc the way I want. :D


Tell me more about that? I have used apt-get source, but I never did figure out how to make it incorporate ubuntu changes.

---

### Post by el_koraco on 2011-03-15
F3 file browsing is my favourite

---

### Post by johntaylor1887 on 2011-03-15
> **TriBlox6432 said:**
> Download vids from the internet without any additional plugins or anything.  Wait for a video (such as youtube) to buffer completely, and it's in your /tmp folder.  Just rename it and drag it to wherever you want.  ;)

That's no longer true as of ubuntu 10.10. Videos no longer show up there.

I now use VideoDownloaderHelper Firefox add-on for this.

---

### Post by NightwishFan on 2011-03-15
> **Alan D said:**
> Tell me more about that? I have used apt-get source, but I never did figure out how to make it incorporate ubuntu changes.

It automatically should patch the downloaded source, at least it does for me.

---

### Post by hotrod6657 on 2011-03-15
> **el_koraco said:**
> F3 file browsing is my favourite

Just tried that and I love it!  That's really cool

---

### Post by marl30 on 2011-03-15
> **el_koraco said:**
> F3 file browsing is my favourite

Great share. I really like this one. :D

---

### Post by teet on 2011-03-15
I'm currently running natty but I think this is a compiz thing.  If you middle-click (scrollwheel click) on maximize your program will maximize itself vertically only.  If you right-click on maximize your program will maximize itself horizontally only.  This is really nifty since I have a widescreen monitor but prefer my browser to be in more of a standard 4:3 format (makes text easier to read).

-teet

---

### Post by wewantutopia on 2011-03-15
What does f3 do in nautilus?  It doesn't do anything for me.

---

### Post by Khakilang on 2011-03-15
I am a normal user and I haven't discover anything. I am just here to see what you guys discover.

---

### Post by weasel fierce on 2011-03-16
In Kubuntu, if you paste (middle mouse button f.x.) straight to the desktop, it pops up the notepad widget :)

---

### Post by mkendall on 2011-03-16
> **johntaylor1887 said:**
> [quote=TriBlox6432]Download vids from the internet without any additional plugins or anything. Wait for a video (such as youtube) to buffer completely, and it's in your /tmp folder. Just rename it and drag it to wherever you want.
That's no longer true as of ubuntu 10.10. Videos no longer show up there.

I now use VideoDownloaderHelper Firefox add-on for this.[/QUOTE]

No. I don't know why it's changed, but it isn't a 10.10 issue. My laptop with 10.10 still caches videos in /tmp. It's my laptop with 9.10 that doesn't. I noticed the change after a Flash update, but I don't know that the update is the cause.

---

### Post by 405jayb on 2011-03-16
Using crontab to delete pics every 30min in the .purple folder thats left behind from instant messenger.

---

### Post by Copper Bezel on 2011-03-16
> In Kubuntu, if you paste (middle mouse button f.x.) straight to the desktop, it pops up the notepad widget

Coordinately, in Gnome, dragging and dropping text to the desktop creates a .txt file. = )

---

### Post by Alan D on 2011-03-16
> **Copper Bezel said:**
> Coordinately, in Gnome, dragging and dropping text to the desktop creates a .txt file. = )

This I will find helpful. Thanks.

---

### Post by uRock on 2011-03-16
> **wewantutopia said:**
> What does f3 do in nautilus?  It doesn't do anything for me.

It is supposed to give you an extra pane so you can browser two folders at once.

---

### Post by wewantutopia on 2011-03-16
> **uRock said:**
> It is supposed to give you an extra pane so you can browser two folders at once.


Ah, thanks.  It must be in newer versions of nautilus.

I'm still using Karmic

---

### Post by uRock on 2011-03-16
> **wewantutopia said:**
> Ah, thanks.  It must be in newer versions of nautilus.

I'm still using Karmic

Yup, Karmic doesn't have that capability.

---

