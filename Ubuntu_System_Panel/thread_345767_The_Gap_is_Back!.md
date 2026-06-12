---
title: "The Gap is Back!"
date: 2007-01-24
forum: Ubuntu System Panel
---

### Post by hanzomon4 on 2007-01-24
Had this problem with the first usp and I fixed it by setting the panel offset to 0. With usp2 it will only go to 1 in uspconfig and the  gconf-editor setting for the offset gets ignored. I've already done the gconftool-2 --recursive-unset /apps/usp, so if anyone has any suggestions I'm all ears.

---

### Post by hanzomon4 on 2007-01-24
Never mind setting it to -5 in the gconf and reloading the plugins fixed it

---

### Post by chanders on 2007-01-24
Believe it or not, I thought of you when I wrote this fix :-D

---

### Post by delfick on 2007-02-25
i have this problem now :D (i think i've had it for a while actually :p)

no matter what i set the usp_offset to (and i killall gnome-panel after changing the number) the usp remains the same distance above the panel... (see screenshot)

---

### Post by kobewan on 2007-02-25
Yeah, I have the same problem. Try middle click dragging USP to a different panel though (or dragging your panel to a different side of the screen), and seeing if usp_offset works then. I've found that for some strange reason, USP has a gap when it is in a panel at the bottom of the screen, but works fine everywhere else.

---

### Post by delfick on 2007-02-25
> **kobewan said:**
> Yeah, I have the same problem. Try middle click dragging USP to a different panel though (or dragging your panel to a different side of the screen), and seeing if usp_offset works then. I've found that for some strange reason, USP has a gap when it is in a panel at the bottom of the screen, but works fine everywhere else.

yep, works if i move the panel to the top of the screen :D

---

### Post by groggyboy on 2008-11-18
So I've returned to USP after some time away.  Good to see it's still being developed.  I remember why I liked it so much!  Anyways, I have the bottom panel gap problem on Intrepid, and I was wondering if there was a fix.

---

### Post by Malac on 2008-11-19
Hi groggyboy,
Which version are you using as I have this on the latest SVN and offset 0 works on the machine I am on whether usp is on the top or the bottom panel position?
What height is your panel set to?
I'll look into this tonight on a couple of other machines and see if I can recreate it.
uspconfig does let you set it to 0 now in the SVN version.

---

### Post by groggyboy on 2008-11-19
my computer is currently unusable - i lost my wireless capabilities, and in trying to fix things, i completely borked it.  i'm doing a fresh intrepid install, but once i have things back up, i'll make sure i've got the latest svn version installed.  i'll get back to you later with more news/details.

---

### Post by groggyboy on 2008-11-19
ok: i have a fresh, up-to-date installation of USP on intrepid.  at first, there was no gap between USP and the bottom panel.  however, when i set the border width to "2" instead of the default "8", the gap reappears.  and no matter what value i set for the USP offset (negative, positive, or zero), the gap doesn't go away.  when i set USP's border back to 8, the gap stays.  my bottom panel is set to 26 pixels.

---

### Post by Malac on 2008-11-20
@groggyboy
I've tried to recreate this using the steps you describe and I can't. Either my theme isn't showing it as obviously or it's something else.
Can you make a backup of your settings using the [Backup] button in uspconfig/Preferences and attach it to a post so I can try your exact settings. Including theme name maybe good and whether you are using compiz or metacity. Thanks.

---

### Post by groggyboy on 2008-11-20
hey malac, thanks for taking the time to look into this.  i use compiz, and my theme is [Shiki-Colors]("http://gnome-look.org/content/show.php/Shiki-Colors?content=86717").  i've attached a screenshot and a backup of my settings (i had to change the extension from .xml to .txt so i could upload it).

---

### Post by Malac on 2008-11-23
New SVN Version uploaded Rev #374
Fix for bottom panel offset bug.
Turned out it was a theme issue. The offset needs changing depending on which theme you are using and panel height.
Please let me know if this doesn't fix it for you groggyboy or if it mucks things up for anyone else can they let me know, thanks.
 
P.S. As this is now working after the auto position stuff is resolved (which makes more sense to me) all users will probably have to reset their offset values, sorry.

---

### Post by groggyboy on 2008-11-24
hey malac!  i've updated USP, and your fix works!  thanks

---

