---
title: "Classic (no effects) session fails to boot w/P4M800 graphics"
date: 2012-08-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-08-17
I was just curious how this would all work out on my old P4M800 graphics so I first tried booting the new Unity session and that's a no go - no surprise there. But I notice that unity-greeter is also removed.

So I had a 20120815 disc laying here that I'd used for other purposes. This was I believe the last spin before the removal of Unity-2d, so I tried  a fresh install and before updating I installed 'gnome-panel' and made sure that I was booting gnome-classic (no effects) OK with no auto-login.

Still refused to boot similar to what I saw testing DE conversions in 12.04 so I tried installing and configuring 'gdm' while in recovery mode but booting is still a no-go :(

I need to review some old notes and think about possibly using the lightdm greeter used by Lubuntu and Xubuntu. Just wanted to give a heads-up ;)

I must be a sick puppy, I love this kind of breakage :redface:

---

### Post by kansasnoob on 2012-08-17
I'm in the middle of something else ATM but I'm thinking about installing 'lightdm-gtk-greeter' and then running:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter
```

Then of course:

```
sudo dpkg-reconfigure lightdm
```

Any thoughts :confused:

---

### Post by mc4man on 2012-08-17
Not really but am curious - why was unity greeter removed? (currently 0ubuntu2 which doesn't run the unity_support_test anymore

---

### Post by kansasnoob on 2012-08-17
> **mc4man said:**
> Not really but am curious - why was unity greeter removed? (currently 0ubuntu2 which doesn't run the unity_support_test anymore

I may be misinterpreting what the changelog says:

> unity-greeter (12.10.0-0ubuntu2) quantal; urgency=low

  * debian/patches/run_unity_support_test.patch:
    - removed, we only support unity-3d now and fallback with llvmpipe
      if there is no GL acceleration (LP: #1035261)

 -- Didier Roche <didrocks@ubuntu.com>  Wed, 15 Aug 2012 08:39:47 +0200

I'm actually a bit clueless, well more than just a bit :biggrin:

---

### Post by kansasnoob on 2012-08-17
Actually I see from looking on my unaffected Intel box that some of the packages I thought were "removed" are actually still there:

[ATTACH]222818[/ATTACH]

Same way with unity-greeter, must just be a config file type of thing.

---

### Post by mc4man on 2012-08-17
I wouldn't know what the current mechanism is.. 
but as far as the changelog - 
It removed a patch from unity-greeter that did this
> Description: try to run unity_support_test for ubuntu for pre-caching the result in /tmp for further call while the user is typing his password.


So one would hope that would have no effect on an updated install that _already had Classic (no effects) installed_ from continuing to be able to login to Classic. (though you seem to say it doesn't allow??

What would also be of some interest if an updated 08/15 install with Classic already installed & _able to log in to _- 
 
If you used today's iso on that hardware  it has only 'unity' on it. So if your hardware failed OpenGL 2.0 & failed to use llvmpipe  then I guess you'd be out of luck even though it could actually run Classic (No effects) unless you used some alt. means to get Classic installed

---

### Post by kansasnoob on 2012-08-17
I noticed at the time that many xorg pkgs were updated as well, so it could even been due to 'xserver-xorg-video-openchrome'. Finally some breakage to focus on :)

I'm going to be testing 12.04.1 images like crazy next week to try and get a few pet bugs fixed but I'll definitely follow up on this later.

---

### Post by kansasnoob on 2012-08-17
I corrected the title to more properly reflect the problem :)

---

### Post by dino99 on 2012-08-17
here on i386 with gnome-classic, unity-greeter is still installed : 3.5 kernel boots as usual, but 3.6 have issue showing lightdm (seems hidden by a strange rgb window, as i can blindly enter the password to continue, but the window is fully corrupted and so not usable)

---

### Post by kansasnoob on 2012-08-17
Many thanks to cariboo907 for correcting my title :)

I'm gonna' need to wipe that install soon to do some 12.04.1 testing but I grabbed some info from a lateral install using that same 20120815 iso.

Here's the applicable part(s) of the history.log:

```
Start-Date: 2012-08-17  04:00:03
Commandline: apt-get install gnome-panel
Install: libpanel-applet-4-0:i386 (3.5.4-0ubuntu2, automatic), gir1.2-gconf-2.0:i386 (3.2.5-0ubuntu2, automatic), alacarte:i386 (3.5.4-0ubuntu1, automatic), indicator-applet-complete:i386 (0.5.0-0ubuntu3, automatic), gnome-session-fallback:i386 (3.5.5-0ubuntu3, automatic), cups-pk-helper:i386 (0.2.1.2-1, automatic), gnome-applets:i386 (3.5.1-0ubuntu2, automatic), gnome-panel:i386 (3.5.4-0ubuntu2), gnome-applets-data:i386 (3.5.1-0ubuntu2, automatic), gir1.2-panelapplet-4.0:i386 (3.5.4-0ubuntu2, automatic), gnome-panel-data:i386 (3.5.4-0ubuntu2, automatic)
Upgrade: gnome-session-common:i386 (3.5.5-0ubuntu1, 3.5.5-0ubuntu3), gnome-session-bin:i386 (3.5.5-0ubuntu1, 3.5.5-0ubuntu3), gnome-session:i386 (3.5.5-0ubuntu1, 3.5.5-0ubuntu3)
End-Date: 2012-08-17  04:01:16

