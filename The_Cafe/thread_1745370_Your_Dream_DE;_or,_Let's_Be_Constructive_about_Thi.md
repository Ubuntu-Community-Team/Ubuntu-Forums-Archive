---
title: "Your Dream DE; or, Let's Be Constructive about This, a TL;DR."
date: 2011-05-01
forum: The Cafe
---

### Post by Copper Bezel on 2011-05-01
There's a fair bit of yay and nay going on for Unity, Gnome Shell, and most of the alternatives. Still, I can't imagine that any UI is perfect for any one person. What would your dream DE UI look like, and how would it handle?

This isn't meant as a serious "Unity suggestions" thread or anything of that sort, and for that matter, it's not about Unity; start from any UI or DE you like. What changes would you make? What features matter to you?

I've been rather obsessively tweaking my own interface lately. I'd been using Gnome with Cairo Dock for quite some time, but after being introduced to Avant Window Navigator, DockBarX, Synapse, and Compiz Standalone (in that order,) I've been getting used to a different way of getting around my desktop. Since my netbook is my primary machine for both work and play, it needs to be equally good for plugging into a projector and putting on a presentation, browsing in bed, and pulling up YouTube clips to show to friends while drunk.

Right now, it looks like this:

[[img]http://dl.dropbox.com/u/17749392/Screenshots/detopic-thumb.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/detopic.png)

It's an abstraction, of course - no amount of time or frustration saved could come close to the amount of time spent tweaking - but that's why it's a hobby. = ) There are three interfaces I'd really see as good models for useful parts for a dream UI: Unity, Windows 7, and a Gnome brainstorm concept I ran into recently.

I was fairly impressed with the Unity workflow but found Unity itself rather limiting in certain ways, and the UI just looks cluttered to me. Still, the general shape of it makes sense, and the lefthand dock is *incredibly* ergonomic once you get used to it.

Although the drawbacks are fairly obvious, I'm also fairly impressed with what Windows 7 is doing with application jump lists. I understand that Windows Phone 7 has some similar features, offering app notifications on their respective icons. If we're doing this dock thing, I'd like to see some of that functionality come into play in desktop Linux. 

Alternately, I love the [_Clever Windows concept by Crantisz_](http://www.omgubuntu.co.uk/2009/06/clever-windows-better-than-gnome-3/), and if you haven't seen the video, check it out; windows cascade automatically so that the tltlebars remain visible at all times, clicking the desktop brings up a smart little launcher, and hovering the top edge of the screen allows the user to "peek" behind maximized windows. The dock is only used for minimized windows, which are simply dragged into it by the title bar, and minimized windows, being "stowed" in the dock, always follow the user to the present workspace, which makes sense to me. I think, though, that especially on small screens, all that window cascading and the always-visible top panel would really become a space problem if the active window isn't maximized, and it could still become difficult to find a particular window at the bottom of the pile or on another workspace.

Considering these, and after having [a discussion with JDShu](http://ubuntuforums.org/showthread.php?t=1728574&page=7) (beginning at #64) about Unity's and Gnome Shell's respective methodologies, I've had a few thoughts on the actual rules and principles I'd like a UI to follow.

**In my dream UI, nothing would ever require the keyboard and mouse at the same time, but the *behavior* would stay the same for any feature that works with both.**

I think it's a good assumption that elements of a UI should retain some consistency whether invoked from the keyboard or from the mouse, but no basic launching or window management function should *require* both. Clicks should invoke clickable things; keystrokes should invoke tabbable things.

If I'm typing, I want to launch, close, and switch tasks from the keyboard. If I'm too drunk to type, it's rather the reverse. More on this below, on Synapse and on task switching.

**In my dream UI, "instant" access to places and applications would mean *instant*.**

I use Synapse to launch anything that isn't pinned and Thunar from the dock to access bookmarked locations. Thunar is nice because it launches instantly (to a "catchall" folder) making it like a desktop folder applet that has bookmarks and that I can Alt+Tab to. I generally have one open per workspace I'm using, pointed to a folder relevant to the task I'm at.

Synapse can be called from the keyboard with Super+Space, but I can also just click any empty desktop space to call Synapse already navigated to its mouse-friendly, scrollable recent applications list.

I set up both of these things after seeing the Clever Windows demo. What I really want is the launcher from the Clever Windows demo.

**In my dream UI, docks would be for applications. Not widgets. Not windows. Not launchers.**

I'll start this with what a dock isn't. I've really come to feeling very strongly that panels need to be reduced as much as possible, and after the recent discussion with JDShu I cited, I don't feel that Unity's system tray is really very well thought out. I think there should be some fairly strict rules for what appears in a system tray; I think of it as an area specifically for daemons (*exclusively,* non-windowed applications only) that require *some* interaction from the user and can return meaningful information through status icons. The MeMenu and Rhythmbox integration that exists in Ubuntu now muddies the distinction between dock and systray. Ideally, it's four to eight little icons in the corner of the screen that stay out of everything else's way. AWN provides this quite peaceably in my present rig. 

In the dock itself, I really want to see dock icons and dock helpers move in the direction of Windows 7's pinned apps or Phone 7's app widgets. I'm presently using  DockBarX in my lefthand AWN panel, and right now, I can right-click an application, running or no, and choose to open a recent document or create a new one, or I can drag a file onto a dock app to open with that application; hovering the Rhythmbox icon gives me media buttons to pause and skip. 

I'd like to see more of this, though; I think *this* is where the MeMenu functionality should happen, for instance, as a Helper function for Gwibber or Empathy's launcher. Ditto for Transmission, Tomboy, Skype, and others. Converging from the other side, in a dream universe, Opera's speed dial list or Firefox's history could be pulled up from the dock icon as well. The whole idea of using a pinned or running app's icon as a little widget for interacting with its basic functions in absence of the window itself is a good one, I think. 

With the centrality of the dock, I think it makes sense for it to be visible at all times, so that the click targets are always easy to find. Naturally, it also needs to auto-hide, to save pixel space. AWN's "transparency" hide, which reduces the dock to a transparent overlay that doesn't interrupt clicking on the window below it, is an *incredible* solution to an insoluable problem that I'd like to see implemented elsewhere. Hell, everywhere.

**In my dream UI, spatial organization and consistent behavior would be paramount.**

For window and workspace switching right now, I'm using the Ring Switcher, Scale, and Expo, with the former two set to ignore other workspaces and the latter two set to hot corners. The hodge-podge of features not really meant to be used together starts to show here.

For consistency with Scale, I'm using the Ring, set to not show minimized windows (stowed, remember,) but I'd really like something like Scale to just work from the keyboard. An integrated task switcher could look like Scale and simply pull the presently selected window slightly for tabbing through, sort of like the Static Switcher blown up to full screen. Captions would naturally be provided, for distinguishing similar-looking windows.

In my present setup, Scale is set to the upper left hot corner, and it's intuitive enough to nudge "behind" a maximized window to pull up everything it's covering. However, this interferes with the location of the close button, and I frequently unmaximize a window before closing it for this reason.

An upper-right hotcorner for the workspace switcher makes intuitive sense to me, and it doesn't conflict with anything; with an infinite target size, it's also as quick to get to as Unity's workspace button, and it doesn't *move.* Having a different wallpaper for each workspace (via Compiz) dovetails nicely with using Thunar as a desktop folder widget; visually and functionally, each workspace is doing its own thing, and it's easier to keep track of things.

Compiz's Expo, however, just isn't as nice as Gnome Shell's workspace view or KWin's Grid, both of which "Scale" each workspace's windows so that all mapped windows presently open are displayed on the screen without overlapping. KWin's grid is particularly spatial, a real toplevel task switcher, and it provides workspace-specific wallpaper and dynamic workspace adding. In my dream UI ... well, actually, KWin's Grid is pretty much a dream already. Compiz just needs to steal it so I can use it. = )

And now for the petty snark:

**In my dream UI, Aero Snap knockoffs would stop being Aero Snap.**

Dragging a window to a right or left edge already means something in Linux. Double-clicking a titlebar already maximizes a window, so maximizing a window on dragging to the top edge doesn't add any convenience or functionality. The one really nice feature of Aero Snap that doesn't duplicate anything else is double-clicking the upper resize handle to maximize the window vertically, and since it's not possible with the present decorators, it isn't implemented. [size=1]So if any gods or developers are listening, can someone, please, pretty-please, make dragging a window to the top edge do this? I'm already using an edge click binding for it, but that conflicts with Fitts's law concerning my systray and window controls and it's a workaround and I don't like it and it would just make sense if they were to actually make use of this thing that Gnome does that Windows ripped off anyway, dammit, but they're doing it better now and I want it back and....[/size]

**In my dream UI, there would be a maximize animation other than the one that comes with Compiz's "wobbly windows" plugin.**

In my dream UI, there would be a maximize animation other than the one that comes with Compiz's "wobbly windows" plugin.

So what's your dream UI? What workflow makes the most sense to you? What desktop metaphors or sensibilities or rules are most important? Where do you want to put your stuff?

---

### Post by Jesus_Valdez on 2011-05-01
I just want some nice Gnome-shell theme.

---

### Post by pookiebear on 2011-05-01
kde's shiny
with gnome 2's menu and panel
but faster than openbox.

---

### Post by aaaantoine on 2011-05-01
Right now?  I'm thinking Gnome Shell with better font management.

---

### Post by el_koraco on 2011-05-01
I've tried putting docks on the side, and can't get used to it. It's not just a question of muscle memory, but I use the left side to move my mouse out of the way when I'm in a maximized window. This is why I actually like window controls on the left hand side, it's faster to reach them. 

The best that I've seen so far is the mock up for Elementary's Pantheon dekstop. It borrows heavily from both Unity for window management with the new generation docky on the bottom and the indicators, as well as with Shell's Applications left hot corner, but in a much better way - similar to OSX lion's launchpad. 

I'd like to see the porting of Windows 7 jump lists as well as the KDE smooth task previews into the dock, as well as fusing Expo with Grid view, just like you said - my right upperhand corner also invokes Expo. My down left corner Invokes the Compiz window presenter, which I agree is not as refined as Kwin's. 

Adding to that, I'd like to see a port of Plasma's Activities and widgets to Compiz. In Plasma (the best desktop right now, anywhere), you can combine separate widgets and styles for each virtual dekstop, and you can also add "Activities" - each new activity starts as a blank slate, which can be molded according to wishes. So you can basically have two or more computers in one. 

As for animations, let them be unintrusive, the quick fadeout ones are the best compromise between some eye candy and not being sick from wobbling. Although, Kwin's Magic lamp effect is pretty nice. 

Man, I need to get laid.

---

### Post by Copper Bezel on 2011-05-01
aaaantoine: Sorry, I should have linked [your thread]("http://ubuntuforums.org/showthread.php?t=1741839"), too. Hell, I even referred to it, but never linked it.

I was actually curious to have your input on this, though. You've put some thought into this, lately, and your Unity suggestions make a lot of sense to me.

Edit: Simultaneous post. Get back to el_koraco's in a moment.

---

### Post by Timmer1240 on 2011-05-01
Im running it good old gnome 2.30.2 do you need anything Better?Ive tryed Kde didnt care for it XFCE shows great promise I could live with that I guess Im old fashioned!You just cant beat Apps Places And System its so darn easy!Openbox it kinda cool too for the clean desktop look

---

### Post by Random_Dude on 2011-05-01
I love how easy to customize gnome is. However, as I mess around with other window managers, I'm starting to find the default ubuntu very slow.
I love the look of openbox with a nice tint2 panel and there are some tools available to make the customization easier.
I love awesomeWM, the way it handles the windows and how you can navigate using keybinds. However, customizing it is a huge pain. I don't know Lua, so I've gave up on trying to do it after wasting a lot of time seeing if I could deduce some stuff.

I've been jumping between Openbox and Awesome lately. I'm beginning to get used to openbox, especially after managing to put dmenu in openbox using [urukrama's tutorial]("http://urukrama.wordpress.com/2008/02/07/using-dmenu-in-pekwm-and-openbox/"). :)

So the perfect one for me would probably be AwesomeWM with an easier way to customize it and a better menu.

Cheers :cool:

---

### Post by Copper Bezel on 2011-05-01
> **el_koraco]I've tried putting docks on the side, and can't get used to it. It's not just a question of muscle memory, but I use the left side to move my mouse out of the way when I'm in a maximized window. This is why I actually like window controls on the left hand side, it's faster to reach them. [/quote]
A dock on the bottom also has the perk of having more space for more running applications, which is a serious scalability concern. And there are use case arguments for a dock on the right side, as well (as some users find a highly visible dock distracting.) I do think that dock on the left is the sanest default in that the left pane is generally the toplevel navigation deck, for instance, in web design and file management. Still, I agree that Unity's decision to lock the dock down on the left is a bad one.

>  The best that I've seen so far is the mock up for Elementary's Pantheon dekstop.
It does look like a nice mix of Unity and Shell features, and it's potentially the simplest and lightest of the three.

I'm not conviced by the ever-present top panel, though. It's the same problem as in Shell and the Clever Windows demo - it's a lot of pixels for a clock, isn't it? I understand the need for whitespace, and it is a very narrow panel, but I still think there's a better solution than this one (or Unity's.)

> It borrows heavily from both Unity for window management with the new generation docky on the bottom and the indicators, as well as with Shell's Applications left hot corner, but in a much better way - similar to OSX lion's launchpad. 
I'm not conviced that a wall of tiles is a reasonably accessible way to navigate a list of programs. Slingshot is overkill. I'd rather see a single-column list of icons *with captions and descriptions,* broken into categories with a navigation row at the top resembling Unity's. Slingshot's argument of "muscle memory" for using pages is also highly dubious, because scrolling is still a faster way to move from one to another, particularly when using a mouse or trackpad. I also think that the, say, six most used apps in a category should be the first on the list. 

For all those reasons, I'd start with Synapse and build from there. I guess it sounds a little traditionalist, as what I'm describing more resembles the old Main Menu than the Dash-Activities-Slingshot concept, but I really feel that all of those provide a rather bewildering display of poorly-identified icons, and Slingshot's full-screen mess is particularly troubling said:**
> I'd like to see the porting of Windows 7 jump lists as well as the KDE smooth task previews into the dock, as well as fusing Expo with Grid view, just like you said - my right upperhand corner also invokes Expo. My down left corner Invokes the Compiz window presenter, which I agree is not as refined as Kwin's. 
DockBarX does previews, but I turned them off after playing with its Opacify feature, which makes a hovered group or list item the only visible window on the screen, much like Aero's peek. I don't know that I like anything that that presents the possiblity of representing the same window twice within the workspace. Simplicity is a big thing for me.

And yeah, I'm really very impressed with KWin's window and workspace selectors over Compiz's, which is really too bad, given how many features Compiz has that KWin doesn't. KWin is, after all, designed to depend so much on KDE, where Compiz is a decent window manager in itself for any DE.

> Adding to that, I'd like to see a port of Plasma's Activities and widgets to Compiz. In Plasma (the best desktop right now, anywhere), you can combine separate widgets and styles for each virtual dekstop, and you can also add "Activities" - each new activity starts as a blank slate, which can be molded according to wishes. So you can basically have two or more computers in one.
I've never played with that. That's extremely nice and would help a very great deal in keeping tasks organized.

> As for animations, let them be unintrusive, the quick fadeout ones are the best compromise between some eye candy and not being sick from wobbling. Although, Kwin's Magic lamp effect is pretty nice. 
Yeah, I'm using variations on Glide and Fade effects exclusively, although I did tweak Razr for my minimize animation - with the tesselation turned off, it distorts the window slightly and flings it in a set direction, so that the window doesn't shrink or angle toward its dock icon. It just flutters off in the direction of the dock, then flutters back.

> Man, I need to get laid.
Ditto. = /

---

### Post by dyltman on 2011-05-01
I kinda jump between the option of a minimalist manual tilling window manager like subtle and a complete and cool DE. 

But what I want in a DE is that everything looks integrated and that everything feels responsive like for instance if you hover a button it gets highlighted, not a 1 sec delayed and then insta highlight but rather a smooth highlight animation. I also find it important that it's unique and interesting but still productive which means that I ruled out kde (I've tried it so many times, I just hate it however). So far unity has prolly came closest to my favourite DE with subtle in second place.

---

### Post by el_koraco on 2011-05-01
Oh, no, you didn't just splice my post into segments. God, who ever came up with that should be shot. 

As for dock positions, they are a thing of preference. I think the Unity design team was either worried that putting a dock at the bottom would be "copying" whomever, or the work was just too much to fiddle with adding options to the launcher. Whatever the case, it should be movable. 

Spatial vs listing. The spatial orientation type is preferable IMO, simply because of the speed. With multitouch trackpads and mouse gestures, you are much faster in navigating through spatial lists than vertical ones, and you have all your applications listed. This takes care of the mouse part. Gnome Shell is superb with the keyboard. I think that the Slingshot variant will include this option. Super and start typing. The Dash is a mess right now, and has to be seriously tweaked. As for the most recent applications, this is coming with Zeitgeist. It uses the same mechanism as Synapse or Gnome Do or Silverlight, but it doesn't display a drop down list of apps, but lays them out clearly. 

To add to the confusion, I really really liked the October Mockup of Shell. remember that? When you opened the Activities panel, you had a left side column, and the Workspace grid was on the right side, sou you could drag and drop applications and documents onto workspaces. Why they replaced it with that launcher-dock idiocy, I have no idea. 

Kwin is the best example of an XWindows DE integrated  Wm. As I've written before, it does its only job - managing the KDE desktop - perfectly. Compiz's greatest strength, its versatility, is also its greates weakness - Kwin doesn't crash or leak memory, ever. If there is a crash, it must be something bad enough to affect the whole Plasma, say like apt-getting kde-desktop on init 5 (my own dev cycle move). The thing with Plasma is that it's made of titanium - if it crashes, it respawns in three seconds flat. Unity certainly can't do that. But the great thing is that Ubuntu decided to build their DE on top of Compiz, it will help both projects a great deal. For my money, the first thing to do is make Compiz rock solid, then one can go to other tasks. 

Plasma Activities are, I don't know. There's just never been anything like it. Put Kubuntu Natty in VB and play with it. I was blown away. And the funny thing is that a lot of long time KDE users are unsure as to how to use them :D Also, I agree with your post on the other thread, Kwin is the only project right now that is consistent in the window management department. That includes Windows and OSX. 

There is another thing that the KDE project has gotten to a very good level now - their Nepomunk/Stringi semantic desktop project. it is a server that catalogues you activities across the board, and integrates with KDE search and launnch services. ALT + F2 brings up Krunner, which is a combination of Synapse and the Gnome ALT + F2 dialog, and can be used to launch applications, do kdesudo, kill processes, anything you can think of. The only trouble with KDE is that you need 4 GB of RAM to utilize it, and Kwin can be slow at times.

---

### Post by el_koraco on 2011-05-01
And, I see you're using Compiz standalone. From what I've heard, it is a beast when it's used like that. That true?

---

### Post by el_koraco on 2011-05-01
post nr3

As for the panel, I like the Ubuntu approach the best. The global menu is a very consistent place to have your menu navigation, plus the appindicators also have a very consistent quality about them. It's just a matter of not adding too much of them. So, the panel finally has a purpose.

---

### Post by aguafina on 2011-05-01
Right no I have 3 systems 

OSx snow leopard
Windows 7
Fedora 15

Of these the closest to my dream desktop is Snow Leopard, the feel, usability, user friendliness, productiveness, ease of use is godlike, going back to the other environments in most respects feels like a backward step and frustrating.
Windows 7 and Gnome are easily the best when it comes to changing the look with themes and fonts, change the font in OSX and there'll be an app that locks up, change the theme and it won't be universally consistant.
Windows 7 plays all my games perfectly, OSX plays many of the top games but lacks a full catalogue without having to use wrappers and I never tried any games on Gnome.

---

### Post by aaaantoine on 2011-05-01
> **Copper Bezel said:**
> aaaantoine: Sorry, I should have linked [your thread]("http://ubuntuforums.org/showthread.php?t=1741839"), too. Hell, I even referred to it, but never linked it.

I was actually curious to have your input on this, though. You've put some thought into this, lately, and your Unity suggestions make a lot of sense to me.

Well, since you asked...

Unlike the guys who put the effort into building Unity and building Gnome Shell, I have not really had any fundamental ideas as to how a desktop should be laid out.  I prefer to take good ideas and tweak them further.

I've spent years messing with different DE layouts in Gnome 2 and KDE 4. Generally I've gravitated toward having the task manager along the left edge of the screen and, when possible and desirable, integrating the rest of the UI into that left hand bar.

(This only works with a wide aspect ratio.  At one point I had a 4:3 screen and I ended up leaving the dock on the bottom edge instead in that case.)

Unity, as you all know by now, has this left edge dock by default, so it wasn't much of a stretch for me when I first tried it out.  The one thing that takes some getting used to for me, still, is the global menu.  Don't get me wrong; when the window is maximized, the implementation is *fantastic!* Between that and other tweaks, Unity goes to great lengths to minimize UI real estate without hiding consistently useful information when you have a maximized window.  But when I've got an IM window in the lower right corner of a large screen, and all three of its menu options are up in the upper left, I get frustrated with how the global menu is positioned.  Now, I'm sure there's a logical reason behind the current design, but suffice to say, for windows that aren't maximized, I'd prefer if the menu bar were still built into the window itself somehow. Indeed, your link to my thread shows one of my proposals for doing just that.

Now, normally on my laptop I use KDE4, but after I upgraded my desktop to Natty testing, I decided to install Gnome 3 on my laptop.  And Gnome 3's Shell really gives me some pause for thought as far as how I work with DEs.  Unlike Unity, its task management is completely different from what I'm used to, but it remains intuitive.  Now I find myself looking for the hot corner when I go to use Unity.  In fact, I went ahead and set the lower right corner as a shortcut for the Scale plugin.  I've known that this feature was configurable for years, but I've never really adapted to using it on a regular basis.

For launching new applications, all the major DEs (Gnome, KDE, Windows, dunno about OS X) have the most important feature implemented: application search.  Beyond that it's really just a matter of preference how to organize the entirety of your applications list.  The jury's still out on the best way to do this.  Unity probably has the best presentation -- most frequently used, then All Apps, then related Apps you can download.  Gnome's big-*** wall of apps is good, too, but the click target area (to get to the Applications view) is annoyingly small and not Fitts' Law friendly.  Windows 7's Start Menu hack is familiar and highly customizable, but Windows apps always have like 3 or 4 different Start Menu links for each application, adding unnecessary nesting and clutter.  But again, these interfaces rarely matter as long as you have pinned apps and can hit the Meta/Win to quickly type to search for the app you want.

Then there's the system tray, indicators, and notifications.  My thoughts on that another time.  I think I already typed too many words. ;)

---

### Post by 3Miro on 2011-05-01
People use computers in different ways for different reasons. People have different visual orientation and different thinking about the machines. There is no way to make one UI that will fit all people. There is no way to make one interface that will fit even a majority of people. People have different ideas of what looks good and what is ugly.

The only good DE is the one that is 100% customizable. Currently KDE comes close, but it is not 100% there. I use XFCE, because I can adjust it the way I want it to be and it is faster than KDE.

Gnome-shell and Unity both suffer severely in the customization department (with Unity being better as it is build on the old very customizable compiz). Since those environments are the first iterations of their kind, I hope they will improve in the future.

---

### Post by oldos2er on 2011-05-01
tl;dr. My dream DE would be OS/2's Workplace Shell for Linux. Guarantee ya it'll never happen.

---

### Post by JDShu on 2011-05-01
First to answer the topic question, I also don't have a concrete idea of a perfect DE. That said, I have a few thoughts floating around regarding DEs which I keep meaning to organize but for now I'll just mention random stuff that comes to mind.

There is a tradeoff between ease-of-learning and ease-of-use. My personal opinion is that for a desktop environment, which most people use daily and for large periods of time, ease-of-use takes priority. However, people generally find ease-of-learning more salient. Shell prioritises ease-of-use, Unity focuses a bit more on ease of learning. I should say, if I was designing a DE that I was going to ship onto a product I was going to sell, then I would prioritise ease-of-learning, because that is how I would attract people from other platforms. People like to use what they are familiar with, after all. But if its a product that I want to use to improve people's user experiences, then ease-of-use is the way to go.

Shell, my current favourite DE, has two major problems with it that irritate me. The first is the outstanding indicators on the bottom right. They are very hard to click on as is, and always seem to be hiding from me so that I can never click on what I want to click on. The second major problem is the lack of an obvious way to shut down. I don't really understand why hiding the shutdown or restart options is so necessary. Another issue is that in shell mode, the all the windows look quite similar - I mean I'm always always working with white windows full of text... and I can't differentiate at first glance nor do I want to spend time reading the names of the windows. Having icons to indicate what application a window belongs to, like the option in compiz scale does it, would really help.

Unity I feel is some kind of middle ground between Shell and Panel. It is more familiar to users than Shell, but still different and can improve workflow compared to Panel. I sometimes wonder about the decision to maximize vertical space at the expense of horizontal space. It seems almost like it is fighting with the form factor of widescreens. Some design decisions are just plain weird at this point, like the tiny triangle indicator, the toaster popping icons, and the way the global menu is hidden.

Customisability is less important than a lot of us realise. Most people use defaults and don't want to waste time modding their interface. So defaults themselves are what is the most important. Sure, you can't please everybody, but definitely try to please the target users, whoever they are.

Lastly, I hear it takes on average 6 iterations of a product before its good. I don't know how this translates to an oss development environment, but I think one release of the product, which is the case for both Shell and Unity is not enough. I get the feeling that 11.10 and Gnome 3.2 will be vastly better as they get feedback and take care of usability problems.

---

### Post by aaaantoine on 2011-05-01
> **JDShu said:**
> Customisability is less important than a lot of us realise. Most people use defaults and don't want to waste time modding their interface. So defaults themselves are what is the most important. Sure, you can't please everybody, but definitely try to please the target users, whoever they are.

Agreed.  Gnome 3 gets a lot right (which is more than could be said for KDE 4.0).

However, Gnome 3's "Normal" font size is too big, and its "Small" font size is near microscopic.  Maybe there shouldn't be x-pt sizes, but there should at least be some intermediate settings.

---

### Post by Dustin2128 on 2011-05-01
Neural interface- skip the desktop metaphor. Falling short of that, a touch sensitive high res holographic projection of the compiz or kwin cube would serve me nicely. Currently: xfce is my dream de. Well, it'd be nice to be a bit more customizable though. But their run dialogue is like a desktop awesomebar. One relevant symbol- my command's ready. No configuration needed. @ el_koraco, my desktop runs kde fine on 2GBs DDR2- compensated for by my relatively powerful graphics card though.

---

### Post by DoktorSeven on 2011-05-01
My dream DE is KDE, pretty much.  So I'm happy...

---

### Post by Copper Bezel on 2011-05-02
el_koraco, I see multiquoting as a service to the third reader and a safeguard against ambiguity. I'm going to demonstrate this by refraining. Try and see who I'm responding to, and which points, just now. = D 

I like the distinction between ease of use and learning curve, but if you remove users' familiarity with other systems from consideration, they become similar things. Unity isn't *inherently* easier to learn than Shell, by virtue of being more intuitive; it's just more similar to other things. I understand why Canonical went that route, and I do prefer the result, but for different reasons. A truly consistent and intuitive system should be easy to learn and quick to navigate if it follows its own rules and if those rules make sense according to the UI's overall metaphor. I think iOS is a fairly good example of this.

I also don't think improving what exists and having a stated set of goals are mutually exclusive things. Everything is built on existing conventions and metaphors, and a lot of those were established by an intuitive logic that wasn't fully articulated. I think that identifying that logic can help a great deal in identifying possible areas for improvement. dyltman's point on responsiveness is also well taken, and I think that's a primary goal, even if it's really impossible to speculate on in this kind of hypothetical discussion. It's another thing I appreciate about Synpase, for instance, to be able to call it and start typing without thinking about whether or not it's going to load in time to catch the string.

In terms of this point on the application launcher, I do think that the search method for launching applications is the ideal. For a real and marketable DE, though, the trick is making something that makes sense in every environment in which it's going to be used. I mean, I want to start with thinking of the hardware as a tablet that works in both orientations, plugs into a keyboard with a trackpad, and then supports an external monitor and peripherals for the home office. That's the ideal, isn't it? So typing might not always be the simplest method. Everything needs to be accessible both ways. For this Slingshot implementation, that also means portrait and landscape formats. 

Slingshot is easier on the eyes than Unity's application view in Dash, but I don't think it's any easier on the brain; the click target areas are tiny, and I just don't understand how a screenful of forty little icons in arbitrary order is meant to be easy to get at. Is there any logic to how Slingshot's pages are organized? A row of three or four icons is easily scannable; a row of eight is a little harder to skim over. If the icons were organized in category pages, there would still be no need for scrolling (which is admittedly easier on a mouse or multi-touch trackpad than on a touch device) but, with fewer apps per page, they could fit into a narrower layout.

On the docks-that-aren't-docks in Unity and Gnome Shell, I'll take Canonical at their word that the left-hand position under the Home button is a design decision, although I don't necessarily think it's a good that they feel the need to enforce what they feel are good habits. It's certainly a design meant for wide screen displays, as well. The dock-thing in Gnome Shell seems like the result of a mixed metaphor; I do think the earlier concept offered more functionality. I don't think of a left-edge panel as fighting with the form factor so much as taking advantage of it. Even if my dock was always visible, I could still easily have two windows up side by side. I do think of the global Application Menu as a justification for the panel, but it's a bad one. Just let the damned thing die.

On CompizStandalone: Yes, it's a beast. It's a monster that devours the dreams of children to feed its endless hunger. Or "a handy way of making Gnome a little more manageable," however you want to put it. = ) The only performance advantages I've noticed had to do with ditching the Nautilus desktop and the Gnome Panel, but that's simple enough without using Standalone. I briefly tried switching to XFCE's background services, but they turned out to be far too limited for my purposes. I *am* using XFCE's power manager, and the Compiz Wallpaper doesn't work under 10.10 Gnome without a workaround.

