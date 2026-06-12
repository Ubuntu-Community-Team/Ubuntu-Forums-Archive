---
title: "How to change the default location of libvirt VM images"
date: 2017-10-22
forum: Virtualisation
---

### Post by satimis on 2017-10-22
Hi all,

Which will be the easy way to change the default location of libvirt VM images

Config of PC
Drive-1 for running Ubuntu 16.04 desktop and KVM

Drive-2 for storage of VM images on a Directory KVM-VM-Images

The default location is on /var/lib/libvirt/images/ of Drive-1

Please advise.  Thanks

Regards
satimis

---

### Post by KillerKelvUK on 2017-10-22
Hi (again) :-)

So you can use libvirt's management toolsets for this, virsh is command line based and the command you want is something like this...

```

virsh pool-edit default

```

default is the name of the storage pool created by...you guessed it...default, when libvirt is installed on the host.

As a safer way to manage this if you are new to libvirt you could just create a 2nd storage pool.  If you like the command line then just get into virsh by typing "virsh" into a terminal prompt and then type "help" to list all the available commands.  You can then get command specific help by typing "help n[I]ame-of-command".

[/I]If you prefer to use a GUI then virt-manager is an option and you can manage storage pools here easily also.

---

### Post by satimis on 2017-10-23
> **KillerKelvUK said:**
> Hi (again) :-)

So you can use libvirt's management toolsets for this, virsh is command line based and the command you want is something like this...

```

virsh pool-edit default

```

default is the name of the storage pool created by...you guessed it...default, when libvirt is installed on the host.

As a safer way to manage this if you are new to libvirt you could just create a 2nd storage pool.  If you like the command line then just get into virsh by typing "virsh" into a terminal prompt and then type "help" to list all the available commands.  You can then get command specific help by typing "help n[I]ame-of-command".

[/I]If you prefer to use a GUI then virt-manager is an option and you can manage storage pools here easily also.
Hi K,

Thanks for your advice

I'm prepared using the folder KVM_Images created on the 2nd drive.  Whether replace defaut with the path /media/satimis/xxxxx-4ac5-yyyyyyy-b6e0-zzzzz/KVM_Images ?

I have read "virsh --help".  It is rather complicate.  Please see attached file virsh_help.txt

Under Storage pool```

storage pool or modify an existing persistent one from an XML file
    pool-delete                    delete a pool
    pool-destroy                   destroy (stop) a pool
    pool-dumpxml                   pool information in XML
    pool-edit                      edit XML configuration for a storage pool
    pool-info                      storage pool information
    pool-list                      list pools
    pool-name                      convert a pool UUID to pool name
    pool-refresh                   refresh a pool
    pool-start                     start a (previously defined)

```
I found pool-edit but couldn't figured out how to add a 2nd storage?

On GUI
Starting Virtual Machine Manager
-> Edit -> Connection Details
-> Storage
Name:
Change;
default

To;
/media/satimis/xxxxx-4ac5-yyyyyyy-b6e0-zzzzz/KVM_Images
?

Please advise.  Thanks

Regards
satimis

---

### Post by KillerKelvUK on 2017-10-23
Okay so, in the snippet below I enter the virsh terminal, I list the currently active storage pools (pool-list), I then create a new storage pool (pool-create-as), I then relist the active pools to see my new one, I then dump the pools xml to see the wider config (pool-dumpxml), I then delete the pool (pool-destroy) and finally list the active pools again to show the newly created has been removed.

```

[FONT=monospace][COLOR=#54FF54]**user@myservername**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ virsh[/COLOR]
Welcome to virsh, the virtualisation interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

virsh # pool-list
 Name                 State      Autostart  
-------------------------------------------
 default              active     yes        
 Images               active     yes        

virsh # pool-create-as --name satimis --type dir --target /mnt/share/downloads/
Pool satimis created

virsh # pool-list
 Name                 State      Autostart  
-------------------------------------------
 default              active     yes        
 Images               active     yes        
 satimis              active     no         

virsh # pool-dumpxml satimis
<pool type='dir'>
  <name>satimis</name>
  <uuid>da278de1-fbe3-4975-b65f-9a1f9e46a42c</uuid>
  <capacity unit='bytes'>11906244657152</capacity>
  <allocation unit='bytes'>8410976972800</allocation>
  <available unit='bytes'>3495267684352</available>
  <source>
  </source>
  <target>
    <path>/mnt/share/downloads</path>
    <permissions>
      <mode>0770</mode>
      <owner>1000</owner>
      <group>1000</group>
    </permissions>
  </target>
</pool>

virsh # pool-destroy satimis
Pool satimis destroyed

virsh # pool-list
 Name                 State      Autostart  
-------------------------------------------
 default              active     yes        
 Images               active     yes    
[/FONT]
```

