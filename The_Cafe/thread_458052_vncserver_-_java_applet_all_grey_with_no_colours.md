---
title: "vncserver - java applet all grey with no colours"
date: 2007-05-29
forum: The Cafe
---

### Post by macmatt on 2007-05-29
Hi. I am running Feisty with tightvnc. I start
```
vncserver
```

and then, when I log in as:

```
http://my.ip.address:5801
```

I can login and move the mouse, but the whole java window is GREY!:(

Please - what do I need to do to amend this?. Thanks!.

---

### Post by edmondt on 2007-05-29
Yes there is, I am guessing you're using Beryl. in your terminal,

nano /usr/local/bin/java

Then paste the code:
#! /bin/bash
XLOCALELIBDIR=/usr/lib32/X11/locale/ AWT_TOOLKIT=MToolkit /usr/lib/jvm/java-6-su
n-1.6.0.00/bin/java ${*}

Hit CTRL + x, Save and Exit then:

chmod +x /usr/local/bin/java

Now you should be able to see your java application in beryl.... hope it helps.

---

### Post by donheff on 2007-06-12
I am having similar problems.  The default remote desktop works on terminal :0 but I installed vncserver so I can run this box headless and I can't get it to work - it delivers the empty grey herringbone pattern that plagues many initial VNC setups.  Ubuntu does not generate an xstartup file like vnc did in my Fedora installations.   I tried adding an xstartup file  but to no avail so far.

Any further suggestions.  I looked through the posts here but haven't found any that work for me so far.

---

