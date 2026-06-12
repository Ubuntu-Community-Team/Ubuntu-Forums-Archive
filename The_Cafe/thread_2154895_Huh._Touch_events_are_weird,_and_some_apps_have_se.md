---
title: "Huh. Touch events are weird, and some apps have secret purposes for them."
date: 2013-06-16
forum: The Cafe
---

### Post by Copper Bezel on 2013-06-16
**TLDR:** Single-finger touch events seem to be read differently from trackpad taps, with hidden touch-scrolling features in certain apps.

I might simply be slow to the party on this one, but I noticed something kinda cool. 

**Bit of background:** I got an Asus x202e recently (lovely, lovely piece of kit.) It has a touchscreen. The touchscreen is, of course, nigh-useless in desktop Ubuntu, and the x202e's is further useless, because it has a quirk of getting stuck in a left-click event and not receiving any more left-click events until it feels better about it. That said, I've been able to play with some touch functionality in Unity and Gnome. I admit that it has become my preferred method of pausing YouTube videos and of scrolling web pages in Chrome with a touch extension installed.

I knew that there was some touch stuff associated with Desktop Unity. Four-finger tap and drag gestures pull up the Launcher and Dash; the three-finger tap calls the much-loved Compiz "Love Handles" plugin (which is mercifully easy to change back to a middle-mouse click* now.) There's also a very finicky application switcher based on performing a very rapid and elaborate sequence of three-finger taps and swipes. ** I also knew that the trackpad and touchscreen read slightly differently. When I handed the three-finger tap over to Synaptics, the love-handles behavior still worked from the touchscreen, and two-finger tapping on the touchscreen doesn't right-click. (Duh, right? Synaptics isn't involved.)

**The bit I found interesting:** I *didn't *know that some core apps seem to respond differently using touch input. I noticed it first in Nautilus - tapping and dragging the background scrolls the window contents, with a special stretch-and-bounce behavior at the top and bottom of the list. Since Nautilus is a core Gnome app, I tried Web (neé Epiphany) and got the same behavior, so I thought perhaps it was a Gnome thing. But then I accidentally discovered that it works in Ubuntu Software Center, too. 

Is this something everyone else already knew about? I had assumed that utouch was mostly just sending the same sorts of events along that multitouch trackpads did. I didn't realize that there was a separate set of events for touchscreens, or that there was development going on within the core apps to support them. I guess it makes sense as a part of making these apps touch-friendly when they're running under Ubuntu Touch, without the configuration and chrome that desktop Unity provides, but it seems to be a GTK3 thing, rather than an Ubuntu thing. (And GTK3 is supposed to support multi-touch, but I'm not really sure what that means. 

So who's writing this stuff, and what does it do?

* UF compose windows don't support middle-click paste. Bad show, UF.

** Typing this topic led me to mess with Touchégg and rebuild Unity to let gestures pass through to it, which makes my trackpad better (yay Exposé gesture, I've missed you so!) and the touchscreen even worse - I never really know *what *tapping with a single finger on the touchscreen is going to do, now. But interestingly enough, even when it stops working as a click event, it works as expected for most of the controls inside Epiphany, Gnome, and USC, as well as the touch scrolling. Tapping and dragging in Gnome Terminal still selects text, too. All of that applies only if the window is selected, though.
 
EDIT: Should this be posted in Ubuntu, Linux, and OS Chat? Sorry if I misplaced it!

---

### Post by Copper Bezel on 2013-06-17
Encountered a further oddity. Inverting scrolling through xinput no longer works for these apps. Or, at least, for gedit and nautilus, which I just tried. Switching the scroll direction on the trackpad for Mac-style "natural scrolling" makes most apps scroll inverted, but scrolling remains "normal" in these windows. I'm really curious where all of this is happening, now. = )

---

### Post by bootch2 on 2013-10-27
TLDR: Touch events from the hardware go through a stack of software: a kernel driver (handles the USB-ness),  the "x input driver", probably the window manager (Unity?), the GUI framework (e.g. GTK or Qt), and finally the app code.  Any of them can alter what is finally delivered to the app, and what happens.  Most of the stack is configurable, but poorly documented.  Yes, the situation with touch events is a mess.

My x input driver is named "wacom" (the filename is xf86-input-wacom).  You can read the source code, it is short and somewhat understandable.  One thing you will see is that it treats touch screens and trackpads (with touch capability) differently.

Another thing you will see is that the "wacom" driver implements some gestures, that is, translates some touch events into different events.  For example, by default, the "wacom" driver translates two-finger touches (moving) into "scroll" events, that is, the app gets an event as if from a mouse scroll wheel.  You can configure the "wacom" driver to not do that.  I don't know, but it might be inverting the scoll direction also.

Also, the Unity window manager (I'm not sure if that is the proper terminology) might be "capturing" certain gestures and not passing the touch events through to an app.  I think Unity is capturing three-finger gestures.

I am trying to understand why a single finger touch on my Bamboo Pen and Touch does not get through (as a bona-fide touch event) to an app I have written.  My stack is whatever comes with Ubuntu 13.4, except that my app is using the Qt framework (not GTK.)

---

### Post by Favux on 2013-10-27
> Also, the Unity window manager (I'm not sure if that is the proper terminology) might be "capturing" certain gestures and not passing the touch events through to an app. 
Yep.

Partial answers to some of your questions on the Linux Wacom multi-touch page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch)  Input appreciated.  :)

---

### Post by bootch2 on 2013-10-27
Favux: thanks, I have read that previously, that's probably where I learned about disabling 2FGT gestures in the wacom driver.  I tried the "discuss" tab on that wiki, and was denied access.  I DO have some suggestions, mainly about technical writing to make it clearer (not so much about technical facts. Except: that page says "by turning the Gesture parameter off the touch contacts are now passed to the X Server".  Shouldn't that say "through the XServer, unmodified" or "to the X client." ?  In other words, isn't the "wacom" driver part of the X server, and apps are X clients?)

And I was just reading the man page for the "wacom" driver (>man wacom).  Under "TOUCH GESTURES>Single Finger(1FG)" it seems to say that to get a touch event from a single finger in an app, a user needs to actually touch the screen twice (tap the screen with a finger and quickly put a finger back down.)  In other words, the wacom driver is also translating (recognizing) single touches into button events (which are not raw touch events to the application.)  Unlike the two-finger gestures, I'm not sure this can be disabled in the wacom driver: the man page says: Option "Gesture" "bool" Enable or disable multi-finger gesture support on the device.  Emphasis on "multi-finger" as opposed to single finger.

I am using /usr/bin/xev to test what X events the wacom driver actually sends.  It opens a window, and displays in the console what X events are received in the window when a user manipulates a mouse or trackpad or other input device when the cursor (focus) is in the window.  So far I have not seen any "touch" events, but I am assuming that xev is outdated with respect to touch events, which were only recently added to X.

---

### Post by Favux on 2013-10-27
Hi bootch2,

> I DO have some suggestions, mainly about technical writing to make it clearer (not so much about technical facts. Except: that page says "by turning the Gesture parameter off the touch contacts are now passed to the X Server". Shouldn't that say "through the XServer, unmodified" or "to the X client." ? In other words, isn't the "wacom" driver part of the X server, and apps are X clients?)
That sounds right.  I probably should change that after I think it through a bit.  Ping felt that it was time for a multi-touch page given all the work they had done in the kernel and Peter adding multitouch to X.  Not to mention all the nice new multi-finger touch hardware Wacom had come out with.   So I got the job, what with being the gopher and all.  You're seeing my limitations.  The hope was/is that others with more expertise would contribute.  You have to ask Peter to get added to the wiki due to a SourceForge limitation on hosted app.s he has to add wiki contributors manually.
```
Under "TOUCH GESTURES>Single Finger(1FG)" it seems to say that to get a touch event from a single finger in an app, a user needs to actually touch the screen twice (tap the screen with a finger and quickly put a finger back down.)
```
Are you talking about the left click drag?  That's me again trying to describe some code contributed by a non-linuxwacom dev.  So my clumsy wording may be giving you the wrong impression.
> In other words, the wacom driver is also translating (recognizing) single touches into button events (which are not raw touch events to the application.) Unlike the two-finger gestures, I'm not sure this can be disabled in the wacom driver: the man page says: Option "Gesture" "bool" Enable or disable multi-finger gesture support on the device. Emphasis on "multi-finger" as opposed to single finger.

That's gone through multiple changes in the kernel and I haven't been able to keep track.  You should seek help from Chris, Jason, or Ping on the linuxwacom-discuss mailinig list:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

---

