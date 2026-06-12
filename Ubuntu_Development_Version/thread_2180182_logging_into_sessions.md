---
title: "logging into sessions"
date: 2013-10-11
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-10-11
this is weird and i am current on all updates. i can log into these sessions enlightenment,lubuntu,lxde,xubuntu, and xfce. however if i try to log into gnome, gnome-fallback or ubuntu(unity) session all i get is a blank screen.

---

### Post by grahammechanical on 2013-10-12
I know that you have not installed Cinnamon but this blog could indicate what is happening on your system.

[http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more](http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more)

> **Important: in my test under Ubuntu 13.10, installing Cinnamon broke the Unity session (I was unable to log in to Unity until I removed Cinnamon; this didn't occur in Ubuntu 13.04) so use it at your own risk!**

Early on in the cycle when I was testing Xmir I had the idea of installing all the desktops of the flavours onto Ubuntu. The system became unusable. The issue was not Xmir but the alternative desktops making territorial claims on the system. Poor little LightDM could not make up its mind what background image to put behind the login, Should it Ubuntu or Kubuntu, or Xubuntu or even Lubuntu? 

It seemed to me that I got not a User Interface but the whole Desktop Environment. Days are coming when the incompatibilities will make mixing and matching too difficult. 

Regards.

---

### Post by rburkartjo on 2013-10-12
gra tks for the info. so i reinstalled my backup of 13.04 and made sure that  cinnamon wasnt installed. it wasnt however i had mate installed , so removed. will wait till the final comes out this coming thursday and try again.

---

### Post by sogood007 on 2013-10-12
I have similar issue with login.  I ended up uninstalled lightdm and pick gdm.  I can now login back.   Just FYI:

---

### Post by rburkartjo on 2013-10-12
sogoo tks for the info. what commands did you run to make the change. not sure how to do it. tks

---

### Post by sogood007 on 2013-10-12
> **rburkartjo said:**
> sogoo tks for the info. what commands did you run to make the change. not sure how to do it. tks

I just 
apt-get remove lightdm

(which will prompt for switch to other dm and I happen to have gdm in the list so I switched. I don't know whether that is the proper way) 

Maybe you can follow this one instead.
[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

---

### Post by rburkartjo on 2013-10-13
tks you can also use this 

[http://www.thelinuxguy.nl/how-tos/how-to-switch-between-lightdm-gdm-or-kdm-in-ubuntulinux/](http://www.thelinuxguy.nl/how-tos/how-to-switch-between-lightdm-gdm-or-kdm-in-ubuntulinux/)


doesnt remove just allows you to change

---

### Post by kansasnoob on 2013-10-13
Sadly 'lightdm' is total crap right now, as is 'ubiquity'. We'll see what happens but this nonsense of "cadence testing" has truly resulted in a JIT process when it comes to the iso images and it's NOT a good process!

I think "cadence" is fine with individual apps but it sucks to put off all the important stuff such as installation and the boot process until the last 4 days!

---

### Post by rburkartjo on 2013-10-14
i tried the link i provide for switching to gdm didnt work. i can switch but if i do i have no logon splash screen. still cant logon to an ubuntu or gnome session. i noticed that if i run sudo apt-get remove lightdm i get this warning
The following packages will be REMOVED:
  lightdm lightdm-gtk-greeter lightdm-kde-greeter
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  lubuntu-core lubuntu-default-session lubuntu-default-settings
  lubuntu-desktop ubuntu-desktop xubuntu-default-settings xubuntu-desktop


does this mean i will be uninstalling both lubuntu and xubuntu?
tks

---

### Post by kansasnoob on 2013-10-15
> **rburkartjo said:**
> i tried the link i provide for switching to gdm didnt work. i can switch but if i do i have no logon splash screen. still cant logon to an ubuntu or gnome session. i noticed that if i run sudo apt-get remove lightdm i get this warning
The following packages will be REMOVED:
  lightdm lightdm-gtk-greeter lightdm-kde-greeter
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  lubuntu-core lubuntu-default-session lubuntu-default-settings
  lubuntu-desktop ubuntu-desktop xubuntu-default-settings xubuntu-desktop


does this mean i will be uninstalling both lubuntu and xubuntu?
tks

I'm hoping that we don't release like this! Things are badly broken and I don't know if it's just 'lightdm' :(

But changing sessions or languages is impossible even though this bug says "fixed":

[https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/1213837](https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/1213837)

Sadly we're craptastically broken only three days prior to release :(

---

### Post by rburkartjo on 2013-10-15
kan guess i will backup 13.10 cause everything is working fine except the two logins and will revert to my backup copy of 13.04. hopefully when i try an upgrade of the final this weekend all will be fine. tks

---