Start-Date: 2012-08-17  04:16:48
Commandline: aptdaemon role='role-commit-packages' sender=':1.75'
Install: libpoppler27:i386 (0.20.3-2ubuntu1), libdrm-nouveau2:i386 (2.4.38-0ubuntu1)
Upgrade: libunity-core-6.0-5:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), bluez-alsa:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), unity:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), libstdc++6:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), plymouth-theme-ubuntu-text:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), libnm-glib-vpn1:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), unity-2d:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), xserver-xorg-input-evdev:i386 (2.7.0-0ubuntu2, 2.7.3-0ubuntu1), libcompizconfig0:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), python3-apport:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), unity-2d-panel:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), bluez-gstreamer:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), libplymouth2:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), xserver-xorg-video-ati:i386 (6.14.99~really6.14.4-0ubuntu2, 6.99.99~git20120713.6ef1ad6a-0ubuntu1), gcc-4.7-base:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), libnux-3.0-common:i386 (3.2.0-0ubuntu1, 3.2.0-0ubuntu3), xserver-xorg-video-tdfx:i386 (1.4.4-1build1, 1.4.5-0ubuntu1), ubuntu-standard:i386 (1.279, 1.280), network-manager:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), xserver-xorg-video-trident:i386 (1.3.5-1build1, 1.3.6-0ubuntu1), xserver-xorg-video-fbdev:i386 (0.4.2-4ubuntu3, 0.4.3-0ubuntu1), xserver-xorg-input-wacom:i386 (0.14.0-0ubuntu3, 0.16.0+0git9f32b03-0ubuntu1), xterm:i386 (271-1ubuntu2, 278-1ubuntu1), xserver-xorg-video-mga:i386 (1.5.0-1build1, 1.6.0-0ubuntu1), libnm-util2:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), libdecoration0:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), plymouth-label:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), bluez-cups:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), lightdm:i386 (1.3.2-0ubuntu2, 1.3.2-0ubuntu3), xserver-xorg-input-vmmouse:i386 (12.9.0-0ubuntu1, 12.9.0-0ubuntu2), xserver-xorg-input-mouse:i386 (1.7.2-2, 1.7.2-2build1), xserver-xorg-video-r128:i386 (6.8.2-1build1, 6.8.4-0ubuntu1), xserver-common:i386 (1.12.1.902-1ubuntu1, 1.12.99.904-0ubuntu1), accountsservice:i386 (0.6.21-6ubuntu2, 0.6.21-6ubuntu3), libunity-2d-private0:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), xserver-xorg-video-openchrome:i386 (0.2.906-2, 0.3.0+0-0ubuntu1), ubuntu-desktop:i386 (1.279, 1.280), xserver-xorg-video-vesa:i386 (2.3.1-1build1, 2.3.2-0ubuntu1), libgomp1:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), apt-xapian-index:i386 (0.44ubuntu5, 0.44ubuntu6), unity-2d-shell:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), xserver-xorg-video-siliconmotion:i386 (1.7.6-1build1, 1.7.7-0ubuntu1), xserver-xorg-video-mach64:i386 (6.9.1-2build1, 6.9.3-0ubuntu1), xserver-xorg-video-sis:i386 (0.10.4-1build1, 0.10.7-0ubuntu1), unity-services:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), xserver-xorg-video-qxl:i386 (0.0.17-2ubuntu2, 0.0.18~gitde66207-0ubuntu1), unity-2d-common:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), apport:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), xserver-xorg-video-s3:i386 (0.6.3-4build3, 0.6.5-0ubuntu1), bluez:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), xserver-xorg-core:i386 (1.12.1.902-1ubuntu1, 1.12.99.904-0ubuntu1), gcc-4.7:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), compiz-plugins-default:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), dash:i386 (0.5.7-2ubuntu2, 0.5.7-3ubuntu1), xserver-xorg-video-savage:i386 (2.3.4-1ubuntu1, 2.3.6-0ubuntu1), xinput:i386 (1.5.99.1-0ubuntu2, 1.6.0-1), libgcc1:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), libaccountsservice0:i386 (0.6.21-6ubuntu2, 0.6.21-6ubuntu3), liblightdm-gobject-1-0:i386 (1.3.2-0ubuntu2, 1.3.2-0ubuntu3), compiz-plugins-main-default:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), libnm-glib4:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), xserver-xorg-video-nouveau:i386 (1.0.1-1build1, 1.0.1-4~ubuntu1), xserver-xorg-video-vmware:i386 (12.0.1-1ubuntu3, 12.0.2+git.e5ac80d8-0ubuntu1), unity-common:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), ubuntu-minimal:i386 (1.279, 1.280), python-problem-report:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), libbluetooth3:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), plymouth-theme-ubuntu-logo:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), unity-2d-spread:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), libgeis1:i386 (2.2.11-0ubuntu1, 2.2.12-0ubuntu1), xul-ext-ubufox:i386 (2.3-0ubuntu1, 2.4~r353-0ubuntu1), xserver-xorg-video-neomagic:i386 (1.2.6-1build1, 1.2.7-0ubuntu1), unity-greeter:i386 (12.10.0-0ubuntu1, 12.10.0-0ubuntu2), libxvmc1:i386 (1.0.6-1ubuntu2, 1.0.7-1ubuntu1), xserver-xorg-video-geode:i386 (2.11.13-4, 2.11.13+git20120726-0ubuntu2), poppler-utils:i386 (0.20.2-2ubuntu2, 0.20.3-2ubuntu1), libitm1:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), debconf:i386 (1.5.45ubuntu1, 1.5.46ubuntu1), libquadmath0:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), cpp-4.7:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), nux-tools:i386 (3.2.0-0ubuntu1, 3.2.0-0ubuntu3), compiz:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), python-apport:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), debconf-i18n:i386 (1.5.45ubuntu1, 1.5.46ubuntu1), compiz-core:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), xserver-xorg-input-synaptics:i386 (1.6.2-1ubuntu2, 1.6.2-1ubuntu4), libnux-3.0-0:i386 (3.2.0-0ubuntu1, 3.2.0-0ubuntu3), binutils:i386 (2.22.90.20120731-0ubuntu1, 2.22.90.20120816-1ubuntu1), apport-gtk:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), xserver-xorg-video-sisusb:i386 (0.9.4-3build1, 0.9.6-0ubuntu1), libxrandr2:i386 (1.3.2-2, 1.4.0-1), ntfs-3g:i386 (2012.1.15AR.5-2ubuntu1, 2012.1.15AR.5-4ubuntu1), python3-problem-report:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), linux-firmware:i386 (1.88, 1.89), xserver-xorg-video-radeon:i386 (6.14.99~really6.14.4-0ubuntu2, 6.99.99~git20120713.6ef1ad6a-0ubuntu1), file-roller:i386 (3.5.4-0ubuntu3, 3.5.4-0ubuntu5), plymouth:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), compiz-gnome:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), xserver-xorg-video-cirrus:i386 (1.4.0-1build1, 1.5.1-0ubuntu1), libpoppler-glib8:i386 (0.20.2-2ubuntu2, 0.20.3-2ubuntu1), xserver-xorg-video-intel:i386 (2.19.0-1ubuntu2, 2.20.3-0ubuntu1)
End-Date: 2012-08-17  04:23:40

