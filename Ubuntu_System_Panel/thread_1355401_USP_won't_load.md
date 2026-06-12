---
title: "USP won't load"
date: 2009-12-14
forum: Ubuntu System Panel
---

### Post by Ms_Angel_D on 2009-12-14
I just switched back to to gnome and wanted to install USP, I followed the directions but when I go to add USP to the panel I get this error:

```
The panel encountered a problem while loading "OAFIID:GNOME_USP".
```

here are my error messages from terminal.
```
angel@angel-desktop:~$ usp run-in-window
Traceback (most recent call last):
  File "/usr/bin/usp", line 33, in <module>
    from easygconf import *
  File "/usr/lib/python2.4/site-packages/usp/plugins/easygconf.py", line 3, in <module>
    from easybuttons import *
  File "/usr/lib/python2.4/site-packages/usp/plugins/easybuttons.py", line 90, in <module>
    import gnomedesktop
ImportError: No module named gnomedesktop
angel@angel-desktop:~$ 
```

Any Ideas?

Thanks in advance,
Angel

---

### Post by delfick on 2009-12-16
mine won't load either.

However I don't get an error

```

&#9484;&#9472;(iambob@iambob-desktop, 17 Dec)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9472;&#9472;&#9472;&#9488;
&#9492;&#9472;(08:12)$ usp -run-in-window
Keybinder Loaded

```

using revision 458 on Ubuntu 9.10

.....

---

### Post by Malac on 2009-12-17
> **Ms_Angel_D said:**
> I just switched back to to gnome and wanted to install USP, I followed the directions but when I go to add USP to the panel I get this error:

```
The panel encountered a problem while loading "OAFIID:GNOME_USP".
```here are my error messages from terminal.
```
angel@angel-desktop:~$ usp run-in-window
Traceback (most recent call last):
  File "/usr/bin/usp", line 33, in <module>
    from easygconf import *
  File "/usr/lib/python2.4/site-packages/usp/plugins/easygconf.py", line 3, in <module>
    from easybuttons import *
  File "/usr/lib/python2.4/site-packages/usp/plugins/easybuttons.py", line 90, in <module>
    import gnomedesktop
ImportError: No module named gnomedesktop
angel@angel-desktop:~$ 
```Any Ideas?

Thanks in advance,
Angel
```
 sudo apt-get install python-gnomedesktop
```
Should do it. IF not let me know.
> **delfick said:**
> mine won't load either.

However I don't get an error

```

&#9484;&#9472;(iambob@iambob-desktop, 17 Dec)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9472;&#9472;&#9472;&#9488;
&#9492;&#9472;(08:12)$ usp -run-in-window
Keybinder Loaded

```using revision 458 on Ubuntu 9.10

.....
Hi Delfick,
Try: ```
usp -w applications
```
If that loads try each plugin until it fails.
OR:
```
uspconfig
```
And backup files and settings and post it on here.
Try ```
killall usp
``` in the event of crash in case any instances are still in memory.

Hope this helps.

---

### Post by delfick on 2009-12-17
> **Malac said:**
> Hi Delfick,

hello :)

> Try: ```
usp -w applications
```

that gave me some helpful errors :)

turns out it was using a dodgy version of easygconf instead of the file it should have been importing.

Now if I do the following it works
```
usp -w applications computer notes
```

(except for the errors about gtk.ToolTip)

but if I do 
```
usp -run-in-window
```

it does the same no errors and nothing shows up.........

---

### Post by Ms_Angel_D on 2009-12-17
> **Malac said:**
> ```
 sudo apt-get install python-gnomedesktop
```
Should do it. IF not let me know.
Hope this helps.


Thanks, that worked perfect :D

---

### Post by Malac on 2009-12-17
> **delfick said:**
> but if I do 
```
usp -run-in-window
```
 
it does the same no errors and nothing shows up.........
Only just noticed the mistake in the line.
There is no hyphen - in front of run-in-window, so:```
usp run-in-window
```
with the hyphen it just runs an instance of usp unattached as it were.
The shorthand for run-in-window is the -w option.
i.e.```
usp -w
``` is the same as ```
usp run-in-window
```
 
I may just get round to sorting out the command line options as I've never liked the 'run-in-window' option if anything it should be '--run-in-window' following linux standards or possibly '--window'.
 
Anyway hope that's sorted. :)

---

### Post by delfick on 2009-12-17
> **Malac said:**
> Only just noticed the mistake in the line.
There is no hyphen - in front of run-in-window, so:```
usp run-in-window
```

ahhhh

that works better :)

> Anyway hope that's sorted. :)

well, it needed to be removed from the panel and reloaded before it would actually appear which I thought didn't need to happen.

nonetheless, I have a menu again :D

---

### Post by Malac on 2010-01-07
> **Ms_Angel_D said:**
> Thanks, that worked perfect :D
Sorry I took a while to reply to this. I will add python-gnomedesktop as a dependency to the next builds.

---

