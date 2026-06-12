---
title: "HOWTO: Install the Java runtime environment"
date: 2005-10-03
forum: Ubuntu Backports
---

### Post by pestie on 2005-10-03
As many of you have noticed, the Java runtime environment (JRE) is no longer available in backports. After complaining about this (I'm such a pathetic whiner!), I was informed that a utility called **java-package** could be used to create an appropriate JRE .deb package. I tried it and it worked, so I thought I'd write a quick HOWTO.

It turns out that the **java-package** package is an extremely handy utility which takes a Java installer file from Sun and repackages it in a .deb file, quickly and painlessly, which can then be installed with **dpkg**. If it's not already installed on your system, install it:
```
sudo aptitude install java-package
```
**java-package** depends on another package called **fakeroot**, which we'll see later. **aptitude** will install this automatically if need be.

You'll need either the Java SDK (if you want to develop Java apps) or the JRE (if you just want to run existing Java apps). You can get the 5.0 version (which I used, as Azureus seems to want it) [here](http://java.sun.com/j2se/1.5.0/download.jsp) or the 1.4.2 version [here](http://java.sun.com/j2se/1.4.2/download.html). The file you actually want is the Linux "self-extracting file" (in my example, **jre-1_5_0_05-linux-i586.bin**). Download this to some convenient location, then open a terminal session in that directory.
Now, make sure you're *not* logged in as root when you do this. You'll get an error if you try this procedure as root. What you're going to do is run the **make-jpkg** command in a "fake root" environment created by the **fakeroot** command. This will keep Sun's installer script from messing with your real system configuration (it apparently likes to mess with stuff in /etc). The actual commands are quite simple. First:
```
fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
```
Replace **jre-1_5_0_05-linux-i586.bin** with the name of the file you downloaded, if you didn't download the same package I did. Follow the prompts (agree to the license agreement, etc.), you'll see a lot of stuff spew across the screen, and at the end you should have a .deb file.

The first time I tried this, I got a bunch of errors you get like, "dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)." Turns out I didn't have gcc installed at all. **sudo aptitude install build-essential** will fix that.

The end result is a file which, in my case, was called **sun-j2re1.5_1.5.0+update05_i386.deb**. So, the next step is to install it:
```
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
```
At this point, Java should be installed. You can check it like this:
```

$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```
And you're done! Now packages that depend on Java, like Azureus, will install correctly. Life is good.

---

### Post by ngms27 on 2005-10-04
I tried this.

The package got built OK, it installed OK but it doesn't work!!!

I find the only option is to install the .bin manually and then point to it via PATH or links.

JonnyT

---

### Post by aetheist on 2005-10-04
When I try this I get 

> david@ubuntu:~$ fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found


---

### Post by NikoC on 2005-10-04
Thanks for this very clearly written how to, works fine for a noob like me!

---

### Post by zac851 on 2005-10-04
I downloaded the 1.4 version and did everything but I came up with this error.

> zac851@linuxbox:~/Desktop$ fakeroot make-jpkg j2re-1_4_2_09-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXtzql6o
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

---

### Post by pestie on 2005-10-04
**ngms27**, what do you mean by "it doesn't work?" If the package installed correctly, **java -version** should show you what version of Java is installed. What's the error message you get instead?

**aetheist**: That just looks like the **java-package** didn't install for some reason. Try **sudo aptitude install java-package**. If it says it's already installed, that's where things get weird.

**zac851**: I didn't run into that myself, but [this thread](http://ubuntuforums.org/showthread.php?t=40887) might help.

**NikoC**: Thanks!

---

### Post by med1972 on 2005-10-04
I ran through all this just fine, built and installed the Sun JDK, but gij is installed and "in the way":
```
mark@kiddo:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
mark@kiddo:~$
```
So I had to remove the gij and gij-4.0 packages. Now Sun's JDK is default:
```
mark@kiddo:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
mark@kiddo:~$
```
Mark

---

### Post by silent_scream on 2005-10-04
when I gave :fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin

Creating temporary directory: /tmp/make-jpkg.XXXX1IJiqm
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done


what's the problem? I read the thread in [http://ubuntuforums.org/showthread.php?t=40887](http://ubuntuforums.org/showthread.php?t=40887)
but I can't understand, cause i'm a new user

---

### Post by Donovan on 2005-10-06
For all who have problems with plugins...

Check if you have "Java-common" package installed. That package is also required to make the java-package procedure work. If not just type in console:

```
sudo aptitude install java-common
```

Then try to run the java-package again as Pestie explained.

---

### Post by bored2k on 2005-10-06
This same trick has been posted before, so please continue it on the other thread.

[http://www.ubuntuforums.org/showthread.php?t=70428&highlight=fakeroot](http://www.ubuntuforums.org/showthread.php?t=70428&highlight=fakeroot)

---

