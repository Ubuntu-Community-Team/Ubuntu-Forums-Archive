---
title: "missing python modules"
date: 2009-02-17
forum: Ubuntu Studio
---

### Post by Smbrandes on 2009-02-17
While trying to install Frescobaldi a GUI for Lilypond I ran across this errror. The following are listed in the 

S@t:~/frescobaldi-0.7.5$ cmake . 
CMake Error: The following Python modules are missing:
  PyKDE4.ktexteditor
  
-- Configuring done


Anyone know a solution? Is this a Bug? 
 The following are listed in the install document
 KDE 4.1.2 or higher, esp. kdelibs, kdebase and Okular from kdegraphics
- Qt 4.4
- Python 2.4, 2.5 or 2.6
- PyQt4
- PyKDE4.

All the above required dependencies and the corresponding devs have been installed. I am baffled.

---

### Post by Stochastic on 2009-02-17
try ```
sudo apt-get install python-kde4-dev
```

---

### Post by Smbrandes on 2009-02-18
Hi Stochastic,

  I checked and that python-kde4-dev was already installed. So I removed it completely and reinstalled, but that did not alter the problem as it still claims the same missing module upon running cmake.

---

### Post by Stochastic on 2009-02-18
hmm, looks like there's some other dependencies that Frescobaldi mentions in its download page and install pages, do you have all those installed?  It looks like it needs some special KDE4 stuff...

---

### Post by Smbrandes on 2009-02-18
Alright after looking over the instructions again. I missed the bit about pate relating to kate as a plugin. I fiddled with kate as recommended. Chased down pate. Which refuses to install as it claims "configure: PyKDE not installed or not in the Python path (could not import pykdeconfig).
Read INSTALL.txt for further instructions"
A further step away or closer?

---

### Post by Smbrandes on 2009-02-18
Installed pate. no effect. Still the above missing PyKDE4.ktexteditor error. Even though I can invoke kate so it must be there somewhere.

---

### Post by Stochastic on 2009-02-18
Well I managed to get it up and running just now.

Things I needed to install were:
python-kde4-dev kdelibs5-dev  (from ubuntu repos)
lilypond-kde4 (from [http://code.google.com/p/lilykde/](http://code.google.com/p/lilykde/) )

then everything was smooth sailing, I did no such pate / kate work etc.. that looks to be in the old lilykde (for KDE 3 not 4) instructions.

edit: oh, looks like pdf preview support requires me to install okular (from the ubuntu repos)

---

### Post by Smbrandes on 2009-02-24
Stochastic,

   It has been a long week. I realized that for some odd reason I had the backports turned off from the repositories, hence the initial difficulties. But somewhere in the fight I messed something else so badly it required a reinstall. Well that was quicker than sorting out whatever it was that was broken. 
   I have tried out the Lilypond using Frescobaldi. It is nice to have an editor function that makes it easier to spot syntax errors. The results are really pleasing, but the syntax is at times somewhat oblique or at least the documentation is. 
 So thanks for the help. 

Smbrandes

---

### Post by Stochastic on 2009-02-24
I agree, that editor is kinda nice to have.  I'm glad you finally got it working, but saddened that it required a re-install (I had my suspicions that your issue might be solved easiest by a re-install).  I hope that the frescobaldi program grows its interface in the releases to come.

As for Lilypond, the best thing for a newbie to do is to open the 'one big page' html documentation, and use your browser's find feature to jump around.  You should be able to find it here: [file:///usr/share/doc/lilypond/html/Documentation/index.html](file:///usr/share/doc/lilypond/html/Documentation/index.html)

There's also Denemo, it's a GUI editor for scores that uses lilypond internally.  It can be useful for those not wanting to work directly with the lilypond code (or at least not all the time).  There are other GUI notation editors around too, but I hear Denemo is a pretty good one.

---

### Post by wbsoft on 2009-03-07
> **Smbrandes said:**
> While trying to install Frescobaldi a GUI for Lilypond I ran across this errror. The following are listed in the 

S@t:~/frescobaldi-0.7.5$ cmake . 
CMake Error: The following Python modules are missing:
  PyKDE4.ktexteditor
  
-- Configuring done


Anyone know a solution? Is this a Bug? 
...

Hi all, I'm the author of Frescobaldi :)

This is a strange error: PyKDE4 (and all other dependencies) is installed correctly, but the ktexteditor module of PyKDE4 is not contained in the version of PyKDE4 of your distribution.

The best thing I can think of is trying to upgrade sip, PyQt4 and PyKDE4 to the newest available versions.

Frescobaldi could very well be the first Python app that embeds katepart (the Kate and KWrite editor part that's part of KDE).

BTW: there are now packages for some different distributions.

---

### Post by jafrez on 2009-04-13
Hi everyone, I am a newby to this forum, very keen in installing frescobaldi on my LTS hardy heron ubuntu system.

I think that the idea of dealing directly with lilypond code lines together with a text editor is a very good idea, however, I had the same trouble as Smbrandes. 

So, I have installed the missing packages :
[I]
- Qt 4.4
- Python 2.4, 2.5 or 2.6
- PyQt4
- PyKDE4.
[/I]
and I finally reach the final error : 
[I]
The following Python modules are missing:
    PyKDE4.ktexteditor
    dbus.mainloop.qt[/I]

Sadly enough, I can not go further... The thing that surprises me is that I have sudo apt-cache searched them and this packages seem to be contained in some other packages such as libqt4 which are already installed on my computer... This does not fit with what wbsoft has said.

Do you any iade please?


THANKS FOR ANY HELP !!!

---

### Post by Smbrandes on 2009-04-30
Jafrez,

   read Stochastics response of FEb. 18th, that has all the pertinent information. 

Wbsoft,

  Nice job on the editor. A minor thing to consider change the close button is perilously close to the tab for running lilypond. I have inadvertently pressed the wrong thing a few times now. No real damage done as I had just saved in every case, but it was sort of comical the first two times before I realized what I had done. 

I upgraded to Jaunty yesterday,not suspecting that would break Frescobaldi. It now produces the following, 
~$ frescobaldi
Traceback (most recent call last):
  File "/usr/local/bin/frescobaldi", line 23, in <module>
    from PyKDE4.kdecore import (ki18n, ki18nc,
ImportError: No module named PyKDE4.kdecore

Apparently this is affecting other jaunty users I saw the same thing on a French forum, And somewhere I read the KDE stuff was still new and or experimental, seems to be affecting also printers for some reason that I don't feel like figuring out. So for the moment there is no Guile to be had. Hopefully that will be rectified soon. My adventures in lilyponding have gotten pretty enormous 30+ pages in the last single project so the editor has become quite useful.

---

