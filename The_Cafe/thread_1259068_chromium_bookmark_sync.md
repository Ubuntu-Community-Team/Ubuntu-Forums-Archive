---
title: "chromium bookmark sync?"
date: 2009-09-05
forum: The Cafe
---

### Post by rifak on 2009-09-05
not sure exactly where to put this, but ive seen other threads about chromium here so i'll stick it here...and i can't see a forum over at the google chromium dev site.

but the question is, does anyone know when/if some sort of bookmark sync will be available for chromium? also, i know that xmarks (the firefox add-on) is working on a google chrome add-on, but no news about a dev xmarks for chromium. since chrome is built from chromium, will the xmarks for chrome work with chromium when its finished?

---

### Post by joey-elijah on 2009-09-06
i#ve installed the xmarks alpha on both chrome linux and chromium linux and it syncs fine! so go ahead and install it.

as for browser sync, i still can't seem to enable it in chrome linux, and i can't imagine it will be available in chromium since it uses Googles servers as a backend.

---

### Post by gnomeuser on 2009-09-06
I believe that sync support is now built in, just run chromium with the --enable-sync parameter to unlock it (early development). That should sync your bookmarks to a folder in Google Docs using XMPP.

---

### Post by rifak on 2009-09-06
with the xmarks option, i tried it last week but it said that the testing is full and i have to wait in order to get the alpha version.

the other --enable-sync doesnt seem to work for me. i use it, and nothing happens. i check in google docs and nothing shows up. i look if there are any options to turn on sync in the options windows and nothing. but now also, ive heard everyone saying that the --enable-plugins flag isnt needed any longer for flash to work, but it is needed in mine. so im not sure if something is a matter with my installation or what.

---

### Post by hanzomon4 on 2009-09-06
Same here with the plugins

---

### Post by gnomeuser on 2009-09-06
[http://arstechnica.com/open-source/news/2009/08/hands-on-bookmark-sync-lands-in-chrome-developer-builds.ars](http://arstechnica.com/open-source/news/2009/08/hands-on-bookmark-sync-lands-in-chrome-developer-builds.ars)

---

### Post by bakshi.hrishikesh on 2009-10-15
> **gnomeuser said:**
> [http://arstechnica.com/open-source/news/2009/08/hands-on-bookmark-sync-lands-in-chrome-developer-builds.ars](http://arstechnica.com/open-source/news/2009/08/hands-on-bookmark-sync-lands-in-chrome-developer-builds.ars)

That is for windows. It says not available for Linux yet.

---

### Post by jetpeach on 2009-10-15
testing for the alpha version of Xmarks was available instantly when i "signed up". i created a new account for Xmarks (don't want to rink my current firefox bookmarks on Xmarks) as a precaution, since it's alpha...
but so far it seems to work great.
steps:
1) update to newest chromium-browser using daily build repo
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
2) sign in (or sign up, link on right) to alpha build of xmarks 
[http://login.xmarks.com/?referrer=http://beta.xmarks.com/welcome](http://login.xmarks.com/?referrer=http://beta.xmarks.com/welcome)
3) after signing in, bottom section is "Xmarks for Chrome alpha" and click sign up. instantly (for me) it let me then click "Getting started" and download the plugin
4) after downloading and installing (downloaded in chromium and it simply asked if i wanted to install it), restart chromium and Xmarks is on the bottom left corner. click it, sign in and if you like choose the option "enable automatic synchronization"

works for me, i have an "--enable-plugins" flag on my chromium icon so it always starts that way when i click it, although i'm not sure this is necessary or not in the latest chromium build...

---

### Post by rifak on 2009-10-15
yeah ive had xmarks installed in chromium for a while now and it works great. but i thought the windows version has an option that syncs it with google documents or something...i dunno, maybe im completely wrong, but i was just wondering. its not a big deal now that xmarks has active development/working addon.

---

### Post by mathyou on 2009-10-25
> **jetpeach said:**
> 
4) after downloading and installing (downloaded in chromium and it simply asked if i wanted to install it), restart chromium and Xmarks is on the bottom left corner. click it, sign in and if you like choose the option "enable automatic synchronization"

works for me, i have an "--enable-plugins" flag on my chromium icon so it always starts that way when i click it, although i'm not sure this is necessary or not in the latest chromium build...

I don't get anything in the bottom left corner. If I go to extensions, the 'options' button for xmarks is greyed out. No where to sign in... :(

---

### Post by FatalChaos on 2009-10-27
> **mathyou said:**
> I don't get anything in the bottom left corner. If I go to extensions, the 'options' button for xmarks is greyed out. No where to sign in... :(

I have this same option, it appears for all of my extensions (lastpass, adblock+, and xmarks). Anyone have any idea what the issue could be? I tried the --enable-extensions flag already.

