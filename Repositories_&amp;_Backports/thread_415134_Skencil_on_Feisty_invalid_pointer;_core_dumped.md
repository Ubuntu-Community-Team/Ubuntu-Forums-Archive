---
title: "Skencil on Feisty: invalid pointer; core dumped"
date: 2007-04-20
forum: Repositories &amp; Backports
---

### Post by gurlyburlyman on 2007-04-20
I just installed Skencil using Synaptic (in Feisty) and it doesn't seem to be working. Clicking on the icon in the Applications menu does nothing, and running from the command line gives me an error:

```
*** glibc detected *** /usr/bin/python: free(): invalid pointer: 0xb7db3ed8 ***
```

followed by a backtrace and ending with ```
Aborted (core dumped)
```. Just in case the backtrace includes some useful information, I've attached it to this post. Also, if I try to run Skencil from the command line with options, I get a segmentation fault.

Any ideas? Thanks!

---

### Post by gurlyburlyman on 2007-04-21
Nevermind; It sounds like I'm running into a bug described here: [http://www.nabble.com/Wanting-to-Try-Skencil-t3390056.html]("http://www.nabble.com/Wanting-to-Try-Skencil-t3390056.html").
To summarize, it seems that the version of Skencil (0.6.17) currently in the repos doesn't play nice with Python 2.5. Bummer.

---

### Post by gustavoguedes on 2007-05-19
I'm having exactly the same problem. Does anyone know how to solve it in a simple manner?

Thanks very much!

---

### Post by fromluxembourg on 2007-06-01
Hi,

I have also the same problem, I googled a bit around on the web but I didn't found any solution :-(

As the ps import function is among the most important I use to start working with skencil/inkscape I hope that will be solved soon.

---

### Post by David Valentine on 2007-06-12
Just to keep this alive, I am having the same problem.  Apparently it is a bug that will be fixed in release 0.6.18.

---

### Post by fromluxembourg on 2007-07-04
Hi guys,

I didn't found the solution to problem (also the SVN try did not solved the problem as I got some compilation errors...:() . Finally I looked around for a simpler solution. The main reason I used to use SKENCIL was to import PS files into INKSCAPE. I played a little bit with SCRIBUS and I found that it has good PS import & SVG export functionalities and that INKSCAPE is able to import its SVG format. 

I know that does not help with SKENCIL but it is a good shortcut while we wait for the new release.

Cheers

---

### Post by simasima on 2007-07-06
SVN version of skencil works well. 

```

sudo aptitude install subversion 
sudo aptitude install python2.5-dev python2.5-imaging
mkdir -p ~/src
cd ~/src
svn checkout https://scm.wald.intevation.org/svn/skencil/skencil/branches/skencil-0.6
cd skencil-0.6
./setup.py configure
./setup.py build
sudo ./setup.py install
```

---

### Post by fromluxembourg on 2007-07-08
Dear simasima,

sorry to bother but on my ACER ASPIRE 5020 AMD 64 compilation fails also by following your instructions.

After 
[INDENT][/INDENT]./setup.py build

i get this:

[INDENT]running 'make' in Pax
gcc -pthread -fPIC -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -I/usr/include/python2.5 -I/usr/include/python2.5    -I/usr/include/tcl8.4 -I/usr/include/tcl8.4 -I/usr/X11/include -c ././paxmodule.c -o ./paxmodule.o
In file included from ././paxmodule.c:30:
././imageobject.h:9:33: error: X11/extensions/XShm.h: No such file or directory
In file included from ././paxmodule.c:30:
././imageobject.h:16: error: expected specifier-qualifier-list before ‘XShmSegmentInfo’
././imageobject.h:28: error: expected declaration specifiers or ‘...’ before ‘XShmSegmentInfo’
././paxmodule.c: In function ‘initpax’:
././paxmodule.c:929: warning: dereferencing type-punned pointer will break strict-aliasing rules
././paxmodule.c:930: warning: dereferencing type-punned pointer will break strict-aliasing rules
././paxmodule.c:931: warning: dereferencing type-punned pointer will break strict-aliasing rules
././paxmodule.c:932: warning: dereferencing type-punned pointer will break strict-aliasing rules
././paxmodule.c:933: warning: dereferencing type-punned pointer will break strict-aliasing rules
././paxmodule.c:934: warning: dereferencing type-punned pointer will break strict-aliasing rules
././paxmodule.c:935: warning: dereferencing type-punned pointer will break strict-aliasing rules
././paxmodule.c:936: warning: dereferencing type-punned pointer will break strict-aliasing rules
make: *** [paxmodule.o] Error 1
exiting because of errors[/INDENT]

but I can't figure which is the problem ... do you have an idea about it. 

Thanks in advance for any hint

---

### Post by eundas on 2007-08-03
Add:

apt-get install x11proto-xext-dev
apt-get install libxext-dev

on top of the previous instructions to compilate the SVN version. Then the errors should go away.

Cheers,

Eduardo

---

### Post by fromluxembourg on 2007-08-22
HI Eduardo,

it was my mistake! Thanks a lot, now skencil works quite well.

Once again I have to say wonderful world the open source community!

Thierry

---

