---
title: "Begging, pleading, etc (PyQt4)"
date: 2006-08-25
forum: Ubuntu Backports
---

### Post by jkugler on 2006-08-25
](*,)

OK...No more meesta noice goi.  If I don't get my package, I'm going to...uh..beg and plead and ask pretty please. :-s 

I desperately want to start working on a PyQt4 project, and would rather not upgrade to Edgy just yet.  The problems I've encountered are partially detailed here:

[https://launchpad.net/products/dapper-backports/+bug/57519](https://launchpad.net/products/dapper-backports/+bug/57519)

Today I tried compiling PyQt4 from source (download from Riverbank), but it required a new sip than dapper had, so I compiled that and create a deb with checkinstall.  Well, that deb had this error:

dpkg: error processing sip4_4.4.5-1_i386.deb (--install):
 trying to overwrite `/usr/lib/python2.4/site-packages/sipconfig.py', which is also in package python2.4-sip4-qt3

So, that won't work, and thus I can't compile it myself.

I am aware that backports just got started ([http://www.ubuntuforums.org/showpost.php?p=1419222&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1419222&postcount=3)) so I know the process is going.  Considering the intricate web of dependencies I have seem to come across (sip4, python-sip4-dev, python2.4-sip4-qt3, etc) is there any chance of seeing this in backports any time soon?  Would a Brib^H^H^H^H paid support incident speed things up any?

Thanks for any hints/insite/pointers you can give.

j

---

### Post by jdong on 2006-08-25
As mentioned in the bug report, I am currently going to reject this backport request.


If you need help installing PyQt4 for your needs, I recommend you ask here on the forums and see if someone can assist you in getting it up and running.


Good luck!

---

### Post by jkugler on 2006-08-26
NOOOOOOO! Well, OK. I see your reasons. I'll see what I can do about getting PyQt4 running on my system.  As to getting an easier-to-maintain language, I thought that was why I chose Python.  The mature Qt bindings for Python was one of (the many) reasons I chose to move to Python in the first place.

At any rate, I'll see what I can do.  Thanks for taking a look at any rate.

j

---

### Post by jdong on 2006-08-26
Good luck on getting that PyQt4 working. Last week I had an equal amount of fun trying to get the latest Mono/Monodevelop running on Dapper.... :)

---

### Post by kovan on 2006-09-24
I think I managed to make a PyQt4 package for Dapper, you can find it here: [http://kovans-ogbot.blogspot.com/2006/09/python-qt-4-bindings-pyqt4-for-ubuntu.html](http://kovans-ogbot.blogspot.com/2006/09/python-qt-4-bindings-pyqt4-for-ubuntu.html)

Feedback appreciated.

---

### Post by jkugler on 2006-09-26
Yeah, I did get that far, but removing pyqt3 breaks kde-guidance, and a few other PyQt3 things, namely Eric.

---

### Post by kovan on 2006-09-26
Yeah :s. It works for me but because I did't have that package installed.

---

