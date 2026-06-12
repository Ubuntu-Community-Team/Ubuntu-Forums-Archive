---
title: "Launching Boinc Manager Fails - Relocation Error"
date: 2019-07-28
forum: Server Platforms
---

### Post by w-kym-wittal on 2019-07-28
When launching Boinc Manager on my server (ver 16.04 LTS), receive the following error:

```
kym@ubuntu:~$ boincmgr
boincmgr: relocation error: boincmgr: symbol _ZThn776_N17wxGenericListCtrl31GetSizeAvailableForScrollTargetERK6wxSize, version WXU_3.0 not defined in file libwx_gtk2u_core-3.0.so.0 with link time reference
```

Checking libwx status, results are:

```
kym@ubuntu:~$ sudo apt-cache search libwxgt*
libwxgtk-media3.0-0v5 - wxWidgets Cross-platform C++ GUI toolkit (GTK+ media library runtime)
libwxgtk-media3.0-0v5-dbg - debugging symbols for the wxGTK media library
libwxgtk-media3.0-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK+ media library development)
libwxgtk-webview3.0-0v5 - wxWidgets Cross-platform C++ GUI toolkit (webview library runtime)
libwxgtk-webview3.0-0v5-dbg - debugging symbols for the wxGTK webview library
libwxgtk-webview3.0-dev - wxWidgets Cross-platform C++ GUI toolkit (webview library development)
libwxgtk3.0-0v5-dbg - debugging symbols for the wxGTK GUI toolkit library
libwxgtk3.0-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)
libwxgtk3.0-0v5 - wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
kym@ubuntu:~$ 
```

Checking wx-config --libs results in:

```
kym@ubuntu:~$ wx-config --libs
The program 'wx-config' can be found in the following packages:
 * libwxbase3.0-dev
 * libwxgtk3.0-dev
Try: sudo apt install <selected package>
```

Which is confusing, since it is listed previously as being installed. Attempting to install the first package above gives:

```
kym@ubuntu:~$ sudo apt install libwxbase3.0-dev
[sudo] password for kym: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libwxbase3.0-dev : Depends: libwxbase3.0-0v5 (= 3.0.2+dfsg-1.3ubuntu0.1) but 3.0.3.1+dfsg-1~ubuntu14.04.1~ppa2 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Attempting to install the second package gives:

```
kym@ubuntu:~$ sudo apt install libwxgtk3.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libwxgtk3.0-dev : Depends: libwxgtk3.0-0v5 (= 3.0.2+dfsg-1.3ubuntu0.1) but 3.0.3.1+dfsg-1~ubuntu14.04.1~ppa2 is to be installed
                   Depends: libwxbase3.0-dev (= 3.0.2+dfsg-1.3ubuntu0.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I have tried:

sudo dpkg --configure -a
sudo dpkg -l | grep ^..r
sudo apt clean
sudo apt update
sudo apt update --fix-missing

I have removed and re-installed Boinc Manager, no change.

I beleive I am above my pay grade in terms of expertise and would request any advice or suggestions as to what to do next.  Thanks in advance.

---

### Post by aljames2 on 2019-07-28
apt update just checks for available updates to your packages.  Were any updates available?  If do, did you also run apt upgrade to install the updates?  Good practice to backup before upgrading.

---

### Post by w-kym-wittal on 2019-07-29
Running sudo apt update found all packages were up to date.

---

