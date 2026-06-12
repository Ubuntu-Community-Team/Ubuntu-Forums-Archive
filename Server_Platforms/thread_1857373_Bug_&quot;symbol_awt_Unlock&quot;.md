---
title: "Bug: &quot;symbol awt_Unlock&quot;"
date: 2011-10-10
forum: Server Platforms
---

### Post by TheRealBecks on 2011-10-10
Hello everyone,

I want to run Tectonicus, a map generator for Minecraft, on my Ubuntu server 11.10 x64 (headless), but I got this bug when starting it:
```
Forcing 64-bit native libraries
Player skin cache is old or corrupt, cleaning...
Creating player icon assembler
Initialising display...
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/server/.tectonicus/native/liblwjgl.so: libjawt.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1924)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1821)
        at java.lang.Runtime.load0(Runtime.java:792)
        at java.lang.System.load(System.java:1059)
        at org.lwjgl.Sys$1.run(Sys.java:70)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
        at org.lwjgl.Sys.loadLibrary(Sys.java:82)
        at org.lwjgl.Sys.<clinit>(Sys.java:99)
        at org.lwjgl.opengl.Display.<clinit>(Display.java:130)
        at tectonicus.rasteriser.lwjgl.LwjglRasteriser.<init>(LwjglRasteriser.java:110)
        at tectonicus.rasteriser.RasteriserFactory.createRasteriser(RasteriserFactory.java:24)
        at tectonicus.TileRenderer.<init>(TileRenderer.java:146)
        at tectonicus.TectonicusApp.run(TectonicusApp.java:808)
        at tectonicus.TectonicusApp.main(TectonicusApp.java:1173)

```(--> can't open shared object file: No such file or directory)

So I edited Tectonicus.*.jar and replaced the files in the "native" folder with the ones out of the LWJGL-project ([http://lwjgl.org](http://lwjgl.org)). The bug, that he can't find  libjawt.so, still exists. libjawt.so is stored in  /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/libjawt.so, but in  /usr/lib/ the file is missing, so I linked it to the one in  java-7-openjdk. Now there's another bug also known from Ubuntu 11.04 with  openjdk-6-jre:

```
Forcing 64-bit native libraries
Player skin cache is old or corrupt, cleaning...
Creating player icon assembler
Initialising display...
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/server/.tectonicus/native/liblwjgl.so: /usr/lib/libjawt.so: symbol awt_Unlock, version SUNWprivate_1.1 not defined in file libmawt.so with link time reference
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1924)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1821)
        at java.lang.Runtime.load0(Runtime.java:792)
        at java.lang.System.load(System.java:1059)
        at org.lwjgl.Sys$1.run(Sys.java:70)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
        at org.lwjgl.Sys.loadLibrary(Sys.java:82)
        at org.lwjgl.Sys.<clinit>(Sys.java:99)
        at org.lwjgl.opengl.Display.<clinit>(Display.java:130)
        at tectonicus.rasteriser.lwjgl.LwjglRasteriser.<init>(LwjglRasteriser.java:110)
        at tectonicus.rasteriser.RasteriserFactory.createRasteriser(RasteriserFactory.java:24)
        at tectonicus.TileRenderer.<init>(TileRenderer.java:146)
        at tectonicus.TectonicusApp.run(TectonicusApp.java:808)
        at tectonicus.TectonicusApp.main(TectonicusApp.java:1173)

```I really don't know what I can do, to fix this bug. Since over two weeks I'm trying to fix it! :/ Has anyone any suggestion?

Greetings from Berlin
Becks

---

### Post by Kothar on 2012-01-24
I know this is an old thread, but I've encountered several posts like this one while trying to solve the same problem.

The answer seems to be "JWGL doesn't support OpenJDK at the moment", and switching to the Sun/Oracle JDK solved the problem for me.

Regards,

Mike.

---

