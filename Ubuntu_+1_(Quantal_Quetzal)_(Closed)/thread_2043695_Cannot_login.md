---
title: "Cannot login"
date: 2012-08-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by chrismine on 2012-08-17
I did some updates this morning - now I cannot login to Quantol anymore.

I get the login screen with my username and the when I input my password it briefly flash my desktop background and goes back to the login screen.

Have somebody also experience this and can somebody help with a possible fix?

Thanks.

---

### Post by Deepak J on 2012-08-17
Even I had experienced the same once. But when I restarted ma syst, everything was fine.

---

### Post by chrismine on 2012-08-17
I did restart a few times already, not even a guest account works...

---

### Post by dino99 on 2012-08-17
get issue here on i386 and 3.5 kernel with nouveau driver: even cant see lightdm greeter for logging (but can blindly enter the password !!!) as i get strange rgb window. 

Booting in recovery with 3.6 kernel i'm getting drm errors

---

### Post by mc4man on 2012-08-17
If you are using nvidia-current then you may have updated xserver to the 1.13 version which is now in main repo.
If so then you will not be able to log in to a ubuntu (3d) session

If you don't have an available 2d session, *Classic (no effects), then either find a way to install it, or remove nvidia-current or downgrade to the previous xserver 1.12 packages (removing nvidia-current may prove easiest

Additionally in the proposed repo are new libglib packages that _could_ cause all sorts of issues if upgraded to, I'd be careful of those

---

### Post by chrismine on 2012-08-17
Thank you mc4man

I purged the nvidia-current driver and back into a working desktop with nouveau driver.

---

### Post by mc4man on 2012-08-17
If your gpu is the one in your sig (Nvidia8600GT GPU), & you find that nouveau has tearing on the Desktop you probably could enable vsync in nouveau. 
(I do so here with a 8400m & it makes quite a difference. 

referring report I have, comment 2 mentions limitations hardware wise.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131)

