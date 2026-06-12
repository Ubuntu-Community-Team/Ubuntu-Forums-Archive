---
title: "A graphic design deficiency"
date: 2013-06-30
forum: Ubuntu, Linux and OS Chat
---

### Post by r_avital on 2013-06-30
I'm sure every one is familiar w119ith the LTS release schedule, but some time ago, I looked it up, and found this useful graphic here:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

The graphic says it all, in more ways than one.  First, it gives you a very quick and very clear idea of what to expect from standard releases, in terms of support, vs. LTS releases.

Looking closer, I found that the legend of the graph had three items, all in very close and practically indistiguishable shades of deep purple.  I don't want to post the full image here, you can see it in the link above, but I'll post just the part showing the legend.

Are they @#%$^ing me???  A human being with healthy eyes and no color-blindness is supposed to be able to look at the graph and at the legend and be able to tell which is which?  I'm looking at a high-quality ViewSonic monitor on a good, fairly recent nVidia card.  I can make out the difference between two of the three, and even that is a strain.

For yuhts, I saved the image and opened it in GIMP, just to use the color-picker to see the differences:

Ubutu Desktop LTS - RGB values are R-119 G-33 B-111
Ubuntu Server LTS = R-94, G-39 B-80
Ubuntu & ubuntu Server LTS = R-119, G-41, B-83

The point is not the graphic, although that's severe enough, it's pretty obvious whoever created it just did an color-pick/paste from his/her destkop background to save time. I get it, developers are busy, I've been there many times, having to document stuff for the user-community is not something you're expected to spend too much time on, and I guess I'm grateful there's a graphic at all.

The point is, it reminded me of exactly that desktop, if you'll all excuse me, the (f)ugly yellow/purple default gnome theme.  Someone could benefit from hiring a graphic designer who didn't just find his/her degree in a fortune cookie this morning.  Not for the graph, of course, but to design themes that actually make sense.  Yes, I know, I wasn't born yeserday, different people with different tastes and all that, but why did this one have to be the default, and why is it so difficult to customize any stock theme to your own liking and save/implement it on your own desktop?  I do remember this was available at least since Hardy or Intrepid.  And yes, I've been to gnome-look.org, 32,45,634 options is as good as no options, who has the time for that?

Better yet, while we're all salivating over "unity" -- why not ***unify*** the 12,637 different gnome "appearance" tools currently floating around into something coherent, useful, that lets you configure very element of your existing theme(s) in a way that doesn't feel like a straightjacket?  I now get panel tooltips in black text on very dark grey background.  I'm sure that's not what I meant to do, when I was paying attention to something else I was adjusting.  I would kill to know which tool I was using when that happened --  gnome-tweak-tool? ubuntu-tweak? gtk-theme-config?  heathen-banshee-voodoo-maker?

These tools are the reason I'm up so late.  Never took me this long to configure any release of Windows to my liking, and I despise Windows.

---

### Post by Copper Bezel on 2013-06-30
On the graph, it's actually a conceptual problem, I think - "server and desktop" and "server only" are *two *things, not three, and there are exactly two distinct colors used, so it works out, and then the key jacks it up. = .

On Windows - I don't get this comparison, because Windows isn't exactly heavy on the theming. You can make it a different color. Admittedly, with Ubuntu, you're limited to just two of those colors without downloading anything, and the default Ambiance and Radiance themes *are* fairly terrible. Personally, I *do* spend much more time configuring a new Ubuntu install than I do a new Windows install, but that's more a difference in the "give up" threshold than a claim that there are fewer things I *want* to change in Windows. = /

But for lack of settings access in general - I'd personal rather Ubuntu's extreme than the experience I had recently trying out KDE again. Settings screens that really try to include everything become a goddamn mess of confusion and redundancies, and just knowing that that option you're looking for is probably in there somewhere doesn't help much in finding it. And tabs, tabs, everywhere!

