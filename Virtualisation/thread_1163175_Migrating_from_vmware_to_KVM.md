---
title: "Migrating from vmware to KVM"
date: 2009-05-18
forum: Virtualisation
---

### Post by HDave on 2009-05-18
I have almost a dozen vmware machines I would like to convert to KVM.  I found some basic instructions on the KVM website [here]("http://www.linux-kvm.org/page/How_To_Migrate_From_Vmware_To_KVM") but they are so cryptic, I can't follow them!

If anyone has found a good way to do this in Jaunty, I'd appreciate getting some pointers.  Thanks!

---

### Post by Pnuts on 2009-05-18
what I did to get KVM working is as follows:

Clean install of 9.04 server
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install openssh-server
--
configure openssh with my laptops key so I do not need a password when connecting via ssh
--all remaining steps done on my laptop, server was moved and because headless at this point--

sudo apt-get install bridge-utils
sudo nano /etc/network/interfaces

changed from this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

to this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	network 192.168.1.1
	broadcast 192.168.1.255
	gateway 192.168.1.1
	bridge_ports eth0
	bridge_fd 9
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off
```

then restarted network services by restarting the server (because im doing this over ssh and I want to avoid issues)
sudo shutdown -r now

[COLOR="Red"]if working locally you could do this instead:
sudo /etc/init.d/networking restart[/COLOR]

then to finish up:

sudo apt-get install kvm libvirt-bin
sudo adduser $USER libvirtd [COLOR="red"]add yourself to libvirtd group to remotely connect as you in virt-manager[/COLOR]
sudo apt-get install python-virtinst

---everything is setup and installed now---
If you are going to use the bridge created above so each VM is directly on the network, you will have to create each guest from the cli. If the guest is ok on its own virtual network using NAT on the host (auto configured) then you can create the guests from virt-manager.

Either way you create it, you can then use virt-manager if you want. This is what I do as it has a nice overview of all of your guests and you can quickly access any of them if needed. I'm sure you can do this from the cli also, but I like the visuals here.

To create a guest from the cli run this command: notes in red

```
sudo virt-install -n name_of_guest \ [COLOR="red"]name seen in virt-manager under host[/COLOR]
-r 256 \ [COLOR="red"]amount of ram to assign to the guest[/COLOR]
-f location_to_save_guest.img \ [COLOR="red"]where to save the new guest[/COLOR]
-s 4 \ [COLOR="red"]size in Gb of new guest[/COLOR]
-c boot_cd.iso \ [COLOR="red"]location of cd iso for initial boot[/COLOR]
--accelerate \ [COLOR="red"]enable kernal acceleration[/COLOR]
--connect=qemu:///system \ [COLOR="red"]i believe needed for virt-manager, not sure[/COLOR]
--vnc \ [COLOR="red"]enables VNC, needed for virt-manager[/COLOR]
--noautoconsole \ [COLOR="red"]not to auto connect to console[/COLOR]
-v \[COLOR="red"]fully virtualized guest[/COLOR]
-smp 2 [COLOR="red"]set number of cpu's to use[/COLOR]

