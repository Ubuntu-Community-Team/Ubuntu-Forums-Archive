---
title: "Add Submenus to System&gt;Preferences"
date: 2007-11-11
forum: Ubuntu Brainstorm
---

### Post by TheForkOfJustice on 2007-11-11
We all know that the System>Preferences menu is long and often goes the whole length of the screen. I suggest adding three submenus:

Settings
Hardware
Networking

and sorting out some of the program icons into the  appropriate section. Like so:

Settings
- Appearance
- Keyboard Shortcuts
- Main Menu
- Multimedia Systems Selector
- Power Management
- Preferred Applications
- SCIM Input Method Setup
- Screen Resolution
- Screensaver
- Sessions
- Sound
- Windows

Hardware
- Bluetooth Preferences
- Default Printer
- Hardware Information
- Keyboard
- Mouse
- PalmOS Devices
- Removeable Drives and Media

Networking
- Network proxy
- Remote Desktop

You may also wish to bring the 'Screens and Graphics' icon over from System>Administration as well.

Does anyone agree with my suggestion?

---

### Post by 23meg on 2007-11-11
No. Reasons:
[list]
[*]More time to navigate
[*]Divergence from upstream
[*]Lots of overhead, since packages need to be modified and new policy needs to be set
[*]It's hard to do a good categorization; one could argue that Screen Resolution and Power Management should be in Hardware, etc.
[/list]

---

### Post by chrisccoulson on 2007-11-11
Fedora does this. I have to say, it is much nicer. 23meg: I know you argue that it takes longer to navigate through to a sub menu, but there is a tradeoff. A single layer menu takes longer to navigate as it becomes more cluttered, so you lose the speed benefit of not having sub menu's. The Ubuntu preferences menu is pretty cluttered now. I find the Fedora way of having sub menu's quicker to navigate due to this reason, as there's only a few entries in each sub menu.

I do agree though that it is hard to categorise some entries. But, the same can probably said of some applications installed in the Applications menu already. For example, should Terminal go under Accessories or System Tools? (I pick that example because Ubuntu has it under Accessories and Fedora has it under System Tools. I don't believe either way is incorrect).

---

### Post by Snowhog on 2007-11-11
One of the pure joys of Linux, is the control it affords the user. What you are describing is of course, something you can already do, assuming you haven't already! \\:D/

---

### Post by 23meg on 2007-11-11
[QUOTE=chrisccoulson]23meg: I know you argue that it takes longer to navigate through to a sub menu, but there is a tradeoff. A single layer menu takes longer to navigate as it becomes more cluttered, so you lose the speed benefit of not having sub menu's. The Ubuntu preferences menu is pretty cluttered now. I find the Fedora way of having sub menu's quicker to navigate due to this reason, as there's only a few entries in each sub menu.[/QUOTE]

You have a point. I'm aware of the tradeoff, but my argument against further grouping is the assumption that most of the time, the user knows what they're looking for when or before clicking "System". Once you know what you're looking for, you have two important cues that help you aim for it: its alphabetical position, and the icon used for it. These make navigation pretty quick, after some basic practice with the menu. 

For example, if you use "Appearance" often, you most likely instinctively plan ahead even before clicking "System" that you're going to go up in the menu after clicking and hovering on "Preferences". Or if you're going for "Removable Drives and Media", you may have the CD icon, or "some round object" as a cue in your mind, and scan the icons for it. You can also combine the two; for example, by looking for a round object around the middle of the menu.

---

### Post by TheForkOfJustice on 2007-11-11
> **Snowhog said:**
> One of the pure joys of Linux, is the control it affords the user. What you are describing is of course, something you can already do, assuming you haven't already! \\:D/

You can also move the shortcuts around in Windows ;)

That being said, editing the shortcuts in Ubuntu has a bug in it.

Shortcuts in the 'System>Preferences' directory (probably others) are duplicated in the 'Other' directory when they are moved into subfolders.  So in the end you end up with two icons:

- One in the subfolder under 'System>Preferences>Whatever'
- One in the 'Other' directory

