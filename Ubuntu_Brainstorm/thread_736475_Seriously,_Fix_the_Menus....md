---
title: "Seriously, Fix the Menus..."
date: 2008-03-26
forum: Ubuntu Brainstorm
---

### Post by Redrazor39 on 2008-03-26
Seriously, Fix the Menus

[B]*Edit* I finally have a solution that will work perfectly. Here it is:

[I]I have an idea for the System menu. We should divide it up more like the applications menu. More specifically, take how we have all of the options organized in GNOME-Control-Center (System > Preferences > Control Center) and use those categories as categories in the System menu. Set everything within those in Control Center as the subcategories in the System Menu. Basically what I'm saying is, take all the categories from GCC and put them in the System menu.

To differentiate between Administrative tasks and normal tasks, put a small padlock icon after the text of the option. This way, the user knows what is an administrative task and what isn't at a glance.[/I][/B]

The current main menu system seems great. Divide it into three comprehensive and simple categories: Applications, Places, and System, and BAM! You&#8217;ve got instant organization. Well, that&#8217;s close, but wrong. Right now, the menus are a bit disorganized, especially the system menu, but I&#8217;ll just go right down the line of what to fix in each category.

Applications:

   1. The categories (Accessories, Games, Internet, etc.) are great. They&#8217;re easy to understand and don&#8217;t just organize by company/developer name, which is almost useless until you know your programs really well. There are a few things that can be improved upon just to make it a little better.
   2. Within each category in the Applications menu (Internet, Games, etc.), organize the actual Applications by alphabetical order. This way, if someone knows which program they want, then they can easily look at the categories and go through the alphabet to find it. This doesn&#8217;t sound like a very useful improvement, but if someone has a large number of applications in a single category, it just makes it easier to find what the user wants. This should only be the default and the user should be allowed to reorder anything they want later.
   3. Minor bugs such as the icons not showing up sometimes should be fixed, but it really doesn&#8217;t happen that often or to many people. In fact, this part should apply to all of the menus.

Otherwise, the Applications menu is pretty good. Nice and simple, well organized, and has what you expect it to have, as well as the Add/Remove button, which is nicely placed.



Places:

This menu is well organized as well and has things like Computer lower down because those are less accessed than, say, Documents. All in all, this menu is pretty good.



System:

This is where we hit the problems. For one thing, it&#8217;s all cluttered up once you get to Preferences or Administration. There are WAY too many options. Also, under Preferences is Control Center, but this is pretty much useless since all of the options are already within the menu. That&#8217;s just sad.

Let&#8217;s start with when you first click on System. You see Preferences, which has almost a full screen height of options, some of which you don&#8217;t even know what they do. Under Administration, you have a bunch of stuff that requires a password to use. Then, you have the About GNOME and all that, and in Preferences, you have Control Center, which has all of this stuff in icon view. Seriously, what the hell? Why would you even use the control center when it&#8217;s all in a menu, and why is the menu so cluttered that you would want to do some extra clicks to reach the control center? This is just all messed up.

   1.

      First, we can combine some of the stuff. For example, in Preferences, combine Mouse, Keyboard, and Printer into a button called "Peripherals". Then, put Emerald Theme Manager (if installed), GL Desktop, Screensaver, Advanced Desktop Effect Settings, and Appearance all in a new category called "Appearance and Effects", that will basically be Appearance as it is now, but with all of these extra things tabbed in there, too. In the Administration category, combine Network and Network Tools into one button that is sectioned off or tabbed to include both. As I look at the System Menu, I realize one thing must be done. We need to unify the Synaptic Package Manager, Software Sources, and Add/Remove Applications. This desperately needs to be done. Just create one window for it all and in the Applications Menu, it can be called Add/Remove, but in System>Administration, it can be called &#8220;Software Manager&#8221;. This would be much easier.
   2.

      Then, what do we really need quicker access to? Just pick those few things and put those in the menus, with everything in the control center window.

One idea that was posten on the Ubuntu forums was to rename System Menu options by function rather that name. For example, if Synaptic Package Manager had to remain, in the menu call it &#8220;Install, Remove, and Manage Software&#8221;.

So that&#8217;s fixing the System Menu. Also, just make things look nice. Add those nice little touches that make life easier and make your computing experience look and feel better and more complete.





