---
title: "What is the most important feature nautilus is lacking?"
date: 2008-01-22
forum: Ubuntu Brainstorm
---

### Post by mangar on 2008-01-22
I don't know if other people can add poll options, if so, please do

---

### Post by kewldude606 on 2008-01-22
- Split view.
- Better performance is always good but Nautilus is fine performance-wise for me.
- Folder breadcrumbs like in Dolphin and Vista where you can not only go back to an above folder by clicking it but go to an "uncle" folder.

---

### Post by mangar on 2008-01-22
There's something I don't understand:
Split views emulates the view mode of Norton commander to some 
degree, but since Nautilus does not support keyboard bound file 
operations, whats the use case? Nautilus uses a totally different usage metaphor - the file browser.

---

### Post by aysiu on 2008-01-22
No *restore from trash* poll option?

---

### Post by mangar on 2008-01-22
There's a 10 options limit.. 
Isn't it a bug, rather than feature?

---

### Post by smartboyathome on 2008-01-22
> **mangar said:**
> There's something I don't understand:
Split views emulates the view mode of Norton commander to some 
degree, but since Nautilus does not support keyboard bound file 
operations, whats the use case? Nautilus uses a totally different usage metaphor - the file browser.

The use cause is that it allows you to compare two or more separate folders side-by-side and allow you to drag-and-drop easily - this is especially useful when you have two folders which are no where near each other on the file system (for example, /media/disk and ~/Pictures/). Rather than have two windows open, you can just split the view of one.

---

### Post by rockin_goliath on 2008-01-22
Dude, we totally need ISO mounting integration. We should be able to mount an ISO of a DVD movie and watch it in totem!

---

### Post by erfahren on 2008-01-22
I'd like to see more information when overwriting an existing file when cutting & pasting

---

### Post by oomingmak on 2008-01-22
Who's the person that voted Nautilus as perfect?

:lolflag:

---

### Post by oomingmak on 2008-01-22
There aren't enough hours in the day for me to list my grievances against Nautilus, but some that immediately spring to mind are:
[COLOR=White].[/COLOR][LIST]
[*]No option for mouse-over selection when Nautilus set to single-click[/LIST][LIST]
[*]No restore from Deleted Items[/LIST][LIST]
[*]No 'Path' columns in folder list view (particularly important if you don't have a 'restore from Deleted Items' facility)[/LIST][LIST]
[*]Column width sizes not retained[/LIST][LIST]
[*]Date column given maximum column width by default (instead of Name column)[/LIST][LIST]
[*]Limited date formats for Date modified column[/LIST][LIST]
[*]Can't set horizontal and vertical icon spacing (same thing applies to desktop)[/LIST][LIST]
[*]Inconsistent naming of Bin (called 'Trash', 'Deleted Items' and 'Wastebasket' all within the same program)[/LIST][LIST]
[*]Incredibly slow when opening folders with over 1000 items in them (like /usr/bin)[/LIST][LIST]
[*]Utterly useless search facility[/LIST][LIST]
[*]No control over what appears in the upper section of Places bar[/LIST][LIST]
[*]No Tooltip display of metadata or notes (so you have to repeatedly right-click and select appropriate tab for every single file and folder)[/LIST][LIST]
[*]No 'Search' context menu on folders (so if you are several folders deep you have to re-type or re-navigate the whole path again just to get back to where you already were).[/LIST][LIST]
[*]Manual folder arrange option makes all folders lurch to the left and doesn't line up with other arrange modes[/LIST][LIST]
[*]Full row select when in list view (means no drag and drop release spot and also can't access folder context menu because there is nowhere to right-click)[/LIST][LIST]
[*]No Invert Selection[/LIST][LIST]
[*]No Undo facility (e.g. ctrl +z to undo a rename)[/LIST][COLOR=White].[/COLOR]
I could easily go on.

---

### Post by ajmal_82 on 2008-01-23
1)I think better context menu's .bette[FONT="Garamond"][SIZE="4"]r sendto..desktop[/SIZE][/FONT] etc:confused:I mean including [SIZE="3"][FONT="Garamond"]how to simple create a shortcut[/FONT][/SIZE].
2)better support for audio player enqueue/play/playlist.
3)[FONT="Times New Roman"][SIZE="3"]restore from trash[/SIZE][/FONT] to original location.:(
4)it will take ages to catch vista but....
[FONT="Times New Roman"][SIZE="3"]better file explorer and drive meter like vista.that shows better information/details about file space/free space[/SIZE][/FONT].
5)integrate search engine.:KS.
6)still many bug fixes.
7)Good cd/dvd writing application like [SIZE="3"]k3b/nero or even better[/SIZE],thats free for Gnome specific.intergrate inside nautilus.
8)Ability to [SIZE="3"]mount iso images[/SIZE] or cd/dvd images  or some other format like
daemon tools.
9)easier nautilus scripts installation and configure.
10)lastly either push wine to limits(wrt installing windows apps) or
provide a [SIZE="3"]alternative to wine[/SIZE].

