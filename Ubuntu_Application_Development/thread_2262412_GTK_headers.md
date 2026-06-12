---
title: "GTK headers"
date: 2015-01-24
forum: Ubuntu Application Development
---

### Post by Alain_Menard on 2015-01-24
[COLOR=#333333][FONT=Lucida Grande]Hi![/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I'm trying to setup my computer for software development and general programming, but I'm having a bit of trouble trying to set it up.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I have Build-Essential install and Eclipse-CDT is working fine. I can compile and run my terminal based code perfectly.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Where I'm having a bit of problem is when I try to compile some GTK example. [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Gnome is installed: [/FONT][/COLOR]
$ dpkg -s libgtk-3-0|grep '^Version'
Version: 3.10.8~8+qiana

[COLOR=#333333][FONT=Lucida Grande]The lib are also installed:[/FONT][/COLOR]
$ dpkg -l libgtk* | grep -e '^i' | grep -e 'libgtk-*[0-9]'
ii  libgtk-3-0:amd64                            3.10.8~8+qiana                                      amd64        GTK+ graphical user interface library
ii  libgtk-3-bin                                3.10.8~8+qiana                                      amd64        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                             3.10.8~8+qiana                                      all          common files for the GTK+ graphical user interface library
ii  libgtk2-perl                                2:1.249-2                                           amd64        Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0:amd64                           2.24.23-0ubuntu1.1                                  amd64        GTK+ graphical user interface library
ii  libgtk2.0-0:i386                            2.24.23-0ubuntu1.1                                  i386         GTK+ graphical user interface library
ii  libgtk2.0-bin                               2.24.23-0ubuntu1.1                                  amd64        programs for the GTK+ graphical user interface library
ii  libgtk2.0-common                            2.24.23-0ubuntu1.1                                  all          common files for the GTK+ graphical user interface library


[COLOR=#333333][FONT=Lucida Grande]But I don't seem to have the headers:[/FONT][/COLOR]
$ pkg-config --modversion gtk+
Package gtk+ was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+' found

[COLOR=#333333][FONT=Lucida Grande]and:[/FONT][/COLOR]
make all 
Building file: ../src/hello.c
Invoking: GCC C Compiler
gcc -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/hello.d" -MT"src/hello.d" -o "src/hello.o" "../src/hello.c"
../src/hello.c:11:21: fatal error: gtk/gtk.h: Aucun fichier ou dossier de ce type
 #include <gtk/gtk.h>
                     ^
compilation terminated.
make: *** [src/hello.o] Erreur 1

[COLOR=#333333][FONT=Lucida Grande]Anybody here can tell me what package I need to install to get the headers?[/FONT][/COLOR]

---

### Post by eezacque on 2015-01-29
Did you install package libgtk-3-dev?

---

### Post by steeldriver on 2015-01-29
^^^ +1

---

