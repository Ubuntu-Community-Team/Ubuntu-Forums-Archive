---
title: "Doesn't have eth0 interface in VM, It can not connect to the Internet directly"
date: 2011-05-12
forum: Ubuntu Cloud and Juju
---

### Post by lemon1707 on 2011-05-12
I had installed Cloud(Ubuntu 11.04 Natty) on 2 machines ( CC,SC,Walrus,Cloud on 1 machine, and Nc on 1 machine). They connect direct to router. Each machine just have one Nic. I installed images from store and test successfully. But when I installed Ubuntu 9.10 Karmic image :

$ sudo kvm -m 512 -drive file=ubuntu9-10.img,if=scsi,index=0,boot=on -boot=c -net nic,model=e1000 -net tap -nographic -vnc :0

Its command talks VM using interface with model e1000 (default of Eucalyptus). And -net tap : connect direct to internet using the host's bridge.

Then, I can log into VM by using Vnc Viewer, but from VM, it can not connect to the internet. I type in VM :
$ ifconfig 
It appear just one interface : lo

Please help me to solve that problem. I don't konw why It doesn't have eth0 interface.

---

### Post by WthIteh on 2011-05-12
did u tried:
```
ifconfig eth0 up
```
command?

---

### Post by lemon1707 on 2011-05-12
One more thing, That is in the /etc/network/interfaces => It have tow interfaces. 'lo' interface and 'eht0' interface. The configuration of eth0
auto eth0
iface eth0 inet dhcp

Then command "ifconfig", just appear "lo" interface with ip. When I command : "ifup eth0", It doesn't work. 
Any experts there, please help me correct that problem. 
Sorry about my english...

---

### Post by lemon1707 on 2011-05-12
thank WthIteh replying,
when i "ifconfig eth0 up". It appear error :
ubuntu@ubuntu: ~$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

Could you give me exactly problem and how to fix that please ?

---

### Post by WthIteh on 2011-05-12
The VM needs a way to know about (virtual) NIC. In this case, kvm and qemu work in the same way. See [http://www.linux-kvm.org/page/Networking](http://www.linux-kvm.org/page/Networking) for details on preparing VM NIC.

---

### Post by lemon1707 on 2011-05-12
Hi WthIteh
I had configured br0 for host OS before install VM. Should we have another solution to fix that?
I think you said that is correct problem. When I create image I always  use "kvm" command instead of "qemu", but i think in my system, It maybe  runs Qemu. Is it important?
Let explain more for me, I spend long time to solve that !

---

### Post by WthIteh on 2011-05-12
> **lemon1707 said:**
> Hi WthIteh
I had configured br0 for host OS before install VM. Should we have another solution to fix that?
I think you said that is correct problem. When I create image I always  use "kvm" command instead of "qemu", but i think in my system, It maybe  runs Qemu. Is it important?
Let explain more for me, I spend long time to solve that !
The qemu and kvm are not (probably) the source of problem.
So where you installed the ifup script? You could also add
"-net tap,script=/path/to/qemu-ifup" option to be sure.

---

### Post by lemon1707 on 2011-05-12
hi WthIteh,
I'm in process install Ubuntu 9.10 Karmic, I had adjust the bridge="br0" in /etc/vmbuilder/libvirt/libvirtxml.tmpl, then I restart host OS and relaunch the VM by commnand :
$ sudo kvm -m 512 -drive file=ubuntu9-10.img,if=scsi,index=0,boot=on -boot c -net nic,vlan=0,model=e1000, -net tap -nographic -vnc :0

I log into VM by using VNC viewer and command "ifconfig" -> It appears IP of eth0, connect direct to internet via br0 ( br0 , the bridge of host ).
Now, I finished installation OS, I will register it with UEC. I hope no error happen.
Thank you a lot. I hope you could guide me to bundle successful Ubuntu 9.10 Karmic into UEC.

---

### Post by lemon1707 on 2011-05-12
Unfortunately, It's still doesn't work. 
When I registerd image onto UEC, It's doesn't work correctly. It's can connect direct to internet when I using the command :
$ sudo kvm -m 512 -drive file=ubuntu9-10.img,if=scsi,index=0,boot=on  -boot c -net nic,vlan=0,model=e1000, -net tap -nographic -vnc :0
Then I upload it onto UEC, It doesn't connect to internet, the outsite can't connect to instance too.
It maybe I didn' point the VM's interface to Host bridge's interface.
Could you give me more infomation, WthIteh ?
Please help me, I spend over a week to configure.

---

### Post by Rusty au Lait on 2011-05-12
> **lemon1707 said:**
> I had installed Cloud(Ubuntu 11.04 Natty) on 2 machines ( CC,SC,Walrus,Cloud on 1 machine, and Nc on 1 machine). They connect direct to router. Each machine just have one Nic. I installed images from store and test successfully. But when I installed Ubuntu 9.10 Karmic image :

$ sudo kvm -m 512 -drive file=ubuntu9-10.img,if=scsi,index=0,boot=on -boot=c -net nic,model=e1000 -net tap -nographic -vnc :0


Does this mean you loaded a Karmic image onto an instance you downloaded from the store and successfully started and are now trying to run a VM of the Karmic image on your instance?
I am confused as to why you are using kvm and/or Qemu.

---

### Post by lemon1707 on 2011-05-12
Hi Justy, thank you for replying
Yes, you are right. I installed Ubuntu 9.10 Karmic I386 from store first, I started it successfully. I mean I can ping it from outsite and It's always running state.
Then I downloaded a Ubuntu 9.10 Karmic iso file from [http://www.ubuntu.com/download](http://www.ubuntu.com/download) for bundling.

I describe the install process for more detail :

1/ First, I create partition on the host with command, notice that host had bridge with namd br0 runnind as eth0 physical:

$ kvm-img create -f qcow2 image.img 5G

2/ Then, copied ubuntu-9.10.iso into /home/lemon1707 to install with command :
$ sudo kvm -m 512 -cdrom ubuntu-9.10.iso -drive file=ubuntu9-10.img,if=scsi,index=0,boot=on -boot d -net nic,vlan=0,model=e1000 -net tap -nographic -vnc :0


3/ When the process installation finished :
I check the VM ip with ifconfig, It doesn't appear eth0 ip, but in the /etc/network/interfaces it had configurated :
auto eth0
iface eth0 inet dhcp


4/ Then I changed bridge='br0' in the file /etc/vmbuilder/libvirt/libvirtxml.tmpl on the host system.
After that I relaunched VM with command,  The VM's eth0 interface up and VM can connect direct to internet.
$ sudo kvm -m 512 -drive file=ubuntu9-10.img,if=scsi,index=0,boot=on -boot c -net nic,vlan=0,model=e1000 -net tap -nographic -vnc :0


5/ I copied initrd.img-2.6.31-14-server and vmlinuz-2.6.31-14-server from VM to host. I registerd it with UEC by using memdisk command. Then I ran it by using Hybridfox, checked the status is running.
Public Ip is 192.168.1.100, private ip 172.19.1.2

But I still can not ping or ssh from outsite ( I had opened ports ). The best thing to do is to let VM's interface know where it can bind with the host's bridge interface for VM can connect direct to outsite.

Are there any problem in the process ? Should I reinstall because I think we should change bridge='br0' in the file /etc/vmbuilder/libvirt/libvirtxml.tmpl before install VM's OS to make sure they can affect ?
Any ideas for that problem ?

---

