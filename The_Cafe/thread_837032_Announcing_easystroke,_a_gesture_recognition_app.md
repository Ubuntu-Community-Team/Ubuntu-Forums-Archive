---
title: "Announcing easystroke, a gesture recognition app"
date: 2008-06-22
forum: The Cafe
---

### Post by Tom Jaeger on 2008-06-22
Hi,

I'd like to announce [easystroke]("http://easystroke.sourceforge.net"), a new gesture recognition application for linux.  Gesture recognition means that you can draw arbitrary curves on the screen by holding down a specific mouse button, and if the program recognizes their shape, it will perform certain actions.  For example, you can configure easystroke to maximize the current window if you draw a straight line in North-East direction.

My primary motivation for writing easystroke was to allow easy operation of a Tablet PCs even without a keyboard present, but of course it will work just as well with a mouse.  It is not meant to replace an onscreen keyboard/input panel such as cellwriter, but rather supplement it.

Here's a short list of the program's main selling points:
[LIST]
[*] It aims to be easy to set up and to configure.  There are no configuration files that need to be edited and no cryptic commands that have to be entered somewhere.
[*] It tries to give the user easy access to the most commonly used features:  Setting up a new gesture requires just a few clicks and will show only one small popup dialog (to actually define the stroke)
[*] It allows you to use strokes of arbitrary shape.  There is no requirement that gestures have to be composed of line segments, and curvy shapes such as an 'S' or a 'G' work just fine.
[*] Some of the features make life without a keyboard a lot easier: You can emulate a scrollwheel, ignore the next stroke and pass the next mouse action to the application (possibly with a modifier held down, so that you can Alt-move or Alt-resize a window without a keyboard) and emulate an additional button that your tablet pen didn't even have in the first place.
[*] The project is still young, so there's much more to come.
[/LIST]

EDIT (Aug 3):  The latest version is 0.2.1.  See [this post]("http://ubuntuforums.org/showpost.php?p=5519620&postcount=118") for details.
EDIT (Aug 17): Released 0.2.2.
EDIT (Dec 12): Current version is 0.3.0
EDIT (Feb 2): Released 0.4.0

The program is available as a .deb package tested on Ubuntu Intrepid and as a source tar.gz.  It is also available through my [launchpad PPA]("https://launchpad.net/~thjaeger/+archive").  There are a few screenshots on the project's [documentation page]("http://easystroke.wiki.sourceforge.net/Documentation").

Thank you,
Tom

---

### Post by Chokkan on 2008-06-22
Looks very cool. I'm currently using [Gestikk]("https://launchpad.net/gestikk") which, I think shares some similarities to your project. I'll give easystroke a try. Could you give me a few pointers on what makes this different (better?) than Gestikk?

---

### Post by Tom Jaeger on 2008-06-22
Hmm, I haven't spent too much time evaluating gestikk, so I might not be the best person to comment on this, but at least from the point of view of a tablet pc user, easystroke has a few clear advantages:  It is more flexible in what strokes it allows (I haven't been able to define an S-shaped stroke in gestikk, for example) and there are actions such as ignore and scroll that are specifically designed to make keyboardless operation easier.  Another obvious difference is that gestikk will pass strokes to the applications, producing spurious right-clicks.  I'd also like to think that easystroke's UI is more polished, but of course, this is a matter of opinion.

---

### Post by Luffield on 2008-06-22
I use Gestikk too and I'm pretty happy with it, but I think I'll give easystroke a try because I'm curious about the statistics :)

---

### Post by bash on 2008-06-22
I'm sitting in front of a windows box atm, so I can't try it. But personally what I'm looking for is basically a version of the firefox plugin all-in-one-gestures for the desktop. Does your programm come close to that?

---

### Post by Chokkan on 2008-06-22
I think that is pretty much what it is. Check out the sourceforge page. Pretty good documentation there.

---

### Post by barbedsaber on 2008-06-22
its bad enough going onto a windows computer, pressing super key+space, and getting annoyed when gnome-do doesn't come up.

---

### Post by Mazza558 on 2008-06-22
How will this work with Firefox and a mouse gestures addon?

---

### Post by Luffield on 2008-06-22
> **barbedsaber said:**
> its bad enough going onto a windows computer, pressing super key+space, and getting annoyed when gnome-do doesn't come up.
You can install Launchy. It's not as good as Gnome-Do but it's better than nothing.

---

### Post by barbedsaber on 2008-06-22
> **Luffield said:**
> You can install Launchy. It's not as good as Gnome-Do but it's better than nothing.

school computer, but thanks anyway.

---

### Post by Tycho Quad on 2008-06-22
Thank you so much Tom! This is exactly what I have been looking for since I moved to Ubuntu and lost my precious Strokeit.

Small feature request, I would like the ability to set mouse buttons as gesture triggers. For example, If I hold down the gesture button and flick the scroll wheel up 3 times, I would like easystroke to skip through 3 tabs. This is how I had it set up in Strokeit, and I really liked it :)

---

### Post by Mazza558 on 2008-06-22
It installs in Gutsy too, just tested.

EDIT:

It doesn't run though.

>  easystroke
easystroke: error while loading shared libraries: libboost_serialization-gcc42-1_34_1.so.1.34.1: cannot open shared object file: No such file or directory


---

### Post by barbedsaber on 2008-06-22
> **Mazza558 said:**
> It installs in Gutsy too, just tested.

EDIT:

It doesn't run though.

well, that would make it very usefull

---

### Post by zmjjmz on 2008-06-22
What arguments would I use to set it to unminimize a window?

---

### Post by Luffield on 2008-06-22
I must be missing something in the configuration procedure, because my gestures don't do anything and the statistics tab always shows -100%.
The documentation is a bit vague there I think. After I set the name, the type and the argument I click "record stroke" and a dialog box pops up, asking if I want to delete current or cancel. I click "delete current" (makes more sense to me but "cancel" doesn't work either), I make the gesture and, well, nothing happens. Nothing shows up in the Stoke column.
Bug? User error?
Other than this problem Easystroke looks very good indeed.

---

### Post by Tom Jaeger on 2008-06-22
> **Tycho Quad said:**
> 
Small feature request, I would like the ability to set mouse buttons as gesture triggers. For example, If I hold down the gesture button and flick the scroll wheel up 3 times, I would like easystroke to skip through 3 tabs. This is how I had it set up in Strokeit, and I really liked it :)

Interesting idea.  I've used strokeit and it actually was part of my motivation for writing easystroke (although its gui servered more as a negative example), but I've never noticed this feature.

This isn't very hard to implement and easystroke is actually doing something quite similar right now in its 'click during stroke' feature (which is actually a lot more involved).  Of course, 'click during stoke' is the exact opposite of what you are looking for.

I don't think anyone would want to use this feature and the current 'click during stroke' at the same time, so it would make sense to enable the feature in the same combo box.  You would then set up individual actions using "Record Stroke", so this won't clutter up the UI, which is very important to me.

The only remaining question is whether this should ignore the gesture that was drawn prior to flicking the scroll wheel or if the action should depend on it, so that you could set up gesture button + scroll wheel to switch tabs in firefox and an 'up' gesture + scroll wheel to do alt+tab.  I don't have a preference here, so I'm inclined to give the user a choice, it'd be just one additional combo box entry.

Tom

---

### Post by Tom Jaeger on 2008-06-22
> **Mazza558 said:**
> It installs in Gutsy too, just tested.

EDIT:

It doesn't run though.

My bad, I got the dependencies wrong.  I'll see if I can fix that, you might need to install the hardy version of libboost-serialization.  Can you paste the output of 'apt-cache search libboost-serial' on your system?

In any case, the binary (easystroke-0.1.2.gz) has boost-serialization statically linked in, so it should run on gutsy.

When I started developing easystroke, I had a few problems with bugs in the version of the gtk library that comes with gutsy.  Hopefully the workarounds I put in place are still working, but I haven't tested this recently, so you might experience some UI glitches.

---

### Post by Tom Jaeger on 2008-06-22
> **zmjjmz said:**
> What arguments would I use to set it to unminimize a window?
That would be a feature that would have to be implemented in the window manager.  The only thing I can think of right now is Alt+Tab, but at least under compiz, that only works if there are at most two windows on the desktop.  Changing the alt+tab order might help, but I couldn't find an option for that.

Tom

---

### Post by Tom Jaeger on 2008-06-22
> **Luffield said:**
> I must be missing something in the configuration procedure, because my gestures don't do anything and the statistics tab always shows -100%.
The documentation is a bit vague there I think. After I set the name, the type and the argument I click "record stroke" and a dialog box pops up, asking if I want to delete current or cancel. I click "delete current" (makes more sense to me but "cancel" doesn't work either), I make the gesture and, well, nothing happens. Nothing shows up in the Stoke column.
Bug? User error?
Other than this problem Easystroke looks very good indeed.

You just do the gesture while the dialog is open.  It'll close automatically.  I should probably disable the 'Delete Stroke' button when there's no stroke set up yet.

---

### Post by Luffield on 2008-06-22
Thanks Tom. It works great now. Excellent job, I love this.

---

### Post by Luffield on 2008-06-22
I think I found a real problem now :)
I added an exception for Firefox and it worked well (although Easystroke called it Navigator for some reason). Then I added Easystroke to my session, logged out and logged in. It started automatically and worked well, but the exception for Firefox didn't work. I quit Easystroke and ran it from the terminal, and then the exception worked again.

---

### Post by Tom Jaeger on 2008-06-22
> **Luffield said:**
> I think I found a real problem now :)
I added an exception for Firefox and it worked well (although Easystroke called it Navigator for some reason). Then I added Easystroke to my session, logged out and logged in. It started automatically and worked well, but the exception for Firefox didn't work. I quit Easystroke and ran it from the terminal, and then the exception worked again.

Thanks, I understand the issue now:  It occurs whenever firefox is started while easystroke is already running.  Easystroke currently asks for the WM_CLASS property only when the window is created and uses a cached value later.  The problem is that firefox sets WM_CLASS later than expected.  This should be easy to fix.

---

### Post by Tom Jaeger on 2008-06-22
> **Luffield said:**
> I think I found a real problem now :)

Fixed in the darcs repository and the attached binary.

---

### Post by Luffield on 2008-06-23
Wonderful! Thank you!

---

### Post by Tom Jaeger on 2008-06-23
> **Tycho Quad said:**
> 
Small feature request, I would like the ability to set mouse buttons as gesture triggers. For example, If I hold down the gesture button and flick the scroll wheel up 3 times, I would like easystroke to skip through 3 tabs. This is how I had it set up in Strokeit, and I really liked it :)

Implemented in darcs and I've also attached a binary.  Just set 'Stroke during click' in the Preferences tab to 'Action' and you should be all set.  Note that this is still very experimental.  In particular, I'm pretty sure it won't work correctly if your trigger button is > 5.

---

### Post by Tom Jaeger on 2008-06-23
> **Tom Jaeger said:**
> In particular, I'm pretty sure it won't work correctly if your trigger button is > 5.
Yup, this is a problem.  The X server does not report events correctly in this case.  I can think of an evil workaround, but I'm not sure I want to go there.

---

### Post by Tycho Quad on 2008-06-23
Works fabulously thank you very much!

I'm getting some weirdities in regard to certain mouse buttons but you already told me of that, besides, i think it's partly because linux is not identifying all my mouse buttons correctly anyway. I have a Logitech MX1000 (non bluetooth) if anyone knows how I could fix that, please let me know.

EDIT: Another small feature request... Would it be possible to perform the gesture on the window under the point where the gesture started, rather than the window in focus?

---

### Post by Tom Jaeger on 2008-06-23
> **Tycho Quad said:**
> 
EDIT: Another small feature request... Would it be possible to perform the gesture on the window under the point where the gesture started, rather than the window in focus?
Good catch, this was a bug. I hadn't noticed it since I use focus on enter.

The attached version might be a little unstable since I've just done some minor refactoring, but it does fix this specific issue :)

---

### Post by Tycho Quad on 2008-06-23
Tom, your my hero. Not a single update to strokeit in over 3 years, and here you are fulfilling mine hours after I make them!

Speaking of bugs, I think I've found another one. I can't get an alt-tab gesture to work with mouse buttons. Ultimately I'd like to have it work like my tab switching gesture, but that might be difficult as you have to hold down the alt and press the tab key many times before getting to the window you want

This would go above and beyond what strokeit did for me. I used another program called TaskSwitchXP to perform this action, but compiz is a much better looking solution.

---

### Post by Luffield on 2008-06-23
> **Tycho Quad said:**
> Tom, your my hero. Not a single update to strokeit in over 3 years, and here you are fulfilling mine hours after I make them!

Yeah, but easystroke is becoming bloatware lately. It's over 220KB now but it used to be under 135KB, it just ROCKED back then. I remember these times as if they were yesterday...

Seriously, though: easystroke is just brilliant and I think it's not too early to try to get it into the Ubuntu repositories. What's the procedure for this? Should the developers do it or can anyone do it?

---

### Post by geoken on 2008-06-23
Fantastic app.

---

### Post by reacocard on 2008-06-23
Sweet app! I compiled it under arch linux and it's working great. Only have a few actions bound right now but I'm sure I'll add more. :D

---

### Post by Tom Jaeger on 2008-06-23
> **Tycho Quad said:**
> 
Speaking of bugs, I think I've found another one. I can't get an alt-tab gesture to work with mouse buttons. Ultimately I'd like to have it work like my tab switching gesture, but that might be difficult as you have to hold down the alt and press the tab key many times before getting to the window you want

This one is harder than it sounds:  Keeping Alt pressed between clicks wouldn't be a too difficult (although I'm not doing it atm), the problem is somewhere else:  In order to show the alt-tab dialog compiz needs to grab the server, which fails since easystroke's button grab is still active (because there are still buttons pressed down).

I still have a trick up my sleeve, but it's a little risky:  Using Xtest to trick the server into thinking the buttons are actually up (which really isn't as big a deal as it seems) and then relying on Xinput to report to us the actual button up event.  If that fails (I'm mainly worried about hot-plugging here, which Xinput doesn't handle well) the user might be stuck with easystroke forever in alt-tab mode.
That said, I have a few ideas how to remedy the situation, but it'll take me a little bit longer to implement it this time.

---

### Post by Tom Jaeger on 2008-06-23
> **Tom Jaeger said:**
> If that fails (I'm mainly worried about hot-plugging here, which Xinput doesn't handle well) the user might be stuck with easystroke forever in alt-tab mode.
That said, I have a few ideas how to remedy the situation, but it'll take me a little bit longer to implement it this time.

Okay, this went faster than I expected:  The solution is to check if xinput is working correctly as opposed to checking if it is available (and just to be safe, I'll probably still make it possible to get out of there by pressing Esc).

I've attached the latest version, which enables alt-tab switching in compiz.  As always, it's highly experimental. (And I'm back to ~135kB again, forgot to strip the symbols last time...)

---

### Post by Tycho Quad on 2008-06-24
I've already made you my hero, haven't I? How about God then? My own personal Deity?

EDIT: Sorry, I think I've found another bug in relation to the new features. Whenever I perform a tab or window switching gesture, it performs it twice for the first one, however, every subsequent press in that same gesture only triggers it once like it should.

---

### Post by Tom Jaeger on 2008-06-26
> **Tycho Quad said:**
> 
EDIT: Sorry, I think I've found another bug in relation to the new features. Whenever I perform a tab or window switching gesture, it performs it twice for the first one, however, every subsequent press in that same gesture only triggers it once like it should.

I've reworked much of the event handling code and the problem you were describing should be fixed now.  There's also been a few user-visible changes, most notably the introduction of a 'button' action.  I have no idea how to call the checkbox that controls whether easystroke will care about the stroke leading up to advanced gestures, so it's called '???' for now.  Feature-wise, I think this is it for 0.1.3, but it needs a little bit more testing first since the implementation of the new features is quite complex.  The plan for 0.2.0 is to enable application-dependent behavior in an unobtrusive way via tags.

Oh, and one last thing: The configuration file format has changed in the development tree, which means that once you've switched to the attached version, you can't go back.  It's probably safest to backup the configuration directory first.

---

### Post by Luffield on 2008-06-29
Tom, on my machine the latest version is causing right-click to stop working altogether after a few minutes of use. I have to end the easystroke process to get the right button active again.
Can someone confirm this?

---

### Post by Tom Jaeger on 2008-06-30
> **Luffield said:**
> Tom, on my machine the latest version is causing right-click to stop working altogether after a few minutes of use. I have to end the easystroke process to get the right button active again.
Can someone confirm this?

Sorry, I haven't seen this problem before.  There've been some more changes to the event handling code lately, so I've attached the latest version, which might fix this, but it's a long shot.  I still need to make some changes to the code in order to be able to effectively debug issues like this.  This is going to have to wait a little bit since I'm severely jetlagged at the moment.

Edit: Attachment added

---

### Post by Luffield on 2008-06-30
No worries Tom.
I can tell that your jetlag is really severe by the fact that you forgot to attach the file :D
Anyway, take your time. I know it will be worth the wait.

---

### Post by Tom Jaeger on 2008-07-04
Luffield, sorry to keep you waiting so long, I've been busy with other things this week.  Anyway, I've reworked the event handling code once again and I'm attaching the lasted development version.  Since it should be more or less functionally equivalent to the last version I posted here, I'd expect your bug to still be present.  I'd greatly appreciate it if you could give this version a try and if you're still having the same issues, I'd be very interested in the last 10-20 lines of the output of "./easystroke -vv" before you start experiencing the problem.  It also might be helpful to know if the issue is present if xinput is disabled, that is if the program is invoked as "./easystroke -x".

Thank you,
Tom

---

### Post by pibach on 2008-07-05
Tom, thanks a lot for this little app! I have been looking for  long to find a proper replacement for StrokeIt. Investigated wavy, xstroke, chickenscratch and gestikk. The latter one seemed to be most suitable and it is nice but suffers from the problems you mentioned as it is not meant to be for tablet pen input but for regular mouse usage.

I had 3 minor issue I ran into using easystroke. First one is that I don't see easystroke as a menu entry (I am using Xubuntu on a ThinkPad x61t). So I cannot start it from the GUI but only from a terminal.
Secondly, I could not store gestures as the gesture file belongs to root, so I had to change file permissions. 
Thirdly, when I right click the easystroke taskbar icon, the context menu shows up at a little weird offset position. 

Of course these issues are minor and easystroke works great here. I have defined a couple of gestures including:

* minimize and close window
* cut, copy, paste
* delete, backspace, space, return
* forward, backward, new tab, close tab for Firefox
* launchers for cellwriter and some other tools

works great so far, accurate and lag free, and makes a whole different tablet experience

Now I am wondering whether it is possible to define a full blown xstroke/graffiti-like alphabet to input text? Anybody did that?

Other questions include:
* is it possible to share the gesture definition with other users? Or have a default gestures file included. This might be very helpful for all first-time users of gesture software and easystroke.
* is it possible to issue a right-click, Ctrl-Click, Shift click, Alt-click to the gesture starting position? This would be great (never succeeded in doing this with StrokeIt).

best regards,

Peter

---

### Post by Tom Jaeger on 2008-07-05
Thanks for you comments, Peter.

> **pibach said:**
> 
I had 3 minor issue I ran into using easystroke. First one is that I don't see easystroke as a menu entry (I am using Xubuntu on a ThinkPad x61t). So I cannot start it from the GUI but only from a terminal.

That seems easy enough, I'll be sure to include a proper .desktop file in the next release.
> 
Secondly, I could not store gestures as the gesture file belongs to root, so I had to change file permissions. 

I have no idea what's going on here. I'm using the standard C++ functions to open and write the config files, so they should get the default permissions.  Is this reproducible?
> 
Thirdly, when I right click the easystroke taskbar icon, the context menu shows up at a little weird offset position. 

Thanks, I hadn't even noticed that. Turned out to be trivial to fix.  Now it would be nice if GTK could be configured to always open menus a few pixels away from the mouse to avoid accidentally activating the first menu item.
[/QUOTE]

> 
Other questions include:
* is it possible to share the gesture definition with other users? Or have a default gestures file included. This might be very helpful for all first-time users of gesture software and easystroke.

I've thought about that but it's not quite clear to me what the right user interface would be.  One idea is to somehow use tags (which I will implement soon anyway to allow application-dependent behavior) in order not to clutter up the UI too much.  I'll get to it eventually, but it's not the highest priority right now.

> 
* is it possible to issue a right-click, Ctrl-Click, Shift click, Alt-click to the gesture starting position? This would be great (never succeeded in doing this with StrokeIt).

Emulating clicks is already possible in the development version, however, the click will originate at the position where the stroke ended.  This seems to be a limitation of XTest, which can't move the pointer and issue the click atomically, so 4 times out of 5, the tablet pen causes the mouse to move back before we get a chance to send the click.  It doesn't even seem to work well with a mouse.  I've tried to send the clicks directly to the active application via XSendEvent, but that didn't work either, presumably because gtk ignores fake button events.

---

### Post by Luffield on 2008-07-05
Thanks for the update Tom. I'm afraid it will be a few days before I'm able to test it - I have some problems with my ISP and I can't connect to the internet from Ubuntu at the moment. I'm not sure I'll be able to test the current version before you release the next one :)

---

### Post by pibach on 2008-07-05
Thanks, Tom again for the detailed answers.

I think I got the purpose of the "Matrix" feature: As long as there are no >70% similarities, you can define as many gestures as you like, with high correct recognition probability. So I'll going to try this for a full alphabet...

Still I have some issues:

* I am starting easystroke via autostart entry. But then x11 crashes when I do a gesture, everything freezes. To fix this I go to console (CTRL-ALT-F1) and do a killall easystroke.
But when I start easystroke from terminal it does not crash. Weird. But there I get the error : "XError: BadWindow (invalid Window parameter): request_code=20". Any hint?

---

### Post by pibach on 2008-07-05
I have defined a full alphabet. I am using it to write this post. Works well so far. My observations:

* works fine and convenient on left click. If I use it on right click it becomes cumbersome after a while. Solution could be either a) a gesture to switch the click options b) on/off toggle c) ingnore if gestures start on GUI elements (e.g. scrollbars). ritePen from evernote does these things pretty well on Windows.

* I cannot have a shift gesture, right? This might be helpful. Otherwise one needs to define a second set of upper case letters.

* when I write in the URL bar of Firefox, then the popup listbox steals focus. I have the same issue with xvkbd, so every key must be enterd twice, quite annoying. GOK (Gnome Onscreen Keyboard) somehow has solved this problem.

* the visual feedback in the taskbar icon does not help much. Would be better to visualize the *actual recognized prototype* there. And make it red if first and second recognition choices are too close or first choice is below threshold. I still get some wrong classifications.

* still it has some slight performance issues when you get going to write fast. Also the windows and panel get flickering.

---

### Post by Tom Jaeger on 2008-07-05
Gotta make this quick, I don't have much time.

> **pibach said:**
> Thanks, Tom again for the detailed answers.
* I am starting easystroke via autostart entry. But then x11 crashes when I do a gesture, everything freezes. To fix this I go to console (CTRL-ALT-F1) and do a killall easystroke.

I can't reproduce this one.  If you're using the latest development version, the output of "easystroke -vv" would be very helpful.  In the future you will just be able to press Esc to get everything back to normal, but that's not implemented yet.  In any case, this is a bug that should be fixed.
> 
But when I start easystroke from terminal it does not crash. Weird. But there I get the error : "XError: BadWindow (invalid Window parameter): request_code=20". Any hint?
Probably not a big deal, this usually means that a window disappeared right after you moved the mouse into it, so we get an error when easystroke queries the window.
[/QUOTE]

---

### Post by Tom Jaeger on 2008-07-05
> **pibach said:**
> I have defined a full alphabet. I am using it to write this post. Works well so far. My observations:

* works fine and convenient on left click. If I use it on right click it becomes cumbersome after a while. Solution could be either a) a gesture to switch the click options b) on/off toggle c) ingnore if gestures start on GUI elements (e.g. scrollbars). ritePen from evernote does these things pretty well on Windows.

I'll think about it.  Scrollbar detection will probably require a good amount of guess-work, I'm not sure how reliable that can be.  You're best bet right now are "Ignore" actions which will simply ignore the next stroke.

> 
* I cannot have a shift gesture, right? This might be helpful. Otherwise one needs to define a second set of upper case letters.

It should be pretty easy to rig something up with shell scripts and xte. I'll elaborate on that later.

> 
* when I write in the URL bar of Firefox, then the popup listbox steals focus. I have the same issue with xvkbd, so every key must be enterd twice, quite annoying. GOK (Gnome Onscreen Keyboard) somehow has solved this problem.

cellwriter has the same issue (and I actually have a patch that solves it that I need to send to the author sometime).  These programs have a much easier time working around this problem since their windows select on Button events and they will still receive the ButtonUp event.  easystroke uses a button grab, which won't get any events if it misses the Down event.  I need to explore whether I can use an Xinput workaround here, but that might just be too hacky - even for my taste.

> 
* the visual feedback in the taskbar icon does not help much. Would be better to visualize the *actual recognized prototype* there. And make it red if first and second recognition choices are too close or first choice is below threshold. I still get some wrong classifications.

I know, the recognition algorithm could definitely benefit from a complete redesign.  It's one of those things that will happen eventually, but probably not too soon.

> 
* still it has some slight performance issues when you get going to write fast. Also the windows and panel get flickering.
I think what you're seeing here are the delays I put in place to reduce flickering, which I believe is mostly a compiz issue.  It'd probably be a good idea to make these delays a little shorter - especially since they don't eliminate flickering completely anyway.  Eventually, I'd like to draw the strokes using a more modern extension like XRender (or whatever it is that compiz' annotate plugin is using, but once again, this is kind of low priority.

---

### Post by pibach on 2008-07-06
Tom, I highly appreciate that you take this much time to answer everything in that detail. 

I agree that the above issues are low priority as easystroke works fine. It makes my tablet a lot more usable. This little tool has the potential to become a killer app for all tablet users. What is required most is only a bit of promotion and some more specific use-case advices. BTW: [here]("http://think-wiki.org/index.php?title=TabletBuntu") I am collection everything for a "TabletBuntu" Edition together with some friends from the ThinkPad Community (in German).

Some more thoughts:

* is there a good way to define macros (as ritePen 3.0 does)? For example "wkr" Gesture Stroke should expand to "with kind regards". Would you do this by a sendevent command?

Edit: I did define some macros successfully using xte command plus str option. In the above example just place in the command field: xte "str with kind regards". Works great!

Edit2: Regarding flickering: I am not using compiz but XFCE without compositing. When I switch on the built in composition, flickering is gone! (Unfortunately, I get the old scroll performance problems on complex Web pages again then)

Edit3: 
* Regarding the crash I could pinpoint it: it occurs if I do a gesture associated to launch xvkbd. This allway crashes. Another gesture launching cellwriter only crashes from time to time. All other gestures I have defined work fine.

* regarding the activation button: what about when placing the cursor into an input field, then around this cursor position all strokes activate on left click? This would be similar to MacOS inking.

---

### Post by Tom Jaeger on 2008-07-07
> **pibach said:**
> BTW: [here]("http://think-wiki.org/index.php?title=TabletBuntu") I am collection everything for a "TabletBuntu" Edition together with some friends from the ThinkPad Community (in German).

This is great.  I have an x61t, too.

> 
Edit: I did define some macros successfully using xte command plus str option. In the above example just place in the command field: xte "str with kind regards". Works great!

Seems like good way of accomplishing this sort of thing.  I'll mention it in the documentation.  As for defining actions consisting of multiple strokes, I might introduce a simple state-based model (since we will need a concept of state for application-dependent gestures anyway), but I somehow resist the idea of introducing full-fleged scripting capabilities.

> 
Edit2: Regarding flickering: I am not using compiz but XFCE without compositing. When I switch on the built in composition, flickering is gone! (Unfortunately, I get the old scroll performance problems on complex Web pages again then)

That's odd, I'm don't see flickering in metacity.
The 'Standard' setting in Preferences/Appearance/Method... might work better for you, but it will prevent screen updates until the gesture is over.

> 
Edit3: 
* Regarding the crash I could pinpoint it: it occurs if I do a gesture associated to launch xvkbd. This allway crashes. Another gesture launching cellwriter only crashes from time to time. All other gestures I have defined work fine.

Fixed.  These weren't really crashes, I previously used the system() call, which would wait for the application to finish before continuing.  Of course you can easily walk around this by appending '&' to your command if you don't want to switch to the development version.

> 
* regarding the activation button: what about when placing the cursor into an input field, then around this cursor position all strokes activate on left click? This would be similar to MacOS inking.
This is a great idea and I shouldn't give up on it too early, but it might not be possible: The X server is not aware of what widgets windows consist of, so there's no way to tell where the text input fields are.

EDIT: It looks like I might be able to abuse the XDND drag and drop protocol, which is based around the idea that the source application must grab the server in order track the pointer outside its window and in order to change the pointer, so the target application can't get any mouse events and has to rely on the source to provide it with the necessary information.  X is a mess.

As for defining a "shift gesture" that causes the next character to be upper case, I would associate the command "touch /tmp/shift" with the shift gesture and then use the command "/path/to/key ..." to press the keys where key is the following shell script (untested):
```

#!/bin/bash
if [ -f /tmp/shift ]
then
  xte "keydown Shift_L" "key $1" "keyup Shift_L"
  rm -f /tmp/shift
else
  xte "key $1"
fi

```

> when I write in the URL bar of Firefox, then the popup listbox steals focus.
Okay, I've taken the plunge and allowed gestures to be initiated as long as we are receiving XInput events.  This seems to work better than I expected, but the fundamental problem remains:  If the server is grabbed (usually because an app is showing a menu), the app will still receive the click event.

I've attached another snapshot.  Again, there've been lots of changes under the hood.  If easystoke is acting weird, you should be able to fix things by pressing escape now (but unfortunately, that means that gestures sending an Escape key will not work for the time being).

---

### Post by pibach on 2008-07-07
Great! I can confirm that with new snapshot:

* Focus issue: I can enter gestures. But as you explained, app receives the click. But when I write on an area that does not do anything on the click it works fine. In my case I use easystroke on right click, and Firefox URL list do not react on right click. So as long as I start gesturing within the popup list, there is no interference. Working. if you use left click for easystroke  it conflicts with grab&drag scrolling. If you disable that, it steals focus...

* "crash": fixed, I can invoke xvkbd. Working.

* flickering: still get flickering on "standard" mode, but that seems to be normal (?). When I choose Xshape it works fine without flickering. Still there seems to be sligth performance issues, as when I do gestures very fast, first part sometimes is not correctly drawn and recognised.

As easystroke works so nicely I experiment using it on left click and did define a "pause" gesture (should be explained in the Documentation as this is very important!). But for more convenient working on left click without interference I have the following idea:

* If you start gesturing and do not move the pen for a threshold (e.g. 500milliseconds, 5 pixels), then ignore gesture mode and transmit input to the underlaying window. This way when you do a scrollbar slide, a drag&grad scroll slide, or some text selection slide, for example, you only get some short delay but can go ahead afterwards.

* nevertheless there should be an easy way to change button option. Then you could switch to right button by a gesture (or by window context in future versions, e.g., no left click gestures over cellwriter). Also there should be a "deactivate" checkbox that can be automatically chosen (by a script) if changing back to laptop mode. To reactivate, one could tab the taskbar icon (and have options on right click menu).

Tom, what do you think about these ideas?

* another nice thing would be to place cellwriter, which I invoke by a geture, nearby the current cursor position (similar as Vista does with the TIP). Is there a way to do this?

---

### Post by Tom Jaeger on 2008-07-07
Thanks, Peter, your feedback is very helpful and your ideas are great.

> **pibach said:**
> Great! I can confirm that with new snapshot:
* flickering: still get flickering on "standard" mode, but that seems to be normal (?). When I choose Xshape it works fine without flickering. Still there seems to be sligth performance issues, as when I do gestures very fast, first part sometimes is not correctly drawn and recognised.

Yes, the first part of strokes is not drawn correctly... Totally forgot about that.  It should be easy enough to fix, after all, all the necessary information is already there.  Both methods have severe drawbacks (XShape's high CPU consumption, for example) and ultimately need to be replaced by something more modern.

> 
* If you start gesturing and do not move the pen for a threshold (e.g. 500milliseconds, 5 pixels), then ignore gesture mode and transmit input to the underlaying window. This way when you do a scrollbar slide, a drag&grad scroll slide, or some text selection slide, for example, you only get some short delay but can go ahead afterwards.

Great idea, especially for devices that only have one "button" such as passive digitizers/touch screens. It shouldn't be too hard since we can have the X server do most of the work for us here.  It requires just a little bit more bookkeeping...
This is definitely 0.1.3 material.  Most of the rest will have to wait for 0.2.x.

For a tablet pen, it'll probably be more convenient to assign a left click to the left-click - middle-click sequence -- another hidden feature.  To set this up, just define a gesture where you first do a left click and then press the side switch while the pen is still on the tablet and then assign the action Button/Button1 to it.

> 
* nevertheless there should be an easy way to change button option. Then you could switch to right button by a gesture (or by window context in future versions, e.g., no left click gestures over cellwriter).

I agree, the hard part here is getting the UI right.  I'll need to think about it a little more.

> 
Also there should be a "deactivate" checkbox that can be automatically chosen (by a script) if changing back to laptop mode. To reactivate, one could tab the taskbar icon (and have options on right click menu).

Deaktivate is something I've been meaning to implement for a while now.  But I'll put it in the menu -- apps that violate the unspoken rule that a left-click on a tray icon should open a window always drive me nuts.

> 
* another nice thing would be to place cellwriter, which I invoke by a geture, nearby the current cursor position (similar as Vista does with the TIP). Is there a way to do this?

I investigated this at some point.  Of course it must be done in cellwriter -- if I remember correctly, cellwriter already has a fifo that it is listening to - so it shouldn't be too intrusive a patch.


The plan is to implement the things that are relatively simple now and then get some more testing done before the release of 0.1.3.  And target all the features that require state in one form or another for 0.2.x

---

### Post by pibach on 2008-07-08
> **Tom Jaeger said:**
> 
For a tablet pen, it'll probably be more convenient to assign a left click to the left-click - middle-click sequence -- another hidden feature. 
Sounds great. But how do you use this feature exactly? Did you redefine the normal left click to be always a right click (invoking easystroke directly), and then get the left click by doing the above?
I think we should record a video to explain the best usage scenarios as it get quite abstract/complex here...

> But I'll put it in the menu -- apps that violate the unspoken rule that a left-click on a tray icon should open a window always drive me nuts.
Hm. This might take too long. A very quick activation is important! Deactivation then can be done by a gesture.

> 
I investigated this at some point.  Of course it must be done in cellwriter -- if I remember correctly, cellwriter already has a fifo that it is listening to - so it shouldn't be too intrusive a patch.
Isn't there something simpler and more generic, e.g., send a move window x,y event to the window manager?

---

### Post by Tom Jaeger on 2008-07-09
> **pibach said:**
> Sounds great. But how do you use this feature exactly? Did you redefine the normal left click to be always a right click (invoking easystroke directly), and then get the left click by doing the above?

No, the normal left click is still a left click, it's only when you press two buttons at the same time that advanced gestures kick in.

> 
Hm. This might take too long. A very quick activation is important! Deactivation then can be done by a gesture.

I can't say that I understand the use case, but I'd suggest using a tablet button then.  Easystroke being activated and deactivated seemingly at random because someone clicked on the tray icon might easily confuse users.

> 
Isn't there something simpler and more generic, e.g., send a move window x,y event to the window manager?
Moving the window isn't a big deal at all if the window is already there, but I don't see how I would make the cellwriter window appear in the first place.

A new snapshot is attached.  I've implemented the abort-the-stroke-if-the-mouse-isn't-moved feature, which it turns out requires Xinput.  I also added a workaround for clicks registering twice when the server is grabbed, but I've decided that the whole accepting gestures when a menu is shown thing is too quirky and confusing, so it has to explicitely be enabled in the preferences now.  In order to solve the problem that clicks on the taskbar steal focus if the gesture button is Button1, I'm now using NET_WM to transfer focus to the app that the user clicked on (EDIT: I'm using yet another method now and I've removed the option again).  The problem is that some window managers do stupid things if they are told to activate a window (compiz, but not metacity raises the window in addition to giving it focus even if there is no Raise-On-Click policy), so I've added an option to disable giving the focus to the application where a stroke originates.

---

### Post by pibach on 2008-07-09
Tom, I am going to test new version asap.

In the mean time I stumbled over some things:

* Ubuntu MID: this seems to have "Finger Gestures". Any information on how this works?

* Tilt detection: on Wacom digitizers you can query the pen tilt. Might be an option for gestures. See this [Nokia Paper]("http://whitepapers.silicon.com/0,39024759,60317849p,00.htm").

* I also have a Nokia n81O. Do you think easystroke will be suitable for that device?

---

### Post by Tom Jaeger on 2008-07-09
> **pibach said:**
> 
* Ubuntu MID: this seems to have "Finger Gestures". Any information on how this works?

From looking at youtube videos, it appears to be similar to Vista's flick gestures.  But their apps have custom UIs anyway, so this is not directly comparable.

> 
* Tilt detection: on Wacom digitizers you can query the pen tilt. Might be an option for gestures. See this .
[Direct link to the Paper]("http://research.nokia.com/files/Tilt%20MenuCHI2008.pdf")
Unfortunately, we don't get tilt information on Tablet PCs (though they might have it on the more expensive wacom tablets).  The only additional information that we can get through xinput is pressure and proximity (i.e. whether the pen or eraser is "in range").  I've thought about whether we can make use of this information, but I haven't come up with anything good.  Maybe a "proximity click", i.e. moving the pen quickly in and out of the range, but that's not very impressive.

---

### Post by Tom Jaeger on 2008-07-10
Here's an idea for pressure: Abort the gesture and pass the click to the application when high pressure is exerted on the pen.
The attached version is identical to the one above, except that strokes are aborted if pressure exceeds 192 (out of 255).  Works pretty well, I think, though it might need a configuration option, since people's pens and writing habits are different.

---

### Post by pibach on 2008-07-10
pressure sensitive stroke abortion works great! Good idea. Alsoabort-the-stroke-if-the-mouse-isn't-moved feature works nicely!  

Now I prefers easystrke on left click. Then, biggest problem ist that over cellwriter, xournal and gimp easystroke should change to work on right click.

Tom> "so I've added an option to disable giving the focus to the application where a stroke originates"

I cannot reproduce this here. Does not work on left click.

with these improvements easystroke became my most most important tabet tool. I'll test it on my n810 soon...

---

### Post by pibach on 2008-07-10
pressure sensitive stroke abortion works great! Good idea. Also abort-the-stroke-if-the-mouse-isn't-moved feature works nicely!  

Now I would prefers easystroke on left click. Then, biggest problem is that over cellwriter, xournal and gimp easystroke should change to work on right click.
Edit: is the 'add exeption' option in the experimental mode intended for this?

Tom> "so I've added an option to disable giving the focus to the application where a stroke originates"

I cannot reproduce this here. Does not work on left click. Firefox continues to steal focus (when I am on left click in easystroke).

Edit: Accuracy issues at gesture begning seem to be fixed. Also xshape visualisation works fine for me, no flickering.

With these improvements easystroke became my most most important tabet tool. I'll test it on my n810 soon...

---

### Post by Tom Jaeger on 2008-07-11
> **pibach said:**
> 
Now I would prefers easystroke on left click. Then, biggest problem is that over cellwriter, xournal and gimp easystroke should change to work on right click.

I'll start working on that once 0.1.3 is released (or maybe I'll call it 0.2.0).  Until then, as you said, adding those applications to the exception list (not experimental, btw) will at least give you your left button back, but gestures won't work in those windows.

> 
I cannot reproduce this here. Does not work on left click. Firefox continues to steal focus (when I am on left click in easystroke).

Hmm, are you sure you set the "Accept gestures when menus are shown" option?

I had another idea why the advanced gestures feature is not working for you.  It only works if the wacom driver's [TPCButton]("http://easystroke.wiki.sourceforge.net/TipsAndTricks") option is enabled.  Speaking of advanced gestures, I've just implemented a (pretty insane) workaround for the problem with the ordering of two button events coming in at the same time, so it won't be necessary to patch the wacom driver anymore to take full advantage of advanced gestures.

---

### Post by pibach on 2008-07-11
> **Tom Jaeger said:**
> I'll start working on that once 0.1.3 is released (or maybe I'll call it 0.2.0).  Until then, as you said, adding those applications to the exception list (not experimental, btw) will at least give you your left button back, but gestures won't work in those windows.

