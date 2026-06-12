---
title: "Help creating windows VM with virt-install, windows hangs on setup?"
date: 2009-11-22
forum: Server Platforms
---

### Post by photoman355 on 2009-11-22
Hi 

I'm having trouble installing windows xp as a virtual machine using virt-install.  I'm able to create the VM no problem but when it is started and windows begins to install, it hangs at the beginning "Setup is starting Windows" (Before HD Format).  I'm using Virt-viewer to view remote from ubuntu client pc.

I've been following the guide here [https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests) and the only thing I can think it might be is the line:

"On Ubuntu Hardy, with KVM-62, the install of windows XP doesn't work when accelerated (ie, using --accelerate), so run the install without that argument, and replace qemu by kvm in the XML defintiion file (in /etc/libvirt/qemu) after the first reboot."

I can't find any reference to this in my qemu config file. Of course it may be something else that's making windows hang.  Here's my xml anyway:

> <domain type='qemu'>
  <name>WINDOWS</name>
  <uuid>095d5f04-6572-bffa-c451-345d256a3da7</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc'>hvm</type>
    <boot dev='cdrom'/>
  </os>
  <features>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
 <disk type='file' device='disk'>
      <source file='/var/lib/libvirt/images/windowsxp.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <source file='/var/lib/libvirt/images/winxp.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
 <interface type='bridge'>
      <mac address='00:16:3e:61:ac:12'/>
      <source bridge='br0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/5'/>
      <target port='0'/>
    </serial>
    <console type='pty' tty='/dev/pts/5'>
      <source path='/dev/pts/5'/>  
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
  </devices>
</domain>
My system info:

HP ML115 AMD Quad Core
Ubuntu Server 8.04LTS

Can anyone help?

---

### Post by photoman355 on 2009-11-23
Bump

---

### Post by devvy on 2009-11-23
I have the same issue. Looks like a problem in any version > 0.9.1 or so, since 0.9.0 was working fine.

My scenario: Ubuntu 9.10 64 bit as host, 64 bit Windows XP as guest on a Intel T3200 (without VT). Under Windows 7 64 bit I could install Windows XP 64 bit using version 0.9.0.

---

### Post by photoman355 on 2009-11-23
Awesome!  Solved and now have a nice new WinXP VM.  

Here's what I did.  Went through the original KVM install with a fine tooth comb making sure everything was installed correctly.  I used

> dpkg -lto list all my installed packages and checked these against the ones required for KVM.  I also installed the QEMU package as that had been referred to in a couple of other forums (Not convinced this was what solved the issue but I thought no harm having it installed).

> sudo apt-get install qemuNext I went through the instructions for guest creation [https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests) making sure i'd done everything.

This is what I think was wrong.  The changes to the XML listed in the tutorial are not clear as everything is lumped together in one list like this

> 
<domain type='kvm'>
  [...]
  <devices>
    [...]
    <disk type='file' device='cdrom'>
      <source file='//home/yhamon/windowsxpsp2.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
  </devices>
</domain>However these should be input into 2 different sections of the XML, here's a copy of my modified version.

> 
<domain type='kvm'>
  <name>WINDOWS</name>
  <uuid>095d5f04-6572-bffa-c451-345d256a3da7</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc'>hvm</type>
    <boot dev='cdrom'/>
  </os>
  <features>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
 <on_crash>restart</on_crash>
  <devices>
    <disk type='file' device='disk'>
      <source file='/var/lib/libvirt/images/windowsxp.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <source file='/var/lib/libvirt/images/winxp.iso'/>
 <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='00:16:3e:61:ac:12'/>
      <source bridge='br0'/>
    </interface>
    <serial type='pty'>
  <source path='/dev/pts/5'/>
      <target port='0'/>
    </serial>
    <console type='pty' tty='/dev/pts/5'>
      <source path='/dev/pts/5'/>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
  <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
  </devices>
</domain>
My original XML had qemu set as the default domain type so I think this is what solved the issue. 

Hope this helps.

---