I like Compiz's interoperability, and I like having a sinple startup script that I can modify if I feel the need. Interoperability is just *nixier than the alternative, and no single DE offers all the parts I want. That said, complete customizability within a single system, as a couple of people are hinting at, is impossible. There's an underlying logic to every system, and not every system is going to require the same set of parts. There most certainly are different computers and different users with different requirements, but to a certain extent, that's why there are different DEs and shells. 

I also don't think responsiveness, sanity, or intuitive consistency, the things that actually make a UI a good one, should be sacrificed just to make hair-splitting tweaks possible, and I don't think the average user should be expected to assemble a sensible environment from an assorted bucket of parts, which is essentially what I feel the default Gnome 2 environment offered. Customizability really does affect a small percentage of users. (But that's really separate from interoperability, which, in a Linux universe where every distro is built on existing components, affects everyone.)

Edit: I don't want to come across as if I'm arguing here, especially in my own thread with "your dream" in the title. I just think there's a chance of coming to some cool solutions on these things. = D

---

### Post by LarsKongo on 2011-05-02
An interface that is 100% customizable with XML and CSS3. ;)

- Link a wallpaper from the cloud to your desktop. No need to save them on your hdd.
```
body { background-image: url('http://picture-from-the-cloud.png'); background-size: 100%; }
```

