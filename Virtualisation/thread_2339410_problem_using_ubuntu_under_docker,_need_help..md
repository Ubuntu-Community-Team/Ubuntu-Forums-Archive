---
title: "problem using ubuntu under docker, need help."
date: 2016-10-08
forum: Virtualisation
---

### Post by lo2ayr on 2016-10-08
hey guys, i have been trying to run application using docker on my mac using ubuntu, but i cant get any program to run, i tried to run firefox but didn't and most important the mcu8051ide as i need this one to use it for my uni, i have download it and installed it on ubuntu VM, but its to heavy to run multiple VMs at the same time, so i have been looking for alternative, and found docker. 

any advices guys would be much appreciated.  


root@70d6fa33b979:/# mcu8051ide                  
IMPORTANT INFORMATION :
	This program is distributed in the hope that it will be useful, but with **ABSOLUTELY NO WARRANTY !**
	This is free software, so you are free to change and redistribute it.
	License: GNU General Public License version 2 or later
	Please report bugs at **[http://mcu8051ide.sf.net](http://mcu8051ide.sf.net)**
Authors:
	Martin Osmera **<martin.osmera@moravia-microsystems.com>**




ERROR: Unable to load library img::png


Tip: try to run mcu8051ide with --check-libraries to see what's wrong.
root@70d6fa33b979:/# 

--------------------------------------------------------------------------------------------------------

root@70d6fa33b979:/# mcu8051ide --check-libraries
MCU 8051 IDE v1.4.9


	Checking libraries...
		1/9 Checking for library BWidget
			Library present	... **NO !**
			Version 1.8	... **NO !**
		2/9 Checking for library Itcl
			Library present	... **YES**
			Version 3.4	... **YES**
		3/9 Checking for library md5
			Library present	... **YES**
			Version 2.0	... **YES**
		4/9 Checking for library Tk
			Library present	... **NO !**
			Version 8.5	... **NO !**
		5/9 Checking for library img::png
			Library present	... **NO !**
			Version 1.3	... **NO !**
		6/9 Checking for library tdom
			Library present	... **YES**
			Version 0.8	... **YES**
		9/9 Checking for library Tcl
			Library present	... **YES**
			Version 8.2	... **YES**


	RESULTS:
		Number of fails: 3
		**PROGRAM WILL NOT RUN**, please install the missing libraries

---

### Post by TheFu on 2016-10-08
Running a GUI program really isn't what Docker is designed to do. Actually, no containers are designed to provide direct HW access.  For running a GUI, you probably want **firejail** instead, but that won't help with HW access.

BTW, programming firmware from a VM isn't going to be a trivial thing (I won't say impossible, because someone will make a 20pg How-To and prove me wrong. VMs don't have direct access to HW (like you'd need to write to the external firmware).  I suspect you really want to dual-boot instead.  OTOH, I haven't any clue about what you are doing or the programs involved, but I do know virtualization.  

If you just want the GUI to create the firmware to be loaded, then use another method to actually write it, fine. That should work.

Also, when posting output, please put the command and output inside "code tags", so things line up.

---

### Post by lo2ayr on 2016-10-09
Well i have seen a tutorial's on how to use docker to run GUI application like netbeans and firefox, but docker host was ubuntu in the Hot-To, not osx, and when running the GUI application it run with the help of x11 so it could run as GUI, i did every thing it tell in the tutorials, but one deferent is the host am using is osx to run docker. but i still get the problem of getting it to run.

when i use this code to run the docker image of netbeans.
```
docker run -ti --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix ubuntu-netbeans
```

