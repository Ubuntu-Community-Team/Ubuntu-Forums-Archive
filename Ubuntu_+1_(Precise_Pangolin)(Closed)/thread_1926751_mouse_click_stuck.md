---
title: "mouse click stuck"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ernestj on 2012-02-16
Has anyone had a mouse issue after update? My mouse on my laptop was dragging and dropping without problem, in fact, it was better than it ever was in 11.10. After update, it now drags but does not want to drop. 
Can I fix this or wait to new update?

Ernie

---

### Post by ernestj on 2012-02-16
I made a post about drag and NO drop, but this is a problem that might need to be addressed. I noticed from another thread that I am not the only one with the stuck mouse click. It highlights the whole page or when trying to drag and drop, does not drop.

Ernie

---

### Post by mc4man on 2012-02-16
Seeing the same on a fresh install, happens at random, have seen it mainly in Firefox but also a couple of other area's. It *May* be related to the updated xserver-xorg-input-synaptics, maybe something else. 

(i've found using the Dash or Super+# to open an app will release the cursor

---

### Post by hvbakel on 2012-02-16
Same here, it might be worthwhile to submit a bug report in launchpad.

---

### Post by mc4man on 2012-02-16
Not sure what to file against? 
Are you seeing with a mouse or touchpad, ect.
here i'm using a laptop - touchpad

Also can't find a way to cause other than it just 'happens', so I've reverted the xserver-xorg-input-synaptics to previous verssion, will see if it occurs over the next few hr.s or so.

---

### Post by ernestj on 2012-02-16
I am using a laptop. It is like trying to drag and drop, but it does not drop. Also, you can click on something and it highlights the page. Like you are trying to highlight a word and the whole page gets highlighted. Like having sticky fingers.

ernie

---

### Post by skeve on 2012-02-16
I'm not sure if I'm having the same issue like everybody here. When I click a window corner ro resize it the touchpad/mouse stucks until I make another click. But honestly I like this behavior more - it's like in MacOS X, and it is something that I wished would be done some day.
I usually prefer touchpad to mouse, so when your touchpad is small it can be hard to move an object  from one point to another if these points are far apart.
I think there should be an option to change this behavior according to one's preferences.

---

### Post by mc4man on 2012-02-17
Well it's not the xserver package, took a while but got the same in a terminal.
Also have seen a couple of times when the left click 'dies' for 20 sec's or so, then comes back.

---

### Post by Milos_SD on 2012-02-17
It is happening to me too, on a desktop PC with a usb mouse. When that happend, I can't even write anything with keyboard, keys just don't respond. Only way to get it working is to activate Scale windows plugin, that I have set to the right top corner of my screen. :) I think it is bug in Unity or Compiz.

---

### Post by grahammechanical on 2012-02-17
I am not getting this problem but what I see happening on my system might be related.

When I press either shift key then keyboard shortcuts stop working. Crtl+Alt+arrow key does not switch workplaces. Ctrl does not open the Dash. F10 does not bring down the top panel menus.

If I am typing a post in this forum or typing in a Libreoffice document and I press shift then the insertion point disappears and you cannot enter text.

I can use the mouse to copy but without the insertion point the mouse cannot paste. When this effect is happening the mouse is unable to insert the insertion point.

If I use the launcher workplace switcher to switch back and forth the issue is corrected. If I switch Libreoffice windows it is rectified. If I click the top of a window it is rectified.

I have twice lost the insertion point whilst typing this post. I have spent a couple of hours trying to work out what was triggering this off.

I get this affect by pressing either shift key. Is this the cause for the problems you are having?

Regards.

---

### Post by Milos_SD on 2012-02-17
@grahammechanical: It is exacly what I was having. It is gone now with Unity 5.4.0 update. :)
But still having problems with expo and applications switcher showing all white. :)

---