- Use CSS3 and HTML5/JavaScript for transition effects and animations.
- Options for people who prefer to use their mouse/keyboard. Mouse-gestures ftw! :)
- Base setup for beginners. No more than 1 panel at the bottom with a menu, task-switcher, indicator-tray and a clock.
- Options for people to put the menubar where they want it. For example: Global, a button like Firefox/Opera/Chrome, classic like Windows and Gnome.
- Don't like something on your desktop?
```
#herpyderpy { display: none; }
```
;)

etc.

So much could be done with an interface like that. :)

---

### Post by BrandonC19 on 2011-05-02
> **Copper Bezel said:**
> 

[[IMG]http://dl.dropbox.com/u/17749392/Screenshots/detopic-thumb.png[/IMG]]("http://dl.dropbox.com/u/17749392/Screenshots/detopic.png")


That is simply a gorgeous desktop, and this is probably a stupid question, but what is that little "notification-area"-esque thing in the upper-right corner?

---

### Post by Copper Bezel on 2011-05-02
Thank you. :D

Both panels are provided by Avant Window Navigator - the one on the left has DockBarX and the Launcher/Taskmanager applet (which is invisible here but manages auto-hide) and the one on the upper right has, in order, the Digital Clock, Sound Menu, Notification Area, Indcator Applet, and Session Indicator Applet.

Edit: LarsKongo, I don't know enough about XML to know which parts of that are serious and which are sarcasm. I kind of like the sound of it, though. = )

---

### Post by BrandonC19 on 2011-05-02
You are welcome, and thank you. :D

---

### Post by el_koraco on 2011-05-02
I'm not saying Slingshot is the ideal, just like Unity, Plasma or Shell. I just think it's come the closest to this idea of mixing the known, the new and the practical. 

The latest mockup of Slingshot mixes the wall of icons with the category view. You get the wall, and on the upper side you get "applications, system, administration" and other categories. IMO it is the best mix of the Shell wall with a sensible category approach.  The unity dash has the best implementation of further segmentation of applications, according to the most used ones, the proposed ones, and so on. The implementation is just a little rugged, and not unified - too many lenses ans stuff. The other thing about Slingshot is that with the spatial and spatial categories design it keeps consistency. work needs to be done on the organization itself, for portrait/landscape and so on. Actually, it seems to me like it doesn't refrain itself from bringing the iOS/Jolicloud/Chrome OS model directly onto the desktop, without fear of complaints. The trick is to make everything as fast as it is in iOS.

I'm also partial to the Ayatana project. i find it as the best use of the panel that I've seen so far. Actually, it's the one thing that i miss the most when using a non Ubuntu distro. The problem with Unity is all the hubub of options you have for invoking the Dash and the launcher - 0x0px for the Launcher, clicking on the same place for the Dash, and so on. Even after using this model for years, one could get confused. Throwing the mouse in the corner like in Shell is superior IMO. You get used to it so quickly, it's harder to get unused :D

As for post splitting , it's no service to the reader, and it is against the very nature of conversation - one no longer discusses with what was said as a whole, but with specific parts of the conversation, which is unnatural. It is not always necessary to cover every little point that had been made. If we were talking in a bar, you wouldn't be splitting my sentences, would you? Admittedly, it's less so a problem with discussions of this nature than with arguments on what kind of economy type is superior, but still. I freaking hate it.

---

### Post by Lucradia on 2011-05-02
No DE is my dream DE.

I don't really need composition, no need for transparency on anything.

I'll stick with openbox thank you.

I'm also not liking the direction XFCE is going so far. The transparency for panels has issues on netbooks when you turn off compositing, where panels will disappear, but still be there (but you can't click on them.)

