---
title: "Gnome-shell_3.5.91 is not working"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-09-09
I opened this thread because it concerns one specific issue with the GS_3.5.91 and Gdm_3.5.91.

Trying to start Gnome session (GS) it fails after funny unfocused (filling the entire screen) Gdm login screen and finally the desktop starts without any panels.

I get this error (fatal IO error 0) from .cache/gdm/session.log
```

...
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1200004 (Desktop) with a timestamp of 0.  This shouldn't happen!
...

```

Gnome classic session works fine.

If I downgrade GS to the version 3.5.4-0ubuntu2, everything works fine.
I only have Gdm_3.5.91 installed (default), with no LightDM installed.

Now, is there a package that must be installed with GS_3.5.91, even it does not depend on it?
Or, is this failure due to nvidia-current_304.43?

---

### Post by kuvanito on 2012-09-09
GS 3.5.91 working fine here :P

---

### Post by Harry33 on 2012-09-09
> **kuvanito said:**
> GS 3.5.91 working fine here :P

Are you using Gdm as default DM?
Do you have a nvidia graphics card?

---

### Post by bmbaker on 2012-09-09
hi Harry i am using the same GS and GDM with nvidia with no problems !
have you looked at your extensions?

---

### Post by Harry33 on 2012-09-09
> **bmbaker said:**
> hi Harry i am using the same GS and GDM with nvidia with no problems !
have you looked at your extensions?

I have never used any extensions.
How does your gdm login screen look alike when you are logging in?
Is it a small nice black window in the middle of the screen or is it grey and filling the entire screen?

---

### Post by jppr on 2012-09-09
I don't have any promlems. I just did ubuntu-gnome-desktop installation and gnome-shell works fine with lightdm and nouveau-driver.

---

### Post by bmbaker on 2012-09-09
> **Harry33 said:**
> I have never used any extensions.
How does your gdm login screen look alike when you are logging in?
Is it a small nice black window in the middle of the screen or is it grey and filling the entire screen?

i have a nice little icon :-)
do you have lightdm installed as well?
if not try installing it and chosing gdm as default again!

---

### Post by sgage on 2012-09-09
> **Harry33 said:**
> I opened this thread because it concerns one specific issue with the GS_3.5.91 and Gdm_3.5.91.

Trying to start Gnome session (GS) it fails after funny unfocused (filling the entire screen) Gdm login screen and finally the desktop starts without any panels.

I get this error (fatal IO error 0) from .cache/gdm/session.log
```

...
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1200004 (Desktop) with a timestamp of 0.  This shouldn't happen!
...

```

Gnome classic session works fine.

If I downgrade GS to the version 3.5.4-0ubuntu2, everything works fine.
I only have Gdm_3.5.91 installed (default), with no LightDM installed.

Now, is there a package that must be installed with GS_3.5.91, even it does not depend on it?
Or, is this failure due to nvidia-current_304.43?

I had all kinds of weird problems with nvidia-current, and reverted to nouveau. Problems gone. Give it a try...

---

### Post by Harry33 on 2012-09-09
> **jppr said:**
> I don't have any promlems. I just did ubuntu-gnome-desktop installation and gnome-shell works fine with lightdm and nouveau-driver.

I know LightDM works yes, but the issue here is that GS_3.5.91 does not seem to work with Gdm and nvidia-current.

Edit:
Well I just tried LightDM (default) by first downgrading to GS_3.5.4 and removing Gdm: it worked OK.
Then, I installed Gdm, but kept LightDM as default DM. Working OK.
But, immediately after upgrading GS to 3.5.91 it is a no go, not even with LightDM as default DM.
So, now this is odd. => a nvidia-current issue then?

---

### Post by Harry33 on 2012-09-09
> **sgage said:**
> I had all kinds of weird problems with nvidia-current, and reverted to nouveau. Problems gone. Give it a try...

Yes I am beginning to suspect it is nvidia-current where the problem is.

---

### Post by jbicha on 2012-09-09
Could someone experiencing this problem please report this bug, preferably to bugzilla.gnome.org against Core/gnome-shell/drivers?

---

### Post by kuvanito on 2012-09-09
> **Harry33 said:**
> Are you using Gdm as default DM?
Do you have a nvidia graphics card?

