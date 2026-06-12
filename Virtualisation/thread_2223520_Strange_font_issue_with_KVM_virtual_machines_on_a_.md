---
title: "Strange font issue with KVM virtual machines on a new Ubuntu 14.04 server"
date: 2014-05-11
forum: Virtualisation
---

### Post by brw2 on 2014-05-11
I installed Ubuntu 14.04 server on a spare headless system this week.  During the install I selected SSH Server and Virtual Machine Host because I wanted to get more familiar with KVM virtual machines.  Most of my virtual machine experience is with VMWare. 

You can see the font problem I am having in [these screenshots]("http://imgur.com/a/jKxSc").

Other than locking down SSH, installing fail2ban and a few other minor security changes it is a default Ubuntu 14.04 server install.  The hardware is an AMD FX-4350, 8GB, SATAIII 500Gb, Gigabyte motherboard with integrated Radeon HD 3000. 

I followed the example on the [Ubuntu Server Guide]("https://help.ubuntu.com/14.04/serverguide/serverguide.pdf") and used virt-install.  I used the following command to create the virtual machine:```
[INDENT]
sudo virt-install -n ubuntu1404i386desktop -r 2048 \ 
--disk path=/home/b/vm/ubuntu1404i386desktop.img,bus=virtio,size=20 \ 
-c /home/b/ISO/ubuntu-14.04-desktop-i386.iso --network network=default,model=virtio \
 --graphics vnc,listen=0.0.0.0 -- noautoconsole -v
[/INDENT]

```
Once the virtual machine is up and running I connect to it using a VNC client.  As you can see in [the screenshots]("http://imgur.com/a/jKxSc") something unusual is happening with some of the fonts. I have tried both UltraVNC and TightVNC, and I have tried changing the jpeg compression and various connection options that deal with graphics to try to resolve the issue. I changed the resolution in the virtual machine to a higher resolution, 1280x768, to see if it corrected the issue.  I installed Xubuntu on another virtual machine, using essentially the same virt-install command, to see if the issue was specifically with Ubuntu but I get the same problem.  I also tried accessing the virtual machines using a VNC viewer running on a Linux desktop and got the same results.

I have tried searching for a solution but I guess my Google-fu isn't good enough to find it.  Has anyone had this problem and found a resolution?

---

### Post by Doug S on 2014-05-12
Hi and welcome to Ubuntu forums,

Yes, I get the exact same issue as you, and always have. And I also use the exact same VNC clients as you. The root issue is that the default cirrus video driver is crap (well, that is just my opinion).
You can fix the issue by changing to the vmware video driver. Use "[COLOR=#ff0000]virsh edit VM_Computer_name[/COLOR]" and change this area:```
    <video>
      [COLOR=#ff0000]<model type='cirrus' vram='9216' heads='1'/>[/COLOR]
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
```to this:```
    <video>
      [COLOR=#ff0000]<model type='vmvga' vram='16384' heads='1'/>[/COLOR]
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
```Notice that in addition to changing the video driver, I also increased the vram size, because according to my math more is needed. Your machine type should have defaulted to this:```
  <os>
    [COLOR=#ff0000]<type arch='x86_64' machine='pc-i440fx-1.7'>hvm</type>[/COLOR]
    <boot dev='hd'/>
  </os>
```if it didn't, and you have this instead:```
  <os>
    [COLOR=#ff0000]<type arch='x86_64' machine='pc-1.0'>hvm</type>[/COLOR]
    <boot dev='hd'/>
  </os>
```Then change that also, otherwise the vmware driver will not work, even though that machine type worked on previous versions and used to be the default.

Additional note: The "virsh edit bla" command will default to the vi editor, but you can change it to your preferred editor. I can not recall how at the moment, but I'll figure it out if you need it.

---

### Post by brw2 on 2014-05-21
Sorry it took me so long to reply.  Thanks for the help.

It seems to have resolved the issue with the fonts not appearing correctly.  However, the display is incredibly slow now almost as if I am trying to access it over dial-up.  I have tried changing various settings to reduce the graphics load but it doesn't seem to make much of a difference.  I did run an update before trying this and it looks like Qemu was updated so it may be an issue with the newer version.  I haven't tried reverting to the older version yet to see if it corrects the problem.  If I switch it back to [COLOR=#FF0000][FONT=Ubuntu Mono]cirrus[/FONT][/COLOR] the display speed goes back to what I had before which is comparable to what I've gotten on VMWare installations on similar systems. 

I'm still working on it and I think  your suggestion has put me on the right track.  When I figure it out I will post an update here. Again, thanks for your help.

---

### Post by Doug S on 2014-05-22
> **brw2 said:**
> ... However, the display is incredibly slow now almost as if I am trying to access it over dial-up... I'm still working on it...  When I figure it out I will post an update here.Thanks for reporting back. I have not experienced any display slow down issue. As you look into it, let me know if you want me to try anything on my system.

---

### Post by KillerKelvUK on 2014-05-26
Had same issue with a 14.04 ubuntu guest, intermittent though.  Changed to 'vmvga' with 64MB vram but left the machine type as per the default in 14.04 and I get video/font stability, however as per brw2's feedback the UI is still laggy although it is usable.  Any recommendations to improve performance/debug?

(Am running Win7 guest without any performance issues and all my VM's are stored on a local SSD so I don't believe this is IO related, unless someone can coach me into the debugged steps to validate?)

```

<domain type='kvm'>
  <name>blacktools-server</name>
  <uuid>77506660-3bc8-3dbd-1678-226f07a4fbec</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <cpu>
    <topology sockets='1' cores='2' threads='2'/>
  </cpu>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/mnt/VMs/blacktools-server.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x2'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:b5:65:5d'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <image compression='auto_glz'/>
      <streaming mode='filter'/>
      <mouse mode='client'/>
      <clipboard copypaste='yes'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='vmvga' vram='65536' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

---

### Post by Doug S on 2014-07-09
For the performance issues mentioned by two posters now, from my experience all I can add is that, for me, things are fine if I use the stock Ubuntu kernel on the host computer. However I very often run a kernel from kernel.org that I build myself using my ubuntu kernel config file, and if I run the same virtual machine guests under that host kernel performance is terrible. (Running VM guests under my test kernels is not something I would normally do, but I did for a test and noticed the perforamnce side effect and recalled this thread, so am adding this comment.)

---

### Post by TheFu on 2014-07-10
Not directly connected to virt-install/VNC issues, but ... 

a) Why use virt-install? Seems there are bugs. There is a good GUI VM manager for libvirt called virt-manager, that runs local or remote over an ssh tunnel and provides a VM creation wizard to setup new VMs AND provide access to many more machine settings. It makes managing VM settings from anywhere that ssh works easy.  So ... libvirt and kvm are the server-side dependencies.  Just virt-manager is needed on the management workstation, which can be the server, if X/Windows was installed there. I run it remote using my normal account remote connection (non-root) with key-based authentication. 

