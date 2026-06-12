---
title: "Won't start."
date: 2007-04-25
forum: Ubuntu System Panel
---

### Post by Hooloovooloo on 2007-04-25
Ok, so i've had this problem time from time and checked the SVN too see if there was a fix, but so far no luck. So i finally registered on the forums to ask what may be wrong.
I can install it and i can choose to add USP2 to the panel, however when i click add it doesn't show up there.
Here's what i got from run-in-window:
```
Using Standard Menu
Loading plugin 'uspuser' : successful
Loading plugin 'system_management' : successful
Loading plugin 'applications' : successful
Loading plugin 'recent' : successful
Static User Image Used
Traceback (most recent call last):
  File "/usr/bin/usp", line 925, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 910, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 671, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 70, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 446, in PopulatePlugins
    self.plugins[plugin].do_plugin()
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 213, in do_plugin
    self.showuser()
  File "/usr/lib/python2.4/site-packages/usp/plugins/uspuser.py", line 168, in showuser
    datelogged = userlist[2+offset]
IndexError: list index out of range

```

---

### Post by Malac on 2007-04-26
If you want to get USP up and running without the user info plugin as this is the one that is having the problems, from your output, then run: ```
uspconfig
```from a terminal and remove the uspuser plugin from the plugins list, click Save and then Close.
Try to add USP again this should at least get it on there.

Thought I'd fixed this but seems I missed an error trap. Thanks for finding it. :)
I have posted a fix to the SVN for this. It is now at Revision 244. If you want to just update.
If it still doesn't work after that then post the output of "usp run-in-window" and "who -s" and I'll check it out.

---

### Post by Hooloovooloo on 2007-04-26
Okies... I got it working by updating, removing the plugin and adding while USP2 was running. It looks a little wierd however. First it says USER on the top, then the picture below and for some reason it says "USE" to the left of the picture. I'd post a screenshot if i wasn't so lazy.
I'll throw in a wish quickly too. I think this meny should be a replacement for the other 3 standars menys. So my with is a shortcut to the come folder, "Computer" link, network etc. Everything you can find in the standard menus should be available. :)

---

### Post by Malac on 2007-04-26
> **Hooloovooloo said:**
> Okies... I got it working by updating, removing the plugin and adding while USP2 was running. It looks a little wierd however. First it says USER on the top, then the picture below and for some reason it says "USE" to the left of the picture. I'd post a screenshot if i wasn't so lazy.
I'll throw in a wish quickly too. I think this meny should be a replacement for the other 3 standars menys. So my with is a shortcut to the come folder, "Computer" link, network etc. Everything you can find in the standard menus should be available. :)
Post the output of who and a screenie would be helpful to diagnose the problem too.

Have you tried adding places as one of the plugins this gives this:[ATTACH]30956[/ATTACH] on my system, which is close to the standard places menu. This plugin includes bookmarks too.

---

### Post by Hooloovooloo on 2007-04-27
Okies, from "who -s" i get nothing. Don't ask me why.

---

### Post by Malac on 2007-04-27
> **Hooloovooloo said:**
> Okies, from "who -s" i get nothing. Don't ask me why.
That's weird as this is usually in a standard install. I can't remember which package this comes with though.
Did you do a server install then add components?
Can't see it making any difference but try just "who"

---

### Post by Hooloovooloo on 2007-04-27
Don*t ask me why but now i get a output from both "who" and "who -s". I know i didn't type it wrong since i tried it a lot of times when i tried before... No, i used the desktop install CD.

```
hooloovoo :0           2007-04-27 18:01
hooloovoo pts/0        2007-04-27 19:20 (:0.0)

```

---

### Post by Malac on 2007-04-28
> **Hooloovooloo said:**
> Don*t ask me why but now i get a output from both "who" and "who -s". I know i didn't type it wrong since i tried it a lot of times when i tried before... No, i used the desktop install CD.

```
hooloovoo :0           2007-04-27 18:01
hooloovoo pts/0        2007-04-27 19:20 (:0.0)

```
Very Strange. :confused:
Try adding the uspuser plugin back and see if it now works, I can only assume it is something that was wrong with 'who' or a sub-system. I'll amend the code to try to catch this weird eventuality. :)

---

### Post by Hooloovooloo on 2007-05-18
Ok, i've been trying it for a while now. I added the plugin and it worked. However it stopped working a few days ago and i haven't tried it since.

---

### Post by alextud on 2007-05-19
Usp wont start and after running : usp run-in-window  it say :
*********** Keybind Failure **************
Using Standard Menu
Loading plugin 'applications' : successful
Traceback (most recent call last):
  File "/usr/bin/usp", line 925, in <module>
    menu_factory(app, None)
  File "/usr/bin/usp", line 910, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 671, in __init__
    self.mainwin = MainWindow()
  File "/usr/bin/usp", line 71, in __init__
    self.CompactButtons()
  File "/usr/bin/usp", line 583, in CompactButtons
    Image1 = icon_factory.load_image( CompactData[3], gtk.ICON_SIZE_MENU )
  File "/usr/lib/python2.4/site-packages/usp/plugins/usp_util.py", line 106, in load_image
    pixbuf = self.load_icon(icon_value, icon_size, force_size)
  File "/usr/lib/python2.4/site-packages/usp/plugins/usp_util.py", line 59, in load_icon
    assert icon_value, "No icon to load!"
AssertionError: No icon to load!

It worked before very well.
If i disable line 59 in usp_util.py it work.
I think I've got thist error because I added to compact list a shorcut created by wine after I installed a win program.


Also can you make an option in uspconfig to make application tab to look like in screenshot. :)
Thanks in advance.

---

