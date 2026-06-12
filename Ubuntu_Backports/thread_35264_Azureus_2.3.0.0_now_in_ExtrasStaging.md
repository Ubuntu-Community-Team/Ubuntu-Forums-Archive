---
title: "Azureus 2.3.0.0 now in Extras/Staging"
date: 2005-05-18
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-18
I'm pleased to announce that I've made a package of Azureus 2.3.0.0, the Java Bittorrent Client, for Hoary. It's, IMO, the best Bittorrent client available.

A few notes on this release:
[list]
[*]I'm not a professional Debian packager -- I just make my packages work.   
[*]This is the "Linux GTK" Azureus binary for i386, taken from Sourceforge.   
[*]The binary included 5 or 6 .so's (libraries). Running a quick shlibdeps on these files showed dependencies for kdelibs4 and qt3. So, live with installing a few extra libraries!   
[*]I set a dependency for sun-j2re1.5, which is in Backports/restricted, and is also the package if you use the recommended java-package method of installing Java.   
[*]There may or may not be a menu icon... I'm no expert on menus, and may try to fix it up by the next revision. It's not _THAT_ big of a deal to make your own menu entry! 
[/list]

---

### Post by Gandalf on 2005-05-18
thanks jdong, keep it going man!

---

### Post by jdong on 2005-05-18
BTW, due to the new mirroring architecture, depending on the server you choose, it may take up to 5 hrs for new packages to show up.

---

### Post by Gandalf on 2005-05-18
ok thanks

---

### Post by defkewl on 2005-05-18
Isn't ABC much better?

---

### Post by jdong on 2005-05-18
I find that Azureus gives faster download speeds (finds peers more intelligently). This was my experience when I torrented the 4GB SuSE 9.3 CD's.

Azureus also has interesting extra features -- Anonymous BT through Tor/I2P, UPnP mapping, hosting a tracker, etc.

---

### Post by ow50 on 2005-05-18
Why not build a package from debian unstable sources?
[http://packages.debian.org/unstable/source/azureus](http://packages.debian.org/unstable/source/azureus)

I havent't tried it for 2.3.0.0, but at least for the previous version it worked.

edit:
Never mind. libswt-gtk-3.1-java dependency seems to be a problem.

edit 2:
libswt-gtk-3.1-java is backportable from breezy (source package name is swt-gtk). Built that and azureus. Ran azureus first as sudo to do the automatic update it wanted. Now azureus seems to run OK.

---

### Post by jdong on 2005-05-18
[QUOTE=ow50]Why not build a package from debian unstable sources?
[http://packages.debian.org/unstable/source/azureus]("http://packages.debian.org/unstable/source/azureus")

I havent't tried it for 2.3.0.0, but at least for the previous version it worked.
[/QUOTE]

Umm, because I didn't see that last night? ](*,)](*,)](*,)

---

### Post by jdong on 2005-05-18
I can't get that to compile, so I'm staying with repackaging the binary :)

---

### Post by ow50 on 2005-05-18
I'll offer the debian unstable build as an alternative. No kde/qt dependencies and there's a menu entry.

This build uses sun-j2sdk1.5, which is at backports, or alternatively java2-runtime and java-virtual-machine, which I don't know where to get. You'll need libswt-gtk-3.1-java and libswt-gtk-3.1-jni, which I built from breezy sources. Those two libs don't exist in hoary and are not used by hoary apps, so it should be fully risk-free to install them. All these packages were built without modifications and without problems.

Azureus might want to update some plugins on the first run. The update should work fine as user, since the plugins are at ~/.Azureus/plugins.

jdong: If you want these in backports, I can rebuild them with the proper backports version tags.

**Edit:**
Links removed. New links at a new post.

---

### Post by jdong on 2005-05-18
Please do add the version trailers. Also, can you enlighten me on how you managed to compile the two? I can't get either swt-gtk or azureus to compile!

---

### Post by darkaudit on 2005-05-18
Since Azureus likes to upgrade itself, might something break the next time a new upstream version is released? I had 2.2.0.0 installed from their site, and it upgraded automagically to 2.3.0.0.

---

### Post by ow50 on 2005-05-18
Here's the packages again with the ubp version trailers:
[azureus_2.3.0.0-2~5.04ubp1_all.deb](http://koti.mbnet.fi/ots/linux/hoary/azureus_2.3.0.0-2~5.04ubp1_all.deb)
[libswt-gtk-3.1-java_3.0+3.1M4-3~5.04ubp1_all.deb](http://koti.mbnet.fi/ots/linux/hoary/libswt-gtk-3.1-java_3.0+3.1M4-3~5.04ubp1_all.deb)
[libswt-gtk-3.1-jni_3.0+3.1M4-3~5.04ubp1_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/libswt-gtk-3.1-jni_3.0+3.1M4-3~5.04ubp1_i386.deb)

[QUOTE=jdong]Also, can you enlighten me on how you managed to compile the two? I can't get either swt-gtk or azureus to compile![/QUOTE]
I don't know what problems you had, but the normal "dpkg-buildpackage -rfakeroot" worked smooth for me. No errors, no need for any tricks. Also, without swt-gtk, you can't compile azureus.

---

### Post by jdong on 2005-05-18
Ok, I'm downloading and uploading.

---

### Post by ow50 on 2005-05-21
There's a new release of azureus, 2.3.0.0-3, in debian unstable. It fixes the mime support for torrent files. I built that with the ubp version trailer, as before, no modifications or problems.

[azureus_2.3.0.0-3~5.04ubp1_all.deb](http://koti.mbnet.fi/ots/linux/hoary/azureus_2.3.0.0-3~5.04ubp1_all.deb)


To clarify my previous post on azureus' java dependencies:
The dependencies are:

sun-j2sdk1.5 | java2-runtime
sun-j2sdk1.5 | java-virtual-machine

java2-runtime and java-virtual-machine are provided by *both* sun-j2sdk1.5 and sun-j2re1.5, both of which are in backports. So either one of those should be enough.

[quote=jdong]Also, can you enlighten me on how you managed to compile the two? I can't get either swt-gtk or azureus to compile![/quote]
Did you have sun-j2sdk1.5 installed? The azureus build depends on
jikes-classpath | java2-compiler
but it seems the jikes-classpath doesn't work for compiling azureus. java2-compiler provided by sun-j2sdk1.5 should work.

---

### Post by NeoChaosX on 2005-05-21
Um, I just installed the Azureus backport, and when it started up, I got this pop-up telling me "Error loading plugin 'azuupdater'". When I click details, I get these messages

```
java.lang.ClassNotFoundException: org.gudy.azureus2.update.UpdaterPatcher
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:683)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:402)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:321)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:156)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run(Initializer.java:270)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport(SWTThread.java:107)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
	at java.lang.Thread.run(Unknown Source)
```
Is this is something important, or should I ignore it?

---

### Post by Leif on 2005-09-24
[QUOTE=NeoChaosX]Um, I just installed the Azureus backport, and when it started up, I got this pop-up telling me "Error loading plugin 'azuupdater'". [/QUOTE]

I get this too. Anyone know how to make it go away ?

---

### Post by strikeforce on 2005-09-24
You just have to update your plugins.  Its a standard thing on azureus.

---

