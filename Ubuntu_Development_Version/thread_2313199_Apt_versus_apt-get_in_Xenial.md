---
title: "Apt versus apt-get in Xenial"
date: 2016-02-10
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2016-02-10
I'm seeing apt in place of apt-get and was just wondering if **apt** is the new **apt-get** or what?

```
cavsfan@cavsfan-le-beast:~$ sudo apt-get dist-upgrade
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libsuitesparseconfig4.4.5
Use **'sudo [COLOR=#ff0000]apt[/COLOR] autoremove'** to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I'm pretty sure this is new in Xenial only but not sure. I know apt-get still works.

---

### Post by dino99 on 2016-02-10
yah, a typo into that comment :p This needs to be reported.

---

### Post by slickymaster on 2016-02-10
See this: [http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/?PageSpeed=noscript](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/?PageSpeed=noscript) and this: [https://mvogt.wordpress.com/2014/04/04/apt-1-0/](https://mvogt.wordpress.com/2014/04/04/apt-1-0/)

---

### Post by syntaxerror74 on 2016-02-10
In fact, apt is just a little more eye-candy :D 
Featuring fancy progress bars and all that stuff...

So if you are on a slow machine, I'd strongly recommend to keep using apt-get because on slow PCs, progress bars are always a CPU hog.

---

### Post by Cavsfan on 2016-02-10
> **dino99 said:**
> yah, a typo into that comment :p This needs to be reported.

:p :rolleyes: :p Lol!

> **slickymaster said:**
> See this: [http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/?PageSpeed=noscript](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/?PageSpeed=noscript) and this: [https://mvogt.wordpress.com/2014/04/04/apt-1-0/](https://mvogt.wordpress.com/2014/04/04/apt-1-0/)

Looks pretty sweet! Thanks for sharing those! I especially liked and strongly agree with the DDH. :D

> **syntaxerror74 said:**
> In fact, apt is just a little more eye-candy :D 
Featuring fancy progress bars and all that stuff...

So if you are on a slow machine, I'd strongly recommend to keep using apt-get because on slow PCs, progress bars are always a CPU hog.

I haven't noticed any progress bars. In Arch Linux there are progress bars in terminal, but my internet speed is so fast it makes no difference.
I've actually got from my ISP - 200Mbps down and 20Mbps up but am limited by a 54Mbps router and old ethernet card that is 100Mbps. 

My son has the fast PC and his tests near 190Mbps down. I am literally blown away by how fast updates go wizzing by in terminal. I mean I get updates at 4Mb download speeds most of the time!

[[IMG]http://www.speedtest.net/result/5075541507.png[/IMG]](http://www.speedtest.net/my-result/5075541507)

Although I did notice this on the 2nd link that slickymaster posted:

```
You can enable/disable the install progress via:

