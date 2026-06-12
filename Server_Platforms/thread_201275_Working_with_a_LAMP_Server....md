---
title: "Working with a LAMP Server..."
date: 2006-06-21
forum: Server Platforms
---

### Post by sean talbert on 2006-06-21
I've installed a LAMP server, but, being fairly new to Linux, I have no idea how to get around and use Linux with only the command prompt. Is there a way to get X\Gnome with a LAMP Server? If not, I'd appreciate help with a few questions (I don't expect long answers, links to documentation are appreciated) : Where are Apache, MySQL and PHP installed? How do I install FTP? How do I edit text files in the command prompt? How do I access MySQL?

Thanks for your help.

---

### Post by spifbv on 2006-06-21
[QUOTE=sean talbert]I've installed a LAMP server, but, being fairly new to Linux, I have no idea how to get around and use Linux with only the command prompt. Is there a way to get X\Gnome with a LAMP Server? If not, I'd appreciate help with a few questions: Where are Apache, MySQL and PHP installed? How do I install FTP? How do I edit text files in the command prompt? How do I access MySQL?

Thanks for your help.[/QUOTE]

To get Gnome:

sudo apt-get install ubuntu-desktop

then reboot.

A good reference for the rest is:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

And a reference for the vi text editor:

[http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

---

### Post by sean talbert on 2006-06-21
Thanks spifbv.

For the desktop, "sudo apt-get install ubuntu-desktop" isn't working. I get the messages: 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-desktop

My network isn't set up yet, does this need internet access? It looks like it does. I also have the desktop CD. Is there a way to install the ubuntu-desktop to my server using that? I'll try dselect.

Thanks

---

### Post by spifbv on 2006-06-21
[QUOTE=sean talbert]Thanks spifbv.

For the desktop, "sudo apt-get install ubuntu-desktop" isn't working. I get the messages: 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-desktop

My network isn't set up yet, does this need internet access? It looks like it does. I also have the desktop CD. Is there a way to install the ubuntu-desktop to my server using that? I'll try dselect.

Thanks[/QUOTE]

You can use dselect.  apt-get will also work if you insert the CD, although it'll just get the version that is on the CD without any updates that may be on the internet.

---

### Post by indieb0i on 2006-06-21
I'm attached to a network and have done updates over the Internet already, but am also getting the message "Couldn't find package ubuntu-desktop". I tried running "sudo aptitude install desktop" and it gave me a list of available packages that included the word desktop (gnome-desktop-data, libgnome-desktop-dev, kdesktop, xfdesktop4, desktop-file-utils, libgnome-desktop-2).

Any ideas?

---

### Post by spifbv on 2006-06-21
[QUOTE=indieb0i]I'm attached to a network and have done updates over the Internet already, but am also getting the message "Couldn't find package ubuntu-desktop". I tried running "sudo aptitude install desktop" and it gave me a list of available packages that included the word desktop (gnome-desktop-data, libgnome-desktop-dev, kdesktop, xfdesktop4, desktop-file-utils, libgnome-desktop-2).

Any ideas?[/QUOTE]

You may need to do this first:

sudo apt-get update

Also check your /etc/apt/sources.list, the dapper and dapper-updates sources should be uncommented e.g.:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

---

### Post by indieb0i on 2006-06-21
It looks like that was partly the problem. I must have had problems connecting to one of the sources, and the installer automatically commented it out. Even after I uncommented it, I couldn't connect. It's all fine now, so it appears to have been a combination of a network glitch and the sources file. Thanks.

---

### Post by sean talbert on 2006-06-22
[QUOTE=spifbv]You can use dselect.  apt-get will also work if you insert the CD, although it'll just get the version that is on the CD without any updates that may be on the internet.[/QUOTE]

I'm unable to get apt-get or dselect to work. When I try "apt-get update" with either the Server or Desktop CD in, it tries to look at a list of websites. How do I get apt-get to look at the CDs? Since dselect allows you to choose the CDROM, I tried that, however when it asked for the packages, it didn't like /dists/stable, and it also wanted the *.deb files location which I only saw in pool, but it didn't like that either. Where do I point dselect to on the CDs?

Thanks

---

### Post by az on 2006-06-22
[QUOTE=sean talbert]I've installed a LAMP server, but, being fairly new to Linux, I have no idea how to get around and use Linux with only the command prompt. Is there a way to get X\Gnome with a LAMP Server? If not, I'd appreciate help with a few questions (I don't expect long answers, links to documentation are appreciated) : Where are Apache, MySQL and PHP installed? How do I install FTP? How do I edit text files in the command prompt? How do I access MySQL?

Thanks for your help.[/QUOTE]
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by sean talbert on 2006-06-22
[QUOTE=sean talbert]I'm unable to get apt-get or dselect to work. When I try "apt-get update" with either the Server or Desktop CD in, it tries to look at a list of websites. How do I get apt-get to look at the CDs? Since dselect allows you to choose the CDROM, I tried that, however when it asked for the packages, it didn't like /dists/stable, and it also wanted the *.deb files location which I only saw in pool, but it didn't like that either. Where do I point dselect to on the CDs?[/QUOTE]

Still trying to get "sudo apt-get install ubuntu-desktop" to work from the Desktop CD (no internet connection). Here's what I've tried so far:

edited /etc/apt/sources.list to comment out URLs.
used apt-cdrom to add the Desktop CD (the Server was already in there) to sources.list.
sudo apt-get update
sudo apt-get install ubuntu-desktop... unable to find ubuntu-desktop.
dselect using the apt sources.list, dselect update, unable to loacate the ubuntu-desktop in the list of packages.

So, to summarize... installed a LAMP server from CD, want to add X/Gnome, however I have only the Desktop CD (no internet connection) to do this, and am having difficulties using apt-get or dselect to find ubuntu-desktop to install.

Thanks

---

### Post by spifbv on 2006-06-26
[QUOTE=sean talbert]Still trying to get "sudo apt-get install ubuntu-desktop" to work from the Desktop CD (no internet connection). Here's what I've tried so far:

edited /etc/apt/sources.list to comment out URLs.
used apt-cdrom to add the Desktop CD (the Server was already in there) to sources.list.
sudo apt-get update
sudo apt-get install ubuntu-desktop... unable to find ubuntu-desktop.
dselect using the apt sources.list, dselect update, unable to loacate the ubuntu-desktop in the list of packages.

So, to summarize... installed a LAMP server from CD, want to add X/Gnome, however I have only the Desktop CD (no internet connection) to do this, and am having difficulties using apt-get or dselect to find ubuntu-desktop to install.

Thanks[/QUOTE]

OK, put the CD in and do this, and show us the output:

sudo mount /media/cdrom0
sudo find /media/cdrom0 | fgrep desktop
grep cdrom /etc/apt/sources.list

I think the problem may be having both the server and desktop cdroms listed in sources.list.  Try commenting out the server cdrom from sources.list and do: 

sudo apt-get clean
sudo apt-get update
sudo apt-get install ubuntu-desktop

---

### Post by NilsRain on 2006-06-28
I'm using a VMware image of Dapper Server, and so far everything is working the same as my warty desktop...

But when I install some packages, such as openssh-server, it sometimes asks for the cd in the drive. 

I don't have a cd. Is there a way to re-point to the online sources?

- N i l s

---

### Post by houstonbofh on 2006-06-29
You can comment out the CD in the repositories.

---

### Post by crouton on 2006-07-03
Ubuntu-desktop is probably just a virtual package or something like that, it only references other packages.  Can't be 100% sure, but it's a thought.

If you want to get an X environment up and running, you could try
> sudo apt-get install xorg-server xorg-common gnome

That should get you the base X environment plus the Gnome window manager.   If it barfs, you should be able to tell from the output what packages (if any) weren't automatically selected.

---

### Post by foxylad on 2006-07-04
It might be easier to do a desktop install, and then install apache, mysql and php.

---

### Post by houstonbofh on 2006-07-04
[QUOTE=foxylad]It might be easier to do a desktop install, and then install apache, mysql and php.[/QUOTE]
Having tried both ways, I can say no...  ubuntu-desktop is just a dependency list, so it may not be on the Desktop CD.  Thy this for Ubuntu desktop.  It will ask for X stuff as well, but everything should be on the Desktop CD.  And make sure your repositories show the desktop CD, and not the server CD.
```
sudo apt-get install alacarte app-install-data app-install-data-commercial at-spi bicyclerepair bittorrent blt bluez-cups bluez-pcmcia-support bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy ca-certificates capplets-data contact-lookup-applet deskbar-applet diveintopython ekiga eog esound esound-common evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal fastjar festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox-gnome-support fping gcalctool gcj-4.1-base gconf-editor gdb gedit gedit-common gij-4.1 gimp-python gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-lighthouseblue gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client java-common java-gcj-compat libadns1 libatspi1.0-0 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1 libavc1394-0 libbeagle0 libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcurl3 libcurl3-gnutls libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libesd-alsa0 libestools1.2 libexchange-storage1.2-1 libflac7 libgail-common libgail-gnome-module libgail17 libgcj-common libgcj7 libgcj7-jar libgd2-noxpm libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgeoip1 libglew1 libglib-perl libgmp3c2 libgnome-desktop-2 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgphoto2-2 libgphoto2-port0 libgpod0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libhsqldb-java libicu34 libid3-3.8.3c2a libidn11 libieee1284-3 libjasper-1.701-1 libjaxp1.2-java libjessie-java libjline-java liblircclient0 liblpint-bonobo0 libmagick9 libmdbtools libmetacity0 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn3 libnautilus-extension1 libneon25 libnetcdf3 libnotify1 liboil0.3 libopal-2.2.0 libopenobex-1.0-0 libpanel-applet2-0 libpisock8 libpisync0 libportaudio0 libpq4 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 libraptor1 librasqal0 libraw1394-5 librdf0 libsane libsdl1.2debian libsdl1.2debian-alsa libservlet2.3-java libsexy2 libshout3 libsmbclient libsndfile1 libsoup2.2-8 libsqlite0 libsqlite3-0 libstlport4.6c2 libtotem-plparser1 libvorbisenc2 libvorbisfile3 libwnck-common libwnck18 libxalan2-java libxerces2-java libxklavier10 libxml2-utils libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxres1 libxt-java metacity mysql-common nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-writer openssl pkg-config python-adns python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-launchpad-integration python-ldap python-libxml2 python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4-adns python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-mysqldb python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-simpletal python2.4-soappy python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml python2.4-xmpp rdesktop rhythmbox rss-glx screensaver-default-images serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tcl8.4 tk8.4 totem totem-gstreamer tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs update-notifier vino vnc-common whois xsane xsane-common xsltproc xvncviewer yelp zenity 

```

---

### Post by mnzt42yd on 2006-07-05
if you have an alternitive install cd  once you have logged onto  system and are at prompt you can use command 

sudo-cdrom add                                  this will mount the cd 
sudo aptitude install ubuntu-desktop       to install   ubuntu desktop 
                            Kubuntu-desktop                  kubuntu desktop

---

