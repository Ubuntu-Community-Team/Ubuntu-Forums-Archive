---
title: "TTY1 doesn't run at boot, but TTYs 2-6 are OK"
date: 2013-02-28
forum: Server Platforms
---

### Post by kornfan71 on 2013-02-28
Hello all,
I'm running Ubuntu Server 12.04.2 LTS, and I have a Lubuntu desktop installed on it. I don't want X Server to start when I boot into Ubuntu, though, so I added the "text" option to Grub's [FONT=courier new]"GRUB_CMDLINE_LINUX_DEFAULT"[/FONT] line.
This much works well. I get dropped to a TTY, and the X server is not started.

However, it drops me to what *should* be TTY1...but it's just a blank screen with a flashing cursor on it.
If I switch to TTY2, I get a login prompt. I checked the output of [FONT=courier new]ps -ef | grep tty[/FONT], and there was no mention of TTY1. Running [FONT=courier new]sudo start tty1[/FONT] starts TTY1 just fine, and it is then 100% usable.

Does anyone know what's going on here? :?

Thanks in advance.

---

### Post by matt_symes on 2013-03-01
Hi

Waht version os Lubuntu are you using ? 

If it is 12.04 or greater then it is using LightDM as the desktop manager. 

You can ensure LightDm does not start at startup by creating an override file and this is the way you want to be doing it.

Remove that text parameter from grub as that was only ever a hack to ensure GDM did not boot at startup and, if i remember correctly, was part of GDM's startup scripts.

So, put the system back as it was.

After that, boot into your system and from a terminal or console type

```
echo "manual" | sudo tee /etc/init/lightdm.override
```

Thst should do it for you.

Kind regards

---

### Post by kornfan71 on 2013-03-01
matt,
Thanks for the reply. I went ahead and removed the text boot option, and added the override. Unfortunately, the same behavior is still happening. It leaves the screen set to TTY7 with the startup info printed on it, and TTY1 does not start. TTY2-6 all have terminals running on them.

---

### Post by matt_symes on 2013-03-01
Hi
> 
Unfortunately, the same behavior is still happening.

Hmm. That's a surprise.

Any chance you can take a picture of TTY1 at startup and upload it here. I would like to see it.

Can you also post the output of

```
cat /etc/init/tty1.conf
```

Kind regards

---

