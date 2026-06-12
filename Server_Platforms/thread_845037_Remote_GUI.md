---
title: "Remote GUI"
date: 2008-06-30
forum: Server Platforms
---

### Post by asmith3006 on 2008-06-30
Hi,

Is it possible to install a GUI-less Ubuntu server but then remotely connect using a gui from another Ubuntu machine?

Basically I want the best of both, the security and lower footprint of not running a GUI, but still being able to configure it using a GUI as I'm a linux newbie.

I'm aware of things like Webmin, but I would really like the full gui if possible.

Thanks.

---

### Post by forger on 2008-06-30
By "full" gui you mean something like a gnome, but without having gnome installed on the server?
I don't think you use a "full" graphical user interface (GUI) if your destination (remote machine) has no GUI installed, unless you make a GUI like webmin, which would end up using commands from ssh or run as a daemon at your server :)

You can always build your own, you have lots of programming languages out there, such as python, perl or php.

File manipulation on the other hand is much easier, using SFTP or FTP and Places > Connect to Server

---

### Post by forger on 2008-06-30
Being a linux newbie, you might want to install the xubuntu-desktop or if you want to make it lighter, some of its dependencies.

I wouldn't suggest to host a server without knowing the security risks, a linux newbie should first play around with the desktop :)

> $ apt-cache depends xubuntu-desktop 
xubuntu-desktop
  Depends: acpi
  Depends: acpi-support
  Depends: acpid
  Depends: alsa-base
  Depends: alsa-utils
  Depends: anacron
  Depends: avahi-daemon
  Depends: bc
  Depends: ca-certificates
  Depends: cupsys
  Depends: cupsys-bsd
  Depends: cupsys-client
  Depends: cupsys-driver-gutenprint
  Depends: dbus
  Depends: dc
  Depends: doc-base
  Depends: foomatic-db
  Depends: foomatic-db-engine
  Depends: foomatic-filters
  Depends: gdebi
  Depends: gdm
  Depends: genisoimage
  Depends: ghostscript-x
  Depends: gnome-app-install
  Depends: gnome-mount
  Depends: gnome-system-tools
  Depends: gtk2-engines
  Depends: gtk2-engines-murrine
  Depends: gtk2-engines-pixbuf
  Depends: gtk2-engines-ubuntulooks
  Depends: gtk2-engines-xfce
  Depends: hal
  Depends: hotkey-setup
  Depends: language-selector
  Depends: lftp
  Depends: libgl1-mesa-glx
  Depends: libglib2.0-data
  Depends: libglut3
    freeglut3
  Depends: libsasl2-modules
  Depends: libxp6
  Depends: openprinting-ppds
  Depends: pnm2ppa
  Depends: powermanagement-interface
  Depends: readahead
  Depends: screen
  Depends: scrollkeeper
    rarian-compat
  Depends: smbclient
  Depends: software-properties-gtk
  Depends: synaptic
  Depends: tango-icon-theme
  Depends: tango-icon-theme-common
  Depends: thunar
  Depends: thunar-archive-plugin
  Depends: thunar-media-tags-plugin
  Depends: thunar-thumbnailers
  Depends: thunar-volman
  Depends: ttf-bitstream-vera
  Depends: ttf-dejavu-core
  Depends: ttf-freefont
  Depends: ubuntu-artwork
  Depends: unzip
  Depends: update-manager
  Depends: usplash
  Depends: vim-runtime
  Depends: x-ttcidfont-conf
  Depends: xfce4-mcs-plugins
  Depends: xfce4-mcs-plugins-extra
  Depends: xfce4-mixer
  Depends: xfce4-panel
  Depends: xfce4-session
  Depends: xfce4-terminal
  Depends: xfce4-utils
  Depends: xfdesktop4
  Depends: xfwm4
  Depends: xfwm4-themes
  Depends: xkb-data
  Depends: xorg
  Depends: xterm
  Depends: xubuntu-artwork-usplash
  Depends: xubuntu-default-settings
  Depends: zenity
  Depends: zip
  Recommends: abiword
  Recommends: abiword-plugins
  Recommends: app-install-data-commercial
  Recommends: apport-gtk
  Recommends: avahi-autoipd
  Recommends: bluez-cups
  Recommends: bluez-utils
  Recommends: bogofilter
  Recommends: brasero
  Recommends: cdparanoia
  Recommends: cups-pdf
  Recommends: displayconfig-gtk
  Recommends: dvd+rw-tools
 |Recommends: evince-gtk
  Recommends: evince
  Recommends: file-roller
  Recommends: firefox
  Recommends: foo2zjs
  Recommends: foomatic-db-hpijs
  Recommends: fortune-mod
  Recommends: gcalctool
  Recommends: gcc
  Recommends: gimp
  Recommends: gnome-accessibility-themes
  Recommends: gnome-games
  Recommends: gnome-power-manager
  Recommends: gnome-screensaver
  Recommends: gnome-system-monitor
 |Recommends: gnumeric-gtk
  Recommends: gnumeric
  Recommends: gucharmap
  Recommends: hal-cups-utils
  Recommends: hplip
  Recommends: jockey-gtk
  Recommends: landscape-client
  Recommends: laptop-detect
  Recommends: libgl1-mesa-dri
  Recommends: libgnome2-perl
  Recommends: libgoffice-gtk-0-6
    libgoffice-0-6
  Recommends: libnss-mdns
  Recommends: linux-headers-generic
  Recommends: make
  Recommends: min12xxw
  Recommends: mousepad
  Recommends: mozilla-thunderbird
  Recommends: network-manager-gnome
  Recommends: notification-daemon
  Recommends: onboard
  Recommends: orage
  Recommends: pidgin
  Recommends: pidgin-otr
  Recommends: powernowd
    powersaved
  Recommends: pxljr
  Recommends: python-exo
  Recommends: ristretto
  Recommends: scim
  Recommends: scim-gtk2-immodule
  Recommends: screensaver-default-images
  Recommends: splix
  Recommends: system-config-printer-gnome
  Recommends: totem
  Recommends: totem-gstreamer
  Recommends: transmission-gtk
  Recommends: ttf-arabeyes
  Recommends: ttf-arphic-uming
  Recommends: ttf-indic-fonts-core
  Recommends: ttf-kochi-gothic
    ttf-kochi-gothic-naga10
  Recommends: ttf-kochi-mincho
    ttf-kochi-mincho-naga10
  Recommends: ttf-lao
  Recommends: ttf-malayalam-fonts
  Recommends: ttf-thai-tlwg
  Recommends: ttf-unfonts-core
  Recommends: ubufox
  Recommends: update-notifier
  Recommends: vinagre
  Recommends: wodim
  Recommends: wvdial
  Recommends: xcursor-themes
  Recommends: xdg-utils
  Recommends: xfce4-appfinder
  Recommends: xfce4-battery-plugin
  Recommends: xfce4-clipman-plugin
  Recommends: xfce4-cpugraph-plugin
  Recommends: xfce4-dict-plugin
  Recommends: xfce4-fsguard-plugin
  Recommends: xfce4-governor-plugin
  Recommends: xfce4-mailwatch-plugin
  Recommends: xfce4-mount-plugin
  Recommends: xfce4-netload-plugin
  Recommends: xfce4-notes-plugin
  Recommends: xfce4-places-plugin
  Recommends: xfce4-quicklauncher-plugin
  Recommends: xfce4-screenshooter-plugin
  Recommends: xfce4-smartbookmark-plugin
  Recommends: xfce4-systemload-plugin
  Recommends: xfce4-verve-plugin
  Recommends: xfce4-weather-plugin
  Recommends: xfce4-xkb-plugin
  Recommends: xfprint4
  Recommends: xscreensaver-data
  Recommends: xscreensaver-gl
  Recommends: xubuntu-docs

