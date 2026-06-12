---
title: "Java Installation from tar.gz on Ubunti 14.04.LTS"
date: 2017-12-20
forum: Server Platforms
---

### Post by ockac23 on 2017-12-20
Hi folks,

I am currently struggling with the installation of java tar.gz installation file downloaded from java.com for my ubuntu 14.4 LTS 64 bit machine.
I followed exactly the simple installation steps according to the instruction on the java.com page. But I think I am missing the installation part, because these instructions below are showing just the unpacking part. But I don't see any ./install file in usr/java/ where I unpacked it. How can I enable the java on my machine? Thank you much.


[LIST=1]
[*]**Change to the directory in which you want to install.** Type:
cd *directory_path_name*
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java/
[*]Move the .tar.gz archive binary to the current directory.
[*]**Unpack the tarball and install Java**
tar zxvf jre-8u73-linux-x64.tar.gz

The Java files are installed in a directory called jre1.8.0_73 in the current directory. In this example, it is installed in the /usr/java/jre1.8.0_73 directory. When the installation has completed, you will see the word **Done**.
[*]**Delete the .tar.gz file** if you want to save disk space.
[/LIST]

---

### Post by LHammonds on 2017-12-20
Sorry, I have not installed Java manually in a VERY long time.  I hook into a repository like the following:

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
sudo add-apt-repository -r ppa:webupd8team/java

```

An open-source alternative that doesn't have the license restrictions of Oracle can be installed as one of the following:

```

sudo apt-get install openjdk-8-jdk
sudo apt-get install openjdk-8-jre

```

LHammonds

---

### Post by QIII on 2017-12-20
I highly recommend the webupd8 route.

It does not contain the Oracle Java binaries as such (Oracle doesn't allow that) but rather a set of scripts that handles the download and installation for you.

A great benefit is that Andrei keeps the scripts updated so that when you do your normal system updates Java will be automatically updated as Oracle provides new releases.

---

### Post by ockac23 on 2017-12-21
Thanks, then I will choose the webupd8team way.
Do I need to create a symbolic link for java?

---

### Post by QIII on 2017-12-21
Andrei's scripts do everything for you.

---

### Post by ockac23 on 2017-12-21
It seems I have some JRE on my machine, should I uninstall it first? When I type 

$ java -version

Output is:

java version "1.8.0_151"
Java(TM) SE Runtime Environment (build 1.8.0_151-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.151-b12, mixed mode)

Andrei's scripts maybe installs JDK in addition? I need java for my browser use. Do I need the JDK?

---

### Post by QIII on 2017-12-21
The JDK is only a number of files used by developers.  To make thing easy, they are brought in.  No need to worry.  They take up very little space.

Don't worry about the JRE you already have.  Several Java versions live happily together.  The script will take care of setting which one is used.

---

### Post by slickymaster on 2017-12-21
> **ockac23 said:**
> It seems I have some JRE on my machine, should I uninstall it first? When I type 

$ java -version

Output is:

java version "1.8.0_151"
Java(TM) SE Runtime Environment (build 1.8.0_151-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.151-b12, mixed mode)

Andrei's scripts maybe installs JDK in addition? I need java for my browser use. Do I need the JDK?
No need to. You can have multiple versions of java running. You can choose which one to use by running in terminal```
sudo update-alternatives --config java
```
But if you prefer to uninstall it just check this thorough howto: [https://askubuntu.com/questions/84483/how-to-completely-uninstall-java#185250](https://askubuntu.com/questions/84483/how-to-completely-uninstall-java#185250)

---