---

### Post by amarkovits on 2009-10-30
> **FatalChaos said:**
> I have this same option, it appears for all of my extensions (lastpass, adblock+, and xmarks). Anyone have any idea what the issue could be? I tried the --enable-extensions flag already.

same problem for me, any fix?

---

### Post by jetpeach on 2009-10-31
i now have the same problem - are you running 64 bit now? i saw that chromium is now using native 64 bit instead of ia32bit to emulate 32 bits... i'm wondering if this could be the problem. xmarks still works fine on the computers i already have it installed on, but the ones i've upgraded to 64bit karmic i can't get it installed on either...

---

### Post by FatalChaos on 2009-11-02
> **jetpeach said:**
> i now have the same problem - are you running 64 bit now? i saw that chromium is now using native 64 bit instead of ia32bit to emulate 32 bits... i'm wondering if this could be the problem. xmarks still works fine on the computers i already have it installed on, but the ones i've upgraded to 64bit karmic i can't get it installed on either...

I'm running the 32 bit version.

---

### Post by rifak on 2009-11-02
im running 32bit version and it's still not working...hmmm

---

### Post by abhiroopb on 2009-11-05
Just updated chromium. It appears that there is an option in the drop down tools menu that reads:

"Sync my bookmarks"

It is greyed out so I can't click on it, but any ideas what this is for? And when google will allow us to use it??

---

### Post by rifak on 2009-11-05
yes, i have the option to Sync but is also greyed out..must be coming soon. also, for those of you who are looking for xmarks, im pretty sure the newer version has a button in the top left corner (where the wrench and options are and stuff). i kept trying to install, reinstall, and rereinstall and nothing every came up down in the bottom right or left corner lol my eyes were wandering and noticed that it is now in the top right by the address bar and options buttons. so, i would check this for those of you who are having troubles.

---

### Post by HappinessNow on 2009-11-05
> **gnomeuser said:**
> I believe that sync support is now built in, just run chromium with the --enable-sync parameter to unlock it (early development). That should sync your bookmarks to a folder in Google Docs using XMPP.It is built in to the latest Developers build,you could also use [Chrome Dial]("http://www.chromeextensions.org/tabs/chrome-dial/") (which syncs to your bookmarks also), again to use Chrome Dial you need to upgrade to the latest Developers Build of Google Chrome/Chromium (see my sig for link).

---

### Post by HappinessNow on 2009-11-05
> **abhiroopb said:**
> Just updated chromium. It appears that there is an option in the drop down tools menu that reads:

"Sync my bookmarks"

It is greyed out so I can't click on it, but any ideas what this is for? And when google will allow us to use it??How about Now!

---

### Post by abhiroopb on 2009-11-05
Which build are you using? Just updated (like a minute ago) and its still not there!

---

### Post by ufmace on 2009-11-06
> **&#20170 said:**
> How about Now!

How'd you manage that? I have the daily builds and just updated it now. About shows version 4.0.237.0 build 31094, and I'm passing --enable-sync, and it's still grayed out. And adblock doesn't seem to be working either.

---

### Post by abhiroopb on 2009-11-06
Still not working for me, just updated.

---

### Post by ikkefc3 on 2009-11-07
> **&#20170 said:**
> How about Now!

It's still greyed out.

---

### Post by re404 on 2009-11-08
> **ufmace said:**
> I'm passing --enable-sync, and it's still grayed out. And adblock doesn't seem to be working either.

how do you do that anyway?

thanks,
R//

---

### Post by abhiroopb on 2009-11-08
The way to do it is:

Type in gksudo gedit /etc/chromium-browser/default in a terminal. And then where its says: CHROMIUM_FLAGS:"". Type in --enable-sync or some other flag.

---

### Post by HappinessNow on 2009-11-09
> **abhiroopb said:**
> which build are you using? Just updated (like a minute ago) and its still not there!

4.0.237.0

---

### Post by abhiroopb on 2009-11-09
I'm on 4.0.241.0...still not there!

---

### Post by re404 on 2009-11-10
I even re-followed all these steps an I'm running 4.0.242.0 (build 31427) now.

I put this in my menu command line: 
**chromium-browser --enable-plugins --enable-sync %U**

And this is in my **/etc/chromium-browser/default**
```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--enable-sync"
```

Still no synced bookmarks!

HELP!

Thanks!

---

### Post by vagamente on 2009-11-12
Nothing... even with 4.0.245.0 (Ubuntu build 31665) and flag activated...

---

