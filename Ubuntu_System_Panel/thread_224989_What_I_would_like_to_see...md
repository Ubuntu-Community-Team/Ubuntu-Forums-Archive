---
title: "What I would like to see.."
date: 2006-07-28
forum: Ubuntu System Panel
---

### Post by chanders on 2006-07-28
You tell me ;)

---

### Post by augied on 2006-07-28
* Panes auto-resize to fit long text (I know you can change the font, but still.)
* Default layout setting.
* Auto-clear should be triggered when the menu is closed.  Ex. you use the filter to find, and then open an app, or decide not to and simply close the menu

---

### Post by chanders on 2006-07-28
> **augied said:**
> * Panes auto-resize to fit long text (I know you can change the font, but still.)
* Default layout setting.
* Auto-clear should be triggered when the menu is closed.  Ex. you use the filter to find, and then open an app, or decide not to and simply close the menu

What do you mean by default layout setting?
Auto resize - definite possibility - next release..
Auto clear - next release ;)

---

### Post by delfick on 2006-07-28
can it be made so that middle clicking on one of the pane options on the left (say u don't have the place pane on but u want to use it for some random reason) middle clicking making it appear for that one time only...so that when u close the menu, the places menu (in this example) turns off again...

if that makes sense

---

### Post by chanders on 2006-07-28
> **delfick said:**
> can it be made so that middle clicking on one of the pane options on the left (say u don't have the place pane on but u want to use it for some random reason) middle clicking making it appear for that one time only...so that when u open the menu again, the places menu (in this example) is no longer there....

if that makes sense

If you mean, 'remember my set config every time I click on system' then that can be done....

Will try for next release...

---

### Post by delfick on 2006-07-28
no.....though that is a good idea.....

more of middle click to temporarily open pane....

---

### Post by chanders on 2006-07-28
> **delfick said:**
> no.....though that is a good idea.....

more of middle click to temporarily open pane....

Sounds interesting... Will definitely look into it...

---

### Post by delfick on 2006-07-28
> **chanders said:**
> Sounds interesting... Will definitely look into it...

cool:D

---

### Post by augied on 2006-07-28
> **chanders said:**
> What do you mean by default layout setting?
I like to only have the places and apps panes visible, but what if I need to access the settings pane (for example to change some settings.)  Right now I would open the menu, open the settings pane, screw up my system, and then reopen the menu to hide the settings pane.  My suggestion is to have a default layout (set in gconf or in the standalone settings app which I am eagerly waiting for) which the menu returns to whenever it is closed.
Now that I think of it, a 'set as default layout' button would fit in nicely in the toggle pane.

Edit: I really need to type faster

---

### Post by chanders on 2006-07-28
> **augied said:**
> I like to only have the places and apps panes visible, but what if I need to access the settings pane (for example to change some settings.)  Right now I would open the menu, open the settings pane, screw up my system, and then reopen the menu to hide the settings pane.  My suggestion is to have a default layout (set in gconf or in the standalone settings app which I am eagerly waiting for) which the menu returns to whenever it is closed.
Now that I think of it, a 'set as default layout' button would fit in nicely in the toggle pane.

Very high on the priority list for the next release ;)

---

### Post by augied on 2006-07-28
> **chanders said:**
> Very high on the priority list for the next release ;)

Great!!

---

### Post by delfick on 2006-07-28
out of interest hows it going with my idea for using the gnome main menu for the "all applications" button (post #149 on this page [http://www.compiz.net/viewtopic.php?id=2112&p=10](http://www.compiz.net/viewtopic.php?id=2112&p=10) )

I think this is the third time i've asked....so sry for the persistance!...but i really want this :D

---

### Post by chanders on 2006-07-28
> **delfick said:**
> out of interest hows it going with my idea for using the gnome main menu for the "all applications" button (post #149 on this page [http://www.compiz.net/viewtopic.php?id=2112&p=10](http://www.compiz.net/viewtopic.php?id=2112&p=10) )

I think this is the third time i've asked....so sry for the persistance!...but i really want this :D

Persistance, gets results...

That is a whole project by itself, but I will put it on my list of things to do...(higher up)  ;)

---

### Post by lazyd2 on 2006-07-28
Is it possible to get the icons in "Places" a bit larger?

---

### Post by atie on 2006-07-28
First of all, thanks for fixing the hex color thing. :D 

*"Not sure how to implement a search and filter simultaneously without adding two entry boxes  Any ideas?"*

Here is (hopefully) idea for the above.

Under "System Management", place beagle-search with icon if system has it. This is because of the nice thing that those icons under "System Management" are always visible.

Then, user presses "beagle-search" button (or icon), the "Search" button is labelled with "Search" as same as current. And, execute beagle-search for search term entered. (I am not quite sure "Gnome File search" is alternatively needed for this search function.)

If "Applications" is not shown but "beagle-search" is pressed, display "Applications" to receive user input for search term.

For the systems not having "beagle-search", Of course not displaying "beagle-search" and "Search" button is labelled with "Filter" maybe. 

**But, I'd like to see, for instance, "nau" + [tab] + [tab] (such as bash completion) brings complete command and "Filter" changed to "Run"   subsequently.**

Basically this idea is about combining deskbar-applet and alt-f2 "Run Application" so probably "Run in terminal" will be requested later I guess. :smile:

I hope this draws your interest, and thanks again! chanders.

---

### Post by chanders on 2006-07-28
> **lazyd2 said:**
> Is it possible to get the icons in "Places" a bit larger?

You got it! - Next release

---

### Post by chanders on 2006-07-28
> **atie said:**
> First of all, thanks for fixing the hex color thing. :D 

*"Not sure how to implement a search and filter simultaneously without adding two entry boxes  Any ideas?"*

Here is (hopefully) idea for the above.

Under "System Management", place beagle-search with icon if system has it. This is because of the nice thing that those icons under "System Management" are always visible.

Then, user presses "beagle-search" button (or icon), the "Search" button is labelled with "Search" as same as current. And, execute beagle-search for search term entered. (I am not quite sure "Gnome File search" is alternatively needed for this search function.)

If "Applications" is not shown but "beagle-search" is pressed, display "Applications" to receive user input for search term.

For the systems not having "beagle-search", Of course not displaying "beagle-search" and "Search" button is labelled with "Filter" maybe. 

**But, I'd like to see, for instance, "nau" + [tab] + [tab] (such as bash completion) brings complete command and "Filter" changed to "Run"   subsequently.**

Basically this idea is about combining deskbar-applet and alt-f2 "Run Application" so probably "Run in terminal" will be requested later I guess. :smile:

I hope this draws your interest, and thanks again! chanders.

This is an excellent idea, but implementing it now would be double work as in the near future I am hoping to integrate deskbar searches with USP... Then you have all the USP goodness with Deskbar :D

---

### Post by lazyd2 on 2006-07-28
> **chanders said:**
> You got it! - Next release
Great and thank you for the time and effort you put on this project

---

### Post by delfick on 2006-07-28
> **chanders said:**
> Persistance, gets results...

That is a whole project by itself, but I will put it on my list of things to do...(higher up)  ;)

excellent...(Simpsons style)

---

### Post by augied on 2006-07-28
> **chanders said:**
> I am hoping to integrate deskbar searches with USP

How exactly will that work?

---

### Post by Note360 on 2006-07-28
Make it so the all applications menu (good job at implementing the whole application browser thing) updates so that I dont have to reboot to see my new apps (have the frequency set to never and then let it be changed in gconf)

---

### Post by chanders on 2006-07-28
> **Note360 said:**
> have the frequency set to never and then let it be changed in gconf)

Dont really understand, it's kinda late ;)

---

### Post by chanders on 2006-07-28
> **augied said:**
> How exactly will that work?

Search field will bring up results similar to what deskbar brings up... (maybe in a new pane or popup)

---

### Post by Note360 on 2006-07-28
Erhm, the rate at which it looks over the directory inorder to display everything in the all applications panel. Does that make sense? It is kinda late for me aswell.

---

### Post by chanders on 2006-07-29
> **Note360 said:**
> Erhm, the rate at which it looks over the directory inorder to display everything in the all applications panel. Does that make sense? It is kinda late for me aswell.

Ok I understand now... The thing is, I wish there was some way to find out from GNOME when something new is installed.... I will have to look into it...

I guess in the interim I could poll every x minutes or something, or even a manual check...