How do I add ecxeptions (I did not succeed doing that). I did not find anything in the documentation.

> 
Hmm, are you sure you set the "Accept gestures when menus are shown" option?

yes. I did enable this. Still when I am on left click in easystroke, Firefox kicks in and I cannot continue writing with easystroke in the URL bar. 

> 
I had another idea why the advanced gestures feature is not working for you.  It only works if the wacom driver's [TPCButton]("http://easystroke.wiki.sourceforge.net/TipsAndTricks") option is enabled.  
I have been playing with TPCButton option. This hoovering is nice if you place gestures on left click. 

Regarding advanced gestures I have to admit that I did not understand the documentation about using that for alt-tab-sitching with a pen.

---

### Post by Tom Jaeger on 2008-07-11
> **pibach said:**
> How do I add ecxeptions (I did not succeed doing that). I did not find anything in the documentation.

Just click on "Add Exception" and then on a window belonging to the application that you want to exclude.

> 
yes. I did enable this. Still when I am on left click in easystroke, Firefox kicks in and I cannot continue writing with easystroke in the URL bar. 

Weird. This works here. Maybe there's some WM interaction.  What' the name of the window manager that are you using?  The output of ./easystroke -vv might also be helpful.

> Regarding advanced gestures I have to admit that I did not understand the documentation about using that for alt-tab-sitching with a pen.
That was an example of what you can do with the scroll wheel of a mouse.  But you can do the same thing with the pen: Draw the gesture and then hold down "the other" button.

Attaching the latest snapshot.  We're getting closer to a release now, I hope.

---

### Post by Tycho Quad on 2008-07-12
You have don excellent work with easystroke Tom, I've never before met a developer who is so willing to listen to what people want out of a program, as well as being so quick to implement said features. You have already nailed what I want out of this program, and I look forward to seeing what comes in the future, features that I never would have thought of.

---

### Post by pibach on 2008-07-12
> **Tom Jaeger said:**
> Just click on "Add Exception" and then on a window belonging to the application that you want to exclude.

Ok, this works in Gnome. But I am using XFCE (Windowmanager ist Xfwm4).

The main reason why I choose XFCE is its superior GUI performance. Might result from my SXGA+ resolution. I get unbearable slow scrolling, e.g., in Firefox, when I am running Gnome. I tested with or without Compiz. Without it is a lot faster, but still Xfwm4 apparently renders a lot faster than Metacity or the KDE window managers do. Don't know why, but apparently here are still severe performance bugs in xorg 7.2 plus Intel drivers and font rendering. I also investigated some options (Exa versus XAA acceleration, Intel batch). No solution yet. Do you know of any? See also [http://www.cworth.org/talks/lca_2008/](http://www.cworth.org/talks/lca_2008/)

---

### Post by Tom Jaeger on 2008-07-12
> **pibach said:**
> I get unbearable slow scrolling, e.g., in Firefox, when I am running Gnome. I tested with or without Compiz. Without it is a lot faster, but still Xfwm4 apparently renders a lot faster than Metacity or the KDE window managers do.

There's something fishy here. I'm not seeing this kind of slowness in compiz.  Sure, it's a little less smooth than on vista, and xfwm might be slightly better, but it's nowhere near unbearable.  I'll attach my xorg.conf

As for the exception problem, I can reproduce this with xfwm, so expect a solution soon.  The weird part is that xprop is working fine with xfwm and I thought I ripped the window picking code from the same codebase.

---

### Post by pibach on 2008-07-12
Tom, do you have the SXGA+ resolution? Do you use antialiasing (subpixel hinting)? Do you use Firefox smooth scrolling (pixel wise scrolling)? Then you should see the same sluggish scrolling performance on complex web pages (all other GUI things perform well, it is only a font rendering issue in combination with high resolution and antialiazing). Whether to call it "unbearable" or "tolerable" might be a matter of taste though. BTW: XFCE without compositing is surely more responsive than Windows.

---

### Post by Tom Jaeger on 2008-07-12
I do have the high-resolution display and I am using subpixel smoothing.  There is a slight slowdown in compiz compared with, say xfwm, but it's barely noticeable in practice.  It's not like in the hardy betas where they enabled EXA without enabling greedy migration heuristics.

I've fixed exceptions by moving over to the latest dsimple.c code, apparently I was using an older version.

---

### Post by Tom Jaeger on 2008-07-12
Tycho Quad, thanks, this would never be possible without the high-quality feedback I'm getting in this forum.

---

### Post by pibach on 2008-07-12
> **Tom Jaeger said:**
> I've fixed exceptions by moving over to the latest dsimple.c code, apparently I was using an older version.

Working here on XFCE!

Is is incredible how fast you are implementing these changes and fixes. Thanks a lot!

Regarding sluggish scroll: Yes, this "greedy migration heuristics" improved my performance a 40%. Still there seem to be font rendering issues (see the link I posted above). It might also be related to Java Script/Flash implementation in Firefox as I do measure higher CPU load on some Web pages in Firefox compared to Opera for example. There are pages where scrolling almost freezes if I enable compositing.

Edit: BTW, why is you post count showing "0 posts"??

---

### Post by pibach on 2008-07-12
Tom, I did some usability test with newest snapshot. And it mostly works fine for me, when I keep easystroke on right click. Biggest issue so far is that I have to enter strokes over list boxes such that the window does not accidentially act on the right click. Only for writing longer with my Graffiti-like strokes holding the right button gets a bit cumbersome. Not a big thing as I usually activate cellwriter for that by a quick easystroke gesture. But cellwriter has some other usability issues and I am wondering how one could best combine the benefits of both tools.

When I change to have easystroke on left click, I loose the grab&drag scroll feature in Firefox. Also I used to open links in new tabs by engaging Quickdrag extension. As you usually do this in a lets say 10:3:1 ratio (scroll:quickdrag link:gesture) you would like to keep scroll&quickdrag on left button in this use case. Also it is a little bit counter intuitive that you cannot slide GUI elements, such as the scrollbar oder the window titlebar. 

Moreover it would be nice if easystroke scroll option could serve as a general scroll method similar to g&d scrolling in Firefox but application independent. Currently the scroll option is nice, but too cumbersome (one issue is that it requires re-activation for every scroll). Maybe you could add a scroll mode to easystroke that is activated on a specific button.

Threfore, the GUI could have an additional "scroll button" to be selected beneath the "gesture button". Ideally the button assignment is application specific so you would need two button parameters for the "exceptions" list that indicate the different assignment. Thus, for each item in that list you'll have an individual gesture button and scroll button different to the default setting. Setting both buttons to "none" would completely disable easystroke then for this application.

And finally a specific gesture then could switch between the two button assignments that are currently active. This could be solved in the easystroke GUI by an additional "switch buttons" action type. These modes should be visualised by the task bar icon.

What do you think about that?

---

### Post by pibach on 2008-07-12
Sluggish scroll in Firefox:
I again tested Firefox versus Opera and it seems to be a more Firefox/xorg related issue. Try for example scrolling this long Webpage: [http://forum.notebookreview.com/showthread.php?t=144783](http://forum.notebookreview.com/showthread.php?t=144783)
which lets my Firefox almost freeze. Opera does scroll it without problems. If you look at process TOP, you can see that most load goes to xorg, indicating some issue between FF, xorg and Intel drivers, probably. Here is also some related info in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/177492").

---

### Post by Melodic_BM on 2008-07-12
I cannot make easystroke. It's telling me that there aren't enough parameters for "XFreeCursor".

---

### Post by Islington on 2008-07-12
Tom: I Love You.

This tool is amazing( written on a tablet comp)

---

### Post by pibach on 2008-07-13
> **pibach said:**
> Sluggish scroll in Firefox
This is off topic but I wanted to tell that I found out the problem of the sluggish scrolling after deeper investigation: If you set mousewheel.withnokey.numlines to 1 (for smother scrolling), engage full page zoom and also enable smooth scrolling, then there are more TrackPoint events generated than Firefox/xorg can handle on time. This results in buffer overload and permanent pre-emption of processes which freezes the scrolling. According to my testing this also happens on Windows and other programs including Opera. Anyway, there additionally seem to be Intel driver issues as load is too high for this kind of 2D operation. But seemingly Windows drivers suffer from exactly the same problem.

---

### Post by Tom Jaeger on 2008-07-14
> **pibach said:**
> 
Moreover it would be nice if easystroke scroll option could serve as a general scroll method similar to g&d scrolling in Firefox but application independent. Currently the scroll option is nice, but too cumbersome (one issue is that it requires re-activation for every scroll). Maybe you could add a scroll mode to easystroke that is activated on a specific button.

This is not a bad idea.  Would be a good use for the eraser.  The way I see it, this requires two things: (1) support for multiple gesture buttons and (2) allowing some of them to fire on button press instead of button release. (2) is essentially trivial, but (1) is more complicated than it might seem.  The backend code has recently been moving in the direction of (1) for unrelated reasons, so I should eventually get around to implementing this.

Until then, you can get very similar functionality by assigning 'scroll' to the Button1 advanced gesture (without motion).  But be sure to use the attached snapshot, advanced-gesture scroll was pretty unreliable with the last one.

> Ideally the button assignment is application specific so you would need two button parameters for the "exceptions" list that indicate the different assignment.

The plan is to make easystroke's behavior dependent on some sort of state that incorporates the current application and a user-definable element, so all of this will be possible.  This idea is appealing because we'll be able to use essentially the same user interface for actions and preferences.  I haven't figured out the details yet, but it's going to be sweet.

> 
If you set mousewheel.withnokey.numlines to 1 (for smother scrolling), engage full page zoom and also enable smooth scrolling, then there are more TrackPoint events generated than Firefox/xorg can handle on time.

Ah, that explains it.  I have disabled smooth scrolling and I don't usually use the track point to scroll in firefox.  But you're right, scrolling under those circumstances is annoying.

---

### Post by Tom Jaeger on 2008-07-14
> **Melodic_BM said:**
> I cannot make easystroke. It's telling me that there aren't enough parameters for "XFreeCursor".

Sorry about that.  I don't always compile before checking stuff in.  It should work now.  If this should happens again, you should be able to fix it by 'darcs unpull'ing the last patch.

---

### Post by pibach on 2008-07-14
> **Tom Jaeger said:**
> This is not a bad idea.  Would be a good use for the eraser.  

The eraser button is hardly usable on our ThinkPads. Therefore best might be to activate scroll mode on right click (i.e., hovering, without left click) and then moving up/down/left/right. Also the scroll behavior ideally could be a bit different to current scroll, by having a speed up the further the pen is moved away from originating position.

> 
The plan is to make easystroke's behavior dependent on some sort of state that incorporates the current application and a user-definable element, so all of this will be possible.  This idea is appealing because we'll be able to use essentially the same user interface for actions and preferences.  I haven't figured out the details yet, but it's going to be sweet.

sounds great! Looking forward for this.

Any news about (auto-) disabling easystroke on Laptop Mode?

---

### Post by Islington on 2008-07-14
is there a way to launch cellwriter & another program at the same time? :confused:

Alt+F2 dialog is pretty useless without cell writer also being present...

---

### Post by Tom Jaeger on 2008-07-14
> **Islington said:**
> is there a way to launch cellwriter & another program at the same time? :confused:
Commands are passed to the shell, so "app1; app2" (without quotes) will execute the two apps sequentially and "app1 & app2" will execute them at the same time.

So this is the command that you'd use to start cellwriter and open the Alt+F2 dialog:
```
cellwriter --show-window & xte 'keydown Alt_L' 'key F2' 'keyup Alt_L'
```

---

### Post by Tom Jaeger on 2008-07-14
> **pibach said:**
> The eraser button is hardly usable on our ThinkPads. Therefore best might be to activate scroll mode on right click (without left click) and then moving up/down/left/right.

How is this better than what is currently possible: have gestures be bound to right click and activate scroll mode by an additional left click? (Try it out, it works really well now)
> 
Also the sroll behavior ideally could be a bit different to current scroll, by having a speed up the further the pen is moved away from originating position.

Yup, the scrolling algorithm could use some improvements.  I was thinking of something along the lines of
```

scroll speed = const * mouse speed ^ c

```
where c is some suitable exponent between 1 and 2.

Is horizontal scrolling something we need?  Obviously, it wouldn't be very hard to implement, but I would imagine that it could be annoying to accidentally trigger it.  At the very least, I think horizontal scrolling should be less sensitive than vertical scrolling.

> 
Any news about (auto-) disabling easystroke on Laptop Mode?
The natural thing to do would be to have a fifo that you can write to in order to change easystroke's "state", then you could disable it via a script or a gesture and enable it using a launcher.

---

### Post by Islington on 2008-07-14
> **Tom Jaeger said:**
> Commands are passed to the shell, so "app1; app2" (without quotes) will execute the two apps sequentially and "app1 & app2" will execute them at the same time.

So this is the command that you'd use to start cellwriter and open the Alt+F2 dialog:
```
cellwriter --show-window & xte 'keydown Alt_L' 'key F2' 'keyup Alt_L'
```

terrific. I never knew about xte.

---

### Post by pibach on 2008-07-14
> **Tom Jaeger said:**
> How is this better than what is currently possible: have gestures be bound to right click and activate scroll mode by an additional left click? (Try it out, it works really well now)

Yes, you're right, works quite good with new snapshot. Right click+left click to activate scrolling is fine (but don't you think a hovering right click wouldn't be better?). And the new formula with some "accelerating factor" as you suggest should help to better hit targets (while background is scrolling). Would be nice if therefore scrolling could be as smooth as possible, i.e., pixel-wise scrolling (as the scrollbar or G&D scroll extension does). But I guess this might no be easily possible (?). Might  also be reasonable to send the deactivation click already to the application?

> Is horizontal scrolling something we need?

I don't see this to be on high priority. But there are definitely apps that will benefit from horizontal scrolling. So ideally this option (+sensitivity) would be context specific

BTW: did you contact the accessibility developers? They might be interested to include easystroke into the upsteam.

---

### Post by Islington on 2008-07-14
On the note of (auto-) disabling easystroke. The program crashes whenever I rotate my screen. I am using a Tablet X41 and the rotation scripts that I am using were found here [link.]("http://liken.otsoa.net/blog/index.php?entry=entry080617-120522")

Running it through terminal I get:
```
islington@Mu:~$ easystroke 
XError: BadWindow (invalid Window parameter): request_code=20
XError: BadWindow (invalid Window parameter): request_code=20
XError: BadWindow (invalid Window parameter): request_code=20
islington@Mu:~$ 

```

---

### Post by Melodic_BM on 2008-07-15
Damn:  undefined reference to `gui_buffer'
Now - there are packages... I could've seen this earlier. -.-

---

### Post by Tom Jaeger on 2008-07-15
> **Melodic_BM said:**
> Damn:  undefined reference to `gui_buffer'

Fixed.

---

### Post by Tom Jaeger on 2008-07-15
> **Islington said:**
> On the note of (auto-) disabling easystroke. The program crashes whenever I rotate my screen. [...]

Running it through terminal I get:
```
islington@Mu:~$ easystroke 
XError: BadWindow (invalid Window parameter): request_code=20
XError: BadWindow (invalid Window parameter): request_code=20
XError: BadWindow (invalid Window parameter): request_code=20
islington@Mu:~$ 

```

Really strange.  This does not look like a crash, it seems easystroke exited cleanly.  (The XError things don't mean anything, I filter most of them out in the development version now).  I can't reproduce this issue,  but I once had a possibly related problem where easystroke would receive spurious WM_DELETE messages and then dutifully shut down.  Rather than try and find the cause of this (it's a really, really strange problem, and could be related to easystroke opening two connections to the X server), I just decided to ignore WM_DELETE.

So the issue might be fixed in the development builds that are attached to some of my posts, if you want to try that out.  But be sure to back up your .easystroke directory first:  Your actions and prefs will migrate to the new version just fine, but they will be overwritten and you won't be able to go back to the earlier version (most likely it'll just crash).  This is a limitation of the boost::serialization library that I use for storage.

---

### Post by Tom Jaeger on 2008-07-15
> **pibach said:**
> Yes, you're right, works quite good with new snapshot. Right click+left click to activate scrolling is fine (but don't you think a hovering right click wouldn't be better?).

Personally, I don't, but if we enable actions to be triggered by a single button press, then we might as well do something useful if an additional button is held down.  It seems kind of complex, though, so I need to be sure that it's worth the trouble.

> 
Would be nice if therefore scrolling could be as smooth as possible, i.e., pixel-wise scrolling (as the scrollbar or G&D scroll extension does). But I guess this might no be easily possible (?).

I'm afraid not.  Scroll wheel events are dumb button presses and apps translate them into a fixed scroll amount.  This amount might be configurable for gtk apps, but that's about it.

> 
 Might  also be reasonable to send the deactivation click already to the application?

I don't understand.

> 
BTW: did you contact the accessibility developers? They might be interested to include easystroke into the upsteam.
The thing about accessibility is that enabling it breaks a few applications and easystroke is one of them:  Accessibility is causing deadlocks, even though it uses gtk's own locking operations.  This looks like a problem with the atk implementation. [Note to self: Mention this in the docs]

EDIT: I have fixed this now.  It turns out that gtk+accessibility doesn't like it at all if its main loop is not run in the main thread.  Weird.  They don't mention any of this in the [GTK+ FAQ]("http://library.gnome.org/devel/gtk-faq/stable/x500.html")

So I've changed the scrolling algorithm as previously indicated (with c = 4/3), and it basically works fine, except for the problems with fast scroll speeds that you mentioned earlier, which become really prominent here.  Interestingly enough, this fails in different ways depending on whether compositing is enabled or not: In compiz, motion events that the driver can't handle are simply dropped and in metacity/xfwm4, they are queued and the computer becomes unresponsive after scrolling.  But I blame the toolkits, they should be able to cope with slow drivers.

---

### Post by pibach on 2008-07-18
> **Tom Jaeger said:**
> Personally, I don't, but if we enable actions to be triggered by a single button press, then we might as well do something useful if an additional button is held down.  It seems kind of complex, though, so I need to be sure that it's worth the trouble.
Currently I run easystroke on left click. And enter scroll mode on a simple gesture, this is the gesture I use most of course. It works fine, but still, requires to bring down the pen, do the gesture, lift the pen again, do the scrolling, then deactivate scrolling by bringing the pen back down. Then you need to lift it up again before you can select, for example, a link in the browser. This works, but it is not particularly convenient. The combination of Grab&Drag Scroll plus FireGestures is more convenient, in comparison, but of course does not work OS-wide and application independent. Anyway, a simple and quick way to distinguish gestures from scrolling strokes is very important. The Vista solution to this is to check for 'flick' gestures, where the pen is been lifted after th egesture. But this is resource consuming as it requires permanent tracking of pen movement and it induces some lag. I don't know the best way, but to distinguish scroll from gesture mode would be a possible solution. And from user perspective, a hoovering right click might be the fastest and easiest to do mode switching. For ressistive touch a quick tab on a non-GUI element might be another good option.

> 
I'm afraid not.  Scroll wheel events are dumb button presses and apps translate them into a fixed scroll amount.  This amount might be configurable for gtk apps, but that's about it.
That's what I've expected. Maybe one could lower the system wide scroll parameter in tablet mode? When I set numlines parmeter in about:config to 1 (instead of the default 3 lines scrolling) it is much smoother - but might lead to the mentioned event-overload problem.

> 
I don't understand.

The problem I see is that scrolling in hoovering mode is too sensitive to directly hit a target (e.g., click-open a link). Probably you could add to your formula an offset parameter. Then, in some range the movement of the pen would not result in scroll, but only if you exceed certain range (e.g. 15mm might be reasonable, best range will need some testing). Within this reach you can precisely hit targets or even do some gesturing (without resulting in a scroll). Then, scroll mode could probably remain permanently active, if these clicks are trasmitted to the app. This might eliminate the need for frequently activating/deactivating scroll mode. 

Edit: I gues "offset parameter" is not possible as you cannot remember originating koordinates of a gesture, right? Then probably exponential acceleration in the scroll formula instead of polinomial might be the way to go? Or could you incorporate the *speed* the pen is moving? And when you end at the border of some scroll area, is there a way to do some continious scroll? Because otherwise you would need to lift pen up an down multiple times to reissue scrolling.

Youst some thoughts, some might be useful. What do you think?

BTW: I switched from Firefox to Epiphany as this browser is more lightweight an does not suffer from the flush()/SQLlight bug that all the time spins up HDD. This way I can surf the web for hours without any HDD activity. And easystroke allows me to conveniently scroll or open links in new tabs by just a gesture. Works great.

> 
So I've changed the scrolling algorithm as previously indicated (with c = 4/3), and it basically works fine.

yes, works fine, huge improvement. 

> 
This is a great feature except for the problems with fast scroll speeds that you mentioned earlier, which become really prominent here.  Interestingly enough, this fails in different ways depending on whether compositing is enabled or not: In compiz, motion events that the driver can't handle are simply dropped and in metacity/xfwm4, they are queued and the computer becomes unresponsive after scrolling.  But I blame the toolkits, they should be able to cope with slow drivers.
Interesting. I think EXA acceleration is part of the problem. As far as I know it obtains only 60% the performance regarding font rendering compared to XAA acceleration. There might be some settings to get this faster. Then these buffer overflows would not appear. But I agree, the window managers/toolkits should be able to handle that. Isn't there a bug report filed?

---

### Post by pibach on 2008-07-20
There a some issues when having easystroke set for left click:

1) easystroke gives unintended focus to apps like cellwriter
2) when I set "accept gestures when menues are shown" then exceptions do not work, e.g., using cellwriter

Edit: with the "Yet another Smooth Scroll" Extension for Firefox you get a smoother scrolling and it accellerates nicely if you want to.

---

### Post by Tom Jaeger on 2008-07-20
I'm a little short on time at the moment, I'll post a more detailed response later this week.

> **pibach said:**
> There a some issues when having easystroke set for left click:
1) easystroke gives unintended focus to apps like cellwriter

I'll look into that, I haven't found a way yet to delegate to the window manager the decision of whether to give focus to a specific window. I'll probably end up duplicating more wm functionality.

> 
2) when I set "accept gestures when menues are shown" then exceptions do not work, e.g., using cellwriter

Thanks, should be fixed in the attached snapshot.

---

### Post by pibach on 2008-07-20
Thanks Tom for the updated shnapshot.

Another small issue:

The ignore gesture after some timeout does not work if I stop moving the pen completely (which might be irritating).

---

### Post by Tom Jaeger on 2008-07-23
I'd like to release version 0.2.0 soon; no new features will go into that version, only bugfixes and minor UI changes.  Consider the attached file "easystroke-0.2.0-rc1" as the release candidate.  As always, comments are welcome.

The plan for 0.3.x is to introduce some form of state - so that actions can be chosen based on the current application and yes, the name and the type of the currently selected GUI element -- provided accessibility is enabled and the app supports it.  My ideas on how to represent this in the GUI are still too half-baked to be discussed here -- but I think I'm going to change the actions list into a tree.  The most important requirement is that the user interface not become more complicated to use for users that don't care about the new features.

Speaking of accessibility, if you want to execute more elaborate actions than are possible via simple keystrokes, GUI-testing frameworks such as [dogtail]("http://people.redhat.com/zcerza/dogtail/") and [LDTP]("http://ldtp.freedesktop.org/wiki/") might be worth investigating. [Note to self: mention this on the wiki]

> **pibach said:**
> 
The ignore gesture after some timeout does not work if I stop moving the pen completely (which might be irritating).

I've added a timeout to work around this problem.  I also needed to generate an additional motion event in order for the app to see the updated cursor position.  I also thought about replaying the whole motion history, but XTest is acting weird here - and I can't send out atomic sequences of XTest commands anyway.

> 
1) easystroke gives unintended focus to apps like cellwriter

Fixed - by inspecting the WMHints of the window.

Regarding scrolling, I've decided that I'd eventually like to implement the thing you proposed (albeit in a more general setting) - but this will require major changes GUI-wise and in the backend.  For now, I have a different idea: proximity, as implemented in the attached file easystroke-dev.  What this does is that it'll stay in scroll or ignore mode until the pen is lifted far enough to be out of range.  Also, it'll only scroll if there's a button pressed.

> 
Scroll wheel events are dumb button presses and apps translate them into a fixed scroll amount. This amount might be configurable for gtk apps

I actually don't think anymore that it's configurable.  There's no gconf setting for it and I think ~/.gtkrc-2.0 only controls style settings (and it would only be effective after restarting the apps anyway).

> 
But I agree, the window managers/toolkits should be able to handle that. Isn't there a bug report filed? 

I'm not aware of any bug reports.  An easy fix would be for GtkAdjustment to only send "value-changed" events when idle.  But I guess there's always a risk of breaking applications that depend on things being done in a certain order.  The much harder part would be setting up a gtk build environment to actually test this.  And even then, there are apps like firefox that have a (probably modified) version of gtk statically linked in.

EDIT: Shoot, I had already uploaded the attachments, but firefox crashed.  Luckily, it had saved the message, but the attachments were gone...
Anyway, since rc1 had issues with modifiers, here's rc2.

