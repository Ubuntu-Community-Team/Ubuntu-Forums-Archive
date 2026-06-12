---
title: "I want to help Linux"
date: 2008-10-06
forum: The Cafe
---

### Post by Lightmaster on 2008-10-06
Good evening everyone!I'm a 17 year old high-school student with some free time on my hands and I'm thinking about helping out the community, because they helped me alot.
I'm not a very technical user right now, but I'm pretty good with translating software into French/Romanian(I'm living in Romania now) so I would be really greatfull if there are any projects in need for some help.

---

### Post by aktiwers on 2008-10-06
> **Lightmaster said:**
> Good evening everyone!I'm a 17 year old high-school student with some free time on my hands and I'm thinking about helping out the community, because they helped me alot.
I'm not a very technical user right now, but I'm pretty good with translating software into French/Romanian(I'm living in Romania now) so I would be really greatfull if there are any projects in need for some help.

Hi

You could sign up at [https://launchpad.net/](https://launchpad.net/) and start translating for projects you like:)

---

### Post by kernelhaxor on 2008-10-06
You could join the Romanian team I guess [https://wiki.ubuntu.com/RomanianTeam](https://wiki.ubuntu.com/RomanianTeam)

---

### Post by mihai.ile on 2008-10-06
I'm Romanian too, but I'm studying in Portugal, I've started also by helping with translations in launchpad, now I made my own project ([www.jkiwi.com](www.jkiwi.com)) and looking forward to send it to the repositories.
In the meanwhile I help whenever possible submitting bugs in launchpad for rhythmbox, gedit plugins, banshee, and help with hardware recognition (submitting bug reports for hal-info data)...
I think the most important thing is to help by avoiding repeated work (for example helping at rhythmbox bugs instead of creating a new mp3 player software)

I also have a laptop, created a wiki page here on Ubuntu Laptop Testing Team and reviewed hardware compatibility and tips&tricks...

Well those are just a few ideas you may also try...

---

### Post by aktiwers on 2008-10-06
> **mihai007 said:**
> I'm Romanian too, but I'm studying in Portugal, I've started also by helping with translations in launchpad, now I made my own project ([www.jkiwi.com]("http://www.jkiwi.com")) and looking forward to send it to the repositories.
In the meanwhile I help whenever possible submitting bugs in launchpad for rhythmbox, gedit plugins, banshee, and help with hardware recognition (submitting bug reports for hal-info data)...
I think the most important thing is to help by avoiding repeated work (for example helping at rhythmbox bugs instead of creating a new mp3 player software)

I also have a laptop, created a wiki page here on Ubuntu Laptop Testing Team and reviewed hardware compatibility and tips&tricks...

Well those are just a few ideas you may also try...

Looks cool that project..  I get this error while running:
> 
aktiwers@HAL2:~$ jkiwi 
java.lang.ClassCastException: java.lang.Long cannot be cast to java.lang.Integer
    at utils.GtkStockIconSWT.createImage(GtkStockIconSWT.java:120)
    at utils.StockIcon.getGTKImageData(StockIcon.java:275)
    at utils.StockIcon.getIcon(StockIcon.java:161)
    at core.MainWindow.createSShell(MainWindow.java:227)
    at core.MainWindow.<init>(MainWindow.java:200)
    at core.Loader$Worker$3.run(Loader.java:495)
    at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at core.Loader.main(Loader.java:235)
Exception in thread "main" org.eclipse.swt.SWTException: Failed to execute runnable (java.lang.IllegalArgumentException: Argument not valid)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at core.Loader.main(Loader.java:235)
Caused by: java.lang.IllegalArgumentException: Argument not valid
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.graphics.ImageData.<init>(Unknown Source)
    at org.eclipse.swt.graphics.ImageData.<init>(Unknown Source)
    at utils.GtkStockIconSWT.createImage(GtkStockIconSWT.java:155)
    at utils.StockIcon.getGTKImageData(StockIcon.java:275)
    at utils.StockIcon.getIcon(StockIcon.java:161)
    at core.MainWindow.createSShell(MainWindow.java:227)
    at core.MainWindow.<init>(MainWindow.java:200)
    at core.Loader$Worker$3.run(Loader.java:495)
    at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
    ... 4 more
aktiwers@HAL2:~$ 




Im on Ubuntu 8.10 :)

---

### Post by mihai.ile on 2008-10-07
uhm... not too good as a first impression eh?
well did you install the .deb version?
If so, are you using Ubuntu 64 bit?
This problem has to do with the fact that the .deb/java/the application can't decide if it's running in 32 or 64 bit enviroment.

When I get home today i'll have a check on this issue...

---

### Post by aktiwers on 2008-10-07
Yes I am on 64bit.. sorry I forget this my self all the time. Just got a new computer :)

---

### Post by mihai.ile on 2008-10-07
Well it seems to me that you have a 64bit system with a java 32bit
So the deb installed and configured the application on a 64bit environment but java is 32bit.

Can you check if you are running a 32bit java?

---

### Post by aktiwers on 2008-10-07
I will check it when I get home from work

---

### Post by aktiwers on 2008-10-07
Yep I am on 64bit Java
> 
aktiwers@HAL2:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
aktiwers@HAL2:~$ 


---

### Post by aysiu on 2008-10-07
How about translating some documentation?

I've had various offers to translate [my tutorials](http://www.psychocats.net/ubuntu/) into non-English languages, but I don't think they've been translated into French or Romanian.

---

