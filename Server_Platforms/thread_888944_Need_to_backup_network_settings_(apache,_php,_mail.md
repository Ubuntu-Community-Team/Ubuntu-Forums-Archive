---
title: "Need to backup network settings (apache, php, mail)"
date: 2008-08-13
forum: Server Platforms
---

### Post by BlueKnight84 on 2008-08-13
Hi.  I'm a newbie to Ubuntu.  I am in need of backing up my network settings, including Apache, php, mail, you name it.  I need to do this because I inherited a server that I would have absolutely NO idea how to restore, and I need to reinstall Ubuntu.

I've been told that by retaining the /home folder is all I need to do, but I'm skeptical.  It's imperative that I be able to reinstall Ubuntu server and simply be able to restore my currently functioning mail server.

So how do I go about backing up my network/server settings?

---

### Post by windependence on 2008-08-13
You will also need /etc and maybe more depending on where things were installed but generally if you back up /home and /ect and install on the same hardware with the same version most things should be OK. You will probably have to reinstall some apps and then restore /etc.

-Tim

---

### Post by BlueKnight84 on 2008-08-13
> **windependence said:**
> You will also need /etc and maybe more depending on where things were installed but generally if you back up /home and /ect and install on the same hardware with the same version most things should be OK. You will probably have to reinstall some apps and then restore /etc.

-Tim

Thanks for the quick response.

The current distribution installed is Ubuntu 6.10.  Old, I know.  So when you say "same version," do you mean I might have problems going from 6.10 to the most current Ubuntu?

---

### Post by windependence on 2008-08-13
Yes, do your reinstall, and then upgrade.

-Tim

---

### Post by BlueKnight84 on 2008-08-13
> **windependence said:**
> Yes, do your reinstall, and then upgrade.

-Tim

I would just reinstall 6.10 and upgrade, but 6.10 is no longer supported and won't upgrade.

Will it work the same if I just backup the /etc and /home folders and install the most recent Ubuntu distro?

---

### Post by windependence on 2008-08-13
Well in theory it should but if they have changed anything in where the config files are stored you could have problems. Where did you see that you can't upgrade from an earlier version? You might have to go up one by one, but I think it can be done? Why are you upgrading? Does someting not work right? the 6.06 LTS release is still supported and lots of people are using it still.

-Tim

---

### Post by BlueKnight84 on 2008-08-13
> **windependence said:**
> Well in theory it should but if they have changed anything in where the config files are stored you could have problems. Where did you see that you can't upgrade from an earlier version? You might have to go up one by one, but I think it can be done? Why are you upgrading? Does someting not work right? the 6.06 LTS release is still supported and lots of people are using it still.

-Tim

I haven't been able to upgrade because I encounter errors anytime I try to use apt-get or network upgrade.  Below is an example:

```
$ sudo apt-get install mailman
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-rendition xserver-xorg-input-evdev
  xserver-xorg-video-newport xserver-xorg-video-s3virge xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-glint
  xserver-xorg-video-fbdev xserver-xorg-input-wacom xserver-xorg-video-v4l
  xserver-xorg-video-mga xserver-xorg-input-mouse xserver-xorg-video-nsc
  xserver-xorg-video-vesa xserver-xorg-video-siliconmotion
  xserver-xorg-video-tga xserver-xorg-video-sis xserver-xorg-video-vga
  xserver-xorg-video-via xserver-xorg-video-s3 xserver-xorg-video-nv
  xserver-xorg-core xserver-xorg-video-tseng xserver-xorg-video-savage
  xserver-xorg-input-all xserver-xorg-input-elographics
  xserver-xorg-video-vmware xserver-xorg-input-kbd xserver-xorg-video-i128
  xserver-xorg-video-neomagic xserver-xorg-video-chips
  xserver-xorg-video-voodoo xserver-xorg-video-i740 xserver-xorg-video-i810
  xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-input-synaptics xserver-xorg-video-sisusb
  xserver-xorg-video-imstt xserver-xorg-video-cirrus
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  pwgen
Suggested packages:
  spamassassin lynx python2.3-korean-codecs python2.2-korean-codecs
  python-japanese-codecs listadmin
The following NEW packages will be installed:
  mailman pwgen
0 upgraded, 2 newly installed, 0 to remove and 34 not upgraded.
Need to get 8035kB of archives.
After unpacking 37.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  pwgen mailman
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com edgy/main pwgen 2.05-1ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com edgy-updates/main mailman 1:2.1.8-2ubuntu2.1
  404 Not Found [IP: 91.189.88.46 80]
Err http://security.ubuntu.com edgy-security/main mailman 1:2.1.8-2ubuntu2.1
  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwgen/pwgen_2.05-1ubuntu1_i386.deb  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/m/mailman/mailman_2.1.8-2ubuntu2.1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

If I could just upgrade, I would.  I wanted to upgrade/reinstall because I want to install Mailman, but I can't install or upgrade because it wont' connect to the mirrors.  I feel like I'm screwed.

---

### Post by windependence on 2008-08-14
Reinstalling seems like a big step and a lot of trouble just to install one package. Let's fix that, OK?

First give me the output of :

```
cat /etc/resolv.conf
```

us.archive.ubuntu.com is resolving to 91.189.88.46 according to the error message, but the IP should be 91.189.88.31. I think you may have a DNS problem.

Also, you can try:

```
apt-get update 
```

before you run the install command for mailman.

-Tim

---

### Post by MJN on 2008-08-14
As it is a 404 error it suggests a file not found error as opposed to the DNS not resolving.
 
If you look at [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwgen/](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwgen/) you can see there's no pwgen_2.05-1ubuntu1_i386.deb but your apt thinks there ought to be.
 
Try running apt-get update as it could well be your package version lists are out-of-date.
 
Mathew
 
Edit: Actually, scrub all that - I've just noticed you're using 6.10 which is no longer supported. I had assumed this just meant it would not receive any further updates but perhaps it actually means it has its repositories wiped? I could well be wrong...  This doesn't stop you upgrading of course, but you will need to use the 7.04 repositories as per the upgrade instructions.

---

### Post by BlueKnight84 on 2008-08-14
> **MJN said:**
> As it is a 404 error it suggests a file not found error as opposed to the DNS not resolving.
 
If you look at [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwgen/](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pwgen/) you can see there's no pwgen_2.05-1ubuntu1_i386.deb but your apt thinks there ought to be.
 
Try running apt-get update as it could well be your package version lists are out-of-date.
 
Mathew
 
Edit: Actually, scrub all that - I've just noticed you're using 6.10 which is no longer supported. I had assumed this just meant it would not receive any further updates but perhaps it actually means it has its repositories wiped? I could well be wrong...  This doesn't stop you upgrading of course, but you will need to use the 7.04 repositories as per the upgrade instructions.

Thanks to both of you for helping me out...

How do I go about using the 7.04 repositories?  So you're saying I can still upgrade, because that would be great!

---

### Post by windependence on 2008-08-15
Yep you sure can.

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

-Tim

---

