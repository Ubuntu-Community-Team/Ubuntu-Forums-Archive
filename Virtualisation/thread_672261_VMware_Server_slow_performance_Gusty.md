---
title: "VMware Server slow performance Gusty"
date: 2008-01-19
forum: Virtualisation
---

### Post by zuan on 2008-01-19
Hi

I installed Vmware Server VMware Server 1.0.4 using apt-get on my notebook, but it realy slow it takes me almost 1 minutes to get the vmware server console to start and sometime it wont connect to localhost vmware-server

I try to install it on my PC that is much older specs than my notebook it worked flawlessly but i can't figure out what wrong with the installation on my notebook

both using gusty

PC = AMD Sempron 1.2GHZ / 1GB MEMORY
Notebook = Intel Centrino Duo Core 1.85GHZ / 1GB MEMORY (SMP kernel)

anyone know why this is happening? the vmware-server on my pc run faster then the one installed on my notebook

THKS

---

### Post by fjgaude on 2008-01-19
If you have setup VMware to use two cores of your CPU, go to only one. That is the issue with dual-core for this release.

Using only one core improves speed dramatically.

---

### Post by HermanAB on 2008-01-19
Always let VMware allocate the full disk image, turn off background snapshots and disable removable devices (CDROM/USB) since those are easy to enable again when needed. Then install VMware tools in the target.

With these changes, it should run at near native speed.

Cheers,

Herman

---

### Post by zuan on 2008-01-19
> **fjgaude said:**
> If you have setup VMware to use two cores of your CPU, go to only one. That is the issue with dual-core for this release.

Using only one core improves speed dramatically.

how do you do that? by setup vmware u mean use two cores virtual client configuration or the vmware-server daemon itself?

---

### Post by fjgaude on 2008-01-19
> **zuan said:**
> how do you do that? by setup vmware u mean use two cores virtual client configuration or the vmware-server daemon itself?

In the client. Load the client, get out of it, then in the VM Settings for client, Processors, there is a place for selecting one or two cores.

---

### Post by zuan on 2008-01-19
well the problem is even starting the vmware-server console is slow i didnt even started the client.

and also seem when ever i try to create a new virtual machine it will hang when creating the disk, the server console having dificulties connecting to the server.

Note:

I have to wait about 50-60 secs after i clicked the vmware-server console to show up
I have to wait 10-15 secs for the server console to connect to localhost :-/

i tried to install the one from .gz d/l from vmware but it have trouble compling the vmnet driver if none work will try Virtualbox 

I only need this to test my pfSense firewall rules set

Thanks

---

### Post by fjgaude on 2008-01-19
When you reinstalled vmware did you completely remove all aspects of it before trying to install? Any config file left ruins the new install.

---

### Post by zuan on 2008-01-19
1st installation is via apt-get
2nd installation via *.gz but never finish

---

### Post by fjgaude on 2008-01-19
It didn't finish, yes, but did you completely remove all items of the initial install?

You can tell, this is one way, in Synaptic, Search for vmware, then click on Status, then click on Not Installed (residual config), then click vmware For Complete Removal. That does it.

Now you can re-install using the downloaded binary.

---

### Post by zuan on 2008-01-21
already done that and reinstall but the same :-/

---

### Post by fjgaude on 2008-01-21
I can't think of anything else, except do a search for vmware items and delete them. Then try to install.

---

### Post by dancresswell on 2008-01-21
I also have slow VM's running under gutsy 7.10.  This is true for both an upgraded machine from edgy 7.04 and a new install on separate machines.  Configuring the VM to single or dual CPU does not make a difference.  This is a huge problem for myself, and it appears for others.  I've read something about it being an issue since the 2.6.20* kernel, but I'm not an expert there.  Regardless of the virtualized OS (windows, 'nix), its pretty much unusable.  I've gone back to 7.04 on my server and started using virtualbox on my laptop for now, although I'd prefer to use vmware as networking via virtualbox is a pain.

Cheers.

---

