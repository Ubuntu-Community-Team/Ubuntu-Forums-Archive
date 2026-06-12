---
title: "Rolling out Ubuntu 8.04 to our office"
date: 2008-05-10
forum: Testimonials &amp; Experiences
---

### Post by kcnnc on 2008-05-10
In our office we have about 20 PCs and planning to scale up to around 100 PCs. Since most of the work are web-based (interacting with our web applications) and using word processor, migrating from XP (what we are using now) to Ubuntu make sense.

Since last week I downloaded 8.04 desktop, configured and tested.
Not having tried Linux desktop seriously since almost a decade ago, Ubuntu made a very impressive first impression.

Firefox, OpenOffice are there. A little search dig up information on how to set up Chinese input. Some configuration work to take out unnecessary applications (games, meda, etc.) and it's ready for prime time.

Today our first user is put on the test box and my plan is to monitor user experience and eventually roll out the the old and new staffs.

For the roll out, I had also found Clonezilla [http://www.clonezilla.org/](http://www.clonezilla.org/)  (based upon Ubuntu as well) to be extremely useful. It can be used to try different configurations and to roll-out configured image to other PCs.

So far, so good. I hope to report more as we progress.

Now to anyone who had rolled-out Ubuntu desktop to a large user group, here are some questions I have:
[LIST=1]
[*]Can you share some of your best practices. Things that you did that you were glad to have in place and works
[*]How do you partition the drive? (We use standard PC with SATA drive) What about user data? Local, separate /home partition, NFS?
[*]How about administration. How many people team you have? Tools? Remote maintenance?
[*]What about upgrade? Do you maintain a local apt-get mirror? Do you enable auto-update?
[/LIST]
Would like see what others had done and learn. Pointer to information would be most helpful.


Thank!

---

### Post by mybunche on 2008-05-10
That's good news to hear. Unfortunately, I have no idea how to help you, just enjoyed reading your future plans.

---

### Post by sports fan Matt on 2008-05-10
The only thing I can tell you ius I always auto update everything.  I think its WONDERFUL that you are bringing Ubuntu to an office enviroment :)

---

### Post by hyper_ch on 2008-05-10
> **kcnnc said:**
> *Can you share some of your best practices. Things that you did that you were glad to have in place and works
Make regular automatic backups :)

> **kcnnc said:**
> *How do you partition the drive? (We use standard PC with SATA drive) What about user data? Local, separate /home partition, NFS?
The actual partitioning is simple... question is only what you do... with regards to backups and stuff you may want to the user home on a centralized computer... that way you only have to backup that one...

---

### Post by songshu on 2008-05-10
first of all, take it slow and always eat your own dogfood first. but that is just common sense not just typical to ubuntu or Linux.

at the moment i have a 10 desktop ubuntu gutsy with a single debian server set up (multiple server instances with vserver)

