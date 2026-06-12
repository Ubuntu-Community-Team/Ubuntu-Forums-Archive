---
title: "Tiny disk image, big machine for developer VM"
date: 2012-12-16
forum: Virtualisation
---

### Post by 1clue on 2012-12-16
Hi, 

I have a need to generate a small-disk-image non-gui 64-bit Linux VM to be run on Mac, Linux or Windows. The current target host is a MacBook Pro with 8g, and that will only go up as time goes by, but for now each of the developers has at least that hardware. The VM guest will be a generic PC-compatible 64-bit Intel box.

I need to run Sun/Oracle Java 6 (non-free) 64-bit, grails 1.3.7, mysql-5.1, sshd and bash, full ipv4/ipv6 support for a normal client. Multiple core support would be a big plus, big memory is necessary. 

I don't think I need a system logger, or authentication. Maybe I need cron, not sure if that's really a system requirement or not. If I could find some tiny distro that would fit, a C compiler would not be necessary. 

If I could make a simple gui then I would throw that on too, maybe blackbox or something, but I think it will be too big. 

The goal is to make a VM whose external image when shut down is 1g or less for the Linux overhead, more for the extra junk we put on. We set it up, get our build working on it and then shut it down, and probably burn the image onto a DVD for posterity. Or transfer it to or from some server or some laptop over the Internet. 

This will be a build-and-forget system, although we will keep the basic image for future similar installations. We are developing custom software on the Java platform. Each customer has a slightly (or not-so-slightly) different build. We've been tagging this in source control, but the problem is we get the customer coming back for a change two years after the installation, and we no longer have a development environment for them at that point. We have the source, just not a working build environment. 

Does somebody know of a tiny distro that already can accomplish this? I'm on the verge of trying to build it with Gentoo, but I would like a low-maintenance solution.

---

### Post by craigp84 on 2012-12-16
There's an official ubuntu "JEOS" distribution, it's trimmed down and designed exclusively to run as a guest OS in a virtualised environment.

Installing the oracle JVM on a vanilla ubuntu install is easy:

[LIST=1]
[*] Download the latest jdk from Oracle in .tar.gz format
[*] Extract the archive with tar xzvf jdk.XXX.tar.gz
[*] Move the JDK into the correct place for Ubuntu: ```
sudo mkdir /usr/lib/jvm
``` then  ```
sudo mv jdkXXXX /usr/lib/jvm
```
[*] Update the alternatives system to reflect the newly installed JDK. There were too many commands to do manually so i created a for loop in bash which filters out only the commands i wanted to register with the system:
```

    for cmd in /usr/lib/jvm/jdk1.7.0_09/bin/[jkpr]*; do
        cmd=$( basename $cmd )
        echo "Registering $cmd with the system alternatives mechanism..."
        sudo update-alternatives --install /usr/bin/$cmd $cmd /usr/lib/jvm/jdk1.7.0_09/bin/$cmd 1
    done

```
[/LIST]

I used ```
java -version
``` and ```
javac -version
``` to confirm these were
setup correctly.

If this is not the only JDK installed on your Ubuntu server, you may run into
an unexpected version being returned in the above test, in that case you can
invoke ```
sudo update-alternatives --config java
``` and repeat for each command
(you could alter the above for-loop).

Of course, this is all a bit crappy doing manually. Better options exist: package the jvm yourself, or use something like puppet to orchastrate the install & other configuration of the machine(s)

---

### Post by 1clue on 2012-12-16
craigp84,

Been there, done that on the Java installation.  I was just looking for a skin and bones distro that's as small as possible.

I'll give it a whirl.

Thanks a bunch.

---

### Post by memilanuk on 2012-12-17
Have you looked @ Turnkey Linux?  They have a variety of VM images (were Ubuntu based, now I think Debian), including a JeOS one...

[www.turnkeylinux.org](www.turnkeylinux.org)

---

### Post by 1clue on 2012-12-17
I've spent the weekend downloading and installing just about every current micro distro that has any hope of meeting my needs.

JeOS 12.04 is the smallest after I installed all my tools by a significant margin.

I did NOT try Gentoo.  Too much time to install IMO.

BTW, the JeOS build is the Ubuntu Server iso, I then go into the options to find a minimal build specifically for VMs.

Thanks.

---

