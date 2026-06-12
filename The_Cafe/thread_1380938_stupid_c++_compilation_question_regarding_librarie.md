---
title: "stupid c++ compilation question regarding libraries"
date: 2010-01-14
forum: The Cafe
---

### Post by Xbehave on 2010-01-14
Ok so i can't really program in c++, but i was trying to track down a bug and wanted to compile a sample of a program
```
#include <QDBusInterface>
#include <QDBusMetaType>
#include <QDBusReply>
#include <QDBusMessage>

int main()
{
QDBusInterface player(QString("org.mpris.%1").arg("amarok"), "/TrackList", "org.freedesktop.MediaPlayer");
QDBusReply<int> length = player.call("GetLength");
cout << length;
return length;
}
```
(probably wont compile but might give me usefull error messages, but instead i get errors regarding the includes
```
SongsInPlaylist.cpp:1:26: error: QDBusInterface: No such file or directory
SongsInPlaylist.cpp:2:25: error: QDBusMetaType: No such file or directory
SongsInPlaylist.cpp:3:22: error: QDBusReply: No such file or directory
SongsInPlaylist.cpp:4:24: error: QDBusMessage: No such file or directory

```
I know the files are in /usr/include/qt4/QtDBus/, but don't know how to include them (adding full path just leads to other errors such as ```
In file included from /usr/include/qt4/QtDBus/QDBusInterface:1,
from SongsInPlaylist.cpp:1:
/usr/include/qt4/QtDBus/qdbusinterface.h:45:43: error: QtDBus/qdbusabstractinterface.h: No such file or directory  
```))

---

### Post by saulgoode on 2010-01-14
You need to pass the path to the header directory to your compiler. With GCC this is done by including

**-I/usr/include/qt4/QtDBus/**

on the command line. (Alternately, you could set the CPATH environment variable.)

---

### Post by MadCow108 on 2010-01-14
usually header files have .h extension which is missing in your code.
you should only omit the extensions with the c++ standard library headers

and the compiler will also need the path to search for the files.
you can provide that with the flag -I:
gcc -I/usr/include/qt

maybe you can use pkg-config (or a qt-config if that exists) to get all necessary flags to compile

---

### Post by Xbehave on 2010-01-14
Thx, i new i should have RTM i just didn't know which one tbh

> **MadCow108 said:**
> usually header files have .h extension which is missing in your code.
The includes are copied from kde, i think they are .cpp files (they have no extension) the directory has .h files too.

---

