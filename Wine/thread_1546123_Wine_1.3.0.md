---
title: "Wine 1.3.0"
date: 2010-08-04
forum: Wine
---

### Post by theShaggy on 2010-08-04
Hey folks,

Anybody know when Wine 1.3.0 is due to hit the repos?  Sounds like a pretty major upgrade, and I know the package was renamed to wine1.2 recently, so maybe I just don't see a new version... is it already up for grabs?

---

### Post by dardack on 2010-08-04
> **theShaggy said:**
> Hey folks,

Anybody know when Wine 1.3.0 is due to hit the repos?  Sounds like a pretty major upgrade, and I know the package was renamed to wine1.2 recently, so maybe I just don't see a new version... is it already up for grabs?

You can always get wine from winehq.org.  I'd stick with 1.2 for now unless you want the development version 1.3.

---

### Post by cogadh on 2010-08-04
If you are referring to the default Ubuntu repository, the 1.3.X series will never be a part of it, since it is the unstable version of Wine. The next version of Wine that will hit the regular Ubuntu repository will be the next stable build after 1.2.X, which will be the 1.4.X series. If you are referring to the Ubuntu Wine PPA repository, it usually takes a few days for a new unstable build to hit it, just be patient, it will update eventually.

---

### Post by cutterjohn on 2010-08-04
> **dardack said:**
> You can always get wine from winehq.org.  I'd stick with 1.2 for now unless you want the development version 1.3.Yes! We want the dev version, otherwise we wouldn't be using the PPA and would stick with what was shipped with 10.4!

Yes we can get the source from winehq, but that's not much help. The PPA was SUPPOSED to house the dev builds...  I'mnot intending to denigrate anyone, but that's the shape of things.  People who want stable stick with what they get from the DEFAULT repos.

[EDIT]
Maybe we need the STABLE(ish) wine PPA and the down and dirty PPA that actually builds dev builds again, as AFAICS it's a bit of chore to setup a wine build for .debs and the PPAs already have that, but seemed to have abandoned it...  1.2 works with ALOT more Windows apps for me, but it has also severely crippled perf on a number of them so I'd like dev builds again or a nice packaged script to run against the sources...

BTW: thanks for building them in a PPA for the last release or so... although at this point I'm willing to go back to direct builds from winehq barring a helpful package build script...
[/EDIT]

---

### Post by theShaggy on 2010-08-05
Cutterjohn speaks my mind, too.  I've been using the dev builds from the Wine PPA since before 1.0, and it has always updated.  I'm only asking in case something changed in the regular repos.

Anyway, thanks for the input.  I'll stay patient and hope that they get the repo up to date (I've heard that 1.3 runs L4D2 significantly better).

---