Start-Date: 2012-08-17  04:33:38
Commandline: apt-get install gdm
Install: gdm:i386 (3.0.4-0ubuntu16)
End-Date: 2012-08-17  04:34:12

Start-Date: 2012-08-17  08:29:17
Commandline: apt-get install lubuntu-core
Install: lightdm-gtk-greeter:i386 (1.1.6-0ubuntu1), libobrender27:i386 (3.5.0-4, automatic), lxsession:i386 (0.4.9.1~git20120708-0ubuntu1, automatic), openbox-themes:i386 (1.0.2, automatic), libfm-data:i386 (1.0-0ubuntu1, automatic), libfm-gtk-bin:i386 (1.0-0ubuntu1, automatic), obconf:i386 (2.0.3+20110805+debian-1, automatic), lubuntu-default-settings:i386 (0.28), lubuntu-icon-theme:i386 (0.30, automatic), lxsession-data:i386 (0.4.9.1~git20120708-0ubuntu1, automatic), lubuntu-artwork:i386 (0.30), plymouth-theme-lubuntu-text:i386 (0.30), pcmanfm:i386 (1.0-0ubuntu1, automatic), lubuntu-core:i386 (0.42), libfm-gtk-data:i386 (1.0-0ubuntu1, automatic), libgif4:i386 (4.1.6-9ubuntu1, automatic), libfm-gtk3:i386 (1.0-0ubuntu1, automatic), lubuntu-artwork-12-10:i386 (0.30, automatic), openbox:i386 (3.5.0-4), libglade2-0:i386 (2.6.4-1ubuntu2, automatic), gnome-icon-theme-full:i386 (3.5.5-0ubuntu1, automatic), elementary-icon-theme:i386 (2.7.1-0ubuntu6, automatic), lxmenu-data:i386 (0.1.2-2, automatic), libfm3:i386 (1.0-0ubuntu1, automatic), lxshortcut:i386 (0.1.2-3, automatic), lxpanel:i386 (0.5.10-1ubuntu2), libid3tag0:i386 (0.15.1b-10build2, automatic), libimlib2:i386 (1.4.5-1ubuntu1, automatic), libmenu-cache1:i386 (0.3.3-1, automatic), libobt0:i386 (3.5.0-4, automatic), plymouth-theme-lubuntu-logo:i386 (0.30)
End-Date: 2012-08-17  08:32:24
```

And the term.log:

```
Start-Date: 2012-08-17  04:00:03
Commandline: apt-get install gnome-panel
Install: libpanel-applet-4-0:i386 (3.5.4-0ubuntu2, automatic), gir1.2-gconf-2.0:i386 (3.2.5-0ubuntu2, automatic), alacarte:i386 (3.5.4-0ubuntu1, automatic), indicator-applet-complete:i386 (0.5.0-0ubuntu3, automatic), gnome-session-fallback:i386 (3.5.5-0ubuntu3, automatic), cups-pk-helper:i386 (0.2.1.2-1, automatic), gnome-applets:i386 (3.5.1-0ubuntu2, automatic), gnome-panel:i386 (3.5.4-0ubuntu2), gnome-applets-data:i386 (3.5.1-0ubuntu2, automatic), gir1.2-panelapplet-4.0:i386 (3.5.4-0ubuntu2, automatic), gnome-panel-data:i386 (3.5.4-0ubuntu2, automatic)
Upgrade: gnome-session-common:i386 (3.5.5-0ubuntu1, 3.5.5-0ubuntu3), gnome-session-bin:i386 (3.5.5-0ubuntu1, 3.5.5-0ubuntu3), gnome-session:i386 (3.5.5-0ubuntu1, 3.5.5-0ubuntu3)
End-Date: 2012-08-17  04:01:16

