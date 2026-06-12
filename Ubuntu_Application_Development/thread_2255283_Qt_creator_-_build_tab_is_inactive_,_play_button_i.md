---
title: "Qt creator - build tab is inactive , play button is inactive .How to activate them?"
date: 2014-12-03
forum: Ubuntu Application Development
---

### Post by loves_oi on 2014-12-03
Hello, I want to develop a software using Python in Qt. I installed python, qt, qt creator  ,sip, pyqt. When i open qt creator , build tab is inactive. Searching on the web, i found a solution,but it doesn't satisfied me.By using tools->external->configure->add->addcategory , i add my path of python. Now when i write some code,it can run with tools->external -> myCategory. However , build tab is inactive. bottom-left play button and other two buttons around it are inactive. I think something is missing. I want to run my code with clicking bottom-left play button, or i want to use develop tab. Why are they inactive? How can i activate them ?
Thanks in advance.

---

### Post by oldfred on 2014-12-04
I have played with qt creator for a project in python. But that was now a couple of years ago.
With python you just create the screens and save that file. 

Then I had to use the converter to make a .py file.

pyuic4 -o pyPortFolioViewUi.py -x pyPortFolioView.ui
chmod 755 pyPortFolioViewUi.py

There are some newer ways to direct use the .ui file in the python scripts, but i have not tried them.

I thought the internal code builder was for C projects which I know nothing about.

---

