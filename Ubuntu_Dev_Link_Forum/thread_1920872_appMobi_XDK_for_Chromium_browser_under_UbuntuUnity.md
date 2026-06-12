---
title: "appMobi XDK for Chromium browser under Ubuntu/Unity?"
date: 2012-02-05
forum: Ubuntu Dev Link Forum
---

### Post by hardmath on 2012-02-05
This may not be closely linked to Ubuntu, but if anyone else has tried this I'd be interested in feedback.

I've got the Chromium browser (among others) installed on Ubuntu 11.4 under the Unity desktop.

I went to the Chrome App store and installed the appMobi XDK in order to experiment with HTML 5 development.

It seems the installation goes okay (as far as a browser plugin), but it asks to create a "desktop launcher".  I agree to this, but then get an error message (a lot of stuff about Java or Javascript classes, as best I can make out), although the icon appears on my desktop.

Double clicking that desktop icon makes it go through much the same process, asking (again) if I agree to create a desktop launcher icon, and resulting in an error message about numerous Java-style classes.

If someone else has tried this, I'll be happy to give the details on the error message.  But I'm guessing something about what I'm trying to do just doesn't make technical sense.

TIA, chip

---

### Post by hardmath on 2012-02-05
Looking more closely at the error messages (see below, emphasis added) it seems to be something to do with the security model:

net.sourceforge.jnlp.LaunchException: **Fatal: Launch Error: Could not launch JNLP file.**
	at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:596)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:887)
Caused by: java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:590)
	... 1 more
Caused by: java.security.AccessControlException: access denied (java.io.FilePermission /System/Library/Java read)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:393)
	at java.security.AccessController.checkPermission(AccessController.java:553)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:549)
	at net.sourceforge.jnlp.runtime.JNLPSecurityManager.checkPermission(JNLPSecurityManager.java:284)
	at java.lang.SecurityManager.checkRead(SecurityManager.java:888)
	at java.io.File.exists(File.java:748)
	at org.simplericity.macify.eawt.DefaultApplication.<init>(DefaultApplication.java:53)
	at com.appMobi.toolkit.Launcher.changeIcon(Launcher.java:108)
	at com.appMobi.toolkit.Launcher.main(Launcher.java:90)
	... 6 more
Caused by: 
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:590)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:887)
Caused by: java.security.AccessControlException: access denied (java.io.FilePermission /System/Library/Java read)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:393)
	at java.security.AccessController.checkPermission(AccessController.java:553)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:549)
	at net.sourceforge.jnlp.runtime.JNLPSecurityManager.checkPermission(JNLPSecurityManager.java:284)
	at java.lang.SecurityManager.checkRead(SecurityManager.java:888)
	at java.io.File.exists(File.java:748)
	at org.simplericity.macify.eawt.DefaultApplication.<init>(DefaultApplication.java:53)
	at com.appMobi.toolkit.Launcher.changeIcon(Launcher.java:108)
	at com.appMobi.toolkit.Launcher.main(Launcher.java:90)
	... 6 more

---

### Post by appmobiJohn on 2012-02-09
I posted directions for getting the XDK up and running on Ubuntu in the appMobi forums, [http://forums.appmobi.com/viewtopic.php?f=18&t=431](http://forums.appmobi.com/viewtopic.php?f=18&t=431)

From the errors you posted (and some googling) it seems that you have openJDK installed. The XDK will NOT run with openJDK. We require that you use Sun's Java (you can find directions on how to get this installed in the directions on our forums).

John

---

### Post by hardmath on 2012-02-09
> **appmobiJohn said:**
> I posted directions for getting the XDK up and running on Ubuntu in the appMobi forums, [http://forums.appmobi.com/viewtopic.php?f=18&t=431](http://forums.appmobi.com/viewtopic.php?f=18&t=431)

From the errors you posted (and some googling) it seems that you have openJDK installed. The XDK will NOT run with openJDK. We require that you use Sun's Java (you can find directions on how to get this installed in the directions on our forums).

John

Thanks, John!  I'll give it a try.

Chip

---

