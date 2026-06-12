---
title: "edubuntu trusty notes -  gnome (no effects)"
date: 2013-10-31
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-10-31
While trying to log on to gnome -flashback (no effects) lightdm login does not present the little icon with my user_name. I have to click 'Lightdm Manager' to bring up the icon.

Also .. the screen gnome background screen that is presented in ubiquity and then chosen  will flicker once real fast and then go to a default background not as originally depicted in ubiquity.

Current default background for Edubuntu Gnome Flashback-no effects:

```

ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
ventrical@ventrical-MS-7798:~$ 


```

---

### Post by kansasnoob on 2013-10-31
I'm curious what method you used to upgrade Edubuntu from Saucy to Trusty?

I noticed a few days ago that the upgrade tests were up at the QA Tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

Wow, glad I looked :)

Lots of early testing images there now!!!!!!!!!!!!

Expect things to blow up a lot for a few weeks :D

---

### Post by ventrical on 2013-11-01
> **kansasnoob said:**
> I'm curious what method you used to upgrade Edubuntu from Saucy to Trusty?

I noticed a few days ago that the upgrade tests were up at the QA Tracker:

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

Wow, glad I looked :)

Lots of early testing images there now!!!!!!!!!!!!

Expect things to blow up a lot for a few weeks :D


```

sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list


```



Yeah.. it's just wild in there.  I didn't think they would start so early.  Don't forget, XP EOL is slowly approaching so  Ubuntu has to be agressive. Maybe thats why.

---

### Post by ventrical on 2013-11-01
kansasnoob wrote:

> 

I wanted to get the "Run Command Prompt" back by pressing Alt+F2 just as  it was in Gnome 2. This can be quite useful if you should ever do  something silly like remove both panels and need to launch the terminal  or another application without being able to access the menu(s).


That is now operable by default in Edubuntu Trusty gnome-flashback (no -effects).

---

### Post by ventrical on 2013-11-01
kansasnoob wrote:

```

sudo apt-get install gnome-panel


```

gnome panel is installed in Edubuntu Trusty by default.

---

### Post by grahammechanical on 2013-11-01
I have just installed Edubuntu saucy. Gnome Fallback is available as an installation option. And it gives Gnome Flashback and Gnome Flashback (no effects) as log in options along with Ubuntu. But Gnome Flashback was a mixture of Gnome panel and Unity. The Launcher was there as was a bottom panel. The top panel did not have any menus or indicators. Needed the terminal to shutdown.

I have now updated it to trusty and the three options work as they should. Although I do not see much difference between Gnome Flashback and Gnome Flashback (no effects). I expect it is more noticeable with lower spec hardware. I also noticed that both flashback options seem to have the right side of the Unity top panel as well as the left side with Applications and Places.

I wondered about the Light Display Manager option but I did not try it. I wonder if it is in preparation for having a choice of Light Display Manager and Mir Display Manager. I remember someone saying something about getting Mir as a log in option at some point in development.

I really do not see how that would be possible because LightDM is more than a login manager and Mir will be also. Surely either of them would be running long before the login screen was needed. Unless it sets the option for the next boot.

I will install Ubuntu Gnome (trusty) tomorrow and see what happens with Flashback there.

Regards.

---

### Post by ventrical on 2013-11-01
I had  the same problem as you did , with gnome-flashback (with effects) and update/upgrade did not resolve it. However, I chose Gnome-flashback from Ubiquity. This was suppossed to install GDM!!  I agree with you 100% here but I also think there is a battle  going on behind the scences (virtually) between gdm and lighdm. With this install as it boots into the DM there is the reminiscent flash of gdm blue in the background, but then lightdm takes over. On another basic ubuntu (trusty)install I actually installed gdm, chose that , then rebooted and now when it boots up it will flash several times with the report  "Lighdm stopping" flicker, flicker, flicker.. then GDM  comes up and I can log on.  Could be a bad graphics card but worked great with Lucid - so nouveau, regardless of if we use gnome-no effects, is vomiting out the old graphics adapters still .

So it is not a matter of salvaging legacy machines then. It is about preparing to upgrade your hardware. Noob working endusers just don't have the time to customize their networks in this fashion and it is even less economical come to think about it.

 Also, there is a battle going on with xmir, X ,lightdm and gdm. These are where the monster bugs lay. This is where there are worlds in collision, side by sides , busted stacks and interfected depends. It's like the kernel is rolling along smoothly, wheels , bells and whistles, waiting to roll like a game mech on a pinball machine and something , some process or interupt, object or module is becomming like a small nut or bolt and naturally the kernel has to put on it's brakes, stop rolling, spit out the plug nickel, bolt or whatever got dropped into it and pull up it's bootstraps in an attempt to find the right shim  to get rolling again. What that bug is .. I dunno atm .. but it's there....plain as the noses on our faces.

 regards..

---

### Post by grahammechanical on 2013-11-01
Oh, the next year will be interesting for practical Ubuntu+1 testers.
 
On Ubuntu Mir will replace Xserver, Lightdm, and Compiz. And the Gnome devs are working on a replacement for GDM that is based on the Wayland protocol. The KDE devs have said that they are not diverting resources from developing KDM until Wayland proves itself. And the XFCE devs are fewer in number than the Xubuntu devs. Redhat and Intel are working together to make Gnome shell a Wayland compositor.

So, bugs a plenty will be on their way. It seems to me, speaking in ignorance, that the Ubuntu devs will be in the best position to patch Mir to Gnome, Kde, Xfce, Lxde and any other DE sitting already on Ubuntu.

Regards.

---

### Post by ventrical on 2013-11-01
Hmmmm.... Maybe GRuDM might be the answer? Grand Unified Display Manager  :)lol

Regards..

---

### Post by QDR06VV9 on 2013-11-01
> **grahammechanical said:**
> Oh, the next year will be interesting for practical Ubuntu+1 testers.
 
.

With Practical being Key!;)
Let's see? Hum, Wisdom or Frustration?
Well "like a moth to flame":D

---

