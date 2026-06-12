---
title: "[SOLVED] webmin file manager java"
date: 2007-01-25
forum: Server Platforms
---

### Post by jkroto on 2007-01-25
I have a ubuntu lamp server running and have installed webmin via the command line.  I can access webmin from all other pc's locally and through ssh.  However, on my edgy desktop I cannot use file manager.  I have java installed and the sites i go to in order to test my java install show me it is working but I can't get the file manager in webmin to work (does work from my other M$ laptop and my remote M$ pc).  Any ideas why? Or what I need to configure to make file manager work from my edgy desktop?

The browers status bar states that the java applet failed.  Here is the error I get

```

Java Plug-in 1.5.0_08
Using JRE version 1.5.0_08 Java HotSpot(TM) Client VM
User home directory = /home/jkroto
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------
basic: New window ID: 0
basic: Stopping applet ...
basic: Removed progress listener: sun.plugin.util.GrayBoxPainter@b162d5
basic: Finding information ...
basic: Releasing classloader: sun.plugin.ClassLoaderInfo@150bd4d, refcount=0
basic: Caching classloader: sun.plugin.ClassLoaderInfo@150bd4d
basic: Current classloader cache size: 1
basic: Done ...
basic: Joining applet thread ...
basic: Destroying applet ...
basic: Disposing applet ...
basic: Quiting applet ...
basic: Joined applet thread ...
basic: New window ID: 2005f28
basic: Value of xembed: 1
basic: setWindow: call before applet exists:2005f28
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@150bd4d, refcount=1
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@4ac00c
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
network: Connecting https://192.168.116.16:10000/file/FileManager.class with proxy=DIRECT
security: Loading certificates from Deployment session certificate store
security: Loaded certificates from Deployment session certificate store
security: Checking if certificate is in Deployment session certificate store
security: Checking if SSL certificate is in Deployment permanent certificate store
network: Connecting https://192.168.116.16:10000/file/FileManager.class with proxy=DIRECT
security: Loading certificates from Deployment session certificate store
security: Loaded certificates from Deployment session certificate store
security: Checking if certificate is in Deployment session certificate store
security: Checking if SSL certificate is in Deployment permanent certificate store
load: class FileManager not found.
java.lang.ClassNotFoundException: FileManager
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:168)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:119)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:599)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:721)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1781)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:650)
	at sun.applet.AppletPanel.run(AppletPanel.java:324)
	at java.lang.Thread.run(Thread.java:595)
Caused by: java.io.IOException: open HTTP connection failed.
	at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:271)
	at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:44)
	at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:158)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:155)
	... 9 more
basic: Exception: java.lang.ClassNotFoundException: FileManager

```

Thanks in advance.

---

