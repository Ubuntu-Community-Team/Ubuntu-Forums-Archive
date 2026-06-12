---
title: "Csound Python binding error"
date: 2010-01-07
forum: Ubuntu Studio
---

### Post by AkiraBergman on 2010-01-07
Here is what I get in Karmic ipython interface;

> In [2]: import csnd
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/home/nuri/<ipython console> in <module>()

/usr/lib/python2.6/dist-packages/csnd.py in <module>()
      5 # This file is compatible with both classic and new-style classes.

      6 
----> 7 import _csnd
      8 import new
      9 new_instancemethod = new.instancemethod

ImportError: /usr/lib/libcsnd.so.5.2: undefined symbol: csoundSetKillXYinCallback

In [3]: 


There seems to be a related bug reported on 19-05-2009;

[https://bugs.launchpad.net/ubuntu/+source/csound/+bug/378235](https://bugs.launchpad.net/ubuntu/+source/csound/+bug/378235)

There are no related errors reported here at the Ubuntu Forums. Is this because there is no error? or nobody tried the Csound-Python interface yet in Karmic?

My Karmic is 64b. I wonder if this error has something to do with that.

---

### Post by rstets on 2010-07-22
I tried in 10.04 getting the same error trying to "import csnd". Any luck figuring out how to fix that?

---

### Post by rstets on 2010-07-22
[http://bpaste.net/show/8162/]("http://bpaste.net/show/8162/")

---

### Post by AkiraBergman on 2010-07-22
I talked (some time ago) to some people at the Csound newsgroup and figured out that Csound is not supported well in Linux due to lack of followers. I think its support is weak in Windows and Mac also. 

A probable solution is to compile it for yourself. I did not try this since compiling can be difficult.

A better solution is to try something newer like CLAM, which is actively developed and has modern features. It is developed in C++, a good language to learn. Csound functions can be integrated into CLAM since Csound is also in C.

In summary, the sound design is not a mature field and requires a lot of work.

---