---

### Post by Copper Bezel on 2011-05-02
It's comparing chess by mail to basketball, isn't it? Rarely in a bar conversation are responses made to thousand-word posts by three different people in a form intended to be casually perused by third parties after the fact.

Generally, I don't draw smilie faces on napikins to let folks know I'm kidding, either. = )

I know Slingshot isn't ideal, but I see your point that it's a good place to start, and it *is* very pretty; I *love* the idea of just evenly darkening the screen like that for shell actions, and it's a very inviting "home screen" look, which I agree already shows some openness to using conventions of the mobile platforms on desktops. 

I'm glad that categories are coming into the mix, though. I'd actually had this thought - what if it did scroll, but horizontally, and the categories were two to four columns each, with a "more" button at the bottom if that's not enough space? It could be equally desktop- and tablet-friendly. Like this:

[img]http://dl.dropbox.com/u/17749392/Screenshots/slingshot-categories.png[/img]

You'd see one or two categories up in portrait, two or three in landscape, just cropped to the breadth of the screen. Maybe give it a wraparound behavior, too.

Believe me, I like Unity and appreciate that it's a rare and real attempt to really think through a desktop UI's workflow, but it does feel so cluttered, particularly that upper left corner, which I too have become used to batting as a panic button (as I've used Scale in one or both upper corners for quite some time.) Hovering and clicking the same area certainly shouldn't perform two different actions. I don't think it's a touch-friendliness consideration as, at least in the way I've been using them, Compiz corners seem to be a stand-in for a swipe already, but it's just too easy to mess up. 

After all the frustration I've had with my upper left corner and finding myself in Scale mode when I'm just trying to close the damned window, I've ended up adding an invisible AWN spacer that leaves a 7px gap of desktop on the left when windows are maximized. (Perks, though, in scrolling to switch desktops and clicking to launch for Synapse.)

On point, though, while I think that the global Application Menu requires extra steps that it shouldn't - in that you can't, for instance, select a menu pertaining to an inactive window via clickthrough anymore - I could get used to it if not for that damned autohide behavior. I just don't get what purpose that's meant to serve.

I really want to know whether or not LarsKongo is kidding. An entirely cloud-based OS is a bit absurd still, and the desktop-as-webapp would be a bit slower than we're used to, but I like the simplicity. = D And Shell is already using CSS....

---

### Post by el_koraco on 2011-05-02
> **Copper Bezel said:**
> It's comparing chess by mail to basketball, isn't it? Rarely in a bar conversation are responses made to thousand-word posts by three different people in a form intended to be casually perused by third parties after the fact.

Generally, I don't draw smilie faces on napikins to let folks know I'm kidding, either. = )



