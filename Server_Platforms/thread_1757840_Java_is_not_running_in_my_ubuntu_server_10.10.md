---
title: "Java is not running in my ubuntu server 10.10"
date: 2011-05-13
forum: Server Platforms
---

### Post by thoufiq on 2011-05-13
Hello All,
I am the new user of linux and installing eclipse IDE in the ubuntu server10.10. I have followed the steps given in the links [COLOR=Red]**[http://www.cyberciti.biz/faq/howto-u...igure-jdk-jre/](http://www.cyberciti.biz/faq/howto-u...igure-jdk-jre/)**[/COLOR] and [COLOR=Red]**[http://eclipse.dzone.com/articles/ho...-33-ubuntu-710](http://eclipse.dzone.com/articles/ho...-33-ubuntu-710)**[/COLOR].  After installing sun-java6-bin, sun-java6-jre and sun-java6-jdk, java  is not running in my ubuntu server10.10. and got error like this


[COLOR=Red][B]$ java -version
Error: could not open '/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jvm.cfg'

$ javac -version
Error: could not open '/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jvm.cfg'

$ javac HelloWorld.java
Error: could not open '/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jvm.cfg'

$ java HelloWorld
Error: could not open '/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jvm.cfg'[/B][/COLOR]

Pls anyone point me to the right direction.

Many Thanks.

---

### Post by hawkmage on 2011-05-13
Did you happen to look at your other post asking this?  

Here is what I posted on it:
Did you try installing Sun java using:
```
sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-jdk
```If you get an error: "Unable to locate package" then  check to see if the Partner package repository is enabled and rerun the  command.  

Then you should be able to do this:
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by thoufiq on 2011-05-13
> **hawkmage said:**
> Did you happen to look at your other post asking this?  

Here is what I posted on it:
Did you try installing Sun java using:
```
sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-jdk
```If you get an error: "Unable to locate package" then  check to see if the Partner package repository is enabled and rerun the  command.  

Then you should be able to do this:
```
sudo update-java-alternatives -s java-6-sun
```


Hello Hawkmage,
                            I had already installed sun-jav6-jre, sun-java6-plugin, sun-java6-jdk. When giving this command **[COLOR=Red]sudo update-java-alternatives -s java-6-sun[/COLOR]**, i got segmentation  fault error like this.


[B][COLOR=Red]$ sudo update-java-alternatives -s java-6-sun
/usr/sbin/update-java-alternatives: line 108: 1785 Segmentation Fault update-alternatives $uaopts --auto $name


[/COLOR][/B][COLOR=Red][COLOR=Black]Thanks[/COLOR]
[/COLOR]

---

### Post by hawkmage on 2011-05-13
You may have Java installed but was it installed using a Ubuntu specific package like would be done by apt-get?  There is definatly something missing and by installing from the Ubuntu repositories using apt-get any dependencies will be resolved.  

What happens if you try running the command:
```
sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-jdk
```

---

### Post by thoufiq on 2011-05-13
> **hawkmage said:**
> You may have Java installed but was it installed using a Ubuntu specific package like would be done by apt-get?

What happens if you try running the command:
sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-jdk

Hello Hawlmage,
                           Thank you for giving me a suggestion....Below is the o/p for sun-java6-jre, sun-java6-plugin and sun-java6-jdk by apt-get.

[B][COLOR=Red]$ sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-jdk
Reading package lists.... Done
Building dependency tree
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java-6jdk is already the newest version.
sun-java-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 90 not upgraded.[/COLOR][/B]

Thanks

---

### Post by hawkmage on 2011-05-13
OK, lets check if there are any broken dependencies with.
```
sudo apt-get check
```

---

### Post by thoufiq on 2011-05-13
> **hawkmage said:**
> OK, lets check if there are any broken dependencies with.
```
sudo apt-get check
```

Hello Hawkmage,
                            This is the o/p for the command sudo apt-get check

[B][COLOR=Red]$ sudo apt-get check
Reading package lists.... Done
Building dependency tree
Reading state information... Done[/COLOR][/B]


Thanks

---

### Post by hawkmage on 2011-05-14
This is odd.  To get Sun Java installed on Ubuntu server all I had to do is edit the "/etc/apt/sources.list" to make sure the partner repositories are active.  Then I ran the following:
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-jdk
```
Since there was no Java installed to begin with there was no need to run the update-java-alternatives.

The URL in the link you provided to the [www.cyberciti.biz](www.cyberciti.biz) is not valid so I can't see what you did.

---

