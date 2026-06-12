---
title: "Linux version of Bluetack's &quot;Hosts Switch&quot; with update feature available for download"
date: 2008-11-28
forum: Security
---

### Post by linuxed on 2008-11-28
Name: Toggle Hosts
Version: 1.0

I use a number of security tools from the bluetack.co.uk website on my Windows pc and I've been searching for some alternatives for Linux.  I use [**IPList**](http://sourceforge.net/projects/iplist) in Linux instead of Protowall, but to this point I never could find a replacement for bluetack's "Hosts Manager" or "Hosts Switch".  I had previously been downloading the hosts list from the bluetack website and manually installing it on my pc by backing up my own and then replacing it with the bluetack hosts list.  Unfortunately it was never as easy as using bluetack's "Hosts Manager" in Windows.  The hosts list on my pc still had to be manually updated and if I wanted to temporarily disable it I had to manually restore my hosts backup.

To hopefully simplify the process of installing, updating and editing my hosts list I put together a very basic package containing a few simple bash scripts that automate the process.  I've attached the deb package to this post for anyone who is interested in downloading it.  Once it's installed there will be 3 new entries in your Internet menu.  The "Hosts: Edit" menu item will open your /etc/hosts file in gedit allowing you to modify any of the entries.  The "Hosts: Enabled" menu item will toggle your hosts file either on or off.  If it says "Enabled" then clicking the menu item will switch it to "Disabled" and vice versa.

When the package is first installed it will backup your existing hosts file by copying it to /etc/hosts.bak.  Anytime you disable the hosts list it will restore your original hosts file (hosts.bak) to /etc/hosts.  The third menu item "Hosts: Update" will download the latest version of bluetack's hosts list, extract it, and then merge it with your original hosts file.

I've only tested this in Kubuntu 8.10 with KDE 4 so you may notice some minor differences on the menus in Gnome.  I'm releasing this into the public domain so feel free to distribute or modify it in any way.  Please note that while I did attempt to protect the integrity of your original hosts file I take no responsibility for any damage caused to your hosts file as a result of the scripts included in this package.  Download and install this package at your own risk.

TIP:
To automatically update your hosts list each time you login simply create a new autostart entry to run "sudo updatehosts" on startup.  In KDE you can just copy the updatehosts file to your Autostart folder.

cp /usr/sbin/updatehosts /home/YourUserName/.kde/Autostart

```

All icons contained in this work are licensed under a
Creative Commons Attribution 3.0 License and their
copyrights belong exclusively to Ray Cheung. All other
files contained in this work are hereby released into
the Public Domain. To view a copy of the public domain
dedication please visit:

http://creativecommons.org/licenses/publicdomain/

or send a letter to:

Creative Commons
171 Second Street
Suite 300
San Francisco, California, 94105
USA

```
[[img]http://i.creativecommons.org/l/publicdomain/88x31.png[/img]](http://creativecommons.org/licenses/publicdomain/)

---

### Post by maxol on 2008-11-29
Thanks for this. Installs fine in Gnome too.

---

### Post by markharding557 on 2008-11-30
would not the gpl be a better licence to use since this protects the rights of freedom of use

---

### Post by linuxed on 2008-11-30
> 
would not the gpl be a better licence to use since this protects the rights of freedom of use

The public domain is the only true FREE.  While the GPL does protect the rights of the original author it also places restrictions on how the software can be distributed or modified.  All of the files included in the package (with the exception of the icons) are currently copyright free and can be distributed or modified in any way.

The icons can still be redistributed but they have to be accompanied by the "Terms of Use" file.  They're free for personal or commercial use, but are released under the Creative Commons Attribution 3.0 License so they're not in the public domain.

---

### Post by oshunluvr on 2011-12-04
Hey, I was looking into BISS host files and stumbled across the old menu entey deb you wrote back in 2008/09 and I was wondering if it was still usable. I'm using Kubuntu 11.04 at the moment and will likely upgrade to 12.04 in April. Thanks for your time.

---

### Post by linuxed on 2011-12-05
I'm currently using it in Ubuntu 10.10 and it works fine.  Go ahead and try to install it.  If it doesn't work you can always remove it.  You can install it with dpkg or gdebi.

**to install**
sudo apt-get install gdebi
sudo gdebi togglehosts1.1.deb

**to remove**
sudo dpkg --purge togglehosts

---

