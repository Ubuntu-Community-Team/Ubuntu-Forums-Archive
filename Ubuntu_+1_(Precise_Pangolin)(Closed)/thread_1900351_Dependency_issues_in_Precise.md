---
title: "Dependency issues in Precise"
date: 2011-12-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rv65 on 2011-12-26
```
Setting up dictionaries-common (1.12.0ubuntu6) ...
install/dictionaries-common: Byte-compiling for emacsen flavour xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
emacs-package-install: /usr/lib/emacsen-common/packages/install/dictionaries-common xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of aspell:
 aspell depends on dictionaries-common (>> 0.40); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell (--configure):
 dependency problems - leaving unconfigured
Setting up emacsen-common (1.4.22ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          emacsen-common: Handling install of emacsen flavor emacs
emacsen-common: Handling install of emacsen flavor xemacs21
emacsen-common: byte-compiling for xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Error while loading 00debian: Symbol's function definition is void: loop
Loading 00debian-vars...
Loading 50dictionaries-common...
Error while loading 50dictionaries-common: No /usr/local/ prefixed paths in load-path
Loading 50emacs-goodies-el...
Package emacs-goodies-el not fully installed.  Skipping setup.
Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
emacs-package-install: /usr/lib/emacsen-common/packages/install/emacsen-common xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing emacsen-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of emacs23-common:
 emacs23-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.
dpkg: error processing emacs23-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs23-bin-common:
 emacs23-bin-common depends on emacs23-common (= 23.3+1-1ubuntu7); however:
  Package emacs23-common is not configured yet.
dpkg: error processing emacs23-bin-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs23:
 emacs23 depends on emacs23-bin-common (= 23.3+1-1ubuntu7); however:
  Package emacs23-bin-common is not configured yet.
dpkg: error processing emacs23 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21-support:
 xemacs21-support depends on emacsen-common; however:
  Package emacsen-common is not configureNo apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               d yet.
dpkg: error processing xemacs21-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21-bin:
 xemacs21-bin depends on xemacs21-support (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-support is not configured yet.
dpkg: error processing xemacs21-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21-mule:
 xemacs21-mule depends on xemacs21-support (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-support is not configured yet.
 xemacs21-mule depends on xemacs21-bin (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-bin is not configured yet.
 xemacs21-mule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-mule (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21:
 xemacs21 depends on xemacs21-mule (>= 21.4.22-3.No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             2ubuntu1) | xemacs21-mule-canna-wnn (>= 21.4.22-3.2ubuntu1) | xemacs21-nomule (>= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-mule is not configured yet.
  Package xemacs21-mule-canna-wnn is not installed.
  Package xemacs21-nomule is not installed.
dpkg: error processing xemacs21 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs-goodies-el:
 emacs-goodies-el depends on emacs23 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacsen is not installed.
  Package xemacs21-mule which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not configured yet.
dpkg: error processing emacs-goodies-el (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hunspell-en-us:
 hunspell-en-us depends on dictionaries-common (>= 0.10); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing hunspell-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-au:
 myspell-en-au depends on dictionaries-common (>= 1.0); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing myspell-en-au (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythes-en-au:
 mythes-en-au depends on dictionaries-common (>= 0.10); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing mythes-en-au (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-hyphenation-en-us:
 openoffice.org-hyphenation-en-us depends on hyphen-en-us; however:
  Package hyphen-en-us is not configured yet.
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wbritish:
 wbritish depends on dictionaries-common (>= 0.20); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing wbritish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xemacs21-gnome-mule:
 xemacs21-gnome-mule depends on xemacs21-mule; however:
  Package xemacs21-mule is not configured yet.
dpkg: error processing xemacs21-gnome-mule (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dictionaries-common
 aspell
 emacsen-common
 emacs23-common
 emacs23-bin-common
 emacs23
 xemacs21-support
 xemacs21-bin
 xemacs21-mule
 xemacs21
 emacs-goodies-el
 hunspell-en-us
 hyphen-en-us
 myspell-en-au
 mythes-en-au
 openoffice.org-hyphenation-en-us
 wbritish
 xemacs21-gnome-mule

Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

These are the errors I get in Ubuntu 12.04 (Precise Pangolin). I do not know why I get dependency errors like this. Any help would be great.

---

### Post by Harry33 on 2011-12-26
Dictionaries-common can be installed separately, without aspell and emacsen packages. The latter are only suggested packages, not compulsory ones.

So, first, only try to install the package dictionaries-common.
And, use synaptic to install the packages.

---

### Post by rv65 on 2011-12-29
I have Abiword, so I need those packages.

---

### Post by teh603 on 2011-12-29
Well, this is an early Alpha so expect a lot of packages breaking until April. That's the one drawback to running the development branch, is that the package manager is borked as often as it works.

---

### Post by rv65 on 2012-01-05
I agree with you on that. Surprisingly it is able to update no problem, except for the dependency issues. I am sure they will be fixed soon.

---

### Post by rv65 on 2012-02-06
```
E: dictionaries-common: subprocess installed post-installation script returned error exit status 255
E: aspell: dependency problems - leaving unconfigured
E: emacsen-common: subprocess installed post-installation script returned error exit status 255
E: emacs23-common: dependency problems - leaving unconfigured
E: emacs23-bin-common: dependency problems - leaving unconfigured
E: emacs23: dependency problems - leaving unconfigured
E: xemacs21-mule: dependency problems - leaving unconfigured
E: xemacs21-mule-canna-wnn: dependency problems - leaving unconfigured
E: xemacs21: dependency problems - leaving unconfigured
E: xemacs21-support: dependency problems - leaving unconfigured
E: xemacs21-bin: dependency problems - leaving unconfigured
E: emacs: dependency problems - leaving unconfigured
E: emacs-goodies-el: dependency problems - leaving unconfigured
E: hunspell-en-us: dependency problems - leaving unconfigured
E: hyphen-en-us: dependency problems - leaving unconfigured
E: myspell-en-au: dependency problems - leaving unconfigured
E: mythes-en-au: dependency problems - leaving unconfigured
E: openoffice.org-hyphenation-en-us: dependency problems - leaving unconfigured
E: wbritish: dependency problems - leaving unconfigured
E: xemacs21-gnome-mule: dependency problems - leaving unconfigured

```

This is what I now have. Stupid dependency issues. I want to fix them, but there seems to be no end in sight. I have the 64 bit version.

---

### Post by dino99 on 2012-02-06
if you have some ppa activated, then deactivate them and update the repo. Check you are using the genuine package(s), if not, force the genuine package(s).
if you still have the issue, then into synaptic: purge then reinstall the broken package(s).

---

### Post by rv65 on 2012-02-06
How do I purge in synaptic.

---

### Post by rv65 on 2012-02-06
Maybe I am not willing to uninstall my entire system just to remove those files.

---

### Post by Harry33 on 2012-02-06
> **rv65 said:**
> How do I purge in synaptic.

With mouse cursor on the target package, right-click on mouse, and choose
"Mark for complete removal".
Then press "Apply" button.

---

### Post by rv65 on 2012-02-07
I have tried to do that, but some of the packages are so interconnected with the system, that I lose a lot of my packages. I think I should just re install precise.

---

### Post by rv65 on 2012-02-07
Tried to purge emacs and xemacs and I get package errors, so now I can not even reinstall it. I think there is a serious bug in those packages that I have mentioned before.

---

### Post by rv65 on 2012-02-10
I did an update and it said that dictionaries-common failed to install or upgrade and so did emacs-common-en.

---

### Post by rv65 on 2012-02-13
```
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75, <> line 87.)

