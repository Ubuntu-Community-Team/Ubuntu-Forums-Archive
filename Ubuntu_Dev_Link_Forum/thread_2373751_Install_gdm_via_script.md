---
title: "Install gdm via script"
date: 2017-10-09
forum: Ubuntu Dev Link Forum
---

### Post by darkproduct on 2017-10-09
Hello,

I'm currently working on a install script for new Ubuntu installations. I have to instal Ubuntu on several pc's and I would like to automate the process.
In this process I'll switch from lightdm to gdm.

I'm using Ubuntu 16.04 LTS and a bash script.

Right now I install gnome-common and gdm, but from there I have no idea how to archive the rest.

Normally, if you install gdm via terminal you'll get to a menu and there you can select gdm3 instead of lightdm. Is there a command line way for the same thing? And how can I suppress this menu?
Second thing to do, is to switch to GNOME in the install screen.

I would like to know, if this is possible and how!

Thanks for you're help, Dark

---

### Post by Kirboosy on 2017-10-10
Hi Dark! If no one has done so already, Welcome to the forums! :D

I would suggest you look into a configuration management tool like, Ansible, Chef, Puppet, Salt Stack, etc. They are dedicated tools to make large scale deployments easier. I personally use Ansible when I need to scale, but that is personal preference. Find whichever one works best for you and run with it.

> Normally, if you install gdm via terminal you'll get to a menu and there you can select gdm3 instead of lightdm. Is there a command line way for the same thing? And how can I suppress this menu?
Second thing to do, is to switch to GNOME in the install screen.

I would recommend trying the following command
```
sudo apt install gdm3 gnome-common -y
```

Hope that helps!
~Caboose

---

### Post by darkproduct on 2017-10-10
Thanks, this is my first conversation on this Forum.

I do not work for a company and I would like to stay by my script solution, because it is much easier for me.

> **Caboose885 said:**
> 
I would recommend trying the following command
```
sudo apt install gdm3 gnome-common -y
```

I use the "-y" parameter already to confirm the installation of the new packages. I'm not sure, if you know what exactly I mean.

Here is a picture:
[IMG]https://i.stack.imgur.com/K8K5b.png[/IMG]

Is it possible to send the key strokes via xdotool? If yes, how do I send the commands while bash performs the installation command?

Darkproduct

---

### Post by mc4man on 2017-10-10
How about you purge lightdm, then install gdm

---

### Post by Kirboosy on 2017-10-10
+1 to purge lightgdm them installing gdm. Easiest path to get it done. No sense in reinventing the wheel.

Why don't you just use the minimal install as the base for the system? Then you won't have to worry about duplicate packages

---

### Post by darkproduct on 2017-10-11
Thanks for the advice. Purging lightdm was exactly what I needed.

The only thing that is left, is to switch to GNOME in the loggin screen:
[IMG]https://www.tecmint.com/wp-content/uploads/2014/05/Install-GUI-in-Arch-Linux-14.jpg[/IMG]

---

### Post by Kirboosy on 2017-10-11
Would it not work to just remove the alternate desktop environment that you won't be using? Then it would be switched to GNOME automatically.

```
sudo apt remove cinnamon
```

---

