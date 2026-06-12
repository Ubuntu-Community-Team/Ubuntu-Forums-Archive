---
title: "How can I get to see the PNGs in this page?"
date: 2008-03-23
forum: The Cafe
---

### Post by Bou on 2008-03-23
Hi guys,

I would like to make some new icons for the typing break applet. To do that I need to see the files now being used, which can be found at [http://svn.gnome.org/viewvc/gnome-control-center/trunk/typing-break/bar.png?revision=4095](http://svn.gnome.org/viewvc/gnome-control-center/trunk/typing-break/bar.png?revision=4095)

The thing is, I don't know where to click to see or save the files. Clicking the filenames seems to take me to a log, right-clicking and saving them gives me a file which seems not to be a real image, EOG tells me.

How on Earth can I see those images?

Thanks in advance for your help guys :)

---

### Post by 23meg on 2008-03-23
You can just check the files out with ```
svn co http://svn.gnome.org/viewvc/gnome-control-center/trunk/typing-break/
```

---

### Post by Bou on 2008-03-23
I get: svn: PROPFIND requirement failed in '/viewvc/gnome-control-center/trunk/typing-break'

---

### Post by Bou on 2008-03-23
svn co [http://svn.gnome.org/svn/gnome-control-center/trunk/typing-break/](http://svn.gnome.org/svn/gnome-control-center/trunk/typing-break/) worked :)

---