---

### Post by mrpeenut24 on 2008-06-30
If you want to run it without a gui, you can have X installed with gnome, xcfe, or kde, and leave them turned off on the server.  Then make sure EnableX11Forwarding in /etc/ssh/sshd_config is set to true.  That way when you connect, you can do so as 
```

ssh -X *server*
```

Doing this, you can run programs that depend on the xfce, gnome, etc libraries without having the overhead of having them run constantly on the server.

---

### Post by asmith3006 on 2008-06-30
> **mrpeenut24 said:**
> If you want to run it without a gui, you can have X installed with gnome, xcfe, or kde, and leave them turned off on the server.  Then make sure EnableX11Forwarding in /etc/ssh/sshd_config is set to true.  That way when you connect, you can do so as 
```

ssh -X *server*
```

Doing this, you can run programs that depend on the xfce, gnome, etc libraries without having the overhead of having them run constantly on the server.

Excellent. Thanks for the advice.

A follow up question would be, do you think it's 'safe' to use Ubuntu as a web-facing LAMP server? I know several linux people who sneer at the idea of using anything other than Centos or similar.

---

### Post by mrpeenut24 on 2008-06-30
Well, it's fairly new to the dedicated server distribution, but I've been using Ubuntu desktop as a server for a few years and never had a problem with it.  I don't feel I'm *reliably* able to answer this, but in my personal opinion, I think it's ready for server use.  As for *safe*, that depends on how you configure it.  Make sure to use difficult-to-guess passwords, don't leave ports open that you're not using, and check on logs every so often.  If you stay smart about it, then yes, it is safe to use as a web-facing server.

