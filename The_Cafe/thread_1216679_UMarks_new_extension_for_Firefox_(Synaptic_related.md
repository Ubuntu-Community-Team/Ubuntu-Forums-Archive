---
title: "UMarks: new extension for Firefox (Synaptic related)"
date: 2009-07-18
forum: The Cafe
---

### Post by lovinglinux on 2009-07-18
The extension allows to generate lists of installed Ubuntu packages, that you can export to your desktop, then import into another Ubuntu system running Firefox and Umarks. It can also be used as a application restoration system, since you can store multiple backups in the same machine. The extension will also get deb packages from the backup cache, if available, or download the missing ones before installing. Packages that are already installed on the target system, but weren&#8217;t installed when/where the backup was created, are automatically removed, allowing you to replicate the same collection of applications on multiple systems or restoring your favorite applications after a clean install of Ubuntu. 

[Umarks Home Page](http://lovinglinux.megabyet.net/?page_id=534)

Please visit and subscribe to the new thread at [http://ubuntuforums.org/showthread.php?t=1464876](http://ubuntuforums.org/showthread.php?t=1464876)

[[IMG]http://img707.imageshack.us/img707/3584/screenshot004pf.png[/IMG]](http://img707.imageshack.us/i/screenshot004pf.png/)

---

### Post by VCoolio on 2009-07-18
Nice idea; will give it a shot. 
- For version 0.2 you could spell "openining a terminal" right (in the Preferences window). 
- Also a live searching bar like in synaptic, or at least a searching bar, would be nice (my list of apps is a bit long...). 
- a searching bar would also enable searching an app that is not yet installed (or am I missing a feature here?
- And ctrl+shift+u is the unicode shortkey, so that's not convenient as it won't bring up the side pane if you're in an entry field (which happens a lot in a browser).

Keep it up and thanks for this.

---

### Post by lovinglinux on 2009-07-18
> **VCoolio said:**
> Nice idea; will give it a shot. 
- For version 0.2 you could spell "openining a terminal" right (in the Preferences window)

Thanks. I guess I need more coffee :)

> **VCoolio said:**
> - Also a live searching bar like in synaptic, or at least a searching bar, would be nice (my list of apps is a bit long...). 

Do you mean a filter to search the list, not to search the sites? That will require some time, because I have no idea how to do it :)

> **VCoolio said:**
> - a searching bar would also enable searching an app that is not yet installed (or am I missing a feature here?

This feature is currently under development and should be available in the version.

> **VCoolio said:**
> - And ctrl+shift+u is the unicode shortkey, so that's not convenient as it won't bring up the side pane if you're in an entry field (which happens a lot in a browser).

Yep, I forgot to fix this before the release. Thanks for pointing that. I will change it for the next version too.

---

### Post by drawkcab on 2009-07-18
wow, great idea, keep working on this

:D

---

### Post by lovinglinux on 2009-07-18
> **drawkcab said:**
> wow, great idea, keep working on this

:D

Thank you. I will certainly keep working on it.

---

### Post by zekopeko on 2009-07-18
i don't think you need to install sqlite explicitly since firefox 3+ uses it for it's bookmark storage. so it's installed my default.
if you could remove the xclip dependency it would be a much nicer user experience.

---

### Post by lovinglinux on 2009-07-19
> **zekopeko said:**
> i don't think you need to install sqlite explicitly since firefox 3+ uses it for it's bookmark storage. so it's installed my default.

No, *sqlite3* is not installed by default. You are indeed correct about the the bookmark implementation in Firefox, but **SQLite 3** functionality is implemented by the package *libsqlite3-0*. The package *sqlite3*, in the other hand, is just a command-line interface for accessing **SQLite 3** databases, which I use in the scripts of the extension.

> **zekopeko said:**
> if you could remove the xclip dependency it would be a much nicer user experience.

I guess I could try distributing the extension as a deb file, so It would be possible to install the dependencies automatically. I will try to do that.

---

### Post by lovinglinux on 2009-07-19
A new version has been released. 

This version introduces an automatic search plug-in generator button in the preferences dialog, that adds 6 search engines (allmyapps.com, appnr.com, getdeb.net, ubuntuforums.org, launchpad.net and linuxappfinder.com) to your search plug-in list, based on your distro settings in the preferences.

---

### Post by thibs on 2009-08-07
@lovinglinux Hi! I just installed version 0.3 but I'm experiencing a little but annoying problem: Umarks is installed and I restarted Firefox but I don't see how to display the Umarks sidebar (?). It is weird as I had no pb with version 0.1... wait wait wait... I just found it on the very bottom right! You really should put an entry in the "display > sidebar" menu no? 

I also wanted to let you know that I just updated allmyapps today... you can now use http://allmyapps.com/package/<package_name> to go directly to the package page (example: [http://allmyapps.com/package/amarok](http://allmyapps.com/package/amarok)) or http://allmyapps.com/search/apps/<search_terms> to search for applications. Allmyapps automatically detects the Ubuntu version the user is using.

Now that I found where umarks is, I will continue testing :)

---

### Post by lovinglinux on 2009-08-07
> **thibs said:**
> @lovinglinux Hi! I just installed version 0.3 but I'm experiencing a little but annoying problem: Umarks is installed and I restarted Firefox but I don't see how to display the Umarks sidebar (?). It is weird as I had no pb with version 0.1... wait wait wait... I just found it on the very bottom right! You really should put an entry in the "display > sidebar" menu no? 

There is also an icon that you can drag to the toolbars. Right-click on the toolbar and select customize.Then drag the icon.

Yes, I should put an entry in the menu. The problem is that I need a keyboard shortcut for that, but finding one that does not conflict with other extensions is something is not easy. So I decided to stick with the buttons only.

> **thibs said:**
> I also wanted to let you know that I just updated allmyapps today... you can now use http://allmyapps.com/package/<package_name> to go directly to the package page (example: [http://allmyapps.com/package/amarok](http://allmyapps.com/package/amarok)) or http://allmyapps.com/search/apps/<search_terms> to search for applications. Allmyapps automatically detects the Ubuntu version the user is using.

Now that I found where umarks is, I will continue testing :)

Thanks for the heads up. I'm currently working on FoxMediaCenter extension, but as soon as I have some time I will work on Umarks updates.

---

### Post by Bölvaður on 2009-08-07
> **lovinglinux said:**
> 
I guess I could try distributing the extension as a deb file, so It would be possible to install the dependencies automatically. I will try to do that.

I recommend you doing so, for some weird reason this doesnt work for me :( but it looks as it should, Im pretty sure nothing is missing (but of course there is).

---

### Post by lovinglinux on 2009-08-07
> **Bölvaður said:**
> I recommend you doing so, for some weird reason this doesnt work for me :( but it looks as it should, Im pretty sure nothing is missing (but of course there is).

Actually I will put a dependency installation script in the next version. All you will need to do is click an install button in the extension preferences.

---

### Post by lovinglinux on 2009-08-08
I have released version 0.0.4, with these changes:

[list][*] dependencies installation added to the extension settings
[*] dependency on xclip was removed, which means only sqlite3 is required to run the extension
[*] database and backup files are created outside the extension directory, in the user profile, so data won't be lost after extension updates
[*] creation and deletion of backups appear now in real-time, so there is no need to reload the sidebar
[*] added a scan button to the sidebar to scan for installed packages and populate the database
[*] added a reload button to the sidebar to allow easy update of the data displayed after a scan
[*] package names selected in the package list are automatically sent to the clipboard and the browser search bar, thus allowing integration with any search plug-in or search web site.[/list]

I don't know when it will e available in the extension home page of Mozilla Add-ons, but you can get it in advance from:

 [https://addons.mozilla.org/en-US/firefox/addons/versions/13153](https://addons.mozilla.org/en-US/firefox/addons/versions/13153)

Please give some feedback about this new version. IMO, is way much better than the previous versions.

---

### Post by shantanuo on 2009-08-12
Very useful add-on indeed.

---

### Post by lovinglinux on 2009-08-12
> **shantanuo said:**
> Very useful add-on indeed.

Thank you. Any bugs or difficulties?

---

### Post by jerrrys on 2009-09-03
good job lovinglinux.  one question...any way to remove the screen icon and have it show up in menu?  i also have a drawer, but it won't let me put it there...

---

### Post by lovinglinux on 2009-09-03
> **jerrrys said:**
> good job lovinglinux.

Thank you. 

> **jerrrys said:**
> good job lovinglinux.  one question...any way to remove the screen icon and have it show up in menu?  i also have a drawer, but it won't let me put it there...

I don't understand the question. I guess I need some sleep :)

I'm currently working on improving FoxMediaCenter extension, which requires a lot of work, so I probably won't be updating Umarks for a while. Unless some serious bug appears. Nevertheless, it won't take too long to get into it. There are some things I want to do to improve it. For instance, sqlite3 won't be required anymore, so no more dependency installation.

Thanks for the feedback, I really depend on it to improve the extension.

---

### Post by jerrrys on 2009-09-03
not really that important, just have this thing about screen real estate...talk to ya again...

---

### Post by Ms_Angel_D on 2009-11-15
Any Chance on making this work with Karmic?

---

### Post by lovinglinux on 2009-11-15
> **Ms_Angel_D said:**
> Any Chance on making this work with Karmic?

It isn't working? What happens?

I'm running a new version that works on Karmic. If you are interested, I can upload it to you, but it has a serious bug. If you close the sidebar it increases the CPU activity to 100% until you open it again. You can avoid this by opening another sidebar before closing it.

---

### Post by Ms_Angel_D on 2009-11-15
> **lovinglinux said:**
> It isn't working? What happens?

I'm running a new version that works on Karmic. If you are interested, I can upload it to you, but it has a serious bug. If you close the sidebar it increases the CPU activity to 100% until you open it again. You can avoid this by opening another sidebar before closing it.

Oh I didn't realize I just uninstalled it because I didn't see any options to pick Karmic & 9.10 guess I'll have to check it out.

---

### Post by lovinglinux on 2009-11-15
> **Ms_Angel_D said:**
> Oh I didn't realize I just uninstalled it because I didn't see any options to pick Karmic & 9.10 guess I'll have to check it out.

Oh, you are correct. There is no such option yet. Nevertheless, it only affects the search feature, not the backups.

I will work on this as soon as I can.

---

### Post by lovinglinux on 2009-12-11
I have uploaded version 0.0.5, which has support for Karmic Koala and a new simplified interface. 

> **[COLOR="Red"]WARNING:[/COLOR]** There is a compatibility issue with All-in-One Sidebar extension, that causes high CPU usage when you close the UMarks sidebar. To avoid this you can switch to a different sidebar before closing it or disable All-in-One Sidebar.

---

### Post by lovinglinux on 2010-03-27
I have just released version 1.0.0, which is considered a stable version and is waiting for Mozilla approval.

This version has a simplified interface, which is launched from the status bar on a new window instead of a sidebar. The compatibility issue with AIOS has been fixed and the extension bring some new options like a style selector and option to select Lucid Linx in the preferences.

Please test it and give some feedback.

---

### Post by lovinglinux on 2010-04-14
I have released version 1.0.1, which has been approved by Mozilla. So now you can get the extension updates through Firefox add-on manager. Please install the new version, to make sure you will get future updates.

---

### Post by Bob63 on 2010-04-21
Tried it (v1.1.0), and I liked it. Looks to be very useful, and no real problems once I understood what the buttons do :).

What about other distros? For example, I like using LinuxMint. They have their own repos for somethings, although the distro is based on Ubuntu. If I have their repos activated - i.e. I'm in a fresh LinuxMint install, the script should pull their packages as well as the Ubuntu packages, right?

BTW, 6 days ago you posted that you released 1.0.1, but the version I got this morning from Mozilla Add-ons installed and shows v 1.1.0. Typo?

---

### Post by lovinglinux on 2010-04-21
> **Bob63 said:**
> Tried it (v1.1.0), and I liked it. Looks to be very useful, and no real problems once I understood what the buttons do :).

I'm trying to make a video tutorial, but recordmydesktop is not working properly in Lucid :(

> **Bob63 said:**
> BTW, 6 days ago you posted that you released 1.0.1, but the version I got this morning from Mozilla Add-ons installed and shows v 1.1.0. Typo?

Is not a typo. Version 1.1.0 is brand new and was uploaded yesterday. I haven't made any announcement yet, because I'm waiting for Mozilla to review and approve it. You can already download it with the direct link posted on my blog, but if you go to the [extension page at Mozilla](https://addons.mozilla.org/en-US/firefox/addon/13153) it still shows version 1.0.1, although I have already changed the extension descriptions and screenshots.

I have moved from 1.0.1 to 1.1.0 because the last one is a major release, which introduces the cache feature, allowing to download, export and import package archives, which means you don't have to download the packages on the destination machine anymore, if you are restoring backups from the same Ubuntu version and architecture. This will allow users to use the extension to replicate installed packages in multiple machines much faster than with version 1.0.1.

I'm very excited about this new feature. 

> **Bob63 said:**
> What about other distros? For example, I like using LinuxMint. They have their own repos for somethings, although the distro is based on Ubuntu. If I have their repos activated - i.e. I'm in a fresh LinuxMint install, the script should pull their packages as well as the Ubuntu packages, right?

The extension uses apt-get, aptitude and dpkg to set the packages, download and install, so they will be pulled from whatever repository you have in your sources list. I haven't tested on other distros, but as long as it uses apt-get, aptitude and dpkg, you should be fine. 

I'm going to test LinuxMint soon, just to make sure.

---

### Post by BrokenKingpin on 2010-04-21
I don't see why everything is a Firefox add-on; what does this have to do with web browsing? This should be something that Synaptic or Software Center should handle, not your web browser.

---

### Post by lovinglinux on 2010-04-21
> **BrokenKingpin said:**
> I don't see why everything is a Firefox add-on; what does this have to do with web browsing? This should be something that Synaptic or Software Center should handle, not your web browser.

This extension started as an add-on to search for packages on allmyapps.com and has evolved into a package backup system. So, that's why it is on the browser. Additionally, using Firefox extension API was much easier for me than making a program with python and building a gtk or qt gui.

I could have done it with shell scripts only, since the extension doesn't do package management by itself, but through temporary bash scripts that access apt-get, aptitude and dpkg. But doing it through Firefox provides easy installation and update platform.

Anyway, aside from the fact that making this a Firefox extension is easier for me, I don't see why this can't be a Firefox extension. Isn't Google OS making everything through the browser? As long as you make sure the user security is not compromised, what's wrong with it? The extension is isolated from the web and it doesn't do anything alone. It still needs that package management system and terminal to perform most of it's actions.

I have been using/developing it since Jaunty and works like a charm. When a new Ubuntu version is released, I create a backup with Umarks, then I make a clean install from alternate CD, installing only kde-minimal, kdeplasma-addons, kdm, xorg and firefox. Then I login, start Firefox and run my backup. It install everything I had before the clean installation. Have you tried?

BTW, if I could do everything from Firefox I would do it. It is the most used application on my machine and it is open all the time. For instance, I also have a an extension, called [FoxRunner](http://lovinglinux.megabyet.net/?page_id=527), that allows to run custom commands and scripts from Firefox. It saves me a lot of time doing things while browsing. It can even run commands posted on the forums from Firefox context menu.

---

### Post by BrokenKingpin on 2010-04-21
> **lovinglinux said:**
> 
Anyway, aside from the fact that making this a Firefox extension is easier for me, I don't see why this can't be a Firefox extension. Isn't Google OS making everything through the browser? As long as you make sure the user security is not compromised, what's wrong with it? The extension is isolated from the web and it doesn't do anything alone. It still needs that package management system and terminal to perform most of it's actions.
Google is doing everything through a browser because their entire OS revolves around the browser (which I personally have 0 interest in), Ubuntu does not. Package management has nothing to do with a web browser, so why limit it to Firefox, which not everyone uses. It just does not make sense to me that this type of utility is a browser add-on. I understand that making it as a FF extension is easier for you, so do what works for you, this is just my personal preference.

> **lovinglinux said:**
> For instance, I also have a an extension, called [FoxRunner](http://lovinglinux.megabyet.net/?page_id=527), that allows to run custom commands and scripts from Firefox. It saves me a lot of time doing things while browsing. It can even run commands posted on the forums from Firefox context menu.
This makes sense as an add-on as you are actually interacting with a webpage.

---

### Post by lovinglinux on 2010-04-21
> **BrokenKingpin said:**
> Google is doing everything through a browser because their entire OS revolves around the browser (which I personally have 0 interest in), Ubuntu does not. Package management has nothing to do with a web browser, so why limit it to Firefox, which not everyone uses. It just does not make sense to me that this type of utility is a browser add-on. I understand that making it as a FF extension is easier for you, so do what works for you, this is just my personal preference.


This makes sense as an add-on as you are actually interacting with a webpage.

But both interact with web pages.

---

### Post by Bob63 on 2010-04-21
Here's a thought:

If I wanted to duplicate an installation of a particular (supported) distro and all the packages, I would not only need the list of packages but the list of sources and the authentication keys. Anyway to include this type of info? Perhaps in a second file.

I mentioned above that I'm using LinuxMint, but I also have some packages from PPAs and sources like Medibuntu and GetDeb. I'm a moderately experienced user, but no technowizard, so I'm not familiar with any method to create a list of sources or authentication keys, short of hunting down the files in the existing system (I do know where the sources file is tho') and copying them down - not certain that would be viable for the authentication keys file anyhow.

This way a user could sit down at a bare PC, install a basic system from a USB thumb drive, install a FF add-on, grab  the lists off the thumbdrive and with a few clicks, install sources, keys and packages.

---

### Post by lovinglinux on 2010-04-21
> **Bob63 said:**
> Here's a thought:

If I wanted to duplicate an installation of a particular (supported) distro and all the packages, I would not only need the list of packages but the list of sources and the authentication keys. Anyway to include this type of info? Perhaps in a second file.

I mentioned above that I'm using LinuxMint, but I also have some packages from PPAs and sources like Medibuntu and GetDeb. I'm a moderately experienced user, but no technowizard, so I'm not familiar with any method to create a list of sources or authentication keys, short of hunting down the files in the existing system (I do know where the sources file is tho') and copying them down - not certain that would be viable for the authentication keys file anyhow.

This way a user could sit down at a bare PC, install a basic system from a USB thumb drive, install a FF add-on, grab  the lists off the thumbdrive and with a few clicks, install sources, keys and packages.

Yes, is doable. In fact, I have already thought about this, but decided to try to code this on the next version. Now I realize I should have made this priority. Kind of my habits fault. I usually update my sources list before doing anything else.

Thanks for bringing this up.

---

### Post by Bob63 on 2010-04-21
> **lovinglinux said:**
> Yes, is doable. In fact, I have already thought about this, but decided to try to code this on the next version. Now I realize I should have made this priority. Kind of my habits fault. I usually update my sources list before doing anything else.

Thanks for bringing this up.

You're welcome.

Actually, I think your priorities are fine. After all, first a piece of software has to do its designed task properly. Only then can it be enhanced. Look how many times MS (among others) has dropped the ball by adding features to wonky apps (or a wonky OS).:rolleyes:

---

### Post by lovinglinux on 2010-04-21
> **Bob63 said:**
> You're welcome.

Actually, I think your priorities are fine. After all, first a piece of software has to do its designed task properly. Only then can it be enhanced. Look how many times MS (among others) has dropped the ball by adding features to wonky apps (or a wonky OS).:rolleyes:

Thanks, but I have wonky stuff too :) One of my extensions has been rejected by Mozila editors twice, because I failed to avoid some javascript warnings. It works perfectly for me, but that's not enough. I'm leaving it on the "procrastination bin" for now, because it has 19.000 lines of code to go through. Another wonky thing, since I could make the code a lot smaller :oops:

---

### Post by lovinglinux on 2010-04-28
I have released a new version, which includes the ability to export/import/restore ppa and medibuntu sources. It also provides several new functionality, like new cache system and preview of which packages will be installed and removed by a back.

Please visit and subscribe to the new thread at [http://ubuntuforums.org/showthread.php?t=1464876](http://ubuntuforums.org/showthread.php?t=1464876)

I will be asking a moderator to lock this thread soon.

---

### Post by cariboo on 2010-04-28
Closed by request. See new thread here:

[http://ubuntuforums.org/showthread.php?t=1464876](http://ubuntuforums.org/showthread.php?t=1464876)

---