```

After this use another machine to connect with virt-manager.

Should be it.

-Pnuts

Edit: After typing the above, I realise this is not what you asked. I blame a late night and a killer headache this morning\afternoon. sorry

---

### Post by HDave on 2009-05-18
Thanks anyway.  I did have need some tips on bridged networked so that was heplful anyway.

In the meantime I found [this]("http://cauldrondevelopment.com/blog/2009/02/26/migrating-a-vmware-xp-install-to-kvm/") which I will try.

---

### Post by bodhi.zazen on 2009-05-19
You can convert your hard drives like this (it is a link to my blog) :

[http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/](http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/)

I blogged as I found a lack of a working step-by-step guide as well.

Once you have converted the HD, fire them up in KVM.

---

### Post by HDave on 2009-05-19
@bodhi.zazen -- My only regret in the thread is that Ubuntu took away the thank you feature of the forum because I'd like to hit the button about 300 times!

How is it I have used VMWare workstation for 2+ years and NEVER new about this utility.  Very cool...thanks.

---

### Post by HDave on 2009-05-20
I am getting the blue screen of death whenever I try to boot the Windows XP VMs.  Do I need to "repair" with the Windows XP install CD or is their something other method that is less destructive.

I have already tried the "-vga wmare" option...no effect.

---

### Post by veloce on 2009-05-21
> **HDave said:**
> I am getting the blue screen of death whenever I try to boot the Windows XP VMs.  Do I need to "repair" with the Windows XP install CD or is their something other method that is less destructive.

I have already tried the "-vga wmare" option...no effect.

Not sure if this is your problem, but while I was floundering around, before Bodhi pointed me to his blog, I stumbled upon a site that said you needed to do something to your windows machine (in vmware) before attempting to move it across.  Something to do with ide vs scsi virtual disks.  The solution was to run (well, get regedit to run) "mergeide.reg" which I think I found on the Microsoft site.

However, I think the error that that caused was a failure to boot, not a BSoD.

The other thing to try is to check that your virtual hardware is as similar to your vmware set up as possible.

---

### Post by David Cartwright on 2009-05-24
> **HDave said:**
> I have almost a dozen vmware machines I would like to convert to KVM.  I found some basic instructions on the KVM website [here]("http://www.linux-kvm.org/page/How_To_Migrate_From_Vmware_To_KVM") but they are so cryptic, I can't follow them!

Assuming your VMware Windows machines are on a Linux host, the following has worked for me (change VM name as appropriate).
*[And note you'll need lots of disk space, either on the server or network or external drive during the conversion processes. So make sure it is available before you begin the process!]*:

1.Make a backup of all the VMware Virtual Machine files in case you need to backout;

2.Remove VMware Tools;

3.Disable the screen saver;

4.Download mergeide.reg from: [http://www.proxmox.com/cms_proxmox/cms/upload/misc/mergeide.reg](http://www.proxmox.com/cms_proxmox/cms/upload/misc/mergeide.reg)

5.Install mergeide.reg;

6.Convert the original VMDK file to a growable VMDK file using the following as a template: (note: it is dash t space zero):
[INDENT]sudo vmware-vdiskmanager -r win2003.vmdk -t 0 win2003-grow.vmdk[/INDENT]

7.Convert the growable VMDK image in to a QEMU file using the following as a template:
[INDENT]sudo qemu-img convert -f vmdk win2003-grow.vmdk -O qcow2 win2003.img[/INDENT]

8.Follow the standard procedures to import QEMU image into Virtual Machine Manager or run from command line;

Let us know how you get on.

cheers .... david

---

### Post by HDave on 2009-05-26
@David Cartwright -- Thanks for the information...your steps worked extremely well.   Sorry for the delay in getting back to everyone, I had some strange problems happen and I was trying to figure out what was going on.

Sometimes when I booted my WinXP-SP3 machines they would not recognize the keyboard or mouse until they were rebooted a couple times.  Never got to the bottom of this.

Also, I discovered that you cannot use "-vga std" when first booting them because the boot process will hang.  Eventually I could fix it by hitting the F8 during boot to start windows in safe mode.  But ultimately I found it was easier to boot with the default vga adapter (cirrus) and then change to VGA later.

I also discovered that if you use "-vga std" Window will complain about not finding a proper driver...tell it to ignore the error and you will be fine.

Thanks again -- I am a happy(ier) man.

---

### Post by davidsf on 2009-06-05
I have followed the steps but I always have a BSOD with INACCESIBLE_BOOT_DEVICE 

I have changed the disk to scsi in libvirt xml (was a scsi disk in vmware) but same occurs. 

How do you import to libvirt?

Thanks

---

### Post by HDave on 2009-06-05
> **davidsf said:**
> I have followed the steps but I always have a BSOD with INACCESIBLE_BOOT_DEVICE

For me, the key to getting rid of this problem was to download and run the mergeide.reg (see above) registry disk repair tool right before shutting down the vm in vmware for the last time.  I also removed vmware tools ahead of time.  Could not get rid of BSOD without mergeide.reg.

I did find that booting with safe mode on the first boot also sometimes help.

---

### Post by veloce on 2009-06-07
> **davidsf said:**
> I have followed the steps but I always have a BSOD with INACCESIBLE_BOOT_DEVICE 

I have changed the disk to scsi in libvirt xml (was a scsi disk in vmware) but same occurs. 

How do you import to libvirt?

Thanks

I think you need to access the disk as ide not scsi.  I believe that is why you need to use mergeide in windows before converting the disk.

EDIT: Oops, sorry for repeating HDave's info - I didn't read all the new posts before replying.

---

