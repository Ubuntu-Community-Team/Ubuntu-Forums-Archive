---
title: "Creating VPN connections via network-manager"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by pferraro on 2013-04-17
I'm aware that the network-manager vpn plugin builds often fall behind the main network-manager module, however, it's been some time now that I've been unable to create new vpn connections via network-manager using either vpnc or openvpn.  Even with the appropriate plugin packages installed, the network manager GUI has no option to create a new vpn connection, but only "Import a file".  I suspect that this is because the network-manager vpn plugins are still at 0.9.6 while the main network-manager package is 0.9.8.  Does anyone else have this problem?  If so, I'll open a ticket to get these packages updated.

---

### Post by dino99 on 2013-04-17
better going to the "network" subforum for such wish

---

### Post by pferraro on 2013-04-17
The network subforum is for current releases only.  This is a raring-specific question.

---

### Post by dino99 on 2013-04-17
> **pferraro said:**
> The network subforum is for current releases only.  This is a raring-specific question.

your request is not u+1 specific (but its up to you indeed)

---

### Post by jbicha on 2013-04-17
What version of gnome-control-center are you running?
Do you have network-manager-openvpn-gnome and network-manager-vpnc-gnome installed?

---

### Post by pferraro on 2013-04-17
I'm running the version from ppa:gnome3-team/gnome3-staging:

$ dpkg -s gnome-control-center
Status: install ok installed
<snip/>
Version: 1:3.8.1-0ubuntu1~raring1

I had the same problem with the 3.8.0 version of gnome-control-center.

Here are the relevant network-manager packages:
$ dpkg -s network-manager
Status: install ok installed
<snip/>
Version: 0.9.8.0-0ubuntu5

$ dpkg -s network-manager-vpnc-gnome
Status: install ok installed
<snip/>
Version: 0.9.6.0-0ubuntu2

$ dpkg -s network-manager-openvpn-gnome
Status: install ok installed
<snip/>
Version: 0.9.6.0-0ubuntu3

---

### Post by jbicha on 2013-04-17
As a workaround for now, consider ppa-purging the GNOME3 Staging PPA.

---

