---
title: "kvm libvirt migration problem"
date: 2011-05-06
forum: Server Platforms
---

### Post by panhcn on 2011-05-06
Hi everyone:

I am new here :D

I am using kvm and libvirt on my Dell server. Now i am trying to migrate one virtual machine from a physical server to another. However, I failed everytime. 

In virsh on physicalServer1, I typed:[INDENT] virsh #  migrate virtualmachine1 qemu+ssh://username@physicalServer2/system
error: operation failed: migration to 'tcp: physicalServer2:49163' failed: migration failed
[/INDENT]Then I searched FAQ part on libvirt.org [http://wiki.libvirt.org/page/FAQ](http://wiki.libvirt.org/page/FAQ)
it says:[INDENT]** error: operation failed: migration to '...' failed: migration failed **

 This is an error often encountered when trying to migrate with  QEMU/KVM. [COLOR=Red]This typically happens with plain migration, when the source  VM cannot connect to the destination host[/COLOR]. You will want to make sure  your hosts are properly configured for migration (see the migration  section of this FAQ) 



[/INDENT]I managed to ssh physicalServer2 in virtualmachine1 shell. So the above red part did not explain my failure. 

I also open ports on physicalServer2, iptables -L shows following information:[INDENT]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
 ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
 ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
 [COLOR=Red]ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpts:49152:49215[/COLOR] 


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
 ACCEPT     all  --  anywhere             [192.168.122.0/24]("http://192.168.122.0/24")    state RELATED,ESTABLISHED 
ACCEPT     all  --  [192.168.122.0/24]("http://192.168.122.0/24")     anywhere            
 ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
 ACCEPT     all  --  anywhere             [192.168.122.0/24]("http://192.168.122.0/24")    state RELATED,ESTABLISHED 
ACCEPT     all  --  [192.168.122.0/24]("http://192.168.122.0/24")     anywhere            
 ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


[/INDENT]The /var/log/libvirt/qemu/virtualmachine1.log on physicalServer2:[INDENT]2011-05-06 13:37:30.708: starting up
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin  QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.14 -enable-kvm -m 2048 -smp  1,sockets=1,cores=1,threads=1 -name openjudge-test -uuid  a8c704bc-a4f9-90db-3e57-40e60b00aac1 -nodefconfig -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/virtualmachine1.monitor,server,nowait -mon chardev=charmonitor,id=monitor,mode=readline -rtc base=utc -boot c -drive file=/media/nfs/virtualmachine1.img,if=none,id=drive-ide0-0-0,format=raw -device ide-drive,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0 -drive if=none,media=cdrom,id=drive-ide0-1-0,readonly=on,format=raw -device ide-drive,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 -netdev tap,fd=20,id=hostnet0 -device rtl8139,netdev=hostnet0,id=net0,mac=00:16:36:8a:22:a0,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -usb -vnc [127.0.0.1:2]("http://127.0.0.1:2/") -vga cirrus -incoming tcp:[0.0.0.0:49163]("http://0.0.0.0:49163/") -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x4
 char device redirected to /dev/pts/0
2011-05-06 13:37:30.915: shutting down


[/INDENT]The /var/log/libvirt/qemu/virtualmachine1.log on physicalServer1 is empty.

Both physical servers are using Ubuntu 11.04. The libvirt and kvm used are installed by apt-get. The libvirt version is 0.8.8.

Is there anyone can help me? Thanks for help!:P:P:P

---

### Post by TheR on 2011-05-08
qemu+ssh://username@physicalServer2/system 

As far as I know root must be enabled in order to use virsh on remote system and since you are using username@... this might not work.

I would check and recheck if all devices are present on destination as well as on source system. Although in my case this kind of error would always be recorded in the log of the destination machine.

by
TheR

---

### Post by panhcn on 2011-05-09
Thanks for your reply.

However, I tried  			 		   		 		 		qemu+ssh://root@physicalServer2/system, it reported the same error message. 

Also, the servers are the same, same brand, same type, same CPU, same memory. The log on destination server is pasted in my question.

Thanks for help.

---

### Post by TheR on 2011-05-10
> **panhcn said:**
> Thanks for your reply.

However, I tried  			 		   		 		 		qemu+ssh://root@physicalServer2/system, it reported the same error message. 

Also, the servers are the same, same brand, same type, same CPU, same memory. The log on destination server is pasted in my question.

Thanks for help.

I really don't have another idea. Log doesn't tell a lot.

/media/nfs/ is probably on remote server and visible from both servers.

---

### Post by matthew.mattoon on 2011-10-12
Hi,

I have a couple of articles on VM migration which should get you past this.

[http://blog.allanglesit.com/2011/08/linux-kvm-management-offline-migration/](http://blog.allanglesit.com/2011/08/linux-kvm-management-offline-migration/)
[http://blog.allanglesit.com/2011/08/linux-kvm-management-live-migration-without-shared-storage/](http://blog.allanglesit.com/2011/08/linux-kvm-management-live-migration-without-shared-storage/)

-matt

---

