---
title: "unity8 just plain busted on yakkety daily"
date: 2016-09-13
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-09-13
Downloaded and installed yakkety  current. Installed unity8 on both nVidia and Intel based form factors.  AtM , unity8 is , well. broke, busted and just not working in any manner to test. These are installs with non-ppa updates. Will unity8 be ready for testing at the end of this cycle or will it go the way of Ubuntu_Next personal image? I do have some installs of xenial that work really well with Libertine containers etc... 

Regards..

---

### Post by ventrical on 2016-09-13
If it is any consolation to other testers of unity8 and it's current state of testability, I have contacted a developer and am awaiting a reply.

Regards..

---

### Post by enricobe on 2016-09-13
> **ventrical said:**
> If it is any consolation to other testers of unity8 and it's current state of testability, I have contacted a developer and am awaiting a reply.

Regards..

Let us know.

---

### Post by mc4man on 2016-09-13
There are 3 crashes from a Unity8 log in on Intel, atm all private bugs though possibly interrelated (egl & dri2

---

### Post by enricobe on 2016-09-13
> **mc4man said:**
> There are 3 crashes from a Unity8 log in on Intel, atm all private bugs though possibly interrelated (egl & dri2
These crashes always appears when I reboot to Unity 7.

---

### Post by mc4man on 2016-09-13
> **enricobe said:**
> These crashes always appears when I reboot to Unity 7.
It's probable that unity8 has no apport crash reporting support so you don't get the pop ups till returning to 7

---

### Post by enricobe on 2016-09-13
> **mc4man said:**
> It's probable that unity8 has no apport crash reporting support so you don't get the pop ups till returning to 7

Yes, I also think so

---

### Post by ventrical on 2016-09-13
> **mc4man said:**
> It's probable that unity8 has no apport crash reporting support so you don't get the pop ups till returning to 7

I know this much:   There was a huge xmir-video-drivers update or something of this effect and that is what crashed the scope block I think. I had to use synaptic in unity7 to get a bunch of held back updates that were not reported by using standard terminal methods.


Regards..

---

### Post by ventrical on 2016-09-13
> **enricobe said:**
> Let us know.

Will do.

---

### Post by ventrical on 2016-09-13
> **mc4man said:**
> It's probable that unity8 has no apport crash reporting support so you don't get the pop ups till returning to 7

@mac4man

Here is the synaptic log I was talking about from a yakkety install that had held back broken packages non ppa (today)

```

Commit Log for Tue Sep 13 04:26:15 2016


Upgraded the following packages:
apparmor-easyprof-ubuntu (16.10.1) to 16.10.3
appstream (0.9.8-4) to 0.9.8-4build1
bsdutils (1:2.28.1-1ubuntu1) to 1:2.28.2-1ubuntu1
click-apparmor (0.3.15) to 0.3.16
compiz (1:0.9.13.0+16.10.20160818.2-0ubuntu1) to 1:0.9.13.0+16.10.20160818.2-0ubuntu2
compiz-core (1:0.9.13.0+16.10.20160818.2-0ubuntu1) to 1:0.9.13.0+16.10.20160818.2-0ubuntu2
compiz-gnome (1:0.9.13.0+16.10.20160818.2-0ubuntu1) to 1:0.9.13.0+16.10.20160818.2-0ubuntu2
compiz-plugins-default (1:0.9.13.0+16.10.20160818.2-0ubuntu1) to 1:0.9.13.0+16.10.20160818.2-0ubuntu2
gir1.2-freedesktop (1.48.0-3ubuntu1) to 1.49.1-2ubuntu1
gir1.2-glib-2.0 (1.48.0-3ubuntu1) to 1.49.1-2ubuntu1
indicator-network (0.8.0+16.10.20160817.2-0ubuntu1) to 0.8.0+16.10.20160817.2-0ubuntu2
init (1.42) to 1.44
init-system-helpers (1.42) to 1.44
isc-dhcp-client (4.3.3-5ubuntu13) to 4.3.3-5ubuntu13.1
isc-dhcp-common (4.3.3-5ubuntu13) to 4.3.3-5ubuntu13.1
isc-dhcp-server (4.3.3-5ubuntu13) to 4.3.3-5ubuntu13.1
libappstream3 (0.9.8-4) to 0.9.8-4build1
libasn1-8-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libblkid1 (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1
libcompizconfig0 (1:0.9.13.0+16.10.20160818.2-0ubuntu1) to 1:0.9.13.0+16.10.20160818.2-0ubuntu2
libconnectivity-qt1 (0.8.0+16.10.20160817.2-0ubuntu1) to 0.8.0+16.10.20160817.2-0ubuntu2
libdecoration0 (1:0.9.13.0+16.10.20160818.2-0ubuntu1) to 1:0.9.13.0+16.10.20160818.2-0ubuntu2
libfdisk1 (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1
libgirepository-1.0-1 (1.48.0-3ubuntu1) to 1.49.1-2ubuntu1
libgrilo-0.3-0 (0.3.1-1) to 0.3.2-1
libgssapi3-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libhcrypto4-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libheimbase1-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libheimntlm0-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libhx509-5-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libicu57 (57.1-3) to 57.1-4
libkrb5-26-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libmirclient9 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
libmircommon6 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
libmircookie2 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
libmirplatform13 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
libmirprotobuf3 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
libmirserver41 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
libmount1 (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1
libnss3 (2:3.25-1ubuntu1) to 2:3.26-1ubuntu1
libroken18-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
libsmartcols1 (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1
libthumbnailer-qt1.0 (2.4+16.10.20160719-0ubuntu1) to 2.4+16.10.20160719-0ubuntu2
libuuid1 (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1
libwind0-heimdal (1.7~git20150920+dfsg-4ubuntu1) to 1.7~git20160703+dfsg-1
mir-client-platform-mesa5 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
mir-graphics-drivers-desktop (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
mir-platform-graphics-mesa-kms10 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
mir-platform-graphics-mesa-x10 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
mir-platform-input-evdev5 (0.24.0+16.10.20160815.3-0ubuntu1) to 0.24.0+16.10.20160815.3-0ubuntu2
mount (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1
python3-apparmor-click (0.3.15) to 0.3.16
python3-pkg-resources (25.2.0-1ubuntu1) to 26.1.1-1
python3-setuptools (25.2.0-1ubuntu1) to 26.1.1-1
python3-software-properties (0.96.24.4) to 0.96.24.6
qml-module-ubuntu-connectivity (0.8.0+16.10.20160817.2-0ubuntu1) to 0.8.0+16.10.20160817.2-0ubuntu2
qml-module-ubuntu-thumbnailer0.1 (2.4+16.10.20160719-0ubuntu1) to 2.4+16.10.20160719-0ubuntu2
qtdeclarative5-ubuntu-thumbnailer0.1 (2.4+16.10.20160719-0ubuntu1) to 2.4+16.10.20160719-0ubuntu2
snapd (2.13+16.10) to 2.14.2+gitcc9d039-0ubuntu5
software-properties-common (0.96.24.4) to 0.96.24.6
software-properties-gtk (0.96.24.4) to 0.96.24.6
thumbnailer-service (2.4+16.10.20160719-0ubuntu1) to 2.4+16.10.20160719-0ubuntu2
thunderbird (1:38.6.0+build1-0ubuntu1) to 1:45.2.0+build1-0ubuntu1
thunderbird-gnome-support (1:38.6.0+build1-0ubuntu1) to 1:45.2.0+build1-0ubuntu1
thunderbird-locale-en (1:38.6.0+build1-0ubuntu1) to 1:45.2.0+build1-0ubuntu1
thunderbird-locale-en-us (1:38.6.0+build1-0ubuntu1) to 1:45.2.0+build1-0ubuntu1
util-linux (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1
uuid-runtime (2.28.1-1ubuntu1) to 2.28.2-1ubuntu1

Installed the following packages:
libprotobuf-lite10 (3.0.0-7ubuntu3)
libprotobuf10 (3.0.0-7ubuntu3)

```

These are what killed the scopes I assume. I tired previous kernel .. etc..

Regards..

---

### Post by ventrical on 2016-09-14
unity8 boots to blackspace bug

[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1623531](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1623531)

regards..

---

### Post by jbicha on 2016-09-14
> **ventrical said:**
> @mac4man

Here is the synaptic log I was talking about from a yakkety install that had held back broken packages non ppa (today)



Why do you use -proposed during the development cycle? It means you'll experience a lot more broken things.

---

### Post by ventrical on 2016-09-14
> **jbicha said:**
> Why do you use -proposed during the development cycle? It means you'll experience a lot more broken things.

It happened on proposed and non proposed installs. I thought that's one of the things we are suppossed to do. Try to break stuff and report bugs :).

Regards..

---

### Post by ventrical on 2016-09-14
> **jbicha said:**
> Why do you use -proposed during the development cycle? It means you'll experience a lot more broken things.

Yep .. that particular install has proposed off.  So that means we are getting broken stuff either way.

edit; I have 10 hard installs of yakkety/xenial with unity8 at various stages on 4 different form factors. Some are ppa and others non ppa. Some with proposed and others with non proposed.  So I am trying to cover all the bases with unity8.  I'm not complaining - just reporting and commenting .. but it would be nice if the yakkety sessions of unity8 had some workability instead of black-screening and black-scoping.

---

### Post by jbicha on 2016-09-14
I'm not disputing unity8 being broken (I haven't tried it). I just noticed that you also complained about protobuf 3.0.0-7ubuntu3 being uninstallable. protobuf 3 is in -proposed only *because* it's a library transition; once the transition is complete it will be promoted to the regular archives. Packages in proposed are automatically promoted to the regular archives once they pass a few automated checks. If a package fails those tests, developers know about it because they can see it on a page like [this]("https://people.canonical.com/~ubuntu-archive/proposed-migration/yakkety/update_excuses.html") so they don't really need bug reports for those kinds of issues.

I believe Ubuntu developers generally don't use -proposed during the development cycle and I'm trying to help testers and users follow their example.

---

### Post by mc4man on 2016-09-14
the crashes associated with this are these 3 reports, though they are still private
Bug #1620994
Bug #1622827
Bug #1620939

crashers seem to remain private longer than they did in past times..

---

### Post by ventrical on 2016-09-14
> **jbicha said:**
> I'm not disputing unity8 being broken (I haven't tried it). I just noticed that you also complained about protobuf 3.0.0-7ubuntu3 being uninstallable. protobuf 3 is in -proposed only *because* it's a library transition; once the transition is complete it will be promoted to the regular archives. Packages in proposed are automatically promoted to the regular archives once they pass a few automated checks. If a package fails those tests, developers know about it because they can see it on a page like [this]("https://people.canonical.com/~ubuntu-archive/proposed-migration/yakkety/update_excuses.html") so they don't really need bug reports for those kinds of issues.

