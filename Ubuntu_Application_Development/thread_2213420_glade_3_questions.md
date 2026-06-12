---
title: "glade 3 questions"
date: 2014-03-26
forum: Ubuntu Application Development
---

### Post by jgw on 2014-03-26
I have decided to make a run at Glade and have some basic questions.  I hope this is the right forum to post to about this.

When I take a look at the micah carrick part 1 tutorial It refers to a tool bar editor that I don't get when I try and edit the toolbar (I did the toolbar select, pencil appeared, etc).  This is also true in the foundations of GTK+ delelopment book.  This makes me wonder about my setup.  I had two choices when installing glade. The first was glade 3.4 and the other was 3.12.  I choose the 3.12 version (assumed it was the newer version, it may have been a bad choice?).  I also note that there is a 3.16 available for manual installation.  I also note that I do have a minimal installation of gtk+2 and more of gtk+3   Hopefully glade has updated the toolbar editor to the one I have (it now has a hierarchy tab on it) but, just in case, I thought I would find out if anybody can tell me if I have set this thing up wrong.

thank you...........

---

### Post by mttolmie on 2014-06-02
Same question as above. I run python 3 in Ubuntu 14.04 Classic desktop. python3-gi binds to the GOject (which includes GTK+ ?). This combination is OK in that I can run the examples out of python-gtk3-tutorial.pdf.
I am looking for a compatible Glade. The choices are Glade, glade-gnome and glade-gtk2. I loaded the last one and it runs so-so; some errors refer to a python 2.7 environment and I do not know which gtk version to mark in the glade preferences.
Is there a better forum for this sort of question?

---

### Post by jgw on 2014-06-03
I want to wish you good luck with your problem.  There is, however, another glade forum but I forget how to get to it.  Perhaps somebody will see this and respond.  I am a c programmer and don't know much about python, played with it but that's about it.  However, if you are messing with Glade I don't think it really makes all that much different as the results are put into files that exist outside of your program and all you should need to do is to create your callbacks.  In theory its supposed to be program independent.  

Good luck!

---

### Post by michael171 on 2014-06-21
I looked at [http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html#Editing_the_Menu_or_Toolbar](http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html#Editing_the_Menu_or_Toolbar) which I think is the tutorial you are refering to and although I have not been using glade 3.16.1-0ubuntu2 from the software center, I fired it up, added a tool bar, right clicked, edit, and on the hierarchy tab along the top I can now add stuff to my toolbar with the tree view on the left as I add menus, childern ....

It seems that this is the version of glade you want glade 3.16.1-0ubuntu2 and I am using pygobject 3.12.0 with python 3.4.0 on ubuntu 14.04 trusty

I hope this helped.  Note that after adding a toolbar or menu bar, after right clicking, selecting edit, and clicking hierarchy ...your tree on the left will be empty till you populate it.  I have not done the tutorial but thank you for bringing attention to this as I was not aware of this tutorial untill you mentioned it.

---

