---
title: "Unable to access jarfile"
date: 2020-02-19
forum: Server Platforms
---

### Post by ghostbacon on 2020-02-19
I'm currently running Ubuntu on my server and wanting to run a Minecraft modded server for me and my mates. I've done this before multiple times but for some reason when I do it now I keep getting the message "Unable to access jarfile"
I've tried fixing this by changing the name and directory and ensuring that I've typed it correctly. I've also tried changing it from ```
**sudo java -Xms4G -Xmx4G -jar forge-1.8.9-11.15.1.1722-installer nogui**
``` to ```
**java -jar /home/thomas/Downloads/minecraf/forge-1.8.9-11.15.1.1722-installer.jar**
```. I've also tried doing ```
**sudo chown -R $thomas:$thomas ~**
``` but no matter anything i do i just can't get it to work.

---

### Post by slickymaster on 2020-02-19
*Thread moved to **Server Platforms**.*

---

### Post by spjackson on 2020-02-19
> **ghostbacon said:**
> I keep getting the message "Unable to access jarfile"
```
**java -jar /home/thomas/Downloads/minecraf/forge-1.8.9-11.15.1.1722-installer.jar**
```

I don't know anything about the specifics of running this particular jar, but I do know something about what is needed for java to execute a jar. If the above command is giving you the above message (or more precisely "Error: Unable to access jarfile /home/thomas/Downloads/minecraf/forge-1.8.9-11.15.1.1722-installer.jar") then there are 2 possible causes:
1. The file does not exist (e.g. perhaps it should be minecraft not minecraf or perhaps there's a lowercase/uppercase inaccuracy)
or 2. You do not have read access to it.

Note that if the jar exists but is corrupt or in some other way invalid, or there are missing dependencies, you will get a different message. What do you get from the following?
```

ls -l /home/thomas/Downloads/minecraf/forge-1.8.9-11.15.1.1722-installer.jar

```

---

### Post by ghostbacon on 2020-02-19
It turns out I did, in fact, spell Minecraft incorrectly although now running this I get the response 
```
A problem occurred running the Server launcher.java.lang.reflect.InvocationTargetException
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.base/java.lang.reflect.Method.invoke(Method.java:566)
    at net.minecraftforge.fml.relauncher.ServerLaunchWrapper.run(ServerLaunchWrapper.java:62)
    at net.minecraftforge.fml.relauncher.ServerLaunchWrapper.main(ServerLaunchWrapper.java:31)
Caused by: java.lang.ClassCastException: class jdk.internal.loader.ClassLoaders$AppClassLoader cannot be cast to class java.net.URLClassLoader (jdk.internal.loader.ClassLoaders$AppClassLoader and java.net.URLClassLoader are in module java.base of loader 'bootstrap')
    at net.minecraft.launchwrapper.Launch.<init>(Launch.java:34)
    at net.minecraft.launchwrapper.Launch.main(Launch.java:28)
    ... 6 more

```

---

### Post by EuclideanCoffee on 2020-02-19
It may have to do with openjdk.

Consider switching to openjdk8.

[https://github.com/MinecraftPortCentral/Cauldron-Issues/issues/26](https://github.com/MinecraftPortCentral/Cauldron-Issues/issues/26)

[https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04)

---

### Post by LHammonds on 2020-02-19
Make sure whatever version of OpenJDK or Oracle Java you use is compatible with Minecraft 1.8 (which is what Forge 1.8 is based on)

My guess would be Java 1.8 flavor but I could be wrong.

---

### Post by ghostbacon on 2020-02-23
It seems I've already got Java 8

---

### Post by spjackson on 2020-02-23
> **ghostbacon said:**
> It seems I've already got Java 8
That is surprising because the ClassLoader error you are getting is precisely what you would get when running some Java 8 code from Java 9 or above. The issue is explained [here]("https://stackoverflow.com/questions/46694600/java-9-compatability-issue-with-classloader-getsystemclassloader"). Note in particular the quotation from the Java 9 release notes.

If you are actually running the jar with Java 8, then I'm afraid I've no idea how you would be getting that error.

---

### Post by ghostbacon on 2020-02-24
Update: I decided to uninstall Java and reinstall Java 8, having done this It's seemed that I've completely broken Java as no matter how many times I do it, "java" is not a recognized command. When doing "sudo update-alternatives --config java", I'm returned with "update-alternatives: error: no alternatives for java".

---

### Post by LHammonds on 2020-02-24
The built-in runtime packages for OpenJDK in Ubuntu are:

```
sudo apt install openjdk-8-jre-headless
```
and
```
sudo apt install openjdk-11-jre-headless
```

To install Oracle Java 8, you need to add their repository, then update and install the runtime:

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt update
sudo apt install oracle-java8-installer
```

If you have mutliple versions of java installed, you use this command to show/set which java is default when you just type "java"

```
sudo update-alternatives --config java
```

Or you could just specify the path to "java" when you are running the program such as:

```
/usr/lib/jvm/java-8-oracle/jre/bin/java -jar /home/thomasthetrain/Downloads/minecraf/forge-1.8.9-11.15.1.1722-installer.jar
```
or
```
/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -jar /home/thomasthetrain/Downloads/minecraf/forge-1.8.9-11.15.1.1722-installer.jar
```

Just make sure you use the path that is setup on your system....rather than copy/paste what I have typed...which may not be accurate to your system.

LHammonds

---

### Post by ghostbacon on 2020-02-24
I've tried this and when running "sudo apt install oracle-java8-installer", I'm returned with the message 
"Reading state information... Done
Package oracle-java8-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'oracle-java8-installer' has no installation candidate"

---

### Post by LHammonds on 2020-02-24
What is the contents of this command?

```
cat /etc/apt/sources.list
```