Start-Date: 2012-08-17  04:16:48
Commandline: aptdaemon role='role-commit-packages' sender=':1.75'
Install: libpoppler27:i386 (0.20.3-2ubuntu1), libdrm-nouveau2:i386 (2.4.38-0ubuntu1)
Upgrade: libunity-core-6.0-5:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), bluez-alsa:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), unity:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), libstdc++6:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), plymouth-theme-ubuntu-text:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), libnm-glib-vpn1:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), unity-2d:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), xserver-xorg-input-evdev:i386 (2.7.0-0ubuntu2, 2.7.3-0ubuntu1), libcompizconfig0:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), python3-apport:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), unity-2d-panel:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), bluez-gstreamer:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), libplymouth2:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), xserver-xorg-video-ati:i386 (6.14.99~really6.14.4-0ubuntu2, 6.99.99~git20120713.6ef1ad6a-0ubuntu1), gcc-4.7-base:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), libnux-3.0-common:i386 (3.2.0-0ubuntu1, 3.2.0-0ubuntu3), xserver-xorg-video-tdfx:i386 (1.4.4-1build1, 1.4.5-0ubuntu1), ubuntu-standard:i386 (1.279, 1.280), network-manager:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), xserver-xorg-video-trident:i386 (1.3.5-1build1, 1.3.6-0ubuntu1), xserver-xorg-video-fbdev:i386 (0.4.2-4ubuntu3, 0.4.3-0ubuntu1), xserver-xorg-input-wacom:i386 (0.14.0-0ubuntu3, 0.16.0+0git9f32b03-0ubuntu1), xterm:i386 (271-1ubuntu2, 278-1ubuntu1), xserver-xorg-video-mga:i386 (1.5.0-1build1, 1.6.0-0ubuntu1), libnm-util2:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), libdecoration0:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), plymouth-label:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), bluez-cups:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), lightdm:i386 (1.3.2-0ubuntu2, 1.3.2-0ubuntu3), xserver-xorg-input-vmmouse:i386 (12.9.0-0ubuntu1, 12.9.0-0ubuntu2), xserver-xorg-input-mouse:i386 (1.7.2-2, 1.7.2-2build1), xserver-xorg-video-r128:i386 (6.8.2-1build1, 6.8.4-0ubuntu1), xserver-common:i386 (1.12.1.902-1ubuntu1, 1.12.99.904-0ubuntu1), accountsservice:i386 (0.6.21-6ubuntu2, 0.6.21-6ubuntu3), libunity-2d-private0:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), xserver-xorg-video-openchrome:i386 (0.2.906-2, 0.3.0+0-0ubuntu1), ubuntu-desktop:i386 (1.279, 1.280), xserver-xorg-video-vesa:i386 (2.3.1-1build1, 2.3.2-0ubuntu1), libgomp1:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), apt-xapian-index:i386 (0.44ubuntu5, 0.44ubuntu6), unity-2d-shell:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), xserver-xorg-video-siliconmotion:i386 (1.7.6-1build1, 1.7.7-0ubuntu1), xserver-xorg-video-mach64:i386 (6.9.1-2build1, 6.9.3-0ubuntu1), xserver-xorg-video-sis:i386 (0.10.4-1build1, 0.10.7-0ubuntu1), unity-services:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), xserver-xorg-video-qxl:i386 (0.0.17-2ubuntu2, 0.0.18~gitde66207-0ubuntu1), unity-2d-common:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), apport:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), xserver-xorg-video-s3:i386 (0.6.3-4build3, 0.6.5-0ubuntu1), bluez:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), xserver-xorg-core:i386 (1.12.1.902-1ubuntu1, 1.12.99.904-0ubuntu1), gcc-4.7:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), compiz-plugins-default:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), dash:i386 (0.5.7-2ubuntu2, 0.5.7-3ubuntu1), xserver-xorg-video-savage:i386 (2.3.4-1ubuntu1, 2.3.6-0ubuntu1), xinput:i386 (1.5.99.1-0ubuntu2, 1.6.0-1), libgcc1:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), libaccountsservice0:i386 (0.6.21-6ubuntu2, 0.6.21-6ubuntu3), liblightdm-gobject-1-0:i386 (1.3.2-0ubuntu2, 1.3.2-0ubuntu3), compiz-plugins-main-default:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), libnm-glib4:i386 (0.9.6.0-0ubuntu2, 0.9.6.0-0ubuntu3), xserver-xorg-video-nouveau:i386 (1.0.1-1build1, 1.0.1-4~ubuntu1), xserver-xorg-video-vmware:i386 (12.0.1-1ubuntu3, 12.0.2+git.e5ac80d8-0ubuntu1), unity-common:i386 (6.2.0-0ubuntu1, 6.2.0-0ubuntu2), ubuntu-minimal:i386 (1.279, 1.280), python-problem-report:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), libbluetooth3:i386 (4.101-0ubuntu4, 4.101-0ubuntu5), plymouth-theme-ubuntu-logo:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), unity-2d-spread:i386 (5.12.0-0ubuntu3, 6.2.0-0ubuntu2), libgeis1:i386 (2.2.11-0ubuntu1, 2.2.12-0ubuntu1), xul-ext-ubufox:i386 (2.3-0ubuntu1, 2.4~r353-0ubuntu1), xserver-xorg-video-neomagic:i386 (1.2.6-1build1, 1.2.7-0ubuntu1), unity-greeter:i386 (12.10.0-0ubuntu1, 12.10.0-0ubuntu2), libxvmc1:i386 (1.0.6-1ubuntu2, 1.0.7-1ubuntu1), xserver-xorg-video-geode:i386 (2.11.13-4, 2.11.13+git20120726-0ubuntu2), poppler-utils:i386 (0.20.2-2ubuntu2, 0.20.3-2ubuntu1), libitm1:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), debconf:i386 (1.5.45ubuntu1, 1.5.46ubuntu1), libquadmath0:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), cpp-4.7:i386 (4.7.1-6ubuntu1, 4.7.1-7ubuntu1), nux-tools:i386 (3.2.0-0ubuntu1, 3.2.0-0ubuntu3), compiz:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), python-apport:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), debconf-i18n:i386 (1.5.45ubuntu1, 1.5.46ubuntu1), compiz-core:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), xserver-xorg-input-synaptics:i386 (1.6.2-1ubuntu2, 1.6.2-1ubuntu4), libnux-3.0-0:i386 (3.2.0-0ubuntu1, 3.2.0-0ubuntu3), binutils:i386 (2.22.90.20120731-0ubuntu1, 2.22.90.20120816-1ubuntu1), apport-gtk:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), xserver-xorg-video-sisusb:i386 (0.9.4-3build1, 0.9.6-0ubuntu1), libxrandr2:i386 (1.3.2-2, 1.4.0-1), ntfs-3g:i386 (2012.1.15AR.5-2ubuntu1, 2012.1.15AR.5-4ubuntu1), python3-problem-report:i386 (2.4-0ubuntu6, 2.4-0ubuntu8), linux-firmware:i386 (1.88, 1.89), xserver-xorg-video-radeon:i386 (6.14.99~really6.14.4-0ubuntu2, 6.99.99~git20120713.6ef1ad6a-0ubuntu1), file-roller:i386 (3.5.4-0ubuntu3, 3.5.4-0ubuntu5), plymouth:i386 (0.8.4-0ubuntu1, 0.8.4-0ubuntu3), compiz-gnome:i386 (0.9.8+bzr3249-0ubuntu2, 0.9.8+bzr3249-0ubuntu4), xserver-xorg-video-cirrus:i386 (1.4.0-1build1, 1.5.1-0ubuntu1), libpoppler-glib8:i386 (0.20.2-2ubuntu2, 0.20.3-2ubuntu1), xserver-xorg-video-intel:i386 (2.19.0-1ubuntu2, 2.20.3-0ubuntu1)
End-Date: 2012-08-17  04:23:40

