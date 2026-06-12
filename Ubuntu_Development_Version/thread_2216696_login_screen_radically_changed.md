---
title: "login screen radically changed?"
date: 2014-04-13
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-04-13
what happened?
Went from login on far left right with the new purlpley backgroung to all grey and login in the middle?
Looks ugly.
Are the developers playing games?

How can i get the login back to normal?

---

### Post by sdowney717 on 2014-04-13
I think I know what this is.

gdm is being used vs lightdm

so then

sudo dpkg-reconfigure gdm
select lightdm

---

### Post by 23dornot23d on 2014-04-14
There is a problem too in lightdm - once the selection list builds up - probably not affect people if they only run one or two desktops ........

So it will not get seen ...... but the bottom selections go off the screen and are not in view ...... it becomes guess work

as to what is lower down on the selection listing .

---

### Post by grahammechanical on 2014-04-14
The login with the grey background and the password panel in the middle is pure Gnome 3 Shell login. We see this in Ubuntu Gnome which does not use LightDM but GDM.

Regards.

---

### Post by ajgreeny on 2014-04-14
I also have this problem but there is only lightdm installed as far as I can see.

Just to check, I tried the ```
sudo dpkg-reconfigure gdm
``` command but lightdm is the only display-manager I have; gdm is definitely not installed.

This change of the look at login first happened a while ago and I ignored it and just put up with the ugly login screen, but I would really like the proper login with the box at middle left of the screen, and purple, not the grey box in the middle.

Today's updates which included lightdm packages has not made any difference at all.

PS: I am running trusty with unity in VirtualBox, not a hardware install proper.  Could that be the reason?  After todays updates tye system experiences an error at bootup related to software 3D rendering, which will be because of the VM, I think, but what about the login screen?

---

### Post by sdowney717 on 2014-04-14
> **ajgreeny said:**
> I also have this problem but there is only lightdm installed as far as I can see.

Just to check, I tried the ```
sudo dpkg-reconfigure gdm
``` command but lightdm is the only display-manager I have; gdm is definitely not installed.

This change of the look at login first happened a while ago and I ignored it and just put up with the ugly login screen, but I would really like the proper login with the box at middle left of the screen, and purple, not the grey box in the middle.

Today's updates which included lightdm packages has not made any difference at all.

PS: I am running trusty with unity in VirtualBox, not a hardware install proper.  Could that be the reason?  After todays updates tye system experiences an error at bootup related to software 3D rendering, which will be because of the VM, I think, but what about the login screen?

you could try install sudo apt-get install gnome.
gnome will ask you what you want, gdm or lightdm as it is installing.

Is your login gray, with user name in direct center? that is what mine looked like, also seemed very minimal, saw no way to select a different desktop.

---

### Post by ajgreeny on 2014-04-14
Here's a screenshot of my login screen in the virtual machine, running in a window, not fullscreen so I could use printscreen from the host.

---

### Post by sdowney717 on 2014-04-14
> **ajgreeny said:**
> Here's a screenshot of my login screen in the virtual machine, running in a window, not fullscreen so I could use printscreen from the host.

gdm login screen i saw on my PC looked like this one I found on google images.

[IMG]http://4.bp.blogspot.com/-WDH66Fiix4U/UIEeB1ONAyI/AAAAAAAALHc/ZIaearoaoSI/s1600/ubuntu-gnome-gdm.png[/IMG]

---

### Post by sammiev on 2014-04-14
> **sdowney717 said:**
> gdm login screen i saw on my PC looked like this one I found on google images.

[IMG]http://4.bp.blogspot.com/-WDH66Fiix4U/UIEeB1ONAyI/AAAAAAAALHc/ZIaearoaoSI/s1600/ubuntu-gnome-gdm.png[/IMG]

Using 14.04 gnome-ubuntu here and have the same screen. Been like that for sometime.

---

