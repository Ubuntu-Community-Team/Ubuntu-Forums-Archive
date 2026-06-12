---
title: "MatLAB with Wine 1.1.32"
date: 2009-11-03
forum: Wine
---

### Post by vietbuddy614 on 2009-11-03
Hi all,

I currently have a MATLAB r2009b installation DVD and have been trying to get it to load in Ubuntu 9.10. I initially came across this site ([https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)) but the installation DVD I have does not have an 'install' file, istead it has a setup.exe . I figured I would try to run it through wine (MATLAB r2008b has a gold rating) and hopefully get something to work. However, when i run:
```
wine /media/cdrom/setup.exe
```

it extracts into my C:/windows/temp folder a temporary folder that contains a .cab and .msi file, but nothing else happens. In addition, wine stops working afterwards. Does anyone have any suggestions as to a solution to this? Thanks in advance.


-vietbuddy

---

### Post by aoanla on 2009-11-03
Not quite help with getting Matlab working, but a suggestion:

Octave is a 95% compatible open-source, linux native Matlab-clone. It's in Ubuntu Software Centre. 
If you don't specifically need Matlab itself, but just something with the same syntax, it might be worth trying Octave first.

---

### Post by vietbuddy614 on 2009-11-03
I actually saw that in my search for an answer and checked it out. Sadly I do need MATLAB specifically, Octave doesn't quite have the functionality that I need. Thanks for the suggestion though!

---

### Post by aoanla on 2009-11-04
Well, it was worth a try :D


So, let's have a look at your problem. 

What do you mean by "Wine stops working afterwards"? The wine process hangs? You can't run anything else in Wine?

It's possible, since the install is via an msi file, that you're hitting bugs with msi installs in Wine.
I notice that there's this bug
[http://bugs.winehq.org/show_bug.cgi?id=14168](http://bugs.winehq.org/show_bug.cgi?id=14168)
concerning some msi installers hanging on 100% cpu time (it's unclear if this is the msi's fault, or wine's).

Still, you could try doing:

wine start nameofmsi.msi

after making wine "work" again, since that's probably what the setup script does anyway...

---

