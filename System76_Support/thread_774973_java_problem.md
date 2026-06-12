---
title: "java problem"
date: 2008-04-29
forum: System76 Support
---

### Post by ewg on 2008-04-29
Sys 76 Sable Performance
Ubuntu 8.04 , 32 bit

I'm having Moneydance trouble since the upgrade to 8.04. I suspect it's related to JAVA. Posts in an Ubuntu forum indicated my System 76 ubuntu is "odd". Apparently although it's there it is not recognized. Does anyone see a problem? 

ewg@ubuntu:~$ java version
The program 'java' can be found in the following packages:
* java-gcj-compat-headless
* openjdk-6-jre-headless
* j2re1.4
* kaffe
* cacao
* gij-4.1
* jamvm
* gij-4.2
* sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

ewg@ubuntu:~$ sudo apt-get install sun-java6-bin sun-java6-jre
[sudo] password for ewg:
Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

ewg@ubuntu:~$ whereis java
java: /usr/bin/java /etc/java /usr/share/java /usr/share/man/man1/java.1.gz
ewg@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

ewg@ubuntu:~$ /usr/bin/java -version
bash: /usr/bin/java: No such file or directory

Any idea why java is not recognized? Is there a way to correct it?

Thanks,

---

### Post by thomasaaron on 2008-04-30
Hi, I received your email on this and responded to it. However, I did not get a response back from you with the details I requested. Here is the text of the email...

I've found some forum posts that indicate Moneydance is being used in Ubuntu 8.04.
Please answer the following questions:

1. Did you UPGRADE to 8.04 from 7.10, or did you do a fresh install of 8.04?
2. Have you tried to install any java versions?
3. What is the output of this command: sudo update-alternatives --config java

---

### Post by ewg on 2008-04-30
Thanks,

I upgraded from 7.10 to 8.04

I may (not sure) have tried to install a java since during the last ubuntu upgrade I had Moneydance problems. 

ewg@ubuntu:~$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          3    /usr/bin/gij-4.2
          4    /usr/bin/gij-4.1
 +        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number:

---

### Post by thomasaaron on 2008-04-30
OK, it looks like you're using openjdk as your default ubuntu version, which might explain why it is "odd."

Moneydance was built to run with sun's java. They're not all created equal.

So, run this command again...
```
sudo update-alternatives --config java
```

And select #1 for your default version. Then try moneydance.

I don't think you would need to reboot. But it wouldn't hurt to go ahead and do it.
Plus, you'll get to hear the cool Ubuntu music. ;)

---

### Post by ewg on 2008-04-30
Thank you! That did the trick.

EWG

---

### Post by rbhigday on 2008-10-12
Thanks for the help, when I could not get Moneydance to run I ended up dl the sun java since it did not install from moneydance. :)

---

