---
title: "Installing pd-extended on Natty"
date: 2011-05-25
forum: Ubuntu Studio
---

### Post by leighgable on 2011-05-25
Hello Friends,

Has anyone managed to install pd-extended on Natty? I tried grabbing the pd-extended source package both from CVS and from the puredata downloads section on the site. 

I cd into the packages section and type make, but then after much building it seems to fail on GEM, returning something along the lines of:

./Pixes/videoV4L.h:43:29: fatal error: linux/videodev.h: No such file or directory

And according to this [bug report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621956") the problem is with an include statement involving the videoV4L package. 

It looks like they've put a patch up somewhere, but I have no idea what to replace, where.

Best, Leigh

---

### Post by leighgable on 2011-05-25
OK, I replaced the GEM/src/Pixes/videoV4L.h file with the one [here]("http://pd-gem.svn.sourceforge.net/viewvc/pd-gem/branches/0.92/Gem/src/Pixes/videoV4L.h?view=markup&pathrev=3937"), and it seems to be building now.

But, then it fails again when trying to build another library:

bsaylor/partconv~.c:34:19: fatal error: fftw3.h: No such file or directory
compilation terminated.

---

### Post by Pablo_F on 2011-05-25
You probably need a

sudo apt-get install libfftw3-dev

Try to get all or most dependencies needed to build puredata with:

sudo apt-get build-dep puredata

---

