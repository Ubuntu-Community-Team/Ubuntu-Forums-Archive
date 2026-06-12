---
title: "Latest 16Apr flashplugin-installer fails."
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kelpdip on 2012-04-16
There seem to be 2 problems here. It requires gksudo, which is not a dependency in apt, and won't be installed on many systems. Then it attempts to run a python script -- package-data-downloader -- with bash.
Automatic Muon Output:
```
Warning: Could not find 'gksudo', starting '/bin/bash' instead.  Please check your profile settings.

/usr/lib/update-notifier/package-data-downloader: line 3: Process new requests to download per-package data: command not found
/usr/lib/update-notifier/package-data-downloader: line 19: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 20: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 21: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 22: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 23: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 24: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 25: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 26: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 27: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 28: import: command not found
/usr/lib/update-notifier/package-data-downloader: line 29: import: command not found
from: can't read /var/mail/datetime
/usr/lib/update-notifier/package-data-downloader: line 32: DATADIR: command not found
/usr/lib/update-notifier/package-data-downloader: line 33: STAMPDIR: command not found
/usr/lib/update-notifier/package-data-downloader: line 34: NOTIFIER_SOURCE_FILE: command not found
/usr/lib/update-notifier/package-data-downloader: line 35: NOTIFIER_FILE: command not found
/usr/lib/update-notifier/package-data-downloader: line 36: NOTIFIER_PERMANENT_SOURCE_FILE: command not found
/usr/lib/update-notifier/package-data-downloader: line 37: NOTIFIER_PERMANENT_FILE: command not found
/usr/lib/update-notifier/package-data-downloader: line 39: failures: command not found
/usr/lib/update-notifier/package-data-downloader: line 40: permanent_failures: command not found
/usr/lib/update-notifier/package-data-downloader: line 42: syntax error near unexpected token `('
/usr/lib/update-notifier/package-data-downloader: line 42: `def create_or_update_stampfile(file):'

```

Was that even the correct script being executed? I'm confused by the way the installer works.
> finn@finn-ThinkPad-X120e:~$ locate flashplugin-installer
/usr/lib/flashplugin-installer
/usr/lib/flashplugin-installer/install_plugin
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/app-install/desktop/flashplugin-installer.desktop
/usr/share/doc/flashplugin-installer
/usr/share/doc/flashplugin-installer/changelog.gz
/usr/share/doc/flashplugin-installer/copyright
/usr/share/package-data-downloads/flashplugin-installer
/var/cache/flashplugin-installer
/var/lib/flashplugin-installer
/var/lib/dpkg/info/flashplugin-installer.config
/var/lib/dpkg/info/flashplugin-installer.list
/var/lib/dpkg/info/flashplugin-installer.md5sums
/var/lib/dpkg/info/flashplugin-installer.postinst
/var/lib/dpkg/info/flashplugin-installer.postrm
/var/lib/dpkg/info/flashplugin-installer.prerm
/var/lib/dpkg/info/flashplugin-installer.templates
/var/lib/update-notifier/package-data-downloads/flashplugin-installer


---

### Post by jfernyhough on 2012-04-16
How are you installing it? I take it you are running Kubuntu if you are using muon?

---

### Post by kelpdip on 2012-04-16
Yes, kubuntu. When installing graphically, with synaptic or muon, the package manager seems to call a helper script for packages that require a post install secondary download. This is the first time that has failed to work with flashplugin-installer, so there is a regression somewhere, although I'm not 100% sure how the secondary download packages work. Someone mistakenly slipped a gksudo in there, I'm assuming.

Command line install with
sudo apt-get install --reinstall flashplugin-installer
worked.

Edit: Been digging through the flashplugin installer.deb configs and scripts, it's over my head.

---

### Post by dcstar on 2012-04-17
> **kelpdip said:**
> Yes, kubuntu. When installing graphically, with synaptic or muon, the package manager seems to call a helper script for packages that require a post install secondary download. This is the first time that has failed to work with flashplugin-installer, so there is a regression somewhere, although I'm not 100% sure how the secondary download packages work. Someone mistakenly slipped a gksudo in there, I'm assuming.
........

Put in a bug report.

---

### Post by Ender985 on 2012-04-17
I think I'm suffering the same problem; today I updated the system and adobe flashplugin installer failed to download some file and could not install. I'm using a standard ubuntu 12.04 installation.

I don't know where the script that is executed is located, so I could not read the errors to confirm it is the same issue; if someone knows how can I execute it from prompt I'll be happy to do so.

---

### Post by plucky on 2012-04-17
> **Ender985 said:**
> I think I'm suffering the same problem; today I updated the system and adobe flashplugin installer failed to download some file and could not install. I'm using a standard ubuntu 12.04 installation.

I don't know where the script that is executed is located, so I could not read the errors to confirm it is the same issue; if someone knows how can I execute it from prompt I'll be happy to do so.

Try ```
sudo apt-get install flashplugin-installer
``` and see what happens.

Today it took a long time to complete,but it eventually did so for me.

Good Luck

---

### Post by philinux on 2012-04-17
> **Ender985 said:**
> I think I'm suffering the same problem; today I updated the system and adobe flashplugin installer failed to download some file and could not install. I'm using a standard ubuntu 12.04 installation.

I don't know where the script that is executed is located, so I could not read the errors to confirm it is the same issue; if someone knows how can I execute it from prompt I'll be happy to do so.

Do a sudo dpkg --configure -a and post back any errors.

It installed fine here. Regular Ubuntu.

---

### Post by dcstar on 2012-04-18
> **philinux said:**
> Do a sudo dpkg --configure -a and post back any errors.

It installed fine here. **Regular Ubuntu**.

The OP says he is using **Kubuntu** and the installer requires gksudo - a GTK component which may not be in the KDE environment?

---

### Post by philinux on 2012-04-18
> **dcstar said:**
> The OP says he is using **Kubuntu** and the installer requires gksudo - a GTK component which may not be in the KDE environment?


```
sudo dpkg --configure -a
``` is not graphical and applies to all flavours.

---

### Post by Ender985 on 2012-04-18
I suspect the problem might be I'm behind a proxy, because the update gets stuck at:

```
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233.orig.tar.gz

IOError: [Errno socket error] [Errno 110] Connection timed out
```

And then a popup shows up with

```
The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.
```

allowing me to try again (which also does not work).

I have set up the proxy settings in all locations I know of, in Network Settings, in .bashrc (exporting $http_proxy), in /etc/apt/apt.conf and in /etc/wgetrc as well, so that both the command line and graphical updates work, wget works, and browsers work. However it might be that the update is trying to get the package in a way where he is unaware of the proxy and thus is failing.

If I run 'sudo apt-get install flashplugin-installer' I get 

```
flashplugin-installer is already the newest version
```

but this is strange, since if I reboot and ask for updates, flashplugin-installer will show up again giving me the same timeout error. Similarly, if I run 'sudo dpkg --configure -a' nothing happens, no errors or any other kind of output. And if I try 'sudo apt-get install --reinstall flashplugin-installer' the same happens, I get stuck at downloading the package and a timeout eventually occurs.

The flash plugin is clearly not properly installed, since all websites that requiere it are complaining to me that I should get the latest version.

Maybe the OP was also working behind a proxy?

Edit: For the record, I can download [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233.orig.tar.gz) just fine both via chromium and via wget.

---

### Post by teh603 on 2012-04-18
I know I'm not behind a proxy, and I had the same problem on 10.10.

---

