---
title: "[newbies only please] What do you have to do in the terminal?"
date: 2010-02-28
forum: The Cafe
---

### Post by sandyd on 2010-02-28
Ive got some extra time on my hands for these two months, as im not working full time at this moment.

Im considering creating some applications, like the one in my signature, that can do stuff without making users go into the terminal (even though the app makes system calls to the terminal)

so, what stuff did you guys have to do in the terminal?
and yes, this is kind of a survey, as im obviously not going to create programs for everything.

---

### Post by _elgato on 2010-02-28
I usually have to add host on etc/host, I made a program in C last year that could ask for an IP and name and add it to the file, but I forgot how I did it. It was very handy, though.

---

### Post by sudoer541 on 2010-02-28
I try to avoid it every way possible. 
If ubuntu wants to compete with Apple and gain users, then the terminal should be completely optional.

---

### Post by alket on 2010-02-28
I'm not newbie, but I think that is really important to have a button in Nautilus with function to give root permissions on that location.

For example after Search button in nautilus to have a button with e key and when you click it the gksudo appears and asks for password when you hit OK you have root access in that folder and a text appears in toolbar that you are browsing this folder as root.

---

### Post by FuturePilot on 2010-02-28
> **babaroga said:**
> I'm not newbie, but I think that is really important to have a button in Nautilus with function to give root permissions on that location.

For example after Search button in nautilus to have a button with e key and when you click it the gksudo appears and asks for password when you hit OK you have root access in that folder and a text appears in toolbar that you are browsing this folder as root.

```
sudo apt-get install nautilus-gksu
```

---

### Post by alket on 2010-02-28
> **FuturePilot said:**
> ```
sudo apt-get install nautilus-gksu
```

Thank You, this should come pre-installed.

---

### Post by gn2 on 2010-02-28
If you could create a GUI front end for [get**_**iplayer]("http://linuxcentre.net/getiplayer") that would be really superb.

---

### Post by sudoer541 on 2010-02-28
you can create a GUI for fixing X server.

---

### Post by tjwoosta on 2010-02-28
How about a GUI for compiling software. Does this already exist?

You know, have it display readme files, have a queue so dependencies can be built first, have inputs for compile options.

---

### Post by sudoer541 on 2010-02-28
> **tjwoosta said:**
> How about a GUI for compiling software. Does this already exist?

You know, have it display readme files, have a queue so dependencies can be built first, have inputs for compile options.

I would love that.

---

### Post by Woolio1 on 2010-02-28
I do a lot of "Sudo apt-get install --reinstall bcmwl-kernel-source"'ing.

My installations break weekly. And I'm getting tired of it. Where's that Win7 OEM disk?

---

### Post by Hman242 on 2010-02-28
I mount disk image files, force reload PulseAudio, and update GRUB.

---

### Post by Jesus_Valdez on 2010-02-28
One thing that I do on the terminal everyday every time that I turn on my laptop is connect me to Internet using mobile broadband

> sudo ./itfchg /dev/sdb

Ah, and force to reload Alsa

---

### Post by WinterMadness on 2010-02-28
I've never installed Java with a gui. I wouldnt even know if there is one.

I think many newbies would have issues with that.

---