then when i run netbeans i get this problem.
```
$ docker run -ti --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix ubuntu-netbeansroot@a1fa343ea21d:/# netbeans&
[1] 9
root@a1fa343ea21d:/# netbeans&
[2] 220
root@a1fa343ea21d:/# netbeans 
Exception in thread "main" Exception in thread "main" java.awt.AWTError: Can't connect to X11 window server using '/private/tmp/com.apple.launchd.4pDAR1EYV4/org.macosforge.xquartz:0' as the value of t
java.awt.AWTError: Can't connect to X11 window server using '/private/tmp/com.apple.launchd.4pDAR1EYV4/org.macosforge.xquartz:0' as the value of t    at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
    at sun.awt.X11GraphicsEnvironment.access$200(X11GraphicsEnvironment.java:65)
    at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
    at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:115)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.awt.X11GraphicsEnvironment.access$200(X11GraphicsEnvironment.java:65)
    at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:115)
    at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:74)


    at java.security.AccessController.doPrivileged(Native Method)
    at java.lang.Class.forName0(Native Method)
    at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:74)    at java.lang.Class.forName(Class.java:264)
    at java.awt.GraphicsEnvironment.createGE(GraphicsEnvironment.java:103)
    at java.lang.Class.forName0(Native Method)


    at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:82)
    at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:126)    at java.lang.Class.forName(Class.java:264)
    at java.lang.Class.forName0(Native Method)
    at java.awt.GraphicsEnvironment.createGE(GraphicsEnvironment.java:103)
    at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:82)


    at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:126)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:264)
    at java.awt.Toolkit$2.run(Toolkit.java:860)    at java.lang.Class.forName(Class.java:264)
    at java.awt.Toolkit$2.run(Toolkit.java:860)
    at java.awt.Toolkit$2.run(Toolkit.java:855)


    at java.awt.Toolkit$2.run(Toolkit.java:855)    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:854)
    at sun.swing.SwingUtilities2.getSystemMnemonicKeyMask(SwingUtilities2.java:2020)
    at java.security.AccessController.doPrivileged(Native Method)


    at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:854)
    at javax.swing.plaf.basic.BasicLookAndFeel.initComponentDefaults(BasicLookAndFeel.java:1158)
    at sun.swing.SwingUtilities2.getSystemMnemonicKeyMask(SwingUtilities2.java:2020)
    at javax.swing.plaf.metal.MetalLookAndFeel.initComponentDefaults(MetalLookAndFeel.java:431)
    at javax.swing.plaf.basic.BasicLookAndFeel.initComponentDefaults(BasicLookAndFeel.java:1158)    at javax.swing.plaf.basic.BasicLookAndFeel.getDefaults(BasicLookAndFeel.java:148)


    at javax.swing.plaf.metal.MetalLookAndFeel.initComponentDefaults(MetalLookAndFeel.java:431)    at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1577)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:539)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:579)
    at javax.swing.plaf.basic.BasicLookAndFeel.getDefaults(BasicLookAndFeel.java:148)


    at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1349)
    at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1577)    at javax.swing.UIManager.initialize(UIManager.java:1459)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:539)


    at javax.swing.UIManager.setLookAndFeel(UIManager.java:579)
    at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1349)
    at javax.swing.UIManager.maybeInitialize(UIManager.java:1426)    at javax.swing.UIManager.initialize(UIManager.java:1459)
    at javax.swing.UIManager.maybeInitialize(UIManager.java:1426)
    at javax.swing.UIManager.getUI(UIManager.java:1006)
    at javax.swing.UIManager.getUI(UIManager.java:1006)


    at javax.swing.JOptionPane.updateUI(JOptionPane.java:1882)
    at javax.swing.JOptionPane.updateUI(JOptionPane.java:1882)    at javax.swing.JOptionPane.<init>(JOptionPane.java:1845)


    at javax.swing.JOptionPane.<init>(JOptionPane.java:1845)    at javax.swing.JOptionPane.showOptionDialog(JOptionPane.java:857)


    at javax.swing.JOptionPane.showOptionDialog(JOptionPane.java:857)
    at javax.swing.JOptionPane.showConfirmDialog(JOptionPane.java:795)
    at javax.swing.JOptionPane.showConfirmDialog(JOptionPane.java:795)    at javax.swing.JOptionPane.showConfirmDialog(JOptionPane.java:757)


    at javax.swing.JOptionPane.showConfirmDialog(JOptionPane.java:757)
    at org.netbeans.MainImpl.execute(Unknown Source)
    at org.netbeans.MainImpl.execute(Unknown Source)
    at org.netbeans.MainImpl.main(Unknown Source)
    at org.netbeans.MainImpl.main(Unknown Source)
    at org.netbeans.Main.main(Unknown Source)
    at org.netbeans.Main.main(Unknown Source)
[1]-  Exit 2                  netbeans
[2]+  Exit 1                  netbeans
root@a1fa343ea21d:/# 
```


i don't think it's going to work. spent enough amount of time trying to get it work. 

it would help if you know a way of getting linux apps to run on osx as i  tried to look for the apps i wanted on HOMEBREW but couldn't find all of them. 

Thanks.

---

### Post by TheFu on 2016-10-09
OSX is not Linux.  I had assumed you had wiped that commercial OS off the Mac and loaded Ubuntu. Can't help with OSX ... or any commercial OS. Sorry.

---