---

### Post by starfry on 2008-01-23
The single and most annoying thing I find lacking in Nautilus is the lack of drag/drop integration like you get on that other platform.

What I mean is, drag a mail out of Thunderbird and drop it into a folder, etc.

---

### Post by oomingmak on 2008-01-23
> **erfahren said:**
> I'd like to see more information when overwriting an existing file when cutting & pasting
Hear, Hear!   =D>

That drives me absolutely nuts.

---

### Post by zero-9376 on 2008-01-23
I find it ridiculous that gnome/nautilus doesn't have restore from trash and have brought this issue up before.

Another thing that annoys me to no end is the way you cannot drag and drop in list view because nautilus uses full row select as mentioned earlier. So many times I have gone to drop something into my music directory only to find that it has disapearred into the abyss of another sub folder.

That last problem is amplified in Gutsy because the normal solution would be to search for the file I just dropped but nautiluses integrated search is broken because I don't have tracker installed and even when I did have it the results were completely independent of the directory from which I was searching. This is the most important issue for me and I hope it is fixed for hardy.

My last issue is a feature request - that nautilus shows the size of the files selected in the statusbar including folders and their contents. That metadata display idea also seems good, maybe integrate it with the information option in the places pane.

---

### Post by gnomeuser on 2008-01-23
The only feature I really miss is PolicyKit integration so I can edit files outside of my current permission realm. This however is being worked on.

Aside that Nautilus really does work well for me on a day to day basis. The new gvfs port is very snappy (though still not entirely feature complete but that is to be expected).

Another cool feature to integrate would be using an Indexer via Xesam to arrange files, create thumbnails and such in downtime cycles instead of on first folder open. This would fix several problems such as slowness when a big folder is loaded the first time as thumbnails are created. Another issue this would fix would be that arrange by type would for once really work, notice how when you arrange by type it doesn't actually do that, it arranges by extension - thus if you have a mixed folder of images, music, text and video files in various formats (say like a temp. download folder), arranging by type does not actually arrange all your video files in one group, all the images in another.. instead you have one clump of videos, then some music, then some more videos.. and so on.. Making this nicer would be rather a sexy feature to me.

---

### Post by 23meg on 2008-01-24
The switch to gvfs will make it possible to fix many of the common gripes. The gvfs-enabled Nautilus is [now in Hardy, and needs testing]("http://ubuntuforums.org/showthread.php?t=676747").

---

### Post by SeanHodges on 2008-01-24
Many of the issues people have been raising could be fixed by writing a small bash script and placing it in the Nautilus scripts directory. It's a little known feature of Nautilus that you can extend it this way.

Quite a few scripts are already available here (including ISO mounting, rockin_goliath):

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

The one gripe I would have about it is that the scripts aren't tightly integrated into Nautilus, you always have to right-click and go into the Scripts item that appears on the context menu. Also, it's not very well advertised.

In response to anyone who says "I shouldn't need to write a bash script to get X feature!", please just ask if someone else can help you do it if you don't want to do it yourself. I'm tired of this "I want it to work my way, but don't want to do a bit of work to achieve it" attitude.

I voted for performance and bug fixes, but then EVERY application could always do with more of that ;)

---

### Post by zero-9376 on 2008-01-24
Anyone interested in doing nautilus scripts should really have a look at the nautilus-actions packages which is in the repos.
Website:
[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)
I just put together a VERY simple menu item that uses gnome-osd to display the path and filename of the selected file. Whats more it integrates much more nicely into the menu and you can set and icon ALL THROUGH A GUI CONFIGURATION system.

