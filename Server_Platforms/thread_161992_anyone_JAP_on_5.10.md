---
title: "anyone JAP on 5.10??"
date: 2006-04-18
forum: Server Platforms
---

### Post by h.ki on 2006-04-18
hi all, i'm installing jap under ubuntu breezy and the verision of java is 1.4.2, I copied the file JAP.jar to :~/jap... 
when i give the usual command: 
 
java -jar JAP.jar  
 
stayng in the directory :~/jap 
 
the answer is: 
 
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit 
at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0) 
at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment() (/usr/lib/libgcj.so.6.0.0) 
at java.awt.Window.Window(java.awt.Window, java.awt.GraphicsConfiguration) (/usr/lib/libgcj.so.6.0.0) 
at java.awt.Window.Window(java.awt.Frame) (/usr/lib/libgcj.so.6.0.0) 
at jap.JAPSplash.JAPSplash(java.awt.Frame) (Unknown Source) 
at JAP.startJAP() (Unknown Source) 
at JAP.main(java.lang.String[]) (Unknown Source) 
at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0) 
at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0) 
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:JAP.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}} 
at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0) 
at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0) 
at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0) 
at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0) 
...8 more 
 
I don't know what is wrong..

---

