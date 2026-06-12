---
title: "Empty menu"
date: 2007-02-09
forum: Ubuntu System Panel
---

### Post by cmost on 2007-02-09
I've been happily running the older release of USP (0.41-1) and decided to give the new one a try.  Before proceeding, I uninstalled the old menu and reset the gconf keys as instructed and also deleted the ~/.usp folder just to be on the safe side.  The new deb file installed fine and the new menu was easily added to my panel.  When I click on the menu, however, there's nothing in it.  It's empty.  (see screenshot.)  Any idea on how to fix this?  The specs for my system are in my sig.  Meanwhile, I'm going to have to go back to the old menu.  Thanks.

---

### Post by chanders on 2007-02-09
Hey cmost, see [here]("http://ubuntuforums.org/showpost.php?p=2122368&postcount=173")

---

### Post by cmost on 2007-02-10
Thanks Chanders, that worked!  I tried searching the threads for the answer, but, I didn't find that post you referenced as it was a bit buried and non-descriptive of the problem.  Anyway, I'm liking the new menu; I really like its flexibility and ability to customize!!!  Just a few questions (please forgive me if already asked.)

1.  How can I make the side pane containing the 'pin menu' button go away for good!  I've tried the various obvious approaches using both the 'preferences' dialog and gconf-editor but it always comes back!

2.  Is there a way to customize the 'Places' plugin to include only my favorite places (such as Computer, home, documents, music, videos, pictures, etc.)  Currently everything in Nautilus's side pane appears in the places.

3.  With the old USP (0.41-1) Beryl effects were applied to the Menu (I think Beryl considered USP to be a so called 'normal' window or dialog.)  When the menu would close, it would do so according to my 'Close 1' animation setting.  The new USP menu does not seem to obey Bery's settings.  Any way to get that back?

Much thanks and great work!!!!  I look forward to the final release!

---

### Post by chanders on 2007-02-10
> **cmost said:**
> Thanks Chanders, that worked!  I tried searching the threads for the answer, but, I didn't find that post you referenced as it was a bit buried and non-descriptive of the problem.  Anyway, I'm liking the new menu; I really like its flexibility and ability to customize!!!  Just a few questions (please forgive me if already asked.)

1.  How can I make the side pane containing the 'pin menu' button go away for good!  I've tried the various obvious approaches using both the 'preferences' dialog and gconf-editor but it always comes back!

2.  Is there a way to customize the 'Places' plugin to include only my favorite places (such as Computer, home, documents, music, videos, pictures, etc.)  Currently everything in Nautilus's side pane appears in the places.

3.  With the old USP (0.41-1) Beryl effects were applied to the Menu (I think Beryl considered USP to be a so called 'normal' window or dialog.)  When the menu would close, it would do so according to my 'Close 1' animation setting.  The new USP menu does not seem to obey Bery's settings.  Any way to get that back?

Much thanks and great work!!!!  I look forward to the final release!

Ok, here goes..

1. Make sure hide sidepane is checked in uspconfig/gconf, and you have no minimized plugins
2. Use the shortcuts plugin instead ;-)
3. USP is now of type DOCK. You may need to make changes in beryl accordingly or change the window type to 'Normal' in /usr/share/usp/usp2.glade

---

### Post by cmost on 2007-02-10
Hi Chanders.  Thanks for your assistance.  I did find the Shortcuts plugin after I posted, which is exactly what I was looking for.  I also adjusted my Beryl settings to accommodate the 'dock' type menu.  Worked great; now the menu fades away when closed.  The last sticking point, however (no pun intended) is the "pin menu" toggle pane.  I cannot get it to hide no matter what I try.  I've tried un-checking the "show side pane" in gconf-editor and also have tried checking "hide side pane" in the preferences dialog.  After each change, i've saved settings and reloaded plugins, to no avail.  I have no plugins docked to the side pane (at least none that I can see) so I can't imagine why it won't go away.  Is it possible my copy of USP has a corruption?  I've attached a screenshot; perhaps you can see something I can't  If you've any ideas, please let me know.  While the side pane isn't that annoying, I'm a minimalist when it comes to my menu and I would rather reclaim the screen space.  Thanks!!!  :lolflag:

---

### Post by chanders on 2007-02-10
Will check..

/offtopic Sure is cold where you're from! It's 35deg C here :-D

---

### Post by cmost on 2007-02-10
LOL!  Don't rub it in!  We're due to get another 4-6" of snow by Tuesday!  :-)

---

