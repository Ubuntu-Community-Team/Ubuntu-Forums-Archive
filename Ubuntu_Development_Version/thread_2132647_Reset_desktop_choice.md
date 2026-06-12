---
title: "Reset desktop choice"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by ELD on 2013-04-05
So I have done a fresh install of 13.04 beta, is there a way to reset my users default desktop choice as my user seems to try to login to a desktop (Cinnamon) that doesn't exist.

This is as a result of using my previous /home that I had partitioned.

---

### Post by carl4926 on 2013-04-05
I'd probably go in with one of my parallel installs and delete all the hidden files and folder (except the ones I need and know are OK to leave)
If you don't have another Linux install in the system, you can do it with Parted Magic

---

### Post by stinkeye on 2013-04-05
I believe you need to edit  /var/lib/AccountsService/users/***$USER*** 

eg mine is /var/lib/AccountsService/users/**glen**

List your installed sessions
```
ls /usr/share/xsessions
```

and edit /var/lib/AccountsService/users/***$USER***
to your chosen session.
```
gksudo gedit /var/lib/AccountsService/users/***$USER***
```


eg my file
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **cat /var/lib/AccountsService/users/glen**
[User]
Language=en_AU
XSession=ubuntu
XKeyboardLayouts=
Background=/home/glen/Pictures/coffee.jpeg
```

---

### Post by zika on 2013-04-05
> **ELD said:**
> So I have done a fresh install of 13.04 beta, is there a way to reset my users default desktop choice as my user seems to try to login to a desktop (Cinnamon) that doesn't exist.

This is as a result of using my previous /home that I had partitioned.If I got Your question right:

1. get out of {lightdm,gdm} to tty1 (AltCtrlF1)
2.1 (if You use LightDM) disable autologin in /etc/lightdm/lightdm.conf
2.2 (if You use GDM) disable autologin in /etc/gdm/custom.conf
3. restart GDM ```
sudo service {lightdm,gdm} restart
```
4. choose another WM and You're OK...

---