EDIT: New RC (I've merged the changes from easystroke-dev)

---

### Post by pibach on 2008-07-25
I think for a typical usage on right click it is fine to be released. However, for elaborate usage scenarios with graffiti or left click, I have issues:

* when I enter letters in some input area in Firefox, then the list of terms to choose from pops up. The input box looses fokus then, when I gesture somewhere, i.e., option "accept gestures when menus are shown" does not work reliably.
* I have a couple of performance issues: sometimes the gesture is recognized as a click, apparently when I do it too fast. Edit: works if I change pixel settings in "Tread as click if..."
* the start of any gesture line does show up only after some delay. But for efficient usage it would be very important to have this lag free.
* when set to right click, gestures do also let the context menu pop up in some situations

Then there still are usability things:
* the new proximity scroll lock is an interesting idea. However lifting the pen that far away from the screen is one of the most inefficient "gestures"
* then in scroll mode you cannot click links, cannot gesture etc. Wouldn't it be possible, to scroll in hoover mode but still accept clicks/gestures for the application on left click?

---

### Post by Luffield on 2008-07-25
Back on Ubuntu, at last.
RC2 seems to work well on my computer, without any issues. I only have a mouse, no tablet.
Looking forward to try the next version.

---

### Post by Tom Jaeger on 2008-07-25
Thanks for the feedback, guys, it's very much appreciated.

> **pibach said:**
> 
* when I enter letters in some input area in Firefox, then the list of terms to choose from pops up. The input box looses fokus then, when I gesture somewhere, i.e., option "accept gestures when menus are shown" does not work reliably.

The problem is that by the time easystroke receives the click event, it already been transmitted to the application, so it seems that there's nothing I can do about this -- short of what gok is doing: detach all input devices from the X server and then send them via XTest, which I don't think is a good idea.  A less evil idea would be to remap the tip to, say button 9 and then fake corresponding button 1 events if we receive button 9 events.  I'll have think about this a little more, but I don't expect it to be easy.

> 
* I have a couple of performance issues: sometimes the gesture is recognized as a click, apparently when I do it too fast. Edit: works if I change pixel settings in "Tread as click if..."
* the start of any gesture line does show up only after some delay. But for efficient usage it would be very important to have this lag free.

This is intentional:  Everything that stays within r pixels of the original position is interpreted as a click and as long we're not sure that it's a gesture, no trail is shown.  I could decrease the default value of r, but I'm not convinced any changes beyond that would make sense.

It would probably a good idea for the wacom driver to release clicks early if pressure is rapidly decreasing in order to prevent motion events from being generated after the pen has been lifted from the surface.

EDIT: You seem to draw your gestures much smaller than I do.  Do you think that you would benefit from subpixel accuracy (as in xournal)?

> 
* when set to right click, gestures do also let the context menu pop up in some situations

This one is the only show-stopper in the list.  What are the situations?  Does this only happen if the menu workaround is enabled?  Can you send me the output of "./easystroke -vvv" when it happens?

> 
* then in scroll mode you cannot click links, cannot gesture etc. Wouldn't it be possible, to scroll in hoover mode but still accept clicks/gestures for the application on left click?
Is what the attached easystroke-dev does what you had in mind.  Maybe scrolling should only be enabled here if the pen speed is at least a certain value.

---

### Post by Tom Jaeger on 2008-07-25
The little tool in the attachment keeps track of what windows have been minimized most recently and undoes activates those windows whenever the user presses Alt+Super+F9.

Also, I've just tried easystroke on intrepid and it appears that there's a bug in recent xorg versions which causes xinput events to be reported in device coordinates rather than screen coordinates.  Hopefully, I can get them to fix the problem, but it wouldn't be impossible to work around this either.  As a temporary workaround, you can disable xinput with the -x command line switch.  On the bright side, XShape performance seems to have improved, meaning that it is possible to draw longer strokes on the screen.

---

### Post by Luffield on 2008-07-26
I found a problem using esaystroke but I'm not sure it's an easystroke issue.

I'm using Hardy, Firefox 3.01 and Mouse Gestures Redox. I use the right mouse button for gestures in both Firefox's extension and easystroke. Easystroke is disabled on the Firefox window.
I minimized the Firefox window with a mouse gesture and then tried to open my home folder using an easystroke gesture on the desktop but the context menu popped up and the gesture didn't work. I went back to Firefox and minimized it again by clicking the minimize thingy on the top of the window, and then easystroke worked normally on the desktop.
A bit more messing around, and I found that minimizing Firefox using the window list on the panel doesn't cause this problem, but going to the desktop with Alt-Ctrl-D or minimizing Firefox with Alt-F9 do.

I guess it could also be a window manager issue. I'm using compiz.

---

### Post by Tom Jaeger on 2008-07-26
> **Luffield said:**
> 
I minimized the Firefox window with a mouse gesture and then tried to open my home folder using an easystroke gesture on the desktop but the context menu popped up and the gesture didn't work.

Okay, I can reproduce the issue.  It only happens if easystroke is started on login.  The problem is that easystroke some misses the creation of the desktop background window.  I'll look into this tomorrow.

EDIT: The problem was that in order to recognize top-level windows, easystroke has to search for windows that are tagged by the window manager, so if no wm is running yet, it won't find any windows.  The solution is to bypass this test if there's no wm.  The problem is fixed in rc4.

---

### Post by pibach on 2008-07-26
> **Tom Jaeger said:**
> 
EDIT: You seem to draw your gestures much smaller than I do.  Do you think that you would benefit from subpixel accuracy (as in xournal)?

the Graffiti gestures I do are quite small, yes. And the recognizer sometimes does produce weird results. Subpixels would be nice user interface improvement, but more important is high recognition accuracy and responsiveness. Another way could be closer integration with cellwriter (e.g., auto invocation, insert and close).

> 
This one is the only show-stopper in the list.  What are the situations?  Does this only happen if the menu workaround is enabled?  Can you send me the output of "./easystroke -vvv" when it happens?

happens when I gesture Graffiti in a text box in Firefox. Then a list pops up to chose from. Gestures outside this list will result in a click event to Firefox. This is regardless of option "Accept gestures when menus are shown" on or off. But I would not rank this a show stopper as you can only produce this by a letter gesture (which most users won't ever do).

> 
Is what the attached easystroke-dev does what you had in mind. Maybe scrolling should only be enabled here if the pen speed is at least a certain value.

Or, if you can figure out scroll area, the other way round: Only if you hover slowly to the edges of the scroll area (e.g., a Firefox Web page) the scroll is activated. The further you go to the edges, the faster is the scroll. If you move faster certain treshold then scroll is not activated (important to reach some item outside scroll area). Also there is some inner area that does not act on hovering scroll such that you can do all gestures and clicks without causing unwanted scrolling. Don't know if this works but might be worth a try. But this of course is stuff for future releases...

---

### Post by Luffield on 2008-07-27
> **Tom Jaeger said:**
> The problem was that in order to recognize top-level windows, easystroke has to search for windows that are tagged by the window manager, so if no wm is running yet, it won't find any windows.  The solution is to bypass this test if there's no wm.  The problem is fixed in rc4.
Thanks for the new version, Tom. I sorry to report that the problem still happens on my computer.

---

### Post by Tom Jaeger on 2008-07-27
> **Luffield said:**
> Thanks for the new version, Tom. I sorry to report that the problem still happens on my computer.
I'm not giving up yet.  Does this also happen when easystroke is started when the window manager is already running?

---

### Post by Luffield on 2008-07-27
> **Tom Jaeger said:**
> I'm not giving up yet.
I didn't think you would :D

> **Tom Jaeger said:**
> Does this also happen when easystroke is started when the window manager is already running?
It works fine when I start it from the terminal.

---

### Post by Tom Jaeger on 2008-07-27
> **Luffield said:**
> 
It works fine when I start it from the terminal.

Can you check this version?  It simply waits for a little bit if there's no wm running.

---

### Post by Luffield on 2008-07-27
No change, I'm afraid.

---

### Post by Tom Jaeger on 2008-07-29
> **Luffield said:**
> No change, I'm afraid.

This one has to work.  It simply re-scans 15 seconds after startup.

I'll release the new version as soon as I find some time to update the documentation.

---

### Post by Tom Jaeger on 2008-07-29
> **pibach said:**
> the Graffiti gestures I do are quite small, yes. And the recognizer sometimes does produce weird results. Subpixels would be nice user interface improvement, but more important is high recognition accuracy and responsiveness. 

Yeah, that's what I meant.  The hope is that using the device resolution will improve recognition results, but ultimately, a new algorithm is needed.  The higher resolution will have to wait before the xorg device event reporting issue is settled, though.  As for responsiveness, I'm not sure what you mean.  Is the 200ms minimum delay between strokes the problem, or is the actual recognition slow (that is, does producing the matrix take a long time)?

Do you think we should draw the stroke before it is even clear that the user is actually doing a gesture?

> 
happens when I gesture Graffiti in a text box in Firefox. Then a list pops up to chose from. Gestures outside this list will result in a click event to Firefox. This is regardless of option "Accept gestures when menus are shown" on or off. But I would not rank this a show stopper as you can only produce this by a letter gesture (which most users won't ever do).

Sorry, I have no clue what's going on here.  Unless the app has grabbed the server (in which case nothing should happen if the option is turned off), no clicks should go through to the application.

> 
Or, if you can figure out scroll area, the other way round: Only if you hover slowly to the edges of the scroll area (e.g., a Firefox Web page) the scroll is activated. The further you go to the edges, the faster is the scroll. If you move faster certain treshold then scroll is not activated (important to reach some item outside scroll area). Also there is some inner area that does not act on hovering scroll such that you can do all gestures and clicks without causing unwanted scrolling. Don't know if this works but might be worth a try. But this of course is stuff for future releases...

Like firefox's autoscrolling?  I've always hated that feature.  Anyway, I think figuring out the extents of scroll areas is possible using accessibility tools, but it might not be very stable (as in apps might randomly hang).  I'd rather stick to what can be accomplished by listening to at-spi events.  See the attached track-focus binary (it's in the access subdirectory in darcs) for an example that tracks focus and [this link]("http://accessibility.freestandards.org/a11yspecs/atspi/adoc/atspi-events.html") for what events are available.  Note that this will only work if accessibility is enabled in the gnome settings.

---

### Post by pibach on 2008-07-29
> **Tom Jaeger said:**
> 
Do you think we should draw the stroke before it is even clear that the user is actually doing a gesture?

Yes, definitely. Also I do consecutive gestures faster than 200ms. There shouldn't be any delay in between. 

To get more confidence in what gestures are doing, there should be additionally some feedback, either visual or audio. Could you draw the recognized/executed gesture pattern&command? Visual feedback should be next to where you do gesturing.

Regarding autoscroll: yes, I agree. I also do not like that implementation. But I think the problem is that it is only based on  cursor position, not on its movement. The trick might be, to find a suitable formula that balances the influence of cursor movement and position.

There's also another simple option:
Enter scrolling as soon as you move the gesture for more than x pixels (all non-scrolling gestures I do are rather small).
Or as soon as you fall below certain pen speed (all non-scrolling gestures I do quite fast).

---

### Post by Luffield on 2008-07-30
Tom, I'm posting this before installing RC5 - everything works well with RC4. After I installed it I logged out and logged in again and the problem still occured, so I guess I had to restart my computer (or X?) for the changes to kick in.
Sorry for making you work a bit harder than needed...

---

### Post by Tom Jaeger on 2008-07-30
> **pibach said:**
> Yes, definitely. Also I do consecutive gestures faster than 200ms. There shouldn't be any delay in between. 

The delay is there to avoid flickering.  The new behavior (implemented in the attached binary) is to still have the delay but fast-track the process if another stroke is started.  This version will also start drawing the gesture once the mouse has moved by 4 pixels, though I'm still on the fence about whether to include the change in the stable version.

> 
To get more confidence in what gestures are doing, there should be additionally some feedback, either visual or audio. Could you draw the recognized/executed gesture pattern&command? Visual feedback should be next to where you do gesturing.

Like what vista does after flick gestures?

> 
There's also another simple option:
Enter scrolling as soon as you move the gesture for more than x pixels (all non-scrolling gestures I do are rather small).
Or as soon as you fall below certain pen speed (all non-scrolling gestures I do quite fast).
One problem with the long gestures is that it might easily lead the pointer out of the window where scrolling can't work.  For low speeds we already have aborting the stroke.  Are you suggesting the the timeout action be configurable?

---

### Post by Luffield on 2008-07-30
Regarding the geture feedback: I agree, it would be great to have this. Mouse Gestures Redox pops up a tooltip one the corner of the Firefox window and writes the gesture there (I think by default this option is off).
I'm not familiar with the vista flick gestures.

---

### Post by Eudinaesis on 2008-07-30
Hi there - thanks so much for making this program!

This is probably just some really silly mistake on my part (I'm a linux newbie) but -- am I supposed to need to run this as root?  When I don't, I get the following message:

easystroke
XError: BadAccess (attempt to access private resource denied): X_GrabKey
Error: Couldn't save preferences.
Segmentation fault

And even when I run it with sudo, I still get: "XError: BadAccess (attempt to access private resource denied): X_GrabKey"

What exactly do I need to do to have this run at startup?

Thanks,
Peter

---

### Post by Tom Jaeger on 2008-07-31
> **Eudinaesis said:**
> am I supposed to need to run this as root?  When I don't, I get the following message:

No, the program should be run as a regular user.  What probably happened here is that you were root the first time you ran the program, so the configuration directory is now owned by root and you don't have write access to it unless you're root.  You can correct this by typing

```
sudo chown -R $UID ~/.easystroke
```

in the command line.

> 
Error: Couldn't save preferences.
Segmentation fault

Now I actually had code in there to test for this case and display a hopefully somewhat helpful error message, but unfortunately (as always is the case with code that gets little testing), this did the exact opposite and just crashed the program.  This will be fixed in the upcoming 0.2.0 release.

> 
And even when I run it with sudo, I still get: "XError: BadAccess (attempt to access private resource denied): X_GrabKey"

This means that easystroke was unable to grab the Escape key, which could be used to abort gestures.  Not a big deal.

> 
What exactly do I need to do to have this run at startup?

System -> Preferences -> Sessions -> Add

I should probably look into whether there is a way to do enable autostart in easystroke's preferences dialog (EDIT: I looks like this is just a matter of creating an appropriate .desktop file in the ~/.config/autostart/ directory.  Won't make the cut for 0.2.0, though)

---

### Post by Tom Jaeger on 2008-07-31
Peter, I've noticed some weird behavior related to focus.  This might be a similar issue.  Can you check if the issue is present in the attached version, which completely disables messing with the input focus?  Thanks.

> **pibach said:**
> 
* when set to right click, gestures do also let the context menu pop up in some situations


---

### Post by pibach on 2008-07-31
> **Tom Jaeger said:**
> Peter, I've noticed some weird behavior related to focus.  This might be a similar issue.  Can you check if the issue is present in the attached version, which completely disables messing with the input focus?  Thanks.
same focus-stealing here.

---

### Post by Eudinaesis on 2008-08-01
Thanks!

> **Tom Jaeger said:**
> No, the program should be run as a regular user.  What probably happened here is that you were root the first time you ran the program, so the configuration directory is now owned by root and you don't have write access to it unless you're root.  You can correct this by typing

```
sudo chown -R $UID ~/.easystroke
```

in the command line.


Now I actually had code in there to test for this case and display a hopefully somewhat helpful error message, but unfortunately (as always is the case with code that gets little testing), this did the exact opposite and just crashed the program.  This will be fixed in the upcoming 0.2.0 release.


This means that easystroke was unable to grab the Escape key, which could be used to abort gestures.  Not a big deal.


System -> Preferences -> Sessions -> Add

I should probably look into whether there is a way to do enable autostart in easystroke's preferences dialog (EDIT: I looks like this is just a matter of creating an appropriate .desktop file in the ~/.config/autostart/ directory.  Won't make the cut for 0.2.0, though)

---

### Post by Tom Jaeger on 2008-08-03
> **pibach said:**
> same focus-stealing here.

Let's give this another try.  This version replays the button press instead of faking it, which seems to solve a few annoying left-click bugs here.

NB. This is a development snapshot, which re-introduces a few bugs and contains some unrelated changes (among them taking advantage of the full tablet resolution, but that will break rotation for now).

---

### Post by tom66 on 2008-08-03
Seems very slow with wobbly windows enabled.

---

### Post by Tom Jaeger on 2008-08-03
> **tom66 said:**
> Seems very slow with wobbly windows enabled.

What do you mean by *slow*?  Wobbly windows certainly doesn't have any effect on performance.

---

### Post by Tom Jaeger on 2008-08-04
I've finally taken the plunge and released 0.2.0, a little too soon, as it turns out, since a little mistake in the Makefile rendered the debian packages unusable.  I corrected this in version 0.2.1 a few hours later.

The new features have been discussed extensively in this thread, therefore I'll be short -- highlights are the so-called [Advanced Gestures]("http://easystroke.wiki.sourceforge.net/FeatureAdvancedGestures#content") and much improved tablet support.

Of course, development doesn't stop at this point.  I plan to release version 0.2.2 before the Intrepid feature freeze (Aug 28);  this version will contain only minor improvements such as better visual feedback;  the bigger changes (application-dependent behavior) will have to wait until version 0.3.0.

I've also created a [launchpad PPA]("https://launchpad.net/~thjaeger/+archive").  By adding the line
```
deb http://ppa.launchpad.net/thjaeger/ubuntu hardy main
```
to you /etc/apt/sources.list file, you'll be able to install the program using synaptics or 'apt-get install' and upgrade it via update-manager or 'apt-get update'.  This also means that in addition to i386, precompiled amd64 and lpia packages are now available.

I'm hoping to get the package accepted into intrepid;  as a first step, I've uploaded it to REVU for review.

---

### Post by Tom Jaeger on 2008-08-05
> **pibach said:**
> To get more confidence in what gestures are doing, there should be additionally some feedback, either visual or audio. Could you draw the recognized/executed gesture pattern&command? Visual feedback should be next to where you do gesturing.

Preliminary support for visual feedback is included in the attached development snapshot.

---

### Post by pibach on 2008-08-09
> **Tom Jaeger said:**
> Preliminary support for visual feedback is included in the attached development snapshot.
Thanks, this works just fine. Only it has some delay to pop up (I like it ultimately responsive)

BTW, in Compiz (which I do not use due to the Firefox scroll problem) the visual feedback gets animated (window open/close effect). To disable this one would need to add the easystroke window to the exceptions.

---

### Post by Tom Jaeger on 2008-08-10
> **pibach said:**
> Thanks, this works just fine. Only it has some delay to pop up (I like it ultimately responsive)

There's no artificial delay, and I don't notice one either.  As soon as the gesture is recognized, the popup will be created.

> 
BTW, in Compiz (which I do not use due to the Firefox scroll problem) the visual feedback gets animated (window open/close effect). To disable this one would need to add the easystroke window to the exceptions.
It's just a regular popup, so its open animation can be configured in the "Open Animation" tab of the Animation plugin.  The default is a 150ms fade-in effect.  If that bothers you, chances the fade-in time for menus and such will bother you, too, so you'll probably just want to adjust this setting.

In other news, development is continuing at a steady pace.  I've basically rewritten the window-tracking code, which will hopefully eliminate a few bugs.  As a user-visible consequence, window manager frames are now their own window class, so they can be listed as an exception, which should make it easier to drag windows if easystroke is set to left-click.
The parameters of the gesture timeout are now configurable if the program is invoked as 'easystroke -e'.
There finally is a decent gesture trail under compiz.  It works by communicating with the 'annotate' plugin via dbus and requires compiz's 'annotate' and 'dbus' plugins to be enabled.  It'll give you smooth, antialiased gestures, reduced CPU-usage compared with the XShape method and configurable color, alpha-transparency and thickness.

I'm attaching a current snapshot.  Note that the internal file format changed again, so I'd suggest a backup of the ~/.easystroke directory if you want to go back to an earlier version.


My efforts to get the program accepted into the Ubuntu repositories turned out to be a tremendous waste of time and energy, as apparently no MOTU is willing to review my package.  It has been suggested to me that I try to get the package into debian first, but I'm not sure about that yet because that too would be a huge time commitment and the outcome would be just as uncertain -- and besides, it would almost certainly mean that I would miss my intrepid goal, so what's the point?

---

### Post by Tycho Quad on 2008-08-11
Very awesome!

Would it be possible to get it to use the "Paint fire on the screen" plugin instead?

---

### Post by Tom Jaeger on 2008-08-11
> **Tycho Quad said:**
> Very awesome!

Would it be possible to get it to use the "Paint fire on the screen" plugin instead?

Yes, but...

First of all, the firepaint plugin doesn't respond to dbus events in the same way the annotate plugin does.  So we need to patch it first (instructions below).
The next issue is that compiz stops receiving dbus messages after a while, for reasons I don't understand.  This only comes up if you're drawing really long strokes and isn't a problem in practice, but it's something to be aware of.  If this should happen, minimizing or maximizing a window will usually restore things back to normal.

EDIT: Now I know what's going on here:  The compiz main loop will only read from other file descriptors if there are no events waiting on the X connection, so if an iteration of painting the fire takes too long, compiz won't receive any dbus messages.  It's not obvious if or how that should be fixed.

Finally, because of these issues I can't possibly include the fire option by default, so you'll have to invoke the program as "./easystroke -e" to even see the option.

Instructions for setting up the dbus-enabled fire plugin:
```

sudo apt-get install compiz-dev compiz-fusion-bcop git-core
git clone git://anongit.compiz-fusion.org/fusion/plugins/firepaint
cd firepaint
make install # you don't need to be root, this goes into the user's HOME directory
compiz --replace &

```
(EDIT: patching is not necessary anymore)

---

### Post by pibach on 2008-08-11
> **Tom Jaeger said:**
> 
It's just a regular popup, so its open animation can be configured in the "Open Animation" tab of the Animation plugin.  The default is a 150ms fade-in effect.  If that bothers you, chances the fade-in time for menus and such will bother you, too, so you'll probably just want to adjust this setting.

There finally is a decent gesture trail under compiz.  It works by communicating with the 'annotate' plugin via dbus and requires compiz's 'annotate' and 'dbus' plugins to be enabled.  It'll give you smooth, antialiased gestures, reduced CPU-usage compared with the XShape method and configurable color, alpha-transparency and thickness.

Interestng. But currently I do not use Compiz (just tested it) as it does slow down scrolling in Firefox unacceptably. And then there is the xrandr problem for rotation. But maybe both problems get solved soon? This would make a very attractive package for a "Tabuntu Editon". BTW: what is the name of that window to put into Compiz as exception?

---

### Post by Tom Jaeger on 2008-08-11
> **pibach said:**
>  And then there is the xrandr problem for rotation.

Solved in intrepid and there's a good workaround for hardy.  However, we need [this patch]("http://gitweb.freedesktop.org/?p=xorg/xserver.git;a=commit;h=37927b8bfa78670b263311ae1f06d2aae973601d") in xserver before easystroke is usable on intrepid (EDIT: package in my PPA).

> BTW: what is the name of that window to put into Compiz as exception?
This works for me: (class=Easystroke) & (override_redirect=1)

---

### Post by Tom Jaeger on 2008-08-14
This time around, I'd like to try to avoid dragging out the release so long, so here's 0.2.2-rc1.  It features visual feedback, a new window tracking logic and "timeout profiles", which control how long it takes for gestures to timeout and how fast you have to move your pen/mouse.  You can see the details if you start easystroke with the -e option.  I chose the parameters more or less at random, so I'm very open to suggestions as to what reasonable profiles might be.

The dbus fire patch will hopefully be in compiz fusion git soon. [EDIT: [here]("http://gitweb.compiz-fusion.org/?p=fusion/plugins/firepaint;a=commit;h=3d8ef8eeb0b5f0138f02f941111acb73790452c5") it is]

By the way, I've now switched to intrepid's xserver/driver/mesa combination for good, scrolling has gotten a lot smoother, but it seems like all the 3d stuff is noticeably slower now.  Also, negative and reflection work now.  Blur, too, but not with reasonable performance.

---

### Post by damagedspline on 2008-08-14
pibach, in the beginning of the thread you mentioned testing it on n810.

do you still have the pre-built binaries? (or maybe more updated ones?)

---

### Post by pibach on 2008-08-16
> **damagedspline said:**
> pibach, in the beginning of the thread you mentioned testing it on n810.

do you still have the pre-built binaries? (or maybe more updated ones?)
Yet I did not run easystroke on my n810 but I would like to. So let's get ahead, probably best way would be to post this in some n810 forum?

---

### Post by pibach on 2008-08-16
> **Tom Jaeger said:**
> 

By the way, I've now switched to intrepid's xserver/driver/mesa combination for good, scrolling has gotten a lot smoother, but it seems like all the 3d stuff is noticeably slower now.
Could you point me to some howto?
I also would be happy with just XFCE compositing for shadows and transparency. This also might be less battery hungry compared to compiz and gives the option to switch of compositing, triggered by laptop mode tools. As far as I know XFCE compositor does not require OpenGL (?). Would you recommend intrepid Mesa 3D GL driver for that purpose? Also the predominant performance issue I get under Compiz concerns scrolling, all 3D effects are reasonably fast.

---

### Post by Tom Jaeger on 2008-08-16
> **pibach said:**
> Could you point me to some howto?
The process is just a matter of adding intrepid lines to sources.list and then upgrading the xserver and libgl1-mesa-dri packages.  If you add 'APT::Default-Release "8.04";' to /etc/apt/apt.conf update-manager won't bother you with updates from intrepid.  You might also need to edit your xorg.conf.

That said, I wouldn't really recommend the upgrade at this point, it turns out there are quite a few issues:  Many 3d operations are noticeably slower (I had to disable the animation plugin and cube reflection), there seem to be problems with textures in 3d apps and videos crash the x server.  I could live with all that, but the biggest problem are random lockups when activating alt+tab switching or the shift switcher.  They don't happen very often, but if they do, the only thing you can do is ssh into your machine and reboot.  Not even the SysRq combinations help anymore.  [EDIT: This apparently went away after I disabled the reflection plugin.]

Another mesa 7.1 rc has just been released a few hours ago, let's hope that it fixes most of the issues.
UPDATE: It doesn't.

> 
I also would be happy with just XFCE compositing for shadows and transparency. This also might be less battery hungry compared to compiz

One should hope that the relevant XRender operations are hardware-accelerated, but if they're not, it'll probably use more power than compiz.
Do the additional 60 interrupts per second that compiz causes really make a such big difference, though?  I find that a little hard to believe.

---

### Post by Tom Jaeger on 2008-08-17
I've released 0.2.2.  Debs are available through my PPA:

[i386]("http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/e/easystroke/easystroke_0.2.2-0ubuntu1_i386.deb")
[amd64]("http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/e/easystroke/easystroke_0.2.2-0ubuntu1_amd64.deb")

Update:  0.2.2-0ubuntu1 is in the [New queue]("https://launchpad.net/ubuntu/intrepid/+queue") for intrepid.

---

### Post by pibach on 2008-08-18
So this means it is evaluated for Intrepid release? Would be great.
I Like the new compiz annotation draw method. I now have configured my desktop with Gnome+Compiz+Emerald+Cairo Dock, very pen friendly (although a bit slow).
However I sometimes get slight corruption, i.e., the red line of the annotation if fine, but the line stored when I define actions shows some hickups. So I need to redraw. Otherwise it works great.
Some slight suggestion: keep the red line visualisation some time (e.g., 500ms) visible.

---

### Post by Tom Jaeger on 2008-08-20
It's already in intrepid.  So I'll have to support version 0.2.2 in some form until at least 8 months from now.  Kind of scary if you think about it.

> **pibach said:**
> 
However I sometimes get slight corruption, i.e., the red line of the annotation if fine, but the line stored when I define actions shows some hickups. So I need to redraw. Otherwise it works great.

This only happens with annotate?  Either way, I don't have much of a clue what's going on here.

> 
Some slight suggestion: keep the red line visualisation some time (e.g., 500ms) visible.

I'm already doing something similar for fire, so this should be easy to do.  I think I'm going to go with 250ms, though.

---

### Post by pibach on 2008-08-20
ok, I'm back to Xfwm4+Compositing, it is a lot more responsive.

Here are some further questions:

* is it possible to query the cursor or mouse position? I would like to start cellwriter close to the input area.
* if activating easystroke on left click you can put the scroll area in the list of exceptions ("Navigator"). Unfortunately it as well disables gestures for the rest of the window. If I add the window frame (for dragging a window) I cannot gesture on the desktop (why is that?). Anyway the "medium" gesture abort timing seems to work fine for me.

---

### Post by Tom Jaeger on 2008-08-20
> **pibach said:**
> 
* is it possible to query the cursor or mouse position? I would like to start cellwriter close to the input area.

The position before or after the stroke?  Both are easy to do, though one of them obviously has to be done inside easystroke.

> 
* if activating easystroke on left click you can put the scroll area in the list of exceptions ("Navigator").

"Navigator" is just the name that firefox gives itself, so this behavior is expected.

> If I add the window frame (for dragging a window) I cannot gesture on the desktop (why is that?).
I can't test this since even when I start xfwm4, nautilus handles the background window.  What is the output of
```
xwininfo | grep 'Window id'
```
when you click on the desktop?

---

### Post by pibach on 2008-08-20
> **Tom Jaeger said:**
> The position before or after the stroke?  

Doesn't matter much as I was just looking for some simple solution outside easystroke. Basicaly I want a behavior similar to Vista's TIP (ultimately better of course), i.e., launch cellwriter and bring it close to the cursor position whenever I hit some text input area with the pen. Currently I use a workaround: I defined a gesture to invoke cellwriter. It allows to have x,y coordinates where to brint it up. These coordinates have to be set according to some query for the mouse (or cursor) position. 

> 
I can't test this since even when I start xfwm4, nautilus handles the background window. 

I am using the exact same setup, xfwm4 on top of Gnome. Finally this will require to retrieve the GTK elements under the pen's position and only invoke a gesture if it is not a "strokeable" one.

But biggest issue still for left click usage is to distinguish mouse or trackpoint versus pen. Best solution herefore would probably be to deactive easystroke if pen is not in proximity.

---

### Post by linuxguymarshall on 2008-08-20
Very nice app. I would like to see webcam integration soon so that maybe we can get a Nintendo wii-like thing going. I would love to hold up X fingers and open up Firefox

---

### Post by Tom Jaeger on 2008-08-20
> **pibach said:**
> Basicaly I want a behavior similar to Vista's TIP (ultimately better of course), i.e., launch cellwriter and bring it close to the cursor position whenever I hit some text input area with the pen.

This isn't actually that hard to do:  At-spi can notify us when the focus changes to a text field, and then we could place cellwriter as close to the cursor as possible without overlapping the input field.  The hardest part would actually be to control cellwriter, which would have to be patched.

> 
Currently I use a workaround: I defined a gesture to invoke cellwriter. It allows to have x,y coordinates where to brint it up. These coordinates have to be set according to some query for the mouse (or cursor) position. 

Querying the mouse position is trivial.  I've attached an example (compile via 'gcc -lX11 query-pointer.c -o query-pointer').

> 
I am using the exact same setup, xfwm4 on top of Gnome. Finally this will require to retrieve the GTK elements under the pen's position and only invoke a gesture if it is not a "strokeable" one.

GTK widgets only exist as data structures inside client applications.  We have to rely on with what information they export through ATK, which isn't good enough to, say, decide if there is a scroll bar under the cursor.

> 
But biggest issue still for left click usage is to distinguish mouse or trackpoint versus pen. Best solution herefore would probably be to deactive easystroke if pen is not in proximity.
The information what device an event came from is available through Xi.  So this is possible, but in practice it will require making the assumption that Xi events are always generated.  This is tantamount to dropping xserver 1.3 support (which is what gutsy uses), but since I can't do the necessary testing, it is a gamble to use easystroke with old xserver versions anyway (if you manage to compile it, that is...).

---

### Post by Tom Jaeger on 2008-08-20
> **linuxguymarshall said:**
> Very nice app. I would like to see webcam integration soon so that maybe we can get a Nintendo wii-like thing going. I would love to hold up X fingers and open up Firefox
It's an interesting idea, but it requires a completely different set of algorithms.  Since I don't know anything about image/video processing, I'm really the wrong person to ask, but I'd accept patches.

Taking advantage of the additional axes of a wiimote would probably be feasible, but don't have one to test this on (is there even a way to hook it up to your computer?).

---

### Post by savantelite on 2008-08-21
once its in the repos I will have it in a flash. Even a deb file I can click install now. I am just to simple for command line.

---

### Post by reacocard on 2008-08-21
> **Tom Jaeger said:**
> 
Taking advantage of the additional axes of a wiimote would probably be feasible, but don't have one to test this on (is there even a way to hook it up to your computer?).

Yes there is, all you need is a bluetooth adapter for the computer. I've used a wiimote as a presentation remote before under ubuntu, using cwiid to turn the wiimote buttons into normal buttons. I haven't investigated the axis abilities at all, but wmgui shows it can get the signals quite readily.

---

### Post by pibach on 2008-08-27
> **Tom Jaeger said:**
> The hardest part would actually be to control cellwriter, which would have to be patched.

according to *man cellwriter* it has the options *--windows-x* and *--windows-y* to specify where it should pop up. But I cannot get this to work.

Another issue with cellwriter is that *cellwriter --show-window * does sometimes not bring up the window when running compiz (works fine on Xfwm4 though and also clicking the tray icon always works). I can get this fixed by restarting cellwriter, weired.

Another downer is that execution of easystroke commands takes a bit long, for cellwriter to come up it takes for example ~2s, whereas cellwriter pops up immediately if I just hit its tray icon.

---

### Post by Tom Jaeger on 2008-08-27
The only solution here is to patch cellwriter and create, say, a dbus interface.  I'd send the author an email, but I'm kind of swamped at the moment.

> 
Another downer is that execution of easystroke commands takes a bit long, for cellwriter to come up it takes for example ~2s, whereas cellwriter pops up immediately if I just hit its tray icon.
This is weird.  Is it only cellwriter that has this problem?  In any case, restarting cellwriter every time you want to use it is not an ideal solution anyway.

---

### Post by Risujin on 2008-08-27
Hi guys! I'm the author of CellWriter. Peter sent me an email about this thread, maybe I can be of help.

> **Tom Jaeger said:**
> The only solution here is to patch cellwriter and create, say, a dbus interface.  I'd send the author an email, but I'm kind of swamped at the moment.

CellWriter uses something much hackier, it just has an open fifo in its settings directory that accepts input to toggle the window.

> This is weird.  Is it only cellwriter that has this problem?  In any case, restarting cellwriter every time you want to use it is not an ideal solution anyway.

Running CellWriter when it is already running does not start a second instance or "restart". The second instance just toggles the main window and quits. It doesn't communicate the --window-x/y parameters this way though, it only checks those when it is started for real. This is fixable of course, if this is really useful for you guys.

---

### Post by all2ez on 2008-08-27
> **Tom Jaeger said:**
> Hi,

I'd like to announce [easystroke]("http://easystroke.sourceforge.net"), a new gesture recognition application for linux.  Gesture recognition means that you can draw arbitrary curves on the screen by holding down a specific mouse button, and if the program recognizes their shape, it will perform certain actions.

Did you ever know that you're my hero,
and everything I would like to be?
I can fly higher than an eagle,
'cause you are the wind beneath my wings.

Seriously, this is a great program!  I'm sorry to perpetuate the comparisons to Stroke-it, but I use that in Windows and have been waiting for a satisfying alternative in Linux.  You have given me what I wanted and more, thanks a lot and keep up the great work!

---

### Post by pibach on 2008-08-31
> **Risujin said:**
> It doesn't communicate the --window-x/y parameters this way though, it only checks those when it is started for real. This is fixable of course, if this is really useful for you guys.
Hi Risujin, great to have you here!

I think the challenging goal is a "Tabuntu" edition with comprehensive pen integration, (at least) at the level Vista does it. Cellwriter and easystroke are the core apps in this respect. So lets discuss how to get them work flawlessly together.

Current workflow for pen-based text input is to activate Cellwriter by clicking its tray icon and moving its window to the desired position. To get this more efficient I suggested to open cellwriter on an easystroke gesture at the position of the gesture. This gesture activation might also be better (and easier to implement) than the auto-activation (mimicking the Vista TIP behavior) we discussed above.

I don't know if fixing the --window-x/y in conjunction with --show-window would be best, as it seems to introduce some delay (Risujin, could you explain this delay?). But anyway this seams to be the most straight forward approach.

Another option might be a direct activation/window placement for common applications from within easystroke, for example, to activate xvkbd at the gesture position. Probably this is quicker and also more general? What do you guys think?

Another important problem is that most tablet users just don't know that there is such a good pen support when using Linux on a tablet PC. The question here is how to package and deliver these tablet goodies to get some more visibility. This should be coordinated with the activities in Ubuntu Netbook Remix and MID Edition. Risujin, what is your suggestion in this respect? 

BTW, I installed the Window-Picker-Applet from Netbook Remix, which does a good job at maximizing screen real estate, perfect for devices with low resolutions/small displays. 

--Peter

---

### Post by pibach on 2008-09-07
No follow up post?

Probably [wmctrl]("http://www.sweb.cz/tripie/utils/wmctrl/") or [devilspie]("http://www.burtonini.com/blog/computers/devilspie") could serve placing windows close to the pen's position?

---

### Post by Tom Jaeger on 2008-09-08
Sorry I haven't replied earlier, I've been very busy with other things lately.  I had already worked on the automated cellwriter invocation, so I'm just going to dump the code on you that I have so far.  It's proof-of-concept code, it'll just kill cellwriter and restart it later instead of hiding and showing it.  It doesn't do any overlap detection and will happily move a window partially off the screen.  Also, trying to quit cellwriter the regular way will make the X server hang.

To do placement properly, we'll need to somehow get the coordinates of the cellwriter window.  I originally suggested dbus for this, but I've now realized that this won't work because the size of the window might change over time, and i don't think dbus makes callbacks particularly easy.  So we're probably going to have to use X11 anyway to get a hold of the cellwriter window and watch it for size changes.  Moving the window is also possible, but it might take some trickery to wait for the right moment.  So it seems like we're good as far as cellwriter is concerned, but it might still be a good idea to make cellwriter's --window-x and --window-y parameters work when cellwriter is already running.

In other news, my PPA contains updated packages that fix a few minor bugs.  I'll make a proper release in time for the intrepid beta freeze.

EDIT: Just looked at cellwriter's source, right now there is a 1-Hz timer responsible for checking the fifo, which causes the delays.  I'll send risujin a patch.

EDIT2: Updated cellwriter package in my PPA.

---

### Post by pibach on 2008-09-09
Thanks for the update, I'll give this a try. 
But isn't the window placement possible by simply engaging [wmctrl]("http://www.sweb.cz/tripie/utils/wmctrl/")? There is the following placement option:
"<MVARG>              Specifies a change to the position and size
                       of the window. The format of the argument is:
                       <G>,<X>,<Y>,<W>,<H>"
Regarding cellwriter I hope that Risujin will do that window-show at x/y fix so there's no workaround needed (in conjunction with your patch this should be fine).

I still see the Grab&Drag scroll option of easystroke being a killer feature, if it works for all apps such as OpenOffice or Epiphany (which do not provide G&D scrolling natively).

What about this simple approach: There's already a gesture timeout implemented. Now check after the timeout if the gesture was a straight vertical movement (up or down). If yes, switch scrolling mode on. 

Another demanding feature are right click and middle click (plus Ctrl-click) gestures that act on the *originating* position.

---

### Post by Tom Jaeger on 2008-09-09
> **pibach said:**
> Thanks for the update, I'll give this a try. 
But isn't the window placement possible by simply engaging [wmctrl]("http://www.sweb.cz/tripie/utils/wmctrl/")? 

Moving the window is easy, that's just a XMoveWindow() call.  But it's important to move the window after it has been mapped and moved by cellwriter, so there's some additional work to do.

> 
I still see the Grab&Drag scroll option of easystroke being a killer feature, if it works for all apps such as OpenOffice or Epiphany (which do not provide G&D scrolling natively).

I actually like the side button idea better, but in any event, this'll have to wait for a little bit.  Next on my list is application-dependent actions and preferences.  I already worked out roughly how the GUI is supposed to look like, I just need to find the time to implement it.

> 
Another demanding feature are right click and middle click (plus Ctrl-click) gestures that act on the *originating* position.
Unfortunately, this is impossible as there is no way to execute XTest requests in an atomic way.

---

### Post by pibach on 2008-09-09
> **Tom Jaeger said:**
> 
I actually like the side button idea better, but in any event, this'll have to wait for a little bit. 

Ok, I am eagerly awaiting your next improvements. Application specific gestures sounds good to me. Nevertheless convenient scrolling is a must.

Currently it works just fine with G&D scrolling in Firefox. I have easystroke on the left click. So I have to wait for the timeout to get G&D kick in. This works very well, as I keep the pen down while reading which triggers the timeout and thus I can scroll immediately on pen movement. But of course this does not work in apps other than firefox.

Implementation shouldn't be too difficult. Isn't it just an additional If-Then line to check the movement and in case it has been less than X pixels (say 10) horizontal (e.g., to mark text) then trigger the scrolling mode? 

> 
Unfortunately, this is impossible as there is no way to execute XTest requests in an atomic way.
Strange. Isn't it possible to store the starting point of the gesture line? That's a bummer.

---

### Post by SunnyRabbiera on 2008-09-09
I personally never liked mouse gestures, as I am always dropping my mouse.

---

### Post by Gourgi on 2008-09-12
bumping this  'cause this app really ROCKS ! :guitar:

---

### Post by Tom Jaeger on 2008-09-12
I'm attaching a new development snapshot, which contains an experimental version of the feature you requested.  Enable 'Timeout Gestures' in the preferences dialog, then you should be able to record gestures involving timeouts.  Timeout gestures require a greater accuracy for a match.

Standard disclaimer: Keep backups if you want to test development versions, you won't be able to go back to the stable version otherwise.

> **pibach said:**
> 
Strange. Isn't it possible to store the starting point of the gesture line? That's a bummer.
The difference is that in this case the event is just delayed and replayed at a later time, so it will use the original coordinates.  But we don't know upfront which button needs to be pressed, so we can't use the same method.

EDIT: Bugfixes

---

### Post by pibach on 2008-09-13
> **Tom Jaeger said:**
> I'm attaching a new development snapshot, which contains an experimental version of the feature you requested.  Enable 'Timeout Gestures' in the preferences dialog, then you should be able to record gestures involving timeouts.  Timeout gestures require a greater accuracy for a match.
Tom, it's gread at what pace you do enhance easystroke and manage to incorporate feature request. 
However, you have to help me as I did not see how to define timeout gestures. I did enable the checkbox under preferences. And then added a new gestures. But then, where can I assign this gesture to be a timeout one?

---

### Post by Tom Jaeger on 2008-09-13
> **pibach said:**
> Tom, it's gread at what pace you do enhance easystroke and manage to incorporate feature request. 
However, you have to help me as I did not see how to define timeout gestures. I did enable the checkbox under preferences. And then added a new gestures. But then, where can I assign this gesture to be a timeout one?
Just let the gesture time out when you're recording :)

---

### Post by pibach on 2008-09-14
> **Tom Jaeger said:**
> Just let the gesture time out when you're recording :)
LoL
Ok, that way it works to record timeout gestures. They are marked by a red cross. But they are not recognised. Sometimes some wrong (non-timeout) gesture is recognised.

---

### Post by Tom Jaeger on 2008-09-14
> **pibach said:**
> LoL
Ok, that way it works to record timeout gestures. They are marked by a red cross. But they are not recognised. Sometimes some wrong (non-timeout) gesture is recognised.

You're probably using the version I posted at first, which had a bug in it.  The updated version should fix this.

---

### Post by Gan Quan on 2008-09-15
Thank you! Great app, I've been looking for a easy-to-use replacement of strokeit since I switched from windows to linux, and now I found my answer, thank you thank you thank you!

Just two suggestions:
1. Application dependent gesture settings, allow gestures to behave differently in different applications.
2. Hide the tray icon.

---

### Post by pibach on 2008-09-15
> **Tom Jaeger said:**
> You're probably using the version I posted at first, which had a bug in it.  The updated version should fix this.
Yes, it does. Works wonderfully now. You have to bring this into the repo release, it improves functionality a lot. Also the scroll acceleration works fine. Only suggestion: the cursor should change to indicate scroll mode (and further visualisation of the scroll gesture is not needed then). Have to play with timeout gestures a bit more, e.g., to define Middle-Click and Ctrl-Click as timeout gestures. And whether it is better to define scroll for up/down gestures or even for a click (I would prefere the latter, but here timeout seems to be a tad too aggressive - I am using medium profile).
BTW, I get segmentation fault when returning to old version, seemingly because format of gesture file has changed.

Edit: still it is a bit difficult to scroll list boxes etc. Thinking for some intuitive solution. Would it, for example, be possible to scroll further if pen exceeds the active scrolling area (currently the scroll then goes to the new area under pen)?

---

### Post by modmadmike on 2008-09-15
Will this work with a wacom intous3 tablet?

---

### Post by Tom Jaeger on 2008-09-15
> **pibach said:**
> the cursor should change to indicate scroll mode (and further visualisation of the scroll gesture is not needed then).

Well, X11 cursor handling leaves a lot to be desired, the best I could do is a flickering cursor (like in the original scroll mode), but even that requires a nasty hack that I'm actually kind of happy to have gotten rid of.

> I would prefere the latter, but here timeout seems to be a tad too aggressive - I am using medium profile).
./easystroke -e gives you more fine-grained control over timeouts.

> 
BTW, I get segmentation fault when returning to old version, seemingly because format of gesture file has changed.

Yup, this is how things stand, unfortunately.  I might roll my own serialization code someday that fixes the issue, but until then, backups are necessary before every upgrade.

> 
Edit: still it is a bit difficult to scroll list boxes etc. Thinking for some intuitive solution. Would it, for example, be possible to scroll further if pen exceeds the active scrolling area (currently the scroll then goes to the new area under pen)?
This has been bothering me, too, but I don't see a way around the current behavior.  The problem is that X11 treats scroll wheel events as (button 4-7) clicks, which are always sent to the application under the cursor.  And with absolute devices, I can't move the cursor before emitting a click.

---

### Post by Tom Jaeger on 2008-09-16
> **modmadmike said:**
> Will this work with a wacom intous3 tablet?

I don't see why it wouldn't.

---

