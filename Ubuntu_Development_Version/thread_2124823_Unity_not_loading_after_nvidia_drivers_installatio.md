---
title: "Unity not loading after nvidia drivers installation"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by SkylineGTR on 2013-03-12
Hi.

I've messed up my ubuntu 13.04.
I've installed nvidia drivers with this commands (found on a STEAM guide):

apt-get install nvidia-experimental-310
apt-get install libgl1-mesa-glx:i386

But now unity does not load. After login I only get the wallpaper, nothing more.
I already purged this packages and tried to reinstall ubuntu-desktop but I still get the same problem.

Any ideas?

---

### Post by dino99 on 2013-03-12
use synaptic to purge the installed nvidia packages, drop the xorg.conf too if it exist, then install nvidia-313-updates

---

### Post by SkylineGTR on 2013-03-12
Nothing :(
Any more ideas?

---

### Post by SkylineGTR on 2013-03-12
Tried to reinstall unity and ubuntu-desktop and nothing.
Tried to reset unity, but I'm getting an error:

dconf reset -f /org/compiz/

Error spawning command line 'dbus-launch --autolaunch= (...): Child process exited with code 1


Have some errors on xsession-error file:
compiz (core) - Error: Plugin 'opengl' not loaded.
(...)
I/O warning : failed to load external entity "/home/myuser/.compiz/session/(...)

---

### Post by SkylineGTR on 2013-03-13
How can I solve this opengl errors on compiz?
How can I have unity back?

Need help please [-o< :-(

---

### Post by wribeiro on 2013-03-13
Ctrl-Alt-t
type ccsm
Enable Unity Plugin

---

### Post by SkylineGTR on 2013-03-13
Still nothing :(

---

### Post by ronacc on 2013-03-13
I'm getting the same thing with the 304.84  nvidia driver , I get the unity desktop but no top bar and no launcher , rt click on the desktop lets you start a terminal and you can launch things that way ( you may need nautilus open terminal installed)  , Gnome-shell works normally so maybe its a compiz problem .

---

### Post by dino99 on 2013-03-14
I usually log into gnome-fallback, and also get that decorator issue: no titlebar, cant resize window, buttons close/minimize/maximize removed, only one workplace available. Removing compiz does not help (i've purged then reinstalled it too, but no more luck), so compiz should not be the faulty package.
I've also seen a mutter package(s) upgrade; that one could have pushed that trouble, but i'm not sure; still investigated before reporting.
Here unity/gnome-shell/gnome-fallback can be loaded normally on i386.

---

### Post by zemikit on 2013-03-14
1. I purge all nvidia-*.
2. Reboot
3. Login
4. Launch gnome-terminal
5. Install ccsm
6. Run ccsm
7. Enable Unity Plugin
8. Resolv conflicts with keys

---

### Post by serdotlinecho on 2013-03-14
To restart unity shell or compiz on 12.10 and 13.04:

Restart unity without restart compiz, in terminal:

```
setsid unity
```

Restart unity by restarting compiz:

```
setsid compiz --replace
```

---

### Post by SkylineGTR on 2013-03-14
I've tried that already, and nothing.

I have a bunch of errors about OpenGL in my xsession-errors:

```
compiz (core) - Error: Plugin 'opengl' not loaded.
```

I've searched about this error and tried some things to fix this opengl error, but none worked.
RR was working great until I followed this guide from steam:
[http://steamcommunity.com/sharedfiles/filedetails/?id=127235417#25477](http://steamcommunity.com/sharedfiles/filedetails/?id=127235417#25477)

I've tried everything and can't fix unity :\
Is my only option format and reinstall RR?

---

### Post by ronacc on 2013-03-14
I got unity working again , heres how . I installed the nvidia 304 updates and the nvidia settings updates ( I don't know if this had anything to do with it ) , I reinstalled unity rebooted and loged into unity ( ubunty default ) still no top bar and launcher , then I brought up ccsm and enabled the unity plugin , it said it conflicted with 2 gnome settings and asked to disable them I clicked disable them and unity came up working . I logged out of unity and into gnome-shell and it also seems to be normal . I logged out of gnome-shell and back into unity and it is still working so it may be as simple as reinstalling unity and letting it disable the 2 things it asks to in ccsm .

---

### Post by dino99 on 2013-03-14
yeah, compiz becomes a pain: there is no schemas inside dconf  :(

---

### Post by VinDSL on 2013-03-14
> **ronacc said:**
> I'm getting the same thing with the 304.84  nvidia driver [...]  Gnome-shell works normally [...]
Unity has not worked correctly, since I started running Gnome 3 Staging.

However, if I load Unity from inside a Gnome-Shell session, it works fine.

Might want to try that...

[LIST]
[*]Login to GS
[*]Open a terminal, type:
```
unity --replace &
```
[*]Press [Enter]
[*]Close terminal, when dialog lags out (decorator error)
[/LIST]

Everything, including Compiz, works perfectly for me.

---

### Post by ronacc on 2013-03-14
@ VinDSL  see my post #13

---

### Post by VinDSL on 2013-03-14
> **ronacc said:**
> @ VinDSL  see my post #13
Oh, okay!  Sorry!

I should have kept reading.

Glad you got it sorted...

---

### Post by mojo636 on 2013-03-20
> **ronacc said:**
> I got unity working again , heres how . I installed the nvidia 304 updates and the nvidia settings updates ( I don't know if this had anything to do with it ) , I reinstalled unity rebooted and loged into unity ( ubunty default ) still no top bar and launcher , then I brought up ccsm and enabled the unity plugin , it said it conflicted with 2 gnome settings and asked to disable them I clicked disable them and unity came up working . I logged out of unity and into gnome-shell and it also seems to be normal . I logged out of gnome-shell and back into unity and it is still working so it may be as simple as reinstalling unity and letting it disable the 2 things it asks to in ccsm .

I can confirm that the above worked for me also :-)

---

### Post by SkylineGTR on 2013-03-22
After trying many things with no success I finally solved my problem :D

1. Format
2. Install RR again

[IMG]http://soshable.com/wp-content/uploads/2010/09/Everything_went_better_than_expected.png[/IMG]

---

### Post by naceira on 2013-04-26
> **ronacc said:**
> I got unity working again , heres how . I installed the nvidia 304 updates and the nvidia settings updates ( I don't know if this had anything to do with it ) , I reinstalled unity rebooted and loged into unity ( ubunty default ) still no top bar and launcher , then I brought up ccsm and enabled the unity plugin , it said it conflicted with 2 gnome settings and asked to disable them I clicked disable them and unity came up working . I logged out of unity and into gnome-shell and it also seems to be normal . I logged out of gnome-shell and back into unity and it is still working so it may be as simple as reinstalling unity and letting it disable the 2 things it asks to in ccsm .

It worked for me too! I had this same issue with the final version of RR released yesterday.
Thanks a lot, Ronacc :)

---

### Post by k_vlad on 2013-04-26
I have the same problem. Ronacc's method dont help. when I set checkbox to install unity plugin it said it needs to install opengl plugin. I click ok install, than it wants to install expo. then expo said it needs opengl. and than i click again install opengl. window closes and still nothing is installed - unity plugin, opengl plugin, expo - nothing installed. stupid ccsm and unity..

---

### Post by naceira on 2013-04-26
That happened to me too. Deactivate plugin and activate again. It worked for me when I repeated it two or three times.
Hope that helps.

I also found this workaround, but I did't test it. In case it is helpful for anyone I post it here:
```
dconf reset -f /org/compiz/
```

---

### Post by aqcohen on 2013-05-08
Try this from your home dir

rm -rf .config/dconf

unity works again, BUT you will be lost your preferences

---

### Post by bogan on 2013-05-08
Hi! All,

I have had the same 13.04 Blank Desktop with five different installations running different Nvidia cards and drivers, and none of the suggestions in this Thread - or others - worked for me.

In nearly all of them I got errors similar to **SkylineGTR **> Error spawning command line 'dbus-launch --autolaunch= (...): Child process exited with code 1
 Or "GLX plug-in not loaded' or 'unable to open display'.

However, the Guest account still worked correctly, as did a new Administration account and Fallback.

The cure of the problems on all my installations was effected by the following: run from a terminal  in Fallback  mode to enter the '--reset-unity' command included in  Unity-Tweak-Tool: ```
sudo apt-get install gnome-session-fallback # if not already installed and log-in to 'fallback'.
echo $DESKTOP_SESSION 
fallback-compiz
sudo apt-get install unity-tweak-tool
gksudo unity-tweak-tool --reset-unity  

Warning: You are about to reset unity to its default configuration. 
   It is normal for your desktop to flicker during the process.    
Type yes to continue, anything else to exit.        Do You wish to continue? _ 
```On rebooting all the log-in options' displays were correct and with intact Launchers and Panels.

 Running the same commands when logged into the faulty Ubuntu/Unity  Blank  Desktop gave a 'Can not open display' message and did nothing.

It is probable - though I have not tried it - that the other compiz/unity reset commands would also work if run in the same way, from a desktop option that** is** working.

See my Thread in Ubuntu+1 for even more suggested cures:[http://ubuntuforums.org/showthread.php?t=2136435](http://ubuntuforums.org/showthread.php?t=2136435)

Chao!,** bogan.**

---

### Post by andrikos on 2013-05-26
> **wribeiro said:**
> Ctrl-Alt-t
type ccsm
Enable Unity Plugin

Thanks!

---

### Post by GuenterErde on 2013-05-26
I have this problem sometimes too. Usually, I load into another desktop enviroment (ie xfce, since it's lightweight), and for some reason, that ususally resolves it. Also try installing a different driver. That does it for me sometimes too.

---

