---
title: "blender does not have a window"
date: 2008-05-19
forum: Ubuntu Studio
---

### Post by jonjonssonite on 2008-05-19
when I start blender-windowed from the pull down ubuntu application menu in the top right, blender starts in full screen mode. Am I doing something wrong? Is this a problem with my computer, ubuntu, or blender?

Oh, and yes blender was installed through the add/remove program, and is fully updated to the current version as of today, may 19nth.

---

### Post by ebharv on 2008-06-22
Try this, either create a new blender launcher or modify a launcher (I created a new on on my desktop) and in the command field type:
 
blender -w -p 0 0 800 600

This will force Blender to open in a bordered window sized 800x600 with lower left corner at (0,0). If you want/need a bigger or smaller window change the 800 and 600 to the dimensions you need. If you use the -p switch you must have the four parameters after it. 

Here's a description of the parameters

-w force window with borders (supposedly mine didn't work either)
-p <x> <y> <w> <h> I'm assuming this means position 
...... <x> x position of lower left corner of window.
...... <y> y position of lower left corner of window.
...... <w> width of window.
...... <h> height of window.

for more help open terminal and type

blender --help

This is not a fix but a work around.

---

