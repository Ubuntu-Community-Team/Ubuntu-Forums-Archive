---
title: "A beautiful, minimal and workable Openbox session, with configuration files..."
date: 2017-04-29
forum: Tutorials
---

### Post by sbnwl on 2017-04-29
> **Openbox is a simple, lightweight and highly configurable window manager and desktop-environment like the Ubuntu Unity, KDE and Gnome. Here in this post I share some tips and set of configuration files that I have tweaked over the years to use on my laptop, desktop and servers.**

The best part about Openbox is that you could install the Openbox-session alongside Ubuntu Unity, Gnome or KDE sessions and it does not interfere with any of them. Moreover, the Openbox session can be used on an xrdp-server while logging in remotely, where there is still no support for a Gnome-session. The procedure described here for installing Openbox-session applies to Ubuntu and all of its derivatives. 

[QUOTE]*If one can afford dealing with package management systems other than **apt,** such as **yum**, **pacman** or **eopkg**, then this tutorial can be implemented in other Linux distributions as well.*

The purpose of this post is to prepare a workable, simple, snappy and responsive desktop environment for the users, yet maintaining a beautiful, aesthetically pleasant (yes, I care for this) desktop with modern touch of effects around the desktop objects and windows. This could especially revive your old machines with low resources.

[/QUOTE]

[HR][/HR][CENTER]**The following steps summarise the procedure to prepare an Openbox Desktop session by yourself:**
[/CENTER]
  [HR][/HR]

**1.** To begin with, one has to install some packages first. Open a terminal and issue the following commands:
```

sudo apt-get install openbox obmenu tint2 xfce4-panel xfce4-notifyd xfce4-whiskermenu-plugin wget unzip scrot xclip gnome-screensaver plank compton feh conky-all curl lxappearance

```

One can skip installing the packages plank, compton, feh, conky-all, curl and lxappearance if they do not care about desktop aesthetics. (**I recommend you do install them for the best experience**)

**2.** Now we need to write some configuration files to use with some of the above packages, though I am not actually going to do it here. Instead I let you **download my own file** [ATTACH=CONFIG]281761[/ATTACH] **  (or [click here]("https://docs.google.com/uc?export=download&id=1ZtVXar81IYSGaIbTLdFJuBwRGN0ej_GO"))**. Place the downloaded zip file in your home folder. [*The whole point of supplying the configuration stuff in one zip file is to make the entire procedure simpler for everybody to implement.* **Plus this configuration pack is the most extended and tweaked one for speed, lightweight, cleanliness and elegance properties, at least for me.**]
```

wget --no-check-certificate -r 'https://docs.google.com/uc?export=download&id=1ZtVXar81IYSGaIbTLdFJuBwRGN0ej_GO' -O OpenboxInstall.zip
mv OpenboxInstall.zip ~/

```

[B]3. Make sure that the downloaded OpenboxInstall.zip file is in your home directory.
[**Caution: If your operating system is Xubuntu or you are already using the XFCE desktop then first backup your original ~/.config/xfce4 directory since we are making changes to this directory.**]
 [/B]
Extract this zip file such that the extracted contents merge with the existing folders and overwrites any existing files within the merged folders.

The following command will do this for you in one go:
```

cd ~/ 
unzip -o OpenboxInstall.zip

```

The -o option makes sure it overwrites the files without prompting. It's almost done now.

**4.** Open the '*gnome-tweak-tool*' (or the unity-tweak-tool) and set the following:
> 
File manager handle the desktop => Off

In newer versions of the *gnome-tweak-tool* (Like in Ubuntu 16.04/18.04), the corresponding option should read:
> 
Icons on Desktop => Off


IT IS NOW DONE !!
*BY NOW, YOU ALREADY HAVE A FUNCTIONAL OPENBOX DESKTOP.*

**FOLLOWING STEPS ARE OPTIONAL, ONLY FOR THOSE WHO CARE FOR DESKTOP AESTHETICS.**
**5.** *This step is **optional***. 
> 
Download and install the open-sans-elementary and raleway-elementary fonts from the source links provided in the 'Sources and References' section at the end of this post.