note: the app installs but doesn't appear to put anything in them menus, use nautilus-actions-config from the terminal or run dialog (alt+f2) to make a new action.

EDIT: attached exported schema which should be able to be added using the import function also ensure gnome-osd is installed to make it work

---

### Post by 23meg on 2008-01-24
Even less known is its extensibility via Python (see nautilus-python). But let's not get too far off topic.

---

### Post by gnomeuser on 2008-01-24
> **SeanHodges said:**
> 
I voted for performance and bug fixes, but then EVERY application could always do with more of that ;)

Actually at least the performance statement is untrue, at some point optimizing is outweighted by added complexity. Say you are optimizing for something like showing a menu, once you hit something like show every item in 0.1 sec, there is no gain in doing it faster since the user won't experience it as being any faster. Additionally overoptimizing of this sort both adds complexity which makes the code harder to maintain and harder to learn so you limit your development resources. You also spend your development time on a pointless task when you could be.. fixing bugs or writing a test suite.

The final comment on performance is that to even optimize in the first place we need hard numbers and a way to reproduce them so we know the impact of a change and the ensure that we are not introducing regressions in other parts of the program. Currently I doubt any such test suite exists nor is being run on a regular basis.. so how do we even know the potential sources of suckage?

"Making it faster is always a good idea" is a bit to simplistic, especially when we have no hard data since that makes us apt to make wrong assumptions.

Federico preaches on this at last years FOSDEM:
[http://video.fosdem.org/2007/FOSDEM2007-ProfilingDesktopApplication.ogg](http://video.fosdem.org/2007/FOSDEM2007-ProfilingDesktopApplication.ogg)

---

### Post by SeanHodges on 2008-01-24
> **gnomeuser said:**
> Say you are optimizing for something like showing a menu, once you hit something like show every item in 0.1 sec, there is no gain in doing it faster since the user won't experience it as being any faster.

Whilst I value your point, and I agree in a way, its not quite as simple as that. Optimisation can account for any part of an application, not just a single aspect of it. Just because Nautilus shows it's context menu quickly doesn't mean that time shouldn't be spent optimising it's SMB interface...

> "Making it faster is always a good idea" is a bit to simplistic, especially when we have no hard data since that makes us apt to make wrong assumptions.

True, but unfortunately you can't easily reflect this kind of response in a simple general public poll :)

---

### Post by zero-9376 on 2008-02-01
> **zero-9376 said:**
> nautiluses integrated search is broken because I don't have tracker installed and even when I did have it the results were completely independent of the directory from which I was searching. This is the most important issue for me and I hope it is fixed for hardy.

YAY!!! Nautilus in Hardy has been fixed so that when I remove tracker and restart nautilus search returns to normal! I can't tell you how grateful I am for this, although it would be nice to get this backported to Gutsy (I don't know what changes so it may not need backporting but rather different compilation options).

Note: Running hardy alpha 3 livecd

---

### Post by JPotter on 2008-02-02
need the option to view as list, like in windows. the current option works like view details.  Its small, but i can't stand either view that is available.

---

### Post by Vadi on 2008-02-02
Just split view. If you actually some time to investigate it's features, click on every button and read every description, it already packs a lot.

---

### Post by MaX on 2008-02-03
List view as in windows is in development IIRC.

Thunar is a great alternative if you want good list-view btw
I voted for performance and metadata

---

### Post by arekkusu on 2008-02-05
I am definitely not impressed with Nautilus.

Some of the improvement I can think of right now:

-Performance improvement on folder with lot's of file

-Undo function

-Trash

-Tab would be nice too.

-More configurable (why can't I have a confirm dialog for sending something to the trash for example)

---

### Post by spoilerhead on 2008-02-06
support for additional mouse buttons (just like firefox)

yes i know that its possible to bind mouse buttons to key combinations, but thats just a workaround, not a solution imho

---

### Post by explemonk on 2008-02-06
After reading this thread I have more issues with Nautilus than I did before. ;)  Nautilus is the reason I switched to KDE.  The two things that drove me absolutely insane are:

1. Full row select (I absolutely **hate** this)
2. Can't rename a folder in the side pane in tree view, either with F2 (which would be ideal), or by context menu.  I have to navigate to the parent folder and rename it in the main pane.

