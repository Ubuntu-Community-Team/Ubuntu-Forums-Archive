---
title: "Why more than one package for a single software?"
date: 2009-12-21
forum: The Cafe
---

### Post by praveesh on 2009-12-21
In windows, mostly the software installer is a single file . But it linux, most of the time, an application requires the installation of more than one file.  And there are dependancies too . What is the technical advantage of this method ? Ie more than one package for a single software

---

### Post by Tristam Green on 2009-12-21
<insert comparison to dll hell for Windows Operating Systems>

---

### Post by Puck7 on 2009-12-21
A package is made of multiple files. Many software uses the same libraries, so no need to install something twice. In windows you have this too, try watching the screen when you install Winamp, you get a bunch of .dll's. It would be the same with other software also.

In Debian/Ubuntu the installer is one file too, it's called a .deb file.

---

### Post by forrestcupp on 2009-12-21
Windows installer exe's are actually a bunch of files plus an installer program all zipped up into an exe file.

---

### Post by scotty64 on 2009-12-21
You will notice that many dependencies are so called libraries. Libraries offer certain functionalities like drawing a window on the screen or decoding an mp3 soundfile. Shared libraries (the files in the "lib" folders with .so at the end) can be used by many different programs. This makes the core packages smaller and the developer does not have to re-invent the wheel to get a certain functionality. Another advantage of splitting an application in multiple packages is that it can save diskspace. Example: You may want to install a flight simulator, but not the terrain data of the entire planet or you want the wordprocessing and spreadsheet parts of an office package, but not the database.
BTW: Although Windows installations seem to be single packages they use libraries as well (the .dll "dynamic link library" files). While Linux is able to keep several versions of the same library on the system, a Windows installer has to decide when to replace an already existing file - with often terrible consequences.

---

### Post by gnomeuser on 2009-12-21
We can get "one package installs" e.g. by using static compilation. However this introduces at least 2 problems, as every library will effectively be duplicated in every program that uses them the packages will be huge. Worse though is this situation.

A number of packages depend on a library (say for.. making the computer go ding - libding). If we compile libding into every package then provided libding gets updated to fix a security problem we now have to recompile and have users update all the packages. 

Had this been done using dynamic linking we'd update libding and provided the API/ABI didn't change all the users would only need to update libding and all the applications would be fixed.

---

### Post by forrestcupp on 2009-12-21
> **gnomeuser said:**
> 
Had this been done using dynamic linking we'd update libding and provided the API/ABI didn't change all the users would only need to update libding and all the applications would be fixed.

Which is a great reason that dll's aren't so bad.  Several installers can include the same dll, but they all install to the same folder, which means that it is only present on your computer once.  Also, it's possible to have different versions of the same library installed at the same time so that your app can use the one that it is compatible with.

Of course it's not always like that, though.  Sometimes you end up with 50 of the same dll's installed in separate local directories.

---

