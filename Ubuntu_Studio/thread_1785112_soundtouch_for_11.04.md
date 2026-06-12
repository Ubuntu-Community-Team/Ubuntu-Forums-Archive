---
title: "soundtouch for 11.04"
date: 2011-06-17
forum: Ubuntu Studio
---

### Post by Flaggmann on 2011-06-17
I am unable to find a repo for ubuntu 11.04-64bit  that includes soundtouch package.
I have all the libs associated with it installed but soundtouch itself is not available in package manager.

I downloaded latest tarball and installed it; it appeared to process normally without errors, however it doesn't show up anywhere and when I attempt to install a custom build of liquidsoap (needs soundtouch as dependency) it is unable to find the soundtouch installed from the tarball..
Suggestions to remedy this problem are welcome.
Thanks

---

### Post by jejeman on 2011-06-17
You can:
1. build deb package for soundtouch, and then install it
or
2. force the install of liquidsoap

---

### Post by Flaggmann on 2011-06-18
Cannot force install of liquidsoap; it won't go past the missing soundtouch dependency.

If it was an ocaml optional format, I could just redo the build without that ocaml-specified lib file and it could work. soundtouch appears to be a lot broader than a format and no option available to build without it.

any other ideas??

---

### Post by crewkid89 on 2011-06-19
Look in /usr/bin to see if the executable is there. If it isn't then it is probably in the directory where you compiled it.  If so you will need to move it to /usr/bin and make sure the permissions are correct.

---

### Post by Flaggmann on 2011-06-19
No the file doesn't exist anywhere on the hard drive. Not in the istall folders or the bin folders.

 it would appear the build files omitted it somehow.

Tried other repos as well but none showing soundtouch...

---

