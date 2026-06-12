---
title: "Java 6 Update 2"
date: 2007-07-06
forum: Repositories &amp; Backports
---

### Post by samjh on 2007-07-06
Just wondering what the release schedule is for Java 6 updates?

We've skipped update 1, and update 2 has just been released.  Are there any plans to bring to the sun-java6-* packages up to date, or is this going to be put off until the Gibbon release?

---

### Post by DarkStarAeon on 2007-07-13
Yeah I'd really like to install update 2 for Java 6 since there is a security patch in it. Can't find any info on how to install it.

---

### Post by Gausian on 2007-07-15
check the java website......they have instructions there

---

### Post by DarkStarAeon on 2007-07-15
Tried that first. didn't work out. That's why I was wondering if there was a better way to do it.

---

### Post by randiroo76073 on 2007-07-16
Try using Automatix2, I think that'll get you the current Java :)
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by DarkStarAeon on 2007-07-16
Ah cool, thanks :)

---

### Post by growltiger on 2007-07-18
Whether I use synaptics or automatix2 or just apt-get, I do not get this version of Java:  1.6.0_02 (build 1.6.0_02-b05).  Instead, I always get 1.6.0 (build 1.6.0-b105).

If I try to make-jpkg from the Sun download, I get this result:

$ fakeroot make-jpkg jdk-6u2-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.ggLoS25962
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done

Any ideas on how to fix this?

---

### Post by growltiger on 2007-07-19
I found that if I took rev 31 of java-packages (found here: <https://launchpad.net/ubuntu/gutsy/+source/java-package/0.31>, I could install Java 6u2.

---

### Post by DriftingDutchman on 2007-07-20
Could you please let us know how to install rev 31 of java-packages as you suggested?

---

### Post by Asham on 2007-07-24
I was under the impression that the applications in the repository lists were to be automatically updated every once in a while. That appears to apply to some of the apps while others are left out. What is the deciding factor and what can be done to improve the current situation?

---

### Post by smartboyathome on 2007-07-24
The apps in Universe are only updated if they have a maintainer in the community. Same with Multiverse. If anyone wants this package, they will have to compile and subit it. Then (if they want) they can maintain it and keep Java up to date.

---

### Post by Asham on 2007-07-24
Ok, I didn't know that. Does it mean anyone can contribute - could I (if I had more knowledge)? Linux is feeling a little foreign to me still and I know I am not *there* yet, but  if I would want to read more about this, where would I start?

---

### Post by smartboyathome on 2007-07-24
If you want to start packaging, you should try the [debian new maintainer's guide]("http://www.debian.org/doc/maint-guide/") or [the ubuntu packaging guide]("http://doc.ubuntu.com/ubuntu/packagingguide/C/") (personally I would go with the ubuntu one). Both have the same info, they are just worded differently.

---

### Post by Seisen on 2007-07-24
> **samjh said:**
> Just wondering what the release schedule is for Java 6 updates?

We've skipped update 1, and update 2 has just been released.  Are there any plans to bring to the sun-java6-* packages up to date, or is this going to be put off until the Gibbon release?

As of right now they are sitting in the Gutsy repo's so they may not be put into the Feisty repos but who knows.

---

### Post by eitan on 2007-07-31
that kind of sucks.  given that they had mr shuttleworth on stage last year at javaone saying that sun and ubuntu would work together to bring the latest java to the ubuntu platform.

it's kind of sad that they can't muster the resources necessary to keep java up to date in the repositories.

it's nice that they're up to date in the gutsy repository but it's no excuse for not putting them in the feisty repo's.  actually it makes it worse:  it means someone already did the work of packaging java6u2 but didn't bother to update feisty.  that really sucks.  sorry for the bad karma.

/ eitan

---

### Post by DriftingDutchman on 2007-08-01
Especially since the version in feisty has security issues and from personal experience I can say major memory leaks as well.

---

### Post by Chudilo on 2007-08-01
So as far as you know, no one is working on creating a build of Java 6.0.1 for Feisty just because Sun's bin file can easily be converted to a deb , and then installed.
Even though it is known that it is required to get Java applications to be displayed in Compiz properly. What happened to the "linux for human beings" thing? Or has this come out of Suns promise to ensure full compatibility with Ubuntu, and people are waiting for sun to provide a special link for an Ubuntu specific .deb ?

Any insight into the situation will be appreciated.

---

### Post by DriftingDutchman on 2007-08-02
I would like to use Java 6 on a Ubuntu production server soon-ish. Normally Sun's VM's are pretty good, but this time they messed up with 1.6.0.0. So now I am left with a few bad options:

-Use Feisty's version: the VM _will_ crash after a while due to memory leaks.

-Use Alien to repackage Sun's rpm: no idea whether it will subtly break things, and I have seen several claims that it is a bad idea.

-Use Sun's .bin file: no idea whether it will subtly break things.

-Change distros: I would rather stay with Ubuntu and it's also the one I know best.

-Try to package my own .debs: no idea whether it will subtly break things.

-Try to use Gutsy's repositories: add them to the repository list, do an update, install the Java6 packages, remove the Gutsy repository lines: no idea whether it will subtly break things now or messes up my package management enough to no longer support some future Feisty updates.

I would guess that the last option is best.. that is - if I knew (for sure) what I was doing..

Any help would be appreciated.

---

### Post by Seisen on 2007-08-02
The last option isn't good because you should never mix repo's like that, it will cause major headaches.

---

### Post by VFiend on 2007-08-02
See security vulnerability at launchpad: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/126059](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/126059)

Basically Sun/Canonical don't seem concerned about bringing security updates to Feisty's Java even though they were trumpeting how great the cooperation was when Feisty was released.

---

### Post by AndriusBurokas on 2007-08-03
Hey everybody, I found pretty cool explanation on how to upgrade from Java 6.0.0 to Java 6.0.2. The provided script is self explanatory, You can use only the needed parts of it, but I can verify that it worked for me :)

