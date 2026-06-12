---
title: "Debian 5"
date: 2009-07-01
forum: The Cafe
---

### Post by waloshin on 2009-07-01
How to do Chmod 777 /var/www in Debian. 

So i can install an SMF forum their.

---

### Post by unknownPoster on 2009-07-01
um...

```

chmod 777 /var/www/

```

---

### Post by waloshin on 2009-07-01
> **unknownPoster said:**
> um...

```

chmod 777 /var/www/

```

I have tried

Su chmod 777 -R /var/www

Sudo chmod 777 --R /var/www

no luck

---

### Post by .Maleficus. on 2009-07-01
Please don't change the permissions on /var/www.  It is owned by root for a reason.

---

### Post by kerry_s on 2009-07-01
> I have tried

Su chmod 777 -R /var/www

Sudo chmod 777 --R /var/www

most commands do not have upper case letters.

Su is just -> su <-by itself no command after it, once your root you can run all the commands you want. i would suggest you enable sudo.

---

### Post by kellemes on 2009-07-01
> **waloshin said:**
> How to do Chmod 777 /var/www in Debian. 

So i can install an SMF forum their.

As said..
Don't change permissions but see to it you get the permissions needed..
"sudo" is the way to go.. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

sudo cp <SMFPACKAGECONTENT> /var/www/smf (or whereever you want it to go..)
You can also open your graphical filemanager (if available) like so..
```
gksudo nautilus
```

Most commands tend to be lowecase..

---

### Post by master_kernel on 2009-07-01
> **kellemes said:**
> As said..
Don't change permissions but see to it you get the permissions needed..
"sudo" is the way to go.. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

sudo cp <SMFPACKAGECONTENT> /var/www/smf (or whereever you want it to go..)
You can also open your graphical filemanager (if available) like so..
```
gksudo nautilus
```

Most commands tend to be lowecase..
**WAIT!**

sudo is not installed by default in Debian, neither is gksudo (and maybe gksu also). Debain users should use 'su', so he's right. Run 'su -c "cp smf/forumfiles /var/www/smf"'.

---

### Post by kerry_s on 2009-07-01
> **master_kernel said:**
> **WAIT!**

sudo is not installed by default in Debian, neither is gksudo (and maybe gksu also). Debain users should use 'su', so he's right. Run 'su -c "cp smf/forumfiles /var/www/smf"'.

gksu is installed if you have gdm gksu & gksudo is the same program, sudo you do have to turn on.
i used the expert install mode & choose not to allow root, so it setup a sudo install for me. i'm using debian testing.

---

### Post by cariboo on 2009-07-01
During a Debian installation, you are prompted to create a root password. To install anything in debian, you have to be root, at the prompt type:

```
su
```

and enter the password you created during installation. Now that you are root, you can do anything you want, but of course be careful as you can quite easily hose the system.

---

### Post by nitehawk777 on 2009-07-01
Yeah,....
To do anything as "root"...
I just go to terminal....and type:
su root  (hit enter)
it will then ask for root's password,....I type in my password for root,..and I can do whatever it is I wanna do as "root"....

Then when I'm in Ubuntu,..I forget sometimes that I have to "sudo" (LOL)

---

### Post by kellemes on 2009-07-02
I'm a big fan of sudo and would [install and use it on Debian]("http://www.debianhelp.co.uk/sudo.htm") too..

The Ubuntu RootSudo-documentation mostly aplies to Debian also.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Good luck.

---