If even the first one could be solved, I'd probably go back to Gnome.

---

### Post by FuturePilot on 2008-02-06
Where's Restore From Trash? That's a must in any modern OS. And as far as I know Nautilus is the only major file manager that doesn't do this.

---

### Post by a9bejo on 2008-02-06
Split and tabbed views should really not be implemented into a file manager - These features belong to the responsibility of a window manager.

Floating-style window managers like Metacity, KWin or Fluxbox could take some of the ideas from [tiling window managers](http://en.wikipedia.org/wiki/Tiling_window_manager) like xmonad or wmii, and implement them so that they are easy to understand and use for "normal" users.

Just let me select an arbitrary number of windows and let the window manager arrange them side by side automatically.  Fluxbox already has this for tabs. They should implement an option to lay out "tabs" side by side.  This would be much better as when every single file manager, web browser etc. bakes its own cake.  I mean, managing windows really sounds like a task for a window manager ;).

---

### Post by MaX on 2008-02-06
> **FuturePilot said:**
> Where's Restore From Trash? That's a must in any modern OS. And as far as I know Nautilus is the only major file manager that doesn't do this.

It's fixed in the new gio enhanced nautilus.

I don't know if Thunar does it?

I've never used the restore function once, not even on Windows... I always shift-delete my files. If I want them gone they should be gone. if not I'll move them somewhere else...

---

### Post by smartboyathome on 2008-02-06
@a9bejo:
I think Split is better suited for a file manager, since it allows drag-n-drop, but that is just me. I think the window manager should not be doing this since it ultimately isn't the window manager's fault the window doesn't suppor this, and would only add weight.

@MaX:
Thunar has had restore from trash for a little while now.

---

### Post by a9bejo on 2008-02-06
> **smartboyathome said:**
> 
I think Split is better suited for a file manager, since it allows drag-n-drop, but that is just me. 

why should drag and drop not work if the window manager would split the windows?  It worked fine with all the tiling window managers that I used. 

> **smartboyathome said:**
> 
I think the window manager should not be doing this since it ultimately isn't the window manager's fault the window doesn't suppor this, and would only add weight.


Well, I guess I see it exactly the other way around ;)  Managing windows is the window manager's job.  It is the only application that needs to do this.  The way it is now, every applications has to implement its own solution, which produces a lot of redundant code.

Also, since every application has its own implementation, windows from different applications do not work together very well.  E.g., firefox and dolphon both have tabs, but I cannot have dolphin and firefox tabs together in the same window.  But this is really useful, I use this to group related applications together all the time in fluxbox.

---

### Post by linuxisfree on 2008-02-06
> **oomingmak said:**
> Who's the person that voted Nautilus as perfect?

:lolflag:

I guess it seems to be working for him / her...

My main greivance vs Nautilus is just this... Won't somebody PLEASE place metadata integration!!! Its REALLY DIFFICULT especially when you've a TON of Music and Videos that Need Renaming.

Now i know EasyTag is good for music, but what about Videos???
(Sorry for the sidetrack)

---

### Post by gnomeuser on 2008-02-07
> **linuxisfree said:**
> 
Now i know EasyTag is good for music, but what about Videos???
(Sorry for the sidetrack)

The problem here is mainly the lack of good standard container formats and ways to change them. You need one tool for matruska, one for the ogg container and such.. I suspect the easiest way to do this is top down, overlay a database on the videos, edit metadata there, add tags and other things for your desktop indexer then have that data flushed back to the files. In some what the same way Banshee works when the copy metadata and copy on move options are set. At any rather this needs to be functionality that's not a seperate program, it needs to be available and integrated. For added bonus points would should have a way to pull metadata from imdb, that would really make media center stuff fun I think, or have a similar musicbrainz' like thing for video?

---

### Post by oomingmak on 2008-02-07
> **linuxisfree said:**
> I guess it seems to be working for him / her...
"Working" and "Perfect" are two entirely different things.

---

