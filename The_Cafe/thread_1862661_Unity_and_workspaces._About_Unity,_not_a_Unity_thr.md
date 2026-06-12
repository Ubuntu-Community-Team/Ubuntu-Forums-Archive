---
title: "Unity and workspaces. About Unity, not a Unity thread."
date: 2011-10-17
forum: The Cafe
---

### Post by Copper Bezel on 2011-10-17
**Abstract / tl;dr version: Why does Unity at default settings have a visible workspace button but exclusively use window switching methods that ignore workspaces?**

Note that this is not a "Unity thread." On-topic posts are those that stay within the overlap on the Venn diagram between "Unity," "Workspaces," "At Default," and "Not Ranting." 

I don't understand Ayatana's understanding of workspaces. [_Neither does Ayatana._](https://wiki.ubuntu.com/Ayatana/Workspaces) I do understand Gnome's. I don't, however, want to jump to the conclusion that no one is driving the bus, that bear is driving the bus, etc., re: Unity's workspace management. Can someone explain to me how Unity *at default settings* reflects an understanding of workspaces?

**Here is how I understand workspaces. **

I've only found workspaces useful when using a configuration that keeps them as separate as possible. Gnome 2 or 3 and Compiz do this in their default upstream configurations. Alt+Tab, if there is one, ignores other workspaces, the taskbar, if there is one, ignores other workspaces, Exposé, if there is one, ignores other workspaces, and so on. In sum, *I* get to ignore my other workspaces and keep my tasks separate, so that my "work machine" can be one workspace and my "home machine" can be another and I can stuff random Chrome windows I'll need later on a third, and then jump to a fourth to edit a bunch of images and generally be messy with things. I can forget that things are open until I need them.

**Here are the features of Unity's use of workspaces that confuse me.**

First, Unity's dock doesn't ignore windows from other workspaces. It's the all-powerful workspace-independent toplevel navigator of all things "your apps." It's visible and functional in the workspace switcher, so for consistency's sake, it probably makes the most sense for all running apps to be displayed there. Slight damage to the workspace concept for me, but I understand why it's done.

Second, there's also the new application switcher that comes with the Unity plugin in 11.10. Again, for consistency, the switcher looks quite a bit like the Unity Launcher, and (I'm guessing) for consistency, it also shows windows from all workspaces, thus, ignores workspace position. Okay, consistency is consistent.

But consistency means that neither of the ordinary methods of window switching respects workspaces, so I begin to wonder why there's a big, visible Workspace button on the Launcher, and why Unity ships with a grid of four workspaces by default. They're actually the same question - reduce workspaces to 1, and the button niftily disappears. But it doesn't *ship* that way.

**My guesses to justify the button are sparse.**

There are a couple of use cases I can see for the Workspace Switcher and its button for a user using the default configuration, but they seem too cumbersome to really serve a purpose.

Exposé (through Scale) is still workspace-specific, and there is a default keybinding for this. If someone finds it, and that someone is a keyboard junkie, I can see an argument for workspaces here, but a tiny one. A person is no more likely to know about this feature than to edit the default settings, and Scale is still primarily a mouse-driven switcher, so invoking it by keyboard is going to make it a clunky process in any case. It's not a core component of the UI experience.

The workspace switcher itself might be an explanation. In Unity 2D, particularly, I understand that it spreads the windows on each workspace, much like KWin. That means organizing windows in boxes and selecting them in a spread of tiny Exposé'd desktops. But Compiz doesn't support this feature.

In 3D, then, switching between tasks using the workspace switcher would make sense for non-maximized windows, but once you throw some maximized windows in, there's no real difference between using this and, say, Scale, except that you're only seeing the windows that happen to be on top for each workspace. Since the Launcher is still functional, you could go to the Workspace switcher and then click an app icon to bring that to the surface, then select it, but that seems like adding an extra step to the window spread you'd get from clicking the same icon without invoking the workspace switcher in the first place.

**Again, I'm not bashing Unity or inviting you to do so.**

My question is not why Unity doesn't emphasize workspaces as a part of the default experience, or why the functionality has been retained at all. I understand both of those things. Anyone with the time to poke through CompizConfig can find useful things for workspaces to do, and if workspaces aren't a core element of Unity's UI, well and good. *But there's that damned button there* leading to a default grid of four workspaces, which seems like a disjoint. That is, those settings are configured by default to hint at the existence of workspace management, but user configuration is required to make any use of it, *so far as I can tell*.

