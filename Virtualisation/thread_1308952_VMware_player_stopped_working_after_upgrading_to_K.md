---
title: "VMware player stopped working after upgrading to Karmic"
date: 2009-11-01
forum: Virtualisation
---

### Post by Rustin Jowe on 2009-11-01
Hello,
    I am new to ubuntu, so I am sorry if this seems rudimentary. I have been running VMware player, but when I up graded to ubuntu 9.1, it stopped working.  When I try to open the player, I get a message saying that several modules need to compiled and loaded into the running kernel. When I click "install," I get the following error:

Unable to build kernel module.

See log file /tmp/vmware-root/setup-15614.log for details.

I have tried looking at the log file, but it does not seem to exist.  

Do you have any suggestions on how I can get the player to work again?
thanks in advance

---

### Post by Rustin Jowe on 2009-11-01
I uninstalled the program, downloaded version 3.0.0, and it installed and worked without any problems.

---

### Post by agurk on 2009-11-01
Same problem here. Got a link to that 3.0 version?

---

### Post by philphys on 2009-11-02
Thanks, that fixed my problem.

To get vmplayer 3.0, just head to VMware's homepage here: [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

You'll need to register to be able to download it.

---

### Post by fjgaude on 2009-11-02
Crazy, but **vmware player 3.0**, from the vmware.com download site, works perfectly with Ubuntu 9.10.

I downloaded the latest vmware servers, 1.0.10 and 2.0.2, and they both gave CRC errors on trying to extract them. I feel that both of these likely have the same update code installed within them to run 9.10 without issue. But, why the CRC error? Can't say. Does anyone know what is going on here?

And I noticed with player 3.0 you can create VMs... I think this may be a new thing for players, eh?

---

### Post by LFS-Nr-3305 on 2009-11-02
> **fjgaude said:**
> Crazy, but **vmware player 3.0**, from the vmware.com download site, works perfectly with Ubuntu 9.10.

And I noticed with player 3.0 you can create VMs... I think this may be a new thing for players, eh?

Indeed ... from "Getting Started":

                                                                                                            1
What Is VMware Player?
  VMware Player is a desktop application that lets you create, configure, and run virtual machines.
  With VMware Player you can use the following features:
      Create virtual machines that can run on a Windows or Linux PC.
  n
      Run virtual machines, making it easy to take advantage of the security, flexibility, and portability of virtual
  n
      machines.

---

### Post by LFS-Nr-3305 on 2009-11-03
I just installed it into my Ubuntu 9.10 "Karmic Koala". It de-installed the old version 2.5 and the installation of Version 3 run within a few minutes. It showed my old VMX as usual and downloaded VMWare tools. Shortly after, I could enable the Shared Folders, and the mouse was not restricted to the VMWare window - everything as usual, but now there is the Menu for "Create a new Virtual Machine" :-).

I do not remember what showed up in version 2.5 when clicking on Help - About VMWare but now it shows, among else, the location of the virtual machine I'm running, a nice feature because normally I only click on it, had forgotten since long where is it's physical locatin (partition and directory) :-).

---

### Post by fjgaude on 2009-11-03
Yes, vmware player, version 3.0, is a gem! Thanks for letting us know of the upgrade, the changes.

I think the code in 3.0 understands what has been happening in the latest kernels and takes care of them with grace.

Today will try again, because the early version of vmware server 1.0.10 were broken, the new download of 1.0.10 server with kernel 2.6.31-14. Keeping my fingers crossed.

---

