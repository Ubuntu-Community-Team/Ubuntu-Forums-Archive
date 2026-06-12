---
title: "interesting visual effects in Gnome Shell"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bmbaker on 2012-02-23
latest update from ricotz-testing ppa gnome-shell version 3.3.90 give a nice effect to the menus and pop-ups :-)

---

### Post by bmbaker on 2012-02-23
filed a bug if anyone else is having this issue!
Bug 670702 - gnome-shell dialogues missing rounded corners

[https://bugzilla.gnome.org/show_bug.cgi?id=670702](https://bugzilla.gnome.org/show_bug.cgi?id=670702)

---

### Post by jbicha on 2012-02-23
How do you know this isn't a problem with your graphics driver instead?

---

### Post by tista on 2012-02-23
Hi bmbaker,

Same issue +1.
Yeah I've experienced that "missing corners" on 3.3.90. and a bit more badly thing, gdm 3.2.1  had similar ugly appearance on gdm-greeter as well... X(

But I suppose it might be caused by codes of gnome-shell instead of mesa drivers because simple mutter desktop effects worked perfectly as another desktop session like gnome-session-fallback or so... anyway now I have not any ideas to solve this. ;)

Anyone knows? or jbicha could do? :)

Regards,
Tista

---

### Post by bmbaker on 2012-02-24
> **jbicha said:**
> How do you know this isn't a problem with your graphics driver instead?

cause it was fine till gnome-shell bumped to 3.3.90 and also the themes mutter etc!

so i filed the bug under gnome-shell themes ......... have to start somewhere :-)

---

### Post by mode7 on 2012-02-25
Wow, this is the only mention I can find *whatsoever* of this exact issue. I am, however, running 11.10, and have this issue on gnome-shell 3.0 and 3.2.
I should note that I am using **xorg-edgers**, so the issue could be related to that.
I am running this on a late 2011 Macbook Pro 8,1, with an Intel HD 3000.

I cannot register on the Gnome Bugzilla at all.. have tried 2 email addresses, and waited several hours. (Yes, checked junk mail, etc)

EDIT:
Purging xorg-edgers and reverting back to 11.10 xorg packages completely fixed the issue for me.. I hope this somehow helps devs to fix the issue, and get you 12.04 users on track again!

---

### Post by jbicha on 2012-02-25
And what do you know, for one user, it *was* a graphics driver problem. :-)

I'm still on gnome shell 3.3.5 but I'll upgrade to 3.3.90 soon....

---

### Post by ricotz on 2012-02-25
> **mode7 said:**
> Wow, this is the only mention I can find *whatsoever* of this exact issue. I am, however, running 11.10, and have this issue on gnome-shell 3.0 and 3.2.
I should note that I am using **xorg-edgers**, so the issue could be related to that.
I am running this on a late 2011 Macbook Pro 8,1, with an Intel HD 3000.

I cannot register on the Gnome Bugzilla at all.. have tried 2 email addresses, and waited several hours. (Yes, checked junk mail, etc)

EDIT:
Purging xorg-edgers and reverting back to 11.10 xorg packages completely fixed the issue for me.. I hope this somehow helps devs to fix the issue, and get you 12.04 users on track again!

Yes, xorg-edgers ppa was the problem here caused by a cairo bug which is fixed now.

---

### Post by tista on 2012-02-25
@jbicha, ricotz and mode7

Thanks for your tracking this issue down... ;) exactly I've used xedgers ppa.

Regards,
Tista

---