I believe Ubuntu developers generally don't use -proposed during the development cycle and I'm trying to help testers and users follow their example.

Thank you for your reply.

First .. allow me to clarify.. I am not complaining about protobuf*. I just reported that there were held and broken packages on an install that was working very reliably and so I installed synaptic as I was getting scopes blackspace with yakkety to begin with and I was not filing a bug on that install in particular. The bug I filed had proposed off (as I already stated and documented with a screenshot). Secondly, I am aware of having proposed repositories enabled on *some* of my installs and for the most part i rarely have breakage this late into the cycle with proposed on but I certainly understand the pitfalls. Thirdly, you mention automated checks on proposed packages before they are released but in development version there are some who would rather do edge testing in the wild, otherwise the controlled quality assurance will miss several scenarios that is impossible for it to emulate.

I feel that the issue is not whether proposed is enabled or disabled because earlier testing by other members has proven that 'quiet' installs will just not work, especially on form factors with nVidia based graphics.  So I am trying to shake the bushes so to speak.  It at least is more considerate then that persons who do not want to be involved in edge testing can move on and test others flavors of ubuntu as it would save a lot of downtime.

Regards..

---

### Post by ventrical on 2016-09-14
> **mc4man said:**
> the crashes associated with this are these 3 reports, though they are still private
Bug #1620994
Bug #1622827
Bug #1620939