LHammonds

---

### Post by ghostbacon on 2020-02-25
I'm returned with
```
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic universe
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

---

### Post by LHammonds on 2020-02-25
Ah, that is a standard list.  I thought the "add-apt-repository ppa:webupd8team/java" would append to that list.  It seems it adds a file here:

```
/etc/apt/sources.list.d/webupd8team-ubuntu-java-bionic.list
```

Which contains the following text:

```
deb http://ppa.launchpad.net/webupd8team/java/ubuntu bionic main
```

However, upon running the add-apt-repository command, you are greeted with this message which basically says Oracle has removed everything older than the most current versions:

```

The Oracle JDK License has changed for releases starting April 16, 2019.

The new Oracle Technology Network License Agreement for Oracle Java SE is substantially different from prior Oracle JDK licenses. The new license permits certain uses, such as personal use and development use, at no cost -- but other uses authorized under prior Oracle JDK licenses may no longer be available. Please review the terms carefully before downloading and using this product. An FAQ is available here: https://www.oracle.com/technetwork/java/javase/overview/oracle-jdk-faqs.html

Oracle Java downloads now require logging in to an Oracle account to download Java updates, like the latest Oracle Java 8u211 / Java SE 8u212. Because of this I cannot update the PPA with the latest Java (and the old links were broken by Oracle).

For this reason, THIS PPA IS DISCONTINUED.

For Oracle Java 11, see a different PPA -> https://www.linuxuprising.com/2019/06/new-oracle-java-11-installer-for-ubuntu.html

That same PPA also has Oracle Java 13 -> https://www.linuxuprising.com/2019/09/install-oracle-java-13-on-ubuntu-linux.html

Old description:

Oracle Java (JDK) Installer (automatically downloads and installs Oracle JDK8). There are no actual Java files in this PPA.

Important -> Why Oracle Java 7 And 6 Installers No Longer Work: http://www.webupd8.org/2017/06/why-oracle-java-7-and-6-installers-no.html

Update: Oracle Java 9 has reached end of life: http://www.oracle.com/technetwork /java/javase/downloads/jdk9-downloads-3848520.html

The PPA supports Ubuntu 18.10, 18.04, 16.04, 14.04 and 12.04.

More info (and Ubuntu installation instructions):
- http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html

Debian installation instructions:
- Oracle Java 8: http://www.webupd8.org/2014/03/how-to-install-oracle-java-8-in- debian.html
 More info: https://launchpad.net/~webupd8team/+archive/ubuntu/java

```

So even if you add the old repository, the package is no longer there as evidenced by the following command:

```
sudo apt search oracle-java8-installer
```

Which means you are out of luck from an official capacity.

Next shot is to try the OpenJDK 8 variant.

```
sudo apt install openjdk-8-jre-headless
```

When I do that, it installs and I can now type this:

```

java -version
openjdk version "1.8.0_242"
OpenJDK Runtime Environment (build 1.8.0_242-8u242-b08-0ubuntu3~18.04-b08)
OpenJDK 64-Bit Server VM (build 25.242-b08, mixed mode)

```

I did not have any version of java installed prior to running these commands.

---

### Post by ghostbacon on 2020-02-26
I'm sure this isn't supposed to happen
```
thomas@server:~$ sudo apt install openjdk-8-jre-headless
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-8-jre-headless is already the newest version (8u242-b08-0ubuntu3~18.04).
0 to upgrade, 0 to newly install, 0 to remove and 7 not to upgrade.
thomas@server:~$ java -version

Command 'java' not found, but can be installed with:

sudo apt install default-jre            
sudo apt install openjdk-11-jre-headless
sudo apt install openjdk-8-jre-headless 

thomas@server:~$ 

```

---

### Post by LHammonds on 2020-02-27
> **ghostbacon said:**
> 
```
openjdk-8-jre-headless is already the newest version (8u242-b08-0ubuntu3~18.04).

```
If it is already installed, then the main issue is the path to "java" which it does not know.

I re-installed openjdk again for you and typed this command to find the location:

```
which java
/usr/bin/java
```

But that is just a symlink to a different location:
```
ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 Feb 27 13:27 /usr/bin/java -> /etc/alternatives/java
```

But this is also a symlink to another location:
```
ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 46 Feb 27 13:27 /etc/alternatives/java -> /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java
```

When I do this command:
```
sudo update-alternatives --config java
```

I get this result because I only have one variation of Java installed and it is all linked correctly:
```
There is only one alternative in link group java (providing /usr/bin/java): /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java
Nothing to configure.

```

Have you tried calling java directly using the command I provided to you earlier?  If that works, you can just create a symbolic link at /usr/bin/java that points to it if you really have to exclude the path to java when calling it.

```
/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -jar /home/thomasthetrain/Downloads/minecraf/forge-1.8.9-11.15.1.1722-installer.jar
```

---

### Post by ghostbacon on 2020-02-27
It seems that it's just not there.
```
/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -jar /home/thomas/Downloads/minecraft/forge-1.8.9-11.15.1.1722-installer.jar
bash: /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java: No such file or directory
```
[ATTACH=CONFIG]285101[/ATTACH]

---

### Post by LHammonds on 2020-02-27
Try removing it and purging all configs related to it:

```

sudo apt remove openjdk-8-jre-headless
sudo apt purge openjdk-8-jre-headless
sudo apt autoremove

```

Now try to install it again:
```

sudo apt install openjdk-8-jre-headless

```

Then see if you can type "java -v" or "which java" to see view the install path.

LHammonds

---

### Post by ghostbacon on 2020-02-27
Thanks LHammonds, I don't really use Linux (as you can see). Although this is one of the main reasons I love Linux, the amount of help you get from the forums, especially to newbies like me.
It's working perfect now

---

