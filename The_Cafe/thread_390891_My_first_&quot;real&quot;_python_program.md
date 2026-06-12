---
title: "My first &quot;real&quot; python program"
date: 2007-03-22
forum: The Cafe
---

### Post by %hMa@?b&lt;C on 2007-03-22
Here is my first python program that is not completely stolen out of the book that I got for my birthday.  It is used to calculate percent error! but it does not have significant figures, which I have no idea how to even implement.
```
#/usr/bin/python
#calculate percent error, enjoy! copyleft Jeff Crowell 2006 under GPL! :)
act = raw_input("please enter the actual, accepted value >>")
exp = raw_input("please enter the experimentally defined value >>")
subt = abs (float (act) - float (exp))
pere = subt / float (act) * 100
print "your percent error is", pere,"%"

```

---

### Post by DoctorMO on 2007-03-22
Interesting, now use glade to create gui of it :-D email me for pointers.

---

### Post by christhemonkey on 2007-03-22
Congrats!

You could modify it to something like this:
```
#/usr/bin/python
#calculate percent error, enjoy! copyleft Jeff Crowell 2006 under GPL! :)
act = raw_input("please enter the actual, accepted value >>")
exp = raw_input("please enter the experimentally defined value >>")
# Get the number of decimal places you want
sf = raw_input("please enter how many decimal places you want > >")
subt = abs (float (act) - float (exp))
pere = subt / float (act) * 100
# Use builtin round function to decide how many decimal places you want
rnd = round(pere, int(sf))
print "your percent error is", rnd,"%" 
```

---

### Post by %hMa@?b&lt;C on 2007-03-22
> **DoctorMO said:**
> Interesting, now use glade to create gui of it :-D email me for pointers.

just a question, is there a specific app to use, or is it in the python code? could you send me a tutorial? 
Thanks!

---

### Post by christhemonkey on 2007-03-22
Glade is an app that can be used to create GUIs.

You still have to do some python to sort of stitch it together but it makes creating GUIs a lot easier.

There are several howtos about, heres one i found helpful:
[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)
[http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/](http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/)
[http://www.learningpython.com/2006/09/02/extending-our-pygtk-application/](http://www.learningpython.com/2006/09/02/extending-our-pygtk-application/)

---

