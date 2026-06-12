---
title: "Ubuntu Server 14.04.2 LTS - Hyper-V 2012R2, UEFI + encyrption not booting up"
date: 2015-07-27
forum: Server Platforms
---

### Post by Codera on 2015-07-27
Hello!

I have a Hyper-V 2012R2 server, where i wanted to deploy a VM with Ubuntu server.
I download the latest version of Ubuntu Server 14.04.2 LTS. 

Following this guide ([http://uglyvpn.com/2015/03/12/install-owncloud-on-ubuntu-4-10-using-hyper-v-pt-1/](http://uglyvpn.com/2015/03/12/install-owncloud-on-ubuntu-4-10-using-hyper-v-pt-1/)) i created Gen2 VM.
From the same guide ([http://uglyvpn.com/2015/03/13/how-to-install-owncloud-on-ubuntu-4-10-using-hyper-v-part-2-of-tbd/](http://uglyvpn.com/2015/03/13/how-to-install-owncloud-on-ubuntu-4-10-using-hyper-v-part-2-of-tbd/)) i set it up with "Guided - use entire disk ant set up encrypted LVM"
The installation went fine, but after reboot it says loadin essential drivers, running scirpt, mouting root file system and for the last thing it asks "Enter passphrase". I try to type it, but nothing happens.
If i do a reset only black screen is shown, for one second grub loader is displayd also. 

After startup, i can press "e", but really do not know what to change? :) With using "c" i tried advanced options, selected "Ubuntu, with Linux 3.16.0.30-generic", but then it is stuck in "Loading initial ramdisk"


Is this kind of como Gen2 UEFI VM + encryption mission impossible? :)
Has anybody tried to get it to work?

On the VM Secure boot is disabled.

---

### Post by PaulW2U on 2015-07-27
*Thread moved to **Server Platforms**.*

---

