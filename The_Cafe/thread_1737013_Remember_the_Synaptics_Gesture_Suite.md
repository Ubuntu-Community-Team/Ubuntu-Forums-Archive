---
title: "Remember the Synaptics Gesture Suite?"
date: 2011-04-22
forum: The Cafe
---

### Post by rob356 on 2011-04-22
About a year ago Synaptics announced the Synaptics Gesture Suite for Linux. Shortly after OSNews [published an email from Synaptics]("http://www.osnews.com/story/23204/Synaptics_Looking_into_Availability_Gesture_Suite_to_End_Users") stating that they would consider releasing the suite to end-users. It has been over a year and the Windows version has been released ("Scrybe"), but no linux love.
I sent them an email about it:
> About one year ago you announced the availability of the Synaptics Gesture Suite for Linux. Shortly after OSNews posted a reply ([http://www.osnews.com/story/23204/Synaptics_Looking_into_Availability_Gesture_Suite_to_End_Users](http://www.osnews.com/story/23204/Synaptics_Looking_into_Availability_Gesture_Suite_to_End_Users)) they received from you, stating that you would look into the possibility of releasing the Synaptics Gesture Suite to end-users. You have done that with the Windows version with the Scrybe product, and I was wondering if/when you will do the same for Linux. I feel that Linux deserves the same attention that Windows does, and it appears that you also do, because you created the Linux version. Currently Synaptics products are severely limited on Linux. The most they can do is 2-finger scrolling. The images on your site promise so much more, but we have yet to see it in Linux. The beauty of Linux and the open source community is, even if you just release a closed source driver, as long as it sends documented events to the X server, Gnome/KDE devs will multiply your work many times over and come up with amazing things.

All I am asking for is an update on the situation. Does Synaptics still plan to offer the Gesture Suite to end-users?

Thank you for your time,
<MY NAME>
I hope other people can send them emails so that we might get a response. I sent it to [mailto:info@synaptics.com]("mailto:info@synaptics.com").

I have tried out utouch/ginn and they are just too buggy to be useable. Please help get this released!

---

### Post by LowSky on 2011-04-23
I hate when companies say they will support something and then never do.

---

### Post by hansdown on 2011-04-23
It seems to have been done for linux.

[http://www.linux.com/news/software/applications/300782-synaptics-gesture-suite-ported-to-linux](http://www.linux.com/news/software/applications/300782-synaptics-gesture-suite-ported-to-linux)

---

### Post by Copper Bezel on 2011-04-23
Yeah, I ran into that months ago and was very tempted to try it out (but my trackpad driver is already hacked to change orientations, so that it's consistent with the display when my netbook is in portrait mode for reading, and that's a more important feature for me.)

---

### Post by Zero Prime on 2011-04-23
On this note, I wish they would hurry and release as a download, but here is the real question.  Why doesn't Gnome support multi-gestures on the touch pad without 3rd party software that has to be configured when KDE already does?

---

### Post by Copper Bezel on 2011-04-23
Ubuntu is actively working on improving their gesture suite, at least. Note though that while some of these functions have to do with the way the DE registers input, some of it has to do with driver capabilities, too.

---

### Post by rob356 on 2011-04-23
I have seen the work on utouch already, looks great, but it only works by itself in a limited number of applications. I tried ginn, but is was just too buggy to replace the synaptics driver.

I think utouch/ginn could become so much simpler and usable if all it had to do is receive events from the driver. Synaptics has done the work, they just have to release it to us!

---

### Post by Copper Bezel on 2011-04-23
Sorry - I should have used a quote. I was responding to Zero Prime, not the topic as a whole. I don't have any experience with ginn or utouch (and as I said, I'm using the Synaptics driver myself.)

I don't fully understand the distinction you're making, so maybe you could explain it a bit more - doesn't a particular application need to know what to *do* with a particular input, anyway? The basic gestures the Synaptics drivers provide, like the three basic click emulations and the two-finger vertical and horizontal scrolling, have something to do in any application; they're all registered as button-click events, passed through whatever xmodmap reassignments you've made, etc. Pinch zoom, rotate, or anything like that is (1) more complex than a click event and (2) only going to apply to applications that support that feature, anyway.

---

### Post by rob356 on 2011-04-23
Ginn + utouch are supposed to replace the synaptics driver. (So instead of synaptics in the driver section, you would use evdev.) From what I understand utouch watches for gestures and passes them to the active application. Almost no applications support these touch events. Ginn can intercept these events and translate them into key presses. For example I set up an "event" in ginn so that a 3-finger swipe to the right presses "Ctrl+[" (back in chrome). The only problem was it was VERY buggy. The cursor jumped all over the place, tapping worked half the time, and scrolling was just pushing the down arrow. Hopefully if synaptics never releases their driver the ginn team can improve ginn, since it holds great promise!

---

### Post by Copper Bezel on 2011-04-23
Oh, yuck. Yeah, I can understand the irritation there.

Random thought, but y'know what would be awesome and *actually* useful? Three-finger drag = Atl+drag. Yeah. Title bars would be instantly obsolete. = D

---

### Post by Copper Bezel on 2011-08-31
I think this thread is dead.

Out of the box, the Synaptics drivers on Ubuntu do more than Scrybe does. I wouldn't give up my middle click for anything, and certainly not for the opportunity to play pictionary.

---

### Post by realzippy on 2011-08-31
> **Copper Bezel said:**
> 
I wouldn't give up my middle click for anything, and certainly not for the opportunity to play pictionary.

You don't have to give up anything...
In fact easystroke speeds up your workflow drastically.
I use it for years,laughing about the "window buttons to the left discussion" (you remember?) or the "unity-quick-access-to-everything-shortcuts"...
..mouse gestures should be 1rst choice when re-inventing the desktop.

---

### Post by Copper Bezel on 2011-08-31
Sorry, I misunderstood. I don't know how Scrybe comes into this, but that's an extraordinarily useful command, and thanks for that.

---

### Post by Enterpart on 2011-09-01
hey Copper your welcome, I thought it comes under Scrybe because Scrybe is used in similar fashion i,e highlight a word and then draw a letter and it loads up a website with your search queried. well I'm happy someone found it useful.

I've got one more tip if your searching on a website with with several other tabs open and use a gesture with this code it will open a new tab at the end (in chrome) and after closing that tab your stuck at the tab at the far right and have to look through to find the one your at

the way around is insert the code
--new-window after google-chrome this will open in a new window

e.g

```
google-chrome --new-window "http://www.youtube.com/results?search_query=`xsel -p | tr [:space:] +`&aq=f"
```

---

### Post by Copper Bezel on 2011-09-01
Yeah, I don't understand how drawing a letter is easier than a keyboard shortcut, but I'm not a mouse gesture person, so I guess I maybe just don't think that way. But I set your command to Super+F in Compiz, and I can imagine a lot of use cases - even just checking a spelling from LibreOffice and such.

---

