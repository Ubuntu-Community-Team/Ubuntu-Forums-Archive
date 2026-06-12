---
title: "No display with nvidia drivers via nvidia-prime (optimus), excepting gnome"
date: 2015-09-06
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-09-06
****Test on a  i7-4700MQ CPU, Intel® Haswell Mobile,  Nvidia GT770m, fresh install of 15.10 with today&#8217;s image
The 352/355 drivers install fine, a restart is to black login screen, logging in from there blindly produces another black screen.

A same day Ubuntu-Gnome image install runs nvidia just fine.
A gnome shell session on an Ubuntu install works fine

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1501041](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1501041)

---

### Post by QDR06VV9 on 2015-09-07
Have you tried this PPA [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)


I was having a few issues with the 352 Driver, But 355 has the majority of those mostly solved.
Regards

---

### Post by aljosa2 on 2015-09-13
test on asus optimus notebook X750JN-TY027H (intel® core™ i7-4710HQ; bit 64; RAM 8GB; nvidia geforce GT 840M), fresh install:

***daily build wily-desktop-amd64.iso 12-Sep-2015:***

wily installation failed at the very beginning of the installation process.

***daily build wily-desktop-amd64.iso 11-Sep-2015:***

wily installation successful. 
the nvidia 352.30 driver from additional drivers installs fine, a restart is to black login screen, logging in from there blindly produces another black screen.

---

### Post by mc4man on 2015-09-13
Still seeing here also though now from a tty apt-get purge nvidia* does work ok & a reboot gives a working login to intel gpu. None of the logs I've seen indicate any reason why no display on nvidia gpu.
Same drivers work fine on 14.04.3 & 15.04

Main reason I tried on 15.10 was to see if my current ubuntu-drivers-common fix for no tearing on a nvidia/optimus/ubuntu session works like it does in 14.04.x & 15.04

---

### Post by QDR06VV9 on 2015-09-13
> [COLOR=#000000]None of the logs I've seen indicate any reason why no display on nvidia gpu.[/COLOR]
And they are still recommending the 352 && 355 Drivers at Nvidia.
None of the selected patches they have(suggested) work.
Regards

---

### Post by mc4man on 2015-09-13
From a black screen (on nvidia) just realized that one doesn't need to remove the currently worthless nvidia drivers, just go to a tty, login &
sudo prime-select intel
then reboot

---

### Post by mc4man on 2015-09-13
Decided to try todays ubuntu-gnome image which after using a workaround to get it to install it showed the same failure, both with Ubuntu repo drivers & the ppa 355 ones.
Downgraded mesa, no change
Downgraded xserver to the first one in Wily & now nvidia works with nvidia-prime. So issue may lie with xserver.
Used just the 2 packages in screen to downgrade with  -

Edit: only seemed to work on Ubuntu-gnome, Ubuntu remains unable to use nvidia here.. So for the moment no longer care, if Ubuntu can get it's stuff together this month great, if not then am losing interest.

---

### Post by xeizoo on 2015-09-15
> **mc4man said:**
> Decided to try todays ubuntu-gnome image which after using a workaround to get it to install it showed the same failure, both with Ubuntu repo drivers & the ppa 355 ones.
Downgraded mesa, no change
Downgraded xserver to the first one in Wily & now nvidia works with nvidia-prime. So issue may lie with xserver.
Used just the 2 packages in screen to downgrade with  -

Edit: only seemed to work on Ubuntu-gnome, Ubuntu remains unable to use nvidia here.. So for the moment no longer care, if Ubuntu can get it's stuff together this month great, if not then am losing interest.

So which is the best multimedia oriented distro? I suggest it still is Ubuntu, even though not perfect.

---

### Post by mc4man on 2015-09-17
> **xeizoo said:**
> So which is the best multimedia oriented distro? I suggest it still is Ubuntu, even though not perfect.

I don't think Ubuntu is very multimedia oriented at all, it offers Videos(totem) & rhythmbox.  In general it just takes from Debian without much or any change.

---

### Post by aljosa2 on 2015-09-21
[**Kernel 4.2.1-stable review**]("http://www.gossamer-threads.com/lists/linux/kernel/2261240#2261240")

hpj at urpla:
*"this revision seems to be missing [PATCH 4.2-rc5] workqueue: Make flush_workqueue() available again to non GPL modules"*

gregkh at linuxfoundation:
*"be patient, it will make it into some future 4.2-stable release"*

---

### Post by mc4man on 2015-09-21
> **aljosa2 said:**
> [**Kernel 4.2.1-stable review**]("http://www.gossamer-threads.com/lists/linux/kernel/2261240#2261240")

hpj at urpla:
*"this revision seems to be missing [PATCH 4.2-rc5] workqueue: Make flush_workqueue() available again to non GPL modules"*

gregkh at linuxfoundation:
*"be patient, it will make it into some future 4.2-stable release"*

Not sure what that has to do with it, I've got nvidia via nvidia-prime working fine here in Ubuntu-Gnome. Ubuntu however is a no-go.

---

### Post by QDR06VV9 on 2015-09-22
This is not a optimus device
```
me@me-Aspire-M3300:~$ inxi -Fxz
System:    Host: me-Aspire-M3300 Kernel: 4.2.0-11-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity 7.3.2 (Gtk 3.16.6-1ubuntu1)
           Distro: Ubuntu 15.10 wily
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 20742
           clock speeds: max: 2600 MHz 1: 1900 MHz 2: 1900 MHz 3: 1400 MHz
           4: 1400 MHz
Graphics:  Card: **NVIDIA GF119 [GeForce GT 520] **bus-ID: 01:00.0
           Display Server: X.Org 1.17.2 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0** NVIDIA 355.06** Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Creative Labs SB Audigy
           driver: snd_emu10k1 port: e800 bus-ID: 04:05.0
           Sound: Advanced Linux Sound Architecture v: k4.2.0-11-generic

```
Just to verify ppa:mamarley/nvidia is working, with some very small glitch's
Regards

---

### Post by mc4man on 2015-09-24
Also fails on Xubuntu & Lubuntu, didn't try Kubuntu but likely there also as all use lightdm.

---

### Post by aljosa2 on 2015-09-27
Problem finally fixed? Waiting for someone to test his optimus device with this new kernel :)

