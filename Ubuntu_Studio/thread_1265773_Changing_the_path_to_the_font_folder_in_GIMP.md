---
title: "Changing the path to the font folder in GIMP"
date: 2009-09-13
forum: Ubuntu Studio
---

### Post by Warren Watts on 2009-09-13
My daughter complained yesterday about not having access to all the fonts she has installed on her computer available to her when she is using GIMP on a different computer on the network.

That got me to thinking, and after a little investigation, I discovered that GIMP can be set up to load the fonts from a specific location.

I copied all of the fonts from her computer to a network share on my server, and voilà!   All of her fonts are now available to her (or anyone else in the network who uses GIMP) on any computer on the network!

Here's how to change the path to the fonts when loading GIMP:

Open GIMP (Duh!)
From the menu, choose Edit-->Preferences
In the Preferences dialog, expand the Folders option in the left pane, and choose Fonts.  (Attachment 1, circled in green)

Click the new folder button (Attachment 2, circled in red), then click the browse button (Attachment 2, circled in blue)

Navigate to the network share that contains your shared fonts, and click Ok! (Attachment 3) 

It's that easy!  Please note that my screenshots are of Xfce Dialogs, but the dialog boxes will be almost the same regardless of the windows manager you are using.

This same text is available with the images inserted in the text on my blog, [Adventures in Linux]("http://kingbeetle66.blogspot.com/2009/09/truetype-fonts-on-network-share.html").

---

