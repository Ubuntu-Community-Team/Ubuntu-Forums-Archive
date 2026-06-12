---
title: "&quot;Normal&quot; Ubuntu vs Ubuntu Studio 10.10"
date: 2011-01-13
forum: Ubuntu Studio
---

### Post by jorgealfonso on 2011-01-13
Hello,

I would like to know what is the advantage of a **fresh install of Ubuntu Studio **nowadays (version 10.10) **vs a fresh install of "normal" Ubuntu** + install of the missing packages.

My understanding is that the main difference WAS the real-time-kernel, BUT NOW that this is gone from the standard install, so I don't see what's the point of installing Ubuntu Studio anymore.

Other key differences, to my understanding, are:
[LIST]
[*] Lighter window manager (but really, does this help that much in terms of performance??)
[*] Audio/video/etc packages pre-installed (but I could install them after, and all of them together installing ubuntustudio-audio, etc...)
[*] No un-necessary packages pre-installed. Not sure which ones... but if they are packages network-manager... come on, I will need these anyway and will end up installing them later!!
[*] Adjustments to the groups to provide access to firewire (ok, this is fine)
[/LIST]

... so... is that it?

I have had Ubuntu Studio on this computer for years now, since I got it, so I can't really tell the difference in terms of performance compared to the regular Ubuntu...

Though, I've installed the regular ubuntu on some friends' computers, and it looks nice, light, appealing, practical, simple. I think I would like to have it on my computer too. Would I have to pay a BIG performance price if I just make an incremental upgrade from "normal" ubuntu to Ubuntu studio? (ex: as described here ---> [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

Thanks for enlightening me :)

---

### Post by cchhrriiss121212 on 2011-01-14
You have covered the differences successfully up there, but I am pretty sure both versions use the same window manager.
Studio is a good introduction to using Linux audio, it has all the best packages and is reasonably stable. But as soon as you know what you want out of the OS it makes more sense to start from a generic base (like Ubuntu) and add what you like.
The advantages are ones of flexibility and choice, however so you won't see any difference in performance.

---

### Post by spencerownside on 2011-01-15
i am sorry if this is the wrong place for this post: i did several search strings but had no luck. 
i would like some help with doing a terminal based upgrade from standard ubuntu to ubuntu studio. 
i preface that i am newer to the terminal but have generally been getting better at navigation and basic commands- so not great, but not my first time. 
i'm using this upgrade info page: 

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

and it contains this code for upgrading: 
sudo aptitude update && sudo aptitude install ubuntustudio-desktop 
ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics 
ubuntustudio-video linux-rt

i have entered this code both with and without "brackets" but am getting the 'command not found' response. i have also tried different combinations of the code isolating specific parts of the studio package code, but haven't had luck there either. 

any help or assistance would be greatly appreciated. muchos gracias.

---

### Post by Totalchaos on 2011-01-16
> **jorgealfonso said:**
> Hello,

I would like to know what is the advantage of a **fresh install of Ubuntu Studio **nowadays (version 10.10) **vs a fresh install of "normal" Ubuntu** + install of the missing packages.

My understanding is that the main difference WAS the real-time-kernel, BUT NOW that this is gone from the standard install, so I don't see what's the point of installing Ubuntu Studio anymore.

Other key differences, to my understanding, are:
[LIST]
[*] Lighter window manager (but really, does this help that much in terms of performance??)
[*] Audio/video/etc packages pre-installed (but I could install them after, and all of them together installing ubuntustudio-audio, etc...)
[*] No un-necessary packages pre-installed. Not sure which ones... but if they are packages network-manager... come on, I will need these anyway and will end up installing them later!!
[*] Adjustments to the groups to provide access to firewire (ok, this is fine)
[/LIST]

... so... is that it?

I have had Ubuntu Studio on this computer for years now, since I got it, so I can't really tell the difference in terms of performance compared to the regular Ubuntu...

Though, I've installed the regular ubuntu on some friends' computers, and it looks nice, light, appealing, practical, simple. I think I would like to have it on my computer too. Would I have to pay a BIG performance price if I just make an incremental upgrade from "normal" ubuntu to Ubuntu studio? (ex: as described here ---> [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

Thanks for enlightening me :)


Well you saw the whole picture right. ubuntustudio without a realtime kernel is.... a normal ubuntu, just looking a little different. The adjustments of user "audio" and of limits.conf nowadays are created automatically with the installation of "Jack-audio-connection-kit" pack, so it's not necessary to be a linux guru to do this sort of conversion. 
So there is no "ubuntu"vs "ubuntu studio" ,but ubuntu IS ubuntu studio. If it's still sounds strange have in mind the following:
There is this thing called "ubuntu minimal". It's about 10MB in size and allows you to do the so called "net-install" of ubuntu system. So suppose you downloaded and installed it and you will get (nothing more than) the core system. The core system basically is the kernel and some set of core programs. when you start this core system instead of GUI, only a terminal will start. And here is the fun part. From this point with just one simple command you can get ubuntu, kubuntu, xubuntu, lubuntu, ubuntu studio, and even debian-like desktop environment. and this command basically is:
1. sudo apt-get install ubuntu-desktop (for ubuntu)
2. sudo apt-get install kubuntu-desktop (for kubuntu)
3. sudo apt-get install xubuntu-desktop (for xubuntu)
4. sudo apt-get install ubuntustudio-desktop (for ubuntu studio)
5. sudo apt-get install gnome-desktop-environment (for ubuntu debianish)
etc, etc, etc ;)
And this is a basic principal , not just for version 10.10
Consider this as an example of the capabilities not as tutorial. After all it's nice to know what you're doing

and most importantly: have fun :D

---

### Post by Totalchaos on 2011-01-16
> **spencerownside said:**
> i am sorry if this is the wrong place for this post: i did several search strings but had no luck. 
i would like some help with doing a terminal based upgrade from standard ubuntu to ubuntu studio. 
i preface that i am newer to the terminal but have generally been getting better at navigation and basic commands- so not great, but not my first time. 
i'm using this upgrade info page: 

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

and it contains this code for upgrading: 
sudo aptitude update && sudo aptitude install ubuntustudio-desktop 
ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics 
ubuntustudio-video linux-rt

i have entered this code both with and without "brackets" but am getting the 'command not found' response. i have also tried different combinations of the code isolating specific parts of the studio package code, but haven't had luck there either. 

any help or assistance would be greatly appreciated. muchos gracias.

the "linux-rt" pack doesn't exist in 10.10 this pack actually installs the realtime kernel but 10.10 doesn't have any. just try it without this part ;)

