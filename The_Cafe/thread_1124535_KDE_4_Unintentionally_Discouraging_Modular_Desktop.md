---
title: "KDE 4 Unintentionally Discouraging Modular Desktop?"
date: 2009-04-13
forum: The Cafe
---

### Post by NightwishFan on 2009-04-13
KDE4.. It is introducing some new concepts, ones designed to update the old desktop metaphor, and ones to make development easier and more rapid. It this entirely a good thing though?

For example. If you install a full featured KDE system, you would probably want to include KWIN. With the new KWIN effects, it is making Compiz sort of obsolete. Not in entirety, but to use compiz on KDE when you have KWIN is sort of like "doubling up" features. There is no real downside to that, but it seem like it would have been better suited to perhaps include compiz KDE integration, rather than their own effects. Using Compiz, when you have a integrated, better supported compositor seems pointless.

This is not really a bad thing, as Linux is about choice, however this trend continues with a few parts of KDE. Consider, Strigi, which is integrated with KDE Control, and Krunner. Or powerdevil, which is integrated as well. Working toward relying on these features is possibly encouraging a slight dependence on them in a desktop, to a small degree.

I am merely wondering if in the future KDE will work to support alternatives. This is not meant to spark an argument either, so please be civil, I do not want a riot on my hands. This is merely my observation as of KDE 4.1.

---

### Post by swoll1980 on 2009-04-13
I think the integrated effects is a good idea, though it has a way to go to catch up with compiz in a year or so it should be great.. Compiz is more of a patch to add 3d effects to a DE that didn't have any, and I don't think it ever was going to be the defacto standard in Linux accelerated desktops.

---

### Post by SunnyRabbiera on 2009-04-13
Well compiz never quite worked that well with KDE anyhow, the Kwin effects is a good substitute and it seems to run better for me at least then Compiz.
But compiz is more versatile

---

### Post by Firestem4 on 2009-04-13
I personally enjoy the integration because it works well. Not that I have anything against compiz, or pro KWin. It works very well with KDE.

The way I see. Its not KDE's responsibility to make Compiz friendly with KDE. That is the Compiz COmmunity's job.

However I do agree that being able to integrate alternatives as well as current software that comes with KDE (Ie: Power devil) Would be nice. But that is also up to the developer of that software.

---

### Post by NightwishFan on 2009-04-13
True. It seems to me that GNOME is more "modular" and is intended to be used with multiple applications such as tracker or beagle (or both). This is what I mean. KDE seems to want to depend on Strigi, and adding Tracker would simply mean less integration. On the other hand, it means more advanced features will become available for KDE applications with the improved rate of development.

---

### Post by namegame on 2009-04-13
Somewhat offtopic, but still related...

The guys over at the KDEmod/Chakra project have been working on making KDE more modularized. However, this is Arch based. I'm not sure if a similar project exists for Ubuntu or any other distribution for that matter.

---

### Post by happysmileman on 2009-04-13
> **NightwishFan said:**
> KDE4.. It is introducing some new concepts, ones designed to update the old desktop metaphor, and ones to make development easier and more rapid. It this entirely a good thing though?
Yes, nothing you've described in this paragraph is a bad thing.

> For example. If you install a full featured KDE system, you would probably want to include KWIN. With the new KWIN effects, it is making Compiz sort of obsolete. Not in entirety, but to use compiz on KDE when you have KWIN is sort of like "doubling up" features. There is no real downside to that, but it seem like it would have been better suited to perhaps include compiz KDE integration, rather than their own effects. Using Compiz, when you have a integrated, better supported compositor seems pointless.
I don't see how it can be considered bad in any way that KWin has extra (optional) features.
There was a lot of talk about Compiz integration, it was chosen that KWin should get the features, instead of integrating Compiz, for a few reasons.
For one, it would be very hard to integrate Compiz or it's plugins into KDE/KWin, as someone who used to use Compiz on KDE3.5, I can verify that the "Compiz integration" was nothing more than a bunch of buggy hacks.
Secondly, there are features in KWin that aren't in Compiz, integrating Compiz would mean throwing away these features, with no guarantee that they'd be available in Compiz any time soon.

Also if a user wants to use Compiz instead of KWin he still has that choice, it may be "pointless" as you say, but are you suggesting that the KDE developers should have chosen not to improve KWin as much just because now it's competitive with Compiz?

> This is not really a bad thing, as Linux is about choice, however this trend continues with a few parts of KDE. Consider, Strigi, which is integrated with KDE Control, and Krunner. Or powerdevil, which is integrated as well. Working toward relying on these features is possibly encouraging a slight dependence on them in a desktop, to a small degree.
Gnome has equivalents for all these things, does it not?
Does anyone complain that Gnome is making people dependent on it, by providing useful features?

> I am merely wondering if in the future KDE will work to support alternatives. This is not meant to spark an argument either, so please be civil, I do not want a riot on my hands. This is merely my observation as of KDE 4.1.
You can replace KWin already, with no hassle, in basically the exact same way you would do it for any other Window Manager, and there is nothing to stop you.
I don't know enough about the others to say so, but there are equivalents of these in Gnome as well as far as I know.

---

### Post by NightwishFan on 2009-04-13
I am not attacking the projects! :lolflag: It just seems that Linux in general, especially KDE are becoming less dependent on cooperation. It is not a bad thing, merely a change. I just wanted some opinions is all, and you gave yours. In a point-by-point why you are wrong form, I suppose, but thanks for your two cents anyway.

---

### Post by Mehall on 2009-04-13
Can I just point out one of the things a lot of people say they like about Windows is the overall integration of it all.

