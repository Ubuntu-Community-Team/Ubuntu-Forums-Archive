---
title: "Help Needed On Open Source Project"
date: 2011-06-02
forum: The Cafe
---

### Post by scott-ian on 2011-06-02
I am starting to develop a program called Quick Deb that makes it easier to create Debian packages.  I cannot do it alone!  To help, email me at [email]ian@perebruin.com[/email] or join the [development team]("https://launchpad.net/%7Equick-deb-team") on Launchpad.  What do you think of my idea?
[URL="http://quickdeb.sf.net/"]
Quick Deb Homepage[/URL]

---

### Post by juancarlospaco on 2011-06-02
C++. Sorry, i didnt know C++

---

### Post by scott-ian on 2011-06-02
You can help without knowing C++.  One feature I would like the program to have is good documentation, and that doesn't require any programming knowledge!  The need may arise for some shell coding too, as I have already coded part of the program in shell.. the only part as of now.

---

### Post by scott-ian on 2011-06-03
Should I program the GUI in GTK of QT?

---

### Post by BrokenKingpin on 2011-06-03
There are already a number of projects out there for this:
[https://launchpad.net/debianpackagemaker](https://launchpad.net/debianpackagemaker) 
[https://launchpad.net/debomatic](https://launchpad.net/debomatic) 
[https://launchpad.net/debcreator](https://launchpad.net/debcreator)

Could you not just contribute to one of these, or what will quick deb offer over these?

I would recommend QT for the graphics toolkit, but I suppose more DEs use GTK, so it is a tough call.

---

### Post by scott-ian on 2011-06-03
I didn't know about these, but my idea is different.  It is not meant to make the creation if a package easy.  The main point is to organise all the features and add a GUI.  I think any feature that cannot be created in an intuitive GUI should have a link to a text editor to add it.  The first version should allow you to use all or almost all of the features available to Debian Packages, even is some involve manual editing.  My Idea would be a relativity simple program, but it would yield some advanced features.  I guess the name doesn't make sense.  Yes, it could easily create a simple package, but with experience, a more advanced one could be created.  That's the plan at least.

---

### Post by JDShu on 2011-06-03
IMO it sounds like you haven't captured the essence of the problem with debs, and why they're difficult.

---

### Post by scott-ian on 2011-06-03
The first draft image can be seen [here]("https://sourceforge.net/project/screenshots.php?group_id=552277").
The idea is basically to add a GUI to the process, but still make it fully functional.  Quick Deb was the first name I came up with for such a program.  I would change it to a clearer name, but it is too late, because I already have it set up on Sourceforage and Lauchpad.  This program is the best for those with knowledge of the Debian packaging system, but they do not like doing the terminal commands and individually editing the files.  Think of QT creator.  You could create code in Vim, and then compile it, but it adds a nice GUI to organise it all.  It is the same idea, just with Debian Packages instead of QT user interfaces.

---

### Post by Bandit on 2011-06-03
> **scott-ian said:**
> I am starting to develop a program called Quick Deb that makes it easier to create Debian packages.  I cannot do it alone!  To help, email me at [email]ian@perebruin.com[/email] or join the [development team]("https://launchpad.net/%7Equick-deb-team") on Launchpad.  What do you think of my idea?
[URL="http://quickdeb.sf.net/"]
Quick Deb Homepage[/URL]

There are a number of other programs that may help get you further alone so you dont have to start from scratch. Check out CheckInstall. It may be int he repositories. It can build debs, but it does it in a very diry way that I dont recommend. 


> **scott-ian said:**
> Should I program the GUI in GTK of QT?

GTK.. 

Reason is KDE can show GTK apts and make them look good without install a ton of dependencies. GNOME on the other hand basicly has to install half the KDE desktop to show QT apts and then they dont match your GTK theme.


BTW, dont design any GUI until you have your base code fully complete and know exactly how you want your program to work. Reason being is you will spend many man hours reworking the gui instead of the base code that counts more.

---

### Post by scott-ian on 2011-06-03
Anyone have a better name for my project?  I have concluded that a rename would be possible.

---

### Post by scott-ian on 2011-06-03
I need a programmer that knows GTK if I can use it!  I already have bookmarked a tutorial on it, so I might be able to learn.

---

### Post by Bandit on 2011-06-03
> **scott-ian said:**
> Anyone have a better name for my project?  I have concluded that a rename would be possible.

Names are not important as they lead you to believe your project is further complete then it really is. Its a mental thing that will make you lazy. :-)
Trust me a really good name will come when the project is comeplete. This is also why many corp projects use code names. So they can rename it a better name when its complete.

---

### Post by Bandit on 2011-06-03
> **scott-ian said:**
> I need a programmer that knows GTK if I can use it!  I already have bookmarked a tutorial on it, so I might be able to learn.

Use GLade.. its simple easy and quick.
Its also in the repositories.

---

### Post by scott-ian on 2011-06-04
The thing is, the name does not really fit the project, and changing it changes the URL.  That means, someone could "loose" the project!  I guess names aren't important, but they may be what helps someone decide whether or not they are interested in the project.

Oh, and thanks for the tip on Glade!

---

### Post by Bandit on 2011-06-04
> **scott-ian said:**
> The thing is, the name does not really fit the project, and changing it changes the URL.  That means, someone could "loose" the project!  I guess names aren't important, but they may be what helps someone decide whether or not they are interested in the project.

Ahh.. wouldnt worry. Something great will come up in time as you start to work on it. Just call it Project: _______________ until its complete and then you will have thought up of a great name.


> 
Oh, and thanks for the tip on Glade!
NP at all. :-)

---

### Post by scott-ian on 2011-06-04
How could zenity be used to enter the password (to sign the package) for use in debuild?  Or would a method other than zenity be better?

---

### Post by scott-ian on 2011-06-05
Anyone willing to help?

---

