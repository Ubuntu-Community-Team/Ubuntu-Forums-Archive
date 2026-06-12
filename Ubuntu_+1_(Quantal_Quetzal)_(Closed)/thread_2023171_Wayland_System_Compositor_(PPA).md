---
title: "Wayland System Compositor (PPA)"
date: 2012-07-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by lucazade on 2012-07-12
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor](https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor)


> A change I'd like to make for 12.10 is to use a compositor to control video from boot to shutdown.

This gives us the following benefits:
- We can have smooth transitions from the splash screen to the greeter to the session and back again
- We don't use VT switching anymore which has been shown to be problematic
- We use one consistent monitor layout for all stages of the boot
- We can use the greeter as the lock screen (couldn't get it to work this cycle for the above reasons)
- We can ensure that you can never accidentally switch to a locked session
- We can show the greeter while the session loads

The technology used will probably be Wayland, and in some ways this change is to implement the Wayland Tech Preview that was proposed for Precise [1].

Note that not all video drivers will support this, and we will continue to support the current system for those that do not support it (primarily the nvidia driver).



It the blueprint there are the instructions to try via PPA... anyone tried?

---

### Post by cecilpierce on 2012-07-12
I will see if it works on mine, but it probably will give me a headache because of nVidia card.
 :(

---

### Post by dino99 on 2012-07-12
i will wait for xwayland first.

---

### Post by jbicha on 2012-07-12
It ***is*** x on wayland.

Don't try setting this up unless you like bleeding edge and know how to get things back to normal afterwards. It didn't really work right on my computer and I have Intel graphics which are supposed to be easier.

---

### Post by cecilpierce on 2012-07-12
I spent most of the day trying to get it right, tried nouveau driver and nvidia-current both worked inside of X but it keeps complaining about 'XDG_RUNTIME_DIR' so I quit for now.

---

### Post by EgoGratis on 2012-07-13
I have one question:

Will user be able to switch to VT if Ubuntu for whatever reason would not load as reliable as it can be done now? Would Ctrl + Alt + F1 still work reliable if booting would fail? 

Thanks.

---

### Post by cecilpierce on 2012-07-13
I was able to get everything back to boot as before by editing or committing out type=weston in /etc/lightdm/lightdm.conf

[SeatDefaults]
#type=weston
autologin-guest=false
autologin-user=cecil
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu

fun to play with though !
greeter-session=unity-greeter

All I got was sqwiggley lines when starting weston in a terminal outside X but it worked inside X in a terminal, its does not like nvidia driver I guess :(

---

### Post by EgoGratis on 2012-07-13
OK i tried the PPA on hardware where nouveau works quite good with Xorg and did everything suggested and after restarting lightdm or rebooting the PC the result is frozen screen showing a lot of artifacts of different color. 

CTRL + ALT + F1 does not work! I solved the issue and i use Xorg again but i hope user will be able to use CTRL + ALT + F1 in the future too just like it could in the past when GUI session is not loaded successfully.

One question if it would work i would get Weston without Xorg or Xorg on Weston? I guess Xorg on Weston otherwise not a lot of programs or Unity would work? 

I hope in future:
-CTRL + ALT + F1 will work when Weston/graphic driver fails in the future.
-Weston is beginning of more robust  graphic driver/display server stack for Linux users.

I guess the transition will be rough with a lot of problems and breakage but in the end i hope Linux will have better graphic driver/display server stack than any other platform.

But it will be rough transition i guess and i don't know when was the last time booting Linux distribution froze my  PC and i could not do anything about it (no CTRL + ALT + F1)!

---

### Post by cecilpierce on 2012-07-13
@EgoGratis

I have nvidia 320.??? in here and I also tried it with nouveau, same problem you had locked up messed up screen but I was able to do Ctrl+Alt+2-6 and just tried it again and got error msg about something, cant remember but when I hit enter in terminal 1 I got login prompt, then changed lightdm.conf, sudo start lightdm, and back in X...I know its a mess  :confused:

---

### Post by EgoGratis on 2012-07-13
> same problem you had locked up messed up screen but I was able to do Ctrl+Alt+2-6

Interesting I could only reboot nothing else worked but if you where able to use VTs then i guess this will work too and we just have to wait a bit and then it will probably work a lot better. If i rememberer correctly first phase is to use Weston and to run Xorg on top of it and yes right now the result is frozen screen but i bet this will change soon but at least we have something! 8-)

---

### Post by cecilpierce on 2012-07-13
Have you seen nerdopolis's wayland live cd ?

[http://ubuntuforums.org/showthread.php?t=1906762&highlight=wayland](http://ubuntuforums.org/showthread.php?t=1906762&highlight=wayland)

---

### Post by EgoGratis on 2012-07-13
I was thinking about this new Wayland/Weston System Compositor and how to introduce it to the Ubuntu users and i don't know what the plans are but i think Ubuntu 12.10 should have the ability to test it and not to be forced upon the users by default.

User should find simple GUI application in the Dash called for example Weston or System Compositor and by running it application would:

-Check if binary driver is installed and if yes then inform the user testing Weston is not an option with binary driver installed.
-Enable Weston for only one reboot or persistence. If testing for only one boot would be enabled "type=weston" setting would be applied only for one boot procedure and if user would get failed boot it would just press the reset button on PC and that is it. User could enable/disable Weston persistence easily too or maybe better option would be to manually  enable persistence in configuration file an option for more advanced users.

I think in this way the result would be:
-Users that are not exposed to breakage first implementation will most surely bring and a lot of useful feedback as result but not from angry but interested users of Ubuntu distribution.
[LEFT]-Developers that can loosen up and make more brave attempts to bring as much of the Wayland implementation in Ubuntu 12.10 as they possibly can and with PPA mentioned in GUI have in next development release majority of Ubuntu users/developers one click away from latest Wayland/Weston efforts on Ubuntu and generally speaking probably the need for custom Wayland/Weston distribution would be much lowered too.
[/LEFT]

---

### Post by cecilpierce on 2012-07-13
That would all be nice but not too many people are interested in wayland yet, hope it picks up,
heres a shot of it inside X, cant get it to work right from term,

---

### Post by lucazade on 2012-07-14
it's time to try it on my i7 with integrated intel.. I still have to install quantal. :)

---

### Post by cecilpierce on 2012-07-14
> **lucazade said:**
> it's time to try it on my i7 with integrated intel.. I still have to install quantal. :)

I just put a QQ on here, for experements  ):P

---

### Post by dino99 on 2012-07-14
better gtk3 coming (ricotz/testing)

#define GDK_WINDOWING_WAYLAND"
-  WAYLAND_PACKAGES="wayland-client xkbcommon "
+  WAYLAND_PACKAGES="wayland-client xkbcommon wayland-cursor"
   if test "x$enable_wayland_cairo_gl" == "xyes"; then
     WAYLAND_PACKAGES="$WAYLAND_PACKAGES wayland-egl egl"
   fi

---

### Post by lucazade on 2012-07-14
> **lucazade said:**
> it's time to try it on my i7 with integrated intel.. I still have to install quantal. :)

bad experience.. crashes and segafults here and there.. hope it will improve soon :)

---

### Post by ventrical on 2012-07-14
Borking up my system with that ppa gave me an opportunity to use midnight commander and re-edit lightdm.conf .. but that didn't matter because I used GDM and it is all back to normal  for now! :)

---

### Post by madjr on 2012-07-14
> **EgoGratis said:**
> I was thinking about this new Wayland/Weston System Compositor and how to introduce it to the Ubuntu users and i don't know what the plans are but i think Ubuntu 12.10 should have the ability to test it and not to be forced upon the users by default.

User should find simple GUI application in the Dash called for example Weston or System Compositor and by running it application would:

-Check if binary driver is installed and if yes then inform the user testing Weston is not an option with binary driver installed.
-Enable Weston for only one reboot or persistence. If testing for only one boot would be enabled "type=weston" setting would be applied only for one boot procedure and if user would get failed boot it would just press the reset button on PC and that is it. User could enable/disable Weston persistence easily too or maybe better option would be to manually  enable persistence in configuration file an option for more advanced users.

I think in this way the result would be:
-Users that are not exposed to breakage first implementation will most surely bring and a lot of useful feedback as result but not from angry but interested users of Ubuntu distribution.
[LEFT]-Developers that can loosen up and make more brave attempts to bring as much of the Wayland implementation in Ubuntu 12.10 as they possibly can and with PPA mentioned in GUI have in next development release majority of Ubuntu users/developers one click away from latest Wayland/Weston efforts on Ubuntu and generally speaking probably the need for custom Wayland/Weston distribution would be much lowered too.
[/LEFT]

i believe some of that stuff is planned. Hopefully will be done right.

---

### Post by cecilpierce on 2012-07-17
> **ventrical said:**
> Borking up my system with that ppa gave me an opportunity to use midnight commander and re-edit lightdm.conf .. but that didn't matter because I used GDM and it is all back to normal  for now! :)

MC is a life saver for me   :)