In virsh you could also look at the pool-edit command to alter the default pool created by libvirt at install.

Regards using virt-manager, you cannot edit an existing pool with this tool you can only create and destroy.  In the storage management area (as you have located) use the + symbol in the bottom left corner to create a new pool and follow the wizard instructions.

---

### Post by satimis on 2017-10-24
> **KillerKelvUK said:**
> Okay so, in the snippet below I enter the virsh terminal, I list the currently active storage pools (pool-list), I then create a new storage pool (pool-create-as), I then relist the active pools to see my new one, I then dump the pools xml to see the wider config (pool-dumpxml), I then delete the pool (pool-destroy) and finally list the active pools again to show the newly created has been removed.

```

[FONT=monospace][COLOR=#54FF54]**user@myservername**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ virsh[/COLOR]
Welcome to virsh, the virtualisation interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

virsh # pool-list
 Name                 State      Autostart  
-------------------------------------------
 default              active     yes        
 Images               active     yes        

virsh # pool-create-as --name satimis --type dir --target /mnt/share/downloads/
Pool satimis created

virsh # pool-list
 Name                 State      Autostart  
-------------------------------------------
 default              active     yes        
 Images               active     yes        
 satimis              active     no         

virsh # pool-dumpxml satimis
<pool type='dir'>
  <name>satimis</name>
  <uuid>da278de1-fbe3-4975-b65f-9a1f9e46a42c</uuid>
  <capacity unit='bytes'>11906244657152</capacity>
  <allocation unit='bytes'>8410976972800</allocation>
  <available unit='bytes'>3495267684352</available>
  <source>
  </source>
  <target>
    <path>/mnt/share/downloads</path>
    <permissions>
      <mode>0770</mode>
      <owner>1000</owner>
      <group>1000</group>
    </permissions>
  </target>
</pool>

virsh # pool-destroy satimis
Pool satimis destroyed

virsh # pool-list
 Name                 State      Autostart  
-------------------------------------------
 default              active     yes        
 Images               active     yes    
[/FONT]
```

In virsh you could also look at the pool-edit command to alter the default pool created by libvirt at install.

Regards using virt-manager, you cannot edit an existing pool with this tool you can only create and destroy.  In the storage management area (as you have located) use the + symbol in the bottom left corner to create a new pool and follow the wizard instructions.

Hi K,

Referring to your advice:
> 
virsh # pool-create-as --name satimis --type dir --target /mnt/share/downloads/


The mount point of drive-2 is```

/media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/

```

I have created a folder 'KVM_Guests' on drive-2

&#10219; ls -ald /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/```

drwxrwxr-x 2 satimis satimis 4096 Oct 22 21:19 /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/

```

The folder is owned by satimis:satimis

Whether the command will be;```

virsh # pool-create-as --name satimis --type dir --target /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/

```
?

I found following document;
Managing Storage with Virtual Machine Manager
[https://www.suse.com/documentation/sles11/book_kvm/data/sec_libvirt_storage_vmm.html](https://www.suse.com/documentation/sles11/book_kvm/data/sec_libvirt_storage_vmm.html)

The "Location" there can be edited

But on my 'Virtual Machine Manager' the Location is fixed (can't be edited). Please see attached screenshot 'screenshot_storage.png'

On Terminal:
&#10219; sudo find / -name virt-manager```

/home/satimis/.cache/virt-manager
find: ‘/run/user/1000/gvfs’: Permission denied
/usr/share/bug/virt-manager
/usr/share/doc/virt-manager
/usr/share/virt-manager
/usr/share/virt-manager/virt-manager
/usr/bin/virt-manager

```

&#10219; ls -al /home/satimis/.cache/virt-manager```

total 304
drwxr-x--x  3 satimis satimis   4096 Oct 22 22:31 .
drwx------ 17 satimis satimis   4096 Oct 24 21:09 ..
drwxr-x--x  2 satimis satimis   4096 Oct 22 22:31 boot
-rw-rw-r--  1 satimis satimis 294575 Oct 24 21:06 virt-manager.log

