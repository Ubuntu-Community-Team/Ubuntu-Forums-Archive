---
title: "Howto: Use Compiz Fusion or xwinwrap to draw your desktop background"
date: 2007-10-15
forum: Tutorials
---

### Post by smartboyathome on 2007-10-15
[size="4"]**PLEASE NOTE: I AM NOT LIABLE TO ANY DAMAGES THIS GUIDE MAY CAUSE.**[/size]

This guide will show you how to set compiz and xwinwrap to draw your background (no script required for xwinwrap!). The advantages of Compiz is that you can use a different background on each desktop, and you won't have problems with conky or other apps, as Nautilus isn't drawing the desktop. The disadvantage of Compiz is that you won't be able to use your desktop like in Nautilus (as a folder), and the background drawing capabilities are very basic (it will shrink/grow a background to the size of the screen you are using). xwinwrap will allow you to draw movies as a background, and will supposedly (I haven't tried it!) run the quake3 demo as a background.

****NOTE!** This gets rid of your desktop icons. At the moment, there is no way to get both. There could be a way if the compiz fusion patch for nautilus was updated to the 2.24 (or upcoming 2.26) version of nautilus, and adapted for XWinWrap. I am not much of a programmer, though, so this is beyond my knowledge. Could make an interesting project if you wanted to try it though.

