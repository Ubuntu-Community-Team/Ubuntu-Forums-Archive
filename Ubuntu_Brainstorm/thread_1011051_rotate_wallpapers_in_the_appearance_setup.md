---
title: "rotate wallpapers in the appearance setup"
date: 2008-12-14
forum: Ubuntu Brainstorm
---

### Post by JustAboutRealJAR on 2008-12-14
I downloaded the source and I think this would be a good place to integrate this feature...

I know you can download programs/scripts to do this as well, but none are in the repos and it really isn't much code to add.

Here's a screenshot of glade:
[IMG]http://fileserver.mixtake.com/images/appearance_wallpaper_rotate.png[/IMG]

Let me know what you think!

Also I'm not well versed in C, so I'm not entirely sure how to implement the behind the scenes code to make this work... if only it was written in python :(

---

### Post by mewithafez on 2008-12-14
Oh but you can use python! [http://www.pygtk.org/](http://www.pygtk.org/)

Here's a tutorial, you probably need to install PyGTK from the repos as well: [http://www.pygtk.org/pygtk2tutorial/index.html]("http://www.pygtk.org/pygtk2tutorial/index.html")

I would say this would be best as a feature request on gnome's bugtracker but I've never done that before.

EDIT: ps this might help as well: [http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm]("http://www.pygtk.org/articles/pygtk-glade-gui/Creating_a_GUI_using_PyGTK_and_Glade.htm")

---

### Post by JustAboutRealJAR on 2008-12-17
> **mewithafez said:**
> Oh but you can use python! [http://www.pygtk.org/](http://www.pygtk.org/)


Hey thanks for the reply, I actually am quite familiar with pygtk, I meant that the existing appearance config app is written in C, but the interface was created in glade so I just added the GUI elements for my feature.

I would have to rewrite the program in python in order too add the functionality using python

---

