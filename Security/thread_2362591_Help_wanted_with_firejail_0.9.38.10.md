---
title: "Help wanted with firejail 0.9.38.10"
date: 2017-05-31
forum: Security
---

### Post by vasa1 on 2017-05-31
I installed firejail 0.9.38.10 which is the version in the repos. I'm trying to run it on the Openbox session of Lubuntu 16.04. 
```
$ uname -r
4.4.0-78-generic
$ 
```
According to [https://firejail.wordpress.com/download-2/](https://firejail.wordpress.com/download-2/), there are much newer versions available from the author's site but, because of "Firejail Long Term Support: 0.9.38.10", I'm assuming that this old version is still supported.

The following commands don't work:```
firejail /home/vasa1/MyFox/firefox/firefox
firejail --overlay /home/vasa1/MyFox/firefox/firefox
firejail --private /home/vasa1/MyFox/firefox/firefox
```They all end with```
/bin/bash: /home/vasa1/MyFox/firefox/firefox: No such file or directory
```but```
firejail --noprofile /home/vasa1/MyFox/firefox/firefox
```works just fine.

However, I want to get the *--overlay* option working because that will, if I understand correctly, not leave any trace behind. The *--noprofile* option, which works, writes to *~/.mozilla* and I don't want that.

My firefox profile in */home/vasa1/.config/firejail/firefox.profile*, is this:```
# Firejail profile for Mozilla Firefox (Iceweasel in Debian)
noblacklist ${HOME}/.mozilla
include /etc/firejail/disable-mgmt.inc
include /etc/firejail/disable-secret.inc
include /etc/firejail/disable-common.inc
include /etc/firejail/disable-devel.inc
caps.drop all
seccomp
protocol unix,inet,inet6,netlink
netfilter
tracelog
noroot
whitelist ${DOWNLOADS}
whitelist ~/.mozilla
whitelist ~/.cache/mozilla/firefox
whitelist ~/Dropbox/MyLinks.html
whitelist ~/Dropbox/Banks.html
include /etc/firejail/whitelist-common.inc

# experimental features
#private-etc passwd,group,hostname,hosts,localtime,nsswitch.conf,resolv.conf,gtk-2.0,pango,fonts,iceweasel,firefox,adobe,mime.types,mailcap,asound.conf,pulse
```

Is there something in my profile that prevents firejail from working properly?

///////////////////////////////////////////////////

More info ...```
firejail --noprofile --overlay /home/vasa1/MyFox/firefox/firefox
```works "partly".

I see```
firejail --noprofile --overlay /home/vasa1/MyFox/firefox/firefox
Parent pid 13068, child pid 13069
OverlayFS configured in /home/vasa1/.firejail/13068 directory
Warning: failed to unmount /sys

Child process initialized

(firefox:2): dconf-CRITICAL **: unable to create directory '/run/user/1000/dconf': Permission denied.  dconf will not work properly.

(firefox:2): dconf-CRITICAL **: unable to create directory '/run/user/1000/dconf': Permission denied.  dconf will not work properly.

(firefox:2): dconf-CRITICAL **: unable to create directory '/run/user/1000/dconf': Permission denied.  dconf will not work properly.


```
The *dconf-CRITICAL* lines keep on coming but the browser opens and things look just fine. But as soon as I click on a link, I **instantly** get
```
Firefox can&#8217;t find the server at connect.bharatbank.com.

    Check the address for typing errors such as ww.example.com instead of www.example.com
    If you are unable to load any pages, check your computer&#8217;s network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.
```It's not just that site but any site gives a similar response. 

I can open local html files (stored on my computer). and "save" them. Of course, when I exit the browser, nothing is written to file or to *~/.mozilla* because of *--overlay*.

---

### Post by vasa1 on 2017-05-31
In [https://github.com/netblue30/firejail/issues/151#issuecomment-159978829](https://github.com/netblue30/firejail/issues/151#issuecomment-159978829) dated Nov 26, 20_15_, the developer states that> I know what the problem is: --net doesn't work for wireless interfaces. I works only for regular wired Ethernet interfaces - wireless doesn't have support in the kernel for some features I need in the network namespace.
And goes on [to suggest]("https://github.com/netblue30/firejail/issues/151#issuecomment-160151762")```
firejail --noprofile --overlay --dns=8.8.8.8
```[or]("https://github.com/netblue30/firejail/issues/151#issuecomment-160232810")```
firejail --noprofile --overlay --dns=8.8.8.8 --dns=8.8.4.4
```

This seems to work for me. I'm on wireless. I'll come back and mark this [SOLVED] once I sure.

---

