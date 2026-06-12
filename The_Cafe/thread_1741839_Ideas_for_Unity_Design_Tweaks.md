---
title: "Ideas for Unity Design Tweaks"
date: 2011-04-28
forum: The Cafe
---

### Post by aaaantoine on 2011-04-28
The attached image speaks for me.  Pardon the sloppy GIMPing and rather lossy compression. :)

Edit: Uploaded new, slightly clearer image with less dead space.

---

### Post by scottykal12 on 2011-04-28
These are really cool ideas. I wonder if there is a way to submit this to the unity team.

---

### Post by grahammechanical on 2011-04-28
I would go with the desktop switcher at the bottom but I do not like the large size home button. It just does not like nice, in my opinion.

Perhaps this kind of stuff could be done through developing themes.

Regards.

---

### Post by aaaantoine on 2011-04-28
> **grahammechanical said:**
> I would go with the desktop switcher at the bottom but I do not like the large size home button. It just does not like nice, in my opinion.

Well it was a quick hand-drawn Ubuntu logo.  I wasn't going for beauty so much as what my ideal layout should be.

I should also comment on why it's cut off as such.

The idea I have is that, by default, it will be a big, round button as drawn.  But if both 1) a window is maximized and 2) the Launcher panel is hidden (options allow the Launcher panel to never hide), it will shrink to fit the top panel as it currently does.

I imagine a transitional animation of the logo growing / shrinking as the mouse cursor is moved into the upper left corner -- the same action which most quickly invokes the launcher panel when it is hidden.

---

### Post by ZarathustraDK on 2011-04-28
I agree with all the suggestions, except the window-menu-thingy. If there are menus available to a window, then it should always be readily apparent to the user without them having check out every window.

