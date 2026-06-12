---
title: "Can't install jre"
date: 2008-07-26
forum: Server Platforms
---

### Post by chougard on 2008-07-26
I've been trying to install jre on my ubuntu-8.04-i386-minimal vps but I keep getting the problem in the picture below.

[IMG]http://chougard.x10hosting.com/Screenshot.png[/IMG]

Any ideas on how to fix it?

Thanks!

---

### Post by gjoellee on 2008-07-26
you can download Java here: [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80) and the install instructions are here: [http://java.com/en/download/help/5000010500.xml](http://java.com/en/download/help/5000010500.xml) this is one other way to install Java...if this doesn't work please tell me

---

### Post by silkstone on 2008-07-26
Try this...

sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin

---

### Post by windependence on 2008-07-26
Yes, you didn't use sudo on the install command and that is why you had some permissions problems.

-Tim

---

### Post by tinny on 2008-07-26
> **gjoellee said:**
> you can download Java here: [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80) and the install instructions are here: [http://java.com/en/download/help/5000010500.xml](http://java.com/en/download/help/5000010500.xml) this is one other way to install Java...if this doesn't work please tell me

No please dont do this!!! The Sun JRE from the repositories is the way to go!

> 
Yes, you didn't use sudo on the install command and that is why you had some permissions problems.


Yes! You have very good eye site :lolflag:

Also, to check that it is setup correctly after install.

```

java -version

```

The output should be something like...

```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

---

### Post by windependence on 2008-07-26
silkstone's directions should get him there fine. I don't know anything about the other method above. :)

-Tim

---