So, again, with as little Unity ripping (or workspace ripping, for that matter) as possible, can someone give me a quick explanation of what Unity's workspaces are meant to do? I'm not assuming that it isn't awesome; I just don't know what it is. What's the intended Zen of Unity workspaces?

And again, this is not a comparison thread, a rant thread, or a support question. I already know that Gnome 3's Shell uses workspaces much more in the way that I do than the way that Unity does, that other environments entirely use other methods or copy Gnome 2 directly and so on and so on. I know that Compiz can be configured to do other things and doesn't need to be left at defaults. 

What I'm curious about is what that way in which Unity uses workspaces at default *is*. Speculation welcome.

---

### Post by screaminj3sus on 2011-10-17
I personally like the alt-tabs behaviour regarding workspaces. Gnome-shell's switcher works the same way and gnome-shell has a much more workspace focused design...

I use workspaces just so I don't have a lot of windows cluttering my desktop and to keep things orginized, but when I bring up alt-tab I want to see all my applications. I don't want to memorize which workspace I had what in. I tend to use workspaces for fullscreen windows I keep open, like my media player.

However an option to have the switcher respect workspaces in ccsm would be a good idea, people have different preferences. Perhaps you should try bringing this up on the ayatana mailing list :)

---

### Post by gsmanners on 2011-10-17
> **screaminj3sus said:**
> I use workspaces just so I don't have a lot of windows cluttering my desktop and to keep things orginized...

Same here. I sometimes drag windows between workspaces, but I always configure my panel to show all the windows. It's just more convenient and wastes less time that way. It may be more distracting, but distractions aren't necessarily a bad thing.

---

### Post by Copper Bezel on 2011-10-18
[QUOTE=screaminj3sus]Gnome-shell's switcher works the same way and gnome-shell has a much more workspace focused design...[/QUOTE]
Well, that's an extension, remember.

> However an option to have the switcher respect workspaces in ccsm would be a good idea, people have different preferences. Perhaps you should try bringing this up on the ayatana mailing list :)
Frankly, given that the feature is already present in every other application switcher, it's not as if they don't know about it. = P But I'm not using Unity myself in any case, so it doesn't matter whether it makes sense to me. I'm mostly just curious to know what workspaces really add to this style of window management (so I appreciate the thoughts on that thus far.)

---

### Post by Larkspur on 2011-10-19
> **Copper Bezel said:**
> I don't understand Ayatana's understanding of workspaces. [_Neither does Ayatana._]("https://wiki.ubuntu.com/Ayatana/Workspaces")

"Workspaces have existed in (basically) their current state for the entire duration a long time"?  Geez,  Ayatana, it's not as if you've got reams of text to edit there.

(A caveat: as your link shows, this is all (unfocussed, meandering) speculation.  I left out the multiple "IMHO"s to try and keep this as short as possible.  Also, I failed to keep this as short as possible).

Basically, the workspace switcher allows a different level of magnification to the launcher bar (as you imply in your post, switching between tasks), and is there to introduce the possibilities of workspaces (by making the new user aware of them and allowing a quick way to interact with them) but the launcher bar *partly* ignores workspaces by design, and the alt-tab switcher does so because it replicates the bar.

Less basically: the workspace switcher is there to allow you to allot windows to workspaces, create tasks or different contexts, and switch between.  That is the only way a default Unity deals with them head-on. The launcher bar is "aware" of workspaces, since it moves the user to the workspace the window is on, and not the window to the workspace that the user is on (which is what you might expect if it ignored workspaces entirely). 

However, the bar cannot respect workspaces when it comes to displaying launchers because it needs to show you all active programs, as it is designed to (eventually) be one of the main ways non-focussed programs interact with the user (we see this already in the launcher indicators for Thunderbird, Firefox, Update Manager, etc. - the bar is how they draw attention to themselves, whichever workspace the user is on).

The alt-tab switcher is a compromise in design; Ayatana seem to have had problems using anything other than a prettified application switcher - you'd think that they would use the launcher bar as the switcher (the icons are large enough), but that causes a few functional and programming issues.  For example: if a user ends up having a large amount of launchers, then you can't guarentee that the active ones (the ones they are going to alt-tab through) are close together, or not collapsed at the bottom, which could end up a mess.  The alt-tab switcher allows you to bunch active programs together in one place, but since it has to follow the capacity of the launcher bar (i.e. show all windows, otherwise it would be inconsistent) it doesn't respect workspaces either.

