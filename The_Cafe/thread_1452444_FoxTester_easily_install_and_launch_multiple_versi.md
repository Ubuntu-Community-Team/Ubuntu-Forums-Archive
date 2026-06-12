---
title: "FoxTester: easily install and launch multiple versions of Firefox simultaneously"
date: 2010-04-11
forum: The Cafe
---

### Post by lovinglinux on 2010-04-11
FoxTester is an extension that allows to Install and launch multiple versions of Firefox while using the default installation and without affecting the default user profile.

[http://www.webgapps.org/addons/foxtester](http://www.webgapps.org/addons/foxtester)

---

### Post by darrenn on 2010-04-12
This will be perfect for the people who want to try out Firefox Lorentz. Like most I hate it when a tab crashes the whole browser. Thanks in advance for creating this.

---

### Post by lovinglinux on 2010-04-12
> **darrenn said:**
> This will be perfect for the people who want to try out Firefox Lorentz. Like most I hate it when a tab crashes the whole browser. Thanks in advance for creating this.

Thanks. I had the idea of creating this when testing Lorentz. :)

---

### Post by Toost Inc. on 2010-04-12
Very awesome. Thanks

Edit: I thought I found this bug where FoxTester didn´t work when the Danbooru Downloader addon was installed as well but aparently that was a fluke since I´ve got now both enabled and can´t reproduce it.

FoxTester does hoewer list every file and install twice for me, but that´s hardly minor.

Screenshot:
[http://i41.tinypic.com/jfg7t4.jpg](http://i41.tinypic.com/jfg7t4.jpg)

Also maybe it´s an idea to add an option to copy your current profile/compatible extensions or like you said make the install more permanent.

---

### Post by lovinglinux on 2010-04-15
> **Toost Inc. said:**
> Very awesome. Thanks.

You are welcome and thanks for the feedback. 

> **Toost Inc. said:**
> Edit: I thought I found this bug where FoxTester didn´t work when the Danbooru Downloader addon was installed as well but aparently that was a fluke since I´ve got now both enabled and can´t reproduce it.

The problem with Danbooru Downloader could be a compatibility issue,  because a couple of functions weren't wrapped in the extension functions and were using common names, so they could conflict with other extensions using similar function names. This has been fixed in the version 1.0.1, which I have uploaded today.

Please let me know if it happens again.

> **Toost Inc. said:**
> FoxTester does hoewer list every file and install twice for me, but that´s hardly minor.

Please tell me if you get duplicated records when after restarting Firefox, when you first access the context menu?

I'm asking this because the extension scans for new files and update the database every time you access the menu and rebuild the menu options with all records from the database. So, instead of adding new records to the menu, it actually recreates all menu options on-the-fly. Nevertheless, I was experiencing a similar problem on another extension of mine. I'm still not sure if this is a Firefox bug or if there is something not working on the extension as it should be.

> **Toost Inc. said:**
> Also maybe it´s an idea to add an option to copy your current profile/compatible extensions or like you said make the install more permanent.

Both options were initially on the design plan, but the extension started to get bloated and complicated, so I decided to release a simpler version and improve from there, based on the users feedback. So there is a big chance that both features will be implemented in future versions. Thanks for the suggestion.

---

### Post by lovinglinux on 2010-05-14
**[COLOR="Red"]Warning:[/COLOR]** FoxTester 1.0.1 is suffering from memory leak when you open several new windows instead of tabs. I know where the problem is, but I don't know yet how to fix it without disabling some functionality. Therefore, I'm putting this extension on inactive status, until I can provide a fully functional version. I recommend disabling this extension until then.

---

### Post by lovinglinux on 2010-05-16
FoxTester 1.0.2 has been released!

This new version brings some important bug fixes and new features. There is no more issues with leaking memory, the file integrity check incompatibilities has been fixed and now you can set any version installed through FoxTester to be your default browser, so you can use it with your Firefox user profile.

[See the video demo](http://foxtester-extension.blogspot.com/2010/05/foxtester-102-released.html).

---

### Post by lovinglinux on 2010-05-31
FoxTester has been approved by Mozilla, so now it is available through the Stable Channel and future updates will be available through Firefox add-on manager.

---

### Post by primetime34 on 2010-07-07
I set the new firefox 4 beta as default...now I can't use foxtester to revert back to the stable release.  Any help on how to do that?  Thanks.

---

### Post by lovinglinux on 2010-07-07
> **primetime34 said:**
> I set the new firefox 4 beta as default...now I can't use foxtester to revert back to the stable release.  Any help on how to do that?  Thanks.

```

sudo rm -r /opt/firefox
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox 
```

This will delete Firefox 4 and revert to the default version.

---

### Post by The Real Dave on 2010-07-07
I'm loving Foxtester :) I must just update from 3.7A5 :D Thanks for spreading this mate :)

---

### Post by lovinglinux on 2010-07-07
> **The Real Dave said:**
> I'm loving Foxtester :) I must just update from 3.7A5 :D Thanks for spreading this mate :)

You are welcome. I will make it compatible with 4.0b soon. The next version will not use the firefox divertion when you set it as default, which will make easier to revert.

---

### Post by Shining Arcanine on 2010-07-07
How does this interact with your system's package manager? Will it pollute your root directory?

---

### Post by lovinglinux on 2010-07-07
> **Shining Arcanine said:**
> How does this interact with your system's package manager? Will it pollute your root directory?

No and no. It install all versions under Firefox profile folder, in a folder named "foxtester", except when you set a version as default, when it copies the install folder to /opt/firefox.

If you already have a firefox folder under /opt, then it will detect it and only allow to set another version as default after removing the one in the opt folder.

---

### Post by xtnsgo on 2010-07-11
Such a good extension!!!  Testing FF 4.0 with it now, thanks:)

---

### Post by lovinglinux on 2010-07-11
> **xtnsgo said:**
> Such a good extension!!!  Testing FF 4.0 with it now, thanks:)

