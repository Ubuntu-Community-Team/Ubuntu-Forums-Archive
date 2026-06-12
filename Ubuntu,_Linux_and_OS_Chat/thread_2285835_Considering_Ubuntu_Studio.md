---
title: "Considering Ubuntu Studio"
date: 2015-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by joseph-anthony-king on 2015-07-08
Hello everyone, I've been using Ubuntu for about two years and I've never really been satisfied with the Unity desktop.  I think Unity is great for productivity but I always felt like the launcher was pushing my work into the corner... silly I know but the great thing about  Linux is the customization for silly preferences!

I'm upgrading my hard drives this month and I'm considering Ubuntu Studio.  I like the suite of tools it comes with but the Xfce desktop appears a little dated.  My computer is an Asus G75VW and it has a decent graphics card that can handle composting.  Does anyone have any experience using advanced compositing effects and recommendations for a polished theme?

Alternatively, has anyone installed the Ubuntu Mate desktop on top of Ubuntu Studio?  To Unity's credit it doesn't look like Windows or OSX but the same can be said of Mate, but it does keep my work front and center.

Thanks for anyone who can make any recommendations!

---

### Post by dawiba2 on 2015-07-08
I think you've kind of answered your own question here :)

However, if you're not keen on Xfce, you could just install Ubuntu Mate (or any other flavour you like) and [URL="https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu#Installing_Packages"]install Ubuntustudio metapackages
[/URL]
Hope that helps

---

### Post by MartyBuntu on 2015-07-09
> **joseph-anthony-king said:**
> 

Alternatively, has anyone installed the Ubuntu Mate desktop on top of Ubuntu Studio?


I use the MATE desktop with Ubuntu Studio 14.04 64bit LTS. Works just fine, although you will have some menu duplications when you add the MATE desktop with Ubuntu Studio, which ships with Xfce by default.

---

### Post by Bucky Ball on 2015-07-09
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Try them all from install media without installing (or as virtual machines) and see what you like. Xubuntu, or should I say xfce4, is highly configurable.

If you want to 'roll your own' why not [install the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") and build it up from there. You add your own desktop and everything else. If you want the UStudio packages, just install 'ubuntustudio-audio' or whatever else you want (installing ubuntustudio-desktop is the same as installing Ubuntu Studio so waste of time installing the mini.iso first if you intend to go there). You can install these directly from the command line or using Software Centre or Synaptics:

```
sudo apt-get install ubuntustudio-audio
```

... for example. The metapackages link provided by dawiba2 would work, but provides more info than you would need to install packages from a package manager or terminal. 

Incidentally, you don't need to install a whole new OS if all you want is to change your desktop environment. xfce4 is used by Xubuntu, lxde for Lubuntu, there are instructions for installing the mate DE, and ... the list goes on. Just install the DE in Ubuntu, log out, choose from Sessions, log in, you're there. New DE.

Good luck with it.

---