---

### Post by asmith3006 on 2008-07-01
If I were to setup the server using the GUI and then disable the GUI, would this be as secure as not installing the gui at all?

If it is, how do I disable the GUI?

Thanks.

---

### Post by mrpeenut24 on 2008-07-02
The gui doesn't really make it any less secure, even if it's enabled.  It just hogs resources all the time.  Disabling it will stop it from hogging those resources until it's needed.

To disable it, do the following:

```

sudo /etc/init.d/gdm stop

```then install sysv-rc-conf

```

sudo apt-get install sysv-rc-conf

```and run it

```

sudo sysv-rc-conf

```then scroll down with the keyboard until you see 'gdm'.

It should look something like:

```

service    1    2    3    4    5    0    6    S
------------------------------------------------
gdm       [ ]  [X]  [X]  [X]  [X]  [ ]  [ ]  [ ]

```go to each of those selected boxes and press the spacebar to unselect them.  This will stop it from running at startup.

If you're ever at the server and need the gui again you can type:
```
sudo /etc/init.d/gdm start
``` then stop it whenever you're done.



EDIT:  This info was for Gnome.  If you're using Xfce, replace every instance of 'gdm' with 'xdm'.  And if you're using KDE, replace it with 'kdm'.

---

### Post by g0bez on 2008-11-17
I realize this is a bit late and you probably already have a solution, but maybe this will be helpful to someone else who browses this way.


I set up Ubuntu servers all the time for people who are completely unfamiliar with linux, but want the stability/safety. There are many web interfaces that you can use which allow you the 'best of both worlds'. We use Plesk control panel... seems to get the job done pretty well. If you only have 1 domain, it is free to use... more domains will cost you.

1. Install the base OS onto the server hardware (DON"T RUN ANY UPDATES).
2. download plesk for the operating system you're using (lynx plesk.com  ... and then browse to the ~3.5MB web installer)
3. You'll need to change the permissions to get it to run on your computer: sudo chmod 755 plesk_installer_name

4. Run the plesk installer: ./plesk_installer_name
5. During the plesk install, you'll need to read up on the various options... I'll leave that up to you.
6. Turn off your firewall
7. Configure web interface (just follow through the screens) by turning your browser to [http://ip.address:8443](http://ip.address:8443)

Voila! You have your Ubuntu/linux box... and a virtually fool proof way to run it!


That said... I would *HIGHLY* recommend using this as a temporary fix, and actually spending the time to learn linux. For this type of application, there really is nothing better than digging in and learning it!

---

