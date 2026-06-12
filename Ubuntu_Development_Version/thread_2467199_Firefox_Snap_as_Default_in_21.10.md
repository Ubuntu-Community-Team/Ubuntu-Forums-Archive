---
title: "Firefox Snap as Default in 21.10"
date: 2021-09-18
forum: Ubuntu Development Version
---

### Post by tea for one on 2021-09-18
This looks like an interesting development.

[https://www.omgubuntu.co.uk/2021/09/ubuntu-makes-firefox-snap-default](https://www.omgubuntu.co.uk/2021/09/ubuntu-makes-firefox-snap-default)

---

### Post by Frogs Hair on 2021-09-18
There are some Ubuntu users who purge snap from there systems which would cause them to find another default browser. I have been using the Firefox ESR PPA for other reasons and I hope that remains available but I won't count on it.

---

### Post by guiverc on 2021-09-18
@tea for one

If you haven't seen it, I'd recommend reading the official notice for it all - [https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210](https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210)

(*it's a somewhat busy thread, same as the `chromium` one was many cycles ago*)

---

### Post by The Cog on 2021-09-19
Hmm. I'm going to have to find an alternative browser. That's a shame - I have used firefox since it first launched.

---

### Post by tea for one on 2021-09-19
> **guiverc said:**
> @tea for one

If you haven't seen it, I'd recommend reading the official notice for it all - [https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210](https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210)

(*it's a somewhat busy thread, same as the `chromium` one was many cycles ago*)

Yes, I had a look at the thread and some info is difficult to find.

For example:-

I was trying to find out if there was going to be a deb packaged version of Firefox in the 21.10 repository?
It was clear that Mozilla would offer a deb but it looked like you would have to go to their website.

I was also interested to read any comments about the Firefox version supplied with Xubuntu 21.10 or Lubuntu 21.10?

---

### Post by ajgreeny on 2021-09-19
An alternative way to continue with Firefox could be to use the .tar.gz direct from Mozilla, unpack it into a folder in /opt and use the executable file in that as I currently do in debian; it works well and automatically updates if you set it to do so.

---

### Post by zika on 2021-09-19
I do use FStable, FDeveloper and FNightly from DL places like this; [https://www.mozilla.org/en-US/firefox/94.0a1/releasenotes/](https://www.mozilla.org/en-US/firefox/94.0a1/releasenotes/) ... From long ago and in 21.10 ...
```
:~$ ll fire*
firefox-nightly:
&#1091;&#1082;&#1091;&#1087;&#1085;&#1086; 12
drwxrwxr-x  3 zika zika 4096 &#1089;&#1077;&#1087; 19 11:57 .
drwxr-xr-x  8 zika zika 4096 &#1089;&#1077;&#1087; 19 11:57 firefox
drwxr-xr-x 28 zika zika 4096 &#1089;&#1077;&#1087; 19 11:51 ..

firefox-developer:
&#1091;&#1082;&#1091;&#1087;&#1085;&#1086; 12
drwxr-xr-x 28 zika zika 4096 &#1089;&#1077;&#1087; 19 11:51 ..
drwxrwxr-x  3 zika zika 4096 &#1089;&#1077;&#1087; 19 08:19 .
drwxr-xr-x  8 zika zika 4096 &#1089;&#1077;&#1087; 19 08:19 firefox

firefox-stable:
&#1091;&#1082;&#1091;&#1087;&#1085;&#1086; 12
drwxr-xr-x 28 zika zika 4096 &#1089;&#1077;&#1087; 19 11:51 ..
drwxrwxr-x  3 zika zika 4096 &#1089;&#1077;&#1087; 19 08:18 .
drwxr-xr-x  8 zika zika 4096 &#1089;&#1077;&#1087; 19 08:18 firefox

```
```
:~$ cat f?.sh
...firefox-developer/firefox/firefox --private --start-maximized & exit
...firefox-nightly/firefox/firefox --private --start-maximized & exit
...firefox-stable/firefox/firefox --private --start-maximized & exit
```

---

### Post by guiverc on 2021-09-19
> **tea for one said:**
> 
I was also interested to read any comments about the Firefox version supplied with Xubuntu 21.10 or Lubuntu 21.10?

I can only provide my understanding, which is *flavors* will not be impacted for *impish* or 21.10.

*Note: from here on I've got my Lubuntu hat on, ie. I'm speaking from my understanding as a member of the Lubuntu team*

Our seed can be found [here]("https://people.canonical.com/~ubuntu-archive/seeds/lubuntu.impish/desktop") where you'll note we use `firefox` from main Ubuntu.

We have received no notification of change for 21.10/*impish*, only for the next *jj* release. It is my belief that detail applies to all *flavors. *However this is my understanding only.

(*I was QA-testing Ubuntu impish yesterday; yet it didn't even occur to me to look at how firefox was delivered...   the [manifest]("https://cdimage.ubuntu.com/daily-live/current/impish-desktop-amd64.manifest") appears to match my own impish system though* *which uses deb*)

-- [I]additional thoughts (Lubuntu hat off) --

my primary box is development thus is currently impish; but has multiple DEs installed including Ubuntu (ie. GNOME), so I'm expecting to see changes occur on this box first. I personally am expecting firefox as a snap (ubuntu-desktop) and the deb to remain (lubuntu-desktop & xubuntu-desktop i have installed) whilst still on 'impish'. 

I expect to see firefox as a snap appear on pure Lubuntu jj systems in mid-November to early- Dec, but when it hits will be a decision of the Ubuntu desktop team plan of action.  this is my estimate only though.

if I'm QA-testing or looking at pure Lubuntu systems, I use other boxes; & not my main 'bloated' primary system (I may use Lubuntu/LXQt most days; but I'm not exclusive to it; besides this system is somewhat heavily modified). On the other boxes I don't update, just re-install so it's always a fresh image of our latest (which helps to identify issues early I feel).
[/I]

---

### Post by tea for one on 2021-09-19
@guiverc

Thank you for the info - very informative.

---

### Post by Dennis N on 2021-09-19
> **ajgreeny said:**
> An alternative way to continue with Firefox could be to use the .tar.gz direct from Mozilla, unpack it into a folder in /opt and use the executable file in that as I currently do in debian; it works well and automatically updates if you set it to do so.

I agree with this remark by ajgreeny. Also, no one has yet mentioned that Firefox comes as a Flatpak as well. I have been using that version in a number of installations for quite a while.

Other distros, like Fedora, Arch and Manjaro, are unlikely to go with a snap version of Firefox as default. Fedora is pro Flatpak - they even have their own Flatpak repository.

---

### Post by VMC on 2021-09-19
As a test I downloaded "firefox-92.0.tar.bz2", purged installed FF. Then expanded the bz2 file into a folder, and ran it. Don't need a deb file. Don't need no **Stinking Snap!**

---

### Post by monkeybrain20122 on 2021-09-20
> **tea for one said:**
> 

I was trying to find out if there was going to be a deb packaged version of Firefox in the 21.10 repository?
It was clear that Mozilla would offer a deb but it looked like you would have to go to their website.



Yes, right at the top and under "[What does this mean and who does it affect?]("https://discourse.ubuntu.com/t/feature-freeze-exception-seeding-the-official-firefox-snap-in-ubuntu-desktop/24210")" 

> This will only impact users of Ubuntu Desktop installing 21.10 or  upgrading to 21.10. If you run one of the flavours, you won’t be  affected - yet. The deb will continue to be supported through the life  cycle of 21.10, and the deb to snap transition is scheduled to be  completed in 22.04. 

There will probably be a ppa when 22.04 lands.

---

### Post by monkeybrain20122 on 2021-09-20
> **Dennis N said:**
> I agree with this remark by ajgreeny. Also, no one has yet mentioned that Firefox comes as a Flatpak as well. I have been using that version in a number of installations for quite a while.

Other distros, like Fedora, Arch and Manjaro, are unlikely to go with a snap version of Firefox as default. Fedora is pro Flatpak - they even have their own Flatpak repository.

does hardware acceleration (vaapi) work with the flatpak? With the .deb it works beautifully on my old intel netbook here. How about installing extensions? Does it work?

---

### Post by Dennis N on 2021-09-20
> **monkeybrain20122 said:**
> does hardware acceleration (vaapi) work with the flatpak? With the .deb it works beautifully on my old intel netbook here. How about installing extensions? Does it work?
Yes, you can install Firefox extensions, like ublock origin for example.
But, like Firefox Snap, Firefox Flatpak cannot use the gnome-shell integration provided by chrome-gnome-shell package to manage gnome-shell extensions. So you either use the Ubuntu repository to install shell extensions, or else download them and install manually which is pretty easy. But this would not be an issue with Ubuntu flavors like Xubuntu which don't use gnome-shell.
Sorry, I don't know about the hardware acceleration. Where is that set?

---

### Post by VMC on 2021-09-20
Hardware acceleration is still there under Performance , and you can still change "Content process limit". Also vaapi is still an option at about:config.

---

### Post by TheFu on 2021-09-20
Snaps AREN'T a terrible idea, but the implementation has no method of local control over the constraints WHICH IS A TERRIBLE problem.
Flatpaks allow local overrides.

Two different philosophies at work. Power to the users, which is the typical Unix philosophy, or power to the packager.  Those are the choices here.
I love the idea of being able to constrain applications and sets of applications - _**provided the constraints are under my control.**_

Snaps need more years of maturing based on the failures I've seen.  On 5 systems, all ubuntu-based, only 1 has consistently had snaps that work ... most of the time.  The other 4 refuse to even start a snap - any snap - program.  Both desktop apps and server tools fail and refuse to work.  That's far from the behavior of a "production" tool.

```
$ /snap/bin/wormhole
Sorry, home directories outside of /home are not currently supported. 
See [https://forum.snapcraft.io/t/11209](https://forum.snapcraft.io/t/11209) for details.

$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See [https://forum.snapcraft.io/t/11209](https://forum.snapcraft.io/t/11209) for details.
```

not currently supported?  When will they be supported?  The location is specified in the damn passwd DB!!!  It isn't like a **getent passwd {userid}** command can't validate that - or the C call getpwent().

NFS support anytime - ever?  If Canonical wants desktops in a corporation, they need to support both NFS and HOME directories outside /home/. They also need to let local admins set additional network storage locations via NFS for every snap to have data read AND written.  In every corporate environment I've worked that wasn't 100% Windows on the desktop, NFS was used for all data storage. Our HOME directories were sized small (quota limits) and we were require to store all project data on the NFS mounts.  Easier for the professional IT people to backup server storage than 50K desktops.

---

### Post by monkeybrain20122 on 2021-09-20
> **Dennis N]Sorry, I don't know about the hardware acceleration. Where is that set?         
[/QUOTE]

[QUOTE=VMC said:**
> Hardware acceleration is still there under Performance , and you can still change "Content process limit". Also vaapi is still an option at about:config.

I don't know if you can just enable vaapi on about:config, maybe someone with a flatpak can check this

I do it by changing layers.acceleration.force-enabled to be true in about:config and start FF with (I made a wrapper script so can start FF with .desktop file)
```
LIBVA_DRIVER_NAME=i965 MOZ_X11_EGL=1 /usr/bin/firefox
```

You can check that it is using vaapi by monitoring cpu usage with the top command and if using intel gpu
```
sudo intel_gpu_top
``` and see that the "video/0" row is not 0.00%

To get intel_gpu_top
```

sudo apt install intel-gpu-tools
```

---

### Post by kurt18947 on 2021-09-20
> **Dennis N said:**
> Yes, you can install Firefox extensions, like ublock origin for example.
But, like Firefox Snap, Firefox Flatpak cannot use the gnome-shell integration provided by chrome-gnome-shell package to manage gnome-shell extensions. So you either use the Ubuntu repository to install shell extensions, or else download them and install manually which is pretty easy. But this would not be an issue with Ubuntu flavors like Xubuntu which don't use gnome-shell.
Sorry, I don't know about the hardware acceleration. Where is that set?

It would suck hugely for me if I couldn't install shell extensions. I just checked Vivaldi on 20.04 and it looks like I can install, delete and modify extensions there if Firefox chooses to be difficult. I presume that will continue to be the case. I keep a chromium based browser installed as secondary for the few sites that don't seem to play well with Firefox.

---

### Post by TheFu on 2021-09-20
I'm curious.

Has ***anyone*** had trouble free use of snaps?

---

### Post by corradoventu on 2021-09-21
Does not seems worse on my Impish...
```
corrado@corrado-n3-ii-0919:~$ time snap run firefox

real	0m8,013s
user	0m6,477s
sys	0m1,932s
corrado@corrado-n3-ii-0919:~$ time firefox

real	0m5,132s
user	0m6,504s
sys	0m1,263s
corrado@corrado-n3-ii-0919:~$
```

---

### Post by ajgreeny on 2021-09-22
> **TheFu said:**
> I'm curious.

Has ***anyone*** had trouble free use of snaps?
And I'm curious as well.
If I want to view libreoffice help which now always shows as read from a local version on /usr/share will that be viewable in a snap version of firefox?  It it's not possible it will be a huge problem for many LO users.

Lack of personal choice is snap's biggest problem for me!

---

### Post by corradoventu on 2021-09-22
On my Ubuntu 21.10 I have the .deb version of Firefox preinstalled and the snap version installed from Ubuntu software. The snap version takes about 15 seconds to start despite having an nvme disk but once started seems ok.
The only problem i found is with Google Earth where i have a message 
> Unfortunately your computer does not support WebGL graphics acceleration; Google Earth cannot be loaded
Hmm. While your browser seems to support WebGL, it is disabled or unavailable. If possible, please ensure that you are running the latest drivers for your video card.
On the same installation with Firefox .deb google earth works fine.

---

### Post by Frogs Hair on 2021-09-22
> **TheFu said:**
> I'm curious.

Has ***anyone*** had trouble free use of snaps?

I don't think so .I've had a few that work very well, but the Chromium snap has had issues on three different operating systems. If they are to be "universal" it would follow that testing on many different snap capable operating systems would be required. I would hope individual  packagers are doing more then then testing on their own system and uploading.  I suspect some packages will be abandoned as maintainers no longer have time or move on to other operating systems just like the PPA system.

---

### Post by monkeybrain20122 on 2021-09-22
It is well known that the chromium snap cannot use hardware  acceleration (but it works for chromium from the ppa). I guess when people say they have no problem with snap  that means their use cases are accommodated. 

The right question should not be "does  it works for you?" ("you" might have different needs than I) but whether the snap has the same functionalities as the .deb version.

I think the argument for Firefox snap makes no sense. This is something that gets regular updated anyway.  Maybe it is just me, but I would rather wait a day or two for the update to get a fully functional version than to grab an update as soon as possible but it might be crippled in some ways.

---

### Post by ajgreeny on 2021-09-22
I do not use snaps at all in my system (Xubuntu 20.04) and have even removed snapd as well as all the infrastructure required to install and use them.

This has caused absolutely no difficulties or problems at all for me, and should firefox become a snap by default I shall still remove all the snap infrastructure and install firefox using one of the alternative methods, probably simply with the .tar.gz archive available direct from Mozilla, assuming, of course, that it is still available.

---

### Post by VMC on 2021-09-22
Its hard to find the latest, but "ungoogled-chromium_93.0.4577.82_1.vaapi_linux.tar.xz" works like firefox, in that you install into a folder
"/opt" , then copy the .desktop to autostart.

The more popular one is version 91, but I keep getting "Aw, Snap!" something went wrong. Not so using version 93. I like the Appimage, but can't find 93, only 91.
Anyway, here is [ungoogled-chromium_93.0.4577.82_1.vaapi_linux.tar.xz]("https://github.com/macchrome/linchrome/releases/download/v93.0.4577.82-r902210-portable-ungoogled-Lin64/ungoogled-chromium_93.0.4577.82_1.vaapi_linux.tar.xz")

---

