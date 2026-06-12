---
title: "What are the first packages you add to a new install?"
date: 2019-05-17
forum: Ubuntu, Linux and OS Chat
---

### Post by cruzer001 on 2019-05-17
For me, its **Nemo** file manager and **Synaptic** package manager.

---

### Post by oldos2er on 2019-05-17
I have a list somewhere:

htop iotop mc atool build-essential ncdu ffmpeg intel-microcode fdupes p7zip-full mkusb dropbox stellarium gsmartcontrol grub-customizer gparted fslint 

grub-customizer and mkusb are from their PPAs.

That's usually enough to begin with.   :)

Edit: Forgot mpv.

---

### Post by cruzer001 on 2019-05-17
I like taking a snapshot of web sites articles and save them for off line viewing and reference.  So my collection manager also gets top billing.  **Zotero** does this nicely.

---

### Post by sisco311 on 2019-05-17
I usually use debootstrap to install a minimal Ubuntu system from an existing one. So my first thing is to install is ubuntu-standard because I need nano and bash-completion (man pages, command-not-found, ....). 

htop is not on the top of my list but I must to install it when I realize that top is an alias to htop in my ~/.bash_aliases 

build-essential is simply essential. 

And from there it depends for what purpose I started to install the OS.

---

### Post by DuckHook on 2019-05-17
Everything oldos2er mentions plus:```
sudo apt install ecryptfs-utils ecryptfs-setup-private screen byobu iftop atop lmsensors hddtemp apt-listchanges nfs-common autofs gdisk inxi glances wakeonlan powerwake whois traceroute smartmontools nautilus-admin gedit-plugins gnome-tweak-tool geany pdfshuffler gufw links2 epiphany-browser gimp inkscape scribus calibre
```

---

### Post by cruzer001 on 2019-05-18
**FFmpeg** is good stuff and another thing on the top of my list is **Mplayer.**  Got to have music and a beer while getting all this sorted out :)

I do have **kod**i set up in a virtualbox and giving it a try, but I don't know, so many bells and whistles.

---

### Post by yetimon_64 on 2019-05-18
> **cruzer001 said:**
> For me, its **Nemo** file manager and **Synaptic** package manager.
My first off are usually gparted (and all required packages for full file system support, which is quite a few packages in itself), synaptic (including apt-xapian-index for the "quick search" search box), caja, mate terminal and gedit with the gedit plugins package.

No matter what flavor of Ubuntu I'm installing caja and mate terminal are always near the top of the list after gparted and synaptic, except on ubuntu-mate of course as they are already there by default.

> **cruzer001 said:**
> **FFmpeg** is good stuff and another thing on the top of my list is **Mplayer.**  Got to have music and a beer while getting all this sorted out :)... Yes, those two and mpv are never far behind on a new install here. Relaxing to some good music is important while "working" :smile:.

---

### Post by SantaFe on 2019-05-19
I used to add Celestia, till Ubuntu dropped it from the repositories.  Tried compiling it myself, and then the script they had to install it but no luck.  Darn it.

---

### Post by SeijiSensei on 2019-05-19
I use Kubuntu so my list of packages might be different:

thunderbird
gimp
smplayer
mpv
virtualbox from the Oracle repository
transmission
nfs-common

Specialized statistical software
gretl
pspp
r-base

---

### Post by cruzer001 on 2019-05-21
Gconf-editor use to be at the top of my list, it was nice to have so many settings in one location.  Dconf still gets installed and it is handy at times, but just not a "top of the list" item anymore.

---

### Post by TheFu on 2019-05-21
Depends on the purpose for the system.  I mostly build servers, so it isn't GUI programs. We use Ansible to script stuff.  The title of each ansible task provides a hint about the purpose:

```
$ ls -1 common_*
common_apt_base_packages.yml
common_apt_cache_settings.yml
common_desktop_apps.yml
common_etc_aliases.yml
common_etc_hosts.yml
common_etc_landscape.yml
common_etc_ntp_client.yml
common_etc_ntp_server.yml
common_etc_static_ip.yml
common_etc_sysctl.conf.yml
common_fix_sudorers.yml
common_fix_systemd_logind.conf
common_inst_smartmontools.yml
common_kernel-cleanup.yml
common_logwatch_settings.yml
common_purge_nano.yml
common_set_locale.yml
```
inside the common_apt_base_packages.yml, has this list:
```
      - python-apt
      - acpid
      - openssh-server
      - iptables-persistent
      - aptitude
      - sysstat
      - ethtool
      - fail2ban
      - rsync
      - rdiff-backup
      - mlocate
      - software-properties-common
      - logwatch
      - lshw
      - ntp
      - tree
      - postfix
      - heirloom-mailx

```
For desktops, add the common_desktop_apps.yml file:
```
   - synaptic
   - xterm
   - firefox
   - chromium-browser
   - thunderbird
   - keepassx
   - geany
   - xournal
   - evince
   - geeqie
   - clementine
   - mlocate
   - fail2ban
   - virt-manager
   - gnupg-curl
   - dillo

```
Some of these are deprecated, but I haven't built a fresh desktop since 2016, though I do have a new laptop.  It was a migration from a prior laptop install.  I know evince is gone - so I setup an aliases so I don't need to know the name of the new program. 
KeePassXC is my choice now.

I also remove some packages:```

   - nano
   - ibus
   - compiz
   - gedit
   - leafpad
   - chrome
   - bluez
   - unity-asset-pool
   - geoclue-ubuntu-geoip
```
vim is my editor. Don't need any others. I never, ever, want to see nano.
Don't want anything with bluetooth on my systems. EVER. Security.
Most of my systems run inside virtual machines. GPU intensive stuff isn't wanted.

