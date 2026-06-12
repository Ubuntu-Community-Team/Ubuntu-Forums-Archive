---
title: "Keyboard sleep button"
date: 2007-05-04
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2007-05-04
I have a keyboard that has extra buttons on it.  One was the sleep button, and it no longer works after I ran the convert_me script.  My other buttons I can re-configure, however I can't find out how to get that button to work again.  Any ideas?  I really like my sleep button, and it worked flawlessly (or seemingly so).

Shane

---

### Post by mhancoc7 on 2007-05-04
> **shane2peru said:**
> I have a keyboard that has extra buttons on it.  One was the sleep button, and it no longer works after I ran the convert_me script.  My other buttons I can re-configure, however I can't find out how to get that button to work again.  Any ideas?  I really like my sleep button, and it worked flawlessly (or seemingly so).

Shane

See if this post will help.
[http://ubuntuforums.org/showpost.php?p=2583271&postcount=6](http://ubuntuforums.org/showpost.php?p=2583271&postcount=6)

Let me know if that did it. I am keeping up with all of these little "bugs" so I can fix them in the next release.

God Bless, Jereme

---

### Post by shane2peru on 2007-05-04
> Tada!

Open up the Conf Editor (System Tools) and go to 'apps -> gnome-power-manager' and check 'can_hibernate' and 'can_suspend'

Their back!

Ok, this is all that pops up when I click the link.  That probably will fix it, but I'm not sure how to open the Conf Editor.  Where do I find that?  Thanks for the quick response.

Shane

---

### Post by mhancoc7 on 2007-05-04
> **shane2peru said:**
> Ok, this is all that pops up when I click the link.  That probably will fix it, but I'm not sure how to open the Conf Editor.  Where do I find that?  Thanks for the quick response.

Shane

Sorry :)

Open terminal and run:
gconf-editor

Then follow the instructions.

Jereme

---

### Post by shane2peru on 2007-05-04
> **mhancoc7 said:**
> Sorry :)

Open terminal and run:
gconf-editor

Then follow the instructions.

Jereme

hmmm,  Well, that didn't seem to fix it.  Usually to set my keyboard buttons up I go to **System -> Preferences -> Keyboard Shortcuts**  And I see a log out option, but I don't see a sleep option in there.  I didn't have to set it before, it just worked, so I don't know how to set that up.  Any other ideas? 

Shane

**Edit:**  OH, I should probably add that I rysnced my home folder and everything in it to an external drive before upgrading, so I can dump those files back here.  However, I like the menu setup, and design of the way that Ub. CE sets up the desktop (they have a great eye for setting up a desktop) and I don't want to loose those settings.  So if someone knew just the right file to move that would be really helpful!.  Thanks.

Shane

---