### Post by grief -l on 2010-03-01
I'm a new user and though I feel a sudden and uncontrollable warmth for you I unfortunately don't know enough about it to answer your question. I have had to use the terminal to try to get my 800 X 600 screen reolution back to 1024 X 768 only to have it mysteriously come back by itself. I also had to compile a wireless driver from a patched file (which, though it "worked", kept dropping it's connection) that I didn't need since an easier fix was to get a new, supported dongle. I've also had to use the console to get ALSA plugins for Audacity to work and to add repositories for Medibuntu.

Another thing I've had trouble with is installing something using the Package Manager, which also installs a plethora of dependencies. Deciding it's not what I want, I uninstall (again with Synaptic), but it only uninstalls the selected app and not the plethora of dependencies. Yes, I know there are Logs (read the first three words of this post), but it's a daunting task to find which one applies and it's useless if uninstalling a few days later after a few shutdowns.

If your skill-set includes coding driver support for hardware I think a full 90% of newbie problems with the console would be resolved. Thanks for what you're doing carlee; it's very much appreciated!

Gabe.

---

### Post by gn2 on 2010-03-01
> **Jesus_Valdez said:**
> One thing that I do on the terminal everyday every time that I turn on my laptop is connect me to Internet using mobile broadband

Ah, and force to reload Alsa

Right-click on a panel and select Add to Panel then select the first option in the list "Custom Application Launcher" click Add then give it a name and enter ```
sudo ./itfchg /dev/sdb
``` as the command, then save it.
**Edit:** You might have to select the type as Application in terminal.

You can now just click a button instead of using the terminal.

You can do the same thing for Alsa with the command ```
sudo /sbin/alsa force-reload
```
That one is type: Application.

---

### Post by tjwoosta on 2010-03-01
Wouldn't it be better to just make the commands autorun at startup?

---

### Post by alket on 2010-03-01
> **tjwoosta said:**
> Wouldn't it be better to just make the commands autorun at startup?

You can add them /etc/rc.local before exit 0

> sudo gedit /etc/rc.local

---

### Post by Perfect Storm on 2010-03-01
> **tjwoosta said:**
> How about a GUI for compiling software. Does this already exist?

You know, have it display readme files, have a queue so dependencies can be built first, have inputs for compile options.

If it needs cmake to compile you can use ccmake. It's not a frontend in the sense of a window pop up, but more a text based app.

Other than that in most cases it's really simple to compile something if it comes with a compile script of a sort. Just need to read the output.

---

### Post by LintonHanes on 2010-03-01
Carlee you're a darling!, (if you do 'everything' I tell you, lol)

I like your flash installer, I'd really love a conkey installer:
>that includes a bandwidth meter showing daily,weekly,monthly accruement
>that has 'top' themes (how do these people make these wonders?)
>asking you for particulars, like month-start? email-account? music-player?

also, have you seen the nautilus-script that converts to 320x240.mp4 for ipods? imho nautilus-scripts are the bomb!

---

### Post by gn2 on 2010-03-01
> **tjwoosta said:**
> Wouldn't it be better to just make the commands autorun at startup?

Depends on whether you want the option of it being done manually.
I use a launcher for the Alsa one on my 8.04 desktop PC because the sound doesn't work after suspend.

---

### Post by sandyd on 2010-03-01
> **LintonHanes said:**
> Carlee you're a darling!, (if you do 'everything' I tell you, lol)

I like your flash installer, I'd really love a conkey installer:
>that includes a bandwidth meter showing daily,weekly,monthly accruement
>that has 'top' themes (how do these people make these wonders?)
>asking you for particulars, like month-start? email-account? music-player?

also, have you seen the nautilus-script that converts to 320x240.mp4 for ipods? imho nautilus-scripts are the bomb!

conkys easy to install
```

sudo apt-get install conky

```
drop the attached file into the home folder and rename as .conkyrc.

run conky```
conky
```

---

### Post by t0p on 2010-03-01
It seems to me that nearly all the tasks brought up in this thread fall into one of two categories: they are either really specific tasks that only the user concerned will ever want to do; or they are jobs that can already be done with a GUI, but the user has only been told how to do it in the terminal.

One task that might well profit from a GUI is that mentioned by gn2: a GUI frontend for get_iplayer.  I don't mind using the terminal to use that particular program; but I can imagine that users less experienced in the ways of the command-line might be put off using get_iplayer because it involves the terminal.  Sometimes, a get_iplayer command can be quite long and unwieldy - for instance, it might be necessary to type in something like

```
get_iplayer --get 174 --mode flashnormal --flvstreamer ~/flvstreamer-1.8a_jackalope
```

and if you're not completely familiar with the program it can be difficult to know which of these options you're supposed to choose.  So yes, a GUI frontend for get_iplayer might be very welcome.

But I still think that most tasks can already be done through a GUI.

---

### Post by Bodsda on 2010-03-01
Sorry for being the first non-positive post to this thread but I honestly think that creating graphical front ends to CLI apps is a terrible idea. Graphical frontends completely destroy any need for the user to learn anything before using the app. This is not a good thing. 

Creating countless GUI frontends just means that eventually computer users will be so unaware of what they are doing and how it works that the skills will be lost. How many professional carpenters are there nowadays? I bet there is no where near the amount there was 50 years ago. Automated machines have taken over and now the skill of carpentry is dying out. 

I would be more inclined to suggest spending free time teaching people how to use these CLI tools instead of blinding them with a pointy clicky pretty wizzy frontend. 

Bodsda

---

### Post by gn2 on 2010-03-01
> **Bodsda said:**
> Sorry for being the first non-positive post to this thread but I honestly think that creating graphical front ends to CLI apps is a terrible idea. 

Fortunately this view is shared by very few people.

---

### Post by plurworldinc on 2010-03-01
As a newbie, i have found the terminal a little tricky, but when i do open up my terminal I am mainly trying to install new software or drivers buy copying and pasting from the forum. I have also found it's a great way to review the content of my folders when i want to do it in a nice relaxing place. go figure!!!

---

### Post by nmccrina on 2010-03-01
> **Bodsda said:**
> Sorry for being the first non-positive post to this thread but I honestly think that creating graphical front ends to CLI apps is a terrible idea. Graphical frontends completely destroy any need for the user to learn anything before using the app. This is not a good thing. 

Creating countless GUI frontends just means that eventually computer users will be so unaware of what they are doing and how it works that the skills will be lost. How many professional carpenters are there nowadays? I bet there is no where near the amount there was 50 years ago. Automated machines have taken over and now the skill of carpentry is dying out. 

I would be more inclined to suggest spending free time teaching people how to use these CLI tools instead of blinding them with a pointy clicky pretty wizzy frontend. 

Bodsda

I agree; the main strength of Linux is the command line. If you want an OS where everything can be done via the GUI then, quite frankly, Windows is probably better for you. The only advantages Linux would have would not have anything to do with the actual operating system: cost, and the ethicalness (?) of FOSS.

---

### Post by Jesus_Valdez on 2010-03-01
> **gn2 said:**
> Right-click on a panel and select Add to Panel then select the first option in the list "Custom Application Launcher" click Add then give it a name and enter ```
sudo ./itfchg /dev/sdb
``` as the command, then save it.
**Edit:** You might have to select the type as Application in terminal.

You can now just click a button instead of using the terminal.

You can do the same thing for Alsa with the command ```
sudo /sbin/alsa force-reload
```
That one is type: Application.
You are a God among men!

Seriously I have never tought of adding a launcher for those things, it just, never ocurred to me.

---

### Post by BenAshton24 on 2010-03-01
> **sudoer541 said:**
> you can create a GUI for fixing X server.

oh the irony :P

---

### Post by ubunterooster on 2010-03-01
Okay, not a newbie but I'm always helping my family of newbies. I like the speed of the terminal.
So far I've only NEEDED to use it for three things: 1, enabling ufw; 2, fixing a corrupted filesystem; 3, manual compilation

---

### Post by madhi19 on 2010-03-02
I install ffmpeg from source after every clean install and I use ffmpeg from the terminal to convert all sorts of media. I also run mediatomb from the terminal and that about it. We got GUI for so many things now that in a way you can use Ubuntu for a long time and not learn all that much about the terminal and Linux.

---

### Post by RabbitWho on 2010-03-02
Last few commands were all

"Unrolling tarballs" 
converting .flv to .ogg
checking core temperate 
pinging
ap get
restarting panel 

but some of those things already have gui equivalents and none of them are difficult 


> 
[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8901578#post8901578")                                  [I]Sorry for being the first  non-positive post to this thread but I honestly think that creating  graphical front ends to CLI apps is a terrible idea. Graphical frontends  completely destroy any need for the user to learn anything before using  the app. This is not a good thing. 

Creating countless GUI frontends just means that eventually computer  users will be so unaware of what they are doing and how it works that  the skills will be lost. How many professional carpenters are there  nowadays? I bet there is no where near the amount there was 50 years  ago. Automated machines have taken over and now the skill of carpentry  is dying out. 

I would be more inclined to suggest spending free time teaching people  how to use these CLI tools instead of blinding them with a pointy clicky  pretty wizzy frontend. blah blah blah self-rightious twaddle
Bodsda[/I]



My mother is a retired accountant with very bad eye sight who get's migraines if she spends too long on the computer and uses it for learning languages (Communicative spoken languages, not programming languages!). She does not need to know how a computer works she only needs it to work.

Get over yourself; a computer is a tool. People have different interests and skills, not everyone needs to understand everything they use or no one would have any time to actually do anything.

---

### Post by alket on 2010-03-02
> **nmccrina said:**
> I agree; the main strength of Linux is the command line. If you want an OS where everything can be done via the GUI then, quite frankly, Windows is probably better for you. The only advantages Linux would have would not have anything to do with the actual operating system: cost, and the ethicalness (?) of FOSS.

What is wrong to have more options like GUI , terminal is still there ?
Does End Users use cmd in windows ?

The question is very simple:
Newbies what do you use terminal for ?

So the basics can be ported to GUI.

---

### Post by Excedio on 2010-03-02
I'd like a simple GUI that can mount a new hard-drive if i've added one. I have a 2nd hard-drive that I leave unmounted just because I don't have the time to go Google searching for the commands to keep it mounted.
 
The good thing is, Nautilus in 9.10 recognizes the unmounted HDD still. When I click on it, it just asks me for a password.
 
Basically...a GUI to mount additional HDDs.

---

### Post by linuxcentre on 2010-03-02
> **t0p said:**
> ...So yes, a GUI frontend for get_iplayer might be very welcome.....

There is 'Web PVR Manager' which is the official get_iplayer GUI - it's web based though.

---

### Post by grief -l on 2010-03-02
> **Bodsda said:**
> Sorry for being the first non-positive post to this thread but I honestly think that creating graphical front ends to CLI apps is a terrible idea. Graphical frontends completely destroy any need for the user to learn anything before using the app. This is not a good thing. 

Creating countless GUI frontends just means that eventually computer users will be so unaware of what they are doing and how it works that the skills will be lost. How many professional carpenters are there nowadays? I bet there is no where near the amount there was 50 years ago. Automated machines have taken over and now the skill of carpentry is dying out. 

I would be more inclined to suggest spending free time teaching people how to use these CLI tools instead of blinding them with a pointy clicky pretty wizzy frontend. 

Bodsda

This is a prime example of what I call "TerminalTosterone", and more so for appearing in a thread like this. TerminalTosterone is rife on this forum and is probably the worst part of linux that noobs like myself have to deal with.

Gabe

---

### Post by RabbitWho on 2010-03-02
> **grief -l said:**
> This is a prime example of what I call "TerminalTosterone", and more so for appearing in a thread like this. TerminalTosterone is rife on this forum and is probably the worst part of linux that noobs like myself have to deal with.

Gabe

Yeah it's pure fanaticism, needing other people to have the same interests as you. It leads to church burning.

---

### Post by gn2 on 2010-03-02
> **linuxcentre said:**
> There is 'Web PVR Manager' which is the official get_iplayer GUI - it's web based though.

Thanks for that, last time I looked at the get_iplayer site, that wasn't available.
Will definitely be giving it a try. :)

---

### Post by Excedio on 2010-03-02
How about we get back on topic here...not gonna point any fingers. By the way...would still really love that GUI to mount additional HDDs. ;-)

---

### Post by sandyd on 2010-03-02
> **Excedio said:**
> How about we get back on topic here...not gonna point any fingers. By the way...would still really love that GUI to mount additional HDDs. ;-)[s]
are you mounting it externally, or internally.

[s]if internally, you **might** wanna tell me the filesystem[/s]psdm can do that... will get straight to adding that in..
if externally, well... im working on that right now. (automount feature through usbmount)[/s]
EDIT:
[http://brainstorm.ubuntu.com/idea/23638/](http://brainstorm.ubuntu.com/idea/23638/)

---

### Post by Excedio on 2010-03-02
> **carlee said:**
> [s]
are you mounting it externally, or internally.

[s]if internally, you **might** wanna tell me the filesystem[/s]psdm can do that... will get straight to adding that in..
if externally, well... im working on that right now. (automount feature through usbmount)[/s]
EDIT:
[http://brainstorm.ubuntu.com/idea/23638/](http://brainstorm.ubuntu.com/idea/23638/)

Awesome! Horace & Bertha (the names of my USB & 2nd HDD) thank you. :-D

---

