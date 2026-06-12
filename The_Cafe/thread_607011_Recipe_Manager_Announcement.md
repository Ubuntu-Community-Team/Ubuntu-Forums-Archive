---
title: "Recipe Manager Announcement"
date: 2007-11-08
forum: The Cafe
---

### Post by Daniel G. Taylor on 2007-11-08
Hey,

I've been using [Gourmet recipe Manager]("http://grecipe-manager.sf.net") for a while now and was somewhat unhappy with it. My main complaint is that it is complicated and has many features that I just don't need. Before anyone gets the wrong idea - I really like the program and am grateful to the developers, but I've been thinking about what I would want in a recipe management program lately and decided to try and hack something together.

I spent the last couple weeks working on my own recipe management program for GNOME in the bit of free time that I have, and now have it in a state where I would like to get some feedback from other developers and users. I am asking for people to test the program and provide feedback - what do you like, what don't you like, what doesn't work?

Before we get to that, here are some of the features:
[LIST]
[*]Simple, user friendly interface
[*]Powerful searching
[*]Recipe printing
[*]Recipe card view themes
[*]Sharing recipes over the network
[*]Viewing other's shared recipes
[/LIST]

There is a preview release available at [http://www.recipemanager.org/files/recipemanager-20071108.tar.bz2](http://www.recipemanager.org/files/recipemanager-20071108.tar.bz2) that contains a clean checkout from my svn server today. A README file is included that explains how to run it and such, but here's a quick rundown:

```
sudo apt-get install python-avahi
wget http://www.recipemanager.org/files/recipemanager-20071108.tar.bz2
tar -xvjf recipemanager-20071108.tar.bz2
cd recipemanager-20071108
./recipemanager
```

The program requires python with gtk, gnome, dbus, and avahi bindings, so for Ubuntu users this means you must install python-avahi before you can run it, everything else is already there! I'm not sure about other distributions.

This is my first time ever making GTK widgets, making my own GTKCellRenderer, using DBUS and Avahi, and my first time using XMLRPC, which I use for the recipe sharing. I have no idea if I did everything right and I'm sure there are plenty of bugs.

If anybody that is a user of Gourmet or anyone interested in testing this could download and test the program I would be grateful. Please leave feedback in this thread. Any developers that are interested in helping (there is still quite a bit to do) should let me know, I'm open to anything and am in the process of setting up public svn access.

The TODO file contains some known bugs and features yet to be implemented, so please consult it before posting replies here. Also, I know that the menu items for copy/paste don't do anything, and I know you can view your own shared recipes (this is on purpose to let others test the networking code)

---

### Post by zeltak on 2007-11-21
Hi

Nice design..looks very promising though without the ability to import it will be very hard for me to switch!

thx

Zeltak

---

### Post by Daniel G. Taylor on 2007-11-26
Thanks! I am actually working with the Gourmet developers now and am working on creating a standard for storing and sharing recipes over the network, then making my recipe manager a reference implementation of that, then finishing some features and doing a release. We have already agreed to share some code and one of the things they suggested I do is look at their import filters.

We have been talking on the Gourmet mailing list, private emails, and IRC. You can follow most of the discussion by checking the archives of the mailing list if you are interested.

I'm not sure how long it will take to finalize the sharing stuff and implement everything I want to, so I can't make any promises on an actual release date, but I'll announce any new releases here as well as on the recipemanager.org site.

---

### Post by IYY on 2007-11-26
The UI looks very good, I must say.

---

### Post by Lostincyberspace on 2007-11-26
Gui is pretty good but it lacks in a lot of places. Like measurements.

---

### Post by Daniel G. Taylor on 2007-11-26
I agree that it is lacking in measurements and cuisines and such. Right now it is basically just a short list of a few metric measurements, but eventually I want to have a nice list of the different metric and empirial measurements and let the user choose which to display in the settings.

Like I said above, I'm working with the Gourmet developers on some format and sharing standards before I update my recipe manager, but when I do I will be updating the measurements and removing the cuisine/course in favor of tags, which Gourmet will also be switching to, and changing servings to yield (which can mean servings, cups, etc). A lot of good discussion on all this is going on with the Gourmet developers on their mailing list and on IRC.

If you are interested in the sharing API I have a draft that I put up today here:
[http://www.recipemanager.org/rsp/rsp10draft.html](http://www.recipemanager.org/rsp/rsp10draft.html)

We are still working on the recipe sharing XML format, and I'd like to have a couple more meetings with at least Thomas before doing more with that.

Feel free to leave any feedback here or on the Gourmet mailing list.

Edit: What measurements would you like to see?

---

### Post by zeltak on 2007-11-27
Hi

thx for the updates! 

I would like to suggest a small request/feature. 

i have been looking in a lot of recipe managers with no sucess for a simple (yet very useful option in my opinion) way to attach a file to a recipe. 
This is useful since i am sure that like me other users have a lot of "old school" recipes that they have scanned or can scan pretty quickly. the ability to add a simple pdf/jpg would save lots of time in adding manually recipes.
i have no idea how long it would take to implement such a feature but would really love to see it if its a simple thing to add. i have zero knowledge in programing but would love to assist in any other way you need.

thx again for your great work

I cant wait to start using Recipe Manager!

Zeltak

---

### Post by booljayj on 2008-04-09
Finally!

This, my friend, is a triumph of simplicity and function. It is clean, stylish, and fast. Bravo, and good luck to you on this project!

As for measurements that I would like to see, imperial units are always good, and fluid measures would definitely be a requirement. Other than that, I can't think of much else.

Implementing a tag system is a fantastic idea, and is definitely something which will help out the program.

I noticed that all the recipes are stored as loose xml files, rather than in a database. Perhaps in the future you might want to switch to something like an sqlite3 database, to improve speed when handling large collections of recipes. Plus, sqlite is very common and well-documented.

I did try gourmet, and while I did like the program it was lacking in many areas and didn't flow very well. This, however, is my new favorite.

---

### Post by diskotek on 2008-04-09
i just had problems about measurements..from the recipes i grab around internet :(

---

### Post by zeltak on 2008-05-04
Hi

is the development on this program still alive? i been waiting for quite a while for progress. I am wiling to help if needed (though i am not a programmer..)

thx

Zeltak

---

### Post by Wiebelhaus on 2009-06-14
> **zeltak said:**
> Hi

is the development on this program still alive? i been waiting for quite a while for progress. I am wiling to help if needed (though i am not a programmer..)

thx

Zeltak

Wondering the same thing.

---

