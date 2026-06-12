---
title: "Adobe Photoshop CS2 Problem"
date: 2010-05-20
forum: Wine
---

### Post by refunlike on 2010-05-20
When I try and run the setup.exe with the Wine installer I get this message;

[IMG]http://i48.tinypic.com/1z3cnl5.png[/IMG]

Does anybody know what's wrong?

---

### Post by mc4man on 2010-05-20
If you're trying to install from a cd several ways - 

*This ppa I believe has removed the cautious-launcher from build
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

*In a terminal go 
```
wine /media/[COLOR="Red"]<mountpoint>[/COLOR]/[COLOR="Blue"]setup[/COLOR].exe
```

Replace <mountpoint> with actual - browse to /media after cd is inserted to see name, replace blue with actual name/spelling if different

*Create a typical fstab entry for the drive ( and cdrom0 dir. in /media

*Edit the wine.desktop launch command and remove the misguided and poorly implemented cautious-launcher command

```
gksu gedit /usr/share/applications/wine.desktop
```

change from this
Exec=cautious-launcher %f wine start /unix

to
```

```Exec=wine start /unix %f

If the .exe is a file then any of above or just right click on .exe - properties and mark as executable

---

### Post by refunlike on 2010-05-20
Thanks a lot bud. :)

---

### Post by TJRC on 2010-05-22
Thanks from me, too.  I'm installing my good old Photoshop 6.0, and this was just what I needed.

---

### Post by mc4man on 2010-05-22
> 'm installing my good old Photoshop 6.0,

You may or may not find these useful - for ps 7, but apply to others

To add a r. click on file that opens the file directly in ps, and or a drag and drop desktop/panel launcher that does the same
[http://ubuntuforums.org/showthread.php?p=9210008#post9210008](http://ubuntuforums.org/showthread.php?p=9210008#post9210008)

If you have issues with compiz and ps Alt+left mouse click actions (not sure the OP got the idea..?
[http://ubuntuforums.org/showthread.php?p=9314245#post9314245](http://ubuntuforums.org/showthread.php?p=9314245#post9314245)

---