### Post by Mr.mouse on 2008-02-07
converting a file by rename it
[http://ubuntuforums.org/showthread.php?t=538246](http://ubuntuforums.org/showthread.php?t=538246)

---

### Post by deepclutch on 2008-02-07
the biggest one is Nautilus lagging "Refresh" option in Desktop right click context menu :evil:

hell,I cant even find any help from nautilus devels or Ubuntu ppl regarding what command is  used for "Refresh" when  F5 or CTRL+R is pressed(definitely NOT "xrefresh -white") is it nautilus restarting?No Ideas.
also any nautilus-actions script for adding a "Refresh"  option in right click menu-NO!bcoz Refresh is so windowish;right? :rolleyes:

among other things tabs for nautilus,making song preview more stable and must-add deps for nautilus for this-mpg321 and vorbis-tool among many.

another file manager for Gnome is not a bad idea IMHO :cool:

---

### Post by chrisccoulson on 2008-02-07
> **deepclutch said:**
> the biggest one is Nautilus lagging "Refresh" option in Desktop right click context menu :evil:

hell,I cant even find any help from nautilus devels or Ubuntu ppl regarding what command is  used for "Refresh" when  F5 or CTRL+R is pressed(definitely NOT "xrefresh -white") is it nautilus restarting?No Ideas.
also any nautilus-actions script for adding a "Refresh"  option in right click menu-NO!bcoz Refresh is so windowish;right? :rolleyes:

among other things tabs for nautilus,making song preview more stable and must-add deps for nautilus for this-mpg321 and vorbis-tool among many.

another file manager for Gnome is not a bad idea IMHO :cool:

I must admit, I didn't even know a refresh option existed - I've never had to use it. Nautilus always seems to refresh automatically when I make any changes in a folder, which is much better than Explorer.

What do you suggest for a new file manager? Should someone develop a new one from scratch with all the features everybody wants, or can you suggest a perfect drop-in replacement that exists already? I don't think GNOME needs a new file manager. While Nautilus could use a few improvements, it would be a waste of effort to just throw it away and adopt something else, as it is still a good file manager and there is a lot of active development going on at the moment. Nautilus has a completely new backend in Hardy, and the future for it looks very exciting.

No piece of software is perfect, and you will never please everyone. I bet that if Nautilus was replaced with something else today, there would still be people here moaning that GNOME needed a new file manager.

---

### Post by deepclutch on 2008-02-07
Well,atleast nautilus needs to be better.esp the crashes which I experienced before :-|
and :lol: are u hearing about CTRL+R refresh for Desktop right now?

---

### Post by Phristen on 2008-02-07
One thing it REALLY lacks is the ability to drag-select while in the View-as-List mode.
And also a multi-column list view mode.

---

### Post by mivo on 2008-02-07
The number one missing feature for me is tabs. In fact, it's *the* feature that Gnome lacks, in my opinion. (The file manager cannot be fully replaced, sadly.)

---

### Post by Chibi-Tatsu on 2008-02-16
Memory management/leakage when dealing with lots of preview-type icons.

Seriously; I was shocked to see nautilus hitting 800 megs.  A little experimentation revealed that it would claim new memory when I opened up a new directory with prevfiew icons, and then never release it.  So if I were to visit my artist galleries... well, it's not pretty.

EDIT: Oh, and the ability to specify a standard folder icon in the folder for the entire system, rather than needing to change the properties of each folder.  I'd like to be able to just drop a file called ".icon.jpg" (so it's hidden) in the folder and have it know that that's supposed to be the folder's icon.

---

### Post by chrisccoulson on 2008-02-17
> **Chibi-Tatsu said:**
> Memory management/leakage when dealing with lots of preview-type icons.

Seriously; I was shocked to see nautilus hitting 800 megs.  A little experimentation revealed that it would claim new memory when I opened up a new directory with prevfiew icons, and then never release it.  So if I were to visit my artist galleries... well, it's not pretty.
If Nautilus is running at 800Megs, then thats probably a bug. It's not normal. Does it happen with a fresh user? I've had a problem like this before, and it went away after deleting my Nautilus profile and thumbnail cache.

---

### Post by 23meg on 2008-02-17
> **MaX said:**
> List view as in windows is in development IIRC.


Christian Neumair has [just submitted it]("http://blogs.gnome.org/cneumair/2008/02/17/new-column-wise-nautilus-view-user-data-backup-replay/") and requests feedback.

---

### Post by mangar on 2008-02-17
about split view:
From what I've see in the Mailing lists:
In order to make split view workable in nautilus, it's needed to folder sync shortcuts, more keyboard shortcuts, duplication of location bar 
and navigation buttons, etc.
In short - duplicate the behavior of Norton Commander (or Total Commander).

