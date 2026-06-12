---
title: "Oracle Virtual Box install USB device recognition problems"
date: 2014-07-24
forum: Virtualisation
---

### Post by Flaggmann on 2014-07-24
I have installed Oracle VirtualBox, from built in synaptic repos, on (ubuntu 12.04, mint 16 & 17, debian 7.5) including guest options package as well as extensions addition to allow use of USB 2.0. I have created a filter for each device that shows up on the host's lsusb listing plus 1 extra blank filter for any other devices that aren't now attached.  I have also added my userID to the vboxusers group. Current Host ubuntu 12.04 LTS and guest is Win XP pro SP 3. Acer Aspire 2GB RAM 64 bit

Virtual box settings shows usb-wireless kybd-mouse, smartphone, ATI USB 600 TV tuner card, generic webcam, all are recognized as devices, however the TV tuner card is listed as a webcam rather than a tuner card and thus is not recognized by catalyst media software installed in the guest. The smartphone is recognized when using it in the desktop/link update mode, however if it is configured as a storage device on using it's added SD card it is not recognized.

No thumb drive storage devices are recognized at all. The bidirectional copy/paste and drag n drop do not appear to work properly either. One can get files back and forth to a thumb drive but have to set up a shared folder from inside the guest that is a shared folder on the host, then go to the host and copy the files from that shared folder to a thumb drive etc.

I have noticed in the google research that this appears to have been a problem for a while without a fix. Any help would be appreciated.

Thanks
Flagg

---

### Post by Flaggmann on 2014-07-24
one would think wih the same trbls in so many flavors of the *nix world the original authors of virtualbox would either post a fix or else pass the whole project off the way they did for open office; does anyone have it working properly with USB devices??

---

### Post by TheFu on 2014-07-25
The original authors? Really?  That was 3 companies ago and most definitely **NOT Oracle.**

Getting Oracle to release open office was not easy and it has fragmented the open/libre-office communities.

---

### Post by Flaggmann on 2014-07-26
> **TheFu said:**
> The original authors? Really?  That was 3 companies ago and most definitely **NOT Oracle.**

Getting Oracle to release open office was not easy and it has fragmented the open/libre-office communities.

I hear you it was just a suggestion.

Further investigation on the initial problem seems to point to a problem with the deb/mint/ubuntu OS kernels rather than virtualbox as the "usbviewer" program does not work either.
It generates an error; 

Can not open the file /sys/kernel/debug/usb/devices
 Verify that you have USB compiled into your kernel, 
 have the USB core modules loaded, and have the 
 usbdevfs filesystem mounted.

adding the required lines to the /etc/fstab to mount the usbfs or usbdevfs does not work as mount destinations (/proc/bus/usb) don't exist and system does not allow root to create them either.
further checks seems to show that the usbfs modules are not built into the default installed kernels and thus a kernel compile appears to be needed. I have never had to do one and am not aware of a straightforward
tutorial to do same at this point either. 

My suspicion is that if I can get "usbviewer" to work that virtualbox will like do so also, hopefully. It appears newer versions of linux OS's are using a different usbfs mount point and older apps like virtualbox still looking for /proc/bus/usb for needed info

If you have any more useful tips or links to help alleviate this problem for me I would appreciate it thanks

---

### Post by sudodus on 2014-07-26
[KVM and virt-manager]("https://help.ubuntu.com/community/KVM/Installation") are part of linux, and work without issues with USB. It is also possible to boot from USB, which is not possible in virtualbox, even if it works to read and write data to and from USB mass storage devices.

-o-

My work-around with virtualbox is, that after every kernel update in the host system, I remove virtualbox and reinstall it.

---

### Post by TheFu on 2014-07-26
+1 for KVM.  Switched about 2 yrs ago from Xen and ESXi (on servers) and virtualbox on desktop and have been extremely pleased with the results.  **KVM+virt-manager completely rock.**  I'd been running Xen and ESXi for a few yrs prior to that, so it wasn't a quick decision and I ran KVM for over 6 months in test before making the jump.

Occasionally I still run VirtualBox on a Windows host ... for demo purposes.  The last time I tried it on an Ubuntu host was long ago and it locked up the entire system - not just the guestOS but the hostOS too.  That same physical system has been running KVM-based VMs for years now, trouble free.

Wish I could help get your vbox stuff working better.  I suspect the USB part of VBox is not F/LOSS, therefore not included in the GPL release.  Others here usually would chime in to tell you to remove the Canonical version, add the Oracle PPA and install it that way.

