---
title: "[IDEA] New Universal Launcher/Menu- Revolve"
date: 2007-10-31
forum: Ubuntu Brainstorm
---

### Post by booljayj on 2007-10-31
Note- I am incapable of programming this myself, but could easily manage a project like this if called upon to do so.

I propose a new universal launcher/menu for the gnome desktop. It is called "Revolve". Slogan: Life should revolve around you.

I have seen and used many beautiful menus and launchers, but I always find them lacking. gDesklet launchers like gnomedock work well at what they do, but are stiff and ugly. Window managers like AWN look wonderful, but could never fulfill the task of being a complete system menu. Many people have their own agendas on how a menu/launcher should look and feel, and often make something so specific that only people like themselves can use it. I'm sick of it, and it's not the way things should be. Why not change it up a bit.

Quicksilver's (Mac) Costellation plugin is the perfect example of how a menu can be set up in both an easy to use and powerful manner. Quite frankly, though, it's just way too cluttered. We need something powerful yet simple for the gnome desktop, something that follows recognizable laws of interface design, something that we can all use easily and cleanly regardless of skill level or application.

First: the user presses the activation key. Everything on the screen dims out, and a circular menu with 4 cardinal directions fades in.

Second: the user reaches for the directional arrows. The user should need nothing but these four buttons to navigate the entire menu. He presses the right button corresponding to the right part of the circle, which happens to open a programs menu.

Third: The circle fades and moves slightly to the left and a list of categories emerges from behind it on the right. This list has five visible options which fade out in either direction. The categories are named for each of the categories of programs in the Gnome menu. The user scrolls the list by pressing up or down, focusing on the category they want to view.

Fourth: The circle and smaller menu move yet again to the left to make room for a list of actually programs to emerge on the right. This list can be navigated by pressing up and down. When the user selects the program they want, they simply press right once more to activate it, causing the whole menu structure to fade away while the application opens.

Fifth: Say the user did not want to open that program, or any at all. They simply need to press left once to move back to the categories list, and left again to focus on the main circle.

Sixth: Now they press up, which leads them to a system menu. The circle fades and moves down while a hyperbolic list structure appears above (subject to change. I need to find something pretty, unique, and easy to use). Preferences form a list arcing to the top and bottom left corners, fading as they get further, and administrative utilities form a similar structure on the right. In the middle is a loqout/power menu.

Seventh: Pressing left will focus on the preferences menu, allowing the user to scroll through the list in a similar method as before. The same occurs when the user presses right. Pressing up will invoke a new method that goes over all the others and contains all logout and power options. Pressing down will, once again, move the user back to the circle.

Eight: The user has not done anything, but still wishes to close Revolve. All they must do is press any key other than an arrow key to exit.

This method will allow a user to access a program in 5 button presses. Yes, it's true that the same can be done with 3 clicks of the mouse on the Gnome Menu (if one clicks on each category to open it), but that does not factor in the time it takes to move the mouse, focus on the correct option, or wait for the menu to open while hovering. This method will be fast, especially if the user can define the order of the programs/categories in the menus. They could keep their most used programs closer to the center and their least used further.

This could easily be implemented in Python, which would allow numerous plugins to easily be written and would give the whole program a very liquid feel. The Cairo libraries seem to be the place to go for vector art animations and the like, so those could be used. Overall I would like to see something as easily modified as Quicksilver, without becoming as bloated as it is. For instance, Amarok users could find a plugin that would allow them to scroll through their albums/artists and set them to play. Compiz users could enable true transparency and accelerated effects. The possibilities are endless.

So... who's with me?

---

### Post by gsiliceo on 2007-10-31
Is good but remember the usability law number 1, dont make the user click(or hit the keyboard) more than 3 times to deliver what he wants.

---

### Post by booljayj on 2007-11-01
Interesting. Do you think that would really apply to something like a program menu, especially one using a regular pattern of easily remembered key presses? I would think that mouse track time takes a big part as well, and this interface would eliminate it completely.

The launcher part of this menu would allow users to set up a list of favorite applications, and those would require much less time to access.

How could this program be modified to keep to that law?

---

### Post by booljayj on 2007-11-01
Crap, posted twice, sorry.

---

### Post by coolen on 2007-11-01
Very nice. Perhaps a favourite applications menu could appear at some point. You most frequently used applications are automatically added to it. You could perhaps implement some form of quick-launch, let the user select their own applications.
This seems like an addon like AWN. Perhaps not implemented in Gnome itself, but a beautiful addition to the desktop.

---

### Post by phenest on 2007-12-28
I have to say, that as far as menu systems go, this will be no easier than any other. But, this is worth doing, simply because it's more aesthetically pleasing than a boring, unfriendly popup menu

I have one more idea to add to this which may improve the navigation and reduce the amount of key presses/mouse click the user needs to do:

Rather than wait for a key press/mouse click to open the sub menu, the sub menu should already be visible (albeit faded out slightly), subject to the most focused item in the original 4 directional 'wheel' or current 'parabolic menu', so the user can see where that item will end up or open next.

With more thought on this, this could use some sort of algorithm to 'Intelligently' guess what the user is looking for by what direction they choose and what sub menus appear. Perhaps based on what applications the user has previously used before and uses most.

Perhaps to the point where a simple pressing of Enter will open the application in the last sub menu without the need for further cursor presses.

Oh yes, one more thing - this must allow the user to use keyboard and/or mouse.

---

### Post by lexen on 2007-12-29
At first, I thought this was a good idea, but it really is to complicated.  It is new, which is good, but people always need to be convinced to do something new and I don't think this has enough going for it to make it convincing.  It looks better, but I could imagine it would slow them down.

     If you have the applications menu dominate the screen, why not show all the options available and have colored boxes around each section.  That way it would be 2 clicks verses 5.  It might take more eye time, but as you adjusted it would get faster and faster.

     In order to get this to work, you would need something that makes it a lot easier to get what you want.  I think both the current system and your system could be replaced with a voice recognition system, but that won't be up and running for a while.

---

