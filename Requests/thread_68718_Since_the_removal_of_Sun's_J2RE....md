---
title: "Since the removal of Sun's J2RE..."
date: 2005-09-24
forum: Requests
---

### Post by PaganHippie on 2005-09-24
... any chance we'll see the inclusion of a Java VM that supports Azureus?  I miss it.

---

### Post by Ubunted on 2005-09-28
The new easiest way to install Java now:

1. [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

2. Download Linux self-extracting file jre-1_5_0_04-linux-i586.bin (or whatever the file is) 15.83 MB

3.
```
sudo apt-get install fakeroot java-package
```


4.
```
sudo fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```
or
```
sudo fakeroot make-jpkg jre-*
```
or
```
sudo fakeroot make-jpkg jdk-*
```


5.
```
sudo dpkg -i *.deb
```

---

### Post by PaganHippie on 2005-09-28
I'll give that a try, thanks.

[edit]

Everything seems OK until I try to make the .deb package.  I get a string of error messages:

/home/angus/jre-1_5_0_05-linux-i586.bin: line 285: /etc/mailcap: Permission denied
cp: cannot remove `/usr/share/pixmaps/sun-java.png': Permission denied
cp: cannot remove `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': Permission denied
cp: cannot remove `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': Permission denied
cp: cannot remove `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 433: /usr/share/mime-info/java-archive.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 434: /usr/share/mime-info/java-archive.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 435: /usr/share/mime-info/java-archive.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 436: /usr/share/mime-info/java-archive.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 437: /usr/share/mime-info/java-archive.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 438: /usr/share/mime-info/java-archive.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 441: /usr/share/mime-info/java-archive.mime: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 442: /usr/share/mime-info/java-archive.mime: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 445: /usr/share/application-registry/java-archive.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 446: /usr/share/application-registry/java-archive.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 447: /usr/share/application-registry/java-archive.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 448: /usr/share/application-registry/java-archive.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 449: /usr/share/application-registry/java-archive.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 450: /usr/share/application-registry/java-archive.applications: Permission denied
cp: cannot remove `/usr/share/pixmaps/sun-java.png': Permission denied
cp: cannot remove `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': Permission denied
cp: cannot remove `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': Permission denied
cp: cannot remove `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 433: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 434: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 435: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 436: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 437: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 438: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 441: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 442: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 445: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 446: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 447: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 448: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 449: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/angus/jre-1_5_0_05-linux-i586.bin: line 450: /usr/share/application-registry/java-web-start.applications: Permission denied

Any ideas?

---

### Post by Jenda on 2005-09-28
EDIT: Ummm I'm having trouble with the deb package.
>  jenda@niniel:~$ fakeroot make-jpkg /home/jenda/Desktop/jre.bin
Creating temporary directory: /tmp/make-jpkg.XXXXhhhWMr
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
I don't think one was created

---

### Post by Jenda on 2005-09-28
OK - I managed in the end.

---

### Post by Kyral on 2005-09-28
Someone should look into compiling Azureus' source code (Yes you can compile Java into a binary that doesn't need the RE)

---

### Post by Ubunted on 2005-09-28
"Permission Denied" messages usually mean you're not running as root. I guess there should be a "sudo" in front of those fakeroot commands.

---

### Post by darkmatter on 2005-09-28
[QUOTE=Ubunted]I guess there should be a "sudo" in front of those fakeroot commands.[/QUOTE]

Yes, there should be.

---

### Post by PaganHippie on 2005-09-29
Hmm, when I tried that it complained:

angus@Talisker:~$ sudo fakeroot make-jpkg jre-*
You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.


What if I ran it from 'root terminal' & left off 'sudo' and 'fakeroot'?

---

### Post by manicka on 2005-09-29
I have azureus 2.3.0.4 (GTK version form the main site) working well with the jre 1.4 version that comes with breezy. At the first startup it complained about 1.5 not being installed. It then downlaoded some updates and has run without any error messages since. I don't really like azureus and prefer bittornado, but it seems to be working okay.

---

### Post by PaganHippie on 2005-09-29
Well, I *am* planning to upgrade to Breezy (though I intend to wait for the 'official' release), so perhaps in a couple of weeks this will be a non-issue.

---

### Post by PaganHippie on 2005-09-30
Just a thought -- would d/l-ing Sun's .rpm file and installing J2RE using alien work?  Anyone?

---

