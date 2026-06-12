---
title: "indicator-network vs network-manager: Is this a valid bug?"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-29
Installing indicator-network it will remove network-manager, network-manager-gnome. As soon as apt finishes the upgrade process. the user will have no valid setup in /etc/network/interfaces and /etc/resolv.conf. No working network. At this point, trying to uninstall indicator-network or reinstall network-manager won't work, as the PC is not connected. 

Indicator-network won't display until the DE is restarted, so the user won't even get a visual clue of what he installed.

I know it's easy for us to quickly fix it: One can use cached packages, get an IP via dhclient or just manually edit /etc/network/interfaces and /etc/resolv.conf, ifdown/ifup the NIC, get ourselves a working connection and then reinstall network-manager (which will then remove indicator-network). 

But an inexperienced user will definitely have borked his PC out of his fixing capabilities. With no network theres also no browsing for online support. He'll likely go for a reinstall.

This is one of those cases in which I'm not sure if reporting it as a bug makes sense. network-manager is OK and so is indicator-network. They're not broken. But, is a threat to beginners ability to use their PCs a bug?  

:confused:

Regards,
Effenberg

---

### Post by dino99 on 2012-03-29
i have none of those installed, are they usefull ?

but as im fully happy with wicd, then i cant elaborate about the buggy network-manager :( (so numerous bugs on launchpad, and seems nobody try to fix network-manager)

---

### Post by effenberg0x0 on 2012-03-29
> **dino99 said:**
> i have none of those installed, are they usefull ?

but as im fully happy with wicd, then i cant elaborate about the buggy network-manager :(

network-manager is a default in a new install. It has bugs, definitely. But, anyway, it seems to work for the most part for the majority of users. As It's sort of similar to what users have on Windows, I'd say it's useful: Just a GUI, friendly way to connect to wired/wireless networks. That's it. no more no less. However, in the background, it directly manages the interfaces, DNS, etc. So, removing it means the user must be able to manually set up a connection.

Tutorials online praise indicators as a nice way easily customize Ubuntu. indicator-network uses connman (I think). It would be an alternative to network-manager. But, after installing indicator-network, the user has no network (because network-manager was removed and indicator-network and connmann were not loaded). 

So, in my POV, it's like having something like, let's say "indicator-hellokitty". Very appealing and seemingly harmless. But, when installed, indicator-hellokitty removes Unity. It's not a bug in either of these two packages, but installing the first "breaks" the user PC unless he knows exactly what he's doing. However, we can safely assume that a large percentage of users don't know what they're doing. So... what to do in this case? Report as bug? 

Regards,
Effenberg

---

### Post by lucazade on 2012-03-29
> **effenberg0x0 said:**
> Installing indicator-network it will remove network-manager

But an inexperienced user will definitely have borked his PC out of his fixing capabilities. With no network theres also no browsing for online support. He'll likely go for a reinstall.


Is an inexperienced user going to remove the  standard network-manager for the indicator-network? I doubt, sincerly. :)
Not a great bug, but yes a warning would be nice!

---

### Post by NHclimber on 2012-03-29
Definitely a bug.

I'm a little confused though:  did apt-get not get connman at all (because it removed network-manager first) or does connman just not have a default working configuration?

Also, for future reference, you should be able to get network-manager back locally with:
```
sudo dpkg -i /var/cache/apt/archives/network-manager*.deb
```

---

