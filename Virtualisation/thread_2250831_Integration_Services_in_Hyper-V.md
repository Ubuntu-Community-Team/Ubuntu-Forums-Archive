---
title: "Integration Services in Hyper-V"
date: 2014-10-31
forum: Virtualisation
---

### Post by sam99 on 2014-10-31
I migrated a Ubuntu Server VM from VMware to Hyper-V and upgraded to 14.10. I am having problems getting Hyper-V Integration Services running. Here are some things I have done:


Add the following to /etc/initramfs-tools/modules -
hv_vmbus 
hv_storvsc 
hv_blkvsc 
hv_netvsc


Running lsmod shows the correct items (hid_hyperv, hv_netvsc, hv_utils, hv_storvc and hv_vmbus)


I have ran sudo apt-get install hv-kvp-daemon-init, but it appears that has been deprecated and replaced with Linux-cloud-tools-generic which I have run.
I have also installed linux-cloud-tools-common and linux-cloud-tools-virtual.


Hyper-V is still showing no Integration Services are running and our backup is failing with error to check Integration Services are installed.


I am having a difficult time finding any other sites that could help. Any suggestions would be great.

---

### Post by bashiergui on 2014-11-08
According to [this]("http://technet.microsoft.com/en-us/library/dn531029.aspx") Ubuntu comes prepackaged with LIS which means you cannot install Microsoft's iso of LIS. The link provided tells you what functionalities are available on an ubuntu guest in hyper-v. Is what you're trying to do listed as possible? (I was too lazy to go through it myself ;))

You might find support on Microsoft's forums. 

Unrelated: what made you choose hyper-v?

---

### Post by sam99 on 2014-11-10
True it does come with it installed, but it has to be manually activated. [These are the instructions I followed]("http://www.serverwatch.com/server-tutorials/installing-and-activating-hyper-v-linux-integration-services.html").

The reason for moving was purely a financial decision. There is an annual cost for vCenter where Hyper-V has none. Along with that, Hyper-V 2012 does everything we need it to do (except run Linux apparently :shock:)

---

