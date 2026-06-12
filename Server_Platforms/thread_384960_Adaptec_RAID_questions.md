---
title: "Adaptec RAID questions"
date: 2007-03-15
forum: Server Platforms
---

### Post by name7ess on 2007-03-15
Hi all,

I setup Dapper on a box with an Adaptec SATA RAID[1]. It uses the aacraid driver and works out of the box.

However I also need a userspace tool in case one disk crashes so I can rebuild it. I also need to get noticed via E-Mail when this happens.

I tried to install StorMan [2], which is only provided as an RPM. Alien did not succeed and ended up with the following error:


```

dpkg-shlibdeps: warning: could not find path for libstdc++-libc6.1-1.so.2
dpkg-shlibdeps: warning: could not find path for libstdc++-libc6.1-1.so.2
dpkg-shlibdeps: warning: could not find path for libstdc++-libc6.1-1.so.2
dpkg-shlibdeps: warning: could not find path for libstdc++-libc6.1-1.so.2
dpkg-shlibdeps: warning: could not find path for libstdc++-libc6.1-1.so.2
dpkg-shlibdeps: warning: could not find any packages for  (libstdc++-libc6.1-1.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++-libc6.1-1 (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libstdc++-libc6.1-1.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++-libc6.1-1 (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libstdc++-libc6.1-1.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++-libc6.1-1 (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libstdc++-libc6.1-1.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++-libc6.1-1 (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libstdc++-libc6.1-1.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++-libc6.1-1 (soname 2, path , dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: StorMan-4.00: No such file or directory

```

uname -a is:

```

Linux blah 2.6.15-28-amd64-server #1 SMP Thu Feb 1 16:32:07 UTC 2007 x86_64 GNU/Linux

```

I also tried to extract the RPM by hand and get the java app running. However it always ends up like this:

```

root@blah:/usr/StorMan# java -cp RaidManS.jar com.ibm.sysmgt.raidmgr.mgtGUI.Launch
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:91)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.Toolkit$2.run(Toolkit.java:836)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:828)
        at sun.swing.SwingUtilities2$AATextInfo.getAATextInfo(SwingUtilities2.java:120)
        at javax.swing.plaf.metal.MetalLookAndFeel.initComponentDefaults(MetalLookAndFeel.java:1556)
        at javax.swing.plaf.basic.BasicLookAndFeel.getDefaults(BasicLookAndFeel.java:130)
        at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1591)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:537)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:577)
        at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1331)
        at javax.swing.UIManager.initialize(UIManager.java:1418)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1406)
        at javax.swing.UIManager.getInstalledLookAndFeels(UIManager.java:421)
        at javax.swing.UIManager.installLookAndFeel(UIManager.java:460)
        at javax.swing.UIManager.installLookAndFeel(UIManager.java:479)
        at com.ibm.sysmgt.raidmgr.util.JCRMOS.setLookAndFeel(JCRMOS.java:136)
        at com.ibm.sysmgt.raidmgr.mgtGUI.Launch.main(Launch.java:2844)

```

I don't really care about this StorMan application, if there is another way to control the raid then that's ok too.

Thanks for your answers!

---
[1] 0000:02:03.0 RAID bus controller: Adaptec AAC-RAID (Rocket) (rev 02)
[2] [http://www.icp-vortex.com/german/download/arc/9047ma_9117d.htm](http://www.icp-vortex.com/german/download/arc/9047ma_9117d.htm)

---

### Post by Mr. C. on 2007-03-16
Is your DISPLAY environment variable set (correctly) when the application is started ?

MrC

---

### Post by name7ess on 2007-03-16
i think so, because if it's not i get this error:

```

Exception in thread "main" java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.applet.Applet.<init>(Applet.java:50)
        at javax.swing.JApplet.<init>(JApplet.java:113)
        at com.ibm.sysmgt.raidmgr.mgtGUI.Launch.<init>(Launch.java:406)
        at com.ibm.sysmgt.raidmgr.mgtGUI.Launch.main(Launch.java:2849)

```

---

### Post by Mr. C. on 2007-03-16
Understood.  I don't know much about this particular app, but here's a reference that may shed some light:

[http://tinyurl.com/2bc6ru](http://tinyurl.com/2bc6ru)

MrC

---

### Post by himey on 2007-10-19
I also have been having an issue using the adaptec storage manager, and according to the adaptec website it does not work with the default aacraid driver and you need to install the driver from adaptec. This may be the same issue you are running into. I can get the app to load using a walkthrough I found, but I get "No controllers were found in this system" when running the app.

walkthrough: [http://lists.us.dell.com/pipermail/linux-poweredge/2006-October/028050.html](http://lists.us.dell.com/pipermail/linux-poweredge/2006-October/028050.html)
adaptec link: [http://ask.adaptec.com/cgi-bin/adaptec_tic.cfg/php/enduser/std_adp.php?p_sid=c71yn6Rh&p_lva=&p_faqid=13711](http://ask.adaptec.com/cgi-bin/adaptec_tic.cfg/php/enduser/std_adp.php?p_sid=c71yn6Rh&p_lva=&p_faqid=13711)

I myself have not been able to exactly figure out how to load the driver in place of the default raid driver :( so thats where my current problem is.

---

