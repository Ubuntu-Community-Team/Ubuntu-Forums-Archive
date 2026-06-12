---
title: "CentOS 8 Virtualization Host; Ubuntu VM install help"
date: 2020-03-31
forum: Virtualisation
---

### Post by ch33zw1z on 2020-03-31
I'm looking for some help with an Ubuntu VM install problem. CentOS 8 is my virtualization host. My linux background is mostly debian based, and I'm kinda forcing myself to learn Redhat due to employment opportunities. 

Goal: CentOS host, Ubuntu VM, pihole

Here's the original thread I posted at the centos forums:

[https://forums.centos.org/viewtopic.php?f=54&t=73883&p=311269#p311269](https://forums.centos.org/viewtopic.php?f=54&t=73883&p=311269#p311269)

I'm to the point now where it looks like the VM is installing, but I land at initramfs. I'm not sure how to kick off a manual install, or if it even see's the 18.04 server ISO to install from.

I am hoping someone here could point me in the right direction, any advice or assistance is appreciated

---

### Post by TheFu on 2020-04-01
Which hypervisor?

---

### Post by ch33zw1z on 2020-04-02
Kvm

---

### Post by TheFu on 2020-04-02
Which hypervisor interface?  virsh or virt-manager?
virt-manager is much like vbox or VMware interfaces.

---

### Post by ch33zw1z on 2020-04-02
I'm using virsh. I'm doing it all CLI, no gui. I made some progress and got the bridge setup, and got the command to perform the install. after the install, I rebooted the VM and now can't get to the serial console, and the IP isn't pinging. So I've still got some work to do. I updated my original thread with the progress, I can post it here as well if it's preferred.

---

### Post by TheFu on 2020-04-02
You do know that virt-manager runs on a workstation from anywhere that has ssh access to the VM host, right?  The server doesn't need any GUi stuff, but your workstation just needs libvirt + virt-manager and to be in the libvirtd group on both the workstation and KVM host.  This doesn't need to be hard.

Many organizations use something like cobbler or virt-install to stand up VMs. I&#8217;ve never used either.  Did read about an entire university network having thousands of workstations OSes reloaded, wiping anything on them previously when a cobbler setup was misconfigured a few years ago. impressive.

---

### Post by ch33zw1z on 2020-04-02
No, I wasn't aware, so thanks for the info. 

It doesn't have to be hard, using a GUI would be easier, but I'm not really going for ease as much as learning what's happening and using the CLI.

---

### Post by ch33zw1z on 2020-04-05
Update: I successfully got the Ubuntu VM installed and can connect. I think my towards the end my problems were two fold:

1) During the install, I was letting the installer run the DHCP config. The last install I did, I canceled out of the DHCP setup, and configured the static IP like I wanted. I had removed the extra arguement statement from my install command already.

2) I was not checking off the openssh software box during the install, so the VM had no SSH service installed.

Latest command:
```
virt-install --name pihole --memory 2048 --vcpus 1 --disk size=16 --install ubuntu18.04 --location /media/ubuntu-18.04.4-live-server-amd64.iso  --cdrom /media/ubuntu-18.04.4-live-server-amd64.iso --nographics --os-variant ubuntu18.04 --network bridge:virbr2 --extra-args="console=tty0 console=ttyS0,115200n8"
```

So this doesn't appear to configure a permanent serial console either, just a console for the install. I haven't researched how to include it in the command, but I started some web searching and here's two links to resolve the current serial console config issue

[https://serverfault.com/questions/364895/virsh-vm-console-does-not-show-any-output](https://serverfault.com/questions/364895/virsh-vm-console-does-not-show-any-output)
[https://wiki.archlinux.org/index.php/working_with_the_serial_console#GRUB](https://wiki.archlinux.org/index.php/working_with_the_serial_console#GRUB)

I'm going to have to modify the xml config for the VM, and grub. I don't want to rely on SSH only

xml serial config
```
<serial type='pty'>
      <source path='/dev/pts/1'/>
      <target type='isa-serial' port='0'>
        <model name='isa-serial'/>
      </target>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/1'>
      <source path='/dev/pts/1'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
```

grub config
```
 cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_TERMINAL=serial
GRUB_SERIAL_COMMAND="serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1"

```

---

