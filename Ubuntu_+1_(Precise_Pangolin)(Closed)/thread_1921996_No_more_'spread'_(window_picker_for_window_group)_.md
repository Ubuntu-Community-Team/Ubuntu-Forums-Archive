---
title: "No more 'spread' (window picker for window group) from all workspaces"
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-02-07
I'm sorta gathering not many care one way or the the other that this has been changed
To point out exactly - thru the whole previous unity life a l. click or 2nd left click on a launcher icon would pull all windows from that window group to the spread (scale)

This has been changed to only pulling from the current workspace, now if you want to open a window whose group is on multiple workspaces   you need to actually go to that workspace to open that particular window.

Personally think this is one of the dumbest design decisions yet.

(particularly in light of the fact that user set bindings for 'scale > Initiate window picker for window group' on all Ws's has been & continues to be broken

For the curious the bug report that set this in motion over a yr. ago
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

Edit: there is a method to get this function back in post 5, currently works on compiz < 0.9.7, as to the future don't know
So this is semi-solved pending setting initiate_all in 0.9.7 or a possible reconsideration of design

---

### Post by fjgaude on 2012-02-07
Yep, sorry state of affairs! I'll get used to it, just as I've changed my workflow with Unity. It's like we may have to go with the flow.

---

### Post by mc4man on 2012-02-07
> **fjgaude said:**
> Yep, sorry state of affairs! I'll get used to it, just as I've changed my workflow with Unity. It's like we may have to go with the flow.
Unfortunately it seems the 'flow' is getting narrower & narrower

---

### Post by Peter09 on 2012-02-08
Agreed - this is really dumb, there has been pressure from some to do this, but giving into to it was the wrong choice in my opinion.

I always understood that the launcher icon was where you managed an application from - this idea appears to have been undermined with this decision.

---

### Post by mc4man on 2012-02-10
This is a semi-replacement that uses a command & binding. Currently works just fine here, I use a key binding. Window state seems be maintained ect.

Note that it requires the dbus plugin in compiz to be enabled, if enabling with ccsm it will go thru it's refresh routine & may return, may not. If not just use any key combo to log out/in, restart x, whatever.

With dbus enabled & ccsm functional enter this command in the Commands plugin, then click on the binding tab of choice & set one (only tested Key

If using a key binding refrain from using Ctrl, [it's a bit borked atm or forever.]("https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/929926") I'm using Shift+Alt+p

One long command - thanks to [Prabhjot for basic com.]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/774059"), I modified it ever so slightly
```
dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/scale/screen0/initiate_all_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:"match" string:$(xprop -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | awk '{print $5}'` | grep "WM_CLASS" | cut -d\" -f4 | awk '{print "class=" $1 }')
```

A log out/in may be required
Obviously you need to initiate it  while focus is on a window of the group desired to pull.

Atm [doesn't work in the upcoming compiz-0.9.7]("https://bugs.launchpad.net/bugs/930514"), hopefully it will

---

### Post by keithpeter on 2012-02-11
> **mc4man said:**
> Unfortunately it seems the 'flow' is getting narrower & narrower

Hello All

Well spotted mc4man, I'm going to have to use Unity next week instead of living in Gnome Shell (I spend a few weeks in each alternately).

Could these changes be an artifact of 'first hour testing'?

> "The first hour is make-or-break, and we research that rigorously, every few months. We call it baseline testing, because we always do the same routine: sit a new, un-prejudiced user down in front of the current snapshot of Ubuntu or its competitors, tell them they have just been given a new PC, camera, USB stick etc, and invite them to get a list of things done." --Shuttleworth, quoted by omgubuntu writer

[http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/](http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/)

---

### Post by BigSilly on 2012-02-11
Sad to see all these options being removed from Ubuntu. The dodge windows thing was a deal breaker for me, and I don't think I'll be installing 12.04, though I will try it on a Live USB. I understand what Canonical is aiming for, and I wish them all the very best in it, but I'm really going to have to just accept that it's not for me personally.

:(

---

### Post by EgoGratis on 2012-02-11
I really don't agree. It's like somebody is trying to "reward us" for "sticking by" when other only spitted in every direction. Thanks!

What is it about this time? "Dumb user" would get confused if the workspace would switch? Now all of us have to play it dumb? Thanks!

---

### Post by keithpeter on 2012-02-11
Hello EgoGratis, BigSilly and all

@Bigsilly: xubuntu 12.04 on my netbook I think. Should see the hardware out. Alt-F11 for app windows and a single panel at bottom gives me all the GUI I need for that simple device.

@EgoGratis: Canonical needs a market (you know, money, income), and it looks like its commodity devices. 

Tablets, TVs and mobile. You play with one in the shop then buy it. I bought a blackberry because I liked the keyboard and 'grokked' the scroll button interface quick. I like to think I'm not dumb, but my use cases are simple for phones and the like.

I could be cheeky and point out it took quite a time for the people here to notice this change in alt-tab behaviour... perhaps our workflows are not as profound and finely tuned as we think they are :twisted:

---

### Post by EgoGratis on 2012-02-11
> Canonical needs a market (you know, money, income), and it looks like its commodity devices. 

Yes and i support this but why are flagship features of Unity Shell being treated like bugs lately? 

> perhaps our workflows are  not as profound and finely tuned as we think they are :twisted:

I think i will notice if i will not be able to use Dodge Like functionality and will have to switch between workspaces to find the application i have opened.

---

### Post by keithpeter on 2012-02-11
> **EgoGratis said:**
> Yes and i support this but why are flagship features of Unity Shell being treated like bugs lately?

Canonical are *really* going for the user testing on Unity, that takes guts I think and I admire them for that. It will be interesting to see where that iteration against testing leads, safe in the knowledge we have choices. Ubuntu != Unity. This particular feature *was* seen by some as [a bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733"), so I guess someone decided to fix it.

Back on topic for the U+1 forum, will the [interface freeze on 23rd Feb]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule") mean that whatever is in Unity then is provided for the *whole* cycle, all 5 years? Just bug fixes and code changes but no change in the interface behaviour?

I'd like to update my guides and contribute to the Ubuntu Manual team's efforts, but not against a moving target :twisted:

---

### Post by geojorg on 2012-02-11
For me the idea is incomplete, they pretend to have a new way of working in one workspace but the show desktop works for all workspaces, this is not consistent. I don't like all my apps to hide, who would ?

I just wrote this on the current bug.

> I would like someone to open this bug once again, or to revert to the last behavior of alt tab in all workspaces, i don't know if someone did not consider that when pressing alt + tab and selecting show desktop it would trigger the show desktop in all workspaces turning all the applications in other workspaces invisible, so i have to conclude that this current feature is incomplete.

I guess that the normal behavior should be to only show desktop in the current workspace. Nevertheless I did like the old way of showing all applications on all of the workspaces, it was more consistent.

Hope someone clear me the show desktop idea or should i open a new bug ?

---

### Post by prusswan on 2012-02-11
> **keithpeter said:**
> Canonical are *really* going for the user testing on Unity, that takes guts I think and I admire them for that. It will be interesting to see where that iteration against testing leads, safe in the knowledge we have choices. Ubuntu != Unity. This particular feature *was* seen by some as [a bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733"), so I guess someone decided to fix it.

Back on topic for the U+1 forum, will the [interface freeze on 23rd Feb]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule") mean that whatever is in Unity then is provided for the *whole* cycle, all 5 years? Just bug fixes and code changes but no change in the interface behaviour?

I'd like to update my guides and contribute to the Ubuntu Manual team's efforts, but not against a moving target :twisted:

Freezing Unity features for next 5 years is pointless, this is not even sufficient time for the target audience, touch screen users to gain critical mass and chime in (is there even such a user on these forums yet?)

---

### Post by keithpeter on 2012-02-11
> **prusswan said:**
> Freezing Unity features for next 5 years is pointless, this is not even sufficient time for the target audience, touch screen users to gain critical mass and chime in (is there even such a user on these forums yet?)

Absolutely agree, but that is not what I asked.

What I asked was: will the Interface Freeze date in Ubuntu 12.04 mean that the version of Unity in 12.04 will retain the same behaviour for the support period of 12.04? 

I'd hope and expect that Unity itself is developed in the *later cycles of Ubuntu*.

---

### Post by mc4man on 2012-02-11
This has absolutely nothing to do with 'new users', 'new user testing testing' ect.

It is simply a design change suggested & approved by very experienced users & has been _intended to happen from almost the the very beginning of Unity._ The bug report is posted in the orig. post, circa Dec. 12 2010

---

