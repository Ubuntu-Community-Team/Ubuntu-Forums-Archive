---
title: "Can't install a specific version of Java"
date: 2008-05-16
forum: Server Platforms
---

### Post by joemanz on 2008-05-16
I am trying to install a specific version of java-jdk on Ubuntu 8.04 server and I kept getting this error:

$ aptitude install sun-java5-jdk=1.5.0-13

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Unable to find a version "1.5.0-13" for the package "sun-java5-jdk"
Unable to find a version "1.5.0-13" for the package "sun-java5-jdk"

Any idea anyone?

Joe

---

### Post by geertn on 2008-05-17
The syntact is right, but that version probably doesn't exist in the repositories.

aptitude show sun-java5-jdk

will give youy the version in the repositories.

---

### Post by joemanz on 2008-05-23
I actually downloaded the jdk version 1.5.0_13 deb package into my repository and try to install it using that command. but it seem to always go and try to get the jdk version 1.5.0_15.  Is there any way to lock it down to a specific version?
Thanks in advance.

---

