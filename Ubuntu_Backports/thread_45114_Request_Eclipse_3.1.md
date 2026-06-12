---
title: "*Request* Eclipse 3.1"
date: 2005-06-28
forum: Ubuntu Backports
---

### Post by Gnobody on 2005-06-28
Please backport this, I can't get the binaries to work on Hoary.

---

### Post by tzutolin on 2005-06-29
[QUOTE=Gnobody]Please backport this, I can't get the binaries to work on Hoary.[/QUOTE]
 Sounds like a good idea :-) 

I would also like to see netbeans 4.1 (or netbeans-dev) ([http://www.netbeans.org](http://www.netbeans.org)) which is an excellent Java IDE backported.

---

### Post by bluear on 2005-09-01
Is there anything being done with Eclipse 3.1 for hoary? I am aware of the [following](https://wiki.ubuntu.com/EclipseIDE) wiki page. However, trying to apt-get eclipse gives me an error:
```
$ sudo apt-get install eclipse-jdt
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package eclipse-jdt
```
Even though following steps detailed below gives me a running eclipse 3.1, the installation is not fully functional. For example, the browser widget (org.eclipse.swt.browser.Browser) does not work. Help uses external browser rather than internal one (for the very same reason). So what is the status of Eclipse 3.1 in hoary?

---

### Post by horacio on 2005-09-05
I need Eclipse for my work, and I want to switch to Ubuntu. I've tried hoary at my home computer, and as I couldn't install Eclipse packages, I upgraded to breezy... and it gave me some other problems.

So me too, I'd like to be able to install easily eclipse in hoary, at least until breezy will be stable :)

---

### Post by supanova on 2005-09-06
Hi All

What do you Guys want?

Eclipse doesn't need to be backported...

Install JDK1.5 then unzip eclipse into a dir of your choice after making sure that your path is correct and run eclipse...

nothing needs to be compiled....

What problems are you actually having

Ciao

---

### Post by jdong on 2005-09-10
Breezy includes native Java, and appeared to be going towards the direction of Fedora with native Eclipse. This system cannot be backported to Hoary because of Hoary's lack of GCC 4.0 with full native Java environment.

Breezy has Eclipse 3.1, so I recommend Eclipse seekers to upgrade to Breezy when it releases next month. For the impatient, do so now; I find Breezy to be fairly stable and usable.

---

### Post by bluear on 2005-09-13
[QUOTE=supanova]
What problems are you actually having
[/QUOTE]
The browser widget does not work. This is not much of a problem when accessing help (which utilizes the same widget, but can also switch to external browser), but it becomes an issue when using Eclipse WTP (see [WTP tutorial](http://www.eclipse.org/webtools/testtutorials/M2/webapptutorial/BuildingAScheduleWebApp.html); section "Adding classes to the schedule" shows integrated browser widget). Lack of integrated browser widget is caused by eclipse not being able to cooperate with libgtkembedmoz.so

**Edit**: Actually, I got the browser widget to work by launching Eclipse with the following script:
```
#!/bin/sh
export MOZILLA_FIVE_HOME="/usr/lib/mozilla-firefox/"
export ECLIPSE_HOME="/opt/eclipse"

$ECLIPSE_HOME/eclipse $*

```

---

### Post by cstudent on 2005-09-16
[QUOTE=supanova]Hi All

What do you Guys want?

Eclipse doesn't need to be backported...

Install JDK1.5 then unzip eclipse into a dir of your choice after making sure that your path is correct and run eclipse...

nothing needs to be compiled....

What problems are you actually having

Ciao[/QUOTE]

This is exactly what I did and I have had no problem running Eclipse on Hoary for the past few months.

---