### Post by kornfan71 on 2013-03-02
Sure. This is what it looks like directly after startup, without hitting anything: 
[http://i1044.photobucket.com/albums/b441/kornfan71/Server%20TTYs/IMG_1424_zps5ccc0e41.jpg](http://i1044.photobucket.com/albums/b441/kornfan71/Server%20TTYs/IMG_1424_zps5ccc0e41.jpg)

This is what TTY1 looks like when I hit CTRL+ALT+F1: 
[http://i1044.photobucket.com/albums/b441/kornfan71/Server%20TTYs/IMG_1429_zpsea09fda5.jpg](http://i1044.photobucket.com/albums/b441/kornfan71/Server%20TTYs/IMG_1429_zpsea09fda5.jpg)
(Bad timing on the picture, but there was a flashing cursor at the top left.)

And this is TTY2 if you're curious:
[http://i1044.photobucket.com/albums/b441/kornfan71/Server%20TTYs/IMG_1428_zps3531429b.jpg](http://i1044.photobucket.com/albums/b441/kornfan71/Server%20TTYs/IMG_1428_zps3531429b.jpg)

Here's /etc/init/tty1.conf:
```
# tty1 - getty#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.


start on stopped rc RUNLEVEL=[2345] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)


stop on runlevel [!2345]


respawn
exec /sbin/getty -8 38400 tty1



```


I also cat'd /etc/init/tty2.conf for comparison:
```
# tty2 - getty#
# This service maintains a getty on tty2 from the point the system is
# started until it is shut down again.


start on runlevel [23] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)


stop on runlevel [!23]


respawn
exec /sbin/getty -8 38400 tty2



```

Would it be alright to change the tty1.conf to match tty2.conf? I figure they would have to be a little different since you're supposed to be dropped at TTY1 after boot...

This is the outupt of "runlevel," if that's pertinent:
```
N  2
```


Thanks in advance!

---

### Post by matt_symes on 2013-03-02
Hi

tty1.conf and tty2.conf are both fine as they are.

Your boot messages are being logged to tty1.

Can you post the output of

```
cat /proc/cmdline
```

Kind regards

---

### Post by kornfan71 on 2013-03-03
matt,
Here's the output of "cat /proc/cmdline":

```



BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=6cd9a7c1-d48c-4ba0-8288-343f352bd169 ro quiet


```

Thanks!

---

### Post by matt_symes on 2013-03-04
Hi

I'm not 100% sure what to suggest at the moment.

You could try adding this to your kernel command line

```
vt.handoff=7
```

I don't think that would help though.

Can you also post the output of

```
ps aux | grep tty
```

Kind regards

---

### Post by schragge on 2013-03-04
> **matt_symes said:**
> You could try adding this to your kernel command line
```
vt.handoff=7
```I'd rather suspect *vt.handoff* being the trigger of this behaviour if it were present, but it isn't. See LP#[lpbug]761830[/lpbug]. In other words, this looks as if *vt.handoff=1* were present on the kernel command line, but it isn't.

---

### Post by kornfan71 on 2013-03-05
Tried the vt.handoff=7; result was a blank screen until I switched to TTYs 2-7 (it appeared to be on 1).

This is the output of "ps aux | grep tty":
```

root       851  0.0  0.0  15784   972 tty4     Ss+  18:28   0:00 /sbin/getty -8 38400 tty4
root       869  0.0  0.0  15784   976 tty5     Ss+  18:28   0:00 /sbin/getty -8 38400 tty5
root       875  0.0  0.0 132040  3588 tty2     Ss+  18:28   0:00 /bin/login --       
root       876  0.0  0.0  15784   980 tty3     Ss+  18:28   0:00 /sbin/getty -8 38400 tty3
root       880  0.0  0.0  15784   980 tty6     Ss+  18:28   0:00 /sbin/getty -8 38400 tty6
server    2328  0.0  0.0   9388   924 pts/0    S+   18:31   0:00 grep --color=auto tty

```

Only other tidbit I noticed: I messed up the vt.handoff command the first time (put in an underscore instead of a period). I was just modifying it at boot time, rather than updating the config, so Grub says it's "Booting a command list." That text stayed on TTY1 after Ubuntu had finished booting. Probably not really important, but I had not seen that happen before. That was also the result with the option vt.handoff=1.

---

### Post by matt_symes on 2013-03-06
Hi

You do not seem to have getty running on tty1 and this would cause the problem you are seeing.

It is going to be a case of looking through you startup scripts to try to identify why.

I will be at work all day so i cannot look until this evening and i'm in the UK.

In the mean time can you post the output of 

```
ls -l /etc/init/tty1.conf
```

Kind regards

---

### Post by matt_symes on 2013-03-06
Hi

I wanted to check the file permissions of the file itself.

@OP can you start the tty from initcl ?

```
sudo initctl start tty1
```

Post back any output from the console. Does his start tty on tty1 ?

Can you start gety manually ?

```
exec /sbin/getty -8 38400 tty1
```

Can you post the output of

```
cat /etc/default/console-setup
```

Kind regards

---

### Post by matt_symes on 2013-03-06
Hi

@OP can you start the tty from initcl ?

```
sudo initctl start tty1
```

Post back any output from the console. Does this start tty on tty1 ?

Can you start getty manually ?

```
exec /sbin/getty -8 38400 tty1
```

Type these commands from a working console 2-6.

Can you post the output of

```
cat /etc/default/console-setup
```

Kind regards

---

### Post by kornfan71 on 2013-03-06
Alright, here goes:

ls -l /etc/init/tty1.conf
```
-rw-r--r-- 1 root root 348 Apr 16  2012 /etc/init/tty1.conf
```
(All the other tty confs are the same)

I ran "sudo initctl start tty1" which added this entry in "ps aux | grep tty". I didn't have to start getty myself. 

```
root     10963  0.0  0.0  15784   972 tty1     Ss+  21:25   0:00 /sbin/getty -8 38400 tty1
```

And here's the contents of /etc/default/console-setup.



```
# Change to "yes" and setupcon will explain what is being doing
VERBOSE_OUTPUT="no"


# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"


# Put here your encoding.  Valid charmaps are: UTF-8 ARMSCII-8 CP1251
# CP1255 CP1256 GEORGIAN-ACADEMY GEORGIAN-PS IBM1133 ISIRI-3342
# ISO-8859-1 ISO-8859-2 ISO-8859-3 ISO-8859-4 ISO-8859-5 ISO-8859-6
# ISO-8859-7 ISO-8859-8 ISO-8859-9 ISO-8859-10 ISO-8859-11 ISO-8859-13
# ISO-8859-14 ISO-8859-15 ISO-8859-16 KOI8-R KOI8-U TIS-620 VISCII
CHARMAP="UTF-8"


# The codeset determines which symbols are supported by the font.
# Valid codesets are: Arabic Armenian CyrAsia CyrKoi CyrSlav Ethiopian
# Georgian Greek Hebrew Lao Lat15 Lat2 Lat38 Lat7 Thai Uni1 Uni2 Uni3
# Vietnamese.  Read README.fonts for explanation.
CODESET="Uni2"


# Valid font faces are: VGA (sizes 8, 14 and 16), Terminus (sizes
# 12x6, 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBold (sizes
# 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBoldVGA (sizes 14
# and 16) and Fixed (sizes 13, 14, 15, 16 and 18).  Only when
# CODESET=Ethiopian: Goha (sizes 12, 14 and 16) and
# GohaClassic (sizes 12, 14 and 16).
# Set FONTFACE and FONTSIZE to empty strings if you want setupcon to
# set up the keyboard but to leave the console font unchanged.
FONTFACE="Fixed"
FONTSIZE="16"


# You can also directly specify nonstandard font or console map to load.
# Use space as separator if you want to load more than one font.
# You can use FONT_MAP in order to specify the Unicode map of the font
# in case the font doesn't have it embedded.


# FONT='lat9w-08.psf.gz brl-8x8.psf'
# FONT_MAP=/usr/share/consoletrans/lat9u.uni
# CONSOLE_MAP=/usr/local/share/consoletrans/my_special_encoding.acm


# You can also specify a screen size that setupcon will enforce.  This can not
# exceed what the current screen resolution can display according to the size of
# the loaded font.
#
# SCREEN_WIDTH=80
# SCREEN_HEIGHT=25


if [ -f /etc/default/keyboard ]; then
    . /etc/default/keyboard
fi

```


At least to my eye, nothing looks out of the ordinary. =/

---

### Post by matt_symes on 2013-03-07
Hi

> At least to my eye, nothing looks out of the ordinary. =/

Neither can i. All is looking good at the moment. This is a puzzler.

Do you have an override file for tty1 or any override files ?

```
ls -l /etc/init/*.override
```

Kind regards

---

### Post by kornfan71 on 2013-03-07
Thanks for sticking with it like you have! I really appreciate it.

Here's the "ls -l /etc/init/*.override:
```

-rw-r--r-- 1 root root 7 Mar  1 15:41 /etc/init/lightdm.override

```

Content of the file is just "manual."

For fun, I ran "sudo telinit 3" on the computer, and to my surprise, this actually started getty in TTY1.
I set runlevel 3 as the default then, but TTY1 didn't launch after rebooting. So, if I change runlevels manually, it launches TTY1 correctly. But I still can't get it to start and drop me to it on boot.

All I can figure at this point is that the lightdm init config *might *have something to do with launching TTY1...but that seems silly.

---

### Post by schragge on 2013-03-07
I'd rather suspect [uwiki]Plymouth[/uwiki] than lightdm, but TBH I don't know.

[highlight]Update.[/highlight]
 [Some]("https://bugzilla.redhat.com/show_bug.cgi?id=467207") [reports]("https://bugzilla.redhat.com/show_bug.cgi?id=471580") [on]("http://comments.gmane.org/gmane.comp.freedesktop.plymouth/615") [strange](http://dev.gentoo.org/~aidecoe/doc/en/plymouth.xml#doc_chap3_sect1) plymouth interactions with tty1.

---

### Post by kornfan71 on 2013-03-07
> **schragge said:**
> I'd rather suspect [uwiki]Plymouth[/uwiki] than lightdm, but TBH I don't know.

[highlight]Update.[/highlight]
 [Some]("https://bugzilla.redhat.com/show_bug.cgi?id=467207") [reports]("https://bugzilla.redhat.com/show_bug.cgi?id=471580") [on]("http://comments.gmane.org/gmane.comp.freedesktop.plymouth/615") [strange]("http://dev.gentoo.org/~aidecoe/doc/en/plymouth.xml#doc_chap3_sect1") plymouth interactions with tty1.


I'm sure this is the not "proper" way to disable plymouth, and I'm not sure if it disabled it completely or what, but I did "rm /etc/init/plymouth*.conf" and rebooted.
The main difference here was that boot messages were logged to TTY1 instead of TTY7. Upon completion of boot, TTY1 was left with the boot messages, TTY2-6 had login prompts as expected, and TTY7 was blank as expected.

So, still no dice. (Assuming what I did completely disabled plymouth.)



P.S. I obviously cannot remove plymouth...here's most of the output from "sudo apt-get -s remove plymouth":
```

server@LanchServer:~$ less output.txt
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
  gstreamer0.10-nice gvfs gvfs-backends gvfs-daemons gvfs-fuse hostname hplip
  ibus ifupdown indicator-datetime indicator-power indicator-session
  indicator-sound initramfs-tools initscripts irqbalance jockey-common
  jockey-gtk kbd kerneloops-daemon keyboard-configuration landscape-common
  language-selector-common language-selector-gnome libapache2-mod-php5 libapr1
  libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libaudio2 libblkid1
  libcanberra-gtk3-module libcryptsetup4 libdevmapper-event1.02.1
  libdevmapper1.02.1 libfarstream-0.1-0 libgdu0 libgksu2-0 libgnomekbd7
  libgoa-1.0-0 libgphoto2-2 libgpod-common libgpod4 libgupnp-1.0-4
  libgupnp-igd-1.0-4 libgweather-3-0 libgweather-common libimobiledevice2
  libio-socket-ssl-perl liblightdm-gobject-1-0 liblvm2app2.2
  liblwp-protocol-https-perl libmount1 libnet-dbus-perl libnice10
  libnm-glib-vpn1 libnm-glib4 libnm-gtk0 libnm-util2 libnss-mdns liboobs-1-5
  libpam-winbind libparted0debian1 libpurple0 libsane libsm6 libunique-3.0-0
  libutempter0 libuuid1 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwww-perl
  libxapian22 libxaw7 libxfce4ui-1-0 libxfconf-0-2 libxklavier16
  libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxmu6 libxt6
  libyelp0 lightdm lightdm-gtk-greeter linux-generic-lts-quantal
  linux-image-3.5.0-25-generic linux-image-generic-lts-quantal
  linux-sound-base logrotate lubuntu-core lubuntu-default-settings
  lubuntu-desktop lubuntu-software-center lxkeymap minidlna mlocate
  modemmanager module-init-tools mount mountall mplayer2 mysql-server
  mysql-server-5.5 netbase network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome ntfs-3g ntp ntpdate openbox
  openbox-themes openssh-client openssh-server osmo parted passwd pidgin
  pidgin-libnotify pidgin-microblog plymouth plymouth-label
  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text
  plymouth-theme-ubuntu-text pm-utils policykit-1 policykit-1-gnome
  powermgmt-base ppp pppconfig pppoeconf pptp-linux printer-driver-gutenprint
  printer-driver-hpcups printer-driver-postscript-hp procps pulseaudio
  pulseaudio-module-x11 pulseaudio-utils python-aptdaemon
  python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat python-xapian
  python-xklavier resolvconf rfkill rsyslog rtkit samba samba-common-bin
  sane-utils screen sessioninstaller simple-scan software-properties-gtk
  ssl-cert synaptic system-tools-backends tasksel tasksel-data telnet
  ubuntu-docs ubuntu-minimal ubuntu-standard ubuntu-system-service udev udisks
  ufw unity-greeter update-manager update-notifier upower upstart ureadahead
  usb-modeswitch usb-modeswitch-data usbmuxd util-linux uuid-runtime whoopsie
  winbind wpasupplicant wvdial x11-apps x11-session-utils x11-utils
  x11-xkb-utils x11-xserver-utils xfburn xfce4-power-manager xfconf xorg xpad
  xscreensaver xscreensaver-data xserver-common xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xterm yelp
The following NEW packages will be installed:
  libqdbm14 php5-cgi
The following packages will be upgraded:
  php5-cli php5-common php5-gd php5-mcrypt php5-mysql
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs libblkid1 (due to e2fsprogs) libuuid1 (due to e2fsprogs)
  util-linux (due to e2fsprogs) hostname mount libmount1 (due to mount)
5 upgraded, 2 newly installed, 303 to remove and 1 not upgraded.

```

So...yeah...:popcorn:

---

