---
title: "[SOLVED] Elementary OS Loki issues installing JDK"
date: 2018-01-21
forum: Ubuntu/Debian BASED
---

### Post by dizzle2 on 2018-01-21
I am about to start working with Android Studio with Elementary OS Loki and I cannot seem to download and install JDK through the terminal. However, I did manage to download the JDK from Oracle, but I do not konw how to install the tar.gz after unpacking. 

Could anyone either:
A: Help me to install the unpacked files

or

B: Help me to figure out what is wrong with apt-get install?

Thanks Much!!!

---

### Post by slickymaster on 2018-01-21
Thread moved to **Ubuntu/Debian BASED** for a better fit

---

### Post by slickymaster on 2018-01-21
I'r recommend you to use the WebUpd8 PPA (this will download the required files from Oracle and install JDK 8). In a terminal window run the following commands:```
sudo apt-add-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

If you do want to go ahead installing it manually, using the Oracle Java binaries you already downloaded just see this tutorial: [https://www.wikihow.com/Install-Oracle-Java-JDK-on-Ubuntu-Linux](https://www.wikihow.com/Install-Oracle-Java-JDK-on-Ubuntu-Linux)

---

### Post by dizzle2 on 2018-01-21
@slickymaster I have tried this tons of times in a few different ways and I keep receiving this error:

```
download failed
Oracle JDK 9 is NOT installed.
dpkg: error processing package oracle-java9-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java8-installer
 oracle-java9-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I suppose I will try and install manually this time. Thank you for your response. I will mark as solved if successful.

---

### Post by dizzle2 on 2018-01-21
I believe there is a 404 error that keeps prompting the issues

---

### Post by slickymaster on 2018-01-21
> **dizzle2 said:**
> I believe there is a 404 error that keeps prompting the issuesYes, you're right. See [https://ubuntuforums.org/showthread.php?t=2374686](https://ubuntuforums.org/showthread.php?t=2374686)

---

### Post by dizzle2 on 2018-01-21
Thank you very much for your help!

---