---

### Post by Note360 on 2006-07-29
Sorry I was guessing as to how it works because I dont know I assmued you where indexing a directory or something

---

### Post by augied on 2006-07-29
> **chanders said:**
> Search field will bring up results similar to what deskbar brings up... (maybe in a new pane or popup)

That sounds to me like a job for a separate pane (plugin?)
BTW does anyone know if the deskbar has gotten less buggy.  Whenever I've tried it (I love it by the way) it's crashed the gnome panel.

---

### Post by RawMustard on 2006-07-29
Hi chanders, as I said to you on compiz-forums, this is turning out just wonderfully :)

Now, if we're going to use these two wonderfull apps as a replacement for the gnome-menubar, we need to be able to drag apps from USP to anywhere we want.  For instance, if I open Control Center, how can I add apps to the custom section from USP?  Soon as I click to drag, USP will launch that app.

---

### Post by QUASAR_FREAK on 2006-07-29
a pixmap button for the applet so we can theme that like the common main button, and if you like a theme engine or somethin like the kbfx, but thats no important the button yes =)

---

### Post by PsyberOneZero on 2006-07-29
How about adding a text label to the left side of the panel with the distrobution name (Dapper Drake 6.06 LTS, Edgy Eft 6.10) Kinda like in windows but much better of course ;)
see attachment

---

### Post by LordMau on 2006-07-29
Looking forward how you implement the deskbar incorporation. Maybe the presence of a search bar within the panel, then user-customization of what actually get launches either simple gnome-search-tool up to beagle. Although I'd suggest if possible as a default have something as a paradigm like the xfce verve commandline plugin.

One thing more, maybe can you provide customization to which file browser launches when clicking a folder in Places. Me I prefer thunar rather than nautilus. At present I don't see a gconf key to modify this.

Thanks!

---

### Post by _simon_ on 2006-07-29
Larger favourite applications icons - or option to have them larger(?)
Option to have Favourite applications spaced closer together.
"All Applications" removed and substituted with a down arrow perhaps? - just looks out of place at the moment.
Ability to add Shared folders from another machine to the places menu.
Ability to add to Computer menu - drag & drop
Remove Settings / Applications / places buttons and use gconf key instead - think I saw you were working on something for this though.
Change pin button to something more recognisable - small pin perhaps?

Search type optional - either apps or files or both rather than just both with no choice.

---

### Post by augied on 2006-07-29
Drag toggle buttons to reorder panes.

---

### Post by Hells_Dark on 2006-07-29
Color for pannels title (Places, Applcations).

---

### Post by chanders on 2006-07-29
> **Hells_Dark said:**
> Color for pannels title (Places, Applcations).

/apps/usp/custom_heading_color

---

### Post by Hells_Dark on 2006-07-29
> **chanders said:**
> /apps/usp/custom_heading_color

Things advances too quickly ^_^
So let's go to put some beautiful colors :P
_____________________________________________

yeah ! I know what i would like to see on a next version !
But it will be hard to explain with my poor english.

So, let's go.
What i don't like, that's the cuted icons that wwe see on the screenshots :
[[img]http://pix.nofrag.com/5b/35/6563cf2421679943d7cd25720d9dt.jpg[/img]](http://pix.nofrag.com/5b/35/6563cf2421679943d7cd25720d9d.html)

The "compiz themer" icon and the "evolution mail" icon are cuted.
That's really not pretty, i find.

So, what i would like, that's the ascencor goes down with a "one icon step".

I know that wont be for now, but please, tell me if you understood me, and if it could be possible.

---

### Post by augied on 2006-07-29
Filter/search bar always gets focus when the menu is opened.
Keyboard shortcut to open menu.
Keyboard navigation through filter results (if possible without the filter bar losing focus.)
Clicking enter after typing in the filter bar runs the app at the top of the list.
With these features, it would be possible to open apps without any use of the mouse.

---

### Post by chanders on 2006-07-29
> **Hells_Dark said:**
> Things advances too quickly ^_^
So let's go to put some beautiful colors :P
_____________________________________________

yeah ! I know what i would like to see on a next version !
But it will be hard to explain with my poor english.

So, let's go.
What i don't like, that's the cuted icons that wwe see on the screenshots :
[[img]http://pix.nofrag.com/5b/35/6563cf2421679943d7cd25720d9dt.jpg[/img]](http://pix.nofrag.com/5b/35/6563cf2421679943d7cd25720d9d.html)

The "compiz themer" icon and the "evolution mail" icon are cuted.
That's really not pretty, i find.

So, what i would like, that's the ascencor goes down with a "one icon step".

I know that wont be for now, but please, tell me if you understood me, and if it could be possible.

I understand, but that would be extremely difficult to do... I will try however (not high priority) ;)

---

### Post by chanders on 2006-07-29
> **PsyberOneZero said:**
> How about adding a text label to the left side of the panel with the distrobution name (Dapper Drake 6.06 LTS, Edgy Eft 6.10) Kinda like in windows but much better of course ;)
see attachment

But where would the compact icons go? ;)

---

### Post by chanders on 2006-07-29
> **RawMustard said:**
> Hi chanders, as I said to you on compiz-forums, this is turning out just wonderfully :)

Now, if we're going to use these two wonderfull apps as a replacement for the gnome-menubar, we need to be able to drag apps from USP to anywhere we want.  For instance, if I open Control Center, how can I add apps to the custom section from USP?  Soon as I click to drag, USP will launch that app.

Very true! I this will be high on the priority of fixes...

---

### Post by augied on 2006-07-29
I started to edit this post when it was still the latest in the thread.  But I realize now that I took too long and I'm afraid you might have missed it.  So here it is again.
> **augied said:**
> Filter/search bar always gets focus when the menu is opened.
Keyboard shortcut to open menu.
Keyboard navigation through filter results (if possible without the filter bar losing focus.)
Clicking enter after typing in the filter bar runs the app at the top of the list.
With these features, it would be possible to open apps without any use of the mouse.

---

### Post by chanders on 2006-07-29
> **augied said:**
> I started to edit this post when it was still the latest in the thread.  But I realize now that I took too long and I'm afraid you might have missed it.  So here it is again.

This would come under "Full keyboard support" which will be implemented when most of the bugs are ironed out... ;)

---

### Post by _profox on 2006-07-29
I have a plan for full theming support, the themes would be tar.gz'ed and would be configurable in gconf (or later in a control panel)
You would be able to mix parts of a custom USP theme with parts of your current GTK theme.

I have an analysis of the code that has to be done in my head, I will try to write it down sometime, but if it's up to me, it's low priority, because the current GTK theme support is good enough, for now.

---

### Post by chanders on 2006-07-29
> **_profox said:**
> I have a plan for full theming support, the themes would be tar.gz'ed and would be configurable in gconf (or later in a control panel)
You would be able to mix parts of a custom USP theme with parts of your current GTK theme.

I have an analysis of the code that has to be done in my head, I will try to write it down sometime, but if it's up to me, it's low priority, because the current GTK theme support is good enough, for now.

Actually full theming support shouldnt be too difficult... We will have to meet on IRC for that.. ;)

---

### Post by _profox on 2006-07-29
No, it's not too difficult :) But I like to plan good theming support that is flexible enough to be hybrid (some things from the usp theme, some things from your gtk theme) and that can be switched on/off
I will try to write it down tomorrow, as I am going to sleep real soon...

IRC: what server/channel ? I am always on irc.freenode.net when I'm on irc, you could register a channel #usp there :) or do you already have one?

Anyway, I'll talk to you tomorrow. I will probably be sleeping through the next release :( ;) good luck with it

---

### Post by RawMustard on 2006-07-29
> **RawMustard]
Now, if we're going to use these two wonderful apps as a replacement for the gnome-menubar, we need to be able to drag apps from USP to anywhere we want. For instance, if I open Control Center, how can I add apps to the custom section from USP? Soon as I click to drag, USP will launch that app.[/quote]

[QUOTE=chanders said:**
> Very true! I this will be high on the priority of fixes...

Fantastic.  Once you get dragging and dropping working, you can change the way we order stuff in places and favourites.  Would be much better than right clicking to order things :)

---

### Post by gruvsyco on 2006-07-30
I would love to see a well written how to on making the menu transparent.

---

### Post by chanders on 2006-07-30
> **gruvsyco said:**
> I would love to see a well written how to on making the menu transparent.

