---
title: "Java 6 JDK"
date: 2008-03-29
forum: Repositories &amp; Backports
---

### Post by nikRbokR on 2008-03-29
Hey.  I'm having trouble with installing the java jdk.  I went and tried to install w/ the synaptic manger, but it didn't work.  Then, according to [this post]("http://ubuntuforums.org/showthread.php?t=722450") I did
```
sudo apt-get update

sudo apt-get install sun-java6-jdk
```

here's the output to the commands:
```
userName@Computer:~$ sudo apt-get update
[sudo] password for userName:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy-updates Release              
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done
userName@Computer:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
```


I downloaded the jdk-ju5-linux-i586-rpm.bin from the sun website... but it doesn't work either.  I'm really confused.  I hope I didn't mess up anything by trying to install by Synaptic Package Manager.

I really need help :(  I'll probably need it for class soon.

---

### Post by marenkar on 2008-03-29
weird, it worked ok in mine

---

### Post by n1kol@! on 2008-04-24
you can download the jdk from sun, which will extract into your home directory. then you have to set up your command line variables, so that if you call java or javac from the command line, the right program is run. i still havent found out how to use java on websites with this method, but that is not a major factor for me.
I hope that helps :)

---

### Post by Jeff250 on 2008-04-24
You need to uninstall the sun-java6-doc package, since this is causing the trouble, and you probably don't really want this anyways.  IDE's like Eclipse will read the javadoc right from the java source files.

---

### Post by Bingulim on 2008-05-12
Go to the normal process of installing the java-6-doc and when it stops at this:
```
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
```

access this site <[http://java.sun.com/javase/downloads/]("http://java.sun.com/javase/downloads/")> and download the Java 6 SE Documentation to the /tmp/ directory. Then, press RETURN.

---

