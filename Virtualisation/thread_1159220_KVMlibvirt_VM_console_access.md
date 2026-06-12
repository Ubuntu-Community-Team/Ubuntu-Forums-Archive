---
title: "KVM/libvirt VM console access?"
date: 2009-05-14
forum: Virtualisation
---

### Post by z0mbix on 2009-05-14
I'm setting up KVM and libvirt on hardy. Everything is working ok if I use VNC to install the hosts, but I wish to use the cli to administer these VMs instead of VNC. I have the following VMs running:

root@vm-host-dmz:~# virsh list
Connecting to uri: qemu:///system
 Id Name                 State
----------------------------------
 28 DevVM-01             running
 30 DevVM-02             running

When I try to access the console, I get the following error:

root@vm-host-dmz:~# virsh console DevVM-01
Connecting to uri: qemu:///system
No console available for domain

root@vm-host-dmz:~# 

I want the KVM equivalent of xm console DevVM-01.

How can I setup console access? If I define a console in the xml config file and virsh define it, the console settings just get removed.

---

### Post by geekshlby on 2009-05-14
Check to determine if a console is defined for a VM:

virsh ttyconsole DevVM-01

If null is returned define one:

virsh edit DevVM-01

Example working console:

```
<serial type='pty'>
 <source path='/dev/pts/2'/>
 <target port='0'/>
</serial>
<console type='pty' tty='/dev/pts/2'>
 <source path='/dev/pts/2'/>
 <target port='0'/>
</console>
```
Note: using "virsh edit" will check syntax and redefine the VM for you once you exit the editing environment.

---

### Post by z0mbix on 2009-05-14
Thanks for the reply. I'm running Hardy. virsh doesn't seem to have the edit command. I have libvirt-bin version 0.4.0-2ubuntu8.1. Any other ideas? Maybe hardy's older version or libvirt-bin doesn't support consoles.

---

### Post by vertigo23 on 2009-05-15
I'm running hardy also, and adding the <serial> and <console> devices isn't working for me.  Here's my domain XML:

```

<domain type='kvm' id='2'>
  <name>mp-testbed01</name>
  <uuid>b996eded-ed4c-d6b6-d28d-13443849070e</uuid>
  <memory>262144</memory>
  <currentMemory>262144</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/home/AUTOHOME/alex/VMs/p4-hot/root.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='network'>
      <mac address='52:54:00:e7:35:c2'/>
      <source network='default'/>
      <target dev='vnet1'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5900' listen='10.10.4.57'/>
    <serial type='pty'>
     <source path='/dev/pts/2'/>
     <target port='0'/>
    </serial>
    <console type='pty' tty='/dev/pts/2'>
     <source path='/dev/pts/2'/>
     <target port='0'/>
    </console>
  </devices>
</domain>

```

When I run "virsh define domain.xml", it doesn't error, but neither the serial nor the console sections show up when I then dump the XML in virsh.

---

### Post by Blinkiz on 2009-05-31
am also looking for the answer to this.
So am bumping this one and subscribing to this thread.

---

### Post by netangel on 2009-09-24
There is a solution.

Just after starting the VM, you can do :
```
sudo tail /var/log/libvirt/qemu/<vm_name>.log
```
Here is a sample reply :
```
/usr/bin/kvm -M pc -m 2048 -smp 4 -monitor pty -drive file=/var/lib/libvirt/images/<vm_name>.img,if=ide,boot=on -net nic,macaddr=00:16:ff:09:28:1e,vlan=0 -net tap,fd=4,script=,vlan=0 -usb -vnc 127.0.0.1:1 
char device redirected to /dev/pts/1 
```
The last line is really important. It tells you that kvm console is accessible to /dev/pts/X tty. Here, X is 1.

Install the socat command (sudo apt-get install socat) and type in :
```
sudo socat - /dev/pts/1
```
You are now connected to kvm console. Type for example :
```
info snapshots
```
or any other kvm command.

BE CAREFUL, to exit from that console, just press Ctrl+C (to quit socat actually).

My problem now is when the VM has run for a while, there is no more the "char device redirected to /dev/pts/X" in the logs ... so I search a method to retreive the actual pts which the VM points to.