Also, when you choose the start menu-esque main menu that is only one button, instead of vertically stacking Applications, Places, and System, separate them Horizonally. You click on the button, then you get something a little more like Linux Mint&#8217;s menu, except the closest thing to your mouse is the Applications section. Here, you click a button as a category (like Games, Accessories, etc.), and then you can scroll through whatever is there in the next column. Places would just be one column because it&#8217;s not that many options, and so would system, except system would have the same Hierarchical menus that pop out of the right side for you to pan through.

---

### Post by Het Irv on 2008-03-26
You can do all these changes to your own computer, It will take some work, but it is possible.  
System ->Prefrences -> Main Menu

---

### Post by Afoot on 2008-03-26
> **Het Irv said:**
> You can do all these changes to your own computer, It will take some work, but it is possible.  
System ->Prefrences -> Main Menu
You could change anything in Ubuntu, but there's a reason this is in the Idea Pool section...

---

### Post by Het Irv on 2008-03-26
Yeah, and I agree that at least the System menu should be cleaned up, guess I should have said that in my first post.  I was just making sure that they knew what they wanted to do was possible now.

---

### Post by iSplicer on 2008-03-26
I, too agree the system menu is too cluttered, but I think everything else is fine

---

### Post by zekopeko on 2008-03-26
keyboard, mice and other input devices should be in a new capplet in GNOME 2.24 like fonts and stuff are in appearances capplet.

---

### Post by Redrazor39 on 2008-03-26
I know it can be done, but it should be done by default. Also, I'm noobish with Ubuntu and I lose the standardization if someone tells me to go somewhere in the menu and I changed it, I'll get completely lost. Also, what I am suggesting includes putting windows together, which I can't in the slightest do (because of lack of knowledge).

---

### Post by Redrazor39 on 2008-03-26
oh ya, and put everything within each subcategory (meaning everything within Accessories, Games, Preferences, etc.) in alphabetical order to just find them easier.

---

### Post by chrisccoulson on 2008-03-26
> **Redrazor39 said:**
> Within each category in the Applications menu (Internet, Games, etc.), organize the actual Applications by alphabetical order. 

I thought they were already arranged in alphabetical order - they certainly are on my machine


> **Redrazor39 said:**
> Minor bugs such as the icons not showing up sometimes should be fixed, but it really doesn&#8217;t happen that often or to many people. In fact, this part should apply to all of the menus.
This is usually down to broken .desktop files I think, or broken themes. Either way, you should raise bug reports against affected packages / contact theme developers etc.

> **Redrazor39 said:**
> This is where we hit the problems. For one thing, it&#8217;s all cluttered up once you get to Preferences or Administration. There are WAY too many options. Also, under Preferences is Control Center, but this is pretty much useless since all of the options are already within the menu. That&#8217;s just sad.

Let&#8217;s start with when you first click on System. You see Preferences, which has almost a full screen height of options, some of which you don&#8217;t even know what they do. Under Administration, you have a bunch of stuff that requires a password to use. Then, you have the About GNOME and all that, and in Preferences, you have Control Center, which has all of this stuff in icon view. Seriously, what the hell? Why would you even use the control center when it&#8217;s all in a menu, and why is the menu so cluttered that you would want to do some extra clicks to reach the control center? This is just all messed up..
I thought that Control Centre was going to be an alternative to the menu structure. Even so, people can still use one or the other - you could have a Control Centre icon on your panel for example.

I do agree that the preferences menu is a bit cluttered though. There was a discussion a while back about using sub categories in the preferences menu (as per Fedora) [here]("http://ubuntuforums.org/showthread.php?t=610045"), which raised some pretty valid points - both for and against the idea.

As for the 'About GNOME' and 'About Ubuntu' options in the System menu, please have a look at [this]("https://blueprints.launchpad.net/ubuntu/+spec/about-this-computer") blueprint:)

---

### Post by smartboyathome on 2008-03-26
About the combining of stuff:
I would hope that CompizConfig will NOT be combined with appearance. It is just to big for it, and would either force a redraw of the window (bad on memory) or would force the window to be huge (bad on how it looks). Also, Add/Remove should NOT be combined with Synaptic, this would create different interfaces and code for the same app, and finding out what did what would be a nightmare. Right now that would be better. And Software Sources IS part of synaptic, I agree that it shouldn't be part of the default menu.

Also, about the menu:
Linux Mint's menu is IMO far from simplistic, and is slow. You can get the same menu with Ubuntu System Panel, and it should be in the repos, but not installed by default.

---

### Post by Redrazor39 on 2008-03-26
Good call. Ok, keep CompizConfig out, and keep add/remove and synaptics separate, but combine software sources and synaptic by tucking software sources in a Tools menu or something.

