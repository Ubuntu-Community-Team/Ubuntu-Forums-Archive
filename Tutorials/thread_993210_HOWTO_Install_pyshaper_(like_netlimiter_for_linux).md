---
title: "HOWTO: Install pyshaper (like netlimiter for linux)"
date: 2008-11-25
forum: Tutorials
---

### Post by dragonfyre13 on 2008-11-25
Here's the site for pyshaper. This tutorial is going to be a quick and dirty that I will clean up later...

[http://www.freenet.org.nz/python/pyshaper/](http://www.freenet.org.nz/python/pyshaper/)

Take a look, see if it's what you're looking for. If it is, read on.

First, you need the requirements for the package you can get from the repos.

```
sudo apt-get install python-geoip python-tk tk8.5 python-pmw tcpdump
```

Now, go install the file. Grab the file from the download link, extract it, and then install it by executing this in the same directory:

```
sudo make install
```

Now the tricky part. There's a requirement not mentioned, and that's also by the same author.

[http://www.freenet.org.nz/python/ezsqlobject/](http://www.freenet.org.nz/python/ezsqlobject/)

First, you need to get it's base library. The reason we're grabbing 0.6 version is because the ezsqlobject library breaks with anything higher (they removed a feature in higher releases called DBMConnection)

```
sudo apt-get install python-setuptools
sudo easy_install SQLObject==0.6
```

This grabs easy_install, like PEAR but for python. In other words, it's a repository for python scripts and libraries specifically.

Now go and get the ezsqlobject library from above, and extract it somewhere. Then, in the directory:

```
sudo python setup.py install
```


Use this to start the daemon:
```
sudo pyshaper start
```

use this to start the gui
```
sudo pyshaper
```

I woudl very much suggest you read the man page, it has a bunch of good information.
```
man pyshaper
```

---

### Post by Inversions on 2009-03-28
Hey dragonfyre13,

Just wanted to say thanks for the great tutorial, it was very helpful!:)

-inversions

---

### Post by snek on 2009-08-06
This tutorial is not working for me under Jaunty.
Specifically the following command doesn't seem to work anymore:
sudo easy_install SQLObject==0.6

It returns an HTML page now, don't think this old version is still being shared by sf.net?

```

sudo easy_install SQLObject==0.6
Searching for SQLObject==0.6
Reading http://pypi.python.org/simple/SQLObject/
Reading http://sqlobject.org/
Reading http://sqlobject.org/devel/
Reading http://sqlobject.org
Best match: SQLObject 0.6
Downloading http://prdownloads.sourceforge.net/sqlobject/SQLObject-0.6.tar.gz?download
error: Unexpected HTML page found at http://prdownloads.sourceforge.net/sqlobject/SQLObject-0.6.tar.gz?download


```

---

### Post by burmanabhay88 on 2009-08-06
thanks for the info. I had been using Wonder Shaper (which doesn't have a GUI) and is practically featureless. Just what I needed....:D

---

### Post by snek on 2009-08-06
I found an SVN repo which still has 0.6 here:
[http://svn.colorstudy.com/SQLObject/branches/0.6/](http://svn.colorstudy.com/SQLObject/branches/0.6/)

Will try to see if I can install it manually

EDIT: One step further!
```

sudo aptitude install subversion
sudo svn co [http://svn.colorstudy.com/SQLObject/branches/0.6/](http://svn.colorstudy.com/SQLObject/branches/0.6/)
cd 0.6
sudo easy_install .
sudo python setup.py install

```But when I try 
```

sudo pyshaper start

```I still get an error:
```

/usr/local/bin/pyshaper:23: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  import sys, os, commands, re, traceback, signal, time, stat, StringIO, popen2, sha
/usr/local/bin/pyshaper:23: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sys, os, commands, re, traceback, signal, time, stat, StringIO, popen2, sha
Traceback (most recent call last):
  File "/usr/local/bin/pyshaper", line 35, in <module>
    import ezsqlobject
ImportError: No module named ezsqlobject

```EDIT2: Fixed this problem! I forgot to follow the step for ezsqlobject! d0h!
```

cd ezsqlobject-0.1.1/
sudo python setup.py install
sudo pyshaper start

``````

/usr/local/bin/pyshaper:23: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  import sys, os, commands, re, traceback, signal, time, stat, StringIO, popen2, sha
/usr/local/bin/pyshaper:23: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sys, os, commands, re, traceback, signal, time, stat, StringIO, popen2, sha
pyshaper detached into background as daemon with pid 27618
pyshaper: version 0.1.3 now running on 30 second cycle...

```

---

### Post by funkygibbon on 2009-12-06
As of Ubuntu karmic, the above instructions didn't work for me, it failed trying to run pyshaper, with the error
```
Traceback (most recent call last):
  File "/usr/local/bin/pyshaper", line 35, in <module>
    import ezsqlobject
ImportError: No module named ezsqlobject

```

Solved by editing the pyshaper.py file, replacing
 ```
import ezsqlobject
```

to:
```
import sqlobject
```

---

### Post by Cadeyrn on 2010-10-17
Works with no errors here in lucid. Thanks!

---

### Post by willskills on 2011-08-03
Little bit of an old thread - but certainly, this works just fine on 11.04, thanks for the concise and clear instructions.

---

### Post by mujahied on 2011-08-12
Thanks worked perfectly

---

### Post by love4linux on 2011-08-13
works for me as well on ubuntu 11.04..thanks

---

### Post by akajonnyg on 2011-12-17
Thanks for the tutorial.
[COLOR="DimGray"]To all you Linux gurus - please please please remember that you to were beginners with Linux once, make it absolutely as simple as possible, and remember that 90% of Linux users are still beginners (inc me). It is the only way to make people use Linux and realise just how terrible windows is!!! [/COLOR]

---

### Post by sriharid on 2012-03-18
It seems that pyshaper site (freenet.org.nz) is down for several days now. Does anyone know of a mirror site from which I can download pyshaper? All references that came up in search seem to lead back to [http://www.freenet.org.nz/python/](http://www.freenet.org.nz/python/)*pyshaper*

---

