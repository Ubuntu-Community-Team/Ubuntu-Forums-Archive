---
title: "USB device not working in Windows 10 VM"
date: 2016-07-06
forum: Virtualisation
---

### Post by saurumanx on 2016-07-06
Hi everyone,

I have Ubuntu 16 installed on a Haswell Clevo laptop.

I'm using KVM with Virtual Machine Manager to run Windows 10 as a guest. I want to use Windows for music production (using Reaper).

I connected windows to my USB sound-card, as shown in the pic below. The device shows up in my software, but the functionality isn't there. Do I need to install some other device?

Thanks!!

[IMG]http://i67.tinypic.com/2z3qvme.png[/IMG]



[img]http://i64.tinypic.com/2ai3ib.jpg[/img]

---

### Post by KillerKelvUK on 2016-07-06
Hi, does the USB device show in the Device Manager in Windows?

---

### Post by MAFoElffen on 2016-07-06
Is your host not sharing it? Such as has full committed control and is not releasing it to be shared? Just wondering.

I know Sound devices can be a bit flakey in KVM. With mine it's a usb dongled wireless headphones. If I run the VM, sometimes I have to plug, unplug, plug it back in... then it works as if nothing had ever been wrong.

---

### Post by saurumanx on 2016-07-08
I don't know how to determine whether my host (Ubuntu) is releasing it to be shared. How can I check for that?

I'm not seeing the device in device-manager,

[IMG]http://i66.tinypic.com/2z67dec.png[/IMG]

Also, you can see the "no devices connected" but the device is really connected. I've done multiple restarts and re-installs. The device itself lights up when I plug it in.

---

### Post by MAFoElffen on 2016-07-09
Go into a terminal to look at the xml of your VM guest's config file (ie: if the name was VM_Name):
```

sudo virsh edit VM_Name

```
Then look within the xml tags for os to the type tag. That section may look similar to this:
```

...
  <os>
    <type arch='i686' machine='[COLOR=#ff0000]pc-i440fx-2.1[/COLOR]'>hvm</type>
    <boot dev='hd'/>
  </os>
...

```
What is highlighted in red was the default chipset for QEMU/KVM. It woorks okay, until you try to do a passthrough. There is a work-around for that, by changing it to the ICH9 chipset emulation. Such as this one:
```

...
  <os>
    <type arch='x86_64' machine='[COLOR=#ff0000]pc-q35-1.6[/COLOR]'>hvm</type>
    <boot dev='hd'/>
    <boot dev='cdrom'/>
    <bootmenu enable='yes'/>
  </os>
...

```
So if you change it to that... the edit commands in virsh edit are the same as they are in VIM and VI. In the file, <Insert> to get into add/edit mode. Edit the file. <Esc> to get out of add/edit mode. <:> to enter a command, <w><q> to write quit.
{code]
:wq
[/code]

---

### Post by saurumanx on 2016-07-10
Thanks!

So my OS looked like this,

  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <boot dev='hd'/>
  </os>

I changed it as you said, and exited / saved with ctrl-shift-X. I got this error.

error:  internal error: PCI bus is not compatible with the device at  0000:00:1e.0. Device requires a PCI Express slot, which is not provided  by bus 0000:00
Failed. Try again? [y,n,i,f,?]: 

I tried installing the VirtIO drivers btw. They're not seeming to make any difference that I can tell.

While looking up solutions, I also found this thread,