b) VNC performance sucks, IMHO.  Use **spice** or **NX** instead.  Spice is part of the KVM/virt-manager setup and provides near-native graphics and audio support. It is not secure by default, but SSL can be added (I understand). Since 14.04, it works reasonably well, though in 12.04 it was buggy and I had issues with the keyboard mapping missing very important keys.  There are additional dependencies and **virt-viewer** is needed on the viewing machine (linux/Windows clients exist).  
In 14.04, the FreeNX server hasn't been ported, so that isn't an option.  For older guestOSes, it does work well.  Any NX client can be used to connect. NX uses ssh as part of the protocol and feels about 2-3x faster than VNC/RDP options.  With a 14.04 clientOS, x2go seems to be the replacement NX solution. I haven't tried this, yet. No 14.04 desktops here, but that will change shortly, perhaps today.   NeatNX server from google seems dead and there is a commercial NoMachine NX server too (closed source) which I've never used.

I find VNC performance on consoles (text) to be REALLY, REALLY, REALLY, REALLY bad.  That is putting it nicely.  I find the IP and reconnect directly over ssh to perform all system management ASAP.  Did I mention VNC is painful?  Haven't had luck trying VGA displays with this, but I was also trying spice at the same time and didn't fully understand the spice setup, so could have easily left a setting for spice that interfered with VGA settings.

Oh ... and if you modify any VM XML files, you'll need to re-define them with virsh.  Using virt-manager makes all that easier/automatic.

i hope this all makes sense.  Of course, I wouldn't use virt-manager if I needed to spin up 5+ VMs, but for the 1-2 new VMs a month I need, it is nice.

---

### Post by Doug S on 2014-07-10
> **TheFu said:**
> a) Why use virt-install? Seems there are bugs. There is a good GUI VM manager for libvirt called virt-manager, that runs local or remote over an ssh tunnel and provides a VM creation wizard to setup new VMs AND provide access to many more machine settings.Yes, Hi TheFu. You have mentioned VM manager to me before on some other thread. However, I have never been able to make it work, and so use virt-install.> **TheFu said:**
> b) VNC performance sucks, IMHO.It has been good enough for me. (I am actually a server guy and only make desktop VM's to help with Ubuntu documentation).> **TheFu said:**
> I find the IP and reconnect directly over ssh to perform all system management ASAP.Yes, I do that also.> **TheFu said:**
> Oh ... and if you modify any VM XML files, you'll need to re-define them with virsh.Yes, of course. Only use "virsh-edit" to modify the xml definition file (see also my post #2 above, where I changed that comment to "RED" just now to emphasize it.)

---

