---
title: "The Firefox cop of coffee"
date: 2011-04-20
forum: The Cafe
---

### Post by Shmantiv_Radio on 2011-04-20
As in the time you have to make one while Firefox awakes from hibernation, looks around, stretches, and decides to launch.

Why *does* Firefox take so long to launch? Chrome on the same PC (netbook) launches within about a second.. =/

---

### Post by robro on 2011-04-20
I am having this problem too, it takes like 10-30 seconds to launch while opera/chromium take 1-5 seconds, but still better than windows (1 - 5 MINUTES!)

---

### Post by Dustin2128 on 2011-04-20
What? Firefox launches instantly for me.

---

### Post by Lucradia on 2011-04-20
> **Dustin2128 said:**
> What? Firefox launches instantly for me.

Same, in both Windows 7 and Ubuntu and about 2 second(s) on my Xubuntu Netbook.

---

### Post by Shmantiv_Radio on 2011-04-20
> **Dustin2128 said:**
> What? Firefox launches instantly for me.

With or without addons?

---

### Post by Elfy on 2011-04-20
With.

---

### Post by Lucradia on 2011-04-20
> **Shmantiv_Radio said:**
> With or without addons?

With addons for me:

greasemonkey and Screengrab

Nothing else is needed because I use my hosts file, so no need for ABP. ubufox doesn't work with Firefox 4.0, so it's disabled.

Also, I never hibernate my computer, or put it to sleep. If I, myself, go on a trip to across town, or go to sleep myself, I always **halt** ;)

---

### Post by Dry Lips on 2011-04-20
I've got a lot of Add-ons on Firefox, but it takes just a few seconds to launch it...
Seems like there's something wrong with your installation... Perhaps an add-on
that is causing trouble?

---

### Post by Shmantiv_Radio on 2011-04-20
> **Lucradia said:**
> With addons for me:

greasemonkey and Screengrab

Nothing else is needed because I use my hosts file, so no need for ABP. ubufox doesn't work with Firefox 4.0, so it's disabled.

Also, I never hibernate my computer, or put it to sleep. If I, myself, go on a trip to across town, or go to sleep myself, I always **halt** ;)

I meant hibernation in a sarcastic sense lol.

I've always had this problem with Firefox for years on Windows and Ubuntu :(

---

### Post by Elfy on 2011-04-20
Have you tried renaming .mozilla and seeing if it works faster then?

---

### Post by Shmantiv_Radio on 2011-04-20
> **forestpiskie said:**
> Have you tried renaming .mozilla and seeing if it works faster then?

I just tried that and it opened a bit faster. Still took about 5 seconds though.

---

