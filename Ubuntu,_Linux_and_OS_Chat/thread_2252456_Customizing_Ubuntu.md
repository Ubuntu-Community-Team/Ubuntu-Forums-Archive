---
title: "Customizing Ubuntu?"
date: 2014-11-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Aidan_Owen on 2014-11-12
I have an Asus n56 laptop and I was running Windows 8 on it from it's purchase date (June 2014) until it got screwed up so badly that I would have to reinstall the OS in October. I went "screw it" and got Ubuntu 14.04 LTS on my laptop. I like it a LOT, but the one thing that I'm really on the fence about is customization. I tried Mint too and I like how you can customize a lot of stuff out of the box, where I don't see a lot of customizability options in Ubuntu. Are there any ways I can customize Ubuntu more than the wallpaper? If I do decide to switch to Mint for customizability will I be able to transfer installed packages and such?

---

### Post by cal1j on 2014-11-12
Hi,

Ubuntu can be RICHLY and almost unlimitedly customized. First of all, you can install other desktop environments on Ubuntu and choose between the built in Unity, Cinnamon, Gnome, LXDE, and KDE. These are very different environments. Secondly, you can change tons of settings by installing Unity Tweak. Here is how I do it: 

                sudo add-apt-repository ppa:tualatrix/ppa  
                sudo apt-get update 
                sudo apt-get install ubuntu-tweak

Also there is the compizconfig-settings-manager. Both it and tweak are are well documented on Google. To install compizconfig-settings-manager, run:

                sudo apt-get install compizconfig-settings-manager

Further by looking through the thousands of apps, you will find many that you may like better than, or in addition to the built in ones. For example, I like to use terminator for my terminal emulator. The terminal can be customized using the .bashprofile and .bashrc files. 

Also, you can customize the grub splash screen too. 

Any more specific questions I'd be glad to answer too. Cheers

---

### Post by ssam on 2014-11-12
Mint uses the highly customisable MATE desktop, which is based on GNOME 2. You can install MATE in ubuntu, and then select it at log in. See [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)

---

### Post by buzzingrobot on 2014-11-12
Customization pretty much depends on the Desktop Environment you are using.  The only way to really know what you prefer is to take a look at each. Some DE's enable more customization than others.  Of course, if you like a DE's default setup, then you won't need to do as much customization.  And, if you just don't like a DE, no amount of customizing is likely to change your mind.

Mint is based on Ubuntu and offers the Cinnamon, Mate, KDE and XFCE DE's.

Ubuntu's default DE is Unity, then there's Kubuntu (KDE), Xubuntu (XFCE), Lubuntu (LXDE) and the not-yet-offical Ubuntu Mate.

---

### Post by vasa1 on 2014-11-12
> **Aidan_Owen said:**
> ...? If I do decide to switch to Mint for customizability **will I be able to transfer installed packages** and such?
I don't know if that is possible or if it is, whether it's a good idea. Of course, you haven't specified what you mean by "and such", so that depends :)

Whay don't you try out Live USBs of whatever you shortlist and then do a clean install of that?

---

### Post by buzzingrobot on 2014-11-12
Mint uses the Ubuntu repos plus their own.  The same packages available to you in any Ubuntu flavor are also available to you in any Mint flavor.

That said, Mint is a different distribution, not something that can be installed "on top of" Ubuntu while you preserve existing installed packages.

Mint follows a slightly different default strategy regarding updates.  You can read about it at their site.  But, any of Mint's Desktop Environments are also available to install on Ubuntu Unity or in distinct distributions. The differences there come down to theming, apps installed by default, and the default configuration choices each makes.

---

### Post by thiebaude on 2014-11-12
Ubuntu is very customizable,[http://noobslab.com]("http://noobslab.com"). I have My ubuntu set to the Mac OSX Theme.:D

---

### Post by Aidan_Owen on 2014-11-12
Thanks for all the awesome help, guys! :D

---

### Post by grahammechanical on 2014-11-12
It all comes down to the approach of the developers to the development of the distribution.

The approach of Ubuntu, as far as I can tell, is to not overly complicate things for the ordinary user while allowing space for Community developers to add value. So, Ubuntu has two themes and not 22 themes. There are utilities for adjusting certain settings but there are are community tools that will give even greater scope for making adjustments.

Ubuntu also has limits as to what the user can change because it is outside the design goals of the Ubuntu project. If this causes us to feel restricted or deprived in any way, then as already been noted, there are alternatives.

With Free and Open Source Software (FOSS) we have choice.

Regards

---

### Post by craig10x on 2014-11-12
And of course, it should be noted that even ubuntu includes a few customizations you can do (in system settings) such as shrinking the size of the unity icons (pixel size) auto-hiding the unity launcher (dock) so that it only pops out when needed, and you can also put the menus back in the windows (the default is the global menu style where the menus appear in the top panel)...You can add the "workspace switcher" and also turn off the online searches (such as the amazon searches) in the dash search (that would be found in the "privacy section")...Adding "ubuntu tweak" (as was previously mentioned) would expand that even more, if you want...

---

