---
title: "dynamic window lists (quicklists) in a ppa"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-03-18
Something that showed as a test py script in the mailing list a while back is now in a ppa.
It will create windowlists, (active) in launcher icon's quicklists

Wouldn't say it won't be without issues, but's it's dev & worth checking out if interested in such stuff
(sometimes I notice it doesn't always raise a window on another desktop, most times it does, maybe a pattern?

There is 1 current 'giveback' I see, the nautilus 'bookmarks' quicklist entries will be disabled, except for items that are there from explicit entries in nautilus-home.desktop (default or user added

(not a big issue here as I've returned the 'Bookmarks' to the panel menu on Desktop focus that was recently removed for being "redundant", which it really wasn't if a  min. of thought was given 

At least here the supplied /etc/xdg/autostart/unity-window-quicklists.desktop would not autostart & was also made not visible. 
The fix  is to edit the OnlyShowIn=UNITY; line to
OnlyShowIn=Unity;

(- & set NoDisplay=false so it shows in System Settings & can be enabled/disabled at will

Blog with ppa link
[http://www.theopensourcerer.com/2012/03/16/unity-window-quicklists/](http://www.theopensourcerer.com/2012/03/16/unity-window-quicklists/)


edit:
If it crashes with  an app (likely at some point), then it (wl), won't restart till a log out/in. 
I may see what effect (good, bad. very bad, or none), giving the .desktop an AutoRestart line has

---

