---
title: "Create new launcher in Unity"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fbicknel on 2012-04-18
Is this a bug?

I used gnome-desktop-item-edit to create a desktop launcher, assigned a nice picture to it and dragged it to the Unity bar.

The launcher is there, but it's just a blank space.  Click on the blank space, it launches.

The icon I assigned it was: /usr/share/icons/hicolor/scalable/apps/gdu-encrypted-unlock.svg

I'll be happy to file a bug if it should be done.
> 
fbicknel@bick-ubtu3:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
fbicknel@bick-ubtu3:~$ uname -a
Linux bick-ubtu3 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
fbicknel@bick-ubtu3:~$ aptitude show unity
Package: unity                           
State: installed
Automatically installed: no
Version: 5.10.0-0ubuntu6
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64

---

### Post by mc4man on 2012-04-18
First I would  - 
open the launcher (.desktop) you created in a text editor & remove one of the Icon= lines if there are 2 (probably the 1st one with a lang in it
(you can just open a gedit window then DnD the launcher on to gedit window

log out/in

---

### Post by JRV on 2012-04-19
You can install alacarte with the command:```
sudo apt-get install alacarte
```

Start alacarte, fill in the blanks and select an icon.
Your .desktop will be stored in ~/.local/share/applications.

---

### Post by josephmills on 2012-04-19
I would also take a look at 
[http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available](http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available)

---

### Post by treesurf on 2012-04-19
> **JRV said:**
> You can install alacarte with the command:```
sudo apt-get install alacarte
```

Start alacarte, fill in the blanks and select an icon.
Your .desktop will be stored in ~/.local/share/applications.

I was having the same problem and this worked for me.  Thank you.

---

### Post by Frogs Hair on 2012-04-19
You can also create launchers from Dash > Main Menu > New Item without adding them to the desktop first . Select the category you want the item to go on the left side . You can choose a path to an icon you would like to use from the icon image on the left side of the launcher dialog box.

---

### Post by Version Dependency on 2012-04-19
As mentioned above, Alacarte really makes the creation of custom launchers a breeze.  It really should be a default program.

---

### Post by josephmills on 2012-04-19
can alacrate do unity quick links ?

---

### Post by mc4man on 2012-04-19
> **josephmills said:**
> can alacrate do unity quick links ?

No, there was a quicklist editor for a while but it may of died out. They are very easy to create in any text editor, The learning curve takes a few min. or so

---

### Post by philinux on 2012-04-19
> **mc4man said:**
> No, there was a quicklist editor for a while but it may of died out. They are very easy to create in any text editor, The learning curve takes a few min. or so

This looks good.

[http://ubuntuforums.org/showpost.php?p=11843139&postcount=365](http://ubuntuforums.org/showpost.php?p=11843139&postcount=365)

---

### Post by Jacobonbuntu on 2012-04-19
Thanks! I just did....

---

### Post by fbicknel on 2012-04-25
[QUOTE=Frogs Hair]You can also create launchers from Dash > Main Menu > New Item  without adding them to the desktop first . Select the category you want  the item to go on the left side . You can choose a path to an icon you  would like to use from the icon image on the left side of the launcher  dialog box.[/QUOTE]Worked perfectly; thanks Mr. Hair.

Once you create the launcher, open dash again, then either run from there as usual or drag the icon to the launcher on the left side and it's always available.

---

