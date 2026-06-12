---
title: "Lightdm login screen logo"
date: 2011-12-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2011-12-16
I still have "Ubuntu 11.10" logo at the bottom left corner, under lightdm login screen, and cant find how to get "ubuntu 12.04" instead.
Wonder which package/script put it there.

---

### Post by yaji on 2011-12-16
Its a PNG file, you can change it with Simple Lightdm Manager.

---

### Post by dino99 on 2011-12-16
> **yaji said:**
> Its a PNG file, you can change it with Simple Lightdm Manager.

Great finding, thanks :)

---

### Post by ventrical on 2011-12-16
I edited one of my installs with GIMP.

---

### Post by dino99 on 2011-12-16
issue reported: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/904622](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/904622)

---

### Post by jbicha on 2011-12-16
That issue was mentioned in the Alpha 1 [release notes]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha1") as bug [892394]("https://bugs.launchpad.net/bugs/892394"). This generally happens every release where it takes a while for the version number to be manually bumped to the new one.

---

### Post by grahammechanical on 2011-12-17
@dino99

After installing and running Simple LightDM Manager it will put two image files in /home/.simpleLightDMManager.

logo.png is the image that you need to modify or replace. With simple LightDM Manager you can replace the background image behind the LightDM greeter with another image, for example one of the background wallpaper images. It will be called file.jpg when put in the .simpleLightDMManager folder. Modify or replace that image if you want and you get the greeter background that you like.

Regards.

P.S. I suppose that another way to do this without Simple LightDM Manager is to modify or replace these two image files

usr/share/unity-greeter/logo.png

and 

usr/share/backgrounds/warty-final-ubuntu.png

---

### Post by dmoconnell on 2011-12-17
or (if you wish to keep the originals in tacked) you could edit the conf file (etc/lightdm/unity-greeter.conf)and just change the background and logo lines 
my 2 cents
Dm

---

### Post by dino99 on 2011-12-17
Thanks you all guys for the feedback & tweaks.
By the way, as Precise is a LTS (will be), better to report such issue (not a show stopper) to fix the release. As previously said, at least 2 reports are opened against lightdm/plymouth, so let devs managing these details and fix the logic.
As a LTS i only test the genuine config, dont want third party disturbing thee whole packaging.
To resume:
- the logo seen under Lightdm login screen comes from /usr/share/gnome-control-center/ui/UbuntuLogo.png: this path is not logical or should not be used, per Jbicha comment.
- the supposed used logo.png is a blank (empty) image, and dont seems to be used (or is hidden under UbuntuLogo. So really needs to be fixed.

note: the greeter package is not installed at all, and still wonder if it does something anyway (installed or purged, cant see the difference.

---

### Post by mc4man on 2011-12-17
I use a default as supplied 12.04 which uses the unity-greeter & logo.png  which atm is the same as is used in 11.10

(for the heck of it grabbed the .png from the greeter bug report, (unity_greeter_logo.png), renamed it logo.png & replaced the logo.png in /usr/share/unity-greeter/ with it. The log in screen now shows it,

---

### Post by grahammechanical on 2011-12-17
> you could edit the conf file (etc/lightdm/unity-greeter.conf)and just change the background and logo lines 

This is true and from looking at unity-greeter.conf on my system, I see that Simple LightDM Manager simply edits that file to point to the images in its own .simpleLightDMManager folder.

Regards.

---

