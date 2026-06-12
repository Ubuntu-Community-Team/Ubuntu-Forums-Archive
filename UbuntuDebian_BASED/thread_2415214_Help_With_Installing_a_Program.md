---
title: "Help With Installing a Program"
date: 2019-03-22
forum: Ubuntu/Debian BASED
---

### Post by ivan23m on 2019-03-22
I need help with installing an app, it is in AppImage format. I already tried making a file executable and double-clicking on it. I went on Properties and checked ''Allow this file to run as a program''. I also tried via Terminal:

```


ivan23m@ivan23m-desktop:~$ cd /home/ivan23m/Downloads/
ivan23m@ivan23m-desktop:~/Downloads$ chmod a+x avidemux_2.7.2.appImage
ivan23m@ivan23m-desktop:~/Downloads$ ./avidemux_2.7.2.appImage
bash: ./avidemux_2.7.2.appImage: cannot execute binary file: Exec format error
ivan23m@ivan23m-desktop:~/Downloads$ 


```

I have Linux Zorin 12.4

---

### Post by Frogs Hair on 2019-03-22
Does the file manager have a setting for running executable files in preferences ?

---

### Post by ivan23m on 2019-03-22
You are going to have to explain to me how to check that. I am going to post screenshots of File Manager Preferences, maybe that will help.

---

### Post by Frogs Hair on 2019-03-22
The executable option would under behavior if it were included. If the setting is not there it just indicates it's not required in your file manager.

---

### Post by ivan23m on 2019-03-22
Ok, so what then? Actually, nevermind, I found a newer version that is in tar.gz format but I also have a problem with that.

```


ivan23m@ivan23m-desktop:~$ cd /home/ivan23m/Downloads/
ivan23m@ivan23m-desktop:~/Downloads$ tar xzf avidemux_2.7.3.tar.gz
ivan23m@ivan23m-desktop:~/Downloads$ ./configure
bash: ./configure: No such file or directory
ivan23m@ivan23m-desktop:~/Downloads$ 


```

---

### Post by yetimon_64 on 2019-03-22
> **ivan23m said:**
> ...

```


ivan23m@ivan23m-desktop:~$ cd /home/ivan23m/Downloads/
ivan23m@ivan23m-desktop:~/Downloads$ tar xzf avidemux_2.7.3.tar.gz
ivan23m@ivan23m-desktop:~/Downloads$ ./configure
bash: ./configure: No such file or directory
ivan23m@ivan23m-desktop:~/Downloads$ 


```

You have missed one step there when trying to configure avidemux, you are still in the Downloads directory. You need to "cd" into the avidemux folder that was created when you extracted the contents of the tar.gz file.
eg.```
ivan23m@ivan23m-desktop:~/Downloads$ cd avidemux_2.7.3
```then ...
```
ivan23m@ivan23m-desktop:~/Downloads/avidemux_2.7.3$./configure 
```
Good luck, regards, yeti

---

### Post by ivan23m on 2019-03-22
Unfortunately, that doesn't work either, it doesn't have that file. I am going to send you a screenshot of a folder. 

```


ivan23m@ivan23m-desktop:~$ cd /home/ivan23m/Downloads/
ivan23m@ivan23m-desktop:~/Downloads$ tar xzf avidemux_2.7.3.tar.gz
ivan23m@ivan23m-desktop:~/Downloads$ cd avidemux_2.7.3
ivan23m@ivan23m-desktop:~/Downloads/avidemux_2.7.3$ ./configure
bash: ./configure: No such file or directory
ivan23m@ivan23m-desktop:~/Downloads/avidemux_2.7.3$ 


```

---

### Post by yetimon_64 on 2019-03-22
It seems that this archive uses other methods to build the package than are usually used.

I've hit a major blockage with this and am unfamiliar with how avidemux is being built here. I have some experimenting to do with this in the mean time; I'm currently experimenting with the bootStap.bash script supplied, but really don't know for sure if what I'm doing is right or not.

 Await further advice from someone who has succeeded building this package. Regards, yeti.

---

### Post by The Cog on 2019-03-23
I see there is a file called README in there. What does that say? I don't know this software, but README files like that usually contain installation instructions.

---

### Post by yetimon_64 on 2019-03-23
> **The Cog said:**
> I see there is a file called README in there. What does that say? I don't know this software, but README files like that usually contain installation instructions.

The readme file is no help, the only contents being ...
> Avidemux is a simple platform video editor for Linux, Windows and MacOsX.
... pretty useless README file for installation instructions that one :).

[[COLOR=#0000ff]--This--[/COLOR]]("http://fixounet.free.fr/avidemux/download.html") site shows to use the avidemux [[COLOR=#0000ff]2.6.x instructions[/COLOR]]("http://avidemux.org/admWiki/doku.php?id=build:install_2.6") for building the 2.7.3 package from source. (Note for OP, blue text in my post contains links to information and sites etc.)

I must admit to trying to build this package this afternoon (AEST time) and failed miserably. Doesn't seem too easy of a task, though I am trying on ubuntu mate 18.04 so it may work better on Zorin, maybe.

Good luck with this one OP, sadly I failed pretty badly here today and had to give up before I messed up my install too much.
Regards, yeti.

---

### Post by ivan23m on 2019-03-23
I want to thank everyone here, especially yeti for the extra effort put in this. I will try to do this by myself, if I succeed I will post an update.

---

