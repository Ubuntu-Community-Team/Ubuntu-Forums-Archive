---
title: "did (dumb) upgrade to 10.04 and can no longer start kvm/qemu machines"
date: 2010-01-24
forum: Virtualisation
---

### Post by extendedping on 2010-01-24
Hi I recently moved away from windows to use linux ubuntu for learning recording (moved to ubuntu 9.10 regular and installed kernel-rt and many of the ubuntu studio packages. well along the way I got interested in learning virtualization and installed a few kvm/qemu machines (centos and freebsd). I was really enjoying. well of course when I heard I could upgrade to ubuntu 10.04 like an idiot I did it (though my wife told me wait till they release the stable version). anyway the upshot is I cannot start my virtual machines any more from either the virt-manager app or from virsh -c qemu:///system start "machinename". I guess I could just back up all my pics etc and reinstall to the 9.10 version but I figured I'd try to fix this first. here is all the diagnostic info I can think to give. I have tried booting to the old kernel to no avail my current one is 

1) brad@ubuntu:/var/lib/libvirt/images$ uname -a
Linux ubuntu 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT Tue Jan 12 11:01:03 UTC 2010 x86_64 GNU/Linux

2) brad@ubuntu:/etc/libvirt/qemu$ ls -l
total 20
-rw------- 1 root root 1315 2010-01-20 10:04 baby.xml
-rw------- 1 root root 1317 2010-01-22 12:32 clunk.xml
-rw------- 1 root root 1230 2010-01-19 11:30 mama.xml
drwxr-xr-x 3 root root 4096 2010-01-23 13:29 networks
-rw------- 1 root root 1230 2010-01-23 12:15 test.xml

3)  brad@ubuntu:/var/lib/libvirt/images$ ls -l
total 14142984
-rwxr-xr-x 1 root root 12884901888 2010-01-22 13:08 baby.img
-rwxr-xr-x 1 root root 12884901888 2010-01-22 13:08 clunk.img
-rw------- 1 root root 12884901888 2010-01-22 14:59 mama.img
-rwxr-xr-x 1 root root 12884901888 2010-01-23 12:17 test.img

4) output of attempting to start vm "test" 

on virt-manager
"Error starting domain: internal error unable to start guest: qemu: could not open disk image : No such file or directory"

and the details tab
"Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 493, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 558, in startup
    self.vm.create()
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 300, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error unable to start guest: qemu: could not open disk image : No such file or directory"

5) test.xml from the /etc/libvirt/qemu$ dir

<domain type='kvm'>
  <name>test</name>
  <uuid>23287fe4-ae17-e8dc-543b-6a8199050b4c</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.11'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/var/lib/libvirt/images/test.img'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='network'>
      <mac address='00:16:36:53:46:75'/>
      <source network='network1'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='en-us'/>
    <sound model='es1370'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
</video>
  </devices>
</domain>

6)output of tail -f /var/log/libvirt/qemu/test.log when trying to start the machine.

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.11 -m 1024 -smp 2 -name test -uuid 23287fe4-ae17-e8dc-543b-6a8199050b4c -monitor unix:/var/lib/libvirt/qemu/test.monitor,server,nowait -boot c -drive file=/var/lib/libvirt/images/test.img,if=ide,index=0,boot=on -drive file=,if=ide,media=cdrom,index=2 -net nic,macaddr=00:16:36:53:46:75,vlan=0,name=nic.0 -net tap,fd=17,vlan=0,name=tap.0 -serial pty -parallel none -usb -vnc 127.0.0.1:1 -k en-us -vga cirrus -soundhw es1370 
qemu: could not open disk image : No such file or directory

7) tail of /var/log messages upon failed start of "test"

8) finally I typed this command by mistake instead of "start" I typed connect, I wonder if that error message means anything

virsh # connect test
error: Failed to connect to the hypervisor
error: internal error unexpected Xen URI path 'test', try ///var/lib/xen/xend-socket

thanks I know that is a million things (and probably nobody will read it all) but I did not know that output would be useful. btw I can in fact still clone a machine using the virt-clone command.

---

### Post by extendedping on 2010-01-25
ok guess a reinstall is in order, never again a development version...

---

### Post by oldefoxx on 2010-01-25
I'm not an expert, But I know you have several choices:

(1) Run from a LiveCD and save /home and every account, then do a reinstall and recover what is in /home that you need.

(2) Just do a reinstall, but pick manual partitioning mode (last choice down) and indicate the same partition structure again.  Don't reformat, and you get to keep /home, accounts, and some config settings.

(3) To combined first two steps together, you can keep /home and accounts. but by using LiveCD to get going, you can find and delete all other folders in partiton which gets rid of almost all the configuration settings as well.  The basic command looks like rm -R /media/part/folder where part is the mounted partition's mount point, and the folder is all of the system folders, such as bin, boot, dev, lib, sbin, sys, and so on.

Because you are using sudo mode, you may have to reset some folder and file rights later so user can access, but chmod will work for that.

---

### Post by hernad on 2010-01-25
I have the same problem, filled bug

[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/512259](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/512259)

---

### Post by hernad on 2010-03-18
after system update everything is ok

---

### Post by leitor on 2010-05-05
I just upgraded from Karmic to Lucid, same problem and messages as reported here. Hernad, exactly what was the "system update" you did to fix the problem? I've done an "apt-get update;apt-get upgrade" but that made no difference...

---

