---
title: "Making  a deb package for JDownloader"
date: 2009-11-07
forum: The Cafe
---

### Post by infestor on 2009-11-07
first off, i have no experience in writing/making deb packages. i use jdownloader as my favorite download manager. but it is written in java and sucks in performance (tried on couple of PCs). so i was wondering if making a deb package for jdownloader makes sense at all in order to improve the performance?

---

### Post by Frak on 2009-11-07
If it's poor now, it'll be poor later. DPMS doesn't affect performance, thankfully.

---

### Post by FuturePilot on 2009-11-07
Packaging it into a deb isn't going to do anything for performance. deb packages are just a way to distribute software, nothing more.

---

### Post by Xbehave on 2009-11-07
It will not help, however look into speeding up your java, if jDownloader is java based.

---

### Post by Frak on 2009-11-07
> **Xbehave said:**
> It will not help, however look into speeding up your java, if jDownloader is java based.
Nothing that a rewrite couldn't fix.

---

### Post by infestor on 2009-11-07
> **Frak said:**
> Nothing that a rewrite couldn't fix.

a rewrite? what do u mean by that?

---

### Post by Frak on 2009-11-07
> **infestor said:**
> a rewrite? what do u mean by that?
Take the source and rewrite it from scratch so it doesn't run so terribly.

---

### Post by infestor on 2009-11-07
> **Frak said:**
> Take the source and rewrite it from scratch so it doesn't run so terribly.

wish i had sufficient java & c skills to rewrite the application :(

for now i guess i will have to bear its clumsiness

---

### Post by Frak on 2009-11-07
> **infestor said:**
> wish i had sufficient java & c skills to rewrite the application :(

for now i guess i will have to bear its clumsiness
[http://www.headfirstlabs.com/books/hfjava/](http://www.headfirstlabs.com/books/hfjava/)

Very easy to read. Takes advanced concepts and gives them to you in easy to understand pictures.

---

### Post by Xbehave on 2009-11-07
> **infestor said:**
> wish i had sufficient java & c skills to rewrite the application :(

for now i guess i will have to bear its clumsiness
I'd look into your java setup perhaps installing the latest sun provided java will speed things up

---

### Post by vexorian on 2009-11-07
a deb package would help in a regard, usually Java apps start with a very small memory limit, if I remember correctly, jDownloader needs -xms512 to work in its command line arguments, and making a deb package for it so that it calls it with this argument automatically would be a good idea.

---

### Post by Xbehave on 2009-11-07
> **vexorian said:**
> a deb package would help in a regard, usually Java apps start with a very small memory limit, if I remember correctly, jDownloader needs -xms512 to work in its command line arguments, and making a deb package for it so that it calls it with this argument automatically would be a good idea.
how would you make a deb pacakge do that?
It'd be easier to just alias it.

```
echo 'alias jDownloader="jDownloader -xms512"' >> .bashrc
```

---

### Post by vexorian on 2009-11-07
Easier for you and me. A .deb package would bother setting that stuff up for normal users.

---

### Post by infestor on 2009-11-07
> **Xbehave said:**
> how would you make a deb pacakge do that?
It'd be easier to just alias it.

```
echo 'alias jDownloader="jDownloader -xms512"' >> .bashrc
```

i checked jd.sh and it seems that it already does -xms512 (or not?): 

```
#!/bin/bash
#JD Installer/Starter Version 0.2
#by Jiaz(JD-Team), jiaz@jdownloader.org
#You need at least:
#1.) bash (its a bash script ;) )
#2.) wget 
#3.) Java Version >= 1.5 (OpenJDK works also in latest Version)

#How to use this?
#1.) chmod +x jd.sh
#2.) Place it anywhere you want
#3.) Running jd.sh for the first time will install and setup JD into JDDIR folder
#4.) Running jd.sh after the first time will start JDownloader directly

#Parameters
# update (will perform an update)

#JD Installation folder (adjust to your needs)
JDDIR=~/.jd
#default path to our install/update tool (DO NOT Change this)
JDINSTALLER=http://update0.jdownloader.org/jdupdate.jar

if [ -e $JDDIR ]
then
if [ "$1" = "update" ]
then
if [ -e $JDDIR/jdupdate.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar jdupdate.jar
exit
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi
fi
if [ -e $JDDIR/JDownloader.jar ]
then
echo "JD Installation found: Starting JD now"
cd $JDDIR
#java -Xmx512m -jar JDownloader.jar --add-links $1 $2 $3 $4 $5 $6 $7 $8 $9
java -Xmx512m -jar JDownloader.jar
exit
else
echo "JD Installation found: No valid JDownloader.jar exist!"
fi
if [ -e $JDDIR/jdupdate.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar jdupdate.jar
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi
else
echo "Download/Start JD-Installer"
mkdir $JDDIR
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi
```

---

### Post by www.rzr.online.fr on 2010-03-21
hi
so did anyone try to package it ? any url of tracker or dsc ?
-- 
[http://rzr.online.fr/q/itp](http://rzr.online.fr/q/itp)

---