And if you try and delete the one listed in 'Other' it ends up deleting BOTH and basically undoing all of your editing.  You will end up with a glitched menu with extra folders. You'll have to go into your ~/.local/share directory and deleting all of your changes manually so the defaults can be restored.

Go ahead and try to do manually what I have suggested in the first post.  You will notice that the 'Other' folder will appear and every shortcut you move to a subfolder will be duplicated in the 'Other' directory.

That, other than simplicity, is why I would like this to be done on the development side of things.

And while we're at it, why is there two programs that basically do the same thing?  The 'Screens and Graphics' in 'System>Administration' and 'Screen Resolution' in 'System>Preferences'?

---

### Post by 23meg on 2007-11-11
[QUOTE=TheForkOfJustice]That being said, editing the shortcuts in Ubuntu has a bug in it.[/QUOTE]

Is it reported?

[QUOTE=TheForkOfJustice]And while we're at it, why is there two programs that basically do the same thing? The 'Screens and Graphics' in 'System>Administration' and 'Screen Resolution' in 'System>Preferences'?[/QUOTE]

There are plans to consolidate them in Hardy.

---

### Post by TheForkOfJustice on 2007-11-11
> **23meg said:**
> You have a point. I'm aware of the tradeoff, but my argument against further grouping is the assumption that most of the time, the user knows what they're looking for when or before clicking "System". Once you know what you're looking for, you have two important cues that help you aim for it: its alphabetical position, and the icon used for it. These make navigation pretty quick, after some basic practice with the menu. 

The same thing could be said if it was put into a subdirectory.  Just one more step. And since there is a shorter list of shortcuts to render on each step and the list is still alphabetized, navigation may even be sped up!

> 
For example, if you use "Appearance" often, you most likely instinctively plan ahead even before clicking "System" that you're going to go up in the menu after clicking and hovering on "Preferences". Or if you're going for "Removable Drives and Media", you may have the CD icon, or "some round object" as a cue in your mind, and scan the icons for it. You can also combine the two; for example, by looking for a round object around the middle of the menu.

All you're saying here is that if they use the shortcut enough, they will know how to find it.  The same point exists if subfolders are used.  Truthfully, if they use something that often they may just want to add a shortcut to a panel or the desktop.  I also don't go by icons since they change with the theme.  I go by the general location and the name.

And the 'deviate from the upstream' argument is weak since it's only a minor configuration edit with little or no impact on the installation of other programs.  If you install Java the 2 icons it installs will still appear in 'System>Preferences'  even with the subfolders present.  No big deal.

You may as well make the same complaint with the default Ubuntu theme which differs from Debian's default.  I'm sure there are plenty of Ubuntu-specific changes to gconf that will back be up on this.

---

### Post by TheForkOfJustice on 2007-11-11
> **23meg said:**
> Is it reported?

Yep.  No action yet.

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/155620](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/155620)

> There are plans to consolidate them in Hardy.

Good. Silly bit of redundancy there :)

---

### Post by 23meg on 2007-11-11
> The same thing could be said if it was put into a subdirectory. Just one more step. And since there is a shorter list of shortcuts to render on each step and the list is still alphabetized, navigation may even be sped up!

The rendering speed isn't the bottleneck; it's the user's speed, which can be assumed to always be slower. And if there is slowness in menu rendering, which I don't experience, but keep hearing that others do, that's a bug to be fixed on its own; it shouldn't be an excuse to rearrange things.

Since a submenu puts an extra step, it slows you down. Note that you have to hover over the submenu item and wait for the new menu to pop up.

> All you're saying here is that if they use the shortcut enough, they will know how to find it. 

I'm also saying how.

> The same point exists if subfolders are used.

Not exactly. If things are divided, there isn't one single alphabetical order that you can rely on.

> If you install Java the 2 icons it installs will still appear in 'System>Preferences' even with the subfolders present. No big deal.

It* is *a big deal. If there are subfolders, it should follow that everything you install from that point onwards should have its proper place. If I install Murrine Configurator, it should go to, say, "Settings" in your scheme, not the top level. If it doesn't, that won't be professional.

---

