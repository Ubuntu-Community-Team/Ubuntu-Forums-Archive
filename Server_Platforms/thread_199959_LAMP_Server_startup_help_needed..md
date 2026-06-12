---
title: "LAMP Server startup help needed."
date: 2006-06-19
forum: Server Platforms
---

### Post by konacoffeeguy on 2006-06-19
Hello, 
   I built a server mainly for a learnng experience, but also because I would like to start hosting my own website online without leaving my desktop on all the time. I downloaded and installed the Dapper Server Cd and did a LAMP install. It then takes me to a command line where I became really...well lot confused but had the question... what do I do now? I belive I need to somehow configure my server so that it has a static ip? is that correct? I believe if I knew what I needed to do I could figure most everything out on my own, but as this is my first server ever, would anyone be able to help me out in telling me what steps I need to take to set up a server that I could host a website on? Thanks to whome ever helps, 
 
Mahalo,
Konacoffeeguy

---

### Post by az on 2006-06-19
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by glotz on 2006-06-19
Would this be of use? [ Ubuntu Server Guide](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

---

### Post by houstonbofh on 2006-06-20
A lot of people may hate this but "apt-get install ubuntu-desktop" or "apt-get install xbuntu-desktop" might help.  GUI tools are a lot more intuitive for new users.  However, if you are really asking, "How do I get a box on the Interweb" I can't help you. :D

---

### Post by glotz on 2006-06-20
And if you plan to get rid of those later, don't use apt-get, use aptitude!

---

### Post by flash777 on 2006-06-21
[QUOTE=glotz]And if you plan to get rid of those later, don't use apt-get, use aptitude![/QUOTE]

Why do you say that? Wouldn't "sudo apt-get remove xxx" do the same? I tried aptitude this morning and its pretty cool. I'll use it more. But I want to know if there is something behind your statement besides the ease of use.

---

### Post by glotz on 2006-06-21
Yes there is, aptitude will remember if it had to install any dependencies and will remove those too when uninstalling, unlike apt-get.

---

### Post by houstonbofh on 2006-06-21
To remove everyhting installed with "ubuntu-desktop" you need to remove;
```
sudo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
```

---

### Post by glotz on 2006-06-21
Exactly, or **sudo aptitude remove ubuntu-desktop**.

I find the latter a little bit handier. This naturally only works if it was originally installed using aptitude.

---

### Post by izzyonstage on 2006-06-22
Personally, I think it would be better to follow the ubuntu perfect setup for your distro.

[http://www.howtoforge.com/perfect_setup_ubuntu_(distro](http://www.howtoforge.com/perfect_setup_ubuntu_(distro) number)

replace (distro number) with your relevant ubuntu dist number (for example. Breezy is 5.10.)

this has pictures to guide you through.

and then you could install SSH secure shell client on your xp machine.
if you would like it i can e-mail the install program for windows.

Hope this helps a bit

---

### Post by uncleclinto on 2006-07-11
[QUOTE=izzyonstage;1169236]Personally, I think it would be better to follow the ubuntu perfect setup for your distro.

[http://www.howtoforge.com/perfect_setup_ubuntu_(distro](http://www.howtoforge.com/perfect_setup_ubuntu_(distro) number)

People keep referring me to this tut, which says don't install the LAMP.  I need the LAMP to run Moodle.  The "perfect setup" doesn't even appear to include PHP 5, which is absolutely necessary to run moodle.

Everybody's in love with this article, but if it's so darn perfect, why does it ignore the new keystroke LAMP install.

---

### Post by az on 2006-07-11
> **uncleclinto said:**
> [QUOTE=izzyonstage;1169236]
People keep referring me to this tut, which says don't install the LAMP.  I need the LAMP to run Moodle.  The "perfect setup" doesn't even appear to include PHP 5, which is absolutely necessary to run moodle.

Everybody's in love with this article, but if it's so darn perfect, why does it ignore the new keystroke LAMP install.

LAMP rocks:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://docs.moodle.org/en/Installing_Moodle](http://docs.moodle.org/en/Installing_Moodle)

It doesn't seem to be much different from installing other LAMP web-applications.

---

### Post by DrSturgeon on 2006-07-11
Presumably you should have configured networking during the installation process.  Are you on a network that has a DHCP server on it, so you got a dynamic address during the install?  Then you just need to reconfigure your network card, which is pretty easy.  But first:

After a LAMP install, you presumably have Apache, MySQL, and PHP all running.  I'd install a text based browser so you can test things (I'm assuming you have an internet connection, if not, skip down to configuring a static IP address):

```
sudo aptitude install links2
```

Now, the default document root for apache is /var/www.  We want to make sure php is working, so we'll create a test script for it.  I forget if /var/www is world writable by default, so I'll use sudo here:

```
sudo nano /var/www/phpinfo.php
```

And enter this into that file:
```
<?php
phpinfo();
?>
```

Save the file (Ctrl-O), and close nano (Ctrl-X).  Permissions can be a little screwy with apache sometimes, so make sure apache can read the file we just created, and then use links2 to browse to it:

```
sudo chmod 755 /var/www/phpinfo.php
links2 http://localhost/phpinfo.php
```

You should see a page that lists a bunch of information about your php install, which means everything is working.

Now, set up a static IP.  You'll need to edit the interfaces file:

```
sudo nano /etc/network/interfaces
```

If you currently have a dynamic ip address, you'll have a line like this one that tells it to use dhcp on this interface:

```
iface eth0 inet dhcp
```

Replace that line with this:

```
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
```

I just put some random numbers in there, but you get the idea.  Address is the IP address you want, netmask is the netmask, gateway is the address of your router.

Save and exit nano.

You should make sure your DNS servers are set in /etc/resolv.conf:

```
sudo nano /etc/resolv.conf
```

And enter them one per line, like this (again, these numbers are just random):

```
nameserver 192.168.1.2
nameserver 192.168.1.3
```

If you had dhcp set up before, this file is probably already fine.

Then restart the network system:

```
sudo /etc/init.d/networking restart
```

You might have to restart apache also, but probably not:

```
sudo apache2ctl restart
```

And you should be good to go.  Check if you can access the script we made from the new ip address:

```
links2 http://192.168.1.99/phpinfo.php
```

---

### Post by houstonbofh on 2006-07-12
Some people hate this, but the gnome gui has a lot of nice admin tools.  > sudo apt-get install ubuntu-desktop This might make it easier to wonder around as a new user.  Note that using synaptic to remove "ubuntu-desktop" actually only removes the meta package, not any components.  However, it does make it passable to remove open office, which is a bit of a useless thing on a server. :D

---

### Post by DrSturgeon on 2006-07-12
Use aptitude instead of apt-get

```
sudo aptitude install ubuntu-desktop
```

Then, if you want to remove it:

```
sudo aptitude remove ubuntu-desktop
```

will remove everything it installed.


But really, take the time to learn the command line.  It'll be worth it in the end.  And there are no gui tools to configure apache and mysql.

---

