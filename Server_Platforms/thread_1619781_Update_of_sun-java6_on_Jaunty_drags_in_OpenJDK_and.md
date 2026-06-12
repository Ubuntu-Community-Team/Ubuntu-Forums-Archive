---
title: "Update of sun-java6 on Jaunty drags in OpenJDK and Netbeans"
date: 2010-11-12
forum: Server Platforms
---

### Post by Captain_Chaos on 2010-11-12
I've been running Jaunty on a VPS hosted by Slicehost for a while now. Always had very few updates, since it's a minimal server install. I have sun-java6 and tomcat6 installed on it, hosting a Java web application.

Today I decided to check for updates again, and suddenly apt-get wants to install a slew of new packages, such as ant, icedtea, jetty, a host of Netbeans related libraries, openjdk, etc.

The only packages it wants to update are sun-java6-bin, sun-java6-jdk and sun-java6-jre, so all these new packages must be dependencies of one of them, or possibly of sun-java6, right?

Does anyone know what's going on? Is this a bug in one of the packages? Is there some way I can install just the genuine updates? How can I find out where exactly these dependencies are coming from?

Many thanks to anyone who can help me figure this out!

Kind regards,
Pepijn Schmitz

PS: I have attached the ouput of the apt-get dist-upgrade command.

---

### Post by Captain_Chaos on 2010-11-12
I have discovered that I can install just the updates to java-6 with the apt-get upgrade command (as opposed to apt-get dist-upgrade).

I'm used to using dist-upgrade to install the latest updates on my systems. Is that wrong?

It still seems wrong that dist-upgrade suddenly wants to install such a slew of new and unnecessary packages which it never has wanted to do before.

---

