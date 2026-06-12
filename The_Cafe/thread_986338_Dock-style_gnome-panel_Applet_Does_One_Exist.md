---
title: "Dock-style gnome-panel Applet: Does One Exist?"
date: 2008-11-18
forum: The Cafe
---

### Post by aaaantoine on 2008-11-18
Because Window List from gnome-panel depends on WnckTasklist to create a standard task list, and because I don't want to mess with any libraries, I've created an independent app.

If you want a dock built into your existing gnome panel, this application will do it.

I've attached two screen shots; one of my current implementation, and one of how the dock would appear on a 48px panel using the Human theme.

[color=red]This marks my first distributed application, so I expect it to be broken for a lot of people.[/color]  However, this is pretty much stable on my platform.

**Installation instructions:**
1. Download the attached tar.gz file.
2. Extract it somewhere in your home folder.
3. Make sure you have libpanelapplet-2.0 and libwnck-1.0 installed, along with their -dev packages.
4. In the terminal, go to the folder and type:
```

make
sudo make install

```
Note that ./configure is omitted because I have not yet implemented it.

**Things I eventually want to add:**
- Handle urgent messages for windows.
- Set icon locations for windows (In other words, add support for minimize, restore, and window preview animations)
- Actually add support for launchers, so that the task "dock" lives up to its name.
- Add smooth icon scaling, if possible.
- Add options for grouping windows.
- Add options for only showing current workspace windows.

**Change log (will provide last 2-3 versions in the event of a regression):**
0.0.2: (Thanks, Eemil!)
- Now brings hidden windows to front when clicking the icon, and only minimizes shown windows.
- Switches to the workspace a window resides in when you click to unminimize / activate a window.

0.0.1: Initial release.  Lists windows from all workspaces, without grouping, on the gnome panel.

Original post:
[quote=aaaantoine]
Basically, I want a panel applet that behaves like AWN.  Does such an application exist?

If not, which idea do you think is better?

1. Write a fork of the Window List applet that is specialized to behave like AWN.
2. Write and submit patches to the Window List applet to add AWN behavior options for the user.

Actually I would probably do a combination of the two if I went forward with this project.  But first, I need to find that source code... :-k

Edit: I use AWN currently.  My reasons for wanting to replace it are as follows.
1. It's buggy.
2. It requires compositing, which won't be a problem for me when DRI2 makes it to Ubuntu, but in the mean time...
3. I want to integrate it into my existing gnome panel to save resources.
[/quote]

---

### Post by aaaantoine on 2008-11-19
So I found the source code in gnome-panel.

But I'm having a hard time trying to find the widgets for the window list applet itself.

window-list.c seems to apply to the preferences window more than anything else.

...This thread should probably move to the Programming forum.

---

### Post by Therion on 2008-11-19
Do you mean something like Gnome Do?

[http://www.flickr.com/photos/73617363@N00/sets/72157602349337246/detail/](http://www.flickr.com/photos/73617363@N00/sets/72157602349337246/detail/)

---

### Post by aaaantoine on 2008-11-19
No.  Gnome Do is great, but a window list it is not.

---

### Post by hanzomon4 on 2008-11-19
That would be cool.. An applet that turns the panel into a dock right?

---

### Post by Bölvaður on 2008-11-19
if I understand correctly, you are trying to make "Window List 2.24.1" behave the same or similarly to awn?

If Im not going to spain over christmas I would love to participate.

[added]
Send me pm about this when you begin.

---

### Post by ufugu on 2008-11-19
If you mean an applet that behaves like an Apple Dock (for example, clicking the Firefox icon will bring you to the current Firefox window instead of opening a new instance) but runs in the panel, then I am right there with you.

Closest two things I've found:

1) Run the XFCE panel with the xfce panel applet "icon box".

2) Run a bottom panel and AWN concurrently.  If you size AWN really small and put your native panel applets far to each end, and then make matching AWN and panel applet backgrounds, you can get a similar result to what you're looking for.

---

### Post by aaaantoine on 2008-11-19
> **Bölvaður said:**
> if I understand correctly, you are trying to make "Window List 2.24.1" behave the same or similarly to awn?

If Im not going to spain over christmas I would love to participate.

[added]
Send me pm about this when you begin.

Pretty much.

If I can ever figure out how the code actually works, my short term plans are as follows:

