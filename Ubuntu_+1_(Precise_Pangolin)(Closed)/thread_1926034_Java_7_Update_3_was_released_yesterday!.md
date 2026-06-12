---
title: "Java 7 Update 3 was released yesterday!"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-02-15
Just FYI.

---

### Post by Gregory Lee on 2012-02-15
I wonder if I have that.  I installed version 7 a short time ago, and "java -version" returns:
```
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11) (6b24-1.11-4ubuntu1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
```

---

### Post by jbicha on 2012-02-15
Java 7 is not recommended for everyone yet. And yes, Java did have a major security update this week: Java 6 Update 31 and 7 Update 3.

Gregory, you probably want to use update-alternatives to point to your Java 7 if you do want to use it.

---

### Post by kevpan815 on 2012-02-15
> **Gregory Lee said:**
> I wonder if I have that.  I installed version 7 a short time ago, and "java -version" returns:
```
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11) (6b24-1.11-4ubuntu1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
```

Nope that means that you have Java 6 Update 24, Just FYI.

---

### Post by kevpan815 on 2012-02-15
> **jbicha said:**
> Java 7 is not recommended for everyone yet. And yes, Java did have a major security update this week: Java 6 Update 31 and 7 Update 3.

Gregory, you probably want to use update-alternatives to point to your Java 7 if you do want to use it.

Yeah I noticed how Iced Tea is still Java 6 Update 24 which is a little out of date. I wish Ubuntu would hurry up and update it however as I received an E-mail today from Oracle's Java E-mail List saying that yesterday's updates are critical in nature. They also address a security risk as well. Just FYI.

---

### Post by prusswan on 2012-02-15
The best way to get the latest java on ubuntu is to use oab-java now

---

### Post by kevpan815 on 2012-02-15
> **prusswan said:**
> The best way to get the latest java on ubuntu is to use oab-java now

Actually the Java 7.0 JDK Runtime just got posted as a download in the Ubuntu Software Center! It's 40 MB's However. :-)

---

### Post by prusswan on 2012-02-15
> **kevpan815 said:**
> Actually the Java 7.0 JDK Runtime just got posted as a download in the Ubuntu Software Center! It's 40 MB's However. :-)

is that sun-java or open-jdk?

---

### Post by Gregory Lee on 2012-02-15
> **kevpan815 said:**
> Nope that means that you have Java 6 Update 24, Just FYI.
If someone doesn't mind answering a beginner's question, what do I have to do to install java 7 (in a structured way)?  I do have java 7 -- the files are there.  I "installed" it using the Software Center -- so how come it's not installed?

---

### Post by kaldor on 2012-02-15
> **Gregory Lee said:**
> If someone doesn't mind answering a beginner's question, what do I have to do to install java 7 (in a structured way)?  I do have java 7 -- the files are there.  I "installed" it using the Software Center -- so how come it's not installed?

You likely have both OpenJDK and Oracle Java installed. When using the CLI utility, it checks for the default Java program.

When running programs individually you can choose to open them with Java or OpenJDK ([SIZE="1"]right click > open with[/SIZE]). It doesn't really matter too much.

---

