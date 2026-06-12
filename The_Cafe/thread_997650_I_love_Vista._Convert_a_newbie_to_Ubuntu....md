---
title: "I love Vista. Convert a newbie to Ubuntu..."
date: 2008-11-30
forum: The Cafe
---

### Post by rpeters83 on 2008-11-30
I've been a windows guy since my first 386 Compaq with DOS and Windows 3.1. I'm a big fan of Vista I'll admit. However, I'm very interested in trying something new, mainly Ubuntu. I have 8.10 running on a separate partition and it's all set up to dual boot between Vista 32-bit and Ubuntu 64-bit. 

I'm very new to Ubuntu, though I have used Linux sparingly in the past. I'm trying to get familiar with the software and the user mindset of the community. Right now I tweaked my desktop with Compiz and played with the effects, as well as played around with the Add/Remove programs tools (I'm even typing this post on it). 

I have some features that I love about Vista that I'm not sure how, or if possible, to turn them on or enable them in Ubuntu. If you could, help me out. I'm not here to bash (rimshot?), but have noticed some initial pros and cons. 

SEARCH (most important)
I love how in Vista I can press the Start key and instantly type in stuff to find such as files or apps. Is it possible to do the same actions in ubuntu? I know there are search features and some program called Beagle seems pretty popular, but is it possible to get that same action on ubuntu?

ALIGN ICONS TO GRID
I can do this easily in Vista and it works. I can adjust the horizontal and vertical heights to my liking. On Ubuntu, I've figured out how to increase the icon size, but as far as alignment, mainly vertical alignment (they seem to have small, vertical locking increments) I would like to see this in Ubuntu or know how to adjust it. 

HOTMAIL SUPPORT
I use Windows Live Mail on Vista and use hotmail as my email. Is there a way to get Evolution or even Thunderbird to work with this? I found an extension for Thunderbird but can't seem to get it to work. 

CHOPPY VIDEO WITH COMPIZ
I tried to play a movie today. I liked how it gave me a bunch of options for codecs to install. Very nice. However, the video is very choppy. It seemed to be caused by Compiz, as when I turned it off, it was smooth. Can this be fixed?

FORCE QUIT APPS
How can I force quit an app? Unfortunately I've had quite a few apps freeze on me (like viewing certain screensavers mainly). How can I force quit an unresponsive app?

CLEAN UP PARTIAL OR SLOPPY INSTALLS
I tried to install something using the whole "make" and running the configure files for a program but gave up mid-way through. Is there a way to clean up these files that were made?

REMOTE DESKTOP TO WINDOWS SERVER
I use remote desktop to connect to a home server running at our house. When I try to connect, it refuses connection, though I can mount the shared drives just fine. What am I doing wrong? I don't want to use VNC if possible. 

Overall I think it's a great OS with a LOT of customisation options. It also seems a little faster at times than Vista. Finally, I LOVE the compiz effects, virtual desktops, and window management features (e.g., expose and rotating windows) it offers. 

I know I won't be able to run my games or Visual Studio, but if I can get help with the issues above, I'd be willing to make ubuntu my main OS. Thanks in advance for the help. 

Ryan

---

### Post by chucky chuckaluck on 2008-11-30
**xkill** is one of the best linux games ever. just type *xkill* into a terminal and a skull with crossbones will appear. use it to 'foce quit' any app you like.

*locate* and *whereis* are the two commands i use to look for stuff (usually something i downloaded to the wrong directory).

---

### Post by earthpigg on 2008-11-30
why convert you? if you are happy with and love vista, stick with it.

;)

---

### Post by sharks on 2008-11-30
> **earthpigg said:**
> why convert you? If you are happy with and love vista, stick with it.

;)

+1

---

### Post by Mr. Picklesworth on 2008-11-30
Err, folks, these are some nice questions. And people are allowed to love more than one operating system. (I love Fedora and Ubuntu, for example).
Don't derail the thread :)