the desktop is basically a slightly adjusted Xubuntu version with openoffice added etc.., upon the ubuntu base i install this
```
acpi, acpi-support, acpid, alsa-base, alsa-utils, anacron, mozilla-plugin-vlc, apmd, avahi-daemon, bc, ca-certificates, cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gutenprint, dbus, dc, doc-base, foomatic-db, foomatic-db-engine, foomatic-filters, gdebi, gdm, genisoimage, ghostscript-x, gnome-app-install, gnome-mount, gnome-system-tools, gtk2-engines, gtk2-engines-murrine, gtk2-engines-pixbuf, gtk2-engines-ubuntulooks, gtk2-engines-xfce, hal, hotkey-setup, language-selector, lftp, libgl1-mesa-glx, libglib2.0-data, libglut3, libsasl2-modules, libxp6, openprinting-ppds, pnm2ppa, powermanagement-interface, readahead, screen, scrollkeeper, smbclient, software-properties-gtk, synaptic, tango-icon-theme, tango-icon-theme-common, thunar, thunar-archive-plugin, thunar-media-tags-plugin, thunar-thumbnailers, thunar-volman, ttf-bitstream-vera, ttf-dejavu-core, ttf-freefont, ubuntu-artwork, unzip, update-manager, usplash, vim-runtime, x-ttcidfont-conf, xfce4-mcs-plugins, xfce4-mcs-plugins-extra, xfce4-mixer, xfce4-panel, xfce4-session, xfce4-terminal, xfce4-utils, xfdesktop4, xfwm4, xfwm4-themes, xkb-data, xorg, xterm, zenity, zip, app-install-data-commercial, apport-gtk, avahi-autoipd, bluez-cups, bluez-utils, bogofilter, brasero, cdparanoia, cups-pdf, displayconfig-gtk, dvd+rw-tools,  file-roller, firefox, foo2zjs, foomatic-db-hpijs, fortune-mod, gcalctool, gcc, gimp, gnome-accessibility-themes, gnome-games, gnome-power-manager, gnome-screensaver, gnome-system-monitor, gucharmap, hal-cups-utils, hplip, jockey-gtk, laptop-detect, libgl1-mesa-dri, libgnome2-perl, libgoffice-gtk-0-6, libnss-mdns, linux-headers-generic, make, min12xxw, mousepad, mozilla-thunderbird, network-manager-gnome, notification-daemon, onboard, orage, pidgin, pidgin-otr, powernowd, pxljr, python-exo, gthumb, scim, scim-gtk2-immodule, scim-tables-additional, screensaver-default-images, splix, system-config-printer-gnome, ttf-arabeyes, ttf-arphic-uming, ttf-indic-fonts-core, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-thai-tlwg, ttf-unfonts-core, ubufox, update-notifier, wodim, wvdial, xcursor-themes, xdg-utils, xfce4-appfinder, xfce4-battery-plugin, xfce4-clipman-plugin, xfce4-cpugraph-plugin, xfce4-dict-plugin, xfce4-fsguard-plugin, xfce4-governor-plugin, xfce4-mailwatch-plugin, xfce4-mount-plugin, xfce4-netload-plugin, xfce4-notes-plugin, xfce4-places-plugin, xfce4-quicklauncher-plugin, xfce4-screenshooter-plugin, xfce4-smartbookmark-plugin, xfce4-systemload-plugin, xfce4-verve-plugin, xfce4-weather-plugin, xfce4-xkb-plugin, xfprint4, xscreensaver-data, xscreensaver-gl, openoffice.org, openoffice.org-gtk, openoffice.org-style-tango, lightning-extension
```

this because i found that simply to be more stable and just enough features that i need.
the last time i tried evolution it was on par with outlook, both feature wise and number of crashes...altough i haven't used or seen any of the two anymore since the last two years.
thunderbird never crashed on me and has great IMAP support, is simple to use and the feature set is somewhere between outlook expres and outlook.

also thunar, the xfce file browser that looks just like nautilus is a lot more stable and faster..
but hey, its all about choice and your mileage may vary..so its up to you.

for a desktop i just install a 10GB / partition for root and 1GB /SWAP and the rest for /home
just in case of a really screwy wrong configuration or mayor upgrade, you always have the option to quickly re install if needed without disturbing any of the users bookmarks etc. they won't even notice.

i'm using apt-cacher on the server and can really recomend it, basically it stores every package you ever download with apt-get including security updates so you only have to download once. but exactly that so you dont have to download anything you don't use.
here's what i use [http://songshu.org/doku/doku.php?id=apt.cipar.net](http://songshu.org/doku/doku.php?id=apt.cipar.net)

i'm planning for a bigger deployment at the moment in different locations, so i'm working on a set up for the clients that allows me not to be there actually. 
this page [http://songshu/doku/doku.php?id=custom-ubuntu](http://songshu/doku/doku.php?id=custom-ubuntu) is what i'm trying to do, still a work in progress but maybe you can pick up an idea. doing a preseeded install over the network allows me to have any user pop in a cd and install everything within about 15 minutes. al they need to do is press enter to start the installation, works really sweet.

the amount of admins? the thing with *nix administrators is that they are a lot more expensive according to the research done by microsoft
this is absolutely true we say, but then again, you also need less of them ;)
i'm planning to maintain 70 desktops when the page i mentioned is finished, pretty confident that it will not be a problem to do that on my own once it is finished.

---

### Post by kcnnc on 2008-05-11
> **hyper_ch said:**
> Make regular automatic backups :)

Any suggestion of the setup?
Rsync?
The target user group don't store much data locally, so it isn't a problem now. But eventually when other user start getting on this desktop.

> **hyper_ch said:**
> The actual partitioning is simple... question is only what you do... with regards to backups and stuff you may want to the user home on a centralized computer... that way you only have to backup that one...

Have thought of that too. For now just to keep the complexity low since this is just one of many things on our plate.

---

### Post by kcnnc on 2008-05-11
Hi songshu,

looks like you are pretty much doing similar things... Thanks for your input!

