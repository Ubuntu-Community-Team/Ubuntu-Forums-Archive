---
title: "Need JRE"
date: 2005-05-18
forum: The Cafe
---

### Post by 1337sithlord on 2005-05-18
Okay Sun Java isnt working on here, and I need some Java runtime environment for Ubuntu,  Does anyone, have one, or know where to get one?  Im surprised it isnt here cause ubunut comes with some pretty 1337 software already.

---

### Post by pdk001 on 2005-05-18
did u try this way (source is here [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre))

wget -c [http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin](http://frankandjacq.com/ubuntuguide/jre-1_5_0_03-linux-i586.bin)
sh jre-1_5_0_03-linux-i586.bin
sudo mkdir /usr/java
sudo mv jre1.5.0_03/ /usr/java/
sudo chown -R root:root /usr/java/jre1.5.0_03/
sudo ln -fs /usr/java/jre1.5.0_03/bin/java /usr/bin/java
sudo ln -fs /usr/java/jre1.5.0_03/bin/java_vm /usr/bin/java_vm
sudo ln -fs /usr/java/jre1.5.0_03/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
sudo ln -fs /usr/java/jre1.5.0_03/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
java -version

---

### Post by WildTangent on 2005-05-18
ya, me and my friend here have tried that one, the link seems to be broken

-Wild

---

### Post by bored2k on 2005-05-18
Download [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) 
Linux (self-extracting file)(.bin)
```
sudo apt-get install java-common fakeroot java-package build-essential
fakeroot make-jpkg jre-1_5_0_02-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update02_i386.deb
```

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=1337sithlord]?  Im surprised it isnt here cause ubunut comes with some pretty 1337 software already.[/QUOTE]

Thats is because JAVA is tied up by legalities (many restrictions on distrobution).

---

### Post by WildTangent on 2005-05-19
[QUOTE=pdk001]did u try this way (source is here [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre))

sudo mv jre1.5.0_03/ /usr/java/
[/QUOTE]
got to that part, and then it told me that that file doesnt exist :-x 

-Wild

---

### Post by jdong on 2005-05-19
Add the Ubuntu Backports repositories to your sources.list:

[b]
deb  [http://ftp2.caliu.info/backports](http://ftp2.caliu.info/backports) hoary-backports main universe multiverse restricted 
deb  [http://ftp2.caliu.info/backports](http://ftp2.caliu.info/backports) hoary-extras main universe multiverse restricted


[/b]then, run [b]apt-get update && apt-get install sun-j2re1.5

[/b]that'll automatically install Java for you, including Firefox plugins.

---

### Post by WildTangent on 2005-05-19
w00t! it works!

edit: i should add it was the ubuntuguide method that worked. if i had seen your method jdong about 20 minutes earlier, i woulda tried it, but me and my friend both got it working now :)

-Wild

---

### Post by 1337sithlord on 2005-05-19
Yay I got it working too.  I was getting so mad, when wild tangent told me that i had to put it in one line at a time lol.  Apparently the word wrap combines some lines so they dont go through, and thats why it kept not working.  Aaaahh.. well, I'm an idiot.  Lol ty

---

