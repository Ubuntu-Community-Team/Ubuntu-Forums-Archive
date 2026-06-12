---
title: "Help about postgresql 8.3 install"
date: 2008-08-19
forum: Server Platforms
---

### Post by ztx on 2008-08-19
I installed ubuntu server,and downloaded install program from postgres,but when i run install program postgresplus_x86_32.bin,I got error message bellow:
------------------------------------------------------
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
	at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:159)
	at java.awt.Window.<init>(Window.java:317)
	at java.awt.Frame.<init>(Frame.java:419)
	at java.awt.Frame.<init>(Frame.java:384)
	at javax.swing.JFrame.<init>(JFrame.java:150)
	at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
	at com.zerog.ia.installer.Main.main(DashoA8113)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.zerog.lax.LAX.launch(DashoA8113)
	at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
----------------------------------------------------------------
I have installed sun JDK 1.6 and xorg,but it can't work.

---

### Post by PerJensen on 2008-08-21
Stack Trace:
java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
at java.awt.GraphicsEnvironment.checkHeadless(Graphic sEnvironment.java:159)
at java.awt.Window.<init>(Window.java:317)

indicates it need an X DISPLAY - I *guess* you need a graphical environment and not just the X libraries.


/Per

---

