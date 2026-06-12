---
title: "DISPLAY Problem"
date: 2016-03-21
forum: Virtualisation
---

### Post by adam192 on 2016-03-21
I'm running ubuntu Desktop 14.04 LTS in a virtual machine inside a Windows 7 machine.  I'm new to Linux and have to set up some things for my job.

I'm having a problem with "X" and display issues.  I got this error message:
```
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=350m; support was removed in 8.0

Start Failed: Failed to initialize graphics environment


java.awt.AWTError: Can't connect to X11 window server using '0.0' as the value of the DISPLAY variable.
	at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
	at sun.awt.X11GraphicsEnvironment.access$200(X11GraphicsEnvironment.java:65)
	at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:115)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:74)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:264)
	at java.awt.GraphicsEnvironment.createGE(GraphicsEnvironment.java:102)
	at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:81)
	at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:126)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:264)
	at java.awt.Toolkit$2.run(Toolkit.java:860)
	at java.awt.Toolkit$2.run(Toolkit.java:855)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:854)
	at java.awt.Toolkit.getEventQueue(Toolkit.java:1734)
	at java.awt.EventQueue.isDispatchThread(EventQueue.java:1041)
	at javax.swing.SwingUtilities.isEventDispatchThread(SwingUtilities.java:1361)
	at javax.swing.text.StyleContext.reclaim(StyleContext.java:454)
	at javax.swing.text.StyleContext.addAttribute(StyleContext.java:311)
	at javax.swing.text.html.StyleSheet.addAttribute(StyleSheet.java:578)
	at javax.swing.text.StyleContext$NamedStyle.addAttribute(StyleContext.java:1501)
	at javax.swing.text.StyleContext$NamedStyle.setName(StyleContext.java:1312)
	at javax.swing.text.StyleContext$NamedStyle.<init>(StyleContext.java:1259)
	at javax.swing.text.StyleContext.addStyle(StyleContext.java:107)
	at javax.swing.text.StyleContext.<init>(StyleContext.java:87)
	at javax.swing.text.html.StyleSheet.<init>(StyleSheet.java:166)
	at javax.swing.text.html.HTMLEditorKit.getStyleSheet(HTMLEditorKit.java:391)
	at com.intellij.util.ui.UIUtil.<clinit>(UIUtil.java:98)
	at com.intellij.ide.plugins.PluginManager.start(PluginManager.java:70)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:497)
	at com.intellij.ide.Bootstrap.main(Bootstrap.java:39)
	at com.intellij.idea.Main.main(Main.java:91)
```

I'm running into this because I want to run the IDE PHPStorm version 10.  It requires Java version 8.  My java is:
```
java version "1.8.0_72"
Java(TM) SE Runtime Environment (build 1.8.0_72-b15)
Java HotSpot(TM) 64-Bit Server VM (build 25.72-b15, mixed mode)
```

After I unpack the tar.gz file for PHPStorm it tells me to go into the bin folder and run:
```
./phpstorm.sh
```

This should open and run the software but instead I just get the error message.  What do people do when they encounter this kind of trouble.  What is the real problem here?  How do I find out what kind of "X" I'm running?  And what "X" should I be running?  Any help would be appreciated.

---

### Post by slickymaster on 2016-03-21
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by MAFoElffen on 2016-03-23
Tell me the details:
- What hypervisor?
- What is your VM video settings?
- You say you are changing the Ubuntu guest desktop to what?

---