> CLEAN UP PARTIAL OR SLOPPY INSTALLS
I tried to install something using the whole "make" and running the configure files for a program but gave up mid-way through. Is there a way to clean up these files that were made?You should *not* need to do that except in some unusual circumstances. For applications built from source, you can usually navigate to their source directory and run "make uninstall".
However, 99.9% of the time, what you need should be in Ubuntu's repositories or nicely available as a Debian package / package repository elsewhere (preferably aimed at Ubuntu). The Debian package system is cool because it handles installations in a completely centralized manner for everything that goes in to the system. Debian packages are carefully created by a generally quite trustworthy authority. In our case, they should all uninstall tidily, and when installed any dependencies (think .Net Runtime :P) are downloaded automatically. You can even Purge any package, which eliminates all of its configuration files, reinstall or reconfigure any package on your system.
It is super tidy.

Check out System -> Administration -> Synaptic Package Manager for advanced package management, or Applications -> Add / Remove... for more streamlined installation of applications.

As for your situation there, it doesn't sound like you ran "make install", (or at least not "sudo make install"), right? If so, there's nothing to worry about; everything is contained in the directory the program's source exists in. You can tidy it up selectively with "make clean". (Usually).

> FORCE QUIT APPS
How can I force quit an app? Unfortunately I've had quite a few apps freeze on me (like viewing certain screensavers mainly). How can I force quit an unresponsive app?The command xkill is one way to do it. Run the command, and then the next window you click will have its associated process annihilated. Careful with it. If you find that you have this sort of thing happen a lot, you can add that function to your panel. Right click the panel, choose Add To Panel and there is an applet to choose called Force Quit.

Oh course, the more typical solution is the list of processes. We have a nice one :)
Go to System -> Administration -> System Monitor. The Processes tab shows all your processes. You can go to the View menu and choose to view All Processes, to show Dependencies (a hierarchy of processes; eg: everything is a child process of init). The Resources tab has very pretty graphs.
Do not worry that there are hundreds of processes listed. Unix systems prefer piles of little, bite-sized programs over single monolitic ones. It's optimized to support this kind of operation quite well.

> CHOPPY VIDEO WITH COMPIZWhat kind of graphics card do you have? It's possible that Compiz just doesn't like your graphics card, although you could check if there are proprietary drivers available (often with more complete acceleration, unfortunately) by going to System -> Administration -> Hardware Drivers.

If the blame is indeed with Compiz, you could try 

> SEARCH (most important)
I love how in Vista I can press the Start key and instantly type in stuff to find such as files or apps. Is it possible to do the same actions in ubuntu? I know there are search features and some program called Beagle seems pretty popular, but is it possible to get that same action on ubuntu?This is one thing I completely *prefer* in Ubuntu vs. any non-free operating system even with all their marketing, although my bias is obvious. In Ubuntu (or really all of Linux land) every application on your computer is catalogued with a very detailed descriptive file with keywords, supported MIME types, categories, names and descriptions.
In this case, the good news is that you don't need to know an application by name to search for it!

My personal favourite search solution is the Deskbar applet (again added to your panel the same way as the Force Quit applet, although you may need to install it from the repositories first). Just type in the name of an application, document, note, etc. and gaze in wonder as it appears. It even does stemming, so for example "Photos" will give you "F-Spot Photo Manager" and "Cheese Webcam Booth" (Cheese also being an example of not needing to know the application by name -- at all).
I also use Beagle to keep track of documents, source code and whatnot. It's super fast and has a nice search tool. By default, Ubuntu uses Tracker which is the same idea really, with some advantages of its own (does a good job searching applications). Deskbar can integrate with either one.
Some people also use Gnome-Do, which is like QuickSilver for the Mac... except for Linux.


Don't be afraid to tinker. There is often some stuff hidden in context (right click) menus. Drag and drop can be satisfying a lot of the time. There are all sorts of options, such as configuring menu accellerator keys. (In System -> Preferences -> Appearance and the Interface tab). You can change the fonts to whatever you want (big? small? long? tall?). TONS of things you can install in Add / Remove Applications.
Expect there to be all sorts of little goodies, and don't be afraid to ask if they exist. I would love to list them all here, but that would be a very long list and everyone would be tired of me if I did.