Here is the link:
[http://www.osdevel.org/blog/1/240/](http://www.osdevel.org/blog/1/240/)

---

### Post by S1l3nt_Hunt3r on 2007-08-03
> **AndriusBurokas said:**
> Hey everybody, I found pretty cool explanation on how to upgrade from Java 6.0.0 to Java 6.0.2. The provided script is self explanatory, You can use only the needed parts of it, but I can verify that it worked for me :)

Here is the link:
[http://www.osdevel.org/blog/1/240/](http://www.osdevel.org/blog/1/240/)


Thanks! I will try at home.

But before I have some questions: In the script there is this comment:

```
# This script installs and configures the JDK 1.6 Update 2 on your Ubuntu 7.04

```
I don't want to install the JDK, because i don't need it.

Do this script work  for the JVM install process?

---

### Post by AndriusBurokas on 2007-08-03
> I don't want to install the JDK, because i don't need it.

Do this script work for the JVM install process?

Well, the script is talking about JDK only, but also as You know the JDK version includes JRE, so if You will ever want to write a program in Java You'll already have the JDK at your side.

In other words I think it's the best option, we poor Ubuntu users can have - this script makes use of the latest java release, so why not to use it.

P.S. I can verify that it works for Kubuntu too.

---

### Post by Seisen on 2007-08-03
Or you guys can wait two months until Gutsy comes out, patience....................

---

### Post by Chudilo on 2007-08-03
I don't think there are updates in Gutsy that would make the newer version of Java run better? However as far as I know java 6.0.1 is required to display Java Swing components in Compiz properly.

EDIT: Java programs can  be fixed to display properly under Compiz by adding 

"export AWT_TOOLKIT=MToolkit"
Into the script that starts the program, or into /etc/environment to make it global for all Java programs

---

### Post by Asham on 2007-08-03
> **Seisen said:**
> Or you guys can wait two months until Gutsy comes out, patience....................

**Will it not be exactly the same if or when an update is released for Gutsy? Or is the current situation specific for Feisty? I am asking since I have not been around long enough to know for myself.**

I gave the packaging resources that were posted a brief reading but it became obvious that I need to learn the basics much more in detail. I hardly know any commands besides from ls.:lolflag:

---

