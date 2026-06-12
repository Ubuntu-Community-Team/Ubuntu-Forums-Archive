---
title: "How to install Oracle Java 8. (Includes JDK and JRE)"
date: 2015-06-23
forum: Tutorials
---

### Post by aaronsantiago89 on 2015-06-23
Firstly, trust me with this, because you can look up how to install this on Google and it will show the same info I am teaching you now.

Now, on with the tutorial.

First, open XTerm on Lubuntu & Kubuntu , Terminal Emulator on Xubuntu, and Terminal on Ubuntu (Main flavor), and type in what's below:


```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get oracle-java8-installer



```


Then, a text-only UI will appear with a Terms and Conditions window and after that a Yes/No window saying for you to agree to the Oracle Java Binary Agreement or something along those lines. Select Yes and Java 8 will continue with the install. After about 6 minutes (Since that's how long it took me to install this) the install will be finished and you can do whatever you need to with the Java Development Kit and/or Java Runtime Environment (Or JRE for short).

Aaron out!!!!

---

### Post by treykuhl on 2015-06-23
svradmin@logstash2:~$ sudo add-apt-repository ppa:webupd8team/java
Cannot add PPA: 'ppa:webupd8team/java'.
Please check that the PPA name or format is correct.
svradmin@logstash2:~$

---

### Post by bapoumba on 2015-06-23
@treykuhl : would you happen to be behind a proxy ?
Edit : or may be this : [http://www.webupd8.org/2014/03/fix-cannot-add-ppa-please-check-that.html](http://www.webupd8.org/2014/03/fix-cannot-add-ppa-please-check-that.html)

---

### Post by treykuhl on 2015-06-23
no proxy

but your cert link comments lead me to realize system time/date was off which was causing problem. my ubuntu server command line foo is weaksauce...too many years playing in windows gui's

got ntp installed need to get it running with job or something now. trying out a logstash so timestamps are a little crucial :-)

spanks

---

### Post by bapoumba on 2015-06-24
Hey, glad to see you found what was going strange :)

Please mark your thread as solved (under thread tools), thanks !

---

### Post by treykuhl on 2015-06-24
since the thread was started by someone else it doesn't appear i have an option to mark it resolved?

---

### Post by bapoumba on 2015-06-24
> **treykuhl said:**
> since the thread was started by someone else it doesn't appear i have an option to mark it resolved?

Oh sorry, I totally missed that /o\
No, you cannot. let's see if the OP will be back to say their issue is solved or not.

---

### Post by treykuhl on 2015-06-24
Sure thing. this is actually listed as a "tutorial" not a problem/incident thread. i posted in here so the answer may be included into the tutorial as known issues which would be valuable for other folks down the road instead of hunting through 3-4 threads to do a simple java install.

---

### Post by CantankRus on 2015-06-25
The website guide where the ppa comes from gives more info than you gave here.
[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)
or
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Nick_Dirschel on 2016-01-14
The third command is listed as ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get oracle-java8-installer[/FONT][/COLOR]
``` I believe that should be ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install oracle-java8-installer[/FONT][/COLOR]
```

---

### Post by Kit_Fox on 2016-02-17
Sorry to bring the thread back from the grave (so to speak). Since I going through university, we are using BlueJ.  Needed Java JDK and followed the instructions here for it.  I am new to Ubuntu and starting to use the terminal more.  Shouldn't the last line "install" before the file name?

---

### Post by vaiven on 2016-12-03
> **aaronsantiago89 said:**
> Firstly, trust me with this, because you can look up how to install this on Google and it will show the same info I am teaching you now.

Now, on with the tutorial.

First, open XTerm on Lubuntu & Kubuntu , Terminal Emulator on Xubuntu, and Terminal on Ubuntu (Main flavor), and type in what's below:


```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get oracle-java8-installer



```


Then, a text-only UI will appear with a Terms and Conditions window and after that a Yes/No window saying for you to agree to the Oracle Java Binary Agreement or something along those lines. Select Yes and Java 8 will continue with the install. After about 6 minutes (Since that's how long it took me to install this) the install will be finished and you can do whatever you need to with the Java Development Kit and/or Java Runtime Environment (Or JRE for short).

Aaron out!!!!

thanks for the steps, I was missing the update-alternatives.
I found a tutorial on [how to install java in ubuntu 16.04]("https://tutorials.technology/tutorials/13-how-to-install-java-oracle-on-ubuntu-the-proper-way.html") that solved my problem!!

---

### Post by kinghov on 2016-12-06
> **vaiven said:**
> thanks for the steps, I was missing the update-alternatives.
I found a tutorial on [how to install java in ubuntu 16.04]("https://tutorials.technology/tutorials/13-how-to-install-java-oracle-on-ubuntu-the-proper-way.html") that solved my problem!!
Thanks.:D

---

### Post by coffeecat on 2016-12-06
> **aaronsantiago89 said:**
> Aaron out!!!!

Hmmm. Someone didn't read [the sticky](https://ubuntuforums.org/showthread.php?t=2143602).

> **Tutorials should be supported.**
[INDENT]*You are expected to offer support for your tutorial, within practical limits. If you fail to respond to requests for help or clarification within a reasonable time, or fail to update your tutorial, the thread will be closed or removed.*[/INDENT]

Thread closed.

---

