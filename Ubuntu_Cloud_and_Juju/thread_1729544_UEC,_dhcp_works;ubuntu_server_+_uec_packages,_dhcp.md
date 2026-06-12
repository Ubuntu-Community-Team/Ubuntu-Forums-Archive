---
title: "UEC, dhcp works;ubuntu server + uec packages, dhcp doesn't work"
date: 2011-04-15
forum: Ubuntu Cloud and Juju
---

### Post by Luis Rodero-Merino on 2011-04-15
Hi,

I'm trying to install an eucalyptus cloud using ubuntu server 10.04 from an usb memory stick.

If at the beginning of the installation process I choose to install the 'Ubuntu Enterprise Cloud', everything goes fine and all required processes are started (during the installation I demand to install the cloud controller, a cluster controller, walrus and a storage controller).

But if I choose to install an 'Ubuntu Server', and then I manually install the packages (apt-get install eucalyptus-cloud eucalyptus-cc eucalyptus-walrus eucalyptus-sc) then _not_ all processes are started: the dhcp server is not running, and in fact /var/run/eucalyptus/net is empty.

Why can this be? Am I supposed to configure the dhcp server manually in the latter case?

Regards, and thank you for your help,

---

### Post by Luis Rodero-Merino on 2011-04-15
Small update: dhcp doesn't work either when installing Ubuntu Enterprise Cloud. 

Very simple question: is the administrator who is supposed to start dhcp manually?

---

### Post by kim0 on 2011-04-18
Hi,
Here are the steps for a correct package install: [https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)
However, as you noticed CDInstall is more streamlined and easier to debug

---

### Post by Rusty au Lait on 2011-04-18
I believe the answer to your question is yes. You will have to setup dhcp yourself. With the CD install you are prompted for dhcp information. When you apt-get the packages yourself you must do several setups yourself.

my 2¢
Follow Kim0's suggestion.

---