I don't think Gnome-Look really is too many choices. There are plenty of awful ones, but I'd say that having thousands of choices in this case is a bit like having tens of them, because no one is going to page through more than the first few pages of GTK3 themes to find something that looks decent. I'd think that a newcomer to Gnome Look would be likely to sort the themes by most-popular to help winnow that down;  and why the themes are not listed that way by default, I think, is more Gnome-Look's problem than Ubuntu's. There *are * a lot of minor variations on Adwaita, Ambience, and MacOS-Aqua-inspired themes to sift out these days, admittedly.

As for Ubuntu Tweak and the like, Ubuntu doesn't produce the extra configuration tools, which is what makes them extra (except for CompizConfig, which is more or less a Canonical project now.) They're all different projects with different purposes. Gnome Tweak Tool is a Gnome project designed around Gnome Shell, so it's useful for settings that aren't included in either Gnome's or Ubuntu's main settings managers, but it's not geared for Ubuntu at all. Ubuntu Tweak, as the name implies, is designed for Ubuntu, and draws together a lot of stuff from a lot of places that go beyond theming and appearance settings (mostly a catch-all for perceived missing features in any kind of settings context.) gtk-theme-config is a very simple little tool that does one thing, written by one person unassociated with Gnome or the Ubuntu Tweak folks. The fact that these guys don't or can't get together has nothing to do with Ubuntu and isn't Ubuntu's problem.