# echo 'Dpkg::Progress-Fancy "1";' > /etc/apt/apt.conf.d/99progressbar
```

---

### Post by Cavsfan on 2016-02-10
All of my update aliases use apt-get and I'm not going to mess with them at this time.

---

### Post by ajgreeny on 2016-02-10
I believe I am correct in saying that Linux Mint has had the option to use **apt** in place of **apt-get** for a while now, though I don't use Mint other than a VM of Mint-17.2-XFCE in VBox, just as a test OS. (I prefer Xubuntu!)

I shall have a test of this in a while just to see if I'm correct.

Yes it does work in Mint 17.2, but I don't remember when it was first used.

---

### Post by grahammechanical on 2016-02-10
It works and so does apt-get

> graham@sdb7-Dev:~$ sudo apt update
[sudo] password for graham: 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                     
Ign:7 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) wily InRelease   
Hit:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease       
Hit:9 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) wily Release
Hit:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-proposed InRelease
Reading package lists... Done  
Building dependency tree       
Reading state information... Done
51 packages can be upgraded. Run 'apt list --upgradable' to see them.


> graham@sdb7-Dev:~$ sudo apt list --upgradable
Listing... Done
compiz/xenial,xenial 1:0.9.12.2+16.04.20160209-0ubuntu1 all [upgradable from: 1:0.9.12.2+16.04.20151211-0ubuntu1]
compiz-core/xenial 1:0.9.12.2+16.04.20160209-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20151211-0ubuntu1]
compiz-gnome/xenial 1:0.9.12.2+16.04.20160209-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20151211-0ubuntu1]
compiz-plugins-default/xenial 1:0.9.12.2+16.04.20160209-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20151211-0ubuntu1]
fontconfig/xenial-proposed 2.11.1-0ubuntu7 amd64 [upgradable from: 2.11.1-0ubuntu6]
fontconfig-config/xenial-proposed,xenial-proposed 2.11.1-0ubuntu7 all [upgradable from: 2.11.1-0ubuntu6]
gettext/xenial-proposed 0.19.7-2ubuntu3 amd64 [upgradable from: 0.19.7-2ubuntu2]
gettext-base/xenial-proposed 0.19.7-2ubuntu3 amd64 [upgradable from: 0.19.7-2ubuntu2]
gnupg-agent/xenial-proposed 2.0.28-3ubuntu2 amd64 [upgradable from: 2.0.28-3ubuntu1]
gnupg2/xenial-proposed 2.0.28-3ubuntu2 amd64 [upgradable from: 2.0.28-3ubuntu1]
grep/xenial 2.22-1ubuntu2 amd64 [upgradable from: 2.22-1]
libasprintf-dev/xenial-proposed 0.19.7-2ubuntu3 amd64 [upgradable from: 0.19.7-2ubuntu2]
libasprintf0v5/xenial-proposed 0.19.7-2ubuntu3 amd64 [upgradable from: 0.19.7-2ubuntu2]
libcompizconfig0/xenial 1:0.9.12.2+16.04.20160209-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20151211-0ubuntu1]
libdecoration0/xenial 1:0.9.12.2+16.04.20160209-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20151211-0ubuntu1]
libfontconfig1/xenial-proposed 2.11.1-0ubuntu7 amd64 [upgradable from: 2.11.1-0ubuntu6]
libgcrypt20/xenial 1.6.5-2 amd64 [upgradable from: 1.6.4-5]
libgettextpo-dev/xenial-proposed 0.19.7-2ubuntu3 amd64 [upgradable from: 0.19.7-2ubuntu2]
libgettextpo0/xenial-proposed 0.19.7-2ubuntu3 amd64 [upgradable from: 0.19.7-2ubuntu2]
libnux-4.0-0/xenial 4.0.8+16.04.20160209-0ubuntu1 amd64 [upgradable from: 4.0.8+16.04.20151210-0ubuntu1]
libnux-4.0-common/xenial,xenial 4.0.8+16.04.20160209-0ubuntu1 all [upgradable from: 4.0.8+16.04.20151210-0ubuntu1]
libpulse-mainloop-glib0/xenial-proposed 1:8.0-0ubuntu2 amd64 [upgradable from: 1:7.1-1ubuntu7]
libpulse0/xenial-proposed 1:8.0-0ubuntu2 amd64 [upgradable from: 1:7.1-1ubuntu7]
libpulsedsp/xenial-proposed 1:8.0-0ubuntu2 amd64 [upgradable from: 1:7.1-1ubuntu7]
libunity-control-center1/xenial 15.04.0+16.04.20160209-0ubuntu1 amd64 [upgradable from: 15.04.0+16.04.20160119-0ubuntu1]
libunity-core-6.0-9/xenial 7.4.0+16.04.20160209.3-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20151218-0ubuntu2]
nux-tools/xenial 4.0.8+16.04.20160209-0ubuntu1 amd64 [upgradable from: 4.0.8+16.04.20151210-0ubuntu1]
pulseaudio/xenial-proposed 1:8.0-0ubuntu2 amd64 [upgradable from: 1:7.1-1ubuntu7]
pulseaudio-module-bluetooth/xenial-proposed 1:8.0-0ubuntu2 amd64 [upgradable from: 1:7.1-1ubuntu7]
pulseaudio-module-x11/xenial-proposed 1:8.0-0ubuntu2 amd64 [upgradable from: 1:7.1-1ubuntu7]
pulseaudio-utils/xenial-proposed 1:8.0-0ubuntu2 amd64 [upgradable from: 1:7.1-1ubuntu7]
python-chardet/xenial-proposed,xenial-proposed 2.3.0-2 all [upgradable from: 2.3.0-1build1]
python-imaging/xenial,xenial 3.1.1-1 all [upgradable from: 3.1.0-1]
python-pil/xenial 3.1.1-1 amd64 [upgradable from: 3.1.0-1]
python3-chardet/xenial-proposed,xenial-proposed 2.3.0-2 all [upgradable from: 2.3.0-1build1]
python3-pil/xenial 3.1.1-1 amd64 [upgradable from: 3.1.0-1]
ubuntu-core-launcher/xenial-proposed 1.0.16 amd64 [upgradable from: 1.0.15]
ubuntu-core-security-apparmor/xenial,xenial 16.04.15 all [upgradable from: 16.04.14]
ubuntu-core-security-seccomp/xenial,xenial 16.04.15 all [upgradable from: 16.04.14]
ubuntu-core-security-utils/xenial 16.04.15 amd64 [upgradable from: 16.04.14]
unity/xenial 7.4.0+16.04.20160209.3-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20151218-0ubuntu2]
unity-control-center/xenial 15.04.0+16.04.20160209-0ubuntu1 amd64 [upgradable from: 15.04.0+16.04.20160119-0ubuntu1]
unity-control-center-faces/xenial,xenial 15.04.0+16.04.20160209-0ubuntu1 all [upgradable from: 15.04.0+16.04.20160119-0ubuntu1]
unity-schemas/xenial,xenial 7.4.0+16.04.20160209.3-0ubuntu1 all [upgradable from: 7.4.0+16.04.20151218-0ubuntu2]
unity-scope-home/xenial 6.8.2+16.04.20160209-0ubuntu1 amd64 [upgradable from: 6.8.2+15.04.20150311.1-0ubuntu1]
unity-scopes-master-default/xenial,xenial 6.8.2+16.04.20160209-0ubuntu1 all [upgradable from: 6.8.2+15.04.20150311.1-0ubuntu1]
unity-services/xenial 7.4.0+16.04.20160209.3-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20151218-0ubuntu2]
update-notifier/xenial 3.166 amd64 [upgradable from: 3.165]
update-notifier-common/xenial,xenial 3.166 all [upgradable from: 3.165]
usb-modeswitch-data/xenial-proposed,xenial-proposed 20160112-1 all [upgradable from: 20151101-1]
x11-apps/xenial 7.7+5+nmu1ubuntu1 amd64 [upgradable from: 7.7+5+nmu1]

> 
graham@sdb7-Dev:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libqt5xcbqpa5 linux-headers-4.3.0-6 linux-headers-4.3.0-6-generic
  linux-headers-4.4.0-2 linux-headers-4.4.0-2-generic
  linux-image-4.3.0-6-generic linux-image-4.4.0-2-generic
  linux-image-extra-4.3.0-6-generic linux-image-extra-4.4.0-2-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  session-shortcuts
The following packages have been kept back:
  usb-modeswitch-data
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins-default fontconfig
  fontconfig-config gettext gettext-base gnupg-agent gnupg2 grep
  libasprintf-dev libasprintf0v5 libcompizconfig0 libdecoration0
  libfontconfig1 libgcrypt20 libgettextpo-dev libgettextpo0 libnux-4.0-0
  libnux-4.0-common libpulse-mainloop-glib0 libpulse0 libpulsedsp
  libunity-control-center1 libunity-core-6.0-9 nux-tools pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils
  python-chardet python-imaging python-pil python3-chardet python3-pil
  ubuntu-core-launcher ubuntu-core-security-apparmor
  ubuntu-core-security-seccomp ubuntu-core-security-utils unity
  unity-control-center unity-control-center-faces unity-schemas
  unity-scope-home unity-scopes-master-default unity-services update-notifier
  update-notifier-common x11-apps
50 to upgrade, 1 to newly install, 0 to remove and 1 not to upgrade.
Need to get 11.4 MB of archives.
After this operation, 62.5 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.


EDIT: the relationship between apt & apt-get

> **apt-get** is the [command line]("https://en.wikipedia.org/wiki/Command_line") package management tool supplied with the Debian package **apt**. APT searches its cached list of packages and lists the dependencies that must be installed or updated.

[https://en.wikipedia.org/wiki/Advanced_Packaging_Tool](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

Regards

---

### Post by rrnbtter on 2016-02-11
Greetings,
I tend to use the simplest form of everything to get to the desired result, hence this thread is to me a welcome addition. Frankly, I use <up><arrow> for my most used commands.

---

### Post by Cavsfan on 2016-02-11
Very interesting grahammechanical! I like the **sudo apt list --upgradable**. I already used my aliases to upgrade the system:

```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'
```

Got a bunch of compiz and many other updates and then ud2 gave me the **4.4.0-4-generic** kernel then rebooted.

I entered **sudo apt list --upgradable** and of course nothing showed.

I guess I'll eventually look at apt more but I'm too old for change. :p

:lol: I also use my up and down arrow keys quite frequently unless I've entered too many commands to easily get back to the ones I want.

---

### Post by QDR06VV9 on 2016-02-11
> **rrnbtter said:**
> Greetings,
I tend to use the simplest form of everything to get to the desired result, hence this thread is to me a welcome addition. Frankly, I use <up><arrow> for my most used commands.
I am sure you already know this, but just to revisit there also is a history usage in the terminal 
```
history
```
Then the entries that have been used will be shown in the terminal followed with numbers...
Here is just a small sample of mine.
```
 187  sudo pacman -S sddm sddm-kcm  
  188  sudo pacman -S breeze-kde4 oxygen-kde4
  189  sudo pacman -S print-manager systemd-kcm
  190  sudo pacman -S sni-qt libappindicator-gtk2 libappindicator-gtk3 libappindicator-sharp
  191  sudo pacman -S lib32-sni-qt
  192  sudo systemctl enable sddm -f
  193  sudo systemctl enable sddm -f
  194  su
  195  streamripper http://streaming.radionomy.com/TheRealFlashbackNow
  196  octpi
  197  inxi -Fxz
  198  killall mate-panel
  199  sudo pacman -Syu
  200  wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.4.tar.xz
  201  pamac
  202  sudo pacman -S gnome
  203  sudo pacman -S gnome-extras
  204  sudo pacman -S gnome-extra
  205  sudo packer -S plasma-desktop
  206  sudo packer -R plasma-desktop
  207  sudo pacman -R kf5 kf5-aids
  208  sudo pacman -R kf5 kf5-aids



``` 
To to shorten the commands you would just enter in the terminal
```
!200
```
Which will call from my examples "wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.4.tar.xz"
Then of course you could also make scripts to do the same effect.
Hope this is of some use!
Kind regards
Hey Cavsfan):P

---

### Post by Cavsfan on 2016-02-13
Guess I learnt something today. :P

I did not know about the history command. And I guess it works in most Linux systems.

Ubuntu and Arch it does for sure. Man history yields some interesting information.

Thanks Runrickus! ):P

---

### Post by QDR06VV9 on 2016-02-13
I am glad that I could be of assistance :D
Cheers Old Friend..

---