But why "inconsistent"?  Why not separate the bar and the switcher?  Well, ignoring the obvious simularity of appearance (and therefore implied function), it's clear that Ayatana have thought a lot about mirroring mouse and keyboard function: for every way of interacting with Unity by mouse, there is almost always a way by keyboard.  Therefore, if the Thunderbird launcher tells you a new email has arrived (and Thunderbird is on another workspace), there must be a keyboard surrogate for a mouse click on the launcher (to move to Thunderbird), but Unity can't depend on Thunderbird being in the first 10 spaces on the bar, hence an alt-tab that ignores workspaces.

None of that explains why Scale doesn't respect workspaces by default, but there you go.

---

### Post by Rubykuby on 2011-10-19
I read the thread, but I didn't really get the question asked, so I may really miss the point here. Regardless, my two pence.

I don't think there's anything wrong with the workspaces as they are. They're fully interactive with one another, easy to switch to and from (I'm using keyboard to switch between them, mainly, do note that) and work like a workspace should. This might be just me, but the only desktop environment I've found that supports dragging a window halfway through the side, then switching workspace and dragging it completely into the new workspace is Unity. I believe this is a really cool and interactive feature. Then again, I haven't tried some other DEs (Gnome 3 just won't work, as much as I'd have loved to try it).

But I don't believe that the way workspaces I think were originally invented don't function on modern desktops. Nowadays, you don't regularly lock off a whole screen with bibs and bobs to do something entirely different on the other. Do note that this is my experience, but I've got a browser running in one workspace, a 3D application in another. And with some luck, chatting and the like in another. I use all three workspaces extensively and simultaneously, but like the cleanliness Ubuntu/Unity offers as in not having a single screen filled with tons of windows, but have them spread out over workspaces.

That's how I'm using workspaces right now, and I can't see the design flaw for the way I use them. People who deliberately separate workspaces and don't work on them simultaneously, however, might not like the current design as much. I guess that's what I'm understanding, do correct me if I'm wrong.

---

### Post by Copper Bezel on 2011-10-19
Larkspur, that seems accurate. I guess workspaces can still serve a purpose in that scheme, but mostly just to provide a "clean desktop." In the case of something like the media player screaminj3sus mentioned, it seems like something similar to minimizing.

Unity doesn't make much use of Scale (except through the Launcher) so it's not surprising that it doesn't really fit into the scheme. I'd imagine that if it *was* used, it'd be invoked through a Launcher item and use the new orange selection outline to match the Alt+Tab. 

[QUOTE=Rubykuby]That's how I'm using workspaces right now, and I can't see the design flaw for the way I use them. People who deliberately separate workspaces and don't work on them simultaneously, however, might not like the current design as much. I guess that's what I'm understanding, do correct me if I'm wrong.[/QUOTE]

Yeah, that's roughly it.

For my use case, I just tend to find that for any one task, I'm likely to have multiple windows up. If I'm editing a batch of images, they're likely to all be stacked up, with maybe a file manager running on that workspace as well. Then I might be working with documents and need a couple of different LibreOffice windows or text editors up and a .pdf viewer or two, etc. If I need to look something up online in the middle of that, I'm more likely to open a new browser window than jump back to another workspace where I have a browser running and open a new tab. I just couldn't stand having all of those things cluttering up my Alt+Tab. So without separated workspaces, I'd find myself closing things I might be getting back to thirty minutes later, whereas with this style of workspace management, I'd just leave them open in the interim.

I will say that I don't see the relevance of "modern desktops" or "nowadays." Do you feel that people have fewer windows running at a time now than they might have a few years ago?

Edit: Missed a bit there.

[QUOTE=Larkspur]However, the bar cannot respect workspaces when it comes to displaying launchers because it needs to show you all active programs, as it is designed to (eventually) be one of the main ways non-focussed programs interact with the user (we see this already in the launcher indicators for Thunderbird, Firefox, Update Manager, etc. - the bar is how they draw attention to themselves, whichever workspace the user is on).[/QUOTE]
And yeah, I understand this bit, and it's quite a better way of doing things than using the system tray for these things. The more the items can become interactive widgets for their applications, both conveying status information and taking commands through quicklists, the better.

---

### Post by krapp on 2011-10-20
Yep, window and workspace management is confusing in Unity, and probably its biggest flaw. The cries about the missing task list are ultimately misplaced.

I like Unity because of how much information it puts into its panel, but I ran back to Openbox because it's a lot easier to dictate window actions in one config. file than to make sense of how Compiz and Gnome are splitting up the keybindings. The default settings are preposterous.

