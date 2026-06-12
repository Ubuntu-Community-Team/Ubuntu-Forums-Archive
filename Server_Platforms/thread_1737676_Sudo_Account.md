---
title: "Sudo Account"
date: 2011-04-23
forum: Server Platforms
---

### Post by main0666 on 2011-04-23
Hi I am new to this and the problem is when I log in (only one account) and use the sudo account it keeps saying access denied when trying to change the file permison, I am trying to set up a simple web server (Joomla) and the diractory will not let me do anything, I can't install any any modules or plgins the site is loaded into /var/www is there a step by step guide.  I have installed Ubunta 10.10, MySql, PHP5, Apache2, Myphpadmin.  Need help?:confused:

---

### Post by usatonycuba on 2011-04-23
> **main0666 said:**
> Hi I am new to this and the problem is when I log in (only one account) and use the sudo account it keeps saying access denied when trying to change the file permison, I am trying to set up a simple web server (Joomla) and the diractory will not let me do anything, I can't install any any modules or plgins the site is loaded into /var/www is there a step by step guide.  I have installed Ubunta 10.10, MySql, PHP5, Apache2, Myphpadmin.  Need help?:confused:
Open your terminal and type:
```
sudo su
```
it will ask for your pass, Enter pass... then type:
```
nautilus
```
a Manager/browser window will be appear, that is nautilus as root, then navigate to File System/var/www/ and there you can do anything through that "window".. it will take no permitions to change anything...

did help?

---

### Post by main0666 on 2011-04-24
> **usatonycuba said:**
> Open your terminal and type:
```
sudo su
```
it will ask for your pass, Enter pass... then type:
```
nautilus
```
a Manager/browser window will be appear, that is nautilus as root, then navigate to File System/var/www/ and there you can do anything through that "window".. it will take no permitions to change anything...
 
did help?
 
 
Thanks for the info it all I get is:
 
Welcome to Ubuntu!
* Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Sun Apr 24 07:05:10 2011 from philip-pc.home
philip@spare-xp:~$ sudo su
[sudo] password for philip:
root@spare-xp:/home/philip# nautilus
Could not parse arguments: Cannot open display:

---

### Post by CharlesA on 2011-04-24
nautilus is a GUI application, so you won't be able to run it without a GUI.

---

### Post by usatonycuba on 2011-04-24
> **main0666 said:**
> Thanks for the info it all I get is:
 
Welcome to Ubuntu!
* Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Sun Apr 24 07:05:10 2011 from philip-pc.home
philip@spare-xp:~$ sudo su
[sudo] password for philip:
root@spare-xp:/home/philip# nautilus
Could not parse arguments: Cannot open display:

> **CharlesA said:**
> nautilus is a GUI application, so you won't be able to run it without a GUI.
That was totally my fault, answered sleepy and tired ... did not read well, you're behind a server, and as @CharlesA it is impossible to see nautilus without a  Graphical Interface.

Anyway ... I see you have NOT problems with your root account, after you did enter your password, there is a "super-user" with root privileges...so? .. you already get you access to it:

```
**[COLOR="DarkRed"]root[/COLOR]@spare-xp:/home/philip#** 
```

Enter any command that you may wanna to executed from there, it will do it with root privileges?..  ...or you can do it directly from terminal.. for example.. file permission  to 755 at /[COLOR="Sienna"]var[/COLOR]/[COLOR="Sienna"]www[/COLOR]/[COLOR="Sienna"]FILE_NAME[/COLOR]:
```

sudo chmod 755 /var/www/FILE_NAME
```
..will ask you for the "sudo" password and that's it

---

### Post by CharlesA on 2011-04-24
> **usatonycuba said:**
> That was totally my fault, answered sleepy and tired ... did not read well, you're behind a server, and as @CharlesA it is impossible to see nautilus without a  Graphical Interface.

Happens to everyone. :)

@OP: You can just move the files to /var/www/ since you are running as root, but be careful.

---

### Post by main0666 on 2011-04-25
> **CharlesA said:**
> Happens to everyone. :)
 
@OP: You can just move the files to /var/www/ since you are running as root, but be careful.
 
Thanks for info I reinstallled every again and it seams to work as it should so I don't have to log in a root, still learning:D

---