Well for starters, USP is of window type "Menu". So in compiz, using the state plugin you can set the opacity....  I will do some research and do a HowTo (Unless someone beats me to it ;))

---

### Post by _simon_ on 2006-07-30
I'm sure I posted the reply to this... de-ja-vu!

You can use the following to set opacity SPECIFICALLY for USP.

Gconf -> apps -> compiz -> plugins -> state -> screen0 -> options -> opacity

Double click on the opacity key and use ADD.

I use

c:Usp:80

This way you can set the opacity specifically for USP without impacting on your global menu setting if you have one.

---

### Post by gruvsyco on 2006-07-30
Thanks guys, I found the post at Compiz that I had seen earlier and posted it over in the Howto.

---

### Post by chanders on 2006-07-30
> **_simon_ said:**
> I'm sure I posted the reply to this... de-ja-vu!

You can use the following to set opacity SPECIFICALLY for USP.

Gconf -> apps -> compiz -> plugins -> state -> screen0 -> options -> opacity

Double click on the opacity key and use ADD.

I use

c:Usp:80

This way you can set the opacity specifically for USP without impacting on your global menu setting if you have one.

Nice! You could also post this in the 'How-to' section so it would be easy to find and you wont have to do it a third time :D

---

### Post by _simon_ on 2006-07-30
> **chanders said:**
> Nice! You could also post this in the 'How-to' section so it would be easy to find and you wont have to do it a third time :D

gruvsyco has beaten me to it :)

Would it be possible to have an gconf entry to change the text colour in USP?

---

### Post by _profox on 2006-07-30
@_simon_: I will work on that :) shouldn't be too hard with the code that's already available

---

### Post by Fluffy, the jolly sheep on 2006-07-30
My (probably far too long) feature requests list, in order of preference:

1. having the places pane share bookmarks with the places system of nautilus & the original menu, since they serve the same purpose. It would also be easier when using a removable hard drive. The network items could be placed in a cascading menu to save some space and the removable drives too, if there are too many.

2. having a 'favorites' category as the first category in the application pane when it's in 'all applications' mode. This category could be active by default when opening the menu. I normally only use the 'all applications' mode because I open too many applications frequently to make efficient use of the current favorites mode. Having a favorites category in all applications mode would allow me to have the best of both.

3. some minor ui changes:
* having the button of an application category in a pressed state when the category is active (because now you have to scan the list of apps to see which category is shown)
* there is a pane seperator at the left border when the toggle pane is hidden, it should be hidden too
* having the buttons in favorites mode to be left aligned, and having an ellipsis (...) when the text is too long

4. being able to move the system panel with the middle mouse button like the other panel items

5. When the favorites pane isn't full, having it automatically fill up with the most used applications

6. Other colors for every pane (like the SLED menu), so you can distinguish them very fast.

---

### Post by augied on 2006-07-30
> **Fluffy, the jolly sheep said:**
> having the places pane share bookmarks with the places system of nautilus & the original menu, since they serve the same purpose.

I've been requesting this for a while now.  I don't know how the removable storage, network locations, and default gnome locations can be done.  But the bookmarks that you add yourself in nautilus are all stored in ~/.gtk-bookmarks.
The syntax for the file is ```
file:///path/to/file filename
``` (the filename at the end is optional if you want it named differently from the actual file (ex. capitalized)).
From what I understand (from looking at the file structure of the deb package) USP coul simply parse out the 'file://' and it would be the same as the file already used.  The problem is that it also creates desktop files for all of the places, and as far as I can tell, nautilus does not.  My solution is that when USP is first started, it checks the gtk-bookmarks file for new places, and creates desktop files for them.  A simpler solution would be to not use desktop files for the places, but I don't know enough about the actual code to know if that's an option.
Please correct me if I completely clueless on any points.

---

### Post by chanders on 2006-07-30
> **Fluffy, the jolly sheep said:**
> My (probably far too long) feature requests list, in order of preference:

1. having the places pane share bookmarks with the places system of nautilus & the original menu, since they serve the same purpose. It would also be easier when using a removable hard drive. The network items could be placed in a cascading menu to save some space and the removable drives too, if there are too many.

Some of this will make it in the next release...


> **Fluffy, the jolly sheep said:**
> 
2. having a 'favorites' category as the first category in the application pane when it's in 'all applications' mode. This category could be active by default when opening the menu. I normally only use the 'all applications' mode because I open too many applications frequently to make efficient use of the current favorites mode. Having a favorites category in all applications mode would allow me to have the best of both.

Nice idea. Will be implemented in the next release

> **Fluffy, the jolly sheep said:**
> 
3. some minor ui changes:
* having the button of an application category in a pressed state when the category is active (because now you have to scan the list of apps to see which category is shown)
* there is a pane seperator at the left border when the toggle pane is hidden, it should be hidden too
* having the buttons in favorites mode to be left aligned, and having an ellipsis (...) when the text is too long

Will try it, and see how it looks...

> **Fluffy, the jolly sheep said:**
> 
4. being able to move the system panel with the middle mouse button like the other panel items


> **Fluffy, the jolly sheep said:**
> 
5. When the favorites pane isn't full, having it automatically fill up with the most used applications

Gnome doesnt support this YET unless it is PATCHED

> **Fluffy, the jolly sheep said:**
> 
6. Other colors for every pane (like the SLED menu), so you can distinguish them very fast.

Shouldnt be too difficult to implement

> **augied said:**
> I've been requesting this for a while now.  I don't know how the removable storage, network locations, and default gnome locations can be done.  But the bookmarks that you add yourself in nautilus are all stored in ~/.gtk-bookmarks.
The syntax for the file is ```
file:///path/to/file filename
``` (the filename at the end is optional if you want it named differently from the actual file (ex. capitalized)).
From what I understand (from looking at the file structure of the deb package) USP coul simply parse out the 'file://' and it would be the same as the file already used.  The problem is that it also creates desktop files for all of the places, and as far as I can tell, nautilus does not.  My solution is that when USP is first started, it checks the gtk-bookmarks file for new places, and creates desktop files for them.  A simpler solution would be to not use desktop files for the places, but I don't know enough about the actual code to know if that's an option.
Please correct me if I completely clueless on any points.

I am working on getting the bookarks file in USP. Anyone have any idea where NAUTILUS stores information for USB plugged drive/CD/Floppy? That would help tremendously...

---

### Post by augied on 2006-07-30
> **chanders said:**
> Anyone have any idea where NAUTILUS stores information for USB plugged drive/CD/Floppy?

I'm researching this.  I haven't found anything yet.

---

### Post by chanders on 2006-07-30
> **augied said:**
> I'm researching this.  I haven't found anything yet.

Thank you! Your research will help greatly... The more people help the faster we get the features we want ;)

@All readers
You dont have to be a programmer to do research. You just need to ask questions and the GNOME developers ar the guys with the answers ;)

---

