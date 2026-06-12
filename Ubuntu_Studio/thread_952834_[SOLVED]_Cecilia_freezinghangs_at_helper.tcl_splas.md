---
title: "[SOLVED] Cecilia freezing/hangs at helper.tcl splash screen"
date: 2008-10-19
forum: Ubuntu Studio
---

### Post by Malac on 2008-10-19
Just installed Cecilia. 
Ran it and it hangs when it gets to helper.tcl in splash screen. The only way to get out of it is "killall wish".
I have searched here and Google but the only hit I got suggested rolling Tcl/Tk back to 8.4.1 the ones in the repos are 8.4.16. I uninstalled 8.5 versions to just leave these ones but to no avail.
I can uninstall this and try installing the 8.4.1 from source but wondered if anyone new of a better solution.

Here is the output from command line which results in the same outcome.```
malac@P700:/usr/share/cecilia$ wish cecilia-tcl
Cecilia installation located in /usr/share/cecilia (automatic)
Loading the sources on Linux!
note: creating new prefs
info: /usr/bin/csound found; verifying version
```

Fairly new to Linux Production, any further info needed let me know.
All help gratefully received.

---

### Post by Stochastic on 2008-10-20
Funny thing, I just ran into this issue myself a couple days ago - I'm sure I bumped into it previously, but this time I really wanted to use Cecilia.  The issue has been reported on launchpad here: [https://bugs.launchpad.net/debian/+source/cecilia/+bug/236251](https://bugs.launchpad.net/debian/+source/cecilia/+bug/236251) and although it has been assigned to someone in the debian camp, it looks like little visible headway is being made.  :confused:  Edit: wait, nevermind, it looks like a fix has been found and is being added upstream - though not for Intrepid anyways.  See here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=476300](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=476300) for more info on the patch.  The file itself is not directly editable, download the Cecilia source, edit the file, then install the package.  Or, you could download the ubuntu .deb file, open with archive manager, find the specified file, edit, save, then install the .deb.  I now have a working Cecilia!

---

### Post by Stochastic on 2008-10-20
Good news, after talking with a few devs, a patch has now been applied to the intrepid version of Cecilia.

---

### Post by Malac on 2008-10-22
Applying the patch worked fine thanks.
You can edit the /usr/share/cecilia/lib/prefs.tcl file after installation
line #186 from :```
if [regexp Version $l] { break }
```
to :```
if [regexp -nocase version $l] { break }
```

---

