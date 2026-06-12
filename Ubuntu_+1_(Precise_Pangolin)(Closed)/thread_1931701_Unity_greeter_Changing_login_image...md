---
title: "Unity greeter: Changing login image.."
date: 2012-02-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-02-26
Hi all,

For those who can't seem to successfully change their login image to a more personal, custom one.

The following worked for me...

```
sudo apt-get purge unity-greeter && sudo-apt-get install ubuntu-desktop
```

Change background picture to something else (just to be sure), from your 'pictures' folder.

I think the secret is also to use pics that are cropped to fit your puters screen size. IE: 16:9; 16:10; 4:3, etc... 
If the pic size is too different from the screen resolution, it simply won't show up on your login screen, but will still as a background. The login screen will just show the default warty login screen.

---

### Post by JOHNNYG713 on 2012-02-26
or install simple lightdm manager ![https://launchpad.net/~claudiocn/+archive/slm/+files/simple-lightdm-manager_0.2-public7_all.deb]("https://launchpad.net/%7Eclaudiocn/+archive/slm/+files/simple-lightdm-manager_0.2-public7_all.deb")

---

### Post by Baldrick_NZ on 2012-02-26
> **JOHNNYG713 said:**
> or install simple lightdm manager ![https://launchpad.net/~claudiocn/+archive/slm/+files/simple-lightdm-manager_0.2-public7_all.deb]("https://launchpad.net/%7Eclaudiocn/+archive/slm/+files/simple-lightdm-manager_0.2-public7_all.deb")

Thanks for that, so it does! 

It doesn't seem to care the size of the images either, though you have to have the chosen predetermined image pre-loaded as a background.

---

### Post by grahammechanical on 2012-02-27
For those who wish to know the script that tells LightDM what image to use as a background image for a certain user is at

/var/lib/AccountsService/users

There you will find scripts for each user which look something like this:

> XSession=ubuntu
XKeyboardLayouts=gb	extd;gr	extended;
Background=/usr/share/backgrounds/Buck_off!_by_SirPecanGum.jpg

LightDM lets each user have his/hers own image according to which static image is selected as the desktop background image. This is where the information is stored. These scripts must get re-written whenever a new desktop background image is chosen.

When a background slide show is chosen then LightDM looks to this script at

> /etc/lightdm/unity-greeter.conf

Which will have something like this:

> background=/usr/share/backgrounds/warty-final-ubuntu.png
draw-grid=true
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb

Note. We can remove the grid by changing "draw-grid=true" to "draw-grid=false" and also replace the logo by pointing to a logo.png of our own design.

Regards.

---

### Post by jloveless on 2012-04-25
> **Baldrick_NZ said:**
> Hi all,

For those who can't seem to successfully change their login image to a more personal, custom one.

The following worked for me...

```
sudo apt-get purge unity-greeter && sudo-apt-get install ubuntu-desktop
```

Change background picture to something else (just to be sure), from your 'pictures' folder.

I think the secret is also to use pics that are cropped to fit your puters screen size. IE: 16:9; 16:10; 4:3, etc... 
If the pic size is too different from the screen resolution, it simply won't show up on your login screen, but will still as a background. The login screen will just show the default warty login screen.
==========================
the second part of the command line has an error. There should not be a hyphen after sudo, as in "sudo-apt-get...". It should read "sudo apt-get..."

---

### Post by BigCityCat on 2012-04-25
> **JOHNNYG713 said:**
> or install simple lightdm manager ![https://launchpad.net/~claudiocn/+archive/slm/+files/simple-lightdm-manager_0.2-public7_all.deb]("https://launchpad.net/%7Eclaudiocn/+archive/slm/+files/simple-lightdm-manager_0.2-public7_all.deb")
That software leaves my 64bit install with a purple screen. Same goes for ubuntu tweak. It doesn't work. I just have to renamewhatever image I want to use in usr/share/backgrounds to warty-final-ubuntu.png.

---

### Post by Frogs Hair on 2012-04-25
I have a purple screen prior to the drum sound no matter what. I think I can live with less than second of purple though. :)

---

### Post by BigCityCat on 2012-04-25
> **Frogs Hair said:**
> I have a purple screen prior to the drum sound no matter what. I think I can live with less than second of purple though. :)

When I use those apps it stays purple and doesn't change until I goto home/cache/wallpaper and delete the image and go back to the default.

---

### Post by BigCityCat on 2012-04-25
I guess it's obvious that Ubuntu will not deliver on lightdm changing the background image to your desktop wallpaper with precise.

---

### Post by sgage on 2012-04-25
You should know that the permissions on your image file need to be readable for group and others, or you will get nothing.

I just rename my file to warty-final-ubuntu.png and put in /usr/share/backgrounds. As long as the permissions are set properly, it has always worked for me.

---

### Post by codingman on 2012-04-25
It will automatically change it to your original background in 12.04. On 11.10 it would show you the default without doing what the OP said or similar.

---

