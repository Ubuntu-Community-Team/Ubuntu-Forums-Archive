---
title: "Upgraded to 11.04 and lost my LTSP network!!!!"
date: 2011-05-02
forum: Server Platforms
---

### Post by pjomara on 2011-05-02
I upgraded my Edubuntu 10.10 LTSP server to 11.04 and I've lost my network.  The server boots fine but none of the workstations connect.  They start the boot process but hang-up as it starts to load the GUI.

The screen on-which the computers hang displays Ubuntu 10.10.  Do I have to manually update the LTSP image?

Thank you in advance for any and all help.

---

### Post by thresher9lzx on 2011-05-10
I upgraded last-night rebooted today, I have the exact same issue.  upgraded from 10.10 -> 11.04.

I found this thread.

I reviewed /opt/ltsp/ folders and show date of last year when I had installed 10.10 

observing /opt/ltsp/images/i386.img was old too.

i ran 

ltsp-update-image -a i386
ltsp-update-kernels 

I am still getting the hang on the ubuntu screen ( would there be an issue with the fuse filesystem mounting/ other what is the packages that should be installed per the upgrade to minimally get LTSP to work?

here is output from ltsp-info:

root@TS:/opt/ltsp/images# ltsp-info
server information:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty

server packages:
rc ldm 2:2.2.1-0ubuntu1
un ldm-edubuntu-theme <none>
ii ldm-server 2:2.2.1-0ubuntu1
un ldm-themes <none>
un ldm-ubuntu-themes <none>
un ldminfod <none>
un ltsp-client <none>
un ltsp-client-core <none>
ii ltsp-docs 0.99+bzr115-1
un ltsp-livecd <none>
ii ltsp-manager 0.0.2-0ubuntu3
ii ltsp-server 5.2.8-0ubuntu1
ii ltsp-server-standalone 5.2.8-0ubuntu1
un ltsp-utils <none>
ii ltspfs 0.7-2

packages in chroot: /opt/ltsp/i386
un ldm <none>
un ldm-themes <none>
ii ldm-ubuntu-theme 2:2.0.41
un ldm-ubuntu-themes <none>
ii ltsp-client 5.2.4-0ubuntu6
un ltsp-client-core <none>
ii ltspfsd 0.7-0ubuntu1
un ltspfsd-core <none>

found: /opt/ltsp/i386/etc/lts.conf

found image: /opt/ltsp/images/i386.img

root@TS:/opt/ltsp/images#

---

### Post by InterpreDemon on 2013-04-29
This is exactly why I asked the same in April of '12... seems I cannot find anybody who has posted an upgrade and debug procedure for Ubuntu with LTSP already running. Very disturbing that after the client image rebuild you still cannot get the clients to boot.

---

