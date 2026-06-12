---
title: "HOWTO: Install scmpc (mpd Last.fm audiscrobbler)"
date: 2011-10-02
forum: Tutorials
---

### Post by DarkDead on 2011-10-02
scmpc is a tiny audioscrobbler for mpd that sends your listened tracks to Last.fm. For more information and download visit the website at [https://github.com/cmende/scmpc]("https://github.com/cmende/scmpc")

This post is just a note to list the libraries needed for compiling on Ubuntu. Besides build-essential you need:
```
sudo apt-get install libcurl4-openssl-dev libconfuse0 libconfuse-dev libglib2.0-dev
```

Then uncompress the source code, navigate to it's directory and do the usual:
```
./configure
make
sudo make install
```

A simple way to make scmpc run on boot is to add an entry on System->Preferences->Startup Applications.

---