[SIZE="4"]**_Getting Started_**[/SIZE]
[INDENT]To get started, you first have to stop nautilus from drawing the background. To do this, use Alt-F2 to go into a terminal and type gconf-editor, then go to /apps/nautilus/preferences, find the entry titled show_desktop, and disable it to "false". You can also use this in a terminal to do the same thing:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```
Now, you are ready to run whatever window manager you want on your desktop. If compiz is started, we can go on to the next step.[/INDENT]

[SIZE="4"]**_Setting the background in Compiz_**[/SIZE]
[INDENT]To set the background, you will need CompizConfig Settings Manager. To install it, go into Synaptic, and search for compizconfig-settings-manager. After you install it, you should have a new entry in your preferences menu called Advanced Desktop Effects, as well as a new entry in Appearance > Visual Effects called "Custom" (if you are on Gutsy). Open up Advanced Desktop Effects, and find an entry called "Desktop Cube" (it should be near the top). Click on it, and then click on the Appearance tab. You should see a section called "Background Images", click the add button to add a background for each desktop. If you want to use a background on more than one desktop, you add it for each desktop you want it on. The order of the backgrounds is the order pf how it will be placed on the desktops. For example, if I have 4 desktops, the first background will be for the first desktop, the second background will be for the second desktop, etc. Add each background until all desktops have a background. Congrats, you are done![/INDENT]

[SIZE="4"]**_Setting the background using Xwinwrap:_**[/SIZE]
[INDENT]You can get xwinwrap from Trevino's repo [here]("http://3v1n0.tuxfamily.org/") or click [this link]("http://3v1n0.tuxfamily.org/pool/feisty/eyecandy/xwinwrap_0.1+cvs20060209_i386.deb") to download the package from the repo for Feisty (also works with Gutsy). 64 bit users can get an ISO from [this post]("http://ubuntuforums.org/showthread.php?p=1743805#post1743805"). Simply double click it in your favorite file manager and it will install. This howto will focus on the command line, but a GUI was written was written for it and is available [here]("http://forum.beryl-project.org/viewtopic.php?p=21057#p21057"). To start, open up a terminal and type this in to start a screensaver playing as your desktop background (you must have xscreensaver installed, or this will not work; it is available in the ubuntu repositories):
```
xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID
```
To start a movie as your desktop background (you must have mplayer installed to use this; it is available in the ubuntu repositories):
```
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg
```
To start the quake3 demo on the desktop (I have not tried this!), use:
```
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- q3demo -window-id WID
```
You have now used Xwinwrap on the desktop![/INDENT]

I hope you enjoyed my howto. :)

---

### Post by nikoPSK on 2007-11-05
Thanks alot!:)

---

### Post by smartboyathome on 2007-11-05
> **nikoPSK said:**
> Thanks alot!:)

You are welcome. :)

---

### Post by Khuezy on 2007-11-05
Could I add a video on my background using the "Background Image" in my Compiz? I'm on Gutsy. Or is it only limited to pictures.

---

### Post by smartboyathome on 2007-11-05
> **Khuezy said:**
> Could I add a video on my background using the "Background Image" in my Compiz? I'm on Gutsy. Or is it only limited to pictures.

Its only limited to pictures. :( But there is xwinwrap for videos. :)

---

### Post by Khuezy on 2007-11-05
IC, thanks

---

### Post by Khuezy on 2007-11-05
What is the size limit on the movie?

---

### Post by smartboyathome on 2007-11-05
> **Khuezy said:**
> What is the size limit on the movie?

The size of your screen (the movie is running at fullscreen).

---

### Post by Khuezy on 2007-11-05
OK, I just saved the file and ran it. I don't know if I successfully installed it, does it have a program under applications or systems?

---

### Post by Khuezy on 2007-11-05
Alright, I need help, I just downloaded a FLV file from youtube and renamed it movie.mpg. 

xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/khue/.mplayer/config
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing movie.mpg.
File not found: 'movie.mpg'
Failed to open movie.mpg.


Exiting... (End of file)
mplayer died, exit status 0

---

### Post by csizi23 on 2007-11-05
Hi guys.
I see this xwinwrap is only for 32bit architeckt , or not ?
If not any1 have a link ?
Thnx

---

### Post by smartboyathome on 2007-11-05
> **Khuezy said:**
> Alright, I need help, I just downloaded a FLV file from youtube and renamed it movie.mpg. 

xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/khue/.mplayer/config
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing movie.mpg.
File not found: 'movie.mpg'
Failed to open movie.mpg.


Exiting... (End of file)
mplayer died, exit status 0

First of all, I don't think FLVs will play, as that is a flash file. Instead, I would suggest downloading it using vixy,net (which converts the Youtube video to AVI, but it is still good enough for playing with mplayer :)).

> **csizi23 said:**
> Hi guys.
I see this xwinwrap is only for 32bit architeckt , or not ?
If not any1 have a link ?
Thnx

I think it is only for 32bit, at least that is what Trevino usually compiles in. You might have to compile it from source instead. [This post]("http://ubuntuforums.org/showpost.php?p=1743805&postcount=9") describes how to install xwinwrap on 64bit.

---

### Post by Khuezy on 2007-11-06
Do I download the AVI one or the MOV?

---

### Post by smartboyathome on 2007-11-06
AVI I know works with Mplayer, but I don't konw about MOVs.

---

### Post by Khuezy on 2007-11-06
WIll the movie start automatically or do I have to put in the code everytime?

---

### Post by Khuezy on 2007-11-06
I still get the same error, 
I could right click on the movie and script it to play in the background. How do I make it auto play when I start ubuntu?

---

### Post by smartboyathome on 2007-11-06
You would probably have to run that script in the beginning (right after GNOME comes up), after Compiz Fusion starts (so Compiz doesn't cover it). I can't remember how to do this, but I remember it being in a topic.

---

### Post by nikoPSK on 2007-11-06
> **smartboyathome said:**
> You are welcome. :)

too bad you have to disable show_desktop... Anyfix for the no icons? I saw a thread but it didn't work for me:(

[http://ubuntuforums.org/showthread.php?t=600909&highlight=cube+wallpapers]("http://ubuntuforums.org/showthread.php?t=600909&highlight=cube+wallpapers")

---

### Post by smartboyathome on 2007-11-06
> **nikoPSK said:**
> too bad you have to disable show_desktop... Anyfix for the no icons? I saw a thread but it didn't work for me:(

[http://ubuntuforums.org/showthread.php?t=600909&highlight=cube+wallpapers]("http://ubuntuforums.org/showthread.php?t=600909&highlight=cube+wallpapers")

Not currently, since Nautilus provides the icons (and it can't do it). If someone could patch it so that it could do screensavers as backgrounds, then it would be better, but I don't think it will be patched for movies (as that will put an extra dependancy on a movie player).

---

### Post by nikoPSK on 2007-11-06
> **smartboyathome said:**
> Not currently, since Nautilus provides the icons (and it can't do it). If someone could patch it so that it could do screensavers as backgrounds, then it would be better, but I don't think it will be patched for movies (as that will put an extra dependancy on a movie player).

well that guide does provide a patch...but it didn't seem to work for me. Since I already have 0.6.2. of compiz.

---

### Post by smartboyathome on 2007-11-06
> **nikoPSK said:**
> well that guide does provide a patch...but it didn't seem to work for me. Since I already have 0.6.2. of compiz.

But that patch only supports multiple wallpapers with Compiz, not XWinWrap. :(

---

### Post by kdarkentity on 2007-11-19
Ok i have wwinwrap installed but im not sure how to get it to play movies as a wallpaper.

---

### Post by smartboyathome on 2007-11-19
Do you also have Mplayer installed?

---

### Post by kyokan on 2007-11-22
Hey guys I've been trying to do exactly this for what seems like years now... Still no joy though.

At the moment I'm running Gutsy with Compiz fusion enabled, nautilus isn't drawing the desktop, it's just plain white at the moment. The problem is that no matter what code I copy and paste, the screensaver or video appears fullscreen OVER all my windows and panels etc, rather than on my desktop. There's a number of tutorials for this out there and I've followed them all to the letter but I always get the same results. Anyone else experienced this? Any help would be greatly appreciated...

---

### Post by smartboyathome on 2007-11-22
I have had this happen to me. It seems to be your particular graphics card which determines if xwinwrap works (on my lappy, which has a Intel GMA 945, it doesn't work).

---

### Post by mate84 on 2007-11-24
Hi!

If I use this how to (compiz, different wallpaper...) , my icons will be disappear!!? But what about my panels? They will be disappear too?

(Just one thing: I try this just one time and I don't know why, but when I added /usr/bin/avant-window-navigator to the sessions, then rebooted,   I had just the cube with different pictures and awn, which is not worked for me so I could not switch off the computer.)

---

### Post by smartboyathome on 2007-11-24
If you use Compiz, your panels will not dissapear (they are not part of Nautilus, which controls the desktop in GNOME).

As for your problem with AWN, I don't know why this happens since i don't use AWN (I am content with GNOME's panels). Maybe try asking around on AWN's forums? There should be someone else with the same problem.

---

### Post by pedro_cesar on 2007-11-25
How can I make it work on 64bit? I have 64bit Ubuntu Gutsy, running Compiz and Amarok. I want to set videos as wallpaper.

---

### Post by smartboyathome on 2007-11-25
You will have to compile xwinwrap manually because I don't think there is a debian package for 64 bit. Let me see if I can find the sources for you...

---

### Post by Nedtlele on 2007-11-26
This sounds fun, any luck with the 64 bit working yet?

---

### Post by smartboyathome on 2007-11-27
No, but I have uncovered that you can download the deb and then install it with dpkg -i --force-architecture filename.deb.

---

### Post by pedro_cesar on 2007-11-28
Jeje I'm back... and after a few changes to the original .deb I was able to compile it again and it "worked", I can run the videos, but they behave as "applications", they will be created on top of the desktop, panels and applications -although as any other application, when I select another one then it moves backwards the one I selected-, it even creates a window selector in the panel, I uploaded a [photo]("http://www.freewebs.com/oxbowc/Pantallazo.png") of this before I read the whole thread, now I see this is common, but I don't know if it is the video card, a friend has ALMOST the same video card than I do (I know the almost could make a difference, but what are the odds?), He has an nVidia GeForce 8600GTM and I an nVidia GeForce 8600GT, -it works fine on his-. I want to know if there is some work around for this.

If I use the command you said "dpkg -i --force-architecture filename.deb." the the video blinks.

---

### Post by smartboyathome on 2007-11-28
I can't help you any more than searching google right now since my video card recently broke. :( I will try to do more as soon as it is fixed!

---

### Post by nikoPSK on 2007-11-28
I hope you resolve your issue! (on board?)

---

### Post by pedro_cesar on 2007-11-28
Ok, what I did was that I set a different transparency level for the video and changed the background color from 0% to 10% white, so that the video isn't dark enough to darken my desktop icons, but light enough to be seen. I'm gonna keep these settings while we find how to fix it.

---

### Post by smartboyathome on 2007-11-28
> **pedro_cesar said:**
> Ok, what I did was that I set a different transparency level for the video and changed the background color from 0% to 10% white, so that the video isn't dark enough to darken my desktop icons, but light enough to be seen. I'm gonna keep these settings while we find how to fix it.

I do know that you can't keep your icons with xwinwrap, since nautilus doesn't really accept a root window as the desktop.

---

### Post by pedro_cesar on 2007-11-28
I have my icons in the Desktop and I can click on them (although I can't drag and drop onto nor from the desktop), they seem to be working fine. 
Isn't there any how to actually replace the wallpaper with a video?
How about Compiz Fusion?

I realized that the Video is also minimizing as any other window when I press CTRL+ALT+D.

Just in case, I'm starting the xwinwrap from a launcher in the desktop with this: ```
xwinwrap -ni -o 0.2 -fs -s -st -sp -b -nf -- mplayer -loop 0 -wid WID -quiet /home/pedro/Setups/XWinRap/Silverlight_Dusk_Widescreen_dreamscene.wmv
```

---

### Post by smartboyathome on 2007-11-28
There is a patch that was created which, while compiz was running, you could replace nautilus's wallpapers with Compiz's. But this doesn't do videos. For that, you would need a different patch which detects if xwinwrap is running and allows xwinwrap to replace the wallpaper with what it contains. It would have to be more complex, though, since xwinwrap does screensavers as well as movies. Overall, it can be done, but would be VERY hard.

---

### Post by pedro_cesar on 2007-11-28
JAJA, Good to know, I'll be off college in a couple of weeks, so I'll have plenty of free time, I'll be counting on this community to get it done (along with me of course), This'll be fun.

---

### Post by ZmooZa on 2007-12-04
there is a compiled 64bit version in the other post :)
[http://ubuntuforums.org/showthread.php?p=1743805#post1743805]("http://ubuntuforums.org/showthread.php?p=1743805#post1743805")

works perfectly :)

---

### Post by smartboyathome on 2007-12-04
Awesome, thanks for letting me know!

---

### Post by larsemil on 2007-12-05
larsemil@diil-ubuntu:~/downloads$ xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID
Error: Unsupported depth 0... exiting
/usr/lib/xscreensaver/glmatrix died, exit status 255

---

### Post by smartboyathome on 2007-12-05
Try running glmatrix on its own (USE THE TERMINAL IN CASE IT GETS BUGGY SO YOU CAN KILL IT), does that give you any error?

---

### Post by nagla on 2007-12-12
is there a way to add new screensavers to xscreensavers?
if there is is there any known snow ones, i want to prep my ubuntu for winter lol

thanks in andvance

---

### Post by tomauty on 2007-12-12
This is awesome, time to split up some mandolux.com backgrounds.

---

### Post by smartboyathome on 2007-12-14
> **nagla said:**
> is there a way to add new screensavers to xscreensavers?
if there is is there any known snow ones, i want to prep my ubuntu for winter lol

thanks in andvance

I think you can add screensavers to ~/.xscreensaver (not sure though, and there is very little documentation on this).

---

### Post by u-blunt-2 on 2008-01-27
Great how to.

I have some question concerning xwinwrap. I would like to have it running a video non-stop in the background. I am running the 64-bit version for 6.10 on gutsy 7.10 AMD64.

1st : How can I get the video to playback on all 4 desktops ? I only get in on one desktop, the one from which I ran the command in terminal. (sticky doesnt sem to work ?)

2nd : How can I make xwinwrap window not detected by compiz-fuzion when I scale all windows ? (wid ??)

3rd: Is there some way to keep the Desktop icons while having a video play in the background? (transparency = 1 ??)

The command I am using is :
```
xwinwrap -ni -o 0.8 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet -loop 0 videofile.mpg 
```

---

### Post by smartboyathome on 2008-01-29
1) I think you may have to do this on each desktop. I am not using this right now, since I am on windows, but I think it might work.
2) I think it may not be possible to do this unless you block all programs from displaying using the switcher.
3) There is no way unless someone creates a variation of the patch that is used to detect if compiz is running and use that background for metacity. I can't program much right now so I wouldn't be able to do this.

---

### Post by QkEterror on 2008-02-22
I have the same error as the one earlier:
```
Error: Unsupported depth 0... exiting
```
Is it possible this has got something to do with running AIGLX. I read somewhere that only xgl was supported. 

I hope this feature is made available through desktop environments like GNOME and KDE so we can also have icons on top of it. It's the only Vista eyecandy linux doesn't have.

---

### Post by mordox on 2008-03-11
on running with command : 

xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -root

i see the screensaver only at the edges where the gnome-panel is.. in the middle i see a black box. how can this be fixed.

:confused:

---

### Post by mordox on 2008-03-11
also running xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID makes it fill up the whole space but this time nothing can come over it ! and only 1 desktop is covered

---

### Post by mordox on 2008-03-11
changing -a to -b doesn't help

---

### Post by smartboyathome on 2008-03-11
What graphics card do you have? This sounds like a driver error.

---

### Post by mazz0 on 2008-05-20
Could anyone tell me what this error means when I try to enable xwinwrap?

```
mazz0@mazz0-desktop:~/Desktop$ xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID
Error: Unsupported depth 0... exiting
/usr/lib/xscreensaver/glmatrix died, exit status 255