There's an existing two-pane file browser for Gnome - Tux Commander:
[http://tuxcmd.sourceforge.net/screenshots.php](http://tuxcmd.sourceforge.net/screenshots.php)

Since the use cases for Nautilus and TuxCmd are relatively disjoint, I think that people who actually need split view may be better off using TuxCmd (or midnight commander under the console (`mc`))

---

### Post by rosegarden78 on 2008-02-18
SEARCH FEATURES.  The poky little puppy was sooooo-o easy to use in XP.

No matter how hard I try I cannot get a search like that easy in Ubuntu.

---

### Post by deepclutch on 2008-02-18
> **zero-9376 said:**
> Anyone interested in doing nautilus scripts should really have a look at the nautilus-actions packages which is in the repos.
Website:
[http://www.grumz.net/?q=taxonomy/term/2/9](http://www.grumz.net/?q=taxonomy/term/2/9)
I just put together a VERY simple menu item that uses gnome-osd to display the path and filename of the selected file. Whats more it integrates much more nicely into the menu and you can set and icon ALL THROUGH A GUI CONFIGURATION system.

note: the app installs but doesn't appear to put anything in them menus, use nautilus-actions-config from the terminal or run dialog (alt+f2) to make a new action.

EDIT: attached exported schema which should be able to be added using the import function also ensure gnome-osd is installed to make it work

Can you help me getting nautilus-actions to add a "Refresh" option to Desktop right click context menu? :)

---

### Post by ilovenicotine on 2008-02-18
A good usable search box that's intuitive and powerful.  Needs filters to "search hidden files" and such.  It should also show the full path to the file when in list mode (ctrl+2) so if I've got 3 image.gifs, I know where each one is located.

---

### Post by ryanhaigh on 2008-02-18
I would like to have the ability to perform file operations on the results returned by the nautilus search (both integrated and places>find files) such as copy/delete. It is something that you overlook until you need to move all your photos/music and they are in random subdirectories but can be very useful. I have been able to achieve the desired result from the command line but I would prefer to be able to do it within the file manger.

By the way its great to see some of these issues being resolved in the new nautilus [http://blogs.gnome.org/alexl/](http://blogs.gnome.org/alexl/) as well as changes coming in Hardy (searching without tracker).

---

### Post by oponek on 2008-02-29
Here is a brainstorm for improving Nautilus performance:
[http://brainstorm.ubuntu.com/idea/1521/](http://brainstorm.ubuntu.com/idea/1521/)

---

### Post by Westies on 2008-02-29
> **spoilerhead said:**
> support for additional mouse buttons (just like firefox)

yes i know that its possible to bind mouse buttons to key combinations, but thats just a workaround, not a solution imho
This!

---

### Post by Redrazor39 on 2008-03-26
Previews would be really good. Look at quick look or even vista preview pane. We really should have something like quick look by now.

---

### Post by blazoner on 2008-03-29
> **spoilerhead said:**
> support for additional mouse buttons (just like firefox)

yes i know that its possible to bind mouse buttons to key combinations, but thats just a workaround, not a solution imho

Essentially, the main issue with this is hardware. Different mouses use different event handlers for their non-standard buttons. There is no standardization other than the 5 typical mouse buttons. (Left, Right, Wheel or Middle-Click, and Scroll-Up/Scroll-Down)
This makes it impossible to write a driver for all mouses.
Currently, the most promising solution is [btnx and btnx-config]("http://ubuntuforums.org/showthread.php?t=455656"). A GUI for detecting, labeling, and assigning actions to button presses using uinput (The uinput driver creates a character device that can be used to create Linux input devices from userspace.)

There are a couple of issues which have yet to be addressed, however:
1) btnx has to be run as root. This is not a problem for the casual user, and works both well and securely, but has not yet been effectively implemented in a workable way for network roll-outs, etc.
2) btnx is currently designed to detect only USB mouses. BlueTooth and other mouse detection has yet to be worked out. (PS2 connectors and adapters don't allow any event handlers, except the 5 I listed here.)

---

### Post by Bubba64 on 2008-03-29
an espresso maker slash wet bar.

---

### Post by Joe_Bishop on 2008-04-02
The 3 features are really needed:
1) Split view - extremely useful while intensive file operations
2) Split items by group
3) Need performance improvement - it should start instantly.
PS I'm very confused about completely useless feature for file browser: tabs. Nobody needs it, actually. The only reason, many people found it useful in the web browser, and they extend it to the file browser. But it follows to the worse design and stability.

