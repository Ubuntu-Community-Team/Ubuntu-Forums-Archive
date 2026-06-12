---
title: "Minimising windows."
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by HDave on 2012-03-09
> **VinDSL said:**
> Heh!  The hills are alive, with the sound of music!

I *think* ppl are finally cottoning up to Unity...  :)

I know 198 more people that would be if Ubuntu would let us [minimize a window by clicking on its launcher icon]("https://bugs.launchpad.net/ayatana-design/+bug/733349").

---

### Post by cariboo on 2012-03-09
> **HDave said:**
> I know 198 more people that would be if Ubuntu would let us [minimize a window by clicking on its launcher icon]("https://bugs.launchpad.net/ayatana-design/+bug/733349").

If you or any of your 198 freinds could come up with a patch, I'm sure that it would be considered closely. Look at [this]("http://ubuntuforums.org/showthread.php?t=1937199") thread, then check out the [unity-design]("https://launchpad.net/~unity-design") mailing list, to see what I mean.

---

### Post by VinDSL on 2012-03-09
Heh!  Let's see...

[LIST]
[*]Left mouse button to open first instance
[*]Center wheel to open new instance(s)
[*]Right mouse button for quicklist
[/LIST]

Personally, I don't use the quicklist feature.  Do you?!?!?

I occasionally try the quicklist to "Quit" an app, but it seldom works.

I would nick the quicklist feature and make the right button a minimizer (or add minimize to the list).

This isn't a condemnation!  Just saying...  ;)

---

### Post by HDave on 2012-03-09
> **cariboo907 said:**
> If you or any of your 198 freinds could come up with a patch, I'm sure that it would be considered closely. Look at [this]("http://ubuntuforums.org/showthread.php?t=1937199") thread, then check out the [unity-design]("https://launchpad.net/~unity-design") mailing list, to see what I mean.

If you had read the comments on the launchpad link I provided (I know there are a lot of them...) you would have seen that someone did provide a working patch...and it was rejected, not because it didn't work, but because  Mark (comment #19) says there is already a way to minimize windows.  So there you have it -- the community wants and expects the launcher to work like every other operating system (and every other Ubuntu launcher) and yet all we get is "Won't Fix".  

We need to get this issue reopened and addressed so that we can get Unity to garner widespread acceptance of both new and existing users.

---

### Post by philinux on 2012-03-09
Posts split off to own thread.

---