### Post by tseliot on 2005-09-30
here's a guide about making your java package:

[http://ubuntuforums.org/showthread.php?p=378870&posted=1#post378870]("http://ubuntuforums.org/showthread.php?p=378870&posted=1#post378870")

---

### Post by jdong on 2005-09-30
1) java-package is the correct method -- that's how Backports Java packages were made, in fact!

2) No sudo is necessary for any command except dpkg -i during install -- just "fakeroot make-jpkg" is good.

---

### Post by PaganHippie on 2005-09-30
I've tried this several times now.  It appears to go smoothly enough (though see below), but after the install, when I try to verify that it worked, I get:

angus@Talisker:~$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
angus@Talisker:~$

While building the .deb, I get a series of 'permission denied' error messages.  I assume that this is not normal.

As a last resort, could I possibly persuade someone who has done this successfully to email me a copy of the correct .deb file?  Much as I dislike the idea of posting an email address in a public forum, I'm getting desperate.

---

### Post by PaganHippie on 2005-10-01
For what it's worth, I solved my problem by simply installing JRE directly from Sun's .bin file into a directory under my own $HOME, installing Azureus directly from the SourceForge download in the same manner, and configuring Azureus by hand. It works beautifully now, and the only 'problem' is that apt-get/Synaptic doesn't know that I have either Java or Azureus installed, which troubles me not at all.

Thanks again for all the help & suggestions, though.  :)

---

### Post by Ubunted on 2005-10-02
So what exactly is stopping Sun from offering that very .deb package for download from their site, thereby saving me and many others a LOT of grief?

I swear, Java has caused me more headaches with Ubuntu than anything else combined. The installation instructions they provide NEVER work for me. I finally remembered to save the .deb on my USB key, but really, it has GOT to be made easier than this!

---

### Post by PaganHippie on 2005-10-02
[quote=Ubunted]So what exactly is stopping Sun from offering that very .deb package for download from their site, thereby saving me and many others a LOT of grief?
[/quote]

Uhm... just a guess, but perhaps nobody has *asked* them to offer a .deb file?  They do have a .rpm, after all....

Maybe, if enough of us flood them with requests for a .deb, we can resolve this issue once and for all.  Whatcha think?

---

### Post by fredricsolstad on 2005-10-05
Yeah.. thats an idea.. I for one am going to send a request to them now to release a .deb version...

---

### Post by Velvet Elvis on 2005-10-06
Does the same method work for the JDK and JDK + netbeans package?

---

### Post by Jenda on 2005-10-06
You can download a .deb somewhere... just gimme a few minutes and I'll find it.

---

### Post by dakira on 2005-10-24
[QUOTE=Kyral]Someone should look into compiling Azureus' source code (Yes you can compile Java into a binary that doesn't need the RE)[/QUOTE]

I did that and I have to tell you that even with the latest GCJ it is not possible to compile Azureus binaries since Azureus uses (alot of) classes not ported to GCJ. Early versions of Azureus use only a few classes not in GCJ but still you'd have to rewrite these parts of Azureus to get it compiled.

So I stopped looking into it, sorry..

---

### Post by coldrick on 2005-10-25
Just a warning: you should *not* be using sudo in front of fakeroot when creating the java .deb: if you want details on how to get Java properly installed, take a look at [http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part](http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part)

Regards,
David

---

### Post by gdlx on 2005-11-17
I have been trying to follow the instructions carefully but seem to be stuck at the beginning.

gdlx@traveler:~$ sudo apt-get install fakeroot java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
gdlx@traveler:~$

What am I not doing?:confused: :confused: 

Thanks for all the help.

---

### Post by pertti on 2005-11-17
It seems that you don't have the multiverse repository enabled. java-package is in the multiverse repository, which is not enabled by default. You can enable it [modifying the /etc/apt/sources.list]("https://wiki.ubuntu.com/AddingRepositoriesCliHowto) config file, or [using synaptic]("https://wiki.ubuntu.com/AddingRepositoriesHowto).

---

### Post by vassie on 2005-11-18
Add the PLF repository from [this]("http://wiki.ubuntu-fr.org/doc/plf") page to your sources.list

Install Java 1.5

```
sudo apt-get install sun-j2re1.5
``` 
Then set it as the default Java VM

```
sudo update-alternatives --config java
``` 
Ben

---

### Post by bsm0f0 on 2005-11-18
ahh sweet, thanks man.

---

