---
title: "Java 6 update 15"
date: 2009-08-09
forum: Security
---

### Post by JarG0n on 2009-08-09
How can Java 6 update 15 be installed on 9.04 Jaunty?  I don't see it in the repository.

---

### Post by espressobeanies on 2009-08-09
Good question. I'm waiting for an answer. The one thing I don't like is that it takes a while for serious updates to be put on the repository.

---

### Post by cariboo on 2009-08-10
Ubuntu does not upgrade to newer version of most programs once an Ubuntu version has been released. The only updates you will get are security updates. To get a newer version of a package you will have to upgrade to a newer version, or install the new version from the producers web site.

---

### Post by JarG0n on 2009-08-10
This IS a high priority security update.

---

### Post by espressobeanies on 2009-08-10
I c cariboo's point. Java is third-party software, not a part of the main package.  If Java's on the main Ubuntu repo, who's in charge of overseeing updated versions getting to the repo?

---

### Post by Arup on 2009-08-10
Download .bin from Java site and follow instructions at [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

Instead of /opt you can put the binary in /usr/lib/jvm folder in case you have previously installed Sun Java.

---

### Post by Pjotr123 on 2009-08-10
It's too easy to dismiss this as software that won't be updated because it's third party stuff in Multiverse.... Most people install it, so it affects most users. Most home users anyway. Canonical (or the community) can't just fail them.

It's important, because it's a security issue. It should be treated as such. On my openSUSE 11.1 box, I received this JRE update yesterday. So here's another big distro, that does take this seriously.

There's a bug report in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559)

Feel free to support it there. :-)

---

### Post by caeroe on 2009-08-10
Weird... I did that and my java -version replies with:

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
**Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)**

Also the test page on that site listed above still says I'm using build 14, the one with the huge honkin' security flaw.

---

### Post by JarG0n on 2009-08-11
> **caeroe said:**
> Weird... I did that and my java -version replies with:

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
**Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)**

Also the test page on that site listed above still says I'm using build 14, the one with the huge honkin' security flaw.

```
user@UbuntuDesktop:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Client VM (build 14.0-b16, mixed mode, sharing)

```

:mad:

While this package (sun-java6-jre) is not officially supported, someone should update it!  I see the maintainer listed in Synaptic.  Maybe I will email him and ask.  

Is there an officially supported version of java that works as well?

---

### Post by cariboo on 2009-08-11
It was updated in Karmic this morning, so there should be an update available for older versions too.

---

### Post by Pjotr123 on 2009-08-12
You can apply a workaround to install the new JRE which is meant for Karmic, in Hardy, Intrepid and Jaunty.

This workaround is for 32-bit Ubuntu only! You have to adapt it for a 64 bit system.

1. Manually download these three files from Multiverse:

Bin: 
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-15-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-15-1_i386.deb)

JRE:
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb)

Plugin:
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-15-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-15-1_i386.deb)

2. Put these files in your home folder, don't leave them on the desktop.

3. Applications - Accessories - Terminal
Execute the following terminal commands (use copy/paste to place them in the terminal):
```
sudo dpkg -i sun-java6-bin_6-15-1_i386.deb sun-java6-jre_6-15-1_all.deb
```

Press Enter. Your password will remain invisible, not even dots, this is normal.

and then:
```
sudo dpkg -i sun-java6-plugin_6-15-1_i386.deb
```

Press Enter.

4. Ready. :)

Bad that we need a workaround... We shouldn't need one. The package maintainer isn't active enough. :(

---

### Post by skixx on 2009-08-12
I did everything you said,but I get this:



Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


and it still don't work
please help, thanks.

---

### Post by JarG0n on 2009-08-13
> **Pjotr123 said:**
> You can apply a workaround to install the new JRE which is meant for Karmic, in Hardy, Intrepid and Jaunty.

This workaround is for 32-bit Ubuntu only! You have to adapt it for a 64 bit system.

1. Manually download these three files from Multiverse:

Bin: 
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-15-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-15-1_i386.deb)

JRE:
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb)

Plugin:
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-15-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-15-1_i386.deb)

2. Put these files in your home folder, don't leave them on the desktop.

3. Applications - Accessories - Terminal
Execute the following terminal commands (use copy/paste to place them in the terminal):
```
sudo dpkg -i sun-java6-bin_6-15-1_i386.deb sun-java6-jre_6-15-1_all.deb
```

