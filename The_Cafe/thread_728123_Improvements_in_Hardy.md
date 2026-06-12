---
title: "Improvements in Hardy"
date: 2008-03-18
forum: The Cafe
---

### Post by Achetar on 2008-03-18
Yesterday, I installed the latest daily build of Ubuntu Hardy (which is an alternate CD, so no LiveCD stuff). I noticed several things that people have been bugging the devs about have been added.

The thing I noticed most was that they have an option in the (very ugly) partitioner to create a separate partition for the home folder. This works perfectly! My home folder is /home/<usrname> yet it is on a different partition (ext3, but the rest of my HDD, aside from M$, is reiser3). This partition is invisible except for the in a partition manager. (was this in gutsy? I didn't run the gutsy installer, I upgraded)

Also, Ubuntu detected my Intersil Prism2.5 WiFi card as a Wifi card, not an ethernet card. And it allowed me to select WPA encryption for the card (I have the updated firmware), which gutsy wouldnt do without serious effort.

Another thing is a new desktop look. While the Human theme remains virtually the same, the desktop background is totally new.

One last thing, I want to thank all of the people who have helped make this project extraordinary!

(I will put more improvements on here as I find them...until the official release!)

---

### Post by NightwishFan on 2008-03-18
Human look has a few minor tweaks I have noticed. The menu has a border and the colours are more subdued.

The Kubuntu Installer has a new Install option to just run the installer, sort of like OpenSUSE.

Compiz-fusion is newer version with some added plugins.

The other stuff is newest Gnome, Pulse Audio etc. It is really good. Already better than Gutsy and not heavier.

---

### Post by Achetar on 2008-03-18
OK, I thought something looked different, but I rarely use the human theme, so I wasn't sure. And you are correct, I didn't list everything. The Ubuntu Hardy Daily Builds only come in AlternateCD form, that is why the installer is ugly. I will continue to play around with it.

I also noticed the new hardware testing app. Very nice! I was able to answer yes to every question! (with a couple comments but nothing major. 

Another thing, nm-applet (the best panel network applet ever written) is now installed by default, so no more installing from disk repos before I can surf! :)

If anyone else has things they notice have been improved in Hardy, please put them up! (screens are nice, too

EDIT: part of the screens I took are on the original post, the rest are on this message. Expect more!

---

### Post by ODF on 2008-03-18
Had some issues with one upgrade of gnome last week.

I really love how it detect your screen.

Still far from stable but very usable.

---

### Post by Bungo Pony on 2008-03-18
That's great news about the /home partition! Everything else looks like it's coming along nicely. Can't wait to try out the final release.

---

### Post by igknighted on 2008-03-18
Still no support for synaptics trackpads and still no support for adjusting screen res without building your own xorg.conf... these are complete showstopper bugs IMO and need to be dealt with if they truly intend to ship without writing an xorg.conf and having it automatically generated.

---

### Post by bobbocanfly on 2008-03-18
Seahorse/GPG is much more prominent (integration in the Nautilus menu's and of course Seahorse by default).

---

### Post by Freddy on 2008-03-18
What happend to that new 'bling, bling' theme that they had going? If one had changed the color on that theme it would actually look good, now it just looks like, ehh well, like before.

---

### Post by aaaantoine on 2008-03-18
**RE: 'bling, bling' theme**
That was a mock-up.  Also, I've seen it written that the artwork overhaul was pushed back to 8.10 because of stability concerns with 8.04.

**RE: synaptics touchpad support**
In 7.10, basic touchpad options are available under System -> Preferences -> Mouse under the Touchpad tab.

Advanced touchpad preferences are available with the gsynaptics package, though use of this application requires modification of xorg.conf.  Also, this is the only way to modify touchpad settings if you are using xserver-xgl.

---

### Post by madjr on 2008-03-18
> **Achetar said:**
> 

The thing I noticed most was that they have an option in the (very ugly) partitioner to create a separate partition for the home folder. This works perfectly! My home folder is /home/<usrname> yet it is on a different partition (ext3, but the rest of my HDD, aside from M$, is reiser3). This partition is invisible except for the in a partition manager. (was this in gutsy? I didn't run the gutsy installer, I upgraded)


i see a problem with "**/home**" being on a different partition

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63012&d=1205866094[/IMG]

the **/home** is just **5GB** and **"/"** (root) is a huge **42GB**....

everyone knows that **/home** is the one that usually **gets out of space**, since we store all **our junk** there.

root partition ("/") don't need that much space...
[B]
i see many people having a space problems issues on one partition or the other..[/B] :(

---

### Post by Lord Illidan on 2008-03-18
Unless he's using the windows partition to share data.. But even then, 42 gb to the / partition is overkill, unless you're planning to store some heavy duty programs in there.

---

### Post by ubuntu27 on 2008-03-18
I like what I am seeing here :D Nice screenshost!
Woo :( I am starting to miss Ubuntu.

---

### Post by igknighted on 2008-03-19
> **aaaantoine said:**
> **RE: 'bling, bling' theme**
That was a mock-up.  Also, I've seen it written that the artwork overhaul was pushed back to 8.10 because of stability concerns with 8.04.

**RE: synaptics touchpad support**
In 7.10, basic touchpad options are available under System -> Preferences -> Mouse under the Touchpad tab.

Advanced touchpad preferences are available with the gsynaptics package, though use of this application requires modification of xorg.conf.  Also, this is the only way to modify touchpad settings if you are using xserver-xgl.

Oh, the touchpads work great in 7.10... it's 8.04 that's the issue.  g/ksynaptics don't do anything if the trackpad isn't being recognized with the proper driver by xorg.  So forget configuring it, I simply want it to use the right driver.  Besides... has g/ksynaptics ever worked for anyone?  I've never had the settings I change there actually stick and so I just go back to the xorg.conf to change them myself.

---

### Post by Achetar on 2008-03-19
> **madjr said:**
> i see a problem with "**/home**" being on a different partition

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63012&d=1205866094[/IMG]

the **/home** is just **5GB** and **"/"** (root) is a huge **42GB**....

everyone knows that **/home** is the one that usually **gets out of space**, since we store all **our junk** there.

root partition ("/") don't need that much space...
[B]
i see many people having a space problems issues on one partition or the other..[/B] :(
Actually, I resized it to 15GB just after I took that shot. The only reason it was 5GB was because I made a typo when setting the partition size. Then I set the root partition to have the rest.

---

### Post by Achetar on 2008-03-19
Actually my synaptics touchpad works great! No problems on it! And yes, I intend to store some pretty big games in the root partition, with saves in /home

---