I don't care, splitting posts is havoc :D 

Omg the horizontal scrolling idea is brilliant. Combine it with mouse gestures and touchpad swipes, and that's it. That's freaking it. Maybe this should be brought to the eOS's team attention, because I doubt the Unity design team would be much inclined to make all too many changes to the Launcher/Dash behavior just yet, and the Gnome project already knows what's best for everyone. i get the feeling they might start to suffer during the further development stages. It's clear that neither Unity nor Gnome Shell will stay as they are now, but they might want to start avoiding being to similar, in which case neither side will be willing to implement the correct ideas. I truly see Pantheon in great shape to pick up ideas from all sides, unconstrained by ideological arguments. 

Btw, I've seen a [video]("http://www.youtube.com/watch?v=l_7f3Lxd4_I") of Shell on a tablet recently. It works much better than I could imagine Unity to work. Talk about a "giant  iPhone OS" there. It's rough around the edges, but I can see how the dynamic multitasking idea works.

Good, we're in agreement with the confusing launcher invocation. And what's up with the slow appearance? What purpose is that supposed to serve? 

Global menu - I guess it depends on preferences and screen size. I put it up on Jupiter yesterday, and I'm liking the consistency of it. I don't even mind it when I have to roll up the mouse to the upper left, but I do see why some people might find it annoying. i kinda like not having the menu in any window, ever, but maybe an option should be given to specify which applications you want to have the menu, and which not to. Say, put it as the default, and give a blacklist in the config files - kinda like there's a whitelist for tray items in Unity. Not too hard to implement, and it would keep the spirit of configurability. Otherwise you'd have the same situation as with the launcher position. 