### Post by hi.io on 2009-11-14
Just got the sync in the new build, but mine is also greyed out.  If you start chrome and quickly click the spanner I see 'sync my bookmarks' activated for a split second then it greys out :(.  It's enough time to click it but it doesn't do anything.  I've got the --enable-sync flag in.

---

### Post by woodrobin on 2009-11-15
Using the latest Chromium build ( 4.0.248.0 (Ubuntu build 32003) ) I have working bookmark sync.

Here is my /etc/chromium/default file contents:

> # Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--enable-sync"Without the --enable-sync added, the option is still grayed out.  With it, the option is active and works.

---

### Post by l-x-l on 2009-11-15
> **re404 said:**
> 

And this is in my **/etc/chromium-browser/default**
```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--enable-sync"
```


Works perfectly for me. Thx.

---

### Post by jensbodal on 2009-11-20
To enable browser sync I just added the --enable-sync to the end of the shortcut installer, and although it is no longer greyed out and claims my browser is synced, it does not seem to be syncing.  I know I have my Chrome browser synced in Windows with 2 computers just fine, and after I enabled it in Ubuntu so far nothing has showed up, maybe it takes longer or maybe I need to do something else.

The feature and all the options are definitely there, just doesn't seem to be working.

---

### Post by luptinpitman on 2009-11-23
Upgraded to 4.0.249.11 and 'Sync my bookmarks' is again disabled (greyed out) with or without --enable-sync.  Checked on two different machines one 9.04 and the other 9.10.

---

### Post by ron5678 on 2009-11-25
All,

I had problems as you all have discribed recently but resolved it by renaming a directory. In all its a simple five steps.

First, I made /etc/chromium-browser/default contain the right flag (CHROMIUM_FLAGS="--enable-sync").

Second, I had to close chromium and delete the /home/username/.conf/chromium folder.  This action loses your prior chromium settings. You might see other chromium related folders that need to deleted under /home/username/.conf and /home/username/.cache/.

Third, launch chromium.  The application acts like this is the first time. Go to the wrench and you will see "Sync my bookmarks" enabled.  Chose it then it gets straight forward.

Fourth, I made appropriate changes to my browser settings since I'd lost them in step 2.

Final, go to another computer and repeat the steps. This time you should see it get sync.

Hope this helps.

---

### Post by ron5678 on 2009-11-25
oops, accidently posted #35 twice. I wish I could delete this.

---

### Post by luptinpitman on 2009-11-25
No such directory exists for me "/etc/chromium-browser/default"

I've reinstalled two machines clean with a fresh install of Chrome and the sync option is grey from the get go so killing an old config file doesn't seem like it would fix the problem anyway.

I am using the Google branded version of Chrome that is installable from Ubuntu Tweak (not that I think the behavior is any different for Chromium).

Thank you for the help.

For the record it looks like other people are seeing the issue as well:  [http://code.google.com/p/chromium/issues/detail?id=28655](http://code.google.com/p/chromium/issues/detail?id=28655)

---

### Post by ron5678 on 2009-11-26
/etc/chromium-browser/default is a file, not a directory. "default" is the file name.

---

### Post by luptinpitman on 2009-11-27
There is no chromium-browser folder under /etc...

Using google-chrome-unstable which obviously creates a different directory structure than a Chromium install, which would explain why I don't have the chromium-browser directory.

But again, the point is moot as a fresh install on a newly installed machine of either Karmic or Jaunty with this particular version disables bookmark sync so deleting any old config files isn't going to have an effect as far as I can see.

I am not the only one seeing the behavior and it appears to affect both google-chrome and chromium installs:  [http://code.google.com/p/chromium/issues/detail?id=28655](http://code.google.com/p/chromium/issues/detail?id=28655)

---

### Post by luptinpitman on 2009-12-01
FWIW:  I was able to get sync functionality back by using chromium-browser instead of google-chrome-unstable.

Current version:  4.0.260.0 (Ubuntu build 33244)

Still have to pass the --enable-sync option.

Was able to confirm this on two different installs; one Ubuntu 9.10 i386 and the other on Linux Mint "Helena".

Installed from either ubuntu-tweak or by manually adding repository shown here:
  
[http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)

Also updated original bug report:  [http://code.google.com/p/chromium/issues/detail?id=28655](http://code.google.com/p/chromium/issues/detail?id=28655)

---

### Post by abhiroopb on 2009-12-06
Sync my bookmarks finally appeared and synced everything perfectly to Google Docs (what a strange place to sync to!)

Build: 4.0.265.0 (Ubuntu build 33925)

Slightly off-topic:

I like using the older version of [adsweep]("http://adsweep.org/") (ver 1.6) which works better for me than the 2.0 version but Chromium insists on auto-updating to the 2.0 version. Is there any way to inhibit this?

---

### Post by SneakyBooBoo on 2009-12-07
i found where Chrome 4.0.249 installs to.

> /opt/google/chrome

From there on i'm clueless what to do next. I can't find the defaults file.

---