---

### Post by cmay on 2008-11-30
> FORCE QUIT APPS
How can I force quit an app? Unfortunately I've had quite a few apps freeze on me (like viewing certain screensavers mainly). How can I force quit an unresponsive app?there is more than one way. 
1 click like a mad man on the close button until a force quit dialog appear.
2 run ps -ax to list all current running programs and kill the one you do not want. 
if you really want just out then ctrl+alt+ this key[ <- ] works on my keyboard as instant reboot. maybe it can be setup in another way.

but if you really love windows then i am not going to convert you. in fact if you like dos aslo then i suggest to give FreeDOS a spin on a old pc that has very little or no use at all. i do that also and its kinda cool to program turbo pascal on it. :)
good luck

---

### Post by eternalnewbee on 2008-11-30
> SEARCH (most important)
I love how in Vista I can press the Start key and instantly type in stuff to find such as files or apps. Is it possible to do the same actions in ubuntu? I know there are search features and some program called Beagle seems pretty popular, but is it possible to get that same action on ubuntu?
Maybe this will help.
> ALIGN ICONS TO GRID
I can do this easily in Vista and it works. I can adjust the horizontal and vertical heights to my liking. On Ubuntu, I've figured out how to increase the icon size, but as far as alignment, mainly vertical alignment (they seem to have small, vertical locking increments) I would like to see this in Ubuntu or know how to adjust it.

Right-click on the desktop, and see options.
> HOTMAIL SUPPORT
I use Windows Live Mail on Vista and use hotmail as my email. Is there a way to get Evolution or even Thunderbird to work with this? I found an extension for Thunderbird but can't seem to get it to work.
Use Pidgin.
> CHOPPY VIDEO WITH COMPIZ
I tried to play a movie today. I liked how it gave me a bunch of options for codecs to install. Very nice. However, the video is very choppy. It seemed to be caused by Compiz, as when I turned it off, it was smooth. Can this be fixed?
Check your Hardware Driver.
> FORCE QUIT APPS
How can I force quit an app? Unfortunately I've had quite a few apps freeze on me (like viewing certain screensavers mainly). How can I force quit an unresponsive app?
Press ALT-F2, and enter xkill. And click on the unresponsive application.
> CLEAN UP PARTIAL OR SLOPPY INSTALLS
I tried to install something using the whole "make" and running the configure files for a program but gave up mid-way through. Is there a way to clean up these files that were made?
In a terminal enter: sudo apt-get clean
> REMOTE DESKTOP TO WINDOWS SERVER
I use remote desktop to connect to a home server running at our house. When I try to connect, it refuses connection, though I can mount the shared drives just fine. What am I doing wrong? I don't want to use VNC if possible.

Never done this. Google it, and add ubuntu.org at the end of your search string.

By the way. Check my name.
If it weren't for the Ubuntu Community, I'd probably be lost.
And one more thing. Nobody here (except maybe some kids) will try to win you over to Ubuntu. If you want to switch, that's your choice.
If you are a Vista lover, just stick to what you've got.
Ubuntu is not Windows. It's like comparing English with Italian. You don't learn a new language overnight. It takes time and effort. I could say so much more, but this basically wraps it up.

---

### Post by Giant Speck on 2008-11-30
> **earthpigg said:**
> why convert you? if you are happy with and love vista, stick with it.

;)

+1 Definitely.

Now, don't take that to mean "Stay away from Ubuntu, n00b."  I'm not telling you to stop using Ubuntu because you like Vista.  I like and still use Vista, too.

Now, let's see if we can help you:

> SEARCH (most important)
I love how in Vista I can press the Start key and instantly type in stuff to find such as files or apps. Is it possible to do the same actions in ubuntu? I know there are search features and some program called Beagle seems pretty popular, but is it possible to get that same action on ubuntu?

Searching for files in Ubuntu is fairly easy.  Just go to the Places menu on the top panel, and select "Search for Files".

