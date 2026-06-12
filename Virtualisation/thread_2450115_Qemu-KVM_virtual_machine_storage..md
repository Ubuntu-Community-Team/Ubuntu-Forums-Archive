---
title: "Qemu-KVM virtual machine storage."
date: 2020-09-07
forum: Virtualisation
---

### Post by ajgreeny on 2020-09-07
I have just installed qemu-kvm as a trial so that I can compare it with VBox which I use quite a lot to test other distros and new *ubuntu versions.

All was OK until I created a VM of Linux-Mint-20 using virt-manager, then noticed that the VMs it creates are placed in /var/lib/libvirt meaning that my root partition was immediately filled to 98%, so that's a non-starter for me.

I managed to remove the VM to release space in the root partition, though I had to do it manually after uninstalling the whole shooting match of qemu-kvm and rebooting.

Do the VMs have to be in the root partition or can they be placed in a folder in my home, which in my case is a separate partition with masses of space?

---

### Post by QIII on 2020-09-07
I put mine either on different devices or even on servers.  You can choose where to put them.

Give me an hour or two to finish what I am doing out in the blazing sun (not fun, just came in for a cold sparking water and a break) and I'll see if I can find some nice instructions.

---

### Post by Dennis N on 2020-09-07
You can put the VM virtual disks where you want. In step 4 of 5, choose "select or create custom storage" then the Manage button. In the next window "Choose Storage Volume" you can add a location for virtual disks with the buttons in lower left. See 2nd screen shot. The contents of that location (if any) appear in the right window. Create a new storage disk for the new VM with the + button above that window. The name of the VM disk file should end with .qcow2. Then choose it and continue.

---

### Post by TheFu on 2020-09-07
libvirt allows about 20 different "backend storage" options. These can range from using any file system you like for storage, to using NFS, to LVM LVs, or ZFS zpools, to using many distributed file systems like CEPH or Sheepdog spread across many other systems.  You have the choice.

So, each has slightly different instructions, but always remember, this is a server tool, not an end user tool.  Storage for VMs, if you just want to use file-based storage on a file system can be located anywhere, but really a HOME directory is a poor choice.  If you have a separate file system for /home/, then you can create a new directory, perhaps /home/VMs/ to hold the VM storage stuff.  Then, inside virt-manager, just add that area as a file-system/directory storage pool.  Or you might want to mount added storage directly to /var/lib/libvirt . I've done that a few times, just to make trivial play VMs have a place to use.
```
$ df -Th
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   22G   12G  9.4G  56% /
/dev/sdb1                         ext2  720M  207M  477M  31% /boot
**/dev/mapper/hadar--vg-libvirt--lv ext4  197G  104G   84G  56% /var/lib/libvirt**
/dev/mapper/vg--hadar-lv--backups ext4  459G  424G   36G  93% /Backups
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd
lxd/containers/pihole             zfs    13G  657M   12G   6% /var/lib/lxd/storage-pools/lxd/containers/pihole

```
That is all the real mounted storage on the system.

For the best performance on a single machine, using a block storage provider like LVM or ZFS will integrate into the libvirt tools.  These are both supported, LVs get created and destroyed as controlled by the virt-manager, once you setup an LVM VG to be used in the GUI.
```
$ sudo lvs
  LV                VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv        hadar-vg -wi-ao---- 200.00g                                                    
  lv-blog44-1604    hadar-vg -wi-ao----  16.20g                    /dev/mapper/hadar--vg-libvirt--lv ext4  197G  104G   84G  56% /var/lib/libvirt                                
  lv-lubuntu11-1604 hadar-vg -wi-a-----  31.00g                                                    
  lv-opnsense       hadar-vg -wi-a-----   5.00g                                                    
  lv-regulus        hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2      hadar-vg -wi-ao----  10.00g                                                    
  lv-spam3          hadar-vg -wi-ao----  10.00g                                                    
  lv-tp-lxd         hadar-vg twi-a-tz--  32.23g             0.00   10.06                           
  lv-u20.04-srv     hadar-vg -wi-a-----  10.00g                                                    
  lv-vpn09-1604     hadar-vg -wi-ao----   7.50g                                                    
  lv-xen41-1604     hadar-vg -wi-ao----  12.50g                                                    
  lv-zcs45-1604     hadar-vg -wi-ao----  25.00g                                                    
  lxd-lv            hadar-vg -wi-ao----  60.00g                                                    
  root              hadar-vg -wi-ao----  22.33g                                                    
  swap_1            hadar-vg -wi-ao----   4.25g
```
Most of those are LVs provided to VMs, controlled by libvirt using KVM as the hypervisor.  Plus, we can create a snapshot of a running VM, mount it and take 100% quiesced backups from the host machine.  If you use file-based storage for VMs, that isn't possible, though qcow2 does support a "snapshot-like" capability, it isn't for backups.  Warning - don't use qcow2 on BTRFS file systems that have CoW enabled.  