On the other hand, I still like the idea of a top panel. It serves as a kind of permanent comfort zone that i know will always be there, so i don't mind the 20 px screen real-estate it is taking up. i know this from my experience with Objectdock in Windows. I put that thing up on XP like four years ago, and removed the panel alltogether. It had all the functions of the panel integrated, but I kinda kept missing a fixed bit of space. Perhaps an idea could be made out of combining the AWN false transparency and the panel.

---

### Post by Copper Bezel on 2011-05-02
Technically AWN uses only real transparency, part of why it's so damned heavy for a panel, but I get your meaning. = ) Yes, that "comfort zone" makes sense, and even iOS and Android make use of one. And, again, I have to admit that I am, now, too. = P But I think that making the panel narrow and overlay-like helps make it feel less claustrophobic. Shell's is the nicest-looking, and Wingpanel is close (but it needs the little curls, I think; there's a strange psychology at work, there.)

My main objection with the global Application Menu in Unity is that it autohides. It actually does already have a blacklist, modified in much the same arcane method as the systray. I think that in principle, it's at least an excellent way to get the menu bars out of the way, because God knows a calculator or media player doesn't need one and the devs aren't going to stop including them any time soon. I also admit that the scenario of needing to access a menu item on a non-focus window that isn't occluded is a fairly rare one.

I definitely agree about the Unity Home Button. I can't help thinking that its click action duplicates functionality from other Launcher items, anyway, and it's not very visible. I think it would be best as a way of pinning the launcher in place; hover *any* part of the button to raise the launcher, click to lock it visible (and adjust maximized windows to the right.)

I also agree about eOS having a little more freedom to move than the two big shells. The stakes are lower, they've invested less, they're newer to the process, and, yes, they appeal to my menu-hating side.

(I'm really glad you liked the Slingshot concept! I think I'll try and do a proper mockup video, as soon as I find out how to do that. I'm not doing much this weekend.)

Unrelatedly, the Shell tablet video *was* surprising smooth. I mean, the window staying resized when the keyboard goes away is a bit alpha, but it didn't seem like there were any obviously missing parts to the interaction, and the use of the whole screen space for the shell makes sense in a touch environment in a way I didn't fully anticipate.

---

### Post by gsmanners on 2011-05-02
My dream UI would be exactly like KDE, only everything on the bottom panel would be on a panel on the LEFT side of the screen, and window decorators would all be on the right side of the windows. I have yet to see anyone even sketch this idea, but I can clearly see it in my head. That type of design would make the best use of space, although it would require people to learn how to read vertically.

---

### Post by MBybee on 2011-05-02
My dream DE would be an updated version of WindowMaker, but modernized with cleaner/higher res icons, and support for newer apps.

XFCE is also about 99% of ideal too, though it's just not quite as attractive. KDE4, Unity, and Gnome3 are all trying to solve a problem I don't have.

---

### Post by el_koraco on 2011-05-02
> **gsmanners said:**
> My dream UI would be exactly like KDE, only everything on the bottom panel would be on a panel on the LEFT side of the screen, and window decorators would all be on the right side of the windows. I have yet to see anyone even sketch this idea, but I can clearly see it in my head. That type of design would make the best use of space, although it would require people to learn how to read vertically.

Install KDE. Move the panel left. Install Shoothtasks. Remove task manager. Put Smoothtasks on panel. You have your dream UI in two minutes after installing the desktop.

---

### Post by gsmanners on 2011-05-02
> **el_koraco said:**
> Install KDE. Move the panel left. Install Shoothtasks. Remove task manager. Put Smoothtasks on panel. You have your dream UI in two minutes after installing the desktop.

Thanks. I'll give that a try once I find the time. :)

---

### Post by el_koraco on 2011-05-02
> **Copper Bezel said:**
> Shell's is the nicest-looking, and Wingpanel is close (but it needs the little curls, I think; there's a strange psychology at work, there.)


Yeah, I was just thinking the same thing yesterday. It'as amazing how a little detail like that can make everything better. i can even forgive Shell the nasty fonts :D

Well, if you could do a video, that would be something one could present to the devs, instead of a forum discussion and a paper mockup. Not gonna be able to help you there. Got a wedding and my 10 year high school reunion on the weekend. Might even get me laid (not really, but the hope never dies). 

i'm 100% with you on the hiding feature of the Unity global menu. It kinda feels like they didn't wanna seem as ripping of OSX, so they added it just like that. That's bull. Apple never had trouble ripping off projects, and it's good that they didn't. Without their KHTML ripoff we'd still have a browser choice between Firefox and Konqueror.

---

### Post by Copper Bezel on 2011-05-02
Yeah, it really is all in those little details.

Good luck in your weekend project, then. = )

