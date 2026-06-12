---
title: "Drag windows from anywhere: Interest?"
date: 2008-08-25
forum: The Cafe
---

### Post by Mr. Picklesworth on 2008-08-25
I have built a patch for Metacity that allows one to drag a window from any unused portion. This is a very simple change (in fact, a removal of what stops the behaviour in the first place! -- more on that later). It is like how Matchbox (aka. the window manager used in Maemo) behaves with dialogs set to Free position mode instead of Fixed.

Here is a mailing list discussion on it:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005330.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005330.html)

Here is my branch on Launchpad:
[https://code.launchpad.net/~dylanmccall/metacity/drag-from-anywhere](https://code.launchpad.net/~dylanmccall/metacity/drag-from-anywhere)

To test this, download the code from my branch on Launchpad. Build it by running sh autogen.sh then make. DO NOT INSTALL IT. Instead, test it by running "./src/metacity --replace" after building. (This way no long-term changes should occur).

Often, this is really superbly cool. For example, with the patch applied I can basically drag any simple GTK-powered window (like panel Properties) from anywhere that feels 'fixed' rather than detachable (in the sense of our visual metaphors). Technically, that is not expecting mouse input for other reasons. Where it works well, I think this gives the desktop a more cohesive, physical feel. That's exactly what we are heading towards with artistic design and with a lot of composited effects (like the wobbly stuff in Compiz). I like to think of windows as something like playing cards being pushed about, so it fits well with that little metaphor.

However, this falls apart with more complex applications and with some other widget toolkits. GTK toolbars and menubars, some containers (like the container for GNOME Appearance Preferences) simply cannot be clicked on to drag a window from within -- even though they intuitively should -- because they act like black holes for mouse events. Firefox doesn't work. OpenOffice doesn't work. (Midori, Epiphany, Abiword and Gnumeric do. *Hint, hint*).
This seems to have been something overlooked in the design of windowing systems and UI toolkits in general. Looks like as soon as a child widget is listening for button events, they'll never reach the parent even if the child gets said event and has nothing to do with it. (For example is disabled or the click is not on the target area, as in toolbars or menubars). Thankfully, the handlers are usually supposed to return 0s somewhere along there.
I can't help but wonder whether this is necessary...

My thought is it probably could be fixed, but could take a huge amount of digging. It also would require that a lot of bug reports be filed along the lines of "this application" or "this widget is sinking mouse events that it does nothing with". For this to work, it would have to kick up a lot of dust; the effect *itself* is consistency or nothing.

Hence this post. This is an arguably trivial thing interface-wise. Basically, you would be able to drag a window from its backing instead of just by its title bar, and this behaviour becomes consistent instead of being only in some places.
For example, MacOS and Windows Vista have this type of behaviour in some default apps. Usually just drag by the toolbar and the status bar, even though other parts of the window are just as stationary. It is not intuitive or predictable because it is implemented at the level of each individual application instead of the toolkit. The window manager itself should handle this, because the toolkit doing it is duplicating functionality that could be subject to change.

I think this will be important as we move towards more touch-based interfaces where clicking on a title bar is not feasible or intuitive with how a touch interface is usually designed. Do you think this is worth it to pursue? What do you think of the idea so far? Does it break anything?

Most importantly: Would you find it a problem if windows behaved the way I propose, or would you welcome the change?

---

### Post by FuturePilot on 2008-08-25
I really like this idea. In fact just a few days ago I was wondering if this could be possible with all applications, as I know some do do this. I really like this functionality. And like you said it would definitely be easier if we are going to be moving towards touch based interfaces in the future.

---

### Post by master5o1 on 2008-08-25
Considering that Songbird can, I expect that it is possible to change firefox somewhere so that it can too.

---

### Post by Sinkingships7 on 2008-08-25
I didn't read the whole thing thoroughly, but the basic gist of it that I got was that this patch allows you to move windows by clicking anywhere on the application and dragging it, so that you don't have to use the title bar. If my 'gist' is correct, how is that any different from holding Alt and clicking/dragging the window? The only place where I see this being really functional is in a touch-controlled environment. 

Again, I'm pretty sure that I missed something big, so please feel free to correct me. Just don't be mean. :)

---

### Post by v8YKxgHe on 2008-08-25
What's wrong with jut using alt+click to move it? Or have I missed something here?

---

### Post by master5o1 on 2008-08-25
> **AlexC_ said:**
> What's wrong with jut using alt+click to move it? Or have I missed something here?


True.

---

### Post by the yawner on 2008-08-25
> **AlexC_ said:**
> What's wrong with jut using alt+click to move it? Or have I missed something here?

Because the idea provides usability to unified themes? I.e. themes that have no dividing line between the title bar and tool bars underneath.

---

### Post by v8YKxgHe on 2008-08-25
> **the yawner said:**
> Because the idea provides usability to unified themes? I.e. themes that have no dividing line between the title bar and tool bars underneath.

I can't see the relevance of that, using alt+click works regardless of what theme you're using.

---

### Post by the yawner on 2008-08-25
Here's the theme I'm using.

[IMG]http://img.photobucket.com/albums/v90/kiel_008/Screenshot-metacity-theme-viewer.png[/IMG]

As you can see, there is no defining line separating the title bar and the tool bar. It might take a little bit of practice before someone gets accustomed that the window can only be grabbed on the title bar area because of the lack of visual hint. I've read on Gnome's HIG that design should be forgiving of users. In terms of usability, this is a no-no.