```

---

### Post by smartboyathome on 2008-05-20
looks like your graphics card doesn't support it. What graphics card is it?

---

### Post by MaindotC on 2008-06-13
Is there some way to use VLC instead of mplayer?  I tried replacing mplayer (in the terminal command of your instructions) w/ vlc and it didn't work :(

---

### Post by smartboyathome on 2008-06-13
I don't think so unless you can get vlc to be fullscreen from the command line, with nothing else up. That is where the main problem comes in.

---

### Post by mazz0 on 2008-07-13
Sorry for the late reply - it's a Radeon X800.  Might be the pro version, can't remember now. Is there a Linux equivolent of Device Manager I could use to find out?

---

### Post by smartboyathome on 2008-07-13
Via [this thread]("http://ubuntuforums.org/showthread.php?t=764005"), it says that ATI drivers aren't working in Hardy, won't be til gutsy, so looks like you are out of luck until Intrepid unless you want to run compiz with SKIP_CHECKS=yes, which is dangerous since the ATI cards are blacklisted for a reason.

---

### Post by howlerbr on 2008-07-25
Hi,

I need some help:

1) I was able to play mplayer in my desktop background. I'm using -loop 0 to loop forever but every time the movie finishes and returns to the begining my screen flashes. For example if I'm using  firefox, when mplayer reaches the end of the movie, mplayer hides my current firefox window (or any other window that has the focus) to give focus to mplayer and then I can see my desktop background. After the movie restarts the focus is returned to firefox window. This is really annoying, I have downloaded some movies from dreamscene and every 3-4 minutes this happens... do you know how can I fix it?

2) I could also run some screensavers (like ripples) in the desktop background but those ones based in opengl (like glmatrix, glgears and others) they also run but in front of all screens (even using -b option) and my screen keeps flashing. Do I need anything special here?

I have a Intel based video card.


Thanks for your help!

---

### Post by smartboyathome on 2008-07-25
1) I don't, since I am not big into Mplayer and use this mainly for screensavers. I would suggest you try reading the man page and seeing if that helps you. Sorry I couldn't help more. :(

2) This is a graphics card related issue, Intel doesn't impliment GL very well, and this also happens when you play videos using GL instead of Xvideo. Makes me mad, really, and I am pretty sure as soon as the open ATI drivers are up to spec with the Nvidia ones (my current video card), then I will switch, and I would already advise you try to get future computers with ATI instead of Intel. :(

---

### Post by scrawl on 2008-08-08
Is there any possibility to get the nautilus icons on the desktop? It seems like  /apps/nautilus/preferences/show_desktop false  does not only hide the background but also hides the icons.
Thanks

---

### Post by smartboyathome on 2008-08-08
There is not. xwinwrap replaces the desktop, and doesn't allow icons to show. :(

---

### Post by Techrocket9 on 2008-08-11
I can't test this, but couldn't you (if you have an extremely fast CPU) create an animated bitmap and set it as the desktop background? It works in XP. (Though my CPU can't handle it and I get .3 FPS)

---

### Post by smartboyathome on 2008-08-11
> **Techrocket9 said:**
> I can't test this, but couldn't you (if you have an extremely fast CPU) create an animated bitmap and set it as the desktop background? It works in XP. (Though my CPU can't handle it and I get .3 FPS)

I don't think so. From what I understand, Internet Explorer renders the wallpaper, so it can render any picture you can view in IE as the background. Nautilus is a file browser, though, and the images it can use as a background are limited. :(

---

### Post by laceration on 2008-08-27
Interestinly I found this in
```
man mplayer
```

> -rootwin     
Play movie in the root window (desktop background). Desktop background images may cover the movie window, though. Only works with the x11, xv, xmga, xvidix, quartz, macosx and directx video output drivers.

so if you 
```
mplayer -rootwin somemovie
```
it will play the movie in the desktop bg??

I tried it with both the nautilus show desktop enabled and disabled. I heard the audio but didn't see anything.  I then tried with a transparent png for the bg and got the same result.  I assumed I had X11.  I don't know what is meant by "video output driver".  Is that the video driver or the windowing system or...?  Got nothing from Wikipedia and [www.google.com?q=define:video output driver](www.google.com?q=define:video output driver).

Thanks for this post!

---

### Post by twister86 on 2008-08-30
hey guys ..I installed xwinwrap ..when i run the code :
```
xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID
```

I get this error :
```

