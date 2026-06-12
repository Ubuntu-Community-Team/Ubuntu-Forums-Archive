---
title: "Setting up a filter/firewall/fileserver"
date: 2008-06-07
forum: Server Platforms
---

### Post by DavidWeight on 2008-06-07
Hi,
I would like to set up a firewall to sit between my router and switch with most ports blocked, but the ability to open up ssh ports, etc.
If possible, I'd like the ability to block bittorrent traffic, and keyword filtering on http traffic.
To complicate it, I'd also like to use the same machine as a samba file server to the intranet.
Does anyone have any pointers/experience with this? I've been using Ubuntu on the desktop for a while, but haven't properly played with the server version before...

Thanks in advance for any help you can give,
David

---

### Post by spiderbatdad on 2008-06-08
My understanding is that your router is this type of firewall. It only opens ports necessary for tcp/ip. Or you forward the lower ports for your ssh and http requests. Any additional serverside firewall would be equally vulnerable once you open the ports you would need open to host files.

Your built-in firewall iptables or ufw is just as effective.

I think a different approach to security would be necessary, if security is your primary concern. Perhaps a web application firewall...which I know nothing about, or start with a minimal http server and learn how to secure it via something like chrooting.

---

### Post by disabledveteran on 2008-06-08
I'm putting together a Small Business Server that includes this type of functionality, and here are some thoughts:

NOTE, I'm still a Linux newbie, so I'm doing this and learning as I go.

I realize that the best security set up is to separate the machines by function - firewall/filter on one system, and file server on another.  However, I am trying to replicate a Small Business Solution based on Ubuntu that is similar to [Collax]("http://www.collax.com") or [ClarkConnect]("http://www.clarkconnect.com") - these companies have successfully built and provided a small biz server based on RedHat source code for several years...and it can be set up on a single machine.

PLAN A:
My intention is to use remote management for this system - both because I am planning on supporting businesses and because I want to mount my *personal* server in some closet space and leave it.  I have selected packages that are supportable via the [Webmin]("http://www.webmin.com") interface.

Here are the steps I have taken so far.
[LIST]
[*]Install Ubuntu Server 8.04 with DNS using entire disk with LVM (for the production version, I will use LVM with encryption).
[*]Install the default Ubuntu server modules: DNS, LAMP, MAIL, OPEN SSH, Print Server (if you need it), Samba File Server - follow instructions for each package to complete installation.  The mail server should be set up to retrieve mail from other accounts and filter them for SPAM/AV.  Specific instructions for SAMBA are [here]("https://help.ubuntu.com/community/SettingUpSamba").
[*]Install latest version of webmin ([Link here]("http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html"), but be sure to replace the version number in the command lines with the latest version 1.420)
[*]Connect to your server using http://<hostname or IP>:10000.  At this point, you can do almost everything from the webmin SSH Login interface.
[*]Install firewall of choice - in keeping with the "Webmin" modules, I installed [Shorewall]("http://www.shorewall.net/shorewall_setup_guide.htm") and activated the accompanying Webmin Module
[*]Install SQUID Proxy with DansGuardian content filter
[*]Install Spam Assassin
[*]I chose to go with [BitDefender]("http://www.bitdefender.com") for my AntiVirus as I've used them before and they have a [webmin module]("http://news.bitdefender.com/NW72-en--Linux-Mailserver-protection-just-got-better.html").
[/LIST]
There are some other modules I've installed for the SBS that won't be necessary for your intranet server...

This is as far as I have made it - anyone care to jump in?

PLAN B:  Download [Untangle]("http://www.untangle.com") and configure SAMBA on the machine.:lolflag:

PLAN C:  Configure firewall and file server on separate Virtual Machines...I'm waiting on Sun's Xen-based Hypervisor to test this one out.

---

