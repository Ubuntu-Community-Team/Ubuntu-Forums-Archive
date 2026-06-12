---
title: "Switching to OpenSUSE 11 KDE from Ubuntu 8.04--what can I expect?"
date: 2008-07-07
forum: The Cafe
---

### Post by 50words on 2008-07-07
I use Ubuntu 8.04 on my work desktop and on my ThinkPad laptop, but I want to try another distro, and since Lenovo sells ThinkPads with SLED pre-installed, I figure OpenSUSE is a good choice.

Also, I want to try KDE, since I already use a few KDE apps, but they don't always look right in Gnome.

What are the big differences I can expect, both between Ubuntu and OpenSUSE and Gnome and KDE?

Any tips for someone making this switch?

---

### Post by ice60 on 2008-07-07
i've used suse 10.2 for ages, but not with KDE. anyway, here are some links that might be helpful.

repos, the Packman repo is really good -
[http://www.benkevan.com/wiki/index.php/Helpful_openSUSE_11.0_Repositories](http://www.benkevan.com/wiki/index.php/Helpful_openSUSE_11.0_Repositories)

you can search for packages here (or install webpin and do it from a terminal) -
[http://packages.opensuse-community.org/](http://packages.opensuse-community.org/)

forums -
[http://forums.opensuse.org/](http://forums.opensuse.org/)

howtos -
[http://en.opensuse.org/Howtos](http://en.opensuse.org/Howtos)

wikis -
[http://opensuse-community.org/Welcome_to_openSUSE-Community.org](http://opensuse-community.org/Welcome_to_openSUSE-Community.org)
[http://en.opensuse.org/Welcome_to_openSUSE.org](http://en.opensuse.org/Welcome_to_openSUSE.org)

the irc channel at freenode is fairly helpful, unless it's changed much in the last 6 months.

one thing i remember with 10.2 (11 might not do this) is it doesn't empty the tmp directory ever! i had to reconfigure it to empty it at shutdown.

the thing i like about suse is unlike ubuntu suse develops just about everthing it uses. i haven't used it much, but suse has it's one-click install, it adds the repo for you and downloads and installs the software you want.

---

### Post by FyreBrand on 2008-07-07
I really like SUSE.  Everything seems to fit so nicely regardless whether you're using gnome or kde.  The one click install is one of my favorite things.  It's somewhere in between the massive repo approach of debian and the Red Hat / Windows approach to rpm single binary installs.

---

### Post by 50words on 2008-07-07
What is the one-click install? (Still waiting for it to download so I can see for myself.)

---

### Post by ice60 on 2008-07-07
there's some one-click installs on this page, just click it and it adds the nvidia repo and downloads and installs the nvida dirver. maybe it even configures it too?? -
[http://en.opensuse.org/Nvidia](http://en.opensuse.org/Nvidia)

here's more about it -
[http://en.opensuse.org/Standards/One_Click_Install](http://en.opensuse.org/Standards/One_Click_Install)
maybe it's more advanced then on this page, i don't know?? -
[http://news.opensuse.org/2007/08/21/sneak-peeks-at-opensuse-103-1-click-install/](http://news.opensuse.org/2007/08/21/sneak-peeks-at-opensuse-103-1-click-install/)

---

### Post by Polygon on 2008-07-07
i tried it, but sadly wasnt able to give it a very good trial run cause my wireless woulden't work even after installing/compiling the drivers, but it seems good once you get used to it.

---

### Post by pape on 2008-07-07
The "brain" of openSUSE is the YaST configuration utility - try spending some time to get familiar with it. In KDE menu, it's under "System".

A number of interesting additional software repositories are listed here:

[http://en.opensuse.org/Additional_YaST_Package_Repositories](http://en.opensuse.org/Additional_YaST_Package_Repositories)

For instance for VLC player with all bells and whistles, add the VideoLan repository (in addition to Packman), and install packages vlc vlc-mozillaplugin libdvdcss libdvdnav w32codec-all.

Also note that Compiz-Fusion can be installed with one click:

[http://en.opensuse.org/Compiz_Fusion](http://en.opensuse.org/Compiz_Fusion)

It can be activated from settings->KDE components->Session Manager from the window manager tab.

---

### Post by madjr on 2008-07-07
> **ice60 said:**
> there's some one-click installs on this page, just click it and it adds the nvidia repo and downloads and installs the nvida dirver. maybe it even configures it too?? -
[http://en.opensuse.org/Nvidia](http://en.opensuse.org/Nvidia)

here's more about it -
[http://en.opensuse.org/Standards/One_Click_Install](http://en.opensuse.org/Standards/One_Click_Install)
maybe it's more advanced then on this page, i don't know?? -
[http://news.opensuse.org/2007/08/21/sneak-peeks-at-opensuse-103-1-click-install/](http://news.opensuse.org/2007/08/21/sneak-peeks-at-opensuse-103-1-click-install/)

i think **one-click-install**

is similar to **mint-install**

mint-install backups the original repos (incase of system freeze or power interruption) before adding different repos and installing the software.

i don't know which one is better thou, worth trying :)

---