Looking over some of the other posts, inxi, autofs, geany and a few others are only installed, if needed. There are 2 NFS servers here, which have been around for years.  I prefer NFS over samba/CIFS and use it all-the-time - in combination with autofs.

Postfix is required since logwatch sends daily, summary, emails. Plus it is handy to be able to whip off an email from a shell. It is configured as a satellite MTA and won't accept any non-local (same machine) email.

Obviously, I pull my ~/bin/ over to any new desktop.  On servers, it is only relevant selected scripts.

---

### Post by Tadaen_Sylvermane on 2019-05-21
Autofs for me. I keep my scripts on an nfs share on my server. My scripts do most of my configuration for a fresh installation so that is my first place to go.

---

### Post by cruzer001 on 2019-05-23
fail2ban

Never really thought of that as a desktop package.  Could be I need to rethink this.

---

### Post by linuxyogi on 2019-05-29
smplayer/mpv/vlc

---

### Post by DanPerecky on 2019-07-12
htop, ssh shell - for sshguard (set up some rules), and the other browsers- Opera and Brave.

---

### Post by TheFu on 2019-07-12
> **cruzer001 said:**
> fail2ban

Never really thought of that as a desktop package.  Could be I need to rethink this.

I install openssh-server on all systems for remote management, rsync, backup needs.  

If ssh is installed, then some sort of brute-force attack protections is needed, period.  That's where fail2ban comes in.  I also modify the /etc/ssh/sshd_config file to block password use from outside the trusted LAN. Only ssh-key/ssh-cert based authentication is allowed from the dangerous, outside, world.  I consider my own wifi subnet as the dangerous, outside, world, just like the internet.  

There are a few other security settings applied to the server config too, but I haven't gone through any "hardening" guide.

---

### Post by hk42 on 2019-07-13
I like to install packages that look the same as their Windows versions:
vlc ,putty ,handbrake,web browser,thunderbird, kodi ,wireshark ,etc
It is then easy to compare the performances and ,no , Linux is not always winner :p
On the other hand on a Windows only system I do exactly the same.
PS : on any Linux distribution "Midnight commander" is a must have for me.
gpm is nice too

---

### Post by speedwell68 on 2019-07-15
nfs-common
conky
Google Chrome
Kodi
ubuntu-restricted-extras
Telegram Desktop
vrms
Handbrake
Minrcraft
Pinta
PCManFM

---

### Post by Skaperen on 2019-07-16
i installed these when i switched from Ubuntu 16.04 to Xubuntu 18.04:
```
#!/bin/bash

pkglist=()

pkg(){
    pkglist=("${pkglist[@]}" "$@")
    return 0
}

pkg    apt-file
pkg    audacity
pkg    audacity-data
pkg    binfmt-support
pkg    btrfs-tools
pkg    build-essential
pkg    cheese
pkg    cpp-7
pkg    curl
pkg    dclock
pkg    docutils-common
pkg    docutils-doc
pkg    ec2-api-tools
pkg    emacs25
pkg    encfs
pkg    eog
pkg    evince
pkg    evince-common
pkg    fail2ban
pkg    ffmpeg
pkg    ffmpeg-doc
pkg    g++-7
pkg    gcc-7
pkg    gcc-7-doc
pkg    git
pkg    git-man
pkg    hercules
pkg    imagemagick-6
pkg    imagemagick-6-doc
pkg    lynx
pkg    lynx-common
pkg    make
pkg    makedev
pkg    mercurial
pkg    mercurial-common
pkg    mercurial-git
pkg    mplayer
pkg    mtools
pkg    nmap
pkg    ntp
pkg    openssh-server
pkg    openvpn
pkg    pike8.0-full
pkg    pike8.0-manual
pkg    pike8.0-reference
pkg    python3-pip
pkg    qemu
pkg    qemu-kvm
pkg    qemu-utils
pkg    rename
pkg    screen
pkg    scrot
pkg    socat
pkg    sox
pkg    ssh-import-id
pkg    subversion
pkg    traceroute
pkg    ubuntu-wallpapers
pkg    ubuntu-wallpapers-bionic
pkg    ubuntu-wallpapers-artful
pkg    ubuntu-wallpapers-karmic
pkg    ubuntu-wallpapers-lucid
pkg    ubuntu-wallpapers-maverick
pkg    ubuntu-wallpapers-natty
pkg    ubuntu-wallpapers-oneiric
pkg    ubuntu-wallpapers-precise
pkg    ubuntu-wallpapers-quantal
pkg    ubuntu-wallpapers-raring
pkg    ubuntu-wallpapers-saucy
pkg    ubuntu-wallpapers-trusty
pkg    ubuntu-wallpapers-utopic
pkg    ubuntu-wallpapers-vivid
pkg    ubuntu-wallpapers-wily
pkg    ubuntu-wallpapers-xenial
pkg    ubuntu-wallpapers-yakkety
pkg    ubuntu-wallpapers-zesty
pkg    wbritish
pkg    wdanish
pkg    wfaroese
pkg    whois
pkg    wmctrl
pkg    wnorwegian
pkg    wswedish
pkg    xvfb
pkg    xubuntu-community-wallpapers
pkg    xubuntu-community-wallpapers-bionic
pkg    xubuntu-community-wallpapers-trusty
pkg    xubuntu-community-wallpapers-xenial
pkg    xzdec
pkg    youtube-dl

exec apt-get install "${pkglist[@]}"

```

i have since installed a few more.  i need to add those to this script

---

### Post by uRock on 2019-07-16
gparted
vlc
wireshark
zenmap
htop
devede
audacity
audacious
gufw
chrome
simplescreenrecorder
bluefish
wifite
motion (as most of my systems have webcams connected to them)
I am sure there are some that I am forgetting. Currently playing on my netbook.

---

