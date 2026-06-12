---
title: "Experienced Python + GTK programmers?"
date: 2011-12-09
forum: The Cafe
---

### Post by jdgregson on 2011-12-09
I'm starting a project called iMobileApps. This project's output will be a program, also called 'iMobileApps' It is a GTK front-end for installing iTunes Applications to your iPhone/iPod Touch, from Linux. The problem is that I've only recently started using Python, and GTK is too complicated for me at this time. It scares me. I need somebody who has a lot (or at lease some) experience with writing GTK GUIs in Python/pygtk. Here are the requirements:
    Moderate knowledge of and experience with Python and GTK/pygtk
    A Launchpad account
    Time
    Patience (I really want to write the base logic, but I'm still learning) 
    Basic communication skills in the English language

I have already written a proof of concept in PHP and JavaScript, and you can watch a video of it here: [http://www.youtube.com/watch?v=SmSQTJpnWkc](http://www.youtube.com/watch?v=SmSQTJpnWkc)

Also, using print screen and the Gimp, I have put together a proposal of what I would like to see the finished product as, here: [http://jdgregson.com/temp/gui-prop.png](http://jdgregson.com/temp/gui-prop.png)

Here is the project's Launchpad page: [https://launchpad.net/imobileapps](https://launchpad.net/imobileapps)

Please, reply if you're interested. Also, do you know of a better place to post this?

---

### Post by ikt on 2011-12-10
Unable to help you but good luck. :)

One thing I would suggest is looking at PyQt4, as I find the whole integration across multiple platforms better.

---

### Post by thatguruguy on 2011-12-10
Have you looked at [Quickly]("http://developer.ubuntu.com/resources/tools/quickly/")?

---

### Post by Bodsda on 2011-12-10
> **jdgregson said:**
> I'm starting a project called iMobileApps. This project's output will be a program, also called 'iMobileApps' It is a GTK front-end for installing iTunes Applications to your iPhone/iPod Touch, from Linux. The problem is that I've only recently started using Python, and GTK is too complicated for me at this time. It scares me. I need somebody who has a lot (or at lease some) experience with writing GTK GUIs in Python/pygtk. Here are the requirements:
    Moderate knowledge of and experience with Python and GTK/pygtk
    A Launchpad account
    Time
    Patience (I really want to write the base logic, but I'm still learning) 
    Basic communication skills in the English language

I have already written a proof of concept in PHP and JavaScript, and you can watch a video of it here: [http://www.youtube.com/watch?v=SmSQTJpnWkc](http://www.youtube.com/watch?v=SmSQTJpnWkc)

Also, using print screen and the Gimp, I have put together a proposal of what I would like to see the finished product as, here: [http://jdgregson.com/temp/gui-prop.png](http://jdgregson.com/temp/gui-prop.png)

Here is the project's Launchpad page: [https://launchpad.net/imobileapps](https://launchpad.net/imobileapps)

Please, reply if you're interested. Also, do you know of a better place to post this?

As far as GTK Gui's go, this is pretty simple. There are dozens of people in the programming talk sub forum who would be happy to slowly help get your GUI code up to scratch. 

Looking at ideviceinstaller, whoever is hosting it also has python-idevicesync and idevicerestore. So everything is there to build your app with a few extra functionalities as well. You could also use his libgpod to allow further abilities like photos/videos, saved files etc.

Drop me a PM if you ever get this off the ground. I'd be happy to help out.

Bodsda

P.S: I don't know how you resisted the urge to call this PyTunes :) - You could have made the program icon look so cool!

---

### Post by oldfred on 2011-12-12
Ubuntu has several libraries in synaptic. Search on iphone in synaptic:
[http://packages.ubuntu.com/oneiric/utils/ideviceinstaller](http://packages.ubuntu.com/oneiric/utils/ideviceinstaller)

Use python on Mac with sqlite
[http://thejeo.blogspot.com/2011/11/sqlite-101-for-iphone-developers.html](http://thejeo.blogspot.com/2011/11/sqlite-101-for-iphone-developers.html)

You can use glade to make a gtk front end for python with the code separate from the gui code. Glade is not a lot harder than Gimp as it is drag & drop.
builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)

---

### Post by jdgregson on 2011-12-12
> **Bodsda said:**
> 
P.S: I don't know how you resisted the urge to call this PyTunes :) - You could have made the program icon look so cool!

PyTunes?!? I laughed out loud. That is an amazing idea, which I honestly didn't think of. But if I was going to name this PyTunes, it would have to be a lot more powerful than I was thinking. Like... on a higher level than Banshee.  

But thanks for the replies, guys! I'll look into those. Especially Glade. It sounds very useful.

---

### Post by oldfred on 2011-12-14
Well, I went and said using glade would be easy.:grin:

I am trying to learn python and did a glade, python app, but recently have been trying to convert to pyqt4 with the same database and logic, so I have not used pygtk for a year.

I thought I could just use glade, create your form and add a bit of python to load form easily. Because I was copying from several sources my logic was not totally correct and took a bit longer just to get something to work.

This is just the form loaded with python. Some menu items do not work, some references were just copied from my other app and may be wrong, but it now loads something similar to your gimp screen with gtk & python.

I think you can just extract to a folder, make executeable the pyApp.py program & it may work. I only have run it from geany, as I like the terminal window for errors & print debugging statements. If using Geany be sure to change to spaces from tabs in both projects and edit,preferences. The geany project file will not work unless you use same path, probably easier to create a new project with your path.

---