Error: Unsupported depth 0... exiting
/usr/lib/xscreensaver/glmatrix died, exit status 255

```

This are the information about my system :
 
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon IGP 330M/340M/350M
 Driver in use:         radeon
 Rendering method:      AIGLX

please help !!

---

### Post by smartboyathome on 2008-08-30
I'm afraid the problem lies in the graphics card. It doesn't play nice with the screensaver. to show this, try runing glmatrix by itself (remember to control+c after it starts to get rid of it). It should give you the same problem.

---

### Post by twister86 on 2008-08-31
I tried to run the glmatrix by itself , and it works just fine !!

---

### Post by smartboyathome on 2008-08-31
I don't know what the issue is then. Sorry. :(

---

### Post by twister86 on 2008-09-01
Thnx for trying to help smartboy ;)..Isn't there any program thats do the same job for xwinwrap...I just wanna put some animated picture or screensaver on the background ...

---

### Post by smartboyathome on 2008-09-01
Not currently, XWinWrap is the only one right now. Only other option is Enlightenment DR17, which uses its own format (not animated pictures or screensavers) in order to animate wallpapers. :(

---

### Post by shantzg001 on 2008-09-03
I found a few short comings with xwinwrap and also wanted a cpl of new features, so I have restarted its development here: [http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap)
Check it out and let me know ur comments and feature requests.

---

### Post by smartboyathome on 2008-09-03
> **shantzg001 said:**
> I found a few short comings with xwinwrap and also wanted a cpl of new features, so I have restarted its development here: [http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap)
Check it out and let me know ur comments and feature requests.

Cool, I will definately check it out when I get a chance. Glad someone took up development!

---

### Post by ace214 on 2008-09-05
I can get this to work with certain screen savers like fiberlamp and galaxy but not glmatrix and many others. Any ideas?

---

### Post by smartboyathome on 2008-09-05
Only thing I can think of is that some screensavers use OpenGL, while others don't, and this has problems with the OpenGL ones.

---

### Post by ace214 on 2008-09-05
> **smartboyathome said:**
> Only thing I can think of is that some screensavers use OpenGL, while others don't, and this has problems with the OpenGL ones.
Yeah, I installed xserver-xgl, restarted X, and tried it again and they work, but it completely swallows my CPU, and slows things down noticeably even when I'm not running xwinwrap.

So, this is a problem with the mesa driver or xwinwrap working with the other??

---

### Post by smartboyathome on 2008-09-05
> **ace214 said:**
> Yeah, I installed xserver-xgl, restarted X, and tried it again and they work, but it completely swallows my CPU, and slows things down noticeably even when I'm not running xwinwrap.

So, this is a problem with the mesa driver or xwinwrap working with the other??

The problem is with the driver. Some graphics cards, like older Intel cards, can have problems with OpenGL, since they don't really have a cache built in, which makes them slow and buggy. Other drivers rely on the CPU to draw the stuff, instead of the GPU. I think yours does the latter, though.

---

### Post by iceshare on 2009-01-12
hi thank u very much for the help i got a falling matrix desktop running now:D 

but i just got 2 questions.

1. how do i stop it?
2. i don't got any icons on the desktop anymore:( how do i get them back and still having the moving desktop?

please help me

---

### Post by iceshare on 2009-01-12
hi thank u very much for the help i got a falling matrix desktop running now:D 

but i just got 2 questions.

1. how do i stop it?
2. i don't got any icons on the desktop anymore:( how do i get them back and still having the moving desktop?

please help me :)

---

### Post by smartboyathome on 2009-01-12
> **iceshare said:**
> 1. how do i stop it?

Use this in a terminal or via alt+f2:
```
killall xwinwrap
```

> **iceshare said:**
> 2. i don't got any icons on the desktop anymore:( how do i get them back and still having the moving desktop?

You can't have both. It is either one or the other. Personally, I don't use desktop icons (I always felt they were an encumbrance, since they were under all windows. I can just as easily open a folder in the file manager and use that instead, with it being more organized). I will post this in the beginning since everyone asks it.

---

### Post by Omen_20 on 2009-08-04
Funny, I was just playing with turning off the desktop today, then I found this. Anyways mplayer plays my videos fine, my desktop is turned off, but when I go to play it with xwinwrap my wallpaper is still present. I went into appearence and didnt find an option to just turn off the Background image, had to have at least a color, so I went back to gconf-editor and found under Nautilus preferences and found that background-set is turned off, I presume by turning off the desktop all together.

So my problem is that my wallpaper will change color kind of, but I cant see the video. It's as if the wallpaper is blocking it. The panels stay normal which are set to transparent so that tells me the desktop is trying to play the video, and I can hear it so I know it is, but the wallpaper is just raining on my parade.

Do you know of any solutions to this?

[IMG]http://i9.photobucket.com/albums/a62/Omen_20/Screenshot-3.png[/IMG]

---

### Post by FireDemonSiC on 2010-08-22
Very, very cool.

However, following the istructions exactly as you stated, XWinWrap will draw the animation over top of EVERYTHING (As I am typing this, I have the matrix raining down in front of FireFox).

Is this the way of the beast, or is it supposed to draw to the desktop only and I did something wrong?

---

### Post by FireDemonSiC on 2010-08-22
> **FireDemonSiC said:**
> Very, very cool.

However, following the istructions exactly as you stated, XWinWrap will draw the animation over top of EVERYTHING (As I am typing this, I have the matrix raining down in front of FireFox).

Is this the way of the beast, or is it supposed to draw to the desktop only and I did something wrong?

Nevermind.  Figured it out.

---

### Post by AdemoS on 2010-10-25
Is it possible run a fullscreen browser (with web page) instead of running a screensaver as the wallpaper?

---

### Post by creen on 2010-11-27
I would like to achieve the same as [AdemoS]("http://ubuntuforums.org/member.php?u=363166"). I have xwinwrap up and running with screensavers and movies, but I would like to view a live webpage as my desktop wallpaper.
When I try to run xwinwrap with google-chrome or firefox as program arguments the browser opens in a separate (normal) window. I suspect this might be due to the mechanism that all browser windows of a particular type is only run as a single process.

Please help if anyone knows how to view a **live** webpage as the wallpaper (or screensaver), thanks!

---

### Post by HX_unbanned on 2011-01-15
> **creen said:**
> I would like to achieve the same as [AdemoS]("http://ubuntuforums.org/member.php?u=363166"). I have xwinwrap up and running with screensavers and movies, but I would like to view a live webpage as my desktop wallpaper.
When I try to run xwinwrap with google-chrome or firefox as program arguments the browser opens in a separate (normal) window. I suspect this might be due to the mechanism that all browser windows of a particular type is only run as a single process.

Please help if anyone knows how to view a **live** webpage as the wallpaper (or screensaver), thanks!

Maybe. Icons and desktop background ( the image ) imho is draw in same process. If it would be tweaked to be split or enabled process resource intrusion and sharing in process scope, we would be able to keep all icons and animate desktop simultaneity ..

Live Wepages is Windows are called "Active Desktop". This is part of Samba functionality. I rumoured, it will come soon, so just wait. You will get it ;)

---

### Post by klikevil on 2011-06-21
Sorry for the necro bump....  

```