Press Enter. Your password will remain invisible, not even dots, this is normal.

and then:
```
sudo dpkg -i sun-java6-plugin_6-15-1_i386.deb
```

Press Enter.

4. Ready. :)

Bad that we need a workaround... We shouldn't need one. The package maintainer isn't active enough. :(

Thank you.  This worked for me, but only after installing unixodbc first; a required dependency for java.

```

user@desktop:~/Bin/java$ sudo dpkg -i sun-java6-bin_6-15-1_i386.deb sun-java6-jre_6-15-1_all.deb
Selecting previously deselected package sun-java6-bin.
(Reading database ... 124433 files and directories currently installed.)
Unpacking sun-java6-bin (from sun-java6-bin_6-15-1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from sun-java6-jre_6-15-1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on unixodbc; however:
  Package unixodbc is not installed.
dpkg: error processing sun-java6-bin (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-15-1) | ia32-sun-java6-bin (= 6-15-1); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-jre

```

I didn't have to install ia32-sun-java6-bin.  Once I installed unixodbc, it installed fine.

```
sudo aptitude install unixodbc
```

```
user@desktop:~/Bin/java$ sudo aptitude install unixodbc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  odbcinst1debian1{a} unixodbc 
The following partially installed packages will be configured:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/362kB of archives. After unpacking 1176kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package odbcinst1debian1.
(Reading database ... 125331 files and directories currently installed.)
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-16build3_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-16build3_i386.deb) ...
Processing triggers for man-db ...
Setting up odbcinst1debian1 (2.2.11-16build3) ...

Setting up unixodbc (2.2.11-16build3) ...

Setting up sun-java6-jre (6-15-1) ...

Setting up sun-java6-bin (6-15-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

Current status: 0 broken [-1].

```

```
user@desktop:~/Bin/java$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)

```

---

### Post by Soul-Sing on 2009-08-13
[SIZE="4"]64 bit systems update-15 install with plugin[/SIZE]
the update-15 file on your Desktop


```
cd /opt
sudo mkdir java
```

```
cd java
sudo mkdir 64
```

```
cd Desktop
```

```
sudo mv ~/Desktop/jre-6u15-linux-x64.bin /opt/java/64
```
```
sudo chmod 755 /opt/java/64/jre-6u15-linux-x64.bin
```

```
cd /opt/java/64
sudo ./jre-6u15-linux-x64.bin
```

```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_15/bin/java" 1
```
```
sudo update-alternatives --set java /opt/java/64/jre1.6.0_15/bin/java
```

[COLOR="Red"]plugin install[/COLOR]


[COLOR="Red"]remove previous versions[/COLOR]
```
rm ~/.mozilla/plugins/libnpjp2.so
```

[COLOR="Red"]or make/create a[/COLOR] ./mozilla/plugin folder

[COLOR="Red"]make/create a symlink[/COLOR]

```
ln -s /opt/java/64/jre1.6.0_15/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

---

### Post by Pjotr123 on 2009-08-18
I have requested the attention of the MOTU's for this grave and serious matter: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559/comments/22](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559/comments/22)

I will keep you posted about the sequel.

---

### Post by JohnnyVW on 2009-08-18
> **Pjotr123 said:**
> You can apply a workaround to install the new JRE which is meant for Karmic, in Hardy, Intrepid and Jaunty.

This workaround is for 32-bit Ubuntu only! You have to adapt it for a 64 bit system.

1. Manually download these three files from Multiverse:

Bin: 
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-15-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-15-1_i386.deb)

JRE:
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-15-1_all.deb)

Plugin:
[http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-15-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-15-1_i386.deb)

2. Put these files in your home folder, don't leave them on the desktop.

3. Applications - Accessories - Terminal
Execute the following terminal commands (use copy/paste to place them in the terminal):
```
sudo dpkg -i sun-java6-bin_6-15-1_i386.deb sun-java6-jre_6-15-1_all.deb
```

Press Enter. Your password will remain invisible, not even dots, this is normal.

and then:
```
sudo dpkg -i sun-java6-plugin_6-15-1_i386.deb
```

Press Enter.

4. Ready. :)

Bad that we need a workaround... We shouldn't need one. The package maintainer isn't active enough. :(

Thanks!  :guitar:

---

### Post by tlu on 2009-08-22
> **Pjotr123 said:**
> I have requested the attention of the MOTU's for this grave and serious matter: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559/comments/22](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559/comments/22)

I will keep you posted about the sequel.

No reaction so far. Very sad and disappointing, indeed :(

---

### Post by herbertportillo on 2009-08-22
Thanks, leoquant.

herbert@herbert-desktop:/$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.1-b02, mixed mode)
herbert@herbert-desktop:/$

---

### Post by DominaDoom on 2009-08-22
I can't get Terminal to cd my Desktop

```
stephieweffie@stephieweffie-laptop:/opt/java$ cd Desktop
bash: cd: Desktop: No such file or directory

```

Does anyone know why this could happen?

---

### Post by Johan! on 2009-08-22
You have to go to your home folder first.
You can do this by typing just "cd".

So:

```
cd
cd Desktop
sudo mv ... 
```
and so on.

---

### Post by Pjotr123 on 2009-08-23
Bad news:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559/comments/38](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559/comments/38)

This really spoils my day. The only option left to us, is updating manually. And checking regularly, if Sun has made a new JRE version, because we have no automatic notification of updates. Heck, even Windows has *that*. :evil:

---

### Post by Pjotr123 on 2009-08-24
On Launchpad, I've proposed two different solutions to this major security problem:

> The thing is, that most Ubuntu desktop users won't know about the need for a manual update of JRE. I've done it already, my machines are secure. But I'm an exception.

May I therefore suggest two other possible approaches, both of which provide good security and both of which are simple:

1. Provide *untested* JRE security updates, which though untested for stability, are at least secure. Issue a warning that they haven't been tested for stability. Better to have untested JRE packages on your machine which are secure, than stable but insecure JRE packages.

This can be achieved by simply making the JRE packages in the development branch (right now: Karmic), available for the stable Ubuntu versions (right now: Hardy, Intrepid and Jaunty).

2. Remove JRE entirely from Multiverse, and only provide OpenJDK. OpenJDK is a Universe package and is being kept secure. When people want JRE anyway, then they are forced to download and install it manually. Therefore they will know that they have to periodically *update* JRE manually as well. They are aware of the risk then.

My favourite solution is number 1. JRE is being made by Sun; a good quality package, made by a big professional company. Not likely to disrupt your system, even if you haven't tested it for Ubuntu.

I hope this will help to find an adequate solution.

---

### Post by Pjotr123 on 2009-08-29
Hurray! :D

Updates for Sun Java JRE have been made available in Proposed, currently only for Hardy, Jaunty and Karmic (not for Intrepid). I advise everyone to activate Proposed *temporarily*, and install the updates for Sun Java 6 from it.

Note: don't install the other Proposed updates! They are still unstable. Deactivate Proposed immediately after installing the Sun Java update.

Proposed can be activated as follows: System - Administration - Software sources - tab Updates - Ubuntu updates: check the box of Proposed.

Please provide test reports here:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426)

---

### Post by Pjotr123 on 2009-10-19
In Karmic, JRE will receive no updates (the current outdated package in the software sources will probably be removed).

I've created a how-to for manual installation of JRE in Karmic:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Not so difficult, luckily. :-)

---

### Post by XCan on 2009-10-19
Wow, didn't know that they decided to dump JRE. Luckily, it's not too hard, especially not to add JRE on a single user account. OpenJDK good alternative? Not even Jabref runs flawlessly on it, neither imageJ, Matlab (gui), Comsol (gui), Sweet Home 3D. I wonder actually which apps do run as they're supposed to. But now I'm drifting off. :)

---

### Post by Soul-Sing on 2009-10-19
Ok pjotr. 
Important in your howto is the java-symlink, good job, and thx.

---

### Post by Pjotr123 on 2009-10-19
> **leoquant said:**
> Ok pjotr. Afaik software in the opt "folder", can be deleted without the sudo or gksudo nautilus command.
Important in your howto is the java-symlink, good job, and thx.

Dank je. :)

Ook beschikbaar in het Nederlands (uitgebreider, ook voor 64-bits): [http://sites.google.com/site/computertip/java](http://sites.google.com/site/computertip/java)

Terzijde: leuk dat je hier reageert. Ben je van plan om nog eens terug te keren op de oude stek van Ubuntu-NL, of heb je daar voorlopig even geen zin meer in?

---

### Post by Pjotr123 on 2009-10-20
I'll start a new topic, because this topic title is no longer correct. The current JRE version is update 16, not 15 anymore.

---