To do so you create (or replace what's in a current one) an /etc/X11/xorg.conf with 
```
Section "Device"
        Identifier "My Graphics"
        Driver "nouveau"
        Option "GLXVBlank" "on"
EndSection
```

---

### Post by chrismine on 2012-08-17
Thanks for that, added it to xorg.conf which was blank...

BTW this is the first time ever that nouveau worked on my setup...

---

### Post by mc4man on 2012-08-17
> **chrismine said:**
> 

BTW this is the first time ever that nouveau worked on my setup...
Same here - well,  it's worked previously but not worth using. 12.10 is the 1st time it's done fairly well, & in some area's particular to my laptop it's better than nvidia, though it's not as good at smooth scrolling in FF

edit - to see any vsync improvement you do need to restart

---

### Post by chrismine on 2012-08-17
I find the nvidia driver snappier with beter quality rendering on my system. Nouveau not as smooth but it is usable at least....

---

### Post by stinkeye on 2012-08-17
> **mc4man said:**
> If your gpu is the one in your sig (Nvidia8600GT GPU), & you find that nouveau has tearing on the Desktop you probably could enable vsync in nouveau. 
(I do so here with a 8400m & it makes quite a difference. 

referring report I have, comment 2 mentions limitations hardware wise.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1019131)

To do so you create (or replace what's in a current one) an /etc/X11/xorg.conf with 
```
Section "Device"
        Identifier "My Graphics"
        Driver "nouveau"
        Option "GLXVBlank" "on"
EndSection
```

I am using GeForce 9400 GT, changing to nouveau drivers and creating xorg.conf allows me to login but graphics are stuffed.
Low resolution, flickering and window remnants all over the place.

---

### Post by mc4man on 2012-08-17
> **stinkeye said:**
> I am using GeForce 9400 GT, changing to nouveau drivers and creating xorg.conf allows me to login but graphics are stuffed.
Low resolution, flickering and window remnants all over the place.
I'm not up on the chipset names, the nouveau fellow said that 'fermi' & later do Not support vsync thru nouveau. I'd try without the xorg.conf

(- the main reason I'm using nouveau here, xserver version aside, is on this particular chipset/mobo compiz Always gets slightly stuffed every session at some point, be it scrolling, context menus opening slower, rotate getting a 'hitch', whatever. Got sick of it & nouveau works well for use case.
Plus the reaction time for upclocking on compiz actions slowed down a bit, forcing me to disable powermizer.

The best driver for this chip was the 195.XX which is long gone & that may have been more because compiz was at 0.8.x

---

### Post by stinkeye on 2012-08-17
> **mc4man said:**
> I'm not up on the chipset names, the nouveau fellow said that 'fermi' & later do Not support vsync thru nouveau. I'd try without the xorg.conf

(- the main reason I'm using nouveau here, xserver version aside, is on this particular chipset/mobo compiz Always gets slightly stuffed every session at some point, be it scrolling, context menus opening slower, rotate getting a 'hitch', whatever. Got sick of it & nouveau works well for use case.
Plus the reaction time for upclocking on compiz actions slowed down a bit, forcing me to disable powermizer.

The best driver for this chip was the 195.XX which is long gone & that may have been more because compiz was at 0.8.x

Thanks. Think I'll leave this to better minds and retreat back to my 12.04
install until it's sorted.

---

### Post by effenberg0x0 on 2012-08-17
(This is probably a dumb question)

Why would they move the new xserver from proposed to main if it's sort of very clear it will lock nvidia-current (and users that installed nvidia from the proprietary installer) out of a usable desktop? I think I still don't understand what proposed is for then.

Regards,
Effenberg

---

### Post by Sworddragon on 2012-08-17
For all who wants to have a working desktop with nvidia-current:

> **Sworddragon said:**
> The XServer 1.12.99 packages are now in the main repository and doing the troubles as explained here. I have now tried some things a few hours to find a solution and the best that I could find was to downgrade the xserver-xorg-*, nvidia-*, linux-image-* and linux-headers-* packages to the Precise version.


This is my /etc/apt/preferences:

```
Package: linux-headers-*
Pin: release v=12.04, l=Ubuntu
Pin-Priority: 1001

Package: linux-image-*
Pin: release v=12.04, l=Ubuntu
Pin-Priority: 1001

Package: nvidia-*
Pin: release v=12.04, l=Ubuntu
Pin-Priority: 1001

Package: xserver-*
Pin: release v=12.04, l=Ubuntu
Pin-Priority: 1001

```

---

### Post by cariboo on 2012-08-17
> **effenberg0x0 said:**
> (This is probably a dumb question)

Why would they move the new xserver from proposed to main if it's sort of very clear it will lock nvidia-current (and users that installed nvidia from the proprietary installer) out of a usable desktop? I think I still don't understand what proposed is for then.

Regards,
Effenberg

My feeling is that in order to make all the proposed changes to Quantal, the developers can't wait for the proprietary driver producers to catch up. Eventually they will produce drivers that work with this version of Xorg.

On my system the nouveau drivers work quite well except for not allowing me to set my preferred resolution (1920X1080), I'm stuck at 1600X1050, but I can put up with that until the proprietary drivers finally arrive. Even GPU temps have come down quite a bit, from running in the mid 50's, they are now in the mid to high 40's.

---

### Post by mc4man on 2012-08-17
> **effenberg0x0 said:**
> (This is probably a dumb question)

Why would they move the new xserver from proposed to main if it's sort of very clear it will lock nvidia-current (and users that installed nvidia from the proprietary installer) out of a usable desktop? I think I still don't understand what proposed is for then.

Regards,
Effenberg
There was some explanation many wk.'s ago  about some of the reasons to use proposed during the dev cycle. 
I didn't pay that close attention other than there could be packages you wouldn't want to install. (or is this case what some wouldn't want to.

As far as I remember proposed generally didn't start during dev until the last 3-4 weeks & then would continue post release, *actually more interest here in proposed post release then early next dev cycle.

This time is obviously different, for another example  there is now some glib packages in proposed., 
(I did & it didn't seem to go well though it was also at the same moment as a poor file-roller package...
Edit - the glib packages are ok to upgrade, seems to have been in combo with a bad file-roller package that was killing g-s-d

As far as moving xorg out to main what cariboo907 said sounds reasonable.

---

### Post by effenberg0x0 on 2012-08-17
Sworddragon: I agree pinning to the latest working config is a smart move. I do it with some packages, like Thunderbird.

Cariboo: Thanks for the explanation, I believe you're correct. I'm not sure I agree with it, but there's nothing to do about it. One problem though: The proprietary installer blacklists nouveau/nvidia-current. After updating, it's easy to get locked out (which can be a little confusing for some users).

Regards,
Effenberg

---

### Post by kurt18947 on 2012-08-17
It was certainly useful to have gnome-classic (no effects).  I'm thinking of those at Gnome who have talked about removing gnome-classic as unnecessary.  This fix could have been done from the command line but if Gnome is truly thinking of new users, not being able to get to a GUI is not newbie/ordinary user friendly.  Yes I know this occurred in a developmental release but keeping a basic GUI seems like a wise idea if you're trying to appeal to the non-technical user.

Thinking this was a password problem, I dropped to a root shell and tried to reset my passwords.  I kept getting a message 
> authentication token manipulation error  I would never have guessed this was due to an video system problem.  I'm glad I didn't discover this tomorrow with the forum offline.

---

### Post by Cavsfan on 2012-08-18
I'm in the same boat. All was fine until the xorg update yesterday morning. It would not boot period.
I spent half the day downloading and trying to install the daily iso and it would not even work.
Downloaded it from 2 sources and md5sum checked OK but, neither would boot.
Finally downloaded the alpha 3, which I had overwritten (DVD-RW) with the daily iso.
Got all the updates still without an nvidia driver. I can't install any of nvidia's drivers.
There is the dependency issue between xorg and the nvidia drivers.

If I install the grub on Quantal the mouse works, but if I install it on my preferred os Lucid the mouse does not move in Quantal.

Like stinkeye said, I think I'll get into Precise or Lucid until they get this sorted out.
What a huge waste of time. *sigh*

---

### Post by effenberg0x0 on 2012-08-18
I have managed to downgrade successfully. There are many ways to do it. We have threads about it here and they are starting to pop at other distros boards. Here's what I did:

- I created a directory in /tmp to hold X debs:
```
mkdir /tmp/ubuntu-proposed-mess

```
- Downloaded PP **xserver-xorg** and **xserver-xorg-common** **precise** debs and saved them to /tmp/ubuntu-proposed-mess/. 
> [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)**precise**/amd64/xserver-common
[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)**precise**/amd64/xserver-xorg-core
- Installed the debs:
```
cd /tmp/ubuntu-proposed-mess
sudo dpkg -i *.deb 

```
At this point, you voluntarily got to a broken deps status and you gotta fix it. There are two solutions: Upgrading the two packages you just downloaded, which would take you back to the previous no-desktop situation or downgrading all packages that depend/rdepend on the two debs you installed. That's what something like aptitude --full-resolver will tell you. You want the second one. 

The best way to do it is to use /etc/apt/preferences to pin these packages versions. Other users have recommended this here. You can also dpkg-query these two packages and get their list of depends/rdepends and download this debs or even use apt-get install package=<version>.

But I was tired and, considering I had a working "Ubuntu Classic (no effects)" session working, I just started it and used Synaptic.
- Pinned the two packages (Package / Lock Version)
- Added PP repos (settings / repositories)
- Settings / Preferences / Distribution / "Prefer Versions from" = "Precise"
- Reloaded packages data (reload button)
- Edit / Fix Broken Packages
- Mark All upgrades button
- Closed synaptic
- Checked sources.list/sources.list.d to make sure all was standard/default, no PP repos and alternative PPAs.
- Checked /etc/modprobe.d/* to make sure nouveau was blacklisted / aliased to trash and nvidia was not.
- Stopped lightdm (sudo service lightdm stop)
- Removed /etc/X11/xorg.conf I was playing with when testing nouveau.
- Re-installed Nvidia 304.37 using the Nvidia binary installer from [ftp://download.nvidia.com/XFree86/Linux-x86_64/304.37/](ftp://download.nvidia.com/XFree86/Linux-x86_64/304.37/). 
- Rebooted. compiz profile was messed up (no unityshell, etc). 
- Resetted Unity. All fine.

After that I tested the PC a little to make sure it was usable for OpenGL, vdpau, etc (it is), checked my "*xorg*" packages versions (via dpkg-query), added them to /etc/apt/preferences (pin) and did a normal apt update&&upgrade.

Regards,
Effenberg

---

### Post by ventrical on 2012-08-18
Just updated one install here and first thing I notice is that all the user_name accounts I created are  now ((null)).

Fun!:)

reboot now !

---

### Post by mc4man on 2012-08-18
For ease of downgrading xserver packages one can first remove all the unneeded ones which is the majority of them 
Then just gather the few actually needed from launchpad, easy to find if you search the exact name which is available in synaptic > the changelogs, or if using synaptic (best), to manage updates/upgrades from it's history
Ex. 
xserver-xorg-core_1.12.1.902 - 
[https://launchpad.net/ubuntu/+source/xorg-server/2:1.12.1.902-1ubuntu1](https://launchpad.net/ubuntu/+source/xorg-server/2:1.12.1.902-1ubuntu1)

xserver-xorg-input-evdev_2.7.0-0ubuntu2
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.7.0-0ubuntu2](https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.7.0-0ubuntu2)
ect,

---

### Post by ventrical on 2012-08-18
I had major problems with that update. Had to use GRUB to get to root to <login> to terminal. I then reinstalled nouveau-firmware (nividia-current just isn't working) and now I have my fvwm-crystal desktop.

 I'm looking over some of the suggestions now. One good thing about semi-borking an install is that it is never entirely lost if you have another stable on the same drive train or system as all those files are easily brought up with Thunar of even Nautilus through Samba I believe.

 I have an 800/600 screen .. :) reminds me of the old days :)

---

### Post by effenberg0x0 on 2012-08-18
> **ventrical said:**
> I had major problems with that update. Had to use GRUB to get to root to <login> to terminal. I then reinstalled nouveau-firmware (nividia-current just isn't working) and now I have my fvwm-crystal desktop.

 I'm looking over some of the suggestions now. One good thing about semi-borking an install is that it is never entirely lost if you have another stable on the same drive train or system as all those files are easily brought up with Thunar of even Nautilus through Samba I believe.

I have an 800/600 screen .. :) reminds me of the old days :)

I got really frustrated with this update yesterday. I use two 24" 1900x1200 monitors. After rebooting I had 2 options: 1 was nvidia-current, working extended desktop, 1900x1200 resolution on both (up to lightdm) but no working DE (useless). 2 was Nouveau, "mirroring" (no extended desktop) which is also useless, 600x480 and a sort-of-working (really unstable) gnome-classic. I think I tried just about any possible tweak to xorg.conf with nouveau, from 0am to 6am, with no luck. Then I decided to downgrade... I must admit that borking a install to that extent and having to invest time to fix it, feeling clueless, was not fun. Maybe if I were a new tester I would just give up after this.

Regards,
Effenberg

EDIT: Oh, and llvmpipe my llvm-a**. The only thing I haven't tried to make llvmpipe work was begging.

---

### Post by effenberg0x0 on 2012-08-18
Double posting... There's something new (and wrong) with SSO now. Yey.

---

### Post by DougieFresh4U on 2012-08-19
Well using ATI Radeon HD3200, have not seen any one 
mention having the 'not able to login' all seem to 
talk of using NVIDIA.
Well I am stuck in the 'boot loop', keeps bringing me 
back to login screen. I am able to use 'guest' login.

---

### Post by effenberg0x0 on 2012-08-19
> **DougieFresh4U said:**
> Well using ATI Radeon HD3200, have not seen any one 
mention having the 'not able to login' all seem to 
talk of using NVIDIA.
Well I am stuck in the 'boot loop', keeps bringing me 
back to login screen. I am able to use 'guest' login.

HI,
Yes, most of the talk is about Nvidia right now. What you're experiencing is another problem. What do you get on logs when it loops back to lightdm? 

Check /var/log/Xorg.0.log, /var/log/kern.log, ~/.xsession-errors and see if you can spot something interesting / out of the ordinary in this logs. Post it here so we can discuss it.

Tip: I'll guess that, if this is not VGA related (the guest account works), you can probably create a new user and login normally with it. You can do it via Grub/Recovery, choose to drop to a root shell, remount it RW (mount -o remount,rw /), add the test user (adduser test-user), reboot (reboot now) and login with it. Give it a try. 

As a side note: In previous cycles a very similar problem was fixed by removing ~/.Xauthority and/or ~/.ICEauthority (mv ~/.Xauthority ~/.Xauthority.backup && mv ~/.ICEauthority ~/.ICEauthority.backup, Ctrl+Alt+F1, login, sudo service lightdm stop, sudo service lightdm start). I don't it still is an issue but wouldn't hurt to test it.

Regards,
Effenberg

---

### Post by Cavsfan on 2012-08-19
I *did* have my installation running pretty smoothly without a nvidia driver installed at all - 1920x1200 res.
I installed some other stuff and when I rebooted, the screen was garbage.
There was no way to anything. I had to press the reset button on my pc.

What is amazing is that it was working so well, I thought even better than Precise until this happened.

Just glad I have Lucid, Precise and windows 7 to fall back on. Hopefully, something will be done to resolve this as I refuse to downgrade any packages or any of that.

---

### Post by 3vi1 on 2012-08-19
I too am stuck in the login loop.  None of the desktops (Unity, Gnome, KDE...) work, with the exception of LXDE.

I'm using an nvidia card here - but updated nvidia-current to the version from xorg-edgers (before that, lightdm would continually try to start and fail).

I've tried removing .ICEAuthority and the other standard files... but nothing seems to help.

Logging in to other accounts, including Guest, also fails.

I'm seeing stuff like this in .xsession-errors.old

```
Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed at /usr/lib/perl5/Gtk2.pm line 138.
Gtk-CRITICAL **: IA__gtk_icon_theme_prepend_search_path: assertion `GTK_IS_ICON_THEME (icon_theme)' failed at /usr/lib/perl5/Gtk2.pm line 138.

```

Though, that can't be the *real* problem, since KDE doesn't work either.

Looks like I'm going to be getting acquainted with LXDE for a while.

---

### Post by Bowmore on 2012-08-19
> **Cavsfan said:**
> I *did* have my installation running pretty smoothly without a nvidia driver installed at all - 1920x1200 res.
I installed some other stuff and when I rebooted, the screen was garbage.
There was no way to anything. I had to press the reset button on my pc.It's probably the same issue that I have seen with the 3.5.0-10 kernel.

To me one workaround was to use an older kernel, e.g 3.5.0-9.

Another workaround is to activate the Ctrl-Alt-Backspace using e.g 3.5.0-9 to be able to logout from the garbage when using 3.5.0-10 or later incl 3.6.0 kernel. After a relogin everything works fine here for the 3.5.0-10 kernel during that session. If you don't have autologin enabled just write your password and press Enter. Then if still garbage press Ctrl-Alt-Backspace and you should come to a normal login screen.

This issue seems to be a DRM issue (logged as PFIFO_CACHE_ERROR) for the nouveau driver so will report that as a bug if 3.5.0-11 does not fix it which it probably won't as I don't think it's a kernel issue but rather a libdrm one, i.e libdrm-nouveau2.

---

### Post by Cavsfan on 2012-08-19
> **Bowmore said:**
> It's probably the same issue that I have seen with the 3.5.0-10 kernel.

To me one workaround was to use an older kernel, e.g 3.5.0-9.

Another workaround is to activate the Ctrl-Alt-Backspace using e.g 3.5.0-9 to be able to logout from the garbage when using 3.5.0-10 or later incl 3.6.0 kernel. After a relogin everything works fine here for the 3.5.0-10 kernel during that session. If you don't have autologin enabled just write your password and press Enter. Then if still garbage press Ctrl-Alt-Backspace and you should come to a normal login screen.

This issue seems to be a DRM issue (logged as PFIFO_CACHE_ERROR) for the nouveau driver so will report that as a bug if 3.5.0-11 does not fix it which it probably won't as I don't think it's a kernel issue but rather a libdrm one, i.e libdrm-nouveau2.

I just clean installed alpha 3 yesterday and have kernel 3.5.0-6 and I believe 3.5.0-10. Although I am not sure.
I'll try that, if I can get into recovery as regular Quantal is way beyond help as it is.
Thanks

---

### Post by Cavsfan on 2012-08-19
Whoa! This is weird! I am logged into Quantal just fine w/o any video driver whatsoever. I didn't install the nvidia or I mean I can't due to dependency issues.
I did not install the nouveau driver either.
I have a conky installed and for the nvidia driver, the version it is just blank. :confused:

I hope they fix this pretty quick. It shows 3 security updates on one conky.
Let's see what happens...

---

### Post by VinDSL on 2012-08-19
Guess I got lucky...

All I did was install (downgrade to):

[INDENT]xserver-xorg-core_1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise_i386.deb[/INDENT]

SOURCE:  [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xorg-server/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xorg-server/)

I didn't touch anything else, but I can now log into Unity & GS just fine.  Firefox & Thunderbird work, too.

Of course, this doesn't come without a small cost...

Synaptic, for instance, *thinks* the xorg package is broken, because it cannot resolve certain dependencies.  Thus, it won't let you update any packages.  LoL!

The package update workaround is:

[LIST]
[*]"Upgrade" the xserver-core to 1.13 (currently 2:1.12.99.904-1).  This will make Synaptic happy.
[*]Login via LXDE (or probably any non-Unity/GS DE)
[*]Upgrade your packages (I use Synapic & apt-get)
[*]"Downgrade" the xserver-core to 1.12
[*]Now you can login to Unity/GS, fully updated
[/LIST]

Heh!  Hope that makes sense.  It's a rather hackish solution...  :)

---

### Post by ventrical on 2012-08-20
> **effenberg0x0 said:**
> I got really frustrated with this update yesterday. I use two 24" 1900x1200 monitors. After rebooting I had 2 options: 1 was nvidia-current, working extended desktop, 1900x1200 resolution on both (up to lightdm) but no working DE (useless). 2 was Nouveau, "mirroring" (no extended desktop) which is also useless, 600x480 and a sort-of-working (really unstable) gnome-classic. I think I tried just about any possible tweak to xorg.conf with nouveau, from 0am to 6am, with no luck. Then I decided to downgrade... I must admit that borking a install to that extent and having to invest time to fix it, feeling clueless, was not fun. Maybe if I were a new tester I would just give up after this.

Regards,
Effenberg

EDIT: Oh, and llvmpipe my llvm-a**. The only thing I haven't tried to make llvmpipe work was begging.

I  had been noticing that you have been spending a lot of time on these problems.   Yeah .. a lot of new testers *would* give up perhaps but it is a great learning experience for others. It also inspires us to try different methods on work-arounds , all for the better good of Ubuntu.

Me? .. been so busy... but yes .. it is just so aggravating (nvidia/xserver scramble). I must admit that these kinds of bugs can take a little joy out of testing. I noticed that even the xsafe graphics mode would not work from GRUB. The screen comes up but there is no mouse - so that is useless in the current situation.

  A new guy not familiar with terminal code would really be frustrated, probably move on elsewhere.

whoops .. I'm off topic again :)

---

### Post by Harry33 on 2012-08-20
> **VinDSL said:**
> Guess I got lucky...
...
Synaptic, for instance, *thinks* the xorg package is broken, because it cannot resolve certain dependencies.  Thus, it won't let you update any packages.  LoL!
...

Heh!  Hope that makes sense.  It's a rather hackish solution...  :)

Synaptic is correct.

If you like, you can very well just remove the xserver meta packages and get rid of all the trouble there:
- xorg
- xserver-xorg-input-all
- xserver-xorg-video-all
And after that, just remove all unnecessray input and video drivers.

The package xserver-xorg is needed for X to start, though.

For example a desktop setup with nvidia-current only needs to have these drivers:
- xserver-xorg-input-evdev
- xserver-xorg-video-vesa
- nvidia-current

:guitar:

---

### Post by VinDSL on 2012-08-20
> **Harry33 said:**
> Synaptic is correct.[...]
That's a hard one to quantify -- a grey area -- but, let's go ahead and say Synaptic is correct.  After all, it's better to be "safe" than "sorry".  ;)

I digress (for purposes of illustration) ...

I was showing *effenberg* a stylistic trick yesterday -- a quick n' dirty way of skinning TB using a certain combination of custom theme components.

The author of one of the themes states:

> **Important note**: This theme is designed around Gnome 3.4 and the 1.0.2 version of the Unico engine. I do not work with any development releases. This theme will break in Gnome 3.5.


Technically, he is correct too -- as "correct" as Synaptic is, in the example above -- but, all I am using in Ubu 12.10 is that themes' window decorations/colors, which work just fine, regardless of the author's opinion of dev releases.  :D

Back on topic...

The larger point is, swapping out the xserver-xorg-core (by itself) takes care of the immediate problem.**[COLOR="DarkRed"]*[/COLOR]** 

[INDENT]**[COLOR="DarkRed"]* _WARNING_[/COLOR]:** Please, don't mix n' match packages, unless you know what you're doing![/INDENT]

> "Whatever gets you through the night 'salright, 'salright [...]

Do it wrong or do it right 'salright, 'salright," [...]

Trust me darlin' come on listen to me, come on listen to me
Come on listen, listen

~John Lennon

SOURCE:  [https://www.youtube.com/watch?v=HNNxeovdN5U](https://www.youtube.com/watch?v=HNNxeovdN5U)

---

### Post by DougieFresh4U on 2012-08-20
> **effenberg0x0 said:**
> HI,
Regards,
Effenberg

Sorry for not getting back yesterday.
I ran updates yesterday and no luck. I ran updates again today, kept getting a lot of I/O errors but all updates ran. Rebooted as at has always in the past. I do not know what the issue was but I am back to 'normal' if that's what it's called :p.
My problem is solved!!
Thanks for your input.

---

### Post by Cavsfan on 2012-08-20
> **VinDSL said:**
> Guess I got lucky...

All I did was install (downgrade to):[INDENT]xserver-xorg-core_1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise_i386.deb[/INDENT]SOURCE:  [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xorg-server/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xorg-server/)

I didn't touch anything else, but I can now log into Unity & GS just fine.  Firefox & Thunderbird work, too.

Of course, this doesn't come without a small cost...

Synaptic, for instance, *thinks* the xorg package is broken, because it cannot resolve certain dependencies.  Thus, it won't let you update any packages.  LoL!

The package update workaround is:

[LIST]
[*]"Upgrade" the xserver-core to 1.13 (currently 2:1.12.99.904-1).  This will make Synaptic happy.
[*]Login via LXDE (or probably any non-Unity/GS DE)
[*]Upgrade your packages (I use Synapic & apt-get)
[*]"Downgrade" the xserver-core to 1.12
[*]Now you can login to Unity/GS, fully updated
[/LIST]

Heh!  Hope that makes sense.  It's a rather hackish solution...  :)

One dumb question: How do I downgrade that thing? If I try to remove the 2:1.12.99.904-0ubuntu1 version it wants to rip out ubuntu-desktop, xorg, xorg-server, etc.
I've got the xserver-common_1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise_all.deb and can install it with Ubuntu Software Center but, it currently says I have a later version installed.

I currently have no nvidia driver installed, but am still somehow able to login.

---

### Post by mc4man on 2012-08-20
> **Cavsfan said:**
> 

I currently have no nvidia driver installed, but am still somehow able to login.
Then why do you want to downgrade xserver?

Just to mention:
It not a waste of time to learn how to downgrade packages properly when running a dev, and in the 'special' case of Xorg to know which xserver packages you need & which can be safely removed.
That way, (if you remove all the needed packages first), you only have a couple to downgrade.

The idea of having to use precise packages is wrong & in the case of causing broken packages - why bother

This issue will likely be resolved shortly anyway - that still doesn't excuse some of the poor advice in this thread

---

### Post by Cavsfan on 2012-08-20
> **mc4man said:**
> Then why do you want to downgrade xserver?

Just to mention:
It not a waste of time to learn how to downgrade packages properly when running a dev, and in the 'special' case of Xorg to know which xserver packages you need & which can be safely removed.
That way, (if you remove all the needed packages first), you only have a couple to downgrade.

The idea of having to use precise packages is wrong & in the case of causing broken packages - why bother

This issue will likely be resolved shortly anyway - that still doesn't excuse some of the poor advice in this thread

As I was on my daily walk, I realized it is probably some flag on apt-get purge to take out just one file.
But, you are right - why bother. 
I think I'll just wait it out. :)
Thanks!

---

### Post by Cavsfan on 2012-08-20
I have flash,  java, can watch youtube videos. Who needs a video driver. ;)

---

### Post by VinDSL on 2012-08-20
> **Cavsfan said:**
> One dumb question: How do I downgrade that thing?
I do it from a terminal.  

Matter of fact, I just upgraded my packages using Synaptic (which requires installing xserver 1.13 to resolve dependencies) 

After the upgrades were completed, I downgraded xserver -> 1.12 via CLI.

xserver 1.12 is located (all by itself) in my ~/Downloads/Xorg folder.

So, all I did was navigate to that folder and use dpkg to install it.

```
vindsl@Zuul:~$ cd Downloads/Xorg
vindsl@Zuul:~/Downloads/Xorg$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
**[COLOR="DarkRed"]dpkg: warning: downgrading xserver-xorg-core from 2:1.12.99.904-0ubuntu1 to 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise[/COLOR]**
(Reading database ... 386372 files and directories currently installed.)
Preparing to replace xserver-xorg-core 2:1.12.99.904-0ubuntu1 (using xserver-xorg-core_1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Setting up xserver-xorg-core (2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise) ...
Processing triggers for man-db ...
vindsl@Zuul:~/Downloads/Xorg$
```

Er...

As mc4man said, there is some poor advice in this thread, so I'll try to give you some good advice.

If you're uncomfortable doing the above, don't do it.  Wait for the "fix".

This isn't a good situation to be practicing your command lines skills ...  ;)

---

### Post by Sworddragon on 2012-08-20
> **VinDSL said:**
> As mc4man said, there is some poor advice in this thread, so I'll try to give you some good advice.

Not poor but maybe not the perfect solution (if you point to my post). Don't forget to post how to pin the package on your solution otherwise a dist-upgrade would cause the problem again.

---

### Post by ventrical on 2012-08-20
> **Harry33 said:**
> Synaptic is correct.

If you like, you can very well just remove the xserver meta packages and get rid of all the trouble there:
- xorg
- xserver-xorg
- xserver-xorg-input-all
- xserver-xorg-video-all
And after that, just remove all unnecessray input and video drivers.

For example a desktop setup with nvidia-current only needs to have these drivers:
- xserver-xorg-input-evdev
- xserver-xorg-video-vesa
- nvidia-current

:guitar:

 I tried this .. then downloaded the xserver1.12 (as VinDSL suggested) opened it, it went through all it's unpak and now I can only get root from GRUB ! I used to be able to login from root and run lightdm to a workable desktop  but now it says it can't read/write after I login from root and I can't sudo apt-get nothing!

 My apologies .. but what is the command again for mounting?

'Hi ho Silver ?   jk .. :)

*edit*

btw .. it's not an absolute priority as I was able to migrate all of my important files. I would just like to see if I could get it back to a workable dekstop.

*edit*

Also , the 'network' optioin from GRUB recovery will not mount the filesystem.

thanks in advance..

---

### Post by Cavsfan on 2012-08-20
This is my screen without any video driver. The fonts on the Crunchbang conky are messed up but, other than that everything is pretty functional.

I am not afraid to downgrade the xorg-server-core but, do I really need to when I have a working system?

Thanks for providing the instructions **VinDSL**. I will definetely note that. You don't have to tell me twice how to do things.

[[IMG]http://thumbnails79.imagebam.com/20684/3f38d3206832385.jpg[/IMG]](http://www.imagebam.com/image/3f38d3206832385)

Where I would run into trouble is if I mess with CCSM, but I am not touching that!
I am hoping they get this resolved fairly quick as there has to be a lot of people out there with the same issues.

I think I'll just hang with what I have for now. ;)

---

### Post by VinDSL on 2012-08-20
> **Sworddragon said:**
> Don't forget to post how to pin the package on your solution otherwise a dist-upgrade would cause the problem again.
Oh, my!  What a tangled web we weave...  :D

Given the exigencies of this temporary hack (let's just call it what it is), you cannot pin xserver-xorg-core.

Well, you can pin it, but... If you do so, you cannot correct the "broken package", so called, and do updates.

Plus, you must make sure to ONLY fix the "broken" xserver-xorg-core component.  Don't fix the other *supposed* "broken packages".

Put another way, all you want to change is xserver-xorg-core, by switching back n' forth between 1.12 & 1.13.  Everything else will take care of itself.

Heh!  I never should have posted this hack, but you cannot un-ring a bell, once it's been rung.

Lesson learned...

---

### Post by xeizo on 2012-08-20
I continue to run Xorg 1.13 as well, but switched to Xubuntu, it deosn't look bad at all imho and gaming became smoother(the 3D graphics card needs no resources for a 3D desktop in the background, only for the current game):

[IMG]http://xeizo.com/blogg/wp-content/uploads/2012/08/xubuntu-2012-08-20-185938-1024x576.png[/IMG]
[http://xeizo.com/blogg/wp-content/uploads/2012/08/xubuntu-2012-08-20-185938.png](http://xeizo.com/blogg/wp-content/uploads/2012/08/xubuntu-2012-08-20-185938.png)

As it feels right now I will stick with Xubuntu for a while :guitar:

---

### Post by Cavsfan on 2012-08-20
> **VinDSL said:**
> Oh, my!  What a tangled web we weave...  :D

Given the exigencies of this temporary hack (let's just call it what it is), you cannot pin xserver-xorg-core.

Well, you can pin it, but... If you do so, you cannot correct the "broken package", so called, and do updates.

Plus, you must make sure to ONLY fix the "broken" xserver-xorg-core component.  Don't fix the other *supposed* "broken packages".

Put another way, all you want to change is xserver-xorg-core, by switching back n' forth between 1.12 & 1.13.  Everything else will take care of itself.

Heh!  I never should have posted this hack, but you cannot un-ring a bell, once it's been rung.

Lesson learned...

LOL! You can please some of the people some of the....
Any way, let's just say I downgrade xserver-xorg-core as you've explained. Then I install nvidia-current or nvidia-current-updates right?
Does it matter which one? Downgrading that file will let this happen correct?
Then I just get updates and xserver-xorg-core gets updated to the latest.
End of story right?
Then I live happily ever after? :p

---

### Post by Cavsfan on 2012-08-20
So, I couldn't help myself and went ahead and downgraded **xserver-xorg-core** and tried to install **nvidia-current-updates**.
Still got an error:

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install nvidia-current-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 nvidia-current-updates : Depends: dkms but it is not going to be installed
                          Depends: xorg-video-abi-11 but it is not installable or
                                   xorg-video-abi-12 but it is not installable
 xserver-xorg-core : Depends: xserver-common (>= 2:1.12.99.904-0ubuntu1) but 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```So, now it's telling me **xserver-common** is the incorrect version. :confused:
Gee, I guess there just is no happily ever after for me. ;)

---

### Post by ventrical on 2012-08-20
This depends problem is a real *destroyer*. Just about lost yet another install!!! The only way to recover was to:

sudo apt-get remove nvidia-current

then

sudo lightdm start

 And I am now logged in successfully to Gnome with (no effects).

Todays updates held back a nvidia-current update so mabey there lies the problem!?

I'm not one for playing it safe but if you are using quantal as a regular then be forwarned about these fixes as they can crack your DE.

---

### Post by fluteflute on 2012-08-20
Given that I don't mind whether I am using open source of proprietary drivers, can someone tell me how to restore access to Unity?

[I don't mind waiting a few days, and updating, if that's the easiest method.]

---

### Post by Cavsfan on 2012-08-20
> **ventrical said:**
> I'm not one for playing it safe but if you are using quantal as a regular then be forwarned about these fixes as they can crack your DE.

That is why I dual boot or now I am quad booting. 
I fixed the problem and update xorg-xserver-core. I also got several updates Firefox etc.

Then I tried to install nvidia-current-updates and got a different error:
```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install nvidia-current-updates
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current-updates : Depends: xorg-video-abi-11 but it is not installable or
                                   xorg-video-abi-12 but it is not installable
E: Unable to correct problems, you have held broken packages.
```I am not jacking with this any more. If the correct updates don't come down the pipe I'll just wait until the beta comes out.
Hopefully it will be fixed by then.

---

### Post by ronacc on 2012-08-20
this update cycle has been worse for me than any since edgy eft . I have 2 installs . one updated from precise and one from the daily's ( replaced every few days ) they act very different , the updated precise is reasonably stable the install from daily is a crap shoot . The last few daily's I cant even install because they die during boot from the dvd  but so far the 2 installs ( updated daily) at least make it to DT ( haven't updated today yet ) I have nouveau on both so I may get away with it . I sure hope the devs give us atleast a week to put the RC through its paces or we may stampede right off a cliff .

---

### Post by ventrical on 2012-08-20
> **Cavsfan said:**
> That is why I dual boot or now I am quad booting. 
I fixed the problem and update xorg-xserver-core. I also got several updates Firefox etc.

Then I tried to install nvidia-current-updates and got a different error:
```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install nvidia-current-updates
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current-updates : Depends: xorg-video-abi-11 but it is not installable or
                                   xorg-video-abi-12 but it is not installable
E: Unable to correct problems, you have held broken packages.
```I am not jacking with this any more. If the correct updates don't come down the pipe I'll just wait until the beta comes out.
Hopefully it will be fixed by then.

harry33, mac4man , effenberg and VinDSL have laid out some really good fixes. They  are all pretty well the same. The only thing.. is that there is a certain order, flowchart if you will, that has to be followed.  The "force version" worked really well a week or so ago and I am sure the methods and fixes proposed here work just as well , but I think in my case I skipped a step , (or two).  Following the instruction , however, still brings up "holding back nvidia-current" and then I go back to that re-loop  bug we had just over a week ago. Lucky for me I also have several varing stages of quantal installs on my 1/2 terabyte HDD so a busted DE here and there is par for the course for me.  I would not , however, try to mislead anyone with limited resources to trash their DE.

 It appears from the chatter that nvidia-current drivers .. etc.. will be comming down the pipe soon and these problems will be resolved.  But , also , correct me if I am wrong, a lot of this activity happened in synchronicity when Unity 2d got pulled from the repos.  

 As for myself.. I have currently  7 towers, 1 desktopPC, 3 laptops and 1 LePan tablet.  All of the PCs have varying stages of Ubuntu quantal on them  so I can afford the extra breakage, (although it costs me in bandwidth( lol)

 But I would say to a tester that does not have the extra hardware resources to wait these nvidia bugs out until the updates are safe to install.  That does not diminish their contributions to the forums. Dual installs or quad installs are just great as one can migrate data from one borked system to a working one on the same hdd or other storage device. Also having a DE like fvwm-crystal on the rack is amost always a sure bet to get up and running.

---

### Post by ventrical on 2012-08-20
> **ronacc said:**
> this update cycle has been worse for me than any since edgy eft . I have 2 installs . one updated from precise and one from the daily's ( replaced every few days ) they act very different , the updated precise is reasonably stable the install from daily is a crap shoot . The last few daily's I cant even install because they die during boot from the dvd  but so far the 2 installs ( updated daily) at least make it to DT ( haven't updated today yet ) I have nouveau on both so I may get away with it . I sure hope the devs give us atleast a week to put the RC through its paces or we may stampede right off a cliff .

I am leaning more now to aquire Intel based video graphics for testing as oppossed to ATi or nVidia corporation because they do not seem to have  the problems during development release as do Ati and nVidia.  I am not here  in ubuntuforums to be a beta tester for nvidia or ATi. I am here to test ubuntu and  doing cross-testing of  these problem drivers takes away a lot of resources for other bugs and testings in other area of ubuntu that need testing.  Actually, testing nvidia adpaters is begginning to be a real bore. It's always the same for the past 3 released, Oneiric, Precise and now quantal, nvidia-current and xserver-xorg. Meanwhile Kubuntu, Xubuntu, edubuntu etc.. get cast off to the way side while everybody gets nvidia-fever :) lol Then .. as usual , near the end  of testing, it suddenly gets fixed!! What a waste of time and brain power .

---

### Post by ronacc on 2012-08-20
Intel graphics have made good gains recently but I have had so much luck with Nvidia for over a decade I hate to change , what I may do for my next box is go with Intel onboard graphics and an Nvidia card so I can switch in bios and have the best of both :D

---

### Post by VinDSL on 2012-08-20
> **Cavsfan said:**
> LOL! You can please some of the people some of the....
Any way, let's just say I downgrade xserver-xorg-core as you've explained. Then I install nvidia-current or nvidia-current-updates right?[...]
Heh!  If you don't mind, I'm going to quit while I'm ahead.

I could explain the whole hacking sequence, in graphic detail, but...

I *feel* like I'm teaching ppl how to shoplift, pick locks, jimmy the ignition in a Toyota, or whatever.  :D

---

### Post by Cavsfan on 2012-08-21
> **VinDSL said:**
> Heh!  If you don't mind, I'm going to quit while I'm ahead.

I could explain the whole hacking sequence, in graphic detail, but...

I *feel* like I'm teaching ppl how to shoplift, pick locks, jimmy the ignition in a Toyota, or whatever.  :D

Yeah, I went ahead and attempted what I thought was the "fix", didn't work, mey, I am done.
I have other options, so I am not greatly concerned by any means. 
What puzzles me is that for the time being I am running fairly normally w/o a video driver.

---

### Post by Cavsfan on 2012-08-21
Bug for my exact problem:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672)

It says it only affects 10 people. You might want to add your name to the list. I am the 10th.

---

### Post by mc4man on 2012-08-21
> **Cavsfan said:**
> Bug for my exact problem:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1032672)

It says it only affects 10 people. You might want to add your name to the list. I am the 10th.
Not sure why nvidia is in that bug - for the moment nvidia-current* has purposely been set Not to install if using xserver 1.13

Right there in the changelog
> nvidia-graphics-drivers (304.32-0ubuntu4) quantal; urgency=low

  * debian/rules:
    - Disable support fo X ABI 13 since the driver doesn't
      seem to work well with the new X.

 -- Alberto Milone <alberto.milone@canonical.com>  Fri, 17 Aug 2012 18:50:05 +0200


So there is no 'bug' on nvidia package failing to install

---

### Post by Bowmore on 2012-08-21
I've issued a bug report about the garbage login/desktop screens at startup/reboot when running the 3.5.0-10 or 11 kernel using the nouveau driver. Found three workarounds mentioned in that bug report to avoid this issue.

The bug report:
[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1039125](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1039125)

---

### Post by dino99 on 2012-08-21
> **Bowmore said:**
> I've issued a bug report about the garbage login/desktop screens at startup/reboot when running the 3.5.0-10 or 11 kernel using the nouveau driver. Found three workarounds mentioned in that bug report to avoid this issue.

The bug report:
[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1039125](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1039125)

an other workaround via xorg.conf:

create (or replace what's in a current one) an /etc/X11/xorg.conf with 
Code:
Section "Device"
        Identifier "My Graphics"
        Driver "nouveau"
        Option "GLXVBlank" "on"
EndSection

---

### Post by Cavsfan on 2012-08-21
I just found that googling "xorg-video-abi-12". It was the 5th on the list. 
Also looks like Debian is having issues with this too.

I think I'll try to brake it. What can I lose?

However searching for "ubuntu 12.10 xorg-video-abi-12" it is 2nd on the list.

---

### Post by Bowmore on 2012-08-21
> **dino99 said:**
> an other workaround via xorg.conf:

create (or replace what's in a current one) an /etc/X11/xorg.conf with 
Code:
Section "Device"
        Identifier "My Graphics"
        Driver "nouveau"
        Option "GLXVBlank" "on"
EndSection
Thanks dino.
However, I've tried that one earlier but didn't work then. Gave it another try now but still doesn't work here as a workaround.

---

### Post by stinkeye on 2012-08-21
I removed the nvidia drivers but doesn't seem to be loading the nouveau drivers.
Just get the drum sound and scrambled screen.
At the scrambled login, going ctrl+alt+F1 logging in and running..,
```
sudo service lightdm restart 
```
brings the login screen up and after login...
```
sudo lshw -c video
```
shows the nouveau driver is in use.
Still need to repeat the procedure for every login though.

```
[COLOR="Green"]glen@Quantal:~$[/COLOR] sudo lshw -c video
[sudo] password for glen: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="Red"]driver=nouveau[/COLOR] latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```
Back in Unity with compiz cube. :D

---

### Post by Bowmore on 2012-08-21
> **stinkeye said:**
> Just get the drum sound and scrambled screen.
At the scrambled login, going ctrl+alt+F1 logging in and running..,
```
sudo service lightdm restart 
```
brings the login screen up and after login...
Yup, an alternative to the Ctrl-Alt-Backspace workaround.
Added to the bug report ;)

---

### Post by grahammechanical on 2012-08-21
I also got the login bounce back from the update that brought in the 3.5.0-10 kernel. That would not have been so bad if Ubuntu 2D had not been removed as an option at the same time.

It is time to become familiar with Recovery mode. I used its dpkg - Repair Broken Packages option and it removed Nvidia-current. Which is strange as I thought that I was using Nouveau on both my Quantal installs. Anyway that fixed the problem I had with what I call Quantal-B.

Now to fix the problem that the same update did to my Quantal-A. I still have the Ubuntu 2D option but I cannot update because of the "section with no package header" error.

It is something called i18n_Translation-en%5fGB. This error which was not of my making is stopping this install from getting any updates. It crashes Software Updater and Synaptic. Even "apt-get update" fails

Any Ideas?

Regards.

---

### Post by Cavsfan on 2012-08-21
> **stinkeye said:**
> I removed the nvidia drivers but doesn't seem to be loading the nouveau drivers.
Just get the drum sound and scrambled screen.
At the scrambled login, going ctrl+alt+F1 logging in and running..,
```
sudo service lightdm restart 
```brings the login screen up and after login...
```
sudo lshw -c video
```shows the nouveau driver is in use.
Still need to repeat the procedure for every login though.

```
[COLOR=Green]glen@Quantal:~$[/COLOR] sudo lshw -c video
[sudo] password for glen: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR=Red]driver=nouveau[/COLOR] latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```Back in Unity with compiz cube. :D

Sweet! I tried a bunch of things and could not break it, but this explains why I am able to login to both Unity and Gnome Classic (which I just now installed).
I got the scrambled screen a few times but, no more. I can login to either just fine. 
Although Gnome Classic needs some work.

```
cavsfan@cavsfan-MS-7529:~$ sudo lshw -c video
[sudo] password for cavsfan: 
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce 9800 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR=Red]driver=nouveau[/COLOR] latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:feae0000-feafffff
```I am going to try to get the compiz cube going. Thanks for posting this! :p

---

### Post by Cavsfan on 2012-08-21
Unity is good to go now. Compiz - check. Cairo Dock open gl - check. Rotating cube - check.
stinkeye, you shouldn't have to login that way. I hope it straightens itself out for you too.

Smoking! :guitar:

---

### Post by 3vi1 on 2012-08-21
The xserver/nvidia-current breakage couldn't have been triggered at a worst time.  There's a two or three week old nouveau bug with the GTX 560 cards that leaves them unable to start X with that driver either.  :\

As I'm much too tired to fight with backleveling xserver right now, I think I'll just wait this one out.

---

### Post by ventrical on 2012-08-21
> **3vi1 said:**
> The xserver/nvidia-current breakage couldn't have been triggered at a worst time.  There's a two or three week old nouveau bug with the GTX 560 cards that leaves them unable to start X with that driver either.  :\

As I'm much too tired to fight with backleveling xserver right now, I think I'll just wait this one out.


+1 ditto :)

---

### Post by stinkeye on 2012-08-23
> **Cavsfan said:**
> Unity is good to go now. Compiz - check. Cairo Dock open gl - check. Rotating cube - check.
stinkeye, you shouldn't have to login that way. I hope it straightens itself out for you too.

Smoking! :guitar:
Solved. I was booting from grub on another hard drive where precise is installed.
Used boot-repair to reinstall grub on the Quantal drive and changed to boot from that drive in the bios.
Loads the nouveau driver without an /etc/X11/xorg.conf file.
Don't know why but it boots fine now. :D

---

### Post by Cavsfan on 2012-08-23
> **stinkeye said:**
> Solved. I was booting from grub on another hard drive where precise is installed.
Used boot-repair to reinstall grub on the Quantal drive and changed to boot from that drive in the bios.
Loads the nouveau driver without an /etc/X11/xorg.conf file.
Don't know why but it boots fine now. :D

That is good! :grin:
When I moved my grub to anything other than Quantal, I have no ability to use my mouse.
But, as long as grub is installed on Quantal the system boots fine with the nouveau driver and I have mouse movement.
I do not find any /etc/X11/xorg.conf file though. I don't know what is up with that but, it works.

Although it was fairly painful when this first happened and I could not boot into Quantal. 
I deleted the Quantal partitions from Lucid without remembering to move the grub first.
Ouch! But, here I am stronger and wiser feeling like LL Cool J after he took out that house intruder this morning. ;)

```
cavsfan@cavsfan-MS-7529:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV92
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    [COLOR=Lime]yes[/COLOR]
Not blacklisted:          [COLOR=Lime]yes[/COLOR]
GLX fbconfig:             [COLOR=Lime]yes[/COLOR]
GLX texture from pixmap:  [COLOR=Lime]yes[/COLOR]
GL npot or rect textures: [COLOR=Lime]yes[/COLOR]
GL vertex program:        [COLOR=Lime]yes[/COLOR]
GL fragment program:      [COLOR=Lime]yes[/COLOR]
GL vertex buffer object:  [COLOR=Lime]yes[/COLOR]
GL framebuffer object:    [COLOR=Lime]yes[/COLOR]
GL version is 1.4+:       [COLOR=Lime]yes[/COLOR]

Unity 3D supported:       [COLOR=Lime]yes[/COLOR]
```

---

### Post by stoneguy on 2012-08-23
For U+1 testing, I do continuous upgrades and only reinstall at milestone releases.

I'm logging in fine from my Classic No Effects desktop and from Xterms. But from VTx I get that same password reject error. No NVIDIA factor here, this is with my VBox VM.

---

### Post by Cavsfan on 2012-08-23
My Unity login is what works well. I even installed Emerald window manager so I have all the bells and whistles now.
It even works better than Precise does at this time. 

My Gnome Classic doesn't work so well but, not sure why.
Have contributed to several bugs so I guess I am doing what we're supposed to be doing.
Just glad that when things blew up it didn't take the system with it.

Still waiting on the Nvidia thing to be worked out but, still doing great meanwhile! :p

---

### Post by Cavsfan on 2012-08-24
When I boot into Quantal now, the monitor shuts off and after several exciting seconds it comes back on and the logon screen looks like I am already logged on.
So, after entering my password the screen looks like the last display and then it refreshes.

---

### Post by fluteflute on 2012-08-27
It turns out that Noveau with the lvmpipe stuff is fairly usable.

But a new NVIDIA driver came out today (not yet into repositories): [http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTM](http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTM)
[http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html)

---

### Post by Cavsfan on 2012-08-27
> **fluteflute said:**
> It turns out that Noveau with the lvmpipe stuff is fairly usable.

But a new NVIDIA driver came out today (not yet into repositories): [http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTM](http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTM)
[http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html)

I would not attempt that on 12.10 unless you like re-installing. But, if you do get it installed and can login afterwards by all means let us know.
I installed 12.04.1 on another partition yesterday and I almost could not get back into Quantal.
If grub is not installed on your 12.10 installation, you have no mouse. After many, many  attempts I was finally able to login into the 3.5.0-6-generic kernel in recovery and installed grub.
At least this has been my experience and I just installed Quantal before Precise.
Quantal apparently does not multi-boot well.

---

### Post by Harry33 on 2012-08-27
This is important:

New nvidia graphics driver (304.43 certified) fixes include a GLX crash fix on X.Org Server 1.13, VDPAU hanging on YouTube, problems with [[COLOR=#234865][COLOR=#234865 !important][FONT=inherit !important][COLOR=#234865 !important][FONT=inherit !important]GNOME[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTM#") Settings Daemon and the display configuration, RandR updates for NVIDIA Settings, and a display palette bug.

So, if the glx crash is now fixed, it means it will work with xserver_1.13.

Now what?
Let's wait xorg-edgers people, like Ricotz, builds an installable deb of nvidia-current_304.43.

---

### Post by Harry33 on 2012-08-28
Now the nvidia-current_304.43 cert is available from the xorg-edgers PPA.
Go get it.

---

### Post by Cavsfan on 2012-08-28
> **Harry33 said:**
> Now the nvidia-current_304.43 cert is available from the xorg-edgers PPA.
Go get it.

I got it and it works great! For the first time on Quantal an actual Nvidia driver!
Whoot!

It is just nvidia-current as I installed it from Synaptic!

Thanks Harry!  
:guitar:

---

### Post by coffeecat on 2012-08-28
> **Harry33 said:**
> Now the nvidia-current_304.43 cert is available from the xorg-edgers PPA.
Go get it.

Thanks. Now I can test Quantal on this laptop again. Unfortunately, the GUI with the nouveau driver was almost unusable with its GeForce 410M graphics.

---

### Post by Cavsfan on 2012-08-28
It looks like the 304.43 driver made it into the regular repos:

```
Preparing to replace nvidia-current 304.43-0ubuntu1~xedgers~quantal2 (using .../nvidia-current_304.43-0ubuntu1_amd64.deb) ...
```I just got that in an update among other things.

I think I'll remove the xswat ppa for the time being.

---

### Post by spiky001 on 2012-08-31
Hi  I have just updated 12.10 It was about 500 packages. Ok it has been about a month since last update, I get an error failed to load sesion ubuntu as you can imagine that means I cant log in at all any Idea how to fix. I do know this is a development version and breakages are expected.

---

### Post by dino99 on 2012-08-31
Dont Panic, you're not alone ):P

but read what others have said first:

[http://ubuntuforums.org/showthread.php?t=2043695](http://ubuntuforums.org/showthread.php?t=2043695)

no need to open an other thread ;)

---

### Post by spiky001 on 2012-08-31
Thks dino I have asked for thread to be moved. Although I have a different cause, I use intel graphics. When I try to login normally the desktop is under the login box and all the buttons work , eg shutdown, wireles connects. If I log in recovery mode, I cant add a new user, As someone mentioned in in linkd post,error is ```
useradd cannot lock /etc/passwd: try agin later
``` Also if i cd /home there is no user dir. User home is on another partition

---

### Post by spiky001 on 2012-08-31
I have googled and found similar problems on earlier versions, the fix was to remove /etc/gshadow.lock, /etc/shadow.lock, /etc/passwd.lock /etc/group.lock None of these file are there. I have noticed while in recovery mode I can su - user and use the sudo command with password.

---

### Post by cariboo on 2012-08-31
> **spiky001 said:**
> I have googled and found similar problems on earlier versions, the fix was to remove /etc/gshadow.lock, /etc/shadow.lock, /etc/passwd.lock /etc/group.lock None of these file are there. I have noticed while in recovery mode I can su - user and use the sudo command with password.

Why would you do that, when you are running as root in recovery mode? No user name or password needed.

---

### Post by spiky001 on 2012-08-31
Hi I was trying to see if I became the user would the password work, I was checking as the error for creating a user was /etc/passwd lock  I was just trying to add info thought it might help.

---