### Post by augied on 2006-07-30
I've found a few references to the GnomeVFSVolumeMonitor which "provides asynchronous notification of mount/unmount events."  That looks promising, however that little quote is the clearest documentation I've found.  I did manage to dig up this [http://developer.gnome.org/doc/API/2.0/gnome-vfs-2.0/gnome-vfs-20-gnome-vfs-volume-monitor.html](http://developer.gnome.org/doc/API/2.0/gnome-vfs-2.0/gnome-vfs-20-gnome-vfs-volume-monitor.html) but I haven't found a python equivalent (also, I barely know anything about C, so for all I know that might be totally unrelated.  On the other hand, I may have just made a major breakthrough without knowing it.  Please let me know if that's the case.)  Hope it helps.

---

### Post by chanders on 2006-07-30
> **augied said:**
> I've found a few references to the GnomeVFSVolumeMonitor which "provides asynchronous notification of mount/unmount events."  That looks promising, however that little quote is the clearest documentation I've found.  I did manage to dig up this [http://developer.gnome.org/doc/API/2.0/gnome-vfs-2.0/gnome-vfs-20-gnome-vfs-volume-monitor.html](http://developer.gnome.org/doc/API/2.0/gnome-vfs-2.0/gnome-vfs-20-gnome-vfs-volume-monitor.html) but I haven't found a python equivalent (also, I barely know anything about C, so for all I know that might be totally unrelated.  On the other hand, I may have just made a major breakthrough without knowing it.  Please let me know if that's the case.)  Hope it helps.

Excellent work! That is just what I was looking for!! Will let you guys know how it progresses...

---

### Post by augied on 2006-07-30
Here's something interesting.
[http://www.gnome.org/~jamesh/code/gvfs-list-drives.c](http://www.gnome.org/~jamesh/code/gvfs-list-drives.c)
I found it here
[http://blogs.gnome.org/view/jamesh/2005/12/17/0](http://blogs.gnome.org/view/jamesh/2005/12/17/0)
(This blog seems to have lots of good info.  I'm going to read more from it.)
This program "dump[s] all the data provided by GnomeVFSVolumeMonitor" which includes 'User visible: true/false' for each volume.  The user visible volumes are the ones which show up in the gnome places menu, nautilus, etc.

---

### Post by chanders on 2006-07-30
> **augied said:**
> Here's something interesting.
[http://www.gnome.org/~jamesh/code/gvfs-list-drives.c](http://www.gnome.org/~jamesh/code/gvfs-list-drives.c)
I found it here
[http://blogs.gnome.org/view/jamesh/2005/12/17/0](http://blogs.gnome.org/view/jamesh/2005/12/17/0)
(This blog seems to have lots of good info.  I'm going to read more from it.)
This program "dump[s] all the data provided by GnomeVFSVolumeMonitor" which includes 'User visible: true/false' for each volume.  The user visible volumes are the ones which show up in the gnome places menu, nautilus, etc.

Very well done... thanks to you, this has gotten even easier (relatively ;))

---

### Post by augied on 2006-07-30
[http://www.pygtk.org/pygnomevfs/index.html](http://www.pygtk.org/pygnomevfs/index.html)

---

### Post by Fluffy, the jolly sheep on 2006-07-30
Thanks for your response chanders. I'm certain the next release of usp will rock even more!

> **chanders said:**
> 
[QUOTE=Fluffy, the jolly sheep;1317183]5. When the favorites pane isn't full, having it automatically fill up with the most used applications

Gnome doesnt support this YET unless it is PATCHED
[/QUOTE]

Is it possible to just count the number of times the application has been opened using usp (counting how many times the button has been clicked in the applications pane)? Because it seems to me that these are the actions that would benefit the most from a shortcut. An application opened by a launcher on the gnome panel wouldn't be counted then and that's okay because it doesn't need yet another shortcut on the usp.

---

### Post by _profox on 2006-07-30
That could be a possibility :) good thinking

---

### Post by chanders on 2006-07-31
> **Fluffy, the jolly sheep said:**
> Thanks for your response chanders. I'm certain the next release of usp will rock even more!



Is it possible to just count the number of times the application has been opened using usp (counting how many times the button has been clicked in the applications pane)? Because it seems to me that these are the actions that would benefit the most from a shortcut. An application opened by a launcher on the gnome panel wouldn't be counted then and that's okay because it doesn't need yet another shortcut on the usp.

It is very possible, but this is assuming that you us USP ONLY to launc applications. Applications launched from the Desktop/Panel/Original gnome menu would not count... It is easy to implement if you are using USP only.

---

### Post by lazyd2 on 2006-07-31
> **chanders said:**
> It is very possible, but this is assuming that you us USP ONLY to launc applications. Applications launched from the Desktop/Panel/Original gnome menu would not count... It is easy to implement if you are using USP only.
Why use anything else than USP...?:D ;)

---

### Post by Fluffy, the jolly sheep on 2006-07-31
> **chanders said:**
> It is very possible, but this is assuming that you us USP ONLY to launc applications. Applications launched from the Desktop/Panel/Original gnome menu would not count... It is easy to implement if you are using USP only.
I think it's fairly reasonable to just take USP into account.

The goal of the favorites pane is to provide an faster way to launch a frequently used application. But if the app is already on the panel, it's probably easier anyway to use that launcher instead of USP. So I think it won't be useful to have yet an additional shortcut on USP. 
As for the original gnome menu, well ... as lazyd2 said, if you've already got usp on your panel, why would anyone still use the original menu :) ?
Only problem can be desktop launchers, for which the argument for panel launchers can go up too, but not all of the time. Kind of depends on usage pattern I guess (whether the user prefers to use the menu or to use the show desktop button when the launcher is covered by an application). But the number of times the app is launched from USP probably is a good enough statistic.

---

### Post by chanders on 2006-07-31
> **Fluffy, the jolly sheep said:**
> I think it's fairly reasonable to just take USP into account.

The goal of the favorites pane is to provide an faster way to launch a frequently used application. But if the app is already on the panel, it's probably easier anyway to use that launcher instead of USP. So I think it won't be useful to have yet an additional shortcut on USP. 
As for the original gnome menu, well ... as lazyd2 said, if you've already got usp on your panel, why would anyone still use the original menu :) ?
Only problem can be desktop launchers, for which the argument for panel launchers can go up too, but not all of the time. Kind of depends on usage pattern I guess (whether the user prefers to use the menu or to use the show desktop button when the launcher is covered by an application). But the number of times the app is launched from USP probably is a good enough statistic.

Ok, well it's all about options right? I will try to get this in a subsequent release... Not promising for the next but you never know...

---

### Post by Hells_Dark on 2006-07-31
I know a new patch allows to change the USP button title (which was System).
Wy could'nt we change the button icon too ? :)

---

### Post by _profox on 2006-07-31
> **Hells_Dark said:**
> I know a new patch allows to change the USP button title (which was System).
Wy could'nt we change the button icon too ? :)

I will work on it this instant ;) I hope I can get it done before the next release, or you'll have to wait for the release after that ;) hehe
(or apply my patch yourself)

I'll do my best, sirO:)

---

### Post by _profox on 2006-07-31
> **Hells_Dark said:**
> I know a new patch allows to change the USP button title (which was System).
Wy could'nt we change the button icon too ? :)

Patch is done, but needs a little more work because the icon won't autohide on start, and I'm researching this, but I have to sleep now. Tomorrow I'll probably release the full patch.

See here to keep up to date:
[https://launchpad.net/products/usp/+bug/54745](https://launchpad.net/products/usp/+bug/54745)

---

### Post by Hells_Dark on 2006-08-01
You rock guys ^_^
Thanks to you all.

---

### Post by _profox on 2006-08-01
Found the issue. Icon wouldn't hide because gtk.main() gets executed after the most code, I fixed this by adding a function to gobject.idle_add, so it gets called back when the main loop is done, causing it to work. Patch is coming up very soon now.

edit: patch is available at [https://launchpad.net/products/usp/+bug/54745](https://launchpad.net/products/usp/+bug/54745)
and I mailed chanders. Let's hope he accepts the patch..

edit 2: with this patch you get 3 new gconf entries in /apps/usp:
button_customicon: try setting this to things like:
[LIST]
[*]computer
[*]go-down
[*]gnome-system
[*]gnome-settings
[*]and other icons you can find in /usr/share/icons/ for your current theme
[/LIST]
button_customtext: try setting this to something like "Menu" or "Ubuntu"
button_hide_icon: check this box to hide the icon and show only the text

to only show the icon, and not the text, just make button_customtext empty

---

### Post by augied on 2006-08-01
I don't know if you are already planning to do this or not, it seems to me like a pretty obvious choice, but I'll suggest it anyway.
Completely modularize (is that a word?) the program.  When that plugin system we keep hearing about is done, remove the places, applications, and settings panes from the main program and make them plugins.

---

### Post by _profox on 2006-08-01
> **augied said:**
> I don't know if you are already planning to do this or not, it seems to me like a pretty obvious choice, but I'll suggest it anyway.
Completely modularize (is that a word?) the program.  When that plugin system we keep hearing about is done, remove the places, applications, and settings panes from the main program and make them plugins.
I think that's the plan, and I think it's a good idea :)

---

### Post by Corey on 2006-08-02
Just discovered this project and it is fantastic! 2 things fromt the novel panel I really want is a favorites and recently used apps tab. recent documents or just a recently used (apps and docs) section would be mighty handy. The cool thing about the favorites tab is that its custom tailored to your preferences. The cool thing about the recently used tab is that its programmatically created based on your usage. Also beagle search is grand in the Novell panl, but deskbar is grander =) It'd be nice if the deskbar was integrated into this!

---

### Post by chanders on 2006-08-02
> **Corey said:**
> Just discovered this project and it is fantastic! 2 things fromt the novel panel I really want is a favorites and recently used apps tab. recent documents or just a recently used (apps and docs) section would be mighty handy. The cool thing about the favorites tab is that its custom tailored to your preferences. The cool thing about the recently used tab is that its programmatically created based on your usage. Also beagle search is grand in the Novell panl, but deskbar is grander =) It'd be nice if the deskbar was integrated into this!

The 'Applications' section is the eqivalent to the 'Favourites' in SLED. If you click on 'All Application' and right click on an item you can choose "Add to Favourites"

Recently used apps/docs is easy to do and will be coming up in a subsequent release

Deskbar is also planned..

---

### Post by _simon_ on 2006-08-02
Had a few thoughts, not sure if they have been covered though.

1. Instead of / as well of compacting System Management to the toggle pane, it would fit nicely where it originally was but in compact icon format horizontally.

2. Option to turn off headings which would intern reduce menu height.

3. Replace Search button with magnifying glass.

4. Option to just display text instead of text+icons.

5. Option to change text colour! (already requested - not sure if going ahead?)

6. Rounded corners to make it more menu like.

---

### Post by _profox on 2006-08-02
Wow, okay, thanks for all the suggestions. Can't promise to get everything in the next release, but I'll work on some of it.
Text colour is one thing that will be there in next release for sure btw

---

### Post by _simon_ on 2006-08-02
Got another! :)

Could the seperator line be thinner? 

I currently have a black background and the seperator is grey and quite thick - it looks ugly.

I keep looking at the search box... it's an odd size and the size increases when you view all applications. Maybe the favourites and all applications pane should be the same size so that the search bar stays the same size?

Personally I think it should be the full width of the pane (if favourites and all applications were the same size) with the magnifying glass instead of search :)

One more thing (for now) in All Applications would it be possible to make the scroll bar thinner?

Edit - like the Vista one - see pic

---

### Post by delfick on 2006-08-02
is it possible for u to make it have real transparency (only the background is transparent...text and icons stay non-transparent)

and then a step further make everything behind it blurred

??

that would be $@#%ing awsome ! :D

...

---

### Post by Hells_Dark on 2006-08-02
I would like to be able to hide some things.
I would like to be able to hide the search box for example.

---

### Post by cantormath on 2006-08-02
I would like to see that all the hardware in the world works with linux.

---

### Post by delfick on 2006-08-02
<offtopic>
> **cantormath said:**
> I would like to see that all the hardware in the world works with linux.

along with all the games in the world (especially gta:san andreas)

</offtopic>

---

### Post by _simon_ on 2006-08-02
I'd like the ability to drag the Quit button into any part of USP I like... currently it won't allow it.

(I have the system bit totally hidden)

---

### Post by Enginerd on 2006-08-02
> **_simon_ said:**
> I'd like the ability to drag the Quit button into any part of USP I like... currently it won't allow it.

(I have the system bit totally hidden)

If you have the tab bar open then you can reduce the system stuff to icons on it. See screenie

---

### Post by _simon_ on 2006-08-02
> **Enginerd said:**
> If you have the tab bar open then you can reduce the system stuff to icons on it. See screenie

Yeah I know but I have that hidden too ;)

---

### Post by zootreeves on 2006-08-02
When you click back on the gnome-panel (or anywhere else on the screen) it should close USP. i.e. you shouldn't be able to have the gnome-panel Aplications menu and the USP menu open at the sametime. Hope that makes sense :)

---

### Post by chanders on 2006-08-02
> **zootreeves said:**
> When you click back on the gnome-panel (or anywhere else on the screen) it should close USP. i.e. you shouldn't be able to have the gnome-panel Aplications menu and the USP menu open at the sametime. Hope that makes sense :)

Makes perfect sense. This is the #1 bug right now that we have to work on..:wink:

---

### Post by Briquet on 2006-08-02
Hi, I got an idea but is kind of different to the right now job's direction:
The USP right now:
1) Has 3 main windows that can be shown at the same time
2) If you change the options to include places or take out system the main window does a little movement before changing, like jumping (unless you got the three options opened)
3) Some options cannot be shown completely because of space.

