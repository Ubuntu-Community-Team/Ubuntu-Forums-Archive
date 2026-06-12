---
title: "Has anyone got todiscgui to work on jaunty"
date: 2009-04-30
forum: Ubuntu Studio
---

### Post by serfcx on 2009-04-30
Have recently upgraded to jaunty studio and have tried both todiscgui from the repos - 0.31 - and from latest svn but the gui refuses to run. I think it might be tied into the move to python 2.6.
Has anyone had any luck with getting this working and if so , how ?

For info svn todiscgui was running fine in 8.10 but I dont want to downgrade for other reasons

---

### Post by serfcx on 2009-05-12
Just thought I would "bump" this

---

### Post by serfcx on 2009-05-21
I think maybe the project has stalled as no response in the tovid google groups either.
I hope someone picks it up and solves the display problem for the gui.:sad:

---

### Post by Boring Bloke on 2009-10-28
I've just got it to work in Karmic

I needed to add a line of code to 
/usr/lib/python2.6/lib-tk/tkMessageBox.py
(i.e. in a terminal window 
gksudo gedit /usr/lib/python2.6/lib-tk/tkMessageBox.py
or 
kdesudo kate /usr/lib/python2.6/lib-tk/tkMessageBox.py
for kubuntu users
)


(make sure that you indent the lines properly, the formatting here is messed up)

def _show(title=None, message=None, _icon=None, _type=None, **options):
    if _icon and "icon" not in options:    options["icon"] = _icon
    if _type and "type" not in options:    options["type"] = _type
    if title:   options["title"] = title
    if message: options["message"] = message
    res = Message(**options).show()
    # In some Tcl installations, Tcl converts yes/no into a boolean
    if isinstance(res, bool):
        if res: return YES
        return NO
**    res = str(res)**
    return res

---

