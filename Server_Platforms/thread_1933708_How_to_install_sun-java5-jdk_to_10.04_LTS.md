---
title: "How to install sun-java5-jdk to 10.04 LTS"
date: 2012-02-29
forum: Server Platforms
---

### Post by cbSuperiorSoundSystems on 2012-02-29
I'm working on a project that involves installing an application from a ppa repo, and it's instructions are rather outdated, but are all I have to work with, and their support is virtually non-existant, so I'm here for some help since the answers I need are likely known by visitors to this forum.

The instructions call for me adding these repos to sources.list, but they 404 when I run aptitude update.

```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
```I've successfully added the ppa repo, but when I try to install the app from it, I get an unmet dependency for sun-java5-jdk, and the install fails.

When I google this I see instructions on how to install sun-java6, and the instructions that pertain to sun-java5 involve using the multiverse repo, which no longer contains the sun-java5-jdk package.

Could someone explain how to get this package installed?

Thanks.

---

### Post by cbSuperiorSoundSystems on 2012-02-29
It dawned on me to do a package search for 'any' Ubuntu variant, and I found that the package is available in hardy, so I just changed the sources.list to point there, and now I can install my application with the dependency met through the hardy repo.

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
```

---

### Post by hawkmage on 2012-02-29
I find that the default package install for Java a bit restrictive.  I will usually just install the Sun Java JDK or JRE and then pointing the app I am trying to run to that version.

What are you trying to do?

---

### Post by sbq on 2012-03-01
I am trying to build Android Froyo, which requires Java 5.

-Sam

---

### Post by hawkmage on 2012-03-01
In that case I would just install the Sun JDK and then make sure that it's on your path first and that you set the JAVA_HOME variable to the install directory.

---

### Post by Sergius14 on 2012-03-05
I'm building CyanogenMod Gingerbread for N1 with no errors with OpenJDK 1.6 ...

Althow if you still want to install Sun JDK, you will find them in the lucid partner channel. Don use older distributions than 10.04 because they are already out of support.

Sun JDK 1.6 should work the same way with Froyo.


In my personal experience, I'm building Gingerbread with OpenJDK with no issues at all.

---

