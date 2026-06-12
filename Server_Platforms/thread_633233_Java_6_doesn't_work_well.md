---
title: "Java 6 doesn't work well"
date: 2007-12-06
forum: Server Platforms
---

### Post by rui.torres on 2007-12-06
Hi everybody


I have a big problem with my JVM.

I installed the sun-java6-jdk package, and the installation occurred with success. The problem is that when I execute java –version command, it is sometimes executed without any problem, and at other times it gives me strange errors (“segmentation fault”, for example).

I have also installed the last version of jdk available at sun, and the problem persists.

So, I suppose that the problem is not of the JVM, but some OS library that is missing.

Other error that appears to me is:

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7e86309, pid=6497, tid=3084471184
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
#
[error occurred during error reporting, step 60, id 0xb]

# An error report file with more information is saved as hs_err_pid6497.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted


Does anyone know what is happening?

Rui Torres

---