I think the option of KDE is a good one, and if you don't like it that way, you want modularity, use Gnome, or don't use an actual DE, and just use a WM and a panel of choice, and add bits that you want to make it FULLY modular if you want.

I think it's good KDE is giving users this choice.

---

### Post by geoken on 2009-04-13
> **NightwishFan said:**
> 

I am merely wondering if in the future KDE will work to support alternatives. This is not meant to spark an argument either, so please be civil, I do not want a riot on my hands. This is merely my observation as of KDE 4.1.

Why should they work to support alternatives? They have created API's that alternatives can use, why should they divert their limited development time to "redundancy for the sake of choice"?

Also, when you try and modularize things too much you introduce bloat because every modular piece must have extra code to facilitate it's integration into other modular parts. Removing a component from an app, then giving it an API so the initial app can still 'talk' to it isn't a win-win situation.

---

### Post by NightwishFan on 2009-04-13
Thank you for you responses. For now I will be offline, so if you want, please discuss among yourselves if you will, and please no arguments. I will be back perhaps tomorrow and I will throw my 2 cents in the pond. :KS

My question I leave for someone to answer if they can:

Is KDE really as "one size fit all" as it appears to be or is it more modular than I think??

> 
Why should they work to support alternatives? They have created API's that alternatives can use, why should they divert their limited development time to "redundancy for the sake of choice"?

Also, when you try and modularize things too much you introduce bloat because every modular piece must have extra code to facilitate it's integration into other modular parts. Removing a component from an app, then giving it an API so the initial app can still 'talk' to it isn't a win-win situation.

Not necessarily. For example, Windows Vista has the new search tool, which is integrated with the start menu. Many people complain about this nice feature because it is "being shoved down their throats".

Perhaps so. However with some development the search box can be used with any back-end a third party developer chooses to write. Creating the framework for features and let the people do the rest. I happen to agree with both.

Many people do not care what back-end or tool they use, just the one in front of them is fine. That attitude is perhaps a bit bad for the future, and all the users become dependent on that one source.

---

### Post by happysmileman on 2009-04-13
> **NightwishFan said:**
> Thank you for you responses. For now I will be offline, so if you want, please discuss among yourselves if you will, and please no arguments. I will be back perhaps tomorrow and I will throw my 2 cents in the pond. :KS

My question I leave for someone to answer if they can:

Is KDE really as "one size fit all" as it appears to be or is it more modular than I think??

As poster above you says, they provide APIs for alternatives, whethe ror not they're used much is irrelevant to them.

One major example of flexibility of KDE4 is plasma (the desktop), as well as running "plasmoids", the widgets created for it, it can also run SuperKaramba widgets, Mac OS X widgets and Google Gadgets. Something which, as far as I know, can't be done by any other single program.

In addition to this, it handles the panels, menus, task manager, system tray and desktop background, all of which (Maybe not the panel, not sure) are treated just like plasmoids and can be replaced just as easily.
If you dislike the defaults, you can replace the menu, task manager and system tray just as easily as you can place widgets on the desktop (Indeed, Lancelot, a third party applications menu, has always been incredibly popular as an alternative to the official menu.)

Another, less overwhelming but still valid, example is Phonon, it's an API for playing media (Which, I'll add, from a developers point of view, is incredibly easy to work with), it allows you to choose the backend for playing media (Or choose more than one, and give an order of preference).

This means that a player that uses the Phonon libraries will work with either Xine or GStreamer, depending on the users preference, instead of the current trend of the programmer having to choose between the two, and forcing users to have them installed.
It also adds reliability, in that if a user has both Xine and GStreamer installed, and chooses to use Xine for playing media, it will use Xine for all his media playing applications. But if Xine isn't able to play a certain format, it will play that format with GStreamer, instead of the user having to use a different player or install extra codecs.

---

### Post by Methuselah on 2009-04-13
The problem the linux desktop is facing in trying to compete with the proprietary offerings is that modularity is often inimical to seemlessness.
It is a much more complex engineering task to build a system where the parts must fit together tightly but each part has to assume that any other part may be missing.
And the more joins there are, the more difficult it is to conceal them.
With the desktop being the centre of the average user's interaction with the computer, the big two DEs seem to be getting more monolithic.

It probably can't be helped.
A desktop environment seems, by nature, monolithic.
So if you opt for a DE, maybe it should be assumed that you're getting something that will toast and butter your bread.
However, one could still opt to install a window manager, a panel, a file manager and assemble something in a modular fashion.

So in a sense, I don't think we are losing the modular desktop; that is still a possibility for the power user.
But it is becoming more and more clear that the big 'Desktop Environments' are NOT modular desktops where pieces are easily interchanged.
Probably a cobbled together GNOME/KDE was always a stop-gap until they matured.

---

### Post by geoken on 2009-04-13
> **NightwishFan said:**
> 

Many people do not care what back-end or tool they use, just the one in front of them is fine. That attitude is perhaps a bit bad for the future, and all the users become dependent on that one source.

Why is it bad? I could understand if your talking about depending on some proprietary app that might lock in your data, but if your talking about FOSS I don't understand what the problem is. You're basically saying that a near perfect app, or at least an app that fulfills the needs of almost all users, is bad because there is no motivation to create an alternative.

---

### Post by NightwishFan on 2009-04-14
Thank you for the replies. I did not know that plasma could run Google gadgets, that is interesting.

Yes, the fact that OSS desktops are competing with proprietary ones was the train of thought I was looking for.

Also, I am saying that if we relied on one "near perfect" application, the lack of useful alternative would essentially be a lack of freedom. However, open source software should not allow such a thing to occur.

My doubts have been satisfied with a little research. KDE satisfies my requirements as they do create a framework for development to improve. I was mainly curious is all.

---