I guess no one here is having any luck with this,
the more I try the worse it gets.
Funny, when I run it in a terminal it says version .95 and the ppa says .89   :confused:

---

### Post by ventrical on 2012-07-18
> **cecilpierce said:**
> MC is a life saver for me   :)

I guess no one here is having any luck with this,
the more I try the worse it gets.
Funny, when I run it in a terminal it says version .95 and the ppa says .89   :confused:

  I am not giving up on Wayland just yet. My most recent attempt was on an older machine with an older nvidia adapter.  I thought I would try on some oolder machines because my more current machines are busy. I'll be getting to those and Wayland soon.

However, sorry for being offtopic, MC has the right stuff in a tight spot!! It is one of the few stand alones from terminal that makes ubuntu a very impressive program to work with.

---

### Post by lehjr on 2012-07-25
Anyone manage to try this successfully yet?

---

### Post by cecilpierce on 2012-07-26
> **lehjr said:**
> Anyone manage to try this successfully yet?

Not me

:(

---

### Post by lehjr on 2012-07-26
Looks like they only officially released 0.95 a day or so ago, at least from what I could make out in the mailing list chatter. And skimming through some of that, I'm still puzzled by the announcement back in February about a 1.0 release being soon. I would have thought that an announcement like that would mean at that point they were at a bug fixing stage, not still ironing out the API and adding features. :rolleyes:

Still though, it looks like Wayland **might** somehow make it into the Quantal beta:
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor](https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor)

