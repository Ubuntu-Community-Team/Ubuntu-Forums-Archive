---
title: "looking for a lightweight browser (for 32-bit)"
date: 2017-09-03
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-09-03
I'm playing OpenMW and I tend to surf the web as I play the game, however, using Firefox along with OpenMW really zaps the RAM, so, I'm looking into a lightweight browser.  OpenMW ([https://openmw.org/en/](https://openmw.org/en/)) is a video game.

I've looked into:
Dillo, but it doesn't load the sites I want to go to, like deviantart.
Midori, but I was told that Midori isn't being maintained anymore.
QupZilla, the latest AppImage version isn't available for 32-bit though.

---

### Post by TheFu on 2017-09-03
lynx?

---

### Post by vasa1 on 2017-09-03
OP wants to visit DeviantArt which is quite a demanding site!

---

### Post by him610 on 2017-09-03
My knowledge is minimal on this, but a light weight browser exists in the repository:

Ubuntu web browser, listed in Synaptic as  [I]webbrowser-app
[/I]
Description: 
A lightweight web browser tailored for Ubuntu, based on the Oxide browser
engine and using the Ubuntu UI components.

---

### Post by vasa1 on 2017-09-03
@him610, I suspect OP is running either Xubuntu or Lubuntu and not Ubuntu.

---

### Post by TheFu on 2017-09-03
The dependency list for  webbrowser-app freaked me out.

```
The following NEW packages will be installed:
  hud libandroid-properties1 libcolumbus1-common libcolumbus1v5 libdbusmenu-qt5 libgsettings-qt1 libhardware2
  libhud2 libhybris libhybris-common1 libmedia1 liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0
  libqt5feedback5 libqt5organizer5 libqt5positioning5 libqt5quicktest5 libubuntugestures5 libubuntutoolkit5
  libunity-action-qt1 qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings qml-module-qtfeedback
  qml-module-qtgraphicaleffects qml-module-qtquick-layouts qml-module-qtquick-window2 qml-module-qtquick2
  qml-module-qttest qml-module-ubuntu-components qml-module-ubuntu-layouts qml-module-ubuntu-performancemetrics
  qml-module-ubuntu-test qml-module-ubuntu-web qtdeclarative5-ubuntu-ui-toolkit-plugin
  qtdeclarative5-unity-action-plugin suru-icon-theme ubuntu-mobile-icons ubuntu-ui-toolkit-theme webbrowser-app
```

So much for light weight.  Most definitely NOT unless you run Qt/KDE already.

If there was any question, I canceled the install.  I use dillo and lynx, but I'm happy to have zero javascript.  dillo isn't sufficient for heavy JS sites and the HTTPS implementation has SERIOUS, SERIOUS, flaws.  Never use dillo if you want a good SSL connection.

---

### Post by ardouronerous on 2017-09-04
Since Midori has been installed already, looks like I'm stuck with Midori.

Is there any danger in using Midori really?

---

### Post by TheFu on 2017-09-04
Running unmaintained software, especially an unmaintained browser, is one of the highest risk activities that can be done on Linux.

---

### Post by ardouronerous on 2017-09-04
There seems to be no other browser available in the repos.
I've looked into other browsers available in the repos;

xombrero - discontinued
Arora - discontinued

The only other choice I have is Pale Moon, but I'm uncertain about it due to Pale Moon not being in Ubuntu's repos.

How is Pale Moon?

---

### Post by dragonfly41 on 2017-09-04
If OP is on Ubuntu 14.04 / 32 bits then one possibility is Amaya (although rather dated - 2012).

[https://www.w3.org/Amaya/User/BinDist.html](https://www.w3.org/Amaya/User/BinDist.html)

One dependency is libssl0.9.8 and on Ubuntu 16.04 this is libssl1.0.0 so Amaya cannot be easily installed.

I had Pale Moon running on Ubuntu 14.04 32 bits before moving up to Ubuntu 16.04 64bits.

---

### Post by ardouronerous on 2017-09-04
I'm running Xubuntu 16.04.

Will Pale Moon run on 16.04 though?

---

### Post by dragonfly41 on 2017-09-04
I have not yet tried it on my latest setup.

Here is a review of browsers.

[https://en.wikipedia.org/wiki/List_of_web_browsers](https://en.wikipedia.org/wiki/List_of_web_browsers)

---

### Post by sudodus on 2017-09-04
> **ardouronerous said:**
> Since Midori has been installed already, looks like I'm stuck with Midori.

Is there any danger in using Midori really?

I found the following information via

[http://midori-browser.org/download/ubuntu/](http://midori-browser.org/download/ubuntu/) and [https://launchpad.net/~midori/+archive/ubuntu/ppa](https://launchpad.net/~midori/+archive/ubuntu/ppa):

**midori 	0.5.11-0ubuntu1 	frenchy82 (2015-08-30)**

and it makes me think, that with no update since August 2015 (2 years ago), Midori might ***not*** be a safe browser.

---

### Post by ardouronerous on 2017-09-04
> **dragonfly41 said:**
> If OP is on Ubuntu 14.04 / 32 bits then one possibility is Amaya (although rather dated - 2012).

[https://www.w3.org/Amaya/User/BinDist.html](https://www.w3.org/Amaya/User/BinDist.html)

One dependency is libssl0.9.8 and on Ubuntu 16.04 this is libssl1.0.0 so Amaya cannot be easily installed.

I had Pale Moon running on Ubuntu 14.04 32 bits before moving up to Ubuntu 16.04 64bits.

I looked into Amaya, it also a discontinued browser.

> **sudodus said:**
> I found the following information via

[http://midori-browser.org/download/ubuntu/](http://midori-browser.org/download/ubuntu/) and [https://launchpad.net/~midori/+archive/ubuntu/ppa](https://launchpad.net/~midori/+archive/ubuntu/ppa):

**midori     0.5.11-0ubuntu1     frenchy82 (2015-08-30)**

and it makes me think, that with no update since August 2015 (2 years ago), Midori might ***not*** be a safe browser.

My other choice is Pale Moon, but as I said, since Pale Moon isn't part of Ubuntu's repos, I'm uncertain about it, have you tried it?

---

### Post by sudodus on 2017-09-04
I tried Midori some years ago. but I have never tried Pale Moon.

I'm usually browsing with Firefox, but it is starting very slowly for me during this summer. I'm still using Firefox because it is updated regularly, and I rely on it.

(Once in a while I'm browsing with Chromium-Browser, when things don't work properly with Firefox.)

---

### Post by vasa1 on 2017-09-04
> **ardouronerous said:**
> I'm playing OpenMW and I tend to surf the web as I play the game, however, using Firefox along with OpenMW really zaps the RAM, ...
Can you add RAM to your system?

---

### Post by ardouronerous on 2017-09-04
RAM already at maximum, 4GB.

---

### Post by dragonfly41 on 2017-09-04
I only have 4GB RAM on my old laptop.   The key is to use a good tab manager to cut down tabs.
I use Chromium Web Browser and have installed OneTab extension.
When I last used Firefox I was using TGH extension (tab groups handler) which allows unused tabs to be put to sleep.

---

### Post by ardouronerous on 2017-09-05
What TGH extension do you recommend? Because there's many available in Firefox's addon page: [https://addons.mozilla.org/en-US/firefox/search/?q=tab+groups+handler&appver=&platform=](https://addons.mozilla.org/en-US/firefox/search/?q=tab+groups+handler&appver=&platform=)

---

### Post by vasa1 on 2017-09-05
When you're low on RAM why do you have several tabs open?

---

### Post by ardouronerous on 2017-09-05
When I play OpenMW, I usually have 2 tabs open, one for Deviantart and one for Morrowind walkthough.

When Firefox is open with one tab, the memory usage is about 1,500MB and can go up to 1,900+MB when on two tabs.

---

### Post by dragonfly41 on 2017-09-05
> **ardouronerous said:**
> What TGH extension do you recommend? Because there's many available in Firefox's addon page: [https://addons.mozilla.org/en-US/firefox/search/?q=tab+groups+handler&appver=&platform=](https://addons.mozilla.org/en-US/firefox/search/?q=tab+groups+handler&appver=&platform=)

The TGH extension I followed some two years ago was developed by Allasso Travesser (which might be a pseudonym for the developer).

[https://addons.mozilla.org/en-US/firefox/addon/tab-groups-helper/reviews/?page=2](https://addons.mozilla.org/en-US/firefox/addon/tab-groups-helper/reviews/?page=2)

But if you only have two tabs to manage it hardly seems worthwhile installing an extension for tabs management.

Perhaps instead you could write a simple python popup browser script as a wrapper for one of your two URL's?

---

### Post by BenginM on 2017-09-05
Try min, and brave.
[URL="https://minbrowser.github.io/min/"]https://minbrowser.github.io/min/
[https://brave.com/](https://brave.com/)
[/URL]

---

### Post by vasa1 on 2017-09-05
The other point is that maybe you've a bunch of extensions doing bad things to your browser.

1.5 GB for one tab seems excessive :(

---

### Post by vasa1 on 2017-09-05
I have the following tabs open in Firefox 57:
[https://www.youtube.com/](https://www.youtube.com/)
[https://chromereleases.googleblog.com/](https://chromereleases.googleblog.com/)
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)
[http://www.webupd8.org/](http://www.webupd8.org/)
[https://news.google.com/news/?ned=us&hl=en](https://news.google.com/news/?ned=us&hl=en)
[https://askubuntu.com/questions?pagesize=50&sort=newest](https://askubuntu.com/questions?pagesize=50&sort=newest)

And the relevant lines from *top -bn 1* are below:```
top - 14:59:35 up 43 min,  2 users,  load average: 0.50, 0.74, 0.68
Tasks: 194 total,   1 running, 193 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.0 us,  3.0 sy,  0.3 ni, 82.3 id,  4.1 wa,  0.0 hi,  0.4 si,  0.0 st
KiB Mem :  8039620 total,  4894040 free,  1687824 used,  1457756 buff/cache
KiB Swap:  8117244 total,  8117244 free,        0 used.  5943908 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1927 vasa1     20   0 2734692 353112 123944 S   0.0  4.4   3:56.15 firefox
 2086 vasa1     20   0 1933928 180876  80256 S   0.0  2.2   0:54.00 Web Content
 3836 vasa1     20   0 1808220 131184  77220 S   0.0  1.6   0:02.49 Web Content
 3875 vasa1     20   0 1994704 237976  80312 S   0.0  3.0   0:09.44 Web Content
 3907 vasa1     20   0 1849668 178516  73656 S   0.0  2.2   0:06.52 file:// Content
 3938 vasa1     20   0 1844548 170376  92640 S   0.0  2.1   0:01.93 Web Content
```
I have two extensions active: Stylus and uBlock origin.

---

### Post by ardouronerous on 2017-09-05
I have these extensions installed:

```
Decentraleyes
Disconnect
DownThemAll!
FoxClocks
Ghostery
Hide Caption Titlebar Plus
HTTPS Everywhere
NoScript
Open Bookmarks in New Tab
Open With
Privacy Badger
Sidebar Auto Show/Hide
Speed Tweaks (SpeedyFox)
Text Contrast for Dark Themes
uBlock Origin
VTzilla
Zoom Page WE
```

One tab loading Ubuntu Forums, and the memory usage is this: 1190+MB and can go up to 1400+MB

EDIT: BTW, I'm running Firefox 55.0.2, I haven't received an update for Firefox 57.

---

### Post by vasa1 on 2017-09-05
So why don't you try disabling most of them?

---

### Post by ardouronerous on 2017-09-05
The actives one on the list are:
```
Disconnect
Ghostery
HTTPS Everywhere
NoScript
Privacy Badger
uBlock Origin 
```

These addons are for security proposes, so I'm not sure if I want to disable them.

---

### Post by vasa1 on 2017-09-05
> **ardouronerous said:**
> The actives one on the list are:
```
Disconnect
Ghostery
HTTPS Everywhere
NoScript
Privacy Badger
uBlock Origin 
```

These addons are for security proposes, so I'm not sure if I want to disable them.
And when you find some other lightweight browser, will that have similar extensions? If not, and these are essential although there seems to be quite a bit of redundancy of function, you're stuck with Firefox :)

---

### Post by TheFu on 2017-09-05
You can run firefox in a firejail --private container. This way, you effectively get a fresh firefox config every startup.  Not much to loose.  Really, I think all browsers and email programs should be run in some sort of container for added security. You can choose if it is allowed to write to your HOME or not.
```

$ firejail --private firefox
```

I run chromium-browser with different settings in this way:
```
alias firechrome='firejail chromium-browser '
alias firepchrome='firejail --private chromium-browser '

```  The 1st lets it write to my real home.  The 2nd puts a virtual, temporary, file system for the browser to run inside. Every time, the environment is 100% fresh, like the first run.  No cookies, no locally stored flash, html5, or other things. When that instance is closed, the virtual file system is removed (poof) and nothing is saved.

Play around with a bash shell with the different firejail settings to see the slight differences.  Oh - firejail needs 16.04 or later to work (easily).

Anyway, just another option to try.

---

### Post by ardouronerous on 2017-09-05
Okay, I've installed and is now testing Chromium.
The extensions I have installed are:
```
Decentraleyes
Disconnect
FoxClocks
Ghostery
HTTPS Everywhere
Privacy Badger
uBlock Origin
```

I have 3 tabs loaded, 1st tab Deviantart, 2nd tab Morrowind walkthrough and 3rd tab Ubuntu Forums, and the memory usage is 1050+MB, certainly much lighter on the memory than Firefox.

Why is Firefox such a memory hog?

---

### Post by vasa1 on 2017-09-05
> **ardouronerous said:**
> ..., and the memory usage is 1050+MB, ...
How do you measure memory usage?

---

### Post by speartip on 2017-09-05
@ardouronerous..
You have 4 privacy extensions there that are more or less doing the same thing and will probably conflict.
IMO I would stick with uBlock Origin & HTTPs Everywhere, & ditch the rest. The less extensions, the lower the memory usage.

---

### Post by ardouronerous on 2017-09-05
> **vasa1 said:**
> How do you measure memory usage?

I'm running xfce4-systemload-plugin 1.1.2

---

### Post by TheFu on 2017-09-05
> **ardouronerous said:**
> Okay, I've installed and is now testing Chromium.
The extensions I have installed are:
```
Decentraleyes
Disconnect
FoxClocks
Ghostery
HTTPS Everywhere
Privacy Badger
uBlock Origin
```

I have 3 tabs loaded, 1st tab Deviantart, 2nd tab Morrowind walkthrough and 3rd tab Ubuntu Forums, and the memory usage is 1050+MB, certainly much lighter on the memory than Firefox.

Why is Firefox such a memory hog?

I had a problem where Firefox was eating 9+G of RAM a few months ago running my normal tabs and my system would lock up a few times a week. It has 4G of RAM and a 4G swap.  I think some addon changed and was updated a few months ago.  

I first also switched to zswap - it is the default for low memory systems now. It didn't directly help, but the system was slightly more responsive.

I removed h.264 and flash completely (cisco's and adobe's binaries) and removed a few old addons that I han't been using for a long time.  Memory use dropped to under 4G doing that alone.  

BTW, did Mozilla ever fix their terrible security flaw where any addon used on 1 tab/page could gain access to any other tab/page's data and transmit it back?  Even some of the "privacy" addons would be tempted to do that, to get some income from tracking us.  At least until they got caught and ruined their reputation. OTOH, what good is a rep if you can't buy food?

Just checked. FF is using about 4.1G now. It has been running since Sunday.

Some of the privacy addons might not really be helping to keep you and me private.  They help provide a fingerprint that can be individual even if we wipe cookies and other local storage every shutdown.  Test your browser's uniqueness. [https://panopticlick.eff.org/](https://panopticlick.eff.org/)   My browser chokes on that test, but I do network blocking against 130K ad and tracking domains.  It is the nuclear option.  But makes most of Google not work. ;)  Gotta choose which is more important, convenience or privacy?

---

### Post by vasa1 on 2017-09-05
> **ardouronerous said:**
> I'm running xfce4-systemload-plugin 1.1.2So the usage is total or for the browser?

---

### Post by ardouronerous on 2017-09-05
Total memory of the computer being used, which is useful whenever I play OpenMW with a browser, so i can know how much memory is being used and when to exit the game, or else my computer freezes.

---

### Post by vasa1 on 2017-09-05
> **ardouronerous said:**
> Total memory of the computer being used, which is useful whenever I play OpenMW with a browser, so i can know how much memory is being used and when to exit the game, or else my computer freezes.
You need to make these things clear :)

All along, I got the impression you were going on about the memory usage by Firefox.

Anyway, as you've seen, extensions can make a difference. By the way, Chromium should have its own task manager. Menu > More Tools > Task Manager.

---

### Post by ardouronerous on 2017-09-08
After looking around the Ubuntu repos, I found another browser that doesn't seem to be discontinued or unmaintained, the latest version was released 8 months ago.

Dooble Web Browser, I've tested the browser by loading two tabs, one tab is Ubuntu Forums and the other tab is Wikipedia, and according to Task Manager, Dooble's RSS is 113.9 MiB, seems very lightweight.

The latest version is 1.56c released on January 1, 2017, but the version available in the repos is version 0.07, so the version available to Ubuntu 16.04 repos is outdated, anyway to update this browser? A PPA perhaps? Thanks.

References:
[Dooble - Wikipedia]("https://en.wikipedia.org/wiki/Dooble")

---

### Post by hans12345 on 2018-01-25
I too was looking for a lightweight browser.

On holiday I take an old Atom based 2 GB RAM laptop with Xubuntu. Modern Firefox is too heavy.

Any advice?

---

### Post by kansasnoob on 2018-01-26
> **hans12345 said:**
> I too was looking for a lightweight browser.

On holiday I take an old Atom based 2 GB RAM laptop with Xubuntu. Modern Firefox is too heavy.

Any advice?

Chromium with uBlock Origin is close to the lightest I've found and it's easy to install. The downside is that uBlock Origin does interfere with some browsing, of course it can temporarily be disabled if need be. I recently brought several Dell Latitude 2110's back to life and for the most part some web content just requires more than a 1.83 GHz CPU w/2GB of RAM can handle - well it does handle it, just some web pages load very slowly.

Actually the lightest solution I found was Edge browser in Windows 10. I set those all up with dual-boots using recycled Windows licenses bought off of Ebay. But Windows always presents problems of its own. Getting everything working in Win 10 was time consuming.

---

