---
title: "Note U+1 Development Version testers and all;"
date: 2016-08-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-26
Hi,

Rather than send a network e-mail I am just making a post here to bring to the attention of testers in the forum that the release day for 16.10 is getting nearer and that testing is needed, ISO dailys especially.

 I know that many of you are dedicated to Ubuntu testing and that you have lots of other work to do but any time you make available for testing is greatly appreciated. It is the diligence in your testing  that makes Ubuntu great!

Thank you for all your excellent current and past work!

Regards..
Ventrical

---

### Post by ventrical on 2016-08-26
currents/

lubuntu (Beta1) [http://cdimage.ubuntu.com/lubuntu/releases/16.10/beta-1/](http://cdimage.ubuntu.com/lubuntu/releases/16.10/beta-1/)

ubuntu-desktop  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

gnome-desktop (Beta1) [http://cdimage.ubuntu.com/ubuntu-gnome/releases/yakkety/beta-1/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/yakkety/beta-1/)

kylin [http://cdimage.ubuntu.com/ubuntukylin/daily-live/current/](http://cdimage.ubuntu.com/ubuntukylin/daily-live/current/)

ubuntu-mate (Beta1)  [http://cdimage.ubuntu.com/ubuntu-mate/releases/yakkety/beta-1/](http://cdimage.ubuntu.com/ubuntu-mate/releases/yakkety/beta-1/)

Cannot find kubuntu (Beta1) only old daily image [http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

Regards..

---

### Post by mc4man on 2016-08-26
I'd suspect that 16.10 will get a little flurry of bug fixes starting in a couple of weeks & then 'release' as is.
Taking a quick (2 min.) look at today's image issues are quite obvious, don't think they need bugs as obvious or won't be fixed anyway.

live session - 
theming is screwed up
Install window remains too small, that leads to -
Partition window never shows all internal partitions if multibooting or whatever. This leads to scrolling down at times, unfortunately any action always moves back to top. This can create inadvertent mistakes. Longstanding, will not be fixed.
Partition size entry box only shows 5 numbers so any volume/free space over 100GB is not fully displayed
If wifi is connected the install does not retain the password setting

Install session - 
theming is screwed - 
unity panel is transparent (the set default is fully opaque  
when any window is open a white line is drawn down right side of screen
context menus are 'lined' in the background
Panel shows artifacts on left side on mouseover

password for wifi - 1st attempt never sets, have to do twice
nautilus's default icon size causes some file names to wrap incorrectly, e.g. 
.
ICEauthoriy
y

These are just first impressions, not any actual use.

---

### Post by #&amp;thj^% on 2016-08-26
> **mc4man said:**
> I'd suspect that 16.10 will get a little flurry of bug fixes starting in a couple of weeks & then 'release' as is.
Taking a quick (2 min.) look at today's image issues are quite obvious, don't think they need bugs as obvious or won't be fixed anyway.

live session - 
theming is screwed up
Install window remains too small, that leads to -
Partition window never shows all internal partitions if multibooting or whatever. This leads to scrolling down at times, unfortunately any action always moves back to top. This can create inadvertent mistakes. Longstanding, will not be fixed.
Partition size entry box only shows 5 numbers so any volume/free space over 100GB is not fully displayed
If wifi is connected the install does not retain the password setting

Install session - 
theming is screwed - 
unity panel is transparent (the set default is fully opaque  
when any window is open a white line is drawn down right side of screen
context menus are 'lined' in the background
Panel shows artifacts on left side on mouseover

password for wifi - 1st attempt never sets, have to do twice
nautilus's default icon size causes some file names to wrap incorrectly, e.g. 
.
ICEauthoriy
y

These are just first impressions, not any actual use.
+1 Just about the way I find it also...and pulseaudio still very buggy on my end.
Thanks mc4man.

---

### Post by ventrical on 2016-08-26
I have multiple installs of yakkety with unity8.  Also with xenial. Xenial  seems more stable. Yakktety tears out all the scopes at any time unexpectedly. (to be expected in devel). When unity8 and libertine work .. they work well. When they break .. they break well also.

Some installs Ctrl+Alt+T will not bring up terminal. New policiy-kit upgrade but don't see any difference. Now there is this transparent top menu line in unity7 that looks just awfull .. yes .. theming indeed.

Constant apport flags about puritine containers when not even running unity8. No sense in filing redundant bugs. Kubuntu looks really sassy. Installed great here but with no network on wired it is useless for live testing.

  I do know that most of the resource braintrust is being applied to snappy but with now being unable to log in to get apps it too is useless unless you have exclusive permissions of some sort.  I stand to be corrected - so go ahead .. somebody correct me :)

Regards..

---

### Post by mc4man on 2016-08-26
Seems the transparent panel has a bug ( and fix),  always a mystery to me how such things 'escaped the lab' to begin with.
The ironic thing is having a truly trans panel hasn't been possible in unity for many cycles (inc. without the drop shadow), now it's there but unintended & soon to disappear
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1617371](https://bugs.launchpad.net/ubuntu/+source/ubuntu-themes/+bug/1617371)

---

### Post by ventrical on 2016-08-26
+1ed it.

---

### Post by VMC on 2016-08-27
> **ventrical said:**
> currents/

lubuntu (Beta1) [http://cdimage.ubuntu.com/lubuntu/releases/16.10/beta-1/](http://cdimage.ubuntu.com/lubuntu/releases/16.10/beta-1/)

ubuntu-desktop  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

gnome-desktop (Beta1) [http://cdimage.ubuntu.com/ubuntu-gnome/releases/yakkety/beta-1/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/yakkety/beta-1/)

kylin [http://cdimage.ubuntu.com/ubuntukylin/daily-live/current/](http://cdimage.ubuntu.com/ubuntukylin/daily-live/current/)

ubuntu-mate (Beta1)  [http://cdimage.ubuntu.com/ubuntu-mate/releases/yakkety/beta-1/](http://cdimage.ubuntu.com/ubuntu-mate/releases/yakkety/beta-1/)

Cannot find kubuntu (Beta1) only old daily image [http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

Regards..
xubuntu [http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

---

### Post by ventrical on 2016-08-27
> **VMC said:**
> xubuntu [http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

wow .. thanks .. How could I forget xubuntu.


Regards..

---