PS:i will make you a quick explanation of every part in this command line, because knowledge is power 
sudo - gives you a root privileges
aptitude - this is a text-based package manager similar to synaptic (you can successfully change this part with 'apt-get')
update - updates your software channels to current state 
&& - and (from C program language) 
install - install 
ubuntustudio-desktop - GUI of ubuntustudio system
ubuntustudio-audio - a collection of applications aimed at audio creation and editing
ubuntustudio-audio-plugins - A collection of LADSPA and DSSI plugins.
ubuntustudio-video - a collection of applications aimed at video creation and editing
ubuntustudio-graphics -  collection of applications aimed at 2D/3D creation and editing.
linux-rt - a metapackge that installs you the latest complete Realtime Linux kernel available.

hope that helps


.

---

### Post by grahammechanical on 2011-01-16
It is the concept that is different. Yes, anyone could install the missing packages into a standard Ubuntu desktop but would they know what packages were available?

Likewise a person could start off with Ubuntu Studio and un-install the programs they do not want and also install the office type programs they do want. 

I like the look of Ubuntu Studio. I like the minimal look and the quality of the desktop background.

I guess that a project like Ubuntu Studio would draw to it those people who were creative in a design sense and not just those who were creative in a functional sense. This kind of project might develop ideas that could be used in standard Ubuntu. In my opinion.

Regards.

---

### Post by cchhrriiss121212 on 2011-01-16
> any help or assistance would be greatly appreciated. muchos gracias.
Hi spencer,
There is no need for you to use the terminal if you do not want to. Open up synaptic package manager and press the reload button. Now search for whatever packages you want and click apply to install them.