Alt+left click is only an alternative to grabbing windows. But it cannot replace direct and seamless interaction with a window and the objects/widgets within.

---

### Post by v8YKxgHe on 2008-08-25
I see, I guess it does make sense to do that really.

---

### Post by Wolki on 2008-08-25
> **AlexC_ said:**
> What's wrong with jut using alt+click to move it? Or have I missed something here?

You lose the alt key for mouse operations. Several applications (usually cross-platform like eclipse or firefox) have mouse button + alt shortcuts for useful stuff. If movement didn't require that shortcut, it could be used for these things.

Mr. Picklesworth, do you have a patch against the version of metacity that's in the repos? I build my own anyway to unbreak workspaces, so I'd try it out.

---

### Post by Bou on 2008-09-29
Hi Mr. Picklesworth, I had the same idea yesterday and opened [this thread]("http://ohioloco.ubuntuforums.org/showthread.php?t=932413") to ask whether it is technically possible. I'm glad to see it is.

I don't have time to read the mailing list thread right now, but I can't wait to do it when I get back home.

Thanks a lot for doing this.

---

### Post by hessiess on 2008-09-29
> **AlexC_ said:**
> What's wrong with jut using alt+click to move it? Or have I missed something here?

it conflicts with a large number of supplications

---

### Post by saulgoode on 2008-09-29
Wouldn't such behavior interfere with the ability to select multiple widgets within a window? For example, drawing a rectangle around a group of icons, or selecting a block of text. If the mousedown event is not over a widget, how does the operation determine that the subsequent mouse drag should not move the window?

---

### Post by Bou on 2008-09-29
> **saulgoode said:**
> Wouldn't such behavior interfere with the ability to select multiple widgets within a window? For example, drawing a rectangle around a group of icons, or selecting a block of text. If the mousedown event is not over a widget, how does the operation determine that the subsequent mouse drag should not move the window?

I think you're misinterpreting the idea. Only areas where currently you get no interaction AT ALL would be used to drag the window. It'll be clearer with a quick mockup I used on my thread:

[IMG]http://img385.imageshack.us/img385/5350/pantbn3.png[/IMG]

---

### Post by Bou on 2008-09-29
By the way Mr. Picklesworth

> **Mr. Picklesworth said:**
> I have built a patch for Metacity that allows one to drag a window from any unused portion.

I thought that it would be GTK you would have to make a patch for, so I'm surprised to see it's a window manager stuff. Do you think a similar patch could be made for Compiz?

---

### Post by Mr. Picklesworth on 2008-09-29
The window manager handles dragging windows, so yes indeed. It's a state fairly unique to desktop Linux and the X window system, but quite cool.
I believe GTK *could* do that, but then I would have to strangle myself. I am firmly opposed to a widget toolkits duplicating the toplevel window manager's job, because it makes changing the behaviour very difficult and it makes window dragging an erratic / clumsy operation.
Windows and MacOS apparently have options for some widgets that developers can toggle which say "this widget can be dragged to move the window", but I think that is a bit silly. (For an example, see how Windows Photo Gallery cannot be moved with a click on empty parts of the window while Media Player can).

A similar patch could *undoubtedly* be made for Compiz, since the matter is really just watching for mouse events in the client widget as well as the title widget.

Having said that, I still need to get around to writing a patch for GTK and give the toolkit people a stern talking to that will undoubtedly unearth why this is the way it was. The fact is, this functionality is disabled explicitly by most window managers because it doesn't quite work; windows take mouse events and then don't use them all the time!
GTK 3, perhaps, could break a few more APIs to take this a step further ;)


At the moment I am still fiddling with kinetic window dragging, so am holding off on that matter. (Throwing stuff is fun).



Why do it and not just alt + drag?
It's about usability. Power users generally don't 'get it', but I am thinking forwards to big desktop touch screens and casual users touching Linux. (Haha). I think this adds a wonderful tactile touch to the environment that is lacking elsewhere.This way, a window is a physical object on a low friction mat:

Some widgets detach from the window, such as icons that can be dragged away onto other things.
Other widgets are very shiny, so one can't pull the window with them (buttons...).
Finally, lots of widgets have some friction or are just painted on the window for decoration. One can naturally drag the window with those.

We currently have the first two points there, but not the third. The third point is critical, however, if we want dragging things to make sense in a natural interface kind of way.



And a quick explanation for the uninitiated. Beware, this will flip your universe upside down:

With the X window system, essentially everything is a window. That is, not just a window from your web browser, but every *widget* inside of that! Every button, text box and pane is a window. (With the exception of XUL, which is evil).

Metacity and Compiz basically look a the top level windows -- that is, the ones people generally recognize as windows (dialogs, menus, windows of Firefox), and add some goodies to make them easily manageable for the user. That is things like shadows to give them depth, title bars, close buttons, window switchers and the ability to move windows (since without a window manager they'll just pile at the top left of the screen).

A neat bonus with all of this is that any widgets (windows) can now be extended with functionality from all sorts of software. For example, you can lock windows from certain input devices so that only one mouse can access them. A program can insert its content inside of a window created by another program (this is how web plugins work).

Xorg sends input events to windows, such that the window with focus usually is the one to get an event. Each widget (window) says that it is listening for particular kinds of events, so Xorg knows to send it those, and any other types of events are sent to its parent, or its parent's parent, or so on. In our case, mouse events ultimately hit the toplevel window managed by Metacity since no widgets between it and what was clicked are listening for mouse events.

---

