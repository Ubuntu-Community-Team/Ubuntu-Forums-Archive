---
title: "vmbuilder generated disk file size"
date: 2012-09-11
forum: Virtualisation
---

### Post by geeksmith on 2012-09-11
vmbuilder creates small disk files for kvm and vmw6 hypervisor machines and full-sized disk files for esxi hypervisor machines.  I didn't specify any disk pre-allocation options (I don't even know if there is such a thing for vmbuilder).

The following VMs were created using the same command, with the exception of the hypervisor choice.

[FONT="Courier New"]
ubuntu-esxi:
total 11G
-rw-r--r-- 1 aaron.smith aaron.smith 3.0G Sep 11 16:55 tmpb9a4Ke-flat.vmdk
-rwx---r-x 1 aaron.smith aaron.smith  487 Sep 11 16:55 tmpb9a4Ke.vmdk*
-rw-r--r-- 1 aaron.smith aaron.smith 7.9G Sep 11 16:55 tmpsuqqPO-flat.vmdk
-rwx---r-x 1 aaron.smith aaron.smith  490 Sep 11 16:56 tmpsuqqPO.vmdk*
-rwx---r-x 1 aaron.smith aaron.smith 1.3K Sep 11 16:56 ubuntu.vmx*

ubuntu-kvm:
total 540M
-rwxrwxr-x 1 aaron.smith aaron.smith   95 Sep 11 17:03 run.sh*
-rw-r--r-- 1 aaron.smith aaron.smith 3.7M Sep 11 17:03 tmpXCjTMI.qcow2
-rw-r--r-- 1 aaron.smith aaron.smith 537M Sep 11 17:03 tmpz8XMvm.qcow2

ubuntu-vmw6:
total 538M
-rw-r--r-- 1 aaron.smith aaron.smith 4.2M Sep 11 17:19 tmpeUGwQZ.vmdk
-rw-r--r-- 1 aaron.smith aaron.smith 550M Sep 11 17:18 tmpU_bTYR.vmdk
-rwx---r-x 1 aaron.smith aaron.smith  672 Sep 11 17:19 ubuntu.vmx*
[/FONT]


Does anybody know why esxi disks are full-sized?  Is it possible to create small disk files for all hypervisors, or specify if the disk should be sparse or fully pre-allocated?

--
@@ron

---

### Post by HostIndia on 2012-09-13
When ESXi 4 runs at its default installation and it detects a  single 2TB RAID 5 volume, it sets up the datastore as one large volume.   Judging from the disk options during the creation of new drive volumes,  the largest allowable partition size under this configuration is 250GB. But you can still just delete the data store and recreate it, choosing a your preferred block size.

I just managed to search a solution for you as following

**From the ESX console:**

[LIST=1]
[*]Log in to the ESX console.
[*]Run the command:

[FONT=Courier New][SIZE=2]# vmkfstools -P <path to datastore>[/SIZE][/FONT]

The block size is in **bold** in this line:

[FONT=Courier New][SIZE=2]Capacity 429228294144 (409344 file blocks * **1048576**), 8896118784 (8484 blocks) available
[/SIZE][/FONT]
Where [FONT=Courier New][SIZE=2]*1048576*[/SIZE][/FONT] is equivalent to a 1 MB block size on a VMFS datastore.
[/LIST]
Hope this helps you.

---

### Post by geeksmith on 2012-09-13
Thank you for the response.  I'm not sure it's relevant to what I'm doing, however.  My question is not about configuring the datastores in ESXi, but using vmbuilder to create a virtual machine for use on ESXi.

vmbuilder generates a vmdk file that is the full size of the virtual disk, which implies that the virtual disk space is pre-allocated rather than allocated on demand.  Virtual machines generated for other hypervisors create disks that allocate space on demand.

--
@@ron

---

