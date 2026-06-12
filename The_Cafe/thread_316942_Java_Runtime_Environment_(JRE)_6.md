---
title: "Java Runtime Environment (JRE) 6"
date: 2006-12-11
forum: The Cafe
---

### Post by yopnono on 2006-12-11
It's out now:
Java Runtime Environment (JRE) 6

[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

---

### Post by K.Mandla on 2006-12-11
I wonder if -- or when -- it will hit the repositories?

---

### Post by hanzomon4 on 2006-12-11
How do you install with out the .deb, Also will this java make java apps "faster" the current one drags *** with apps like azureus

---

### Post by kuja on 2006-12-11
hanzomon4:

Download the .bin file to your home folder, then, pull up the ever-handy shell:

```

chmod +x j??-6-linux-*.bin
sudo ./j??-6-linux-*.bin
sudo cp j??1.6.0 /usr/lib/jvm/java-1.6.0-sun
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-1.6.0-sun/jre/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/java-1.6.0-sun/jre/bin/java

```

I'd think that would be copy and pastable. I'd think, what a silly thing to do.

---

### Post by Polygon on 2006-12-11
i cant wait until java comes preinstalled in ubuntu and other distros now that it is open sourced

but this will hold me over for now

---

### Post by Boris2 on 2006-12-12
> **Polygon said:**
> i cant wait until java comes preinstalled in ubuntu and other distros now that it is open sourced
AFAIK java 6 isn't open sourced, the opened the java 7 tree.

Anyway, as long as some important parts are missing (I'm thinking of the whole classpath) it would be senseless to include the opened java.

So I think it'll take a long time for open source java to hit the repos.

Edit: I used [this](http://ubuntuforums.org/showpost.php?p=1307829&postcount=14) to install it. Worked great with the correct filename.

---

### Post by GarethMB on 2006-12-13
It'd be nice if someone who's done this can write a shell script :)

---

### Post by Kimm on 2006-12-13
Does anyone experiance any performance gain using Java 6?

---

### Post by Boris2 on 2006-12-14
> **Kimm said:**
> Does anyone experiance any performance gain using Java 6?
I havenät tested, but there should be, because HotSpot was signifantly improved:
[http://weblogs.java.net/blog/opinali/archive/2005/11/mustangs_hotspo_1.html](http://weblogs.java.net/blog/opinali/archive/2005/11/mustangs_hotspo_1.html)

> **GarethMB said:**
> It'd be nice if someone who's done this can write a shell script :)
Download [this](http://ubuntuforums.org/attachment.php?attachmentid=21024&stc=1&d=1166087751) patch. (**No guarantee for this to work, use at your own risk**)
```
cd /usr/share/java-package/
sudo patch -p 1 </path/to/java-package_mustang.txt
cd
fakeroot make-jpkg jdk-6-linux-i586.bin
sudo dpkg -i sun-j2sdk6.0_6.0.0_i386.deb
sudo update-alternatives --config java
sudo update-alternatives --config javac
sudo update-alternatives --config jar
# etc
```

---

### Post by fede on 2006-12-14
Following Kuja's procedure, I did some minor changes to the steps in his code that didn't work for me. This is the code that I used:

```

chmod +x j??-6-linux-*.bin
sudo ./j??-6-linux-*.bin
sudo mkdir /usr/lib/jvm
sudo mkdir /usr/lib/jvm/java-1.6.0-sun
sudo cp j??1.6.0 /usr/lib/jvm/java-1.6.0-sun/jre -r
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-1.6.0-sun/jre/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/java-1.6.0-sun/jre/bin/java
java -version

```

You will have to accept sun's license. 
This worked fine in a clean Edgy install. Thanks Kuja for your help!

---

### Post by sabitha on 2006-12-22
> **fede said:**
> Following Kuja's procedure, I did some minor changes to the steps in his code that didn't work for me. This is the code that I used:

```

chmod +x j??-6-linux-*.bin
sudo ./j??-6-linux-*.bin
sudo mkdir /usr/lib/jvm
sudo mkdir /usr/lib/jvm/java-1.6.0-sun
sudo cp j??1.6.0 /usr/lib/jvm/java-1.6.0-sun/jre -r
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-1.6.0-sun/jre/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/java-1.6.0-sun/jre/bin/java
java -version

```

You will have to accept sun's license. 
This worked fine in a clean Edgy install. Thanks Kuja for your help!
 didnt work :(
admini@ubuntu:~$ java -version
bash: java: command not found

---

### Post by foureight84 on 2006-12-22
does this new version fix that blank app screen in java apps that uses swing when running beryl?

---

