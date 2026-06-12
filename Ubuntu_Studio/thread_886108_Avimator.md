---
title: "Avimator"
date: 2008-08-10
forum: Ubuntu Studio
---

### Post by trucker33377 on 2008-08-10
is there anyone who knows how to install this? i need help with it ubuntu 8.04

---

### Post by Stochastic on 2008-08-11
The basic process is: 1) download the source tarball from their website, 2) untar the file, 3) compile the software

This is not as easy for beginner linux users as I've made it out to be.  Here is a nice guide to help you along your way: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by trucker33377 on 2008-08-11
first off im told that i should use QAVIMATOR but i dont seem to understand how to get that one at there site im pointed to a revision page with a list of files.

    *  COPYING
    * Doxyfile
    * TODO
    * bin/
    * documentation/
    * examples/
    * icons/
    * libquat/
    * qavimator.pro
    * src/
    * templates/
I'm just not that good with linux. Ive made things work with tar files but that about as far as ive made it

---

### Post by Stochastic on 2008-08-11
To get qavimator you need to use a program called svn (short for subversion).  First, install svn on your computer ```
sudo apt-get install svn
```
Then you need to get the files by running svn with their directory as an input: ```
svn co https://qavimator.svn.sourceforge.net/svnroot/qavimator qavimator
```

Now you should have that file tree in a folder on your computer.  And just like the download page from qavimator explains, you simply need to execute these commands to get things up and running: ```
cd qavimator/
./compile
./bin/qavimator
```

You may run into missing dependencies along the way of those last three commands (specifically the second one), so it's possible you'll need to read some error messages (always look at the first error) and go hunting for some libraries (use 'apt-cache search {packagename}' or 'apt-file search {filename}' replacing {somethingname} with the actual name).

---

### Post by trucker33377 on 2008-08-12
thaxs i got it up and running

---

### Post by dyingsun on 2009-01-25
Hi, sorry to bump an old thread, but Im trying to install qavimator and I'm getting stuck here:


Now you should have that file tree in a folder on your computer.  And just like the download page from qavimator explains, you simply need to execute these commands to get things up and running: ```
cd qavimator/
./compile
./bin/qavimator
```


When I try the second (compile) command it tells me:

bash: ./compile: No such file or directory

