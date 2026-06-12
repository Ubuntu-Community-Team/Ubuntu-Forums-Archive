---
title: "So, what about the spatial Nautilus?"
date: 2006-10-22
forum: The Cafe
---

### Post by mostwanted on 2006-10-22
[SIZE="5"]What is it?[/SIZE]

Nautilus is, in a default Gnome installation, spatial, meaning that each folder has a single window assigned to it and that this folder window saves its position and size every time you close it. This behaviour was used in the old Macintosh operating systems (even the first OSX'es?), but not in the latest ones AFAIK.

The spatial Nautilus is great for working in several folders at the same time and for prearranging the folders for specific tasks. For example, I could place my local web directory in one half of the screen area, my server directory in the other half and then every time I need to drag-n-dropload (did I just make a new word? :P) files to my server I just open the two folders and they're ready for this task; I don't have to place them and resize them every time.

[SIZE="5"]Concerning Ubuntu...[/SIZE]

In Ubuntu, however, the spatial Nautilus has been abandoned and instead the familiar browser view from Windows, KDE and OSX is used. This is easier for newcomers one could argue.

So, since a large user base, maybe even the majority of Gnome users, are using the browser view instead of the default spatial view, should the default behaviour then be changed to the browser view? It's a bit weird how some distros keep the one view, while others keep the other - it's amazing how much of a difference it makes to Gnome to shift between those two opposing behaviours.

[COLOR="Navy"]*N.B. You can change the behaviour of Nautilus in the gconf-editor.*[/COLOR]

---

### Post by darkhatter on 2006-10-22
isn't that a copy of the old windows, and all those windows makes a mess

---

### Post by Bloodfen Razormaw on 2006-10-22
Indeed, spatial nautilus should not be default, or even available.  It is a monstrosity and the model is only functional up to a dozen or so files.  When the number of files grows beyond that you can't use it to effectively manage them.  Everyone abandoned spatial views years ago because usability testing shows them to be god-awful.  Imitating real world filing proved to be pintless; computers are here to make things easier, not just do the same old thing again.

However, even though the flaws with spatial file management have been pointed out repeatedly to the GNOME developers they refuse to fix it.  Ubuntu is doing the right thing by fixing GNOME's mess, whether or not they want to upstream.

---

### Post by Ubunted on 2006-10-22
Wasn't Spatial the default in Warty?

All I remember is that I hated it with a passion.

---

### Post by skymt on 2006-10-22
I prefer the hybrid version of spatial mode used by Rox. You navigate using one window, eliminating the mess of windows Nautilus spatial mode creates. If you want to branch your browsing, just middle-click a folder and it opens in a new window. Want the folder one level up in a new window? Middle-click the up button. Want to move a file to a direct subdirectory of your home folder? Middle-click the home button (or just use the rename dialog). Best of both worlds, in my experience.

---

### Post by .t. on 2006-10-22
I also hate spatial. I dunno why it gets so much praise on gnome-usability.

---

### Post by TheMono on 2006-10-22
Stupid idea. However, I disagree that it "should not be default, or even available" - if some want it, leave it there, but it certainly should not be default.. The sort of people who want to use it know how to change it.

---

### Post by picpak on 2006-10-22
> **skymt said:**
> If you want to branch your browsing, just middle-click a folder and it opens in a new window.

Thunar has this feature...but not with the up button though.

---

### Post by Bloodfen Razormaw on 2006-10-22
> I prefer the hybrid version of spatial mode used by Rox. You navigate using one window, eliminating the mess of windows Nautilus spatial mode creates. If you want to branch your browsing, just middle-click a folder and it opens in a new window. Want the folder one level up in a new window? Middle-click the up button. Want to move a file to a direct subdirectory of your home folder? Middle-click the home button (or just use the rename dialog). Best of both worlds, in my experience.
That's not a hybrid, its just normal browsing.  Being able to open multiple windows is a feature of every file browser (in fact Konqueror does it just like Rox, applying it to Up/Back/Forward/etc).  The thing that makes spatial different is that the view of every location in every window is saved.  The scrollbar is where you last left it, the folders and icons are where you left them, etc.  They thought people would remember the physical location of their files.  It turns out it was not a good idea, but to admit that would try to hurt the "usability" face GNOME tries to put on.

> I also hate spatial. I dunno why it gets so much praise on gnome-usability.
Because if they didn't ignore the usability problems that are exposed in GNOME they would have to admit GNOME has had usability problems for years.  The same usability problems have been exposed in numerous usability tests as far back as 2001.  Their usability reports page only shows me three usability studies they have done in the entire lifetime of their project (in contrast, KDE has made 16 reports in the past 2 years), and GNOME is almost entirely absent from projects like OpenUsability which are made specifically to help improve desktop usability.  It seems usability is just a word to GNOME, not something to be practiced.

---

### Post by skymt on 2006-10-22
> **Bloodfen Razormaw said:**
> That's not a hybrid, its just normal browsing.  Being able to open multiple windows is a feature of every file browser (in fact Konqueror does it just like Rox, applying it to Up/Back/Forward/etc).  The thing that makes spatial different is that the view of every location in every window is saved.  The scrollbar is where you last left it, the folders and icons are where you left them, etc.  They thought people would remember the physical location of their files.  It turns out it was not a good idea, but to admit that would try to hurt the "usability" face GNOME tries to put on.

I was referring to the use model of Rox compared to Konqueror and Nautilus (in browser mode). To move a file in the traditional explorer model, you use one window, navigate to a folder, then either copy-and-paste to another folder, or drag it to another pane. The large default window size and amount of chrome makes multiple windows impractical. With Rox and Nautilus spatial mode (and the classic Mac Finder it's based on), you use multiple windows. Nautilus has one window for each folder. I just close most of them after using them to go one level deeper. Rox keeps the benefits of the multiple-window model, but with only one window for each browsing path. As I said, best of both worlds.

The main flaw in Nautilus spatial mode, as I see it, is that the target keeps moving. Users are used to one window per task or sub-task, not one per object. If the task is to open a file, it shouldn't open a new window for each step in the task. Rox is perfect in that aspect. If the task is to open a file, it's just one window. If the task is to move a file, it's two windows: one to locate the file to move (a sub-task) and another to locate the destination (another sub-task).

---

### Post by Bloodfen Razormaw on 2006-10-22
> I was referring to the use model of Rox compared to Konqueror and Nautilus (in browser mode). To move a file in the traditional explorer model, you use one window, navigate to a folder, then either copy-and-paste to another folder, or drag it to another pane. The large default window size and amount of chrome makes multiple windows impractical. With Rox and Nautilus spatial mode (and the classic Mac Finder it's based on), you use multiple windows. 
I don't see the difference.  Konqueror can be as small and slim as a Rox window.  But most people who do extensive drag and drop prefer multi-pane file managers rather than managing windows.  GNOME actually used to have that.  Before 1.4 it used Midnight Commander for its file manager.  It lacked even the most remedial integration with anything else, but at least it was good at what it did.

---

### Post by skymt on 2006-10-22
> **Bloodfen Razormaw said:**
> I don't see the difference.  Konqueror can be as small and slim as a Rox window.The Konqueror interface is optimized for one window, which is not my preferred workflow. I like Konqueror, it's the best explorer-style file manager I've used. It's just not Rox.> **Bloodfen Razormaw said:**
> But most people who do extensive drag and drop prefer multi-pane file managers rather than managing windows.I don't. I prefer the ability to manipulate each window separately. With a good window manager, it's just as convenient.

As I said, that's just what I've found most useful. Konqueror is probably the best file manager for new users. I'm not a new user.

---

### Post by hanzomon4 on 2006-10-23
I like spatial for drag and drop, but having so many windows open is a pain. I would love to just hold ctrl and then click on a folder to open up a new browser window for the drag and drop.

EDIT: oops! you can by holding shift, this also applies to stopping new windows popping up for each folder opened in spatial.

---

### Post by Wolki on 2006-10-23
I could not live without spatial file management anymore - anything else just feels nadequate.

---

### Post by Starchild on 2006-10-23
In Spatial Nautilus middle-click is your friend.

---

### Post by hanzomon4 on 2006-10-23
> **Starchild said:**
> In Spatial Nautilus middle-click is your friend.

Oh yeah, thanks... Much better the pressing shift.

---

### Post by argie on 2006-10-23
@OP: You could use devilspie to get what you want. It seems to do exactly this task, and for more than just nautilus.

---

### Post by Lord Illidan on 2006-10-23
Everyone is free to use what he/she wants. Me, i prefer Gnome and browser mode..but if anyone wants to use KDE, Spatial Mode or whatever, they're free.

---

### Post by Wolki on 2006-10-23
> **hanzomon4 said:**
> Oh yeah, thanks... Much better the pressing shift.

Note that this also works on files... If you middle-click a file, that ddocument opens and the folder closes. Occasionally very convenient :)

---

### Post by aysiu on 2006-10-23
The KDE v. Gnome posts that have no explicit connection to spatial v. browser modes of file management have been moved to [Poll: Gnome vs KDE](http://www.ubuntuforums.org/showthread.php?t=190994).

For the curious among you, there was another spatial thread a while ago called [Nautilus Spatial Principle: share your views on how to use it](http://www.ubuntuforums.org/showthread.php?t=182400&highlight=spatial).

---

