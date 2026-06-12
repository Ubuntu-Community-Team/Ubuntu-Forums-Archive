---
title: "Matlab (installed using WINE) activation problem"
date: 2009-10-29
forum: Wine
---

### Post by hmuralid on 2009-10-29
Hello,

I installed Matlab using WINE. After the installation, when the activation window popped up, since I had the activation license I clicked the manual option and to give the path of the license file, when I pressed browse an error message "There was an unexpected exception.See the log file." popped up. Also I tried typing the path myself. But it shows "Access Denied" for any path. Here's the log file below. Please help me!!

(Oct 28, 2009 22:47:49)MATHWORKS ACTIVATION IS EXITING WITH A STATUS OF 0 
(Oct 28, 2009 22:48:30)MATHWORKS ACTIVATION IS STARTING UP. 
(Oct 28, 2009 22:48:40)3184 
sun.awt.shell.Win32ShellFolder2.getFileChooserIcon  (Unknown Source) 
sun.awt.shell.Win32ShellFolderManager2.get(Unknown Source) 
sun.awt.shell.ShellFolder.get(Unknown Source) 
com.sun.java.swing.plaf.windows.WindowsLookAndFeel  $LazyWindowsIcon.createValue(Unknown Source) 
javax.swing.UIDefaults.getFromHashtable(Unknown Source) 
javax.swing.UIDefaults.get(Unknown Source) 
javax.swing.MultiUIDefaults.get(Unknown Source) 
javax.swing.UIDefaults.getIcon(Unknown Source) 
javax.swing.UIManager.getIcon(Unknown Source) 
javax.swing.plaf.basic.BasicFileChooserUI.installI  cons(Unknown Source) 
javax.swing.plaf.basic.BasicFileChooserUI.installD  efaults(Unknown Source) 
javax.swing.plaf.basic.BasicFileChooserUI.installU  I(Unknown Source) 
com.sun.java.swing.plaf.windows.WindowsFileChooser  UI.installUI(Unknown Source) 
javax.swing.JComponent.setUI(Unknown Source) 
javax.swing.JFileChooser.updateUI(Unknown Source) 
javax.swing.JFileChooser.setup(Unknown Source) 
javax.swing.JFileChooser.<init>(Unknown Source) 
javax.swing.JFileChooser.<init>(Unknown Source) 
com.mathworks.instwiz.WILicenseFileChooser.<init>(  WILicenseFileChooser.java:20) 
com.mathworks.activationclient.view.options.Activa  tionOptionsPanelImpl$6.actionPerformed(ActivationO  ptionsPanelImpl.java:8:cool: 
javax.swing.AbstractButton.fireActionPerformed(Unk  nown Source) 
javax.swing.AbstractButton$Handler.actionPerformed  (Unknown Source) 
javax.swing.DefaultButtonModel.fireActionPerformed  (Unknown Source) 
javax.swing.DefaultButtonModel.setPressed(Unknown Source) 
javax.swing.plaf.basic.BasicButtonListener.mouseRe  leased(Unknown Source) 
java.awt.Component.processMouseEvent(Unknown Source) 
javax.swing.JComponent.processMouseEvent(Unknown Source) 
java.awt.Component.processEvent(Unknown Source) 
java.awt.Container.processEvent(Unknown Source) 
java.awt.Component.dispatchEventImpl(Unknown Source) 
java.awt.Container.dispatchEventImpl(Unknown Source) 
java.awt.Component.dispatchEvent(Unknown Source) 
java.awt.LightweightDispatcher.retargetMouseEvent(  Unknown Source) 
java.awt.LightweightDispatcher.processMouseEvent(U  nknown Source) 
java.awt.LightweightDispatcher.dispatchEvent(Unkno  wn Source) 
java.awt.Container.dispatchEventImpl(Unknown Source) 
java.awt.Window.dispatchEventImpl(Unknown Source) 
java.awt.Component.dispatchEvent(Unknown Source) 
java.awt.EventQueue.dispatchEvent(Unknown Source) 
java.awt.EventDispatchThread.pumpOneEventForFilter  s(Unknown Source) 
java.awt.EventDispatchThread.pumpEventsForFilter(U  nknown Source) 
java.awt.EventDispatchThread.pumpEventsForHierarch  y(Unknown Source) 
java.awt.EventDispatchThread.pumpEvents(Unknown Source) 
java.awt.EventDispatchThread.pumpEvents(Unknown Source) 
java.awt.EventDispatchThread.run(Unknown Source)

---

### Post by unmole on 2009-10-29
Using a resource intensive program like Matlab with WINEis not such a good idea. I suggest you try Octave instead [www.**gnu](www.**gnu)**.org/software/**octave**/

---