The LVs used directly for VM storage above don't get mounted on the hostOS, only inside each VM.  You can see I'm not 100% consistent with my naming.  Oh well.

You can also see that regulus ran out of storage, so I added some more.  That was accomplished without rebooting either the host or the VM. I posted the commands in these forums 1-3 months ago.  LVM is pretty amazing.

You can always use symlinks to redirect storage to another file system as well. I've done that a few times.  On a different machine, 
```
root@romulus:/raid/media/VMs/VMs# ls
blog.qcow2                        ubudesk.img
vpn-1604.qcow2
nextcloud.qcow2                   vpn-1604.qcow2-2018.01.27.bak
ntp.qcow2                         xen41.img
redmine.img                       xen51-README-Backup_Method.txt
spam2.img                         zcs43.img
spam2.qcow2                       zcs43-u10.04.img

```
Inside each xml file which holds the VM definition for that specific machine, the full path or connection method are stored. If you need to move stuff from /var/lib/libvirt to somewhere else, you can use **virsh edit {name of VM}**, and that will use your default EDITOR to modify the settings.  No need to run as root, just need for the userid to be in the libvirtd gid.  Further, since remote management is built into libvirt, this works from other systems that have ssh access.  Just setup an **qemu+ssh://thefu@romulus/system** connection. I have 4 VM hosts at home, but can create, install, manage, shutdown each from any other workstation that has ssh connectivity to the host.

One last thing.  The default networking created by libvirt is only NAT.  If you want bridged networking, then you'll need to set that up.  For servers, that's pretty much mandatory.

Clear as mud?

---

### Post by QIII on 2020-09-07
Thanks for helping ajgreeny out, folks!  I had to leave him hanging to run out and melt in the sun this afternoon.

---

### Post by ajgreeny on 2020-09-08
QIII, I hope you are now out of the blazing sun and happy again but thanks to all of you for the guiding comments..

I found a Web at [https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/](https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/) which seems to say what you've  all said, as far as I can make out anyway, so I'll  be starting again this evening when time al&#314;ows, but even though using LVM may be a worthwhile way to go eventually, I will avoid  adding that extra complication at the moment; LVM is more of a mystery to me at present than KVM.

Wish me luck; I'll keep in touch and tell all the details later.

---