Start-Date: 2012-08-17  04:33:38
Commandline: apt-get install gdm
Install: gdm:i386 (3.0.4-0ubuntu16)
End-Date: 2012-08-17  04:34:12

Start-Date: 2012-08-17  08:29:17
Commandline: apt-get install lubuntu-core
Install: lightdm-gtk-greeter:i386 (1.1.6-0ubuntu1), libobrender27:i386 (3.5.0-4, automatic), lxsession:i386 (0.4.9.1~git20120708-0ubuntu1, automatic), openbox-themes:i386 (1.0.2, automatic), libfm-data:i386 (1.0-0ubuntu1, automatic), libfm-gtk-bin:i386 (1.0-0ubuntu1, automatic), obconf:i386 (2.0.3+20110805+debian-1, automatic), lubuntu-default-settings:i386 (0.28), lubuntu-icon-theme:i386 (0.30, automatic), lxsession-data:i386 (0.4.9.1~git20120708-0ubuntu1, automatic), lubuntu-artwork:i386 (0.30), plymouth-theme-lubuntu-text:i386 (0.30), pcmanfm:i386 (1.0-0ubuntu1, automatic), lubuntu-core:i386 (0.42), libfm-gtk-data:i386 (1.0-0ubuntu1, automatic), libgif4:i386 (4.1.6-9ubuntu1, automatic), libfm-gtk3:i386 (1.0-0ubuntu1, automatic), lubuntu-artwork-12-10:i386 (0.30, automatic), openbox:i386 (3.5.0-4), libglade2-0:i386 (2.6.4-1ubuntu2, automatic), gnome-icon-theme-full:i386 (3.5.5-0ubuntu1, automatic), elementary-icon-theme:i386 (2.7.1-0ubuntu6, automatic), lxmenu-data:i386 (0.1.2-2, automatic), libfm3:i386 (1.0-0ubuntu1, automatic), lxshortcut:i386 (0.1.2-3, automatic), lxpanel:i386 (0.5.10-1ubuntu2), libid3tag0:i386 (0.15.1b-10build2, automatic), libimlib2:i386 (1.4.5-1ubuntu1, automatic), libmenu-cache1:i386 (0.3.3-1, automatic), libobt0:i386 (3.5.0-4, automatic), plymouth-theme-lubuntu-logo:i386 (0.30)
End-Date: 2012-08-17  08:32:24
```

And of course even more pkgs would be updated now:

```
The following NEW packages will be installed:
  libdrm-nouveau2 libpoppler27 python-lxml
