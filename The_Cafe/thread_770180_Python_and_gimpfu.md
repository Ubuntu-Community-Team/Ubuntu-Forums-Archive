---
title: "Python and gimpfu"
date: 2008-04-27
forum: The Cafe
---

### Post by ravindra.rajaram on 2008-04-27
I'm trying to do something with Python and the gimpfu package.
Here is the sample code.

[I]#!/usr/bin/python
import sys
try:
        sys.path.append("/usr/lib/gimp/2.0/python/")
        from gimpfu import *
        img = gimp.Image(420,300,RGB)
        gimp.Display(img)
except ImportError:
        print "Could not import gimpfu package"
[/I]


When I execute this with GIMP's "Python-fu"console, things are fine.
But, when I run the same program in a shell (after saving the code in a file)
I get the message below:

[I]LibGimpBase-ERROR **: gimp_wire_write_msg: the wire protocol has not been initialized
aborting...
Aborted (core dumped)[/I]

Any explanation for this behavior? It appears that some initializations performed by Script-Fu are missing in the stand-alone execution on the python code.
How can I make this work when I run this stand-alone?

Thanks,
RR

---

### Post by ravindra.rajaram on 2008-05-04
Did I post my query in the wrong area??
If so, can some one redirect me please??

Thanks,
RR

---

### Post by saulgoode on 2008-05-04
I don't use Python with GIMP but you might find your answers in [this gimp.org document](http://www.gimp.org/docs/python/index.html).

---

### Post by ravindra.rajaram on 2008-07-05
Been busy for sm time..thx for the response..
I'll look for more details in the doc.

Thanks,
RR

---

### Post by sivakrishna on 2008-08-02
It worked when I run this in python console within GIMP.

---

