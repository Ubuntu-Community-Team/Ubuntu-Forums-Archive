---
title: "Unable to install libglu1-mesa-dev"
date: 2006-10-04
forum: Repositories &amp; Backports
---

### Post by codemaster on 2006-10-04
I recently installed XGL and Beryl with the intention of attempting to install them (I eventually gave up although I plan on trying later on). Oddly enough, this left my compiler saying it was unable to link to -lGLu, so I went on a hunt to find out what was wrong.

I reached a point to find that libglu1-mesa-dev was not installed! I've been attempting to reinstall this so that I can achieve my OpenGL programs to link properly once more, but to my avail I only am given this error everytime I attempt to reinstall the library:

libglu1-mesa-dev: Depends: libglu1-mesa (= 6.4.1-0ubuntu8) but 6.5.1+cvs20060824 is to be installed

I have already attempted to reinstall libglu1-mesa but that also didn't work.] (*,)  Any help with this is greatly appreciated!

---

### Post by rollsrice on 2006-11-08
I realise that this reply comes very late, but I just ran into this same problem and subsequently fixed it, so I thought I might as well post it here for future reference.

What I did was, I first downloaded the libgl1-mesa deb from here:
[http://packages.ubuntu.com/dapper/libs/libgl1-mesa](http://packages.ubuntu.com/dapper/libs/libgl1-mesa)

Then,
> sudo dpkg -i --force-downgrade /the/file/you/just/downloaded

This downgrades your version of libgl1-mesa to the one that's needed.

Once that is done simply install libglu1-mesa-dev:
> sudo apt-get install libglu1-mesa-dev

I hope this helps someone.

---

### Post by glebb on 2007-01-05
Thank you! I was having similar problems with libglu1-mesa and your post solved that one as well (with a little tweaking). I guess my problems were caused by compiz and xgl that I tried out in the past.

---

### Post by beastwoo on 2007-01-09
I ran into the same problem on Edgy when trying to install freeglut3-dev, which I needed for development work with VTK.  Dependencies led to a conflict between my installed libglu1-mesa and libglu1-mesa-dev, I think because libglu1-mesa had been updated from a cvs repo for Compiz/Beryl support.  Forcing the downgrade as suggested here seemed to work.  Now I bet Beryl is broken.  :(

EDIT: Maybe Beryl wasn't the culprit....I reinstalled it, and it works fine.

---

### Post by TeKniKal on 2007-01-12
Isn't there a possibility to make the dev-package of mesa get up to date to that CVS-version? I'm experiencing exactly the same problem (and I also have Compiz/XGL/Beryl installed, but  i'd like to install KVM which needs this dev package)? Can somebody give me a good pointer on how to do this (in apt-get, synaptic, of it that's impossible, perhaps a short help on how to do this by hand, my major concern is that I don't know that much about Linux that if something goes wrong with the dependencies, my whole system will crash and make me want to reformat).

---