You are welcome. :)

---

### Post by Gavin77 on 2010-07-19
I'm trying this out on FF 3.6.6 & Kubuntu Lucid.  Am I missing any dependencies as it doesn't work.  It creates empty folders in the Foxtester subfolder of my FF profile and the created profile only contains prefs.js with 0 bytes size.

I've tested it with:
firefox-3.6.7.tar.bz2
firefox-4.0b1.tar.bz2
firefox-4.0b2pre.en-US.linux-i686.tar.bz2

---

### Post by lovinglinux on 2010-07-19
> **Gavin77 said:**
> I'm trying this out on FF 3.6.6 & Kubuntu Lucid.  Am I missing any dependencies as it doesn't work.  It creates empty folders in the Foxtester subfolder of my FF profile and the created profile only contains prefs.js with 0 bytes size.

I've tested it with:
firefox-3.6.7.tar.bz2
firefox-4.0b1.tar.bz2
firefox-4.0b2pre.en-US.linux-i686.tar.bz2

The profile files should be created when you start the installed testing version. What happens when you choose the "Launch" option from the menu?

---

### Post by Gavin77 on 2010-07-19
When I select Launch, nothing at all happens.
In my profile these are the only folders/files created after choosing to install firefox 4b1 for example:

> ~/.mozilla/firefox/gox9hspw.default/foxtester/install/
~/.mozilla/firefox/gox9hspw.default/foxtester/install/firefox-4-0b1/
~/.mozilla/firefox/gox9hspw.default/foxtester/profiles/
~/.mozilla/firefox/gox9hspw.default/foxtester/profiles/firefox-4-0b1-foxtester/prefs.js


---

### Post by Gavin77 on 2010-07-19
I just tried manually extracting the firefox archive into the /foxtester/install/firefox-4-0b1 directory and then launching it and it worked so there's a problem with the initial extraction phase.

---

### Post by lovinglinux on 2010-07-19
> **Gavin77 said:**
> I just tried manually extracting the firefox archive into the /foxtester/install/firefox-4-0b1 directory and then launching it and it worked so there's a problem with the initial extraction phase.

That's what I was suspecting. See if you can extract it with **tar -xvjf**. That is what the extension uses.

---

### Post by Gavin77 on 2010-07-19
> **lovinglinux said:**
> That's what I was suspecting. See if you can extract it with **tar -xvjf**. That is what the extension uses.