[http://unix.stackexchange.com/questions/250938/qemu-usb-passthrough-windows-guest](http://unix.stackexchange.com/questions/250938/qemu-usb-passthrough-windows-guest)

but I have no idea what anything he wrote means. I'm completely fresh from Windows so this stuff is a little over my head.

---

### Post by KillerKelvUK on 2016-07-10
Hi saurmanx, from the picture you posted in #4 there are 2 'other devices' which look like hardware which windows doesn't know about as you haven't installed the drivers yet, my guess is that one of these is your sound card.  Revert the changes you made to your guest chipset (the ones MAF advised in post #5) and get back into Windows, once their right click those 'other device' and select 'update driver'...if windows can't locate the drivers automatically you'll need to supply the driver file from the manufacturers website.

---

### Post by saurumanx on 2016-07-12
OK, thanks.

The MIYO is a USB 2.0 device, not a PCI, but I guess that doesn't matter here?

---

### Post by KillerKelvUK on 2016-07-12
Actually my mad that does make a difference, sorry I missed the USB confirmation in your OP.  If the Windows device manager isn't even showing the USB device then its not getting to the vm, MAF's post was looking to change your guest chipset architecture to a more recent Q35 revision which has better USB support although I'd expect some recognition of the USB device in your current config even if the i440FX chipset can't do much with it.  When you run the guest take a look at the logs, based on your config above the log should be at "/var/log/libvirt/qemu/Windows", is that showing any error in passing the USB device through...its possibly a permissions error i.e. the KVM user doesn't have permissions to grab the usb device and assign it to the guest, if so that should be an easy fix.

Another test would be to use SPICE USB redirection as a test, basically attached the USB device to the guest once Windows has booted.  To do this you'll need the remote-viewer binary which is part of the virt-viewer package which was likely installed when you installed virt-manager.  Just run remote-viewer, put in the connection URL for your Windows guest which will be something like "spice://127.0.0.1:*port"* (get the port number from the 'Display Spice' device thats part of your current config).  This will get you a remote desktop connection to the guest but on the ubuntu menu bar for remote-viewer you'll have an option to attached a USB device, give this a try and see if that works any better also.

---

### Post by saurumanx on 2016-07-16
Ok. Is there a simpler way then? If my guest chipset architecture is out  of date, can I update? Or change my settings to more bleeding-edge?  Maybe running Archbang will mean I'll have the updated chipset  automatically?

My brain hurts reading your instructions, and I still haven't managed  the original suggestion of updating the chipset using the command line,  but if that's the only way, I'll try to figure it out.


Also, does it matter whether I use Spice Channel or TCP for USB redirection? The default was Spice. TCP requires I write the "host"

---

### Post by KillerKelvUK on 2016-07-16
> **saurumanx said:**
> Ok. Is there a simpler way then? If my guest chipset architecture is out  of date, can I update? Or change my settings to more bleeding-edge?  Maybe running Archbang will mean I'll have the updated chipset  automatically?

My brain hurts reading your instructions, and I still haven't managed  the original suggestion of updating the chipset using the command line,  but if that's the only way, I'll try to figure it out.


Also, does it matter whether I use Spice Channel or TCP for USB redirection? The default was Spice. TCP requires I write the "host"

The chipset is a virtual chipset...as you are using virt-manager to create your guests this will default to use i440FX, you can alter this using virt-manager but only when you initially create the guest i.e. the very first time just before your run it by clicking the 'Begin Installation' button.

[IMG]https://s32.postimg.org/af1hvm1wl/Screenshot_from_2016_07_16_17_42_31.png[/IMG]

It is possible to change the chipset of a guest after you have finished setting it up however it can be complicated and this was what MAF was suggesting you do, however if you aren't familiar with virsh and libvirt xml I'd recommend against in and advise you just to recreate the guest from scratch.

However this may not help you at all, if you can post the output of the log file in a reply here...like I say the log file should be in a directory here /var/log/libvirt/qemu/ and it will be named the same as your guest, this will help tell us whether KVM/Qemu is able to pass the USB through or not.

---

### Post by saurumanx on 2016-08-01
Ok, thanks.

The logs seem to be locked. I can't open them, upload them, or even copy them. When I right-click-properties the 'owner' is root. I guess I have to do something to 'unlock' it.

Edit - I figured out how to unlock. :) Will upload in one minute.

Here's the error I get trying to make a machine with a different chipset.