---

### Post by madjr on 2012-07-26
> **lehjr said:**
> Looks like they only officially released 0.95 a day or so ago, at least from what I could make out in the mailing list chatter. And skimming through some of that, I'm still puzzled by the announcement back in February about a 1.0 release being soon. I would have thought that an announcement like that would mean at that point they were at a bug fixing stage, not still ironing out the API and adding features. :rolleyes:

Still though, it looks like Wayland **might** somehow make it into the Quantal beta:
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor](https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor)


maybe the delay could be because they are now discussing how to proceed with the binary blobs situation:

[http://www.phoronix.com/scan.php?page=news_item&px=MTE0NjI](http://www.phoronix.com/scan.php?page=news_item&px=MTE0NjI)


I don't think wayland should be rushed. They just need not to screw up and do things right. So if it takes a little longer am ok with that.

---

### Post by lehjr on 2012-07-26
> **madjr said:**
> maybe the delay could be because they are now discussing how to proceed with the binary blobs situation:

[http://www.phoronix.com/scan.php?page=news_item&px=MTE0NjI](http://www.phoronix.com/scan.php?page=news_item&px=MTE0NjI)


I don't think wayland should be rushed. They just need not to screw up and do things right. So if it takes a little longer am ok with that.

I don't think it should be rushed either, I'm just saying it seems odd to have a "coming soon" announcement for something that's still at this stage 5 months later. If you look at the mailing list chatter over the last few days, some of the stuff in there is pretty odd to see at this stage, like patches to add copy and paste functionality, discussions on how to get fullscreen to work, proposing API changes, things like that. As far as having it in the first Quantal beta, I don't see it since it's only about 6 weeks away, but maybe.

---

### Post by madjr on 2012-07-26
> **lehjr said:**
> I don't think it should be rushed either, I'm just saying it seems odd to have a "coming soon" announcement for something that's still at this stage 5 months later. If you look at the mailing list chatter over the last few days, some of the stuff in there is pretty odd to see at this stage, like patches to add copy and paste functionality, discussions on how to get fullscreen to work, proposing API changes, things like that. As far as having it in the first Quantal beta, I don't see it since it's only about 6 weeks away, but maybe.

well a 1.0 release is a pretty big step.

I hope it feels like 1.0 release and not like an alpha (i.e. like kde4.0's first release which was not even very stable :P).

---

### Post by cecilpierce on 2012-07-26
Maybe this is why Im having trouble with mine, think I'll try nouveau 
:P

---

### Post by lehjr on 2012-07-27
My results following those instructions leave me with the low graphics mode or w/e it's called (essentially trying to fall back on the very same drivers the instructions tell us to remove). I'm guessing that maybe the system tries to fall back on X if weston fails, but noting that I see in the weston log really jumps out and says that.

From what I can tell having looked elsewhere the PPA page is missing information, specifically about **weston.ini** and **$XDG_RUNTIME_DIR**. Creating the weston.ini file is pretty simple once you find the information (which I need to find again). The second issue is **$XDG_RUNTIME_DIR**, something that isn't so easy to solve:    [https://blueprints.launchpad.net/ubuntu/+spec/foundations-q-xdg-runtime-dir](https://blueprints.launchpad.net/ubuntu/+spec/foundations-q-xdg-runtime-dir)

---

### Post by lehjr on 2012-07-28
> **lehjr said:**
> My results following those instructions leave me with the low graphics mode or w/e it's called (essentially trying to fall back on the very same drivers the instructions tell us to remove). I'm guessing that maybe the system tries to fall back on X if weston fails, but noting that I see in the weston log really jumps out and says that.

From what I can tell having looked elsewhere the PPA page is missing information, specifically about **weston.ini** and **$XDG_RUNTIME_DIR**. Creating the weston.ini file is pretty simple once you find the information (which I need to find again). The second issue is **$XDG_RUNTIME_DIR**, something that isn't so easy to solve:    [https://blueprints.launchpad.net/ubuntu/+spec/foundations-q-xdg-runtime-dir](https://blueprints.launchpad.net/ubuntu/+spec/foundations-q-xdg-runtime-dir)

Reading on even further, I've seen posts in the[**[COLOR="Blue"] Wayland Live CD discussion [/COLOR]**]("http://ubuntuforums.org/showthread.php?p=11809731#post11809731")that suggest these aren't that important, so I dunno, but then again I've never been able to get that live cd to start with wayland /weston instead of X.

OK, I did some more testing and I still can't get weston to work with the instructions given. However, I can use weston-launch by merely using **export XDG_RUNTIME_DIR=/tmp/ && weston-launch** without having to mess around with installing or uninstalling anything. The INI file may be useful with some documentation. So far it I managed to add things to the panel using the [launcher] entries, but I couldn't change the wallpaper.

---

### Post by cecilpierce on 2012-07-29
I cant get wayland live cd to work so im useing a spare QQ with .94 wayland suff and nouveau driver and I get this:
warning: XDG_RUNTIME_DIR "/home/cecil" is not configured
correctly.  Unix access mode must be 0700 but is 755,
and XDG_RUNTIME_DIR must be owned by the user, but is
owned by UID 1000...

What to do ???

---

### Post by cecilpierce on 2012-07-29
Nouveau didnt work so good so I went back to nvidia-current 302.17, better responce   :)

---

### Post by lehjr on 2012-07-29
> **cecilpierce said:**
> I cant get wayland live cd to work so im useing a spare QQ with .94 wayland suff and nouveau driver and I get this:
warning: XDG_RUNTIME_DIR "/home/cecil" is not configured
correctly.  Unix access mode must be 0700 but is 755,
and XDG_RUNTIME_DIR must be owned by the user, but is
owned by UID 1000...

What to do ???

So far weston-launch is the only thing that I can get working, and even that does whine about XDG_RUNTIME_DIR. I've found that even if you set XDG_RUNTIME_DIR to a directory with the mode set to 700 it still gives errors, and doesn't consider 700 to be 0700.

In order to get **weston-launch** to work, you may need to create the **weston-launch** group and add yourself to it:

```
sudo groupadd weston-launch
sudo usermod -a -G weston-launch $USER
```

There's a bit more information [[COLOR="RoyalBlue"]here[/COLOR]]("http://wayland.freedesktop.org/xserver.html") at the bottom under "Running".

Before logging out of X, it would be better to try running **XDG_RUNTIME_DIR=/tmp && weston-launch** from a terminal within your current session, this way you can test whether or not it will even launch successfully, then you can use <CTRL><ALT><F7> and <CTRL><ALT><F8> to go back and forth between your desktop and weston. 

That's as far as I've gotten, but it's a start. I also just managed to get the the "desktop-shell" to change color and take a background image, using the **weston.ini** file and changing **[wayland-desktop-shell]** to **[shell]** because this has apparently changed at least once. The **weston.ini** file isn't needed, but if you want to experiment a bit, here's the one I'm using: ```
[shell]
background-image=/usr/share/wallpapers/albatross-2009-10.png
panel-color=0x90ff0000
locking=true

[launcher]
icon=/usr/share/weston/terminal.png
path=/usr/bin/weston-terminal

[launcher]
icon=/usr/share/weston/terminal.png
path=/usr/bin/weston-terminal


```

If the PPA packages included the demos then the desktop shell would be more interesting because then launchers could be added, but in its current form it's pretty boring and doesn't do much.

---

### Post by lehjr on 2012-07-29
> **cecilpierce said:**
> Nouveau didnt work so good so I went back to nvidia-current 302.17, better responce   :)

Very nice.

---

### Post by lehjr on 2012-07-29
> **cecilpierce said:**
> Nouveau didnt work so good so I went back to nvidia-current 302.17, better responce   :)