```

&#10219; ls -al /usr/share/virt-manager/virt-manager```
 
-rwxr-xr-x 1 root root 9589 Dec  7  2015 /usr/share/virt-manager/virt-manager

```

&#10219; ls -al /usr/bin/virt-manager```
 
-rwxr-xr-x 1 root root 59 Sep  7 23:32 /usr/bin/virt-manager

```

They are owned by root:root

Whether change the owner on both of them to 'satimis:satimis' ?  Then I can edit 'Location'?

But I can't resolve why I can start 'Virtual Machine Manager' on Terminal as 'satimis' without complaint?

Please advise.  Thanks

Regards
satimis

---

### Post by satimis on 2017-10-25
Hi K,

I have figured out the solution.  It is NOT so complicate and doesn't need creating a second pool.  Just start creating a new guest on Virtual Machine Manager directly.

Pre-requisite
1) Create a folder 'KVM_Guests' on drive-2 as user (in my case)

&#10219; ls -ald /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/```

drwxrwxr-x 2 satimis satimis 4096 Oct 25 12:25 /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/

```

2) drive-2 must be mounted before starting creating a new virtual machine


Steps are as follows:-

Start Virtual Machine Manager (as user)
-> Create a new virtual machine

check -> Local install media (ISO image or CDROM)
-> Forward
check -> Use ISO image
-> Browse -> Browse Local
select xxx.iso
-> Open

check -> Automatically detect operating system based on install media
-> Forward

Memory (RAM): 1024
CPUs: 1
-> Forward

check -> Create a disk image for the virtual machine
[ 20 ] Gib
check -> Select or create custom storage

-> Manage -> Browse Local

-> Other Locations
select Drive-2
-> KVM_Guests

Name: ubuntu1604-pc1b00
-> Open

-> Forward

Ready to begin the installation```

Name: ubuntu1604-pc1b00
OS: Generic
Install: Local CDROM/ISO
CPUs: 1
Storage: 20.0 GiB....66/KVM_Guests/ubuntu1604-pc1b00

```
-> Finish

Then follow the instruction to finish installing Ubuntu16.04 as KVM guest.

&#10219; ls -al /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/```

total 10030124
drwxrwxr-x 2 satimis satimis        4096 Oct 25 12:25 .
drwxrwxrwx 9 root    root           4096 Oct 23 16:45 ..
-rw------- 1 root    root    21478375424 Oct 25 11:19 generic.qcow2
-rw------- 1 root    root    21478375424 Oct 25 12:36 ubuntu1604-pc1b00