Considering that you just can pick one option at a time so why to have many options show at the same time? this idea is based on the UCC (which I consider just perfect), is like integrating UCC and USP:
keeping the same size window and the options places, applications and settings at one side but when you pick one you'll see the whole options of that category displayed in the space of the whole window(like in the UCC where you got the menus at one side and when you pick one all the options in that category are shown) this way:
1) The usability won't be affected having the idea that you just select one option at the same time
2) You'll have more space (better looking and you could add easily another options like gdeskbar or beagle if you want)
3) The window will remain in the same size so won't be jumping when you change from one option to another 
4) You'll able to include the complete UCC in the option Settings and not only four alternatives and the control panel.

Of course another menu to include your favorite programs would help a lot (but this should not only include applications but also places or settings options), like having the fast menu (your personalized menu of all) and the complete menu with all the options shown this way.

I know how hard you've worked until know and you have done a terrific job! so take this as another point of view.

Cheers

---

### Post by chanders on 2006-08-02
> **Briquet said:**
> Hi, I got an idea but is kind of different to the right now job's direction:
The USP right now:
1) Has 3 main windows that can be shown at the same time
2) If you change the options to include places or take out system the main window does a little movement before changing, like jumping (unless you got the three options opened)
3) Some options cannot be shown completely because of space.

Considering that you just can pick one option at a time so why to have many options show at the same time? this idea is based on the UCC (which I consider just perfect), is like integrating UCC and USP:
keeping the same size window and the options places, applications and settings at one side but when you pick one you'll see the whole options of that category displayed in the space of the whole window(like in the UCC where you got the menus at one side and when you pick one all the options in that category are shown) this way:
1) The usability won't be affected having the idea that you just select one option at the same time
2) You'll have more space (better looking and you could add easily another options like gdeskbar or beagle if you want)
3) The window will remain in the same size so won't be jumping when you change from one option to another 
4) You'll able to include the complete UCC in the option Settings and not only four alternatives and the control panel.

Of course another menu to include your favorite programs would help a lot (but this should not only include applications but also places or settings options), like having the fast menu (your personalized menu of all) and the complete menu with all the options shown this way.

I know how hard you've worked until know and you have done a terrific job! so take this as another point of view.

Cheers

I appreciate you input ;) This idea is not very difficult to accomplish. It would take some work but is very doable. The thing is, how many people would like this as an option...

The reason USP is different from UCC is because you can get info _about_ a lot more albeit less :wink: 

Why dont you start a poll thread and maybe a simple mockup of your design and if enough people want it, we will implement this..

Looking forward to the mockups (hint: cut and paste screenshots are your friends)

---

### Post by Hells_Dark on 2006-08-02
> **Hells_Dark said:**
> I would like to be able to hide some things.
I would like to be able to hide the search box for example.
yeah. I know.

It would be great if there were an option to change the search box into a command box ! :)

---

### Post by chanders on 2006-08-02
> **Hells_Dark said:**
> yeah. I know.

It would be great if there were an option to change the search box into a command box ! :)

The command box is doable (in cgonf maybe a key that says searce/command?)
Actually it would 'emulate' the command box as autocompletion etc will not work. I am not sure if there are any libraries that allow this..

[COLOR="Red"]*[/COLOR]As for the ability to hide the search box, I will put it in the next release..

---

### Post by Briquet on 2006-08-02
> **chanders said:**
> I appreciate you input ;) This idea is not very difficult to accomplish. It would take some work but is very doable. The thing is, how many people would like this as an option...

The reason USP is different from UCC is because you can get info _about_ a lot more albeit less :wink: 

Why dont you start a poll thread and maybe a simple mockup of your design and if enough people want it, we will implement this..

Looking forward to the mockups (hint: cut and paste screenshots are your friends)

Yeah I agree with you, users should be consulted first. I'll do the mockup.

---

### Post by Corey on 2006-08-02
> **chanders said:**
> The 'Applications' section is the eqivalent to the 'Favourites' in SLED. If you click on 'All Application' and right click on an item you can choose "Add to Favourites"

Recently used apps/docs is easy to do and will be coming up in a subsequent release

Deskbar is also planned..
Ooh wow, I love it when features are already implemented I just didn't know how to use them. Looking forward to deskbar and recently used. There is one feature that is missing though. Its from the normal gnome-panal. I can't drag an application onto a panal to make a launcher or onto the desktop to make a shortcut like I could with the original gnome-panal. Kinda important I think. 