### Post by pibach on 2008-09-17
> **Tom Jaeger said:**
> 
./easystroke -e gives you more fine-grained control over timeouts.

Thanks for the hint, this was helpful. I configured scroll to trigger on a simple left click and changed timeout setting a bit. But this timeout of course can conflict with other intended slides. Still not sure which configuration might be best. How do others use it?

> 
The problem is that X11 treats scroll wheel events as (button 4-7) clicks, ..
Ok, I see. So what about a "circular scroll" approach? Synaptics is calling it "Chiral Motion".

Another problem still remains and might be related: the middleclick (or mousewheel or pen) scrolling is not as responsive as the grab & drag  (or scrollbar) scrolling is. Seems to be two different scrolling mechanisms.

Btw, I get the following errors:

** (easystroke:21626): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/OSX-theme-mod/gtk-2.0/Range/null.png,
borders don't fit within the image
XError: BadWindow (invalid Window parameter): X_QueryTree
Info: Device Presence not implemented

seemingly my Gtk-Theme is corrupted?

---

### Post by GrouchoMarx on 2008-09-17
Thanks for this great app! Super useful. I second these suggestions:

> **Gan Quan said:**
> Just two suggestions:
1. Application dependent gesture settings, allow gestures to behave differently in different applications.
2. Hide the tray icon.

Is there currently no way to remove the tray icon?

---

### Post by Tom Jaeger on 2008-09-17
> **pibach said:**
> Ok, I see. So what about a "circular scroll" approach? Synaptics is calling it "Chiral Motion".
Interesting idea.  I'll prototype it to see if it is a viable solution.

> 
Another problem still remains and might be related: the middleclick (or mousewheel or pen) scrolling is not as responsive as the grab & drag  (or scrollbar) scrolling is. 

Scroll wheel events are discrete, so there's nothing I can do here.  Maybe in a few years if the [scroll wheel as valuator thing]("http://thread.gmane.org/gmane.comp.freedesktop.xorg/31201/focus=31202") actually happens.

> 
Btw, I get the following errors:

** (easystroke:21626): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/OSX-theme-mod/gtk-2.0/Range/null.png,
borders don't fit within the image
XError: BadWindow (invalid Window parameter): X_QueryTree
Info: Device Presence not implemented

They're all harmless.

---

### Post by Tom Jaeger on 2008-09-17
> **GrouchoMarx said:**
> 1. Application dependent gesture settings, allow gestures to behave differently in different applications.
I'm working on this right now, but it will take a while as I have a lot of other things going on at the moment.

> 2. Hide the tray icon.
I suppose it would be nice if this were possible, but it's not a very high priority.

---

### Post by pibach on 2008-09-17
> **Tom Jaeger said:**
> 
Scroll wheel events are discrete, so there's nothing I can do here.  
Yes sure. And I am using "Yet another Scrolling Extension" to smooth this out a bit. But somehow scrolling with grab & drag extension is slightly better regarding responsiveness. And ultimately only the best solution will succeed. The scrolling issue is very important, as in tablet mode the main activity typically is reading text (Web, PDF, or Word) while using the pen for navigating and commenting. So we might need some further brainstorming and discussion how to make this as smooth and intuitive as possible. E.g., one option might be to use easystroke scroll in all apps but grab & drag scroll in Firefox as an exception. Also an open question is what to do about scrolling in inking apps such as xournal (as this requires to be an exception to enable the inking).

Just a remark on todays compiz update (I already moved to Intrepid Ibex): this seems to improve scrolling performance. Still not as responsive as native Metacity, but it comes close now (before it was a factor of 2 difference).

---

### Post by ericesque on 2008-09-17
Fantastic work, Tom.  I saw this covered on Lifehacker a few days ago and HAD to boot into Ubuntu for the first time in a while (been gaming a lot lately) just to try it.

I particularly like to use it to issue commands for Compiz Fusion since all the keystroke combinations are so similar and difficult for me to remember.

I'm not using gestures for launching applications, but rather as a method of interacting with the GUI.  So rotating the cube, max, min, close, show desktop etc. are all handled by gestures that make sense to me.  It makes the OS feel so interactive!! The next best thing to touch commands!

Thanks again!

---

### Post by lovinglinux on 2008-09-21
Thank you. Very useful application.

---

### Post by hongleong on 2008-09-23
Hi Tom,

Thanks for sharing your useful program with the rest of us.

Btw, I noticed that if I were to disable the popup feedback by unchecking Preferences > Show Popups, it'll get automatically checked again after I restart the program. Any idea how to fix this?

Thank you.
hongleong

---

### Post by Tom Jaeger on 2008-09-23
> **hongleong said:**
> Btw, I noticed that if I were to disable the popup feedback by unchecking Preferences > Show Popups, it'll get automatically checked again after I restart the program. Any idea how to fix this?

Thanks, this is indeed a bug (I'll provide updated packages in my PPA tomorrow).  As a workaround you can change any other option and then change it right back, this will save all the options.

---

### Post by hongleong on 2008-09-23
Yep, that works. Thanks. :)

---

### Post by russo.mic on 2008-09-29
Totally beats gestix.  Keep up the great work!  Thanks!

Russo

---

### Post by Luffield on 2008-09-30
I just upgraded to Intrepid beta and easystroke lost some functionality - key combinations work, but commands don't. Anyone else experiencing this problem? Is there a way to fix it?

---

### Post by Tom Jaeger on 2008-09-30
> **Luffield said:**
> I just upgraded to Intrepid beta and easystroke lost some functionality - key combinations work, but commands don't. Anyone else experiencing this problem? Is there a way to fix it?

I can't reproduce this issue on the latest intrepid with easystroke from intrepid.  What is the command that is not working?

---

### Post by Luffield on 2008-10-01
I have a gesture to launch nautilus and it does nothing, although it is recognized. However, today the gestures to launch gedit and firefox do work - but last night they didn't.

---

### Post by Tom Jaeger on 2008-10-02
> **Luffield said:**
> I have a gesture to launch nautilus and it does nothing, although it is recognized. However, today the gestures to launch gedit and firefox do work - but last night they didn't.

The problem is that nautilus won't open a window if the DESKTOP_AUTOSTART_ID environment variable is set (which is the case if easystroke is autostarted).  The problem disappears after easystroke is restarted.

I've fixed this issue in git by unsetting the environment variable at startup, but the fix probably won't end up in intrepid.  I will eventually make it available through my PPA, though.

As a workaround, you can manually unset the environment variable before starting nautilus, i.e. use
```
unset DESKTOP_AUTOSTART_ID; nautilus
```
as the command.

---

### Post by Luffield on 2008-10-03
Thanks Tom!

---

### Post by olejorgen on 2008-10-05
How do I open the config gui?
```

ole:~$ easystroke
Error: Couldn't read action database.
Error: Couldn't read preferences.

```
PS: I'm running a somewhat non-standard system. Debian unstable with ion3 (WM)

---

### Post by Tom Jaeger on 2008-10-05
> **olejorgen said:**
> How do I open the config gui?
```

ole:~$ easystroke
Error: Couldn't read action database.
Error: Couldn't read preferences.

```
PS: I'm running a somewhat non-standard system. Debian unstable with ion3 (WM)

The configuration dialog is opened via the tray icon, which you don't see because ion doesn't support the tray specification for [ideological reasons]("http://modeemi.fi/~tuomov/ion/faq/features.html").  I don't know what the external programs are that he is talking about, but I suppose gnome-panel will work.

---

### Post by olejorgen on 2008-10-05
Yes, I suspected something like that. Would you consider adding a simple command switch(*) for starting with the configuration window? Obviously not a big deal, but I think it's good principle to force as little as possible on people

(*) or accepting a non-intrusive patch

gnome-panel is a pain beacuse it totally ignores the WM. lxpanel works

---

### Post by Tom Jaeger on 2008-10-05
> **olejorgen said:**
> Yes, I suspected something like that. Would you consider adding a simple command switch(*) for starting with the configuration window?

I've committed a patch to master and the stable branch.  Eventually, you'll be able to show/hide the main window using a gesture, but that will require some unpleasant cellrenderer hackery first.

---

### Post by Tom Jaeger on 2008-10-10
> **Tom Jaeger said:**
> Eventually, you'll be able to show/hide the main window using a gesture, but that will require some unpleasant cellrenderer hackery first.

I've implemented this in master now (type = Misc, argument = Show/Hide).

---

### Post by realn on 2008-10-13
Thank you. That's one of my favourite apps. And I'm using it for only 1 hour.

---

### Post by Tom Jaeger on 2008-10-22
Here's a little preview of what 0.3.0 is going to bring.  The biggest new feature is certainly application-dependent behavior.
To use the feature, simply open the "Applications" expander add the application that you want to give special treatment to to the list.  As long as this application is selected, all changes you make to the actions list will be restricted to that application. So for example if you "delete" an action, it will still be recognized in all other applications, and you can actually restore it by enabling the "show deleted rows" option and then resetting the action.

Less notable features include
[LIST]
[*] It is now possible to assign a different button for a particular application (e.g. xournal) in the exceptions list
[*] Timeout gestures have already been mentioned in this thread
[*] Easystroke can be disabled for specific devices
[*] Actions can now be executed from the command line using *easystroke send "foo"* if the action is named foo.  This is equivalent to *dbus-send --type=method_call --dest=org.easystroke /org/easystroke org.easystroke.send string:"foo"*
[*] You can disable easystroke using the tray menu or by a gesture
[*] There are 3 new actions if you select "Misc" as the action type: "unminimize" undos the last minimize actions, "Show/Hide" brings up or hides the configuration dialog and "Disable (Enable)" disables (or enables if you invoke the action from the command line) the program.
[*] I've given up on changing the pointer in scroll mode.  There's a blue popup in the upper right corner of the screen now instead.
[*] I've dropped support for some of the advanced features when xinput is not available.  This was a nightmare to maintain and xinput shouldn't be a issue anymore on recent x servers.
[*] Due to popular demand, I've introduced an option to change the stroke color
[*] I've probably forgotten a few things, I'll add them to the list as I think of them.
[/LIST]

As always, since this is a pre-release version, I strongly recommend to make a backup of your ~/.easystroke directory before testing it.  Also, since I've made a few changes to the fragile ecosystem that is event handling, so look out for regressions.

EDIT: Removed the binary, see the latest snapshot at the end of this thread instead.

---

### Post by sarah.fauzia on 2008-10-25
> **Tom Jaeger said:**
> Hi,

I'd like to announce [easystroke]("http://easystroke.sourceforge.net"), a new gesture recognition application for linux.  Gesture recognition means that you can draw arbitrary curves on the screen by holding down a specific mouse button, and if the program recognizes their shape, it will perform certain actions.  For example, you can configure easystroke to maximize the current window if you draw a straight line in North-East direction.

My primary motivation for writing easystroke was to allow easy operation of a Tablet PCs even without a keyboard present, but of course it will work just as well with a mouse.  It is not meant to replace an onscreen keyboard/input panel such as cellwriter, but rather supplement it.

Here's a short list of the program's main selling points:
[LIST]
[*] It aims to be easy to set up and to configure.  There are no configuration files that need to be edited and no cryptic commands that have to be entered somewhere.
[*] It tries to give the user easy access to the most commonly used features:  Setting up a new gesture requires just a few clicks and will show only one small popup dialog (to actually define the stroke)
[*] It allows you to use strokes of arbitrary shape.  There is no requirement that gestures have to be composed of line segments, and curvy shapes such as an 'S' or a 'G' work just fine.
[*] Some of the features make life without a keyboard a lot easier: You can emulate a scrollwheel, ignore the next stroke and pass the next mouse action to the application (possibly with a modifier held down, so that you can Alt-move or Alt-resize a window without a keyboard) and emulate an additional button that your tablet pen didn't even have in the first place.
[*] The project is still young, so there's much more to come.
[/LIST]

EDIT (Aug 3):  The latest version is 0.2.1.  See [this post]("http://ubuntuforums.org/showpost.php?p=5519620&postcount=118") for details.
EDIT (Aug 17): Released 0.2.2. 

The program is available as a .deb package tested on Ubuntu Hardy, a source tar.gz, and a standalone binary.  It is also available through my [launchpad PPA]("https://launchpad.net/~thjaeger/+archive").  There are a few screenshots on the project's [documentation page]("http://easystroke.wiki.sourceforge.net/Documentation").

Thank you,
Tom

I must say that your program is absolutely amazing! I'm running it in Intrepid and it's working perfectly; I was always annoyed that I could not use my computer well in tablet mode because I couldn't use my on-screen keyboard (from CellWriter) to prompt Compiz commands (such as Alt-Super, then Button 1) to toggle Annotate. My only concerns are two--one of which is a limitation of the Annotate plugin. After activating it, it only stays activated for as long as my pen is on the screen--as soon as I lift it, it's untoggled. The compiz documentation for Annotate says to hold down on the Alt-Super keys in order to be able to lift the pen and continue writing... is there a way easystroke could simulate a repeat keypress? If it's already a feature, I would appreciate if you could clarify it for me--I'm new to this, and I enjoy this software tremendously! It's far, far superior to Vista pen flicks.

The other quirk is that the EasyStroke icon always shows the last used gesture... but it defaults to the blue X which doesn't look so nice (and I must say, overall, the GUI is fantastic). Is there a possibility to let it default to the original easystroke icon, and not the last used stroke?

---

### Post by Tom Jaeger on 2008-10-26
> **sarah.fauzia said:**
> My only concerns are two--one of which is a limitation of the Annotate plugin. After activating it, it only stays activated for as long as my pen is on the screen--as soon as I lift it, it's untoggled. The compiz documentation for Annotate says to hold down on the Alt-Super keys in order to be able to lift the pen and continue writing... is there a way easystroke could simulate a repeat keypress? If it's already a feature, I would appreciate if you could clarify it for me--I'm new to this, and I enjoy this software tremendously! It's far, far superior to Vista pen flicks.

This is intentional.  Easystroke uses the annotate plugin to draw the current gesture on the screen to give the user instant feedback and then immediately clears the screen as soon as the gesture is over.  If you want to use easystroke to actually use the annotate plugin to draw something, you should use another method to draw the gesture line and then set up an ignore gesture with Alt+Super as the argument.  This works best if the "Stay in scroll or ignore mode..." option is enabled.  Alternatively, an Alt+Super+Button1 advanced gesture will also work.

> 
The other quirk is that the EasyStroke icon always shows the last used gesture... but it defaults to the blue X which doesn't look so nice (and I must say, overall, the GUI is fantastic). Is there a possibility to let it default to the original easystroke icon, and not the last used stroke?
There's really not much of a point in the tray icon changing anymore now that we have popup notification, so I've removed this behavior in master.  In case someone complains, I will revert that change and make this an option.

---

### Post by Tom Jaeger on 2008-10-26
Here's another beta.  The stroke previews look much better now and it is finally possible to reorder the list of actions using drag and drop, which turns out to be more painful than I anticipated, so I will probably move to a tree-based concept in the future that would make it possible to group actions.  This version might still be a little unstable.

---

### Post by sarah.fauzia on 2008-10-26
> **Tom Jaeger said:**
> This is intentional.  Easystroke uses the annotate plugin to draw the current gesture on the screen to give the user instant feedback and then immediately clears the screen as soon as the gesture is over.  If you want to use easystroke to actually use the annotate plugin to draw something, you should use another method to draw the gesture line and then set up an ignore gesture with Alt+Super as the argument.  This works best if the "Stay in scroll or ignore mode..." option is enabled.  Alternatively, an Alt+Super+Button1 advanced gesture will also work.


There's really not much of a point in the tray icon changing anymore now that we have popup notification, so I've removed this behavior in master.  In case someone complains, I will revert that change and make this an option.

I think didn't clarify what I meant about the Annotate plugin. I used Easystroke to *activate* the Annotate plugin (in addition to using it to draw the current gesture). However, the Annotate plugin only stays active, after I've drawn the gesture I keyed to Annotate, for as long as my pen is on the screen. As soon as I lift the pen, then it deactivates (like the documentation says it would, but "holding" on Super-Alt would enable it to stay toggled). I do have it in ignore mode (that enabled me to key the gesture to just Super-Alt). If I misunderstood you, then I'd appreciate the clarification :)

I'll definitely appreciate the change to the tray icon--I think I'll download that new beta!

---

### Post by GrouchoMarx on 2008-10-29
It might improve usability if the gesture icons would in some way indicate a failed gesture. On a slow system (compiling) or with certain commands (firefox), it often takes some time to realize that the gesture didn't work. Conversely, sometimes you think it failed when it didn't, and you accidentally start another process. Some feedback for failed gestures, like a small red 'x' in the corner of the icon, might help.

Anyways, really appreciate your work on this great project. Easystroke has been very useful! Thanks!

---

### Post by Luffield on 2008-10-29
I like your idea a lot, GrouchoMarx.

---

### Post by Tom Jaeger on 2008-10-31
Sorry for the late reply, I've been busy with other things.

> **sarah.fauzia said:**
> I think didn't clarify what I meant about the Annotate plugin. I used Easystroke to *activate* the Annotate plugin (in addition to using it to draw the current gesture). However, the Annotate plugin only stays active, after I've drawn the gesture I keyed to Annotate, for as long as my pen is on the screen. As soon as I lift the pen, then it deactivates (like the documentation says it would, but "holding" on Super-Alt would enable it to stay toggled). I do have it in ignore mode (that enabled me to key the gesture to just Super-Alt). If I misunderstood you, then I'd appreciate the clarification :)
I think I see what you're saying now.  You want easystroke to stay in ignore mode until *a particular* mouse button is pressed.  That's a reasonable suggestion, but I'm not sure yet in how much generality the idea should be exposed or how the best UI for it would look like.  It don't think it will happen before 0.3.0, but I'll keep the idea in mind.

---

### Post by Tom Jaeger on 2008-10-31
> **GrouchoMarx said:**
> It might improve usability if the gesture icons would in some way indicate a failed gesture. On a slow system (compiling) or with certain commands (firefox), it often takes some time to realize that the gesture didn't work. Conversely, sometimes you think it failed when it didn't, and you accidentally start another process. Some feedback for failed gestures, like a small red 'x' in the corner of the icon, might help.

Right now, we have notification of successful gestures by popups and of failed gestures by the "bell".  I've implemented the suggestion in git for now (see the attached snapshot, and remember to keep backups), but I can't say I like the behavior very much.

---

### Post by sarah.fauzia on 2008-10-31
[COLOR="Silver"]I know I mentioned before not wanting to see the last stroke in the notification icon, but now I request that you keep it that way, because I've disabled Compiz as it's interfering with screen rotation (see my post on [this]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/132065") launchpad bug). Unless that's fixed, I don't think I'll be using any compositing manager in the future, not even metacity's, for that gave me trouble as well (and I'm worrying about it ruining my computer...I've been getting really nasty artifacts). Not meaning to go off tangent on this thread's discussion, but I just wanted to give my input on this (as Tom said he'd take out the feature unless anyone specially requested it :) ).[/COLOR]

I apologize for the fickleness, but I actually appreciate the new version more (without the show gesture feature in the notification icon, despite not using compiz). It looks much more tidier, and I'm all-around impressed by the new features--the touch support is wonderful! I'm so glad I can map a gesture to right-click and right-click with my finger now :). If this was a feature before, I had not noticed it... I definitely noticed the new feature of rearranging gestures, and this was also a big bonus.

Thanks for the great update, Tom! :)

---

### Post by sarah.fauzia on 2008-11-08
I've been really enjoying making gestures for specific applications, especially Xournal. It now has me worried though; I have so many gestures, what would I do if my computer crashed? Or what if I wanted to use the same gestures on another tablet? I think it'd be really good if easystroke had its own special backup utility, just to backup preferences and gestures (to a user-specified backup location). It'd give me a lot less to worry about then! :)

I also like the new feature to temporarily disable easystroke. It's been tremendously useful! In firefox, easystroke tends to interfere with browsing, but I still want it enabled when I want to copy, paste, etc. So I temporarily disable it and re-enable it when I need it again. Thanks for all the work you've put into this program! :)

---

### Post by pibach on 2008-11-09
> **sarah.fauzia said:**
> I've been really enjoying making gestures for specific applications, especially Xournal.

How do you do that? I had to put xournal on the list of exceptions, to make easystroke not interfere with xournal's inking. 

>  In firefox, easystroke tends to interfere with browsing...
I use easystroke most in Firefox. Works perfectly, no interference. I have it on left click, so I do not need to press the button. G&D scrolling works fine too since Tom has incorporated the gesture timeout. To open links in new tabs I use Quickdrag extension. 

Also the scroll gesture is very useful, e.g., to scroll in PDF documents. Still here is some room left for improvements (e.g., "circular scroll").

Another small feature request: I would like to be able to verify the installed version to figure out whether updates did succeed - as there was the update yesterday. 

I still have to play with the new features. Any experiences how to use the new app-based gestures? And where can I configure the "bell" that informs me of an unrecognised gesture?

---

### Post by sarah.fauzia on 2008-11-09
If you go to Preferences under Easystroke, there are two columns under Exceptions--Applications, and Button. If you change the button modifier to Button3 (right-click), rather than leaving it as the default (<App disabled>), then you can use all your regular gestures, plus the gestures you configure specially for the specific application (they appear in bold, even the gestures themselves, so you can tell them apart that way), except, while holding down the right-click. For me that isn't hard with my tablet pen, and perhaps it'd be similarly easy for you.

As for the problem I have with firefox, I agree, it's very useful to use gestures in firefox. And if I change the timeout, then it's very convenient (I don't then experience problems such as, when selecting text, it thinks it's my gesture for the Space key). But the con to changing the timeout is that then some of my more advanced gestures (advanced as in the complexity of the shape, without lifting the pen), don't work. I have to repeat the same gesture a few times for it to then finally register. So that's why I prefer temporarily disabling easystroke.

[edit] I just checked, I've already set the gesture button for gestures in firefox to Button3, like I was just thinking to do after typing this post! [/edit]

---

### Post by Tom Jaeger on 2008-11-10
> **sarah.fauzia said:**
> I've been really enjoying making gestures for specific applications, especially Xournal. It now has me worried though; I have so many gestures, what would I do if my computer crashed? Or what if I wanted to use the same gestures on another tablet? I think it'd be really good if easystroke had its own special backup utility, just to backup preferences and gestures (to a user-specified backup location). It'd give me a lot less to worry about then! :)
easystroe saves all its information in the ~/.easystroke directory, so it should be easy to back up.  Gesture import/export is planned for a later version (probably not anytime soon, though, because I have to work out issues with boost::serialization, which causes segfaults on invalide data).

> **pibach said:**
> 
Another small feature request: I would like to be able to verify the installed version to figure out whether updates did succeed - as there was the update yesterday. 
*easystroke --version* will show the version string.

> And where can I configure the "bell" that informs me of an unrecognised gesture?
Supposedly the bell can be configured in gnome under System->Preferences->Sound.  But I disabled it and I'm using a compiz effect instead.

---

### Post by imnotashinobi on 2008-11-12
Amazing application! I love using mouse gestures and would probably love using gestures on a tablet [when i can afford one]. I used to miss autohotkey from my days in xp, until I found easystroke. The only feature I miss now is universal text replacement; I didn't bother much with autohotkey's other abilities. Anyways, the new features in easystroke are great, but I have one request:

Confirmation on "Remove Application/Group".

I don't know if this was asked before, but it would be nice to have. I found out there was no confirmation dialogue the hard way :P. Can't wait to see what is planned next! I even subscribed to SF.

Cheers!

---

### Post by realthor on 2008-11-12
Hello,

I have just started with your application as it's one of my last things to improve on desktop usability, together with gnome-do and different plugins/settings in compiz. I find your app great and would like to report a little on it:

**1st**: I guess this is a bug...I open nautilus, then go to any picture, open it, it opens with eog and then I perform a close app gesture (the famous DR ) and instead of closing the eog nautilus is closed as if it would be in focus. I first suspected that my setting in compiz regarding "Click to focus" which isn't checked could be to blame but I have tried moving eog to be sure it has the focus and the same result.
 
Can this be replicated?

**2nd**: This is a suggestion: In firefox the gestures are very simple, like U,D,L,R and any combination of these ones. This is great for working with a mouse and there is little space for missinterpretations. Can you PLEASE add a checkbox to make each gesture an approximative shape of the real thing (in Adobe Flash if i remember well there is a function to "round" shapes drawn with freehand)

It would be great if each gesture could be approximated to segments of straight lines like up-down, left-right and oblique.

**3rd**: This is a question :P : I could be wrong here but i guess when I define the same gesture for a specific app -that is defined also globally- the first one takes precedence?! This would be very helpful in a close tab/close app scenario where on applications that have tabs the gesture would close the current tab and in apps that have no tabs it would close the app.

Also here the U,D,L,R, and all oblique variations will be quite helpful as an Down+Right gesture like in firefox wouldn't be ignored if the Right part is too long drawn or mixed up with the Down-only gesture (imagine minimize) if the Right part is to short. At least that's what happened to me.

Best regards and can't wait for an answer to these issues.

---

### Post by Tom Jaeger on 2008-11-13
> **imnotashinobi said:**
> The only feature I miss now is universal text replacement; I didn't bother much with autohotkey's other abilities.
autokey ([http://autokey.sourceforge.net/](http://autokey.sourceforge.net/)) might be what you're looking for (never tried it myself).

> Confirmation on "Remove Application/Group".
Thanks, I was going to add that, but then somehow forgot.  This is fixed in git now and will be part of the next release.

---

### Post by Tom Jaeger on 2008-11-13
> **realthor said:**
> **1st**: I guess this is a bug...I open nautilus, then go to any picture, open it, it opens with eog and then I perform a close app gesture (the famous DR ) and instead of closing the eog nautilus is closed as if it would be in focus. I first suspected that my setting in compiz regarding "Click to focus" which isn't checked could be to blame but I have tried moving eog to be sure it has the focus and the same result.
 
This is actually intentional, and I go to considerable lengths to track which window the cursor is in and then give it focus when a gesture is performed.  It never occurred to me that someone might not want that feature, but if this is important to people, I might consider making it an option.

> 
**2nd**: This is a suggestion: In firefox the gestures are very simple, like U,D,L,R and any combination of these ones. This is great for working with a mouse and there is little space for missinterpretations. Can you PLEASE add a checkbox to make each gesture an approximative shape of the real thing (in Adobe Flash if i remember well there is a function to "round" shapes drawn with freehand)

It would be great if each gesture could be approximated to segments of straight lines like up-down, left-right and oblique.

Easystroke doesn't store gestures as sequences of straight lines because this is impractical for many use cases (especially on tablets).  This allows for a much wider range of shapes that can be used as gestures.

> 
**3rd**: This is a question :P : I could be wrong here but i guess when I define the same gesture for a specific app -that is defined also globally- the first one takes precedence?! This would be very helpful in a close tab/close app scenario where on applications that have tabs the gesture would close the current tab and in apps that have no tabs it would close the app.

There is no notion of gestures being "the same".  easystroke computes a score that reflects how closely two gestures match, which never is 100% since it's practically impossible to draw two identically gestures.  So in your situation it would appear more or less random which of the two gestures easystroke chooses.  You have two options here:
(1) While the application is selected, just change edit the action for that gesture, it will become bold to indicate that it is different than the default action for that gesture.
(2) Delete the gesture for the application (it can be restored be enabling the option 'show deleted rows' and then resetting the deactivated row) and then create a new one.
Editing a particular application will never affect the default gestures in any way.

---

### Post by realthor on 2008-11-13
[INDENT]> This is actually intentional, and I go to considerable lengths to track which window the cursor is in and then give it focus when a gesture is performed. It never occurred to me that someone might not want that feature, but if this is important to people, I might consider making it an option.
[/INDENT]

As long as I believe that the highest window in the stack is the one the user is focusing his attention at it would be grat such an option as it's easier to close a window by a mouse gesture than trying to reach the X button every time...considering that different sizes winows have different positions for the button.

[INDENT]> Easystroke doesn't store gestures as sequences of straight lines because this is impractical for many use cases (especially on tablets). This allows for a much wider range of shapes that can be used as gestures.[/INDENT]

Yas it's obvious EasyStroke focuses more on the tablet market but I guess unless all laptops at least will get a touch-screen 95% of the users of your software are mouse-users and from a mouse-gesture point of view it's impractical to create two similar strokes because you'll never make the exact shape of a gesture (most often mouse-gestures exist for speed and you draw an "L" shape to close an app it's always an "L" but sometimes you make it longer on the H axis , other times on the Y axis).
This is why as a mouse user focused on speed an option like "fidelity of capture" to be set to high and low (low would be to aproximate to a few line segments) would be great but it's your choice to implement it of course.

Best Regards and keep it up.

---

### Post by imnotashinobi on 2008-11-14
Thank you very much for the link, Tom. autokey doesn't seem to do anything[?], but I appreciate the heads up. It does seem to be what I'm looking for though. I'll have to go bother the author about it later.

Oh well... on to easystroke matters...
These are pretty much cosmetic matters: I believe the "Timeout Gestures" checkbox should be moved from the "Advanced" tab to the "Preferences" tab. It just makes more sense. The "Timeout profile" drop-down menu is right there. Or, perhaps, switch them? Just my little bit of user interface criticism. Take it or leave it, it's a small matter.

Now for a new "problem" [as in minor, unoccasional annoyance] I found. Would it be possible for the click NOT to go through on timeouts? I prefer to use Button 3 for gestures. However, this produces right clicks at inopportune times.

How do we get this app into the official Ubuntu repositories? It's already so polished and reliable. I can't wait to see what's planned for in the next release. My guess: a popup menu for gestures that are equal to or less than a user-defined percent from each other in response to a gesture that shows enough potential to be another one, thus allowing for two [or more] commands to have nearly identical gestures while still allowing for the user to easily select between them. I've obviously been staring at the "History" tab for too long; but I think that'd be neat!

---

### Post by GrouchoMarx on 2008-11-14
Hi Tom,

Thanks for the update. When using version

```
easystroke 0.3.0-0ubuntu1~ppa1~hardy
```

I receive the following error on startup:
```
XError: BadAccess (attempt to access private resource denied): X_GrabKey
```

Also, if I hide the tray icon in the preferences, easystroke segfaults on the next attempted gesture.

Let me know if you need any system info.

Besides that, you said that you weren't happy with the check mark and red circle in the system tray icon. An alternative solution would be to show the previous gesture in blue and green if successful (like before), and have failed gestures show in red. No additional emblems would be necessary.

Cheers

---

### Post by realthor on 2008-11-14
Man, I am really getting to realize the power of easystroke. The more gestures I define the less chances are easystroke will mix up gestures.
As long as there are unique shaped gestures for each action it is ok.

I would like to make a couple of suggestion and hear from wou what you think of them:

- the first one i still believe is a bug, as the starting point of my gesture is inside of the eog window, not over the below nautilus window. I agree with closing the app below the starting point of the mouse gesture. Anyway this isn't crucial as I think I can track the active window by xprop's _NET_ACTIVE_WINDOW(WINDOW).

-second it would be nice to make the argument somehow recursive and have a "Add Argument" button for the situations you want a few actions to be played one after another. Nothing that ca't be made with a command type and a script as an argument but we're for user friendly stuff right?

- the most important would be to move the contextual menu a few pixels away for users that use right click for "gesture button" because I get too many clicks on the first option in the contextual menu.

Thanks a lot for your work and hope our suggestion can help the app become better.

---

### Post by Tom Jaeger on 2008-11-15
> **realthor said:**
> 
Yas it's obvious EasyStroke focuses more on the tablet market but I guess unless all laptops at least will get a touch-screen 95% of the users of your software are mouse-users and from a mouse-gesture point of view it's impractical to create two similar strokes because you'll never make the exact shape of a gesture (most often mouse-gestures exist for speed and you draw an "L" shape to close an app it's always an "L" but sometimes you make it longer on the H axis , other times on the Y axis).
This is why as a mouse user focused on speed an option like "fidelity of capture" to be set to high and low (low would be to aproximate to a few line segments) would be great but it's your choice to implement it of course.
There is no question that the recognition algorithm could be improved.  I have a few thoughts on how this can be done, but the problem is highly non-trivial and the need for an algorithm that is not too computationally intensive makes it even more challenging.  I don't think restricting my attention to a particular use-case is the solution.


> **imnotashinobi said:**
> 
Oh well... on to easystroke matters...
These are pretty much cosmetic matters: I believe the "Timeout Gestures" checkbox should be moved from the "Advanced" tab to the "Preferences" tab. It just makes more sense. The "Timeout profile" drop-down menu is right there. Or, perhaps, switch them? Just my little bit of user interface criticism. Take it or leave it, it's a small matter.
The idea here was most users are probably not going to use timeout gestures, which is why I relegated them to the advanced tab.

> 
Now for a new "problem" [as in minor, unoccasional annoyance] I found. Would it be possible for the click NOT to go through on timeouts? I prefer to use Button 3 for gestures. However, this produces right clicks at inopportune times.
Where do these spurious right-clicks come from?


> How do we get this app into the official Ubuntu repositories? It's already so polished and reliable.
Version 0.2.1.1 is already in intrepid, but I haven't taken the time to request an update to 0.3.x for jaunty yet.  I'll probably wait for at least 0.3.1 for that, but I'll be updating my PPA regularly.

> I can't wait to see what's planned for in the next release. My guess: a popup menu for gestures that are equal to or less than a user-defined percent from each other in response to a gesture that shows enough potential to be another one, thus allowing for two [or more] commands to have nearly identical gestures while still allowing for the user to easily select between them. I've obviously been staring at the "History" tab for too long; but I think that'd be neat!
Thanks, this is a good idea and probably not too hard to implement.

> **GrouchoMarx said:**
> Hi Tom,
Thanks for the update. When using version
```
easystroke 0.3.0-0ubuntu1~ppa1~hardy
```
I receive the following error on startup:
```
XError: BadAccess (attempt to access private resource denied): X_GrabKey
```

This is not a big deal, it just means that you won't be able to use Esc to cancel gestures.

> 
Also, if I hide the tray icon in the preferences, easystroke segfaults on the next attempted gesture.

Thanks, fixed in git.  This is the reason why I'm always a little reluctant to introduce new options: They greatly increase the potential for regressions.


> **realthor said:**
> 
- the first one i still believe is a bug, as the starting point of my gesture is inside of the eog window, not over the below nautilus window. I agree with closing the app below the starting point of the mouse gesture. Anyway this isn't crucial as I think I can track the active window by xprop's _NET_ACTIVE_WINDOW(WINDOW).

The intended behavior is for the application where the gesture started to get focus, so yes, this looks like a bug.  What window manager are you using?  Also, can you confirm that the bug doesn't happen if you move the cursor out of the eog window first and then back in?

> 
-second it would be nice to make the argument somehow recursive and have a "Add Argument" button for the situations you want a few actions to be played one after another. Nothing that ca't be made with a command type and a script as an argument but we're for user friendly stuff right?

If you just need a sequence of commands, you can use 'foo; bar; ...; baz' since commands are executed in a shell; I don't think there's a need for a fancy gui here.  If you're trying to mix commands with key presses, I'd be interested in a use case.

> 
- the most important would be to move the contextual menu a few pixels away for users that use right click for "gesture button" because I get too many clicks on the first option in the contextual menu.

I can't control the position of context menus.  How do these spurious clicks come about, though?  Unintended timeouts?

---

### Post by Tom Jaeger on 2008-11-23
> **realthor said:**
> 
- the first one i still believe is a bug, as the starting point of my gesture is inside of the eog window, not over the below nautilus window. I agree with closing the app below the starting point of the mouse gesture. Anyway this isn't crucial as I think I can track the active window by xprop's _NET_ACTIVE_WINDOW(WINDOW).

Could you check if this bug is fixed in the attached snapshot?

---

### Post by realthor on 2008-12-02
Yes!!!This snapshot fixed the issue. Thanks.

---

### Post by realthor on 2008-12-02
Risking to get really annoying I have noticed that mouse detection is better without compiz that when special effects are activated. If I deactivate visual effects I seem to double the amount of pixels drawn on the screen by easystroke. This can be noticed when you draw very quickly a gesture, with compiz on sometime i get only the final one or two strokes. Can this be improved? Mouse gestures equals speed and making them in a speedy way makes the work more efficient... .

- pushing my luck: what about on-screen strokes with anti-aliasing, opacity, glow effects? Are they difficult to implement? You could use compiz effects to do this?

Thanks.

---

### Post by Tom Jaeger on 2008-12-02
> **realthor said:**
> 
- pushing my luck: what about on-screen strokes with anti-aliasing, opacity, glow effects? Are they difficult to implement? You could use compiz effects to do this?
The XShape extension and compiz don't play together very well.  I would therefore recommend to draw strokes via the 'annotate' plugin when running compiz (needs the 'dbus' plugin to be enabled).  This will also give you anti-aliasing and control over width and opacity (no glow effects, though).  This should probably be documented better, but I'm already behind on the documentation of the new features...

---

### Post by sarah.fauzia on 2008-12-06
Application specific gestures are not working in Kubuntu Intrepid. I thought it was my gesture button that was perhaps off (the right click button Button3), but even when I try in other applications (where I use Button1), easystroke will show the stroke being made (I have XShape enabled), but the gesture doesn't seem to register. In xournal, if I leave the gesture button as Button3, the gesture is not even drawn on the screen (unless I use Button1), but even then the gesture doesn't do anything. All other gestures that are not application-specific work perfectly! I'm not sure if you're planning to support KDE4, but I just tried it out (and like it), and would hope this bug is possible to fix. Thanks!

