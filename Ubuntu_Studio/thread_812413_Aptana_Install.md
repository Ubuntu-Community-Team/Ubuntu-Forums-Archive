---
title: "Aptana Install"
date: 2008-05-29
forum: Ubuntu Studio
---

### Post by willworkforart on 2008-05-29
I've been struggling with this for several days now and have gone through old posts with a fine toothed comb, but can't figure this out. Help.

I downloaded and unzipped the standalone Aptana, when I go to launch it, it gives me an error and points me to this log file. I tried a couple things, but still no luck. Thanks for the help!


```
!SESSION 2008-05-29 21:48:38.528 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.osgi 4 0 2008-05-29 21:48:41.566
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: /home/wwfa/aptana/configuration/org.eclipse.osgi/bundles/109/1/.cp/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
	at com.aptana.ide.rcp.Application.run(Application.java:43)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2008-05-29 21:48:41.605
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-29 21:48:41.605
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-29 21:48:41.606
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2008-05-29 21:48:41.606
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-05-29 21:48:41.606
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar [19] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-05-29 21:48:41.606
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.
```

---

### Post by prismatic7 on 2008-05-29
This really isn't the right forum for your question - try the [Server Platforms](http://ubuntuforums.org/forumdisplay.php?f=339) forum.

---

### Post by MystaMax on 2008-06-05
this isn't server related. I'd put it in the [General help section]("http://ubuntuforums.org/forumdisplay.php?f=331").

I'm having a similar problem, but I can launch aptana. I can't load the start page, or anything that uses the internal browser.

Did you try the plugin version?

---

### Post by Stochastic on 2008-06-05
> **prismatic7 said:**
> This really isn't the right forum for your question - try the [Server Platforms](http://ubuntuforums.org/forumdisplay.php?f=339) forum.

> I'd put it in the General help section.

I'd say this belongs here.  Web multimedia development is legitimate in these forums.  But these first two responses clearly indicate how often web multimedia gets discussed around here (beyond the annoying "how do I use adobe" posts).

Unfortunately I too, can't offer any advice to the OP; other than suggesting they ask on the [Aptana forums]("http://forums.aptana.com/") (and of course post back with any solutions you've found).

Edit: hmm, actually this ```
wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
``` makes me wonder if you're trying to install this on a 64-bit install?  Seems like something trivial that I'd expect ajax developers to be aware of though (but ya never know).

---

