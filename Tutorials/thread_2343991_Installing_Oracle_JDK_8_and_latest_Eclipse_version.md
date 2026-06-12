---
title: "Installing Oracle JDK 8 and latest Eclipse version on Ubuntu"
date: 2016-11-21
forum: Tutorials
---

### Post by Erdem on 2016-11-21
Hello everyone!
Hope this guide will be helpful for some people.

Lets start! :D

Before installing Eclipse we should have Oracle JDK installed in our system. 
On Ubuntu it is very easy. Open terminal and enter following commands

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
sudo apt-get install oracle-java8-set-default
```

Now we have Oracle JDK 8 installed in our system. 
To check it you can run this command

```
java -version
```

Output should be like

```
java version "1.8.0_111"
Java(TM) SE Runtime Environment (build 1.8.0_111-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.111-b14, mixed mode)
```

Go to address down below and download eclipse tar.bz package
[http://www.eclipse.org/downloads/eclipse-packages/](http://www.eclipse.org/downloads/eclipse-packages/)

Now we will extract eclipse to /opt folder

```
sudo tar -xvzf ~/Downloads/eclipse* --directory /opt/
```

After extracting eclipse we should create a eclipse shortcut in unity launcher

```
sudo gedit /usr/share/applications/eclipse.desktop
```

Copy and paste all to the gedit window

```
[Desktop Entry]
Name=Eclipse
Type=Application
Exec=/opt/eclipse/eclipse
Terminal=false
Icon=/opt/eclipse/icon.xpm
Comment=Integrated Development Environment
NoDisplay=false
Categories=Development;IDE;
Name[en]=Eclipse
```

Save and close gedit.

Your all done installing latest eclipse in your Ubuntu! =d>

---

