---
title: "Ubuntu server and virtual box questions..."
date: 2013-07-11
forum: Virtualisation
---

### Post by Reduced_Oxygen on 2013-07-11
So I want to set up two virtual Windows XP systems and be able to VNC into them. I want to run these Virtual machines on ubuntu server (as I am familiar with ubuntu) how would I go about doing this?/Where should I look for answers?

---

### Post by Simon_WM on 2013-07-11
I would suggest that you download VirtualBox [https://www.virtualbox.org/](https://www.virtualbox.org/) or VMware Player [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/) and then create your virtual instances

---

### Post by SeijiSensei on 2013-07-11
I'd use VirtualBox and make sure to configure the virtual network interfaces in "bridged" mode.  That way they get addresses directly from your network's DHCP server and are visible to other machines on the local network.  In the default "NAT" mode you would have to tunnel incoming traffic through the host back to the guest.  In bridged mode, you should be able to see each machine with VNC.

I'd devote at least 512M to a Windows XP guest; 768M if you can afford it.  On an Ubuntu box with 2 GB of total memory, you'll have plenty of room for all of them.

Remember you'll need two legitimate Windows license keys to do this.

---

### Post by newbie-user on 2013-07-12
I have an Ubuntu 12.04 server running a headless VirtualBox. You can control your VMs via the command line, or your can use something like phpVirtualBox ([https://code.google.com/p/phpvirtualbox/](https://code.google.com/p/phpvirtualbox/))

To install headless Virtualbox after adding the repository:
```
sudo apt-get install virtualbox-[current version] --no-install-recommends
```

I've attached my notes on the install with phpVirtualBox

---

### Post by Hexxus on 2013-07-13
I've done quite a bit with virtulization so let me fill you in on a few different products and my experiences.


1. KVM - this is native in Ubuntu Server, by default its a CLI access only, which worked out well and I do recall there being an Ubuntu GUI client (its really basic though) and had no issues with it.There are web gui's out there. I've tried a few and found them super-clunky and buggy requiring me to send many emails for support to just get things working despite following the best practices created. I did however really like that it was Ubuntu underneath the hood running everything.

2. VMware, I run the full VMware ESXi hyper-visor at my data-center and generally speaking its "OK". Not the greatest but it gets the job
done. I don't like that the ESXi platform is a Windows only based GUI application and we've had our share of corrupt VMDK files. License expenses are extreme in my opinion but eh.

3. Virtualbox - I have not personally used it more then running it inside an operating system like Windows, it seemed to work pretty well. But
I cannot comment on anymore of it. I see alot of users on here using it without issues and seems to be highly recommended by some.

4. Xen-Server by Citrix. I run it at home and love it. Easy to install and use, can get a free-license for it. Does everything I would like and has
many of VMware licensed features in their free-license. Only qualm is that it too has a Windows only GUI.

---

### Post by CharlesA on 2013-07-13
You could use Vbox headless with phpvirtualbox, which is what I used for a long time before switching to KVM (Proxmox ftw).

Depending on the version of XP, you could just set the network adapter to bridged mode and remote desktop into the VM.

EDIT: @Hexxus: That has been my experience with KVM before I tried Proxmox. I like the Proxmox web interface way better than any of the other KVM interfaces I used previously. The only problem is it is not available for Ubuntu (Debian Only), but that's not a big deal for me.

---

### Post by HalfNote5 on 2013-07-18
If you're still looking for info, I thought I'd add my two cents - I just virtualized an old Feisty Fawn server for VirtualBox (which I can recommend from experience - especially with VNC (put the machine settings in Bridged mode, as SeijiSensei noted, and it works perfectly).

Credit where credit is due, I modified the process here: [http://blogs.technet.com/b/enterprise_admin/archive/2010/05/13/linux-p2v-with-dd-and-vhdtool-easy-and-cheap.aspx](http://blogs.technet.com/b/enterprise_admin/archive/2010/05/13/linux-p2v-with-dd-and-vhdtool-easy-and-cheap.aspx) 

And essentially, I grabbed the old machine's hard drive, and did the following (note I've grabbed the WHOLE HARD DRIVE and not just a partition of it) 

 dd if=/dev/sda of=/somepath/FeistyFawn.ddimg  

That's it.  Then (under Windows, but I'm betting the thing will work under WINE) use the VHD tool: [http://archive.msdn.microsoft.com/vhdtool](http://archive.msdn.microsoft.com/vhdtool)   (I have a backup of it here:  [http://zombie-process.com/winnet-bin/vhdtool.exe](http://zombie-process.com/winnet-bin/vhdtool.exe) )  as such:  C:\> vhdtool.exe C:\somepath\FeistyFawn.ddimg 

Then rename the thing: [*sudo wine]  C:\somepath> ren FeistyFawn.ddimg  FeistyFawn.vhd
*On Linux w/ wine. Remove brackets.

When it boots, it'll throw a fsck error, and you'll have to manually edit your fstab, because I guarantee it's not going to be happy about what's currently in there.

You'll want to run     vol_id -u /dev/sda1   (or whatever the main drive's device is) and find the UUID to replace the one that's in the fstab.  Also, if there's multiple hard drives that WERE in the old machine, but they're not (currently) present in the virtual environment (they can be virtualized and added later) then you'll want to comment them out for the time being. 

I HAVE found that leaving my cifs/samba shares in the fstab works like a charm! = )

Cheers!

-Duffy

P.S. You'll probably have to run sudo dpkg-*reconfigure* xserver-xorg   (or its equivalent, depending on your flavor of Linux, but as this IS the Ubuntu forum...) on older machines (Feisty in my case), because they will NOT like whatever vid card is emulated by VBox. Also, I enabled I/O APIC, set the chipset it ICH9, and movd the vhd file tot he "IDE" devices column, rather than the "SATA" as Feisty was throwing a bit of a fit. Should not be a problem on newer versions.)

---