```


I have no idea whether the same steps can be applied to import guest images.  I'll try later when having time.

Thanks

Regards

---

### Post by KillerKelvUK on 2017-10-26
Hey Satimis...

> 
[COLOR=#000000]I found following document;[/COLOR]
[COLOR=#000000]Managing Storage with Virtual Machine Manager[/COLOR]
[https://www.suse.com/documentation/s...orage_vmm.html]("https://www.suse.com/documentation/sles11/book_kvm/data/sec_libvirt_storage_vmm.html")

[COLOR=#000000]The "Location" there can be edited[/COLOR]

[COLOR=#000000]But on my 'Virtual Machine Manager' the Location is fixed (can't be edited). Please see attached screenshot 'screenshot_storage.png'[/COLOR]


That linked page only shows creating and deleting storage pools, there is nothing there about editing them.  I've never seen a way to edit a storage pool from within virt-manager.

> 
[COLOR=#000000]&#10219; ls -al /usr/share/virt-manager/virt-manager[/COLOR][COLOR=#000000]Code:
 
-rwxr-xr-x 1 root root 9589 Dec  7  2015 /usr/share/virt-manager/virt-manager[/COLOR]
[COLOR=#000000]&#10219; ls -al /usr/bin/virt-manager[/COLOR][COLOR=#000000]Code:
 
-rwxr-xr-x 1 root root 59 Sep  7 23:32 /usr/bin/virt-manager[/COLOR]
[COLOR=#000000]They are owned by root:root

[/COLOR][COLOR=#000000]Whether change the owner on both of them to 'satimis:satimis' ? Then I can edit 'Location'?[/COLOR]

[COLOR=#000000]But I can't resolve why I can start 'Virtual Machine Manager' on Terminal as 'satimis' without complaint?[/COLOR]

[COLOR=#000000]Please advise. Thanks[/COLOR]


The contents under /usr/share is owned by root...always.  I don't believe any of those files are used by the main application binary, they typically include documentation and configuration examples etc.  Changing the ownership of this location won't have any impact however I wouldn't recommend just blindly altering these.  Similarly changing the ownership of the application binary is just not needed, if you look at the permissions of /usr/bin/virt-manager it allows 'others' to read and execute the file but only the owner can 'write'...this is why your own user can execute it even though the file is owner by the root user....this is typical of all binaries here I believe.

Regards your final solution, this will work and in fact it is an alternative way to create a storage pool.  If you look now at your available storage pools I expect that /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/ will be listed.  Virt-manager automates this process when using its 'Browse' function.

---

### Post by satimis on 2017-10-26
> **KillerKelvUK said:**
> Hey Satimis...



That linked page only shows creating and deleting storage pools, there is nothing there about editing them.  I've never seen a way to edit a storage pool from within virt-manager.



The contents under /usr/share is owned by root...always.  I don't believe any of those files are used by the main application binary, they typically include documentation and configuration examples etc.  Changing the ownership of this location won't have any impact however I wouldn't recommend just blindly altering these.  Similarly changing the ownership of the application binary is just not needed, if you look at the permissions of /usr/bin/virt-manager it allows 'others' to read and execute the file but only the owner can 'write'...this is why your own user can execute it even though the file is owner by the root user....this is typical of all binaries here I believe.

Regards your final solution, this will work and in fact it is an alternative way to create a storage pool.  If you look now at your available storage pools I expect that /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/ will be listed.  Virt-manager automates this process when using its 'Browse' function.
Hi K,

Your advice noted and thanks.

Now I have centos7 and ubuntu 16.04 running on KVM.  The speed on starting them up as well as closing them is relatively slower than the VMs on VirtualBox.  I suppose it is because the formers are running on WD 7,200 rpm HD and the latters are running on SSD.  Anyway this is only a test and I won't care too much.  In future I would install SSD on PC for virtualization.

Now I shall start exporting the VMs on VirtualBox and import the same to KVM.  Since I have ceased running KVM for prolonged time, I need spending time to find relevant documentation.  I'll come back afterwards.

Regards
saimis

---

### Post by KillerKelvUK on 2017-10-26
Glad you solved this satimis, have fun getting to know KVM again ;-)

---

### Post by satimis on 2017-10-27
> **KillerKelvUK said:**
> Glad you solved this satimis, have fun getting to know KVM again ;-)

Hi K,

Performed following test:-

Start PC1A (1TB SSD)

On Terminal:-
satimis@PC1A:~&#10219; cp VirtualBox\ VMs/ub1604dkpc1_00/ub1604dkpc1_00.vdi /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/

satimis@PC1A:~&#10219;
ls /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/ | grep .vdi```

ub1604dkpc1_00.vdi

```


Close PC1A (1TB SSD) and start PC1B (250G SanDisk SSd)

On Terminal run:-
satimis@PC1B:~&#10219; cd /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/

satimis@PC1B:/media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666&#10219; qemu-img convert -f vdi -O qcow2 ub1604dkpc1_00.vdi ub1604dkpc1_00.qcow2

satimis@PC1B:/media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666&#10219; ls | grep .qcow2```

ub1604dkpc1_00.qcow2

```

&#10219; cp /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/ub1604dkpc1_00.qcow2 /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/ub1604dk-pc1a00.qcow2
(copy ub1604dkpc1_00.qcow2 and re-name it as ub1604dk-pc1a.qcow2)

Start Virtual Machine Manager
-> Create a new Virtual Machine
(check) Import exiting disk image -> Forward

-> Browse -> Browse Local
select ub1604dk-pc1a00.qcow2
-> Open
```

Provide the existing storage path:
/media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666/KVM_Guests/ub1604dk-pc1a00.qcow2

Choose an operating system type and version
OS type: Generic
Version: Generic

```
-> Forward

```

Choose Memory and CPU settings
Memory (RAM): 1024 MiB
CPUs: 1

```
-> Forward

Ready to begin the installation
Name: (change generic to ub1604dk-pc1a00)
-> Finish

Importing VM of Virtualbox to KVM is successful.  ub1604dk-pc1a00 is now running on KVM

I'll conclude my exploration here.

My next exploration will be installing oVirt on a guest of KVM testing "nested virtualization environments"

Lot of thanks for your support and your time spent to assist me.

Regards
satimis

---

