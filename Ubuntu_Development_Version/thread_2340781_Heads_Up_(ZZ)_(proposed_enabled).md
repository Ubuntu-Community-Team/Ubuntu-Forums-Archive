---
title: "Heads Up (ZZ) (proposed enabled)"
date: 2016-10-22
forum: Ubuntu Development Version
---

### Post by zika on 2016-10-22
```
Setting up grub-pc (2.02~beta2-36ubuntu12) ...dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 128
Processing triggers for libc-bin (2.24-3ubuntu1) ...
Errors were encountered while processing:
 grub-pc
```More later...
Update&#8321;: Reboot was OK. This time I've dogged a bite from proposed...
Update&#8322;: My patience is not my virtue. Now, that all packages are done, on another machine (at work), all is nice with  grub-pc/zesty,now 2.02~beta2-36ubuntu12 amd64 ...
Update&#8323;: Grub2 (2.02~beta2-36ubuntu12 amd64) still refuses to configure on this machine (home) so I'll have to investigate further...
Update&#8324;: Yes, I've reported that it affects me in appropriate bug report...
Update&#8325;: This &#8222;bug&#8220; is totally self-inflicted in my case. As soon as found some spare time I've checked all the scripts involved and my typo in one of them triggered this error in Grub2 configuring itself. Mea culpa, mea maxima culpa... Removed myself from a list of affected for this bug.

---

### Post by ventrical on 2016-10-22
It didn't happen here.

---

### Post by zika on 2016-10-22
> **ventrical said:**
> It didn't happen here.As far as I can see You do not have proposed enabled so...

---

### Post by ventrical on 2016-10-22
Uhh.. yes .. I just re-read your post.  It's 4:30 am here... obviously I need sleep :)

Regards..

---

### Post by rrnbtter on 2016-10-23
Greetings,
New install, proposed enabled, Intel system, all is well..... so far.

Distributor ID:	Ubuntu
Description:	Ubuntu 16.10
Release:	16.10
Codename:	yakkety
rrnbtter@rrnbtter-Satellite-L305:~$ uname -a
Linux rrnbtter-Satellite-L305 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:01:44 UTC 2016 i686 i686 i686 GNU/Linux

---

### Post by ventrical on 2016-10-23
> **rrnbtter said:**
> Greetings,
New install, proposed enabled, Intel system, all is well..... so far.

Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety
rrnbtter@rrnbtter-Satellite-L305:~$ uname -a
Linux rrnbtter-Satellite-L305 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:01:44 UTC 2016 i686 i686 i686 GNU/Linux

It's Zesty Zapus  :)

regards..

---

### Post by zika on 2016-10-23
> **rrnbtter said:**
> Greetings,
New install, proposed enabled, Intel system, **all is well..... so far**.

Distributor ID:    Ubuntu
[B]Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety[/B]
rrnbtter@rrnbtter-Satellite-L305:~$ uname -a
Linux rrnbtter-Satellite-L305 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:01:44 UTC 2016 i686 i686 i686 GNU/LinuxI (obviously wrongly) assumed that we need a thread where HUs could be announced and only for ZZ (as it is given in the name of the thread). Back to the point where everything is written everywhere... Mea culpa.

---

### Post by rrnbtter on 2016-10-23
Greetings,
Sorry guys! I put a fresh yakkety install on a spare HD so as to have a clean Zesty upgrade and forgot to upgrade. Bad case of early onset can't remember nothing! It ain't easy being old. I will upgrade and report back. Thanks

---

### Post by rrnbtter on 2016-10-23
Greetings,
Yep, not ready for proposed yet.
This is what I get without it.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  efibootmgr fwupdate libclone-perl libhtml-parser-perl libio-pty-perl
  liblist-moreutils-perl liblocale-gettext-perl libnet-ssleay-perl
  libsystemsettings1 libxml-parser-perl onboard onboard-data perl perl-base
  ubuntu-system-settings xserver-xorg-input-all
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
rrnbtter@rrnbtter-Satellite-L305:~$ 

rrnbtter@rrnbtter-Satellite-L305:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Zesty Zapus (development branch)
Release:	17.04
Codename:	zesty
rrnbtter@rrnbtter-Satellite-L305:~$ 