xwinwrap -g 1279x1024+0+0 -ni -d x-nautilus-desktop -ov -s -st -sp -nf -b -debug -o 0.9 -- /usr/lib/xscreensaver/fiberlamp -window-id WID # Lost my desktop icons, but I have an animated fiber lamp as my background now!

```

You don't have to disable your icons to do that one, but you won't be able to see them, at least you'll be able to click though.

---

### Post by ellaivarios on 2011-07-04
Who uses icons anyway man?? I have not used desktop icons ever in my entire life. Desktop icons are just another type of shortcut dude. For the love of god.. Seriously who cares about having clutter of shortcuts, instead of a nice image? Put all your shortcuts on the panel.

---

### Post by |Anthony| on 2012-01-07
The only time i us an icon is for mounts... like when a usb is plugged in or a network share.
I wrote a frontend for xwinwrap called VDesk - Visual Desktop. [You can get it for free at gnome-look]("http://gnome-look.org/content/show.php/VDesk+-+Visual+Desktop?content=141678"). It gives you an easy way to configure your animated wallpaper and i still have use of my desktop icons (if needed).

As far as putting a browser in xwinwrap... you can put any program that accepts WID assignment inside an xwinwrap window (as far as i know). MPlayer and VLC accept WID assignments so that you can use them as media players in your browser or some other app. I'm not sure if any web browsers will be coded that way.

---

