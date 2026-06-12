---
title: "Windows XP Install using virt-install"
date: 2008-07-27
forum: Virtualisation
---

### Post by pcman312 on 2008-07-27
I've been able to get the virtual machine running using [https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM"), however, during the install of Windows XP, it reboots and then requires the CD to be in the tray. I'm running this from an .iso file located in ~/VM/windows.iso. When I get to that point of needing the CD, it cannot find the cd. Is there a way of mounting the iso to a virtual cd drive within the VM so it can finish its installation?

Here's a screenshot for reference:
[Screenshot](http://www.athemon.com/misc_images/winxp.png)

---

### Post by pcman312 on 2008-07-28
Bump

---

### Post by ax2008 on 2008-07-31
Bump, facing same issue.

---

### Post by Yann2 on 2008-07-31
Hello, yes - wanted to add this to the wiki but for some reason didnt yet.
Add this to your /etc/libvirt/qemu/yourvm.xml :

  <disk type='file' device='cdrom'>
      <source file='//home/yhamon/win2000server.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>

in the <devices> section; then run virsh, shutdown the VM, redefine the VM:

define /etc/libvirt/qemu/yourvm.xml

And start the VM again; this should mount the iso and enable you to continue the install. Let me know if this work for you (it should).

---

### Post by ax2008 on 2008-07-31
Yes, it does work, but one extra '/' should be removed from <source file ... /> -

<disk type='file' device='cdrom'>
<source file='/home/yhamon/win2000server.iso'/> 
<target dev='hdc' bus='ide'/>
<readonly/>
</disk>

---

### Post by ax2008 on 2008-08-01
Then I replaced "qemu by kvm in the XML file once installed", I started the VM using "virsh -c qemu:///system start xp", I found the keyboard input is messed up for the VM - type "qwer", see "c.gv"

Any solution?

---

### Post by ax2008 on 2008-08-02
The keyboard input problem is seen through "virt-viewer"

---

### Post by Yann2 on 2008-08-03
Are you sure you selected the correct keymap during the install? I didn't have this bug...

---

### Post by ax2008 on 2008-08-04
I believe so - everything is fine if kqemu or qemu is used instead of kvm. Another problem is IP addresses on kvm Windows guest can't be pinged from host or the other Linux guests, arping is incomplete.

"
......$ sudo cat /etc/libvirt/qemu/xp2.xml
<domain type='kvm'>
  <name>xp2</name>
  <uuid>2ffe3992-d81d-c297-2a2b-b0a9d232dd8b</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/home/arthur/vm/xp2.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <source file='/home/arthur/iso/winxp_oem.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='00:16:3e:5b:7f:2c'/>
      <source bridge='br0'/>
    </interface>
    <interface type='network'>
      <mac address='00:00:30:00:a0:10'/>
      <source network='default'/>
    </interface>
    <interface type='network'>
      <mac address='00:00:30:00:a0:12'/>
      <source network='default1'/>
    </interface>
    <interface type='network'>
      <mac address='00:00:30:00:a0:14'/>
      <source network='default2'/>
    </interface>
    <interface type='network'>
      <mac address='00:00:30:00:a0:16'/>
      <source network='default3'/>
    </interface>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>

......$ sudo more /etc/libvirt/qemu/networks/default.xml
<network>
  <name>default</name>
  <uuid></uuid>
  <bridge name="virbr%d" />
  <ip address="172.16.117.1" netmask="255.255.255.0">
  </ip>
</network>

......$ sudo more /etc/libvirt/qemu/networks/default1.xml
<network>
  <name>default1</name>
  <uuid>c6f30123-fc91-741b-6dbb-65a6b39cbb49</uuid>
  <bridge name='virbr%d' stp='on' forwardDelay='0' />
  <ip address='192.168.74.1' netmask='255.255.255.0'>
  </ip>
</network>

......$ sudo more /etc/libvirt/qemu/networks/default2.xml
<network>
  <name>default2</name>
  <uuid>6f0b027b-e23d-de01-30d7-76cc0439b371</uuid>
  <bridge name='virbr%d' stp='on' forwardDelay='0' />
  <ip address='172.16.139.1' netmask='255.255.255.0'>
  </ip>
</network>

......$ sudo more /etc/libvirt/qemu/networks/default3.xml
<network>
  <name>default3</name>
  <uuid>fbc50e8b-e800-b8ba-c815-7dd02d64db20</uuid>
  <bridge name='virbr%d' stp='on' forwardDelay='0' />
  <ip address='192.168.249.1' netmask='255.255.255.0'>
  </ip>
</network>
"

---

### Post by eival on 2008-08-05
if you use the VM box from Sun they have an easy to follow setup, an theres a menu when you start it up that lets you easily click each hardware device on your computer an tell it to mount or unmount from the VM, so in this case you could add your CD ROM drive with just a click, no need for terminal.

---

### Post by ax2008 on 2008-08-05
The keyboard input problem is seen on a box with _not_ Intel Core 2 T7200 _but_ AMD Opteron 2352 processor

---

### Post by ax2008 on 2008-08-06
> **ax2008 said:**
> The keyboard input problem is seen on a box with _not_ Intel Core 2 T7200 _but_ AMD Opteron 2352 processor

It turns out that "apt-get install kvm ......" on ubuntu 8.04 actually installs kvm-62. The keyboard-input and network problems go away after kvm-64 is compiled and installed. Please refer to -
[http://kvm.qumranet.com/kvmwiki/Guest_Support_Status](http://kvm.qumranet.com/kvmwiki/Guest_Support_Status)

---