### Post by 23meg on 2007-11-11
> **TheForkOfJustice said:**
> Yep.  No action yet.

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/155620](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/155620)

You should keep each bug report to one bug. Please edit it, and file a separate bug for the second one and cross-link them.

---

### Post by TheForkOfJustice on 2007-11-11
> **23meg said:**
> No. Reasons:
Lots of overhead, since packages need to be modified and new policy needs to be set


For some editing to the menu?? Please tell me that is an exaggeration.

Can you tell me what package has the default menu in it and what file(s) to mess with?  I've been thinking of making this change to LFC.  I can let you know how that all works out.

> It's hard to do a good categorization; one could argue that Screen Resolution and Power Management should be in Hardware, etc.


That's a valid point and I may want to change that in my plans.  Not a major one that would invalidate the idea, though.

Are there also plans to merge 'Multimedia Systems Selector" and "Sound"?  I know 'Multimedia Systems Selector' also has settings for some video functions but they could be merged with 'Screens and Graphics'/'Screen Resolution' with their upcoming merger you mentioned.

I also noticed the 'Network' and 'Network Tools' shortcuts in 'System>Administration' could be subfoldered in the 'Networking' folder too, but since they need the admin password so I'm reluctant to do anything to them.

---

### Post by 23meg on 2007-11-11
> For some editing to the menu?? Please tell me that is an exaggeration.

Of course it's not. Ideally, every package that's not installed by default and adds menu items would need to be re-told where to install their menu items.

---

### Post by TheForkOfJustice on 2007-11-11
> **23meg said:**
> The rendering speed isn't the bottleneck; it's the user's speed, which can be assumed to always be slower. And if there is slowness in menu rendering, which I don't experience, but keep hearing that others do, that's a bug to be fixed on its own; it shouldn't be an excuse to rearrange things.

Since a submenu puts an extra step, it slows you down. Note that you have to hover over the submenu item and wait for the new menu to pop up.

I always attributed the pause as a rendering issue (the list of icons in System>Preferences is a biggie after all).  People who complain about it probably have slower systems, so they can detect it easier.  Mine is 800MHz w/ 256MB RAM so I would fall into this category.

So I don't think it is a bug.

> I'm also saying how.

They can also find the shortcut by remembering what number the icon is in a smaller submenu without even looking at the names or icons. As things are now, after the 4th icon down I start to lose count and just hunt for the name from its general location if I remember the location at all. I've been using Ubuntu for awhile and I still find myself occasionally going up one shortcut at a time trying to remember which one had the utility I was looking for. Having submenus would elimininate a lot of incorrect choices and leave you with the more likely candidates.  Not to mention reducing the chances of hitting the wrong shortcut. 

I haven't been able to test this rendering hypothesis properly because of the bug I mentioned earlier.  I'll have to edit the default menu manually in order to do that.

All that being said, there is more than one way to find the shortcut and once they know where it is its an easy matter to select it.  I'm fairly certain that submenus will not affect the speed of getting to a shortcut.

> 
Not exactly. If things are divided, there isn't one single alphabetical order that you can rely on.


Incorrect. Everything on the toplevel would be organized A-Z.  Everything in each individual subfolder would be listed A-Z.  All that would matter is the order for the folder you are currently looking in.

> 
It* is *a big deal. If there are subfolders, it should follow that everything you install from that point onwards should have its proper place. If I install Murrine Configurator, it should go to, say, "Settings" in your scheme, not the top level. If it doesn't, that won't be professional.

If it is in the top level, since that is nearly empty, then the shortcut for the new program would be instantly visable and the user would have no need to browse any of the subfolders.  However, without the subfolders the toplevel would be full of so many shortcuts that you would not be able to find the shortcut as easily.

Then there's the fact that since the menu is so long now it only takes a few shortcuts to make the arrows appear and you know what a bother than can be having to scroll up and down with them to find the shortcut you are after.  Java itself installs 2 shortcuts and I'd probably be getting the arrows now if I hadn't removed my top panel.

Than there is the Accessability factor.  People with bad eyes need themes with larger icons and text. You know they are getting those arrows right away and scrolling with the arrows isn't helping them a damn bit.