### Post by keithpeter on 2012-03-09
> **HDave said:**
> ...because  Mark (comment #19) says there is already a way to minimize windows.

Hello HDave and all

Interesting. Did Canonical do 'first hour user' testing of several alternatives and decide that the current methods for minimising windows are best?

Or is Mr Shuttleworth becoming less scientific?

Back to plumbing now (on topic for this sub-forum), I'm doing a reinstall from the beta to test the installer and see what the nouveau drivers can do on this hardware.

---

### Post by cariboo on 2012-03-09
@HDave, how about getting together with the creator of the patch, and creating a ppa with the patched Unity version, fo those that want that particular function.

@VinDSL, I use quicklists fairly often, the one I use the most, is one I picked up from [askubuntu]("http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available") , called ssh-launcher, it allows me to access my server via ssh with just a couple of clicks. See the screenshot

---

### Post by t1497f35 on 2012-03-09
> **cariboo907 said:**
> @HDave, how about getting together with the creator of the patch, and creating a ppa with the patched Unity version, fo those that want that particular function.


You forgot to tell them to also compile their own drivers and to write a new kernel.

Minimize on click is a must have, no matter what tests have or have not been done. No need to be defensive on some of Canonical's wacky decisions.

---

### Post by mc4man on 2012-03-09
> **VinDSL said:**
> 

I would nick the quicklist feature and make the right button a minimizer (or add minimize to the list).

This isn't a condemnation!  Just saying...  ;)
That's one thing that will never happen, quicklists as seen now & what may arise are what sets unity's launcher apart. 
Here, rather than use individual icons for everything, I group them in categories.
 So for instance "Utilities" contains 10 apps or scripts. better  than 10 icons for my use & display

What may arise down the road, either officially or not, who knows, there are many possibilities. 
For instance in screen is an example of a 'dynamic window list', accessed thru the quicklist window.

In this case have 5 FF windows open on various Ws's, they are then shown & accessible thru the quicklist
(whether something like this ever comes about don't know, was more of an Ex. of what could be done to provide window lists

---

### Post by x-shaney-x on 2012-03-09
I am also used to clicking on icons to minimize in both Windows and KDE but I just don't miss it in unity.
I don't know why but I don't even try minimizing via the launcher, I just automatically use the window buttons.
Maybe it is because they are on the left and generally closer to the launcher anyway I dunno.

In any case, trying to reason with Mark on this (or any other) issue on the mailing lists seems pointless to me.
On one subject he says changes have to be made because it will be confusing to users who have only ever experienced mac and windows, but on other subjects he insists on changing things AWAY from what people would be used to on windows or mac.  Pointless.

---

### Post by tekstr1der on 2012-03-09
> **cariboo907 said:**
> ...how about getting together with the creator of the patch, and creating a ppa with the patched Unity version, fo those that want that particular function...

Last word from the patch author was that he was not willing to maintain a separate branch of unity. That branch would be a lot to maintain given the frequency of changes.

I had applied his patch and built against that (Natty) version of Unity and it worked perfectly, solving one of the biggest usability issues in Unity. The sum total of user-facing changes resulting from the patch added a single option to CCSM. Problem solved with all common use-cases are covered. Unfortunately the prevailing closed minds (WON'T FIX) and deaf ears of the development team leave a lot to be desired.

---

### Post by cariboo on 2012-03-09
> **t1497f35 said:**
> You forgot to tell them to also compile their own drivers and to write a new kernel.

Minimize on click is a must have, no matter what tests have or have not been done. No need to be defensive on some of Canonical's wacky decisions.

Minimize on icon click only works for those that don't have the Launcher hidden, for those who use a hidden launcher, it is far quicker to click the minimize button in the application tile bar, instead of unhiding the launcher, then clicking the icon.

I wasn't being defensive or dismissive, HDave said there was a patch to make the function work, to test it you have to compile Unity from source, if they've done that already, it's just a short step to creating a ppa, and making the patched version available to those who want it. 

What does creating drivers and a kernel have to do with it?

---

### Post by HDave on 2012-03-09
> **cariboo907 said:**
> @HDave, how about getting together with the creator of the patch, and creating a ppa with the patched Unity version, fo those that want that particular function.

A reasonable question, but I just don't have the skill set.  I'm just a user-type person...I've gotten many friends and family to run with Ubuntu and am just trying to get the system to be the best it can be...without getting inundated by questions like "How come my windows don't minimize anymore".   Yes, perhaps I have idiots for friends ;-) and perhaps I am an idiot too....I just want to minimize windows like I did in Windows, KDE, Gnome 2, Ubuntu AWN, Ubuntu Cairo, Mac, etc.

---

### Post by snkiz on 2012-03-09
This is one I actually agree with Canonical about. The launcher doesn't manage "windows" it manages applications. If you have multiple windows open for an app and expect the single launcher icon to minimize a window, witch one does it minimize? Having it minimize if only a single window is open could work, however that would mean you have a totally different function in the event of multiple windows. "New" users don't understand dodge, we can't possibly expect them to grasp that idea.

---

### Post by t1497f35 on 2012-03-10
> **snkiz said:**
> This is one I actually agree with Canonical about. The launcher doesn't manage "windows" it manages applications. If you have multiple windows open for an app and expect the single launcher icon to minimize a window, witch one does it minimize?
This question has been answered a long time ago, just look at window$, it's there for a few years already.

@cariboo the question is sarcasm for the need to bend over backwards to get in obvious features. You and I know Unity was put in as a half-backed solution (even a Unity dev acknowledged it) and now is time to make it better than the alternatives and one should acknowledge obvious features which need to be in, not suggest supplying patches and creating PPAs. This type of features should have been taken care of right at the beginning, it's not rocket science, really.

---

### Post by snkiz on 2012-03-10
> **t1497f35 said:**
> This question has been answered a long time ago, just look at window$, it's there for a few years already.

Last I looked at windows their taskbar still was window based not application based, I don't see the relevance.

---

### Post by t1497f35 on 2012-03-10
> **snkiz said:**
> Last I looked at windows their taskbar still was window based not application based, I don't see the relevance.
Both win7 and Unity can and do manage windows, regardless if they're win or app based. Two cases:

Win7: 2 open apps under same icon: clicking on the icon window$ shows  both of them to choose from.
Unity: 2 open apps under same icon: click on the icon you get one of them, clicking again, both to choose from.

So far so good. However:

Win7: 1 open app: clicking on its icon you minimize it if it was in front of you, or, it gets in front of you if it wasn't.
Unity: 1 open app: clicking on its icon does nothing if it's already in front of you. Can't you see that this last bit is missing? Again, being app or window based doesn't matter.

---

### Post by snkiz on 2012-03-10
IMO bad design. the left click is changing functions. Besides like I said if dodge is too hard, that's friggin imposible

---

### Post by t1497f35 on 2012-03-10
> **snkiz said:**
> IMO bad design. the left click is changing functions. Besides like I said if dodge is too hard, that's friggin imposible
Bad design? On whose part? If you're talking about win7 - I disagree here, since hundreds of millions of people are using it and I haven't read anywhere anyone complaining about this particular feature, it's logical and handy.

And remember, usability is more important than design or theory, since the very existence of design and theory are there to create good usability, if something is useful from a usability point of view but can't be done because of the overall design - common sense implies that the design must be changed accordingly. Unfortunately I noticed that some folks don't understand/agree on that.

---

### Post by snkiz on 2012-03-10
> **t1497f35 said:**
> Bad design? On whose part? If you're talking about win7 - I disagree here, since hundreds of millions of people are using it and I haven't read anywhere anyone complaining about this particular feature, it's logical and handy.

So was dodge. Now I measure unity by the dictators standards.

Really, it wouldn't be that hard to figure out, but hell they can barely code what they have so what can you do?

---

### Post by x-shaney-x on 2012-03-10
@ t1497f35

Many millions of people are using Windows but not all are using it by choice. Many HAVE to get used to the way Windows does things.


@ snkiz

Dodge is one of the things I was referring to several posts ago.
Mark reasons that dodge is confusing because it's not what users expect to happen and it confuses them.
Yet he is ignoring pleas regarding minimizing from the launcher which IS what people are expecting to happen.

Though I think it's best to focus on each problem as an individual thing rather than comparing issues are it gets even more frustrating :)

---

### Post by t1497f35 on 2012-03-10
> **snkiz said:**
> So was dodge. Now I measure unity by the dictators standards.

Really, it wouldn't be that hard to figure out, but hell they can barely code what they have so what can you do?
Yep, I agree that the forces who are in charge to take critical decisions about Unity are too restrictive and bureaucratic. Dodge should have stayed as an option since it wasn't buggy, people found it useful and since Linux is generally about (much) more choice than window$.

---

### Post by t1497f35 on 2012-03-10
> **x-shaney-x said:**
> @ t1497f35

Many millions of people are using Windows but not all are using it by choice. Many HAVE to get used to the way Windows does things.


True, but this doesn't apply to minimizing the window by clicking its icon - which is what I mean - hundreds of millions of people are doing so and few to no one complaining about it. And lets be honest - I don't have to bring up such examples, common sense is enough to figure this out.

---

### Post by snkiz on 2012-03-10
> **x-shaney-x said:**
> @ t1497f35

Many millions of people are using Windows but not all are using it by choice. Many HAVE to get used to the way Windows does things.


@ snkiz

Dodge is one of the things I was referring to several posts ago.
Mark reasons that dodge is confusing because it's not what users expect to happen and it confuses them.
Yet he is ignoring pleas regarding minimizing from the launcher which IS what people are expecting to happen.

Though I think it's best to focus on each problem as an individual thing rather than comparing issues are it gets even more frustrating :)

No, it speaks to his character and his real view of the Ubuntu community. This things are systemic, and when you take them as a whole you begin to see the problem.

---