Anyway wonderful job!

---

### Post by chanders on 2006-08-02
> **Corey said:**
> Ooh wow, I love it when features are already implemented I just didn't know how to use them. Looking forward to deskbar and recently used. There is one feature that is missing though. Its from the normal gnome-panal. I can't drag an application onto a panal to make a launcher or onto the desktop to make a shortcut like I could with the original gnome-panal. Kinda important I think. 

Anyway wonderful job!

Drag and Drop definitely needs some work (source of the phantom icons ;)) This will need to be re-implemented to remove these issues. A timeline for this is not available at this moment though... sorry :???:

---

### Post by chanders on 2006-08-02
> **_simon_ said:**
> Got another! :)

Could the seperator line be thinner? 

I currently have a black background and the seperator is grey and quite thick - it looks ugly.

I keep looking at the search box... it's an odd size and the size increases when you view all applications. Maybe the favourites and all applications pane should be the same size so that the search bar stays the same size?

Personally I think it should be the full width of the pane (if favourites and all applications were the same size) with the magnifying glass instead of search :)

One more thing (for now) in All Applications would it be possible to make the scroll bar thinner?

Edit - like the Vista one - see pic

Do you have custom-colors selected? This might get rid of your 'grey' separator problem. The size is not configurable as it has to be the size of the other buttons (gtk limitation)

[COLOR="Red"]*[/COLOR]The searchbox icon and size will be in the next release

The scrollbar size is also set by your theme, not USP...

---

### Post by hazart on 2006-08-02
Not sure if it has been mentioned before. There are two **critical usability features** USP is missing.

[LIST=1]
[*]**Using the absolute corner pixel.** You know how you tend to pull your mouse fast to the bottom left corner and click. This makes it MUCH faster to access the menu! Currently i have to slow down the mouse to find the exact location of the button, which is very frustrating...
[*]**Keyboard shortcuts!** People tend to forget one of the most important aspects of the modern desktop environment. The best desktop would be not using the mouse at all! So PLEASE add something like CTRL + ESC to access the menu. IT'S very important i think.
[/LIST]

Just my two cents.

---

### Post by lazyd2 on 2006-08-02
> **hazart said:**
> Not sure if it has been mentioned before. There are two **critical usability features** USP is missing.

[LIST=1]
[*]**Using the absolute corner pixel.** You know how you tend to pull your mouse fast to the bottom left corner and click. This makes it MUCH faster to access the menu! Currently i have to slow down the mouse to find the exact location of the button, which is very frustrating...
[*]**Keyboard shortcuts!** People tend to forget one of the most important aspects of the modern desktop environment. The best desktop would be not using the mouse at all! So PLEASE add something like CTRL + ESC to access the menu. IT'S very important i think.
[/LIST]

Just my two cents.

1. I don't have that problem...
2. I agree.

---

### Post by _profox on 2006-08-02
I think we can add #2, but I think #1 is handled by gnome-panel.

---

### Post by Hells_Dark on 2006-08-02
> **chanders said:**
> 
[COLOR="Red"]*[/COLOR]As for the ability to hide the search box, I will put it in the next release..
Amazing :)

---

### Post by _profox on 2006-08-02
> **hazart said:**
> Not sure if it has been mentioned before. There are two **critical usability features** USP is missing.

[LIST=1]
[*]**Using the absolute corner pixel.** You know how you tend to pull your mouse fast to the bottom left corner and click. This makes it MUCH faster to access the menu! Currently i have to slow down the mouse to find the exact location of the button, which is very frustrating...
[*]**Keyboard shortcuts!** People tend to forget one of the most important aspects of the modern desktop environment. The best desktop would be not using the mouse at all! So PLEASE add something like CTRL + ESC to access the menu. IT'S very important i think.
[/LIST]

Just my two cents.

#1. What window manager are you using? When I put the applet to the left, I make use of the absolute corner pixel (this is with 0.31 but I think all versions have this)

#2. This will be added in a future release, if you want, you can request the feature on our launchpad as a bug (we will make the type: wishlist)
[https://launchpad.net/products/usp/+filebug](https://launchpad.net/products/usp/+filebug)

---

### Post by mattisking on 2006-08-03
[LIST=1]
[*]Leave the applet icon transparent when clicked.
[*]Font Colors for the "System" label.
[*]An override option for changing the applet icon
[*]A quicker way to get to the gconf settings... and launching gconf-editor would be fine
[*]Better left alignment of applications in list: Can provide screenshot, but basically if text is longer than normal it shoves that item farther to the left making it un-aligned
[*]If I click "System" and then alt-tab to Firefox, usp stays dropped even though I don't have it pinned.
[*]Background image for panel.
[*]Maybe there are some ideas that could come from the gimmee project?
[/LIST]

I love this applet. I've removed the standard Menu's entirely now ever since the support for transparency. Rock on guys/gals.

---

### Post by Gioppo on 2006-08-03
I got a problem.

When I change the USP icon, it is displayed "shrinked" in size, with a border around it. I can't resize the border as it seems there's no option in gconf to do it.

I use gnome with metacity, with OSX icons (tango derived).

---

### Post by _profox on 2006-08-03
> **mattisking said:**
> [LIST=1]
[*]Leave the applet icon transparent when clicked.
[*]Font Colors for the "System" label.
[*]An override option for changing the applet icon
[*]A quicker way to get to the gconf settings... and launching gconf-editor would be fine
[*]Better left alignment of applications in list: Can provide screenshot, but basically if text is longer than normal it shoves that item farther to the left making it un-aligned
[*]If I click "System" and then alt-tab to Firefox, usp stays dropped even though I don't have it pinned.
[*]Background image for panel.
[*]Maybe there are some ideas that could come from the gimmee project?
[/LIST]

I love this applet. I've removed the standard Menu's entirely now ever since the support for transparency. Rock on guys/gals.

[LIST=1]
[*]Leave the applet icon transparent when clicked.
**I think that's not possible with the type of button we use, we might change this in the future though.**
[*]Font Colors for the "System" label.
**I was going to work on it. In the near future I will do this**
[*]An override option for changing the applet icon
**What do you mean? in version 0.31 it is possible to change the icon by using applet_iconname (try putting "computer" for example) However, in 0.31 it is not fully working and you have to restart the applet for the changes to take effect. In the next release this will be fixed (patch is already committed)**
[*]A quicker way to get to the gconf settings... and launching gconf-editor would be fine
**We have a control panel for our menu scheduled**
[*]Better left alignment of applications in list: Can provide screenshot, but basically if text is longer than normal it shoves that item farther to the left making it un-aligned
**I don't know what you mean, but if you mean the all applications section with a few categories ahving their applications farther to the right... That should be fixable. But you mean something else?**
[*]If I click "System" and then alt-tab to Firefox, usp stays dropped even though I don't have it pinned.
**This only happens if you keep the focus on the applet button ("System" button) but we will make it so that you can't alt+tab when opening the menu**
[*]Background image for panel.
**This will come in due time... (Full theming support is planned for a future release)**
[*]Maybe there are some ideas that could come from the gimmee project?
[/LIST]

---

### Post by missmoondog on 2006-08-03
i would like to see standby work on desktops like it does in winblows xp. doesn't work at all in kubuntu dapper on any of my 7 systems! :(

---

### Post by chanders on 2006-08-03
> **missmoondog said:**
> i would like to see standby work on desktops like it does in winblows xp. doesn't work at all in kubuntu dapper on any of my 7 systems! :(

I meant tell me what you would like to see in *USP*... but standby working is good too ;)

---