---

### Post by TheForkOfJustice on 2007-11-11
> **23meg said:**
> Of course it's not. Ideally, every package that's not installed by default and adds menu items would need to be re-told where to install their menu items.

The toplevel is good enough so I do not see why any programs that aren't the default need special treatment.  I brought this up to make the default menu smaller, not for any special need for all programs to fall into some order.

Any new shortcuts that are installed would be installed on the toplevel just like they are now, and since there won't be 20-something icons in the way they will be instantly found by the user.  There's no need to make changes to where any other programs put their icons.

---

### Post by smartboyathome on 2007-11-11
> **TheForkOfJustice said:**
> The toplevel is good enough so I do not see why any programs that aren't the default need special treatment.  I brought this up to make the default menu smaller, not for any special need for all programs to fall into some order.

Any new shortcuts that are installed would be installed on the toplevel just like they are now, and since there won't be 20-something icons in the way they will be instantly found by the user.  There's no need to make changes to where any other programs put their icons.

Um... no. I would say this would look unprofessional. Not only would people be asking "Why is program XYZ not in Preferences menu ABC?", but it would also make it look like we only cared to fix the packages in the default install.

---

### Post by 23meg on 2007-11-12
> 
I always attributed the pause as a rendering issue (the list of icons in System>Preferences is a biggie after all). People who complain about it probably have slower systems, so they can detect it easier. Mine is 800MHz w/ 256MB RAM so I would fall into this category.

So I don't think it is a bug.

If something doesn't work reasonably well on a reasonably modern configuration where it would be expected to work, that's a bug to be fixed.

> They can also find the shortcut by remembering what number the icon is in a smaller submenu without even looking at the names or icons. As things are now, after the 4th icon down I start to lose count and just hunt for the name from its general location if I remember the location at all. I've been using Ubuntu for awhile and I still find myself occasionally going up one shortcut at a time trying to remember which one had the utility I was looking for. Having submenus would elimininate a lot of incorrect choices and leave you with the more likely candidates. Not to mention reducing the chances of hitting the wrong shortcut.

I haven't been able to test this rendering hypothesis properly because of the bug I mentioned earlier. I'll have to edit the default menu manually in order to do that.

All that being said, there is more than one way to find the shortcut and once they know where it is its an easy matter to select it. I'm fairly certain that submenus will not affect the speed of getting to a shortcut.

I disagree, due to reasons I've given in previous posts. At this point I think you or somebody else should make a video to compare average navigation speeds.

> Incorrect. Everything on the toplevel would be organized A-Z. Everything in each individual subfolder would be listed A-Z. All that would matter is the order for the folder you are currently looking in.

> If it is in the top level, since that is nearly empty, then the shortcut for the new program would be instantly visable and the user would have no need to browse any of the subfolders. However, without the subfolders the toplevel would be full of so many shortcuts that you would not be able to find the shortcut as easily.


> 
The toplevel is good enough so I do not see why any programs that aren't the default need special treatment. I brought this up to make the default menu smaller, not for any special need for all programs to fall into some order.

Any new shortcuts that are installed would be installed on the toplevel just like they are now, and since there won't be 20-something icons in the way they will be instantly found by the user. There's no need to make changes to where any other programs put their icons.

Again, no, that wouldn't be consistent and professional. Having stuff added to the toplevel menu when there are separate menus designated for separate functions isn't acceptable. Seperate menus would be a feature, and with such a central feature, you need to actually utilize it.

> 
Then there's the fact that since the menu is so long now it only takes a few shortcuts to make the arrows appear and you know what a bother than can be having to scroll up and down with them to find the shortcut you are after. Java itself installs 2 shortcuts and I'd probably be getting the arrows now if I hadn't removed my top panel.

For people with low resolution displays, that's a point.

> Than there is the Accessability factor. People with bad eyes need themes with larger icons and text. You know they are getting those arrows right away and scrolling with the arrows isn't helping them a damn bit.

There's truth to that; however, getting more arrows to hover over and search for stuff in regardless of whether the menu fits in the screen or not is the flipside.

