---
title: "Idea: concept-based theming"
date: 2009-04-04
forum: The Cafe
---

### Post by MaxIBoy on 2009-04-04
I've been thinking about this for a while, and I'm pretty sure I have this figured out.


User interface design has begun to stretch the boundaries of the desktop metaphor. This may or may not be a good thing, but I think that a certain set of unspoken rules has emerged. The closer they are adhered to, the better the interface. All of these metaphors center around [scale invariance](http://en.wikipedia.org/wiki/Scale_invariance) of the user experience. There are two key concepts: objects, and the priorities of those objects. If you prefer, you can add a third concept, which is the progression of time (the "when" of the objects.) 


To get an idea of what I mean, a workspace is of higher priority than a window, a window is of higher priority than a tab, and a tab is of higher priority than a single icon. Each of these things is an object (or, if you prefer, a node in some kind of tree structure.) You can "promote" an object in priority (for instance, moving a tab to its own window or clicking on an icon,) "demote" an object in priority (minimizing a window, making it a component or "child node" of the taskbar,) and move an object between two parent nodes of equivalent priority (moving a window to a different workspace.) In addition, you can move an object "into the past" (click on a link to a different webpage) or pull an object "out of the past" (click on the "back" button in a browser.) 


I propose that, as you move up or down the levels of priority, the visual representations should have some kind of self-similarity. 

Furthermore, these concepts are simple enough that even a computer could keep track of them. This opens up interesting possibilities for encoding information about which metaphors to use, and embedding the information into the application itself. The developer of a browser could use some kind of API to mark the "back" button as a mechanism for pulling things out of the past. 

Then, the users could decide how each metaphor should be visually represented. Moving an object back from the past would, for one user, be a vertical animated scrolling effect, and for another user, would be an animated "spinning newspaper" effect. This would be theme-able, the same way Compiz users can go into CCSM and choose what animations to apply to specific events. That way, the users get a consistent visual experience accross all their applications, while leaving room for customization, and probably also making it easier for developers to keep their UIs clean and visually pleasing.




Thoughts?

---

### Post by geoken on 2009-04-04
First off, modern GUI's do store everything in a hierarchical tree.

Secondly, how would people know what an element is for when it's look is based of it's position in the display list (which is usually irrelevant to a user) rather than the actual function of that element. For example, if an app had a text entry area should that widgets 'look' be based on what it does rather than it's position in a display list.

To go with a simple tree metaphor, do you think a file manager would be more useful if the file icons represented the level of that file rather than what the file actually was. So instead of having different icons for pics, audio files and txt files they'd all have the same icon dependent on what level they're on.

---

### Post by MaxIBoy on 2009-04-04
I think I made it adequately clear that this should be "scale invariant." Scale invariance means that no matter how far in or out you zoom, it looks the same. Basic definition of a fractal. Promoting an icon to a file browser window would look somehow similar to maximizing a window.

---

