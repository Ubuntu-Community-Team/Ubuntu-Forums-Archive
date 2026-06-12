---
title: "Cant Found jvm file in /etc &amp; Java is not running"
date: 2011-05-12
forum: Server Platforms
---

### Post by thoufiq on 2011-05-12
Hello All,
          I am the new user of linux and installing eclipse IDE in the  ubuntu server10.10. I have followed the steps given in the links [COLOR=Red]**[http://www.cyberciti.biz/faq/howto-u...igure-jdk-jre/]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/")**[/COLOR] and [COLOR=Red]**[http://eclipse.dzone.com/articles/ho...-33-ubuntu-710]("http://eclipse.dzone.com/articles/how-run-eclipse-33-ubuntu-710")**[/COLOR]. After installing sun-java6-bin, sun-java6-jre and sun-java6-jdk, i cant found the [COLOR=Red]jvm file in /etc[/COLOR]. While giving the below command i got only one result but in that link they have given 4 to 5 results.How to find the [COLOR=Red]jvm file in /etc[/COLOR].


[COLOR=Red][B]$ sudo update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun

$ java -version
Error: could not open '/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jvm.cfg'[/B][/COLOR]

[COLOR=Red][B]$ javac -version
Error: could not open '/usr/lib/jvm/java-6-sun-1.6.0.21/jre/lib/i386/jvm.cfg'[/B][/COLOR]
 

Pls anyone point me to the right directions.

Many Thanks.

---

### Post by hawkmage on 2011-05-12
Did you try installing Sun java using:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk
```
If you get an error: "Unable to locate package" then check to see if the Partner package repository is enabled and rerun the command.  

Then you should be able to do this:
```
sudo update-java-alternatives -s java-6-sun
```

---