> ALIGN ICONS TO GRID
I can do this easily in Vista and it works. I can adjust the horizontal and vertical heights to my liking. On Ubuntu, I've figured out how to increase the icon size, but as far as alignment, mainly vertical alignment (they seem to have small, vertical locking increments) I would like to see this in Ubuntu or know how to adjust it.

Unfortunately, the only way to align icons in Ubuntu is to right-click the desktop and select "Keep Aligned."  Unless I'm mistaken, there currently isn't a way to vertically or horizontally align icons, nor is there a way to set horizontal and vertical alignment amounts.

> HOTMAIL SUPPORT
I use Windows Live Mail on Vista and use hotmail as my email. Is there a way to get Evolution or even Thunderbird to work with this? I found an extension for Thunderbird but can't seem to get it to work.

Try this:  [http://lifehacker.com/software/hotmail/check-hotmail-using-thunderbird-34583.php](http://lifehacker.com/software/hotmail/check-hotmail-using-thunderbird-34583.php)

> CHOPPY VIDEO WITH COMPIZ
I tried to play a movie today. I liked how it gave me a bunch of options for codecs to install. Very nice. However, the video is very choppy. It seemed to be caused by Compiz, as when I turned it off, it was smooth. Can this be fixed?

I'm not sure how to help you with this.  What media player were you trying to play the video in?

> FORCE QUIT APPS
How can I force quit an app? Unfortunately I've had quite a few apps freeze on me (like viewing certain screensavers mainly). How can I force quit an unresponsive app?

Type Alt+F2.  When the Run Dialog pops up, enter

```
killall [application]
```

Substituting [application] for the name of the application.

You can even start System Monitor, right-click on the process in the Processes tab, and select "Kill process."

> CLEAN UP PARTIAL OR SLOPPY INSTALLS
I tried to install something using the whole "make" and running the configure files for a program but gave up mid-way through. Is there a way to clean up these files that were made?

You could try this command in the terminal:

```
sudo apt-get install -f
```

> 
REMOTE DESKTOP TO WINDOWS SERVER
I use remote desktop to connect to a home server running at our house. When I try to connect, it refuses connection, though I can mount the shared drives just fine. What am I doing wrong? I don't want to use VNC if possible.

This one I know I can't help you with.  Sorry.  Hopefully, someone else can find the solution to this problem for you.

---

### Post by Bou on 2008-11-30
> **rpeters83 said:**
> SEARCH (most important)
I love how in Vista I can press the Start key and instantly type in stuff to find such as files or apps. Is it possible to do the same actions in ubuntu? I know there are search features and some program called Beagle seems pretty popular, but is it possible to get that same action on ubuntu

Hi Ryan,

I just got an idea from reading that, and filed a suggestion. You can see (and support it) [here]("https://bugs.launchpad.net/ubuntu/+source/deskbar-applet/+bug/303641"), and you can see a self-explaining mockup attached.

---

### Post by Mazza558 on 2008-11-30
> **Bou said:**
> Hi Ryan,

I just got an idea from reading that, and filed a suggestion. You can see (and support it) [here]("https://bugs.launchpad.net/ubuntu/+source/deskbar-applet/+bug/303641"), and you can see a self-explaining mockup attached.

Great idea. :)

---

### Post by lametike on 2008-11-30
is vista that good?lots of app cant run....chunks of prob and i hate it to the bones...

---

