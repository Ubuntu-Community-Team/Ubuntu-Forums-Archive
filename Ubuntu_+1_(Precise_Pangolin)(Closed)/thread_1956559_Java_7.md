---
title: "Java 7"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-04-11
G'day;  Got another problem, trying to install oracle java 7 by running the following commands

code.
sudo apt-get purge openjdk*

sudo add-apt-repository ppa:eugenesan/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

But I get the following error 

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone help me please.
Regards Miykel

---

### Post by jfernyhough on 2012-04-11
I'll install it to have a go on mine, but what's wrong with OpenJDK7?

---

### Post by jfernyhough on 2012-04-11
So according to the output on the terminal:

```
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-11 12:18:37--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.45.230.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.45.230.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-11 12:18:38--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|80.239.148.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]

```

Basically, it's downloading a text file. It can't install a text file.

---

### Post by jfernyhough on 2012-04-11
Looking through the .deb postinst it's downloading to /var/cache/oracle-java7-installer

I'm going to try downloading manually from [http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u3-download-1501626.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u3-download-1501626.html) (I think the installer fails because it hasn't accepted the download agreement) then copying jdk-7u3-linux-x64.tar.gz into place. I'll then run $ sudo dpkg --configure -a and hopefully it will find the file already there.

--edit
Nope, it overwrites. Annoying.

--edit 2
That's possibly the worst package ever. Now it won't allow itself to be removed as the pre-removal script triggers an attempt to download and install. Gah.

--edit 3
ppa-purge won't shift it.

---

### Post by jfernyhough on 2012-04-11
I knew I should have checked the PPA page before I installed. Builds have failed since 19th March.

[https://launchpad.net/~eugenesan/+archive/java](https://launchpad.net/~eugenesan/+archive/java)

My advice: do not use this package. Or this PPA.

Now I have to work out how on Earth to get the thing off my system.

---

### Post by Miykel on 2012-04-11
G'Day jfernyhough, Thanks for the replies, I was trying to install Shape Collage and it called for this java, found the solution here;

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

Worked like a beauty, it's all good to expand my own knowledge base.

Regards Miykel

---

### Post by dino99 on 2012-04-11
i'm using the alexander255 ppa to get it, no trouble :)

---

### Post by jfernyhough on 2012-04-11
This is all well and good but I'm still stuck with a broken deb gunking up my system. Unless I can work out how to use the "local" template I guess I'll have to upload the file somewhere, alter the control and preinst files to point to that server, reinstall it, hope it works, then remove it.

What a faff.

---

### Post by jfernyhough on 2012-04-11
OK, so a horrible hack workaround. Replaced the control file in alexander255's oracle-java-installer.deb with that from oracle-java7-installer.deb so it will replace the crap deb. Now I can remove it.

As a side note, alexander255's PPA is for Java 6, not Java 7.

---

### Post by dino99 on 2012-04-11
> **jfernyhough said:**
> OK, so a horrible hack workaround. Replaced the control file in alexander255's oracle-java-installer.deb with that from oracle-java7-installer.deb so it will replace the crap deb. Now I can remove it.

As a side note, alexander255's PPA is for Java 6, not Java 7.

oh, shame on me :(
that one for java7 : ppa:webupd8team/java

---

### Post by hisshadiness on 2012-04-11
> **jfernyhough said:**
> I knew I should have checked the PPA page before I installed. Builds have failed since 19th March.

[https://launchpad.net/~eugenesan/+archive/java](https://launchpad.net/~eugenesan/+archive/java)

My advice: do not use this package. Or this PPA.

Now I have to work out how on Earth to get the thing off my system.

The same thing happened to me :-( Here's how you uninstall the eugenesan java and get a working install:

**Uninstall**
1. cd /var/lib/dpkg/info
2. sudo rm oracle-java7-installer.*
3. sudo dpkg --remove --force-remove-reinstreq oracle-java7-installer

**Install Working Java**
1. sudo add-apt-repository ppa:webupd8team/java
2. sudo apt-get install oracle-java7-installer

Cheers!

---

### Post by jfernyhough on 2012-04-11
Ah ha, nice. That one even works! No more manual update-java for me! :D

> **hisshadiness said:**
> The same thing happened to me :sad: Here's how you uninstall the eugenesan java and get a working install:--snip--Great first post!

---

### Post by adb3 on 2012-04-11
Thanks [hisshadiness]("http://ubuntuforums.org/member.php?u=1610807"), your solution fixed my problem!

---