[**Kernel 4.2.2-stable review**]("http://www.gossamer-threads.com/lists/linux/kernel/2265788#2265788")
[I]Pseudo-Shortlog of commits: 
Tim Gardner <tim.gardner [at] canonical> 
workqueue: Make flush_workqueue() available again to non GPL modules[/I]

---

### Post by mc4man on 2015-09-27
> **aljosa2 said:**
> Problem finally fixed? Waiting for someone to test his optimus device with this new kernel :)

[**Kernel 4.2.2-stable review**]("http://www.gossamer-threads.com/lists/linux/kernel/2265788#2265788")
[I]Pseudo-Shortlog of commits: 
Tim Gardner <tim.gardner [at] canonical> 
workqueue: Make flush_workqueue() available again to non GPL modules[/I]

You really should pay attention, that isn't the issue as that fix came in early August. 
As mentioned the nvidia module builds fine, is loaded fine, ect., ect.  Logs for all non working sessions seem fine.
Just no display on nvidia  except in a gnome session with gdm as DM

---

### Post by mc4man on 2015-09-28
Actually now finding this interesting rather than frustrating, also a decent exercise in keyboard use/memory, so put in a new install of today's Ubuntu image, also installed gnome-shell but keep everything else as is.

As it turns out everything works fine, just no display at greeter or upon login. So apps can be opened, commands run, logs created or copied.
I can listen to music, play videos, ect., ect.  Just no display.
Ex.
After blind login open a terminal (ctrl+alt+t
Start a player on a vid, it plays fine, I hear it. No errors on playback as seen in stdout to a file, it uses vdpau, ect.

> Playing: 1.mp4
 (+) Video --vid=1 (*) (h264)
 (+) Audio --aid=1 --alang=und (*) (aac)
AO: [pulse] 44100Hz stereo 2ch float
Using hardware decoding (vdpau).
VO: [opengl-hq] 1920x1080 vdpau

Exiting... (Quit)


For the times when I'd like to actually see what I'm doing one can switch sessions at the black greeter with tab, enter, tab, enter, then password,  enter..

Maybe it's just blanking the screen while in anything but gnome session, don't know how to test that yet.

---

### Post by mr12 on 2015-10-01
Hi just for reference, i fixed the same problems months ago, maybe it can help you guys.

[http://forum.ubuntu-it.org/viewtopic.php?f=47&t=597866](http://forum.ubuntu-it.org/viewtopic.php?f=47&t=597866)

Its in italian because im italian and i like my country language, take your time to translate it.

Ps: lightdm work, but only after 10 minutes of "no use", because the bug fix itself when screen go sleep and then get wakeup from user doing (like move mouse or press a key)

For more you need to read the topic.

> **mc4man said:**
> Maybe it's just blanking the screen while in anything but gnome session

You got a point, good boy :)

---

### Post by mc4man on 2015-10-01
> **mr12 said:**
> Hi just for reference, i fixed the same problems months ago, maybe it can help you guys.

[http://forum.ubuntu-it.org/viewtopic.php?f=47&t=597866](http://forum.ubuntu-it.org/viewtopic.php?f=47&t=597866)

Its in italian because im italian and i like my country language, take your time to translate it.
)
Thanks for info - had already come to conclusion it revolved around 'blanking' the screen & implemented a temp hack-around  via a startup script until it can be fixed properly in either the driver, nvidia-prime or ubuntu-drivers-common.

Your xorg.conf edit looks promising but is of no positive affect here, could be how I added it to xorg.conf but the translation was unclear on that point & I've no interest deciphering that forum thread any further. If in fact an xorg.conf section would resolve then that would need to be patched into u-d-c so it was automatically written in on gpu change(s).

---

### Post by mr12 on 2015-10-02
The xorg.conf on my topic have a blanking command, so no need script at start-up.
My topic solution not work only if you use the latest "drm" packages, because they block forever the screen in the black-sleeping state.
I blocked "drm" after many restore with clonezilla so im sure are them the problem, myabe with a old version of them the problem can be avoided...

---

### Post by bryan-internalfx on 2015-10-18
> 'blanking' the screen & implemented a temp hack-around

What was your hack work around script?

I have the same issue....

---

### Post by mc4man on 2015-10-18
> **bryan-internalfx said:**
> > 'blanking' the screen & implemented a temp hack-around

What was your hack work around script?

I have the same issue....
To note: If the display is returned at the greeter screen then the login will be fine, however haven't found a decent way to force a blank/unblank at the greeter.
So because I'm a single user, single session, have enabled autologin to bypass the greeter. When I do a log out from an ubuntu session then I still need to do a blind login.
(- It's actually easy to do blind logins & even switch users and/or sessions with the tab key, a little practice when on Intel gpu shows how..

So for one user - 
create ~/bin or place script in a bin in $PATH, ~/bin is easier
Assuming using ~/bin
```
mkdir -p ~/bin
```
```
gedit ~/bin/blank1
```
use this in ^
```
#!/bin/bash
xset dpms force off 
xset dpms force on
```
save & close gedit
make script executable either thru right click on script > permissions or
```
chmod u+x ~/bin/blank1
```
Create a startup
```

mkdir -p ~/.config/autostart && gedit ~/.config/autostart/blank1.desktop
```
use this inside ^
```
[Desktop Entry]
Type=Application
Exec=blank1
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=blank
Comment=bug hack fix
X-GNOME-Autostart-Delay=
```

Open System Settings > User Accounts > set your user to autologin if not wanting to do a blind login at fresh boot greeter
Reboot

Edit: the side advantage of using autologin is if you log out of your session & the greeter shows up then you'll know the bug has been fixed, then one can remove the script & autostart .desktop.

---

### Post by QDR06VV9 on 2015-10-18
@mc4man thanks and can confrim this works on a Toshiba Qosmio X70 with GTX 770M.
Did this last nite for a Friend.
Feeling a little stupid here now though I did not add in the hack

```
#!/bin/bashxset dpms force off 
xset dpms force on
```

As I did not see this last nite.(I know it was not posted yet.)
But I did add
Create a startup

> mkdir -p ~/.config/autostart && gedit ~/.config/autostart/blank1.desktop

```

[Desktop Entry]
Type=Application
Exec=blank1
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=blank
Comment=bug hack fix
X-GNOME-Autostart-Delay=
```



So is this going to effect my buddy's Laptop soon?
Sor far it is working after 2 reboots
Thanks && Regards

---

### Post by mc4man on 2015-10-18
> **runrickus said:**
> @mc4man thanks and can confrim this works on a Toshiba Qosmio X70 with GTX 770M.
Did this last nite for a Friend.
So is this going to effect my buddy's Laptop soon?
Sor far it is working after 2 reboots
Thanks && Regards
I don't know how widespread this issue will be with nvidia mobile chips & nvidia-prime but certainly has the possibility to affect a large number of users come release if not fixed. 
I'm going to keep adding affected or possible causative sources to the bug report until someone in Ubuntu takes a look at.
(currently confirmed, critical,  5 sources listed, am going to add lightdm today.

I'm starting to consider a new Ubuntu bug for 16.04/unity7/compiz, et al. - 
"Ubuntu bug #2 - If you can't do it right then don't do it at all"

---

### Post by QDR06VV9 on 2015-10-18
Thank you sir!
More info may be related,This install was **Wily Mate with GDM**
 I installed his with Ubuntu graphics PPA, and your tear free PPA, Dont know if that was needed but did more for testing purpose's.
Will update if any relevant information pops up.
Best Regards

---

### Post by mc4man on 2015-10-18
> **runrickus said:**
> Thank you sir!
More info may be related,This install was **Wily Mate with GDM**
 I installed his with Ubuntu graphics PPA, and your tear free PPA, Dont know if that was needed but did more for testing purpose's.
Will update if any relevant information pops up.
Best Regards
In regards to the tear-free test ppa. It does not 'fix' the issue which is well known to nvidia & nvidia-prime maintainer but does eliminate about 99% of tearing here on 2 mobile chips, tested on Ubuntu & Ubuntu-Gnome
(- the mobile chipset tearing occurs everywhere on installs that use a compositing window manager.
Right now on a GTX 775m the only tearing I see is when moving the mouse cursor inside of a video window or moving it  in a fullscreen video. Otherwise it's perfect.

I have a 940m laptop coming this week, I may try Ubuntu on it though it wouldn't surprise me if Ubuntu doesn't work at all right now. (skylake i7cpu
Maybe someday they'll fix the tearing on mobile or maybe wayland/mir won't have this issue (or maybe Ubuntu won't use compositing after 16.04..

---

### Post by emil15 on 2015-10-19
Hi.

I installed xubuntu 15.10, on my asus with 650m optimus. Got the login screen, and then a black screen after login. My solution:

After getting the black screen I hit:

   CTRL+ALT+F1, then logged in.

then:

   sudo nano /etc/X11/xorg.conf

In the first section I changed:

```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


```

to:
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "intel"
    Inactive "nvidia"
EndSection


```

Switching the target of "Screen 0" and "Inactive", is the important part here.

After a reboot, I logged in just fine. But when I went to the nvidia-settings, nvidia was set to active, but after setting intel be active, everything behaved just as expected.

Hope it does you some good. 

Cheers.

---

### Post by mc4man on 2015-10-19
This will allow the use of the _Unity greeter,_ if the greeter display is restored then the session will be fine.

If the autostart script was in place then disable

Alter the sleep time of unity-greeter from 300 to 4 (sec) in /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
(at bottom of file, assumes 4 sec is enough time to enter password, if not either increase a few seconds or just realize if greeter screen goes to sleep just move the cursor to re-awaken to complete desired task.

```
sudo -H gedit /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```

Ex. of section
 ```
   <key name="idle-timeout" type="i">
      <default>4</default>
      <summary>Number of seconds of inactivity before blanking the screen. Set to 0 to never timeout.</summary>

```
recompile schemas
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

Log out or restart, at black greeter screen wait at least 4 sec., then press a key or move cursor/mouse. (or wait for value set above in the .xml if not 4
The greeter screen will become visible - Quickly enter password & press enter while the screen is still visible. If screen goes dark awaken with mouse or touchpad.

Login session will have a visible display as expected

Note: Xubuntu & Lubuntu use a different greeter, no clue as how to alter the time to sleep for their greeter's

---

### Post by flocculant on 2015-10-20
don't have this issue - no -prime, but if it is the same issue as [lpbug]1507676[/lpbug] Nvidia-Prime not switching from intel to nvidia leading to a black screen - and it appears to be - then that's marked critical, alberto milone is looking at it and it's been talked about in #ubuntu-release this morning

---

### Post by aljosa2 on 2015-10-20
**Will 2015 finally be the year of the Linux desktop?**
> **flocculant said:**
> don't have this issue - no -prime, but if it is the same issue as [lpbug]1507676[/lpbug] Nvidia-Prime not switching from intel to nvidia leading to a black screen - and it appears to be - then that's marked critical, alberto milone is looking at it and it's been talked about in #ubuntu-release this morning

i am quite confused because when installing nvidia driver with nvidia-prime, inside nvidia-settings nvidia is already selected as default option, and *(today at the end of 2015)* that's exactly our problem for which a simple solution is switching *(somehow: one must be able to deal with the black screen of death)* to intel.

---

### Post by flocculant on 2015-10-20
> **aljosa2 said:**
> **Will 2015 finally be the year of the Linux desktop?**


i am quite confused because when installing nvidia driver with nvidia-prime, inside nvidia-settings nvidia is already selected as default option, and *(today at the end of 2015)* that's exactly our problem for which a simple solution is switching *(somehow: one must be able to deal with the black screen of death)* to intel.

I'm just putting information into this thread about a similar issue for those affected by this bug - where it is being looked at by someone who can do something

"<tseliot> flocculant: the package has been accepted into wily, so you might want to give it a try when it lands"

If you want to talk about the  'year of the linux desktop' meme - then take it to one of the 2 'chat' sub-forums, easy to find in the Discussions area - this area is not for that. Frankly I couldn't care less about meme's.

---

### Post by flocculant on 2015-10-20
Changelog for ubuntu-drivers-common

ubuntu-drivers-common (1:0.4.11) wily; urgency=medium

  * gpu-manager.c:
    - Rely on /var/log/syslog to get information about unloaded modules.
      This should minimise the current slowdown on boot (LP: #1307069).
    - Switch from intel to modesetting as the default driver on hybrid
      intel/nvidia systems because of a regression in the intel driver
      (LP: #1507676).

 -- Alberto Milone <alberto.milone@canonical.com>  Mon, 19 Oct 2015 17:35:12 +0200

---

### Post by mc4man on 2015-10-20
> **flocculant said:**
> don't have this issue - no -prime, but if it is the same issue as [lpbug]1507676[/lpbug] Nvidia-Prime not switching from intel to nvidia leading to a black screen - and it appears to be - then that's marked critical, alberto milone is looking at it and it's been talked about in #ubuntu-release this morning
That 'fixed' it though it **wasn't** that nvidia-prime wasn't switching to nvidia from intel, the nvidia drivers were loaded fine & obviously could be used, display or no display.
I could play videos using nvidia (vdpau) just fine even though they couldn't be seen.

Just more of the continuing lack of attention to the Desktop version.. & bugs,  ect.

Ot - a new build for wily of u-d-c for those that benefit from the reduced tearing will show in the tear free ppa shortly.

---

### Post by mr12 on 2015-10-21
Why not adding blank option into xorg.conf?
Too much easy for use it?

---

### Post by mc4man on 2015-10-21
> **mr12 said:**
> Why not adding blank option into xorg.conf?
Too much easy for use it?
Because it had no effect..

---

### Post by mr12 on 2015-10-22
> **mc4man said:**
> Because it had no effect..

My laptop, and others from IT forum users, can say "yes it works". (From 18/05/2015)
How do you think i use nvidia-prime on wily and 4.1.1 kernel? (mate+gdm)
Im not a magician.

The bug need only gdm/kdm/mdm(into mint latest build version) and the value in xorg.conf, im not interested in edit lightdm or unity schemes, because not all uses unity (i hate unity just for example)

---

### Post by mc4man on 2015-10-22
> **mr12 said:**
> My laptop, and others from IT forum users, can say "yes it works". (From 18/05/2015)
How do you think i use nvidia-prime on wily and 4.1.1 kernel? (mate+gdm)
Im not a magician.

The bug need only gdm/kdm/mdm(into mint latest build version) and the value in xorg.conf, im not interested in edit lightdm or unity schemes, because not all uses unity (i hate unity just for example)
As noted before this wasn't an issue with gdm & gnome session in the first place so an xorg edit or bug 'fix' is/was irrelevant.
Otherwise Ubuntu uses lightdm & most *bunt's were affected & use lightdm & lightdm greeters where an xorg edit was worthless 
As far as mate & kubuntu I could care less. 
Ciao

---

### Post by mr12 on 2015-10-22
> **mc4man said:**
> As noted before this wasn't an issue with gdm & gnome session in the first place so an xorg edit or bug 'fix' is/was irrelevant.
Otherwise Ubuntu uses lightdm & most *bunt's were affected & use lightdm & lightdm greeters where an xorg edit was worthless 
As far as mate & kubuntu I could care less. 
Ciao

That is not true...
I make many tests, lightdm not read the blank time settings, i tried to edit them many times not a change.
GDM instead works...
How can you say that you said if im using this method from many months ago? Its a fact.
And what you say to the guys that used with success my method? Open your eyes and your mind...

---

### Post by mc4man on 2015-10-22
> **mr12 said:**
> That is not true...
I make many tests, lightdm not read the blank time settings, i tried to edit them many times not a change.
GDM instead works...
How can you say that you said if im using this method from many months ago? Its a fact.
And what you say to the guys that used with success my method? Open your eyes and your mind...
Take some reading lessons then get back...

---

### Post by mr12 on 2015-10-23
> **mc4man said:**
> Take some reading lessons then get back...

likewise you, then read that topic.

---

### Post by cariboo on 2015-10-23
The way this is going, I might as well close this thread, and mc4man can start a new thread updated to Xenial. Thread closed.

---

