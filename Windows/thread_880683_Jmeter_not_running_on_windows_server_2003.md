---
title: "Jmeter not running on windows server 2003"
date: 2008-08-05
forum: Windows
---

### Post by sudhir_gupta24 on 2008-08-05
hi

I am new user of jmeter and trying to run it.when i am going to run jmeter it's giving me following error message. can any one help me.I am using jdk1.6.please give me a solution.


Exception in thread "main" java.lang.UnsupportedClassVersionError: org/apache/jmeter/NewDriver (Unsu
pported major.minor version 48.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(Unknown Source)
        at java.security.SecureClassLoader.defineClass(Unknown Source)
        at java.net.URLClassLoader.defineClass(Unknown Source)
        at java.net.URLClassLoader.access$100(Unknown Source)
        at java.net.URLClassLoader$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClassInternal(Unknown Source)


regard's
 Sudhir

---

### Post by PmDematagoda on 2008-08-05
If this is something related to Windows(from the title, it does look like it), then you may not be able to get much help here since this is a forum dedicated to providing support for Ubuntu Linux, perhaps a Windows or Java forum would be better suited for your needs?

---

### Post by drubin on 2008-08-05
To me it looks like your java version is below the one that this was compiled on. I am using 1.6.0_07 on windows, this may or maynot be the issue.

---