---

### Post by JDShu on 2011-05-02
Part of designing is to take into account the target users. Those users are probably more familiar with currently existing desktop UI. That is, yes, if we wiped everybody's memory of how to use DEs then Shell might not be harder than Unity to learn, but we do not design in a vacuum and so existing user knowledge needs to be considered.

---

### Post by jerenept on 2011-05-02
My dream WM: Unity, without the GlobalMenus. They annoy me (personally)

---

### Post by Copper Bezel on 2011-05-02
I guess I'll sig that one, too, now. = D

JDShu, I don't think I really disagree with you; I argued as much in the other thread, regarding the dock and min-max buttons. It's just that simultaneously, we have iOS being regarded as "easier" than Windows by Windows people, and I don't know what to do with that.

---

### Post by jerenept on 2011-05-02
> **Copper Bezel said:**
> I guess I'll sig that one, too, now. = D

Thank you!!

---

### Post by Jackslaps on 2011-05-03
My dream DE is a mix between Windows Phone 7 and Openbox. Basically I want Crunchbang with with Windows Phone 7 aesthetics or Windows CE 7 aesthetics. I'm into very minimalistic themes and quite honestly I wish I had a computer that would look like it belonged to IKEA, or would fit in perfectly in Mirror's Edge or something. My current GTK theme is a mix of different themes. The window borders are from a theme I got called Black_and_White, and everything else is either Dust or Dust Sand with either Humanity or Humanity Dark icons depending on what wallpaper I feel like having. I deleted the bottom panel and replaced it with Docky to mimic the Openbox thing on the bottom while keeping the top panel as transparent as possible to make it look like glass.

