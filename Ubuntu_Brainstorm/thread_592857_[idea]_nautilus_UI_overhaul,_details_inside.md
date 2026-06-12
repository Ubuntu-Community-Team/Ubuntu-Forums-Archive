---
title: "[idea] nautilus UI overhaul, details inside"
date: 2007-10-26
forum: Ubuntu Brainstorm
---

### Post by mangar on 2007-10-26
synopsis:

1. The crumb bread navigation makes "back" "forward" "up" "stop" "refresh" button redundant, as they replicate functionality already provided by the crumb bread navigation, I think they can be removed.

2. "home" "computer" are already present at the "places" dialog,
they can be removed.

suggestions:
1. remove nautilus' tool bar, it serves no purpose.

2. replace zoom in / out with a slider, move it to the lower right corner (similar to ms - office 2007)

3. replace the "icons/ details" drop down list with two icons,
move it to the left of the zoom slider.

4. replace the zoom slider and the mode switcher with a search box.

_Mock up - crumb bread mode:_

[IMG]http://img98.imageshack.us/img98/3308/nautilusmockupqz0.png[/IMG]

When the text insertion mode button is pressed:

_-Navigation Mode:_

[IMG]http://img84.imageshack.us/img84/3577/nautilusmockupqz0cb7.png[/IMG]

_- Just copy Pathfinder for mac._
[[IMG]http://img440.imageshack.us/img440/6453/picture1jv6.th.jpg[/IMG]](http://img440.imageshack.us/my.php?image=picture1jv6.jpg)[[IMG]http://img440.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by mangar on 2007-10-27
added Mockup

---

### Post by Turgon on 2007-10-27
I like the search bar and the zoom slider, but I don't think the rest is such a good idea I use the arrow buttons activly and its cluttered to go to the places menu each time you need the home folder. 

What I would like to see is if they made every icon the same size. Today files with a preview is much much bigger that the regular icons which makes things look ugly.

---

### Post by mangar on 2007-10-27
Places: the first entry on the "places" side menu is "home".

can you add a mock-up of your idea?

---

### Post by smartboyathome on 2007-10-27
I don't like getting rid of the forward/back buttons either. If navigation was still there, this might be a good idea. As it is, I don't like it. I will see if I can edit your pic to show what I am thinking.

EDIT: @ Turgon, you could go to your home folder using the sidebar.

EDIT2: Changes to your mockup below...
I took out the icon view changer, and added in its place a navigation bar which includes shortcuts to go to your home folder, the Nautilus computer meta-folder, and mounted/unmounted drives. Also, added navigation buttons (need to be better implemented).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48027&stc=1&d=1193504194[/IMG]

---

### Post by chrisccoulson on 2007-10-27
You can already get rid of the main toolbar by hiding it in the View menu. I personally prefer the toolbar there, as I don't use breadcrumb mode, so rely on using the navigation buttons.

I do like the search bar idea though. 

The zoom slider IMO would only be useful if you could hover the mouse over it and zoom with the scrollwheel (which is how it already works in Nautilus). And +/- buttons that you click on to adjust zoom in sensible steps (as already exists) are more useful for laptop touchpad users. Having to click, hold and drag a slider with a touchpad would be a usability nightmare.

---

### Post by mangar on 2007-10-27
Some remarks:
1. The buttons are next to the "search" entry box, should they exist, imho they should be to the left of the crumb bread bar,
otherwise they imply navigation in the search entries.

2. The "Up" button equals in functionality to pressing the "slice" to the left of the current folder -- can be removed.

3, The little location icons on the status-bar replicates the functionality of the "places" side bar, and are hard to reach.

4. I'm not entirely sure that the "back" "forward" (in history, rather than file system hierarchy) should be kept.

5. The way XFCE's Thunar solved it: show navigation bars only when using manual location entry:

5.1 Crumb bread mode:
[IMG]http://thunar.xfce.org/images/filewindow-1-thumb.png[/IMG]

5.2 Textual navigation mode:
[IMG]http://thunar.xfce.org/images/filewindow-2.png[/IMG]

---

### Post by NullHead on 2007-10-27
I like it just the way gutsy has it's defaults.

---

### Post by mangar on 2007-10-28
Updated Mockup, added url mode

---

### Post by zolookas on 2007-10-28
Search bar like in firefox (and in mockups) would be nice.

---

### Post by xlinuks on 2007-10-28
I like (a lot) the new design from Reply #5 by smartboyathome
IMO it's both easier to use and smarter.

---

### Post by Turgon on 2007-10-28
The updated mockup is much better. I', not sure if its really a big improvement over the default gutsy look, but im sure it could be done if many thinks it's better.

---

### Post by smartboyathome on 2007-10-28
I integrated my idea for the bottom of Nautilus and navigation with your mockups for the back/forward/etc buttons.

Textual Navigation mode:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48227&stc=1&d=1193615258[/IMG]

"Breadcrumb" mode:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48228&stc=1&d=1193615264[/IMG]

---

### Post by mangar on 2007-10-28
The edited mockup is very cluttered, too many buttons, in too many places, and a lot of replicated functionality (IMHO).

How many buttons do you think you can remove, while keeping the same functionality (Hint - look at synopsis at my first post.. :) )?

