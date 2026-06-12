---
title: "Need help editing my source.list file"
date: 2006-09-04
forum: Repositories &amp; Backports
---

### Post by dsarat on 2006-09-04
Hi,
I have tried to edit my source.list file using kdesu, sudo but I cannot bring up the file to edit... ](*,) 

I did reinstall kubuntu but still not able to do this. Please help.

---

### Post by Anonii on 2006-09-04
> **dsarat said:**
> Hi,
I have tried to edit my source.list file using kdesu, sudo but I cannot bring up the file to edit... ](*,) 

I did reinstall kubuntu but still not able to do this. Please help.
_sudo gedit /etc/apt/sources.list_

Then paste the error message...

---

### Post by dsarat on 2006-09-04
I'm using kubuntu. So, used kate to edit the file. This is what I get. Thanks!

sudo kate /etc/apt/source.list
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
QObject::disconnect: Unexpected null parameter
~ScimInputContextPlugin()

---

### Post by Anonii on 2006-09-04
Heh got the same error with kate, too :P

Anyway, kate sucks anyway, try:

*sudo nano /etc/apt/sources.list*

or if you want a GUI application (alltho I prefer nano) try:

*sudo kwrite /etc/apt/sources.list*

---

### Post by dsarat on 2006-09-04
Hey, used kwrite this time around... Still the same error. 
Don't have a clue what is giving me the problem. Used nano tooo it brings up blank file. Same with kwrite and kate when used with sudo they bring up the application with blank file. Have u seen this problem before ???

sudo kwrite /etc/apt/source.list
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
~ScimInputContextPlugin()

---

### Post by Anonii on 2006-09-04
Yes... Its the problem of the typo :)
You opened "source.list" instead of "sources.list"
I tried opening my list with kwrite, and I cant indeed.
So you will have to work with nano that seems to work all right.
Command line > GUI , anyway :]

---

### Post by dsarat on 2006-09-04
Feel so dumb... Now am able to open file and edit ... Thanks Anonii...

---

