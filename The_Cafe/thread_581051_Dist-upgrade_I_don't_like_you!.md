---
title: "Dist-upgrade I don't like you!"
date: 2007-10-19
forum: The Cafe
---

### Post by Gargamella on 2007-10-19
This is the first time I don't make the clean installation of the newer release.
I was using xubuntu 7.04 with many pieces of software not default by xfce.

well, upgrading it uninstalled wicd,beryl, leaving me without an network configuration and a window manager.
Than the restricted driver manager told me that my wireless card was disabled (before the upgrade, it was installed), so I went to my father's office to install it again by ethernet.

There were no big problems for me ( it took a while but then all was ok), but I am worry for beginner users who make a dist-upgrade.

I mean that the dist-upgrade should just update all the software as possible WITHOUT unistalling the soft that it can't renew.

I might be wrong, and I know that probably xubuntu it is much different from ubuntu...but I would like a painless upgrade, maybe customizible in software installation/uninstallation.

What do you think about it ?

---

### Post by orange2k on 2007-10-19
Well, I only have a problem with Evolution: it won`t read my mail anymore - the send/recieve button is greyed out...

But everything else works fine - still I plan to do a clean install with the 64-bit version after I finish one BIG torrent download...

---

### Post by AndyCooll on 2007-10-19
I always prefer a clean install. I've never been satisfied with upgrading, I always seem to get errors etc. Might be just me and the fact that when I've upgraded it's been on older more temperamental hardware. Nonetheless, these days I always do a clean install.

:cool:

---

### Post by Wolki on 2007-10-19
You did a dist-upgrade? That method of upgrading is deprecated, you're supposed to use update-manager which does additional checks to ensure a safe upgrade. The release notes always contain information on upgrading.

> **Gargamella said:**
> There were no big problems for me ( it took a while but then all was ok), but I am worry for beginner users who make a dist-upgrade.

I mean that the dist-upgrade should just update all the software as possible WITHOUT unistalling the soft that it can't renew.

That would too often lead to half-installed and untested systems. Upgrades will work with customized setups (I'm doing it since breezy), but you can't expect testing on all setups that a user might have. Every software outside the repositories is a new potential point of failure. 

> **orange2k said:**
> Well, I only have a problem with Evolution: it won`t read my mail anymore - the send/recieve button is greyed out...

You probably have Evolution set to "Offline". The button is in the lower left corner of the window.


[edit] I'm not very exact in the above. dist-upgrades are fine for upgrading within a release (i.e. to install the latest updates for feisty if you're running feisty and so on). They are not recommended for upgrading between versions of distributions ( feisty -> gutsy etc.)

---

### Post by orange2k on 2007-10-19
> **Wolki said:**
> 
You probably have Evolution set to "Offline". The button is in the lower left corner of the window.

I`ll try that. Thanks...:)

---

### Post by CaptainTux on 2007-10-19
> **AndyCooll said:**
> I always prefer a clean install. I've never been satisfied with upgrading, I always seem to get errors etc. Might be just me and the fact that when I've upgraded it's been on older more temperamental hardware. Nonetheless, these days I always do a clean install.

:cool:

As do I.  Look at it this way.  Once every 6-12 months ya gotta go through your files and clean them up.  :)

---

### Post by bobbocanfly on 2007-10-19
I always do a semi-clean install, the new ISO, installed but keeping my home partition and pasting in some of my /etc directory. Never had a problem for the last 2 updates.

---

### Post by digitalbenji on 2007-10-19
likewise, I prefer a clean install as well.  A fresh start, ya know?

I was also concerned about using the upgrader, since I've been running compiz-fusion, and I wanted to be sure I got gutsy packages.

I also backed up some config files from /etc/.

---

### Post by sefs on 2007-10-19
This clean install every release is ms windows-esque.

---

### Post by CaptainTux on 2007-10-19
> **sefs said:**
> This clean install every release is ms windows-esque.

I would not say that.  I have just found that, for the most part, a clean install is usually less problematic.  

This has been true for me in Mac and a few Linux distros.  

I also know people that upgrade all the time without issue.  It's all good.  :)

---

### Post by PartisanEntity on 2007-10-19
I tried upgrading, left the laptop running all night, the upgrade tool got to the point where it is supposed to 'read cache' and just stayed there. So now my sources.list has been changed to gutsy, but when I try to go ahead with the upgrade it just sits there with the message: reading cache.

Upgrading from edgy to feisty was a breeze in comparison to this :)

---

### Post by Miguel on 2007-10-19
I usually dist-upgrade my machines. With aptitude, of course, due to it's better dependency resolving capabilities. I guess that in the last 6 months the only time I've used apt-get instead of aptitude was when installing anjuta. And this was only because aptitude's will to install also "recommended" packages wanted to download an amazing number of useless (to me) packages.

My personal experience with dist-upgradies is a positive one. My first dist-upgrade  was Hoary to Breezy beta. It went OK, as did Breezy to Dapper (flight 5, if my memory serves me) and dapper to edgy (some time before the beta). Actually, the only dist-upgrade in which I had trouble was on a Debian sarge to etch on my university PC, when etch wasn't even in feature freeze. This had me playing with touch and initramfs because of the newer 2.6 kernel and the new image method. However, bug 129910 makes it difficult to recommend dist-upgrading to gutsy. I know, I dist-upgraded to gutsy somewhere around June.

---

### Post by orange2k on 2007-10-19
> **PartisanEntity said:**
> I tried upgrading, left the laptop running all night, the upgrade tool got to the point where it is supposed to 'read cache' and just stayed there. So now my sources.list has been changed to gutsy, but when I try to go ahead with the upgrade it just sits there with the message: reading cache.

Upgrading from edgy to feisty was a breeze in comparison to this :)

Thats probably because the servers are overheating right now...:(
Wait a couple of days and it should be fine...
I tried to download Gutsy via mirrors last night, but I failed - so I used torrents...

edit: I just noticed that the forum has reached another record: most active users ever...

---

### Post by Gargamella on 2007-10-20
> **Wolki said:**
> You did a dist-upgrade? That method of upgrading is deprecated, you're supposed to use update-manager which does additional checks to ensure a safe upgrade. The release notes always contain information on upgrading.


I made the upgrade by the update-manager, sorry for the misunderstanding due to my post

---

### Post by angkor on 2007-10-20
I had zero problems with the upgrade this time around. I usually try an upgrade first, if it's too problematic I can always reinstall.

Third party drivers will always need reinstalling when you're going to use a new kernel, nothing new, and beryl is pretty much deprecated.

---