crashers seem to remain private longer than they did in past times..

I have had a bug (online-accounts-ui crashed) that I reported and unmarked it from private. I was notified that it was a dupe and  for some reasons it was toggled back to private.

---

### Post by ventrical on 2016-09-14
#1620939

had this crash several times but would not let me report.

[URL="https://bugs.launchpad.net/ubuntu/+source/unity-scope-click/+bug/1620939"]https://bugs.launchpad.net/ubuntu/+source/unity-scope-click/+bug/1620939


[/URL]

---

### Post by ventrical on 2016-09-14
> **mc4man said:**
> the crashes associated with this are these 3 reports, though they are still private
Bug #1620994
Bug #1622827
Bug #1620939

crashers seem to remain private longer than they did in past times..

ahh I think jbicha unflagged them. :)

---

### Post by mc4man on 2016-09-14
I would say that during the bulk of dev -proposed is just a holding 'pen', not really of value for testing & use of is possiblibly  counter productive. It's likely that during the last several weeks -proposed starts getting proposed bug fixes & whatnot that could benefit from testing.

---

### Post by ventrical on 2016-09-14
> **mc4man said:**
> I would say that during the bulk of dev -proposed is just a holding 'pen', not really of value for testing & use of is possiblibly  counter productive. It's likely that during the last several weeks -proposed starts getting proposed bug fixes & whatnot that could benefit from testing.

