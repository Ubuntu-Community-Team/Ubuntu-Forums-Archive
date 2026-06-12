---
title: "VMWare Tools - Do I Need Them?"
date: 2010-04-01
forum: Virtualisation
---

### Post by Thund3rstruck on 2010-04-01
Hi,

I'm running VMWare Server v2.0.2 on Ubuntu Server 9.10 and I just created a Ubuntu 9.10 guest. I can't figure out how to install vmware-tools or if I even need it. This guest is a terminal only server that is going to host apache-svn. 

When I click 'Install VMWare Tools' in the web app, it reports that VMWare tools is mounted on the guest but when I navigate to /media/cdrom, there is nothing there. 

Not sure what to do now.

---

### Post by Thund3rstruck on 2010-04-01
Ok, I had to manually mount the cdrom drive and I was able to install VMWare tools. I don't see any difference in the font or anything else in the terminal so I still don't know if it did actually anything. At least VMWare doesn't keep warning me that VMWare tools isn't installed.

---

### Post by bhaverkamp on 2010-04-01
Biggest reason for installing tools is to improve the network and video performance of your VM. The virtual drivers pass data to/from the hardware more efficiently than the emulation of the physical hardware that would other wise happen. Also there is a good chance that you have at least some tools bundled with your OS. I noticed this for the Lucid beta, it has the drivers for the virtual hardware builtin.

---

### Post by dcstar on 2010-04-03
> **Thund3rstruck said:**
> Ok, I had to manually mount the cdrom drive and I was able to install VMWare tools. I don't see any difference in the font or anything else in the terminal so I still don't know if it did actually anything. At least VMWare doesn't keep warning me that VMWare tools isn't installed.

And of course you have followed the instructions to run the **vmware-toolbox** command when you log into your VM, haven't you?

---

### Post by Thund3rstruck on 2010-04-12
> **dcstar said:**
> And of course you have followed the instructions to run the **vmware-toolbox** command when you log into your VM, haven't you?

Actually I just gave up on it and downloaded a Ubuntu VM appliance with everything already installed. I could not get VMWare-Tools (the config script) to successfully patch the kernel for any of the distributions I tried (Ubuntu 9.10, Fedora 12, etc) other than Red Hat Enterprise 5.3 and I just got tired to fooling around with it. 

Clearly, Ubuntu, Fedora, and the other distributions are not designed to be virtualized in VMWare.

---

### Post by dcstar on 2010-04-17
> **Thund3rstruck said:**
> 
.........
Clearly, Ubuntu, Fedora, and the other distributions are not designed to be virtualized in VMWare.

Funny how I have a pile of Ubuntu (and other Linux) VMs that originally ran ok in VMware Server, and now run quite successfully in VMware Player 3.1, isn't it?

All have VMware Tools installed.

---

### Post by meskes on 2010-04-28
If you'd like to have the advanced features, like Unity, mouse integration, common clipboard etc, yes.

---

### Post by LebLinux on 2010-04-29
Guys, I have installed vmware-tools and the vmxnet module is installed too but when I do the ifconfig -a it only shows eth0 and lo doesn't show the other vmware networks any ideas please? I need to pinpoint the virtual eth0 to another network card on windows host machine(Bridging). I am using ubuntu server 9.10 as a guest.

---

### Post by bhaverkamp on 2010-04-29
> **LebLinux said:**
> Guys, I have installed vmware-tools and the vmxnet module is installed too but when I do the ifconfig -a it only shows eth0 and lo doesn't show the other vmware networks any ideas please? I need to pinpoint the virtual eth0 to another network card on windows host machine(Bridging). I am using ubuntu server 9.10 as a guest.

I am assuming you did the ifconfig on the guest. Yes, you will only see the eth0 device. To see the other networks you must create additional NICs for your VM on workstation (or whatever your using). WHen you create the additional NICs you are offer'd an opportunity to connect them to whatever networks you like. ONly the host will show all the networks by default.

---

### Post by LebLinux on 2010-04-30
> **bhaverkamp said:**
> I am assuming you did the ifconfig on the guest. Yes, you will only see the eth0 device. To see the other networks you must create additional NICs for your VM on workstation (or whatever your using). WHen you create the additional NICs you are offer'd an opportunity to connect them to whatever networks you like. ONly the host will show all the networks by default.

So bottom line I need to add another NIC for ubuntu server guest? and Add virtual network on the host (windows server)?

---