---

### Post by Tom Jaeger on 2008-12-06
> **sarah.fauzia said:**
> Application specific gestures are not working in Kubuntu Intrepid. I thought it was my gesture button that was perhaps off (the right click button Button3), but even when I try in other applications (where I use Button1), easystroke will show the stroke being made (I have XShape enabled), but the gesture doesn't seem to register. In xournal, if I leave the gesture button as Button3, the gesture is not even drawn on the screen (unless I use Button1), but even then the gesture doesn't do anything. All other gestures that are not application-specific work perfectly! I'm not sure if you're planning to support KDE4, but I just tried it out (and like it), and would hope this bug is possible to fix. Thanks!

Okay, so the kde window manager nests application windows more deeply than necessary (and gratuitously so; the parent of the application window has exactly the same geometry and only one child), which seems like a bad idea because it probably confuses more applications than just easystroke.  Anyway, I've implemented a breadth-first search when looking the application window, which should fix your kde issues and will hopefully have minimal impact on the behavior under other window managers.

---

### Post by sarah.fauzia on 2008-12-06
Could you possibly incorporate this as an update? It might be because I'm new to Kubuntu, but I'm having trouble executing the program from file. Again, thanks, I truly appreciate your quick response :)

---

### Post by Tom Jaeger on 2008-12-06
> **sarah.fauzia said:**
> Could you possibly incorporate this as an update? It might be because I'm new to Kubuntu, but I'm having trouble executing the program from file. Again, thanks, I truly appreciate your quick response :)
This needs more testing before I can release it.  I've repackaged the snapshot as a tar.gz, which preserves permissions and should therefore be easy to launch from the GUI.

---

### Post by sarah.fauzia on 2008-12-07
> **Tom Jaeger said:**
> This needs more testing before I can release it.  I've repackaged the snapshot as a tar.gz, which preserves permissions and should therefore be easy to launch from the GUI.

Hmm... it's still not opening Easystroke, after extracting the archive. Is this only for 32-bit Kubuntu? (just looking at the package name). I use 64-bit. 

It did occur to me later that it would be unwise to immediately upgrade it in the PPA (in case of regressions), but could you possibly include the whole source file in the archive, so I could install it from source? I hope it wouldn't be inconvenient.

---

### Post by Tom Jaeger on 2008-12-07
> **sarah.fauzia said:**
> Hmm... it's still not opening Easystroke, after extracting the archive. Is this only for 32-bit Kubuntu? (just looking at the package name). I use 64-bit.
Yes, sorry, the binary will only work in a 32-bit environment and I don't have a 64-bit installation that I could build this on.  See [the wiki]("http://easystroke.wiki.sourceforge.net/BuildInstructions") for instructions on how to build from source.  The following should work:

```

sudo apt-get install g++ libboost-serialization-dev libgtkmm-2.4-dev libxtst-dev libdbus-glib-1-dev
git clone git://github.com/thjaeger/easystroke.git
cd easystroke
make -j2
./easystroke

```

---

### Post by sarah.fauzia on 2008-12-08
Thanks Tom! Now Easystroke is working perfectly--but I had to disable KDE's desktop effects first (it was making the strokes render too slowly). No other quirks I can see other than Easystroke not showing up in my programs list in KDE; is there a way to specify the correct installation directory? I'm assuming that's why it isn't showing up, as I had to create some directories in /usr/share for it to install; specifically, */usr/local/share/applications* (where I had to create the *applications* folder), and */usr/local/share/icons/hicolor/scalable/apps* for the easystroke icon (where I had to create the *scalable* and *apps* folders). If I didn't create those directories, the installation would abort. I hope my input helps, and, again, thank you for responding so quickly! If you hadn't updated it for me Kubuntu would have been utterly useless without Easystroke!

I'm attaching the DEB package checkinstall created when I installed Easystroke, both for reference and if anyone needs it.

[EDIT] Actually, the default launcher for Easystroke is now appearing in the Kubuntu menu. I don't know if it's because I created a custom launcher and it did something, or if it took time... I do know that when I went and made the launcher, there wasn't yet a default launcher for Easystroke. [/EDIT]

---

### Post by imnotashinobi on 2008-12-10
is it not meant to work with caps lock on?

---

### Post by Tom Jaeger on 2008-12-11
> **sarah.fauzia said:**
> Thanks Tom! Now Easystroke is working perfectly--but I had to disable KDE's desktop effects first (it was making the strokes render too slowly).

Same comment as above, XShape and a composited desktop don't play along very well.  In compiz, I can work around this by using the annotate plugin to draw on the screen, not sure if there's something similar for the kde window manager.  I need to look into making 32-bit visuals work (I tried this once without any luck).

> 
 No other quirks I can see other than Easystroke not showing up in my programs list in KDE; is there a way to specify the correct installation directory?

```
make PREFIX=/usr install
```

> If I didn't create those directories, the installation would abort.
That's odd, 'install -D' should create those directories automatically.

---

### Post by Tom Jaeger on 2008-12-11
> **imnotashinobi said:**
> is it not meant to work with caps lock on?

Apparently X treats Caps Lock as a modifier again (last time I tested this, this wasn't the case).  Fixed in git and the attached snapshot.

---

### Post by imnotashinobi on 2008-12-12
Thanks! I was panicking the first time I disabled it via caps lock and wondered what happened to easystroke. ^_^;

---

### Post by zefew on 2008-12-14
Neither easystroke 3.0 nor git HEAD don't compile on gutsy. It's using 
format function which is not defined in the Glib::ustring header. Has anyone 
installed easystroke on gutsy successfully? If so how did you get around the error?

$ sudo apt-get install g++ libboost-serialization-dev libgtkmm-2.4-dev libxtst-dev libdbus-glib-1-dev
$ make -j2
...
stats.cc:116: error: ‘format’ is not a member of ‘Glib::ustring’
stats.cc:136: error: ‘format’ is not a member of ‘Glib::ustring’
stats.cc: In member function ‘void Stats::on_pdf()’:
stats.cc:226: error: ‘format’ is not a member of ‘Glib::ustring’
g++ -Wall  `pkg-config gtkmm-2.4 gthread-2.0 dbus-glib-1 --cflags` -Os -MT util.o -MMD -MP -MF util.Po -o util.o -c util.cc
make: *** [stats.o] Error 1
make: *** Waiting for unfinished jobs....

---

### Post by Tom Jaeger on 2008-12-15
> **zefew said:**
> Neither easystroke 3.0 nor git HEAD don't compile on gutsy.

The attached patch should do it.  Notice that easystroke isn't tested with the version of xserver that is in gutsy, and there's likely to be breakage.  You might need to start easystroke as "easystroke -x" to get gestures at all.

---

### Post by Tom Jaeger on 2008-12-15
I'd like to get a new version 0.3.1 out soon.  The biggest change is a new method to show gestures on a composited desktop.  Initial testing on my hardware looks promising, but I'd like to get some more testing done on different setups before I release it.  If I don't get any complaints, I'll update a new package to my PPA tomorrow.
Apart from that, I've fixed a few bugs since 0.3.0 and added an option to configure autostart.

---

### Post by zefew on 2008-12-15
> **Tom Jaeger said:**
> The attached patch should do it.  Notice that easystroke isn't tested with the version of xserver that is in gutsy, and there's likely to be breakage.  You might need to start easystroke as "easystroke -x" to get gestures at all.

Thanks for the patch, Tom.

Apart from `format' thing, which your patch resolves, I found there was another
errror:

	win.cc:197: error: ‘class Glib::RefPtr<Gtk::StatusIcon>’ has no member named ‘reset’

So i temporarily comment #197 out, after which the built went okay.  But, as
soon as I execute easystroke (either with -x or not), I get the following
segmentation fault.

| $ ./easystroke 
| XError: BadClass, invalid event class: request_code=147, minor_code=6
| 
| (easystroke:29334): gtkmm-CRITICAL **: gtkmm: object `treeview_actions' not found in GtkBuilder file.
| segmentation fault (core dumped)
| $ ./easystroke  -x
| 
| (easystroke:29343): gtkmm-CRITICAL **: gtkmm: object `treeview_actions' not found in GtkBuilder file.
| segmentation fault (core dumped)

Do you think I need a different version of libgtkmm? my system currently has:

libgtkmm-2.4-1c2a                               install
libgtkmm-2.4-dev                                install
libgtkmm-dev                                    install
libgtkmm1.2-0c2a                                install
libgtkmm2.0-1c2a                                install
libgtkmm2.0-dev                                 install

---

### Post by Tom Jaeger on 2008-12-15
> **zefew said:**
> 
	win.cc:197: error: ‘class Glib::RefPtr<Gtk::StatusIcon>’ has no member named ‘reset’

reset used to be called clear in earlier versions of gtkmm.

> 
| (easystroke:29334): gtkmm-CRITICAL **: gtkmm: object `treeview_actions' not found in GtkBuilder file.

Make sure that libxml2-utils is installed and rebuild.  You might need a newer version of the gtk-builder-convert script.

---

### Post by sarah.fauzia on 2008-12-23
I just installed openSUSE 11.1 on my system (the same x61 tablet), and again, this time, with KDE 4. I interestingly still needed to create the same folders in order for checkinstall to proceed (easystroke isn't in openSUSE's repos :(), and again I had to create a menu entry before a menu entry would appear. But, otherwise, easystroke seems to run without a hitch in openSUSE :)

[EDIT]Spoke slightly too soon. There appears to be an issue in portrait mode. I don't remember this occurring in Ubuntu, but it did happen in Kubuntu: When in portrait mode, and I make a gesture towards the bottom of the screen, only the top half of the stroke shows (if at all). It can get to the point where nothing shows. In Kubuntu (I haven't checked in openSUSE yet), disabling gestures showing on the screen... did not disable gestures from showing on the screen. But the stroke, despite it not showing properly, was properly recognized by Easystroke. Any thoughts? [/EDIT]

[EDIT] Checked in openSUSE, disabling gestures showing worked. It could be that I was using the Easystroke that you had just fixed for me (in Kubuntu), and not the latest 3.1 that was just released (as I am using now). Maybe. But the issue in portrait mode still stands. [/EDIT]

---

### Post by Tom Jaeger on 2008-12-23
> **sarah.fauzia said:**
> Spoke slightly too soon. There appears to be an issue in portrait mode. I don't remember this occurring in Ubuntu, but it did happen in Kubuntu: When in portrait mode, and I make a gesture towards the bottom of the screen, only the top half of the stroke shows (if at all). It can get to the point where nothing shows. In Kubuntu (I haven't checked in openSUSE yet), disabling gestures showing on the screen... did not disable gestures from showing on the screen. But the stroke, despite it not showing properly, was properly recognized by Easystroke. Any thoughts? [/EDIT]
In 0.3.1, I've handed screen size change notification off to gdk, which listens for ConfigureNotify events on the root window, a method I thought was at least as reliable as the randr notification events I used previously.  I'm assuming that restarting the app while in portrait mode fixes the problem.

I can't reproduce this, but when testing kwin, I found a more serious problem, which is hopefully restricted to xserver-1.6:  The X server sneaks in an EnterNotify between reporting the core and Xi button press, which throws easystroke off.  The timestamps are still identical, so this is fixable.

Speaking of xserver-1.6, there've been a few changes that broke the way easystroke implements some of its advanced features.  It looks like I can fix this by using an entirely different method, but it's quite a bit of work (this work is happening mostly on the 'next' branch in git, in case someone's running jaunty).

---

### Post by sarah.fauzia on 2008-12-23
You're correct, restarting Easystroke in portrait mode does fix the problem. Good to know!

---

### Post by momonari on 2008-12-30
Hi,
I've just started using easystroke.
I've found that sometimes, easystroke "locks up" my input devices. I think it only happens when I define a gesture for a particular application. E.g., I defined a gesture to hit the Escape key for aMSN message windows, easystroke just calls the application "container_0". Sometimes it works, but other times, it will lock up, my computer doesn't respond to any mouse or keyboard input but my OS is still running.
What could be the cause of this? And is there something I can do when it happens to get easystroke to unlock my mouse and keyboard?

Thanks.

Momonari

---

### Post by Islington on 2008-12-30
> **momonari said:**
> Hi,
I've just started using easystroke.
I've found that sometimes, easystroke "locks up" my input devices. I think it only happens when I define a gesture for a particular application. E.g., I defined a gesture to hit the Escape key for aMSN message windows, easystroke just calls the application "container_0". Sometimes it works, but other times, it will lock up, my computer doesn't respond to any mouse or keyboard input but my OS is still running.
What could be the cause of this? And is there something I can do when it happens to get easystroke to unlock my mouse and keyboard?

Thanks.

Momonari

run it through a terminal and see if any errors pop up on such a lockup. it may help to figure out whats going on.

---

### Post by tanxiaojing on 2008-12-30
Are you a lover of sports? If your answer is yes, keep going. It is a good habit; it will keep you healthy and fit.
  In order to enjoy your sports, you need some good quality sportswear. However the high cost may keep you from enjoying the sports. Don’t worry. From now on, we will solve the problems for you. We are one of the Chinese sportswear trading company; we sell all kinds of sportswear at the reasonable price.
  More details please click [http://www.nikeboss.com]("http://www.nikeboss.com")  I really hope you can find what you need.
MSN: [http::popcorn://nikeboss@live.com]("http://nikeboss@live.com")

---

### Post by Tom Jaeger on 2008-12-30
> 
What could be the cause of this? And is there something I can do when it happens to get easystroke to unlock my mouse and keyboard?

I can't reproduce the issue on a 1.5.3 X server, but I get a simliar behavior (100% reproducible) on the 1.6.0 beta servers.  The cause might be the same or it might not.  In my case, this looks like a bug in the X server, which seems to have problems handling overlapping pointer and keyboard grabs.  Another cause could be misbehaving device drivers.

Does the problem only occur with the Escape key?  What window manager are you using?  What version of the X server?  Can you check if the attached binary (which removes the call to XGrabKey) fixes the problem?  If not, could you send me the output of "easystroke -vvv" when this problem occurs?

Normally, you should be able to reset easystroke by pressing Escape, but it looks like this is actually part of of the problem.  The other option is to switch to a console (or use ssh) to kill easystroke.  That should release the grab that is responsible for the lockup.

---

### Post by momonari on 2008-12-30
> **Tom Jaeger said:**
> Does the problem only occur with the Escape key?  What window manager are you using?  What version of the X server?  Can you check if the attached binary (which removes the call to XGrabKey) fixes the problem?  If not, could you send me the output of "easystroke -vvv" when this problem occurs?

I'm kinda new to Linux so I don't know how to find most of that. I'm using Ubuntu 8.10 with Compiz. How do I find out what window manager I'm using and what version of the X server?

It only happens with the Escape key, whether I define it for a particular application or define it as a global gesture.
The attached binary fixes the problem, however, after I close the message window with the gesture, I cannot type in aMSN anymore, i.e., if I open another message window, I can't type. I must restart aMSN. However, I believe this is a problem with SCIM and not easystroke.
Here is the output when I close the message window with the gesture (with the attached binary), my gesture button is the right mouse button, the gesture looks like the letter u and is of type "Key", namely, the Escape key:

```
Excecuting Action Gesture 15...
New event handling stack: Idle 
Motion: (804, 660)
Release: 3 (804, 660)
Entered window 0x3000323 -> 0x3000323
XError: BadWindow (invalid Window parameter): X_GetProperty
Entered window 0x40000cf -> 0x40000cf
```

Thanks.

Momonari

---

### Post by Tom Jaeger on 2008-12-31
> **momonari said:**
> I'm kinda new to Linux so I don't know how to find most of that. I'm using Ubuntu 8.10 with Compiz. How do I find out what window manager I'm using and what version of the X server?

Thanks, that's all the information I need.  Compiz is the window manager.

> 
It only happens with the Escape key, whether I define it for a particular application or define it as a global gesture.
The attached binary fixes the problem, 

Okay, so the lesson we learn from this is that synchronous pointer and keyboard grabs can't be safely combined.  I'll most likely just remove the ability to abort gestures in the next versions.

> 
however, after I close the message window with the gesture, I cannot type in aMSN anymore, i.e., if I open another message window, I can't type. I must restart aMSN. However, I believe this is a problem with SCIM and not easystroke.

They're lots of reports out there of SCIM causing problems like this, but bug #66104 is closed for some reason.

> 
```
Excecuting Action Gesture 15...
New event handling stack: Idle 
Motion: (804, 660)
Release: 3 (804, 660)
Entered window 0x3000323 -> 0x3000323
XError: BadWindow (invalid Window parameter): X_GetProperty
Entered window 0x40000cf -> 0x40000cf
```

Thanks.  Nothing unusual going on here.

---

### Post by momonari on 2008-12-31
> **Tom Jaeger said:**
> Okay, so the lesson we learn from this is that synchronous pointer and keyboard grabs can't be safely combined.  I'll most likely just remove the ability to abort gestures in the next versions.

So I should be able to gesture the Escape key in a future version? Please update us when you fix this. Thanks.

> **Tom Jaeger said:**
> They're lots of reports out there of SCIM causing problems like this, but bug #66104 is closed for some reason.

I never found a way to get SCIM working properly with aMSN. Whenever something happens in the message window, I have to click away and click back to input more text. This is one of the times I've had to actually restart aMSN to fix it. But that's off-topic.

---

### Post by Tom Jaeger on 2008-12-31
> **momonari said:**
> So I should be able to gesture the Escape key in a future version? Please update us when you fix this. Thanks.

Yes, definitely.  I'm planning on releasing the new versions (0.3.2 for xservers <= 1.5 and 0.4.0 for xserver 1.6) when the new xserver comes out.

---

### Post by sarah.fauzia on 2008-12-31
Is this possibly related to a problem I have with Nautilus? I can't say it happens every time, but at least almost every time I try to do a file transfer, while easystroke is open, long lines (in the color that I make gestures in), appear on the screen, and go crazy, splitting off into many directions. This does not allow me to see what's going on with the file transfer, or do anything to stop the lines from continuing to appear. Closing easystroke before the file transfer prevents this problem. Since I only use Nautilus, I'm not sure if the problem is keyed to Nautilus (no longer using KDE, so I'm not sure if it happens with Dolphin as well). I thought that just temporarily disabling easystroke would do the trick--but it didn't.

This isn't a big inconvenience, but I thought I should mention it in case anyone else is experiencing similar problems.

---

### Post by momonari on 2008-12-31
> **sarah.fauzia said:**
> Is this possibly related to a problem I have with Nautilus? I can't say it happens every time, but at least almost every time I try to do a file transfer, while easystroke is open, long lines (in the color that I make gestures in), appear on the screen, and go crazy, splitting off into many directions. This does not allow me to see what's going on with the file transfer, or do anything to stop the lines from continuing to appear. Closing easystroke before the file transfer prevents this problem. Since I only use Nautilus, I'm not sure if the problem is keyed to Nautilus (no longer using KDE, so I'm not sure if it happens with Dolphin as well). I thought that just temporarily disabling easystroke would do the trick--but it didn't.

This isn't a big inconvenience, but I thought I should mention it in case anyone else is experiencing similar problems.

I'm on Nautilus and it's not happening here.

---

### Post by sarah.fauzia on 2009-01-01
> **momonari said:**
> I'm on Nautilus and it's not happening here.

It might also be computer specific because it happens on my Motion tablet, and my sister's (both of the same model), but I haven't (yet) seen it happen on my X61t now that I think about it. I'm using almost the same exact install on both my Thinkpad and my Motion (Ubuntu 8.10 64-bit, Openbox, same software running, overall same configurations as I don't like using two computers on a daily basis with different interfaces). And my sister, running an almost pristinely fresh install of Ubuntu Intrepid (64-bit) has the same exact problem (so it can't be Openbox-specific, or specific to other interfering software). Hope there's a solution :)

I'll try to take a screenshot the next time I see it happen to give a better idea.

---

### Post by Tom Jaeger on 2009-01-05
> **sarah.fauzia said:**
> It might also be computer specific because it happens on my Motion tablet, and my sister's (both of the same model), but I haven't (yet) seen it happen on my X61t now that I think about it. I'm using almost the same exact install on both my Thinkpad and my Motion (Ubuntu 8.10 64-bit, Openbox, same software running, overall same configurations as I don't like using two computers on a daily basis with different interfaces). And my sister, running an almost pristinely fresh install of Ubuntu Intrepid (64-bit) has the same exact problem (so it can't be Openbox-specific, or specific to other interfering software). Hope there's a solution :)

I'll try to take a screenshot the next time I see it happen to give a better idea.

Hmm, could be a bug in the intel driver that is specific to GMA950.  Do you have a compositor running (i.e. are strokes anti-aliased or not)?  I'm assuming you're using the "Default" method.

---

### Post by aikiwolfie on 2009-01-05
> **Tom Jaeger said:**
> Hi,

I'd like to announce [easystroke]("http://easystroke.sourceforge.net"), a new gesture recognition application for linux.  Gesture recognition means that you can draw arbitrary curves on the screen by holding down a specific mouse button, and if the program recognizes their shape, it will perform certain actions.  For example, you can configure easystroke to maximize the current window if you draw a straight line in North-East direction. ...

The only place I've ever seen a genuine need for gestures was on Bump Top. And even then Bump top users could probably manage with normal controls. Sorry I just don't get the whole fascination with gestures. Mostly they seem to duplicate stuff that can be done faster with a simple point and click. Like maximize a Window.

Maybe maximizing a window is a bad example if you want to sell this to people.

---

### Post by Islington on 2009-01-05
> **aikiwolfie said:**
> The only place I've ever seen a genuine need for gestures was on Bump Top. And even then Bump top users could probably manage with normal controls. Sorry I just don't get the whole fascination with gestures. Mostly they seem to duplicate stuff that can be done faster with a simple point and click. Like maximize a Window.

Maybe maximizing a window is a bad example if you want to sell this to people.
Its much cooler on a tablet. much more intuitive than going to a random point and clicking.

---

### Post by Lightstar on 2009-01-05
Just dropping by to say that I totally love this thing!

Way better than Gestikk.. at least for me!
Gestikk was way too strict with my moves.

In my short linux experience (been on linux 100% for 2 years) this program is probably the one I'm the most happy about.

---

### Post by momonari on 2009-01-05
> **aikiwolfie said:**
> The only place I've ever seen a genuine need for gestures was on Bump Top. And even then Bump top users could probably manage with normal controls. Sorry I just don't get the whole fascination with gestures. Mostly they seem to duplicate stuff that can be done faster with a simple point and click. Like maximize a Window.

Maybe maximizing a window is a bad example if you want to sell this to people.

It's more convenient to be able to do everything with the mouse than having to let go of my mouse and press keys on my keyboard. E.g., to go to my desktop on the right, I would have to press Ctrl+Alt+Right, with a mouse gesture, I just draw a line to the right.

Most of the time, I'm sitting back in my chair or holding my chin with my left hand, so if I can do everything with the mouse with my right hand without having to change my posture, it's a lot easier.

And as others have pointed out, you don't have to move your mouse to whatever button (e.g., the maximise button) and perform the action, you just draw the gesture wherever your mouse is.

---

### Post by momonari on 2009-01-05
Double post, please delete.

> **aikiwolfie said:**
> The only place I've ever seen a genuine need for gestures was on Bump Top. And even then Bump top users could probably manage with normal controls. Sorry I just don't get the whole fascination with gestures. Mostly they seem to duplicate stuff that can be done faster with a simple point and click. Like maximize a Window.

Maybe maximizing a window is a bad example if you want to sell this to people.

It's more convenient to be able to do everything with the mouse than having to let go of my mouse and press keys on my keyboard. E.g., to go to my desktop on the right, I would have to press Ctrl+Alt+Right, with a mouse gesture, I just draw a line to the right.

Most of the time, I'm sitting back in my chair or holding my chin with my left hand, so if I can do everything with the mouse with my right hand without having to change my posture, it's a lot easier.

And as others have pointed out, you don't have to move your mouse to whatever button (e.g., the maximise button) and perform the action, you just draw the gesture wherever your mouse is.

---

### Post by zhocchao on 2009-01-07
@tom
I really like your software. (problem solved. Next time i'll RTFM twice)
@aikiwolfie
maximizing windows is a pretty good example

g
z

---

### Post by Tom Jaeger on 2009-01-07
> **zhocchao said:**
> @tom
I really like your software. Are there any future plans for exceptions? (As I run Firefox fullscreen on one workspace I don't need my window managing gestures there. I would like to have the same gestures with different commands for Firefox).
This is possible since 0.3.0, though badly documented:  Open the 'Applications' expander, click 'Add Application' and then select a firefox window.  You can now add, modify or delete gestures at will -- this will only affect the particular application you selected.  Changes between the default assignments are indicated in boldface.

---

### Post by zhocchao on 2009-01-07
Thank you, I found it on my own.
Really great!
z

---

### Post by sarah.fauzia on 2009-01-07
> **Tom Jaeger said:**
> Hmm, could be a bug in the intel driver that is specific to GMA950.  Do you have a compositor running (i.e. are strokes anti-aliased or not)?  I'm assuming you're using the "Default" method.

No, I'm not running a compositor. Yes, I am using the Default method (if I didn't, would I not experience the bug?). Output of lspci: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by Tom Jaeger on 2009-01-07
> **sarah.fauzia said:**
> No, I'm not running a compositor. Yes, I am using the Default method (if I didn't, would I not experience the bug?). Output of lspci: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

No, 'Default' actually falls back to Shape, as this is the only available method if running without a compositor.  Does this happen with other XShape clients, too?  Say if you run xeyes, minimize it and then run do your nautilus thing?

As a workaround, we could destroy the shaped window every time we've used it and then re-create it the next time, but I don't know how expensive an operation creating a screen-sized window really is.

---

### Post by Islington on 2009-01-07
My keystrokes are no longer showing up on screen using compiz annotate. The annotate function works in ccsm, and easygesture is recognizing the keystroke, and is behaving normally. whats going on?

---

### Post by Tom Jaeger on 2009-01-07
> **Islington said:**
> My keystrokes are no longer showing up on screen using compiz annotate. The annotate function works in ccsm, and easygesture is recognizing the keystroke, and is behaving normally. whats going on?

My guess is that the dbus plugin is not enabled.  You could also try the 'Default' method, it works pretty well on compiz now.

---

### Post by Tom Jaeger on 2009-01-09
> **sarah.fauzia said:**
> No, I'm not running a compositor. Yes, I am using the Default method (if I didn't, would I not experience the bug?). Output of lspci: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

> **Tom Jaeger said:**
> No, 'Default' actually falls back to Shape, as this is the only available method if running without a compositor.  Does this happen with other XShape clients, too?  Say if you run xeyes, minimize it and then run do your nautilus thing?

As a workaround, we could destroy the shaped window every time we've used it and then re-create it the next time, but I don't know how expensive an operation creating a screen-sized window really is.

Let's give this a shot.  I've commited this change on the test-shape branch in git.  Can you check if it solves the problem:
```

git clone git://github.com/thjaeger/easystroke.git
cd easystroke
git chekout origin/test-shape
make -j2 && ./easystroke

```

---

### Post by sarah.fauzia on 2009-01-10
> **Tom Jaeger said:**
> Let's give this a shot.  I've commited this change on the test-shape branch in git.  Can you check if it solves the problem:
```

git clone git://github.com/thjaeger/easystroke.git
cd easystroke
git chekout origin/test-shape
make -j2 && ./easystroke

```

Thanks! I'll try this out as soon as I can, hopefully tomorrow.

---

### Post by zhocchao on 2009-01-15
When i disable "Show tray icon", easystroke quits. (when i click on hide)

---

### Post by Tom Jaeger on 2009-01-16
> **zhocchao said:**
> When i disable "Show tray icon", easystroke quits. (when i click on hide)

What version of easystroke is that?  Also, are you sure it really crashes?  Without any tray icon the only way to bring up the configuration window again is by using a gesture or the dbus interface.

---

### Post by Tom Jaeger on 2009-01-16
Okay, we're finally nearing the 0.4.0 release; I've just released the first beta.  Changes in the upcoming 1.6 X server forced me to rewrite most of the event handling code for 0.4.0.  I've done most of my testing on beta X servers (plus a few patches, more on that later), but from the limited testing I have done on older X servers, it seems to be working really well on them, too, so I'll probably skip the 0.3.2 release.  I've only added jaunty packages to my PPA, but they should work on intrepid, too (they do on my mostly-intrepid system anyway, let me know if you have any troubles installing them):

[http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/e/easystroke/)

Version 0.3.98.1 is what you want.

As for the changes, aside from xserver-1.6 support, the only major change is support for multiple buttons, which should mostly be useful to people that have mice with a lot of buttons, which you can now assign arbitrary actions to.  To use the feature, just open the 'Additional Buttons' expander on the 'Preferences' tab and add buttons that you want to use for gestures there.  Another new feature that my come in handy when using additional buttons is the 'Instant gestures' checkbox on the lower left corner of the button dialog.  It will cause actions to immediately trigger when the button is pressed.  As an example, if you want to map button 8 on your mouse to the 'Alt' modifier, you would first add the button to the list of additional buttons with the instant checkbox turned on and then add a gesture of type 'Ignore' and press 'Alt + <any key>' in the detail column.  When recording the gesture, simply click button 8, and you should be all set.

Also, easystroke is now set up for localization.  So far, I've only added German translations (but someone who's actually running a German-localized OS should probably have a look at them...).  If you want to help out with the translation effort, I've set up a launchpad project page that should make contributing translations really easy.  The process is (or will be...) explained on the easystroke wiki:

