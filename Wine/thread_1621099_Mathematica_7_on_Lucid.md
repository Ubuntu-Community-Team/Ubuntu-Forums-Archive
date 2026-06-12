---
title: "Mathematica 7 on Lucid"
date: 2010-11-13
forum: Wine
---

### Post by VOLKOV9 on 2010-11-13
Hey, so here's the situation:

I have a Lucid partition and a Windows XP partition, with Mathematica 7 installed successfully on the XP partition.  With most other programs, I can boot into Lucid, mount the XP partition, and run the software through Wine, no questions asked.    (I have a symbolic link at ~/.wine/drive_c/Program\ Files to the Program Files folder in my Windows partition.)  My Wine is whatever version the repos have.  However, I get the following error upon trying to open Mathematica.exe :

"System Not Configured
Mathematica could not find an important resource.  The resource should have been installed with Mathematica.
If you are attempting to run Mathematica from a file server you must purchase a network license from Wolfram Research"

Also, upon trying to open math.exe, I get:

"Unable To Locate DLL
The dynamic link library mathdll.dll (or one of its components) could not be found in the Mathematica 7 subdirectory SystemFiles\Kernel\Binaries\Windows, the main Mathematica directory, or anywhere on the search path."

(mathdll.dll is, in fact, in that very folder.)

I know Wine has some kind of dll override feature, but don't know how to use it.

I know others have gotten Mathematica to work through Wine (according to WineHQ).

Anybody know how to help me out?

Thanks in advance!

---

### Post by VOLKOV9 on 2010-11-22
*bump*

---