---

### Post by qamelian on 2008-03-26
> **Redrazor39 said:**
> Good call. Ok, keep CompizConfig out, and keep add/remove and synaptics separate, but combine software sources and synaptic by tucking software sources in a Tools menu or something.
Software sources are already in a menu in Synaptic, called Repositories in the Settings menu. I like them as a separate option as well though because there are times when I might want to add or remove a repo and don't need to go into full-blown Synaptic to make the adjustment.

---

### Post by googlah on 2008-03-28
Totally agree on this. Everything in System which has to do with the screen for instance, should be placed under one icon only. Like, screen resolution, screensaver, (GL Desktop?) and so on. A better improvement of this, because the System menu is really hard to get a hand on right now.

---

### Post by alexforcefive on 2008-03-28
I'd like to see the Preferences menu replaced entirely with gnome-control-center. By the way, you can't do it yourself. I tried last night and eventually came across [this bug]("https://bugs.launchpad.net/alacarte/+bug/123955")

---

### Post by smartboyathome on 2008-03-28
> **alexforcefive said:**
> I'd like to see the Preferences menu replaced entirely with gnome-control-center. By the way, you can't do it yourself. I tried last night and eventually came across [this bug]("https://bugs.launchpad.net/alacarte/+bug/123955")

You can't insert any item into the system menu, unfortunately. If you could, then I would like it put there for those who would use it. :)

---

### Post by zekopeko on 2008-03-28
there was a try to replace system and preferences with gnome-control-center but a bunch off people complained.
Mac OS X has implementation like that and mac's are pretty easy to use.
I know that GCC is a little slower than the hierarchical model we use now (only when opening) but it removes the clutter and has search functionality which could be used to great effect if we give a lot of metadata to the entries in it (ie. a lot of description that the end user isn't aware but can search by it).

---

### Post by Redrazor39 on 2008-03-29
yes, Personally I proposed that we just clean up the menus, while still allowing an option just below the Administration button in the System menu for the Gnome Control Center with a seriously improved search function.

---

### Post by NightwishFan on 2008-03-29
If you guys want to see a cluttered menu run a Knoppix live cd. :lolflag:
They have the same program listed 6x but I have no complaints. I assume some users will though.

---

### Post by CarpKing on 2008-03-30
I agree that some capplets should be combined, but you have to be careful to avoid making things hard to find within them.  It would also be nice to be able to easily have a GCC entry in place of the pref & admin menus; this should be default eventually, but probably with an option to switch back.  For GCC to be default, it should be arranged such that all the default capplets can be seen without scrolling.  Combining capplets would help this happen.

---

### Post by OzzyFrank on 2008-04-01
Well, call me a fascist, but I don't think what one person sees as his perfect menu layout should be made default for the rest of us. I think it's all pretty good as it is, and what isn't for me, I change with a few mouse-clicks. Too many options? That's a new complaint, haha! And I would say the Control Center is good for people who don't want to keep going into the menus when changing a bunch of preferences, and for newbies wanting a look around (especially if they're used to the Control Panel in Windows). But I also wouldn't remove the individual items just because Control Center is there, or start grouping them together (more than some of them already are, like in Appearance).

Icons not showing up? I thought that was the domain of the developers of programs, no? Correct me if I am wrong, though.

To combine Mouse, Keyboard, and Printer into a button called "Peripherals" would be absolutely horrid, and confusing for newbies. Hope no-one is listening to that idea! Especially since printers would be "Peripherals" but the others more like "Input Devices"!

And let's keep the menus dropping down as they do now. I am sure there are hacks out there for those who want more of a horizontal thing happening.

---

### Post by Mr. Picklesworth on 2008-04-02
There are a lot of things under Preferences and Administration that do not actually *set* anything, and then there is a whole other System Tools category with a seemingly random collection of applications.
The Applications -> System Tools category should be removed, replaced with System -> Tools. It should contain Network Tools, System Monitor, Device Manager, Avahi, System Log...

GNOME 2.22 has definitely improved the menus a tad. I think one of the bigger offenders here is Java, which places a really ugly (and for most users useless) Policy Tool under system preferences -- and this happens for both OpenJDK and Sun's bother, both of which can be installed at the same time.
It has never made sense to me that the Java runtime environment needs to be so bloody obtrusive.

---

