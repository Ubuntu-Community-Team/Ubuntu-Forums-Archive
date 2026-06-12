---
title: "java security warnings apply for ubuntu 12.04?"
date: 2013-03-22
forum: Security
---

### Post by ubto66 on 2013-03-22
ubuntu is updated. installed via software centre is open sdk java 7. version is openjdk-7-jre 7u15-2.3.7.
That is not the latest java version avaible since oracle java is 7u17? Is that a security issue? Some websites running high security standards cannot be accessed with openjdk-7-jre 7u15-2.3.7.
Thanks.

---

### Post by cybergalvez on 2013-03-22
because of license issues Ubuntu does not ship with Oracle java any longer. If you want Oracle java you have to install it yourself. There are lots of threads on how to do it and Webup8.org has a PPA that also installs and keeps the Oracle java up to date

---

### Post by slickymaster on 2013-03-22
See [USN-1755-2: OpenJDK 7 vulnerabilities]("http://www.ubuntu.com/usn/usn-1755-2/")

---

### Post by ubto66 on 2013-04-07
Thank you for answers.
I know how to install oracle java sun manually on ubuntu 12.04. But updating is easier with the open jdk7. And about the usn-1755-2 I thought the latest openjdk7 should be named 7u17 and not 7u15. If openjdk7u15 is the same as oracle 7u17 sun, then openjdk7 is not made good enough because there are sites that will run with oracle 7u17 sun but not openjdk7u15. But generally when it comes to security, installing the latest openjdk should protect the computer.

---