---

### Post by 23meg on 2007-11-12
[QUOTE=TheForkOfJustice]
Can you tell me what package has the default menu in it and what file(s) to mess with? I've been thinking of making this change to LFC. I can let you know how that all works out.[/QUOTE]

There's no single package that has them; they get installed by different individual packages. You can use apt-file or dlocate to find out what package each file comes from.

---

### Post by Rinzwind on 2007-11-12
Oops double post

---

### Post by Rinzwind on 2007-11-12
Would it not be enough to have 1 program that scans for all .desktop files and then let's you edit them into a new menu-structure? That way anyone can make their own menu.

You insert some keywords in the program like 'games' 'tetris' and the program searches for .desktop files and shows them (it might even look into the description of the package(?)) and then let you drop these into another folder and all the .desktop files change to the new menu. 

I would love to be able to have the menu in another order for instance: 

Games 
   Board
   Tetris (yeah it needs an own group ;) )
   etc.

During Feisty I had -all- games installed and did this once by hand but it takes ages to do. I hated that ugly scrollbar so much I actually did that ;) 

Advantages:
(1) Packages don't need updating.
(2) If you do not care about it you don't use it. 
(3) Everybody happy :lolflag:

---

### Post by Burgundavia on 2007-11-12
The real fix to this issue is to merge the capplets into each other, in a more logical manner, thus having less of them. Upstream is already doing this.

Corey

---

### Post by TheForkOfJustice on 2007-11-12
> **smartboyathome said:**
> Um... no. I would say this would look unprofessional. Not only would people be asking "Why is program XYZ not in Preferences menu ABC?", but it would also make it look like we only cared to fix the packages in the default install.

Have you ever considered that NOT putting your default icons into organized subfolders is unprofessional?  Like you didn't care about a neat and ordered menu and just left the icons there sprawled out in a long list.

Then consider how rare it is for someone to install a program that creates a shortcut to the 'System>*' area of the menu. If they do install a shortcut there, whether this user is a newbie or an expert they will just be happy to have one that will be easy top find since it is on the toplevel of a much shorter, alphabetized menu. Not having it in a folder like the defaults would even be preferrable since you would find it even faster.

I believe my idea is much more professional and user-friendly.

---

### Post by TheForkOfJustice on 2007-11-12
> **Burgundavia said:**
> The real fix to this issue is to merge the capplets into each other, in a more logical manner, thus having less of them. Upstream is already doing this.

Corey

Can you elaborate on this please?  I've been hoping for some time that they would merge the gnome-control-center and capplets-data packages and then create a seperate deb for each utility, and make gnome-control-center as a seperate deb thatt will install the other utilities as dependencies (but the other utilities wouldn't be dependent on gnome-control-center so it could be removed at any time). This could permit any individual utility to be removed our replaced at any time.

I've been waiting for that since there have been problems with 'showing' the gnome-control-center shortcut in alacarte (the shortcut duplicates itself) and that once you uninstall Evolution the 'About Me' utility remains even though it becomes rendered useless without Evolution present.

Please tell me this is their plan!

---

### Post by 23meg on 2007-11-12
[QUOTE=TheForkOfJustice]Have you ever considered that NOT putting your default icons into organized subfolders is unprofessional? Like you didn't care about a neat and ordered menu and just left the icons there sprawled out in a long list.[/QUOTE]

They *are* in an organized subfolder, which is Preferences, a subfolder of System. There's another subfolder, and that's Administration. 

Just look at the default menu. It doesn't give an unprofessional impression at all.

---

### Post by TheForkOfJustice on 2007-11-12
> **Rinzwind said:**
> Would it not be enough to have 1 program that scans for all .desktop files and then let's you edit them into a new menu-structure? That way anyone can make their own menu.

You insert some keywords in the program like 'games' 'tetris' and the program searches for .desktop files and shows them (it might even look into the description of the package(?)) and then let you drop these into another folder and all the .desktop files change to the new menu. 

I would love to be able to have the menu in another order for instance: 

