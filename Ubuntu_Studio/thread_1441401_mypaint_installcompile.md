---
title: "mypaint install/compile"
date: 2010-03-28
forum: Ubuntu Studio
---

### Post by Lord M on 2010-03-28
I can't find a way to make mypaint run on a ubuntu studio 9.10 64bit.

I can't find a pre-build package on a repository nor compile it from source for lacks of pacakges. But yet, I am new to ubuntu, so I may not know some software source I can add to the repository list to make my installations easier with synaptic package manager.

Here's the log running

sudo scons && ./mypaint

scons: Reading SConscript files ...
Building for python2.6
swig -o mypaintlib_wrap.cpp -noproxydel -python -c++ mypaintlib.i
python generate.py
Checked brushsettings.hpp
scons: done reading SConscript files.
scons: Building targets ...
protoc --python_out=. lib/strokemap.proto
sh: protoc: not found
scons: *** [lib/strokemap_pb2.py] Error 127
scons: building terminated because of errors.

I will thank you for any help.

____edit_____

I got the right package from
[URL="http://www.getdeb.net/welcome/"]
http://www.getdeb.net/welcome/[/URL]

Just add the repository downloading a .deb from teh website and then run normally apt-get from terminal. Easy and I got mypaint

---