---

### Post by robro on 2011-05-03
Something that can be customized from top to bottom.

---

### Post by jjpcexpert on 2011-05-03
One that kills processes that report disuse for longer than 365 days. And only open windows.

---

### Post by JDShu on 2011-05-03
> **Copper Bezel said:**
> 
JDShu, I don't think I really disagree with you; I argued as much in the other thread, regarding the dock and min-max buttons. It's just that simultaneously, we have iOS being regarded as "easier" than Windows by Windows people, and I don't know what to do with that.

Well iOS and Windows havel very different aims. iOS is very app focussed to allow media consumption while Windows has more focus on multitasking and productivity. Comparing them is really apples to oranges, I think.

---

### Post by Lucradia on 2011-05-03
For those who want to know what my openbox would entail, excerpt from debian forums:

> Mini.iso, debian-multimedia / medibuntu, then install:

```
apt-get install openbox obmenu menu obconf openbox-themes gtk-themes-murrine gtk-chtheme alsa-utils iceweasel xorg pcmanfm gnome-icon-theme stalonetray conky flashplugin-nonfree hplip xsane gimp pidgin pidgin-libnotify gstreamer0.10-x gstreamer0.10-ffmpeg ffmpeg faad faac totem freepats x264 libdvdcss2 lxterminal htop scrot unclutter xdg-utils usbmount --no-install-recommends
```

Source: [http://forums.debian.net/viewtopic.php?f=20&t=50703](http://forums.debian.net/viewtopic.php?f=20&t=50703)

---

### Post by BrokenKingpin on 2011-05-03
XFCE is pretty damn close for me. A few modifications I would like to see to it though (or applications developed specifically for XFCE):

- It's own login manager. Currently GDM is used in most XFCE distros, but this brings in a boat load of Gnome dependencies that are not needed for anything else. I use SLiM myself, which works, but is lacking a few features.

- Added utilities for configuration. Again a lot of the applications from gnome work in XFCE such as the network manager and bluetooth configuration, but they also rely on too many Gnome dependencies.

- Thunar (file manager) to support tabs and bookmarks to remote shares

- A native panel applet like DockBarX. DockBarX works through XfApplet, but it is buggy.

- A few bugs cleaned up around power management

All in all I want XFCE left as is for the most part, just with added features that Gnome2 has, without the Gnome2 bloat.

---

### Post by BrokenKingpin on 2011-05-03
> **Lucradia said:**
> 
I'm also not liking the direction XFCE is going so far. The transparency for panels has issues on netbooks when you turn off compositing, where panels will disappear, but still be there (but you can't click on them.)
This is a known issue. If you remove the panel and add it back you should not see any more issues with turning off/on the compositor. It is quite annoying though, but not a deal breaker.

---

### Post by gsmanners on 2011-05-03
> **BrokenKingpin said:**
> - It's own login manager. Currently GDM is used in most XFCE distros, but this brings in a boat load of Gnome dependencies that are not needed for anything else. I use SLiM myself, which works, but is lacking a few features.

...

- Thunar (file manager) to support tabs and bookmarks to remote shares

...

I've used xdm in place of gdm before, and that worked out okay. There are [plans]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-lightdm") to replace gdm with lightdm in Ubuntu, and that will probably follow into Xubuntu.

Thunar will not support tabs. This comes from the devs:

> Bad usability and there are already similar file managers that provide tabs.

see [http://forum.xfce.org/viewtopic.php?id=5904](http://forum.xfce.org/viewtopic.php?id=5904)

---

### Post by Retlol on 2011-05-03
Linux stability, gnome-shell a few versions from now with windows apps.

---

### Post by Simian Man on 2011-05-03
> **Copper Bezel said:**
> Dragging a window to a right or left edge already means something in Linux. Double-clicking a titlebar already maximizes a window, so maximizing a window on dragging to the top edge doesn't add any convenience or functionality. The one really nice feature of Aero Snap that doesn't duplicate anything else is double-clicking the upper resize handle to maximize the window vertically, and since it's not possible with the present decorators, it isn't implemented.

In Kwin, middle-clicking the maximize button maximizes horizontally and right-clicking it maximizes it vertically.

---

### Post by aaaantoine on 2011-05-03
> **Simian Man said:**
> In Kwin, middle-clicking the maximize button maximizes horizontally and right-clicking it maximizes it vertically.

Incidentally, this works the same in Unity, except vice versa.  Neat trick.  Didn't know about it before.

---

### Post by keithpeter on 2011-05-03
> **aaaantoine said:**
> Incidentally, this works the same in Unity, except vice versa.  Neat trick.  Didn't know about it before.

Middle click toggles vertical, right click toggles horizontal in Xubuntu 11.04's XFCE.

I must be taking the DE for granted. I just use XFCE and make it look like windows XP with a task bar at the bottom with a menu on the right of the bar and indicators on the left. Creature of habit I suppose. 

The rest is dmenu bound on Alt-Space and the Alt-Tab window cycle.

---

### Post by BrokenKingpin on 2011-05-04
> **gsmanners said:**
> Thunar will not support tabs.
I know, but this my my dream DE :P

---

### Post by Copper Bezel on 2011-05-04
I wouldn't want tabs in Thunar - that it doesn't support them is one of my favorite things about it - but I wouldn't mind if the drag-and-drop behavior between Thunar windows was actually, say, consistent.

> In Kwin, middle-clicking the maximize button maximizes horizontally and right-clicking it maximizes it vertically.

Metacity / GTK-Window-Decorator has the option, and I just made it my titlebar double-click for a while. I don't think of right or middle-clicking as a very intuitive or straightforward action for this behavior, though, and I frequently found myself accidentally unmaximizing vertically on maximized windows no matter what button binding I used. The Compiz binding I'm using removes horizontal and toggles vertical maximize when I click the top edge of the screen, which works for me; I'd just kind of like, in the absolute ideal, for it to be the action for clicking the top edge of the *window*, instead (Snap style.)

---

### Post by Frogs Hair on 2011-05-04
I would like to see the Unity panel with custom settings like some of the docks have .
I know I could boot into Classic amd install a dock , but I don't want to do that becuse that is what I have been doing for the past year and Gnome 2.xx will most likely be gone be gone by 11.10 .

---

### Post by Copper Bezel on 2011-05-04
Yeah, but you can use a dock in Shell, too; alternately, either Cairo Dock or AWN can provide a dock-and-panel layout to replace Unity.

---