I appreciate your reply.  During the early part of the new dev cycle I usually open proposed with deliberation in an attempt to see what kind of breakage may be in the pipe. I do it more just out of enthusiasm, not trying to be a smart ass.  I also have installs that have proposed off. And these are the ones that are breaking! Just look at the bug reports. Need I say more.

Regards..

---

### Post by jbicha on 2016-09-14
> **ventrical said:**
> ahh I think jbicha unflagged them. :)

Yes, crash reports can be made public by the bug reporter or you can ask in #ubuntu-bugs or #ubuntu-devel for someone to look at making specific reports public. Crash reports are not automatically made public.

---

### Post by ventrical on 2016-09-15
> **jbicha said:**
> Yes, crash reports can be made public by the bug reporter or you can ask in #ubuntu-bugs or #ubuntu-devel for someone to look at making specific reports public. Crash reports are not automatically made public.

Thanks ...

btw .. as for protobuf3 in proposed ...  I had no idea how this happened as I had proposed off but the bug tracker tells me I had proposed on - so my bad .. and my apologies... I allowed this to slip through the net and my original assumptions are wrong. I think perhaps I may have filed a bug out of frustration because unity8 is intermittently breaking on multiple installs across several different form factors so to avoid causing further confusion I'll double check my bug reports in the furture.

Regards..

---

### Post by ventrical on 2016-09-16
Unity8 is back , screen up .. but now the scopes window just races with animated icon.

Regards..

---

### Post by enricobe on 2016-09-17
This is the bug (or one of them) that made Unity8 crash

[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1620994](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1620994)

It has been fixed in the last mesa update

---

### Post by ventrical on 2016-09-18
Thanks enricobe. Updating now.

---

### Post by ventrical on 2016-09-18
Bravo unity8 ! There is wind in the sails once again :)

Regards..

---

### Post by ventrical on 2016-09-18
@graham

it's working good on nVida graphcis set box now ... if you want to give it a spin and let us know ?

 Regards..

---

### Post by PaulW2U on 2016-09-18
It is indeed working again but the first time I've actually seen a working Unity 8 for myself. I managed to watch a music video and looked through the settings panels. Obviously there's not a lot else there yet. :)

On returning to Unity 7 I was met with multiple prompts to report crashes - bug [#1618590]("https://bugs.launchpad.net/ubuntu/+source/qtbase-opensource-src/+bug/1618590") was the only one I could see that had already been reported.

---

### Post by ventrical on 2016-09-21
Can copy and paste from gedit in containers

> 
the quick brown fox


---

### Post by ventrical on 2016-09-26
Unity8 desktop /no apps store ,/no apps scopes in Apps/ freezes up on nVidia box. It has deprecated.

At least Firefox works from Libertine container.

Regards..

---

### Post by mc4man on 2016-09-26
[Maybe]("http://duke.a-13.net/") next year..

---

### Post by ventrical on 2016-09-26
> **mc4man said:**
> [Maybe]("http://duke.a-13.net/") next year..

Ouch !   :)

---

### Post by ventrical on 2016-09-26
About 350mb thismorning... and now another batch. Looks like the joints a jumping ..

```

The following NEW packages will be installed:
  libboost-serialization1.61.0 libzmqpp4 linux-headers-4.8.0-17
  linux-headers-4.8.0-17-generic linux-image-4.8.0-17-generic
  linux-image-extra-4.8.0-17-generic
The following packages will be upgraded:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-tools console-setup console-setup-linux ghostscript
  ghostscript-x gir1.2-libertine gsfonts keyboard-configuration
  libaccount-plugin-facebook libaccount-plugin-flickr
  libaccount-plugin-generic-oauth libaccount-plugin-google libertine
  libertine-tools libgs9 libgs9-common liblibertine1
  libonline-accounts-client1 libunity-scopes1.0 libzmq5 linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev python3-libertine
  python3-libertine-lxc python3-software-properties qml-module-qtquick-layouts
  qml-module-ubuntu-onlineaccounts-client
  qtdeclarative5-online-accounts-client0.1 signon-plugin-oauth2
  software-properties-common software-properties-gtk thermald
  ubuntu-keyboard-data ubuntu-system-settings-online-accounts
  unity-plugin-scopes
40 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 84.2 MB of archives.
After this operation, 313 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Interesting to see if the singon-plugin and online-accounts-client will let me install apps.

regards..

---

### Post by ventrical on 2016-09-27
No.  Nothing yet.

---