### Post by beastrace91 on 2010-08-05
> **theShaggy said:**
> (I've heard that 1.3 runs L4D2 significantly better).

Have you tried this yet? That alone makes me want to start compiling from source...

~Jeff

---

### Post by ronnielsen1 on 2010-08-05
> Have you tried this yet? That alone makes me want to start compiling from source...Worked good for me. I did compile

> I compiled this under Ubuntu 10.04 with checkinstall. If there are any problems, let me know as this is my first attempt

[https://files.one.ubuntu.com/NieCL6U2SCSDg0vVHKzVgw](https://files.one.ubuntu.com/NieCL6U2SCSDg0vVHKzVgw)[http://ubuntuforums.org/showthread.php?p=9680343#post9680343](http://ubuntuforums.org/showthread.php?p=9680343#post9680343)

I guess the link doesn't work. Sorry.

---

### Post by cogadh on 2010-08-05
Why do some of you seem to think the Wine PPA has been abandoned? So it has been a few days since 1.3.0 was released, big deal. This is not the first time there has been a minor delay between a release and a package build, I'm am absolutely certain it won't be the last time.

Nothing has changed in regards to the repos; the default Ubuntu repo will always have the current stable release of Wine only (version 1.2 at the moment), the Wine PPA will always have the current development/unstable version (the 1.3.X series at the moment). You just need to be patient and give Scott Ritchie and Co. time to build the new package. Chances are, building the stable 1.2 packages for each currently supported version of Ubuntu has priority over getting the latest unstable package out.

---

### Post by namebrandon on 2010-08-05
I see in the post ron linked to that the .deb is now available for 1.3 ? I tried this ~15 hours ago, have they been posted since then? Just want to make sure I'm not being slipped crazy pills.

---

### Post by cogadh on 2010-08-05
I'm not sure what ron is talking about. I'm looking at the Wine PPA right now and there is no 1.3 package available.

EDIT - I think he might have confused a couple of updates for Wine's support packages as the 1.3 update. Both the wisotool and winetricks packages were updated in the last day or so, but Wine itself was not.

---

### Post by dino99 on 2010-08-05
do you mind you guys that Scott maybe spend free time like you do too

---

### Post by 0004tom on 2010-08-05
It's on the wine PPA now, just do an apt-get update and install wine1.3

apt-get will tell you it's going to remove wine1.2 and install wine1.3 if you do it this way.

```
sudo apt-get install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mplayer-skins
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  wine1.2
The following NEW packages will be installed
  wine1.3
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
```


```
 wine --version
wine-1.3.0
```

---

### Post by cogadh on 2010-08-05
Odd that it doesn't consider 1.3 an upgrade from 1.2, but rather a whole new package. I can't remember, is that what happened with 1.0 - 1.1?

---

### Post by theShaggy on 2010-08-05
Awesome, 4Tom.  Looks like the repo needed to be upgraded on my system.  Installing now.

---

### Post by namebrandon on 2010-08-05
Does this remove all the crap .dll's and random chaff I installed on my 1.2 install trying to get DirectX9 to work? Or should I completely uninstall / blow away 1.2 and the .wine directory, and then install 1.3?

---

### Post by cogadh on 2010-08-05
No, it will not blow away your existing .wine directory and any changes you have made to it, it only installs/replaces the Wine core files. If you want to start all over again clean, then just re-name or delete your .wine directory before or after you install 1.3.

---

### Post by ronnielsen1 on 2010-08-05
> 
EDIT - I think he might have confused a couple of updates for Wine's  support packages as the 1.3 update. Both the wisotool and winetricks  packages were updated in the last day or so, but Wine itself was not.

No what I was TRYING to do was to offer the deb to people. I compiled it from the source and installed it with checkinstall. That gave me a nice little deb file which I uploaded to my ubuntu account and tried to post a link to it. When I checked it from another computer and it asked me for my account name and password I knew I made a mistake. Sorry tried offering the deb file before they did. It didn't work

---

### Post by soldier1st on 2010-08-06
Wine 1.3 is a development build so why do you want that so stick to the stable releases(i myself stick to the version from the repositories).

---

### Post by What Rights on 2010-08-06
The development never worked for me, But I have no need for wine anyhow.

---

### Post by ronnielsen1 on 2010-08-06
[http://ubuntuone.com/p/BpY/](http://ubuntuone.com/p/BpY/)

should actually give you the deb now.

> Wine 1.3 is a development build so why do you want that so stick to the  stable releases(i myself stick to the version from the repositories). 	
Because it works like 1.2 except it has a lot of bug fixes.

[http://www.wine-reviews.net/wine-reviews/wine-release/wine-130-released.html](http://www.wine-reviews.net/wine-reviews/wine-release/wine-130-released.html)

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-Wineconfiguration-1.png[/IMG]

---

### Post by cogadh on 2010-08-06
> **soldier1st said:**
> Wine 1.3 is a development build so why do you want that so stick to the stable releases(i myself stick to the version from the repositories).
For most of us, the development builds are the only ones we use because of the increased functionality and software support they have and the frequency with which bugs are fixed (unstable gets updated roughly every two weeks). In fact, until the release of the 1.0 stable build a few years ago, the unstable build was the only option for everyone using Wine; we just kept on using it even though a stable option was available. 

If you are using "mission critical" software in Wine, then sure, sticking with the stable build is the *second* smartest thing you can do (the smartest would be switching to an equivalent Linux native application); using the stable build means you get consistently predictable results from using Wine. However, if you want the best possible performance from your app in Wine and you don't mind dealing with potential bugs and regressions, unstable is definitely the way to go. Frankly, its been quite a while since an unstable build introduced a regression or bug that was anything more than annoying and even then, it never lasted more than one build. For what I use Wine for (primarily games), the unstable builds have been virtually stable.


> **ronnielsen1 said:**
> [http://ubuntuone.com/p/BpY/](http://ubuntuone.com/p/BpY/)

should actually give you the deb now.

However, in the interests of keeping things consistent, we really should be pointing people at the official release of 1.3.0, which is now available [via the Ubuntu Wine PPA]("http://www.winehq.org/download/deb"). Unless someone has a specific need to compile Wine themselves, they should only use the official packages.

---

### Post by ronnielsen1 on 2010-08-06
> However, in the interests of keeping things consistent, we really should be pointing people at the official release of 1.3.0, 

:D Understandable. When I started it was a couple of days before they came out with their deb. I figured it would be cool to be the first to offer the deb. Didn't work (The deb did - sharing it didn't) :( Oh well, tried to contribute

---

### Post by Ravensound on 2010-08-20
1.3 is this available for early versions? (eg 8.10)

I recently had to modify 1.0 to get the beta Streamerp2p2.0 working:

Extract Streamerp2p2.0 files from website ([www.streamerp2p.com](www.streamerp2p.com))
Install and run Winetricks, select dcom98 then delete oleaut32 and rpcrt4 (leaving just ole32) from the libraries.  Run from execution file (no installation).

The current version of streamerp2p works in wine 1.0 after installation as per windows, without any modification.

---

### Post by handy on 2010-08-20
wine-1.3.1-1 just came in inside of the last 12 hours on the Arch side, where it is considered stable.

---

### Post by dino99 on 2010-08-21
im waiting for it as it resolve lot of bugs and bring some new stuff.
By the way 1.3.0 is very stable on my system where it run all the day long without trouble.

---

