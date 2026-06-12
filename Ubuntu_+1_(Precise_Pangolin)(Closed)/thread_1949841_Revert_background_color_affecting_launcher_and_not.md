---
title: "Revert background color affecting launcher and notification area color"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sacridex on 2012-03-31
Hello,

in some older patch the color of the launcher has been changed to pickup dynamically the color of the background, and in some recent patch the notification area in the top right corner does the same.

So my question is, how can i get back to the black styled launcher and notification area?

Some attachments to show what i mean:
In my first attached screenshot you can see the notification area(volume information).
And i also tried to change the launcher color, because there is a setting option in CCSM.
I just raised the opacity(to 160, but it doesnt matter, the effect appears with opacity 1 too) and all the Launcher items are now pure black. :(
In the second screenshot i changed the color to rgb(1,1,1), then the launcher is no more pure and dark black, but the Dash/Trash Icon is gray instead of black.

And in my last screenshot you can see the old launcher style, the screenshot was taken directly before the patch with the new color behaviour came(I was just updating as you can see ^^).

thx

---

### Post by mc4man on 2012-03-31
It's a pretty tough go to get 'black' or a 'smoked glass' launcher in unity-3d
As far as the notify-osd - if you use version as noted here it looks pretty good. -  [http://ubuntuforums.org/showpost.php?p=11806123&postcount=5](http://ubuntuforums.org/showpost.php?p=11806123&postcount=5)

The launcher is a different story, maybe the code  can be reverted but the change was quite some time ago...

If #000000 was usable in the override then that would be one way but as you've seen it's currently not in the least.
(whether a bug or limitation not sure, filed some time ago here
[https://bugs.launchpad.net/unity/+bug/924586](https://bugs.launchpad.net/unity/+bug/924586)

An almost, but not really, solution is to set the background override to #000001, then set the icon display to 'Backlight and Edge Illumination'

If they ever managed to get the 'no blur' option to actually work that might do it or close, though wouldn't hold breath, it's almost never worked in the past yr.+

---

