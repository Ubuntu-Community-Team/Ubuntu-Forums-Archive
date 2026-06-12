---
title: "Installing Java on 12.04."
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by stchman on 2012-04-03
Hello all.

I used to install the sun-java6 packages on my Ubuntu systems.  Since Oracle and Canonical have pretty much yanked all the .deb stuff to install Java I figure I would use the OpenJDK7.

I used to install Java 6 via this command line:

```

sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```

I'm gathering that the same can be accomplished using these packages:
```

sudo apt-get install openjdk-7-jdk openjdk-7-jre icedtea-7-plugin

```

This should install the JRE, JDK, and the browser plugin.  I guess I'll have to do without the fonts.

Thanks.

---

### Post by stchman on 2012-04-04
I believe I have found a solution.

Linux Mint has the Sun/Oracle Java .deb installers in their repositories.  They are 6u26, but they will work.

[http://packages.linuxmint.com/list.php?release=Lisa#upstream](http://packages.linuxmint.com/list.php?release=Lisa#upstream)

The sun-java6 packages are there and they work in Ubuntu 12.04.  I have verified they work and installed them using dpkg command.

---

### Post by zeljkojagust on 2012-04-04
Check this link: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
It shows how to install latest version of Oracle's Java on Ubuntu/Debian based distros.

---

### Post by Perfect Storm on 2012-04-05
This works easy and flawless: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by craig10x on 2012-04-05
I can do you even better! (lol) this is a link to a thread in the linux mint forums that gives you 4 simple commands you can copy and paste into the terminal (one at a time of course) that will install the latest sun-java in an deb based linux distro!  

It is a pre-packaged deb file and it also adds in a "script" (see the line right after that one in the link) which you can use to get an updated version at any time one becomes available (once you have installed with that initial deb file, of course)...

[http://forums.linuxmint.com/viewtopic.php?f=42&t=93052](http://forums.linuxmint.com/viewtopic.php?f=42&t=93052)

I used it to install sun-java (actually oracle now....but this is the licensed version you need)...on both ubuntu 11.10 and 12.04....

---

