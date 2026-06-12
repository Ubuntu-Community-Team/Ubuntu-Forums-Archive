---
title: "Hardy Heron--Fix for Gimp 2.4.5 Problem with Moving Selections."
date: 2008-05-19
forum: Ubuntu Studio
---

### Post by VirtualEntity on 2008-05-19
Gimp 2.4.5 has changed the selection tool considerably, eliminating it's "old" mode of operation where you could drag to move a selected part of the image or (I think) shift and drag to copy said selected part of the image.

Now, it appears that the old technique only succeeds in moving or resizing the selection box, (ellipse or whatever) without having any effect on the image or the portion we want to select.

There is also a bug in the "Move" toolbox dialog that shows when one changes the default to "Move: Selection (red square icon) instead of the default of the entire image/layer which is that the greyed out options are both "Move selection".  Of course, for our benefit, "Move selection" is selected....confused:

While there is no fix presently available for this cosmetic bug, the work-around to get the select tool working to move or copy parts of an image is as follows:

To actually use the selection tools to MOVE or COPY parts of an image or layer around, do the following:

1. You select a region and then commit the selection by pressing the enter key, by clicking on it once.  Don't click an edge, though, or the select will resize or re-shape.  Click ONCE in the center of the selection.  (Twice will just return you to the resizeable/editable select box.)

2.  COPY THE SELECTION TO A NEW LOCATION:
Hold down Shift and Alt.  Click the selection box once, then again to copy its contents and move it around to wherever you want the contents copied.

  -or-

3.  MOVE THE SELECTION TO A NEW LOCATION:
Hold down Control and Alt.  Click the selection box once, then again, to MOVE its contents around to wherever you want it moved, leaving the original location blank (prob. with layer base-color showing through.)


People had some problems with these control keys under some desktop environnements and some distributions so you'll have to try it on yours.

I have tested it and found that it works just fine with Hardy Heron X64 on an HP HDX Dragon 9000 20" laptop.

---

