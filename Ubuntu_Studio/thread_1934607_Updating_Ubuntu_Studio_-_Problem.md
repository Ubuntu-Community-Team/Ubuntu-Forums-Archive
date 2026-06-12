---
title: "Updating Ubuntu Studio - Problem?"
date: 2012-03-02
forum: Ubuntu Studio
---

### Post by hbnmgr on 2012-03-02
Using Update Mgr - shows No updates to install, Pkg info was last updated 87 days ago", and when I hit the CHECK button - I get ... "Failed to download Repository information".

Using the instructions here ..
[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

I get the following;

```

Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Ign http://archive.canonical.com oneiric/partner Translation-en
W: Failed to fetch cdrom://Ubuntu-Studio 11.10 _Oneiric Ocelot_ - Release i386 (20111011.1)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-Studio 11.10 _Oneiric Ocelot_ - Release i386 (20111011.1)/dists/oneiric/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

```

Any ideas?  I just want to make sure I have all the Studio Updates.
Learned how to change the Theme to Studio, but can't find "Login Window Themes".

Instructions:  [B]Then select *System* -> *Administration* -> *Login Window*, enter your password, and select *[UbuntuStudio]("https://help.ubuntu.com/community/UbuntuStudio")* in the list of Login Window themes ". 

Have Application Menu / System --- but no Administration !?!?!?


[/B]

---

### Post by jejeman on 2012-03-03
Open software sources and disable CDROM repository.
Or go in sinaptic > settings > repositories, and ond the first tab "ubuntu software" disable cdrom repository.

---

### Post by hbnmgr on 2012-03-03
Thanks, but --- Where is Login Window Themes?

---

### Post by cfhowlett on 2012-03-04
> **hbnmgr said:**
> Thanks, but --- Where is Login Window Themes?

Plymouth manages the Ubuntu boot process (before the root filesystem is mounted) and also provides a graphical boot animation. To change your Plymouth theme use « sudo update-alternatives --config default.plymouth && sudo update-initramfs -u

---

### Post by hbnmgr on 2012-03-05
Get the following;
```

There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth
Nothing to configure.
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic

```Now What?  

To reiterate, I am trying to [B]Change the theme to [UbuntuStudio]("https://help.ubuntu.com/community/UbuntuStudio"). According to the instructions ...

> In the Ubuntu menu, select *System* -> *Preferences* -> *Appearance* -> *Theme* and select *[UbuntuStudio]("https://help.ubuntu.com/community/UbuntuStudio")* from the list of themes that is presented to you. Then select *System* -> *Administration* -> *Login Window*[I]

However there is no Preference etc under System. Appearance is under Settings but there is no Themes, Administration or Login Window anywhere.

It seems something did not complete even though I installed from Ubuntu Studio CD, and recently ran the following in Terminal.

```


```[/I][/B]```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```[B][I]

BTW - I'm using XFCE Desktop. 
Any suggestions?

Thanks!

[/I][/B]

---

