---
title: "Torrent Episode Downloader"
date: 2007-02-25
forum: The Cafe
---

### Post by saracen on 2007-02-25
Does anyone know of [anything similar to TED]("http://www.ted.nu/") but for Ubuntu?

---

### Post by PurplePenguin on 2007-02-25
According to that website, it's java-based.  It should run in Ubuntu.

---

### Post by Mateo on 2007-02-25
didn't work for me

```
matthew@matthew-desktop:~/Desktop/ted$ java -jar ted.jar
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:60: Engine "clearlooks" is unsupported, ignoring
Exception in thread "main" java.lang.UnsatisfiedLinkError: no tray in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.jdesktop.jdic.tray.internal.impl.GnomeTrayAppletService.<clinit>(Unknown Source)
        at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
        at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at ted.TedMainDialog.initGUI(TedMainDialog.java:158)
        at ted.TedMainDialog.<init>(TedMainDialog.java:131)
        at ted.TedMain.main(TedMain.java:40)

```

---

### Post by saracen on 2007-02-25
yeah, i was getting some errors too

---

### Post by saracen on 2007-02-25
I got this error (something to do with system tray in the java desktop package):

```
saracen@veritas:~/Desktop/tedv080.zip_FILES$ java -jar ted.jar
/usr/share/themes/Silicon/gtk-2.0/gtkrc:64: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Silicon/gtk-2.0/gtkrc:177: Priority specification is unsupported, ignoring
Exception in thread "main" java.lang.UnsatisfiedLinkError: no tray in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.jdesktop.jdic.tray.internal.impl.GnomeTrayAppletService.<clinit>(Unknown Source)
        at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
        at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at ted.TedMainDialog.initGUI(TedMainDialog.java:158)
        at ted.TedMainDialog.<init>(TedMainDialog.java:131)
        at ted.TedMain.main(TedMain.java:40)

```

So I copied the jdic.jar file from my Frostwire installation (under /usr/lib/frostwire) and pasted it into the linux subdirectory of TED.  Now I get this error and I'm stuck:

```
saracen@veritas:~/Desktop/tedv080.zip_FILES$ java -jar ted.jar
/usr/share/themes/Silicon/gtk-2.0/gtkrc:64: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Silicon/gtk-2.0/gtkrc:177: Priority specification is unsupported, ignoring
Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/jdic/tray/TrayIcon
        at ted.TedMainDialog.initGUI(TedMainDialog.java:158)
        at ted.TedMainDialog.<init>(TedMainDialog.java:131)
        at ted.TedMain.main(TedMain.java:40)

```

---

### Post by banjobacon on 2007-02-26
I think Azureus has an RSS plugin. Check that out.

---

### Post by loftx on 2007-02-28
> **Mateo said:**
> didn't work for me

```
matthew@matthew-desktop:~/Desktop/ted$ java -jar ted.jar
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:60: Engine "clearlooks" is unsupported, ignoring
Exception in thread "main" java.lang.UnsatisfiedLinkError: no tray in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at org.jdesktop.jdic.tray.internal.impl.GnomeTrayAppletService.<clinit>(Unknown Source)
        at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
        at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at ted.TedMainDialog.initGUI(TedMainDialog.java:158)
        at ted.TedMainDialog.<init>(TedMainDialog.java:131)
        at ted.TedMain.main(TedMain.java:40)

```

Try starting ted with the following code to fix this error:

```
java -Djava.library.path=linux -jar ted.jar 
```

Works for me!

---

### Post by userundefine on 2007-02-28
Or just use democracy player.

---

### Post by precinto on 2007-03-02
> **loftx said:**
> Try starting ted with the following code to fix this error:

```
java -Djava.library.path=linux -jar ted.jar 
```

Works for me!

Works here too.

---

### Post by odzx on 2007-03-23
> java -Djava.library.path=linux -jar ted.jar
getting this error:
> oded@oded-desktop:~/Ted$ java -Djava.library.path=linux -jar ted.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/oded/Ted/linux/libtray.so: /home/oded/Ted/linux/libtray.so: wrong ELF class: ELFCLASS32
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at org.jdesktop.jdic.tray.internal.impl.GnomeTrayAppletService.<clinit>(Unknown Source)
        at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
        at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at org.jdesktop.jdic.tray.TrayIcon.<init>(Unknown Source)
        at ted.TedMainDialog.initGUI(TedMainDialog.java:158)
        at ted.TedMainDialog.<init>(TedMainDialog.java:131)
        at ted.TedMain.main(TedMain.java:40)


---

### Post by tedsupport on 2007-08-02
hi there, I'm one of the developers of ted. I see that you have some problems getting ted running on linux. Since we did not test ted on linux, it could be that there are some things that ted tries to do that are not allowed (or supported) on linux.

First make sure you use the newest version of ted (0.90). [Get it here]("http://www.ted.nu/download.php").

As it seems from the exception messages you post here, there is an error occuring when ted tries to add a tray icon. There is a way to overcome this, simply add "noTray" as argument when you start ted.

so start ted with "java -jar ted.jar noTray"

some more info can be found on [our forum]("http://www.ted.nu/forum/viewtopic.php?t=279").

If you have some more questions, please contact me. We really want to have ted running smoothly on linux!

---

### Post by UbuWu on 2007-08-02
You can easily do that yourself using deluge's rss pluging and sharetv.org rss feeds. But ted indeed makes it even easier.

---

### Post by daradib on 2007-12-08
Or in the TED configuration you can uncheck "Add ted to the system tray" under Look and Feel. That did it for me.

---

### Post by Kissell on 2008-12-04
None of the suggestions here are working for me in Hardy server x86.  When I launch the ted.jar it comes up saying this is my first time, but then it stops responding.

I'd really like to auto-schedule torrent download of my favorite show, because I don't have a DVR.  Please help!

---

### Post by wolfen69 on 2008-12-04
just go to [http://tvrss.net/](http://tvrss.net/) and go to the shows link at the top. they have every tv show torrent imaginable. it won't be automated, but you'll be able to get what you want.

---

### Post by magmon on 2008-12-04
> **wolfen69 said:**
> just go to [http://tvrss.net/](http://tvrss.net/) and go to the shows link at the top. they have every tv show torrent imaginable. it won't be automated, but you'll be able to get what you want.

{Drools} DUDE, I can download house!

---

### Post by geoken on 2008-12-04
Miro + TV RSS is what I've used in the past.

You go to TV RSS, find the show you want then copy the feed link to your clipboard. Then in Miro you create a new channel and past in the feed URL.

---

### Post by magmon on 2008-12-04
Eh, im content with downloading the video files and putting them in my videos folder. I currently have like 2 gig of video downloading in transmission xD.

---

### Post by geoken on 2008-12-04
> **magmon said:**
> Eh, im content with downloading the video files and putting them in my videos folder. I currently have like 2 gig of video downloading in transmission xD.

You would still be doing that with Miro. The only difference would be that the downloads would start automatically and that the files would all be going into folders that you set. For example, all my tv shows go into their own folder (automatically) when they're done downloading. If I was away from my computer for a week, I would automagically find new episodes of all my TV shows sitting in the appropriate folders.

---

### Post by mangurt on 2008-12-04
> **geoken said:**
> Miro + TV RSS is what I've used in the past.

You go to TV RSS, find the show you want then copy the feed link to your clipboard. Then in Miro you create a new channel and past in the feed URL.

+1 for this set-up.  It was even explained on CNET
[http://news.cnet.com/8301-13739_3-9775271-46.html](http://news.cnet.com/8301-13739_3-9775271-46.html) ):P

---