---

### Post by mango42 on 2011-01-16
Much respect to **Totalchaos** for such a Lucid explanation of the fundamentals but, from a new user's POV I think **grahammechanical** gets right to the crux of the matter:-

> It is the concept that is different. Yes, anyone could install the missing packages into a standard Ubuntu desktop but would they know what packages were available?

This is why UbuntuStudio has its' very prominent place IMO, regardless of whether it has a special kernel or no; it's a showcase of what is available in Linux Audio for those who don't yet know their Hydrogen from their PureData, (let alone great packages like QTractor being left out!) ;-)

IMO, [this]("https://help.ubuntu.com/community/UbuntuStudioPreparation") is probably the best place to start for those who query before plunging.

---

### Post by spencerownside on 2011-01-18
thank you everyone for the help. i have upgraded all my pcs to studio. i think i am digging it, although its pretty new and still haven't gotten to really test the full potential yet. i am curious about the synaptic package manager section. 
it seems as though ALSA & JACK are 2 of the main things that are supposed to be included in Studio, but when i go through synaptics there are many things, including (as examples) ALSA & JACK features. 
How do i sift through the literally hundreds of items under synaptics and how do i determine which ones are more important than others?

---

### Post by Pablo_F on 2011-01-18
Hi, 

Yes, there are lots of software packages in the ubuntu repositories. Some of them are just libraries or utilities, including packages that install automatically as "dependencies" when you install a bigger package. 

There is another tool for installing software, called "software center". There you will see end-user applications. 

Oh wait, just read:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

You probably have all what you need to get going. The hard part is not installing packages but properly configure the system so you can use jack and friends without hassle. It is not rocket science but you need to invest some time on it.

Cheers! Pablo

---

### Post by Pablo_F on 2011-01-18
Hi again,

The terminal is useful to show information in plain text, this is, for forum help. *dpkg -l* lists the packages in your system. ii means "installed". If you filter the results trhough a pipe with grep you can see the alsa related packages and the jack related packages that you have installed. This is:

dpkg -l | grep alsa

dpkg -l | grep jack

Cheers! Pablo

---

### Post by juancho2374 on 2011-03-30
Hi...

Ok, so it is or it's not a good idea to install studio from regular ubuntu? I'm already updating the packages without the live kernel, but will it work as the original studio? what's the real difference?...

besides... when I tried to install everything via synaptic, it didn't let me instal the Usplash theme for ubuntu studio... what is it anyway?

I think I have to replace things on regular ubuntu with the studio ones... any thoughts on that? 

excuse me if I'm kind of a linux-idiot but I'm actually trying my best...

c ya:guitar:

---

### Post by Totalchaos on 2011-04-02
> **juancho2374 said:**
> Hi...

Ok, so it is or it's not a good idea to install studio from regular ubuntu? I'm already updating the packages without the live kernel, but will it work as the original studio? what's the real difference?...

this ideas are basically the same idea. You can directly install ubuntu studio, or tweak regular ubuntu by installing audio-video production software and there will be no difference considering performance. In every linux based OS, the Operating system itself is actually the "linux-image-2.6.xx", everything else is a programs, that you use on this OS. So the major difference between regular and studio is the difference between linux-generic and linux-realtime . The major idea behind RT kernel and RT priority is that when you execute a process with realtime priority (for example if you press a key on your midi-keyboard) your computer will decrease the priorities (or kind-a stops the execution) of all other processes until the process with realtime priority is been processed (you can say that for this few milliseconds your PC will work only for you to hear the sound as fast as possible after you press the key on the keyboard).

Here is some good ideas for ya. The first idea is to "downgrade" to 10.04. This version right now is solid stable, has a proper studio kernel , and long term support.
The second idea is to hold your breath and wait for the shiny new stuff from 11.04 

PS: "Usplash" is an obsolete program that was used for showing the ubuntu logo during system start-up. it was successfully replaced with "Plymouth"

:-({|= \\:D/

---

