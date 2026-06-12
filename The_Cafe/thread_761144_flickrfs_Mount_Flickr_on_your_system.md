---
title: "flickrfs: Mount Flickr on your system"
date: 2008-04-20
forum: The Cafe
---

### Post by vishzilla on 2008-04-20
I was browsing Lifehacker when I came across this. [Flickrfs]("http://manishrjain.googlepages.com/flickrfs"), amazing tool for Flickr fans

---

### Post by Polygon on 2008-04-21
wow, i must try this.

---

### Post by SuperSon!c on 2008-04-21
shoud've just went  ahead and named it flickerffs, because that's what i think everytime i see it.  pretty cool looking and i will definitely check this out.

---

### Post by takuhii on 2008-04-29
except it doesn't work, appears to be very buggy.

I originally installed it from Synaptic, but couldn't see what to do with it from there. So I found a newbie installtion guide, even that failed to get it working...

---

### Post by delerious010 on 2008-08-20
I just installed from the Repos.
To get sets working, you've got to : 

1. Add myself to the **fuse** group.
2. Modify the flickrfs module as follows : 

# vi /usr/lib/python2.5/site-packages/flickrfs/flickrfs.py
# jump to line 200
# add a line and indent a block of text "def fsinit(self):"

```

    self._mkdir("/tags")
    self._mkdir("/tags/personal")
    self._mkdir("/tags/public")

  **def fsinit(self):**
    background(timerThread, self.sets_thread,
               self.sync_sets_thread, sets_sync_int) #sync every 2 minutes

```

Now, I've noticed that Nautilus totally locks up when accessing a set for the first time. If you let it load everything ( ridiculously slow the fist time ), it'll download and cache the meta files to make things faster the next time round. 

As dumb as it may seem, I'm going to test running : 
find sets -type f -exec cat {} \; &> /dev/null
To see if it helps at all. If so, it's functionality to think of adding to the python file.

---

### Post by dekaru on 2009-01-18
Hello.

I tried installing flickrfs following several guides out there but I haven't been successful.. has anyone else had any luck ?

All I get when I run the script is a cross for mouse pointer and this as a console output:
[INDENT]
/home/dekaru/.flickrfs/flickrfs.py: 14: __author__: not found
/home/dekaru/.flickrfs/flickrfs.py: 15: __license__: not found
import: unable to grab mouse `': Resource temporarily unavailable.[/INDENT]

Any help ??

---