### Post by mattisking on 2006-08-03
[LIST=1]
[*]Leave the applet icon transparent when clicked.
**I think that's not possible with the type of button we use, we might change this in the future though.**
[COLOR="Blue"]Cool deal.[/COLOR]
[*]Font Colors for the "System" label.
**I was going to work on it. In the near future I will do this**
[COLOR="Blue"]Yay.[/COLOR]
[*]An override option for changing the applet icon
**What do you mean? in version 0.31 it is possible to change the icon by using applet_iconname (try putting "computer" for example) However, in 0.31 it is not fully working and you have to restart the applet for the changes to take effect. In the next release this will be fixed (patch is already committed)**
[COLOR="Blue"]I didn't realize that. Thanks![/COLOR]
[*]A quicker way to get to the gconf settings... and launching gconf-editor would be fine
**We have a control panel for our menu scheduled**
[COLOR="Blue"]Cool.[/COLOR]
[*]Better left alignment of applications in list: Can provide screenshot, but basically if text is longer than normal it shoves that item farther to the left making it un-aligned
**I don't know what you mean, but if you mean the all applications section with a few categories ahving their applications farther to the right... That should be fixable. But you mean something else?**
[COLOR="Blue"]Yes, I think we're on the same page there.[/COLOR]
[*]If I click "System" and then alt-tab to Firefox, usp stays dropped even though I don't have it pinned.
**This only happens if you keep the focus on the applet button ("System" button) but we will make it so that you can't alt+tab when opening the menu**
[COLOR="Blue"]Possibly. I'll need to look further. I'm not sure you need to stop Alt-Tab. Actually I think that's a bad idea. If another application takes focus away, "simply" go away unless pinned of course.[/COLOR]
[*]Background image for panel.
**This will come in due time... (Full theming support is planned for a future release)**
[COLOR="Blue"]Awesome.[/COLOR]
[*]Maybe there are some ideas that could come from the gimmee project?
[/LIST]

---

### Post by _profox on 2006-08-03
Another note on #6: The Novell main-menu (Slab/Uslab) that I have running here for comparison purposes stops the alt+tab when you open it up. The normal GNOME main menu does the same. That's why it seemed the most obvious thing to do to me. But maybe we can fix it the way you want... I'll have to look into that

---

### Post by lazyd2 on 2006-08-03
Don't know if it has been asked, but is it possible to edit the icons(at least in "Places")?

---

### Post by blackened on 2006-08-04
I like what you've done with the new release. You've implemented most of the things I had hacked into 0.27. A few I would like to see added that weren't.

1. Add the option to place the Apps/Places/System/Pin toggle buttons on either the left or right side.

2. The ability to change the panel button and icon size. I had done some dirty hacks on 0.27 to enlarge it to just a dialog sized icon, but it seems you've passed the button sizing to be handled by the panel in the new version. Course I'm no python expert so I might have just missed it.

See screenshot [here]("http://ubuntuforums.org/gallery/data/2/blk_072906.png") for more detail.

Great work and progress guys.

---

### Post by FuzzySkat on 2006-08-04
Add translation support.

---

### Post by _simon_ on 2006-08-04
I'm glad you replaced the search button with an icon but the binoculars are ugly!

Can I suggest the OSX search icon.... I don't know if you are allowed to use it though?

---

### Post by gruvsyco on 2006-08-04
The search icon must be the default search icon for your particular icon theme.  As I sit here and toggle through icon themes that particular icon does indeed change.

---

### Post by delfick on 2006-08-04
how's it going for adding icons to the left toggle pane side thing part of the menu? (in the highlighted section of this screenshot [http://delfick755.googlepages.com/iconsidea.png](http://delfick755.googlepages.com/iconsidea.png) )  
(i know i've asked before but i can't remember where...)

and what i said on post #82 over here [http://ubuntuforums.org/showthread.php?t=224989&page=9](http://ubuntuforums.org/showthread.php?t=224989&page=9)

thnx

---

### Post by _simon_ on 2006-08-04
> **gruvsyco said:**
> The search icon must be the default search icon for your particular icon theme.  As I sit here and toggle through icon themes that particular icon does indeed change.

Strange, I use OSX icons but the icon displaying is NOT an OSX icon :confused:

What's the name of the icon it's using?

Edit: Found it I think... "gtk-find.png" in the "Stock" folder.

Edit: Yes, it was using the above. Renamed and resized the one I want to use!

---

### Post by chanders on 2006-08-04
> **lazyd2 said:**
> Don't know if it has been asked, but is it possible to edit the icons(at least in "Places")?

**Mat** across at compiz.net said this was going to try this patch next. I will contact him and see how it is going. If not I will implement it..

> **blackened said:**
> I like what you've done with the new release. You've implemented most of the things I had hacked into 0.27. A few I would like to see added that weren't.

1. Add the option to place the Apps/Places/System/Pin toggle buttons on either the left or right side.

This will be added but it's not too high up on the priority list :D 

> **delfick said:**
> how's it going for adding icons to the left toggle pane side thing part of the menu? (in the highlighted section of this screenshot [http://delfick755.googlepages.com/iconsidea.png](http://delfick755.googlepages.com/iconsidea.png) )  
(i know i've asked before but i can't remember where...)

and what i said on post #82 over here [http://ubuntuforums.org/showthread.php?t=224989&page=9](http://ubuntuforums.org/showthread.php?t=224989&page=9)

thnx

Last night started implementing the plugins. The icons tie directly with them, so you'll get those icons when the plugins are released ;)

---

### Post by lazyd2 on 2006-08-04
[QUOTE=chanders]Mat across at compiz.net said this was going to try this patch next. I will contact him and see how it is going. If not I will implement it..[/QUOTE]

Thanks :-({|=

---

### Post by jestersmurf on 2006-08-04
I'd like all the cool stuff your doing ported to Kubuntu or just KDE for that matter... 

You do really cool stuff, and I use KDE, tried Gnome for a while, but there are a lot of features in KDE than I need when I work, plus I like the freedom you have in KDE...

But the stuff you make almost make me wanna port back to gnome ;) - If its possible please someone make this for KDE...

Jester

---

### Post by LordMau on 2006-08-04
Under the Computer/ settings panel, you've given the option to customize the links where the assorted short-cuts can lead. For the "Theme" item, can it be changed so that it reflects the theme setting of the present desktop environment, or make it user configurable?

Right now, since i'm running xfce, I've changed the shortcut to this to the equivalent xfce command, but this doesnt reflect on the panel. Looks like it refers only to what is specified under GNOME.

---

### Post by chanders on 2006-08-04
> **LordMau said:**
> Under the Computer/ settings panel, you've given the option to customize the links where the assorted short-cuts can lead. For the "Theme" item, can it be changed so that it reflects the theme setting of the present desktop environment, or make it user configurable?

Right now, since i'm running xfce, I've changed the shortcut to this to the equivalent xfce command, but this doesnt reflect on the panel. Looks like it refers only to what is specified under GNOME.

You are right. It reads the GNOME settings. Is there some gconf key that shows the theme for XFCE?

---

### Post by delfick on 2006-08-04
[Quote=chanders][Quote=delfick]how's it going for adding icons to the left toggle pane side thing part of the menu? (in the highlighted section of this screenshot [http://delfick755.googlepages.com/iconsidea.png](http://delfick755.googlepages.com/iconsidea.png) )
(i know i've asked before but i can't remember where...)

and what i said on post #82 over here [http://ubuntuforums.org/showthread.php?t=224989&page=9](http://ubuntuforums.org/showthread.php?t=224989&page=9)

thnx[/Quote]

Last night started implementing the plugins. The icons tie directly with them, so you'll get those icons when the plugins are released [/Quote]

cool....:D

also...what about my second question about what i said on post #82 at [http://ubuntuforums.org/showthread.php?t=224989&page=9](http://ubuntuforums.org/showthread.php?t=224989&page=9)

(basically are u able to implement real transparency and blur behind the menu...????....or can that only be done through a compiz plugin?)

(excuse my persistance...again)

---

### Post by chanders on 2006-08-04
> **delfick said:**
> cool....:D

also...what about my second question about what i said on post #82 at [http://ubuntuforums.org/showthread.php?t=224989&page=9](http://ubuntuforums.org/showthread.php?t=224989&page=9)

(basically are u able to implement real transparency and blur behind the menu...????....or can that only be done through a compiz plugin?)

(excuse my persistance...again)

Current version of PyGTK doesnt support it, but the next will ;) THEN we'll be able to do some really cool stuff!

---

### Post by delfick on 2006-08-04
> **chanders said:**
> Current version of PyGTK doesnt support it, but the next will ;) THEN we'll be able to do some really cool stuff!

Cool!

when will that be?

---

### Post by chanders on 2006-08-04
> **delfick said:**
> Cool!

when will that be?

Dunno :-k Will have to check into that...

---

### Post by LordMau on 2006-08-04
> **chanders said:**
> You are right. It reads the GNOME settings. Is there some gconf key that shows the theme for XFCE?

