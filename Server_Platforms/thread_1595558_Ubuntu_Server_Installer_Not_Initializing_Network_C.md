---
title: "Ubuntu Server Installer Not Initializing Network Car"
date: 2010-10-13
forum: Server Platforms
---

### Post by ScottMorris on 2010-10-13
Hello all,

Sorry if this has already been posted :(  I have been searching for the last hr and a bit and came up with nothing on this issue, so here it goes.

I'm trying to setup a Node in an Ubuntu Enterprise Computing cloud.  The machine I'm using, an HP desktop, seems to have issues with its on board network card not being detected by Linux.  I then went out and grabbed a new network card that was PCI and installed it.

Now when I run the installer the light on my switch shows the card has connection to it (at a reduced speed however, 100 vs. 1000 Mbit/sec).  When the installer gets to the configuration of the network part it just fails to obtain an address.

I am using the same card model in the Cloud Controller, because I wanted Gigabit and not 100Mbit.  For that PC I just had to edit /etc/network/interfaces and append eth1 to the file to start it up.

The card I'm using is a ```
 Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10) 
``` and it is being seen by lspci.

My question is, is there a way to start this manually so the installer can have network access and properly configure the Node Controller from the Cloud Controller?

*Edit: I'm using Ubuntu Server 10.10*

Edit 2: The card shows connection to my switch but doesn't want to get a dhcp address, and the manual address doesn't want to work :(

Thanks in advance,

Scott

---

