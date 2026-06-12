---
title: "Oh good lord he's made of wood"
date: 2007-04-20
forum: The Cafe
---

### Post by DoctorMO on 2007-04-20
Hi,

I just thought I'd check to see if my wacom tablet now works since support was added in kernel 2.6.18 and feisty is kernel 2.6.20 anyway did anyone notice this new feature:

```

doctormo@terous:~$ xidump -l
The program 'xidump' is currently not installed.  You can install it by typing:
sudo apt-get install wacom-tools
bash: xidump: command not found

```

Very cool, so I thought I'd test it again with another app I know is not installed, xine:

```

doctormo@terous:~$ xine
The program 'xine' is currently not installed.  You can install it by typing:
sudo apt-get install xine-ui
Make sure you have the 'universe' component enabled
bash: xine: command not found

```

So not only did it tell me how to install the program but also instructed me to enable the universe repositories; this is now only a minor matter of asking if the user wants that program installed I guess.

---

### Post by jfinkels on 2007-04-20
> **DoctorMO said:**
> Hi,

I just thought I'd check to see if my wacom tablet now works since support was added in kernel 2.6.18 and feisty is kernel 2.6.20 anyway did anyone notice this new feature:

```

doctormo@terous:~$ xidump -l
The program 'xidump' is currently not installed.  You can install it by typing:
sudo apt-get install wacom-tools
bash: xidump: command not found

```

Very cool, so I thought I'd test it again with another app I know is not installed, xine:

```

doctormo@terous:~$ xine
The program 'xine' is currently not installed.  You can install it by typing:
sudo apt-get install xine-ui
Make sure you have the 'universe' component enabled
bash: xine: command not found

```

So not only did it tell me how to install the program but also instructed me to enable the universe repositories; this is now only a minor matter of asking if the user wants that program installed I guess.

Yep, this is a new program enabled by default in Feisty called "command-not-found". I think it's pretty annoying, but I'm sure lots of people will appreciate it!

---

### Post by eentonig on 2007-04-20
I found it indeed an awsome future they've added. And will definitely be an aid for new users getting to know the terminal interface.

---

### Post by Super King on 2007-04-20
Very cool feature.

> Oh good lord he's made of wood

Bender, right? :)

---

### Post by ubuntu27 on 2007-04-20
> **DoctorMO said:**
> Hi,

I just thought I'd check to see if my wacom tablet now works since support was added in kernel 2.6.18 and feisty is kernel 2.6.20 anyway did anyone notice this new feature:

```

doctormo@terous:~$ xidump -l
The program 'xidump' is currently not installed.  You can install it by typing:
sudo apt-get install wacom-tools
bash: xidump: command not found

```

Very cool, so I thought I'd test it again with another app I know is not installed, xine:

```

doctormo@terous:~$ xine
The program 'xine' is currently not installed.  You can install it by typing:
sudo apt-get install xine-ui
Make sure you have the 'universe' component enabled
bash: xine: command not found

```

So not only did it tell me how to install the program but also instructed me to enable the universe repositories; this is now only a minor matter of asking if the user wants that program installed I guess.


Yep that one of the  new feature in Feisty that it is advertised in the official Ubuntu 7.04 Tour page!

Here: 
[https://wiki.ubuntu.com/7.04Tour#head-81ce3127b6b1dd26736df504e3d2d238711a9a84](https://wiki.ubuntu.com/7.04Tour#head-81ce3127b6b1dd26736df504e3d2d238711a9a84)

---