Games 
   Board
   Tetris (yeah it needs an own group ;) )
   etc.

During Feisty I had -all- games installed and did this once by hand but it takes ages to do. I hated that ugly scrollbar so much I actually did that ;) 

Advantages:
(1) Packages don't need updating.
(2) If you do not care about it you don't use it. 
(3) Everybody happy :lolflag:

Too. Much. Work.

Also very resource intensive if they scan for *all* desktop files.  But you do point out something: If people do not like the original place a shortcut was placed they can (and do) move it with Alacarte. Moving a shortcut that's on the toplevel *yourself* to it's *proper* folder (if it's original location on the toplevel was offensive to the user) isn't a big job. Having it installed in the toplevel by default could be described as a feature in that case so the user can find the new icon faster and then relcate it if they felt like it.

As for your problem with all those games (you installed ALL of them?!), I hope they have all been better arranged since Feisty if there was a sorting issue.  Damned if I would install *all* of them to find that one out! :shock:

---

### Post by smartboyathome on 2007-11-12
> **TheForkOfJustice said:**
> Have you ever considered that NOT putting your default icons into organized subfolders is unprofessional?  Like you didn't care about a neat and ordered menu and just left the icons there sprawled out in a long list.

Then consider how rare it is for someone to install a program that creates a shortcut to the 'System>*' area of the menu. If they do install a shortcut there, whether this user is a newbie or an expert they will just be happy to have one that will be easy top find since it is on the toplevel of a much shorter, alphabetized menu. Not having it in a folder like the defaults would even be preferrable since you would find it even faster.

I believe my idea is much more professional and user-friendly.

That is how YOU think, but others (like me) would wonder why it wasn't put int he proper folder. Also, Gnome's interface guidelines say that a user should be able to get to anything within two menus, I think. This would go against those, too.

---

### Post by TheForkOfJustice on 2007-11-12
> **23meg said:**
> If something doesn't work reasonably well on a reasonably modern configuration where it would be expected to work, that's a bug to be fixed.

All I'm saying is that the program works fine but my hardware may not be optimal for performance. So it may not be a software bug.

> 
I disagree, due to reasons I've given in previous posts. At this point I think you or somebody else should make a video to compare average navigation speeds.


Yeah, we are not going to solve this for certain unless someone does and I don't have to resources or time.  However, if less shortcuts are to be rendered as per my example, then logically it should have the shortest load time.

> 
Again, no, that wouldn't be consistent and professional. Having stuff added to the toplevel menu when there are separate menus designated for separate functions isn't acceptable. Seperate menus would be a feature, and with such a central feature, you need to actually utilize it.

You're assuming that the feature of the seperate folders is the only feature being added.  Having a new icon appear in a near-empty toplevel is also a feature because it can be found much more easier than if all shortcuts were in the toplevel.  


> 
For people with low resolution displays, that's a point.
1024x768 here and if I still had the top gnome panel then I'd be getting the scroll arrows after I installed Java. It didn't take much for me and 1024x768 is a pretty common resolution.

> 
There's truth to that; however, getting more arrows to hover over and search for stuff in regardless of whether the menu fits in the screen or not is the flipside.

They are two potential problems created by the current state of the menu that are solved by my suggestion.

---

### Post by TheForkOfJustice on 2007-11-12
> **smartboyathome said:**
> That is how YOU think, but others (like me) would wonder why it wasn't put int he proper folder. Also, Gnome's interface guidelines say that a user should be able to get to anything within two menus, I think. This would go against those, too.

1) You can find newly added programs easier with my method if they add shortcuts to the 'System>*' area of the menu.
2) After you find it you can use Alacarte to move it to the folder you believe it should be in if it's current location offend you.
3) Guidelines are just that: Guidelines.  You can do whatever you want to the menu. Don't mistake what the Gnome devs suggest as law.

---

### Post by smartboyathome on 2007-11-12
> **TheForkOfJustice said:**
> 1) You can find newly added programs easier with my method if they add shortcuts to the 'System>*' area of the menu.
2) After you find it you can use Alacarte to move it to the folder you believe it should be in if it's current location offend you.
3) Guidelines are just that: Guidelines.  You can do whatever you want to the menu. Don't mistake what the Gnome devs suggest as law.