The only people I'd recommend stay using VirtualBox over KVM are those with better performing (non-gaming) graphics needs. If you want gaming to work better inside a VM - Xen with a dedicated (specific model) ATI GPU in passthru mode seems to be the ticket.

I've you'd like a reasonably gentle intro to KVM+virt-manager, let us know. I've given a presentation on that a few times now - not as much as my virtualbox performance tuning presentation, but still it is helpful.

---

### Post by Flaggmann on 2014-08-02
Thanks for tips and offer; I tried it and attempted to conver all my old VirtBox HD's to vdmk, vdi and RAW and then tried importing them into kvm but it didn't work so it looks like I will have to reinstall windoze from the dvd's again using virt manager kvm. I hv original disk, SP3 so at least that much is saved but the !GB subsequent updates is a problem as wireless ISP in rural area don't have "urban unlimited data caps" so it gets expensive to just re-install without first trying imports etc.

---

### Post by SeijiSensei on 2014-08-02
> **sudodus said:**
> My work-around with virtualbox is, that after every kernel update in the host system, I remove virtualbox and reinstall it.

You don't need to do that if you install VirtualBox from the Oracle repositories as described on the virtualbox.org site.  When my kernels are updated, dkms kicks in and rebuilds the kernel module automatically.

---

### Post by sudodus on 2014-08-02
> > **sudodus said:**
> My work-around with virtualbox is, that after  every kernel update in the host system, I remove virtualbox and  reinstall it.

You don't need to do that if you install VirtualBox from the Oracle  repositories as described on the virtualbox.org site.  When my kernels  are updated, dkms kicks in and rebuilds the kernel module automatically.

Thank you! I'll try that when I settle for 14.04.1 LTS as my production system.

---

### Post by piscvau on 2015-02-08
Hello,
I am reopening this thread because I am unable to see any USB device in my virtual machine. My configuration is :
Oracle virtual box version version 4.3.20 r96996; my Host system is Xubuntu 14.04; my guest system windows XP 32 bits Service Pack 3. My PC is a GigabyteP27 (CPU is an Intel[SUP]®[/SUP] Core™ i7 with a graphics chipset  NVIDIA[SUP]®[/SUP] GeForce[SUP]®[/SUP] GTX 765M GDDR5 2Go).

I have installed the extension for USB 2.0 . I have installed the invited addons in the guest system. I am a member ot the vboxusers group. The virtual machine is configured with the USB 2.0 device and I have added an empty filter. 
When I inserta USB key of 4GO in my USB 2.0 port (I also have USB 3.0 ports on this PC), it is automatically mounted in the Xubuntu system. But is does not show in the virtualbox. In the menu USB devices I always have "no USB device connected". I have tried another USB devices a Serial to USB converter from Prolific. Does not show either in the virtual box.

I have installed this same configuration on the same Hardware last t week and after several hours of trying, the virtual box finally showed the USB key. I did not understand what made it work. I have spent the whole afternoon trying to get it to work on this other PC without success. I have tried to uninstall and reinsthall the invited extensions but it does not help. 

I have seen many posts on several forums reporting USB detection problems in the virtual box but no clear answer about what needs to be done. I have tried to introduce the USB device before starting the virtual machine and after. Does not seem to make any difference.

I have seen several posts mentioning that KVM works better but I do not know if I can switch to it:
 My PC CPU is an Intel[SUP]®[/SUP] Core™ i7 with a graphics chipset  NVIDIA[SUP]®[/SUP] GeForce[SUP]®[/SUP] GTX 765M GDDR5 2Go. 
My functional requirements are:  a windows virtual machine which can communicate easily with my host ubuntu (this is why I would not like a dual boot). The windows virtual machine needs to work with several types of USB devices (scanner, USB to serial converter, a Hiface device) and run several programs on Windows including foobar2000, Design a Knit, microsoft Visio 2003. The windows virtual machine needs also to have a netwok capability to communicate with a NAS.

Any help would be very welcomed.
piscvau

---

### Post by sudodus on 2015-02-09
My experience of KVM + virtmanager is rather limited, but quite positive. I run it in a Toshiba laptop with an Intel i5 processor and it works quite well to use the processor and communication (ethernet, USB, monitor ...). I read the following wiki page and what I found ***via simple searches of the internet*** to learn how to use it

[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

---

