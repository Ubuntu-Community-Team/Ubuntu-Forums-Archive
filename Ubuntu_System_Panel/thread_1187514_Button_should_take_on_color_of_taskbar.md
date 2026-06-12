---
title: "Button should take on color of taskbar"
date: 2009-06-14
forum: Ubuntu System Panel
---

### Post by cmost on 2009-06-14
I've been using USP for a long time!  Love it!  I recently installed one of the new Murrine themes and added a custom background for my gnome-panel.  Unfortunately, USP's background did not shift to match the gnome-panel background and stuck out like a sore thumb.  In fact, it still stuck out even when I switched the panel to "use system theme" for the panel.  Ugly!  Believe it or not, I went back to Gnome's default 'Applications, Places, System' bar to maintain a nice appearance.  It seems as though USP should always take the background of the gnome-panel.  Any thoughts?  I'm using USP 2, the latest version.

---

### Post by Malac on 2009-06-15
USP follows the theme that the desktop is currently using, unfortunately if you change the theme in anyway usp requires that you log out and back in again or killall gnome-panel to register the change. This is an unreported bug that is low on the dev list at the moment.

Hope this helps.

P.S. If this is not a solution to your problem then post again with screenshots please.

Thanks, Malac.

P.P.S. I've just read your post again and see what you are getting at now. We used to have an option I seem to recall way back in usp 0.41 which let you set a background image for the button. I will have a dig through the old code.
Malac.

P.P.P.S. :)
Okay I have checked through the code and it is definitely a bug I have fixed it and should be doing a commit to the SVN within an hour (time now is Mon, 15 Jun 2009 23:40:40 +0100 )

P.P.P.P.S. :D
Fix uploaded to SVN Rev# 426

---

### Post by cmost on 2009-06-15
Hi Malac!  Thanks so much for your response.  I went ahead and updated via SVN but unfortunately the issue persists.  I've included two screenshots:  the first one shows the updated USP menu with my current theme.  Notice the solid black background while the rest of the panel is translucent.  The second screenshot shows how Ubuntu's Applications, Places, System menu bar appears on the same panel.  Whatever code causes the menu bar to display in the same manner as the gnome-panel should be incorporated into USP if it's not too difficult a feat.

---

### Post by Malac on 2009-06-15
Did you reload usp after updating from the SVN or killall gnome-panel or logoff then on again.
I have done the code on mine and it now gives me this:
[ATTACH]117820[/ATTACH]
for set colour for 50% transparent.

And this:
[ATTACH]117821[/ATTACH]
for a picture.

If this persists after a reset can you let me know which theme it is you are using and which picture is not transfering to usp correctly. If it's one of your own please attach it or pm to me.

Thanks.

---

### Post by cmost on 2009-06-20
Hi Malac!  Thanks for your assistance.  I'm sorry I didn't reply sooner as I have been out of town on business.  I tested the revised USP but it seems to look the same.  The theme I'm using is a Murrine theme called "smootheWhite" from Gnome-look.  Other themes exhibit the same issue.  I should inform you that I have recompiled Nautilus with rgba enabled.  This adds subtle transparency to Window frames and the gnome-panel.  Perhaps this is the root of the issue.  If it's too big a hassle to fix at this time, don't worry.  I can wait patiently for USP 3!  :lolflag:

---

### Post by Malac on 2009-06-20
> **cmost said:**
> Hi Malac!  Thanks for your assistance.  I'm sorry I didn't reply sooner as I have been out of town on business.  I tested the revised USP but it seems to look the same.  The theme I'm using is a Murrine theme called "smootheWhite" from Gnome-look.  Other themes exhibit the same issue.  I should inform you that I have recompiled Nautilus with rgba enabled.  This adds subtle transparency to Window frames and the gnome-panel.  Perhaps this is the root of the issue.  If it's too big a hassle to fix at this time, don't worry.  I can wait patiently for USP 3!  :lolflag:
I don't think it would have anything to do with your "custom" nautilus. As far a I know gnome-panel draws itself and doesn't rely on nautilus for anything here.

Can you try doing another update only this time use "./usp_update* **install***", then Reboot the computer.
There may be a bug in the update script which is not updating certain files. I have noticed this with the language files a couple of times. Latest SVN Rev is #430.

Thanks again for your patience.:D

---