1. Remove the text from the Window List entries (fork).  Or, create an option to remove the text (patch).
2. Make icon resize with panel size instead of using multiple rows.
3. When text is removed, the Window List buttons should always fit the icon instead of expanding to fill available space.

That's the "easy" stuff.  From there I would like to try figuring out integrating launchers.

---

### Post by Bölvaður on 2008-11-19
I would guess it might be easiest to copy the code from "Window List 2.24.1" and rename it to "Panel Dock 0.0.1"

Then you can use the same code for minimizing the windows and just have an if statement to check if there is instance of that applications already running, if not then we can use bash command to execute the program or look into the code in gnome-menu (not sure)

---

### Post by PCessna on 2008-11-19
You can make one.

Make new panel, Uncheck expand, choose your size, place on screen, check hide buttons, auto-hide if you want, add applets and shortcuts you want and presto!, You got yourself a nice homemade dock from GNOME's Panel. :)

---

### Post by aaaantoine on 2008-11-19
> **Bölvaður said:**
> I would guess it might be easiest to copy the code from "Window List 2.24.1" and rename it to "Panel Dock 0.0.1"

Then you can use the same code for minimizing the windows and just have an if statement to check if there is instance of that applications already running, if not then we can use bash command to execute the program or look into the code in gnome-menu (not sure)

It surprises me how deep this rabbit hole goes.

On line 519 of window-list.c, the _fill function refers to a function not found elsewhere in the source code.
```
tasklist->tasklist = wnck_tasklist_new (NULL);
```

I checked wncklet.c and wncklet.h, and also window-list.c to see what this is.  If I were to guess, this refers to a function in the include file linked to on line 25:
```
#include <libwnck/libwnck.h>
```

But wait, wnck_tasklist_new() is not in libwnck.h... But libwnck.h refers to tasklist.h, which has the following declaration:
```
GtkWidget *wnck_tasklist_new (WnckScreen *screen);
```

But no function.  Where is this function?

Also, while I was digging around trying to find the function, I came across this reassuring line in window.h (still in libwnck):
```
#error "libwnck should only be used if you understand that it's subject to frequent change, and is not supported as a fixed API/ABI or as part of the platform"
```

So, I have a feeling that basing this project on the Window List applet will not be as easy as I thought.

Edit: See [http://library.gnome.org/devel/libwnck/stable/WnckTasklist.html](http://library.gnome.org/devel/libwnck/stable/WnckTasklist.html) for reference.

---

### Post by aaaantoine on 2008-11-25
So... I decided to write my own from scratch.  See OP.

Let me know what you think. :)

---

### Post by fubbleskag on 2008-12-06
i am currently quite deeply in love with you

---

### Post by smartboyathome on 2008-12-06
Nice! If I were still using GNOME, I would use it. Fortunately, E17 has something similar. ;)

---

### Post by Giant Speck on 2008-12-06
We need more people like you making gnome-panel applets!

---

### Post by meg23 on 2008-12-06
thanks I have been looking for something like this.

---

### Post by aschwerin.moses on 2008-12-06
okay.. i've installed it.. but not sure what to do next.. can any one please guide me

---

### Post by Giant Speck on 2008-12-06
> **aschwerin.moses said:**
> okay.. i've installed it.. but not sure what to do next.. can any one please guide me

Right click on a panel and click "add to panel" it will be listed as "Task Dock"

---

### Post by tdrusk on 2008-12-07
> **PCessna said:**
> You can make one.

Make new panel, Uncheck expand, choose your size, place on screen, check hide buttons, auto-hide if you want, add applets and shortcuts you want and presto!, You got yourself a nice homemade dock from GNOME's Panel. :)
If this post is what the TS wanted I respect your simplistic thinking.

---

### Post by the yawner on 2008-12-07
> **fubbleskag said:**
> i am currently quite deeply in love with you

I find the concept somewhat similar to Window 7 taskbar. I'll be looking forward to this project's development. :popcorn:

---

### Post by aschwerin.moses on 2008-12-10
im not able to install "libpanelapplet-2.0" or "libpanelapplet-2.6-dev" .. why?????? what to do??????

---

### Post by geoken on 2008-12-10
Do the icons scale up in relation to panel width?

My biggest gripe with the default gnome applet is that the icons don't scale up.

