---
title: "HOWTO: Get rid of video TEARING in Compiz with NVIDIA"
date: 2010-01-25
forum: Tutorials
---

### Post by kopiwe on 2010-01-25
You experience [COLOR=Red][Screen Tearing]("http://en.wikipedia.org/wiki/Screen_tearing") [/COLOR]when watching video in Compiz? Here is the solution:

_**First:**_
Type in Terminal
```
sudo apt-get install compizconfig-settings-manager
```Open:* CompizConfig Settings Manager*: [I](System -> Preferences -> CompizConfig Settings Manager)
[/I] Find: [I]General Options - Display Settings
Change:
[/I]
[LIST]
[*]"Sync To VBlank" to "enabled"
[/LIST]
[U][B] 
Second:[/B][/U]
Open:* Nvidia X Server Settings*: [I](System -> System Settings -> Nvida X Server Settings)
[/I] Find: *OpenGL Settings*
Change:

[LIST]
[*]"Sync To VBlank" to "enabled"
[/LIST]
[U][B]
Third:[/B][/U]
Open: *System -> Preferences -> Startup Applications*
Add a new entry:

[LIST]
[*] Name:   "Nvidia Settings"
[*]Command:  "nvidia-settings --load-config-only "
[/LIST]
[U][B] 
Optional:[/B][/U]
For a smoother window movement and compiz-cube rotation, set "refresh rate"  equal to the refresh rate of your monitor (nvidia-settings -q RefreshRate). 
Compiz incorrectly detects a bogus refresh rate because of nvidias dynamic-twinview solution.

Open:* CompizConfig Settings Manager*: [I](System -> Preferences -> CompizConfig Settings Manager)
[/I] Find: *General Options - Display Settings*
Change:

[LIST]
[*]"Detect Refresh Rate" to "disabled"
[*] "Refresh Rate" to "60"
[/LIST]
*Hint: You could set the refresh rate of compiz double the refresh rate  of your monitor **(120 in my case) *[I]for **extra smoothiness!**
[/I] 


restart X. *(sudo restart gdm)*


There you go, no more tearing.

---

### Post by phDaemon on 2010-01-25
Cool...i did a search for sync to vblank but came up with nothing...is this for weaker gcards?

---

### Post by TomBous on 2010-01-25
Hi, thank you for you How To. I was waiting for these since 1 year :)

---

### Post by lovinglinux on 2010-01-25
Unfortunately, that doesn't work for everyone. On my machine, the tearing is fixed [this way](http://ubuntuforums.org/showthread.php?p=7950332#post7950332).

---

### Post by comcroa on 2010-01-25
Wow! Nice tutorial. It worked like a charm on my side.
Thanks!
-Daniel

---

### Post by skalka on 2010-01-26
Doesn't work for me, my pdf are still unreadable. The only solution at the moment is using Metacity.

---

### Post by yarjar on 2010-01-26
This worked perfectly for me - thank you so much! Excellent tutorial.

---

### Post by jerrynewt on 2010-01-27
Is the command "nvidia-settings -(one)" or nvidia-settings -(small L)" ??
When I use the copy and paste in terminal I can't tell which one is input for the command. I used the copy and paste, but just wondering which one it is.

---

### Post by Cresho on 2010-01-28
Here don't listen to those guys...just kidding!

if you want nvidia-settings to globally stick, you need to put nvidia-settings -l into Xsessions

in kubuntu it is 

#sudo kate /etc/X11/Xsession


in ubuntu it is


#sudo gedit /etc/X11/Xsession

and paste the "its little l by the way"

the portion should look like this

```
#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 967 2005-12-27 07:20:55Z dnusinow $
nvidia-settings -l
set -e
```

and then you have the rest of the code which im not posting.

anyway, reboot and it takes effect.  If you want to test it out, open up nvidia-settings, then raise the brightness, close and reboot.  then you will see that the drivers take effect.  This is the perfect way to get nvidia-settings to stick in all user desktops.

Now I recommend kaffeine for kde and smplayer or kaffeine for gnome.  Make sure in smplayer, you use direct rendering and ......damn i forgot..ohh yeah use opengl.  This syncs video playback.  Fix compiz normaly like you do.  Since nvidia-settings kicks in before compiz fusion, this fixes all problems because compiz kicks in after.  so nvidia settings will stick.


Everybody has been looking for the secret sauce and here it is.  The guy who posted ontop is partially correct but it only works for hary and lower.  You need to have nvidia-settings start off before compiz starts or settings will not stick.


do the brightness check and you'll see the difference and dont forget to reset brightness before you forget..... also if your using a compositor, nvidia-settings will take effect after a reboot.  If your not, then you need to not reboot....lol

---