1) Even if TO YOU it may make it easier, it won't make it look any better (as I said, either make one way standard or the other, there aren't gray areas on this type of thing.
2) Even IF you can change it, that doesn't excuse a half done standard.
3) Guidlines help organize things that should be organized (like menus). They should be taken more seriously than you are taking them.

---

### Post by 23meg on 2007-11-13
[QUOTE=TheForkOfJustice]All I'm saying is that the program works fine but my hardware may not be optimal for performance. So it may not be a software bug.[/QUOTE]

And I'm saying that I keep hearing this from people who have pretty modern configurations, so it can be something to fix on its own.

> However, if less shortcuts are to be rendered as per my example, then logically it should have the shortest load time.

My point was that as long as the render time isn't the bottleneck, it's not an argument for navigation speed. 

> You're assuming that the feature of the seperate folders is the only feature being added. Having a new icon appear in a near-empty toplevel is also a feature because it can be found much more easier than if all shortcuts were in the toplevel.

I've explained multiple times that I don't consider it a feature, but a bug. You're of course free to disagree.

> 1024x768 here and if I still had the top gnome panel then I'd be getting the scroll arrows after I installed Java. It didn't take much for me and 1024x768 is a pretty common resolution.

> They are two potential problems created by the current state of the menu that are solved by my suggestion.

As has been said, your suggestion isn't the only way to solve them, and as things stand, is a less than optimal way to solve them.

> 1) You can find newly added programs easier with my method if they add shortcuts to the 'System>*' area of the menu.
2) After you find it you can use Alacarte to move it to the folder you believe it should be in if it's current location offend you.

What you apparently don't want to accept is that this isn't how things are expected to work. If the user installs new software, it's expected that its menu entry just automagically goes to *exactly where it belongs*, not somewhere near where it belongs. If it's acceptable to throw things into the toplevel menu and expect the user to move them if they don't like it, it should also be acceptable to throw new software installed to the toplevel Appplications menu. Needless to say, it isn't, and the behaviour you suggest will be inconsistent with the way the rest of the menus work.

> 
3) Guidelines are just that: Guidelines. You can do whatever you want to the menu. Don't mistake what the Gnome devs suggest as law.

Sure, on your own system, you can do whatever you want. On a system deployed to hundreds of thousands of computers, however, it makes sense to take guidelines such as the HIG a bit more seriously.

Here's the relevant section from the GNOME HIG at [http://developer.gnome.org/projects/gup/hig/2.0/menus-types.html#menu-type-submenu](http://developer.gnome.org/projects/gup/hig/2.0/menus-types.html#menu-type-submenu) :

> 
A submenu appears when the user clicks its title, which is indicated by a small arrow symbol beside its label. You can save space on long menus by grouping related commands onto a single submenu.

**Guidelines**
[list]
[*]Use submenus sparingly, as they are physically difficult to navigate and make it harder to find and reach the items they contain.
[*]Do not create submenus with fewer than three items, unless the items are added dynamically (for example the File->New Tab submenu in gnome-terminal).
[*]Do not nest submenus within submenus. More than two levels of hierarchy are difficult to memorize and navigate.[/list]

---

### Post by sstusick on 2008-01-23
One thing that has been bothering me as of late, is the gnome menu. Can't they defragment the menu a little bit? Everything is scattered about messily. 

For example, they could also add "Screen Resolution"  "Screen Saver" and "Power Management" tabs to the Appearance menu. 

Add a "Mouse & Keyboard" menu holding the Mouse and Keyboard and universal access settings.

Fedora has the right idea: [IMG]http://www.thecodingstudio.com/opensource/linux/screenshots/scaled/Fedora%208/7.gif[/IMG]

This would neaten up the menus quite a bit and make them more intuitive. 


Just my 2 cents.

---

### Post by 23meg on 2008-01-23
I've moved this post to the thread where the same idea is discussed. Let's leave the other thread for discussion of the topics the OP has brought up.

---

