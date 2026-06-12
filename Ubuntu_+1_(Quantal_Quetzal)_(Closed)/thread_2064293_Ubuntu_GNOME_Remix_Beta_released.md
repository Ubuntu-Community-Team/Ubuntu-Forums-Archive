---
title: "Ubuntu GNOME Remix Beta released"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-09-28
Since a lot of the info in [my original post]("http://ubuntuforums.org/showthread.php?t=2052509") is now outdated I felt it best to start a new thread related solely to Jeremy Bicha's Ubuntu GNOME Remix Beta release which is explained in the release notes here:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta)

The MD5SUMS, package manifests, and standard download links can be found here:

[http://bicha.net/ubuntu-gnome-remix/](http://bicha.net/ubuntu-gnome-remix/)

Please do however use the [torrents]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta#Download_Beta") wherever possible to reduce the load on the servers :)

Please also consider subscribing to the mailing list:

[https://lists.launchpad.net/ubuntu-gnome/](https://lists.launchpad.net/ubuntu-gnome/)

One of the projects greatest needs ATM is someone to fill the role of QA lead. In Jeremy's own words:

> I'm still looking for a QA Lead. The QA Lead ideally should have
plenty of in-depth knowledge and experience of Launchpad and
development of Ubuntu and GNOME. I guess there's not a lot of people
with that background with the interest of taking on this
responsibility, but I'm still hopeful! :) In the meantime, I'll be
taking on that role.

More on the need for a QA team here:

[https://lists.launchpad.net/ubuntu-gnome/msg00012.html](https://lists.launchpad.net/ubuntu-gnome/msg00012.html)

There is also an IRC channel for discussions regarding the development of Ubuntu GNOME Remix:

> #ubuntu-gnome

I hope I'm not leaving out any essential info ;)

---

### Post by Kirk M on 2012-09-29
Is the beta a hybrid ISO? The reason I ask is that no matter how I write the iso file (amd64) to my thumb drive it absolutely refuses to boot stating that there is no image to mount. It appears that it's looking for casper on a CD not a thumb drive or so says the path. My thumb drive is formatted to FAT32 (the tables are fine) and as a test I wrote and successfully booted both Ubuntu 12.10 beta 2 and Linux Mint Maya (both amd64 versions) via the same thumb drive.

I've used two different versions of Unetbootin (version available in 12.04 repositories as well as the latest version via PPA) as well as the USB Creator from a 12.10 beta 2 install (The USB Creator crashes constantly) to no avail. Is this a bug in the ISO or is a DVD only iso the only version available at the moment?

---

### Post by cariboo on 2012-09-29
I used the Startup Disk Creator utility in Precise to create a usb drive, as the same app crashed in Quantal. Once done, it booted with with only the usual graphics problem.

---

### Post by kansasnoob on 2012-09-29
I've just been using DVD's here so I'm clueless about creating a boot-able flash drive.

---

### Post by EmilyRose on 2012-09-29
I succesfully installed via a USB drive earlier today using the USB startup disk creator in precise as well.

---

### Post by Stinger on 2012-09-30
> **cariboo907 said:**
> I used the Startup Disk Creator utility in Precise to create a usb drive, as the same app crashed in Quantal. Once done, it booted with with only the usual graphics problem.
> **EmilyRose said:**
> I succesfully installed via a USB drive earlier today using the USB startup disk creator in precise as well.
[GNObuntu page 21]("http://ubuntuforums.org/showthread.php?t=1999827&page=21")
[usb-creator-gtk crashed]("http://ubuntuforums.org/showthread.php?t=2064033")

Just to sum it all up.
[LIST]
[*]The dd command it only creates an non boot-able ISO 9660 image :(
[*]The usb-creator crashes when creating the boot sector ( when you are asked for a password last in the process) [Bug#915626]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/915626")
[/LIST]

There are two ways to create a bootable version of the beta.
[LIST]
[*]Burn the iso to a DVD or 
[*]Boot into a livesession or installed version of Ubuntu / Ubuntu Gnome-Shell Remix 12.04 and use the usb-creator from there
[/LIST]

There really should be more focus on having a working usb-creator as many users nowadays use bootable usb-pen's. :rolleyes:

---

### Post by kansasnoob on 2012-09-30
> There really should be more focus on having a working usb-creator as many users nowadays use bootable usb-pen's.

Agreed. I still use DVD's but more and more machines no longer even have optical drives ;)

---

### Post by Stinger on 2012-09-30
@kansasnoob
You can find the iso images at ftp.gnome.org too:

[http://ftp.gnome.org/pub/GNOME/misc/ubuntu-gnome-remix/](http://ftp.gnome.org/pub/GNOME/misc/ubuntu-gnome-remix/)

Hosted by:
Academic Computer Club Umeå University

---

### Post by dino99 on 2012-09-30
im using LiveUSB (multisystem) to directly load iso

[http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://liveusb.info/dotclear/](http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://liveusb.info/dotclear/)

---

### Post by stoneguy on 2012-09-30
Installed in a VBox VM directly from ISO. Manual reboot no problems. Updated system to current, still OK.

Then went to add network printer. Got [indent]
FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.[/indent]

Same thing happens on quantal desktop if I try to set printers after installing gnome-panel and logging onto No Effects. Printer setup only works fron Unity.

I think there's a report in Launchpad for this, but looks like it's being ignored, since Unity is the official way of the future.

:-x:

---

### Post by EmilyRose on 2012-09-30
So an update after using it for a day or so now. Overall I'm very impressed and like it quite a lot. 

One thing that I think should really be included by default is the activity-log-center-control-center package which adds the "Privacy" section to System Settings allowing users to control logging on their systems.  I'm also a fan of synaptic and don't understand why it was removed from the default packages. 

One problem that I am having right now is regarding installing .deb files. While installing via the command line using dpkg works fine, double clicking ends with an "The action cannot be completed." and more details gives the following error:

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 489, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/sessioninstaller/core.py", line 669, in _install_package_files
    interaction, sender)
TypeError: install_package_files() takes exactly 4 arguments (5 given)

---

### Post by Stinger on 2012-10-01
> **stoneguy said:**
> Installed in a VBox VM directly from ISO. Manual reboot no problems. Updated system to current, still OK.

Then went to add network printer. Got [indent]
FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.[/indent]

Hi
Did you try the workaround from the [Ubuntu GNOME Shell Remix release notes ?]("http://ubuntu-gs-remix.sourceforge.net/p/release-notes/release-notes-1204/")

> **Network printer setup in System Settings does not work correctly:**
The default printer setup tool displays a message about FirewallD missing, if it can't find a printer, the recognition may or may not work after entering the IP manually. For network printers with integrated scanner the wrong network protocol may be chosen by default.
Workaround: Start system-config-printer from the [Alt]+[F2] prompt and set up your printer. You have to do this only once.

Or open terminal. Type, system-config-printer , press enter and then add printer.
should give the same result :)'

I don't have a network printer to test with, so please report back.

---

### Post by Stinger on 2012-10-01
> **EmilyRose said:**
> 
One problem that I am having right now is regarding installing .deb files. While installing via the command line using dpkg works fine, double clicking ends with an "The action cannot be completed." and more details gives the following error:

I'm currently filing bugs against the Gnome package manager 'packagekit', one of them is your issue too, you can add yourself to the bug or comment if you like:
[LIST]
[*]Local deb package cannot be installed by double clicking it [bug#1059600]("https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1059600")
[*]I cannot re-install a package from packagekit [bug#1059077]("https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1059077")
[*]Cannot lock package version from packagekit [bug#1059072]("https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1059072")
[*]I cannot switch server from within package-kit [bug#1059081]("https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1059081")
[/LIST]
Anyone that would like packagekit to be as feature-full as synaptic please add yourselves to the above bugs and comment if you like :)

---

### Post by Fitoschido on 2012-10-01
> **Stinger said:**
> Anyone that would like packagekit to be as feature-full as synaptic please add yourselves to the above bugs and comment if you like :)

That won't happen, GNOME is "redesigning" (read: dumbing-down) all these apps so expect less features :/

---

### Post by Stinger on 2012-10-01
> **Fitoschido said:**
> That won't happen, GNOME is "redesigning" (read: dumbing-down) all these apps so expect less features :/
Well I could be sitting around with my thumb up my a.. but that  won't happen either :-P

---

### Post by stoneguy on 2012-10-01
> **Stinger said:**
> Or open terminal. Type, system-config-printer , press enter and then add printer.
should give the same result

That did the trick. Thx.

---

### Post by tsger on 2012-10-01
Very cool, but I cannot add a new imap account to Evolution.

---

### Post by kansasnoob on 2012-10-01
I really have to say ........... WOW!

I haven't been this impressed with anything new in a very long time :guitar:

I'll grant you that I stumbled upon two problems with "gdm":

[http://ubuntuforums.org/showthread.php?t=2064778](http://ubuntuforums.org/showthread.php?t=2064778)

And I fumbled just a bit with a few configuration changes, but I find this "spin" of Gnome Shell quite usable - at least as much so as Unity - but I'm the most impressed with the Classic (no effects) session using plain old Metacity :)

I haven't bothered with running any actual benchmark testing but, from a pure usability standpoint, this is blazing fast on my old VIA hardware:

> VIA C7 CPU @ 1500MHz
VIA CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)
VIA VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
1GB DDR2 RAM

Don't get me wrong. Either Lubuntu or Xubuntu also run well enough on that hardware, but I fell in love with Gnome during Ubuntu Gutsy :)

In fact 7.10 and 9.04 were my all time favorite Ubuntu's based on overall performance - this could easily become number three on the list :D

I'm still fiddling with theming but:

[ATTACH]224965[/ATTACH]

Not great but I've only started playing.

I just want to express my heartfelt thanks to Jeremy Bicha and everyone else involved for building this \\:D/

---

### Post by Chdslv on 2012-10-02
Kansasnoob,

Don't get me wrong, but what if one just install Gnome 3.6 using Synaptic? Once, you have everything you need installed in 12.10 and got rid of other apps you don't need, you could just go to Synaptic, reload it and install gnome-shell and synaptic would give you Gnome 3.6. Then log out and you'd find Gnome in the Unity-Greeter. 

Believe me, I am not saying anything against your remix, but anyone, who has 12.10 (latest) could install Gnome-shell in the background while working on something else. Hope you don't mind my saying this.

Gnome-panel is there, so any one could install Gnome-Classic, Enlightenment is there too. Kubuntu, Lubuntu, Xubuntu DEs are there too, KDE, LXDE, XFCE4 is there too. Cinnamon and Mate are not there, but if you include Mint repos, or Clem's repos, that too could be installed. 

**PS: I am not belittling/criticizing anyone. I saw what's there in the 12.10 repos.**

---

### Post by DisappearingOak on 2012-10-02
I'm having a problem with Gnome Remix where at boot, when the Plymouth is supposed to show, the monitor goes into standby mode until the display manager loads. So I'm not able to see the bootsplash.

---

### Post by Mr.JJ on 2012-10-02
> **Fitoschido said:**
> That won't happen, GNOME is &quot;redesigning&quot; (read: dumbing-down) all these apps so expect less features :/

If you hate gnome, just don't use it. And what are you doing on a gnome remix beta thread, anyway? May be this is not your 'more features added by the minute' desktop thread. 

But if you are really interested to know how wonderful applications could be designed (and do not look like some pgmers, like me, spend an afternoon throwing all the widgets into a window with their eyes closed), go check the tentative design in this page: [https://live.gnome.org/Design/Apps/Software](https://live.gnome.org/Design/Apps/Software)

---

### Post by Mr.JJ on 2012-10-02
> **Stinger said:**
> I'm currently filing bugs against the Gnome package manager 'packagekit', one of them is your issue too, you can add yourself to the bug or comment if you like

Added a me too for the deb bug. 

I did not yet get the new plymouth and grub themes. I wonder if it is added to the default repo or one of the ricotz repos. Anyone else do not see those changes, yet?

---

### Post by kansasnoob on 2012-10-02
> **Chdslv said:**
> Kansasnoob,

Don't get me wrong, but what if one just install Gnome 3.6 using Synaptic? Once, you have everything you need installed in 12.10 and got rid of other apps you don't need, you could just go to Synaptic, reload it and install gnome-shell and synaptic would give you Gnome 3.6. Then log out and you'd find Gnome in the Unity-Greeter. 

Believe me, I am not saying anything against your remix, but anyone, who has 12.10 (latest) could install Gnome-shell in the background while working on something else. Hope you don't mind my saying this.

Gnome-panel is there, so any one could install Gnome-Classic, Enlightenment is there too. Kubuntu, Lubuntu, Xubuntu DEs are there too, KDE, LXDE, XFCE4 is there too. Cinnamon and Mate are not there, but if you include Mint repos, or Clem's repos, that too could be installed. 

**PS: I am not belittling/criticizing anyone. I saw what's there in the 12.10 repos.**

I know how to set up a classic DE, I even made these notes:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

But since Ubuntu dropped Unity-2D and Metacity in favor of Compiz + llvmpipe the aforementioned old VIA hardware is a total no-go with Ubuntu Quantal :(

Another out-of-box huge difference between using "ubuntu-desktop" and "ubuntu-gnome-desktop" is the default settings. Since this spin has no Unity and no Compiz it's much easier to get the intended pure Gnome experience.

This really is as close to pure gnome as one can get, right down to the choice of browsers and package managers, so I'd think it would be very useful for the gnome devs themselves also :)

---

### Post by Stinger on 2012-10-02
If any of you guys and girls use [Ubuntu-tweak]("http://ubuntu-tweak.com/"), you'll be thrilled to hear that soon we'll have Ubuntu-tweak-Gnome without the compiz dependencies.
I filed a bug against Ubuntu-tweak and got a very positive response \\:D/
[Bug#1059067]("https://bugs.launchpad.net/ubuntu-tweak/+bug/1059067")

---

### Post by x-shaney-x on 2012-10-02
Just wondering... it has been mentioned it is a *mostly* pure gnome experience.
What compromises have been made that stop it being a completely gnome experience?
Not so much individual apps but as a whole?

---

### Post by Mr.JJ on 2012-10-03
> **x-shaney-x said:**
> What compromises have been made that stop it being a completely gnome experience?
Not so much individual apps but as a whole?

In the core side, the control center comes to mind. That is not updated to the 3.6 version and currently is a highly pached (by ubuntu) 3.4 version.
Coming to the applications side, nautilus, totem, gstreamer etc. are old versions (you have to add gnome 3 ppa to get the new versions). Gnome documents, boxes and the new clock applications are not installed.

---

### Post by Harry33 on 2012-10-03
Gnome Remix is using the same official repositories that also Ubuntu Desktop uses.
Certain packages are not installed on the Gnome Remix setup (for example Unity DE) and some packages are not installed on the default Ubuntu Desktop (for example Gnome-shell DE).

However, vast majority of the packages are same and a number of them are specially Ubuntu patched packages.

---

### Post by bmbaker on 2012-10-03
for anyone having corrupted graphics or no mouse using the live-session i found this wks:
boot into a live session setup your wifi-network
switch to virtual terminal (strg-alt-F2)
enter

```
sudo apt-get update 
sudo apt-get upgrade ubiquity
```

when its finished 

```
sudo service gdm stop
sudo service gdm start
```

cheers BB

---

### Post by jbicha on 2012-10-03
> **Mr.JJ said:**
> In the core side, the control center comes to mind. That is not updated to the 3.6 version and currently is a highly pached (by ubuntu) 3.4 version.
Coming to the applications side, nautilus, totem, gstreamer etc. are old versions (you have to add gnome 3 ppa to get the new versions). Gnome documents, boxes and the new clock applications are not installed.

The latest gstreamer is available in the regular Ubuntu repositories; it's just that no package in main will be using it until next cycle.

Clocks is not considered to be part of GNOME 3.6; I don't think Fedora 18 will include it by default. On the other hand, it's a small package so we can take it or leave it. What do you think? It's pretty lousy as an alarm clock as the "ringtone" isn't customizable and the app has to be running; they haven't built a system service yet.

---

### Post by markbl on 2012-10-03
> **Harry33 said:**
> Gnome Remix is using the same official repositories that also Ubuntu Desktop uses.
Certain packages are not installed on the Gnome Remix setup (for example Unity DE) and some packages are not installed on the default Ubuntu Desktop (for example Gnome-shell DE).

However, vast majority of the packages are same and a number of them are specially Ubuntu patched packages.
So what is the difference between using Gnome Remix, and using a standard Ubuntu install plus the gnome 3 ppa + installing gnome-shell?

---

### Post by x-shaney-x on 2012-10-03
> **markbl said:**
> So what is the difference between using Gnome Remix, and using a standard Ubuntu install plus the gnome 3 ppa + installing gnome-shell?

Presumably you would then still have the ubuntu/unity stuff and defaults.  The gnome stuff would be an addition to rather than instead of.

---

### Post by Mr.JJ on 2012-10-03
> **jbicha said:**
> Clocks is not considered to be part of GNOME 3.6; On the other hand, it's a small package so we can take it or leave it. What do you think? 

 Clocks is more of an alpha/preview release this cycle, just like boxes were last time. Thats the reason it is not officially considered to be part of this cycle.

At the same time, it is interesting in its own right. The world clocks is awesome. You add the cities, and just open it in those 'what time is it in there' moments. This is very handy, especially if you are interacting with an international team etc. Also, with usual alarm, stopwatch, and timer, it is a nice utility to have. Currently, there are no other applications that provides these services. And the application isn't really alpha quality. So, we could include that by default, if no space constraints.

---

### Post by markbl on 2012-10-03
> **x-shaney-x said:**
> Presumably you would then still have the ubuntu/unity stuff and defaults.  The gnome stuff would be an addition to rather than instead of.
Of course I realise that gnome remix has the disadvantage that I don't have the option to log out of gnome shell to try out unity. But I was asking what the advantage of gnome remix is compared to standard ubuntu install + add-apt-repository ppa:gnome3-team/gnome3 + apt-get install gnome-shell.

Seriously, why does gnome remix exist? What does it give us ubuntu gnome-shell users over a standard ubuntu install?

---

### Post by x-shaney-x on 2012-10-03
> **markbl said:**
> Of course I realise that gnome remix has the disadvantage that I don't have the option to log out of gnome shell to try out unity. But I was asking what the advantage of gnome remix is compared to standard ubuntu install + add-apt-repository ppa:gnome3-team/gnome3 + apt-get install gnome-shell.

Seriously, why does gnome remix exist? What does it give us ubuntu gnome-shell users over a standard ubuntu install?

If you already have regular ubuntu them maybe there isn't a lot of point and you can get pretty much the same results yourself, as you said.

I think it is more aimed as an alternative as an installation.
For example, you could easily turn an ubuntu install into kubuntu, lubuntu, xubuntu etc but if you prefer lxde or kde to unity, you aren't likely to install regular ubuntu to then start installing kde etc, you would just install the ubuntu flavour that suits?

It's the same with ubuntu gnome. If you want gnome rather than unity, what's the point of installing ubuntu+ unity to then install gnome afterwards if you can just install ubuntu+gnome from the start?

Remember that when gnome remix is a final release, it will be in line with all the other 12.10 releases so just gives users that other option.

I for one, will be installing gnome remix without a doubt so I am grateful for the work being done here, if I do indeed go for ubuntu.

---

### Post by jbicha on 2012-10-03
> **markbl said:**
> Of course I realise that gnome remix has the disadvantage that I don't have the option to log out of gnome shell to try out unity. But I was asking what the advantage of gnome remix is compared to standard ubuntu install + add-apt-repository ppa:gnome3-team/gnome3 + apt-get install gnome-shell.

Seriously, why does gnome remix exist? What does it give us ubuntu gnome-shell users over a standard ubuntu install?

The Ubuntu GNOME Remix doesn't include the GNOME3 PPA by default so you don't need that.

To get the same result, you could install ubuntu-gnome-desktop and uninstall ubuntu-settings and ubuntu-artwork (as that includes Ubuntu-specific overrides such as having Nautilus handle the desktop, and theme stuff). Make sure to set gdm as default instead of lightdm.

Why does Kubuntu exist? Why does Lubuntu?

Additional advantages of the Ubuntu GNOME Remix:

[LIST]
[*]The GNOME experience is more pure than it was in 12.04 LTS and I believe it will even better in 13.04.
[*]Our work also makes it easier for other derivatives to choose the GNOME settings they wish to override without needing to patch a dozen packages.
[*]I'm tired of hearing new GNOME contributors being told to use Fedora instead of Ubuntu, especially as generally I've found Ubuntu+1 to be more reliable than Rawhide. It's a bad thing if the majority of users are using a distro that developers aren't. For instance, I believe Boxes was broken during much of this cycle; if there were Boxes developers using Ubuntu, maybe it wouldn't have been.
[*]If we become an official Ubuntu flavor, then we have at least a bit more influence with Ubuntu for our goal of shipping the latest GNOME as pure as possible.
[/LIST]

---

### Post by markbl on 2012-10-03
Thanks for your response Jeremy. I appreciate your efforts.

I **much** prefer Ubuntu over RH/Fedora but happen to prefer GNOME shell over Unity so I am very glad you are striving to maintain gnome-shell/ubuntu compatibility.

---

### Post by Harry33 on 2012-10-04
Gnome-control-center 3.6.0 and gnome-settings-daemon 3.6.0 could very well be uploaded to the GNOME3 PPA:
 - Ubuntu official repos still have the old 3.4.2
 - version 3.6.0 issues are with Unity, not with Gnome-shell
 - version 3.6.0 with Gnome Remix would then be more Gnome.

---

### Post by Mr.JJ on 2012-10-04
> **Harry33 said:**
> Gnome-control-center 3.6.0 and gnome-settings-daemon 3.6.0 could very well be uploaded to the GNOME3 PPA:
 - Ubuntu official repos still have the old 3.4.2
 - version 3.6.0 issues are with Unity, not with Gnome-shell
 - version 3.6.0 with Gnome Remix would then be more Gnome.

 Just to add to that, I added the staging ppa (without the testing ppa) and control-center and settings-daemon (were upgraded and) works fine. All in support/vote for moving these to gnome3 ppa, if there are no other major issues (Jeremy already said he will get it into gnome3 ppa, but let's all force him to do it fast).

---

### Post by Stinger on 2012-10-04
@Mr.JJ
Why are you so busy forcing Jeremy ? Just use the staging ppa if it's important to you.
See if you can find a way to contribute instead.
If you are a launchpad member you could make a bugreport instead and everyone who agrees with you can mark them selves as affected.

---

### Post by Mr.JJ on 2012-10-04
> **Stinger said:**
> @Mr.JJ
Why are you so busy forcing Jeremy ?  May be you dont understand the concept of community distros. The community, to a certain extend, has the power to 'influence' the decisions taken on community distros. If there are enough requests of a feature, chances are that it will get implemented.
No one is forcing Jeremy in 'literal' sense (That was a light-heated end note. And I used the word vote, if you didn't notice). It is of course his discretion. At the same time he cannot guess or assume what the user/community needs. As users we should help him to understand the needs of the community. And forums are the best platform to do this (with discussions/opinions from diff. users etc.). I don't see any issues with that. And Jeremy for his part has always shown interest to know our preferences. I hope Jeremy will reply with his views on this.
> **Stinger said:**
>  Just use the staging ppa if it's important to you. 
It is evident that you didn't read my comment. My comment is only two sentences and the first sentence clearly says I AM USING THE STAGING PPA. 
The purpose of a community distro is to reach common grounds on the community requirements. It is about what the community wants. Not 'you' or 'I' as individuals, but the majority. With your logic, there is no point for Ubuntu gnome remix itself. Let users add the repos and install the packages, done. But my view is, unless there are technical or other restrictions, there is no point in keeping features away from the community, especially if there is a need. And I have already explained why I don't feel confident in using the staging ppa for day to day work.
> **Stinger said:**
> If you are a launchpad member you could make a bugreport instead and everyone who agrees with you can mark them selves as affected.

This is not a bug to begin with (I do have almost 12 issues raised in bugzilla against gnome 3.6 itself, please don't comment about things which you don't have any idea about.). The developers know about it and the decision is already made. It is just a matter of time, there is no point in raising a bug report. But if Jeremy wants it, I could do that, no probs.

You seem to be seriously limited on the language side (reading many of your responses). Many a time, you seem to get it all wrong about the intended tone or context of a particular comment etc. So, I leave your response as a mistake and ignorant than as purposeful.

---

### Post by cariboo on 2012-10-04
Could we please keep this on topic, instead of sniping at each other.

---

### Post by Stinger on 2012-10-04
> **EmilyRose said:**
> 
One problem that I am having right now is regarding installing .deb files. While installing via the command line using dpkg works fine, double clicking ends with an "The action cannot be completed." and more details gives the following error:
My Bug reports regarding packagekit, [bug#1059600]("https://bugs.launchpad.net/ubuntu/+source/gnome-packagekit/+bug/1059600"), which actually is a sessioninstaller bug, and [bug#1060395]("https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/1060395"), which was a packagekit bug, has given the following workaround until the sessioninstaller bug is fixed.

If you need to install a local package and want to try packagekit
[LIST]
[*]remove the sessioninstaller package
[*]install the gdebi-core and gnome-packagekit-tools packages and reboot
[*]check the menu entry for the softwareinstaller, as you can see in my screenshot, it should say 'gpk-install-local-file %F' and NOT 'gksu gpk-install-local-file %F', if it does, remove gksu and close the menu (packagekit does not need to be run as super user).
[*]Now you should be able to install local packages by double clicking them ;)
[/LIST]
when you are finished you can install the sessioninstaller again (you'll need it for codecs in Totem).

---

### Post by kansasnoob on 2012-10-04
> **cariboo907 said:**
> Could we please keep this on topic, instead of sniping at each other.

In deed :)

This project is almost certain to reach fruition since "ubuntu-gnome-desktop" is now in the repos.

Those who don't like it, or don't care about it, should just ignore it.

Use whatever you like, just don't drop bombs on the stuff you don't like :D

How boring would it be if we had only one option :confused:

---

### Post by jbicha on 2012-10-04
> **Harry33 said:**
> Gnome-control-center 3.6.0 and gnome-settings-daemon 3.6.0 could very well be uploaded to the GNOME3 PPA:
 - Ubuntu official repos still have the old 3.4.2
 - version 3.6.0 issues are with Unity, not with Gnome-shell
 - version 3.6.0 with Gnome Remix would then be more Gnome.

Bummer, I had a much longer reply written out (with reasons) but didn't hit "Submit" and then I thought I'd log out of GNOME to see what the latest Unity updates did. I'll try to reply later if I'm not too busy, but basically, I won't be adding gnome-control-center and gnome-settings-daemon to the official GNOME3 PPA. They have a very real chance of breaking Unity.

You can find some related thoughts at [bug 1045914]("http://pad.lv/1045914").

---

### Post by Harry33 on 2012-10-05
We have another, more serious issue with Ubuntu 12.10 now, and concerning Unity.

The latest libunity9 package (6.8.0-0ubuntu1) depends on unity-common now.
    
> Depends on:
[LIST]
[*]                  [             dconf-gsettings-backend                       ]("https://launchpad.net/ubuntu/quantal/amd64/dconf-gsettings-backend")
[*]                  [             libc6                            (>=                2.2.5)                       ]("https://launchpad.net/ubuntu/quantal/amd64/libc6")
[*]                  [             libdbusmenu-glib4                            (>=                0.4.2)                       ]("https://launchpad.net/ubuntu/quantal/amd64/libdbusmenu-glib4")
[*]                  [             libdee-1.0-4                            (>=                0.5.12)                       ]("https://launchpad.net/ubuntu/quantal/amd64/libdee-1.0-4")
[*]                  [             libgee2                            (>=                0.5.0)                       ]("https://launchpad.net/ubuntu/quantal/amd64/libgee2")
[*]                  [             libglib2.0-0                            (>=                2.32.1)                       ]("https://launchpad.net/ubuntu/quantal/amd64/libglib2.0-0")
[*]                  [             libunity-protocol-private0                            (>=                6.8.0)                       ]("https://launchpad.net/ubuntu/quantal/amd64/libunity-protocol-private0")
[*]                  [             unity-common                            (>=                6.0.0-0ubuntu3)                       ]("https://launchpad.net/ubuntu/quantal/amd64/unity-common")
[/LIST]
This is due to the fact that Unity may crash if unity-common is not installed.

OK, but what happens now:
If we, who use ununtu-gnome-remix, and perhaps do not use unity at all, now upgrade to the libunity_6.8.0, we get unity-common and compiz with all its dependencies installed too.
This is because unity-common depends on compiz-gnome

> Depends on:
[LIST]
[*]                  [             compiz-gnome                            (>>                1:0.9.8+bzr3319)                       ]("https://launchpad.net/ubuntu/quantal/i386/compiz-gnome")
[*]                  [             dconf-gsettings-backen                       ]("https://launchpad.net/ubuntu/quantal/i386/dconf-gsettings-backend")
[/LIST]
  
And compiz-gnome in turn depends on a number of compiz related stuff.

    > Depends on:
[LIST]
[*]                  [             compiz-plugins-default                            (=                1:0.9.8.4-0ubuntu1)                       ]("https://launchpad.net/ubuntu/quantal/i386/compiz-plugins-default")
[*]                  [             dconf-gsettings-backend                       ]("https://launchpad.net/ubuntu/quantal/i386/dconf-gsettings-backend")
[*]                  [             gconf2                            (>=                2.28.1-2)                       ]("https://launchpad.net/ubuntu/quantal/i386/gconf2")
[*]                  [             gnome-settings-daemon                            (>=                3.4.2-0ubuntu9)                       ]("https://launchpad.net/ubuntu/quantal/i386/gnome-settings-daemon")
[*]                  [             gsettings-desktop-schemas                       ]("https://launchpad.net/ubuntu/quantal/i386/gsettings-desktop-schemas")
[*]                  [             libatk1.0-0                            (>=                1.12.4)                       ]("https://launchpad.net/ubuntu/quantal/i386/libatk1.0-0")
[*]                  [             libc6                            (>=                2.7)                       ]("https://launchpad.net/ubuntu/quantal/i386/libc6")
[*]                  [             libcairo2                            (>=                1.2.4)                       ]("https://launchpad.net/ubuntu/quantal/i386/libcairo2")
[*]                  [             libcompizconfig0                       ]("https://launchpad.net/ubuntu/quantal/i386/libcompizconfig0")
[*]                  [             libdecoration0                            (>=                1:0.9.8.2)                       ]("https://launchpad.net/ubuntu/quantal/i386/libdecoration0")
[*]                  [             libgdk-pixbuf2.0-0                            (>=                2.22.0)                       ]("https://launchpad.net/ubuntu/quantal/i386/libgdk-pixbuf2.0-0")
[*]                  [             libglib2.0-0                            (>=                2.28.0)                       ]("https://launchpad.net/ubuntu/quantal/i386/libglib2.0-0")
[*]                  [             libgtk2.0-0                            (>=                2.24.0)                       ]("https://launchpad.net/ubuntu/quantal/i386/libgtk2.0-0")
[*]                  [             libmetacity-private0a                            (>=                1:2.34.0)                       ]("https://launchpad.net/ubuntu/quantal/i386/libmetacity-private0a")
[*]                  [             libpango1.0-0                            (>=                1.14.0)                       ]("https://launchpad.net/ubuntu/quantal/i386/libpango1.0-0")
[*]                  [             libwnck22                            (>=                1:2.22)                       ]("https://launchpad.net/ubuntu/quantal/i386/libwnck22")
[*]                  [             libx11-6                       ]("https://launchpad.net/ubuntu/quantal/i386/libx11-6")
[*]                  [             libxrender1                       ]("https://launchpad.net/ubuntu/quantal/i386/libxrender1")
[*]                  [             session-migration                       ]("https://launchpad.net/ubuntu/quantal/i386/session-migration")
[/LIST]
The main issues here is that ubuntu-gnome-remix uses Nautilus, that is built against libunity9 and it depends on it.
If that dependency would be lowered to recommends or suggests, there would not be any issues, because users who would have only Gnome-shell DE installed could then remove libunity9.

So where can I find nautilus, that does not depend on libunity9?
Gnome3 PPA perhaps?
How about that Jeremy?

---

### Post by mc4man on 2012-10-05
> **Harry33 said:**
> 
So where can I find nautilus, that does not depend on libunity9?
Gnome3 PPA perhaps?
How about that Jeremy?
I would think that ppa is hesitant to provide builds that break unity though probably in the case of libunity it's more the unity launcher support, not anything broken
(bookmarks auto added to  nautilus launcher's quicklists, ect.

I typically use a git nautilus here on unity, sometime with, most times without the support patch, ie. no dep on libunity. No big loss, can be added to the .desktop but may be enough to disallow doing in _that_ ppa.

(Ot - naut 3.6 going to 3.6.1 breaks unity launcher use on this seemingly insig. commit
[http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16646#src/nautilus-application.c](http://bazaar.launchpad.net/~vcs-imports/nautilus/master-git/revision/16646#src/nautilus-application.c)

---

### Post by DisappearingOak on 2012-10-05
I was wondering.. I saw an article about Gnome's new Software Center and wondering if it will be included in uGuntu? :)

---

### Post by Stinger on 2012-10-05
@Harry33
I see your point, it would need some creative thinking from Jeremy to fix this one, a real 'dealbreaker' :(

from the [Change logs for “libunity” source package in Quantal]("https://launchpad.net/ubuntu/quantal/+source/libunity/+changelog"):
> [ Dmitry Shachnev ]
  * Make libunity9 depend on unity-common >= 6.0.0-0ubuntu3 ([LP: #1055019]("https://bugs.launchpad.net/ubuntu/+source/libunity/+bug/1055019")).

I think this proves the need for the 'Ubuntu Gnome Remix' to have it's own packages as I have said earlier ( like Xubuntu, Lubuntu... etc ).
The Ubuntu packages will most likely be more and more tangled up with Unity

---

### Post by Stinger on 2012-10-05
> **DisappearingOak said:**
> I was wondering.. I saw an article about Gnome's new Software Center and wondering if it will be included in uGuntu? :)
Yeah I have seen it too, the [Gnome App Center]("http://worldofgnome.org/gnome-is-ready-to-unleash-the-beast-an-app-center/")
Gnome developers are still working on it and it may be included in Gnome 3.8, looks very promising ;)

---

### Post by jbicha on 2012-10-05
Thanks Harry for noticing the libunity9 problem. I've reported [bug 1062099]("http://pad.lv/1062099") and it is being worked on.

> **Stinger said:**
> 
I think this proves the need for the 'Ubuntu Gnome Remix' to have it's own packages as I have said earlier ( like Xubuntu, Lubuntu... etc ).
The Ubuntu packages will most likely be more and more tangled up with Unity

I think you severely underestimate the complications that would cause.

---

### Post by Stinger on 2012-10-05
> **jbicha said:**
> 
I think you severely underestimate the complications that would cause.
Yeah you are right, it's more an idea from my perspective, I know it would be a complicated process and involve a lot of resources.
It just makes me sad to see that every time Unity has needs, we, the Gnome fans, have to settle for a less favorable solution. :(

---

### Post by Stinger on 2012-10-05
> **Harry33 said:**
> We have another, more serious issue with Ubuntu 12.10 now, and concerning Unity.

The latest libunity9 package (6.8.0-0ubuntu1) depends on unity-common now.
    
This is due to the fact that Unity may crash if unity-common is not installed.

OK, but what happens now:
If we, who use ununtu-gnome-remix, and perhaps do not use unity at all, now upgrade to the libunity_6.8.0, we get unity-common and compiz with all its dependencies installed too.
This is because unity-common depends on compiz-gnome

And compiz-gnome in turn depends on a number of compiz related stuff.

    The main issues here is that ubuntu-gnome-remix uses Nautilus, that is built against libunity9 and it depends on it.
If that dependency would be lowered to recommends or suggests, there would not be any issues, because users who would have only Gnome-shell DE installed could then remove libunity9.

So where can I find nautilus, that does not depend on libunity9?
Gnome3 PPA perhaps?
How about that Jeremy?
Phew the developers worked fast to fix this one :D
Quoted from the changelog:
> Changelog
libunity (6.8.0-0ubuntu2) quantal; urgency=low

  [ &#321;ukasz 'sil2100' Zemczak ]
  * Cherry-picked from upstream.
    - libunity9 now depends on unity-common which depends on compiz
      (LP: #1062099)
    - Build failure: be tolerant of missing GSettings (LP: #973518 )
  * debian/control:
    - Remove dependency to unity-common, as now we're more fault-tolerant
      about missing schemas

  [ Didier Roche ]
  * debian/control:
    - Actually, downgrade it rather to suggests.
 -- Didier Roche <didrocks@ubuntu.com>   Fri, 05 Oct 2012 15:49:08 +0200
You can now upgrade safely again
Thanks to the developers for fixing this so quickly.

---

### Post by DangerMouseUK on 2012-10-05
Hi guys,

Thanks to all involved in making this remix - finally answered my search for the right distro for me.

I'm going to hop onto IRC sooner or later and get involved in helping out if I can.

For now a quick question - I selected auto-login during the initial setup and now it won't turn off. Logging out just logs me back in straight away.

I know its a known issue on the Wiki page - but I can't seem to turn off autologin - it says off, but it still automatically logs me in anyway.

Thanks
DM

---

### Post by kansasnoob on 2012-10-05
> **DangerMouseUK said:**
> Hi guys,

Thanks to all involved in making this remix - finally answered my search for the right distro for me.

I'm going to hop onto IRC sooner or later and get involved in helping out if I can.

For now a quick question - I selected auto-login during the initial setup and now it won't turn off. Logging out just logs me back in straight away.

I know its a known issue on the Wiki page - but I can't seem to turn off autologin - it says off, but it still automatically logs me in anyway.

Thanks
DM

Have a browse here:

[http://ubuntuforums.org/showthread.php?t=2064778](http://ubuntuforums.org/showthread.php?t=2064778)

I really should file bugs I guess :(

---

### Post by DangerMouseUK on 2012-10-06
Heh - it's cool bro :) Gonna go and edit the config files now and see if I can get my login screen back :)

---

### Post by DisappearingOak on 2012-10-06
Hi, I'm on the beta and have a problem where, in Brightness and Lock, I've set Turn off screen to Never and Lock to Off, and in Power Settings, I've set Suspend to 'Don't Suspend'. But when there's inactivity, monitor goes to standby mode still after 15 minutes, so the settings don't seem to be working. How do I fix this?

---

### Post by kansasnoob on 2012-10-07
Just thought I'd add a couple of links to the gdm related problems:

[http://ubuntuforums.org/showthread.php?p=12282492#post12282492](http://ubuntuforums.org/showthread.php?p=12282492#post12282492)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1063267](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1063267)

Basically with the version of gdm in Ricotz staging, along with all packages from Ricotz testing/staging and the Gnome 3 PPA, gdm now obeys the settings applied in System Settings.

But log out still does NOT work if you have auto-login set ;)

Sorry I can't be of more help, my abilities are just limited ATM :)

---

### Post by DangerMouseUK on 2012-10-07
Hey bro, I purged the ricotz PPA's and now it all seems to be working which is strange - I didn't even edit anything. Just thought I'd do a cleanup before editing.

Weird ! All I did was purge the staging and testing PPAs and it replaced the packages and hey presto - all working :-s
 
I also purged them because changing brightness on my laptop caused the window manager to crash with the staging and testing PPAs should really file some bugs on that one.

---

### Post by DisappearingOak on 2012-10-08
Another problem: Starting Gnome tweak tool from terminal, if I use the automatic install for shell themes, it says installed successfully and lists the new theme but the theme doesn't work. Manually installing the archive to /home/.themes works though, but the tweak tool installer is broken.

Also there seems to be a problem with rhythmbox, if I maximize it and then double click the title bar to restore it, it won't restore, then i have to drag the titlebar down to restore it but the window size stays the same as in maximized state. This happens a lot for me.

---

### Post by Stinger on 2012-10-09
OK, we just got another goodie, Epiphany/Web just got updated to 3.6.0 (webkit 1.10.0), please give it a spin ;)
Ubuntu now has the most complete and stable Gnome 3.6 AFAIK, great :D
Thanks to Jeremy and all other developers involved.

---

### Post by kansasnoob on 2012-10-09
> **Stinger said:**
> OK, we just got another goodie, Epiphany/Web just got updated to 3.6.0 (webkit 1.10.0), please give it a spin ;)
Ubuntu now has the most complete and stable Gnome 3.6 AFAIK, great :D
Thanks to Jeremy and all other developers involved.

I don't use Epiphany ......... erm, I have an old bloated 1+ GB .mozilla folder that's been following me around for over a decade :redface:

But for sure, once you have gdm working properly (or switch to lightdm) this is the best experience I've had with gnome-shell.

And what really makes it great is that classic + metacity runs just wonderfully on low spec hardware :guitar:

---

### Post by Stinger on 2012-10-12
Hi all
I'm trying to sum up the bugs in Ubuntu GNOME Remix that's not fixed yet to make some more reports.

[LIST]
[*]I cannot access 'suspend' or 'hibernate' from the shell menu's

[*]The timer/spinner keeps spinning for a while when launching Nautilus from the menu/launcher. (If you look closer in the menu, Nautilus is launched with the '%U' parameter, 'nautilus %U').
If I launch nautilus from terminal (no %U) or remove %U from the menu, Nautilus just instantly springs into action.
[/LIST]

If you have other bugs that need attention please report them here I'll try to se if I can reproduce and make a report on launchpad, or better yet make a bug report on launchpad yourselves.

Lets make this release as stable as possible :D

---

### Post by Hazzabin on 2012-10-14
In Gnome Classic for some reason I've got duplicated top panel, any ideas how to fix.....I don't think it's a "bug"


Hazz

---

### Post by tista on 2012-10-15
> **Hazzabin said:**
> In Gnome Classic for some reason I've got duplicated top panel, any ideas how to fix.....I don't think it's a "bug"


Hazz

Hi Hazzabin ;)

Means "A panel is covered with an another panel?"
So check them out now:

1. What number of processes were running as gnome-panel?
2. Is there anything unexpected "startup applications" to kick gnome-panel off?
3. /usr/share/gnome-session/sessions/gnome-classic.session is normal?

Generally, gnome-panel must be kicked by gnome-session requirements order like #3 file instead of any kind of startup applications.

4. If unfortunately bottom-panel had been moved to top, then remove it.

Best Regards,
Tista

---

### Post by x-shaney-x on 2012-10-16
Just a quick question regarding the Gnome 3 and Ricotz PPA's.

Are these PPA's actually discouraged for use with UNR or are they encouraged as to improve the Gnome experience more?

I know there are issues with certain packages but I was earlier under the impression the PPA's are kind of meant to be used almost but now I'm feeling that's not the case?

---

### Post by x-shaney-x on 2012-10-16
Oh and another question, this time regarding GDM:

With KDM and LightDM, the last logged in user is at the login prompt with the password field focused, meaning the user simply has to type the password as soon as they get to login screen.

I noticed using GDM in Kororaa, I had the extra step of having to click the user or press enter, THEN enter the password. An extra step.

On UGR, I can't even press enter, I have to do tab, THEN enter, THEN the password or go to the mouse again to click.
So up to TWO extra steps.  Even when there is only one user.
I think at the very least there user's password entry should be focused if there is only one user?

Is this behaviour likely to change?

---

### Post by jbicha on 2012-10-16
> **x-shaney-x said:**
> 
I think at the very least there user's password entry should be focused if there is only one user?

Is this behaviour likely to change?

Yes, I believe that's a bug.

---

### Post by Stinger on 2012-10-16
> **x-shaney-x said:**
> Just a quick question regarding the Gnome 3 and Ricotz PPA's.

Are these PPA's actually discouraged for use with UNR or are they encouraged as to improve the Gnome experience more?

I know there are issues with certain packages but I was earlier under the impression the PPA's are kind of meant to be used almost but now I'm feeling that's not the case?
You only need the [Gnome3 ppa]("https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=quantal") to have a complete Gnome 3.6 experience as it says [here]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta?action=show&redirect=UbuntuGNOME%2FReleaseNotes#What.27s_Not_Included").
You can also see there are a few issues with 'System Settings' that needs attention. 
> A separate ubuntu-control-center will not make it into Ubuntu 12.10 but is still a goal for 13.04.

My install is working just fine with the Gnome3 ppa :)

---

### Post by jbicha on 2012-10-16
> **jbicha said:**
> Yes, I believe that's a bug.

And that's fixed in gnome-shell 3.6.1 which has been uploaded as a Stable Release Update.

---

### Post by Stinger on 2012-10-16
> **jbicha said:**
> And that's fixed in gnome-shell 3.6.1 which has been uploaded as a Stable Release Update.
Great, I was just about to ask how the status was for Gnome 3.6.1 in Ubuntu, I can strike that from my list now :lol:

---

### Post by mc4man on 2012-10-16
I'd assume the gnome3 ppa will be doing a Videos(Totem) upgrade soon, that would be a good thing, were some recent fixes to grilo (youtube) & the mozilla plugin (mov, mp4)  that resolved standing issues.

If it goes to nautilus-3.6.1 then the probable break in unity should be checked & fixed one way or the other. (if still applicable, was the other day or so.

---

### Post by bmbaker on 2012-10-16
was just checking [http://git.gnome.org/browse/gdm/](http://git.gnome.org/browse/gdm/)
and wondering if we will get a GDM update too :-):-)

---

### Post by x-shaney-x on 2012-10-16
> **jbicha said:**
> And that's fixed in gnome-shell 3.6.1 which has been uploaded as a Stable Release Update.

Indeed. Just updated and now can just press enter and password.
Still not as easy as having the password box focused but maybe I'm just picky (and lazy).

Just wondering on the status of auto-login?
I haven't used auto-login for some years and I have been reading of problems with it?
The odd bits of changelogs I've seen suggest it might be solved (or partially).

---

### Post by jbicha on 2012-10-16
> **x-shaney-x said:**
> Still not as easy as having the password box focused but maybe I'm just picky (and lazy).


For design issues like that, your best bet is to talk to the developers, in this case either via IRC (I believe #gnome-shell or #gnome-design on irc.gnome.org) or bugzilla.gnome.org.

> **x-shaney-x said:**
> 
Just wondering on the status of auto-login?
I haven't used auto-login for some years and I have been reading of problems with it?
The odd bits of changelogs I've seen suggest it might be solved (or partially).

Autologin should be working now. If you have any problems with it, please file a Launchpad bug.

---

### Post by sgage on 2012-10-17
With the Final Release of 12.10 coming up tomorrow, will a Final Release of Gnome Remix be coming along soon?

---

### Post by smartboyhw on 2012-10-17
> **sgage said:**
> With the Final Release of 12.10 coming up tomorrow, will a Final Release of Gnome Remix be coming along soon?
Should be:D

---

### Post by x-shaney-x on 2012-10-17
I was under the impression gnome remix would be released alongside the other Ubuntu releases?

---

### Post by Stinger on 2012-10-17
If you belive the [release notes]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes"), it's gonna be released tomorrow:
> The next planned milestone release is the final release, scheduled for October 18! :D 

BTW the Gnome 3.6.1 packages are beginning to arrive, just got gdm 3.6.1 and got Gnome-shell 3.6.1 earlier today.
Maybe Jeremy want to hold the release to we have a complete Gnome 3.6.1 ? Should only be a matter of a day or a couple of days I think.
Cheers

---

### Post by jbicha on 2012-10-17
> **Stinger said:**
> 
Maybe Jeremy want to hold the release to we have a complete Gnome 3.6.1 ?

Nope, the release will be on October 18, as scheduled.

But I would really like for next October release to be after the GNOME .1 release.

---

### Post by reiga on 2012-10-18
when we can expect the release ? :popcorn:

---

