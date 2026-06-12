---
title: "IDEA: Let the sun-java packages assign aliases for the commandline to their JRE's!"
date: 2008-08-15
forum: Ubuntu Brainstorm
---

### Post by Reiger on 2008-08-15
In order to use the SUN JRE 6 while passing commandline arguments on to the 'target' Java application; one has to invoke the java program which resides in /usr/lib/jvm/java-6-sun/jre/bin/java. Typing out that in full, each time is somewhat inconvenient.

However, the following ought to be much more convenient:
With installing any of the sun-javaX-yyy packages, have the installer change ~/.bashrc to include the following:
```

alias java<version>='<JAVA_HOME>/jre/bin/java'

```

So, for example with installing sun-java6-jdk or sun-java6-jre; that becomes
```

alias java6='/usr/lib/jvm/java-6-sun/jre/bin/java'

```

---

### Post by tinny on 2008-08-15
> **Reiger said:**
> In order to use the SUN JRE 6 while passing commandline arguments on to the 'target' Java application; one has to invoke the java program which resides in /usr/lib/jvm/java-6-sun/jre/bin/java. Typing out that in full, each time is somewhat inconvenient.

However, the following ought to be much more convenient:
With installing any of the sun-javaX-yyy packages, have the installer change ~/.bashrc to include the following:
```

alias java<version>='<JAVA_HOME>/jre/bin/java'

```

So, for example with installing sun-java6-jdk or sun-java6-jre; that becomes
```

alias java6='/usr/lib/jvm/java-6-sun/jre/bin/java'

```

Are you saying you want a way to conveniently use multiple Java installs?

E.g.
```

java ....... (Java 1.5...)
java2 ....... (Java 1.6....)
java3 ....... (OpenJDK)

```

Are you aware of the following command?

```

sudo update-alternatives --config java

```

This command allows you to set what Java install will be used by default.

---

### Post by Reiger on 2008-08-15
Yes & yes. But the sudo command transfers the problem so to speak. Should one try to run the GCJ for instance after transferring default-status to SUN's JRE 6 -- one has to go through the same...

EDIT: The idea is to have the X in the javaX command represent the 'version' of Java to use, in such a way it's immdediately clear which java is called. java6 is "obviously" JRE 6; java5 is "obviously" JRE 5. Etc. etc.

---