### Post by Bou on 2008-11-30
By the way, I also created a Brainstorm idea: [http://brainstorm.ubuntu.com/idea/16081/](http://brainstorm.ubuntu.com/idea/16081/)

---

### Post by Vince4Amy on 2008-11-30
> CHOPPY VIDEO WITH COMPIZ

Which player are you using to view videos, if it's mplayer there is an easy way to fix this.

---

### Post by bonzodog on 2008-11-30
> **rpeters83 said:**
> 
CLEAN UP PARTIAL OR SLOPPY INSTALLS
I tried to install something using the whole "make" and running the configure files for a program but gave up mid-way through. Is there a way to clean up these files that were made?
Ryan
Did you run "configure" then "make", then "make install". If you ran it all the way to make install, then the prog is installed across your system. To remove it, go back to the original source directory where it was, and run "make uninstall".

If, however, you did not get that far, then all the files for the program are still contained in the source directory, and you can simply delete the directory.

---

### Post by tsali on 2008-11-30
Sounds like you are expecting a drop in replacement for Vista...which Ubuntu is not.

I will be the first to admit that Vista is very good...it is my primary OS and has very slick features.

HOWEVER...once you can get oriented that Ubuntu is a complete OS and desktop environment in its own right, it puts you in a better position to appreciate the way things are done...even if they aren't the same as Vista.

Many of your questions would be better answered in the technical sections of the forum.

You may also find that different desktop environments offer things more to your liking. I would say that KDE offers a more Windows-like environment.

Try giving Kubuntu a shot and see what you think.

---

### Post by rpeters83 on 2008-11-30
WOW! This is another reason I like linux - the quick responses. 

I'm not expecting anyone to win me over. I've been wanting to play with Ubuntu for a while but my older laptop could not run it due to unsupported (or hard to find) ATI drivers so I gave up. 

I also want to learn Linux for my field as well. Doesn't hurt to be fluent in a couple OS's. 

So, where do I begin...

- I tried several movie players, from the default one, to mplayer, to VLC. All had choppiness. My card is an ATI Radeon HD 2600 XT. I already have the restricted video driver activated. Any ideas?

- I tried using sudo apt-get removeall and it removed a bunch of stuff it said was no longer being used. I will also check out the Synaptic Package Manager.

- The hotmail plugin that was linked to was actually the one I tried. I guess I'm not sure how to set it up to be honest. I currently have both plugins installed but do not know the URL for the mail host. 

- I'm downloading gnome-do as I type this.

- I'll try the force quit options suggested

Now I have more questions, mainly about the UI and color tweaks. I guess that'll be for another thread. Thanks!

---

### Post by rpeters83 on 2008-11-30
Wow. Gnome-do is perfect. Thanks!

---

### Post by rpeters83 on 2008-11-30
Another question! What is a good MP3 player? The default one has the visualization that I cant seem to turn off and it flickers (like the choppy video I mentioned earlier)

---

### Post by zmjjmz on 2008-11-30
> **rpeters83 said:**
> Another question! What is a good MP3 player? The default one has the visualization that I cant seem to turn off and it flickers (like the choppy video I mentioned earlier)

I like [Consonance](https://launchpad.net/%7Eloell/+archive/+files/consonance_0.3.0-1~ppa6_i386.deb).
And it's pretty easy to turn off the visualization in Rhythmbox. Just click on the "Visualization" button and it should go away.

TIP: Chances are you'll find a really good application but it's only available in source code form. What you should do is google "<Application name> ppa".
What you'll find is someone's PPA (Personal Package Archive) with a binary deb (just click and install) for it (most of the time). This will probably save a lot of work on your part.

---

### Post by Mr. Picklesworth on 2008-11-30
I like Banshee, which is in the repositories and in the [Banshee Team PPA]("https://launchpad.net/~banshee-team/+archive").
(I assume you've tried Rhythmbox?)
(PPAs are really cool; they add to your system's list of repositories in a tidy manner. Everything installed from them is kept completely up to date via the same central update manager).

Glad to hear that Gnome-Do works for you.

Unusual for MPlayer to be choppy :/
I remember my Radeon card had issues with video playback running Compiz, so it may be that. I'm not a Compiz person though, so I couldn't guess what may fix it :(
If the solution turns out to be disabling Compiz and you still want things to look pretty, check out [Metacity's compositor]("http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/"). (Metacity is Ubuntu / GNOME's default window manager, where Compiz is enabled automatically when it is supported). The option is currently hidden away, but it works and it is fast! (And I use it).

---

### Post by Sealbhach on 2008-11-30
> **rpeters83 said:**
> Wow. Gnome-do is perfect. Thanks!

Was just about to recommend it.

+1


Also Banshee is really nice.

.

---

### Post by bash on 2008-11-30
As for choppy/tearing movie playback on ATI card with the restricted driver:

You have to set the Video output to X11 in the preferences of you favourite player (for example in VLC). That fixed the choppy video playback for me. Sadly ATI has a thing for releasing bad and/or buggy video driver for Linux.

---

### Post by phrostbyte on 2008-11-30
I don't know if someone already said this, but for the last thing you can use the tool "rdesktop" to remote into any Windows server with terminal services enabled.

---

### Post by SunnyRabbiera on 2008-11-30
> **bash said:**
> As for choppy/tearing movie playback on ATI card with the restricted driver:

You have to set the Video output to X11 in the preferences of you favourite player (for example in VLC). That fixed the choppy video playback for me. Sadly ATI has a thing for releasing bad and/or buggy video driver for Linux.

those ATI cards have been nothing but trouble so no wonder he is having issues, hopefully in the future ATI will provide us with more support.

---

### Post by Daveski on 2008-11-30
> **phrostbyte said:**
> I don't know if someone already said this, but for the last thing you can use the tool "rdesktop" to remote into any Windows server with terminal services enabled.

It is also in the main menus under Applications, Internet, Terminal Server Client. If you want to remote INTO the Ubuntu machine - that is, remote control it from another machine, use VNC. The VNC server can be enabled under System, Preferences, Remote Desktop. The VNC viewer is a free download for most OSes and is in the Ubuntu repositories.

---

### Post by Mr. Picklesworth on 2008-11-30
> **bash said:**
> As for choppy/tearing movie playback on ATI card with the restricted driver:

You have to set the Video output to X11 in the preferences of you favourite player (for example in VLC). That fixed the choppy video playback for me. Sadly ATI has a thing for releasing bad and/or buggy video driver for Linux.

Ah, right! That jogged my memory. I recommend trying this with gstreamer first, since it is the system used by most integrated things in this distribution. For example, Totem (the default Movie Player) uses GStreamer, as do video converters, audio editors, etc...
Hit Alt-F2, enter "gstreamer-properties" and hit Run. In that program, head to the Video tab and try the different Default Output plugins to see if one of them works better for you.

Lots of programs, as bash mentions, also have that sort of stuff in their Preferences.

---

### Post by bash on 2008-12-01
> **Mr. Picklesworth said:**
> Ah, right! That jogged my memory. I recommend trying this with gstreamer first, since it is the system used by most integrated things in this distribution. For example, Totem (the default Movie Player) uses GStreamer, as do video converters, audio editors, etc...
Hit Alt-F2, enter "gstreamer-properties" and hit Run. In that program, head to the Video tab and try the different Default Output plugins to see if one of them works better for you.

Lots of programs, as bash mentions, also have that sort of stuff in their Preferences.

Cool, didn't know you could set that for Gstreamer globally. As I mostly use VLC or Mplayer for video playback I have to set it each time, as those aren't Gstreamer based. But this will save me some trouble in the future for Gstreamer applications.

---

### Post by rpeters83 on 2008-12-01
I actually tried MPlayer, messed with some settings and it's working flicker-free now. 

Only other problem is the menu and drop-down font's for Firefox/Thunderbird are different than the OS UI menus...

---

### Post by ubuntu27 on 2008-12-01
> **rpeters83 said:**
> I actually tried MPlayer, messed with some settings and it's working flicker-free now. 

Only other problem is the menu and drop-down font's for Firefox/Thunderbird are different than the OS UI menus...

Open Mozilla Firefox, and go to EDIT menu/Preferences/Content

Now change the fonts as the way you wish :)


To change the System fonts, just go to 
SYSTEMS menu/Preferences/Appereance

a new Windows will open-up.


Go to the FONTS tab.  

Now you can change the System Fonts to your liking. 
Try to match Firefox's font with the System one :)

---

### Post by forrestcupp on 2008-12-01
> **earthpigg said:**
> why convert you? if you are happy with and love vista, stick with it.

;)

+1 also.

There's no need to ditch Vista.

---

