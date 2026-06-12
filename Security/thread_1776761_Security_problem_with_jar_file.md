---
title: "Security problem with jar file"
date: 2011-06-06
forum: Security
---

### Post by princebouja on 2011-06-06
Hi,

I developed an application with java for both ubuntu and windows. For windows, I converted the jar file to .exe.  I want to do the same for ubuntu because I noticed that there are programs (like JAD) that can make reverse engineering for jar file in order to see the source code. As there are some passwords in my code, I can't deliver the jar file to ubuntu users, using the usual script "java -jar file.jar".

So my question is, how to convert a jar file to an executable one for ubuntu?

---

### Post by doas777 on 2011-06-06
you probably want to start here:
[http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)

I've never tried binary compiling a java app, so no idea how it will work for you.

ultimately, code obfuscation is your best bet, but it is impossible to make your code truely un-decompilable. if the computer can understand it, so can another program.
I've worked with dotfuscator in .net, but never tried it in java.
this looks like a corallary product:
[http://www.semdesigns.com/products/obfuscators/JavaObfuscator.html](http://www.semdesigns.com/products/obfuscators/JavaObfuscator.html)

also be sure to test. on your windows executable, usually strings remain in their encoded format even as binary data, so usually passwords in an EXE can be viewed with a tool like Sysinternals "strings.exe" or Processexplorer.
[http://technet.microsoft.com/en-us/sysinternals/bb842062](http://technet.microsoft.com/en-us/sysinternals/bb842062)

i've never tried any codebreaking on a unixy system, but I would check the output of the gnu java byte->bin compiler as well, with whatever tool is appropriate.

---

