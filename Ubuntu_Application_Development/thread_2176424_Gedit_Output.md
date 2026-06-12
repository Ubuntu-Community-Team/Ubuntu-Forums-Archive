---
title: "Gedit Output"
date: 2013-09-24
forum: Ubuntu Application Development
---

### Post by nasdaqtr on 2013-09-24
I have an application that basically writes out the MAC address of the machine on a text file.
The app appeared to work fine before the updates. It also works on some other machines but when I try it on Intel Xeon machines, the Gedit file is unreadable. The filename is supposed to be MacAddress.txt and now its showing up as some wingbat letters and the file also does not contain anything.
Any ideas what might be going wrong here from anyone will be highly appreciated.

---

### Post by tgalati4 on 2013-09-24
Are all the machines 64-bit?  Perhaps you have a mix of 32-bit and 64-bit machines.

Use *cat* to examine the file in a terminal:

```
cat MacAddress.txt
```

This application, is it a simple script file?  Perhaps there are differences in the version of shell or bash that are being used to generate it.

Check the default languages on the machine and make sure they are the same.

---

### Post by nasdaqtr on 2013-09-24
It is a Xeon 1200 processor which should support 64 bit. When I run Lscpu command, it gives me Architecture as i686. The surprising thing is that running the same command on Core2Quad, I get the architecture as i686 but the same exact app works on that machine.

I couldnt use the cat command because the text file name is some strange dingbat characters that do not even copy.

---