### Post by OzzyFrank on 2008-04-02
Yeah, for someone like me, the Java tools are a waste of space, but figured there'd be others out there who would be screaming if they weren't included. But maybe the Applications menu would be a better place than the System one? I just figured if my System menu starts filling up with useless stuff, I'll just go in there and hide a few things, like Java. But yeah, I agree there are a few things in the System menu that don't even do anything, like the Cursors app (what's with that?!?!). But rather than remove them, I'd like to see them fixed, hehe.

---

### Post by Redrazor39 on 2008-04-03
I just got an idea. How about we keep almost all of the stuff in the menus as they are, but organize them differently? This is how:

First, take Control Center out of preferences and put it right below Administration in the system menu. Next, here's the main thing, organize the items in Preferences and Administration by category, but have small, subtle titles separating them. Small center-aligned text with a horizontal line on each end that separates the categories. This way, things will be much easier to find, AND people who just want the control center can use it with two clicks.

I think this is the easiest and simplest solution. The cool thing is, the hard part (organization) is already done! If you go to the control center, everything is organized in categories. Just place things in that order in the menus and then have small text tiles between them to show some separation.


What do you think?

---

### Post by smartboyathome on 2008-04-03
I like that idea the most of any so far.

---

### Post by Redrazor39 on 2008-04-03
thanks. Really, I was just trying to get them organized for easier and quicker access (the whole point people like menus more than GCC) and I hated looking through all of those options that weren't ordered that well. I really think we (or someone) should do this; it wouldn't be that hard (at least I don't think so, but I'm not expert ;) )

---

### Post by Het Irv on 2008-04-04
> **Redrazor39 said:**
> I just got an idea. How about we keep almost all of the stuff in the menus as they are, but organize them differently? This is how:

First, take Control Center out of preferences and put it right below Administration in the system menu. Next, here's the main thing, organize the items in Preferences and Administration by category, but have small, subtle titles separating them. Small center-aligned text with a horizontal line on each end that separates the categories. This way, things will be much easier to find, AND people who just want the control center can use it with two clicks.

I think this is the easiest and simplest solution. The cool thing is, the hard part (organization) is already done! If you go to the control center, everything is organized in categories. Just place things in that order in the menus and then have small text tiles between them to show some separation.


What do you think?

Just playing Devil's Advocate here:
The major complaint I have is that you are not really fixing the problem, just making it worse.  The menus are to long as it is and you are proposing to make them longer by adding titles to each section. {/DA}

Once you get past that bump you have a great idea.  Although I would like for the titles to be left-aligned Bold with no Icon.

P.S If I got your idea wrong tell me.

---

### Post by Redrazor39 on 2008-04-04
You took my suggestion the right way and I'm glad someone played devil's advocate. How about we combine a few things that obviously need to be combined, such as all the screen options to "Screen Settings".

Then we do the title thing. Even if the menus are too long, it's good to have this organization because menu scrolling isn't that bad (I have to); just look at Vista. The start menu is just fine, but that's not the point. The point is make the menus smaller if you can, but more importantly organize them better.

That was my train of thought.

---

### Post by Het Irv on 2008-04-07
Just as a personal prefrence I don't like scrolling menus, but yeah if we could combine a few things it should work.  
I think the best way to impliment this would be to slightly change alacart (Main Menu) so that you had 3 or 4 basic styles of menus, orginal, type sorted, control center, ect.  Then the user could customize from there.

---

### Post by Redrazor39 on 2008-04-07
Great Idea, Het! We should have these basic styles. Original is w/e Canonical makes, type sorted is like putting the small titles in them, control center just has System > Control Center button, and alphabetical arrangement. Then, give the user full customization

GENIUS!

we might have  a final idea coming up soon to submit to Canonical...

---

### Post by arvevans on 2008-04-07
There is more wrong with Menus than just managing categories and what is in each one.
[LIST=1]
[*]You cannot make a new menu even though the menu editor makes it look like you can (Gnome/alacarte).
[*]Software installs do not tell you which, if any, menu newly installed software will appear in (Gnome).  Some installs can never be found on any menu.
[*]Routine distro and some application updates sometimes overwrite some menu entries (Gnome).
[/LIST]

Available instructions indicate you can do some menu manipulation by editing:
[LIST]
[*]$XDG_CONFIG_DIRS/menus/${XDG_MENU_PREFIX}applications.menu
[*]$XDG_CONFIG_DIRS/menus/applications-merged/
[*]$XDG_DATA_DIRS/applications/
[*]$XDG_DATA_DIRS/desktop-directories/
[*]/usr/share/gnome/share/applications
[*]/usr/share/app-install/desktop/
[*]/usr/share/applications/
[*]$HOME/.gtk-bookmarks
[/LIST]

