---
title: "Alt+Tab switcher not showing all open windows"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-17
Since an update yesterday or the day before alt+tab switcher isn't showing all open windows. I also noticed that in Unity's Launcher bar open windows have different markings now. There are some with a triangular arrow next to them, and some have an empty arrow (>). Those with the triangular arrow show in the Alt+tab switcher, and those with the empty arrow don't. Any solutions?

---

### Post by mc4man on 2012-02-17
open the unity plugin settings > switcher & disable the bias option which now defaults to current viewport only (as does much in unity

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-18
Nice, that did the trick. Thanks. However, I don't want to have windows from all viewports in the switcher. I just want it to work as expected with windows in current viewport. And also, what is the reason for different arrow indicators in launcher if all of my windows are on the same (first) viewport?

---

### Post by mc4man on 2012-02-18
> and some have an empty arrow (>). Those with the triangular arrow show in the Alt+tab switcher, and those with the empty arrow don't.

> means that app has windows open, (visible or min) on another viewport, if you're saying that you get > with no apps on any other vp then that's not proper.

If so, then create a new user & ck. there

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-18
mc4man yes, that's what's happening. Although all open windows are on the same viewport, some of them sometimes have a triangle for a mark, and some have an empty arrow. Those two can change eventually. That started just a few days ago with one of the updates.

I just checked on the Guest account and the same problem exists. I'll create a new user account a bit later and try there.

---

### Post by mc4man on 2012-02-18
> **&#1058 said:**
> mc4man yes, that's what's happening. Although all open windows are on the same viewport, some of them sometimes have a triangle for a mark, and some have an empty arrow. Those two can change eventually. That started just a few days ago with one of the updates..
I think that over the past week a lot of inconsistent & possible  poor behavior has been introduced, I don't see what you're seeing but that doesn't mean anything really. Myself will likely wait a week or so then dump this install & start fresh

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-18
That's exactly what I'm about to do, although I ain't waiting that long.

---

### Post by screaminj3sus on 2012-03-03
dont bother reinstalling, I'm seeing this on a clean install of the beta. Is there a bug report on this?

---

### Post by kelpdip on 2012-03-03
I get the same behaviour. It seems like the open arrow > is given to programs launched without the unity toolbar -- from terminal, or system toolbar, or nautilus for instance. Focus has no effect on the indicator. Solid arrow is assigned to programs launched from unity toolbar. Only solid arrows sow up in alt-tab. Mail, empathy, system settings, media/office files launched from nautilus are affected.

---

### Post by screaminj3sus on 2012-03-03
> **kelpdip said:**
> I get the same behaviour. It seems like the open arrow > is given to programs launched without the unity toolbar -- from terminal, or system toolbar, or nautilus for instance. Focus has no effect on the indicator. Solid arrow is assigned to programs launched from unity toolbar. Only solid arrows sow up in alt-tab. Mail, empathy, system settings, media/office files launched from nautilus are affected.

Yeah that exactly describes what I'm seeing. I noticed if you bring up the desktop switcher with super + s, the effected apps suddenly show up in the alt tab switcher.

EDIT: Found a workaround. In compizconfig > unity > Switcher uncheck "Bias alt tab to prefer only windows on current viewport". Personally I prefer this behaviour anyway :)

It seems like for some reason unity is considering windows not open from the launcher as being in a seperate viewport, even though all these windows are in one viewport.

---

### Post by mc4man on 2012-03-03
Don't see that at all, such are the variances ot PP.
Here all windows open on a WS get a solid arrow not matter how they were opened

(though here now have this bug where - 
 if  gnome-terminal is open on a WS then most times when then opening nautilus from the launcher or launcher quicklist it puts the nautilus window on top without focus (blue arrow

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-03
It all got back to normal for me with one of the recent updates. Now I'm using Beta 1 and all windows on active viewport are showing with a triangular arrow.

---

### Post by screaminj3sus on 2012-03-04
> **&#1058 said:**
> It all got back to normal for me with one of the recent updates. Now I'm using Beta 1 and all windows on active viewport are showing with a triangular arrow.

hmmm, strange that im still seeing this. 12.04 beta with all of latest updates.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-04
It is strange, but that's not the only problem with Unity that's coming and going. Since recently, when you press & hold Super key, you can see a keyboard short cuts overview, in which it is written that switching workspaces is done with 'Super+Shift+Cursor keys', while since a few days ago it is being done with 'Ctrl+Alt+Cursor keys'. Also, Unity's Dash is conflicting with any other dock application, e.g. Docky when it comes to minimizing and raising windows. Fingers crossed that all this will be fine before final release.

---

### Post by edm1 on 2012-03-04
I launched a [bug report]("https://bugs.launchpad.net/unity/+bug/944995") for this yesterday. Sounds like the same problem.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-04
I wouldn't worry too much about it though. It's obvious that developers are actively improving the switcher's behaviour. With each update it's becoming more stable.

---

