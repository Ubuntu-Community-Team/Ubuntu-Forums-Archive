---
title: "Changing the Shell prompt color in Ubuntu Server 18.04 LTS"
date: 2019-07-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Peter Alien on 2019-07-18
Hello,

Can anyone tell me how can i change the Shell prompt color and the commands i write in it to another color in Ubuntu Server 18.04?
Is it possible?

I searched for it but so far i didn't found anything about it!


Just another question is it possible to install XAMPP or LAMPP in Ubuntu Server 18.04? I ask this because i think this apps have a GUI but Ubuntu Server only has the Shell.


Many thanks in advanced.

Pedro

---

### Post by &amp;KyT$0P# on 2019-07-18
> **Peter Alien said:**
> Can anyone tell me how can i change the Shell prompt color and the commands i write in it to another color in Ubuntu Server 18.04?
Is it possible?

If using bash, as is by default in Ubuntu 18.04, you need to edit [FONT=Courier New]~/.bashrc[/FONT], look for a line like this -
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;[COLOR="#FF0000"]**32**[/COLOR]m\]\u@\h\[\033[00m\]:\[\033[01;[COLOR="#FF0000"]**34**[/COLOR]m\]\W\[\033[00m\]\$ '
```
You can change the "32" and "34" (emphasized above) to other numbers between 30 and 37 to make other colors.

(At the risk of information overload, [this post]("https://ubuntuforums.org/showthread.php?t=2404439&p=13811171#post13811171") contains a script which when run will show you all the color possibilities and the codes to get them.)

---

### Post by Peter Alien on 2019-07-19
Many thanks, halogen2.

I changed the colors of the Shell prompt editing .bashrc file. But can you tell me if it's possible to edit the color of the text that i write after the Shell prompt in Ubuntu Server 18.04?

---

### Post by mastablasta on 2019-07-22
> **Peter Alien said:**
> 
Just another question is it possible to install XAMPP or LAMPP in Ubuntu Server 18.04? I ask this because i think this apps have a GUI but Ubuntu Server only has the Shell.


they do not. server editing is done in configuration files. 

MySQL/MariaDB has phpmyadmin which can help you configure it in GUI (in browser)


> [COLOR=#242729][FONT=Arial]XAMPP is a completely free, easy to install Apache distribution containing MariaDB, PHP, and Perl. The XAMPP open source package has been set up to be incredibly easy to install and to use.[/FONT][/COLOR]

X stands for the OS. in linux it will change to L so LAMPP or without Perl - LAMP.

if you want a GUI to administer server have a look at Ajenti or if you want something more like small business server have a look at Zentyal. For home media server the Debian based OpenMediaVault is also good. 


still sooner or later you will get to (text) configuration files. Ajenti comes with nice editor in the GUI.

---

### Post by Peter Alien on 2019-07-30
Many... many thanks mastablasta.

---