i am using gdm and no,i do not have an nvidia video card.i stay away from nvidia,ati and amd.i am an intel boy :) :) :)

---

### Post by sgage on 2012-09-09
> **Harry33 said:**
> I have never used any extensions.
How does your gdm login screen look alike when you are logging in?
Is it a small nice black window in the middle of the screen or is it grey and filling the entire screen?

I have the grey full-screen thing. Ugh! Not sure when that change came in. I started a separate thread on it, see if anyone has any insight...

---

### Post by Harry33 on 2012-09-09
> **jbicha said:**
> Could someone experiencing this problem please report this bug, preferably to bugzilla.gnome.org against Core/gnome-shell/drivers?

Sure I would, but I do not have enough data for that now.
Needs further viewing.

---

### Post by Harry33 on 2012-09-09
> **sgage said:**
> I have the grey full-screen thing. Ugh! Not sure when that change came in. I started a separate thread on it, see if anyone has any insight...

For me the grey ugly Gdm appeared right after I upgraded GS to 3.5.91.
And the small black nice window comes back after downgrading to GS_3.5.4.

---

### Post by Stinger on 2012-09-09
> **Harry33 said:**
> For me the grey ugly Gdm appeared right after I upgraded GS to 3.5.91.
And the small black nice window comes back after downgrading to GS_3.5.4.

I guess you'll have to make a choice:
If you want to sit in 'in the back of the bus' with your small black nice window 
or:
If you want to ride up front were the view is much better and accept "grey ugly Gdm" witch I don't think it is at all :razz:

---

### Post by jppr on 2012-09-09
> **Harry33 said:**
> For me the grey ugly Gdm appeared right after I upgraded GS to 3.5.91.
And the small black nice window comes back after downgrading to GS_3.5.4.

Why use  the gdm which don´t work... when there is lightdm which work...

---

### Post by Harry33 on 2012-09-09
> **Stinger said:**
> I guess you'll have to make a choice:
If you want to sit in 'in the back of the bus' with your small black nice window 
or:
If you want to ride up front were the view is much better and accept "grey ugly Gdm" witch I don't think it is at all :razz:

Those are not the options for me however.
If I choose to upgrade GS to 3.5.91, I get no panels and that means a broken GS.
So, I have to use GS_3.5.4 and that means also a nice black Gdm login screen. :guitar:

---

### Post by Harry33 on 2012-09-09
> **jppr said:**
> Why use  the gdm which don´t work... when there is lightdm which work...

Well for me not even LigtDM works if upgrade GS to 3.5.91.
So I have to keep GS_3.5.4 for now, and then Gdm works just fine and it comes also with a small face browser. :guitar:

---

### Post by Stinger on 2012-09-09
> **Harry33 said:**
> Those aro not the options for me however.
If I choose to upgrade GS to 3.5.91, I get no panels and that means a broken GS.

