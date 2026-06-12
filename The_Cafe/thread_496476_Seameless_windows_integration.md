---
title: "Seameless windows integration?"
date: 2007-07-09
forum: The Cafe
---

### Post by ago on 2007-07-09
I was reading about wine-doors ([http://www.wine-doors.org/](http://www.wine-doors.org/)) I have not tried it yet but it looks like a great app. Essentially though, it is a package manager for windows applications, that takes care of all the boring (and sometimes difficult) set-up / prerequisites of wine so that applications can be installed/upgraded/uninstalled and run smoothly. At first sight it looks to me like there are a lot of apt-like features in there (and I am not referring to the GUI). So the first question that popped to my mind was: why not use apt for that directly?

I did not delve too deeply into it, but using apt should be possible and of course the windows packages would need to be hosted in a dedicated repository. The end user would be able to install windows applications from add-remove-programs (g-a-i), and once installed, the windows applications would be available via ordianary menus. Of course users should get the education window about binary blobs and non-foss products with a list of foss alternatives, but the idea is that such a tool will certainly lower entry barriers for many. 

[img]http://www.wine-doors.org/screens/ss-winedoors-1.png[/img]

How does it work? Essentially each deb package contains information on how to setup the windows application in Ubuntu/Wine and may or may not include the application installer itself (setup.exe). Some packages which are freely distributable will include the binary, the others will only include the metadata (preinst/postinst scripts, dependencies, wine specific settings and so on...) and then will require a separate wizard with filebrowser/downloader to fetch the non-distributable files from CD/local-file/web.

The same packages might be used with a different backend, e.g. using [Seamless Virtualization](https://help.ubuntu.com/community/SeamlessVirtualization) (in which case wine-specific settings/prerequisites will be ignored).

This does not imply that wine should be pre-installed by default, but that wine should be better integrated on Ubuntu so that once users activate the windows repository everything is one click away and users do not interact with wine directly. Not all Windows packages need to be included (it would be impossible), only those for which there is sufficient demand and/or lack of alternatives. 

Pros: 

* Takes away some of the main reservations many have against Linux
* Easier for people to switch completely, particularly all those that did not do so because of 1 or 2 applications they cannot live without
* People would enjoy all the benefits of apt for their windows programs (difficult to go back after that...)
* It would spur development of Wine
* Convenient route for commercial company to cover Linux customer base (=> better wine support, company themesleves would end up providing the packages)
* More games

Cons:

* Lesser incentive for people to try open source alternatives.
* Security/Privacy concerns (still much better than running the same programs on windows)
* Patent issues

My personal view is that in the long term it is far more important to have people to swap platform/OS rather than having them swap applications. So if that helps to bring people over to Ubuntu, even if it does not help to switch people from quicken to gnucash (or even making thing worse for gnucash), so be it. It is essential though to make sure that people make informed decisions and they are well informed of the implications of using binary blobs, but if they still want to use them, it should be technically possible and even easy for them to do so.

---

### Post by tgoose on 2007-07-09
Ideally, it wouldn't be necessary but since we don't live in an ideal world I think it's a very good idea!

---

### Post by forrestcupp on 2007-07-09
Looks pretty cool, but it looks like it's probably not quite ready yet.

Also, I'll bet that most of the stuff they have in the repos have good Linux alternatives.  I mainly use wine for commercial apps.

---

### Post by WinterWeaver on 2007-07-09
HMM... that looks interesting... Ima gonna give it a bash one day, cause I can never be bothered trying to do everything manually.

---

### Post by mr_byte on 2007-07-09
Looks nice, and lower overhead than the virtualization solution I'm using now. (VirtualBox).

---