The archive extracts fine manually using **tar -xvjf**

---

### Post by Gavin77 on 2010-07-19
You'll be glad to know that I've figured out what the problem was.  I had a space in the folder name of my source directory.  I changed Firefox Builds to Firefox_Builds and it works now :)

---

### Post by lovinglinux on 2010-07-19
> **Gavin77 said:**
> You'll be glad to know that I've figured out what the problem was.  I had a space in the folder name of my source directory.  I changed Firefox Builds to Firefox_Builds and it works now :)

Good to know. Thanks for the heads up. I need to update the extension to work with Firefox 4 and to make some improvements, so I will look into this issue too.

---

### Post by lovinglinux on 2010-07-19
I have created a bug report at [http://code.google.com/p/foxtester/issues/detail?id=2](http://code.google.com/p/foxtester/issues/detail?id=2) so it can be tracked.

---

### Post by jminker on 2010-07-19
I just found your extension today while searching for a way to test Firefox 4 without interfering with my default install. I checked out the demo and decided to install it, and within minutes I had a fully functioning Firefox 4 install running side-by-side with my current 3.6.6 install. What an excellent idea for an extension! Thanks for coming up with it.

Jim

---

### Post by lovinglinux on 2010-07-19
> **jminker said:**
> I just found your extension today while searching for a way to test Firefox 4 without interfering with my default install. I checked out the demo and decided to install it, and within minutes I had a fully functioning Firefox 4 install running side-by-side with my current 3.6.6 install. What an excellent idea for an extension! Thanks for coming up with it.

Jim

I'm glad to read that. Thanks a lot. It needs improvements, but it works quite well for me. I have created it because I need to test my extensions with different versions of Firefox. Additionally, in order to support Firefox users I usually need to test several versions. So it is quite handy :)

---

### Post by lovinglinux on 2010-07-19
[FoxTester 1.0.3](http://foxtester-extension.blogspot.com) has been released today and is available for download through the extension site. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This new version just adds compatibility with Firefox 4.0b2pre.

---

### Post by lovinglinux on 2010-07-21
FoxTester 1.0.4 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This new version just adds compatibility with Firefox 4.0b3pre.

---

### Post by lovinglinux on 2010-07-26
FoxTester 1.0.5 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This new version fixes an issue with upper case hashes and spaces

---

### Post by japzone on 2010-09-08
Firefox 4.0b5 is here!!:popcorn:

Time to see what's better.

One thing I wish is that Greasemonkey and Session Manager would update for comparability with Firefox 4.0. They are my Two most used Extensions and I miss them when using 4.0.

---

### Post by lovinglinux on 2010-09-08
> **japzone said:**
> Firefox 4.0b5 is here!!:popcorn:

Time to see what's better.

One thing I wish is that Greasemonkey and Session Manager would update for comparability with Firefox 4.0. They are my Two most used Extensions and I miss them when using 4.0.

Indeed. I'm using 4.0b5 for a couple of days, since the first build candidate was available. Is looking really good so far, although there are still 19 extensions disable on my profile and 52 enabled. Most of the enabled ones are not compatible, but still work with compatibility check disabled.

---

### Post by japzone on 2010-09-10
New Add-On for Firefox 4.0 from Mozilla. It's called [Add-On Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"). It's for Reporting whether certain Add-Ons Still Work or Don't Work in Firefox 4.0 and if they Work a Little what Features Don't Work Properly. When you install it it Disables the Compatibility Block Automatically without having to add a String to Firefox's Config Screen. It's the very tool I've been wishing I had when Beta testing. Give it a try.

_**Add-On Compatibility Reporter**_:
[https://addons.mozilla.org/en-US/firefox/addon/15003/](https://addons.mozilla.org/en-US/firefox/addon/15003/)

---

### Post by lovinglinux on 2010-09-10
> **japzone said:**
> New Add-On for Firefox 4.0 from Mozilla. It's called [Add-On Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"). It's for Reporting whether certain Add-Ons Still Work or Don't Work in Firefox 4.0 and if they Work a Little what Features Don't Work Properly. When you install it it Disables the Compatibility Block Automatically without having to add a String to Firefox's Config Screen. It's the very tool I've been wishing I had when Beta testing. Give it a try.

_**Add-On Compatibility Reporter**_:
[https://addons.mozilla.org/en-US/firefox/addon/15003/](https://addons.mozilla.org/en-US/firefox/addon/15003/)

Is not new, but that is what I recommend on my tutorials. I'm currently using it with FF 4. Nevertheless, due to Firefox extreme changes, several extensions don't work, even with this add-on.

---

### Post by japzone on 2010-09-10
> **lovinglinux said:**
> Is not new, but that is what I recommend on my tutorials. I'm currently using it with FF 4. Nevertheless, due to Firefox extreme changes, several extensions don't work, even with this add-on.

Thankfully it turns out Session Manager does work with 4.0 so that makes me happy. You never know If you screw something up and FF crashes, and I prefer Session Manager's Restoration Options to FF built in ones.

---

### Post by simonchimera on 2010-09-13
I've just tried installing the latest stable FoxTester along with firefox-4.0b5.tar.bz2 for my x64 Ubuntu machine and when I enable the beta Firefox the majority of the icons on the tool bar are missing and have a red cross instead. Does anyone know if I have missed something here or is this a bug?

---

### Post by lovinglinux on 2010-09-13
> **simonchimera said:**
> I've just tried installing the latest stable FoxTester along with firefox-4.0b5.tar.bz2 for my x64 Ubuntu machine and when I enable the beta Firefox the majority of the icons on the tool bar are missing and have a red cross instead. Does anyone know if I have missed something here or is this a bug?

Did you get the 64 bit version of Firefox?

---

### Post by simonchimera on 2010-09-13
> **lovinglinux said:**
> Did you get the 64 bit version of Firefox?

In the Mozilla FTP I downloaded from the linux-x86_64 then en-US. I think this is the right version but I'm not 100%

edit: just downloaded and tried the linux-i686 version as well to check but this has the same outcome - no icons.

---

### Post by simonchimera on 2010-09-13
Just reinstalled the x86_64 tar.bz2 file three times and on the third attempt I now have icons! Must have been a bad download or something?

---

### Post by lovinglinux on 2010-09-13
> **simonchimera said:**
> Just reinstalled the x86_64 tar.bz2 file three times and on the third attempt I now have icons! Must have been a bad download or something?

The extension also has a hash checker, so you can check the download integrity before installing. To do that, highlight the hash number on Mozilla's FTP site, then select "Check File" option from the extension menu and select the file to be checked.

---

### Post by lovinglinux on 2010-09-16
FoxTester 1.0.6 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This new version fixes an issue with watched folder names containing spaces.

---

### Post by Budchekov on 2010-11-16
Hi lovinglinux, many thanks for a wonderful addon, I came across it at Mozillazine, sure makes things easy.
Is there any way to launch 4.0 versions other than firing up 3.6 and right clicking, create a launcher/desktop shortcut?
Bud.

---

### Post by lovinglinux on 2010-11-17
> **Budchekov said:**
> Hi lovinglinux, many thanks for a wonderful addon, I came across it at Mozillazine, sure makes things easy.
Is there any way to launch 4.0 versions other than firing up 3.6 and right clicking, create a launcher/desktop shortcut?
Bud.

You are welcome.

Unfortunately, this feature is not available right now, but I will consider it for a future version.

---

### Post by lovinglinux on 2010-12-08
FoxTester 1.0.9 has been released today and is available for [download]("https://addons.mozilla.org/en-US/firefox/addon/141505/versions/"). It will be available through Firefox extension manager as soon it gets reviewed by Mozilla editors. 

This version fixed missing plugin folders and updates the skin due to Firefox 4 changes.

---

### Post by lovinglinux on 2011-03-21
Edited

---

### Post by lovinglinux on 2011-03-25
I received some compelling requests to bring FoxTester back. So here it is. 

Version 1.1.0 is available for download. This version brings some improvements and bug fixes.

**Changelog:**

[LIST]
[*]moved menu to the toolbar icon
[*]fixed menu issues
[*]removed hash check functionality
[*]added latest-mozilla-central download feature
[/LIST]

**IMPORTANT:** It is recommended to uninstall all versions of Firefox installed by previous FoxTester versions, prior to upgrading the extension.

---

### Post by lovinglinux on 2011-04-13
FoxTester 1.1.2 has been released today and is available for download.

This version adds support for new Mozilla development scheme and repositories.

It is recommended to use the new "Reset" function to clean up all installations before using this new version.

**Changelog:**

[LIST]
[*]added support for new Mozilla development scheme and repositories
[*]added option to reset all installations and database
[*]added links to releases, beta, aurora and nightly ftp repositories
[/LIST]

---

### Post by lovinglinux on 2011-04-19
FoxTester 1.1.3 has been released today and is available for download.

This version fixed a reported bug, that affects non-English files from aurora and mozilla-central, causing the version numbers to be displayed improperly in the menus.

**Changelog:**
[LIST]
[*]improved menu file names regex
[*]changed uninstall icon
[/LIST]

---

### Post by lovinglinux on 2011-04-30
FoxTester 1.1.4 has been released today and is available for download.

This version introduces support for testing Fennec (Firefox for mobile), Seamonkey and Thunderbird, among other improvements.

**Changelog:**

[LIST]
[*]added support for testing Fennec, Seamonkey and Thunderbird
[*]added link redirection according to browser language
[*]added dynamic icons to sub menus, according to application and version
[*]switched from ftp to http links
[*]fixed oncommand  security issues
[*]improved preferences dialog
[/LIST]

---

### Post by lovinglinux on 2011-07-06
Released version 1.1.7

**Changelog**

[LIST]
[*]fixed first run download menus errors
[*]added compatibility with Firefox 8.0a1
[*]added mouse pointer effects to images
[/LIST]

---

### Post by AlexanderDGreat on 2011-08-14
Thank you, lovinglinux, because of you Firefox gets a little better everyday! How do you use it? :)

---

### Post by lovinglinux on 2011-08-15
> **AlexanderDGreat said:**
> Thank you, lovinglinux, because of you Firefox gets a little better everyday! How do you use it? :)

You are welcome.

You can find instructions on how to use it at [http://www.webgapps.org/add-ons/foxtester/documentation](http://www.webgapps.org/add-ons/foxtester/documentation)

---

### Post by AlexanderDGreat on 2011-08-15
Found it! I'm amazed at your work! Keep it up. Thanks! :)

---

### Post by el_koraco on 2011-08-15
I'm interrested in how the new add-on model will work when Aurora goes to 8. A stable nr 6 has appeared on the FTP server, so it ain't gonna be long now.

---

### Post by lovinglinux on 2011-08-15
> **AlexanderDGreat said:**
> Found it! I'm amazed at your work! Keep it up. Thanks! :)

Thanks.

> **el_koraco said:**
> I'm interrested in how the new add-on model will work when Aurora goes to 8.

What do you mean?

> **el_koraco said:**
> A stable nr 6 has appeared on the FTP server, so it ain't gonna be long now.

It is scheduled for tomorrow.

---

### Post by el_koraco on 2011-08-15
> **lovinglinux said:**
> Thanks.
What do you mean?


[This]("http://www.h-online.com/open/news/item/Firefox-6-available-version-8-to-offer-add-on-control-Update-1322874.html"). Admittedly, not a problem in our case, but let's see how this works on the Windows side. It's gonna be a PITA for you with upgrades and your gazillion add-ons :D

---

### Post by lovinglinux on 2011-08-15
> **el_koraco said:**
> [This]("http://www.h-online.com/open/news/item/Firefox-6-available-version-8-to-offer-add-on-control-Update-1322874.html"). Admittedly, not a problem in our case, but let's see how this works on the Windows side. It's gonna be a PITA for you with upgrades and your gazillion add-ons :D

That only affects add-ons installed by third-party applications. I don't have any of those. However, this will also affect add-ons installed globally, like *Ubuntu Firefox Modifications* (ubufox) and *Global Menu Bar Integration* (firefox-globalmenu), shipped with Ubuntu. So we may receive a warning for those add-ons, unless the Ubuntu MozillaTeam do something about it.

---