---

### Post by mivo on 2008-04-02
> **Joe_Bishop said:**
>  I'm very confused about completely useless feature for file browser: tabs. Nobody needs it, actually.

The people who voted for that option obviously consider it a useful feature. Personally, I see no use for the features you listed and would like to see, but I wouldn't project my own opinion on everyone else and say that they are completely useless features for anyone, only because they are not needed by me.

---

### Post by Person98 on 2008-06-09
i really like the mouse gestures in thunar how about some of those you get so used to them, but thunar isn't my ideal browser for other reasons. also someone mentioned iso mounting in nautilus that would be awsome

---

### Post by linuxd00 on 2008-06-10
SEARCH AS YOU TYPE for files when browsing

---

### Post by smartboyathome on 2008-06-10
> **linuxd00 said:**
> SEARCH AS YOU TYPE for files when browsing

Until we get a better search tool, this would eat up a huge amount of cpu.

---

### Post by linuxd00 on 2008-06-11
> **smartboyathome said:**
> Until we get a better search tool, this would eat up a huge amount of cpu.

i mean "search as you type" only within the current view/Folder.
this isnt that hard i think. Its just like the firefox feature. you type and it jumps to the first occurrence within the folder you are currently in.

this was actually the missing feature that made me move to pcmanfm

---

### Post by smartboyathome on 2008-06-11
> **linuxd00 said:**
> i mean "search as you type" only within the current view/Folder.
this isnt that hard i think. Its just like the firefox feature. you type and it jumps to the first occurrence within the folder you are currently in.

this was actually the missing feature that made me move to pcmanfm

You can, actually. Click in the portion with all the files, and then start typing the name of the file.

---

### Post by bruce89 on 2008-06-11
> **smartboyathome said:**
> You can, actually. Click in the portion with all the files, and then start typing the name of the file.

Same goes for some normal GtkTreeViews as well.

---

### Post by ryanhaigh on 2008-06-12
You can also press Ctrl-S to bring up a selection dialog that will allow you to select multiple files using wildcards. Of course there is a big difference between selecting and filtering.

---

### Post by jnewm on 2008-07-23
Another vote for:
UNDO, UNDO, UNDO...
I know Ubuntu shouldn't emulate windows for no reason, but the lack of undo is particularly nasty for us dual users.  I'm stuck using Windows at work (for now), and I am just used to knowing that I can fix my stupid mistakes--for instance, if I screw up and accidentally hit the delete between, or hit the delete button while the wrong window is selected, or accidentally drag a folder into another folder.  Generally in these situations, I know I screwed up and deleted or moved something, but I have no idea what.  So I really depend on the undo function.

And Restore From Trash...

Thanks for asking! :)

---

### Post by rogier.de.groot on 2008-07-23
The most important missing feature?
Subversion integration!!!
You know, like TortoiseSVN in Windows or the SVN KIO slave thingy in KDE!
No more update/commit on the damn command line!

---

### Post by smartboyathome on 2008-07-23
> **rogier.de.groot said:**
> The most important missing feature?
Subversion integration!!!
You know, like TortoiseSVN in Windows or the SVN KIO slave thingy in KDE!
No more update/commit on the damn command line!

This is a very low importance feature imo. There aren't many devs who don't know about SVN and would benefit. I think a separate tool would be in order.

---

### Post by bruce89 on 2008-07-23
> **smartboyathome said:**
> This is a very low importance feature imo. There aren't many devs who don't know about SVN and would benefit. I think a separate tool would be in order.

A Nautilus extension would be perfect for this; in fact, one may exist already.

---

### Post by mazz0 on 2008-08-08
Breadcrumbs!!!!!!!!!!! (I'm using exclamation marks to signify how much I want this feature, you see) - and not some cheap buttons that either replace or sit above/below the path text entry box, but integrated like in Vista.

---

### Post by SuperSonic4 on 2008-08-08
I voted tabs but it really doesn't bother me given that I run KDE :p and can use Konqueror or Krusader (root or otherwise)

---