### Post by mikewhatever on 2011-04-20
Got any addons from this list installed?
[https://addons.mozilla.org/en-US/firefox/performance/](https://addons.mozilla.org/en-US/firefox/performance/)

---

### Post by kaldor on 2011-04-20
On a non-cold start, Firefox 4.0 loads in roughly 3 seconds each time. Chromium 12 is almost instant.

Firefox 3.x was horrible, though. After upgrading to Firefox betas a few months ago I noticed a huge improvement.

Note I use very few addons and I do have three app tabs on Firefox.

---

### Post by Lucradia on 2011-04-20
> **mikewhatever said:**
> Got any addons from this list installed?
[https://addons.mozilla.org/en-US/firefox/performance/](https://addons.mozilla.org/en-US/firefox/performance/)

As a note: VideoDownloadHelper is junk now. You can't use the old transcode features anymore without paying a subscription, as well as other things. Better off with the MP4 download from userscripts.org

---

### Post by mikewhatever on 2011-04-20
> **Lucradia said:**
> As a note: VideoDownloadHelper is junk now. You can't use the old transcode features anymore without paying a subscription, as well as other things. Better off with the MP4 download from userscripts.org

I know, the thread topic is vague, but let's try not to digress anyway.

---

### Post by Pogeymanz on 2011-04-20
Firefox is definitely slower to launch than Chrom{e,ium}, but Opera takes about the same time to launch as Firefox, for me.

Opera closes much faster though.

Something that helps Firefox's startup time is the defrag the SQL databases it uses. Try running this script:

```
#!/bin/bash

killall firefox
echo "Please wait while the databases are optimized..."
find $HOME/.mozilla/ \( -name "*.sqlite" \) \
    -exec sqlite3 {} vacuum \; \
    -exec sqlite3 {} reindex \;
echo "Firefox databases optimized with success!"

```

---

### Post by Dustin2128 on 2011-04-20
> **Shmantiv_Radio said:**
> With or without addons?
Dozens of addons.

---

### Post by Lucradia on 2011-04-20
> **Pogeymanz said:**
> Firefox is definitely slower to launch than Chrom{e,ium}, but Opera takes about the same time to launch as Firefox, for me.

Opera closes much faster though.

Something that helps Firefox's startup time is the defrag the SQL databases it uses. Try running this script:

```
#!/bin/bash

killall firefox
echo "Please wait while the databases are optimized..."
find $HOME/.mozilla/ \( -name "*.sqlite" \) \
    -exec sqlite3 {} vacuum \; \
    -exec sqlite3 {} reindex \;
echo "Firefox databases optimized with success!"

```

:|

```
firefox: no process found
Please wait while the databases are optimized...
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
find: `sqlite3': No such file or directory
Firefox databases optimized with success!
```

---

### Post by NightwishFan on 2011-04-20
Firefox takes between 5-15 seconds to start for me (and I do not use addons). Depends on the IO load at the time. My disk is only 5400rpm.

---

### Post by Pogeymanz on 2011-04-20
perhaps you don't have sqlite installed?

---

### Post by Lucradia on 2011-04-20
> **Pogeymanz said:**
> perhaps you don't have sqlite installed?

You're right I don't :V

```
Package: sqlite                          
State: not installed
Version: 2.8.17-6build2
Priority: optional
Section: misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 90.1k
Depends: libc6 (>= 2.4), libreadline6 (>= 6.0), libsqlite0 (>= 2.8.17)
Suggests: sqlite-doc
Description: command line interface for SQLite
 SQLite is a C library that implements an SQL database engine. Programs that
 link with the SQLite library can have SQL database access without running a
 separate RDBMS process.

```

---

### Post by Copper Bezel on 2011-04-21
...

Why would you make a script that returns a message, but can only ever return one message, which is the one you just pasted into the terminal? I don't think of it as reassuring....

---

### Post by jerenept on 2011-04-21
> **Pogeymanz said:**
> perhaps you don't have sqlite installed?

just do this:
[https://addons.mozilla.org/en-US/firefox/addon/vacuum-places-improved/]("https://addons.mozilla.org/en-US/firefox/addon/vacuum-places-improved/")

---

### Post by LowSky on 2011-04-21
video of it taking longer than 5 seconds or it doesnt happen.

unless your using a live cd, use 10+ add-ons, or your pc has less than a GB of RAM. it cant be that slow.

---

### Post by K_45 on 2011-04-21
I have 4 add-ons, IceWeasel 4 on a Debian netinstall running XFCE with less than 200mb RAM used on boot. Firefox takes around 4 or 5 seconds to load up, and then proceeds to swallow 100mb almost instantly . . . have 4GB DDR3, a bit less (3.6GB or so) due to the onboard GPU.

---

### Post by NightwishFan on 2011-04-21
> **K_45 said:**
> I have 4 add-ons, IceWeasel 4 on a Debian netinstall running XFCE with less than 200mb RAM used on boot. Firefox takes around 4 or 5 seconds to load up, and then proceeds to swallow 100mb almost instantly . . . have 4GB DDR3, a bit less (3.6GB or so) due to the onboard GPU.

Similar setup and results here. Though just about every single browser uses this much memory for me. (Chromium, Midori, Epiphany)

---

### Post by K_45 on 2011-04-21
> **NightwishFan said:**
> Similar setup and results here. Though just about every single browser uses this much memory for me. (Chromium, Midori, Epiphany)

I should also add that I have avoided anything GNOME, no Synaptic or gksu, or gdm. So only thing GNOME is policykit. Chromium on another laptop with the same OS but 6GB RAM and 2 addon's takes 1 -2 seconds to start.

---

### Post by Lucradia on 2011-04-21
> **jerenept said:**
> just do this:
[https://addons.mozilla.org/en-US/firefox/addon/vacuum-places-improved/]("https://addons.mozilla.org/en-US/firefox/addon/vacuum-places-improved/")

I don't like that one review:

> This extension blocks the extension manager... I have to close FF brutally, and rerun it in safe mode. (Firefox 4.0 under Linux)

Rated 1 out of 5 stars by Serge_del on April 17, 2011 

---

### Post by Shmantiv_Radio on 2011-04-21
> **LowSky said:**
> video of it taking longer than 5 seconds or it doesnt happen.

unless your using a live cd, use 10+ add-ons, or your pc has less than a GB of RAM. it cant be that slow.

Screen capture on a netbook?

Yeah, right.. ¬¬

---

### Post by Lucradia on 2011-04-21
> **Shmantiv_Radio said:**
> Screen capture on a netbook?

Yeah, right.. ¬¬

Speaking of, I saw this one video of someone recording full 1080p on an IBM T41 Laptop, it was surprisingly... smooth, even with compiz.

---

### Post by lovinglinux on 2011-04-21
Firefox startup is slowed down mostly by extensions. Also, if you start Firefox with the bookmarks sidebar open and your database is not optimized, then it can be affected too.

I have around 60 extensions installed and don't have a problem.

See my tutorials on Firefox optimization:

[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)

You can test Firefox startup time with [About Startup]("https://addons.mozilla.org/en-US/firefox/addon/about-startup/") extension.

---

### Post by jerenept on 2011-04-21
> **Lucradia said:**
> I don't like that one review:

That has never happened with me.

---

### Post by Lucradia on 2011-04-22
> **lovinglinux said:**
> Firefox startup is slowed down mostly by extensions. Also, if you start Firefox with the bookmarks sidebar open and your database is not optimized, then it can be affected too.

I have around 60 extensions installed and don't have a problem.

See my tutorials on Firefox optimization:

[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)

You can test Firefox startup time with [About Startup]("https://addons.mozilla.org/en-US/firefox/addon/about-startup/") extension.

Too bad peacekeeper has been down for a few hours for me, still won't load.

Too bad you can't do this: [http://www.webgapps.org/firefox/extension-optimization](http://www.webgapps.org/firefox/extension-optimization) on Windows.

**network.http.pipelining.firstrequest** isn't in Firefox 4 by default, make sure to change your tutorial over there.

---

### Post by lovinglinux on 2011-04-22
> **Lucradia said:**
> Too bad peacekeeper has been down for a few hours for me, still won't load.

Too bad you can't do this: [http://www.webgapps.org/firefox/extension-optimization](http://www.webgapps.org/firefox/extension-optimization) on Windows.

**network.http.pipelining.firstrequest** isn't in Firefox 4 by default, make sure to change your tutorial over there.

I am currently upgrading the site CMS and will rewrite many tutorials.

---

