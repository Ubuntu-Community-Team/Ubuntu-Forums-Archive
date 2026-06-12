---
title: "How do I run this blender ?"
date: 2009-09-02
forum: Ubuntu Studio
---

### Post by 1080p on 2009-09-02
How do I run this blender ?

[http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=888](http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=888)

when I double click blender it does not run.

---

### Post by x33a on 2009-09-02
take a look here:

[https://help.ubuntu.com/community/Blender](https://help.ubuntu.com/community/Blender)

---

### Post by stumbleUpon on 2009-09-02
> **1080p said:**
> How do I run this blender ?

[http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=888](http://www.graphicall.org/builds/builds/showbuild.php?action=show&id=888)

when I double click blender it does not run.


Install blender from the terminal by using this command

```
sudo aptitude install blender
```

then you should be able to see blender in Applications > Graphics menu

---

### Post by cotcot on 2009-09-05
No need to install. Download the tar.bz2 from the blender website; extract, go to the extracted folder and double click the blender executable.

---

### Post by dagoth_pie on 2009-09-05
If you install it through that
```
sudo aptitude install blender
```
command already suggested, it will set it up and integrate it into Ubuntu, what is likely, is there's a missing program that runs underneath blender, installing it through the repository will find anything missing and install that as well.

The other option is to go into the terminal then type
```
cd /directory/you/extracted/blender/to
chmod a+x ./blenderexecutable
./blenderexecutable
```

Replace the directory and executable file with the right names, and that will fix what is possibly the problem, if it doesn't run, it will print an error in the command line, copy and paste that here.

---