```

This is a new error which could cause the dependency issues.

---

### Post by cariboo on 2012-02-13
> **rv65 said:**
> ```
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75, <> line 87.)

```

This is a new error which could cause the dependency issues.

Install dialog.

---

### Post by rv65 on 2012-02-14
```
Preparing to replace libssl1.0.0:i386 1.0.0e-3ubuntu1 (using .../libssl1.0.0_1.0.0g-1ubuntu1_i386.deb) ...
Unpacking replacement libssl1.0.0:i386 ...
Setting up libssl1.0.0 (1.0.0g-1ubuntu1) ...
Setting up libssl1.0.0:i386 (1.0.0g-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 718509 files and directories currently installed.)
Preparing to replace libgphoto2-l10n 2.4.11-4ubuntu1 (using .../libgphoto2-l10n_2.4.11-4ubuntu2_all.deb) ...
Unpacking replacement libgphoto2-l10n ...
Preparing to replace libgphoto2-port0 2.4.11-4ubuntu1 (using .../libgphoto2-port0_2.4.11-4ubuntu2_amd64.deb) ...
De-configuring libgphoto2-port0:i386 ...
Unpacking replacement libgphoto2-port0 ...
Preparing to replace libgphoto2-port0:i386 2.4.11-4ubuntu1 (using .../libgphoto2-port0_2.4.11-4ubuntu2_i386.deb) ...
Unpacking replacement libgphoto2-port0:i386 ...
Setting up libgphoto2-port0 (2.4.11-4ubuntu2) ...
Setting up libgphoto2-port0:i386 (2.4.11-4ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 718509 files and directories currently installed.)
Preparing to replace libgphoto2-2:i386 2.4.11-4ubuntu1 (using .../libgphoto2-2_2.4.11-4ubuntu2_i386.deb) ...
De-configuring libgphoto2-2 ...
Unpacking replacement libgphoto2-2:i386 ...
Preparing to replace libgphoto2-2 2.4.11-4ubuntu1 (using .../libgphoto2-2_2.4.11-4ubuntu2_amd64.deb) ...
Unpacking replacement libgphoto2-2 ...
Setting up libgphoto2-2:i386 (2.4.11-4ubuntu2) ...
Setting up libgphoto2-2 (2.4.11-4ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 718509 files and directories currently installed.)
Preparing to replace lightdm 1.1.2-0ubuntu2 (using .../lightdm_1.1.2-0ubuntu3_amd64.deb) ...
Unpacking replacement lightdm ...
Preparing to replace midori 0.4.3-1 (using .../midori_0.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement midori ...
Preparing to replace tmux 1.6-1 (using .../tmux_1.6-1ubuntu1_amd64.deb) ...
Unpacking replacement tmux ...
Preparing to replace ttf-lyx 2.0.2-1ubuntu1 (using .../ttf-lyx_2.0.2-1ubuntu2_all.deb) ...
Unpacking replacement ttf-lyx ...
Preparing to replace ttf-mscorefonts-installer 3.4ubuntu1 (using .../ttf-mscorefonts-installer_3.4ubuntu2_all.deb) ...
mscorefonts-eula license has already been accepted
Unpacking replacement ttf-mscorefonts-installer ...
Preparing to replace netbase 4.46ubuntu1 (using .../netbase_4.47ubuntu1_all.deb) ...
Unpacking replacement netbase ...
Preparing to replace accountsservice 0.6.15-2ubuntu4 (using .../accountsservice_0.6.15-2ubuntu6_amd64.deb) ...
Unpacking replacement accountsservice ...
Preparing to replace libaccountsservice0 0.6.15-2ubuntu4 (using .../libaccountsservice0_0.6.15-2ubuntu6_amd64.deb) ...
Unpacking replacement libaccountsservice0 ...
Preparing to replace openssl 1.0.0e-3ubuntu1 (using .../openssl_1.0.0g-1ubuntu1_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace abiword-plugin-grammar 2.9.2+svn20120123-1 (using .../abiword-plugin-grammar_2.9.2+svn20120123-1build1_amd64.deb) ...
Unpacking replacement abiword-plugin-grammar ...
Preparing to replace abiword-plugin-mathview 2.9.2+svn20120123-1 (using .../abiword-plugin-mathview_2.9.2+svn20120123-1build1_amd64.deb) ...
Unpacking replacement abiword-plugin-mathview ...
Preparing to replace abiword-common 2.9.2+svn20120123-1 (using .../abiword-common_2.9.2+svn20120123-1build1_all.deb) ...
Unpacking replacement abiword-common ...
Preparing to replace abiword 2.9.2+svn20120123-1 (using .../abiword_2.9.2+svn20120123-1build1_amd64.deb) ...
Unpacking replacement abiword ...
Preparing to replace compiz-plugins-main 1:0.9.6-0ubuntu4.2 (using .../compiz-plugins-main_1%3a0.9.7.0~bzr19-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins-main ...
Preparing to replace compiz-plugins 1:0.9.6+bzr20110929-0ubuntu8 (using .../compiz-plugins_1%3a0.9.7.0~bzr2995-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins ...
Preparing to replace unity 5.2.0-0ubuntu3 (using .../unity_5.2.0-0ubuntu4_amd64.deb) ...
Unpacking replacement unity ...
Preparing to replace compiz-gnome 1:0.9.6+bzr20110929-0ubuntu8 (using .../compiz-gnome_1%3a0.9.7.0~bzr2995-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-gnome ...
Preparing to replace compiz-plugins-default 1:0.9.6+bzr20110929-0ubuntu8 (using .../compiz-plugins-default_1%3a0.9.7.0~bzr2995-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins-default ...
Preparing to replace compiz-plugins-main-default 1:0.9.6-0ubuntu4.2 (using .../compiz-plugins-main-default_1%3a0.9.7.0~bzr19-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins-main-default ...
Preparing to replace compiz-core 1:0.9.6+bzr20110929-0ubuntu8 (using .../compiz-core_1%3a0.9.7.0~bzr2995-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-core ...
Preparing to replace libcompizconfig0 0.9.5.94-0ubuntu2 (using .../libcompizconfig0_0.9.7.0~bzr428-0ubuntu1_amd64.deb) ...
Unpacking replacement libcompizconfig0 ...
Preparing to replace libdecoration0 1:0.9.6+bzr20110929-0ubuntu8 (using .../libdecoration0_1%3a0.9.7.0~bzr2995-0ubuntu1_amd64.deb) ...
Unpacking replacement libdecoration0 ...
Preparing to replace libunity-core-5.0-5 5.2.0-0ubuntu3 (using .../libunity-core-5.0-5_5.2.0-0ubuntu4_amd64.deb) ...
Unpacking replacement libunity-core-5.0-5 ...
Preparing to replace unity-services 5.2.0-0ubuntu3 (using .../unity-services_5.2.0-0ubuntu4_amd64.deb) ...
Unpacking replacement unity-services ...
Preparing to replace unity-common 5.2.0-0ubuntu3 (using .../unity-common_5.2.0-0ubuntu4_all.deb) ...
Unpacking replacement unity-common ...
Preparing to replace compiz 1:0.9.6+bzr20110929-0ubuntu8 (using .../compiz_1%3a0.9.7.0~bzr2995-0ubuntu1_all.deb) ...
Unpacking replacement compiz ...
Preparing to replace fontconfig 2.8.0-3ubuntu4 (using .../fontconfig_2.8.0-3ubuntu5_amd64.deb) ...
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lyx /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/msttcorefonts
Unpacking replacement fontconfig ...
Preparing to replace gir1.2-accountsservice-1.0 0.6.15-2ubuntu4 (using .../gir1.2-accountsservice-1.0_0.6.15-2ubuntu6_amd64.deb) ...
Unpacking replacement gir1.2-accountsservice-1.0 ...
Preparing to replace gnome-control-center-data 1:3.2.2-2ubuntu7 (using .../gnome-control-center-data_1%3a3.2.2-2ubuntu8_all.deb) ...
Unpacking replacement gnome-control-center-data ...
Preparing to replace gnome-settings-daemon 3.2.2-0ubuntu15 (using .../gnome-settings-daemon_3.2.2-0ubuntu16_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace gnome-control-center 1:3.2.2-2ubuntu7 (using .../gnome-control-center_1%3a3.2.2-2ubuntu8_amd64.deb) ...
Unpacking replacement gnome-control-center ...
Preparing to replace libgnome-control-center1 1:3.2.2-2ubuntu7 (using .../libgnome-control-center1_1%3a3.2.2-2ubuntu8_amd64.deb) ...
Unpacking replacement libgnome-control-center1 ...
Preparing to replace gnome-panel-control 3.5.0-2ubuntu1 (using .../gnome-panel-control_3.5.0-2ubuntu2_amd64.deb) ...
Unpacking replacement gnome-panel-control ...
Preparing to replace gstreamer0.10-nice 0.1.1-1ubuntu1 (using .../gstreamer0.10-nice_0.1.1-1ubuntu2_amd64.deb) ...
Unpacking replacement gstreamer0.10-nice ...
Preparing to replace gwibber-service-facebook 3.3.3-0ubuntu1 (using .../gwibber-service-facebook_3.3.3-0ubuntu2_all.deb) ...
Unpacking replacement gwibber-service-facebook ...
Preparing to replace gwibber-service-identica 3.3.3-0ubuntu1 (using .../gwibber-service-identica_3.3.3-0ubuntu2_all.deb) ...
Unpacking replacement gwibber-service-identica ...
Preparing to replace gwibber-service-twitter 3.3.3-0ubuntu1 (using .../gwibber-service-twitter_3.3.3-0ubuntu2_all.deb) ...
Unpacking replacement gwibber-service-twitter ...
Preparing to replace libept1.4.12 1.0.6~exp1 (using .../libept1.4.12_1.0.6~exp1ubuntu1_amd64.deb) ...
Unpacking replacement libept1.4.12 ...
Preparing to replace liblightdm-gobject-1-0 1.1.2-0ubuntu2 (using .../liblightdm-gobject-1-0_1.1.2-0ubuntu3_amd64.deb) ...
Unpacking replacement liblightdm-gobject-1-0 ...
Preparing to replace libqapt1 1.2.95-0ubuntu1 (using .../libqapt1_1.2.95-0ubuntu3_amd64.deb) ...
Unpacking replacement libqapt1 ...
Preparing to replace libqapt-runtime 1.2.95-0ubuntu1 (using .../libqapt-runtime_1.2.95-0ubuntu3_amd64.deb) ...
Unpacking replacement libqapt-runtime ...
Preparing to replace libservlet2.5-java 6.0.35-1 (using .../libservlet2.5-java_6.0.35-1ubuntu1_all.deb) ...
Unpacking replacement libservlet2.5-java ...
Preparing to replace linux-firmware 1.68 (using .../linux-firmware_1.69_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace python-debtagshw 1.8.0+git20120126ubuntu3 (using .../python-debtagshw_1.8.0+git20120213ubuntu1_all.deb) ...
Unpacking replacement python-debtagshw ...
Preparing to replace qapt-batch 1.2.95-0ubuntu1 (using .../qapt-batch_1.2.95-0ubuntu3_amd64.deb) ...
Unpacking replacement qapt-batch ...
Preparing to replace ubuntu-artwork 54 (using .../ubuntu-artwork_55_all.deb) ...
Unpacking replacement ubuntu-artwork ...
Preparing to replace xserver-xorg-input-evdev 1:2.6.99.901-1ubuntu3 (using .../xserver-xorg-input-evdev_1%3a2.6.99.901+git20120126-0ubuntu2_amd64.deb) ...
Unpacking replacement xserver-xorg-input-evdev ...
Preparing to replace xvidenc 8.4.2~dfsg-0ubuntu1 (using .../xvidenc_8.4.3~dfsg-0ubuntu1_all.deb) ...
Unpacking replacement xvidenc ...
Preparing to replace compiz-fusion-plugins-main 1:0.9.6-0ubuntu4.2 (using .../compiz-fusion-plugins-main_1%3a0.9.7.0~bzr19-0ubuntu1_all.deb) ...
Unpacking replacement compiz-fusion-plugins-main ...
Preparing to replace python-farsight 0.0.31-1ubuntu2 (using .../python-farsight_0.0.31-1ubuntu3_amd64.deb) ...
Unpacking replacement python-farsight ...
Preparing to replace python-packagekit 0.7.2-2ubuntu1 (using .../python-packagekit_0.7.2-2ubuntu2_all.deb) ...
Unpacking replacement python-packagekit ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Setting up dictionaries-common (1.12.1ubuntu2) ...
install/dictionaries-common: Byte-compiling for emacsen flavour xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
emacs-package-install: /usr/lib/emacsen-common/packages/install/dictionaries-common xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of aspell:
 aspell depends on dictionaries-common (>> 0.40); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up emacsen-common (1.4.22ubuntu1) ...
emacsen-common: Handling install of emacsen flavor emacs
emacsen-common: Handling install of emacsen flavor xemacs21
emacsen-common: byte-compiling for xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Error while loading 00debian: Symbol's function definition is void: loop
Loading 00debian-vars...
Loading 50dictionaries-common...
Error while loading 50dictionaries-common: No /usr/local/ prefixed paths in load-path
Loading 50emacs-goodies-el...
Package emacs-goodies-el not fully installed.  Skipping setup.
Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
emacs-package-install: /usr/lib/emacsen-common/packages/install/emacsen-common xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing emacsen-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of emacs23-common:
 emacs23-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.
dpkg: error processing emacs23-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs23-bin-common:
 emacs23-bin-common depends on emacs23-common (= 23.3+1-1ubuntu7); however:
  Package emacs23-common is not configured yet.
dpkg: error processing emacs23-bin-common (--configure):
 dependency problems - leaving unconfigured
Setting up lib32asound2 (1.0.25-1ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of emacs23-lucid:
 emacs23-lucid depends on emacs23-bin-common (= 23.3+1-1ubuntu7); however:
  Package emacs23-bin-common is not configured yet.
dpkg: error processing emacs23-lucid (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs23 | emacs23-lucid | emacs23-nox; however:
  Package emacs23 is not installed.
  Package emacs23-lucid which provides emacs23 is not configured yet.
  Package emacs23-lucid is not configured yet.
  Package emacs23-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-mule-canna-wnn:
 xemacs21-mule-canna-wnn depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-mule-canna-wnn (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-nomule:
 xemacs21-nomule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-nomule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-support:
 xemacs21-support depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-mule:
 xemacs21-mule depends on xemacs21-support (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-support is not configured yet.
 xemacs21-mule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-mule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs-goodies-el:
 emacs-goodies-el depends on emacs23 | emacsen; however:
  Package emacs23 is not installed.
  Package emacs23-lucid which provides emacs23 is not configured yet.
  Package emacsen is not installed.
  Package xemacs21-mule which provides emacsen is not configured yet.
  Package emacs which provides emacsen is not configured yet.
  Package emacs23-lucid which provides emacsen is not configured yet.
  Package xemacs21-mule-canna-wnn which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not installed.
  Package xemacs21-nomule which provides emacsen is not configured yet.
dpkg: error processing emacs-goodies-el (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hunspell-en-us:
 hunspell-en-us depends on dictionaries-common (>= 0.10); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing hunspell-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of myspell-en-au:
 myspell-en-au depends on dictionaries-common (>= 1.0); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing myspell-en-au (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-hyphenation-en-us:
 openoffice.org-hyphenation-en-us depends on hyphen-en-us; however:
No apport report written because MaxReports is reached already
                                                                Package hyphen-en-us is not configured yet.
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wbritish:
 wbritish depends on dictionaries-common (>= 0.20); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing wbritish (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-gnome-mule:
 xemacs21-gnome-mule depends on xemacs21-mule; however:
  Package xemacs21-mule is not configured yet.
dpkg: error processing xemacs21-gnome-mule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up libgphoto2-l10n (2.4.11-4ubuntu2) ...
Setting up lightdm (1.1.2-0ubuntu3) ...
Setting up midori (0.4.3-1ubuntu1) ...
rmdir: failed to remove `/etc/xdg/midori/extensions/libadblock.so': No such file or directory
Setting up tmux (1.6-1ubuntu1) ...
Setting up ttf-lyx (2.0.2-1ubuntu2) ...
Setting up ttf-mscorefonts-installer (3.4ubuntu2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

All fonts downloaded and installed.
Setting up netbase (4.47ubuntu1) ...
Installing new version of config file /etc/services ...
Setting up libaccountsservice0 (0.6.15-2ubuntu6) ...
Setting up accountsservice (0.6.15-2ubuntu6) ...
Setting up openssl (1.0.0g-1ubuntu1) ...
Installing new version of config file /etc/ssl/openssl.cnf ...
Setting up abiword-common (2.9.2+svn20120123-1build1) ...
Setting up abiword (2.9.2+svn20120123-1build1) ...
Setting up abiword-plugin-grammar (2.9.2+svn20120123-1build1) ...
Setting up abiword-plugin-mathview (2.9.2+svn20120123-1build1) ...
Setting up compiz-core (1:0.9.7.0~bzr2995-0ubuntu1) ...
Setting up compiz-plugins-main-default (1:0.9.7.0~bzr19-0ubuntu1) ...
Setting up compiz-plugins-main (1:0.9.7.0~bzr19-0ubuntu1) ...
Setting up libdecoration0 (1:0.9.7.0~bzr2995-0ubuntu1) ...
Setting up compiz-plugins-default (1:0.9.7.0~bzr2995-0ubuntu1) ...
Setting up compiz-plugins (1:0.9.7.0~bzr2995-0ubuntu1) ...
Setting up unity-services (5.2.0-0ubuntu4) ...
Setting up libunity-core-5.0-5 (5.2.0-0ubuntu4) ...
Setting up unity-common (5.2.0-0ubuntu4) ...
Setting up compiz-gnome (1:0.9.7.0~bzr2995-0ubuntu1) ...
Installing new version of config file /etc/compizconfig/unity.ini ...
Setting up libcompizconfig0 (0.9.7.0~bzr428-0ubuntu1) ...
Setting up compiz (1:0.9.7.0~bzr2995-0ubuntu1) ...
Setting up unity (5.2.0-0ubuntu4) ...
Setting up fontconfig (2.8.0-3ubuntu5) ...
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lyx /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/msttcorefonts
Regenerating fonts cache... done.
Setting up gir1.2-accountsservice-1.0 (0.6.15-2ubuntu6) ...
Setting up gnome-control-center-data (1:3.2.2-2ubuntu8) ...
Setting up gnome-settings-daemon (3.2.2-0ubuntu16) ...
Setting up libgnome-control-center1 (1:3.2.2-2ubuntu8) ...
Setting up gnome-control-center (1:3.2.2-2ubuntu8) ...
Setting up gnome-panel-control (3.5.0-2ubuntu2) ...
Setting up gstreamer0.10-nice (0.1.1-1ubuntu2) ...
Setting up gwibber-service-facebook (3.3.3-0ubuntu2) ...
Setting up gwibber-service-identica (3.3.3-0ubuntu2) ...
Setting up gwibber-service-twitter (3.3.3-0ubuntu2) ...
Setting up libept1.4.12 (1.0.6~exp1ubuntu1) ...
Setting up liblightdm-gobject-1-0 (1.1.2-0ubuntu3) ...
Setting up libqapt1 (1.2.95-0ubuntu3) ...
Setting up libqapt-runtime (1.2.95-0ubuntu3) ...
Setting up libservlet2.5-java (6.0.35-1ubuntu1) ...
Setting up linux-firmware (1.69) ...
Setting up python-debtagshw (1.8.0+git20120213ubuntu1) ...
Setting up qapt-batch (1.2.95-0ubuntu3) ...
Setting up ubuntu-artwork (55) ...
Setting up xserver-xorg-input-evdev (1:2.6.99.901+git20120126-0ubuntu2) ...
Setting up xvidenc (8.4.3~dfsg-0ubuntu1) ...
Setting up compiz-fusion-plugins-main (1:0.9.7.0~bzr19-0ubuntu1) ...
Setting up python-farsight (0.0.31-1ubuntu3) ...
Setting up python-packagekit (0.7.2-2ubuntu2) ...
dpkg: dependency problems prevent configuration of xemacs21-bin:
 xemacs21-bin depends on xemacs21-support (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-support is not configured yet.
dpkg: error processing xemacs21-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21:
 xemacs21 depends on xemacs21-mule (>= 21.4.22-3.2ubuntu1) | xemacs21-mule-canna-wnn (>= 21.4.22-3.2ubuntu1) | xemacs21-nomule (>= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-mule is not configured yet.
  Package xemacs21-mule-canna-wnn is not configured yet.
  Package xemacs21-nomule is not configured yet.
dpkg: error processing xemacs21 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 dictionaries-common
 aspell
 emacsen-common
 emacs23-common
 emacs23-bin-common
 emacs23-lucid
 emacs
 xemacs21-mule-canna-wnn
 xemacs21-nomule
 xemacs21-support
 xemacs21-mule
 emacs-goodies-el
 hunspell-en-us
 hyphen-en-us
 myspell-en-au
 openoffice.org-hyphenation-en-us
 wbritish
 xemacs21-gnome-mule
 xemacs21-bin
 xemacs21
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What I could salvage during the update log.

---

### Post by rv65 on 2012-02-24
Nobody seems to be interested in this bug :(. I updated the desktop not longer after Alpha 1 so thats why. My Laptop which I updated later does not have this bug. I cannot even install XeMacs. I think dictionaries-common has to be updated to fix it. Purging this will effectively purge the system.

---

### Post by effenberg0x0 on 2012-02-24
> **rv65 said:**
> I cannot even install XeMacs.
Then we should assume something is broken in your system. A default installation of PP allows me to install Xemacs, as you can see below:

> 
[01:06 AM][ahsl:AL-DESK:~]
$ sudo apt-get install xemacs21
[sudo] password for ahsl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-gobject-dev python-gi-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcompfaceg1 xemacs21-basesupport xemacs21-bin xemacs21-mule xemacs21-mulesupport
  xemacs21-support
Suggested packages:
  xemacs21-supportel
The following NEW packages will be installed:
  libcompfaceg1 xemacs21 xemacs21-basesupport xemacs21-bin xemacs21-mule
  xemacs21-mulesupport xemacs21-support
0 upgraded, 7 newly installed, 0 to remove and 4 not upgraded.
Need to get 35.0 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe libcompfaceg1 amd64 1:1.5.2-5 [14.9 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe xemacs21-support all 21.4.22-3.2ubuntu1 [4,514 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe xemacs21-bin amd64 21.4.22-3.2ubuntu1 [524 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe xemacs21-mulesupport all 2009.02.17.dfsg.1-1 [4,471 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe xemacs21-basesupport all 2009.02.17.dfsg.1-1 [23.2 MB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe xemacs21-mule amd64 21.4.22-3.2ubuntu1 [2,266 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe xemacs21 all 21.4.22-3.2ubuntu1 [5,058 B]
Fetched 35.0 MB in 25s (1,389 kB/s)                                                   
Selecting previously unselected package libcompfaceg1.
(Reading database ... 396158 files and directories currently installed.)
Unpacking libcompfaceg1 (from .../libcompfaceg1_1%3a1.5.2-5_amd64.deb) ...
Selecting previously unselected package xemacs21-support.
Unpacking xemacs21-support (from .../xemacs21-support_21.4.22-3.2ubuntu1_all.deb) ...
Selecting previously unselected package xemacs21-bin.
Unpacking xemacs21-bin (from .../xemacs21-bin_21.4.22-3.2ubuntu1_amd64.deb) ...
Selecting previously unselected package xemacs21-mulesupport.
Unpacking xemacs21-mulesupport (from .../xemacs21-mulesupport_2009.02.17.dfsg.1-1_all.deb) ...
Selecting previously unselected package xemacs21-basesupport.
Unpacking xemacs21-basesupport (from .../xemacs21-basesupport_2009.02.17.dfsg.1-1_all.deb) ...
Selecting previously unselected package xemacs21-mule.
Unpacking xemacs21-mule (from .../xemacs21-mule_21.4.22-3.2ubuntu1_amd64.deb) ...
Selecting previously unselected package xemacs21.
Unpacking xemacs21 (from .../xemacs21_21.4.22-3.2ubuntu1_all.deb) ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/xemacs21/emodules.info.gz'
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up libcompfaceg1 (1:1.5.2-5) ...
Setting up xemacs21-mulesupport (2009.02.17.dfsg.1-1) ...
Setting up xemacs21-basesupport (2009.02.17.dfsg.1-1) ...
Setting up xemacs21-support (21.4.22-3.2ubuntu1) ...
Ignoring install-info called from maintainer script
The package xemacs21-support should be rebuilt with new debhelper to get trigger support
Setting up xemacs21-bin (21.4.22-3.2ubuntu1) ...
update-alternatives: using /usr/lib/xemacs-21.4.22/x86_64-linux-gnu/movemail to provide /usr/bin/movemail (movemail) in auto mode.
update-alternatives: using /usr/lib/xemacs-21.4.22/x86_64-linux-gnu/mmencode to provide /usr/bin/mmencode (mmencode) in auto mode.
update-alternatives: using /usr/bin/b2m.xemacs21 to provide /usr/bin/b2m (b2m) in auto mode.
update-alternatives: using /usr/bin/etags.xemacs21 to provide /usr/bin/etags (etags) in auto mode.
update-alternatives: using /usr/bin/gnuclient.xemacs21 to provide /usr/bin/gnuclient (gnuclient) in auto mode.
update-alternatives: using /usr/bin/gnuattach.xemacs21 to provide /usr/bin/gnuattach (gnuattach) in auto mode.
update-alternatives: using /usr/bin/gnudoit.xemacs21 to provide /usr/bin/gnudoit (gnudoit) in auto mode.
update-alternatives: using /usr/bin/rcs-checkin.xemacs21 to provide /usr/bin/rcs-checkin (rcs-checkin) in auto mode.
update-alternatives: using /usr/bin/ellcc.xemacs21 to provide /usr/bin/ellcc (ellcc) in auto mode.
Setting up xemacs21-mule (21.4.22-3.2ubuntu1) ...
update-alternatives: using /usr/bin/xemacs21-mule to provide /usr/bin/xemacs21 (xemacs21) in auto mode.
emacs-install xemacs21
install/a2ps: Handling install for emacsen flavor xemacs21
Compiling /usr/share/xemacs21/site-lisp/a2ps/a2ps-print.el...
Wrote /usr/share/xemacs21/site-lisp/a2ps/a2ps-print.elc
Compiling /usr/share/xemacs21/site-lisp/a2ps/a2ps.el...
Wrote /usr/share/xemacs21/site-lisp/a2ps/a2ps.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour xemacs21
Compiling /usr/share/xemacs21/site-lisp/dictionaries-common/debian-ispell.el...
Wrote /usr/share/xemacs21/site-lisp/dictionaries-common/debian-ispell.elc
Compiling /usr/share/xemacs21/site-lisp/dictionaries-common/ispell.el...
Wrote /usr/share/xemacs21/site-lisp/dictionaries-common/ispell.elc
Compiling /usr/share/xemacs21/site-lisp/dictionaries-common/flyspell.el...
Wrote /usr/share/xemacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor xemacs21
emacsen-common: byte-compiling for xemacs21
Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Loading site-start...
Loading 00debian-vars...
Loading 50a2ps...
Loading 50asymptote...
Loading 50autoconf...
Loading 50cmake-data...
Loading 50devhelp...
Loading 50dictionaries-common...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el...
Compiling /etc/xemacs21/site-start.d/00debian-vars.el...
Wrote /etc/xemacs21/site-start.d/00debian-vars.elc
Compiling /usr/share/xemacs21/site-lisp/debian-startup.el...
Wrote /usr/share/xemacs21/site-lisp/debian-startup.elc
Done
install/cmake-data: Byte-compiling for xemacs21
Compiling /usr/share/xemacs21/site-lisp/cmake-data/cmake-mode.el...
Wrote /usr/share/xemacs21/site-lisp/cmake-data/cmake-mode.elc
Done
Setting up xemacs21 (21.4.22-3.2ubuntu1) ...
update-alternatives: using /usr/bin/xemacs21 to provide /usr/bin/xemacs (xemacs) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

[01:10 AM][ahsl:AL-DESK:~]
$ 
Do not say yes or no to any solution proposed by APT. Just hit Ctrl+C, but lets have a look at whats the output of: 
```
sudo apt-get install --reinstall xemacs21
```Regards,
Effenberg

---

### Post by rv65 on 2012-03-01
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 24 not upgraded.
21 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up dictionaries-common (1.12.1ubuntu2) ...
install/dictionaries-common: Byte-compiling for emacsen flavour xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
emacs-package-install: /usr/lib/emacsen-common/packages/install/dictionaries-common xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of aspell:
 aspell depends on dictionaries-common (>> 0.40); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing aspell (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of dictionaries-common-dev:
 dictionaries-common-dev depends on dictionaries-common (>> 0.3.6); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing dictionaries-common-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up emacsen-common (1.4.22ubuntu1) ...
emacsen-common: Handling install of emacsen flavor emacs
emacsen-common: Handling install of emacsen flavor xemacs21
emacsen-common: byte-compiling for xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Error while loading 00debian: Symbol's function definition is void: loop
Loading 00debian-vars...
Loading 50dictionaries-common...
Error while loading 50dictionaries-common: No /usr/local/ prefixed paths in load-path
Loading 50emacs-goodies-el...
Package emacs-goodies-el not fully installed.  Skipping setup.
Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
emacs-package-install: /usr/lib/emacsen-common/packages/install/emacsen-common xemacs21 xemacs21 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing emacsen-common (--configure):
 subprocess installed post-installation script returned error exit status 255
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs23-common:
 emacs23-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.
dpkg: error processing emacs23-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs23-bin-common:
 emacs23-bin-common depends on emacs23-common (= 23.3+1-1ubuntu7); however:
  Package emacs23-common is not configured yet.
dpkg: error processing emacs23-bin-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs23-lucid:
 emacs23-lucid depends on emacs23-bin-common (= 23.3+1-1ubuntu7); however:
  Package emacs23-bin-common is not configured yet.
dpkg: error processing emacs23-lucid (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs23 | emacs23-lucid | emacs23-nox; however:
  Package emacs23 is not installed.
  Package emacs23-lucid which provides emacs23 is not configured yet.
  Package emacs23-lucid is not configured yet.
  Package emacs23-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-mule-canna-wnn:
 xemacs21-mule-canna-wnn depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-mule-canna-wnn (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-nomule:
 xemacs21-nomule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-nomule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-support:
 xemacs21-support depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-mule:
 xemacs21-mule depends on xemacs21-support (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-support is not configured yet.
 xemacs21-mule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
dpkg: error processing xemacs21-mule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs-goodies-el:
 emacs-goodies-el depends on emacs23 | emacsen; however:
  Package emacs23 is not installed.
  Package emacs23-lucid which provides emacs23 is not configured yet.
  Package emacsen is not installed.
  Package xemacs21-mule which provides emacsen is not configured yet.
  Package emacs which provides emacsen is not configured yet.
  Package emacs23-lucid which provides emacsen is not configured yet.
  Package xemacs21-mule-canna-wnn which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not installed.
  Package xemacs21-nomule which provides emacsen is not configured yet.
dpkg: error processing emacs-goodies-el (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hunspell-en-us:
 hunspell-en-us depends on dictionaries-common (>= 0.10); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing hunspell-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of myspell-en-au:
 myspell-en-au depends on dictionaries-common (>= 1.0); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing myspell-en-au (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of wbritish:
 wbritish depends on dictionaries-common (>= 0.20); however:
  Package dictionaries-common is not configured yet.
dpkg: error processing wbritish (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-gnome-mule:
 xemacs21-gnome-mule depends on xemacs21-mule; however:
  Package xemacs21-mule is not configured yet.
dpkg: error processing xemacs21-gnome-mule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of openoffice.org-hyphenation-en-us:
 openoffice.org-hyphenation-en-us depends on hyphen-en-us; however:
  Package hyphen-en-us is not configured yet.
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-bin:
 xemacs21-bin depends on xemacs21-support (= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-support is not configured yet.
dpkg: error processing xemacs21-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21:
 xemacs21 depends on xemacs21-mule (>= 21.4.22-3.2ubuntu1) | xemacs21-mule-canna-wnn (>= 21.4.22-3.2ubuntu1) | xemacs21-nomule (>= 21.4.22-3.2ubuntu1); however:
  Package xemacs21-mule is not configured yet.
  Package xemacs21-mule-canna-wnn is not configured yet.
  Package xemacs21-nomule is not configured yet.
dpkg: error processing xemacs21 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 dictionaries-common
 aspell
 dictionaries-common-dev
 emacsen-common
 emacs23-common
 emacs23-bin-common
 emacs23-lucid
 emacs
 xemacs21-mule-canna-wnn
 xemacs21-nomule
 xemacs21-support
 xemacs21-mule
 emacs-goodies-el
 hunspell-en-us
 hyphen-en-us
 myspell-en-au
 wbritish
 xemacs21-gnome-mule
 openoffice.org-hyphenation-en-us
 xemacs21-bin
 xemacs21
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Did the command you proposed, and I get this.

---

### Post by effenberg0x0 on 2012-03-01
Ok, I think it's a good attempt to dpkg-reconfigure all packages. Although it might take a while, you clearly have unconfigured and partially installed packages. This *should* fix it.

```

sudo apt-get remove xemacs21

```You should see only emacs-related packages being removed. Anything too different from this = Hit NO.
> 
The following packages will be REMOVED:
  xemacs21 xemacs21-bin xemacs21-mule xemacs21-support
```

sudo dpkg-reconfigure -a
sudo aptitude update && sudo aptitude safe-upgrade
sudo apt-get install --reinstall xemacs21

```Regards,
Effenberg

---

### Post by jbicha on 2012-03-01
I don't think running dpkg-reconfigure is a good idea. It should be sufficient to run

```
sudo dpkg --configure -a
```

---

### Post by effenberg0x0 on 2012-03-01
> **jbicha said:**
> I don't think running dpkg-reconfigure is a good idea. It should be sufficient to run

```
sudo dpkg --configure -a
```

Hi JBicha, you're right, I guess I was being too aggressive, dpkg-configure *should* be enough. 

Thanks,
Effenberg

---

### Post by rv65 on 2012-03-02
Nothing is working, I still cannot get the errors removed.

---

### Post by effenberg0x0 on 2012-03-02
Please copy / paste the output of the following commands here:
```

sudo cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/*

```

Regards,
Effenberg

---

### Post by mc4man on 2012-03-02
What does this show? (won't Do anything

```
sudo apt-get -s purge dictionaries-common
```

---

### Post by effenberg0x0 on 2012-03-02
> **mc4man said:**
> What does this show? (won't Do anything

```
sudo apt-get -s purge dictionaries-common
```

Good question. I have no idea how a broken / half-installed package reacts to purge and would like to see it.  Smart of you to use simulate :) I'm betting wrong repos/conflicting PPA will end up being the source of the issue here.

Regards,
Effenberg

---

### Post by rv65 on 2012-03-02
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise main restricted
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates main restricted
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise universe
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise multiverse
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise multiverse
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates multiverse
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security main restricted
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security main restricted
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security universe
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security multiverse
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-proposed restricted main multiverse universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security multiverse
michael@rv65-desktop:~$ sudo cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise main restricted
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates main restricted
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise universe
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise multiverse
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise multiverse
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates multiverse
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security main restricted
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security main restricted
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security universe
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security multiverse
deb http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-proposed restricted main multiverse universe
deb-src http://san.csc.calpoly.edu/ubuntu/ubuntu/ precise-security multiverse

```

Output of Command 1

```
-rw-r--r-- 1 root root 142 Jan  5  2011 /etc/apt/sources.list.d/chromium-daily-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root 136 Jan  9  2011 /etc/apt/sources.list.d/chromium-daily-ppa-maverick.list.save
-rw-r--r-- 1 root root 136 Jul  1  2011 /etc/apt/sources.list.d/chromium-daily-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 136 Jul  1  2011 /etc/apt/sources.list.d/chromium-daily-ppa-natty.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:18 /etc/apt/sources.list.d/chromium-daily-ppa-oneiric.list
-rw-r--r-- 1 root root 140 Dec  1 23:05 /etc/apt/sources.list.d/chromium-daily-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  68 Feb  6 02:18 /etc/apt/sources.list.d/chromium-daily-ppa-oneiric.list.save
-rw-r--r-- 1 root root 176 Feb 13 13:54 /etc/apt/sources.list.d/google-chrome.list
-rw-r--r-- 1 root root 176 Dec  1 23:05 /etc/apt/sources.list.d/google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 Feb 13 13:54 /etc/apt/sources.list.d/google-chrome.list.save
-rw-r--r-- 1 root root 175 Feb 13 13:54 /etc/apt/sources.list.d/google-earth.list
-rw-r--r-- 1 root root 175 Dec  1 23:05 /etc/apt/sources.list.d/google-earth.list.distUpgrade
-rw-r--r-- 1 root root 175 Feb 13 13:54 /etc/apt/sources.list.d/google-earth.list.save
-rw-r--r-- 1 root root 279 Feb 13 13:54 /etc/apt/sources.list.d/medibuntu.list
-rw-r--r-- 1 root root 279 Dec  1 23:05 /etc/apt/sources.list.d/medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 279 Feb 13 13:54 /etc/apt/sources.list.d/medibuntu.list.save
-rw-r--r-- 1 root root 414 Feb 13 13:54 /etc/apt/sources.list.d/opera.list
-rw-r--r-- 1 root root 414 Dec  1 23:05 /etc/apt/sources.list.d/opera.list.distUpgrade
-rw-r--r-- 1 root root 414 Feb 13 13:54 /etc/apt/sources.list.d/opera.list.save
-rw-r--r-- 1 root root   0 Mar  3  2011 /etc/apt/sources.list.d/paul-climbing-ppa-natty.list
-rw-r--r-- 1 root root  68 Mar  3  2011 /etc/apt/sources.list.d/paul-climbing-ppa-natty.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/portis25-test-oneiric.list
-rw-r--r-- 1 root root 130 Dec  1 23:05 /etc/apt/sources.list.d/portis25-test-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  98 Feb  6 02:17 /etc/apt/sources.list.d/portis25-test-oneiric.list.save
-rw-r--r-- 1 root root   0 Nov  9 21:14 /etc/apt/sources.list.d/seamonkey2-seamonkey2-oneiric.list
-rw-r--r-- 1 root root 146 Nov  9 12:58 /etc/apt/sources.list.d/seamonkey2-seamonkey2-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  71 Nov  9 21:14 /etc/apt/sources.list.d/seamonkey2-seamonkey2-oneiric.list.save
-rw-r--r-- 1 root root 130 Jul  1  2011 /etc/apt/sources.list.d/shiki-mediainfo-natty.list.distUpgrade
-rw-r--r-- 1 root root 130 Jul  1  2011 /etc/apt/sources.list.d/shiki-mediainfo-natty.list.save
-rw-r--r-- 1 root root   0 Sep 19 20:26 /etc/apt/sources.list.d/shiki-mediainfo-oneiric.list
-rw-r--r-- 1 root root 100 Sep 19 20:26 /etc/apt/sources.list.d/shiki-mediainfo-oneiric.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/stebbins-handbrake-releases-maverick.list
-rw-r--r-- 1 root root 230 Dec  1 23:05 /etc/apt/sources.list.d/stebbins-handbrake-releases-maverick.list.distUpgrade
-rw-r--r-- 1 root root 113 Feb  6 02:17 /etc/apt/sources.list.d/stebbins-handbrake-releases-maverick.list.save
-rw-r--r-- 1 root root 160 Jul  1  2011 /etc/apt/sources.list.d/stebbins-handbrake-releases-natty.list.distUpgrade
-rw-r--r-- 1 root root 160 Jul  1  2011 /etc/apt/sources.list.d/stebbins-handbrake-releases-natty.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/tobydox-lmms-maverick.list
-rw-r--r-- 1 root root 200 Dec  1 23:05 /etc/apt/sources.list.d/tobydox-lmms-maverick.list.distUpgrade
-rw-r--r-- 1 root root 102 Feb  6 02:17 /etc/apt/sources.list.d/tobydox-lmms-maverick.list.save
-rw-r--r-- 1 root root 126 Jul  1  2011 /etc/apt/sources.list.d/tualatrix-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 126 Jul  1  2011 /etc/apt/sources.list.d/tualatrix-ppa-natty.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list
-rw-r--r-- 1 root root 200 Dec  1 23:05 /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  98 Feb  6 02:17 /etc/apt/sources.list.d/tualatrix-ppa-oneiric.list.save
-rw-r--r-- 1 root root  89 Feb 13 13:54 /etc/apt/sources.list.d/ubuntu-mozilla-daily-firefox-aurora-oneiric.list
-rw-r--r-- 1 root root 174 Dec  1 23:05 /etc/apt/sources.list.d/ubuntu-mozilla-daily-firefox-aurora-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  89 Feb 13 13:54 /etc/apt/sources.list.d/ubuntu-mozilla-daily-firefox-aurora-oneiric.list.save
-rw-r--r-- 1 root root 174 Feb 13 13:54 /etc/apt/sources.list.d/ubuntu-mozilla-daily-firefox-aurora-precise.list
-rw-r--r-- 1 root root 174 Feb 13 13:54 /etc/apt/sources.list.d/ubuntu-mozilla-daily-firefox-aurora-precise.list.save
-rw-r--r-- 1 root root   0 Dec  2 17:25 /etc/apt/sources.list.d/ubuntu-mozilla-daily-thunderbird-aurora-oneiric.list
-rw-r--r-- 1 root root 182 Dec  1 23:05 /etc/apt/sources.list.d/ubuntu-mozilla-daily-thunderbird-aurora-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  89 Dec  2 17:25 /etc/apt/sources.list.d/ubuntu-mozilla-daily-thunderbird-aurora-oneiric.list.save
-rw-r--r-- 1 root root 182 Feb 13 13:54 /etc/apt/sources.list.d/ubuntu-mozilla-daily-thunderbird-aurora-precise.list
-rw-r--r-- 1 root root 182 Feb 13 13:54 /etc/apt/sources.list.d/ubuntu-mozilla-daily-thunderbird-aurora-precise.list.save
-rw-r--r-- 1 root root 154 Jul  1  2011 /etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root 154 Jul  1  2011 /etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-natty.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-oneiric.list
-rw-r--r-- 1 root root 228 Dec  1 23:05 /etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 112 Feb  6 02:17 /etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-oneiric.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root 134 Dec  1 23:05 /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 100 Feb  6 02:17 /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list.save
-rw-r--r-- 1 root root 146 Jul  1  2011 /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-natty.list.distUpgrade
-rw-r--r-- 1 root root 146 Jul  1  2011 /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-natty.list.save
-rw-r--r-- 1 root root 220 Jul 29  2011 /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list
-rw-r--r-- 1 root root 140 Dec  1 23:05 /etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 107 Feb  6 02:17 /etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/webupd8team-y-ppa-manager-oneiric.list
-rw-r--r-- 1 root root 154 Dec  1 23:05 /etc/apt/sources.list.d/webupd8team-y-ppa-manager-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 110 Feb  6 02:17 /etc/apt/sources.list.d/webupd8team-y-ppa-manager-oneiric.list.save
-rw-r--r-- 1 root root   0 Dec  2 00:20 /etc/apt/sources.list.d/xorg-edgers-ppa-oneiric.list
-rw-r--r-- 1 root root 138 Dec  1 23:05 /etc/apt/sources.list.d/xorg-edgers-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root  67 Dec  2 00:20 /etc/apt/sources.list.d/xorg-edgers-ppa-oneiric.list.save
-rw-r--r-- 1 root root   0 Feb  6 02:17 /etc/apt/sources.list.d/xorg-edgers-ppa-precise.list
-rw-r--r-- 1 root root  67 Feb  6 02:17 /etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.save

```

Did those two commands and this is what I get.

---

### Post by effenberg0x0 on 2012-03-02
Thanks. We can see you have added many alternative sources (PPAs, those inside /etc/apt/sources.list.d/). These alternative sources offer their own software and versions of packages. They may or may not be compatible to Ubuntu official sources packages and, sometimes, there's conflict. This is my bet for what you're facing there. But I may be wrong. 

To check it: Ideally, you would have to go through each of these PPAs to see what packages they provide, and see if these packages conflict with the official repos packages. 

It would be slow and painful. I'm not gonna have you do this. Give me 10 minutes, I'll think of something to auto-test it...

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-03-02
Hey, 
I haven't piped it, but you can play with it separately, and improve it, which is better.

So, this are the PPA_NAMES you have in your PPAs, so you dont have to ls -> cat -> translate -> tee them to some file or save hem to an array. This is stdout, you choose what to do.
```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|precise||g' | sed -e 's|lucid||g' | sed -e 's|main||' | sed -e 's|^ppa||g' | sed -e 's|#||g' | sed -e 's| ||g' | awk 'BEGIN {FS="/"} {print $1}'; done

```Then you can look at your apt for info regarding the packages from each of those PPAs:
```
grep '^Package' /var/lib/apt/lists/ppa.launchpad.net_${PPA_NAME}*Package); done
```And finally, you need to check two informations with dpkg-query:
1) Is the package still installed?
2) What are it's conflicts?

```
dpkg-query -W -f='Package ${Package} status is ${Status}. Conflicts: ${Conflicts}\n' <EachPackageNameYouGotFromPreviousCommand>
```Notice that this is just to avoid simply ppa-purging all your PPAs, which would be too brutal.

Regards,
Effenberg

I forgot to suggest you one more thing: Maybe you can easily find out whats wrong by checking which packages are not reported as "Installed OK" by dpkg. They can be broken, Half-Installed, etc. You could try something like this:
```
dpkg-query -W -f='${Package} status is: ${Status}\n' | grep -v 'ok'
```
It will grep all lines that have no "ok". In a normal system, you should get no output.

---

### Post by rv65 on 2012-03-04
A lot of those ppa's I have removed from my system, which makes it more ironic.

---

### Post by rv65 on 2012-03-04
I checked dictionaries-common and have the previous version config file with the latest version of the software. It probably is broken.

---

### Post by rv65 on 2012-03-04
> **effenberg0x0 said:**
> Hey, 
I haven't piped it, but you can play with it separately, and improve it, which is better.

So, this are the PPA_NAMES you have in your PPAs, so you dont have to ls -> cat -> translate -> tee them to some file or save hem to an array. This is stdout, you choose what to do.
```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e 's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e 's|oneiric||' | sed -e 's|precise||g' | sed -e 's|lucid||g' | sed -e 's|main||' | sed -e 's|^ppa||g' | sed -e 's|#||g' | sed -e 's| ||g' | awk 'BEGIN {FS="/"} {print $1}'; done

```Then you can look at your apt for info regarding the packages from each of those PPAs:
```
grep '^Package' /var/lib/apt/lists/ppa.launchpad.net_${PPA_NAME}*Package); done
```And finally, you need to check two informations with dpkg-query:
1) Is the package still installed?
2) What are it's conflicts?

```
dpkg-query -W -f='Package ${Package} status is ${Status}. Conflicts: ${Conflicts}\n' <EachPackageNameYouGotFromPreviousCommand>
```Notice that this is just to avoid simply ppa-purging all your PPAs, which would be too brutal.

Regards,
Effenberg

I forgot to suggest you one more thing: Maybe you can easily find out whats wrong by checking which packages are not reported as "Installed OK" by dpkg. They can be broken, Half-Installed, etc. You could try something like this:
```
dpkg-query -W -f='${Package} status is: ${Status}\n' | grep -v 'ok'
```
It will grep all lines that have no "ok". In a normal system, you should get no output.

All those commands show errors, and I really do not know how to properly do this.

---