> **songshu said:**
> the last time i tried evolution it was on par with outlook, both feature wise and number of crashes...altough i haven't used or seen any of the two anymore since the last two years.
thunderbird never crashed on me and has great IMAP support, is simple to use and the feature set is somewhere between outlook expres and outlook.

The problem with evolution is that a lot of the gnome environment seems to be linked to it. I tried to remove it and lots of dependencies came up.

Our requirement is rather simple, web and some text processing, so mail client is not needed.


> **songshu said:**
> also thunar, the xfce file browser that looks just like nautilus is a lot more stable and faster..
but hey, its all about choice and your mileage may vary..so its up to you.

Heard good things about xfce but my limitation is time to try new things.

> **songshu said:**
> for a desktop i just install a 10GB / partition for root and 1GB /SWAP and the rest for /home
just in case of a really screwy wrong configuration or mayor upgrade, you always have the option to quickly re install if needed without disturbing any of the users bookmarks etc. they won't even notice.

All the PCs comes standard with 80G hdd. The user hard use half of it. Right now it is 2G swap and 30G /

In the next version I will probably do 
2G swap 5G / 25G /home

I'm thinking:
512M /boot
the rest LVM, then everything can be move around in future.
Too much for a desktop?

> **songshu said:**
> i'm using apt-cacher on the server and can really recomend it, basically it stores every package you ever download with apt-get including security updates so you only have to download once. but exactly that so you dont have to download anything you don't use.
here's what i use [http://songshu.org/doku/doku.php?id=apt.cipar.net](http://songshu.org/doku/doku.php?id=apt.cipar.net)


Thanks for this tip. Looking for something like this.

> **songshu said:**
> i'm planning for a bigger deployment at the moment in different locations, so i'm working on a set up for the clients that allows me not to be there actually. 
this page [http://songshu/doku/doku.php?id=custom-ubuntu](http://songshu/doku/doku.php?id=custom-ubuntu) is what i'm trying to do, still a work in progress but maybe you can pick up an idea. doing a preseeded install over the network allows me to have any user pop in a cd and install everything within about 15 minutes. al they need to do is press enter to start the installation, works really sweet.

Very interesting! I like to see this work and maybe work on it as well.

> **songshu said:**
> the amount of admins? the thing with *nix administrators is that they are a lot more expensive according to the research done by microsoft
this is absolutely true we say, but then again, you also need less of them ;)
i'm planning to maintain 70 desktops when the page i mentioned is finished, pretty confident that it will not be a problem to do that on my own once it is finished.

We are targeting 100 desktops. I don't forsee major problem but there are always small user issues to deal with. Like this morning, the test user asked a few questions on how to use certain feature of the chinese input (I must say SCIM did quite an impressive work)

And it is indeed a problem to get an admin that is conversant with Linux. Perhaps we will just get a fresh person and train him/her.

Your wiki has very good information that I need. I'm thinking of setting up a wiki as well to share information with people doing similar thing.

---

### Post by freebeer on 2008-05-11
FWIW, I use rsync to backup my office machines (Win boxes) to my Linux server, then rsync via ssh the server data to an offsite machine.  So far it works well.

---

### Post by songshu on 2008-05-12
scim? chinese?

its the best option i have heard and seems to be a better option then the default mechanism in XP, but then there are others as well i think like njstar and stuff.

not that i have any clue because my chinese is limited to ordering beer, say bottoms up and i love you, but i asked around and that was the answer i got.
i'm actually planning deploying to it in china so i would more then appreciate to know your findings on that, 

i use dokuwiki, because it was simple to install, easy to edit and it saves me having to look where i stored my notes if the previous day was "gambay" night ;)

for the partitioning you could do exactly that, but depending on what you need to its best to keep it as simple as possible, you will not need to do the typical "server" setup with /boot /var /usr etc..

the reason i keep plenty of space for / is because the thing that actually could fill up easily is /tmp, depending on how many dvd's they are burning 5GB is fine indeed till max 10GB

i never actually never do more than 1GB of RAM which is already to much, if it would ever even fill up that far, people would already have done the hard-reboot long before that.

---

### Post by CREEPING DEATH on 2008-05-12
I use 10 gigs for /, 1-3X RAM aount for Swap (3X with <512, 2X with 512-1024, 1X with >1024), and the rest for /Home.  / needs to be able to hold the entire OS and cache all the updates and such, 10 gigs makes sure there'll always be room.

CD

---