Very nice. Looks like you have a little nicer weston.ini than I do :cool:

edit: Odd, my edit turned into a separate response

---

### Post by cecilpierce on 2012-07-29
I tried XWayland-Running cmds and got error msg at the end, cant figure it out!

Here is my /home/cecil/.config/weston.ini file:

---

### Post by cecilpierce on 2012-07-29
Dah! just figured out how to send code, im getting OLD
:P

```
[shell]
type=desktop-shell.so
background-image=/home/cecil/Pictures/tw.jpg
background-color=0x00000000
panel-color=0x900000ff
locking=true

[launcher]
icon=/usr/share/icons/gnome/32x32/apps/utilities-terminal.png
path=/usr/bin/weston-terminal

[launcher]
icon=/usr/share/icons/gnome/32x32/apps/web-browser.png
path=/usr/bin/firefox

[launcher]
icon=/usr/share/icons/gnome/32x32/apps/kfm.png
path=/usr/bin/gnome-terminal

[launcher]
icon=/usr/share/pixmaps/gksu-root-terminal.png
path=/usr/bin/mc
```

---

### Post by madjr on 2012-07-29
Are Ubuntu developers checking this thread ?

I would guess they would be needing a lot of early testers for this.

---

### Post by lehjr on 2012-07-29
> **madjr said:**
> Are Ubuntu developers checking this thread ?