---

### Post by acelin on 2008-12-10
> **geoken said:**
> Do the icons scale up in relation to panel width?

My biggest gripe with the default gnome applet is that the icons don't scale up.

My biggest grip with the Gnome Panel is it doesn't always show up upon login. Not very reliable either, even on really nice computers.

---

### Post by Bölvaður on 2008-12-10
I attached some rough ideas on how this could turn out.
I interviewed some people on how they use docks and window lists and this is the fruit of that labor.

---

### Post by fubbleskag on 2008-12-10
> **aschwerin.moses said:**
> im not able to install "libpanelapplet-2.0" or "libpanelapplet-2.6-dev" .. why?????? what to do??????
```
sudo apt-get install libpanel-applet2-0 libpanel-applet2-dev
```

> **geoken said:**
> Do the icons scale up in relation to panel width?

My biggest gripe with the default gnome applet is that the icons don't scale up.

[http://ubuntuforums.org/attachment.php?attachmentid=95499&d=1228615131](http://ubuntuforums.org/attachment.php?attachmentid=95499&d=1228615131)

my panel is set to 65pixels and my launcher icons scale up fine - the icons in this applet seem to only scale up to about 48px or so, though

> **Bölvaður said:**
> I attached some rough ideas on how this could turn out.
I interviewed some people on how they use docks and window lists and this is the fruit of that labor.this would fulfill all of my needs exactly as you've described.

---

### Post by aschwerin.moses on 2008-12-10
> **fubbleskag said:**
> ```
sudo apt-get install libpanel-applet2-0 libpanel-applet2-dev
```


Thank you... libpanel-applet2-0 was already installed

But when i install libpanel-applet2-dev, i get an error ... ive tried to install those unmet files, but even those give an error, asking to downgrade other files.. what to do??..

[I]sudo apt-get install libpanel-applet2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpanel-applet2-dev: Depends: libbonoboui2-dev (>= 2.1.1) but it is not going to be installed
                        Depends: libglade2-dev (>= 1:2.5.0) but it is not going to be installed
                        Depends: libgnomeui-dev (>= 2.5.4) but it is not going to be installed
                        Depends: libgtk2.0-dev (>= 2.11.3) but it is not going to be installed
E: Broken packages[/I]

---

### Post by eti.que on 2008-12-27
Works like a charm on my Eeepc 1000H. Exactly what I have been looking for. Awesome. Looking forward to the next developements.

---

### Post by Stefanie on 2009-01-05
nice work! i love this applet. if you could add an option to show only the applications on the current workspace it would be perfect.

---

### Post by Bölvaður on 2009-01-05
This project has been terminated, I was going to contribute but he stopped before I began and I wouldnt have time for this any more any way.
If you are interested in taking over I guess the best way is to check out his codes and ask the OP for how he was recycling the code from gnome-applet and all those programs.

---

### Post by aaaantoine on 2009-01-05
In the event I return to using Gnome, I will see what else I can do with the applet.  However it was proving to be painful to do something as simple as making the icon flash when a message is received.

My conclusion was that it would be better and possibly easier to port this functionality into the existing Window List applet and wnck's tasklist object.  The only reason I don't is because I don't know the first thing about contributing code to Gnome, and for some reason I doubt they would accept it.

Thanks for the interest.  I'm glad that there are a number of people that like this idea.


Edit: Also I would not exactly say that the project has been terminated.  The source code is there.  I encourage better programmers than myself to see what they can do with this based on the ideas posted in this thread.

---

### Post by aaaantoine on 2009-01-05
> **Bölvaður said:**
> I attached some rough ideas on how this could turn out.
I interviewed some people on how they use docks and window lists and this is the fruit of that labor.

Cosmetically I'm not a fan of the numbering system suggested for grouped applications.  I'd prefer a way to superimpose a solid bold number (with soft shadow or outline for contrast) over the icon in one of the corners of the button.

The labeling system is a decent idea, but like the numbering it messes with the uniform shape of the task dock buttons.  I'll refer to my suggestion above, and place 2 or 3 letters (or whatever fits without being cut off) in the corner opposite to the number of windows open.

I really like the "New Window" option suggested for launchers that have at least one open instance.

---

### Post by Stefanie on 2009-01-05
> **Stefanie said:**
> nice work! i love this applet. if you could add an option to show only the applications on the current workspace it would be perfect.

Is there anyone who is interested in this idea and can have a look at the source code to see if it would take a lot of work to implement? I don't have much experience in programming but if it's as easy as fiddling with a few lines I might give it a try.

---

### Post by Anarchj on 2009-01-21
it would be cool to have notifications on icons (to replace the icontray) and when you move mouse on app icon it shows you if there are more windows in one icons an then you click on the window you want (2 firefox windows etc...).
Sorry for my english, and thank you for this applet!

---

### Post by Vermind on 2009-01-24
Hi,
This applet looks very promising.
I propose a patch, which:
[LIST=1]
[*]Does not minimize a window when it is hidden. Instead, brings the window to front, and only minimizes a window when it is visible already.
[*]Moves you to the workspace where the window resides when you click on an icon that represents a window not on the current workspace.
[/LIST]
I propose this be called taskdock 0.0.2 (since the current versioning doesnt allow for very small changes to be noted otherwise...).

(Patch attached)

---

### Post by hawkbane47 on 2009-01-26
How does one install this patch?

---

### Post by aaaantoine on 2009-01-26
> **Vermind said:**
> Hi,
This applet looks very promising.
I propose a patch, which:
[LIST=1]
[*]Does not minimize a window when it is hidden. Instead, brings the window to front, and only minimizes a window when it is visible already.
[*]Moves you to the workspace where the window resides when you click on an icon that represents a window not on the current workspace.
[/LIST]
I propose this be called taskdock 0.0.2 (since the current versioning doesnt allow for very small changes to be noted otherwise...).

(Patch attached)

Hm, I thought that stuff was already working.

I suppose in the spirit of being the maintainer I should look into posting the updated package...

Edit: Haven't tested it, but I applied the patch and posted it in the OP.

---

### Post by mariner09 on 2009-01-27
I just installed task-dock 0.0.2 and it's not workspace aware.  Clicking an icon for an app on another workspace does nothing.

Could it depend on the setting for the app window tool that makes it workspace aware?

---

### Post by mariner09 on 2009-01-27
I did get a warning on the compile as follows:

smcmackin@Mariner-T61:~/Desktop/taskdock-0.0.2$ make
Building dependencies in: .depend
Compiling taskdock.c
taskdock.c:480: warning: ISO C does not allow extra ‘;’ outside of a function
Linking taskdock-applet
smcmackin@Mariner-T61:~/Desktop/taskdock-0.0.2$ sudo make install

---

### Post by mariner09 on 2009-01-27
OK, an update...

If I don't have an app with focus, it will switch to the workspace that holds the app I select.

If an app has focus, you don't move to the new workspace.

---

### Post by Vermind on 2009-01-28
Hm, You mean that it is possible to have focus on an app that is on a different workspace? Which window manager did you try with? I was using metacity. This would be quick to fix, I think...

---

### Post by X-Stranger on 2009-01-28
Good stuff!
Is is possible to do drag-n-drop window button to resort them? Gnome app panel has this useful functionality.

---

### Post by X-Stranger on 2009-01-28
It will be also great to put the sources to SVN repository.

---

### Post by PsychedelicReaction on 2009-01-28
I think you should join the force with [this other project]("http://www.gnome-look.org/content/show.php/DockBar?content=97822") with the same aim,  it also as windows grouping (that's why im preferring this one).

---

### Post by aaaantoine on 2009-01-28
> **PsychedelicReaction said:**
> I think you should join the force with [this other project]("http://www.gnome-look.org/content/show.php/DockBar?content=97822") with the same aim,  it also as windows grouping (that's why im preferring this one).

Oo, thanks for the link.

Looks good, too.

> **X-Stranger said:**
> It will be also great to put the sources to SVN repository.

I hear that git is better.  Then again, I haven't researched it much other than what Linus has to say about it, and he programmed the thing.

---

### Post by Vermind on 2009-01-29
Hello,
> [QUOTE]Originally Posted by PsychedelicReaction
I think you should join the force with this other project with the same aim, it also as windows grouping (that's why im preferring this one).
Oo, thanks for the link.[/QUOTE]
For me, this program's inability to work on the upper panel and its requirement on larger panel size are not good, since I am looking to conserve vertical screen space on my eee pc with a 1024x600 resolution. To this end I have removed the lower panel and am keeping the top panel small. I have also removed the menu bars and bookmark bars from Firefox.
Expect me to piratize and customize the grouping from that other applet soon, if the license there allows it, of course.

---

### Post by Vermind on 2009-01-29
Hi,
I made [DockBar]("http://www.gnome-look.org/content/show.php/DockBar?content=97822") work on top panels as well as bottom ones, and made icons smaller (24 px button size, 20px icon size). These are two separate patches that I will attach here.
Download DockBar 0.05, extract it and my patches to its directory, and apply them with the commands (in the DockBar directory):
```
patch -p0 < dockbar-0.05-top-panel.patch
patch -p0 < dockbar-0.05-small.patch
```
In that order. If You do not want smaller icons, do not apply the -small patch.
I notified the author of [DockBar]("http://www.gnome-look.org/content/show.php/DockBar?content=97822"), about my patches. The smaller icons patch is not optimal; when the icons do not come from the icon theme, their scaling is not perfect.

P.S. DockBar 0.05 looks nice with the dimmed buttons for minimized windows :)

P.P.S. If you saw this post and downloaded the patches before this addition, download again. The dockbar-0.05-top-panel.patch had a bug which caused the group window not appear correctly when near screen left edge. This has been fixed, and also contains a bugfix for the original DockBar 0.05: group window would overflow the screen when close to the right edge of the screen.

---

### Post by Vermind on 2009-01-30
Deb packages,
for the lazy and for quick trying out:
(the -small includes the -small patch, the other one just the fix for top panel and overflow bugfix)

---

### Post by Anarchj on 2009-01-30
> **Vermind said:**
> Deb packages,
for the lazy and for quick trying out:
(the -small includes the -small patch, the other one just the fix for top panel and overflow bugfix)

Thank you so much!

---

### Post by artisol on 2009-02-03
Thanks. I'm looking for this . Great !

---

### Post by Vermind on 2009-02-03
The applet has been updated to version 0.1,
now with scaling to any size and support for panels in all directions: [DockBar 0.1]("http://www.gnome-look.org/content/show.php/DockBar?content=97822"). Here, again, the deb for the lazy attached. Edit: Fixed version for the deb, from 0.1 to 0.10. 0.1 < 0.05 < 0.10, since zeroes don't count. If You downloaded this before and got a "downgrade" warning, this is fixed now.

P.S. Instructions for making a deb of virtually anything:

[LIST=1]
[*]Create a makefile that contains the installation commands. An example for dockbar:
```
install:
	cp dockbar.py /usr/bin/.
	cp GNOME_DockBarApplet.server /usr/lib/bonobo/servers/.

```
[*]install and run the program called checkinstall, in the program's directory. You can get it with ```
apt-get install checkinstall
```.
Example:
```

checkinstall --requires=python-gnome2-desktop --arch all --maintainer yourname@yourdomain.org
```
[/LIST]

Checkinstall will ask you for a package description, then create a .deb that contains the installed files, and install it for you (requires root access). You can also specify not to install.

---

### Post by Vermind on 2009-02-04
I noticed that if I remove the gnome window list, and use dockbar exclusively, and then log out and log in to gnome, Metacity shows a minimize "animation" to lower right corner regardless of my panel location, while compiz does not show minimize at all, but seems to show unminimize from the previous center of the minimized window.
So, these do not target the minimize/unminimize in the right spot with dockbar. However, task dock sets the minimize in my upper left corner, which is a bit better. Neither applet does the Right Thing in this though, which would be to target the minimize and unminimize at the window/group buttons in the panel. I wonder what Window List does to make that happen?

---

### Post by Vermind on 2009-02-28
Hi,
[dockbar-0.11 has been released]("http://www.gnome-look.org/content/show.php/DockBar?content=97822").

New features (from the page above): 
> -fixed- run-in-window
-fixed- normal unminimization of OOo windows
-+- scroll on window button to shade/unshade
-+- window name length 40 chars limit

I attached the deb package for lazy people.

---

### Post by bryonak on 2009-03-11
Good work there, just two requests:
1. Workspace awareness would make it really useful.
2. Right clicking should offer the same menu as the default window list (like taskdock).
*EDIT: 3. Highlighting (or something similar) the currently active window would be nice too.*

Also if you add launchers to the main code, please offer an option to turn them off completely (personally, I need just a window list).


By the way, isn't this thread supposed to be about taskdock?
I hope aaaantoine doesn't mind your hijacking.

Just a quick comparison from a user's point of view: taskdock has the right click menu, but dockbar looks prettier and has the "hover preview" (although that one doesn't really look pretty compared to, say, compiz' preview). Neither supports listing only one workspace.

---

### Post by Hells_Dark on 2009-03-11
Nice.

---

### Post by Vermind on 2009-03-11
Hello,
Sorry for hijacking ;).
It's about a dock style gnome panel applet, like the title says, so I assume more alternatives are welcome, though.

---

### Post by aaaantoine on 2009-03-11
Alternatives are very much welcome.  I started the thread initially wondering if such a thing existed.  And then started working on my own.

I'm still in KDE land now, and I discovered a plasmoid that behaves similarly to these gnome applets: [sTasks](http://www.kde-look.org/content/show.php/STasks?content=99739)

---

### Post by bryonak on 2009-03-12
> **aaaantoine said:**
> Alternatives are very much welcome.

Good thinking :D

Taskdock is stalled at the moment, then?

@Vermind:
Any info about the status of dockbar?

---

### Post by Vermind on 2009-03-12
[Dockbar 0.13 released]("http://www.gnome-look.org/content/show.php/DockBar?content=97822")
> 0.13
-fixed- some icons search engine bugs

0.12
-+- new icons style
-+- new icons search engine
0.12.5 - stupid bug fixed

The new version fixes some icon transparency ugliness issues, and adds a "partially minimized" state: if one or more of an application's windows are minimized, and one or more unminimized, left half of the icon will be transparent and the right half opaque.

The -patched version includes a patch by me to fix compiz and metacity minimize animation targeting. With this patch, application minimize animations should correctly minimize to the icon in your panel. I need feedback on this; I am not sure it works 100% yet.

The -orig version is 0.13, without modifications.

---

### Post by fubbleskag on 2009-03-15
I'd forgotten about this thread and happy to return and find that support for launchers has been added. :)

---

### Post by Vermind on 2009-04-13
Hello again everyone,
> **fubbleskag said:**
> happy to return and find that support for launchers has been added. :)
I have moved on to the [experimental version of dockbar]("http://www.gnome-look.org/content/show.php/Dockbar+Experimental?content=101604") as well, called dockbarx. The current version (0.21.0) supports launchers, but you must:
[LIST]
[*]have the specified launcher in the gnome menu, panel, or desktop
[*]Specify the program name when adding it to dockbarx.
[/LIST]
This can be accomplished by creating your launcher somewhere out of the way, starting the program specified by the launcher, and then dragging the launcher to dockbarx. You will then be able to select the program name from a drop-down list.

I have no complaints about this version. group buttons and window buttons look nice, minimizing happens to the correct location of the icon, and the look is polished. 

I packaged the latest version, it is attached.

---

### Post by dungpt on 2009-05-06
dockbarx is good.
however it's seems some problem with design.

- no hover effect
- no onclick effect

it doesn't look nice like windows 7.

---

### Post by Vermind on 2009-05-07
I think you will notice there have been a lot of improvements to dockbarx.
Please check the official PPA:
[https://launchpad.net/~dockbar-main/+archive/ppa](https://launchpad.net/~dockbar-main/+archive/ppa)
and the screenshots on the GNOME-Look page:
[http://www.gnome-look.org/content/show.php/DockbarX?content=101604](http://www.gnome-look.org/content/show.php/DockbarX?content=101604)

---

### Post by dbrenha on 2009-05-27
i've just tried the dockbar and it's great!
just a suggestion:
take a look at the right click functions on gnome-do's docky, it's much more practical.

---

### Post by prismpirate on 2009-05-30
Perfect for what I was looking for. Thanks a  lot!

---

### Post by fubbleskag on 2009-09-21
is there something similar to this for KDE panels?

---

### Post by AllRadioisDead on 2009-09-21
> **fubbleskag said:**
> is there something similar to this for KDE panels?
Yes, check out stasks.

---

### Post by andy16666 on 2009-11-28
Very nice work on the applet. I was looking for something exactly like this...not big and flashy like AWN or Gnome-Do Docky, but nice and simple.

---

