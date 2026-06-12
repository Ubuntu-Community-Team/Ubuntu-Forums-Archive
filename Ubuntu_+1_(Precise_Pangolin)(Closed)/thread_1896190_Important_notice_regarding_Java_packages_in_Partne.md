---
title: "Important notice regarding Java packages in Partner archive"
date: 2011-12-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-16
I would think that this would effect 12.04 also, so I installed 
icedtea6-plugin and openjdk-6-jdk.
See this link that is dated yesterday.
[https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html")
They install OK, and you need to restart Firefox if you install the plugin.

---

### Post by Sworddragon on 2011-12-17
Because of this I changed already some weeks ago to OpenJDK. I'm using only Minecraft and at the beginning there were some problems with OpenJDK 7. But now all is working fine.

---

### Post by dino99 on 2011-12-17
sadly java6 is still requested by some banks and administrations, as they dont knows about something else :(, so ferramroberto/java ppa is still needed.

---

### Post by irv on 2011-12-17
> **dino99 said:**
> sadly java6 is still requested by some banks and administrations, as they dont knows about something else :(, so ferramroberto/java ppa is still needed.

I just checked to make sure my bank website is still working and it is. That is a problem with some technologists. it keeps changing and one has to keep up with it.

---

### Post by effenberg0x0 on 2011-12-17
I have done a script that downloads java-6-sun, java-6-oracle and java-7-oracle from vendor website (if not already present at localhost $USER/downloads/jvm folder, creates a ramdisk at /tmp/ram and puts each of them at a separate folder inside /tmp/ram/jvm/<jvm package> at every boot, while keeping OpenJDK as the system default. This setup allows me to use cmdline arguments, temporary soft-links, etc to use a specific JVM with some apps, like Eclipse, but systemwide java/javac are set at alternatives to OpenJDK.  

You can launch a single instance of Firefox/Chrome with a specific version of Java (for banking, etc), while keeping the system defaults to OpenJDK, as an example.

My TODO was to create a way to specify programs/jvm pairs at /etc/defaults/javaram or $USER/.javaram/config to have these customised shortcuts created at login, destroyed on logout.

It's far from being as generic as it should, as it relies on my specific system paths and other tweaks to run, but I was working on making it usable at other PCs. As soon as I have the time to make it generic and improved, I'll post it here as it might help someone else.

---

### Post by tlcstat on 2011-12-17
Greetings,
No problem with Open Java 7 on my Oneiric installation. I don't think that any of these difficulties between Oracle Java and Open Java and Ubuntu would necessarily follow into a new Kernel. Most of the problems occur with non native or privately developed linux software that depend on a full implementation of Oracle Java. An example is, some text display problems and mouse behavior in MoneyDance. There are probably others but my NeroLinux 4.0b is working just fine. Most of these problems tend to update away. The solution is for Open Java to become more compliant since the Private java driven softwares will build on a licensed java and not the Open version. Incidentally, Money Dance is working fine with Open Java 7, you will have to download their version without the built in java package. That the limit of my experience. 
tlcstat

java version "1.7.0_147-icedtea"
OpenJDK Runtime Environment (IcedTea7 2.0) (7~b147-2.0-0ubuntu0.11.10.1)
OpenJDK Client VM (build 21.0-b17, mixed mode, sharing)

---

### Post by BigCityCat on 2011-12-18
I usually do java like this. I'm assuming I will be un affected.

not sure?

[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by jfernyhough on 2011-12-18
That site seems complicated. It's much easier than that.

Install update-java:
$ sudo apt-add-repository ppa:nilarimogard/webupd8
$ sudo apt-get update
$ sudo apt-get install update-java

Download and extract Java (e.g. from [http://jdk7.java.net/download.html](http://jdk7.java.net/download.html)). Note I have chosen the 64-bit JDK:
$ cd ~/download
$ wget [http://www.java.net/download/jdk7u4/archive/b04/binaries/jdk-7u4-ea-bin-b04-linux-x64-13_dec_2011.tar.gz](http://www.java.net/download/jdk7u4/archive/b04/binaries/jdk-7u4-ea-bin-b04-linux-x64-13_dec_2011.tar.gz)
$ tar -zxf jdk-7u4-ea-bin-b04-linux-x64-13_dec_2011.tar.gz

Decide where to put Java. I bung it in /usr/lib/jvm but update-java will look in your $home too.
$ sudo mv jdk1.7.0_4 /usr/lib/jvm/jdk1.7.0

Run update-java. Select /usr/lib/jvm/jdk1.7.0. Click OK.
$ update-java

Done.

Updating is easy (though not as easy as a .deb); just download the new version, delete the old one, copy in the new one, run update-java again.

---

### Post by dino99 on 2011-12-18
Thanks for the heads up guys :)

Sometimes for security reasons, banks/administrations wants java6 with javascript & cookies enabled (and the user dont), so i wonder if a "fake" java installation can exist  ( like wine does with IE for example)?

---

### Post by effenberg0x0 on 2011-12-18
> **dino99 said:**
> Thanks for the heads up guys :)

Sometimes for security reasons, banks/administrations wants java6 with javascript & cookies enabled (and the user dont), so i wonder if a "fake" java installation can exist  ( like wine does with IE for example)?

I've been playing for a while with a script to make this automatic.
The system use alternatives to point out to OpenJDK.
```

ahsl@AL-DESK:~/dev/teste$ ls -la /usr/bin/jav{a,ac}
lrwxrwxrwx 1 root root 22 Dec 12 21:04 /usr/bin/java -> /etc/alternatives/java
lrwxrwxrwx 1 root root 23 Dec 12 21:04 /usr/bin/javac -> /etc/alternatives/javac
ahsl@AL-DESK:~/dev/teste$ ls -la /etc/alternatives/jav{a,ac}
lrwxrwxrwx 1 root root 46 Dec 12 21:04 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java
lrwxrwxrwx 1 root root 43 Dec 12 21:04 /etc/alternatives/javac -> /usr/lib/jvm/java-6-openjdk-amd64/bin/javac

```I can start other JVMs using a script, at a ramdisk.
```

ahsl@AL-DESK:~$ sudo /etc/init.d/javaram start
At checkJVM: JVMs already in ramdisk
ahsl@AL-DESK:~$ ls -la /tmp/ram/jvm/
total 0
drwxr-xr-x  5 root root 0 Dec 19 00:43 .
drwxr-xr-x  3 root root 0 Dec 19 00:43 ..
drwxr-xr-x 10 root root 0 Dec 19 00:43 java-6-oracle
drwxr-xr-x 10 root root 0 Dec 19 00:43 java-6-sun
drwxr-xr-x 10 root root 0 Dec 19 00:43 java-7-oracle

```System default:
```

ahsl@AL-DESK:~$ java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b24~pre1-1ubuntu3)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

```At ramdisk: 
```

ahsl@AL-DESK:~$ export JAVA_HOME=/usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java
ahsl@AL-DESK:~$ export PATH=$PATH:/usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java
ahsl@AL-DESK:~$ alias java=/tmp/ram/jvm/java-6-sun/bin/java
ahsl@AL-DESK:~$ java -version
java version "1.6.0_01"
Java(TM) SE Runtime Environment (build 1.6.0_01-b06)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_01-b06, mixed mode)
ahsl@AL-DESK:~$ 

```Of course there are a couple better ways to do it. For an example: You can change /usr/bin/java or alternatives/java, so that if firefox pid invokes it, the java used is JVM(x). Otherwise it's JVM(y). But other PIDs will default to openJDK.

It's more or less what I'm doing here in a larger script that runs as a service.

---

### Post by grahammechanical on 2011-12-19
By coincidence I was reading this last night (actually early in the morning)

[http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/")

Regards.

---

### Post by madjr on 2011-12-19
removing software without proper notification or equivalent is bad practice, added a bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/906388](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/906388)

---

### Post by zika on 2011-12-19
I'm using, from quite long time ago, Java in DIY arrangement...
Local (user-owned) folder and system-wide registration (using update-alternatives)... Now it is Java7...
There are several threads about that (in which I've participated).
One of the reasons I've started that behavior are (sudden) changes in path(s) mainstream goes...

I have a question: does OpenJDK support (pure) 64-bit install?
(Update: Silly me, I've remembered, now, it did, even before SUN Java...)

---

