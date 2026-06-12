---
title: "How to build apps using PyQt?"
date: 2013-03-15
forum: Ubuntu Dev Link Forum
---

### Post by spinderworka on 2013-03-15
Hi there!
In the beginning this topic was designed like "what am I doing wrong?" issue, but now I would like to ask you to make sure that all I'm doing is correct.
The issue is that in [Wikipedia article]("http://en.wikipedia.org/wiki/PyQt") I found the words "PyQt4 contains the following Python modules. <..> *The QtDesigner module contains classes that allow Qt Designer to be extended using PyQt*.", but QT Designer only allows to create forms using QT libraries, not PyQt. QT Creator also doesn't allow to write apps using PyQT. I've been trying to figure out how to connect PyQt with QT Cteator, and that's the result of my thoughts:

[LIST=1]
[*]Create form in QT Designer using original QT classes. 
[*]Save file as _*filename*_.ui 
[*]Open terminal and change directory to the one containing *_filename_*.ui 
[*]Execute **pyuic4 *_filename_*.ui > mainform.ui** 
[*]In our main programm file type **import mainform.ui** and create instance of our class, for example: 
[/LIST]
[IMG]http://www.ephotobay.com/image/testapp.png[/IMG]

[COLOR=#222222][FONT=Verdana]So, am I right? Perhaps there is an easier and more native way to create applications using PyQt?[/FONT][/COLOR]

---

### Post by lykwydchykyn on 2013-03-15
That's pretty much the process as I understand it; I think if you use Eric there are some tools to automate this process, but I don't care for Eric as an IDE.  Any more I just hand-code my forms (or write something to build them from a config), since I don't do anything terribly complex.

Remind me, does pyuic output python code?  You might need to redirect it to "mainform.py" to import it.

---

### Post by spinderworka on 2013-03-15
> **lykwydchykyn said:**
> You might need to redirect it to "mainform.py" to import it.

As I understand, for python no matter what file types I import.

I found this example on wikipedia, and it works well for me :)

---

### Post by Carl H on 2013-05-13
PyQt can be treated as any other Python module, so you can just code with it directly. 

I personally don't use QtCreator/Designer at all. I much prefer to code the GUI elements by hand, as this gives me a lot more understanding and control over what's going on. It also seems more natural to me.

---

### Post by oldfred on 2013-05-13
I typically have 3 tasks running, I open geany, terminal, & Qt designer.

Then I edit screens in Qt designer, save, & in terminal I have a script that is just the pyuic4 command for this projects ui file & make sure permissions are set with chmod. Then I can run it in geany and see if my changes worked the way I thought.

---