**6.** Download and install [COLOR=#000000][Moka]("https://github.com/snwh/moka-icon-theme"), [arc]("https://github.com/horst3180/arc-icon-theme") or [/COLOR][MAC iOS]("https://dl.opendesktop.org/api/files/download/id/1474772478/Mac%20iOS%20Icon%20theme%20v2.tar.xz")[COLOR=#000000] icon themes. Also install the [arc gnome shell theme]("https://github.com/horst3180/arc-theme"). 
First install the arc-theme:
[/COLOR]```

wget https://github.com/horst3180/arc-theme/archive/master.zip
unzip -o master.zip
mkdir -p ~/.themes/arc-theme
mv ./arc-theme-master/common/* ~/.themes/arc-theme
rm -r arc-theme-master [COLOR=#000000][FONT=&amp]master.zip[/FONT][/COLOR]

```

Now install the *moka* icon theme:
```

wget https://github.com/snwh/moka-icon-theme/archive/master.zip
unzip -o master.zip
mkdir -p ~/.local/share/icons
mv ./moka-icon-theme-master/Moka ~/.local/share/icons
rm -r moka-icon-theme-master master.zip

```

Now install the *arc* icon theme:
```

wget https://github.com/horst3180/arc-icon-theme/archive/master.zip
unzip -o master.zip
mkdir -p ~/.local/share/icons
mv ./arc-icon-theme-master/Arc ~/.local/share/icons
rm -r arc-icon-theme-master master.zip

```

Now open either *lxappearance* (in terminal) or the *gnome-tweak-tool* (*gnome-tweaks* in Ubuntu 18.04 and later) and set the *shell theme* as *arc*, and *icon theme* also as *arc*.

**7.** Log out of current session. Select the *Openbox Session* from the login screen and then log into your account. If all gone well, your beautiful Openbox Desktop Session should be ready to serve you!
(*Just look for the "openbox gear" at the login screen and select it before logging into your account.*)

___________________________________________________________________________________________________________________________________________________________________
To undo the customized changes to your openbox session, or to renew the openbox configuration (in case you messed up while playing yourself with the configuration files) the following commands are here for you:
```

cd ~/.config/ && rm -rf openbox tint2 xfce4 plank
cd ~/.local/share/ && rm -rf xfce4 plank
cd ~/ && rm .compton.conf .conkyrc

```
____________________________________________________________________________________________________________________________________________________________________

Sources and References:
> 
1. Theme Mistral-Thin at: [https://www.box-look.org/p/1169127/](https://www.box-look.org/p/1169127/)
2. conky-google-now at : [http://satya164.deviantart.com/art/Conky-Google-Now-366545753](http://satya164.deviantart.com/art/Conky-Google-Now-366545753)
3. Fonts open-sans-elementary at:[https://github.com/frappe/fonts/tree/master/usr_share_fonts/truetype/open-sans-elementary](https://github.com/frappe/fonts/tree/master/usr_share_fonts/truetype/open-sans-elementary)
4. Fonts raleway-elementary at: [https://github.com/frappe/fonts/blob/master/usr_share_fonts/truetype/raleway-elementary]("https://github.com/frappe/fonts/blob/master/usr_share_fonts/truetype/raleway-elementary/Raleway-Medium.ttf")


---

### Post by Dennis N on 2017-04-29
Lubuntu uses openbox as window manager, so could Lubuntu be the starting point?

---

### Post by Frogs Hair on 2017-04-29
Moved to *Tutorials*

---

### Post by sbnwl on 2017-04-30
Thank you Mr. [**[COLOR=#C61919][B]Frogs Hair**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1024576").

---

### Post by sbnwl on 2017-04-30
> **Dennis N said:**
> Lubuntu uses openbox as window manager, so could Lubuntu be the starting point?

Yes, It can be. In fact you could try any Ubuntu derivative. It's fine.

---

### Post by again? on 2017-04-30
Well done. Nice use of the whisker menu with tint2.
Tested in Ubuntu-Gnome 17.04 and works.(Had to restart for the openbox session to appear in gdm)
Just needed a few tweaks to the autostart file  to run a polkit authentication agent and set a correct path to 
a desktop wallpaper.
Also edited the network interface, WOEID and a couple of other settings in the conky config.

---

### Post by sbnwl on 2017-04-30
@guber2
> **guber2 said:**
> Well done. Nice use of the whisker menu with tint2.
Tested in Ubuntu-Gnome 17.04 and works.(Had to restart for the openbox session to appear in gdm)
Just needed a few tweaks to the autostart file to run a polkit authentication agent and set a correct path to 
a desktop wallpaper.
Also edited the network interface, WOEID and a couple of other settings in the conky config.

Seen your screenshot and happy to have helped you. I could see you have changed the location for weather forecast by setting appropriate WOEID for your city. I have some suggestions to make it more beautiful:
1. Use Moka or [MAC iOS]("https://dl.opendesktop.org/api/files/download/id/1474772478/Mac%20iOS%20Icon%20theme%20v2.tar.xz") or arc icon theme.
2. Use the [arc gnome theme]("https://github.com/horst3180/arc-theme") in your gnome-session.
3. Your third launcher icon (for web browser) is missing in the xfce4 panel. Right click on this and edit it using automatic configuration provided for firefox/google-chrome.

I have also revised the tutorial post accordingly.

Here is how mine looks like:
[ATTACH=CONFIG]274882[/ATTACH]

---

### Post by Melodie on 2018-01-02
Hi, 

Bento Openbox Remix has been out since 2012, please feel free to give it a try and ask questions! [https://bentovillage.me/en/a-propos/](https://bentovillage.me/en/a-propos/) [https://linuxvillage.org/en/blog/2015/07/10/presentation-bento-trusty-rc2/](https://linuxvillage.org/en/blog/2015/07/10/presentation-bento-trusty-rc2/)  [http://downloads.linuxvillage.org/?C=M;O=D](http://downloads.linuxvillage.org/?C=M;O=D)

---

### Post by sbnwl on 2018-11-19
@[**[COLOR=#C61919][B]Frogs Hair**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1024576")

I think nobody reads the *Tutorials* these days.
Best would be to place in discussions.

---

### Post by wildmanne39 on 2018-11-19
Hello sbnwl, the tutorial section of the forum is still active and people do read and post new tutorials to this sub-forum, since this is a tutorial this is the correct sub-forum for your thread and will stay here.

Thanks for posting it and keeping it updated!

---

### Post by sbnwl on 2018-11-25
@[**[COLOR=#C61919][B]wildmanne39**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=508533")
Hello wildmanne39,
I have updated the tutorial and configuration files.
Strange enough, I never see the thread view count changing. Is the view count at fourms dead or broken?
I see the thread count for newer posts are still changing without any problems.

---

### Post by sbnwl on 2018-11-25
Hi all,
The tutorial is now updated. Please try, test and then share your Openbox experience.
Thank you.

---

### Post by wildmanne39 on 2018-11-25
The thread count is broken, it only shows a few then no more, there have been 12 views in the last 30 days.

---

