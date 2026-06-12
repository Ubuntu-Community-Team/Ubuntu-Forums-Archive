---
title: "Eclipse &quot;An error has occurred. See the log file...&quot;"
date: 2013-04-08
forum: Ubuntu Application Development
---

### Post by tr0m4n on 2013-04-08
Hey I've wanted to start developing with Eclipse. I installed it from the Ubuntu Software Center, when I first opened it, it said: An error has occurred. See the log file
/home/[NAME]/.eclipse/org.eclipse.platform_3.7.0_155965261/configuration/1365439518685.log,"

This is was the .log file says:
```
!SESSION 2013-04-07 18:27:46.576 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.7.0_17
java.vendor=Oracle Corporation
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=de_DE
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2013-04-07 18:27:51.391
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
    no swt-gtk-3740 in java.library.path
    no swt-gtk in java.library.path
    Can't load library: /home/roman/.swt/lib/linux/x86/libswt-gtk-3740.so
    Can't load library: /home/roman/.swt/lib/linux/x86/libswt-gtk.so

    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:285)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
    at org.eclipse.swt.internal.C.<clinit>(C.java:21)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
    at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:695)
    at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
    at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:153)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:95)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:601)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1410)
```

I hope that anyone can help me!

---

### Post by Bashing-om on 2013-04-08
tr0m4n; Hi !

Maybe;
```
sudo apt-get update
sudo apt-get upgrade
``` see if that pulls in the libraries and java requirements.[INDENT=2]
just my thought

[/INDENT]

---

### Post by tr0m4n on 2013-04-09
Nope hasn't done anyting..

---

### Post by Bashing-om on 2013-04-09
tr0m4n;

OK, what happens if we get specific to the eclipse application ?
```
sudo dpkg-reconfigure eclipse<XXX>
```where XXX = the identification of the eclipse package.
Maybe eclipse does not like the java packages ????[INDENT=3]
just a thought

[/INDENT]

---

### Post by tr0m4n on 2013-04-11
> **Bashing-om said:**
> 
where XXX = the identification of the eclipse package.
Maybe eclipse does not like the java packages ????

Maybe a dumm question but what du you mean with "identification of the eclipse package?

---

### Post by Bashing-om on 2013-04-11
tr0m4n;

I expect that the package "eclipse" to have appended to it some version numbers. "dpkg-reconfigure" must have a specific target.[INDENT=2]
regards

[/INDENT]

---

### Post by tr0m4n on 2013-04-12
Typed in:

```
sudo dpkg-reconfigure eclipse 3.7.0_155965261
```

It said me that the packet 'eclipse' isn't installed :/

---

### Post by Bashing-om on 2013-04-12
tr0m4n;
That response is true ... A package by the name only of "eclipse" is not installed. The package name should be something like:
"eclipse-3.7.0_155965261" Notice the "-" between e and 3; that makes the package as one name vice two packages as input.
A space in linux is a delimiter -> two file names.
See if this is the proper name:
```
dpkg -l eclipse-3.7.0_155965261
``` If it is, the result will list that file, else the name is not correct.
To find all the eclipse files on your system, this should work:
```
dpkg -l "eclipse*"
```[INDENT=2]
try'n to help

[/INDENT]

---

### Post by tr0m4n on 2013-04-13
The first code didn't work. Tried the second one, this is what it said:
```

  Name           Version      Description
  eclipse        <none>        (No description avaible)
  eclipse-common <none>        (No description avaible)
  eclipse-ecj    <none>        (No description avaible)
  eclipse-jdt    3.7.2-1        Eclipse Java Development Tools (JDT)
  eclipse-jdt-gc <none>        (No description avaible)
  eclipse-pde    3.7.2-1        Eclipse Plug-in Development Environment (PDE
  eclipse-pde-gc <none>        (No description avaible)
  eclipse-platfo 3.7.2-1        Eclipse platform without development plug-in
  eclipse-platfo <none>        (No description avaible)
  eclipse-platfo 3.7.2-1        Eclipse platform without development plug-in
  eclipse-platfo <none>        (No description avaible)
  eclipse-platfo <none>        (No description avaible)
  eclipse-plugin <none>        (No description avaible)
  eclipse-rcp    3.7.2-1        Eclipse Rich Client Platform (RCP)
  eclipse-rcp-gc <none>        (No description avaible)
  eclipse-source <none>        (No description avaible)

```

---

### Post by Bashing-om on 2013-04-13
tr0m4n;
Well..well. seems you have met all requirements for package installation.
see:
```
apt-cache show eclipse
```
As eclipse depends on > Depends: eclipse-jdt (>= 3.7.2-1), eclipse-pde (>= 3.7.2-1)
I suggest to re-configure those dependencies and see what results.
```
 sudo dpkg-reconfigure eclipse-pde eclipse-jdt
```looking for dpkg generated errors.[INDENT=2]

hope this helps

[/INDENT]

---

### Post by tr0m4n on 2013-04-13
Ok, I have the same depends. 

Nothing changed after re-configureing the dependencies. Same Error, same .log file...

---

### Post by tr0m4n on 2013-04-13
I do have the same depends. I reconfigured as you said...same error and same logfile.

---

### Post by Bashing-om on 2013-04-13
tr0m4n; Hi !

What I wanted to know is if there were any errors only with re-configuring the dependency flles ? Working from the bottom up.
[INDENT]
try'n to help

[/INDENT]

---

### Post by tr0m4n on 2013-04-13
```
roman@roman-ThinkPad-T500:~$  sudo dpkg-reconfigure eclipse-pde eclipse-jdt
[sudo] password for roman: 
roman@roman-ThinkPad-T500:~$ 

```

That's everything!

---

### Post by Bashing-om on 2013-04-13
tr0m4n;
In that case, I can not advise further, I have no idea presently why eclipse has errors.
I hope others can offer advise.
[INDENT]
just do not know enough

[/INDENT]

---

### Post by schragge on 2013-04-13
As the the problem seems to be that eclipse cannot find SWT library, also try to reconfigure or even reinstall *eclipse-rcp*
```
sudo dpkg-reconfigure eclipse-rcp
```
(It is *eclipse-rcp* that depends on *libswt-gtk-3-java*).

---

### Post by tr0m4n on 2013-04-14
> **schragge said:**
> As the the problems seems to be that eclipse cannot find SWT library, also try to reconfigure or even reinstall *eclipse-rcp*
```
sudo dpkg-reconfigure eclipse-rcp
```
(It is *eclipse-rcp* that depends on *libswt-gtk-3-java*).

Nope, didn't work!

---

### Post by DeadKP on 2013-05-17
i had the same problem and this helped for me, i hope it helps for you to ;)
[http://stackoverflow.com/questions/10165693/eclipse-cannot-load-swt-libraries](http://stackoverflow.com/questions/10165693/eclipse-cannot-load-swt-libraries)

*this part:
on my Ubuntu 12.04 **32 bit**. I edit the command to: 
  
ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86/ 

 And on Ubuntu 12.04 **64 bit** try: 
  
ln -s /usr/lib/jni/libswt-* ~/.swt/lib/linux/x86_64/

---

### Post by tr0m4n on 2013-05-29
Wow worked! Thanks!

---

### Post by Bashing-om on 2013-05-29
Wow! As I live and learn.

Ain't it wonderful what a symlink does/ shortcut for right file in the right place, Huh .
[INDENT=2]
Good things do happen

[/INDENT]

---

### Post by bps201 on 2013-07-16
i have same problem but now it's sloved
thanks DeadKP and tr0m4n :D

---