### Post by Malac on 2007-02-11
> **cmost said:**
> Hi Chanders.  Thanks for your assistance.  I did find the Shortcuts plugin after I posted, which is exactly what I was looking for.  I also adjusted my Beryl settings to accommodate the 'dock' type menu.  Worked great; now the menu fades away when closed.  The last sticking point, however (no pun intended) is the "pin menu" toggle pane.  I cannot get it to hide no matter what I try.  I've tried un-checking the "show side pane" in gconf-editor and also have tried checking "hide side pane" in the preferences dialog.  After each change, i've saved settings and reloaded plugins, to no avail.  I have no plugins docked to the side pane (at least none that I can see) so I can't imagine why it won't go away.  Is it possible my copy of USP has a corruption?  I've attached a screenshot; perhaps you can see something I can't  If you've any ideas, please let me know.  While the side pane isn't that annoying, I'm a minimalist when it comes to my menu and I would rather reclaim the screen space.  Thanks!!!  :lolflag:
Hi,
This was a bug with the alpha .deb file version it has been addressed in the SVN version but we have not got round to updating the .deb file yet. 
We should hopefully be ready for a . deb file Beta release of USP2 soon, as I think we are ready for a feature freeze now.
You can either wait until then or use the SVN version see this :
[http://www.ubuntuforums.org/showthread.php?t=231574](http://www.ubuntuforums.org/showthread.php?t=231574)
for info on how to checkout a copy from the SVN and also a script which updates it for you and installs it to the correct main folders.
Or you can edit /usr/bin/usp using the info at post #96 here :
[http://www.ubuntuforums.org/showthread.php?t=331364&page=10](http://www.ubuntuforums.org/showthread.php?t=331364&page=10)

Hope this helps.

---

### Post by cmost on 2007-02-11
Thanks Malac!  I'm not big on messing with SVN software (save for Beryl...too good to resist) so I'll just live with this minor glitch until the next *.deb is released.  You guys are going a great job with this panel.  I really hope to see it adopted by the Gnome project as an official Gnome app.  I know many people don't care for Novell's SLAB menu (me being one of those.)  Your menu is just right!  Do hurry with the "official" release.  Most of us can't wait!  Thanks for the help.

---

### Post by undercover90 on 2007-02-11
I have an empty window, too!

the terminal say this:

```
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 127, in showuser
    self.anim=gtk.gdk.PixbufAnimation(facepic)
gobject.GError: Datei »/home/andreas/.face« konnte nicht geöffnet werden: No such file or directory

```

undercover90

---

### Post by Malac on 2007-02-11
> **undercover90 said:**
> I have an empty window, too!

the terminal say this:

```
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 127, in showuser
    self.anim=gtk.gdk.PixbufAnimation(facepic)
gobject.GError: Datei »/home/andreas/.face« konnte nicht geöffnet werden: No such file or directory

```undercover90
Either open gconf-editor, go to /apps/usp/user and add the full path to a picture in animated_picture(it doesn't have to be animated) or [System->Preferences->Login Photo] and set one up there.

Ich hoffe, daß dies hilft du, Malac. :)

---

### Post by undercover90 on 2007-02-12
Sorry, It doesn't run without problems...

```
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
Static User Image Used
```

I hope, that these problems will be fixed.

underocver90

---

### Post by Malac on 2007-02-12
> **undercover90 said:**
> Sorry, It doesn't run without problems...

```
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
Static User Image Used
```I hope, that these problems will be fixed.

underocver90
"No recent applications" is not an error as such.
It's more like a debug message to let you know that no recent applications have been recorded yet.
Is it still not running?

---

### Post by undercover90 on 2007-02-12
The menue is still empty. I can only see "User, Appliacations, Recent and System Managment"

undercover90

sorry for my bad English...

---

### Post by Malac on 2007-02-12
> **undercover90 said:**
> The menue is still empty. I can only see "User, Appliacations, Recent and System Managment"

undercover90

sorry for my bad English...
Have you tried this. [here]("http://ubuntuforums.org/showpost.php?p=2122368&postcount=173")

---

### Post by undercover90 on 2007-02-12
Yes, of course.

I opened the application.list, the recenttapps.list and the applicationfoulder. All are empty. 

The terminal:

```
Loading plugin 'uspuser' : sucessful
Loading plugin 'system_management' : sucessful
Loading plugin 'applications' : sucessful
No recent applications
Loading plugin 'recent' : sucessful
No recent applications
Static User Image Used

```

I think, that there were no failure.

---