Not to say I prefer the global menu above the given suggestion, but there need to be another "window-centric" menuing way of going about this smarter with fewer clicks which is not the old way of doing it. I say this because the idea of isolating the tray icons up there to the right syncs perfectly well with having the window-controls (close window etc.) on the left when maximizing a window (the top of the screen will then be one big bar, with the tray-icons going on top of the blank part of a given windows titlebar). Currently (can't speak for low-res screens) a large part the top-panel is dedicated to the global-menu, waaay to much, about 1000 pixels of blank space on my screen. I'd much rather see my wallpaper than empty panel in those places.

---

### Post by aaaantoine on 2011-04-28
> **ZarathustraDK said:**
> I agree with all the suggestions, except the window-menu-thingy. If there are menus available to a window, then it should always be readily apparent to the user without them having check out every window.


The window menu would have a button cut-out of some sort in the title bar to show that there is, indeed, a menu.  I had drawn this, but I think the effect had become too subtle after downsizing the image and setting a low quality for the image.

If there is no menu, the button will not exist, and the title bar will look as it currently does.

> Currently (can't speak for low-res screens) a large part the top-panel is dedicated to the global-menu, waaay to much, about 1000 pixels of blank space on my screen. I'd much rather see my wallpaper than empty panel in those places.

On a 1920 wide screen, it's something like 1600x22, or 35,200 pixels, that are wasted.

---

### Post by ZarathustraDK on 2011-04-28
> **aaaantoine said:**
> The window menu would have a button cut-out of some sort in the title bar to show that there is, indeed, a menu.  I had drawn this, but I think the effect had become too subtle after downsizing the image and setting a low quality for the image.

If there is no menu, the button will not exist, and the title bar will look as it currently does.

Hmm... still a bit sceptical about this. It'd probably be nice for you and me who are comfortable with the applications, but think about a new user experiencing (for instance) Gimp for the first time. It'd make the learning curve steeper since they'd have to memorize the menus on 3 diffrent windows; though the global menu has exactly the same problem in regards Gimp, it at least presents the user with an overview of the menus whenever a one-window program is in focus and being used.

> **aaaantoine said:**
> On a 1920 wide screen, it's something like 1600x22, or 35,200 pixels, that are wasted.

I varies depending on the program used, programs that actually use the global menu would make this number smaller, my estimate is from Firefox in focus but nevermind, it's a helluva lot of wasted pixels, we agree :D

---

### Post by aaaantoine on 2011-04-28
> **ZarathustraDK said:**
> Hmm... still a bit sceptical about this. It'd probably be nice for you and me who are comfortable with the applications, but think about a new user experiencing (for instance) Gimp for the first time. It'd make the learning curve steeper since they'd have to memorize the menus on 3 diffrent windows; though the global menu has exactly the same problem in regards Gimp, it at least presents the user with an overview of the menus whenever a one-window program is in focus and being used.

I figure if Unity is going to hide the menu bar anyway, at least hide it closer in proximity to the window itself. :P

And the problem with your example is that Gimp only has a menu for whichever window the image is contained in.  At some point they dropped the menus from the toolbar windows.

The current situation with Gimp is even worse than it would be in my proposal, as I discovered while making this mockup. If your focus is on one of the toolbar windows, there is no menu in the top panel.  You have to explicitly switch focus to the image window, *then* move the cursor to the top / press alt.  Very annoying.  At least with this design, you can move your mouse over the drop-down-menu button on the image window to bring it up.

(As a side note, this will probably be fixed when GIMP's single window mode is fully developed.)

---

### Post by ZarathustraDK on 2011-04-28
Another, daredevilish, suggestion could be to simply move the menus to the titlebar of the window. It's not like you're looking at the Sudoku-window and go "gee, I wonder what this program I just opened is called, I need to know so badly it must have an entire horizontal row in the window dedicated to it in order to remind me".

EDIT: It's not the proposal vs. global menu I'm against, it's having to mouseover something in order to get to view the menus. Menus ("File" "Edit" etc.) should simply always be visible without requiring the user to hunt for them. A big part of learning a new program is glancing at the menubar while using the program, and contemplate the possible interactions.

---

### Post by aaaantoine on 2011-04-28
Maybe.  But doing that would step on the toes of features we often take for granted, particularly if the menu spans the width of the title bar.

- Double-clicking the title bar to maximize.
- Clicking and dragging the title bar to move.
- Sometimes useful information in the title bar (such as the name of the current document) -- though I've said before that this information should probably be somewhere in the window itself.

---

### Post by seeker5528 on 2011-04-28
I don't think the home button needs to be bigger, it just needs to look more like a button, or at least give some indication when you mouse over it that it actually provides something.

Personally I prefer the unified menu to having a Firefox style dropdown menu. I don't think there is going to be any change of direction on the unified menu idea anyway, which makes changes to the length of the top panel unlikely. 

Later, Seeker

---

### Post by Copper Bezel on 2011-04-28
I've been thinking in this direction as well, and it's how I have things laid out with AWN, more or less, although I don't have any need for the application menu, trash bin, or workspace switcher - I use Synapse, my Thunar bookmark, and a hot corner, respectively. (The resulting layout is fairly sleek, with nothing but a systray in the upper right and a little DockBarX on the left.)

My solution to the global menu would be a "..." button in the window frame to the right of the title to show or re-hide the menu, perhaps with a hover action of showing the menu until the cursor leaves the area. Realistically, I *need* a menu bar in GIMP or OpenOffice but *never* use Rhythmbox's after initial configuration. Icing if the system could remember which applications the user left the menu displayed on so that they launch that way. Much like your mockup, it's probably impossible without writing a new Compiz window decorator for Unity but makes sense in usability terms.

Edit: Incidentally, I also don't know why minimized windows have workspaces. It's another item I've been considering, and I wonder what your thoughts would be on that. I tweaked DockBarX a bit to always restore minimized windows to the current workspace and ignore them unless they're selected specifically, and I like the effect; as with the old option in Gnome Panel, minimized windows are simply "stowed" "in the dock."

---

### Post by Version Dependency on 2011-04-28
What Unity really needs is to drop the entire top panel completely.  It's not needed at all.  The date/time and the systray icons can all move to the Unity launcher.  And then the whole global menu stuff will no longer be necessary.  One panel or dock can get the job done.

---

### Post by BigCityCat on 2011-04-28
They need to make it possible to adjust the shadow opacity. It's too heavy.

---

### Post by Copper Bezel on 2011-04-29
[QUOTE=Version Dependency]The date/time and the systray icons can all move to the Unity launcher. And then the whole global menu stuff will no longer be necessary.[/QUOTE]

Well, ideally, the global menu saves two rows for maximized windows, not just one, although I suppose that could be accomplished without a panel. The Launcher's fairly crowded already, though. It wouldn't just be a Windows Superbar turned vertical if it kept the trash, mounted drives, and workspace switcher along with everything else.

---

### Post by ZarathustraDK on 2011-04-29
Also we should keep in mind that the corners of the screen are a more attractive place to put stuff because you can throw the mouse there without having micromanage it. This particular notion has a fancy name that currently escapes me -.-'

---

### Post by areteichi on 2011-04-29
> **aaaantoine said:**
> The attached image speaks for me.  Pardon the sloppy GIMPing and rather lossy compression. :)

Edit: Uploaded new, slightly clearer image with less dead space.

These are all brilliant ideas. I would love to see them implemented.
Have you reported anything on Launchpad?

---

### Post by 3rdalbum on 2011-04-29
> **ZarathustraDK said:**
> Also we should keep in mind that the corners of the screen are a more attractive place to put stuff because you can throw the mouse there without having micromanage it. This particular notion has a fancy name that currently escapes me -.-'

I don't mean to sound like a Mac fanboi, but what you're referring to is known as "Fitt's Law".

In Unity I'd like to see the workspace switcher work like the old one from Gnome - being able to switch workspaces right then and there, rather than entering a workspace-switching-mode. Of course, on touch devices or on keyboard control you'd enter the workspace-switching-mode.

When originally designing the Mac OS (here I go again!) they had the idea of never having a different mode on the desktop where the user's actions do something different to normal. They had to break the rule once, at least (clicking on an icon's name will enter the name-changing-mode), but I think it's a good idea to limit the number of "modes" that the user can enter.

To improve Unity, I'd put some sort of visual indication that there is a menu available (the global menu). I like the clean look of the panel, but there needs to be some way of letting the user know that there are menus.

I'd like to see dash widgets that can be placed into the Shortcuts lense.

I'd like to see more useful quicklists - for instance, right-clicking on a CD or DVD in the launcher should reveal the option to "Copy Disc...".

I'd like to be able to right-click the launcher and add shortcuts that way, that will be executed with gnome-open.

I'd like for System Settings to be reimplemented as a lense; I believe this idea has already been suggested within Ubuntu. It makes perfect sense this way too.

And honestly, I'd like to see a way of putting the launcher on the bottom of the screen. I'd keep it on the left, but at least it would stop some complaints. SOME complaints.

Oh, and some more nice visual effects; like when you mouse-over the global menubar, have the menus follow eachother in. Or when you log into Unity, the launcher icons do a Mexican Wave as a way of welcoming you to your desktop :-)