### Post by mc4man on 2012-02-18
At least here the cursor stick on left click is continuing to happen on occasion. 
I was able to find a way to cause pretty much at will - here it involves starting to highlight something & a small tap on the touchpad in a certain way

It's possible that disabling the 'tap to click' in g-c-c option may help

So filed a bug on a possible? suspect package & included some videos showing it happening

[https://bugs.launchpad.net/ubuntu/+source/utouch-geis/+bug/934770](https://bugs.launchpad.net/ubuntu/+source/utouch-geis/+bug/934770)

---

### Post by mc4man on 2012-02-18
If being affected by this _on a touchpad_ there are a couple of things to try - hopefully this will be fixed, not sure yet...

These two are only per session changes though could be added to startup script - 

This will affect nothing concerning tap to click, may help, may not (not too much here
```
synclient LockedDrags=0
```

This will set back to the eay it was, at least here, YMMV
```
synclient LockedDrags=0 TapButton1=1 TapButton2=3 TapButton3=2
```
If you don't care about tap to click at all then try disabling in System Settings

---

### Post by cryptotheslow on 2012-02-19
mc4man - I agree with your analysis about leaving it to sit still a while.

I can't reliably cause the stuck select / click / grab to happen on demand, but when it does it seems the more I click or move around the longer it takes to resolve itself. Whereas simply doing nothing for a time (10 - 30 seconds here) and it will always free itself up and go back to normal.

I seem to most commonly experience the problem when typing in a text box (e.g. like this forum reply box) and have to conclude it is to do with unintended palm activation of the touchpad (even though I have disable when typing apparently enabled). Frustrating little glitch for sure :)

---

### Post by mc4man on 2012-02-19
> **cryptotheslow said:**
> mc4man - I agree with your analysis about leaving it to sit still a while.

I can't reliably cause the stuck select / click / grab to happen on demand, but when it does it seems the more I click or move around the longer it takes to resolve itself. Whereas simply doing nothing for a time (10 - 30 seconds here) and it will always free itself up and go back to normal.

I seem to most commonly experience the problem when typing in a text box (e.g. like this forum reply box) and have to conclude it is to do with unintended palm activation of the touchpad (even though I have disable when typing apparently enabled). Frustrating little glitch for sure :)
The easiest way to reproduce on a touchpad is this - Assumes that double & triple taps function. (or run this to make sure
synclient TapAndDragGesture=1

Open a text file or even a reply here, do a quick double tap on the touchpad while slightly moving your tap finger up or down. This will highlight text & cause a 'grab' that won't release until you cease activity & wait a bit.

I'm fairly sure this is related to whatever has recently been done as far as touch/mouse gesture support

For the moment I've decided here to set back to previous  Since doing so have had no occurrences of a stuck grab or an unresponsive left click that I also got from time to time.

(I think people with small touchpads are more likely to be affected as they tend to lift & reposition finger on touchpad a lot, opening the possibility for a double tap & move gesture 

```
gedit ~/.config/autostart/synclient.desktop
```

```
[Desktop Entry]
Type=Application
Exec=synclient LockedDrags=0 TapButton1=1 TapButton2=3 TapButton3=2
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=5
Name=onetap
```

I remain curious as to how they'll fix this for users of normal touchpads, eliminating double & triple taps is one way though not the best solution

---

### Post by mc4man on 2012-02-21
If keeping the new defaults  - 
If getting the 'stuck cursor' then a 2 tap should release (here that means 2 single finger taps

If getting an inadvertent grab then a single tap will release, just watch where releasing

If getting an unresponsive left click then maybe a 2 tap will restore, otherwise cease activity & it should restore in 5 sec's or so.

Myself can't be bothered with this or trying to use the very small touchpad here in a new way & will just create a Startup as shown above

---

### Post by WarriorIng64 on 2012-02-23
This is a known issue caused by a design change. Some people felt drag-and-drop was too difficult the way it was before, so it was proposed that the drag should continue until the trackpad is tapped again to stop it.

The bug you want to go and mark yourself as affected on is [Bug 934770]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/934770"). Currently, this bug is looking for user feedback in order to decide whether this change should be reverted.

---

### Post by cariboo on 2012-02-23
Instead of starting a new thread for each mouse problem, lets keep them all in the same thread. Merged two threads.

---

### Post by ernestj on 2012-02-23
I was starting to think that this problem was done on purpose as a new way to drag and drop. If feedback is needed, then I do not like it. It highlights my whole page and I have to spend time trying adding another tap to unlock. The drag and drop on 11.04 was very good. On 11.10, once two finger scroll was finally an option, the drag and drop did not work well at all. Then, when I first installed 12.04, drag and drop was perfect, the best yet. To me, this is not a step in the right direction with the drag and drop locked. They had it perfect with the original set-up on 12.04.

Thanks,
Ernie

---

### Post by cariboo on 2012-02-23
Just out of curiosity, have you tried a different mouse? I've had some of the problems you described, but switching to a different mouse solved the problem.

---

### Post by mc4man on 2012-02-23
> **ernestj said:**
> I was starting to think that this problem was done on purpose as a new way to drag and drop. If feedback is needed, then I do not like it. It highlights my whole page and I have to spend time trying adding another tap to unlock. The drag and drop on 11.04 was very good. On 11.10, once two finger scroll was finally an option, the drag and drop did not work well at all. Then, when I first installed 12.04, drag and drop was perfect, the best yet. To me, this is not a step in the right direction with the drag and drop locked. They had it perfect with the original set-up on 12.04.

Thanks,
Ernie

If desired you can test by reversing  *most* *of the changes* by running this in a terminal. If it doesn't help or produces undesirable results then a simple log out/in will return you to current settings or you reverse by running the 2nd command below.
```
synclient LockedDrags=0 TapButton1=1 TapButton2=3 TapButton3=2
```

to reverse above

```
synclient LockedDrags=1 TapButton1=1 TapButton2=3 TapButton3=0
```

Edit: the command could obviously be shortened to just what's being changed, posted all to assure if any of the taps had be changed, so 

synclient LockedDrags=0  TapButton3=2
or
synclient LockedDrags=1  TapButton3=0

---

### Post by WarriorIng64 on 2012-02-23
> **cariboo907 said:**
> Just out of curiosity, have you tried a different mouse? I've had some of the problems you described, but switching to a different mouse solved the problem.

A regular mouse / the physical mouse buttons next to the trackpad work fine. The problem is with drag-and-drop when using just the trackpad itself by tapping and dragging.

---

### Post by matt_symes on 2012-02-23
I have been seeing these exact same problems.

I have been unloading and reloading the mouse driver when all else fails (as it has a couple of times), but for most cases a double tap or bringing up the dash fixes it. (I have been using a touchpad, not a mouse)

I will try your suggestions mc4man.

This is a real step back in usability as it's too easy to trigger this behaviour unintentionally.

---

### Post by mc4man on 2012-02-23
There is a new package coming shortly, (xserver-xorg-input-synaptics -
1.5.99~git20120223-0ubuntu1) that should set things back to the way they where

For those that happened to like the locked drag they could likely adjust as needed thru synclient

---

### Post by matt_symes on 2012-02-23
> **mc4man said:**
> There is a new package coming shortly, (xserver-xorg-input-synaptics -
1.5.99~git20120223-0ubuntu1) that should set things back to the way they where

For those that happened to like the locked drag they could likely adjust as needed thru synclient

Excellent. I think that is the right way forward.

---

### Post by WarriorIng64 on 2012-02-23
I got the xserver-xorg-input-synpatics update, and I can confirm that it fixes the issue by reverting to the old behavior.

---

### Post by ernestj on 2012-02-24
I second that. I updated this morning and mouse behavior is back to normal and working great!!:D

---