rrnbtter@rrnbtter-Satellite-L305:~$ uname -a
Linux rrnbtter-Satellite-L305 4.8.0-27-generic #29-Ubuntu SMP Thu Oct 20 21:01:44 UTC 2016 i686 i686 i686 GNU/Linux
rrnbtter@rrnbtter-Satellite-L305:~$

---

### Post by zika on 2016-10-24
What's the HU? More a post for [https://ubuntuforums.org/showthread.php?t=2340194&p=13558941#post13558941](https://ubuntuforums.org/showthread.php?t=2340194&p=13558941#post13558941) ... Code-tags would help in reading...
I've edited my post above to notify that HU with grub is over... If anyone reads posts at all... ;)

---

### Post by ventrical on 2016-10-24
> **zika said:**
> What's the HU? More a post for [https://ubuntuforums.org/showthread.php?t=2340194&p=13558941#post13558941](https://ubuntuforums.org/showthread.php?t=2340194&p=13558941#post13558941) ... Code-tags would help in reading...
I've edited my post above to notify that HU with grub is over... If anyone reads posts at all... ;)

Well,  I am reading your posts and I have no idea what a "HU" is. Would you care to elaborate?

Regards..

---

### Post by zika on 2016-10-24
> **ventrical said:**
> Well,  I am reading your posts and I have no idea what a "HU" is. Would you care to elaborate?
Regards..Given in the name of the thread. Mea culpa.

---

### Post by ventrical on 2016-10-24
:)

I used to be quicker at one time deciphering nmenonics.


Thanks for the HU.

;)

Regards..

---

### Post by MikeMecanic on 2016-11-16
Kernel 4.9 is in proposed and should be in main soon.
 
 
 ```
Installation finished. No error reported.

 Generating grub configuration file ...
 Found linux image: /boot/vmlinuz-4.9.0-040900rc5-generic
 Found initrd image: /boot/initrd.img-4.9.0-040900rc5-generic
 Found linux image: /boot/vmlinuz-4.9.0-1-generic
 Found initrd image: /boot/initrd.img-4.9.0-1-generic
 Found linux image: /boot/vmlinuz-4.8.0-27-generic
 Found initrd image: /boot/initrd.img-4.8.0-27-generic

 Found memtest86+ image: /memtest86+.elf
 Found memtest86+ image: /memtest86+.bin
 Found Windows 10 (loader) on /dev/sda1
 done
 Setting up dnsutils (1:9.10.3.dfsg.P4-10.1ubuntu2) ...
 Setting up linux-generic (4.9.0.1.2) ...

```

---

### Post by dino99 on 2016-11-16
Well, can't go past the greeter loop with a nvidia driver    lp: 1640181

Error! Bad return status for module build on kernel: 4.9.0-1-generic (x86_64)
Consult /var/lib/dkms/nvidia-370/370.28/build/make.

---

### Post by Smask on 2016-11-16
Mike, I just noticed that zesty-proposed got auto-disabled here on my my boxes (did software-updates* do something?) and enabling it again brought in about 200Mb of updates and cleared out most of the list containing Local or obsolete packages (including Linux kernel 4.8.0-27)

---

### Post by MikeMecanic on 2016-11-16
> **Smask said:**
> Mike, I just noticed that zesty-proposed got auto-disabled here on my my boxes (did software-updates* do something?) and enabling it again brought in about 200Mb of updates and cleared out most of the list containing Local or obsolete packages (including Linux kernel 4.8.0-27)