---

### Post by Virgofenix on 2007-10-28
I'd be happy if Nautilus' UI became exactly like Vista's Windows Explorer's. The breadcrumb feature there was dead-on, and the embedded toolbar into title bar was beautiful and non-distracting.

I don't think Nautilus needs a search bar in every window. Deskbar can function as the easy to access search, and Nautilus already has search as you type, along with the built-in search function.

---

### Post by YetAnotherNoob on 2007-10-28
> **Virgofenix said:**
> I'd be happy if Nautilus' UI became exactly like Vista's Windows Explorer's. The breadcrumb feature there was dead-on, and the embedded toolbar into title bar was beautiful and non-distracting.

I have to admit the same feeling.  I now beleive Vista explorer file manager has a better layout than Nautilus.  Personally I use a lot of context menus and shortcut keys.  I rarely use toolbars.  I agree with mangar toolbars at the top should be used sparingly (other wise they are pure clutter).

I think the bread crumb buttons in Nautilus tend to be (vertically) too large.

> **Virgofenix said:**
> I don't think Nautilus needs a search bar in every window. Deskbar can function as the easy to access search, and Nautilus already has search as you type, along with the built-in search function.

I think the search box is a good feature, not sure how it is to be implemented though?
Option (1) you have to transfer focus to the box using mouse/keyboard?
Option (2) as you type it automatically populates the box?

---

### Post by Virgofenix on 2007-10-29
> **YetAnotherNoob said:**
> 

I think the search box is a good feature, not sure how it is to be implemented though?
Option (1) you have to transfer focus to the box using mouse/keyboard?
Option (2) as you type it automatically populates the box?