---

### Post by Copper Bezel on 2011-10-20
I'm not even sure that it's a glaring flaw, though. Unity just doesn't seem to use or need workspaces. It would certainly become unwieldy with 10+ apps running, but anyone used to using workspaces could simply enable one of the other existing Alt+Tab options or Scale and so on. It's just that in the default experience, the workspace button seems about as weird as having minimizing enabled would have seemed in Gnome Shell, like a vestigial bit that hasn't quite been rethought as a part of the overall experience.

As it is, it's a bit like putting mirrors in the kitchen to make it seem larger. And I guess there's nothing wrong with that, per se.

The task list is another thing. I do think we might have heard a *little* less of that if the window captions in Scale (and thus in the Launcher's window spread effect) weren't inexplicably broken in the Compiz rewrite, particularly while their equivalent was simultaneously being implemented in Shell's spread effects. Not to troll my own thread with a much-repeated Unity complaint, but I'm getting a little sick of batting around well-nigh-identical LibreOffice document window previews trying to figure out which is which.

---

### Post by justynbutler on 2011-10-20
Copper Bezel, you've expressed my own confusion perfectly!

It does seem contradictory that there are multiple workspaces configured by default yet Unity is being designed to effectively ignore them.

The new Unity switcher is designed around the idea that people will choose a window in an application-driven way. You think of the application that you'd like to use and you select it (via the launcher or the switcher). Now you are using your application - if you need a different window of that application, select it with alt-`. It is geared towards using one application at a time.

This approach makes workspaces obsolete, since they are only of use for either/both of the following:
1) Grouping of multiple related windows.
2) Locating windows spatially - to find a particular window the user looks to where they left it, e.g. bottom left workspace.
In place of (1) Unity imposes a specific way of grouping windows: by application.
Obviously (2) is not used if the user is selecting the window by application instead.

I would say that Ayatana needs to decide either to drop the idea of workspaces (by default, anyway) or to specifically allow them as a "parallel" workflow.

If the latter option then more functionality needs to be enabled by default, particularly in the area of the switcher. My personal preference (as someone who thinks workspaces are useful and should be kept) is for a new keybinding to be created to select a window (rather than an application) on the current workspace. That is, the old behavior on new keys.

I think ctrl-alt-tab is perfect for this because it fits in perfectly with the use of ctrl-alt-[arrow] to switch workspaces.

In such a workflow:
User has grouped windows into workspaces. They wish to type in a window on a specific workspace.
They press ctrl-alt-[arrow] and move to desired workspace. Then ctrl-alt-tab to select a window on that workspace. Ideally they can do all this without releasing ctrl-alt inbetween.

I have proposed this in a bug report here: [https://bugs.launchpad.net/unity/+bug/863399](https://bugs.launchpad.net/unity/+bug/863399)

I also brought up the fundamental workspace confusion on the Ayatana mailing list, but have yet to receive a response: [https://lists.launchpad.net/ayatana/msg06678.html](https://lists.launchpad.net/ayatana/msg06678.html)

---

### Post by gsmanners on 2011-10-20
> **justynbutler said:**
> ... since they are only of use for either/both of the following:
1) Grouping of multiple related windows.
2) Locating windows spatially - to find a particular window the user looks to where they left it, e.g. bottom left workspace.

Or 3) Hiding unrelated windows. <-- not the same as 1)

It's a subtle but important distinction.

---

### Post by justynbutler on 2011-10-20
> **gsmanners said:**
> Or 3) Hiding unrelated windows. <-- not the same as 1)

It's a subtle but important distinction.

I disagree, that is exactly what minimization is for. Otherwise my next question would be: what is the point of minimization?

---

### Post by gsmanners on 2011-10-20
> **justynbutler said:**
> I disagree, that is exactly what minimization is for. Otherwise my next question would be: what is the point of minimization?

Minimizing could also be termed iconifying or whatever. The point is that you want the window off the desktop, but you still want to keep an eye on what the application is doing or you want to be reminded that it exists or maybe some unknown reason that only the user knows.

This is thing I don't really understand. There are a vast number of desktop arrangements, and we can only guess what their purpose is. Why even bother trying to deconstruct every possible purpose?

---

