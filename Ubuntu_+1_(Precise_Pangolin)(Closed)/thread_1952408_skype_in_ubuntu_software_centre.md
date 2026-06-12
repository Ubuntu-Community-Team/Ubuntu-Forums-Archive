---
title: "skype in ubuntu software centre?"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2012-04-04
I have a couple of machines testing 12.04 beta 2 updated and neither is showing skype in ubuntu software centre.
In update manager 'settings' and then 'other software' tab, I see that partner software is not enabled by default. 
However, when I check it to enable, I see that the partner software is then enabled, and in fact also then uncommented in /etc/(whatever) sources list, but, after a refesh then skype still does not seem to be offered.  I am told elsewhere that it was believed skype was added to the partners list a couple of days ago.

Is this a bug?

---

### Post by Pilot6 on 2012-04-04
It is not a bug. Skype is not in precise repo yet. You can download and install .deb from skype.com

---

### Post by alphacrucis2 on 2012-04-04
Installing Skype from partner repos worked for me when I just tried it.


```
sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  skype-bin:i386
The following NEW packages will be installed:
  skype skype-bin:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,234 B/23.6 MB of archives.
After this operation, 29.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.canonical.com/ubuntu/ precise/partner skype amd64 2.2.0.35-0precise2 [2,234 B]
Fetched 2,234 B in 0s (3,191 B/s)  
Selecting previously unselected package skype-bin:i386.
(Reading database ... 317028 files and directories currently installed.)
Unpacking skype-bin:i386 (from .../skype-bin_2.2.0.35-0precise2_i386.deb) ...
Selecting previously unselected package skype.
Unpacking skype (from .../skype_2.2.0.35-0precise2_amd64.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Setting up skype-bin:i386 (2.2.0.35-0precise2) ...
Setting up skype (2.2.0.35-0precise2) ...
```

```
 cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"


```


Seems to work ok.

---

### Post by candtalan on 2012-04-04
> **alphacrucis2 said:**
> Installing Skype from partner repos worked for me when I just tried it.

So it will presumably also work for me when using apt-get, thanks.
However, what is different about the ubuntu software centre that skype is not showing up?

---

### Post by alphacrucis2 on 2012-04-04
> **candtalan said:**
> So it will presumably also work for me when using apt-get, thanks.
However, what is different about the ubuntu software centre that skype is not showing up?


It may be related to this:

[http://askubuntu.com/questions/35124/what-does-ubuntu-software-center-error-bad-quality-package-means](http://askubuntu.com/questions/35124/what-does-ubuntu-software-center-error-bad-quality-package-means)

I guess you could manually download the deb package and try double clicking on it from nautilus and see what usc makes of it.

---

### Post by philinux on 2012-04-04
> **candtalan said:**
> I have a couple of machines testing 12.04 beta 2 updated and neither is showing skype in ubuntu software centre.
In update manager 'settings' and then 'other software' tab, I see that partner software is not enabled by default. 
However, when I check it to enable, I see that the partner software is then enabled, and in fact also then uncommented in /etc/(whatever) sources list, but, after a refesh then skype still does not seem to be offered.  I am told elsewhere that it was believed skype was added to the partners list a couple of days ago.

Is this a bug?

It's listed under my SC right now I've had partner activated for a while and maybe a recent update has brought it in.

---

