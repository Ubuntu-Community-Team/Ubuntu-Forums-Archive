---
title: "GUI Desktop on Server 7.04"
date: 2007-06-13
forum: The Cafe
---

### Post by tamays on 2007-06-13
Although I hate to repeat myself (I just posted this message in the Beginners Section) here goes... I installing Ubuntu Server 7.04, and with a little trouble I was able downloading and installing the Desktop. Once the installation was complete (little over an hour) I rebooted the server only to find my old friend, the command prompt. I asked myself, did I miss something? Is there a command or script I need to run? regrettably myself didn't have a clue. I turned to my books only to find that all the books I have, and all the web pages I have read assume I have the desktop up and running. So, a little hint would be nice, a complete answer would be great... Any help is welcome.

Thanks, Tom. ;)

---

### Post by maniacmusician on 2007-06-13
> **tamays said:**
> Although I hate to repeat myself (I just posted this message in the Beginners Section) here goes... I installing Ubuntu Server 7.04, and with a little trouble I was able downloading and installing the Desktop. Once the installation was complete (little over an hour) I rebooted the server only to find my old friend, the command prompt. I asked myself, did I miss something? Is there a command or script I need to run? regrettably myself didn't have a clue. I turned to my books only to find that all the books I have, and all the web pages I have read assume I have the desktop up and running. So, a little hint would be nice, a complete answer would be great... Any help is welcome.

Thanks, Tom. ;)
The server is headless; no GUI

edit: oh, you already installed the gui. you have to install the xorg packages. there's xserver-xorg, and maybe a couple of others.

---

### Post by zvacet on 2007-06-13
If you installed desktop with this 


```
sudo aptitude install ubuntu-desktop
```

and it is still seams like it is not there 

```
sudo /etc/init.d/gdm start
```

---

### Post by az on 2007-06-13
> **tamays said:**
> Although I hate to repeat myself (I just posted this message in the Beginners Section) here goes... I installing Ubuntu Server 7.04, and with a little trouble I was able downloading and installing the Desktop. Once the installation was complete (little over an hour) I rebooted the server only to find my old friend, the command prompt. I asked myself, did I miss something? Is there a command or script I need to run? regrettably myself didn't have a clue. I turned to my books only to find that all the books I have, and all the web pages I have read assume I have the desktop up and running. So, a little hint would be nice, a complete answer would be great... Any help is welcome.

Thanks, Tom. ;)

The server kernel is not ideal for a desktop.  That may cause some problems.  As well, you may not have completed the installation of all the packaged (for some reason, I dunno)

run


sudo apt-get install linux-generic

and then 
sudo apt-get -f install

and it should work fine.

---

