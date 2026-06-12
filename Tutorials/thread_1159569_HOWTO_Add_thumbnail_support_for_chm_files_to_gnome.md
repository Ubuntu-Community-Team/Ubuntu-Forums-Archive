---
title: "HOWTO: Add thumbnail support for chm files to gnome"
date: 2009-05-14
forum: Tutorials
---

### Post by monraaf on 2009-05-14
For anyone out there with chm files, I wrote a script that will add thumbnail support for chm files to gnome. With this script you'll get thumbnails of your chm files in the nautilus file manager. The script uses the largest image from the homepage of the chm file to generate the thumbnail, usually this will be an image of the front cover.

First you'll need to install the dependencies of this script:

```

sudo apt-get install python-beautifulsoup python-chm imagemagick

```

The script itself:

```

#!/usr/bin/env python

import sys, os
from chm import chm
from BeautifulSoup import BeautifulSoup

class ChmThumbNailer(object):
    def __init__(self):
        self.chm = chm.CHMFile()

    def thumbnail(self, ifile, ofile, sz):

        if self.chm.LoadCHM(ifile) == 0:
            return 1

        bestname    = None
        bestsize    = 0
        base        = self.chm.home.rpartition('/')[0] + '/'
        size, data  = self.getfile(self.chm.home)

        if size > 0:
            if self.chm.home.endswith(('jpg','gif','bmp')):
                self.write(ofile, sz, data)
            else:
                soup = BeautifulSoup(data)
                imgs = soup.findAll('img')
                for img in imgs:
                    name = base + img.get("src","")
                    size, data = self.getfile(name)
                    if size > bestsize:
                        bestsize = size
                        bestname = name
                if bestname != None:
                    size, data = self.getfile(bestname)
                    if size > 0:
                        self.write(ofile, sz, data)
        self.chm.CloseCHM()

    def write(self, ofile, sz, data):
        fd = os.popen('convert - -resize %sx%s "%s"' % (sz, sz, ofile), "w")
        fd.write(data)
        fd.close()

    def getfile(self,name):
        (ret, ui) = self.chm.ResolveObject(name)
        if ret == 1:
            return (0, '')
        return self.chm.RetrieveObject(ui)

if len(sys.argv) > 3:
    chm = ChmThumbNailer()
    chm.thumbnail(sys.argv[1], sys.argv[2], sys.argv[3])

```

Name the script something like **chm-thumbnailer.py**, save it somewhere (e.g. in a bin directory in your home directory) and make it executable:

```

chmod a+x chm-thumbnailer.py

```

Next you'll have to let gnome know about this script:
(**Note:** the code below assumes you have saved the script as: /home/myname/bin/chm-thumbnailer.py **you must replace it with the actual location of the script**)

```

gconftool --type=string --set "/desktop/gnome/thumbnailers/application@x-chm/command"  "/home/myname/bin/chm-thumbnailer.py %i %o %s"
gconftool --type=bool --set "/desktop/gnome/thumbnailers/application@x-chm/enable"  "true"

```

That's all. Now just use nautilus to navigate to a folder with chm files in it and the thumbnails will be generated.

---

### Post by downg on 2009-12-05
it works great:cool:
u shine my ubuntu;)

---

### Post by Anduu on 2009-12-06
Great tip - works great :D

Not sure if it was a glitch with my system but I had to restart nautilus before it kicked in.

---

### Post by the hoplite on 2010-06-02
Perfect.. Thanks!

---

### Post by jejemon on 2010-06-02
Awesome script sir!as what they say works like a charm. Just applied it on my newly installed Ubuntu 10.04 and works in an instant. No tweaking needed to get it working right unlike other scrips out there that works depending on the type of machine that you have. I will install this on my cousin's machine and I hope I am right in saying works without the need to edit the script.

---

### Post by calibre45 on 2011-10-06
Doesn't work in 11.04. Is there any way to fix it?

---

### Post by r_mano on 2011-11-15
It does not work in gnome3 --- see my post here with some info  [http://ubuntuforums.org/showthread.php?p=11459233#post11459233](http://ubuntuforums.org/showthread.php?p=11459233#post11459233)

maybe together we can find a solution...

---

### Post by r_mano on 2011-11-25
I solved for my XFig thumbnailer: [http://ubuntuforums.org/showthread.php?t=1881360](http://ubuntuforums.org/showthread.php?t=1881360)

I am available to give hints for this one. Just contact me.

---