It's all very confusing.  On top of that, there seem to be several GUI menu editing programs, of which some work, some partially work, and some may not work:
[LIST]
[*]Alacarte
[*]Gnome_menu_edit
[*]Smeg
[*]update-menus (in CLI)
[*]Kmenuedit
[/LIST]
and so on.

There are also some "applications" that can be installed which claim to add specific menu categories (i.e. "Ham Radio") to the main menu, but didn't work for me.

It's all very confusing.  Is there a specific and official/reliable way to edit menus (1) in Gnome), (2) in KDE, etc.?

Arv
_._

---

### Post by Perpetual on 2008-04-07
I like how Fedora has sub-menus.  Not on a Fedora machine right now to explain but if you have used Fedora, you know what I mean.

---

### Post by Het Irv on 2008-04-07
I think the best way to approach any Idea in Ubuntu is to give the user more general options, allowing them to see a few basic ideas, and then let them customize.  But to keep any interfaces as simple as possible.

---

### Post by Redrazor39 on 2008-04-07
> **Perpetual said:**
> I like how Fedora has sub-menus.  Not on a Fedora machine right now to explain but if you have used Fedora, you know what I mean.
I don't really like sub-menus because then it's over-surfing the menus and not getting what you want. Think of the classic start menus in Windows and it's just hellish.
> **Het Irv said:**
> I think the best way to approach any Idea in Ubuntu is to give the user more general options, allowing them to see a few basic ideas, and then let them customize.  But to keep any interfaces as simple as possible.
I want to quote you so much. I made a wiki pretty much based on this point at [www.thenewbuntu.wetpaint.com](www.thenewbuntu.wetpaint.com) and I need some more support, but can I quote you? I agree with you 100000000%

---

### Post by Het Irv on 2008-04-07
No need, I joined your Wiki. I think you'll figure out who I am.  Just let me know what you need me to do.

---

### Post by Redrazor39 on 2008-04-07
Thanks. Basically, it's about how we can make Ubuntu more "user friendly" (whatever that really means) and really define the term with specifics as to how to do so. You can post any ideas you come up with and I'm trying to work on this "Main Article" that will eventually be organized as something to submit to various developers as the parts pertaining to what they develop. You can make threads, etc. to suggest changes. 

Right now, there's pretty much nobody there, but anyone can edit it (I'm not sure if I should change that policy or not) and anyone can join the wiki. 

If you have any improvement suggestions of your own, have at it! That's what a wiki is welcome to, whether it's about what the wiki is about or improving the actual wiki.

---

### Post by Redrazor39 on 2008-05-10
I have an idea for the System menu. We should divide it up more like the applications menu. More specifically, take how we have all of the options organized in GNOME-Control-Center (System > Preferences > Control Center) and use those categories as categories in the System menu. Set everything within those in Control Center as the subcategories in the System Menu. Basically what I'm saying is, take all the categories from GCC and put them in the System menu.

To differentiate between Administrative tasks and normal tasks, put a small padlock icon after the text of the option. This way, the user knows what is an administrative task and what isn't at a glance.

---

### Post by smartboyathome on 2008-05-11
See my post in your other thread (perhaps these two should be merged?)

---

### Post by Redrazor39 on 2008-05-11
Which other thread? I thought I saw something extremely similar to it and wanted to quote you, but I couldn't find it, so I just typed up what I could remember and think of.

I really think these should be merged.

---

### Post by smartboyathome on 2008-05-11
The reorganize thread.

---

### Post by strabes on 2008-05-16
> Also, when you choose the start menu-esque main menu that is only one button, instead of vertically stacking Applications, Places, and System, separate them Horizonally. You click on the button, then you get something a little more like Linux Mint&#8217;s menu, except the closest thing to your mouse is the Applications section. Here, you click a button as a category (like Games, Accessories, etc.), and then you can scroll through whatever is there in the next column. Places would just be one column because it&#8217;s not that many options, and so would system, except system would have the same Hierarchical menus that pop out of the right side for you to pan through.

openSUSE has this type of menu by default. It's in ubuntu's repositories. The package is called gnome-main-menu. Install it by running ```
sudo aptitude install gnome-main-menu
```Then add it to your panel by right clicking on some blank space on your panel, clicking on "Add to Panel..." and then finding the "Main Menu" applet with the computer icon. I used it for awhile but I ended up deciding that I like ubuntu's default menu system better.

---