The following packages will be upgraded:
  accountsservice apport apport-gtk apt-xapian-index binutils bluez bluez-alsa
  bluez-cups bluez-gstreamer compiz compiz-core compiz-gnome
  compiz-plugins-default compiz-plugins-main-default cpp-4.7 dash debconf
  debconf-i18n file-roller gcc-4.7 gcc-4.7-base gnome-session
  gnome-session-bin gnome-session-common humanity-icon-theme
  libaccountsservice0 libbluetooth3 libcompizconfig0 libdecoration0 libgcc1
  libgeis1 libgomp1 libitm1 liblightdm-gobject-1-0 libmtdev1 libnm-glib-vpn1
  libnm-glib4 libnm-util2 libnux-3.0-0 libnux-3.0-common libplymouth2
  libpoppler-glib8 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqtcore4 libqtgui4 libquadmath0 libstdc++6 libunity-2d-private0
  libunity-core-6.0-5 libxrandr2 libxvmc1 lightdm linux-firmware
  network-manager ntfs-3g nux-tools plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text poppler-utils
  python-apport python-problem-report python-pycurl python3-apport
  python3-problem-report qdbus software-center ubuntu-desktop ubuntu-minimal
  ubuntu-standard ufw unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-common unity-greeter unity-services
  x11-apps xinput xserver-common xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xterm xul-ext-ubufox
127 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 74.9 MB of archives.
After this operation, 5,574 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
```

I think I'll get both a gnome classic (no effects) session and an Lubuntu core session booting with 'lightdm-gtk-greeter' ............. then I'll try updating again and see what blows up :D

---

### Post by kansasnoob on 2012-08-17
BTW I'm mostly concerned about the ongoing viability of Metacity going forward. Not a big deal because Openbox works just fine ......... just a curiosity thing :)

---

### Post by kansasnoob on 2012-08-17
Still no good :(

I'm going to concentrate on 12.04.1 testing now:

[http://iso.qa.ubuntu.com/qatracker/milestones/230/builds](http://iso.qa.ubuntu.com/qatracker/milestones/230/builds)

Once that's out of the way it'll be interesting to see what happens with a fresh Lubuntu Quantal install :)

---

### Post by kansasnoob on 2012-08-28
Lubuntu is also a no-go with VIA graphics:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625)

I'd hope we're not dropping support altogether for these graphics chips because this is the box I use the most for testing ubiquity and d-i :(

I can see Ubuntu dropping it but I'd hope Lubuntu and Xubuntu will still be able to support it.

---

