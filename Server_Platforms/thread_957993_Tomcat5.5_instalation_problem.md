---
title: "Tomcat5.5 instalation problem"
date: 2008-10-24
forum: Server Platforms
---

### Post by K.I.N.G.U.B.U.N.T.U on 2008-10-24
Hello,

I am having a problem with tomcat5.5. I installed it from the synaptic package manager. When I try to run the startup.sh script as root, I get an error:

Code:

james@james-laptop:/usr/share/tomcat5.5/bin$ sudo ./startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

I have also tried

Code:

james@james-laptop:/usr/share/tomcat5.5/bin$ sudo -s ./startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

I have set JAVA_HOME in both .bashrc and /etc/default/tomcat5.5:

Code:

JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.07/

but the I still get the same errors.

Curiously, when I run either scripts as a normal user, it starts up and goes until a permission denied error is thrown.

Code:
james@james-laptop:/usr/share/tomcat5.5/bin$ ./startup.shUsing CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun-1.6.0.07/jre/
touch: cannot touch `/usr/share/tomcat5.5/logs/catalina.out': Permission denied
./catalina.sh: 348: cannot create /usr/share/tomcat5.5/logs/catalina.out: Permission denied

I do not know what is going on! I have tried uninstalling, reinstalling, all the different thread on this forum about this topic but after two days I have been going in circles and have got to the stage where it is necessary to write this long post in the hope that someone can help me!

Please help me!

And thank you all in advance

---

### Post by teh2 on 2008-10-24
Hey! Finally something that I can help out with. Yippee!

I found the following web page that solved the Catalina.out problem for me:

[http://my.opera.com/subjam/blog/install-tomcat-5-5-in-debian-and-ubuntu](http://my.opera.com/subjam/blog/install-tomcat-5-5-in-debian-and-ubuntu)

Now I'm stuck on trying to make jspwiki run.

Good luck!

---

### Post by lykwydchykyn on 2008-10-24
Make sure you have the Java SDK installed, and use:
```

/etc/init.d/tomcat5.5 start

```
to start tomcat.  That's what worked for me when I was messing with it, though I'm not a tomcat expert by any means.

---

### Post by K.I.N.G.U.B.U.N.T.U on 2008-10-24
yes thank you, this worked perfectly, also found that if you type sudo -s <return> startup.sh <return> it also works, thank you both for your replies, there are really appreciated!!

---

### Post by bangeko on 2008-11-27
> **lykwydchykyn said:**
> Make sure you have the Java SDK installed, and use:
```

/etc/init.d/tomcat5.5 start

```
to start tomcat.  That's what worked for me when I was messing with it, though I'm not a tomcat expert by any means.

In my hardy,
```

/etc/init.d/tomcat5.5 start

```

did not work when I deploy opencms,
but if I use

```

/usr/share/tomcat5.5/bin/startup.sh

```
work fine

after add
```

JAVA_HOME=/usr/lib/jvm/java-6-sun

```
in catalina.sh

---