I don't think xfce uses gconf to store its configuration. From what I read they use a standard and use the .config folder under each home directory to store settings. To be exact, in my  system, I saw at 

```
~/.config/xfce4/mcs_settings/gtk.xml
```

is where the settings for the theme is stored. The file contents of gtk.xml are

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mcs-option SYSTEM "mcs-option.dtd">

<mcs-option>
	<option name="Gtk/CanChangeAccels" type="int" value="0"/>
	**<option name="Gtk/CursorThemeName" type="string" value="Silver"/>**
	<option name="Gtk/CursorThemeSize" type="int" value="24"/>
	<option name="Gtk/FontName" type="string" value="Sans 10"/>
	<option name="Gtk/KeyThemeName" type="string" value="Default"/>
	<option name="Gtk/ToolbarStyle" type="string" value="icons"/>
	<option name="Net/CursorBlink" type="int" value="1"/>
	<option name="Net/CursorBlinkTime" type="int" value="500"/>
	<option name="Net/DndDragThreshold" type="int" value="8"/>
	<option name="Net/DoubleClickTime" type="int" value="300"/>
	**<option name="Net/IconThemeName" type="string" value="Vista-Inspirate_1.0"/>**
	**<option name="Net/ThemeName" type="string" value="Clearlooks"/>**
	<option name="Xft/Antialias" type="int" value="1"/>
	<option name="Xft/HintStyle" type="string" value="hintfull"/>
	<option name="Xft/Hinting" type="int" value="1"/>
	<option name="Xft/RGBA" type="string" value="none"/>
</mcs-option>

```
I highlighted the relevant items (including the cursor theme). Would it possible to refer here for the panel "Theme" item?

---

### Post by _profox on 2006-08-04
That's very well possible :) if you post it as a bug/wish on launchpad, we will definately look at it. [http://www.launchpad.net/products/usp](http://www.launchpad.net/products/usp)

---

### Post by LordMau on 2006-08-06
> **_profox said:**
> That's very well possible :) if you post it as a bug/wish on launchpad, we will definately look at it. [http://www.launchpad.net/products/usp](http://www.launchpad.net/products/usp)

Hi posted there. :p 

[THEME item]("https://launchpad.net/products/usp/+bug/55366")

[Quit.. under XFCE]("https://launchpad.net/products/usp/+bug/55364")


Hopefully guess what I'm looking forward to is a moreflexible, less gnome-centric USP. Don't mind if the defaults are GNOME long as the end-user is able to adapt those aspects to their own needs.

Thank for letting us mess your project!

---

### Post by chanders on 2006-08-06
> **LordMau said:**
> Hi posted there. :p 

[THEME item]("https://launchpad.net/products/usp/+bug/55366")

[Quit.. under XFCE]("https://launchpad.net/products/usp/+bug/55364")


Hopefully guess what I'm looking forward to is a moreflexible, less gnome-centric USP. Don't mind if the defaults are GNOME long as the end-user is able to adapt those aspects to their own needs.

Thank for letting us mess your project!

Heh heh heh, no problem... The more the merrier..

---

### Post by LordMau on 2006-08-07
I'm curious what is the direction regarding the Recently Used Documents and/or Recently used apps panel item?

I actually am favor in having a Recently Used Doc section in USP.

---

### Post by chanders on 2006-08-07
> **LordMau said:**
> I'm curious what is the direction regarding the Recently Used Documents and/or Recently used apps panel item?

I actually am favor in having a Recently Used Doc section in USP.

As soon as the plugin system is finished, this will be one of the first plugins I will write (or someone else ;))

---

### Post by dcohen on 2006-08-08
Didn't read through the whole thread, but some easier customization would be great for nubs such as myself (like a simple right click to change opacity, color, that kind of thing).  Also, though I guess it'd come with the plugins, some sort of RSS support would be pretty awesome.

---

### Post by chanders on 2006-08-08
> **dcohen said:**
> Didn't read through the whole thread, but some easier customization would be great for nubs such as myself (like a simple right click to change opacity, color, that kind of thing).  Also, though I guess it'd come with the plugins, some sort of RSS support would be pretty awesome.

This is planned but there is only so much I can do in so much time.. Right now I am working on the plugin system and when it is done I will look at the configuration window (Unless someone wants to volunter? ;))

---

### Post by ursula_gb on 2006-08-08
HI Chanders:
I would like to see a new menu icon or have the option to change it, because is kind of big, I don't like so much. 
Bye

---

### Post by chanders on 2006-08-08
> **ursula_gb said:**
> HI Chanders:
I would like to see a new menu icon or have the option to change it, because is kind of big, I don't like so much. 
Bye

You mean the applet icon? This is configurable with gconf-editor in /apps/usp..

It's not that big though.. post a pic lets see how big the button is on yor pc..

---

### Post by ursula_gb on 2006-08-08
> **chanders said:**
> You mean the applet icon? This is configurable with gconf-editor in /apps/usp..

It's not that big though.. post a pic lets see how big the button is on yor pc..

yeap, you were right, not that big, I have changed the applet icon text, but i couldn't change the applet icon size, without the text looks small. 
I went to gconf-editor in /apps/usp and I don't know exactly how to change it.
thanks for your help

---

### Post by mattisking on 2006-08-08
I noticed today when I wanted to go to "About Gnome" that the System entries off the "Main Menu" are not listed anywhere within "All Applications". In pariticular, there is no place for "About Ubuntu" or "About Gnome" or any of the "Help" section that comes with the normal "Main Menu". I think to be an effective replacement that needs to be addressed, maybe even in it's own pane. 

Also, I continue to see some icons not resized properly for some applications (like istanbul).

---

### Post by chanders on 2006-08-09
> **mattisking said:**
> I noticed today when I wanted to go to "About Gnome" that the System entries off the "Main Menu" are not listed anywhere within "All Applications". In pariticular, there is no place for "About Ubuntu" or "About Gnome" or any of the "Help" section that comes with the normal "Main Menu". I think to be an effective replacement that needs to be addressed, maybe even in it's own pane. 

Also, I continue to see some icons not resized properly for some applications (like istanbul).

The icon size is a known bug with low priority... 

I will look into the gmenu implementation to see if I can get it in as I don't want to hard code these items (they create more problems later for none GNOME users)

---

### Post by Eman64 on 2006-08-10
First off, great menu.

Secondly, I'd like to see:
1 - A preferences icon for the menu it's self, like if you right click on the applet. That way you don't have to run gconf-editor every time.

2 - Does anyone elses Control Center button not work? It's frustrating to me.

3 - More preferences. Everyone has already said them.

And lastly, make the thing present time in 12 hour format. I don't like reading 20 o' clock.

Other than that, great

---

### Post by chanders on 2006-08-10
> **Eman64 said:**
> First off, great menu.

Secondly, I'd like to see:
1 - A preferences icon for the menu it's self, like if you right click on the applet. That way you don't have to run gconf-editor every time.

In the works after the plugin system is finished...

> **Eman64 said:**
> 2 - Does anyone elses Control Center button not work? It's frustrating to me.

You didnt read the first post in the main thread, did you ;)  Configurable via gconf or apt-get install gcontrol if you have quinn's repository

> **Eman64 said:**
> 3 - More preferences. Everyone has already said them.

For? The plugin system  will allow you to add nearly anything you like as long as someone does the plugin..

> **Eman64 said:**
> And lastly, make the thing present time in 12 hour format. I don't like reading 20 o' clock.

Other than that, great
Will do for the next release..

---

### Post by hexion on 2006-08-20
1) I would like to integrate cairo-clock into gnome panel clock as a popup...

Better explained..

I would like to have the clock in digital style in the gnome panel, as it is actually, but when I put the mouse over it I'd like it popups an analogic 3D clock like cairo-clock.

2) Same but with weather info. Just the temperature in the panel, and when putting mouse over it, raising a picture with the weather status (rainy sun, cloudy moon... like in gdesklets) and info about the wind, humidity...

3) Being able to modify a menu app just right-clicking it. When I want to edit a menu app I have to go to "alacarte" util and search it there... I think it's more simple just right-clicking it and editing that link (with alacarte too, but more directly)

4) Visual, easy, and integrated applications to set actions in multimedia keyboards and mice. For the keyboard, an application like "keytouch" would be fine, and for mice cloning logitech utilities for windows... or so.

There you have some suggestions ;)

---

