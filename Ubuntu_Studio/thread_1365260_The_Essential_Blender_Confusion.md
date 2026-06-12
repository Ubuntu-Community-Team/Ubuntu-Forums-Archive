---
title: "The Essential Blender Confusion"
date: 2009-12-27
forum: Ubuntu Studio
---

### Post by Joseph Schwenker on 2009-12-27
There is a section in Chapter 3, page 56 of The Essential Blender that says

> You'll see that this animation is not satisfactory for two reasons. First, the electron follows more of a diamond shaped path around the nucleus than a circle. Second, the electron stops below the nucleus, instead of continuing back through to its starting point.

First, let's round out the path that the electron follows. With the electron selected, press the K-key. Three olive-colored copies of the icosphere appear, one at each of the locations where we had set a key. The K-key toggles the display of keys in the 3D view.

Scrub with the LMB in the timeline until the electron is halfway between the left and upper keys.

If you try to use the G-key at this point, you will find that the icosphere does not move. This is because in this key view mode your transformations like move, rotate and scale only work on already set keys, not the actual object.

So, let's add a new key here, then move it to create a better circular path. Use I-key, and select "Loc" as before to insert a new key. Then with the G-key, move the key up and to the left. You will see the electron object move too, but this is only a result of moving the key. You are not moving the electron directly.

This part confuses me, as when I move to the frame halfway between the left and top frames (32) press I, then Loc, and then try to move the key, all of the electron keys move.  If I press the K key so that only one key is visible, then I can just move one.  This is very confusing to me!  Could someone help to explain why this is happening?  I am using Blender 2.48a.

---

### Post by cotcot on 2009-12-27
I followed the example in the book and made a note on the same issue that it is not OK. I have no answer yet. Best is to go with this question to the [[COLOR="Red"]blenderartists[/COLOR]]("http://blenderartists.org/forum/") forum.

---

### Post by Joseph Schwenker on 2009-12-27
> **cotcot said:**
> I followed the example in the book and made a note on the same issue that it is not OK. I have no answer yet. Best is to go with this question to the [[COLOR="Red"]blenderartists[/COLOR]]("http://blenderartists.org/forum/") forum.

Thanks, I'll try and ask my question there.

---

