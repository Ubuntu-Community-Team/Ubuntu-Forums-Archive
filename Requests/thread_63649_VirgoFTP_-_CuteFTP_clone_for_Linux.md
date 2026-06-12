---
title: "VirgoFTP - CuteFTP clone for Linux"
date: 2005-09-08
forum: Requests
---

### Post by ubuntufans on 2005-09-08
[http://freshmeat.net/projects/virgoftp/?branch_id=60100&release_id=205110](http://freshmeat.net/projects/virgoftp/?branch_id=60100&release_id=205110)

It's a great applications and well written

---

### Post by KingBahamut on 2005-09-08
Sounds nice, though probably not near as functional as Gftp.

---

### Post by ubuntufans on 2005-09-09
[QUOTE=KingBahamut]Sounds nice, though probably not near as functional as Gftp.[/QUOTE]
 I got it to run on my gentoo, it's actually more functional as gftp after playing with it for a while. and filter works well too

---

### Post by void_false on 2005-09-09
I'd like to see this too in repos cause gFTP crashes sometimes on my box and interface isnt perfect. For example I must expand uploading files tree to see my upload speed.

---

### Post by rwabel on 2005-09-10
strange, I get the following error message:
```
rwabel@RALPH:~/virgoFtp_1.0_linux_gtk_x86$ ./virgoFtp.english
start the VirgoFtp
10-Sep-05 3:42:16 PM edu.sysu.virgoftp.gui.FTPGUI main
INFO: load the preference
10-Sep-05 3:42:19 PM edu.sysu.virgoftp.gui.FTPGUI main
INFO: create the Contents of the Shell
Exception in thread "main" java.lang.NoClassDefFoundError: while resolving class: edu.sysu.virgoftp.gui.Utils
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at edu.sysu.virgoftp.gui.widgets.QuickLoginBar.QuickLoginBar(org.eclipse.swt.widgets.Composite) (Unknown Source)
   at edu.sysu.virgoftp.gui.FTPGUI.createShellContents() (Unknown Source)
   at edu.sysu.virgoftp.gui.FTPGUI.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: javax.sound.sampled.Clip not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./,file:lib/swt.jar,file:lib/virgoftp.jar,file:./,file:lib/xerces.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   ...7 more

```

---

### Post by bbskill on 2005-09-14
[QUOTE=rwabel]strange, I get the following error message:
```
rwabel@RALPH:~/virgoFtp_1.0_linux_gtk_x86$ ./virgoFtp.english
start the VirgoFtp
10-Sep-05 3:42:16 PM edu.sysu.virgoftp.gui.FTPGUI main
INFO: load the preference
10-Sep-05 3:42:19 PM edu.sysu.virgoftp.gui.FTPGUI main
INFO: create the Contents of the Shell
Exception in thread "main" java.lang.NoClassDefFoundError: while resolving class: edu.sysu.virgoftp.gui.Utils
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at edu.sysu.virgoftp.gui.widgets.QuickLoginBar.QuickLoginBar(org.eclipse.swt.widgets.Composite) (Unknown Source)
   at edu.sysu.virgoftp.gui.FTPGUI.createShellContents() (Unknown Source)
   at edu.sysu.virgoftp.gui.FTPGUI.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: javax.sound.sampled.Clip not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./,file:lib/swt.jar,file:lib/virgoftp.jar,file:./,file:lib/xerces.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   ...7 more

```[/QUOTE]

please print the information.
java -version

---

### Post by rwabel on 2005-09-14
[QUOTE=bbskill]please print the information.
java -version[/QUOTE]
aha, I've just seen that I've a strange java version
```
rwabel@RALPH:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Debian 4.0.1-4ubuntu6)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

I've also installed the sun version. Maybe I should remove the gij version. Does anyone else have this strange java version on the system? I'm on breezy

---

### Post by bbskill on 2005-09-15
[QUOTE=rwabel]aha, I've just seen that I've a strange java version
```
rwabel@RALPH:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Debian 4.0.1-4ubuntu6)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

I've also installed the sun version. Maybe I should remove the gij version. Does anyone else have this strange java version on the system? I'm on breezy[/QUOTE]

gij is a jvm partly implement of gcc.gnu organisation which is integrated into GCJ, and  it hasn't implemented the javax.sound.* package yet . so please replace it with sun jvm.

---

### Post by rwabel on 2005-09-15
[QUOTE=bbskill]gij is a jvm partly implement of gcc.gnu organisation which is integrated into GCJ, and it hasn't implemented the javax.sound.* package yet . so please replace it with sun jvm.[/QUOTE]
 no need to remove it :)
Check this forum [entry]("http://ubuntuforums.org/showpost.php?p=351937&postcount=2")
It's really a cool feature with the alternative java in breezy. you can switch between different java versions

and vigroftp is working now :-)

---

### Post by elvislu on 2006-01-19
[QUOTE=rwabel]no need to remove it :)
Check this forum [entry]("http://ubuntuforums.org/showpost.php?p=351937&postcount=2")
It's really a cool feature with the alternative java in breezy. you can switch between different java versions

and vigroftp is working now :-)[/QUOTE]

cool!

---

### Post by mac_hasi on 2008-06-21
```
 Originally Posted by rwabel
no need to remove it
Check this forum entry
It's really a cool feature with the alternative java in breezy. you can switch between different java versions

and vigroftp is working now 
```

It doesn't work for me. I only have one java entry. So i can't change anything. What should i do now to solve the java problem?

---

