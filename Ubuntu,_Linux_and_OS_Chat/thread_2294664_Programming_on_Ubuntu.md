---
title: "Programming on Ubuntu"
date: 2015-09-12
forum: Ubuntu, Linux and OS Chat
---

### Post by brian-mccumber on 2015-09-12
I just switched from a strictly Windows development environment to an Ubuntu/Linux development environment and I have had to overcome a few obstacles and learn a few things in order to do the same things I was doing in Windows in Ubuntu. I think I might have a tenuous handle on things now, but this transition and an image that I saw surfin' teh webs inspired me to make an image that accurately depicted my struggle. 

[ATTACH=CONFIG]264373[/ATTACH]

---

### Post by grahammechanical on 2015-09-12
You cannot teach an old dog new tricks but humans are a different matter. We can still learn new things.

I have never done any programming in Windows. In fact I have never done any programming at all. Not what you would call programming. But even I know that we do not try to program using the command line. At the very least we need a text editor. Better still a specialist application and even an Integrated Development Environment (IDE) or a Software Development Kit (SDK).

[http://blog.didrocks.fr/](http://blog.didrocks.fr/)

[URL="https://developer.ubuntu.com/en/"]https://developer.ubuntu.com/en/


[/URL]

---

### Post by brian-mccumber on 2015-09-12
That was more a comic comparison of the difficulty level of those two languages, I don't use the terminal to write stuff. I was just blown away at how difficult it was for me to use bash to make a simple program. Bash looks similar to c and php but that's about the only thing it has in common with them.

I use Geany and Gedit to write programs using bash, c, python, and freeBASIC. I have found that without Visual Studio's drag and drop interface builder that I have to set up the gui manually through code using the gtk libs and this can be difficult for someone who has always had the ide perform this task for them. 

I did install the Ubuntu sdk about 4 days ago and have managed to get a simple gui to compile and run, but I haven't found where to correctly set it's height and width properties and I haven't figured out where to add code for the gui events yet, I tried adding some variables to the click handler for a button and apparently you can't put variables there. The sdk environment is cluttered, confusing, and vague and not fun to use at all. I just got frustrated and figured I would just use python, freeBASIC, or c and gtk instead. I did set the width and height properties for the gui in it's properties section but the ui still opens at an arbitrary width and height, not the one I specified in the properties. I have looked for material about how to use the Ubuntu SDK but the stuff I have read only compounded my confusion and haven't figured out how to make anything that does anything with it yet except change a label text on a button click which was the sample app that I finally got to compile.

At least the web development pipeline hasn't changed that much between the two systems. In fact switching to Ubuntu has actually made that alot easier on me. Now instead of 6 programs and a wamp server to create and deploy a website, I only need Gimp, a text editor and the file manager connected to the web host.

---

### Post by coldraven on 2015-09-13
Have a look at QT Creator. AFAIK it is free for non-commercial use. It can be installed from the Software centre.
[https://en.wikipedia.org/wiki/Qt_Creator](https://en.wikipedia.org/wiki/Qt_Creator)

---

### Post by flaymond on 2015-09-13
Hi,

Just  wanna add - 

You can use C + GTK+2 (I don't like GTK+ 3, visually slower), C++ + Qt4/Qt5 or C++ with GTKmm, Python with either Gtk2 or Gi (GTK+3), PyQt4/PyQt5 (pyqt4 available for both python v2 & v3 version), PySide (PySide available for both python v2 & v3), wxpython (only for python v2, phoenix in development), Vala (generate C code and very well integrated with GTK), seed (javascript + gtk), PHPGtk and much more. 


For Ubuntu, I suggest to take a look not just the languages it supports, but the tools, says the famous Valgrind & GDB for C, Git (I love this one for my Control Version System), bzr (you might need this to distribute .deb package easily to Launchpad + ppa), vim, make, autotools (or cmake if you want), gcc/g++, and much more.


You can create GUI programs with Bash+Zenity - [https://help.gnome.org/users/zenity/stable/](https://help.gnome.org/users/zenity/stable/)

and example of product that use Zenity - [https://help.ubuntu.com/community/mkusb/v9](https://help.ubuntu.com/community/mkusb/v9) (by sudodus and friends)

also, if you familiar with Visual Basic, why don't you take a look at Gambas - [http://gambas.sourceforge.net/en/main.html](http://gambas.sourceforge.net/en/main.html)

I never tried Gambas, but it sounds good from the user feedbacks.

---

### Post by brian-mccumber on 2015-09-13
Hey thanks for the feedback. I went ahead and uninstalled Ubuntu sdk which in turn uninstalled QT creator I don't think I want to mess with it right now, I want to get a simple pipeline going for making desktop apps with gui's using languages that I am familiar with and QT was only making things worse.

I think I am just going to work on figuring out the gtk libs using c as the language and for something that is like VB I found freeBASIC and it works for me and it can mix up c code with the basic code so I can use the c headers for gtk through freeBASIC to create gui's also, but I can write in a language is is similar to BASIC. And freeBASIC can use Screen so it's really easy to make a window and then draw on it which is fun to do. Screenres is great and easy to implement, just enter in screenres 640,480,32 and it makes a 640x480 window that cannot be resized with 32 bit colors, plus it has mouse support so I could actually create a gui just by drawing on the screen and use collision detecting to fire the window events. I have tried running numerous scripts from gtk tutorials and I found that not all of them work, some do and some don't, plus I had trouble figuring out how to make Geany compile using the gtk libs. I got that sorted out now but now I have to figure out how to add controls to the gui's and handle their events which boils down to me learning how to use the gtk libs which is proving to be a chore and a half considering Visual Studios used to handle all that for me. I have written plenty of c programs but they were always displayed in the console but I don't mind learning new things. I may go back and revisit Ubuntu sdk after I figure out how to make a gui app using c and gtk but for now I want to concentrate on learning to use the gtk libs as I will be learning another complete language when I start messing with QT.

Zenity looks promising I will definitely be checking that out. I have a script that I wrote to query my Hughesnet modem and display my  data cap information and it uses the terminal for output, pretty much the same thing as their status meter for Windows, but I have been wanting to pipe the output to some kind of gui and I think this will do the trick.

I appreciate the responses and I will be going through the links you guys gave me and I will also be trying to find some decent tutorials on c and gtk in the meantime. I have found some but like I said most don't work or won't compile and the ones that do work are so simple, like one button and a label, that I really can't learn how to set up and use the other controls in gtk from them. I did find this link - [http://www.gtk.org/documentation.php](http://www.gtk.org/documentation.php) - and I will be reading and trying the stuff there, but I am always open to suggestion.

P.S. I have been using gcc and g++ to compile the c + gtk examples that worked and I found that I can use either c or c++ for this.

---

