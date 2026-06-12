---
title: "Can't get Azureus to run"
date: 2006-08-22
forum: Server Platforms
---

### Post by Wasted on 2006-08-22
Hi,

I've been using Debian for a while for my download server. After putting together a new server, I've decided to switch to give Ubuntu a try.

I've found everything fairly straightforeward thus far, however. I can't seem to get Azureus running. I don't have Gnome or any window manager installed, but X11 is. I am attempting to run it over SSH with the GUI for the initial set up and tuning before switching to the command line and using the Swing web interface.

When I try to run Azureus, I get the splash screen, then it crashes saying that SWT encountered an X-Windows error (I'll attach the output below).

The latest version of Azureus runs fine from my Debian box, but not with Ubuntu. I've tried using Azureus both from the Ubuntu repository, and directly off sourceforge. And I'm using Sun Java SDK 1.5 update 8 built using java-package (I've tried other JVM's, but Azureus still crashes).

Has anyone encountered anything like this before? or even better, does anyone know how to fix it?

```
osk@Onyx:/usr/azureus$ ./azureus 
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/usr/azureus/Azureus2.jar:/usr/azureus/commons-cli.jar:/usr/azureus/log4j.jar:/usr/azureus/swt.jar" -Djava.library.path="/usr/azureus" -Dazureus.install.path="/usr/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 394 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Azureus TERMINATED.
```

Thanks in advance.

---