[http://easystroke.wiki.sourceforge.net/Translations](http://easystroke.wiki.sourceforge.net/Translations)

Finally, a note for users that are already using jaunty:  You might notice a few bugs with the beta, these are most probably bugs in the X server.  I've done my best to get fixes for them in the X server (currently, I still have 8(!) patches applied on top of server-1.6 branch).  They're all in master and waiting to be cherry-picked for X server 1.6 -- which will hopefully happen before the 1.6 release.

---

### Post by Tom Jaeger on 2009-01-16
> **pibach said:**
> 
Moreover it would be nice if easystroke scroll option could serve as a general scroll method similar to g&d scrolling in Firefox but application independent. Currently the scroll option is nice, but too cumbersome (one issue is that it requires re-activation for every scroll). Maybe you could add a scroll mode to easystroke that is activated on a specific button.

Threfore, the GUI could have an additional "scroll button" to be selected beneath the "gesture button". Ideally the button assignment is application specific so you would need two button parameters for the "exceptions" list that indicate the different assignment. Thus, for each item in that list you'll have an individual gesture button and scroll button different to the default setting. Setting both buttons to "none" would completely disable easystroke then for this application.


Okay, it took quite a while, but this is finally possible now:  Add Button3 as an (instant) additional button and then assign a 'Scroll' gesture to it.  You can even control what happens when the left button is pressed while you're scrolling (the default is to let the click through): Just define a gesture by pressing first button 3 and then (without releasing button 3) pressing button 1.  I think it would make sense to assigning button 3 to this gesture.

---

### Post by zhocchao on 2009-01-16
> **Tom Jaeger said:**
> What version of easystroke is that?  Also, are you sure it really crashes?  Without any tray icon the only way to bring up the configuration window again is by using a gesture or the dbus interface.

It's 0.3.1 . The gestures don't work and I looked for it in System Monitor



edit: I installed 0.3.98.1 and it's the same

---

### Post by Tom Jaeger on 2009-01-16
> **zhocchao said:**
> It's 0.3.1 . The gestures don't work and I looked for it in System Monitor

Fixed in git and uploaded an updated intrepid 0.3.1 package to my PPA.  It'll probably take a half hour to build.

---

### Post by zhocchao on 2009-01-16
great ! thank you!

---

### Post by Luffield on 2009-01-16
0.3.98.1 installed successfully on Intrepid and works great. Thanks for your efforts Tom!

---

### Post by zhocchao on 2009-01-16
> **Tom Jaeger said:**
> Fixed in git and uploaded an updated intrepid 0.3.1 package to my PPA.  It'll probably take a half hour to build.

Now easystroke crashes when I uncheck "Show tray icon" without clicking Hide after about 1-2 s.

---

### Post by Gourgi on 2009-01-17
> **Tom Jaeger said:**
> 
Also, easystroke is now set up for localization.

[http://easystroke.wiki.sourceforge.net/Translations](http://easystroke.wiki.sourceforge.net/Translations)


i've started the greek translation in launchpad
keep up the good work Tom :guitar:

---

### Post by Tom Jaeger on 2009-01-17
> **zhocchao said:**
> Now easystroke crashes when I uncheck "Show tray icon" without clicking Hide after about 1-2 s.

Are you sure you're using the latest version from the PPA?  Just to be safe, I've added checks whether the icon exists to two more places where it is accessed (that I don't think can be called when there is no icon, though).

---

### Post by Tom Jaeger on 2009-01-17
> **Gourgi said:**
> i've started the greek translation in launchpad

Thanks.  Very much appreciated.

---

### Post by zhocchao on 2009-01-17
> **Tom Jaeger said:**
> Are you sure you're using the latest version from the PPA?  Just to be safe, I've added checks whether the icon exists to two more places where it is accessed (that I don't think can be called when there is no icon, though).

Maybe I was to fast yesterday though I waited 2 hours for install (as it crashed before I clicked Hide I thought this was the new version. After the update today it works perfectly

---

### Post by EvilGnome on 2009-01-21
This is fantastic, and apparently getting better. Thank you, Mr. Jaeger.

With this new beta release, are rocker and/or wheel gestures possible yet?

I thought it was worth a try, so I added mouse buttons 1 and 3 as instant gesture buttons and mapped gestures as shown in the attached screenshot. This was unsuccessful, and those buttons were kind of stolen by the instant gestures, making it difficult to use them normally.

So I disabled those extra buttons. Hopefully the picture will make it clear what I'm trying to do.

My question is: should I be doing this another way, not at all, or in a future release instead?

Thank you very much,
Andy

---

### Post by Tom Jaeger on 2009-01-21
> **EvilGnome said:**
> 
So I disabled those extra buttons. Hopefully the picture will make it clear what I'm trying to do.

Thanks, the picture was very helpful.  This is exactly the kind of thing that is planned for 0.4.0, and we're closer to it than you might think.  Basically, I think of instant gestures as gestures that are triggered on pressing the button rather than releasing it.  The problem here is that there is no action defined that is to be executed when the button is pressed and I just haven't given enough thought to what the default should be.  So right now you need to tell easystroke what to do:  Define a gesture by just pressing the button and then assign either of the following actions to it:
[LIST]
[*] 'Ignore' will ignore the button press, but will replay it if you release the button right away.  This is probably the better option for button 3, as the popup menu might have some unpleasant side effects otherwise (at least on X servers <= 1.5.x)
[*] 'Button X' will let the click through (at least conceptionally, what actually happens is quite scary), and will release the button when another button is pressed.
[/LIST]
That's the theory anyway.  In practice, this works quite well on recent 1.6 beta X servers, but it should also work on older servers (I just haven't tested it very thoroughly).

So the remaining question is what the default should be.  I think what I described as 'Button X' above would make the most sense, but I'll need to think about it a little more.

---

### Post by Tom Jaeger on 2009-01-21
I've just uploaded a second beta release that contains all the fixes that have accumulated since beta 1 and adds Czech translations (thanks, Jakub).  Binary packages (look for 0.3.98.2-0ubuntu2) are in my PPA:

[http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/thjaeger/ubuntu/pool/main/e/easystroke/)

---

### Post by EvilGnome on 2009-01-21
Thanks Jaeger. Oh, another question:

I don't use a system tray (and would really rather not), so every time I want to manage my gestures I run a killall easystroke && easystroke -g. Is there a better/cleaner way to do this? Do you think maybe the manager executable should be distinct from the daemon executable?

Thanks again,
Andy

---

### Post by zhocchao on 2009-01-21
> **EvilGnome said:**
> Thanks Jaeger. Oh, another question:

I don't use a system tray (and would really rather not), so every time I want to manage my gestures I run a killall easystroke && easystroke -g. Is there a better/cleaner way to do this? Do you think maybe the manager executable should be distinct from the daemon executable?

Thanks again,
Andy

Hi
You can define a gesture for that: Type: Misc...show/hide

---

### Post by EvilGnome on 2009-01-21
> **zhocchao said:**
> Hi
You can define a gesture for that: Type: Misc...show/hide

Perfect, thanks very much!

---

### Post by sarah.fauzia on 2009-01-25
I decided it was about time to mention how thankful I am that you made Easystroke. It's my most-used, most indispensable application. I have 28 gestures in default, and 46 in total when I include the ones for specific applications. And counting. Four gestures I just made today for ePDFView. I am no longer using Ubuntu--I'm using Arch Linux--but Easystroke is in the AUR so it's still very easy to install! I'm also no longer using my Motion, so that's why I hadn't posted my test results on it (since I didn't get to install the easystroke you made available on the git repo). However, my sister has a Motion, so I'll try to install it on that ASAP.

Thanks for making the best program ever; it's priceless for using Linux on a tablet :)

---

### Post by GrouchoMarx on 2009-01-27
Hi Tom,

I'd like to thank you once again for your work on easystroke, one of the most useful utilities around.

I have a question regarding the gesture timeout profiles. It seems that the "conservative" timeout setting is still too short to reliably perform some gestures, like like Alt-Tabbing via the mouse-wheel. I simply cannot perform mouse-wheel gestures without turning timeouts off completely. What is the hard-coded value for the conservative timeout-profile? Might it not make sense to increase the conservative timeout profile, as there happen to be three shorter ones?

---

### Post by Tom Jaeger on 2009-01-28
> **GrouchoMarx said:**
> I simply cannot perform mouse-wheel gestures without turning timeouts off completely. What is the hard-coded value for the conservative timeout-profile? Might it not make sense to increase the conservative timeout profile, as there happen to be three shorter ones?

You'll have more fine-grained control over timeout settings if you start easystroke with the '-e' command line argument.

I don't have strong opinions of what profiles should be available.  I'm personally using 'Flick' and hardly ever try the others, so I depend on user feedback here.  Basically, if people feel that a certain set of parameters is useful, it should be a setting.  The default setting should be something where timeouts are still usable and discoverable, but hard to trigger accidentally (when doing regular gestures, so wheel gestures don't count here).  I don't know if that's the case currently, if not the default parameters should be adjusted.

So I'm inclined to rename the current 'Conservative' setting to 'Default' and then add a new setting below that.  Could you suggest parameters that work for you?

---

### Post by GrouchoMarx on 2009-01-28
I just want to make sure that I understand what the timeout even does: I assume that the gesture timeout is the length of time it takes for the gesture to be ignored if you pause while performing a gesture. If this is the case, then honestly I can't even see a difference between the various timeout profiles because they are so short (just a fraction of a second in each case). When I use Button 3 to initiate a gesture, followed by Buttons 4 or 5 (mousewheel) to alt-tab through programs, what ends up happening is that after pressing Button 3, the gesture times out before I'm able to initiate the mousewheel. It would make things easier if the conservative timeout profile (or whatever you want to call the longest one) would be at least 2 seconds long.

I hope I've made sense.

---

### Post by sarah.fauzia on 2009-01-29
I have a suggestion for a new possible feature. Could we make gestures for words themselves? For example, my mother (a doctor) often has to type the term "pelvic pain". She would like to make a gesture that would just insert the text. I see myself perhaps using it to insert passwords! Or some other commonly used words. Is this type of feature already in the works, perhaps?

---

### Post by zhocchao on 2009-01-29
hi
use this as command (xvkbd must be installed):
xvkbd -xsendevent -text "bla...bla...."
g
z


edit: OK use xte

---

### Post by Tom Jaeger on 2009-01-29
> **GrouchoMarx said:**
> I just want to make sure that I understand what the timeout even does: I assume that the gesture timeout is the length of time it takes for the gesture to be ignored if you pause while performing a gesture.
Not quite.  There are actually two parameters: the 'Timeout' parameter controls how it will take for the gesture to time out if the mouse isn't moved at all.  The 'Minimum speed' parameter plays more of a role when determining the timeout if part of the gesture has already been performed.

>  It would make things easier if the conservative timeout profile (or whatever you want to call the longest one) would be at least 2 seconds long.


Can you actually test this? ("easystroke -e". and then set the profile to 'Custom').  2 seconds seems too long to me -- this would basically amount to not having any timeouts at all.  I'd especially encourage you to try lowering the 'Minimum speed' parameter.

---

### Post by Tom Jaeger on 2009-01-29
> **sarah.fauzia said:**
> I have a suggestion for a new possible feature. Could we make gestures for words themselves? For example, my mother (a doctor) often has to type the term "pelvic pain". She would like to make a gesture that would just insert the text. I see myself perhaps using it to insert passwords! Or some other commonly used words. Is this type of feature already in the works, perhaps?

This has been suggested before, but I've so far been reluctant to add it because (a) it can be easily accomplished using command line tools (xte 'str foo') and (b) I don't know of a way to make it work with non-English characters (e.g. xte 'str äø©').  I don't really think (a) is a valid concern anymore, since this seems to be something that's useful to users, but I'd still like to address (b) first.  I'll see if I can find a way to (ab)use the clipboard spec to get the desired effect.

---

### Post by Devport on 2009-01-29
This app is fantastic - great work. Its so nice to reduce the neccessity to use the keyboard to a bare minimum.

I love to switch channels in tvtime by painting the channel number.

Thanks for this great tool.

---

### Post by GrouchoMarx on 2009-01-29
Hi Tom,

After experimenting with the custom profile I agree that two seconds is probably overkill. But any less than one second makes it difficult to comfortably execute the Mouse3 + Mousewheel combination. With a one second timeout I can execute that gesture naturally, without rushing. Whether it makes sense to change the conservative timeout profile on account of one person, having problems with one gesture, I can't say, but currently the default profiles are so short that it's hard to tell the difference between them. If you're going to have multiple default profiles, then in my opinion you might as well make the longest profile, well, long ;). Of course there is always the option of fully implementing the custom profile, which I rather liked.

Anyways, hope the feedback was useful and thanks again for your excellent work!

---

### Post by Brett Ryland on 2009-01-30
Hi Tom, thanks for such a useful app. I recently upgraded to the latest version (from about version 0.2.2) and I miss the tray icon changing to reflect the last used gesture. I prefer not to have popups and the various methods to show gestures do not perform well on my machine for some reason.
On page 19 of this thread you said...
> There's really not much of a point in the tray icon changing anymore now that we have popup notification, so I've removed this behavior in master. In case someone complains, I will revert that change and make this an option.
Is it still possible to make this an option?

---

### Post by Tom Jaeger on 2009-01-30
> **GrouchoMarx said:**
> 
After experimenting with the custom profile I agree that two seconds is probably overkill. But any less than one second makes it difficult to comfortably execute the Mouse3 + Mousewheel combination. With a one second timeout I can execute that gesture naturally, without rushing. Whether it makes sense to change the conservative timeout profile on account of one person, having problems with one gesture, I can't say, but currently the default profiles are so short that it's hard to tell the difference between them. If you're going to have multiple default profiles, then in my opinion you might as well make the longest profile, well, long ;). Of course there is always the option of fully implementing the custom profile, which I rather liked.

Thanks for your comments.  I've made the following changes for 0.4.0:

[LIST]
[*]Renamed 'Conservative' to 'Default'
[*]Added a 'Conservative' profile with 1s timeout and a minimum speed of 10 px/s (the latter probably won't make much of a difference)
[*]Increased the upper limit for the (experimental) custom profile to 2500 ms
[/LIST]

I'm planning to rework the timeout algorithm for 0.4.1; it doesn't work very well with long timeouts, and over-emphasizes absolute speeds, which probably aren't that meaningful.

---

### Post by Tom Jaeger on 2009-01-30
> **sarah.fauzia said:**
> I have a suggestion for a new possible feature. Could we make gestures for words themselves? For example, my mother (a doctor) often has to type the term "pelvic pain". She would like to make a gesture that would just insert the text. I see myself perhaps using it to insert passwords! Or some other commonly used words. Is this type of feature already in the works, perhaps?

Implemented in the 'next' branch.  For inserting keys that aren't on the keyboard, it relies on unicode input (Ctrl+Shift+U, hex code, space), which only works in gtk apps at this point.

---

### Post by pibach on 2009-01-31
Haven't yet tried easystroke Version 4, just waiting for official release.
I am very happy with current version. Also general scroll mode works fine, I assigned it to a simple click timeout gesture. Gesture button is the normal click. For apps that need the pen input, e.g., xournal, just assign button 3 in the exceptions, and even scrolling works fine then. Only if scrolling could be tweaked a bit with a speed parameter would be nice, as I prefer a faster scrolling. 

A minor bug is that gestures are not shown in portrait mode in the lower part of the screen when using Metacity, Compiz works fine though (might be because I have the high SXGA+ resolution?). 

I have defined >100 gestures including all letters. So I can directly correct text without invoking cellwriter, works nicely. But this also induces some issues:
* difficult on list boxes (e.g., Firefox URL bar) as it mixes up the focus (still the initial problem we have discussed in the beginning of this thread)
* for longer input cellwriter still is best. I invoke cellwriter by a gesture. This is fine. It is not positioned perfectly but this is not a big problem. But the need to always hit the "enter" button to get the cellwriter buffer inserted is annoying. Would it be possible by entering this if cellwriter loses focus? Or by stroking a specific symbol? Or just after some timeout? Probably redirect this to cellwriter developer?

BTW, does anybody know how to make the popup window opaque in compiz?

---

### Post by Tom Jaeger on 2009-01-31
A new X server release candidate finally arrived with all the necessary fixes for easystroke in it, so I've released a release candidate for 0.4.0 as well:

[Source]("http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/easystroke_0.3.99.1.orig.tar.gz")
[i386 package]("http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/easystroke_0.3.99.1-0ubuntu1_i386.deb")
[amd64 package]("http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/easystroke_0.3.99.1-0ubuntu1_amd64.deb")

These are jaunty packages, but they should work on intrepid as well, let me know if they don't.

Aside from a few bug fixes, the release candidate adds a new 'Text' action, allows to disable easystroke by a middle-click on the tray icon and makes the changes to the timeout profiles that I've discussed above.  We also have Italian translations now (thanks Massimiliano).

---

### Post by Tom Jaeger on 2009-01-31
> **Brett Ryland said:**
> Hi Tom, thanks for such a useful app. I recently upgraded to the latest version (from about version 0.2.2) and I miss the tray icon changing to reflect the last used gesture. I prefer not to have popups and the various methods to show gestures do not perform well on my machine for some reason.
On page 19 of this thread you said...

Is it still possible to make this an option?

It's too late for 0.4.0 now, but I could make this an option in 0.4.1.  Does anybody else have an opinion on this?

---

### Post by Tom Jaeger on 2009-01-31
> **pibach said:**
> Only if scrolling could be tweaked a bit with a speed parameter would be nice, as I prefer a faster scrolling.

I'll see what I can do for 0.4.1.

> 
A minor bug is that gestures are not shown in portrait mode in the lower part of the screen when using Metacity, Compiz works fine though (might be because I have the high SXGA+ resolution?). 

Thanks, fixed in 0.3.99.1.  It turns out that Xlib's DisplayWidth() function isn't working, so I'm using the corresponding gdk function now.

> 
* difficult on list boxes (e.g., Firefox URL bar) as it mixes up the focus (still the initial problem we have discussed in the beginning of this thread)

If the issue is what I think it is, a fix will have to wait until X server 1.7.

> 
* for longer input cellwriter still is best. I invoke cellwriter by a gesture. This is fine. It is not positioned perfectly but this is not a big problem. But the need to always hit the "enter" button to get the cellwriter buffer inserted is annoying. Would it be possible by entering this if cellwriter loses focus? Or by stroking a specific symbol? Or just after some timeout? Probably redirect this to cellwriter developer?

Yes, in theory, these things are possible, but they would need to be handled in cellwriter itself.

> 
BTW, does anybody know how to make the popup window opaque in compiz?

This should work:
```
class=Easystroke & type=Normal & override_redirect=1
```

---

### Post by Robbyx on 2009-02-01
I am really sorry to be asking such crass questions but as I haven't been able to get the keystrokes to show in the Actions tab I better ask them.

1. What do I do to ensure the Easystroke remembers my key stroke? Of course I have added an action. I click on record a stroke. Immediately a warning box opens up advising that the next stroke will be associated with the Gesture 2. I cancel the box, do an upward gesture with the centre mouse button pushed down, and nothing extra appears in the stroke column of the action tab. I expected to see the keystroke as a pic.

2. Argument: Are the entries literal or recorded key strokes? I tried ALT F4 (as function key entries and it closed the program's window). Should I literally type the letters not the function keys?

Robin

---

### Post by EvilGnome on 2009-02-01
> **Robbyx said:**
> Immediately a warning box opens up advising that the next stroke will be associated with the Gesture 2. I cancel the box

Don't cancel the box. As it says, just perform the gesture anywhere but over the buttons.

> **Robbyx said:**
> I tried ALT F4 (as function key entries and it closed the program's window). Should I literally type the letters not the function keys?

You should be using the actual keys, ALT and F4. Make sure the type is set to key and the details column reads "Key Combination..."

---

### Post by Robbyx on 2009-02-01
> **EvilGnome said:**
> Don't cancel the box. As it says, just perform the gesture anywhere but over the buttons.

To what buttons are you referring? I am not clear.


> 
You should be using the actual keys, ALT and F4. Make sure the type is set to key and the details column reads "Key Combination..."

I just tried it and the keystrokes closed the program. So I am still getting it wrong.

---

### Post by Tom Jaeger on 2009-02-01
See the attached video.

---

### Post by Robbyx on 2009-02-02
> **Tom Jaeger said:**
> See the attached video.

Thank you for that video. It made all the difference. For my version of Easystroke I have now learnt the following:

1. For the argument to take the keystrokes I had to change the name of the action from the default Gesture 2 to a name such as close.

2. The record stroke button does not work. Double clicking the Stroke column opened the same boxes as Record stroke except this time the stroke was recorded.

I am using the version 0.2.2.1-0 Ubuntuntu2

Robin

---

### Post by Gourgi on 2009-02-03
greek translation completed.
i'll try easystroke to jaunty soon ;)

---

### Post by Tom Jaeger on 2009-02-03
> **Robbyx said:**
> Thank you for that video. It made all the difference. For my version of Easystroke I have now learnt the following:

1. For the argument to take the keystrokes I had to change the name of the action from the default Gesture 2 to a name such as close.

2. The record stroke button does not work. Double clicking the Stroke column opened the same boxes as Record stroke except this time the stroke was recorded.

I am using the version 0.2.2.1-0 Ubuntuntu2

Robin

This is truly weird.  I have no clue what could cause this.  Is this still happening with more recent versions of easystroke?

---

### Post by Tom Jaeger on 2009-02-03
> **Gourgi said:**
> greek translation completed.
i'll try easystroke to jaunty soon ;)

Thank you!  I've imported the translations into git, they will be part of the next release (I had already tagged 0.3.99.2 earlier today, so they're not in it).

---

### Post by Tom Jaeger on 2009-02-03
I've made another release candidate (0.3.99.2), including mostly bugfixes that have accumulated over next.  They should become available in the easystroke PPA in about 15 minutes:

[http://ppa.launchpad.net/easystroke/ppa/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/easystroke/ppa/ubuntu/pool/main/e/easystroke/)

---

### Post by Robbyx on 2009-02-03
> **Tom Jaeger said:**
> This is truly weird.  I have no clue what could cause this.  Is this still happening with more recent versions of easystroke?

Is there a repository with a later version? I used the latest version in synaptic.

Robin

---

### Post by Robbyx on 2009-02-03
> **Tom Jaeger said:**
> I've made another release candidate (0.3.99.2), including mostly bugfixes that have accumulated over next.  They should become available in the easystroke PPA in about 15 minutes:

[http://ppa.launchpad.net/easystroke/ppa/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/easystroke/ppa/ubuntu/pool/main/e/easystroke/)

I am getting an error message from the package installer:

Dependency is not satisfiable: libc6.

I tried installing 

0.3.99-2-:ubuntu1

Robin

---

### Post by Luffield on 2009-02-03
RC2 also failed to install on my Intrepid machine with the same error message Robin got. I do have libc6 installed, it's version 2.8~20080505-0ubuntu9.

On my Jaunty VM, RC2 installed and works fine. libc6 version is 2.9-0ubuntu9.

---

### Post by Tom Jaeger on 2009-02-03
> **Luffield said:**
> RC2 also failed to install on my Intrepid machine with the same error message Robin got. I do have libc6 installed, it's version 2.8~20080505-0ubuntu9.

On my Jaunty VM, RC2 installed and works fine. libc6 version is 2.9-0ubuntu9.

Thanks, I've added intrepid packages to the [PPA]("https://launchpad.net/~easystroke/+archive/ppa/") as well. i386 is available now, amd64 will take another 20 minutes to get published.

---

### Post by Robbyx on 2009-02-03
> **Tom Jaeger said:**
> Thanks, I've added intrepid packages to the [PPA]("https://launchpad.net/~easystroke/+archive/ppa/") as well. i386 is available now, amd64 will take another 20 minutes to get published.

Thank you.

Robin

---

### Post by Tom Jaeger on 2009-02-03
Something completely different for a change:  I'm currently looking into how the gesture matching algorithm might be improved.  I only have half-baked ideas so far and I won't be able to spend much time on easystroke during the next few months, so the new algorithm might take a while to materialize.  Anyway, I got a cool picture out of one of the ideas that I'd like to share:

[IMG]http://easystroke.sourceforge.net/easystroke.jpg[/IMG]

I'll spare you the math, but comparing two strokes basically amounts to finding the "brightest" path from the lower left corner to the upper right corner of each of the small squares while avoiding to move in NorthWest/SouthEast direction.

---

### Post by GrouchoMarx on 2009-02-03
I would be interested to see the math if you'd like to share :)

---

### Post by Tom Jaeger on 2009-02-04
> **GrouchoMarx said:**
> I would be interested to see the math if you'd like to share :)

Well, okay.  The main reason the current algorithm is less than optimal is that it lacks any support for reparametrization.  This means for example, that when you try to make the 7th gesture in the picture but make the vertical part a little to short, it will be recognized as the last gesture be cause the corner is about a third of the way into the gesture in both cases.
Suppose your two gestures are given as paths A,B: [0,1]->R^2. The best way to visualize a reparametrization is as a path r: [0,1] -> [0,1]x[0,1] from the unit interval to unit square, where (x,y) is in the image of r if position x in gesture A corresponds to position y in B under the reparametrization.  Of course we want A to locally look near x like B near y, so we assign a score phi(x,y) to the pair (x,y) capturing how well the gestures match locally.  The pictures above are plots of phi(x,y), where white = 0 = good and black = 1 = bad.  One can think of more sophisticated measures, but in the picture I just compared the directions for the gestures at x and y.  The total score of a path is just the integral of phi along the path and the infimum over all paths expresses how well the two gestures match.  Doing this alone would be a little problematic as it allows for reparamatrizations containing jumps (where one of the gestures may just be a part of the other gesture).  This can be fixed in several different ways:  By restricting the set of allowed paths, by factoring in the length of the path or by penalizing motion in NW/SE direction, but in any case, this is a minor technical point.

The interesting question now is how do we find that optimal path with as little computational effort as possible?  First of all, the problem has a nice theoretical solution:
If we assume that A and B are smooth (we can always find a smooth interpolating curve) the unit square can be given the structure of a Riemannian manifold by setting (for example) g = (0.5 + phi(x,y))(dx&#8855;dx+dy&#8855;dy), so the shortest path will always be a geodesic and we could (theoretically) just shoot geodesics (which just amounts to solving an ODE) from the origin and see where they land.  But I don't think it's going to work for sequence-of-line-segments types of strokes, because the behavior near the corners of checkerboard-like pictures is chaotic, and we may easily hit the limits of numerical precision.
So I think a more discreet algorithm is needed.  Since we're looking for a shortest path, Dijstra's algorithm is the natural candidate.  Our graph has on the order of n^2 vertices and can be made reasonably sparse, so we'd get complexity O(n^2 log(n)).  This might be fast enough, especially if we find a way to weed out obviously bad matches early on, but it's something to keep in mind (the current algorithm has complexity O(n)).  The bigger problem is that it is harder to penalize jumps as we lose path length information due to aliasing issues.

This is about as far as I've thought this through, so clearly, there's a lot of work ahead before this can be made into a working implementation.

---

### Post by Luffield on 2009-02-04
> **Tom Jaeger said:**
> Thanks, I've added intrepid packages to the [PPA]("https://launchpad.net/~easystroke/+archive/ppa/") as well. i386 is available now, amd64 will take another 20 minutes to get published.

Thanks Tom, this version works well.

---

### Post by pibach on 2009-02-07
> **Tom Jaeger said:**
> It's too late for 0.4.0 now, but I could make this an option in 0.4.1.  Does anybody else have an opinion on this?
An ideal visual feedback would be some in place morph that transforms the actual gesture to the prototype gesture. But this might be rather resource intensive. A visual feedback within the tray icon is too far out of focus and needs too much eye travel. However, it would be better than nothing.

Regarding the algorithm. I could delegate this to a team of students, April-June, if this helps.

---

### Post by pibach on 2009-02-07
> **Tom Jaeger said:**
> 
This should work:
```
class=Easystroke & type=Normal & override_redirect=1
```

yes, does work, thanks.

---

### Post by Islington on 2009-02-07
> **Tom Jaeger said:**
> It's too late for 0.4.0 now, but I could make this an option in 0.4.1.  Does anybody else have an opinion on this?
I would love to have that back.:D

---

### Post by mr_deimos on 2009-02-07
First of all, thanks for this wonderful app, Tom :)

I have a small feature request. I already posted it on [sourceforge tracker](https://sourceforge.net/tracker/index.php?func=detail&aid=2577687&group_id=229797&atid=1078457), but i guess there's a bit more going on here, at the forums.
How about adding an option to reverse scroll direction? Right now it's not really intuitive, especially on tabletPC - you drag the pen down, and the page moves up, so it feels as if you were dragging a scroll slider rather than the actual window contents. Sure, some people might like that, but i prefer it the opposite way, like in grab-and-drag firefox extension. I compiled a modified easystroke version for myself with scrolling direction reversed - it was just a matter of adding one minus sign (if anyone is interested, details are in the tracker request) in the scroll speed curve calculation expression. Since the change is trivial, and doesn't require large modifications to the code, how about adding it as an option in the easystroke config? I think many users would find it more intuitive when they are able to compare the two methods.

Ideally, it would be great to have some inertia in scrolling mode (if you drag the page and release the pen/mouse button, the page will continue moving for a while), but that might require some deeper changes and probably there are some more important changes planned :)

---

### Post by Tom Jaeger on 2009-02-08
> **pibach said:**
> An ideal visual feedback would be some in place morph that transforms the actual gesture to the prototype gesture. But this might be rather resource intensive.
I don't really see the point.  And yes, it seems that at least on my system, simultaneous drawing operations are somewhat of a performance problem (this might be at least partly compiz' fault)

> 
A visual feedback within the tray icon is too far out of focus and needs too much eye travel. However, it would be better than nothing.

We do have popups, they're not going away.

> 
Regarding the algorithm. I could delegate this to a team of students, April-June, if this helps.
I've already implemented a new algorithm.  I'm actually quite happy with the results.  Surprisingly enough, performance is on par with the old algorithm, but I'd still like to optimize it a little further.

---

### Post by Tom Jaeger on 2009-02-08
> **Islington said:**
> I would love to have that back.:D

All right, I'll bring it back as an option in 0.4.1.

---

### Post by Tom Jaeger on 2009-02-08
> **mr_deimos said:**
> 
How about adding an option to reverse scroll direction? Right now it's not really intuitive, especially on tabletPC - you drag the pen down, and the page moves up, so it feels as if you were dragging a scroll slider rather than the actual window contents. Sure, some people might like that, but i prefer it the opposite way, like in grab-and-drag firefox extension. I compiled a modified easystroke version for myself with scrolling direction reversed - it was just a matter of adding one minus sign (if anyone is interested, details are in the tracker request) in the scroll speed curve calculation expression. Since the change is trivial, and doesn't require large modifications to the code, how about adding it as an option in the easystroke config? I think many users would find it more intuitive when they are able to compare the two methods.

I'll make this an option in 0.4.1.  I'll also add an option for adjusting scroll "speed".

> 
Ideally, it would be great to have some inertia in scrolling mode (if you drag the page and release the pen/mouse button, the page will continue moving for a while), but that might require some deeper changes and probably there are some more important changes planned :)
Scrolling works by faking scroll wheel events, which are handled as button presses by the X server and thus inherently discrete.  So this is not really an option -- at least not until the toolkits adopt XI 2.0.

---

### Post by GrouchoMarx on 2009-02-08
> **Tom Jaeger said:**
> All right, I'll bring it back as an option in 0.4.1.

Although I initially found this feature distracting, it eventually grew on me to the point that I really missed it when it disappeared (oh, fickle users :p). If you end up restoring the gesture feedback in the system tray, then you might consider making successful gestures appear in green and blue (as usual), but have failed gestures appear in red (I remember you said that you weren't so keen on the checkmark and dot, so this could be an elegant alternative).

---

### Post by Luffield on 2009-02-08
I like GrouchoMarx's idea.

---

### Post by Tom Jaeger on 2009-02-08
[Version 0.4.0]("https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455") is finally here.  Not much has happened since the last RC, the only notable change is the addition of Spanish translations (thanks Paco).

If you've used my PPA before to get easystroke,  I would ask you to switch over to the new easystroke PPA (I'll keep copying the new packages into my PPA for a while, though):

```
deb http://ppa.launchpad.net/easystroke/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/easystroke/ppa/ubuntu intrepid main
```


This is going to be a short-lived release since I really want to get the new algorithm into jaunty (you can already test it on the next branch in git).

---

### Post by Islington on 2009-02-09
awesome. Trying it now. will post tommorrow.

---

### Post by EvilGnome on 2009-02-10
OK, I'm really close to being completely set up with wheel and rocker gestures, but am still having a couple of issues.

Possibly relevant setup values

**Version**: 0.4.0-0ubuntu1~intrepid
**Gesture Button**: Button 2
**Additional Buttons**: Button 3, (Instantly) Button 1
--
**Action**: Volume Up
**Stroke**: 1->4 (left click then scroll up)
**Result**: Works, but initial click works as regular click (kind of expected, not a problem) and the first scroll unit also scrolls in addition to changing the volume (very minor annoyance)

Volume Down is pretty much the same.

Volume Mute is pretty much the same, but it's set up with a middle click rather than a scroll. The regular and middle clicks go through to their normal operations, as with Volume Up.

**Action**: Next Tab
**Stroke**: 3->5 (right click then scroll down)
**Result**: Works, but the key combination is ctrl+pagedown, and the ctrl activates upon release, which is an annoyance for me as ctrl-clicking on text in firefox brings up an answers.com popup.

Previous Tab is predictably similar.

**Action**: Close Tab
**Stroke**: 3->1 (right click then left click)
**Result**: Works, but the combo is ctrl+w, and the ctrl is activated both on gesture completion and on release, bringing up more answers.com popups

**Action**: Undo Close Tab
**Stroke**: 1->3 (left click then right click)
**Result**: Doesn't work. Key combo is Shift+Ctrl+T. Easystroke overlay reads Shift+Ctrl, and the right click immediately goes through and acts normally. The T key is not being simulated?
--

I'm not that clear on whether or not button 3 should be set as instant or not. Anyway, I hope this highlights some small kinks to be ironed out. Thank you again for the great application, support, and development.

Let me know what you think of this, or if I should clarify/try anything.

EDIT: After using the above-described tab gestures a bit more, it turns out that they are highly unreliable. Many times, nothing happens, and I'm not sure what makes the difference. It might just be flash items eating my input. I'll continue to investigate.

---

### Post by Tom Jaeger on 2009-02-10
Thanks for your feedback.

> **EvilGnome said:**
> 
**Action**: Volume Up
**Stroke**: 1->4 (left click then scroll up)
**Result**: Works, but initial click works as regular click (kind of expected, not a problem)
Yup, unavoidable the way you set things up.  What might help here would be another timeout profile that would give you enough time to perform the advanced gesture but would trigger the "timeout" as soon as the mouse is moved.  (this is also necessary for click-and-hold, which some people seem to want, not sure why, though).  Of course, it would have to be possible to set up different timeout profiles for different buttons, but I want to do that for colors anyway.

> 
and the first scroll unit also scrolls in addition to changing the volume (very minor annoyance)

This is a limitation due to the way X servers <= 1.5 work.  If one button is pressed already, any further click will always be sent to the application.  The problem doesn't exist when running easystroke on the upcoming 1.6 server (which will be in jaunty).

> 
**Result**: Works, but the key combination is ctrl+pagedown, and the ctrl activates upon release, which is an annoyance for me as ctrl-clicking on text in firefox brings up an answers.com popup.

Not sure what you mean here.

> 
**Action**: Undo Close Tab
**Stroke**: 1->3 (left click then right click)
**Result**: Doesn't work. Key combo is Shift+Ctrl+T. Easystroke overlay reads Shift+Ctrl, and the right click immediately goes through and acts normally. The T key is not being simulated?

This is the same problem as above.  The T key is pressed but firefox ignores it because of the menu.

> 
I'm not that clear on whether or not button 3 should be set as instant or not.

The thing is that right-clicks will usually result in menus being shown, which will have all sorts of bad side effects.  So you're probably better off not making this an instant button.  The ideal solution (if you want to continue using the button) is the same I outlined for button 1 above.

> 
EDIT: After using the above-described tab gestures a bit more, it turns out that they are highly unreliable. Many times, nothing happens, and I'm not sure what makes the difference. It might just be flash items eating my input. I'll continue to investigate.
Which ones are affected exactly? Any output if you run easystroke through a terminal?  Could this just be timeouts?

---

### Post by EvilGnome on 2009-02-10
Thank you for your response.

> Which ones are affected exactly? Any output if you run easystroke through a terminal? Could this just be timeouts?

No terminal output, don't think it's timeouts. It looks like if a flash element of a webpage has focus, then the gestures I wrote about above that start with a right-click (next, previous, and close tab) will not work. But gestures that start with a left-click DO work, even when the cursor is hovering directly over the flash element. And "regular" gestures (middle-click, drawn figures) work fine everywhere. Temporarily changing button 3 to instant, just for testing, didn't help.

> Not sure what you mean here.

Sorry for that poor explanation. What happens is that when I release a gesture (right-click + scroll) that keys ctrl+pageup, the application in focus receives an undesired ctrl+right-click event. I guess this is the X<=1.5 issue you described. Cool.

Thanks a lot,
Andy

---

### Post by Tom Jaeger on 2009-02-10
> **EvilGnome said:**
> It looks like if a flash element of a webpage has focus, then the gestures I wrote about above that start with a right-click (next, previous, and close tab) will not work. But gestures that start with a left-click DO work, even when the cursor is hovering directly over the flash element. And "regular" gestures (middle-click, drawn figures) work fine everywhere. Temporarily changing button 3 to instant, just for testing, didn't help.

Sorry for that poor explanation. What happens is that when I release a gesture (right-click + scroll) that keys ctrl+pageup, the application in focus receives an undesired ctrl+right-click event. I guess this is the X<=1.5 issue you described. Cool.

I just tested this on an xserver-1.5 system, and I can't reproduce either of those issues.  It is true that ButtonRelease events are always sent to the application (unavoidable on X Servers <= 1.5), but applications generally ignore this, so I don't think that's the problem here.  If you want to investigate this further, could you post the output of 'xev' when performing a Button3-gesture over the xev window?

---

### Post by mr_deimos on 2009-02-11
> **Tom Jaeger said:**
> 
Scrolling works by faking scroll wheel events, which are handled as button presses by the X server and thus inherently discrete.  So this is not really an option -- at least not until the toolkits adopt XI 2.0.
I know that it probably won't be possible to do a system-wide _smooth_ scrolling, but from what i see in current version the scrolling speed is controlled by sending mouse buttons 4-6 at variable frequency - the faster the stylus moves, the more often the clicks are sent. So maybe instead of just stopping to send these mouse buttons after the stylus has been raised, easystroke could just gradually decrease their frequency. I don't know how well it would work, but it might just be worth a try. Scrolling trough long text documents or folder lists in windows mobile in similar way (one line at a time) actually works pretty well with some inertia added. Anyway, it's only an idea and nothing really important as long as scrolling direction is customizable :D

I do have one more feature request - this one shouldn't be too hard. Could easystroke set a few environment variables upon successful stroke recognition? I'm especially interested in coordinates of gesture start and end points. i already checked that inserting system("X_START=70"); in the code makes it possible to later use $X_START variable in command triggered by gesture. I'm just not sure at which point in the code i can obtain start and end coordinates of the stroke.
In case you're wondering what good it's for - i was thinking of creating a little script that would pop up cellwriter right under your pen tip (near where you started the stroke) instead of its last position.

---

### Post by Tom Jaeger on 2009-02-13
> **mr_deimos said:**
> I know that it probably won't be possible to do a system-wide _smooth_ scrolling, but from what i see in current version the scrolling speed is controlled by sending mouse buttons 4-6 at variable frequency - the faster the stylus moves, the more often the clicks are sent. So maybe instead of just stopping to send these mouse buttons after the stylus has been raised, easystroke could just gradually decrease their frequency. I don't know how well it would work, but it might just be worth a try. Scrolling trough long text documents or folder lists in windows mobile in similar way (one line at a time) actually works pretty well with some inertia added.

Sorry, this is really not an option at this point.  In fact, if scrolling is delayed due to the system being too slow to respond, we're actually running in some nasty problems right now.

> 
I do have one more feature request - this one shouldn't be too hard. Could easystroke set a few environment variables upon successful stroke recognition?

Done.  The variables are called "EASYSTROKE_X1" and "EASYSTROKE_Y1" for the starting point and "EASYSTROKE_X2" and "EASYSTROKE_Y2" for the endpoint.

---

### Post by mr_deimos on 2009-02-14
> **Tom Jaeger said:**
> Done.  The variables are called "EASYSTROKE_X1" and "EASYSTROKE_Y1" for the starting point and "EASYSTROKE_X2" and "EASYSTROKE_Y2" for the endpoint.

Thanks a lot, variables work like a charm. So does the inverted scrolling.
In case someone is interested, here's a script i used with EASYSTROKE_X and EASYSTROKE_Y variables:
```
#!/bin/bash
# This script toggles the cellwriter letter recognier and pops up its window at
# designated coordinates. CellWriter has to be running and its window must be already
# created (opened at least once) for the script to work. 
if [ "x$1" == "x" ] ; then
	echo "two parameters needed - desired x and y position of cellwriter window"
	exit 1
fi

#Try to obtain CellWriter's window id

CW_WIN_ID=`xwininfo -name "CellWriter"|grep "id:"|cut -f 4 -d \ `
if [ "x$CW_WIN_ID" == "x" ] ; then
	echo "error: can't find cellwriter window, exiting"
	exit 1
fi


#Check if Cellwriter's window is visible
CW_MAP_STATE=`xwininfo -name "CellWriter"|grep "Map State"|cut -f 2 -d :`
echo "map state: x$CW_MAP_STATE"

#If the window is visible, hide it
if [ "x$CW_MAP_STATE" == "x IsViewable" ] ; then
	echo "cw window is mapped, hiding"
	echo "H" > ~/.cellwriter/fifo
	exit 0
fi

#if the window is hidden, move it to desired coordinates and show it
if [ "x$CW_MAP_STATE" == "x IsUnMapped" ] ; then
	echo "cw window is unmapped, showing"
	echo "moving window to $1 $2"
	xdotool windowmove $CW_WIN_ID $[ $1-20 ] $[ $2-30]
	echo "S" > ~/.cellwriter/fifo
	exit 0
fi

```
I created a gesture triggering command:
```

~/Scripts/cellwriterToggle.sh $EASYSTROKE_X1 $EASYSTROKE_Y1

```
And now cellwriter pops up near the stylus, right where i need it, so i don't have to chase it around the screen anymore ;) It's probably not the best way of doing it (modifying cellwriter itself would certainly work way better), but does the trick well enough for me :D

---

### Post by martynp on 2009-02-15
Upgrade manager gave me the latest version and it won't let me change or add a new action......

is this a bug?

When running from terminal I get this:

Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?

(easystroke:8071): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:2267: signal `button-release-event' is invalid for instance `0xa2f9d70'

Thanks

---

### Post by EvilGnome on 2009-02-15
> **martynp said:**
> Upgrade manager gave me the latest version and it won't let me change or add a new action......

is this a bug?

When running from terminal I get this:

Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?

(easystroke:8071): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:2267: signal `button-release-event' is invalid for instance `0xa2f9d70'

Thanks

It looks like you have multiple easystroke instances running. Just try running
```
killall easystroke
```

and then hit Alt+F2 and run
```
easystroke -g
```

---

### Post by martynp on 2009-02-15
Thanks for the reply..... This is not the problem though.

I followed the above instructions and the problem remains. This has only started occurring since the last upgrade!

Thanks in advance

---

### Post by zhocchao on 2009-02-15
Got the same problem. Cannot change/add commands. Text/key/adding strokes is ok. No error messages running from terminal.

---

### Post by Tom Jaeger on 2009-02-15
> **zhocchao said:**
> Got the same problem. Cannot change/add commands. Text/key/adding strokes is ok. No error messages running from terminal.

This is a known problem that I introduced when adding 'Text' actions.  It will be fixed in 0.4.1 (I'll announce a beta release soon).

---

### Post by Tom Jaeger on 2009-02-15
> **martynp said:**
> Upgrade manager gave me the latest version and it won't let me change or add a new action......

Is it just commands that don't work or is it impossible to add or change any type of action?

Also, what distribution are you running?

> 
Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?
Error: An XInput grab failed
Is easystroke already running?

This means that another program has grabbed an XInput device.  This will only be a problem if this is the device that you want to use for gesturing.  If that's the case and you can't figure out which application is responsible, you can start easystroke as 'easystroke -x' as a last resort, but you'll use functionality.

> 
(easystroke:8071): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:2267: signal `button-release-event' is invalid for instance `0xa2f9d70'

So the gtk documentation lied to me.  What this means in practice is that you won't be able to middle-click on the tray icon to disable easystroke.

---

### Post by martynp on 2009-02-15
I'm running Intrepid.

Anything entered into the command box is either reverted back to it's original when changing or blanked out if adding.

I have changed nothing since before the latest update.

Hope this helps.

Martyn

---

### Post by Tom Jaeger on 2009-02-15
I've just released a beta version for 0.4.1.  The most exciting new feature is a new stroke matching algorithm, which should give much better results (in particular, for sequence-of-line-segments type strokes).
I've also changed the timeout algorithm.  I haven't spent much time adjusting the parameters for the predefined profiles, chances are that some of them are suboptimal.  If you can't find a decent profile, to use, start the program via 'easystroke -e', set the profile to 'Custom' and let me know what parameters work for you.

Other changes include

[LIST]
[*]The 'Command' bug is fixed now.
[*]There is an option to make a gesture button a 'Click & Hold' button, which allows you (in combination with timeout gestures) to assign actions to a click-and-hold gesture, but will instantly timeout if the mouse is moved.  I think timeout gestures are a better solution to this problem, but people seem to want this feature (probably because this is the way windows does it).  A more interesting use case is if you want to use a button for advanced gestures without button presses being passed to the application.
[*]As discussed here earlier, I've added an option to show the last stroke in the tray icon.
[*]There's an option to change scroll speed and direction.
[/LIST]

Packages (0.4.0.98.1) can be downloaded here:
[http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/)

---

### Post by Tom Jaeger on 2009-02-20
I've release 0.4.1 with only cosmetic changes from the beta.

PPA: [https://launchpad.net/~easystroke/+archive/ppa](https://launchpad.net/~easystroke/+archive/ppa)
Download link: [https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=662700](https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=662700)

---

### Post by Tom Jaeger on 2009-03-12
I've made a release candidate for the upcoming 0.4.1.1 release, which I hope to get into jaunty, so let me know if you have any issues with it.  The changes from 0.4.1 are mostly cosmetic except for a few minor bugfixes.

.debs (for intrepid and jaunty) are in my PPA:

[http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/)

The version number of the latest rc is 0.4.1.0.99.2.

---

### Post by pibach on 2009-03-13
Tom, great work, it's getting better and better.

Could briefly explain the way it gets into the repositories? Why don't we get you're stable updates by the normal ubuntu repository? Latest release there is 0.3.1, somehow. Then I don't understand which PPA to add to sources.list to get the latest stable release:
deb [http://ppa.launchpad.net/easystroke/ppa/ubuntu](http://ppa.launchpad.net/easystroke/ppa/ubuntu) intrepid main
or
deb [http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/) intrepid main
?

---

### Post by Tom Jaeger on 2009-03-13
> **pibach said:**
> Tom, great work, it's getting better and better.

Could briefly explain the way it gets into the repositories? Why don't we get you're stable updates by the normal ubuntu repository? Latest release there is 0.3.1, somehow. Then I don't understand which PPA to add to sources.list to get the latest stable release:
deb [http://ppa.launchpad.net/easystroke/ppa/ubuntu](http://ppa.launchpad.net/easystroke/ppa/ubuntu) intrepid main
or
deb [http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/](http://ppa.launchpad.net/thjaeger/ppa/ubuntu/pool/main/e/easystroke/) intrepid main
?

Sorry, I should have explained this earlier, since it is a little confusing.  So the main repo is the easytroke PPA:

[https://launchpad.net/~easystroke/+archive/ppa](https://launchpad.net/~easystroke/+archive/ppa)

This contains the latest stable version and this is what most people would want to add to their sources.list.  If I have pre-release versions (such as the release candidate I posted about yesterday), they'll go into my own PPA ([https://launchpad.net/~thjaeger/+archive/ppa](https://launchpad.net/~thjaeger/+archive/ppa)), so that people can test them if they wish to.  My PPA also usually contains a few other packages, so if you only care about easystroke, I would suggest to just install the .deb.

In Ubuntu, I don't have much control over the package once a new version of Ubuntu is released (unless there are critical bugfixes), this is why for intrepid, we're stuck with 0.2.2.1, and jaunty will have 0.4.1.1.

---

### Post by cta16 on 2009-03-13
Does EasyStroke support multitouch gestures? Or does any other gesture program support multitouch?

---

### Post by Luffield on 2009-03-13
> **cta16 said:**
> Does EasyStroke support multitouch gestures? Or does any other gesture program support multitouch?

I don't think it's currently possible with Linux at all. Multitouch requires [MPX]("http://en.wikipedia.org/wiki/MPX") and it's not currently a part of xorg. I don't think it's too far off though.

---

### Post by Tom Jaeger on 2009-03-14
> **cta16 said:**
> Does EasyStroke support multitouch gestures? Or does any other gesture program support multitouch?

The necessary infrastructure is just not there at the moment.  Once we have MPX and it is clear how multi-touch will be mapped to MPX, it probably won't be too hard to add support to easystroke.  But don't hold your breath, it doesn't seem like anyone has worked the details out yet (see for example [this thread]("http://thread.gmane.org/gmane.comp.freedesktop.xorg/37777") on the xorg mailing list), so I'd be surprised if linux distributions got multi-touch support before Window 7 comes out.

---

### Post by pibach on 2009-03-14
> **Tom Jaeger said:**
> Sorry, I should have explained this earlier, since it is a little confusing...
Thanks for the explanation.

I am using easystroke on my Thinkpad x61 tablet. But I would also like to use it on my Nokia n810. Is their any chance to get a port for Maemo on ARM architecture?

---

### Post by olejorgen on 2009-03-15
One thing that potentially could be useful is chained geastures. (like chained keybindings in eg. emacs) That would increase the number of reliable gestures.

Should be mostly gruntwork to implement too

---

### Post by GrouchoMarx on 2009-03-15
Just upgraded to the new version. Phenomenal work Tom.

It's evident that there's been a big improvement on sequence-of-line-segment stroke recognition. With the previous algorithm it frequently confused the more simple mouse gestures (L == LD, R == RD, etc...). Now it always gets them right. Also really appreciate the return of the last gesture in the icon tray, and with color feedback to boot! Also the system tray icon timeout was a nice touch. And the conservative profile is just right. Really, this 4.1 release has hit all the marks. Thanks again for your great work.

Cheers.

(Ok, so I am nitpicking now: 1) The system tray feedback icons for mouse buttons (4,5, etc...) show up really tiny for some reason, 2) When I switch windows using the mouse wheel via keystroke (Alt+Tab), a blue box appears in the top right corner of the screen saying "Alt" or "Shift+Alt" depending on the modifier. Is this expected behaviour?)

---

### Post by Tom Jaeger on 2009-03-16
> **pibach said:**
> I am using easystroke on my Thinkpad x61 tablet. But I would also like to use it on my Nokia n810. Is their any chance to get a port for Maemo on ARM architecture?

I'm not sure what this entails.  Does the build fail?  Is easystroke not working?  I noticed that Maemo is still based on the kdrive server, so you'll lose some features;  but they're supposed to be switching to xorg in the next version.

---

### Post by Tom Jaeger on 2009-03-16
> **olejorgen said:**
> One thing that potentially could be useful is chained geastures. (like chained keybindings in eg. emacs) That would increase the number of reliable gestures.

The plan is to eventually implement support for different "states", but I don't have a lot of time to work on easystroke at the moment, so this will probably take a few months.

---

### Post by Tom Jaeger on 2009-03-16
> **GrouchoMarx said:**
> Just upgraded to the new version. Phenomenal work Tom.

Thanks.

> 
1) The system tray feedback icons for mouse buttons (4,5, etc...) show up really tiny for some reason,

The main reasons that the numbers are so small is that the tray icon is a scaled-down version of the 'stroke' column and that there needs to be enough space to accommodate extra buttons (represented as "2->2", for example).

I'm open to suggestions, though, I'm not particularly attached to the current design, to say the least.

> 
2) When I switch windows using the mouse wheel via keystroke (Alt+Tab), a blue box appears in the top right corner of the screen saying "Alt" or "Shift+Alt" depending on the modifier. Is this expected behaviour?)

Yes, this is supposed to notify the user that a modifier is currently being held down by easystroke.  This can be turned off ("Show OSD" in the advanced tab) in 0.4.1.1.

---

### Post by Tom Jaeger on 2009-03-16
I've released 0.4.1.1, with virtually no changes since the RC.  It can be downloaded from sourceforge or the easystroke PPA:

[https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=668742](https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=668742)
[https://launchpad.net/~easystroke/+archive/ppa](https://launchpad.net/~easystroke/+archive/ppa)

---

### Post by Scubdup on 2009-03-18
Hi there. Playing around with Easystrokes and I've been impressed with its usability (even I can use it so it must good!)

I'm trying to see if I can change workspaces just using my mouse. I thought I could use easystrokes to have one of my mouse buttons replace Ctrl + Alt and then hopefully press that and drag to change screens but I can't figure out how.

Any ideas?

EDIT: Ignore me. I am blind. My objective can be perfectly achieved by selecting "Viewport Switcher" under "Desktop" in Compiz Config Settings Manager, and in the options, under "Desktop-based Viewport Switching" next to "Initiate Plugin Action" choose the button of your choice from the drop-down menu.

---

### Post by Tom Jaeger on 2009-03-18
[deleted duplicate message]

---

### Post by Tom Jaeger on 2009-03-18
> **Scubdup said:**
> Hi there. Playing around with Easystrokes and I've been impressed with its usability (even I can use it so it must good!)

I'm trying to see if I can change workspaces just using my mouse. I thought I could use easystrokes to have one of my mouse buttons replace Ctrl + Alt and then hopefully press that and drag to change screens but I can't figure out how.

Any ideas?

You can use timeout gestures to emulate Ctrl+Alt+Button1.  See the video below.

[http://easystroke.sourceforge.net/timeout.ogg](http://easystroke.sourceforge.net/timeout.ogg)

---

### Post by olejorgen on 2009-03-20
> **Tom Jaeger said:**
> The plan is to eventually implement support for different "states", but I don't have a lot of time to work on easystroke at the moment, so this will probably take a few months.
Multiple gesture modifiers could be nice too. ie. possible to use both win+right_button and win+left_button and ctrl+middle_button for the same gestures (that does different things)

---

### Post by schmolch on 2009-03-22
I have some problems with easystroke.
ctrl++ and ctrl+- rarely ever work, they are always recognized and the picture is displayed but nothing happens.
Same for ctrl+z (undo).
I would like to use those shortcuts for firefox and xournal to zoom in and out.
If i use the shortcuts physically on the keyboard they always work, but not with easystroke.
Is nobody else having this issue?

PS: Im using Jaunty

---

### Post by Tom Jaeger on 2009-04-08
> **olejorgen said:**
> Multiple gesture modifiers could be nice too. ie. possible to use both win+right_button and win+left_button and ctrl+middle_button for the same gestures (that does different things)

This is possible at the moment using the 'Additional Buttons' feature.  What's not possible is to have different modifiers on the same button bound to different actions, mainly because it doesn't seem that useful a feature and it's not clear how the GUI for that would work.

---

### Post by Tom Jaeger on 2009-04-08
> **Tom Jaeger said:**
> This is possible at the moment using the 'Additional Buttons' feature.  What's not possible is to have different modifiers on the same button bound to different actions, mainly because it doesn't seem that useful a feature and it's not clear how the GUI for that would work.

I can't reproduce this issue.  Can you try executing the following command in a terminal and then move the focus to the firefox window (assuming an American keyboard layout)?  This should be equivalent to what easystroke does when emulating a key press.

```
sleep 3; xte 'keydown Control_L' 'keydown Shift_L' 'key plus' 'keyup Shift_L' 'keyup Control_L'
```

---

### Post by pibach on 2009-04-18
> **Tom Jaeger said:**
> I'm not sure what this entails.  Does the build fail?  Is easystroke not working?  I noticed that Maemo is still based on the kdrive server, so you'll lose some features;  but they're supposed to be switching to xorg in the next version.

I actually have no insight what this would require. But even Jaunty should run on the n810, so then it might be just a matter of compiling it for ARM(?).

Another issue I have with my x61t: I love to use easystroke with the stylus. But with the trackpoint it ads some permanent lag (I am using all gestures straight on left click). Is it possible to deactivate easystroke on the trackpoint but keep it active on the stylus?

---

### Post by Tom Jaeger on 2009-04-18
> **pibach said:**
> Another issue I have with my x61t: I love to use easystroke with the stylus. But with the trackpoint it ads some permanent lag (I am using all gestures straight on left click). Is it possible to deactivate easystroke on the trackpoint but keep it active on the stylus?

Advanced -> Devices

---

### Post by pibach on 2009-04-18
> **Tom Jaeger said:**
> Advanced -> Devices
Wow. Thanks!
Clean and functional interface. Like it. But it is so much more powerful than one might think at first glance that many features remain unexplored. Probably a video tutorial would help?

---

### Post by Depressed Man on 2009-04-29
I don't get it.. I installed easystroke from the Jaunty repo. I changed the method to annotate and then I turned on annotate and dbus in the ccsm (compiz settings manager). Yet nothing shows up when I try to make a stroke.

---

### Post by pibach on 2009-04-30
> **Depressed Man said:**
> I don't get it.. I installed easystroke from the Jaunty repo. I changed the method to annotate and then I turned on annotate and dbus in the ccsm (compiz settings manager). Yet nothing shows up when I try to make a stroke.


Does it work with standard drawing method though?

---

### Post by Depressed Man on 2009-05-01
Nope, nothing shows up when it asks me to draw a stroke. (Can it work with Compiz in default)

Edit: I tried without a mouse and it seems to work. Going try it with a mouse later.

Edit2: Ok I figured out what was wrong. It works with the mouse as well. But the problem is it won't work with application specific gestures. It won't let me create them for them. If I create them in default and then drag and drop them into the application specific ones it'll show up. But then the gestures aren't showing up unless they're also located in default.

---

### Post by zhocchao on 2009-05-03
I have a problem with easystroke crashing on Jaunty. When xinput is disabled it works (mouse and stroke have the same position), but the gestures don't time out, so I can't use the scroll bars (left button). When its enabled, the strokes seem to have a different resolution from the mouse (1 inch mouse=2 inch stroke), so I get out of the screen and then easystroke crashes with segmentation fault (Intel 915 graphics).

How can I assign a double click to a stroke?

As an idea: How about a no_button_mode. After each stroke easystroke should center the mouse and every move is a stroke. Could be useful when watching dvd or listening to music?

---

### Post by Tom Jaeger on 2009-05-03
> **Depressed Man said:**
> 
Edit2: Ok I figured out what was wrong. It works with the mouse as well. But the problem is it won't work with application specific gestures. It won't let me create them for them. If I create them in default and then drag and drop them into the application specific ones it'll show up. But then the gestures aren't showing up unless they're also located in default.

This is intentional.  See this tracker item for details.

[http://sourceforge.net/tracker/?func=detail&aid=2620482&group_id=229797&atid=1078457](http://sourceforge.net/tracker/?func=detail&aid=2620482&group_id=229797&atid=1078457)

---

### Post by Tom Jaeger on 2009-05-03
> **zhocchao said:**
> I have a problem with easystroke crashing on Jaunty. When xinput is disabled it works (mouse and stroke have the same position), but the gestures don't time out, so I can't use the scroll bars (left button). When its enabled, the strokes seem to have a different resolution from the mouse (1 inch mouse=2 inch stroke), so I get out of the screen and then easystroke crashes with segmentation fault (Intel 915 graphics).

I've recently fixed this in git (it's still living on the next branch).  I'm planning to release a new version as soon as I figure out how to reliably detect rotation.

> 
How can I assign a double click to a stroke?

You'll need an external application for that.  Using xte (in the xautomation package) you can do
```
xte 'mouseclick 1' 'mouseclick 1'
```

---

### Post by Tom Jaeger on 2009-05-10
I've just released 0.4.3,  which is mostly a bugfix release, but also adds the ability to drag multiple items.

Download:
[https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=681607](https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=681607)

PPA:
[https://launchpad.net/~easystroke/+archive/ppa](https://launchpad.net/~easystroke/+archive/ppa)

---

### Post by Tom Jaeger on 2009-05-12
Here's another release, I guess this is what 0.4.2 should have been.  This release fixes two annoying bugs, so everyone is encouraged to upgrade.

Download:
[https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=682157]](https://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=682157])

PPA:
[https://launchpad.net/~easystroke/+archive/ppa](https://launchpad.net/~easystroke/+archive/ppa)

---

### Post by sarah.fauzia on 2009-05-23
I'm using ArchLinux now, 64-bit. With 0.4.4 (didn't have this problem with 0.4.3) Easystroke is seg faulting and not working at all. In 0.4.3, it was having problems with the new X Server and running rather sluggishly. Without HAL and hotplugging enabled, Easystroke worked flawlessly (but at the expense of my keyboard not working, so I re-enabled HAL).

---

### Post by Tom Jaeger on 2009-05-23
> **sarah.fauzia said:**
> I'm using ArchLinux now, 64-bit. With 0.4.4 (didn't have this problem with 0.4.3) Easystroke is seg faulting and not working at all.

That's really odd, I don't see any change at all between 0.4.3 and 0.4.4 that could be causing a segfault.  Could you send me a backtrace:

```

git clone git://github.com/thjaeger/easystroke.git
cd easystroke
echo 'DFLAGS = -ggdb' > debug.mk
make -j2
gdb ./easystroke
run
# Wait for crash
bt

```

> 
In 0.4.3, it was having problems with the new X Server and running rather sluggishly. Without HAL and hotplugging enabled, Easystroke worked flawlessly (but at the expense of my keyboard not working, so I re-enabled HAL).
That's also strange.  It could be that some devices are listed twice.  What is the output of 'xinput --list'?

Thanks.

---

### Post by sarah.fauzia on 2009-05-23
I was mistaken--it wasn't 0.4.3 that was acting sluggishly (I was imagining it was whatever version previous than the current one that I upgraded to, but I saw that you updated to 0.4.3 quite recently). It was probably 0.4.1 that I had, or 0.4.2 at best. But I did just upgrade to 0.4.4 and Easystroke is seg faulting, except when I do easystroke -x, but this causes problems with Xournal, where the shape of the gesture activates an actual pen stroke as well as the action of the gesture itself, and a problem with gesture timeouts (but you said the latter would be the case). 

In any case, here's the output of xinput --list. Also, I'm not the only one with this problem--there's another Arch 64 user who has posted at the package's [page](http://aur.archlinux.org/packages.php?ID=20055) detailing the same issue. Here's the pertinent comment from the page:

> Comment by: evilgnome on Thu, 14 May 2009 16:42:12 +0000

    For some reason after the latest update easystroke segfaults when launched here on arch 64. Running in verbose mode tells me that it opened the mouse device before faulting.

```

xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PnP Device (WACf008)"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"ThinkPad Extra Buttons"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PnP Device (WACf008) touch"	id=4	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 50
		Max_value is 931
		Resolution is 106
	Axis 1 :
		Min_value is 80
		Max_value is 953
		Resolution is 141
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PnP Device (WACf008) eraser"	id=6	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"TPPS/2 IBM TrackPoint"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Video Bus"	id=9	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

I'm now using the wacom-names script so the names of my wacom devices are linuxwacom readable, so this output of xinput was before I began using the script. Either way, easystroke still isn't working.

Oh, and here's the backtrace you requested:
```

(gdb) run
Starting program: /home/sara/easystroke/easystroke 

Program received signal SIGSEGV, Segmentation fault.
Grabber::update_device_list (this=0x258) at /usr/lib/gcc/x86_64-unknown-linux-gnu/4.4.0/../../../../include/c++/4.4.0/bits/stl_tree.h:482
482	      { return static_cast<_Link_type>(this->_M_impl._M_header._M_parent); }
(gdb) bt
#0  Grabber::update_device_list (this=0x258) at /usr/lib/gcc/x86_64-unknown-linux-gnu/4.4.0/../../../../include/c++/4.4.0/bits/stl_tree.h:482
#1  0x000000000044cfea in Grabber::init_xi (this=0x10dd490) at grabber.cc:303
#2  0x000000000044d26c in Grabber (this=0x10dd490) at grabber.cc:233
#3  0x0000000000451695 in Main (this=0x7fff9628bac0) at main.cc:1410
#4  0x000000000045193c in main (argc_=<value optimized out>, argv_=0x0) at main.cc:1882

```

---

### Post by Tom Jaeger on 2009-05-25
Thanks for the information.  I believe I have [fixed]("http://github.com/thjaeger/easystroke/commit/efba26ee44ee4492fc28fe57d0a0e6d3bdfca278") the segfault in git now, the problem seems to have been a device that couldn't be opened (just do a 'git pull' in the easystroke directory and then 'make -j2 && ./easystroke').  I'd be interesting to know which one that is, there should be an error message when starting easystroke.

As for the other issue, I'm not sure what you mean by sluggishness.  In any case, a verbose log (easystroke -vvvvv > easystroke.log) when you experience the issue would be helpful.

Thanks.

---

### Post by sarah.fauzia on 2009-05-25
The sluggishness was that when I would make a gesture within an application, the gesture would not immediately be activated. That is not the case in 0.4.4, now, at least not when I run easystroke with -x (I can't run easystroke any other way, with it segfaulting). Sorry for not being more exact. I will try the version in the git repo now, thanks!

---

### Post by sarah.fauzia on 2009-05-25
> **Tom Jaeger said:**
> Thanks for the information.  I believe I have [fixed]("http://github.com/thjaeger/easystroke/commit/efba26ee44ee4492fc28fe57d0a0e6d3bdfca278") the segfault in git now, the problem seems to have been a device that couldn't be opened (just do a 'git pull' in the easystroke directory and then 'make -j2 && ./easystroke').  I'd be interesting to know which one that is, there should be an error message when starting easystroke.

As for the other issue, I'm not sure what you mean by sluggishness.  In any case, a verbose log (easystroke -vvvvv > easystroke.log) when you experience the issue would be helpful.

Thanks.

```

easystroke -vvv
Loaded preferences.
Loaded actions.
grabbing: None
Opened Device "stylus" (absolute, supports proximity).
Segmentation fault
```

Still segfaulting, but here's the log. Thanks for the quick reply! :)

---

### Post by Tom Jaeger on 2009-05-25
> **sarah.fauzia said:**
> 

Still segfaulting, but here's the log. Thanks for the quick reply! :)

Sorry, I'll need another backtrace then.  Could you turn off optimizations by adding the line 'OFLAGS   =' to the file debug.mk and then rebuild (make clean && make -j2) and run gdb again.  Thanks.

---

### Post by sarah.fauzia on 2009-05-25
There's a file debug.mk.ex--would you like me to rename it debug.mk, and use that? It has:

```

DFLAGS   = -ggdb #-pg
OFLAGS   =
CXX      = ccache g++

```

Wait, I configured it with the first two lines in the debug.mk only, and there are no errors being reported by gdb. I tested it out myself, and it's working perfectly.

```

(gdb) run
Starting program: /home/sara/easystroke/easystroke 

```

No errors, as you can see--this is the only output. And the gestures within applications are working perfectly as well! Thanks! :) So I suppose turning off optimizations fixes things? What optimizations are these, exactly?

---

### Post by Tom Jaeger on 2009-05-27
> **sarah.fauzia said:**
> 
No errors, as you can see--this is the only output. And the gestures within applications are working perfectly as well! Thanks! :) So I suppose turning off optimizations fixes things? What optimizations are these, exactly?

These are just compiler optimizations, i.e. different flags passed to g++, they can't really be responsible for fixing the issue.  I guess what you're seeing is the difference between running ./easystroke (the locally built version with the fixes included) and easystroke (whatever is installed in /usr/bin or whereever).  But I'm glad that the sluggishness was fixed, so I'll probably make a 0.4.5 release soon.

---

### Post by sarah.fauzia on 2009-05-27
Thanks, I'm glad to hear it. I've just noticed another little issue that I thought I should bring to your attention. When I make gestures on top of an application, Easystroke functions perfectly, and continues to do so if I close the window (with a gesture, though I tested by closing via gesture or by going to File > Close, and the result is the same), and there is another application open. My window manager is dwm, so applications automatically take up whatever desktop space is available. Say, I had Xournal open in tag three (dwm uses "tags", similar to workspaces). I close Xournal, then Easystroke doesn't function--it doesn't show a single pen stroke on the screen when I try to make a gesture, as if it wasn't running. But if I switch to tag 2 and back to tag 3, Easystroke works again. 

I tried to reproduce the problem with gdb running, and here is what I got:

```

(gdb) run
Starting program: /home/sara/easystroke/easystroke 
XError: BadWindow (invalid Window parameter): X_SetInputFocus
XError: BadWindow (invalid Window parameter): X_SetInputFocus

```

[EDIT] I don't think the backtrace reflects the true nature of the problem, because I did a little test... I enabled the setting in dwm to respect size hints, which I had previously disabled because windows were overlapping each other when they shouldn't. When I enabled it, no errors are reported by the debugger, **yet the problem I specified still exists**. I tried to run Easystroke in verbose mode, yet I didn't see any errors that I could identify, at least...

A little information about size hints from the dwm article in the ArchWiki:

> If you find that there are empty gaps of desktop space outside your terminal windows, it is likely due to your terminal font size. You can either tweak the size until you find a sweet spot that closes the gap, or you can toggle resizehints to False in your config.h file:

static Bool resizehints = False; /* False means respect size hints in tiled resizals */

This will cause dwm to ignore resize requests from client windows--this will affect all windows, not just terminals. The downside to this workaround is that some terminals may suffer redraw anomalies (ghost lines, premature line wraps, etc.).  [/EDIT]

---

### Post by constantin.blanariu on 2009-05-28
Hey, Tom!

I'm looking forward to setting up easystroke and use it intensively, but unfortunately I have a problem with it.

When I push Record Stroke for an action, the window shows up, but even though I draw something with
the mouse, nothing happens, the stroke does not get recorded and the window does not disappear unless
I push the Cancel button.

I am using Jaunty on a amd64 system.

If you need any more info please tell me and I will provide it.

Thank you,

Constantin

---

### Post by Tom Jaeger on 2009-05-29
> **constantin.blanariu said:**
> Hey, Tom!

I'm looking forward to setting up easystroke and use it intensively, but unfortunately I have a problem with it.

When I push Record Stroke for an action, the window shows up, but even though I draw something with
the mouse, nothing happens, the stroke does not get recorded and the window does not disappear unless

Are you using the latest version (i.e. 0.4.4)?

---

### Post by constantin.blanariu on 2009-05-30
> **Tom Jaeger said:**
> Are you using the latest version (i.e. 0.4.4)?

Yes, I have 0.4.4-0ubuntu1~jaunty.

---

### Post by sarah.fauzia on 2009-06-03
I should mention that my problems with Easystroke have only gotten worse :(. Easystroke is randomly crashing X when I make a gesture; random, as it happens with different gestures and isn't the slightest bit predictable. So, randomly when making a gesture I'm taken back to the console where I have to re-login... I've already once lost a little bit of work. But this really is the best gesture application of all time, so I really can't stop using Easystroke, even while I feel under the constant threat of losing my work and doing (File-Save As) nearly continuously.

Thanks for looking into these issues.

---

### Post by inspriation26 on 2009-06-03
dude that sounds amazing! I'll have to try that out!

---

### Post by Tom Jaeger on 2009-06-08
> **sarah.fauzia said:**
> I should mention that my problems with Easystroke have only gotten worse :(. Easystroke is randomly crashing X when I make a gesture; random, as it happens with different gestures and isn't the slightest bit predictable. So, randomly when making a gesture I'm taken back to the console where I have to re-login... I've already once lost a little bit of work. But this really is the best gesture application of all time, so I really can't stop using Easystroke, even while I feel under the constant threat of losing my work and doing (File-Save As) nearly continuously.

Thanks for looking into these issues.

Unfortunately, I'm a little short on time right now, so I probably won't be able to install arch and look at the issues myself for a few weeks, but I am aware of one crasher-bug in the 1.6 xserver that can be triggered by using easystroke in a specific way:

[http://bugs.freedesktop.org/show_bug.cgi?id=19034](http://bugs.freedesktop.org/show_bug.cgi?id=19034)

The patch attached to that bug report never made it into the official xserver repository, but ubuntu jaunty is using the patch, so it should be considered reasonably safe.  I don't know if this is the bug that you're seeing, but in any case, in order to investigate it further, an xserver backtrace would be helpful.

---

### Post by sarah.fauzia on 2009-06-10
Oh, all right then. Perfectly understand the time issues; I'll try to get a backtrace, and then use the patch you mentioned. Thanks.

---

### Post by sarah.fauzia on 2009-06-13
I tried to retrieve the backtrace, but whenever I would attach gdb to the xserver process, X would freeze, so I couldn't reproduce the problem. I'll admit I'm not very experienced in this arena, but if you have any suggestions, I would appreciate them. If not, I'll just try again as soon as I have the time. Thank you for taking precious time to explain your own time-based difficulties.

---

### Post by Johnmajor on 2009-06-14
Hey I'm new to both Ubuntu and Easystroke. As a Windows convert it looks like a great replacement for Strokeit thus far. However is it possible to send automated text in Pidgin messenger using a gesture?

In Strokeit you could just set it as 'text goes here [enter]'. Is there anyway to do a similar action in Easystroke? Thanks in advance.

---

### Post by Tom Jaeger on 2009-06-15
> **sarah.fauzia said:**
> I tried to retrieve the backtrace, but whenever I would attach gdb to the xserver process, X would freeze, so I couldn't reproduce the problem. I'll admit I'm not very experienced in this arena, but if you have any suggestions, I would appreciate them. If not, I'll just try again as soon as I have the time. Thank you for taking precious time to explain your own time-based difficulties.

Did you type 'cont' at the gdb prompt to continue running the process? (all this needs to be done over ssh)

---

### Post by Tom Jaeger on 2009-06-15
> **Johnmajor said:**
> Hey I'm new to both Ubuntu and Easystroke. As a Windows convert it looks like a great replacement for Strokeit thus far. However is it possible to send automated text in Pidgin messenger using a gesture?

In Strokeit you could just set it as 'text goes here [enter]'. Is there anyway to do a similar action in Easystroke? Thanks in advance.

I'm not sure I understand the question, but you might want to look into whether pidgin can be controlled from the command line.  If you just want to insert a fixed text, there's a 'Text' action that can do that.

---

### Post by sarah.fauzia on 2009-06-17
> **Tom Jaeger said:**
> Did you type 'cont' at the gdb prompt to continue running the process? (all this needs to be done over ssh)

Well, that'd explain it. Didn't use ssh. I'll try again during the weekend--thanks!

---

### Post by Melhisedek on 2009-07-04
Can easystroke assing buttons? I want left tilt of my middle mouse button to act as a middlemouse press. Is that possible?

Thank you for your time!

---

### Post by Tom Jaeger on 2009-07-04
> **Melhisedek said:**
> Can easystroke assing buttons? I want left tilt of my middle mouse button to act as a middlemouse press. Is that possible?

Yes.  Add the tilt button as an additional button and be sure to check "Instant Gestures".  Then record a gesture by clicking the button and assign Button/Button3 as its action.

Alternatively, you can use the xinput tool to change the button mapping of the device.

---

### Post by sarah.fauzia on 2009-07-12
Here's something strange I have noticed for quite some time... I'm sorry, but I can't pinpoint it with having started with a specific past release, though I know, in the past, I didn't have this problem. I have a gesture for the shape recognizer tool (activated by the keystroke Shift-Cntrl-s), but when I make the gesture, Xournal does not activate the shape tool (but sometimes eventually will, after many, many repeated times, and after using gestures for other tools, e.g. the ruler). However, easystroke is recognizing my gesture for the shape tool everytime (as seen by examining the history).

[edit] This was a bug with Xournal in activating the keyboard shortcut for the shape tool in fullscreen, and there is an easy fix for this at Xournal's sourceforge page, in Denis' comment to my bug report. [/edit]

---

### Post by sarah.fauzia on 2009-07-19
Tom, X server is *still* crashing because of easystroke. I discovered something in my Xorg.0.log that I think is the backtrace you needed (which appeared after an X server crash because of easystroke):

```

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4ee356]
1: /usr/bin/X(xf86SigHandler+0x6f) [0x49234f]
2: /lib/libc.so.6 [0x7f0f688c8f90]
3: /usr/bin/X(DeliverEventsToWindow+0x454) [0x45a124]
4: /usr/bin/X(DeliverDeviceEvents+0x32f) [0x45acdf]
5: /usr/bin/X(ProcessOtherEvent+0x3b3) [0x53bf83]
6: /usr/bin/X(ProcessKeyboardEvent+0xd0) [0x5630d0]
7: /usr/bin/X(mieqProcessInputEvents+0x340) [0x4cf4c0]
8: /usr/bin/X(ProcessInputEvents+0x9) [0x492df9]
9: /usr/bin/X(Dispatch+0x2ad) [0x44d36d]
10: /usr/bin/X(main+0x3b5) [0x4339d5]
11: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f0f688b59ed]
12: /usr/bin/X [0x432e59]

Fatal server error:
Caught signal 11.  Server aborting

```

I really hope you can fix it soon because it's no fun losing one's work randomly when using easystroke, and easystroke is an indispensable piece of software.

---

### Post by gazzanova on 2009-07-26
> **constantin.blanariu said:**
> Hey, Tom!

I'm looking forward to setting up easystroke and use it intensively, but unfortunately I have a problem with it.

When I push Record Stroke for an action, the window shows up, but even though I draw something with
the mouse, nothing happens, the stroke does not get recorded and the window does not disappear unless
I push the Cancel button.

I am using Jaunty on a amd64 system.

If you need any more info please tell me and I will provide it.

Thank you,

Constantin

Has anyone found a solution to this problem?

i'm getting this too

currently running sabayon 4.2 with compiz and easystroke 0.4.7

---

### Post by Tom Jaeger on 2009-07-31
> **gazzanova said:**
> Has anyone found a solution to this problem?

i'm getting this too

currently running sabayon 4.2 with compiz and easystroke 0.4.7

Sabayon appears to be running an old (1.5) xserver that I don't test against anymore.  Could you try older versions of easystroke to see if this a regression and when it was introduced?

---

### Post by gazzanova on 2009-08-02
> **Tom Jaeger said:**
> Sabayon appears to be running an old (1.5) xserver that I don't test against anymore.  Could you try older versions of easystroke to see if this a regression and when it was introduced?

Fantastic Tom!!!

I had to revert to version 0.3.1 to get it to run on my system

Once again thanks Tom

---

### Post by Tom Jaeger on 2009-08-15
> **constantin.blanariu said:**
> Hey, Tom!

I'm looking forward to setting up easystroke and use it intensively, but unfortunately I have a problem with it.

When I push Record Stroke for an action, the window shows up, but even though I draw something with
the mouse, nothing happens, the stroke does not get recorded and the window does not disappear unless
I push the Cancel button.

I am using Jaunty on a amd64 system.

If you need any more info please tell me and I will provide it.

Thank you,

Constantin

> **gazzanova said:**
> Has anyone found a solution to this problem?

i'm getting this too

currently running sabayon 4.2 with compiz and easystroke 0.4.7

I've just released 0.4.8, which fixes a bug that could be the cause of this.

---

### Post by hamsandwich on 2009-08-17
First off, awesome software. This should be available on every operating system, now that I've been using it for a while I couldn't do without it.

I recently upgraded to Jaunty amd64 and easystroke was working, but with a recent update (within the last week or two) gestures do not work. Launching it a in a terminal I get the dreaded "an Xinput grab failed...". I can get it to work by using 'easystroke -x'. It now seems to work fine for me but I am wondering what kind of features I am now missing by doing this.

Thanks!

---

### Post by Tom Jaeger on 2009-08-17
> **hamsandwich said:**
> First off, awesome software. This should be available on every operating system, now that I've been using it for a while I couldn't do without it.

I recently upgraded to Jaunty amd64 and easystroke was working, but with a recent update (within the last week or two) gestures do not work. Launching it a in a terminal I get the dreaded "an Xinput grab failed...". I can get it to work by using 'easystroke -x'. It now seems to work fine for me but I am wondering what kind of features I am now missing by doing this.

Thanks!

There's two causes of this error messages that I can think of:  A device isn't behaving correctly or there is an application that has an active grab on one or more devices.  I would try only enabling the device that you're using for gestures in Advanced/Devices.  Unfortunately, there's no way of telling which application is responsible for a grab (apart from running gdb on the X server), so this is kind of hard to debug.  Are there any applications you've recently started using?

What you're missing when using the -x switch is the gesture timeout feature as well as the ability to use advanced gestures and timeout gestures.

---

### Post by atimkara on 2009-08-18
> **Tom Jaeger said:**
> Are there any applications you've recently started using?


I switched from xfce4 to gnome and started seeing this error.

&#9660;
&#9650;

---

### Post by Tom Jaeger on 2009-08-18
> **atimkara said:**
> I switched from xfce4 to gnome and started seeing this error.


A standard gnome setup doesn't interfere with easystroke at all, so it must be some special application or some special setting.  I'm not aware of any other applications that use XGrabDeviceButton at all (and google codesearch couldn't find any), so this is kind of a mystery to me.  Does this happen for any gesture button or just for specific buttons/modifier combinations?

---

### Post by hamsandwich on 2009-08-18
> **Tom Jaeger said:**
> There's two causes of this error messages that I can think of:  A device isn't behaving correctly or there is an application that has an active grab on one or more devices.  I would try only enabling the device that you're using for gestures in Advanced/Devices.  Unfortunately, there's no way of telling which application is responsible for a grab (apart from running gdb on the X server), so this is kind of hard to debug.  Are there any applications you've recently started using?

What you're missing when using the -x switch is the gesture timeout feature as well as the ability to use advanced gestures and timeout gestures.

Hmmm. I use apt-get frequently, probably too frequently. But the only thing of consequence I recall installing recently is checkgmail. Problems very well may have occurred during a normal software update of existing packages. I would be glad to look at it further, but I don't know how to start an X session with gdb or what to look for.

---

### Post by atimkara on 2009-08-18
> **atimkara said:**
> I switched from xfce4 to gnome and started seeing this error.


I dont know what's happened but it is working now.
&#9660;
&#9650;

---

### Post by zhocchao on 2009-08-21
It seems that easystroke doesn't work with fvwm (I tried with Metisse). I got some xlib errors. Is that a known issue?

---

### Post by Tom Jaeger on 2009-08-21
> **zhocchao said:**
> It seems that easystroke doesn't work with fvwm (I tried with Metisse). I got some xlib errors. Is that a known issue?

I just tested fvwm and fvwm2, and both worked fine.  What is the exact error message?

---

### Post by zhocchao on 2009-08-23
I get this

```

a@gs:~$ easystroke
Xlib:  extension "RANDR" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Warning: XInput extension not available
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".

```

I get this for a new user. When I try with normal user, I have to stop easystroke from autostart to have Metisse working.

edit:Could be a Metisse problem. I discovered that fvwm-crystal is not working on my installation.

---

### Post by Tom Jaeger on 2009-08-23
> **zhocchao said:**
> I get this

```

a@gs:~$ easystroke
Xlib:  extension "RANDR" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Warning: XInput extension not available
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".
Xlib:  extension "Generic Event Extension" missing on display "127.0.0.1:1.0".

```

I get this for a new user. When I try with normal user, I have to stop easystroke from autostart to have Metisse working.

edit:Could be a Metisse problem. I discovered that fvwm-crystal is not working on my installation.

Metisse seems to be using a custom-modified X server going at least back to 2004, which doesn't have the necessary extensions to run easystroke properly.  They also seem to have gotten the X protocol slightly wrong, easystroke should fall back to using only core requests, which should work on X servers of any kind.

---

### Post by BionicSeahorse on 2009-08-29
I just tried adding an application and X crashed:

```
$ easystroke -v
Opened Device "Macintosh mouse button emulation" (relative, does not support proximity).
Opened Device "Logitech USB Receiver" (absolute, does not support proximity).
Opened Device "Logitech USB Receiver" (relative, does not support proximity).
Error: A grab failed.  Resetting...
Fatal Error: Connection to X server lost, restarting...

```

The same thing happened when I tried adding a WM_CLASS exception. The really weird part is that I was able to add an application (opera) and configure some strokes just fine minutes before. Now all I get is a crashed X every time.

I am running Kubuntu 9.04 amd64 with compiz git. Let me know if you need more details and I will post them for you.

Any help would be appreciated!

---

### Post by Tom Jaeger on 2009-08-29
> **BionicSeahorse said:**
> I just tried adding an application and X crashed:

```
$ easystroke -v
Opened Device "Macintosh mouse button emulation" (relative, does not support proximity).
Opened Device "Logitech USB Receiver" (absolute, does not support proximity).
Opened Device "Logitech USB Receiver" (relative, does not support proximity).
Error: A grab failed.  Resetting...
Fatal Error: Connection to X server lost, restarting...

```

The same thing happened when I tried adding a WM_CLASS exception. The really weird part is that I was able to add an application (opera) and configure some strokes just fine minutes before. Now all I get is a crashed X every time.

I am running Kubuntu 9.04 amd64 with compiz git. Let me know if you need more details and I will post them for you.

Any help would be appreciated!

Does this only happen with compiz or are other window managers affected, too?  I tried looking at the compiz source, but they split up everything into a thousand repositories, do you know of any way of downloading them all?  Since this is a server crash, could you attach an Xorg.log?
Your mouse seems fishy to me.  There are two devices with the same name (which unfortunately means that you can't disable one of them in easystroke).  Easystroke should be able to deal with this, but it is possible that they're sending out events more or less at the same time and trigger a race condition in the server.  Do you have another mouse that you can test this with?

Thanks.

---

### Post by Davaris on 2009-08-29
Just suggestion:
Can you it make it work so a gesture can accept multiple strokes? I am a pen user and I want to be able to write code words, so I don't have to remember anything.

A guy call Sumocat uses ritePen this way with his tablet and has hundreds of commands available to him and many of his commands use words that are similar to each command.

---

### Post by BionicSeahorse on 2009-08-30
> **Tom Jaeger said:**
> Does this only happen with compiz or are other window managers affected, too?  I tried looking at the compiz source, but they split up everything into a thousand repositories, do you know of any way of downloading them all?  Since this is a server crash, could you attach an Xorg.log?
Your mouse seems fishy to me.  There are two devices with the same name (which unfortunately means that you can't disable one of them in easystroke).  Easystroke should be able to deal with this, but it is possible that they're sending out events more or less at the same time and trigger a race condition in the server.  Do you have another mouse that you can test this with?

Thanks.

The reason why you see the two Logitech devices is probably due to the fact that I have two separate receivers: one for my wireless keyboard and a separate one for the mouse. One receiver is supposed to take care of both devices, but in my case I upgraded to a MX Revolution mouse and the original dongle won't recognize it, so I physically disconnected the mouse portion from the first receiver and connected the new dongle alongside it instead.

What I did just now for testing purposes was connect yet another Logitech wireless keyboard/mouse combo that I have lying around and disconnected all the other receivers, and easystroke is grabbing windows again!

So I guess if there were a way to disable the keyboard receiver and just keep the MX Revo receiver enabled inside easystroke, things would be perfect in my case. But all I saw with my easystroke advanced pane was one entry for a "Logitech USB Receiver", not two.

BTW, Compiz was definitely not the problem either. KWin also triggered this crash just the same.

Hope that all made some sense! I would attach the Xorg.log file, but I figured it wasn't needed now that we know what the problem is.

Is there anything else that you'd like me to try, Tom? Thanks again for such a cool app.

---

### Post by Tom Jaeger on 2009-08-30
> **BionicSeahorse said:**
> 
So I guess if there were a way to disable the keyboard receiver and just keep the MX Revo receiver enabled inside easystroke, things would be perfect in my case. But all I saw with my easystroke advanced pane was one entry for a "Logitech USB Receiver", not two.

That's not possible unfortunately.  The only reliable way for easystroke to identify devices is by their name, so you'd have a 50% chance of easystroke disabling the wrong device.  It's also not clear if this would prevent the server crash from happening.  There might be a way to disable the device altogether using hal, but I'm not familiar enough with hal to know how this would work.

> 
Hope that all made some sense! I would attach the Xorg.log file, but I figured it wasn't needed now that we know what the problem is.

I'd still like to see an Xorg.log.  This crash might be easy to fix, and the log contains a backtrace that you can use to see where exactly the crash happened.

Thanks.

---

### Post by BionicSeahorse on 2009-08-30
> **Tom Jaeger said:**
> I'd still like to see an Xorg.log.  This crash might be easy to fix, and the log contains a backtrace that you can use to see where exactly the crash happened.

Thanks.

I just tried replicating the error and easystroke was able to grab just fine! So I guess this crash doesn't happen every single time. I promise to attach the log as soon as it crashes again.

---

### Post by R3fr4cti0n on 2009-09-27
so will this work for touchscreen gesture recognition?

---

### Post by Tom Jaeger on 2009-09-27
> **R3fr4cti0n said:**
> so will this work for touchscreen gesture recognition?

I don't see why it wouldn't.

---

### Post by azteca_04 on 2009-09-27
Hi, i don't know if its possible or not, but what i want to do is make a script that when i ran it it execute Alt + F4 or Fn + F8 on a laptop, this is because i will not have a keyboard on that laptop i'm going to execute that script using ssh from another computer, can it be done?? thanks for the help

---

### Post by avel on 2009-09-30
May I just say what a **brilliant** piece of software easystroke is.

It works on my HP TX1000ux tablet like a charm.

One of the best things about it is its customized gestures per-application. They can be defined very easily and it's *so* versatile! 

So, the one application that was benefited most by easystroke was chromium browser (aka Google Chrome). With easytrokes, one can define mouse gestures for chromium very easily, and bring Opera-style mouse gestures to it.

And by having it at the window-manager / system level instead of the application level, it seems to work more smoothly, too. And the visual feedback is very nice!

[IMG]http://null.noc.uoa.gr/public/misc/chromium-easystroke-gestures.png[/IMG]

---

### Post by varsamakos on 2009-10-09
That was very helpful avel!
Thanks for sharing.

---

### Post by Tekmoor on 2009-10-20
I have a couple questions/feature requests about Easystoke:

My first question is about the blue notifications that appear in the top right of the screen when a modifier key is in use (e.g. when I do my alt-tab stroke the word alt appears in a blue box in the top right). It'd be nice to turn these off as I find them distracting and I'm not sure why they're there.

Second I wonder if there could be a better way to cancel strokes. I find I, quite often, start performing a stroke and then change my mind (e.g. I am going to close a Firefox tab, but then see something interesting on the page and decide not to) and at this point I need to cancel the stroke. The way I do this is just by making a bunch of scribbles so that Easystroke doesn't recognize the stroke as anything and therefore Easystroke doesn't do anything when it gets the stroke. But I'd love a way to be able to cancel strokes faster and easier. I realize there is a stroke timeout option, however I find this isn't a good solution (I have timeout off) because either you have to wait awhile for the timeout or it just happens too soon, the timing can never be perfect as each stroke is different.

I just want to emphasis that these are minor things, I've been constantly using Easystroke everyday since basically right when this thread was created and I've found it incredibly helpful and time-saving, so thank you very much Tom (and thanks for reading this)!

[SIZE=1](forgive me if these things were already discussed in the thread, I did a search but didn't see them)[/SIZE]

---

### Post by Tom Jaeger on 2009-10-27
> **Tekmoor said:**
> I have a couple questions/feature requests about Easystoke:

My first question is about the blue notifications that appear in the top right of the screen when a modifier key is in use (e.g. when I do my alt-tab stroke the word alt appears in a blue box in the top right). It'd be nice to turn these off as I find them distracting and I'm not sure why they're there.

Advanced/Show OSD.

> 
Second I wonder if there could be a better way to cancel strokes. I find I, quite often, start performing a stroke and then change my mind (e.g. I am going to close a Firefox tab, but then see something interesting on the page and decide not to) and at this point I need to cancel the stroke.


One thing that comes to mind is just pressing a different mouse button.  By default, this will let the click through, but if you define the appropriate advanced gesture and enable the "ignore strokes leading up to advanced gestures" (which hopefully still works, I haven't tested it in a while...) you can get it to do nothing.

For a while, you could abort gestures by pressing Escape, but I had to remove this feature as it would lock up the X server in rare instances.

If you have any other ideas about how to abort gestures, I'd be interested to hear them.

---

### Post by Tekmoor on 2009-10-28
> Advanced/Show OSD.Wow, I'm not sure how I missed that... thanks!

> If you have any other ideas about how to abort gestures, I'd be interested to hear them.     It's tricky, but one possibility may be to have a timeout that only starts once the cursor is idle. I.e. when the user is performing a stroke and the cursor has not moved for X seconds then cancel the stroke.
Again, it's a pretty minor thing.

---

### Post by feistybird on 2009-11-20
Thank you! easystroke is really a useful utility that can improve gnome desktop usability.

My compiz stopped working since upgraded to 9.10 karmic, yet the "view port switcher" function (switching workspaces by scrolling the mouse wheel under compiz) is a must for me  (sort of "boss-key" for my Gnome desktop), so I found the easystroke,  it made the worksapce switching even more easy and convenient with simple mouse gestures!  I hope gnome team can include this useful utility into the future Gnome versions by default.

---

### Post by przemo_li on 2009-11-25
Hi, Your App is great !!

But unfortunately this to commands don't work for me (both actions type command).

xte 'keydown Alt_L' 'key F2' 'keyup Alt_L'
xte 'keydown Alt_L' 'key F4' 'keyup Alt_L'

Both works fine if lunched from console (Gnome Terminal).

Commands that are names of apps works fine.

I've tried to use Key type with Alt + Tab and Ctr + T but none of them works.
Ok Ctr + T worked once but when after 10 that did not work.

---

### Post by pibach on 2010-01-29
Hi Tom, 

weired behavior: I use easystroke on pen, when I mark a word in Firefox, gesture tmes out as expected and word gets marked. When I use Chrome, then the text selection does not start at the beginning stroke of the gesture but at the point when it times out. Difficult to use for text selection. Is this a Chrome issue? Or an easystroke one?

---

### Post by cosimo on 2010-01-30
Hey TOm,.
  I try to contact you on a monthly basis to say thanks for one of the best applications for gesture recognition available.
  It is a pleasure using easystroke...it is , in my opinion, near flawless!! :)
Anyone unfamiliar with easystroke should install and try it out.
Since it is systemic,  it works with everything including compiz!
I have used gesture recognition software on both windows and mac  and easystroke is far superior to any available on those platforms.
  With this application, once you have used it, cuts work time by 1/3  , actually more !!
open..close..activate..delete...whatever you do can be done with a mouse can be done with gestures.
 Close an application and open another in a second!
The tie in with compiz using annotate is also quite cool!
   I push easystroke on both #compiz and #cairo-dock channels whenever I can.
I consider easystroke to be one of the best "companion" applications to compiz that is out there let alone the best companion application for Linux in general.
 Thanks Tom..and dont let this die :)

coz

---

### Post by Luffield on 2010-01-30
Hear, hear!

---

### Post by pibach on 2010-01-30
> **cosimo said:**
> Hey TOm,.
  I try to contact you on a monthly basis to say thanks for one of the best applications for gesture recognition available.


Couldn`t agree more.
In 2010 we will see lots of Arm based touch tabtets such as iPad. There easystoke could become even more valuable.

---

### Post by realzippy on 2010-01-30
Yeah.easystroke is great!!
One of the most useful apps ever...really miss it when on other machines.
Thanks,Tom!!

---

### Post by pibach on 2010-02-08
> **pibach said:**
> Hi Tom, 

weired behavior: I use easystroke on pen, when I mark a word in Firefox, gesture tmes out as expected and word gets marked. When I use Chrome, then the text selection does not start at the beginning stroke of the gesture but at the point when it times out. Difficult to use for text selection. Is this a Chrome issue? Or an easystroke one?
Could anybody test this weired behavior with Google Chromium? Thanks.

---

### Post by Luffield on 2010-03-26
Is anyone currently having problems with Easystroke on Lucid? I've used it for a few weeks and it worked great, but I've just updated my system and Easystroke stopped working (the app is running, but gestures are not being drawn or recognized).
I'm testing Lucid on Virtualbox and I installed a new version of Virtualbox today so this might actually be where the problem lies.

---

### Post by schmolch on 2010-03-26
> **Luffield said:**
> Is anyone currently having problems with Easystroke on Lucid? I've used it for a few weeks and it worked great, but I've just updated my system and Easystroke stopped working (the app is running, but gestures are not being drawn or recognized).
I'm testing Lucid on Virtualbox and I installed a new version of Virtualbox today so this might actually be where the problem lies.

I have a different problem on Lucid.
It registers my secondary pen-button even when the pen is not pressed down on the screen. I guess thats a issue with linuxwacom.
Other than that it works.

---

### Post by Luffield on 2010-03-27
schmolch, are you running Lucid on a real computer or a virtual one?

---

### Post by schmolch on 2010-03-27
real

---

### Post by chriskin on 2010-03-27
i don't know if this is considered a bug but it's a little annoying sometimes : certain gestures are recognised as something that they don't even look like. (a clearly painted pentagon got recognised as a triangle today, for example)

is there any way to make easystroke accept gestures only if they are more than 80-85% similar to the target gesture?

---

### Post by Luffield on 2010-03-28
OK, the issue I'm having must be a Virtualbox bug. I upgraded my laptop to Lucid today and easystroke works well.

---

### Post by nsk7even on 2010-04-17
Hello, I use easystroke for my touchscreen laptop GA-T1028X and it works really well.

But I can not configure CAPS LOCK as an action. Anyone an idea why?

Maybe there is another alternative to be able to write capital letters instead of learning easystroke the complete alphabet twice? :D

---

### Post by sarah.fauzia on 2010-04-17
When I upgraded to the latest boost in ArchLinux's repos, 1.41.0-1, my old gesture database was incompatible, and I had to re-make all my gestures from scratch. This is pitiful enough, but the problem I have is worse. My gesture for moving windows to another workspace, which utilizes the keyboard command Mod-Shift-{1,...,9} in Xmonad, no longer works, but it worked before. I tried to check if this was related to upgrading boost by downgrading and making the gesture again, and strangely enough, it didn't work with the old boost either. So the problem must have existed with it too, but it wasn't apparent until I had to delete my old gestures file.

The only error I get from the terminal is when I start Easystroke, and that is:

```
Error: Connection to DBus failed
```

which I don't know why I'm getting, as both hal and dbus are running.

It might be helpful to note that before I upgraded boost, I was also running the xorg-server-antidesktop package in ArchLinux, which enables running the latest X server without hal. So I had dbus then, for easystroke, but no hal. So my problem might have now appeared because I'm using X server with hotplugging enabled.

Thank you for your help.

Sara

---

### Post by Vesperatus on 2010-05-06
I seem to be having issue understanding how the click and hold works.

I'm using a touchscreen and I can only make it work if I use a combination of a key and the mouse 1 button.

I can't have the click and hold feature working. 
If I enable ( click and hold ) Button 1, the last gesture in my history is the correct one but there is a " 3 -> " drawn over it. 

If I enable "Ctrl - Button 1", the history shows the correct gesture without the " 3 -> ".

Any idead ? Running Lucid lynx netbook remix.

---

### Post by Eudinaesis on 2010-05-13
Hrm. I'm having an odd problem with Easystroke on Lucid 10.04 -- whenever I try to make a gesture with my pen, the program closes/crashes. I'm using a Lenovo x61t tablet. This problem doesn't seem to happen if I enable the touchstick and try using that instead, but of course the whole point is to use it when in tablet mode. Any ideas?

---

### Post by ThomasAdam on 2010-05-14
> **zhocchao said:**
> It seems that easystroke doesn't work with fvwm (I tried with Metisse). I got some xlib errors. Is that a known issue?

Don't see why you'd need this with FVWM, seeing as that has stroke support built in to it, and can act as a per-window binding anyway.

-- Thomas Adam

---

### Post by Eudinaesis on 2010-05-14
Hrmm - I managed to get it working in Lucid by recompiling version 4.11 (I was using 4.9 back on Karmic). Neither 5.3 nor 5.2 would work, even when I recompiled them. Not sure what's going on with that.

---

### Post by primetime34 on 2010-05-16
How can you have the fire on screen from compiz be used with the easystroke gestures like some youtube videos have?

---

### Post by primetime34 on 2010-05-16
So does nobody know how to do this?

---

### Post by nsk7even on 2010-05-16
Don't know what you mean...

---

### Post by primetime34 on 2010-05-16
I have seen a youtube video or two where the users gestures are shown via firestrokes...see this video to see what I mean [http://www.youtube.com/watch?v=wud2npWU20E](http://www.youtube.com/watch?v=wud2npWU20E)

---

### Post by nsk7even on 2010-05-17
lol you won't believe it: after minutes of experimenting with settings of Compiz Fire Plugin I looked into Easystroke and voilà there is an option for that! :D :D

It is on second tab in the middle (I ommit my german titles and own translation attempts, you will find it) ;)

And it looks really nice, I think I will keep it - thanx for that idea!

---

### Post by primetime34 on 2010-05-18
Great find...can't believe I missed it!!

---

### Post by realzippy on 2010-06-01
...fire stopped working.Lucid/gnome/emerald/NVIDIA/2.6.32-22.When gesturing,screen freezes,
fire stays...anyone else?

---

### Post by Luffield on 2010-06-01
Yup, same thing happened on my machine.

---

### Post by Legendary_Bibo on 2010-06-01
This will go perfectly hand in hand with my Okami-esque desktop.

---

### Post by realzippy on 2010-06-01
> **Luffield said:**
> Yup, same thing happened on my machine.

tried compiz package from tom`s ppa;unfortunately it does not help.
You also run Lucid64/gnome/emerald/NVIDIA/2.6.32-22  ??

---

### Post by Luffield on 2010-06-01
Lucid, gnome, nvidia, same kernel (generic), but I'm not using emerald. Happened to me on a 64-bit installation, and reinstalling the 32-bit version didn't solve this.

---

### Post by realzippy on 2010-06-01
I also tested new nvidia beta driver;same issue.

---

### Post by Legendary_Bibo on 2010-06-01
I started it up but nothing happened.

---

### Post by Luffield on 2010-06-01
not even a new icon in the tray?

---

### Post by realzippy on 2010-06-01
@bibo

you run jaunty?
Had this issue on 9.04,simply did not work..

---

### Post by realzippy on 2010-06-01
fire works again...after *disabling* sync to VBlanc in CCSM/GeneralOptions/DisplaySettings...

---

### Post by nsk7even on 2010-06-01
For me it's still working: Lucid with 2.6.32-22 and NVIDIA GTX 260 with 195.36.24
//Edit: oh I missed last post

---

### Post by Legendary_Bibo on 2010-06-01
> **realzippy said:**
> @bibo

you run jaunty?
Had this issue on 9.04,simply did not work..
Nope, I have lucid. When I click on it to start it up an icon goes to my icon tray and when I click on it, it just makes my screen flash.

---

### Post by MountainX on 2010-07-06
> **Tom Jaeger said:**
> Hi,

I'd like to announce [easystroke]("http://easystroke.sourceforge.net"), a new gesture recognition application for linux.  

I just found out about easystroke. It is awesome. Thanks!

---

### Post by MountainX on 2010-07-06
Now that I'm addicted to using easystroke with my mouse, I'm thinking about trying it with a tabet. What would be the best gesture-input tablet for Linux? The first one I found was the Wacom Bamboo Pen and Touch. But I appreciate any recommendations.

---

### Post by schmolch on 2010-08-07
- deleted bugreport since its apparently some weird **** with the language/layout settings -

---

### Post by hariks0 on 2010-11-03
Hi Tom,

It is a really great application I have come across in Linux. It has made my life a lot simpler. I amaze my friends who use windows with its multiple actions. When I draw an 'O' to open/close the CD tray [with *eject -t *command], they simply gets flabbergasted. [Of course such a gadget is now available for windows also]. The possibilities of this super application is limitless.

However, there are two suggestions from my part though. What about a Master Gesture Option to enable/disable Easystroke? Once disabled, Easystroke will listen only to the Master stroke to enable. It will help us to use Mouse Button1 as usual and for Easystoke also at the same time. Now I have set a gesture to disable easystroke. But I have to right click the icon and deselect 'Disabled' to enable it again.

The second suggestion is to have an option for Profiles/Backup of gestures.

Thanks and hearty appreciation on a job well done !

:guitar::popcorn:

---

### Post by ubername on 2011-04-18
Hi
I am trying to use easystroke in Natty and it seems not to recognise the 'release' part of clicks (it works fine on my older installs - I love it!). For example, when trying to record the gestures, I click the button, draw the shape and release the button but it carries on recording the shape until I click again. Actually, it's not quite that simple - I cant explain it but it is similar to that. The side effect is that it messes with that button's use when not trying to draw gestures (i.e. in normal usage) as I need to click twice if easystroke is enabled.

Sorry this is a bit rambling - hopefully someone else will have the same experience and be able to explain the behaviour better.

---

### Post by chriskin on 2011-04-18
> **ubername said:**
> Hi
I am trying to use easystroke in Natty and it seems not to recognise the 'release' part of clicks (it works fine on my older installs - I love it!). For example, when trying to record the gestures, I click the button, draw the shape and release the button but it carries on recording the shape until I click again. Actually, it's not quite that simple - I cant explain it but it is similar to that. The side effect is that it messes with that button's use when not trying to draw gestures (i.e. in normal usage) as I need to click twice if easystroke is enabled.

Sorry this is a bit rambling - hopefully someone else will have the same experience and be able to explain the behaviour better.


it started happening to me as well.
to be exact, it started happening after my daily update last monday (or some day really close to it)


i think i took some screenshots of the packages i updated the day it started happening - i can't seem to find them though. if/when i do,i will edit this post


edit : here you go, hope it helps
[http://dl.dropbox.com/u/452182/New%20folder/Screenshot.png](http://dl.dropbox.com/u/452182/New%20folder/Screenshot.png)
[http://dl.dropbox.com/u/452182/New%20folder/Screenshot-1.png](http://dl.dropbox.com/u/452182/New%20folder/Screenshot-1.png)
[http://dl.dropbox.com/u/452182/New%20folder/Screenshot-2.png](http://dl.dropbox.com/u/452182/New%20folder/Screenshot-2.png)
[http://dl.dropbox.com/u/452182/New%20folder/Screenshot-3.png](http://dl.dropbox.com/u/452182/New%20folder/Screenshot-3.png)


by the way, it seems that easystroke chose to remove itself from autostart as well
not that it's difficult to put it there again - i just mention it because it's a little strange

---

### Post by Luffield on 2011-04-19
On natty in a virtualbox machine, I can't even record a stroke :(

---

### Post by ubername on 2011-04-28
Well I have managed to get it working in a very convoluted way

I downloaded an RPM from

```
http://kojipkgs.fedoraproject.org/packages/easystroke/0.5.4/1.fc14/src/easystroke-0.5.4-1.fc14.src.rpm
```


Then unpacked the tar file in that

then did

```
sudo apt-get build-dep easystroke
```

then cd to where I unpacked the tar file then 

```
make
```

(I guess I could do a 'make install' but it's good enough for me at the moment)

---

### Post by chriskin on 2011-04-28
150mb of additional space - that hurt
can you build a .deb of that please?


EDIT : latest update on 11.04 makes easystroke work perfectly again
Good work :D

---

### Post by pibach on 2011-07-31
> **MountainX said:**
> Now that I'm addicted to using easystroke with my mouse, I'm thinking about trying it with a tabet. What would be the best gesture-input tablet for Linux? The first one I found was the Wacom Bamboo Pen and Touch. But I appreciate any recommendations.

Best device? Probably a Galaxy Tab 10.1 with a native Linux4Tegra install?

---

### Post by MountainX on 2011-07-31
>  by Mountain X: Now that I'm addicted to using easystroke with my mouse, I'm thinking  about trying it with a tabet. What would be the best gesture-input  tablet for Linux? The first one I found was the Wacom Bamboo Pen and  Touch. But I appreciate any recommendations.
> **pibach said:**
> Best device? Probably a Galaxy Tab 10.1 with a native Linux4Tegra install?

When I wrote that I was referring to a traditional digitizing tablet for input to the desktop PC. After the iPad, the word "tablet" means something else now.

I'm not sure how I would use a Galaxy Tab 10.1 as an input device for my PC. Maybe it could be done... if someone developed software for that, maybe it would even take digitizing tablet input to a new level... but I'm sure that any current solution would be far inferior to what I want. 

I want something for Linux like the Apple Magic Trackpad with gesture recognition that works as well as the Magic Trackpad and Better Touch Tool on a Mac.

---

### Post by pibach on 2011-07-31
The MagicTouchpad drivers for Linux are not what are looking for?
 [http://www.youtube.com/watch?v=1Ek4QaFQ1qo](http://www.youtube.com/watch?v=1Ek4QaFQ1qo)

Easystroke does not handle multitouch, unfortunately.

I think ubuntu is going this direction:
 [https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

---

### Post by MountainX on 2011-07-31
> **pibach said:**
> The MagicTouchpad drivers for Linux are not what are looking for?
 [http://www.youtube.com/watch?v=1Ek4QaFQ1qo](http://www.youtube.com/watch?v=1Ek4QaFQ1qo)

Easystroke does not handle multitouch, unfortunately.

I think ubuntu is going this direction:
 [https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

I tried Touchégg many months ago and it sucked so bad I stopped using my Magic Trackpad with Linux. But the video looks pretty good. I think I'll try it again now. Thanks.

---

### Post by MountainX on 2011-07-31
> **pibach said:**
> 
I think ubuntu is going this direction:
 [https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

I tried that too when 10.10 first came out and it really sucked. I gave up after a lot of effort to get it to work well. It almost sent me back to the iMac for good.

---

### Post by ninjaaron on 2011-07-31
I installed this today on my Dell Inspiron Duo.  It's perfect, since multitouch is broken on this hardware in Linux.  I plugged strait into a library of scripts and compiz settings that I created for managing tablet-related actions on the duo.  Easystroke starts in the background in tablet-mode, and so far I have gestures to close, minimise, and fullscreen windows, activate the unity "love handles," show all windows, call the virtual keyboard, rotate the display clockwise or counter-clockwise, and invoke the scroll-wheel.

Easy was the final missing piece to my home-brewed touch UI.  Thanks so much!!

---

### Post by pibach on 2011-07-31
> **MountainX said:**
> I tried that too when 10.10 first came out and it really sucked. I gave up after a lot of effort to get it to work well. It almost sent me back to the iMac for good.

Yeah, still under development, but should work in Natty: [https://wiki.ubuntu.com/Multitouch/GettingStarted/Natty](https://wiki.ubuntu.com/Multitouch/GettingStarted/Natty)
All the Tegra/Oak Trail/Meego tablets will give this some spin, I would expect. We'll see...

---

### Post by pibach on 2011-08-03
@Tom: what are your plans / thoughts regarding integration of easystroke and moultitouch/touchegg in Ubuntu? Does it run well on a dual input tablet PC, such as Fujitsu Q550 with capacitive touch and digitiser stylus? Such that multitouch finger input is processed by touchegg and stylus input (or single finger) is processed by easystroke. Is this possible?

---

### Post by realn on 2011-08-11
Please, keep up the great work. Easystroke is my no. 1 app now. It is so much better than any other similar app - it is really customizable and it recognizes EVERYTHING, even handwriting. That's what I expect from an application like this, and not 3 fingers swiping, 10 fingers pinching and all that nonsense. 
Please, keep it going.
Thanks a lot for your app 
Your most faithful user.

---

### Post by ninjaaron on 2011-08-11
> **realn said:**
> Please, keep up the great work. Easystroke is my no. 1 app now. It is so much better than any other similar app - it is really customizable and it recognizes EVERYTHING, even handwriting. That's what I expect from an application like this, and not 3 fingers swiping, 10 fingers pinching and all that nonsense. 
Please, keep it going.
Thanks a lot for your app 
Your most faithful user.

Yeah right.  I'm his most faithful user. :p

---

### Post by nsk7even on 2011-08-12
Oh no - it's me! :lolflag:

---

### Post by realn on 2011-08-12
Well, let's see - I have 48 gestures defined and I use all of them: starting from putting the PC into hibernation, getting the volume/brightness up/down, docking windows into the dock bar (see kdocker), waking-on-lan my server  ... only your imagination is the limit. I don't understand why easystroke is not advertised on the streets, or smth.
Oh ... did I forget to mention close/minimize/maximize window, increase/decrease fonts ? No, I didn't, these go without saying ...
Again ... huge fan ... huge

---

### Post by ninjaaron on 2011-08-12
> **realn said:**
> Well, let's see - I have 48 gestures defined and I use all of them: starting from putting the PC into hibernation, getting the volume/brightness up/down, docking windows into the dock bar (see kdocker), waking-on-lan my server  ... only your imagination is the limit. I don't understand why easystroke is not advertised on the streets, or smth.
Oh ... did I forget to mention close/minimize/maximize window, increase/decrease fonts ? No, I didn't, these go without saying ...
Again ... huge fan ... huge

awe snap. I only have 39 gestures, but give me time, I discovered it like a week ago... but I do have it calling user scripts for screen rotation, activation of the virtual keyboard, also adjusting brightness, etc...

and yes, zooming and window controls are a given.:P

---

### Post by nsk7even on 2011-08-29
Hi guys,

my SSD crashed so I did fresh install of Natty (prior: Maverick) and now I don't see my lovely fire anymore.

Enabled and tested the fire within ccsm which is working.

Easystroke works as normal, but the fire is invisible - just as if I wouldn't have enabled the fire plugin ... any ideas?

Maybe the fire plugin was internally renamed? Because it is not localized anymore (I am not sure, but I think it was prior).

Can s. o. on a lucid box check the name please: ccsm => settings => plugin list => active plugins => firepaint

---

### Post by Enterpart on 2011-08-30
for those of you that have mouse button 1 as your gesture button and want to use it without triggering easystroke heres the solution


go on "Advanced" tab on easystroke and tick "timeout gestures" now if you wanted to use click 1 conventially, just wait a half a second after clicking. This is because if no stroke is made after an intial second it bypasses easystroke. You get used to it and it becomes the norm after a while.

tell me if it works? enjoy

P.s I have lots of nice scripts I'm willing to share if anyone is interested and I have over 150 gestures. I can use a script that after highlighting and performing a gesture the it opens that search term in any website of my choosing like scrybe.

---

### Post by realn on 2011-08-31
Enterpart, you're the dude. I'm interested in your scripts, I can share mine, too. A good part of them are linked though to keyboard shortcuts that trigger scripts from within the xbindkeys app.

---

### Post by nsk7even on 2011-08-31
Ich hab den Bug zu meinem Problem (Feuer tut nicht) gefunden:
[http://sourceforge.net/apps/trac/easystroke/ticket/93](http://sourceforge.net/apps/trac/easystroke/ticket/93)

Oh sorry, its english here: I found the corresponding bug to my problem (fire gesture does not work in natty) (see above)

---

### Post by Enterpart on 2011-09-01
I've got one more tip if your searching on a website with with several other tabs open and use a gesture with this code it will open a new tab at the end (in chrome) and after closing that tab your stuck at the tab at the far right and have to look through to find the one your at

the way around is insert the code
--new-window after google-chrome this will open in a new window

e.g

```
google-chrome --new-window "http://www.youtube.com/results?search_query=`xsel -p | tr [:space:] +`&aq=f"
```

Realn Ive got a script that imitates pinch to zoom if your interested, just ask :p what did you think of that last one?

---

### Post by wxuyec on 2012-03-26
I am using ubuntu10.04, and I just installed the easystroke.
but  why can I not add actions? when I press the button of
add actions and specify what commands will be executed,
and then I want to record the gesture, it does not work.
no matter how I move my mouse, the gesture can't be recorded.

---

### Post by MountainX on 2012-03-26
> **wxuyec said:**
> I am using ubuntu10.04, and I just installed the easystroke.
but  why can I not add actions? when I press the button of
add actions and specify what commands will be executed,
and then I want to record the gesture, it does not work.
no matter how I move my mouse, the gesture can't be recorded.

I haven't used it in a while. (I plan to start using it again soon.) But I remember when I first tried it, I had that same issue. It just takes playing around with it and following the instructions ***very*** carefully.

---

### Post by nsk7even on 2012-03-26
check the setting for the mouse button that is activated for gestures
additionally check the devices that are recognised as usable easystroke devices

---

### Post by wxuyec on 2012-03-27
thanks. I uninstall the easystroke installed from the software center and reinstall it from synaptic. now it works. I don't know why.

---

### Post by Nightmist on 2012-07-21
> **nsk7even said:**
> Ich hab den Bug zu meinem Problem (Feuer tut nicht) gefunden:
[http://sourceforge.net/apps/trac/easystroke/ticket/93](http://sourceforge.net/apps/trac/easystroke/ticket/93)

Oh sorry, its english here: I found the corresponding bug to my problem (fire gesture does not work in natty) (see above)

I really want water/fire for my gestures. I am using Pangolin, and it's not working here either (I have fire/water enabled and working with compiz). I read the information in the link, and it seems the guy made it work... but I couldn't really understand what he did... Did you make it work? Is there an easy way to fix it?

---

### Post by nsk7even on 2012-07-21
Yes it is working for me on precise!

You need:
- Compiz fire plugin enabled
- Compiz dbus plugin enabled
- Easystroke 0.5.5.x (because this fixes communication with compiz)

Check the easystroke ppa and install the most recent version and you should be able to use id!

---

### Post by Nightmist on 2012-07-23
> **nsk7even said:**
> Yes it is working for me on precise!

You need:
- Compiz fire plugin enabled
- Compiz dbus plugin enabled
- Easystroke 0.5.5.x (because this fixes communication with compiz)

Check the easystroke ppa and install the most recent version and you should be able to use id!

That did it! Thanks alot!
I hadn't enabled dbus, and adding the ppa updated easystroke.

EDIT1: If I have any complains, it's that the fire plug-in makes the rest of the screen darker. Kind of annoying if you use gestures alot (which I do). Or maybe I can adjust that somehow? Also, the water plug-in ripples too much to be useful :/

EDIT2: You can adjust it! Now everything is just dandy!

---

### Post by nsk7even on 2013-03-12
Hey guys, I just ran into a problem:
When configuring an exception within Easystroke this works for normal windows/applications, but not for my ut2004 when it is run in fullscreen mode.
It does exclude the game when running it in windowed mode, but after switching to fullscreen the exception rule gets confused somehow.

This may work for others, as I have two monitors and when switching to fullscreen, the X server metamode is changed to a single monitor mode automatically. Therefore I tested with manually activating the single monitor metamode prior to switching to fullscreen, which did not worked either. But I don't know what is going on in the background... and I don't know if those metamodes makes a difference at all :D

If there is another Easystroke user around playing egoshooters or other games in fullscreen mode, is it working over there?

---