### Post by Copper Bezel on 2011-10-20
Because that's what Ayatana is doing, and because Unity emphasizes the default experience, so anything that's in that default experience needs to have a purpose you could explain to a new user (or, better, that you wouldn't have to explain.)

I wish I'd done some searching on this and found that bug report before posting, but thanks for bringing it in, justynbutler. It looks like all the relevant issues have been brought up there, but we'll see if there's anything relevant to add to the mailing list item. I'm not convinced that adding yet another keystroke to the already quite complex Alt+Tab is necessary. 

In the ideal, if workspaces are to be retained at all by default, I *think* I'd want to see a spatial window switching method worked in alongside the application switching methods - a use of Scale by default likely as another Launcher item and, though this would likely be absurdly complex to implement, a modification to the Workspace Switcher Expo screen that would spread the windows on each workspace, as in KDE. Instead of trying to jam one system into the other, just separate them completely.

---

### Post by justynbutler on 2011-10-20
Mark Shuttleworth has weighed in to the bug report at [https://bugs.launchpad.net/unity/+bug/863399](https://bugs.launchpad.net/unity/+bug/863399), also mentioning this thread.

He has clarified that the intended behavior of the Unity launcher and switcher is for their actions to be restricted to the current workspace, but that this has not yet been implemented.

This clears up the issue posed in this thread.

---

### Post by gsmanners on 2011-10-20
Interesting.

> Among many other changes we'd like to see in Workspaces:

 * Alt-TAB should only switch between apps on the current Workspace
 * Clicking on a Launcher icon for an app running elsewhere but not in
the current Workspace, which knows how to have multiple windows and
create new windows, should create a new window in the current Workspace

Nice. I like these ideas.

---

### Post by Copper Bezel on 2011-10-20
Well, I'm quite happy with this, obviously. = ) And a neat perk is that in the Workspace Switcher, selecting any workspace would reflect what apps presently have windows on it in the Launcher itself. Very cool; I look forward to seeing this implemented.

I particularly like the second feature mentioned by Shuttleworth. I find it very useful in DockBarX now.

---

### Post by Bazon on 2011-10-22
The workspaces issue is exactly the thing which makes unity unusable for me.

I'm a teacher, and so I'm used to have an ordering in context by workspaces:
workspace 1: private
workspace 2: school general
workspace 3: physics - middle class
workspace 4: physics - high class
workspace 5: mathematics - middle class
workspace 6: mathematics - high class

The things I need recurring or I'm working with momentary are always opened on the matching workspace.
And when I'm on that workspace, everything I need is just one click away in the taskbar.

With unity, that's impossible: That application entered approach is just wrong for me. For example, I always have many pdf documents open on all workspaces. Clicking on the evince icon in the launcher just **destroys** that order.
Also, selecting a pdf document by a smaller screenshot just as in scale/exposé is much harder than just selecting it by windowtitle in the taskbar.

So I also really wonder what the use of workspaces in Unity should be, for me, the workspace concept is just broken in unity. 

Maybe the developers want workspaces just for a clean view with only one window not minimized? My old trick to achieve that - use the "show desktop" function and then only restore the window I need - doesn't work any more in 11.10: Clicking on the launcher restores ALL windows:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/878293](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/878293)


P.S.:
I'm on Xubuntu+Compiz and Lubuntu (on netbook) since 11.04, I only look at unity occasionally.

---

### Post by Copper Bezel on 2011-10-22
I take it you missed the link.

[QUOTE=Mark Shuttleworth]The Forums thread at [http://ubuntuforums.org/showthread.php?t=1862661](http://ubuntuforums.org/showthread.php?t=1862661) is
essentially correct - the relationship between Workspaces and the rest
of Unity is inconsistent. That's simply because we have not yet got to
implement Workspaces the way we'd like, and what's currently shipping is
the Compiz Workspaces plugin bolted alongside the rest of Unity.

Some pieces are already in place, for example, the Launcher
distinguishes between apps running on this workspace, and other workspaces.

Among many other changes we'd like to see in Workspaces:

 * Alt-TAB should only switch between apps on the current Workspace
 * Clicking on a Launcher icon for an app running elsewhere but not in
the current Workspace, which knows how to have multiple windows and
create new windows, should create a new window in the current Workspace

I've cc'd John Lea and Stewart Wilson who are the right folk to lead
further discussion.

Mark[/QUOTE]

For now, the workaround for folks like you and me is to use Gnome Shell. = D

---

### Post by Bazon on 2011-10-22
That's indeed good news, hope they get it soon! :-)

---

### Post by castrojo on 2011-10-26
This is fixed in trunk! \o/

---

