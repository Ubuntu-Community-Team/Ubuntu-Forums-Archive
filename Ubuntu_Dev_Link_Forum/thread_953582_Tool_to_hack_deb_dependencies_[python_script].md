---
title: "Tool to hack deb dependencies [python script]"
date: 2008-10-20
forum: Ubuntu Dev Link Forum
---

### Post by ]FT[ on 2008-10-20
Hi guys, I've just written a little python program which pop up a text editor file in which you can modify the dependencies of a deb file, and then it pack it again (without overwrite the original one). You can use it putting it in any folder, chmod +x it, for eg:

[LIST=1]
[*]sudo mv hack-deb.py /usr/local/bin/
[*]sudo chmod +x /usr/local/bin/hack-deb.py
[*]hack-deb.py opera_9.60.2436.gcc4.qt4_i386.deb
[/LIST]
it will product the file:
[INDENT]opera_9.60.2436.gcc4.qt4_i386-hack.deb
[/INDENT].
Maybe I could design a qt interface... we'll see! :popcorn:
Ciao!
Riccardo

```

#!/usr/bin/env python
#-*- coding:utf-8 -*-

# Text editor to use (uncomment only one, if more the last one will be used):
editor = "gedit"
# editor = "kate"
# editor = "kwrite"
# editor = "mousepad"



### STOP HERE ###

import sys, os

def checkDeb(s):
    if s.find(".deb") != -1:
        try:
            f = open(s)
            f.close()
        except IOError:
            return False
        return True
    return False

if len(sys.argv) != 2 or not checkDeb(sys.argv[1]):
    print "__DEB Dependencies Hacker__ by RickDesantis"
    print "Give me the name of the existing deb file:"
    print "\t%s %s" % (sys.argv[0][sys.argv[0].rfind("/")+1:], "<file.deb>")
    exit(-1)

deb = sys.argv[1]
ftmp = "tmpdir"
hdeb = "%s-hacked.deb" % deb[0:deb.find(".deb")]

os.system("dpkg-deb -x %s %s" % (deb, ftmp))
os.system("dpkg-deb --control %s %s/DEBIAN" % (deb, ftmp))
os.system("%s %s/DEBIAN/control" % (editor, ftmp))
os.system("dpkg -b %s %s" % (ftmp, hdeb))

```

---

### Post by artfwo on 2010-08-15
Hey, thanks for the script! Found this post by googling for "hack dependencies binary deb". Helped me to install pd-extended nightly auto-build on Maverick :D

---