I would guess they would be needing a lot of early testers for this.

Considering some don't even bother looking at the bug reports on launchpad, I doubt it. They still haven't figured out what they're going to do about XDG_RUNTIME_DIR yet, and that would be a really important first step, especially since they plan on putting in the beta release just over a month away. Then again, you'd think that if Canonical was really that gung-ho about adopting Wayland they would have contributed more than 15 lines of code to the project.

---

### Post by cecilpierce on 2012-07-29
@lehjr

New cd out on Wayland Live CD (check last post)and a new script, but I haven't tried the script yet.

[https://sourceforge.net/p/rebeccablackos/](https://sourceforge.net/p/rebeccablackos/)

---

### Post by lehjr on 2012-07-29
> **cecilpierce said:**
> @lehjr

New cd out on Wayland Live CD (check last post)and a new script, but I haven't tried the script yet.

[https://sourceforge.net/p/rebeccablackos/](https://sourceforge.net/p/rebeccablackos/)

Thanks, I'll have to check it out and see what wonders it brings. :-D

I tried building Wayland myself, but with the 0.85 build script instead of doing it manually, but I ran into an error with an undefined type. I'll check the wayland IRC channel tomorrow and see if I can find where it's supposed to be defined. I suspect the script might be outdated, but there is still an error with the source code.

---

### Post by cecilpierce on 2012-07-30
@lehjr

I tried that a few times with no luck (or knowlege).
I wish some one would write a book "Wayland for Dummys".

---

### Post by lehjr on 2012-07-30
> **cecilpierce said:**
> @lehjr

I tried that a few times with no luck (or knowlege).
I wish some one would write a book "Wayland for Dummys".

At this point even some basic, up-to-date documentation would be an improvement.

---

### Post by cecilpierce on 2012-07-30
Really!
Im having fun but no joy, tried the script and got errors but that could be me doing something wrong as usual, I tried 'sudo stop ligntdm' and got DRM not found along with XDG, bla bla bla stuff, but...when I did 'sudo start lightdm' I got a popup window titled 'Choose Display Server' with two options, Xorg and Wayland, but no matter witch one I choose it just goes back to KDE desktop, bummer :confused:

---

### Post by lehjr on 2012-07-30
> **cecilpierce said:**
> Really!
Im having fun but no joy, tried the script and got errors but that could be me doing something wrong as usual, I tried 'sudo stop ligntdm' and got DRM not found along with XDG, bla bla bla stuff, but...when I did 'sudo start lightdm' I got a popup window titled 'Choose Display Server' with two options, Xorg and Wayland, but no matter witch one I choose it just goes back to KDE desktop, bummer :confused:

When I tried the CD I didn't even bother to stop lightdm, I figured it was probably already in the "westoncaller" script. Either way, it works for me (loads the desktop shell) until I click on anything, then it crashes back to a command prompt with a bunch of errors. The build script I was going to use is only setup for building 0.85, which is pretty pointless. So I was going to edit it using the current build documentation, but after thinking about it, I really don't think my 8 year old desktop is anywhere near up to the task.

---

### Post by cecilpierce on 2012-07-30
Don't feel bad, mine is 7 years old and only has 2 DDR1 slots (2 gigs).
I have a spare Compaq AMD64 with 4 slots but cant find any cheap memory, I guess its as old as this one.

---

### Post by lehjr on 2012-07-30
> **cecilpierce said:**
> Don't feel bad, mine is 7 years old and only has 2 DDR1 slots (2 gigs).
I have a spare Compaq AMD64 with 4 slots but cant find any cheap memory, I guess its as old as this one.

Same reason I only have 2GB of RAM. I have 4 slots, with 512MB RAM each. For the cost of a decent set of larger modules I could upgrade the whole system. 

The last time I compiled Qt it took several hours and I ended up doing it all over again on my wife's Dual core laptop, and even then took quite a long time.

---

### Post by lehjr on 2012-08-01
Just a word of caution, today's set of updates left me without an X-server due to an unmet dependency on **xorg-input-abi-16**, and maybe others. I haven't dug into it much because I really hate trying to do things from the command line.

---

### Post by cecilpierce on 2012-08-01
WOW!
Exact same thing happen to me yesterday but with 'xorg-input-abi-12'. Spent all day looking and trying things but no luck, had to reinstall but didnt format so I only had to reinstall a few of my favorite pkgs.
Good luck, let me know if you found a better way.
                         :mad:

I think this thread is simular: 'No login screen' or maybe this, its solved but didnt see it yesterday: 'Unable to login 12.10 after updates'

---

### Post by lehjr on 2012-08-01
I think it was the "Pre-Release" updates that I had enabled. I manually edited the sources.list file from inside another install and disabled it. Then I had to do some purging before reinstalling xorg. 

basically ```
 sudo apt-get remove --purge xserver*
```
then
```
 sudo apt-get install xorg
```

Then either reboot or 
```
sudo stop lightdm
sudo start lightdm

```

While I'm sure it can be done from the command line, I'm unaware of any tools to aid in that and the console based text editor isn't something that inspires confidence.

---

### Post by cecilpierce on 2012-08-01
> **lehjr said:**
> I think it was the "Pre-Release" updates that I had enabled. I manually edited the sources.list file from inside another install and disabled it. Then I had to do some purging before reinstalling xorg. 

basically ```
 sudo apt-get remove --purge xserver*
```
then
```
 sudo apt-get install xorg
```

Then either reboot or 
```
sudo stop lightdm
sudo start lightdm

```

While I'm sure it can be done from the command line, I'm unaware of any tools to aid in that and the console based text editor isn't something that inspires confidence.

I tried something like that and it would purge but not install anything so I gave up, glad some one had some luck.

---

### Post by lehjr on 2012-08-01
Now that I have my system running stable again I think it's time to try the xorg-edgers PPA, that is after I purge everything from this one.

---

### Post by cecilpierce on 2012-08-01
> **lehjr said:**
> Now that I have my system running stable again I think it's time to try the xorg-edgers PPA, that is after I purge everything from this one.

Nice!
I have one installed just for that but haven't looked at it in a week or so, too much other junk going on here, let me know how it comes out and whats new (and improved).

---

### Post by madjr on 2012-08-10
Well here is the latest ubuntu wayland news:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wayland_postponed&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wayland_postponed&num=1)


and A Linux LiveCD To Play With Wayland/Weston:

[http://www.phoronix.com/scan.php?page=news_item&px=MTE1Nzc](http://www.phoronix.com/scan.php?page=news_item&px=MTE1Nzc)

---

### Post by lehjr on 2012-08-10
> **madjr said:**
> Well here is the latest ubuntu wayland news:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wayland_postponed&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wayland_postponed&num=1)


and A Linux LiveCD To Play With Wayland/Weston:

[http://www.phoronix.com/scan.php?page=news_item&px=MTE1Nzc](http://www.phoronix.com/scan.php?page=news_item&px=MTE1Nzc)

Thanks. Since Wayland won't be much more than it is now in 12.10, we probably won't see more of it until 13.04 as an option, since that will be an LTS release. I guess the best hope for full implementation won't even be until 13.10. I think Fedora still plans on having it in their next release, FC18, so at least there will be that option.

---

### Post by EgoGratis on 2012-08-10
Ubuntu 13.04 won't be LTS release next LTS release will be Ubuntu 14.04.

---

### Post by lehjr on 2012-08-10
> **EgoGratis said:**
> Ubuntu 13.04 won't be LTS release next LTS release will be Ubuntu 14.04.

Ah, so maybe 13.04 will see Wayland implemented then. That's still quite a ways off from now though. It's really not surprising, if you look at their blueprints you'll see very little Wayland related  activity.

---

### Post by t1497f35 on 2012-08-11
> **lehjr said:**
> Ah, so maybe 13.04 will see Wayland implemented then. That's still quite a ways off from now though. It's really not surprising, if you look at their blueprints you'll see very little Wayland related  activity.
Yes, but it's to be expected since Wayland is pretty hard to get to work **well** on a wide enough line of hw. So it's easier and more practical to wait for a stable Wayland 1.0 release which I'm expecting to be released around December this year.

---

### Post by lehjr on 2012-08-11
> **t1497f35 said:**
> Yes, but it's to be expected since Wayland is pretty hard to get to work **well** on a wide enough line of hw. So it's easier and more practical to wait for a stable Wayland 1.0 release which I'm expecting to be released around December this year.

I think your estimate is pretty good based on what I've tried between the xorg-edgers PPA and the live CD. That could probably have been sped up more if Ubuntu devs were a bit more active in code contributions to Wayland. I still get a bit of a chuckle over that "1.0 release coming soon" announcement from back in February. Either way, I'd rather not see it rushed like Gnome 3 was. I am anxious to see the API stabilize enough to start seeing tutorials for the simplest of things like creating native windows and things of that nature.

---

### Post by Hungry Man on 2012-08-12
Has anyone got it working on 12.10? Do the open source ATI drivers work with it?

I'll read through the thread later in case I missed these answers already but I'd be interested in running Wayland over X.

---

### Post by lehjr on 2012-08-12
> **Hungry Man said:**
> Has anyone got it working on 12.10? Do the open source ATI drivers work with it?

I'll read through the thread later in case I missed these answers already but I'd be interested in running Wayland over X.

The XWayland part of the Wayland Live CD worked for me a week ago, but not Wayland natively. That may have changed though. And everything I have here is ATI/AMD based. 

But AFAIK, there aren't any working PPA builds at the moment so you would probably have to build it yourself and I'm guessing the code changes faster than the documentation.

---

### Post by cecilpierce on 2012-08-12
Any news on Fedora-Wayland ?

---

### Post by lehjr on 2012-08-12
> **cecilpierce said:**
> Any news on Fedora-Wayland ?

As far as I can tell there isn't much activity surrounding it. They apparently have Weston in their FC18 repos, but I can't even find much recent activity on their forums about it. There's nothing about it in the FC18 plans either. It might just be that no one is going to plan on using it until after the testing and bug fixing stage, and they still have to get it working before any wide scale tests can be done.

Just getting Wayland itself working is one thing, there's still much work to be done in terms of code changes required to make things work with it.

---

### Post by cecilpierce on 2012-08-13
I searched to and didn't find much of anything.

I have an old Dell 260 that has intel video and a nvidia dvi card, took out the card and tried to run RBL and it locked up worse then it did with the nv card :P

---

### Post by lehjr on 2012-08-13
> **cecilpierce said:**
> I searched to and didn't find much of anything.

I have an old Dell 260 that has intel video and a nvidia dvi card, took out the card and tried to run RBL and it locked up worse then it did with the nv card :P

I guess backwards compatibility might be an issue for Wayland then.

---

### Post by cecilpierce on 2012-08-14
> **lehjr said:**
> I guess backwards compatibility might be an issue for Wayland then.

I thought my intel would work because nerdopolis is using intel, can't figure this wayland out, guess it just don't like me :P

---

### Post by lehjr on 2012-08-14
> **cecilpierce said:**
> I thought my intel would work because nerdopolis is using intel, can't figure this wayland out, guess it just don't like me :P

I have an older Intel based machine that I picked up over the weekend. When I get a chance I'll see if I can get that LiveCD working on there.

---

