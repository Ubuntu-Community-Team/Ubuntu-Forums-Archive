---
title: "Shorewall V Guarddog"
date: 2005-01-02
forum: Server Platforms
---

### Post by britishtrident on 2005-01-02
My setup is pretty simple an a desktop PC that also acts as an internal FTP server for holding dailly backups from Windows PCs. 
Internet connection is via a NATS router but I have always run internal firewalls to protect against attacks from trojans that might get on to the Windows PCs.
I have installed Shorewall but I really don't like it and have still to create /etc/shorewall/shorewall.conf file to get it working. 

In the past I have used GuardDog but atempts to compile  it on Ubuntu from a tar ball fail due to dependancy problems.
Is GaurdDog  available  with its required dependancies in .deb form  from another  repsitory

---

### Post by britishtrident on 2005-01-02
Ah 1 found GuardDog in Universer repository  --- installs and runs more or less OK

---

### Post by Bart Van on 2005-01-02
I installed Guarddog 2.3.0-2 from the Ubuntu universe repository without problems... 
It's a great firewall application, easy to use and gives full stealth (according to grc.com).

Negative sides are that it needs quite a lot of kde packages that you probably won't need for anything else on a standard ubuntu desktop, and the font is dead ugly in Ubuntu... (Apparently this can be fixed by installing and running kcontrol - see [this post](http://www.ubuntuforums.org/showthread.php?t=1441&highlight=kde+font))

To enable universe:
> Universe is one of the repositories used by synaptic package manager.
By default this one is disabled, to use it run the synaptic package manager and go to the settings/repositories menu and click on it.
A box will open showing the repositories, just put a tick in the universe ones to enable them.[(ubuntulinux.org)](http://www.ubuntulinux.org/support/documentation/faq/kde/talkback/1101662715/view?searchterm=universe)

---

### Post by britishtrident on 2005-01-02
[QUOTE=Bart Van]I installed Guarddog 2.3.0-2 from the Ubuntu universe repository without problems... 
It's a great firewall application, easy to use and gives full stealth (according to grc.com).

Negative sides are that it needs quite a lot of kde packages that you probably won't need for anything else on a standard ubuntu desktop, and the font is dead ugly in Ubuntu... (Apparently this can be fixed by installing and running kcontrol - see [this post](http://www.ubuntuforums.org/showthread.php?t=1441&highlight=kde+font))

To enable universe:
[(ubuntulinux.org)](http://www.ubuntulinux.org/support/documentation/faq/kde/talkback/1101662715/view?searchterm=universe)[/QUOTE]
 Even with the full KDE installed Guarddog is still very ugly  --- I suspect fonts are substituted

---