If you look at the file descriptors of the kvm VM (lsof -p <kvm_process_number>, you found :
```
...
kvm     6249 root   10u   CHR    5,2                 1675 /dev/ptmx
...

```
The process has opened /dev/ptmx. The problem I'm facing is that I don't know any mean of retreiving the pts part (the slave part) of that opened master tty. There is just a C function called "ptsname", but I didn't find a script command to do the same ... Does someone know about that ?

---

### Post by nullzone on 2010-07-19
Another way is to define a serial console.

Add a serial device to be used as a conseole in the libvirt XML file of your virtual machine (it is a device so, add that inside the <device></devices> directives):

```

<serial type="pty">
      <source path="/dev/pts/3"/>
      <target port="1"/>
    </serial>

```Go into your Virtual machine (use ssh, vnc or anyway) and define a tty to be used as a serial console. To do this just create a new upstart script, lets say **/etc/init/ttyS0.conf** with this code:

```

# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -L 38400 ttyS0 vt102

```In your core server, reload your libvirt-bin and reboot the machine (it is necesary so the kernel will detect the new serial defined previously in your VM XML file):

```
$ sudo reload libvirt-bin
$ sudo virsh shutdown <your_vm_name>
... wait ...
$ sudo virsh start <your_vm_name>

```You will see the serial in your kernel/dmesg logs after the boot as follow:[INDENT][I]serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[/I][/INDENT]It is all ... you have now a console defined and up-&-running. To log on in your virtual machine you can now use:

```
$ sudo virsh console <your_vm_name>
```----

Aditionally, you could get the boot-messages in the console and not only a login console after the full boot just editiing inside the virtual machine the /etc/default/grub file as follow:

```
GRUB_CMDLINE_LINUX="console=ttyS0,38400n8 console=tty0"
```Some ppl talk about setting the GRUB_TERMINAL variable with a "serial" value so your should have a complete serial access from the beginning to the grub boot. Tbh, I havent need this yet so... if anybody have done any test I'd apreciate a clear input about how to get this working correctly.

Cheers,

Nullzone

---

### Post by Blinkiz on 2010-07-20
Nice guide nullzone, thanks

---

### Post by Harpette on 2011-01-07
> **nullzone said:**
> 

<serial type="pty">
      <source path="/dev/pts/3"/>
      <target port="1"/>
    </serial>


In my (limited) experience, specifying a source path is unnecessary, since it automatically gets assigned one after you boot the vm. Also, a target port of "0" works for me.

> *create a new upstart script, lets say **/etc/init/ttyS0.conf***

I read elsewhere a same script defined as /etc/event.d/ttyS0 ; what's the difference ? Which is better / more appropriate ?

> [I]In your core server, reload your libvirt-bin:

$ sudo reload libvirt-bin[/I]

Don't need to do that, perhaps because i didn't specify a source path above

Other than these, thanks Nullzone for your guide which did help me much.

---

### Post by addihetja on 2011-07-05
I followed these directions but I still can't connect to the console:

> virsh # start Ubuntu804
Domain Ubuntu804 started

virsh # console Ubuntu804
No console available for domain

This is what I got from /var/log/libvirt/qemu/Ubuntu804.log:
> LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 2048 -smp 1 -name Ubuntu804 -uuid 3e5f089d-dc8b-a642-c108-d3408d040230 -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/Ubuntu804.monitor,server,nowait -monitor chardev:monitor -boot c -drive file=/home/truenorth/ubuntu-kvm/tmpfAmN6M.qcow2,if=ide,index=0,boot=on,format=qcow2 -net nic,macaddr=52:54:00:ad:da:bf,vlan=0,model=virtio,name=virtio.0 -net tap,fd=55,vlan=0,name=tap.0 -chardev null,id=serial0 -serial chardev:serial0 -parallel none -usb -vnc 127.0.0.1:0 -vga cirrus 
pci_add_option_rom: failed to find romfile "pxe-virtio.bin"


Here is my /etc/libvirt/qemu/Ubuntu804.xml file:
> <domain type='kvm'>
  <name>Ubuntu804</name>
  <uuid>3e5f089d-dc8b-a642-c108-d3408d040230</uuid>
  <memory>2097152</memory>
  <currentMemory>2097152</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <serial type='tty'>
    <source path='/dev/ttyS0'/>
    <target port='0'/>
  </serial>
  <console type='tty' tty='/dev/ttyS0'>
    <source path='/dev/ttyS0'/>
    <target port='0'/>
  </console>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/home/admin/ubuntu-kvm/tmpfAmN6M.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:ad:da:bf'/>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>


Here is my /etc/init/ttyS0.conf:
> s service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -L 38400 ttyS0 vt102

There is no GUI installed on the server (which is running 11.04, btw) so I need to run virsh. I've tried all sorts of variations of this ([]("http://libvirt.org/formatdomain.html") f.x.

---

### Post by asianscion on 2012-05-02
I know this thread is old but I was searching for this exact problem and was having a tough time with it.

Here is the solution I found:

Setup:

Macbook Pro running Mac OS X 10.7.3
Dell R210 Server running Ubuntu 10.04 with KVM-QEMU installed

Settings on Mac
> MacBook-Pro:~ user$ cat ~/.ssh/config 
ServerAliveInterval=60
ForwardX11=yes
MacBook-Pro:~ user$

Command on server
> root@vmhost1:~#  virt-viewer name-of-VM

If you get something along the lines of
> (virt-viewer:2399): Gtk-WARNING **: cannot open display: localhost:10.0
Log out and log back in.  Try virt-viewer again, and it should work.

---

