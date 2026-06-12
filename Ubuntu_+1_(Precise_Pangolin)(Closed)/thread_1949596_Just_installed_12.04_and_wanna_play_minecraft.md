---
title: "Just installed 12.04 and wanna play minecraft"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jeggy94 on 2012-03-30
I just installed Ubuntu 12.04 beta 2 64bit on my Dell XPS 15.
Openjdk ain't in the software center. I really wanna get Minecraft to work on my laptop.

anyone know of anyway i can get it to work?

---

### Post by linuxd1 on 2012-03-30
Check this : [http://ubuntuforums.org/showthread.php?t=1812767](http://ubuntuforums.org/showthread.php?t=1812767)

---

### Post by Jeggy94 on 2012-03-30
> **linuxd1 said:**
> Check this : [http://ubuntuforums.org/showthread.php?t=1812767](http://ubuntuforums.org/showthread.php?t=1812767)

Openjdk ain't in the software center... thats why i asked here

---

### Post by dino99 on 2012-03-30
> **Jeggy94 said:**
> Openjdk ain't in the software center... thats why i asked here

find it & install it via synaptic

sudo apt-get install synaptic
sudo synaptic

---

### Post by Jeggy94 on 2012-03-30
> **dino99 said:**
> find it & install it via synaptic

sudo apt-get install synaptic
sudo synaptic

I tried that and i installed openjdk 6 and it don't show up when i right click on the .jar file :/

---

### Post by cariboo on 2012-03-30
According to [this]("http://ubuntuforums.org/showthread.php?t=1945777&highlight=minecraft") thread, you need to install Sun/Oracle java, instead of the open version.

---

### Post by kaldor on 2012-03-30
*sudo apt-get install openjdk-7-jre*

Worked for me. One PC gets a black screen when logging into Minecraft, though.

If that doesn't exist...

1- Open Ubuntu Software Centre
2- Edit the software sources (on one of the menubar options- forget where)
3- Make sure Universe and Multiverse repos are check'd.

Close USC, and reload the repos and try again:

*sudo apt-get update && sudo apt-get install openjdk-7-jre*

Good luck.

Edit: I also have the issue with it not showing up in the list when clicking. My temporary solution is to just open a terminal, cd to the directory where minecraft.jar is located, and run this command:

```
java -jar minecraft.jar
```

---

### Post by Jeggy94 on 2012-03-30
> **kaldor said:**
> *sudo apt-get install openjdk-7-jre*

Worked for me. One PC gets a black screen when logging into Minecraft, though.

If that doesn't exist...

1- Open Ubuntu Software Centre
2- Edit the software sources (on one of the menubar options- forget where)
3- Make sure Universe and Multiverse repos are check'd.

Close USC, and reload the repos and try again:

*sudo apt-get update && sudo apt-get install openjdk-7-jre*

Good luck.

Edit: I also have the issue with it not showing up in the list when clicking. My temporary solution is to just open a terminal, cd to the directory where minecraft.jar is located, and run this command:

```
java -jar minecraft.jar
```

Thanks, that worked :D

---