[http://i65.tinypic.com/az6z44.png](http://i65.tinypic.com/az6z44.png)

And here are the logs for 3 machines I tried making.

[https://www.dropbox.com/s/ucuxg2ldo8eehp6/Windows.log?dl=0](https://www.dropbox.com/s/ucuxg2ldo8eehp6/Windows.log?dl=0)
[https://www.dropbox.com/s/ju6g3xm9g4kz5db/Windows2.log?dl=0](https://www.dropbox.com/s/ju6g3xm9g4kz5db/Windows2.log?dl=0)
[URL="https://www.dropbox.com/s/0b4692xfrhxxqh9/Windows3.log?dl=0"]https://www.dropbox.com/s/0b4692xfrhxxqh9/Windows3.log?dl=0

[/URL]

---

### Post by KillerKelvUK on 2016-08-01
Okay, so I've looked through all 3 of your logs posted and none show any signs of a USB device being assigned.  Referring to your file for "Windows.log" the top 11 lines are the command that is run to create your virtual machine...I've cut them out and put them below is a way that makes it easier to read...

```

QEMU_AUDIO_DRV=spice /usr/bin/kvm-spice 
-name Windows 
-S 
-machine pc-i440fx-wily,accel=kvm,usb=off 
-cpu Haswell-noTSX 
-m 16000 
-realtime mlock=off 
-smp 4,sockets=4,cores=1,threads=1 
-uuid 44916ee7-caba-486d-9233-bcfd58627333 
-no-user-config 
-nodefaults 
-chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-Windows/monitor.sock,server,nowait 
-mon chardev=charmonitor,id=monitor,mode=control 
-rtc base=utc,driftfix=slew 
-global kvm-pit.lost_tick_policy=discard 
-no-hpet 
-no-shutdown 
-global PIIX4_PM.disable_s3=1 
-global PIIX4_PM.disable_s4=1 
-boot strict=on 
-device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x6.0x7 
-device ich9-usb-uhci1,masterbus=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x6 
-device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x6.0x1 
-device ich9-usb-uhci3,masterbus=usb.0,firstport=4,bus=pci.0,addr=0x6.0x2 
-device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x5 
-drive file=/var/lib/libvirt/images/Windows.qcow2,format=qcow2,if=none,id=drive-virtio-disk0,cache=writeback 
-device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 
-drive if=none,id=drive-ide0-0-1,readonly=on 
-device ide-cd,bus=ide.0,unit=1,drive=drive-ide0-0-1,id=ide0-0-1 
-drive file=/home/k/Downloads/virtio-win-0.1.102.iso,format=raw,if=none,id=drive-ide0-1-0,readonly=on 
-device ide-cd,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 
-netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=28 
-device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:49:0d:1f,bus=pci.0,addr=0x3 
-chardev pty,id=charserial0 
-device isa-serial,chardev=charserial0,id=serial0 
-chardev spicevmc,id=charchannel0,name=vdagent 
-device virtserialport,bus=virtio-serial0.0,nr=1,chardev=charchannel0,id=channel0,name=com.redhat.spice.0 
-spice port=5900,addr=127.0.0.1,disable-ticketing,image-compression=off,seamless-migration=on 
-device qxl-vga,id=video0,ram_size=67108864,vram_size=67108864,vgamem_mb=16,bus=pci.0,addr=0x2 
-device intel-hda,id=sound0,bus=pci.0,addr=0x4 
-device hda-duplex,id=sound0-codec0,bus=sound0.0,cad=0 
-chardev spicevmc,id=charredir0,name=usbredir 
-device usb-redir,chardev=charredir0,id=redir0 
-chardev spicevmc,id=charredir1,name=usbredir 
-device usb-redir,chardev=charredir1,id=redir1 
-device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on

```

Each line above adds or configures a different aspect to your virtual machine i.e the -cpu tells it what CPU model to use and the -m tells it how much RAM to assign and so on.

If your virtual machine had a USB device assigned to it I would expect the above to have a line in there something like this... 

```
-device usb-host,hostbus=3,hostaddr=8,id=hostdev0
```

The fact that yours doesn't would suggest you haven't actually added in the USB device to to virtual machine configuration.  Do you still have the virtual machine for the "Windows.log" in virt-manager or have you since removed/deleted it?

---

### Post by saurumanx on 2016-08-02
Ok, I made another new machine,

This one has the device installed, and the "USB host device" passed through like the original screenshot.

I'm not seeing any text like you say, but I've no idea what I'm doing, so I uploaded it to dropbox again

[https://www.dropbox.com/s/4g8bs4ynvglhvtp/WindowsV7.log?dl=0](https://www.dropbox.com/s/4g8bs4ynvglhvtp/WindowsV7.log?dl=0)

Thanks!!

---

### Post by KillerKelvUK on 2016-08-02
Okay, so I've taken another look and your right its not their so...hopefully you've not deleted that new machine you created as we need to take a different look at it now.  Open up a terminal and type in the following command and post back the output...

```

virsh dumpxml WindowsV7

```

EDIT:

Also please from a terminal please post the output of

```

lsusb

```

You can post the outputs directly into the forum thread just use the Advanced thread reply UI and hit the # button then put the text you want to post inbetween the code tags.

---

### Post by saurumanx on 2016-08-03
Thanks!! Here's virsh dumpxml WindowsV7

```
k@Komputerrr:~$ virsh dumpxml WindowsV7
<domain type='kvm'>
  <name>WindowsV7</name>
  <uuid>5a370cf0-07f8-403d-b3fd-28678e40deb8</uuid>
  <memory unit='KiB'>8192000</memory>
  <currentMemory unit='KiB'>8192000</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell-noTSX</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/WindowsV7.qcow2'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:32:66:d9'/>
      <source network='default'/>
      <model type='rtl8139'/>
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
      <image compression='off'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x20b1'/>
        <product id='0x305f'/>
      </source>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>


```

Here's lsusb
```
k@Komputerrr:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0781:5583 SanDisk Corp. 
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 003 Device 005: ID 5986:0512 Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by KillerKelvUK on 2016-08-03
Okay so good news... the virsh output clearly shows you have assigned a USB device to the virtual machine:

```

 <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x20b1'/>
        <product id='0x305f'/>
      </source>
    </hostdev>

```

Problem is your lsusb output doesn't show the USB device as connected to your host, I'd expect lsusb to report it something like "Bus 003 Device 006: ID 20b1:305f XMOS Ltd MIYO USB Audio 2.0" based on your first and last thread posting.  Was the USB audio device connected to the system when you ran lsusb?

---

### Post by MAFoElffen on 2016-08-03
> **KillerKelvUK said:**
> Okay so good news... the virsh output clearly shows you have assigned a USB device to the virtual machine:

```

 <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x20b1'/>
        <product id='0x305f'/>
      </source>
    </hostdev>

```

Problem is your lsusb output doesn't show the USB device as connected to your host, I'd expect lsusb to report it something like "Bus 003 Device 006: ID 20b1:305f XMOS Ltd MIYO USB Audio 2.0" based on your first and last thread posting.  Was the USB audio device connected to the system when you ran lsusb?
That is just odd. Not seeing that either, and that's what I would have expected. Everything else looks like it is in place now.

---

### Post by saurumanx on 2016-08-03
The device wasn't plugged in. Here's the output while the device is plugged in, and I'm listen to music through it.

```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 010: ID 20b1:305f XMOS Ltd 
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 003 Device 004: ID 5986:0512 Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Another thing, the virtual machine will not start if the USB device isn't plugged in... so something is there, it just doesn't work.

Also, I tried passing through a regular USB thumb drive and it worked no problem.


I should say, I'm actually able to listen to music in the virtual machine using the device, the problem is only that the inputs and outputs don't show up in my DAW (what I use for music production).

I can get the machine to work in my DAW using a generic driver (ASIO4ALL) so the problem seems to only be with the native driver?

---

### Post by KillerKelvUK on 2016-08-03
> **saurumanx said:**
> The device wasn't plugged in. 

:) made me smile after all that!

I think your summation is correct i.e. a windows driver issue.  Does the Windows device manager still show unknown devices or devices needing a driver to be presented?

---

### Post by saurumanx on 2016-08-04
It doesn't seem to be in device manager,

[IMG]http://i67.tinypic.com/3am8x.png[/IMG]

---

### Post by KillerKelvUK on 2016-08-04
> **saurumanx said:**
> It doesn't seem to be in device manager,



Those are USB Controllers, you need to look under 'Sound, Video and Game Controllers' I suspect.

You know I'd also clear up those other PCI devices that need drivers...

---

### Post by saurumanx on 2016-08-04
I've been told it should be counted as USB, but here are the sound controllers expanded. I tried updating those PCI devices but it didn't work. Is there any chance they could affect the MIYO?

[IMG]http://i66.tinypic.com/kd5wed.png[/IMG]

---

### Post by KillerKelvUK on 2016-08-04
Odd, you're sure the USB audio device is connected and playing through your virtual machine?  What is shown under playback devices and recording devices in the Sound app under the Windows control pannel?

---

### Post by saurumanx on 2016-08-05
So here I'm again listening to music in the virtual machine using the device, however the device isn't showing up in the settings, it only shows up as "speakers". But in a bare metal windows, the device would be listed here as MIYO. If you need, I can boot into a bare metal installation and take screen-shots of how things show up in Windows normally.

[IMG]http://i66.tinypic.com/5mq7r.png[/IMG]

---

### Post by KillerKelvUK on 2016-08-05
Nah, that's a virtual sound adaptor...your virtual machine configuration includes a sound device, see here from your xml posted prev... (its also shown in the screen shot on your original post)

```

<sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
</sound>

```

Go back into virt-manager and remove the sound device and re-test, I'm betting you'll have no audio at all.

---

### Post by saurumanx on 2016-08-06
Yes, you're right.

So the real problem is still this,

[img]http://i64.tinypic.com/2ai3ib.jpg[/img]

I need the inputs / outputs to show up in Reaper. I can make it work using another driver (ASIO4ALL) but I really need it to work with these drivers.

Would it make a difference if I used a different host OS? I could try installing ArchBang as host?

---

### Post by saurumanx on 2016-08-06
So I'm thinking. The sound output is "virtualized", but the guest should have direct/bare metal access to the USB MIYO device, right? Maybe I have to change some setting about sound virtualization?

---

### Post by KillerKelvUK on 2016-08-06
Changing your host i doubt will make a different as KVM and qemu work the same regardless of the distro.  I suggest one of two scenarios are at play... 1) you USB device isn't being passed through to the guest with something like a permissions issue at play. 2) it's there but you need to get the right driver to those 2 unknown devices shown in the device manager in Windows.

What happens if you add the USB device to the guest in virt-manager but after the guest has booted?

---

### Post by heiko_s on 2016-08-07
There are multiple ways of playing sound in kvm, or passing through a USB device. The simplest is
```
-device usb-host,hostbus=2,hostaddr=3
``` as used in
```
qemu-system-x86_64 \
...
-device usb-host,hostbus=2,hostaddr=3 \
...
```
Determine the values using lsusb.

You could also pass through your USB host controller such as:
```
-device vfio-pci,host=00:1a.0
```

To list all USB host controllers, use
```
lspci | grep "USB"
```

Use the following command to determine the PCI bus ID of the USB host to pass through:
```
usb-devices
```
Look for the audio device you wish to pass through, then look for a line like:
SerialNumber=0000:00:1a.0

The "0000:00:1a.0" is the PCI bus ID. Just make sure no other USB devices are connected to this USB host, unless of course those you like to pass them through to the VM.

Within Windows, you would then have to install the device drivers for the USB device.

Frankly, I find that using virt-manager just complicates matters.

---

### Post by heiko_s on 2016-08-07
Another note: I doubt that changing the host (Q35) makes a difference. However, passing the entire USB controller might work. It will not require a new installation of Windows.

But the first thing to try is to install the Windows device drivers for the unrecognized devices.

---

### Post by saurumanx on 2016-08-10
> **heiko_s said:**
> Another note: I doubt that changing the host (Q35) makes a difference. However, passing the entire USB controller might work. It will not require a new installation of Windows.

But the first thing to try is to install the Windows device drivers for the unrecognized devices.

Ok, so I'll try installing those drivers first. But how to install? I don't even know what they are. When I try the right-click ->update/install drivers in the device manager, Windows says it can't find the drivers.

---

### Post by KillerKelvUK on 2016-08-10
> **saurumanx said:**
> Ok, so I'll try installing those drivers first. But how to install? I don't even know what they are. When I try the right-click ->update/install drivers in the device manager, Windows says it can't find the drivers.

Have you tried the virtio drivers? If not grab the latest .iso from here ([https://fedoraproject.org/wiki/Windows_Virtio_Drivers](https://fedoraproject.org/wiki/Windows_Virtio_Drivers)) and try pointing the Windows driver search at that.

---

### Post by MAFoElffen on 2016-08-10
Wow... I just realized that this is post #34, and, well... I just search the whole thread. You have mentioned that this is to pass-through a USB 3.0 sound card. You have not mentioned a brand/model of that device...

It now sees the USB 3.0 hub, but not the device...

What I would do is to go to the manufacturers web site and download a driver for that device, for Windows 10, for the same arch as your VM. Some Windows device files have their own install program.If it has it's own install application, it will usually also look to see if it can see that device connected... 

Some are in archives, where you expand them, then point the device manager's search for drivers to that folder. Both would rewuire you to get it inside the VM Guest to install it, which would be easiest to download directly into the VM. Most WIndos USB device files ask you to reboot the OS to complete the install of the device driver.

---

### Post by saurumanx on 2016-08-17
> **KillerKelvUK said:**
> Nah, that's a virtual sound adaptor...your virtual machine configuration includes a sound device, see here from your xml posted prev... (its also shown in the screen shot on your original post)

```

<sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
</sound>

```

Go back into virt-manager and remove the sound device and re-test, I'm betting you'll have no audio at all.

You're right. If I remove the device, no sound passes through it (instead it comes through my laptop speakers).

> **KillerKelvUK said:**
> Changing your host i doubt will make a  different as KVM and qemu work the same regardless of the distro.  I  suggest one of two scenarios are at play... 1) you USB device isn't  being passed through to the guest with something like a permissions  issue at play. 2) it's there but you need to get the right driver to  those 2 unknown devices shown in the device manager in Windows.

What happens if you add the USB device to the guest in virt-manager but after the guest has booted?


If I add the device after boot, it behaves the same as before.

Someone in KVM Irc Chat told me I can disable the device in the host (Ubuntu) in order to give the guest unshared access? Is this what you mean about the permissions?

> **KillerKelvUK said:**
> Have you tried the virtio drivers? If not grab the latest .iso from here ([https://fedoraproject.org/wiki/Windows_Virtio_Drivers](https://fedoraproject.org/wiki/Windows_Virtio_Drivers)) and try pointing the Windows driver search at that.

I tried the Virtio drivers before, but I'll try as you say, pointing the missing drivers at that (currently I just have a vanilla install, no 'optimizations / customizations').

I should just download the "Stable virtio-win iso", no the x86-floppy or the 'Full archive'?

> **MAFoElffen said:**
> Wow... I just realized that this is post #34,  and, well... I just search the whole thread. You have mentioned that  this is to pass-through a USB 3.0 sound card. You have not mentioned a  brand/model of that device...

It now sees the USB 3.0 hub, but not the device...

What I would do is to go to the manufacturers web site and download a  driver for that device, for Windows 10, for the same arch as your VM.  Some Windows device files have their own install program.If it has it's  own install application, it will usually also look to see if it can see  that device connected... 

Some are in archives, where you expand them, then point the device  manager's search for drivers to that folder. Both would rewuire you to  get it inside the VM Guest to install it, which would be easiest to  download directly into the VM. Most WIndos USB device files ask you to  reboot the OS to complete the install of the device driver.

This is the device, [https://gomiyo.com/](https://gomiyo.com/) it's a USB 2.0 sound-card. I've installed the drivers from the site, but I'll try like you say, dig into the archive and try pointing the unknown devices at it.

---

### Post by saurumanx on 2016-08-17
Ok, I got the drivers from the VirtIO ISO. They were balooning drivers and a serial-driver - I think for the SSD as well. Here they are.

[IMG]http://i64.tinypic.com/16k2xaf.png[/IMG]


So since these devices have been "filled" using the VirtIO drivers, I guess there's no point opening up the MIYO install file? I'm assuming everything from this has installed properly, since it's just an .exe that I double click, and everything works normally in native-Windows.


Btw. thanks so much everyone for helping me. I know my question is 1/3 Ubuntu, 1/3 KVM, and 1/3 Windows, so I'm always being told to ask in difference forums. It seems like these are mostly Windows problems, but Windows user will have no idea (and the company doesn't support VMs officially, so no help there).

---

### Post by KillerKelvUK on 2016-08-17
> **saurumanx said:**
> 
This is the device, [https://gomiyo.com/](https://gomiyo.com/) it's a USB 2.0 sound-card. I've installed the drivers from the site, but I'll try like you say, dig into the archive and try pointing the unknown devices at it.

So I had a look at this site and under the support section ([https://gomiyo.com/pages/support](https://gomiyo.com/pages/support)) for the Windows drivers the following is shown...

> 
To use MIYO with a Windows® computer, you must first install the MIYO USB driver. Unfortunately, Windows® does not support the USB Audio Class 2 standard like other modern operating systems. While we have made every effort to make MIYO as easy to use as possible, this requirement could not be avoided without compromising MIYO&#8217;s performance.


Have you followed this instruction properly in your Windows guest?

---

### Post by saurumanx on 2016-08-17
> **KillerKelvUK said:**
> So I had a look at this site and under the support section ([https://gomiyo.com/pages/support](https://gomiyo.com/pages/support)) for the Windows drivers the following is shown...



Have you followed this instruction properly in your Windows guest?

Yes. So I've gone through the installation process again, and what I notice, at the end of the install, there's a part where you must unplug the device, and plug it in. But the device is never 'recognized' when it's plugged in, and so the software, I'm thinking, never completely completes installation. Hence there's nothing under device manager for it (it should be under 'sound, video and game controllers').

So back to the original question... why is it not being recognized? Even though sound is passing through it with the virtual driver.

I'm thinking it has something to do with the 'sound device' being passed through. I'm using ich6, but I've used every other option (ich9 also works for sound, but still no MIYO. Other devices don't work at all). If I click "add hardware"-"sound device" it gives me the same 6 options of sound devices, but no option to add a MIYO sound device.

The device shows up in Ubuntu, 

[IMG]http://i64.tinypic.com/2mi5fg1.png[/IMG]

So maybe I need to pass this through?

---

### Post by saurumanx on 2016-09-01
I've also tried passing the device through to an Arch guest. It is the  same - sound works, but it appears as a virtualized device, not as the  actual MIYO with MIYO settings. So the guest is recognizing the USB  device as a virtual soundcard. I had the idea to pass-through the  internal sounds card (who knows?) but got this error.

```

rror starting domain: unsupported configuration: host doesn't support passthrough of host PCI devices

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 90, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 126, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/libvirtobject.py", line 83, in newfn
    ret = fn(self, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1402, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 1035, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: unsupported configuration: host doesn't support passthrough of host PCI devices

```

Anyhow, maybe it's completely not worth trying that anyhow.

I was reading this site, [http://ask.xmodulo.com/pci-passthrough-virt-manager.html](http://ask.xmodulo.com/pci-passthrough-virt-manager.html) is says

"[COLOR=#444444][FONT=Arial]Essentially, PCI passthrough bypasses the virtualization layer, and directly exposes a PCI device to a VM. No other VM can access the PCI device."

Is that also true of USB passthrough? Because my device is still usable in the host when it's being passed through to the VM. Maybe there's a special way I can passthrough USB for direct / non virtualized access?

I'm also reading something similar here,
[https://www.redhat.com/archives/vfio-users/2015-September/msg00309.html](https://www.redhat.com/archives/vfio-users/2015-September/msg00309.html)

"
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]The second option was doing a PCI device assignment of my integrated audio controller.  This option worked significantly better, as I didn't have to reconnect any speakers in a different configuration.  Of course, you will only have audio on either the host or the VM with this option.  There are still slight pops and noise in the audio, but it's very infrequent, and typically only in more intensive games at this point.  I found that I could use the USB sound card on the host without issue in this configuration." It seems he had a similar problem, but I don't really understand what he's saying.
[/FONT][/COLOR]

---

### Post by KillerKelvUK on 2016-09-02
> **saurumanx said:**
> So back to the original question... why is it not being recognized? Even though sound is passing through it with the virtual driver.

So what you've posted here is making more sense, your USB sound device is being claimed by the host and used as the host primary sound output.  So then you go create a guest virtual machine and in that machine you have a virtual sound card, the guest operating system thinks it has a sound device and uses that virtual sound card to create its audio...the magic of qemu/kvm then happens which is the routing of the guest audio back to the host in the hope the host has an actual sound card + speakers to play the sounds on.  In your case you do, its the same USB sound device you want to have working in your guest but instead its claimed and working on your host.

This all circles back to the fact that the USB device isn't being passed through to your guest as something is stopping it and that something is likely because your host is grabbing it on boot, loading a driver against it and then setting it as your default sound device.  Because of this (and I am speculating a little here) qemu/kvm is unable to broker the release of the USB device from the host so it can pass it through to the guest, the really odd bit here is the lack of any error logs indicating that this conflict is happening.

Regards the idea of passing through your hosts internal sound card, other than this being pretty advanced stuff the error message you included in your last post suggested your hardware doesn't have the requisite capabilities for PCI passthrough.  Like you were concluding I think this maybe a step too far at the moment.

Now I know when you've tested stuff from this thread previous there's been some confusion and you've tested without the USB device actually being connected so if you can be extra vigilant on the next steps we might be able to change things around to remove any possibility of conflict by stopping the host from loading a driver against the USB sound card.

So with the USB sound device connected and from your host's terminal (so ignoring any virtual machines for now), please can you post back the results of the command ```
usb-devices
```

---

### Post by saurumanx on 2016-09-06
> **KillerKelvUK said:**
> 
So with the USB sound device connected and from your host's terminal (so ignoring any virtual machines for now), please can you post back the results of the command ```
usb-devices
```

```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8008 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=14
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=09 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=0512 Rev=06.11
S:  Manufacturer=Generic
S:  Product=BisonCam, NB Pro
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c7a ProdID=0603 Rev=02.00
S:  Manufacturer=EgisTec
S:  Product=EgisTec_ES603
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=03 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=07dc Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```

Also, I managed to get the device really passed through! It was so simply, I went "virtual machine -> pass through USB device". Not in the Virt-manager GUI, but in the bar on top, where 'file' 'edit' 'view' etc. are.... I didn't even realize this area existed. Anyhow, this got the driver installed fully, and my DAW software recognizes the device... but... every time I load the software with that driver activated, the VM becomes unusably slow, often freezing. CPU reaches 100% usage.

---

### Post by heiko_s on 2016-09-07
I'm with KillerKelvUK. I just like to add a few things:

> Error starting domain: unsupported configuration: host doesn't support passthrough of host PCI devices

The error above looks like as if your PC doesn't support any kind of passthrough. This is usually the case when there is no IOMMU support. Does your CPU support IOMMU? It must be turned on in the BIOS.

To check this, see [here under Part 1 - Hardware requirements]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692").

kvm supports several ways of passing through USB devices. My suggestion above was to pass through a PCI device, in fact the entire USB controller. This will only work when you have at least two separate controllers, and the one you pass through should be in a IOMMU group of its own. When you pass through a USB controller, you pass through a PCI device that sits on the PCI bus. Windows will recognize that as a hardware device and search for a suitable driver for the chipset this USB controller uses. Windows has actually direct access to this hardware.

The tutorial I referred to above describes how to set up a Windows 10 virtual machine using kvm and run the qemu command in a little script.

Another method to pass through the USB device is to specify the vendor:model ID. This is not the same as doing PCI passthrough as I suggested, since Windows won't see the actual USB controller, but only the device. That method is usually fine for mouse and keyboard, but it might not work with your sound device.

vfio drivers are not needed for USB, nor for PCI passthrough.

(Another thing: I know some people like fancy GUIs but I had quite bad experiences with the virt-manager application. What's the point of a GUI when one has to hack the XML files anyway?)

So, here are the steps I suggest:

1. See if your hardware supports IOMMU.

2. Check whether or not you got a spare USB host controller that you can pass through using PCI passthrough.

3. If yes, see if that USB host controller sits in its own IOMMU group.

4. If all is fine, you can pass the USB controller through to Windows using the PCI bus ID of the USB controller. In qemu terminology it looks like:
```
-device vfio-pci,host=08:00.0
```
where host=08:00.0 is the PCI bus ID of the host controller.

Check out the tutorial as you also need to unbind the USB controller from the Linux host. It's all described there.

For reference, the other method of passing through the USB device looks like this in the qemu command:
```
-usb -usbdevice host:045e:076c
```

---

### Post by KillerKelvUK on 2016-09-07
> **saurumanx said:**
> ```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8008 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=14
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=09 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=0512 Rev=06.11
S:  Manufacturer=Generic
S:  Product=BisonCam, NB Pro
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c7a ProdID=0603 Rev=02.00
S:  Manufacturer=EgisTec
S:  Product=EgisTec_ES603
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=03 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=07dc Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.04
S:  Manufacturer=Linux 4.4.0-36-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```

Also, I managed to get the device really passed through! It was so simply, I went "virtual machine -> pass through USB device". Not in the Virt-manager GUI, but in the bar on top, where 'file' 'edit' 'view' etc. are.... I didn't even realize this area existed. Anyhow, this got the driver installed fully, and my DAW software recognizes the device... but... every time I load the software with that driver activated, the VM becomes unusably slow, often freezing. CPU reaches 100% usage.

So saurumanx I got to ask...was your usb sound device connected when you ran the usb-devices command as I don't see it in the list?  Based on your previous post I would expect to see a where the P: Vendor= line shows "20b1"!

> Also, I managed to get the device really passed through! It was so simply, I went "virtual machine -> pass through USB device".

Is this really what it said or was it more like "Redirect USB device"?  I'm guessing this is redirection which is different to passthrough, however for your use case I couldn't comment on the pros or cons of the tech.

---

### Post by saurumanx on 2016-09-08
> So saurumanx I got to ask...was your usb sound device connected when you ran the usb-devices command as I don't see it in the list? Based on your previous post I would expect to see a where the P: Vendor= line shows "20b1"!

It was connected (plugged in a lit up) but I'm realizing recently it's not "recognized" every time I've plugged it in, maybe some other bug (is bug the right word for that?)

> Is this really what it said or was it more like "Redirect USB device"? I'm guessing this is redirection which is different to passthrough, however for your use case I couldn't comment on the pros or cons of the tech. 

Sorry, it said "redirect"

> 1. See if your hardware supports IOMMU.

My BIOS has no options for enabling VT-d. I was told it could support it, but maybe that was wrong.

I typed "dmesg | grep -e DMAR -e IOMMU" in the terminal as per the instructions, and I get this output.

```

[    0.000000] ACPI: DMAR 0x00000000DB9B6DA0 0000B8 (v01 INTEL  HSW      00000001 INTL 00000001)
[    0.035079] DMAR: Host address width 39
[    0.035081] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.035087] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.035088] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.035090] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
[    0.035091] DMAR: RMRR base: 0x000000dbea8000 end: 0x000000dbeb6fff
[    0.035092] DMAR: RMRR base: 0x000000dd000000 end: 0x000000df1fffff
[    0.035093] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.035094] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.035095] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.035311] DMAR-IR: Enabled IRQ remapping in x2apic mode

```

Which is not what the tutorial above says it should be, so I guess this means my CPU won't support it.

In this case I'm considering an entirely different plan - buying a second laptop, and remote-desktoping my current computer. So Windows Server and Linux Client. It would give the same experience, but I think run more smoothly (or maybe I'm wrong about VT-x?)

---

### Post by heiko_s on 2016-09-09
What's your CPU? The exact model.

Without VT-d you cannot do PCI passthrough. It may not be an issue if you can get it to work with USB passthrough. As it seems you weren't lucky with that, so far at least. I'm afraid I can't help here.

---

### Post by KillerKelvUK on 2016-09-09
> **saurumanx said:**
> It was connected (plugged in a lit up) but I'm realizing recently it's not "recognized" every time I've plugged it in, maybe some other bug (is bug the right word for that?)

Could be a software bug somewhere in the kernel however more likely a faulty usb device or usb port.  Have you tried it in other ports?  For now I'd recommend you forgot trying to pass it through a focus on figuring out if you have faulty hardware, if you can consistently get the usb device connected, recognised and working as your hosts soundcard then we can restart troubleshooting this thread.  We need to be confident that when you connect the device it powers up, the host detects and loads the driver thus it appears in the output of lsusb and usb-devices, without this we'll just go in circles like we have.

If the device is faulty or you have bad usb ports then figuring our whether you can passthrough your onboard sound maybe your only option hence working through your hardware specs with heiko_s is a good move.

---

### Post by saurumanx on 2016-09-10
> **KillerKelvUK said:**
> Could be a software bug somewhere in the kernel however more likely a faulty usb device or usb port.  Have you tried it in other ports?  For now I'd recommend you forgot trying to pass it through a focus on figuring out if you have faulty hardware, if you can consistently get the usb device connected, recognised and working as your hosts soundcard then we can restart troubleshooting this thread.  We need to be confident that when you connect the device it powers up, the host detects and loads the driver thus it appears in the output of lsusb and usb-devices, without this we'll just go in circles like we have.

If the device is faulty or you have bad usb ports then figuring our whether you can passthrough your onboard sound maybe your only option hence working through your hardware specs with heiko_s is a good move.

Ok, I realized it was a faulty USB cable (I have 3 cables I cycle between, my phone etc. use the same cable. One of them works inconsistently.)

Here's the output concerning my CPU, but in short it's an Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz

```
k@Komputerrr:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2701.054
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2943.527
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2749.148
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2700.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 4
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2758.957
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 5
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2855.039
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 6
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2871.808
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 7
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping    : 3
microcode    : 0x1e
cpu MHz        : 2838.691
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 7
initial apicid    : 7
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts
bugs        :
bogomips    : 5387.75
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:


```

---

### Post by saurumanx on 2016-09-11
Ok, good new guys; I switched to Fedora, and it's working!! I should have just done that a long time ago. The VM itself is a bit slow, but I think that can be improved through some tweaks.

I really don't like Fedora... don't know why. I like the idea of Arch. So I'm going to try and get Arch Anywhere working, and see if it works as well as or maybe better than Fedora; if not I'll just stick with Fedora.

---

