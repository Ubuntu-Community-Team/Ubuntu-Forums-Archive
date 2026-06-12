---
title: "Java builds"
date: 2014-05-03
forum: Virtualisation
---

### Post by spacerocket on 2014-05-03
Hello,

I use saucy salamander (13.10) and want to have java. I found this:

[https://launchpad.net/ubuntu/+source/openjdk-6](https://launchpad.net/ubuntu/+source/openjdk-6)

Should I choose [6b31-1.13.3-1ubuntu1~0.13.10.1]("https://launchpad.net/ubuntu/+source/openjdk-6/6b31-1.13.3-1ubuntu1%7E0.13.10.1") or [             6b27-1.12.6-1ubuntu2]("https://launchpad.net/ubuntu/+source/openjdk-6/6b27-1.12.6-1ubuntu2")?

Then compile the tar file?

Anyway I should use OpenJDK-packages because Oracle is not available I think.

Is there another way to install these packages, for example:

```
sudo apt-get install icedtea-6-plugin
```

---

### Post by sammiev on 2014-05-03
Depends how you will be using Java that you may need Oracle Java. [This]("http://www.webupd8.org/2014/03/oracle-java-8-stable-released-install.html") is a great read and updates itself as required. It's great for gaming programs if that is what you are looking to do.

---

### Post by ajgreeny on 2014-05-03
Why do you want the openjdk-6 version of those packages instead of the openjdk-7 version which I am sure is in the repos of 13.10?

---

### Post by spacerocket on 2014-05-03
[http://www.freechess.org/Login/jin/index.php](http://www.freechess.org/Login/jin/index.php)

Do I need oracle for that?


For Jin officially supported platforms are Microsoft Windows, Mac OS X and  [COLOR=#ff0000]Linux[/COLOR], although Jin should work on any operating system with a modern [Java Runtime Environment]("http://www.java.com") (1.4 or later).                 

[http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)

Maybe Linux x64 is enough

---

### Post by sammiev on 2014-05-03
> **spacerocket said:**
> [http://www.freechess.org/Login/jin/index.php](http://www.freechess.org/Login/jin/index.php)

Do I need oracle for that?


For Jin officially supported platforms are Microsoft Windows, Mac OS X and  [COLOR=#ff0000]Linux[/COLOR], although Jin should work on any operating system with a modern [Java Runtime Environment]("http://www.java.com") (1.4 or later).                 

[http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)

Maybe Linux x64 is enough

The link you provided recommends Oracle Java.

---

### Post by spacerocket on 2014-05-04
I downloaded the tar file from here: [https://www.java.com/en/download/linux_manual.jsp?locale=en](https://www.java.com/en/download/linux_manual.jsp?locale=en)   and should be oracle.

Then I made a directory java (In Home) and moved the tar-file there and extracted. Then I did

```
$ cd java/jre1.7.0_55/
```

Then I typed **install** -> /java/jre1.7.0_55$ install
install: missing file operand

---

### Post by QIII on 2014-05-04
Hello!

Please make this easier on yourself.  There is a PPA at webupd8.org that does all of the downloading, installing and set up for you with three commands in the terminal.  The beauty of using that PPA is in the fact that as Oracle makes updates to Oracle Java, the PPA is updated and you will get automatic updates as you do your normal updates.

sammiev pointed you to webupd8's Oracle Java 8 installer.  I would recommend Oracle Java 7, since 8 is not yet a final release.  But the point is the same:  make this easy on yourself and don't beat your head against a wall.

Again:  Please see [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) for the *easiest possible way* to install Oracle Java.

---

### Post by sammiev on 2014-05-04
> **QIII said:**
> Hello!

Please make this easier on yourself.  There is a PPA at webupd8.org that does all of the downloading, installing and set up for you with three commands in the terminal.  The beauty of using that PPA is in the fact that as Oracle makes updates to Oracle Java, the PPA is updated and you will get automatic updates as you do your normal updates.

sammiev pointed you to webupd8's Oracle Java 8 installer.  I would recommend Oracle Java 7, since 8 is not yet a final release.  But the point is the same:  make this easy on yourself and don't beat your head against a wall.

Again:  Please see [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) for the *easiest possible way* to install Oracle Java.

+1

---

### Post by spacerocket on 2014-05-04
Thanks for help.

Now I have Oracle java 7. [http://www.jinchess.com/unix_download](http://www.jinchess.com/unix_download)  

There is said "On a reasonably modern distro, simply unpacking the .tar.gz file and  double-clicking the "jin" file inside the resulting directory should  work"

Now does this mean that this would connect me automatically to freechess.org? I want to be able to connect to freechess by double-clicking the Jin-file. When I double click jin inside** jinchess/jin-2.14.1** there is:

```
#!/bin/sh

# Java command
JAVA_CMD=java

# Check if GCJ
$JAVA_CMD -version 2>&1 | grep -i -q "gcj\|gnu\|gij"
if [ $? -eq 0 ]
then
    echo "You seem to be running GNU's Java implementation, which is incomplete."
    echo "Jin requires Sun's Java (or a fully compatible version) 1.4 or later."
    echo "If you can't install it with your distribution's package manager, you"
    echo "can obtain and install it manually from http://www.java.com"
    exit
fi

# Follow links
filename=`readlink -f $0`
if [ -z "$filename" ]
then
    filename=$0
fi

# Change to Jin's directory - Jin needs to be run from its directory
cd `dirname $filename`

# Run Jin
$JAVA_CMD $JAVA_OPTS -jar jin.jar $*
```


I don`t want to connect to FICS with **CD jinchess/jin-2.14.1 ./jin**. (NOTE I CREATED JINCHESS DIRECTORY AND EXTRACTED THE TAR-FILE INSIDE THAT) =)

If there is that way I described above or at least possibility to create shortcut somewhere would be OK.

---

### Post by sammiev on 2014-05-04
Post #7 has it all. Delete or uninstall all other java versions. Sun's Java and Oracle Java is the same.

---

### Post by QIII on 2014-05-04
Just so this makes some sense:  The Ravenous Monstoracle ate Sun.  Sun is no more.  The Sun brand now belongs to Oracle.

---

### Post by spacerocket on 2014-05-05
"Delete or uninstall all other java versions."

How?

[B]
"You can also  create a symlink to the jin script in your ~/bin directory[/B]"   

How? I would expect something like

n -s /<full>/<path>/<to>/<file> /usr/local/bin

What if I want to create that symlink inside jin-2.14.1 directory?

---

