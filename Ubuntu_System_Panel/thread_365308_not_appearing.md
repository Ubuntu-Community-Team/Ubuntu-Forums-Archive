---
title: "not appearing"
date: 2007-02-19
forum: Ubuntu System Panel
---

### Post by Ghitze on 2007-02-19
well I  did every thing that the howto for USP2 said.. but I end up with a applet that doesnt show up :( .. this I get when I run  ' usp run-in-window ' 

(usp:8675): libglade-WARNING **: could not find glade file '/usr/share/usp/usp2.glade'
Traceback (most recent call last):
  File "/usr/bin/usp", line 847, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 837, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 626, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 39, in __init__
    self.wTree = gtk.glade.XML( self.gladefile, "window1" )
RuntimeError: could not create GladeXML object


anyone?

---

### Post by Mateo on 2007-02-19
Is this the USP2alpha or the SVN?

---

### Post by Ghitze on 2007-02-19
sorry that I did not mention it.. it is the SVN

---

### Post by Mateo on 2007-02-19
ohh, I know what the problem is here. I originally had the same problem.  What it is, is that the script doesn't create the /usr/share/usp directory.  So do:

```
mkdir /usr/share/usp
```

then rerun the install script.  The file is missing because it tried to copy the file into a non-existent directory.  I thought they fixed this problem in the script but maybe not.

---

### Post by Ghitze on 2007-02-19
Thank you :-D  It worked ;-)

---

### Post by PsyberOneZero on 2007-02-19
> **Mateo said:**
> ohh, I know what the problem is here. I originally had the same problem.  What it is, is that the script doesn't create the /usr/share/usp directory.  So do:

```
mkdir /usr/share/usp
```

then rerun the install script.  The file is missing because it tried to copy the file into a non-existent directory.  I thought they fixed this problem in the script but maybe not.

That's my bad, I'll have the new version of the script in SVN in a few minutes.

---