### Post by realzippy on 2010-01-28
> **Cresho said:**
> Here don't listen to those guys...just kidding!

if you want nvidia-settings to globally stick, you need to put nvidia-settings -l into Xsessions

in kubuntu it is 

#sudo kate /etc/X11/Xsession


in ubuntu it is


#sudo gedit /etc/X11/Xsession

and paste the "its little l by the way"

the portion should look like this

```
#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 967 2005-12-27 07:20:55Z dnusinow $
nvidia-settings -l
set -e
```

and then you have the rest of the code which im not posting.

anyway, reboot and it takes effect.  If you want to test it out, open up nvidia-settings, then raise the brightness, close and reboot.  then you will see that the drivers take effect.  This is the perfect way to get nvidia-settings to stick in all user desktops.

Now I recommend kaffeine for kde and smplayer or kaffeine for gnome.  Make sure in smplayer, you use direct rendering and ......damn i forgot..ohh yeah use opengl.  This syncs video playback.  Fix compiz normaly like you do.  Since nvidia-settings kicks in before compiz fusion, this fixes all problems because compiz kicks in after.  so nvidia settings will stick.


Everybody has been looking for the secret sauce and here it is.  The guy who posted ontop is partially correct but it only works for hary and lower.  You need to have nvidia-settings start off before compiz starts or settings will not stick.


do the brightness check and you'll see the difference and dont forget to reset brightness before you forget..... also if your using a compositor, nvidia-settings will take effect after a reboot.  If your not, then you need to not reboot....lol

I use a script which runs *nvidia-settings -l* before compiz starts to have AntiAliasing running (Cube looks much better)...thought with your solution I could get rid of it,but your solution **does not work**.
Tested it on Karmic and Lucid....(did not test brightness but AA and AF)

Edit:
Surprisingly *nvidia-settings -l* in autostart does the job on Lucid....

---

### Post by GameboyRMH on 2010-02-21
Worked for me too! Thanks! First time I've had tear-free video using nvidia drivers! :D

Karmic 64bit
Dual GTX 260 core 216 superclocked in SLI.

---

### Post by kopiwe on 2010-05-21
Tearing is still not fixed in Lucid, but this tutorial works here aswell. updated

---

### Post by boina on 2010-06-17
Great great help kopiwe!!!!! Thank you very much.... I've been loking for a solution to this since ubuntu 9.10 with an nvidia GeForce 7200 SE until ubuntu lucid with an nvidia GT220!!!!
Worked like a charm here!!!!!

---

### Post by papibe on 2010-06-22
This works! Thanks kopiwe :p, ...but

I'd like to ad a caveat. If you have dual head setup, you need an extra trick (especially if you have two different monitors). The following steps works when the monitors are configured as two separate X Screens.

When you go to CompizConfig Setting Manager (CSM), before going to General Options, you'll see in the upper left corner a field that shows Screen 0, or Screen 1. You need to setup Sync to VBlank for both screens.

The problem is that even if you change that field for both screens, it DOES NOT work unless you do it separately:

1. Open CSM on screen 0 (main monitor) and set Sync to VBlank. Close it.
2. Go to your screen 1 (other monitor), and open CSM there. Now set Sync to VBlank there.


...and then worked for me (I even have a compiz-cube working in each screen!)
Regards.

---

### Post by Forming on 2010-06-25
Thanks , thats useful.

---

### Post by selittl on 2010-07-26
This fixed the tearing for me in Lucid.  Using VLC everthing works great.  I still get herky jerkyness playing matroska vids on mplayer though.  Any fix for that?

---

### Post by kopiwe on 2010-08-08
> **selittl said:**
> This fixed the tearing for me in Lucid.  Using VLC everthing works great.  I still get herky jerkyness playing matroska vids on mplayer though.  Any fix for that?


Matroska is only the container for a codec, wich is probably the h.264 in your case. If it is, you could try the "vdpau" instead of the "xv" video output. [VDPAU]("http://en.wikipedia.org/wiki/VDPAU") uses your graphic card to accelerate video playback.

---

### Post by Dakiraun on 2010-11-03
Works well on the work laptop, but not on the home one.  Home laptop is an old Compaq R3000 which uses the 440 Go GPU.  For some reason, enabling V-Sync in Compiz causes it to not come out of stand-by/suspend.  I imagine this is just a quirky issue related to that particular system though.  The tearing is not too bad on it anyway.

---

### Post by ymerdawe on 2012-03-27
My tearing problem was caused becauce i have two screens. I Started nvidia settings: under the tab xvideo settings i selected my tv to be the "sync to this display device". At first i tried with the compiz thing but i did not even have the setting to set the refresh rate after unchecking auto detect

---