Not sure which package I need (Linux newbie, in case you haven't noticed ;-)

TIA!

---

### Post by dyingsun on 2009-01-27
Nobody? :( Don't suppose its available as a deb package?
I've also tried qmake and make, with all updated dependencies in place. Qmake gives no output, make has a big error dump, as follows:
```


:~/qavimator$ qmake && make
cd libquat && make -f Makefile
make[1]: Entering directory `/home/damien/qavimator/libquat'
make[1]: Nothing to be done for `first'.
make[1]: Leaving directory `/home/damien/qavimator/libquat'
cd src && make -f Makefile
make[1]: Entering directory `/home/damien/qavimator/src'
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQAVIMATOR_DATAPATH=\\\"/usr/share/qavimator\\\" -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../libquat -I/usr/include -I/usr/share/qt3/include -o animation.o animation.cpp
<command-line>: warning: missing terminating " character
In file included from animation.cpp:27:
animation.h:25:18: error: QTimer: No such file or directory
In file included from iktree.h:26,
                 from animation.h:27,
                 from animation.cpp:27:
bvhnode.h:24:18: error: QtCore: No such file or directory
In file included from bvhnode.h:28,
                 from iktree.h:26,
                 from animation.h:27,
                 from animation.cpp:27:
rotation.h:24:19: error: QString: No such file or directory
animation.cpp:47: error: stray ‘\’ in program
animation.cpp:47: error: missing terminating " character
In file included from iktree.h:26,
                 from animation.h:27,
                 from animation.cpp:27:
bvhnode.h:84: error: ISO C++ forbids declaration of ‘QList’ with no type
bvhnode.h:84: error: expected ‘;’ before ‘<’ token
bvhnode.h:136: error: ISO C++ forbids declaration of ‘QList’ with no type
bvhnode.h:136: error: expected ‘;’ before ‘<’ token
bvhnode.h:137: error: ISO C++ forbids declaration of ‘QMap’ with no type
bvhnode.h:137: error: expected ‘;’ before ‘<’ token
bvhnode.h:140: error: ISO C++ forbids declaration of ‘QList’ with no type
bvhnode.h:140: error: expected ‘;’ before ‘<’ token
bvhnode.h:141: error: ISO C++ forbids declaration of ‘QList’ with no type
bvhnode.h:141: error: expected ‘;’ before ‘<’ token
In file included from animation.cpp:27:
animation.h:42: error: expected class-name before ‘{’ token
animation.h:43: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
animation.h:45: error: expected ‘;’ before ‘public’
animation.h:53: error: expected `;' before ‘IKPartType’
animation.h:53: error: ISO C++ forbids declaration of ‘IKPartType’ with no type
animation.h:148: error: expected `:' before ‘slots’
animation.h:149: error: expected primary-expression before ‘void’
animation.h:149: error: ISO C++ forbids declaration of ‘slots’ with no type
animation.h:149: error: expected ‘;’ before ‘void’
animation.h:157: error: expected primary-expression before ‘void’
animation.h:157: error: ISO C++ forbids declaration of ‘signals’ with no type
animation.h:157: error: expected ‘;’ before ‘void’
animation.h:191: error: ‘NUM_IK’ was not declared in this scope
animation.h:202: error: ‘IKPartType’ is not a type
animation.h:203: error: ‘IKPartType’ is not a type
animation.h:208: error: ‘QTimer’ does not name a type
In file included from animation.cpp:29:
bvh.h:76: error: ‘QStringList’ does not name a type
bvh.h:77: error: ‘QStringList’ does not name a type
animation.h:60: error: ‘typedef enum Animation::FigureType Animation::FigureType’ is private
bvh.h:83: error: within this context
bvh.h:88: error: ISO C++ forbids declaration of ‘QList’ with no type
bvh.h:88: error: expected ‘;’ before ‘<’ token
bvh.h:89: error: ISO C++ forbids declaration of ‘QList’ with no type
bvh.h:89: error: expected ‘;’ before ‘<’ token
bvh.h:93: error: ‘QStringList’ does not name a type
bvh.h:99: error: ‘QStringList’ does not name a type
animation.cpp: In constructor ‘Animation::Animation(BVH*, const QString&)’:
animation.cpp:47: error: expected primary-expression before ‘;’ token
animation.cpp:67: error: ‘IK_LHAND’ was not declared in this scope
animation.cpp:68: error: ‘IK_RHAND’ was not declared in this scope
animation.cpp:69: error: ‘IK_LFOOT’ was not declared in this scope
animation.cpp:70: error: ‘IK_RFOOT’ was not declared in this scope
animation.cpp:78: error: ‘timer’ was not declared in this scope
animation.cpp:78: error: ‘timeout’ was not declared in this scope
animation.cpp:78: error: ‘SIGNAL’ was not declared in this scope
animation.cpp:78: error: ‘SLOT’ was not declared in this scope
animation.cpp:78: error: ‘connect’ was not declared in this scope
animation.cpp: In member function ‘void Animation::loadBVH(const QString&)’:
animation.cpp:93: error: ‘const class QString’ has no member named ‘toLatin1’
animation.cpp: In member function ‘void Animation::saveBVH(const QString&)’:
animation.cpp:101: error: ‘const class QString’ has no member named ‘toLatin1’
animation.cpp: In member function ‘void Animation::setNumberOfFrames(int)’:
animation.cpp:146: error: ‘emit’ was not declared in this scope
animation.cpp:146: error: expected `;' before ‘numberOfFrames’
animation.cpp: In member function ‘void Animation::setFrame(int)’:
animation.cpp:163: error: ‘NUM_IK’ was not declared in this scope
animation.cpp:165: error: ‘ikOn’ was not declared in this scope
animation.cpp:172: error: ‘emit’ was not declared in this scope
animation.cpp:172: error: expected `;' before ‘currentFrame’
animation.cpp:173: error: expected `;' before ‘frameChanged’
animation.cpp: In member function ‘void Animation::setEaseIn(BVHNode*, int, bool)’:
animation.cpp:228: error: ‘emit’ was not declared in this scope
animation.cpp:228: error: expected `;' before ‘redrawTrack’
animation.cpp: In member function ‘void Animation::setEaseOut(BVHNode*, int, bool)’:
animation.cpp:245: error: ‘emit’ was not declared in this scope
animation.cpp:245: error: expected `;' before ‘redrawTrack’
animation.cpp: In member function ‘bool Animation::easeIn(BVHNode*, int)’:
animation.cpp:261: error: ‘const class QString’ has no member named ‘toLatin1’
animation.cpp: In member function ‘bool Animation::easeOut(BVHNode*, int)’:
animation.cpp:277: error: ‘const class QString’ has no member named ‘toLatin1’
animation.cpp: In member function ‘void Animation::applyIK(const QString&)’:
animation.cpp:331: error: ‘emit’ was not declared in this scope
animation.cpp:331: error: expected `;' before ‘redrawTrack’
animation.cpp: At global scope:
animation.cpp:336: error: variable or field ‘setIK’ declared void
animation.cpp:336: error: ‘IKPartType’ was not declared in this scope
animation.cpp:336: error: expected primary-expression before ‘bool’
make[1]: *** [animation.o] Error 1
make[1]: Leaving directory `/home/damien/qavimator/src'
make: *** [sub-src] Error 2
```

Thanks!

---

### Post by Stochastic on 2009-01-27
I should have made a clear warning in my previous post that this is not even alpha software yet, it's not really ready for newbies to use.  The SVN checkout looks at the most recent development snapshot, and as such, things are bound to break, change, improve, fail, and otherwise be unstable.  I'd use a different app until this one makes a stable release, or until you're more comfortable with reading through source code.

---

### Post by dyingsun on 2009-01-27
Ok, will have a look at something else :)

Thanks for your reply!

---

### Post by wolfear on 2009-01-29
Thought I'd throw this is out there. I have qavimator up and running using this thread from the qavimator forums:
[http://forum.qavimator.org/viewtopic.php?t=820]("http://forum.qavimator.org/viewtopic.php?t=820")
So far, the only issue, and it sort of makes it unusable until I find the fix, is the window won't resize verticly, so can't reach the rather important buttons along the bottm edge.
Still looking for the solution.

---

