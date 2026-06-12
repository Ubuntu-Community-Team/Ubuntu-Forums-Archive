---
title: "problems installing nvidia-glx-dev, libgl1-mesa-dev or libgl-dev not found?"
date: 2006-11-03
forum: Repositories &amp; Backports
---

### Post by pyros on 2006-11-03
Ok, so I want to build vegastrike from svn, Im trying to resolve the dependencies, but I keep getting this error when I try installing nvidia-glx-dev:

The following packages have unmet dependencies:
  nvidia-glx-dev: Depends: 
libgl1-mesa-dev but it is not going to be installed or
                           libgl-dev
                  Depends: libglu1-mesa-dev but it is not going to be installed or
                           libglu-dev

Trying to install libgl1-mesa-dev gives me this error:
The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.4.1-0ubuntu8) but 6.5.1+cvs20060824 is to be installed


Is this a bug in the repos? Has anyone here experienced this problem? Or even better, is anyone here able to compile vegastrike from svn on dapper?

EDIT:
Ok. so, I found it on launchpad, but am having problems installing it. am I correct that I will basically have to have to set up a seperate install just to get nvidia-glx-dev installed?

---

### Post by ScarletEmerald on 2006-11-04
Maybe you need to downgrade libgl1-mesa from the CVS version to version 6.4.1?

---

### Post by pyros on 2006-11-04
yeah, I meant to post a follow up on this... not exactly my brightest moment :) two posts down from mine I found one about *-dev package problems. the packages I needed were on launchpad, I just had to install them piecemeal. However, I would loose some programs I needed for other projects due to dependence on the newer versions. So in a fit of... something, I formated and installed edgy. I really just needed an excuse. I tried running apt-get build-dep for vegastrike and it appears to have installed everything I need.

---