I guess it *was* easier, before Gnome 3, to switch theme components and set GTK colors straight from the Appearance Settings window. I don't think of that as "modifying themes," since themes really can be modified directly and that's not what the Appearance Settings window was doing. That said, the simplified settings screens really are kind of a good thing, as opposed to the crazy mess of applications available under "preferences" and "administration" prior to Gnome 3 (though it's irritating that some, like Startup Applications, are still left out of the System Settings manager.) In any case, I don't think fine control of individual colors makes a lot of sense; again, if you really want to dig in and change those things, it's always possible to edit the themes themselves. Not exactly *intuitive*, mind, but I don't think it's really a common enough task to need a graphical editor for. I mean, there are a *lot* of colors to set, and there's no reasonable way to simplify the mess of settings that would really represent, but why stop at colors? Should the settings manager include controls all the widget sizes, bevel radii, styles, etc.? Should there be an Emerald-esque Metacity theme manager for controlling title bars? There's a lot of information in a GTK theme, and singling out colors seems arbitrary to me.

Ideally, I'd rather just see an easy way to install additional complete, packaged themes that would appear in Appearance Settings, like a few really good themes included in the repos and thus installable through the Software Center. A default system theme that didn't hurt might help, too; there's a reason that Ubuntu's choice of such a dark, heavy theme is as unique as it is, and it's not because they're ahead of the curve. The orange is probably a little bright, as well. (I don't know where you're seeing purple, though. That's only in the default background and the Dash, which takes its colors from the background, so as soon as you change the background, there's no purple. The login screen, I suppose, but it's quite pretty.)

---

### Post by vasa1 on 2013-06-30
> **r_avital said:**
> ... all in very close and practically indistinguishable shades ...
This seems to be the fashion on several sites. Not found any explanation. Maybe it's just a mindless do as others do.

---

### Post by castrojo on 2013-06-30
> **r_avital said:**
> I get it, developers are busy, I've been there many times, having to document stuff for the user-community is not something you're expected to spend too much time on, and I guess I'm grateful there's a graphic at all.

So if you already opened the thing in GIMP, why not just fix it and replace the one on the site with a readable one?

---

### Post by r_avital on 2013-06-30
> **castrojo said:**
> So if you already opened the thing in GIMP, why not just fix it and replace the one on the site with a readable one?

Theres an idea... I had no idea I had the privileges on that site to do that.  Thanks!

---

### Post by MadmanRB on 2013-06-30
> **Copper Bezel said:**
> 

On Windows - I don't get this comparison, because Windows isn't exactly heavy on the theming. You can make it a different color. Admittedly, with Ubuntu, you're limited to just two of those colors without downloading anything, and the default Ambiance and Radiance themes *are* fairly terrible. Personally, I *do* spend much more time configuring a new Ubuntu install than I do a new Windows install, but that's more a difference in the "give up" threshold than a claim that there are fewer things I *want* to change in Windows. = /

Personally I really like ambiance and radiance, sure they are not colored blue, blue and more blue with lots of gloss and glaze But Ubuntu is trying to stand out here.

> But for lack of settings access in general - I'd personal rather Ubuntu's extreme than the experience I had recently trying out KDE again. Settings screens that really try to include everything become a goddamn mess of confusion and redundancies, and just knowing that that option you're looking for is probably in there somewhere doesn't help much in finding it. And tabs, tabs, everywhere!

And a contradiction, you complain about how limited Ubuntu is and yet complain that KDE has too many options.
You just said a paragraph ago you like windows because you can change from the default theme easily without extra stuff.
Make up your mind.

> I don't think Gnome-Look really is too many choices. There are plenty of awful ones, but I'd say that having thousands of choices in this case is a bit like having tens of them, because no one is going to page through more than the first few pages of GTK3 themes to find something that looks decent. I'd think that a newcomer to Gnome Look would be likely to sort the themes by most-popular to help winnow that down;  and why the themes are not listed that way by default, I think, is more Gnome-Look's problem than Ubuntu's. There *are * a lot of minor variations on Adwaita, Ambience, and MacOS-Aqua-inspired themes to sift out these days, admittedly.

Again you bring up that Ubuntu has too few choices and yet complain about having too many choices, again please make up your mind.

> I guess it *was* easier, before Gnome 3, to switch theme components and set GTK colors straight from the Appearance Settings window. I don't think of that as "modifying themes," since themes really can be modified directly and that's not what the Appearance Settings window was doing. That said, the simplified settings screens really are kind of a good thing, as opposed to the crazy mess of applications available under "preferences" and "administration" prior to Gnome 3 (though it's irritating that some, like Startup Applications, are still left out of the System Settings manager.) In any case, I don't think fine control of individual colors makes a lot of sense; again, if you really want to dig in and change those things, it's always possible to edit the themes themselves. Not exactly *intuitive*, mind, but I don't think it's really a common enough task to need a graphical editor for. I mean, there are a *lot* of colors to set, and there's no reasonable way to simplify the mess of settings that would really represent, but why stop at colors? Should the settings manager include controls all the widget sizes, bevel radii, styles, etc.? Should there be an Emerald-esque Metacity theme manager for controlling title bars? There's a lot of information in a GTK theme, and singling out colors seems arbitrary to me.

Again you backpedal here, what KDE has is what gnome lost, gnome used to have the same gui config options that KDE has, you praise Gnome for it and yet scorn KDE?

> Ideally, I'd rather just see an easy way to install additional complete, packaged themes that would appear in Appearance Settings, like a few really good themes included in the repos and thus installable through the Software Center. A default system theme that didn't hurt might help, too; there's a reason that Ubuntu's choice of such a dark, heavy theme is as unique as it is, and it's not because they're ahead of the curve. The orange is probably a little bright, as well. (I don't know where you're seeing purple, though. That's only in the default background and the Dash, which takes its colors from the background, so as soon as you change the background, there's no purple. The login screen, I suppose, but it's quite pretty.)
And in the same breath you both condemn and compliment Ubuntu default theme, again make up your mind please.

---

### Post by vasa1 on 2013-06-30
> **castrojo said:**
> So if you already opened the thing in GIMP, why not just fix it and replace the one on the site with a readable one?
Immutable page.

---

### Post by Elfy on 2013-06-30
> **vasa1 said:**
> Immutable page.

Looks editable to me when I'm logged in.

---

### Post by Copper Bezel on 2013-06-30
MadmanRB, I did express a number of opinions in there, but very few of them had to do with which desktop is "better" than another, and not every observation I made was meant as a "point" for one side or another. I actually don't care much about that in this case - I wasn't looking at this as a Spiderman-vs.-Wolverine, who-would-win conversation. Since I didn't make it very clear, I find Windows difficult to fit to my workflow because there are a lot of options I'm used to that aren't there, and I find KDE baffling, but I'm certainly biased by being more familiar with the various flavors of Gnome, too. None of that's really important to what r_avital was talking about. He was saying that Ubuntu needed easier theme customization, and I was mostly disagreeing.

It was a rather confusing post, I admit. Could have taken some time to organize that junk.

> **MadmanRB said:**
> Personally I really like ambiance and radiance, sure they are not colored blue, blue and more blue with lots of gloss and glaze But Ubuntu is trying to stand out here.
No, I'm aware of that, and I'm also aware that Ambiance has become a part of Ubuntu's brand identity - it shows up in all the little screenshots when people promote software for Ubuntu, and it probably has to stay for that reason alone. I just happen to agree with r_avital that it's ugly. 

> And a contradiction, you complain about how limited Ubuntu is and yet complain that KDE has too many options.
You just said a paragraph ago you like windows because you can change from the default theme easily without extra stuff.
Make up your mind.
Yeah, no. I said that in Windows, the user can choose a theme color. That's most certainly not high praise, and certainly didn't mean that I "like Windows." KDE *does *have too many options. Ubuntu *is *limited in terms of theming, but I didn't and wouldn't say it's *too *limited. The worst I said was that it'd be nice to have some mechanism for installing themes as "packs" that would actually show up in the Settings->Appearance screen, this little menu:

[IMG]https://dl.dropboxusercontent.com/u/17749392/Image%20Hosting/Mockupzen/appearance.png[/IMG]

As it is, it's awkward that newly installed themes don't appear in the most obvious place, and it's made more awkward by the fact that only Ambiance and Radiance are there to begin with, then compounded by my feeling that they're not great themes. It's an amazingly useless menu, and it'd be nice if changing the destkop theme could be handled within the normal settings screens (that is, not Gnome Tweak,) even if that theming was offered in a somewhat limited way.

Basically, I don't know who's supposed to use that control, because people who use Gnome Tweak would ignore it, and it doesn't do much good for people who don't.

> And in the same breath you both condemn and compliment Ubuntu default theme, again make up your mind please.
No. I was responding to a thing that r_avital said about the "(f)ugly yellow / purple" GTK theme. I happen to agree that it's ugly, and yet it is not, in fact, purple or yellow. = ) I did say that the login screen (the Unity greeter) is very pretty, but that's nuts to do with any of this other stuff.

---

### Post by r_avital on 2013-06-30
Copper,

Thanks for a very well thought-out reply. I'm glad I'm not the only one who thinks the default theme is an atrocity.

You've made some excellent points and I agree with most of them.  One thing that's being overlooked however, is the relevance to the end-user, especially the novice, or even the experienced one who tries gnome or kde or xfce for the first time (You've admitted yourself your frustrations with kde).  Namely, experienced users such as the ones here will know the difference between what's developed by Canonical and what's developed by small teams or even individuals, but many don't know and couldn't care less.  Tough tamales for them, I understand that, you need to expect such inconsistencies when you're dealing with free-beer-free-speech software tools.  Even Windows users, who have seen a favorite firefox/thunderbird theme disappear and no longer maintained would have that experience.

Which brings me to this -- have you witnessed the mini-civil war that went on, over thunderbird putting tabs above toolbars?  One developer devoted pages and pages on his web site to advocate in favor of that change, and made very convincing arguments, which in the end, did not pacify the rather large portion of users who screamed about it.  So he had the decency to release an addon that reverted to the old scheme.  That makes it perfectly identical to how TB worked before the change, and is therefore an acceptable solution.  But you know that the fallback gnome2 under the current ubuntu releases is not really gnome2, right?  For instance, adding a launcher to your panel in a "gnome-classic" session is impossible, without logging off, loggin on with a "gnome classic no effects" session, make the change there, log off/log on again.  That's just one example.

I'm really not much of a wow-factor or eye-candy user.  I just want cr@p to work without hurting my eyes, and most of the time it does, with ubuntu.  I like the productivity of switching workspaces with a mouse-wheel, but don't like the sudden panic when you flip the wheel into an empty workspace without noticing, and are looking at a blank screen and go wtf how did it all disappear - so I'll use a compiz rotating cube to get the visual feedback that what's happening is happening because I did something, not because something crashed.  But I won't bother decorating the cube caps, not trying to impress anyone, just trying to get work done.

FWIW I've just booted into xubunty for the first time, from a usb stick, I like it so far (just a few minor gripes), and might move to it.  But man, this is so much more work than I anticipated, when all I wanted was a smooth transition from one LTS (lucid) to another (precise).

---

### Post by MadmanRB on 2013-06-30
> **Copper Bezel said:**
> 

No, I'm aware of that, and I'm also aware that Ambiance has become a part of Ubuntu's brand identity - it shows up in all the little screenshots when people promote software for Ubuntu, and it probably has to stay for that reason alone. I just happen to agree with r_avital that it's ugly.

So what would you have as Ubuntus default colors?
More glossy?
More glassy?
More blue?
More gray?
More gradient?
Again all that stuff is in Windows or OSX, and to be honest i am kind of with Mark Shuttleworth that it makes things too "kitchenware" in appearance, all shiny and bright.
I find both too sterile, I like the more humble looks of ubuntu.
You may call it ugly, I call it a nice alternative to the blue/gray/glossy/gradiant default themes of ubuntus main competitors.

> 
Yeah, no. I said that in Windows, the user can choose a theme color. That's most certainly not high praise, and certainly didn't mean that I "like Windows." KDE *does *have too many options. Ubuntu *is *limited in terms of theming, but I didn't and wouldn't say it's *too *limited. The worst I said was that it'd be nice to have some mechanism for installing themes as "packs" that would actually show up in the Settings->Appearance screen

As it is, it's awkward that newly installed themes don't appear in the most obvious place, and it's made more awkward by the fact that only Ambiance and Radiance are there to begin with, then compounded by my feeling that they're not great themes. It's an amazingly useless menu, and it'd be nice if changing the destkop theme could be handled within the normal settings screens (that is, not Gnome Tweak,) even if that theming was offered in a somewhat limited way.


Gnome used to have something like that, it got ditched when the Gnome developers became insane and changed everything for the worst.

> Basically, I don't know who's supposed to use that control, because people who use Gnome Tweak would ignore it, and it doesn't do much good for people who don't.

The fact that you need something like gnome tweak tool is a huge weakness in gnome right now, ubuntu sadly inherits those flaws you are pointing out.

---

### Post by grahammechanical on 2013-06-30
I understand what they are trying to show. First, a colour type for for standard releases (orange) and a colour type for LTS releases (purple) and they are using the prime colour of Ubuntu (orange) and Canonical (Purple). It is called product identification.

With 10.04 LTS the desktop had a shorter support term than the server. So a slight variation in the purple colour. But from 12.04 LTS onwards both server and desktop have the same length of support and hence there is not a variation in the purple line for 12.04 LTS and 14.04 LTS.

It is all here written down:

> [COLOR=#333333][FONT=Ubuntu Beta]A new LTS version is released every 2 years. In previous releases, a Long Term Support (LTS) version had 3 years support on Ubuntu (Desktop) and 5 years on Ubuntu Server. Starting with Ubuntu 12.04 LTS, [/FONT][/COLOR]**both**[COLOR=#333333][FONT=Ubuntu Beta] versions will receive 5 years support. There is no extra fee for the LTS version; we make our very best work available to everyone on the same free terms. Upgrades to new versions of Ubuntu are and always will be free of charge.[/FONT][/COLOR]

I believe in the saying: "the worker is worthy of his hire." In the case of Ubuntu I apply that to mean - give credit for all the hard work that is being done on my behalf with cost to those who develop Ubuntu but no cost to me who use it.

Regards.

---

### Post by Copper Bezel on 2013-06-30
[QUOTE=r_avital][COLOR=#000000]You've made some excellent points and I agree with most of them. One thing that's being overlooked however, is the relevance to the end-user, especially the novice, or even the experienced one who tries gnome or kde or xfce for the first time (You've admitted yourself your frustrations with kde). Namely, experienced users such as the ones here will know the difference between what's developed by Canonical and what's developed by small teams or even individuals, but many don't know and couldn't care less. Tough tamales for them, I understand that, you need to expect such inconsistencies when you're dealing with free-beer-free-speech software tools. Even Windows users, who have seen a favorite firefox/thunderbird theme disappear and no longer maintained would have that experience.[/COLOR][/QUOTE]
Yeah, I get that. And, obviously, Canonical isn't prioritizing this part of the experience, or they'd release their own tool to include all of these features. If the features are important, then that *is* an oversight. 

I think that especially with Gnome 2, since there wasn't a monolithic "default experience," the features that any one user depended on were often very different from the features that others might; there were a lot of options and combinations of options that could provide very different desktop experiences in a few clicks. That's an extra complication in trying to replace it, if anyone had intended to really just "replace" Gnome 2, since the expected feature set is basically undefined. (Can't help wondering if Compiz transitioning to a Mir compositor is going to mean much the same problem over again, if CCSM stops working and Canonical has to pick which plugins and tweaks to invest in.)

The Thunderbird example is a good one, but it simply can't happen in every case. Leaving the option of using old UIs or deprecated features adds an extra load on developers, particularly in testing. When we're talking about two separate desktop environments, with totally different feature sets and code bases, I don't see how that could work out - Gnome Classic might not be a very polished product, but it's a fairly impressive and presumably costly gesture. (Not to say that that makes it useful.) And the option to switch back to the old way of doing things is almost *always* a stopgap measure that will eventually get dropped in a future version, so it seems like delaying the inevitable.

(Should note that, as usual, the weirdness that happens when running Classic under Compiz is yet another "not the same project" problem. What Ubuntu calls Classic (No Effects) is provided by Gnome, and Ubuntu offers the option of running it under Compiz, but it's not *designed* to run under Compiz, and the combination isn't really backed by anyone; it's really no different than opting to run Compiz over Xfce or KDE. I guess the onus would fall on Canonical, if anyone, to make it work, but I'm not sure what would make it a priority or really why the option is provided at all.)

---

### Post by Copper Bezel on 2013-06-30
> **MadmanRB said:**
> So what would you have as Ubuntus default colors?
More glossy?
More glassy?
More blue?
More gray?
More gradient?
Again all that stuff is in Windows or OSX, and to be honest i am kind of with Mark Shuttleworth that it makes things too "kitchenware" in appearance, all shiny and bright.
I find both too sterile, I like the more humble looks of ubuntu.
You may call it ugly, I call it a nice alternative to the blue/gray/glossy/gradiant default themes of ubuntus main competitors.
Certainly no gloss! And I'm not deeply committed to my aesthetic preference. It just seems dark and heavy to me. I prefer and end up using light themes in the Orta / Greybird / Adwaita family, but these admittedly read as Macish. I don't know what I'd honestly prefer as a default.

> Gnome used to have something like that, it got ditched when the Gnome developers became insane and changed everything for the worst.
Well, yeah, there used to be a lot of settings in the old Appearance Settings, and now it has one nearly-non-functional drop-down menu. What I'm suggesting is that they at least make the drop-down menu do *something,* like perhaps offering themes in a bit more "packaged" form, where the GTK, window, and icon themes all come in a bundle, installed system-wide, and then can be selected from that drop-down menu. Else, if Ambiance and Radiance are the only options they're interested in supporting in that screen, they might as well have a toggle switch between "light theme" and "dark theme." 

I actually *prefer *the more granular control that Gnome Tweak Tool and the old Appearance settings offered, and I'm quite happy using Tweak Tool.

> The fact that you need something like gnome tweak tool is a huge weakness in gnome right now, ubuntu sadly inherits those flaws you are pointing out.
Yeah, I'd tend to agree. It should at least be integrated into the main settings manager as Advanced Settings, and right now, it's a catch-all for "features that we left out of all the other settings screens," which seems like a very silly organizational principle to me.

---

### Post by MadmanRB on 2013-06-30
> **Copper Bezel said:**
> Certainly no gloss! And I'm not deeply committed to my aesthetic preference. It just seems dark and heavy to me. I prefer and end up using light themes in the Orta / Greybird / Adwaita family, but these admittedly read as Macish. I don't know what I'd honestly prefer as a default.

Yeah those are mac like themes, but really if you want a mac like theme by default go pear OS if you dont want the apple route.
As for dark themes not being your style then why doesnt radiance suit you?
Again personally I think gray/blue/glossy/glassy themes are overdone as default themes for all the major OS's, as long as you cvan theme it on your own there is really no point in moaning.

---

### Post by vasa1 on 2013-06-30
> **Elfy said:**
> Looks editable to me when I'm logged in.Same here.

But then what does immutable page mean?

---

### Post by vasa1 on 2013-06-30
[This page]("http://design.ubuntu.com/web/colour") has:
> Supporting colours

In addition, there is a supporting colour palette for when communications have a consumer or enterprise focus.
Light aubergine

#77216F: Consumer focus
Mid aubergine

#5E2750: Balance of consumer and enterprise focus
Dark aubergine

#2C001E: Enterprise focus. This is the primary colour for Server and Cloud.
which is partly different than what I see using gColor's dropper:
I get from (left to right):  #77216F, #5E2750, and #772953.

Edit: forgot to include:
> Canonical aubergine

#772953

---

### Post by Copper Bezel on 2013-06-30
> **MadmanRB said:**
> Yeah those are mac like themes, but really if you want a mac like theme by default go pear OS if you dont want the apple route.
As for dark themes not being your style then why doesnt radiance suit you?
I probably overstated my dislike for it. The orange is a little too saturated and plasticky, and I don't like how it (or Ambiance) looks in Nautilus or GTK2 apps, where the titlebar looks "cut off" - in GTK3 apps, the toolbar blends with the titlebar and everything looks nice and smooth. The themes I listed are a bit more understated overall. That buttery champagne color is really nice, though - really distinct and a lovely choice. I don't particularly care for Mac themes for Mac's sake, and I actively dislike the skeuomorphic metal-textured ones. I just personally like the simplicity that happens to come with a lot of Mac-inspired themes (often more so than with OSX Aqua itself.) 

But that's all personal preference stuff. Again, I actually think that Ambiance is too dark and heavy *as a default theme*, because I just don't think it's very inviting, but I also understand why Ubuntu couldn't change the look too greatly even if they felt the same way, because it's been around long enough to cut out a space for what an Ubuntu-like theme is. = ) I agree that it's good that it isn't a glassy, metal, or flat-colors theme, because distinctness from Windows and Mac is important. I also don't know what that leaves. 

> Again personally I think gray/blue/glossy/glassy themes are overdone as default themes for all the major OS's, as long as you cvan theme it on your own there is really no point in moaning.
Right, and I'm just saying, as you did with reference to the Tweak Tool, that it'd be nice if theming was simpler for other people who don't care to go through the extra steps, which I think r_avital was saying, too. So I don't think we're actually greatly disagreeing here.

---

### Post by craig10x on 2013-07-01
Radiance is really nice...i always switch to it right after installing...i think it looks great with that color scheme...They really should offer at least a handful of options instead of really only basically the two that have any practical use (Ambiance and Radiance) but i am thankful that Radiance is the option...i think it helps it look more "mac like" then the default does...It has a much more of a metal look to it and i prefer a lighter scheme over a black one...

---