Sorry to hear that, are you using standard Ubuntu or [Ubuntu gnome remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/1210Alpha?action=show&redirect=UbuntuGNOME%2FReleaseNotes") like me ?

---

### Post by Harry33 on 2012-09-09
> **Stinger said:**
> Sorry to hear that, are you using standard Ubuntu or [Ubuntu gnome remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/1210Alpha?action=show&redirect=UbuntuGNOME%2FReleaseNotes") like me ?

This is a standard Ubuntu, more or less, but a "minimalistic" installation.
I have removed everything I do not need (like Unity, Evolution ...).

---

### Post by Stinger on 2012-09-09
I would recommend you to try [Ubuntu Gnome Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/1210Alpha") if you can find the time, it could isolate this 'bug' to the standard ubuntu build.
I can guide you through if any trouble ;)

---

### Post by VinDSL on 2012-09-09
> **Harry33 said:**
> Now, is there a package that must be installed with GS_3.5.91, even it does not depend on it?
Brilliant, Harry!  You spurred me to action...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-9-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-9-sep-2012-1.png")[/INDENT]


I worked on the Conky weather section, this morning, until I was "blind".

** Note to self:  Wash your eye glasses before working with sed!  :D

Anyway, between jbicha's suggestions and your comments, I cobbled it all together.

Man, this GS 3.6 is sweet!  

Gotta go update my Facebook... BRB

---

### Post by VinDSL on 2012-09-09
Okay, let's start with this...
> **jbicha said:**
> That's how it works. gdm can either be run in shell mode where GNOME Shell provides the log-in screen or in fallback mode which doesn't need GNOME Shell or working 3D and looks like gdm 3.0 as present in Ubuntu 12.04 LTS.

[B][COLOR="DarkRed"]You should be able to force fallback mode by editing /etc/gdm/greeter.gsettings and uncommenting the following lines:

```

[org.gnome.desktop.session]
session-name='gdm-fallback'

```

That's done by default in Debian Wheezy, and they also uncomment the bottom two lines in that file.
[/COLOR][/B]
If you're curious about tweaking GDM, you should also check out custom.conf in that same directory.

I did the above, then I re-installed LightDM, and chose it as the default DM.

I should mention, last night, after I upgraded to GS 3.5.91-1, LightDM started behaving poorly, on boot/restart/logout et cetera. The only background it would display was the default "Purple Monkey Vomit" -- it would flash a couple of times, before settling down, and all that nonsense.  It didn't follow the desktop wallpaper, as is the norm.

After installing LightDM, today, I decided to restart and login to GS 3.5.4.  Everything worked fine (LightDM picked up my desktop wall too) so I continued down the road...

I used apt-get to upgrade to GS 3.5.91 -- this time paying close attention to "recommended" packages, per the question you planted in my mind, in post #1.

```
vindsl@Zuul:~$ sudo apt-get install gnome-shell
[sudo] password for vindsl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-shell-common
[B][COLOR="DarkRed"]Recommended packages:
  gnome-contacts gnome-session-fallback[/COLOR][/B]
The following packages will be upgraded:
  gnome-shell gnome-shell-common
2 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Need to get 0 B/1,534 kB of archives.
After this operation, 137 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

These seemed like reasonable additions, so I installed them.

```
vindsl@Zuul:~$ sudo apt-get install gnome-contacts

vindsl@Zuul:~$ sudo apt-get install gnome-session-fallback

```

One, or the other, installs "recommended" desktop-base.  I judged this to be a little silly, but I installed it anyway.

```
vindsl@Zuul:~$ sudo apt-get install desktop-base

```

Heh!  It (or one of the depends) sure made GRUB look pretty -- has a Debian logo on light-blue background now. :)

Finally, I restarted -- logged into GS 3.5.91 using LightDM -- and life is good again.

I *think* the only reason GDM is required is if you (or your screensaver et cetera) locks your desktop.  If GDM isn't your default DM, your password will not be recognized.  

Put another way, GS 3.6 et al. requires GDM to process the password, when attempting to unlock your screen -- you cannot unlock it with LightDM -- they aren't compatible, in this respect.  At least, that's what I gather from reading around.  Haven't tried it yet.  ;)

Okay, gonna go check Unity & LXDE now...

---

### Post by jbicha on 2012-09-09
Right. gdm used to recommend desktop-base which didn't seem like a good idea. It's good you like the artwork though!

---

### Post by VinDSL on 2012-09-09
> **jbicha said:**
> Right. gdm used to recommend desktop-base which didn't seem like a good idea. It's good you like the artwork though!
Would look great with that gorgeous, slick-skinned, pangolin wall from the official backgrounds!

Heh!  I think I'll see if I can toss that one in... :)

---

### Post by VinDSL on 2012-09-09
Well, isn't that a h00t!?!?!  Gnome Classic is back in LightDM.

I won't bore you with yet-another-screenshot...  LoL!  :D

Interesting!

Classic is a little janky -- noticed the desktop switcher is broken, for instance.

Got Conky, Chromium, Dropbox & Guayadeque running, and it's only using 428MB RAM.

Okay, off to check Unity & LXDE...

---

### Post by VinDSL on 2012-09-09
WoW!  Everything is working!

This thing (ancient iron) is flying in Unity!

Haven't said that for a while.  :guitar:

Okay, back to Conky...

Latez

---

### Post by Harry33 on 2012-09-10
> **VinDSL said:**
> 
...

I used apt-get to upgrade to GS 3.5.91 -- this time paying close attention to "recommended" packages, per the question you planted in my mind, in post #1.
...
[B][COLOR=DarkRed]Recommended packages:
  gnome-contacts gnome-session-fallback[/COLOR][/B]
...
One, or the other, installs "recommended" desktop-base.
...

...

So, you are saying the installation of one or more of those recommended packages made GS_3.5.91 work again?
I already have gnome-session-fallback, but not gnome-contacts nor desktop-base.

I will try those later today.
Thanks.

---

### Post by Harry33 on 2012-09-10
> **Stinger said:**
> I would recommend you to try [Ubuntu Gnome Remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/1210Alpha") if you can find the time, it could isolate this 'bug' to the standard ubuntu build.
I can guide you through if any trouble ;)

I think it is easier to check the differencies between these two packages first:
- ubuntu-gnome-desktop
- ubuntu desktop
See below the details.
Anyway, the main differencies are certain gnome applications and ubuntu applications.


**Ubuntu-gnome-desktop** depends on these (not in ubuntu desktop):
- brasero (recommended in ubuntu-desktop)
- fonts-cantarell
- gcr
- gnome-backgrounds
- gnome-color-manager
- gnome-contacts
- gnome-dictionary
- gnome-disk-utility (recommended in ubuntu-desktop)
- gnome-icon-theme-extras
- gnome-keyring
- gnome-online-accounts
- gnome-shell dependencies
- gnome-sushi
- gnome-tweak-tool
- gnome-user-share
- gnome-video-effects
- gstreamer1.0 (-alsa, -plugins-base-apps, -pulseaudio)
- itstool
- metacity
- simple-scan (recommended in ubuntu-desktop)
- tracker
- ubuntu-gnome-default-settings
- vino (recommended in ubuntu-desktop)
- yelp-tools
- yelp-xls

**Ubuntu-desktop** has these additional dependencies:
- checkbox-qt
- gnome-power-manager
- language-selector-gnome
- lightdm
- notify-osd
- software-center
- system-config-printer-gnome
- ubuntu-artwork
- ubuntu-release-upgrader-gtk
- ubuntu-sounds
- unity
- unity-greeter
- update-manager
- update-notifier

**Ubuntu-gnome-desktop** recommends on these (not in ubuntu desktop):
- abiword
- cheese
- epiphany-browser
- gnome-packagekit
- gnome-panel
- gnome-search-tool
- gnumeric
- indicator (-datetime, -printers, -sync)

**Ubuntu-desktop** recommends these additional packages:
- activity-log-manager-control-center
- branding-ubuntu
- firefox (-gnome-support)
- landscape-client-ui-install
- libreoffice packages
- overlay-scrollbar
- qt-at-spi
- remmina
- thunderbird (-gnome-support)
- totem-mozilla
- ubuntu-docs
- ubuntuone
- xul-ext-ubufox

---

### Post by jbicha on 2012-09-10
> **Harry33 said:**
> This is a standard Ubuntu, more or less, but a "minimalistic" installation.
I have removed everything I do not need (like Unity, Evolution ...).

You didn't try to remove evolution-data-server, did you? Try reinstalling that and see if that helps.

---

### Post by Harry33 on 2012-09-10
> **jbicha said:**
> You didn't try to remove evolution-data-server, did you? Try reinstalling that and see if that helps.

Yes I had removed that package. Gnome-panel does recommend it though.
However, neither gnome-panel nor gnome-shell depend on it.
And, Gnome-panel_3.5.91 and Gnome-shell_3.5.4 do work without it.

Anyway, Gnome-shell_3.5.91 does not work without evolution-data-server.

Thanks Jeremy.

---

### Post by VinDSL on 2012-09-10
> **Harry33 said:**
> So, you are saying the installation of one or more of those recommended packages made GS_3.5.91 work again?
I'm not sure WHAT fixed the problem.  :(

I was heavily involved with tweaking Conky, at the time, and occasionally playing around with GS during breaks in the action, in order to clear my mind.

It was easy enough to go through my bash history, and see what I installed, but that doesn't backtrace all the files that were installed from the various packages, and in which order they were installed.

My *gut feeling* is, re-installing LightDM -- and choosing it as my default DM -- is what did the trick.

Thinking back, LightDM was the only DM that was installed on this machine, before I installed GS 1.5.91-1.  When I originally installed GDM -- but, choose LightDM as the default DM -- it seemed to bork LightDM.  When, I rinsed LightDM and choose GDM as my default DM, GS 1.5.91-1 still wouldn't work. So, I downgraded to GS 1.5.4-2 and everything came alive.

I was happy to have everything working, so I decided to leave things be, for the time being... until, I read your post.  That rang a bell.  It *seemed* to gel (in my mind) with what jbicha had posted in another thread.

I decided to give it a whirl; apply jbicha's tweak, re-install GS 1.5.91-1, LightDM, and any "Recommended" packages that popped up along the way. And, we were off to the races.

Truthfully, I don't know which package(s) fixed the problem.  If I had the time to do things properly, I would have performed the installs one at a time, and documented which package did what. 

Heh!  I was "dead sure" that none of those packages would make one bit of difference.  I was shocked when GS 1.5.91-1 booted properly, especially since I choose LightDM as my default DM.  And, I might mention, I did a full upgrade via Synaptic, before going to bed, and it survived a cold boot this morning.

Wish I could be of more help, but at least the text above might explain the rationale I used in the disjointed process of fixing this problem.

I guess it'll have to remain an exercise in the second-order coefficient.  

I don't plan to knock Humpty Dumpty off the wall, so I can put him back together again. LoL!  :D

---

### Post by Harry33 on 2012-09-11
> **VinDSL said:**
> I'm not sure WHAT fixed the problem.  :(
...
  LoL!  :D

OK, fine!

For me the missing package really was evolution-data-server.
I haven't had that one installed for a long time now.
Now suddenly GS_3.5.91 requires it.

However, from the GS package properties I can see that it does not depend on it, nor recommend it, not even suggest it.
It should definitely be a dependency.

---

### Post by mips on 2012-09-11
> **VinDSL said:**
> 
It was easy enough to go through my bash history, and see what I installed, but that doesn't backtrace all the files that were installed from the various packages, and in which order they were installed.

You could always check your apt logs...

---

### Post by VinDSL on 2012-09-11
> **mips said:**
> You could always check your apt logs...
Checked my apt logs, and yes, there it was.  Thanks!

> **Harry33 said:**
> For me the missing package really was evolution-data-server.
According to my apt logs, this was applied (along with many others) when I re-installed the LightDM package:

```
evolution-data-server:i386 (3.5.91-0ubuntu1, automatic)
```
Here's the entire line, from the log...
```
Install: lightdm-remote-session-freerdp:i386 (0.3-0ubuntu1, automatic), libebook-1.2-14:i386 (3.5.91-0ubuntu1, automatic), lightdm-remote-session-uccsconfigure:i386 (0.3-0ubuntu1, automatic), lightdm:i386 (1.3.3-0ubuntu3), python3-pycurl:i386 (7.19.0-5ubuntu1, automatic), liblightdm-gobject-1-0:i386 (1.3.3-0ubuntu3, automatic), libedata-cal-1.2-18:i386 (3.5.91-0ubuntu1, automatic), libfreerdp-plugins-standard:i386 (1.0.1-1ubuntu7, automatic), libedata-book-1.2-15:i386 (3.5.91-0ubuntu1, automatic), libtimezonemap1:i386 (0.3.2, automatic), indicator-datetime:i386 (12.10.0-0ubuntu1, automatic), evolution-data-server:i386 (3.5.91-0ubuntu1, automatic), remote-login-service:i386 (0.5.0-0ubuntu1, automatic), libebackend-1.2-5:i386 (3.5.91-0ubuntu1, automatic), unity-greeter:i386 (12.10.2-0ubuntu4, automatic), libpam-freerdp:i386 (0.4.0-0ubuntu1, automatic), libfreerdp1:i386 (1.0.1-1ubuntu7, automatic), freerdp-x11:i386 (1.0.1-1ubuntu7, automatic), thin-client-config-agent:i386 (0.6, automatic)
```
So, I think you nailed it down, Harry.  ;)

---

### Post by mips on 2012-09-11
> **VinDSL said:**
> Checked my apt logs, and yes, there it was.  Thanks!

No problemo. The only reason I know about apt logs was because I was scratching around in them two days ago to see what caused things to go wrong after an update :lolflag:

---

