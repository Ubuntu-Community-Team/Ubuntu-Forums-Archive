---
title: "Read a File of /dev/*"
date: 2012-11-05
forum: Ubuntu Dev Link Forum
---

### Post by JAG Franco on 2012-11-05
Hi

I need to read a file, but this file is written by a driver, for example /dev/myFile.
I want to read the file with Java, and I have tried with java.io classes, I can read other files, but I can't read myFile, maybe the reason is that the file is always changing with the information of the device.
I tried with C# and I couldn't either.

Thank you

---

### Post by codemaniac on 2012-11-05
> **JAG Franco said:**
> Hi

I need to read a file, but this file is written by a driver, for example /dev/myFile.
I want to read the file with Java, and I have tried with java.io classes, I can read other files, but I can't read myFile, maybe the reason is that the file is always changing with the information of the device.
I tried with C# and I couldn't either.

Thank you

Have you checked the file permissions of /dev/myFile?
Make sure it has read bits on in order to get it read by your Java code .

---

### Post by JAG Franco on 2012-11-07
The file permissions are:
crw-rw-rw- 1

---

