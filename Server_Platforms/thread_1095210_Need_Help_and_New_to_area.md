---
title: "Need Help and New to area"
date: 2009-03-13
forum: Server Platforms
---

### Post by phillip.byrd on 2009-03-13
I installed gnome desktop as I am very new and needed some graphical interface and a way to check my email and web pages as I worked on this.

I am trying to installed a DMS package from logicaldocs. The file is on the Desktop, took me awhile to figure out it was case sensistive but now i get this error message in the terminal.

Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so


here is the whole thing

phillip@ubuntu:~/Desktop$ java -jar logicaldoc-cross-platform-installer-4.0.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
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
	at java.awt.EventQueue.isDispatchThread(EventQueue.java:810)
	at javax.swing.SwingUtilities.isEventDispatchThread(SwingUtilities.java:1361)
	at com.denova.ui.SwingRunner.invokeAndWait(Unknown Source)
	at com.denova.JExpress.Installer.JExpressInstaller.main(Unknown Source)
phillip@ubuntu:~/Desktop$ 

thanks for any help
Phillip

---

### Post by hyper_ch on 2009-03-13
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by phillip.byrd on 2009-03-13
found the answer to my problem here, i think

[http://ubuntuforums.org/showthread.php?t=1092670&highlight=unsatisfiedLinkError](http://ubuntuforums.org/showthread.php?t=1092670&highlight=unsatisfiedLinkError)

---

