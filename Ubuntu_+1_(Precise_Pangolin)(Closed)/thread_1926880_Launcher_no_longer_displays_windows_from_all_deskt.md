---
title: "Launcher no longer displays windows from all desktops on double click"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by _oOMOo_ on 2012-02-17
It's quite possible I'm being breathtakingly stupid, but I'm pretty sure in previous Ubuntu Unity incarnations, when I had say a terminal open on each of 3 different desktops, when I moved over to the launcher and double clicked, it activated the Compiz Scale plugin or similar and displayed all three on the current desktop so I could quickly move to the desired instance.

It no longer seems to work this way - am I missing an obvious setting in CCSM?

Thanks for any enlightenment!

---

### Post by mc4man on 2012-02-17
see here
[http://ubuntuforums.org/showthread.php?t=1921996](http://ubuntuforums.org/showthread.php?t=1921996)

Atm the only 'official' way to pull up all windows of a group is thru unity's alt-tab switcher making sure to disable the 'bias alt-tab to prefer windows on current viewport'

(I had a workaround to bind a command thru dbus to do this but now initiate_all is broken in scale so it won't work now

---

### Post by _oOMOo_ on 2012-02-17
Thanks mc4man, should have searched a bit harder. I would consider this quite a serious regression as Alt Tab is too slow. Why on earth would this be removed? It doesn't affect anyone who doesn't want it.

Do you know of a bug report - if not I'll submit one now?

Thanks again,

Jon

---

### Post by mc4man on 2012-02-17
> Do you know of a bug report - if not I'll submit one now?
Don't waste your time on a new one. 

In the 1st post in link I posted the orig. report that set this in motion 14 months ago, nothing more to be said there either though feel free if you wish

---

### Post by EgoGratis on 2012-02-17
Yes i hope this gets improved too and to work again like it did in the past or at least to be optionally and still officially supported! It's confusing for the user because he/she must know where exactly (number of the workspace or screen) the window of desired application is opened. 

Old behavior just summons it in front of the user when clicking on the button in Launcher and redirects the user where he/she needs to be to see it and the user does not have to think about anything but this new approach is something suitable for i guess just one screen and one workplace? I personally would put the old behavior in every brochure of the product just beside best features available that the product provides!

---

### Post by EgoGratis on 2012-02-17
One more problem found:

User selects Quit in Quicklist and it closes all running instances of  application across all workspaces and there is no indication some open  instances from this group of application exist because user can't summon  them all on working space. The only way to find out is to switch among  all available workplaces to find out if there are any opened windows  belonging to this group of applications!

---

### Post by mc4man on 2012-02-17
> **EgoGratis said:**
> One more problem found:

User selects Quit in Quicklist and it closes all running instances of  application across all workspaces and there is no indication some open  instances from this group of application exist because user can't summon  them all on working space. The only way to find out is to switch among  all available workplaces to find out if there are any opened windows  belonging to this group of applications!
You  see a > on left side of the icon when there are open (visible or min) windows on other WS's. 

Atm scale will not work in any way I can find on all viewports, either all windows or window group. It will only do all_* on current viewport, whether intentional or broken don't know & that's one of those questions where getting a straight answer is quite a chore
(over the last 14 months had several bugs on scale > group, whether from launcher or in scale itself

Currently ring switcher can use all window & all windows of a group on all viewports, not quite the same...

---

### Post by EgoGratis on 2012-02-17
> You  see a > on left side of the icon when there are open (visible or min) windows on other WS's. 

True but only if you don't have application(s) from the same group opened on current workspace.

---

### Post by mc4man on 2012-02-17
Sorry, was slightly mis-understanding you.

Well they've decided that the current Ws is more important than anything else & I'm sure you read MS's techno explanation of Ws's, tasks, ect. which is all well & good, even maybe true,  but still flawed logic in this regard

Anyway the train's left the station on this so the only thing atm is to look for alt. means, if any.

I will find it a shame if scale is being purposely confined to the current output only  though wouldn't be surprised if it was.

---

### Post by EgoGratis on 2012-02-18
> Well they've decided that the current Ws is more important than anything else

But if user use only one workspace old behavior works exactly the same as new one?

> Anyway the train's left the station on this so the only thing atm is to look for alt. means, if any.

I did my part by providing feedback as (long time) Unity user and that is basically all i can do yes and other that would still like to use this feature and Dodge alike mode expressed their opinion too. Maybe if "unofficial" solution will exist for Ubuntu 12.04 in some PPA or staying a bit longer on Ubuntu 11.10 or something else will be possible i don't know. This two features was just flagship features of Unity Shell from my point of view and knowing that when maximizing window launcher will not hide anymore (always hide is really not an option) and when using more then one workspace i will have to do a lot of hide/seek operations this i have to comprehend and accept somehow or as i said maybe (i hope) third option will emerge!

---