If Proposed is enable it stay that way here (always enable).  For the clean up on local or obsolete, it is made by me in Synaptic manually.  An incoming Kernel never cleans the machine for me and I don’t remember seeing an issue like this.   
 Except maybe when the boot partition is in the saturation region.  Even there, a message asks to clean the partition.  I don’t understand? Did you _reload_ the content of Software & updates after enabling Proposed?  It’s about the only thing I see.

 The 200MB your talking about is the full content of Proposed when you enable it the first time.
 
 [B]Content of Proposed as shown in Synaptic after a fresh install of Gnome 17.04 (232MB):
 [/B]
 
 [HTML]Commit Log for Sun Nov 13 17:39:09 2016

  Upgraded the following packages:
 appstream (0.10.2-1) to 0.10.3-1
 efibootmgr (0.12-4) to 14-1
 ffmpeg (7:3.2-2) to 7:3.2-2build1
 fonts-opensymbol (2:102.7+LibO5.2.2-0ubuntu2) to 2:102.7+LibO5.2.2-0ubuntu3
 fwupd (0.7.2-0ubuntu1) to 0.7.4-2
 fwupdate (0.5-2ubuntu4) to 8-3
 fwupdate-signed (1.11+0.5-2ubuntu4) to 1.12+8-3
 gir1.2-javascriptcoregtk-4.0 (2.14.1-1) to 2.14.2-1
 gir1.2-lokdocview-0.1 (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 gir1.2-notify-0.7 (0.7.6-2svn1) to 0.7.7-1
 gir1.2-webkit2-4.0 (2.14.1-1) to 2.14.2-1
 gnome-photos (3.22.1-1) to 3.22.2-1
 gnome-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2) to 3.22.2+git20161108.0.a58dfc7-0ubuntu1
 gnome-software-common (3.20.1+git20161013.0.d77d6cf-0ubuntu2) to 3.22.2+git20161108.0.a58dfc7-0ubuntu1
 gstreamer1.0-plugins-good (1.8.3-1ubuntu1) to 1.8.3-1ubuntu2
 gstreamer1.0-pulseaudio (1.8.3-1ubuntu1) to 1.8.3-1ubuntu2
 gtk2-engines-pixbuf (2.24.30-4ubuntu2) to 2.24.31-1ubuntu1
 iw (3.17-1) to 4.9-0.1
 krb5-locales (1.14.3+dfsg-2) to 1.15~beta1-1
 libappstream4 (0.10.2-1) to 0.10.3-1
 libavcodec57 (7:3.2-2) to 7:3.2-2build1
 libavdevice57 (7:3.2-2) to 7:3.2-2build1
 libavfilter6 (7:3.2-2) to 7:3.2-2build1
 libavformat57 (7:3.2-2) to 7:3.2-2build1
 libavresample3 (7:3.2-2) to 7:3.2-2build1
 libavutil55 (7:3.2-2) to 7:3.2-2build1
 libbasicusageenvironment1 (2016.07.19-1) to 2016.11.06-1
 libcairo-gobject2 (1.14.6-1build1) to 1.14.6-1.1
 libcairo2 (1.14.6-1build1) to 1.14.6-1.1
 libdfu1 (0.7.2-0ubuntu1) to 0.7.4-2
 libedit2 (3.1-20150325-1ubuntu2) to 3.1-20160903-1
 libfwupd1 (0.7.2-0ubuntu1) to 0.7.4-2
 libgail-common (2.24.30-4ubuntu2) to 2.24.31-1ubuntu1
 libgail18 (2.24.30-4ubuntu2) to 2.24.31-1ubuntu1
 libglib2.0-0 (2.50.0-1) to 2.50.2-1
 libglib2.0-bin (2.50.0-1) to 2.50.2-1
 libglib2.0-data (2.50.0-1) to 2.50.2-1
 libgroupsock8 (2016.07.19-1) to 2016.11.06-1
 libgspell-1-1 (1.0.3-1ubuntu3) to 1.2.0-2
 libgssapi-krb5-2 (1.14.3+dfsg-2) to 1.15~beta1-1
 libgstreamer-plugins-good1.0-0 (1.8.3-1ubuntu1) to 1.8.3-1ubuntu2
 libgtk2.0-0 (2.24.30-4ubuntu2) to 2.24.31-1ubuntu1
 libgtk2.0-bin (2.24.30-4ubuntu2) to 2.24.31-1ubuntu1
 libgtk2.0-common (2.24.30-4ubuntu2) to 2.24.31-1ubuntu1
 libjavascriptcoregtk-4.0-18 (2.14.1-1) to 2.14.2-1
 libk5crypto3 (1.14.3+dfsg-2) to 1.15~beta1-1
 libkpathsea6 (2016.20160513.41080-6) to 2016.20160513.41080-7
 libkrb5-3 (1.14.3+dfsg-2) to 1.15~beta1-1
 libkrb5support0 (1.14.3+dfsg-2) to 1.15~beta1-1
 liblibreofficekitgtk (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 liblouis-data (2.6.5-1) to 3.0.0-3
 libmirclient9 (0.24.1+16.10.20160928-0ubuntu1) to 0.24.1+16.10.20160928-0ubuntu2
 libmircommon6 (0.24.1+16.10.20160928-0ubuntu1) to 0.24.1+16.10.20160928-0ubuntu2
 libmirprotobuf3 (0.24.1+16.10.20160928-0ubuntu1) to 0.24.1+16.10.20160928-0ubuntu2
 libnih1 (1.0.3-4.3ubuntu1) to 1.0.3-6ubuntu1
 libnotify-bin (0.7.6-2svn1) to 0.7.7-1
 libnotify4 (0.7.6-2svn1) to 0.7.7-1
 libpcap0.8 (1.7.4-2) to 1.8.1-3
 libpostproc54 (7:3.2-2) to 7:3.2-2build1
 libpulse-mainloop-glib0 (1:9.0-2ubuntu2) to 1:9.0-5ubuntu2
 libpulse0 (1:9.0-2ubuntu2) to 1:9.0-5ubuntu2
 libpulsedsp (1:9.0-2ubuntu2) to 1:9.0-5ubuntu2
 libreoffice-avmedia-backend-gstreamer (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-base-core (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-calc (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-common (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-core (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-draw (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-gnome (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-gtk3 (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-impress (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-math (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-ogltrans (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-pdfimport (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-style-elementary (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-style-galaxy (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-style-tango (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreoffice-writer (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libreofficekit-data (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 libsasl2-2 (2.1.26.dfsg1-15) to 2.1.27~72-g88d82a3+dfsg-1
 libsasl2-modules (2.1.26.dfsg1-15) to 2.1.27~72-g88d82a3+dfsg-1
 libsasl2-modules-db (2.1.26.dfsg1-15) to 2.1.27~72-g88d82a3+dfsg-1
 libswresample2 (7:3.2-2) to 7:3.2-2build1
 libswscale4 (7:3.2-2) to 7:3.2-2build1
 libusageenvironment3 (2016.07.19-1) to 2016.11.06-1
 libvlc5 (2.2.4-4) to 2.2.4-8
 libvlccore8 (2.2.4-4) to 2.2.4-8
 libwebkit2gtk-4.0-37 (2.14.1-1) to 2.14.2-1
 libwebkit2gtk-4.0-37-gtk2 (2.14.1-1) to 2.14.2-1
 libxml2 (2.9.4+dfsg1-2) to 2.9.4+dfsg1-2.1
 libxml2-utils (2.9.4+dfsg1-2) to 2.9.4+dfsg1-2.1
 libzeitgeist-2.0-0 (0.9.16-0ubuntu5) to 0.9.16-0ubuntu6
 linux-generic (4.8.0.26.35) to 4.8.0.27.36
 linux-headers-generic (4.8.0.26.35) to 4.8.0.27.36
 linux-image-generic (4.8.0.26.35) to 4.8.0.27.36
 pulseaudio (1:9.0-2ubuntu2) to 1:9.0-5ubuntu2
 pulseaudio-module-bluetooth (1:9.0-2ubuntu2) to 1:9.0-5ubuntu2
 pulseaudio-utils (1:9.0-2ubuntu2) to 1:9.0-5ubuntu2
 python-libxml2 (2.9.4+dfsg1-2) to 2.9.4+dfsg1-2.1
 python-requests (2.10.0-2) to 2.11.1-1
 python-urllib3 (1.15.1-2) to 1.16-1
 python3-louis (2.6.5-1) to 3.0.0-3
 python3-requests (2.10.0-2) to 2.11.1-1
 python3-uno (1:5.2.2-0ubuntu2) to 1:5.2.2-0ubuntu3
 python3-update-manager (1:16.10.7) to 1:17.04.1
 python3-urllib3 (1.15.1-2) to 1.16-1
 snapd (2.16+16.10ubuntu1) to 2.17.1+17.04ubuntu1
 uno-libs3 (5.2.2-0ubuntu2) to 5.2.2-0ubuntu3
 update-manager (1:16.10.7) to 1:17.04.1
 update-manager-core (1:16.10.7) to 1:17.04.1
 ure (5.2.2-0ubuntu2) to 5.2.2-0ubuntu3
 vlc (2.2.4-4) to 2.2.4-8
 vlc-data (2.2.4-4) to 2.2.4-8
 vlc-nox (2.2.4-4) to 2.2.4-8
 vlc-plugin-notify (2.2.4-4) to 2.2.4-8
 vlc-plugin-samba (2.2.4-4) to 2.2.4-8
 zeitgeist-core (0.9.16-0ubuntu5) to 0.9.16-0ubuntu6
 
 
 Installed the following packages:
 gir1.2-appstreamglib-1.0 (0.6.4-2)
 gir1.2-gusb-1.0 (0.2.9-1)
 libchromaprint1 (1.3.2-2)
 libebitdo1 (0.7.4-2)
 libefiboot1 (30-1ubuntu1)
 libefivar1 (30-1ubuntu1)
 libfwup1 (8-3)
 libglew2.0 (2.0.0-3)
 libgspell-1-common (1.2.0-2)
 liblivemedia57 (2016.11.06-1)
 liblouis12 (3.0.0-3)
 libsmbios2v5 (2.3.1-0ubuntu1)
 libvlc-bin (2.2.4-8)
 libvpx4 (1.6.0-3)
 libx265-95 (2.1-2)
 libxapian30 (1.4.1-1)
 libxdelta2 (1.1.3-9.1ubuntu1)
 linux-headers-4.8.0-27 (4.8.0-27.29)
 linux-headers-4.8.0-27-generic (4.8.0-27.29)
 linux-image-4.8.0-27-generic (4.8.0-27.29)
 linux-image-extra-4.8.0-27-generic (4.8.0-27.29)
 vlc-bin (2.2.4-8)
 vlc-l10n (2.2.4-8)
 vlc-plugin-base (2.2.4-8)
 vlc-plugin-qt (2.2.4-8)
 vlc-plugin-skins2 (2.2.4-8)
 vlc-plugin-video-output (2.2.4-8)
 vlc-plugin-video-splitter (2.2.4-8)
 vlc-plugin-visualization (2.2.4-8)
 xdelta (1.1.3-9.1ubuntu1)
 
 
[/HTML] Regards,

---

### Post by Smask on 2016-11-16
> **MikeMecanic said:**
> If Proposed is enable it stay that way here (always enable).  For the clean up on local or obsolete, it is made by me in Synaptic manually.  An incoming Kernel never cleans the machine for me and I don’t remember seeing an issue like this.   
 Except maybe when the boot partition is in the saturation region.  Even there, a message asks to clean the partition.  I don’t understand? Did you _reload_ the content of Software & updates after enabling Proposed?  It’s about the only thing I see.

 The 200MB your talking about is the full content of Proposed when you enable it the first time.

I usually have proposed enabled on all boxes here, but somehow something disabled proposed...

My normal update routine is  as follows: Update-Mangler only, unless it asks "Partial upgrade?", where the answer is "**NO! **I don't need another hole in my head"  just update whatever package it think can be updated safely. Then I run Synaptic (with reload) to check what will be added or removed.

Stuff I had in my Local or obsolete list, until today:
nih and nih-dbus, these two has been there since Xenial days
kernel 4.8.0-27, remnant since dist-upgrade from Yakkety.
libc
initramfs-tools
snapd
some gstreamer packages


Kernel 4.9 is the first kernel update since Yakkety

---

### Post by MikeMecanic on 2016-11-16
> **Smask said:**
> I usually have proposed enabled on all boxes here, but somehow something disabled proposed...

My normal update routine is  as follows: Update-Mangler only, unless it asks "Partial upgrade?", where the answer is "**NO! **I don't need another hole in my head"  just update whatever package it think can be updated safely. Then I run Synaptic (with reload) to check what will be added or removed.


You were on Xenial and last week *.27 was removed in Proposed under Kylin ZZ in the middle of the week.  I do believe they were having problems with this one.  That would maybe explain why you lost it.
 
 It is exactly the way to proceed when we run custom Kernel or when Proposed is enable= read twice the content of incoming updates.   
 
 What do you see in Synaptic under residual conflicts that can explain the lost?  Is there an upgrade folder shown in status?  Upgrade returns this type of error sometime.

FYI, Gnome runs very well and the only things that goes wrong is that SMPlayer PPA'S are not available yet.

---

