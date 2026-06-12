---
title: "Installing VMWare-Server 2.0 in Ubuntu 8.10"
date: 2009-01-29
forum: Virtualisation
---

### Post by fester225 on 2009-01-29
Does anybody have a procedure for installing VMWare-Server 2.0 in Ubuntu 8.10?

The old install procedures aren't working here, and anything with any-any is out of date. It would be very helpful for the procedure to include getting the "build essentials" installed.

---

### Post by Cato2 on 2009-01-29
I ended up installing VMware Server 2.0 from a tar file because the Canonical partner/commercial repository didn't work, even when I downloaded the .deb and used dpkg.  This was on Ubuntu 7.10 using a Hardy kernel, but the installer detected this and worked fine.

This is the main link I used - although it covers Server 1.0 which has a GUI not a web interface, it's pretty good. [http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

If you need to get Windows physical systems transferred over to VMware, try VMware Converter for P2V conversion - it worked very well so now I have converted the Windows half of my dual boot desktop into a VM.

LATER: Here's the link from this forum's Mega-Thread covering just what you need: [http://ubuntuforums.org/showpost.php?p=6122138&postcount=2](http://ubuntuforums.org/showpost.php?p=6122138&postcount=2)


Here are my notes which should help you - in Foswiki/TWiki format.

[[[http://communities.vmware.com/community/vmtn/server/server2](http://communities.vmware.com/community/vmtn/server/server2) VMware Server 2 Forum]]

[[[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html) How to install VMware Server 1.0 in Ubuntu 7.10]] - quite good but the admin client is not web-based in 1.0.

Useful links:
   * [http://sanbarrow.com/vmx.html](http://sanbarrow.com/vmx.html) - good list of all config file items (.vmx)
   * [http://petruska.stardock.net/Software/VMware.html](http://petruska.stardock.net/Software/VMware.html) - utilities including VMX builders
   * [http://www.easyvmx.com/easyvmx.shtml](http://www.easyvmx.com/easyvmx.shtml) - EasyVMX, online VMX builder

[http://vmetc.com/](http://vmetc.com/) - blog on virtualization


---+++ Setup

Installed from tar file - did first try a .deb file downloaded from canonical repo, installed with dpkg but failed.

Put all commands and libs under /usr/local, with the VMs in =/opt/vmware/virtual-machines=

Tried to do CheckInstall but the .deb built did not install.

Installed fine, detected the Hardy kernel used with Gutsy installation OK.

   * I created a =vmware= user via KDE user mgmt tool - otherwise it defaults to root as admin user

Admin console (VMware Infrastructure Web Access) is at [https://localhost:8333](https://localhost:8333).

   * This was very, very slow to echo characters during login to start with - however, it was OK in Opera and ended up being OK in Firefox

   * Had to create a new datastore in shell - i.e. root-owned directory that contains VMs - then created it in web interface

   * Created VM OK and started it, but couldn't see the Console tab - this only appears on VMs selected from Inventory - found out in VMware forum fortunately.  The Remote Console plugin is actually VNC turned into a plugin and can run full-screen or in a window - hence you get remote access for free, but it's not very secure.

   * You need to start/stop VMs from the web interface not from the console.

---

### Post by HermanAB on 2009-01-29
The v2.0 thing is kinda crappy and not worth the trouble really.  The previous version works way better.  Some things are *not* better with a web server.

It certainly makes Virtualbox look better.

Cheers,

Herman

---

