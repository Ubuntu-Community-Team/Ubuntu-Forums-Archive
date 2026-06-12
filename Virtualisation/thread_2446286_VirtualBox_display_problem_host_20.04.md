---
title: "VirtualBox display problem: host 20.04"
date: 2020-06-27
forum: Virtualisation
---

### Post by zbigiman on 2020-06-27
Hi,
I've just installed Virtualbox 6.1 - Version 6.1.10 r138449 (Qt5.12.8) - on Ubuntu 20.04 LTS and it works very slow. The Virtualbox interface is laggy, f.g. when I uncheck some checkbox in the setting it doesn't change, etc. It works very slow and laggy before running a virtual machine. There is some problem with screen refreshing, see screenshots, links below:

[https://u.pcloud.link/publink/show?code=XZsKjIkZtKoTsgLmrEF7336ojqh7U55S51gk](https://u.pcloud.link/publink/show?code=XZsKjIkZtKoTsgLmrEF7336ojqh7U55S51gk)
[https://u.pcloud.link/publink/show?code=XZLljIkZ3T790Syvvbj9gn5z40WcAJVIw79V](https://u.pcloud.link/publink/show?code=XZLljIkZ3T790Syvvbj9gn5z40WcAJVIw79V)

I was using Virtualbox on older ubuntu based distros and the interface was always smooth. Any ideas what's going on?

---

### Post by ajgreeny on 2020-06-27
Post moved to its own new thread.

---

### Post by ajgreeny on 2020-06-29
What is your host hardware?
This looks rather like a problem stemming from that rather than the guest.

Do you use the guest-additions of the same version as your Vbox, and have you installed them in the XP guest.
I still have, but do not use a VM of WinXP, mine having 2G ram compared to your 512MB, though I don't  think that is your problem as it is the Vbox window display as well as the guest  causing problems.

Perhaps it's  worth trying using Vbox version 6.0 in place of 6.1 as some users have had much greater success with that earlier and still fully supported version.

---

### Post by zbigiman on 2020-06-29
[COLOR=#1C1E21][FONT=Helvetica]My host hardware is:
[/FONT][/COLOR][COLOR=#1C1E21][FONT=Helvetica][FONT=inherit]Processor: Intel® Core&#8482; i5-7200U CPU @ 2.50GHz × 4[/FONT]
[FONT=inherit]Graphics: Mesa Intel® HD Graphics 620 (KBL GT2)[/FONT]
[FONT=inherit]Ram: 7,5 GiB[/FONT][/FONT][/COLOR][COLOR=#1C1E21][FONT=Helvetica][FONT=inherit]

[FONT=inherit]It should be enough, I was using Virtualbox on worse configurations.[/FONT][/FONT][/FONT][/COLOR][COLOR=#1C1E21][FONT=Helvetica]

Finally I've installed Gnome Boxes and everything works perfectly, so I don't know what had happened with Virtualbox on Ubuntu 20.04.

Update:
My kernel is:
[/FONT][/COLOR]5.4.0-39-generic

What more information do You need?

---

### Post by ajgreeny on 2020-06-29
I will admit to not knowing of gnome-boxes, and I don't know if it's needed on a gnome host (I use Xubuntu), but if you are now happy and the problem is solved please mark SOLVED using **Thread Tools** menu at the top of this thread

---

### Post by kneutron on 2020-06-30
--Could be your video driver. Post results of ' lspci '

---

### Post by monkeybrain20122 on 2020-06-30
What if you change graphic controller in Settings > Display to VBoxSVGA?

---

### Post by zbigiman on 2020-07-01
Here is lspci output

lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point LPC Controller/eSPI Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

---

### Post by ajgreeny on 2020-07-01
OK. Now let's see the output of ***lspci -ks 00.02.0***

That will show us the driver in use.  It may not help, but all info is usually of use in some way..

---

### Post by zbigiman on 2020-07-01
I've recorded video, to show how the bug with VirtualBox display looks like. It's fresh instalation of VirtualBox:
[https://u.pcloud.link/publink/show?code=XZ41NIkZHmcKSwhdlB5SVPAosjSCOYonLeck](https://u.pcloud.link/publink/show?code=XZ41NIkZHmcKSwhdlB5SVPAosjSCOYonLeck)
It happens only in VirtualBox. All other applications works fine.

---

### Post by monkeybrain20122 on 2020-07-01
Did you try changing display driver like I said above?

---

### Post by ajgreeny on 2020-07-01
Am I right in thinking that it is the VBox window itself that does not display correctly, not the running VM?

---

### Post by SeijiSensei on 2020-07-01
In my 20.04 installation, using the VBoxSVGA driver produces an "Invalid Settings" error. However it is the only driver that works properly for me. I ignore the error and get a lovely 16:9 image that fills my display in fullscreen mode. So if you get the "Invalid Settings" error, just ignore it and use the SVGA driver.  In the VB manager, adjust Settings > Display > Graphics Controller for the guest.

I'm running the newly-released 20.04 version of VB, 6.1.10 r138449 (Qt5.12.8).  However, I was running the 19.10 version until fairly recently and got the same error.

---

### Post by monkeybrain20122 on 2020-07-01
> **SeijiSensei said:**
> In my 20.04 installation, using the VBoxSVGA driver produces an "Invalid Settings" error. However it is the only driver that works properly for me. I ignore the error and get a lovely 16:9 image that fills my display in fullscreen mode. So if you get the "Invalid Settings" error, just ignore it and use the SVGA driver.  In the VB manager, adjust Settings > Display > Graphics Controller for the guest.


I got invalid settings error but reinstalling guest additions fixed it.

---

### Post by zbigiman on 2020-07-02
Here is the output for lspci -ks 00:02.0 :
 
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
    DeviceName:  Onboard IGD
    Subsystem: Dell HD Graphics 620
    Kernel driver in use: i915
    Kernel modules: i915

---

### Post by zbigiman on 2020-07-02
> **ajgreeny said:**
> Am I right in thinking that it is the VBox window itself that does not display correctly, not the running VM?
Yes, the problem is with VirtualBox window. It's buggy from the beggining, before install and run any VM.
I've posted the video how the fresh install of VirtualBox looks like, here is the link: [https://u.pcloud.link/publink/show?code=XZ41NIkZHmcKSwhdlB5SVPAosjSCOYonLeck](https://u.pcloud.link/publink/show?code=XZ41NIkZHmcKSwhdlB5SVPAosjSCOYonLeck)
All other apps works fine, so it's very strange issue...

---

### Post by ajgreeny on 2020-07-02
Well at least that means we can forget about problems with your choice of the Graphics Controller in VMs as it seems to be the graphics of the host causing the display problem of the VBox window.

Normally, Intel integrated graphics are very well supported in Ubuntu and Linux in general so I'm not quite sure what to suggest here, and I'm certainly no expert when it comes to display problems.

I hope I haven't missed this detail somewhere in the thread, but are you using an xorg or a wayland graphics session?  You make the choice of this at the login screen, so check that out and let us know which you use now, and then try logging in using the alternative graphics session.

---

