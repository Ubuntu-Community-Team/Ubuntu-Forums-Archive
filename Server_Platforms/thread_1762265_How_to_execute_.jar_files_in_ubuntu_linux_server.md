---
title: "How to execute .jar files in ubuntu linux server"
date: 2011-05-19
forum: Server Platforms
---

### Post by ankit.pandey3 on 2011-05-19
Hi friends...........
I have a .jar file named "server.jar". In windows it executes on simply double click on it but I want to execute it on the server and I don't know how to do it???
I have Filezilla to upload any file on server and putty for cmd prompt.
Plz let me know where i have to upload my file on server and hoto execute it.....
It's urgent plzzzzz make it fast.......
Thanks in advance.................

---

### Post by dtfinch on 2011-05-19
If you have java installed, you'd run "java -jar server.jar".

If you want your program to keep running when you close putty, you could try something like "setsid java -jar server.jar >log.txt 2>&1 </dev/null &", which would disconnect it from your session to prevent it from being killed when you exit, and redirect its input and output to prevent it from failing if it tries to print.

If you don't have java installed, you could either try the OpenJDK JRE or Sun/Oracle's JRE. For OpenJDK's, installing "default-jre-headless" might be enough, or "default-jre" if the program has graphical dependencies. For Oracle's JRE, you would add or enable the partner repository in /etc/apt/sources.list and install the sun-java6-jre package. [These instructions](http://corecontentonly.com/2011/04/30/installing-java-on-ubuntu-11-04-natty-narwhal/) would work for Natty, though you'd change the "jdk" to "jre" unless you need to compile programs as well, and for other versions of Ubuntu you'd change "natty" to the name of your version.

If you happen to have both OpenJDK and Oracle's JRE's already installed (probably not), the java command might default to OpenJDK's. If that turns out to be incompatible with your program, running "update-alternatives --config java" should let you select which you want it to use.

---

### Post by ankit.pandey3 on 2011-05-19
> **dtfinch said:**
> If you have java installed, you'd run "java -jar server.jar".

If you want your program to keep running when you close putty, you could try something like "setsid java -jar server.jar >log.txt 2>&1 </dev/null &", which would disconnect it from your session to prevent it from being killed when you exit, and redirect its input and output to prevent it from failing if it tries to print.

If you don't have java installed, you could either try the OpenJDK JRE or Sun/Oracle's JRE. For OpenJDK's, installing "default-jre-headless" might be enough, or "default-jre" if the program has graphical dependencies. For Oracle's JRE, you would add or enable the partner repository in /etc/apt/sources.list and install the sun-java6-jre package. [These instructions]("http://corecontentonly.com/2011/04/30/installing-java-on-ubuntu-11-04-natty-narwhal/") would work for Natty, though you'd change the "jdk" to "jre" unless you need to compile programs as well, and for other versions of Ubuntu you'd change "natty" to the name of your version.

If you happen to have both OpenJDK and Oracle's JRE's already installed (probably not), the java command might default to OpenJDK's. If that turns out to be incompatible with your program, running "update-alternatives --config java" should let you select which you want it to use.


I upload my jar file in root folder and then i run command
"root@li226-128:~#sudo java -jar server.jar" and "root@li226-128:~#java -jar server.jar" but I got following error msg.

"Exception in thread "main" java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
        at java.awt.Window.<init>(Window.java:437)
        at java.awt.Frame.<init>(Frame.java:419)
        at javax.swing.JFrame.<init>(JFrame.java:218)
        at Server.InfiniteChatServer.<init>(InfiniteChatServer.java:42)
        at Server.InfiniteChatServer.main(InfiniteChatServer.java:283)"
Can you plz tell me where is problem.....???
Plz help me......

---

### Post by elico on 2011-05-19
well the java app you are using is using some graphical interface so you must run it on a desktop environment and not just on ordinary SSH or SHELL.

---

### Post by dtfinch on 2011-05-19
X11 over ssh would probably work for testing. You install Xming on Windows, run it, and enable the X11 forwarding option in putty. The program would then display locally. But closing putty would kill its connection to your X server and it as well.

For a long running gui app on a server, you'll want something like xvfb to create a headless X server, and x11vnc to access it remotely when needed. I've described it before [here](http://ubuntuforums.org/showthread.php?t=1740572), though you'll probably want to remove the -nopw option and specify a password (-passwd yourpassword). And if you need window borders, you'll probably want to install a window manager like metacity or openbox and run it in the script.

---

### Post by ankit.pandey3 on 2011-05-20
> **elico said:**
> well the java app you are using is using some graphical interface so you must run it on a desktop environment and not just on ordinary SSH or SHELL.

But sir how????

---

### Post by ankit.pandey3 on 2011-05-22
What hapeen???
Reply anyone please........

---

### Post by dtfinch on 2011-05-22
I thought I explained it, and you haven't provided more info, so I don't know what else to say without repeating myself. For long term, you'll need an X server like xvfb running on the server, because your [chat server](http://www.codeproject.com/KB/java/iChat-Server_Client.aspx) is a GUI app that was written/tested only on Windows, though you should also be able to test it out with putty's X11 forwarding enabled and Xming installed and running on your Windows desktop. Where are you stuck?

---

### Post by ankit.pandey3 on 2011-05-22
> **dtfinch said:**
> I thought I explained it, and you haven't provided more info, so I don't know what else to say without repeating myself. For long term, you'll need an X server like xvfb running on the server, because your [chat server]("http://www.codeproject.com/KB/java/iChat-Server_Client.aspx") is a GUI app that was written/tested only on Windows, though you should also be able to test it out with putty's X11 forwarding enabled and Xming installed and running on your Windows desktop. Where are you stuck?


Friend Now I getting the error
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1649)
        at java.lang.Runtime.load0(Runtime.java:787)
        at java.lang.System.load(System.java:1022)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1750)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1667)
        at java.lang.Runtime.loadLibrary0(Runtime.java:840)
        at java.lang.System.loadLibrary(System.java:1047)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
        at java.awt.Component.<clinit>(Component.java:572)
        at Server.InfiniteChatServer.<init>(InfiniteChatServer.java:42)
        at Server.InfiniteChatServer.main(InfiniteChatServer.java:283)


What is the problem now??
Please help.........

---

### Post by dtfinch on 2011-05-22
If you installed the headless jre, you need to install the regular jre (default-jre) because it's a gui app. That'll provide that library file.

---

### Post by ankit.pandey3 on 2011-05-23
Yes...It works...
I just set the classpath and run XManager(passive).....and jar file executes..

---

