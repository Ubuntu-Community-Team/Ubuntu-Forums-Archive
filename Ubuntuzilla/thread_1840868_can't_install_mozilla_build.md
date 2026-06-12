---
title: "can't install mozilla build"
date: 2011-09-08
forum: Ubuntuzilla
---

### Post by matteosistisette on 2011-09-08
Hi,

I followed step-by-step the installation instructions at [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

Previously I had Firefox 3.6 installed, which came with Ubuntu.

Now I have a "Mozilla Build of Firefox" item in under the Internet submenu of the system applications menu, but when I launch it, the same old Firefox 3.6 is still launched.

I didn't get any error during the installation process.

What am I missing? Here's the terminal output from the installation:
```

sudo apt-get install firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 15.9MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main firefox-mozilla-build i386 6.0.2-0ubuntu1 [15.9MB]
Fetched 15.9MB in 13s (1,194kB/s)                                              
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 250434 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_6.0.2-0ubuntu1_i386.deb) ...
Adding 'diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up firefox-mozilla-build (6.0.2-0ubuntu1) ...
```

---

### Post by Enigmapond on 2011-09-08
If you are attempting to install the current stable version of FF. Try adding the ppa:

```
sudo add-apt-repository **ppa:mozillateam/firefox-stable**
```

Then update and upgrade.

Cheers!

---

### Post by matteosistisette on 2011-09-08
Oh my,

I simply needed to restart the computer. This should DEFINITELY be mentioned in the guide, as it is far from obvious (I think it is the first time I have to restart the system just to get an update to a program to work).

@Enigmapond this is not about ff-stable, this is about ubuntuzilla; the repository is another one and I had already added it (otherwise the apt-get install command would have given errors).

---

### Post by nanotube on 2011-09-13
actually, you just needed to quit firefox. if a firefox process is running, trying to start it will just spawn a new window of existing process.

---