### Post by TheFu on 2020-09-08
> **ajgreeny said:**
>  
I found a Web at [https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/](https://www.linux.com/audience/devops/creating-virtual-machines-kvm-part-1/) which seems to say what you've  all said, as far as I can make out anyway, so I'll  be starting again this evening when time al&#314;ows, but even though using LVM may be a worthwhile way to go eventually, I will avoid  adding that extra complication at the moment; LVM is more of a mystery to me at present than KVM.

Wish me luck; I'll keep in touch and tell all the details later.

I used raw images for years because the new-fangled vdi/qcow files where significantly slower.  Fixing storage performance later is one of the harder things to correct, though not really THAT hard if you have downtime allowed.  If SSD storage is used, the worse performance just doesn't matter.

The whole type-1 vs type-2 is marketing. Because VMware puts that you cannot post unapproved performance results into their license agreements, nobody does.  Real world testing on the same hardware between Xen, KVM and ESXi ... let's just say, KVM is fastest and most convenient. VMware ESXi is very picky about hardware. 3/4 devices here weren't supported by it due to the SATA controllers used. Also, there really is no host-based way to perform backups without spending $1000 on a bad backup tool. If you treat each VM like a physical machine and do backups that way, then it doesn't matter.

Big performance tips:
* always choose virtio for storage controllers
* always choose virtio for networking (NICs)

** For Windows VMs, you may want to choose an Intel PRO/1000 NIC and SATA or SCSI controller to avoid driver hassles, so you don't have to load redhat virtio drivers during emergency boots. The performance for the disks isn't THAT different, though for networking 1 Gbps limitation between VMs and the host on the say system is 20-40x slower than what virtio provides.

---

### Post by ajgreeny on 2020-09-08
Thanks to all of you.

I managed to get a VM running having now changed the storage folder to my home and have been playing around with it this evening with few problems other than sharing host folders (if it is possible) or using USB disks, eg thumb drives.  It took a while to figure out how to exit from fullscreen but then I noticed the small icons that appear when the cursor is moved to the middle of the top screen edge; dead simple when you know. Speed and smoothness of the graphics is certainly very good, and faster than VBox, I think.  Touchpad scrolling works perfectly which is certainly not the case with VBox where I have to scroll manually by pulling down the scrollbar with the cursor.

I will keep searching for answers to the USB, shared folders, and any other problems I come across, but thanks again for the help.

---

### Post by Dennis N on 2020-09-08
> ... few problems other than sharing host folders (if it is possible) or using USB disks, eg thumb drives.
I takes a while to figure things out. I work from a VM much of the time (as I am right now), not just for testing. These two items I can give you an answer.

USB: With Ubuntu host, to make the USB accessible from the VM you have to "redirect" the USB device: exit VM full screen mode, then from the Virt-Manager Menu > Virtual Machine > Redirect USB Device.

Access Host: The only method I know to gain access to the Host is to connect over the local network by SSH, just as you would connect to any another computer on the network.

---

### Post by TheFu on 2020-09-08
Use NFS for shared folders. Treat the host and the guest like physical machines.

For USB, there are some tricks. Usually, I just scp/sftp the files from the host into the VM, if there isn't an NFS connection.  With ssh-keys setup, this stuff is trivial.

As for graphics, if you use SPICE and QXL, don't forget that all this works over the network too. You don't have to be in the same room.  
```
virt-viewer --connect qemu+ssh://hadar/system regulus
```
where
* regulus is a VM running somewhere with QXL video drivers
* hadar  is a DNS name on the network known to the current host for the VM host. An IP should work.  The current userid, if it matches between the VM host and current host will be used or add "thefu@hadar" where hadar is now.

On the same machine, use:
```
$ virt-viewer regulus
```

Over a trusted LAN, we can force not to use SSH tunneling by adding a --direct option, but leave everything else there.
Thanks to SPICE and QXL, we can watch hidef video through this connection, though it would be better to access the files directly (via NFS or DLNA) and let the local hardware play the video.

Oh ... and virt-viewer has a menu where connecting a USB device is pretty simple. A checkbox for the device and "ok" button.

This will work over just the ssh port, over the internet too, but audio and video probably won't work.  For low bandwidth connections, consider loading up x2go and using that. x2go also works over ssh using ssh credentials and honors all ~/.ssh/config settings for different hostnames, IPs, userids, and ports. Those are the most important parts, but everything is documented in the ssh_config manpage, so if you want a keepalive or a specific pki file pair to be used, that's all possible.

A quick little connection script that just needs the KVM/Spice hostname changed:
```
#!/bin/bash
if [[ $HOSTNAME == "hadar" ]] ; then
    # For local connection on hadar
    /usr/bin/virt-viewer -a -d  $1 &
else
    # For remote connections on the LAN
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system $1 &
fi
```
So... if this script is in your PATH, perhaps ~/bin/vview, run it with **vview regulus** and it will do the correct connection for local or remote and we don't have to remember these details anymore regardless of our client.  To connect to my winult box, **vview winult** is the command.   The $1 argument is just the VM name as far as libvirt knows. It is case-sensitive.  If no argument is provided - I don't know what happens. I use aliases to call the script from keyboard accel shortcuts.  

Any guest with QXL video drivers works with spice and will have a fast GUI experience. My local and remote setups both use openGL for graphics drawing. Fast.  Like running on a physical machine, but without knowing it. My hardware is pretty medium-cheap for 2 yrs old.  Lets the local GPU get used.  There is a Windows virt-viewer too, but I don't have ssh-keys setup on that, so it isn't nearly as clean for connections.

I need to load up an old WinXP VM and see how some old games play.  Can't wait to try a flight sim out now that I've seen how fast it is.  Really can't imagine any of my 10-25 yr old games performing badly with the snappiness I just saw.

---

### Post by Dennis N on 2020-09-08
I would add this about accessing host. You only need to manually connect (with IP address) once! The Ubuntu in the VM will offer to 'remember' the connection details. Then, I bookmarked some key folders on the host so I can access them from Gnome's 'Places Menu'. Click there and you automatically connect and open that host location in file manager. This works in Ubuntu MATE also.

---

### Post by ajgreeny on 2020-09-09
Wow!
I think my brain is fried; there is so much more to this than I knew, and a huge amount to get my head around.

One step at a time, and thank you for so much help; much more than I expected to get so quickly.

---

### Post by TheFu on 2020-09-09
This is just the tip of the iceberg!

**If** you won't ever use a remote connection into the VM, say so and lots of stuff becomes completely unrelated. Because that's almost the only way I ever connect into a VM, all that information is crazy important to me.
Also, if you want to run older OSes, like WinXP or earlier, there are a bunch of HW things that we all use today which have zero support. The MB chipset, NICs, disk controllers.  For example, WinXP didn't include Intel PRO/1000 drivers or virtio drivers, so picking those will end in failure.  The drivers exist, but we have to hunt them down to use them. I wouldn't expect Intel to leave WinXP support files online today.  Would be fun to run OS/2 Warp ... hummmm.  Have my CD somewhere here.

---

### Post by ajgreeny on 2020-09-16
Just a quick update for all who have given me such useful information.

I've now been using KVM/qemu for virtualising Linux Mint for just over a week and I'm very impressed.  Graphics are better than VBox, with no problems getting the full resolution, and no guest additions to add to get USB or host files sharing; I just ssh connect to the host which I suppose is possible using VBox as well though I have never done so.

I am now aboiut to try importing a qcow2 file of Windows-10 that I have created by converting a vmdk file extracted from the Windows-10.ova created by exporting the VBox-VM.  I will update this after the deed is done and let you know how easy (or difficult) it was.

Once again, many thanks to all who have helped me so far.

---

### Post by TheFu on 2020-09-16
> **ajgreeny said:**
>  I am now aboiut to try importing a qcow2 file of Windows-10 that I have created by converting a vmdk file extracted from the Windows-10.ova created by exporting the VBox-VM.  I will update this after the deed is done and let you know how easy (or difficult) it was.

Windows is VERY picky about hardware changes, especially if the motherboard changes.  ova is a virtualbox format. Don't know how well it works with anything else.  

There is a Windows program that will remove all drivers and put the machine into a state that is nearly ready for a fresh install, just with all your programs.  I used that about a decade ago to avoid losing 7MC TV recorded file data.  sysprep? I think that's the name, but don't quote me.

Once you have moved to KVM with a Windows VM, make note of the settings in the XML file. Those will be what you have to retain forever, as you move from VM host to VM host the next 30 years.  There are specific motherboard models.  The libvirt XML files are stored under /etc/libvirt/ somewhere. Don't just go edit those. **virsh edit** is necessary, if you don't use virt-manager.  For migrations, we can dump the XML, then "define" it on a new system or after making any changes we like. But there are names and UUIDs that need to be modified too.  KVM with libvirt likes to keep track of UUIDs in a multi-host environment, so as VMs get migrated either manually or using migration techniques with shared storage, the libvirt subsystem doesn't get confused.

Did you setup a linux bridge or are you using NAT?

---

### Post by QIII on 2020-09-16
Just as an aside: I have found that KVM does not handle BSDs or pure Unixes well if they have a GUI.  Command-Line only is fine.  BSDs with GUIs seemed to work in VBox, but you can't run both VBox and KVM at the same time.

---

### Post by ajgreeny on 2020-09-16
I am trying the Windows-10 import just as an experiment, not because I need it for anything; I haven't really used Windows properly for 15 years so this is just a "for interest" exercise.

Watch this space!

---

### Post by TheFu on 2020-09-16
> **QIII said:**
> Just as an aside: I have found that KVM does not handle BSDs or pure Unixes well if they have a GUI.  Command-Line only is fine.  BSDs with GUIs seemed to work in VBox, but you can't run both VBox and KVM at the same time.

Linuxen have QXL drivers built-in, but there are other display types supported with KVM - Cirrus and VMVGA are the safe, but slower fallbacks which should work with anything.  Cirrus is like from 1990, maybe earlier.  I vaguely recall a BSD desktop with support for "spice" and QXL, but don't recall which has it.

Virtual machine hosts need a kernel module which connects into the VT-x or AMD-v kernel extensions, so only one can be run at the same level.  

However, thanks to nested virtualization, it is possible to run KVM on the hardware, then have a VM running Xen and a VM inside it running Vbox.  Sorta like "inception".  It is fun, but not really useful in production. 

For play environments, there's all sorts of things possible.  I've seen people running Xen on the hardware, then using KVM to host LXD and docker containers and having ESXi in another VM, just because they could. Just remember, only 1 hypervisor using hardware VM extensions can be run at the same level.

Whenever possible, for non-Windows VMs, please choose virtio drivers for storage and networking.  It is good to have 45 Gbps connections between VMs and the host, rather than 1 Gbps connections.  For Windows VMs, if virtio isn't an automatic option, it is probably best to stick with SATA/SCSI for storage and Intel PRO/1000 since those drivers should always be available from Win7 forward.  WinXP has the Intel PRO/1000 drivers, but only as separate downloads, which means in "safe mode", you'll need to have those drivers easily accessible.  The same applies to virtio drivers from Redhat for Windows. I decided to use virtio for storage and networking and it was a little better (faster, fewer resources), but the hassle factor when Windows refused to boot for any reason made me wish I hadn't.

Most popular Linux distros have supported virtio for 10+ yrs.

---

### Post by ajgreeny on 2020-09-17
I followed the info at [https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2](https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2) to convert the ova to qcow2 and I am surprised to find that Windows 10 works very much better using KVM than it does in VBox.

It runs smoothly and fast with none of the terrible lag that I've seen trying the same thing when importing the same ova into VBox.

Definitely one up for KVM at the moment.

---

