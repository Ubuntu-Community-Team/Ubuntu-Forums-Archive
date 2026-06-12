---
title: "No module named QtWebKit"
date: 2018-04-05
forum: Ubuntu Development Version
---

### Post by arapaho on 2018-04-05
I wanted to install on Ubuntu 18.04 application Anki from its developer's website 
[https://apps.ankiweb.net](https://apps.ankiweb.net)
I installed stable version Source .deb (2.0.50)  without errors but when I want to run it I get error:

```
~$ anki
Traceback (most recent call last):
File "/usr/bin/anki", line 5, in <module>
import aqt
File "/usr/share/anki/aqt/__init__.py", line 12, in <module>
from aqt.qt import *
File "/usr/share/anki/aqt/qt.py", line 22, in <module>
from PyQt4.QtWebKit import QWebPage, QWebView, QWebSettings
ImportError: No module named QtWebKit
```

In repositories there is Anki version 2.1 available but I don't want to use it because I heavily rely on add-ons that development version from Ubuntu repositories doesn't support yet. 

What can I do?

---

### Post by mc4man on 2018-04-05
Try the pre-compiled version available on website. It should run, it not suitable then you'll have to use the latest version or go back to 16.04

---

### Post by oldfred on 2018-04-05
I barely know python, but have my own program.
I am planning on not adding pyqt4 to my 18.04 and just use pyqt5, but lots of changes.

But changing from qt4 to qt5 I added this to my notes.

# [https://pythonspot.com/en/pyqt5-webkit-browser/](https://pythonspot.com/en/pyqt5-webkit-browser/)
# PyQt4&#8217;s QtWebKit module has been split into PyQt5&#8217;s QtWebKit and QtWebKitWidgets modules.

---

### Post by monkeybrain20122 on 2018-04-05
Because qtwebkit is deprecated since qt5.6 or something, now it uses qtwebengine instead. So you need to get an older version of qt5 (like compiled locally) and link your application to it like with LD_LIBRRARY_PATH. or get a newer version of your app compiled against qt5.9

---

