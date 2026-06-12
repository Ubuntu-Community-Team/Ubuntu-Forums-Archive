---
title: "MAAS Node Inside VirtualBox - Install Fails"
date: 2012-05-14
forum: Ubuntu Cloud and Juju
---

### Post by dotnetted on 2012-05-14
Hi all,

Is is possible to install a MAAS node inside Virtual Box on the same physical machine that is running the MAAS controller? If not, is there another way to get a node running on the same box as the controller?

When installing 12.04 as a MAAS node inside Vbox it correctly detected the MAAS server (same.ip.as.vbox.host:80). As soon as I advance to the next step the installation sends sigterms and shuts down.

(Same problem as: [http://askubuntu.com/questions/129196/maas-node-install-shutdown-error-when-installing-from-cd-rom](http://askubuntu.com/questions/129196/maas-node-install-shutdown-error-when-installing-from-cd-rom))

EDIT:
Also, the web interface shows "Node added but never seen". I assume this node was 'added' from the installer inside the Vbox instance right before it decided to shut down.

Thanks for any info!

---

### Post by andrejonker on 2012-06-13
Maybe not exact answer you were looking for, but here's walkthrough by MARCO CEPPI : [http://marcoceppi.com/2012/05/juju-maas-virtualbox/](http://marcoceppi.com/2012/05/juju-maas-virtualbox/)

Also note:  I happily selected that option when the machine suddenly SIGKILLs all processes then powers off.

and later: Each machine will turn off after successful setup and MAAS Dashboard will update.

---