Also, anyone else noticed that GDM looks horrible? Can we improve the looks of it? And anyone else noticed that in GDM the shutdown button is in the bottom-right, and in Unity it's in the top-right? That needs to be changed.

---

### Post by aaaantoine on 2011-04-29
> **areteichi said:**
> These are all brilliant ideas. I would love to see them implemented.
Have you reported anything on Launchpad?

I started a discussion in the Ayatana mailing list.  The general feedback is that my window menu-button idea sucks. :P (But at the same time, it's no worse than the current menu bar implementation.)

EDIT to amend:
> **3rdalbum said:**
> Also, anyone else noticed that GDM looks horrible? Can we improve the looks of it? And anyone else noticed that in GDM the shutdown button is in the bottom-right, and in Unity it's in the top-right? That needs to be changed.

Having used the GDM that's distributed with Gnome 3, I can say that this will most likely be fixed in Ubuntu 11.10.

EDIT 2:
> **3rdalbum said:**
> I'd like for System Settings to be reimplemented as a lense; I believe this idea has already been suggested within Ubuntu. It makes perfect sense this way too.

Strongly disagree.  System Settings does not need screen real estate.  By all means, pin it to the launcher if you want (you can do this, you know), but by default it should be neatly tucked away.  (Or am I misunderstanding what you mean by "Lens"?)

Its position in the "Power" menu is somewhat appropriate.  But it shouldn't be at the bottom of that menu.  It should be higher up, as it is in Gnome 3.

---

### Post by Copper Bezel on 2011-04-29
> **3rdalbum]"Fitt's Law".[/quote]
Fitts's law, actually. = ) You don't run the risk of sounding like a Mac fanboy, though - it's become almost trendy to invoke it in reference to the new shells. It's the one scientific-sounding term everyone wants to sound like they know. I'm guilty myself. = D

Seriously, though, I don't think it's possible to talk about UI considerations and not sound like a Mac fanboy. Apple has always made a sensible UI a key part of their desktop experience, where Windows and most Linux distros seem to put less emphasis on this (at least in terms of talking about it less.) 

> When originally designing the Mac OS (here I go again!) they had the idea of never having a different mode on the desktop where the user's actions do something different to normal. They had to break the rule once, at least (clicking on an icon's name will enter the name-changing-mode), but I think it's a good idea to limit the number of "modes" that the user can enter.[quote]
I think Unity's plan is exactly the opposite of this - a screen for every major function. As long as the functions all follow consistent metaphors between, that's not entirely unreasonable. I also think the fact that the Unity panels remain present during the workspace switching makes it less harsh a transition from the "normal" view.

But yes, certainly, the workspace switcher widget could be useful if it didn't have to act like every other icon on the dock, with exactly one action when clicked. Or, alternately, to retain the large click target, why not make it function like AWN's Slick Switcher, which displays a number for the present workspace and, when clicked, presents a small preview of the present workspaces, which can then themselves be clicked?

[quote]I'd like for System Settings to be reimplemented as a lense said:**
> 
I'm not certain that I fully understand Lenses yet, as aaaantoine said, but from what I've seen of them, this makes sense; a lens's behavior is almost identical to the category view of the KDE or XFCE System Settings, Windows' Control Panel, etc., and the expectation is that users will have many more Lenses than they ever had Places.

[quote]Also, anyone else noticed that GDM looks horrible? Can we improve the looks of it? And anyone else noticed that in GDM the shutdown button is in the bottom-right, and in Unity it's in the top-right? That needs to be changed.Andrew at WebUpD8 just posted that Canonical is considering shipping Oneiric with LDM, a CSS-based login screen with full customizability. I don't imagine Ubuntu's GDM will change much, but it might just go away.

[quote]I'd like to see more useful quicklists - for instance, right-clicking on a CD or DVD in the launcher should reveal the option to "Copy Disc...".
Yeah, I don't understand the death of right click. It's not as if the UI doesn't have some seriously mouse-dependent, touch-unfriendly features already, or as if "tap and hold" couldn't substitute for anything that now requires a right click. The individual Launcher item for a running app *needs* "launch new" and a window list. I couldn't live without those features in DockBarX.

---

