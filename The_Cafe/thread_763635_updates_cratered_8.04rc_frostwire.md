---
title: "updates cratered 8.04rc frostwire"
date: 2008-04-23
forum: The Cafe
---

### Post by CouchMaster on 2008-04-23
I just installed new updates on the rc version of 8.04 and frostwire quit working - something about not finding user/bin/lang or something to that effect
of course I've un/reinstalled it - no go
and I'm now using limewire - 
but - anyone got any ideas on how to fix it?

---

### Post by barbedsaber on 2008-04-23
having the same problem, when you try to type frostwire into the commandline, you  get a path, and when you follow it, one of the folders is missing, dunno what to do about it tho...


```
harry@lenovo:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

harry@lenovo:~$ 

```

---

### Post by don762003 on 2008-04-23
used, sudo update-java-alternatives -s java-6-sun, and it worked for me. maybe this will help. I also had the same exact output on my terminal.

---

### Post by barbedsaber on 2008-04-23
> **don762003 said:**
> used, sudo update-java-alternatives -s java-6-sun, and it worked for me. maybe this will help. I also had the same exact output on my terminal.

you fixed it!!!!!!!!

you are singularly the coolest person alive, I thank you

---

### Post by CouchMaster on 2008-04-23
Great fix - worked for me too!

---

