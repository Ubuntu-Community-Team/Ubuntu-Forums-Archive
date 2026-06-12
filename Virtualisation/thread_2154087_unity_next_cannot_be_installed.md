---
title: "unity next cannot be installed"
date: 2013-06-13
forum: Virtualisation
---

### Post by Andrew Bastin on 2013-06-13
Hello there,

I am trying to install unity next on my pc but go unsuccessful because I cannot complete the build the make stops because the makefile cannot be found. I am using ubuntu 13.04.

Please help

Andrew Bastin

---

### Post by Cheesemill on 2013-06-13
Are you following the official instructions? They don't mention using the make command anywhere.

[http://unity.ubuntu.com/getinvolved/development/unitynext/](http://unity.ubuntu.com/getinvolved/development/unitynext/)

---

### Post by Andrew Bastin on 2013-06-14
Yeah, Of course I am following the official instructions.When the command ./build is issued it also triggers a make install command.
I tried to run the qt Project file (qmlscene) and it says:

" [COLOR=#1414be][FONT=Monospace]Starting /usr/lib/x86_64-linux-gnu/qt5/bin/qmlscene -I /home/antu/unity/unity-next/builddir/plugins -I /home/antu/unity/unity-next/builddir/tests/plugins -I /home/antu/unity/unity-next/builddir/tests/utils/modules /home/antu/unity/unity-next/Shell.qml[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///home/antu/unity/unity-next/Shell.qml:20 module "LightDM" plugin "LightDM-qml" not found[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]/usr/lib/x86_64-linux-gnu/qt5/bin/qmlscene exited with code 255[/FONT][/COLOR][COLOR=#000000][FONT=Monospace]"[/FONT][/COLOR][COLOR=#be1414][FONT=Monospace][/FONT][/COLOR]

Please help

Andrew Bastin

---

