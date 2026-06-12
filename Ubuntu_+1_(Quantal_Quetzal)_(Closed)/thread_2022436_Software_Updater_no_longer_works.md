---
title: "Software Updater no longer works"
date: 2012-07-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mcellius on 2012-07-10
Sometime this morning (10 July 2012) the Software Updater stopped working on my Quantal machine.  That is, it doesn't open at all, either from the Software Up To Date menu item under the gear wheel, or from the Software Update icon in the Dash.

When it started I was running the 3.5.0-3-generic kernel, but I have since upgraded to the 3.5.0-4-generic kernel and the problem persists.  Has anyone else encountered this?  Or is it just me?

---

### Post by arpanaut on 2012-07-10
Me Too...

Apport  directed me to this bug:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1013276](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1013276)

Seems to be getting proper attention.

---

### Post by mcellius on 2012-07-10
I added myself as affected by the bug, too.  However, I never get any error message at all unless I try to run it from the CLI; I'm not quite sure I'm experiencing the exact same thing as the reported bug.

---

### Post by mc4man on 2012-07-11
> **mcellius said:**
> I added myself as affected by the bug, too.  However, I never get any error message at all unless I try to run it from the CLI; I'm not quite sure I'm experiencing the exact same thing as the reported bug.
Likely you are, the terminal error would probably match the bug

For some reason it seems that python-2.7 is being used instead of python3. (this isn't the only case.

To demo you could try this from a terminal, it should run

```
python3 /usr/bin/update-manager
```

Edit:
Considering usr/bin/python is python 2.7, if you edit /usr/bin/update-manager to 
#! /usr/bin/python3
it should work ok for now

---

### Post by scradock on 2012-07-11
> **mc4man said:**
> Likely you are, the terminal error would probably match the bug

For some reason it seems that python-2.7 is being used instead of python3. (this isn't the only case.

To demo you could try this from a terminal, it should run

```
python3 /usr/bin/update-manager
```

I tried that - it works fine.

Even more exciting, editing /usr/bin/update-manager (which is a script/text file) to change the first line [#!/usr/bin/python] to [#!/usr/bin/python3] solves the bug, so one can simply run Update manager from the launcher.
HTH

---

### Post by mcellius on 2012-07-11
Thanks guys!  I edited /usr/bin/update-manager as you suggested and it now works again!

---

### Post by balloons on 2012-07-11
YAY -- more python3 fallout. Be prepared for this all cycle! (and on the lookout!)

---

### Post by scradock on 2012-07-12
> **guitara said:**
> YAY -- more python3 fallout. Be prepared for this all cycle! (and on the lookout!)
So - so was this just an oversight - "OK, we have to move update-manager to python3, but I forgot to edit the "include python" line to read "include python3"? Or is there supposed to be a mechanism for making this happen seamlessly - "alternatives" or something like that - that didn't work? 

Any insights, anyone?

---

