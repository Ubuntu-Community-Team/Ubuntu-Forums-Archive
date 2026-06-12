---
title: "update-alternatives --install ARGH!!!"
date: 2014-06-05
forum: Server Platforms
---

### Post by Danny_R on 2014-06-05
hello all

please find attached a screen shot of an error im receiving when trying to configure java

[[IMG]http://i25.photobucket.com/albums/c81/mudcow007/S8FXADM_zps483a4514.png[/IMG]](http://s25.photobucket.com/user/mudcow007/media/S8FXADM_zps483a4514.png.html)

im copying instructions on how to install something, the instructions said to run the following command

```
update-alternatives --install /usr/bin/java java /opt/jre1.8.0_05/bin/java
```

can anyone see what the issue is?

many thanks

---

### Post by steeldriver on 2014-06-05
You're missing the <priority> value I think, e.g.

```

$ update-alternatives --config java
There is 1 choice for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      auto mode
* 1            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode

```

```

$ sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
update-alternatives: --install needs <link> <name> <path> <priority>
.
.
.

```

but
```

$ sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java **1061**

```

works, i.e. now
```

$ update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode

Press enter to keep the current choice
[*], or type selection number:

```

---

### Post by Danny_R on 2014-06-05
Awesome thanks!!

---

### Post by monkeybrain20122 on 2014-06-05
And why are you running with root instead of sudo?

---

