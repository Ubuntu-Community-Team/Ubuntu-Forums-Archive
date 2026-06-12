---
title: "Can't remove Java?"
date: 2017-12-14
forum: Server Platforms
---

### Post by ptmuldoon on 2017-12-14
I'm trying to remove Java from my Ubuntu 16 Server, but seem stuck with unable to locate the java-installer?  From what I remember and the below, I had previously installed Oracle's Java 8 on the machine.

```

ptmuldoon@OpenHab2:~$ java -version
java version "1.8.0_151"
Java(TM) SE Runtime Environment (build 1.8.0_151-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.151-b12, mixed mode)
ptmuldoon@OpenHab2:~$ sudo apt-get purge oracle-java8-installer
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'oracle-java8-installer' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And I see this in the jvm directory
```

ptmuldoon@OpenHab2:/usr/lib/jvm$ ls
java-8-oracle

```

---

### Post by QIII on 2017-12-14
Hello!

Do you recall how you installed it?

---

### Post by ptmuldoon on 2017-12-14
That's the big question, as it was done so long ago.

I'm pretty sure I had installed Oracle's PPA, updated, and then installed version 8.

I have this in /etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list
```

deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main

```

And when I run this command, it shows these two options
```

ptmuldoon@OpenHab2:~$ sudo update-alternatives --config java
There is 1 choice for the alternative java (providing /usr/bin/java).

  Selection    Path                                     Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-8-oracle/jre/bin/java   1081      auto mode
* 1            /usr/lib/jvm/java-8-oracle/jre/bin/java   1081      manual mode

```

---

