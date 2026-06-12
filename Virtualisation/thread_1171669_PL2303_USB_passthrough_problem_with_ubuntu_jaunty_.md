---
title: "PL2303 USB passthrough problem with ubuntu jaunty server"
date: 2009-05-27
forum: Virtualisation
---

### Post by paulskvm on 2009-05-27
Hello all,
I am trying to get a PL2303 usb serial converter to passthrough to a guest. It is part of X10 CM11 converter that I want to run on a guest running linuxmce or heyu.

To summarise, the host looks like it is giving the PL2303 to the guest, but the guest does not know about it.

The long version follows.

The host is a ubuntu 9.04 jaunty server called ent:
Linux ent 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

Here are my steps:

1. I created a guest jaunty server called heyu with the following command:

sudo virt-install \
--connect qemu:///system \
--name heyu \
--ram 1048 \
--disk path=/vm/heyu/heyu.img,size=10 \
--accelerate \
--vnc \
--cdrom /home/download/ubuntu/ubuntu-9.04-server-amd64.iso \
--os-type=linux \
--os-variant=ubuntuJaunty \
--hvm 

let ubuntu install and do the updates.

2. plug in the CM11 Pl2303 and the host sees the device:

me@ent:/dev$ lsusb | grep PL2303
Bus 006 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
me@ent:/dev$ 

3. the device is automatically created:

me@ent:/dev$ ls -l ttyUSB0
crw-rw---- 1 root dialout 188, 0 2009-05-25 22:01 ttyUSB0
me@ent:/dev$ 

4. shutdown the guest add the following to the guest's xml file heyu.xml:

<hostdev mode='subsystem' type='usb'>
<source>
<vendor id='0x067b'/>
<product id='0x2303'/>
</source>
</hostdev> 

Vendor id and product id are from the lsusb on the host.

5. on host define and start guest in virsh:

virsh # define /etc/libvirt/qemu/heyu.xml
Domain heyu defined from /etc/libvirt/qemu/heyu.xml

virsh # start heyu
Domain heyu started

virsh # 

6. check usb on host:

me@ent:/dev$ lsusb | grep PL2303
Bus 006 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
me@ent:/dev$ ls -l ttyUSB0
ls: cannot access ttyUSB0: No such file or directory
me@ent:/dev$ 

lsusb still shows the PL2303 and it has gone from /dev/ttyUSB0, so I think that the host has given it to the guest.

7. on the guest it is not there:

me@heyu:~$ lsusb
Bus 001 Device 002: ID 0627:0001 Adomax Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
me@heyu:~$ 

me@heyu:~$ ls -l /dev | grep -i usb
crw-rw---- 1 root   root    252,   1 2009-05-25 22:28 usbdev1.1_ep00
crw-rw---- 1 root   root    252,   0 2009-05-25 22:28 usbdev1.1_ep81
crw-rw---- 1 root   root    252,   3 2009-05-25 22:28 usbdev1.2_ep00
crw-rw---- 1 root   root    252,   2 2009-05-25 22:28 usbdev1.2_ep81
crw-rw---- 1 root   root    253,   0 2009-05-25 22:28 usbmon0
crw-rw---- 1 root   root    253,   1 2009-05-25 22:28 usbmon1
me@heyu:~$ 

The above output is the same as when the guest is started without the usb entry for the CM11/PL2303 in the heyu.xml file.

dmesg on the guest does not show anything for the converter:

me@heyu:~$ dmesg | grep 2303
me@heyu:~$ 

dmesg on the host shows the device being disconnected:
[627456.001375] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[627456.001389] pl2303 6-1:1.0: device disconnected
me@ent:/dev$ 

With a memory stick passthrough works ok from the same host (ent) to the same guest (heyu).

If anyone has made passthrough with a usb serial converter work or can help or give me any pointers as to what to try next I'd really appreciate it.

Thanks, Paul

---

### Post by syphr42 on 2009-10-17
Did you ever solve this issue? I have the exact same converter and I'm trying to do pretty much the same thing - get LinuxMCE to recognize it for an Insteon PLM (very similar to your X10 device). I have tried passing it to the guest as a USB device and as a serial device.

In the log when I try USB I see this:

usb: open device 6.2
husb: config #1 need -1
husb: 1 interfaces claimed for configuration 1
husb: grabbed usb device 6.2
usb_linux_update_endp_table: Broken pipe
Warning: could not add USB device host:067b:2303

However, when I try as serial everything seems to go just fine and I see an available /dev/ttyS1 that I can connect to with powerman's plmpower, but I can only send one command and then all I get is "plmpower: EOF on read" and it quits until I reboot the guest. plmpower on the host using /dev/ttyUSB0 works perfectly for any number of commands. I have been searching quite a lot and I'm stuck. Any help would be great.

P.S.

My USB config:

    <hostdev mode='subsystem' type='usb'>
      <source>
        <vendor id='0x067b'/>
        <product id='0x2303'/>
      </source>
    </hostdev>

My serial config:

    <serial type="dev">
      <source path="/dev/ttyUSB0"/>
      <target port="1"/>
    </serial>

---

