---
title: "jar with embedded derby db not working"
date: 2016-12-15
forum: Ubuntu Application Development
---

### Post by andrei.nistor on 2016-12-15
I am experiencing some problems with a java application that i made in eclipse. it is a simple app that should connect to a embedded derby db. it works well when i run it from eclipse. after exporting the jar file it runs well on windows10 but throws "java.sql.SQL.SintaxErrorException:Table/View 'REGISTRATION' does not exist." error when i run it in terminal from ubuntu. i use openjdk 8, eclipse neon, ubuntu16.04LTS. i have included in resources the embedded driver, derby.jar, derbytools.jar and built the path to the named resources. the question is why is it throwing this exception in ubuntu and works just fine in windows?

---

### Post by andrei.nistor on 2016-12-17
Reinstalled ubuntu on machine and now it works. so there was the problem. the os was not working properly.

---