Nautilus already has a feature like "Option (2)" (try it yourself if you're using gnome). However, it isn't true search. It just jumps to the filename you're typing. Example: you want to find a file named "13_car.jpg", you have to type "13_car" and not "car".

---

### Post by YetAnotherNoob on 2007-10-29
> **Virgofenix said:**
> Nautilus already has a feature like "Option (2)" (try it yourself if you're using gnome). However, it isn't true search. It just jumps to the filename you're typing. Example: you want to find a file named "13_car.jpg", you have to type "13_car" and not "car".

Yes I know it's quite useful.  I guess I was wondering how the mangar's search tool would be used.  The current Ctrl+F feature does basically the same thing doesn't it?

---

### Post by mangar on 2007-10-29
I think that the search bar should serve as a filter, for files in the current directory (and maybe subdirectories), with support for metadata and file content filtering (use xesam api, supported by strigi, tracker, beagle (I think)).

for example, Joe is in his "downloads" folder, and wants to find Radioheads' "In Rainbows" , and move it to his music archive; He does not remember the exact file name, and the download directory is filled to the brim with miscellanea. Joe writes "In Rainbows" in the search bar, and gets the following files list:

"My little Pony, playing In rainbows.jpeg".
"Radiohead - In rainbows.zip"
"My little pony stories.odf"

---

### Post by airtonix on 2007-10-29
dont like your idea mangr.

but i do like how you tried to move them away from where they were.

i would like to see all components 'dragable'..the files frame, the tree frame ,teh tool bars the buttons on the bars.....everything...nothing is sacred!

except my bad speliing

---

### Post by mangar on 2007-10-29
@airtonix
Brainstorm time!
What, in your opinion, would be a better use?
(I've just described the way it's done in Vista, which is okay, IMHO).

Please provide use-cases.

---

### Post by BungaMan on 2007-10-30
I don't care how nautilus is overhauled, as long as it doesn't waste space and uses small icons and can show split panels showing 2 directory contents next to eachother.

---

### Post by coolen on 2007-10-31
Two words: split view.

---

### Post by BungaMan on 2007-10-31
Here's my split view mockup.  Very simple.  Two dirs, side by side.  Joined the two toolbars into 1.  Nautilus is for file management.. well now you can get the job done easier.  Copying from one place to an other is more obvious. So is comparing directory content.  Drag n drop ... the whole thing will become a pleasure to work with.

Imagine how easy it would be to compare two dirs with digicam pictures and both containing a whole bunch of XYZ_001.jpg.  With icon view you can easily compare them without needing to open the files.

---

### Post by booljayj on 2007-10-31
You are spot on with a lot of your ideas, especially moving the zoom bar to the bottom and adding the filter bar. Yes, I said filter bar, because that's ideally what it should be. It should filter not only entities in the current directory, but in subdirectories as well. Tracker search tool, already packaged with Gutsy, would be the way to do this. If I'm in a folder with these sub-folders and files:

school/homework/essay1.doc
school/homework/cells and stuff.odt
school/information/essay1prompt.doc
music/simon says.mp3
music/misc/come sail away.mp3
music/misc/say anything.mp3

typing "say" in the filter bar should yield this revised tree:

school/homework/essay1.doc
school/information/essay1prompt.doc
music/simon says.mp3
music/misc/say anything.mp3

You get the idea. Also, I like the idea of hiding the back/forward buttons within the breadcrumb mode. This makes perfect sense to me. Make it a configurable option and you've just made everyone happy.

---

### Post by coolen on 2007-10-31
Okay, I'm all for the filter box.
Combine it with a split view (I'd prefer multiple views, but two is better than one), and you've got yourself a killer file manager.

---

### Post by gabtrat on 2008-03-27
smartboyathome's last mockup is basically what I was thinking.
However buttons to change between icons and list view would be nice.

---

### Post by graabein on 2008-04-08
> **coolen said:**
> Okay, I'm all for the filter box.
Combine it with a split view (I'd prefer multiple views, but two is better than one), and you've got yourself a killer file manager.

[GNOME 2.24 will hopefully include...]("http://ubuntuforums.org/showthread.php?p=4506335#post4506335")

But wait a tick, what exactly is column and list views? Is it something like list and detail views in *ugh* Windows Explorer? Or is it like the Mac (columns)?

---

### Post by 23meg on 2008-04-08
That's probably a typo; list view has been available for ages. What's new is the "Compact" view ([available in trunk now]("http://blogs.gnome.org/cneumair/2008/03/30/compact-view-has-landed-in-nautilus-trunk/")). Column view is probably like Finder's columns.

---

### Post by graabein on 2008-04-11
> **23meg said:**
> That's probably a typo; list view has been available for ages. What's new is the "Compact" view ([available in trunk now]("http://blogs.gnome.org/cneumair/2008/03/30/compact-view-has-landed-in-nautilus-trunk/")). Column view is probably like Finder's columns.

Well that's good news. I've not tried OS X too much but the column view could be useful I suppose. Home directories seldom have very deep directory trees, don't they? And compact view looks good enough. 

Another thing I'd like to see in a file manager is the possibility of bigger icons/thumbnails for browsing image directories. Faster than having to open an image viewer program...

---

### Post by mangar on 2008-09-27
Updated mockup.
I've been using Leopard lately, and Finder is a pretty awful file manager.
Than I've found Pathfinder. The best browser-metaphor (Explorer style) file manager ever.

More details:
[http://www.cocoatech.com/pf4/](http://www.cocoatech.com/pf4/)

---

### Post by UbuWu on 2008-09-27
I like your mockup. Love the simplicity of it. I don't like pathfinder as much. Did you add a brainstorm idea we can vote for?

---

### Post by mangar on 2008-09-27
I've added the ideas to brainstorm:
[http://brainstorm.ubuntu.com/contributor/mangar/ideas/](http://brainstorm.ubuntu.com/contributor/mangar/ideas/)

I won't add a "Copy Pathfinder" idea, since it's guaranteed to get negative vote..

---

### Post by Choad on 2008-10-02
> **mangar said:**
> synopsis:

1. The crumb bread navigation makes "back" "forward" "up" "stop" "refresh" button redundant, as they replicate functionality already provided by the crumb bread navigation, I think they can be removed.

2. "home" "computer" are already present at the "places" dialog,
they can be removed.

suggestions:
1. remove nautilus' tool bar, it serves no purpose.

2. replace zoom in / out with a slider, move it to the lower right corner (similar to ms - office 2007)

3. replace the "icons/ details" drop down list with two icons,
move it to the left of the zoom slider.

4. replace the zoom slider and the mode switcher with a search box.

[snip]

+1 from me. that looks way better

---

