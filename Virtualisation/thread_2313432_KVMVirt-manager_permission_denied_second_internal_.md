---
title: "KVM/Virt-manager permission denied second internal hdd"
date: 2016-02-12
forum: Virtualisation
---

### Post by wfacedrive on 2016-02-12
My host is Kubuntu 15.10 running Windows 10 as the client under virt-manager.  I am currently running a KVM VGA pass-through set up and everything seems to be running ok.  However, when I try to add a second internal HDD with a storage pool I get [Errno1] permission denied.

I stumbled upon this post but it was closed without an answer [http://ubuntuforums.org/showthread.php?t=2235266](http://ubuntuforums.org/showthread.php?t=2235266).  I've been searching for a few days trying to find an answer and have found none.  The closest thing I can think is that it has to do with my group permissions but I'm unsure.

id in terminal gives me the following (blue is the username):
```
uid=1000(blue) gid=1000(blue) groups=1000(blue),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),127(sambashare),129(libvirtd)
```

The libvirt error itself is as follows:
```
Error starting domain: internal error: process exited while connecting to monitor: 2016-02-12T17:07:32.579090Z qemu-system-x86_64: -drive file=/media/blue/Storage/.StorageVM.raw,if=none,id=drive-virtio-disk1,format=raw: Could not open '/media/blue/Storage/.StorageVM.raw': Permission denied

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 91, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 127, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1357, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 1007, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error: process exited while connecting to monitor: 2016-02-12T17:07:32.579090Z qemu-system-x86_64: -drive file=/media/blue/Storage/.StorageVM.raw,if=none,id=drive-virtio-disk1,format=raw: Could not open '/media/blue/Storage/.StorageVM.raw': Permission denied
```

I have tried several different formats such as qcow2 as well as have even tried using EXT4 or NTFS and other file formats all to no avail.  Currently using EXT4.

Any help appreciated.  Thanks!

---

### Post by MAFoElffen on 2016-02-12
You mentioned Kubuntu as the host, kvm as the hypervisor, Virt-manager as your guest connect... and a windows 10 as the guest.

Please describe how you tries to add another virtual disk image to your VM guest. I am assuming you tried through virt-manager settings, virtual disks, then through setting on that VM guest correct? Edit-- I looked at your other thread. It was not clkosed, you did get feedback, where TheFu asked for some inoput, which you did not supply.

Looking at your permission errors... Your are storing your virtual images on a 1 TB USB External dirve? That is formated as ext4... how are you mounting to that and please supply the output from:
```

sudo blkid
sudo fdisk -l

```

---

### Post by wfacedrive on 2016-02-14
Sorry for the late reply. I did NOT post this or had anything to do with this [http://ubuntuforums.org/showthread.php?t=2235266](http://ubuntuforums.org/showthread.php?t=2235266) this was simply the closest I found to the problem I have encountered.  I am running a 2tb internal secondary hard drive with a 1tb storage pool set to .raw.  The path is media/blue/Storage/StorageVM.raw  <- This is what I'm trying to add to my virt-manager. 

 I opened my existing virtual machine which is running Windows 10.  Instead of pressing "Play" I press "Show Virtual Hardware Details." I then follow the GUI to "add hardware" and select "Storage." I then proceed to "Select managed or existing storage."  I then selected media/blue/Storage/StorageVM.raw and used the following input of "VirtIO" and "RAW" as the format.  However it does not matter which format I use as I still recieve [Errno 1].  I have also tried setting the path using chmod 777 *yes I know this is NOT recommended only did this for testing purposes* thinking maybe this would give virt-manager the permission it needed but to no avail.

All I want to do is add this storage to my virtual machine. :/

Here is my blkid:
```
/dev/sda1: LABEL="Storage" UUID="c3a84fc0-c628-4755-8423-a66b408f8b33" TYPE="ext4" PARTUUID="9b29aec8-01"
/dev/sdb1: LABEL="SWP" UUID="87defdc1-6d49-40d8-95dd-38eaba55defe" TYPE="ext4" PARTUUID="3a56f960-2a91-4268-ad8a-a401356f0f79"
/dev/sdc1: UUID="A073-9B6C" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="3b93cf57-9e91-4a84-bc02-643ea59c6c13"
/dev/sdc2: UUID="cfd9d420-ce90-40e1-9713-22556e84c532" TYPE="ext4" PARTUUID="6ee49f12-8bc5-41d1-a0c3-8966ae59b307"
/dev/sdc3: UUID="6fb7a830-1360-4610-9a72-b40a08a9faa2" TYPE="swap" PARTUUID="abd8bcb5-eaad-4a35-baa2-5095a1434671"
/dev/sdd1: LABEL="Samsonite" UUID="51189F6C138BD3D8" TYPE="ntfs" PARTUUID="5a8a14ac-01"
```

Here is my fdisk -l:
```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes                                
Sector size (logical/physical): 512 bytes / 4096 bytes               
I/O size (minimum/optimal): 4096 bytes / 4096 bytes                  
                                                                     
                                                                     
Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors               
Units: sectors of 1 * 512 = 512 bytes                                
Sector size (logical/physical): 512 bytes / 4096 bytes               
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9b29aec8

Device     Boot Start        End    Sectors  Size Id Type
/dev/sda1        2048 3907022847 3907020800  1.8T 83 Linux


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: AEE9D675-D8EE-4526-8097-42A0CB115CA6

Device     Start        End    Sectors   Size Type
/dev/sdb1   2048 1953523711 1953521664 931.5G Linux filesystem


Disk /dev/sdc: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8D4E3EA5-9CD0-47C6-83AF-7F17817BDB15

Device         Start       End   Sectors   Size Type
/dev/sdc1       2048   1050623   1048576   512M EFI System
/dev/sdc2    1050624 216621055 215570432 102.8G Linux filesystem
/dev/sdc3  216621056 250068991  33447936    16G Linux swap


Disk /dev/sdd: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5a8a14ac

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdd1          63 1250263727 1250263665 596.2G  7 HPFS/NTFS/exFAT
```

I am also up for changing the .raw to a different format like .iso or something else if it gives me access to it and read/write abilities within the virtual machine.  Thanks again!

---

### Post by KillerKelvUK on 2016-02-14
> [COLOR=#000000]However, when I try to add a second internal HDD with a storage pool I get [Errno1] permission denied.[/COLOR]

Not sure I quite follow...
1) Your Windows guest has a hdd image created within one storage pool and you're attempting to add a 2nd hdd image located within a another storage pool?
2) You just created a second hdd image and aren't stuffed about storage pools?

Please post the output for 'virsh pool-list' along with the answer to the above as well as confirm whether you've reconfigured libvirt to use anything other than the default username/group?

---

### Post by wfacedrive on 2016-02-14
[ATTACH=CONFIG]267303[/ATTACH][ATTACH=CONFIG]267304[/ATTACH][ATTACH=CONFIG]267305[/ATTACH]

I hope these shots help clear things up.  Picture 1:  What I want to add (Properties show the file name ect.)  Picture 2: Navigating to "Add Hardware" and adding the .raw file from Picture 1.  Picture 3: The error I get.

Here is my output of virsh pool-list:
 Name                 State      Autostart 
-------------------------------------------
 blue                 active     yes       
 kvm                  active     yes       
 Storage              active     yes

To answer question one more thoroughly this is the path of the virtual machine: /home/blue/winpro.raw  60gb is being used on my 102.8gb hard drive.  I'm trying to add media/blue/Storage/StorageVM.raw to my VM.

Also here's this:
groups
blue adm cdrom sudo dip plugdev lpadmin sambashare libvirtd

---

### Post by wfacedrive on 2016-02-14
If you need any further information let me know.

---

### Post by KillerKelvUK on 2016-02-15
How are you creating the hdd images, using qemu commandline or using virt-manager?  Can you share the permissions for the paths to each storage pool as well as the contents of the pools please (ls -la /[COLOR=#000000]media/blue/Storage/ and ls -la /[/COLOR][COLOR=#000000]home/blue/[/COLOR]).

---

### Post by MAFoElffen on 2016-02-15
My first post to you I asked for to to return that from your guest... That does not match what I would expect your guest to be. That looked more like from your host(?) With the sizes and descriptions, I am positive that is what you posted.

 But it was I who mistakenly confused you = I missed that it was a Windows styled guest.

Since it is a Windows guest, Please post that screen shots, from your Windows guest of what it shows in Admin Tools > Storage > Disk Management...

Need me to post something from one of mine as an example? In the meanwhile, let me explain. When you create a disk image, whatever format. It is a blank, unformated disk without a partition table.

After it is created, whatever OS the guest is, a file manager looks for file systems, which are not on a blank disk. You must first add a partition table, partition and format the partitions ... before any file manager is going to see it. We first want to see if the VM defined it (post a snip of the xml). Since is is a dynamic file, get a copy of it via:
```

cat /etc/libvirt/qemu/NameOfVM.xml > ~/Documents/NameOfVM.xml

```
Then via seeing how the VM guest sees it from it's disk manager. If it sees it, then prep'ing the disk for that OS.

---

### Post by wfacedrive on 2016-02-17
the I will post the outputs later tonight for you **[COLOR=#000000]KillerKelvUK[/COLOR]** I currently don't have access to the machine.  I used the qemu command line to create the storage.  I originally used the script file method to create my virtual machine.  I later moved to virt-manager.  There is still data on this storage pool. I will also post back screenshots and the cat output for you [**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547") when I get home.  Sorry for the delayed response and thanks for all the help so far!

---

### Post by wfacedrive on 2016-02-17
I will post the outputs later tonight for you **[COLOR=#000000]KillerKelvUK[/COLOR]** I currently don't have access to the machine.  I used the qemu command line to create the storage.  I originally used the script file method to create my virtual machine.  I later moved to virt-manager.  There is still data on this storage pool. I will also post back screenshots and the cat output for you [**[COLOR=#dd4814][B]MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547") when I get home.  Sorry for the delayed response and thanks for all the help so far!

---

### Post by wfacedrive on 2016-02-18
Here is the output for KillerKelvUK:

```
blue@angel:~$ ls -la /media/blue/Storage/
ls: cannot access /media/blue/Storage/: No such file or directory
blue@angel:~$ ls -la /media/blue/Storage/
total 990668536
drwxrwxrwx  4 root root          4096 Feb 14 12:04 .
drwxr-x---+ 3 root root          4096 Feb 18 06:16 ..
drwx------  2 root root         16384 Feb 13 06:35 lost+found
drwxrwxrwx  2 blue blue          4096 Feb 13 02:22 StorageBin
-rw-rw-r--  1 root root 1014444452864 Feb 14 13:52 StorageVM.raw
```

```
blue@angel:~$ ls -la /home/blue/
total 62914780
drwxr-xr-x 22 blue blue        4096 Feb 18 05:54 .
drwxr-xr-x  3 root root        4096 Dec  7 12:42 ..
drwx------  3 blue blue        4096 Dec  7 16:09 .adobe
drwx------  2 blue blue        4096 Dec 27 12:04 .aptitude
-rw-------  1 blue blue       11058 Feb 14 19:40 .bash_history
-rw-r--r--  1 blue blue         220 Dec  7 12:42 .bash_logout
-rw-r--r--  1 blue blue        3771 Dec  7 12:42 .bashrc
drwxrwxr-x 11 blue blue        4096 Feb 18 05:56 .cache
drwx------ 15 blue blue        4096 Feb 18 06:16 .config
drwx------  3 blue blue        4096 Dec  7 12:52 .dbus
drwxr-xr-x  2 blue blue        4096 Dec  7 12:52 Desktop
-rw-------  1 blue blue          48 Feb 14 10:26 .directory
drwxr-xr-x  2 blue blue        4096 Feb 11 14:56 Documents
drwxr-xr-x  2 blue blue        4096 Dec 18 13:53 Downloads
drwx------  3 blue blue        4096 Feb 18 06:14 .gconf
-rw-r-----  1 blue blue           0 Dec 18 14:01 .gksu.lock
-rw-rw-r--  1 blue blue         342 Dec  7 12:52 .gtkrc-2.0
drwxr-xr-x  3 blue blue        4096 Dec 11 18:13 .kde
drwxrwxr-x  3 blue blue        4096 Dec 22 20:57 kvm
-rw-------  1 blue blue          44 Feb 11 16:01 .lesshst
drwxr-xr-x  3 blue blue        4096 Dec  7 12:52 .local
drwx------  3 blue blue        4096 Dec  7 16:09 .macromedia
drwx------  4 blue blue        4096 Dec  7 15:18 .mozilla
drwxr-xr-x  2 blue blue        4096 Dec  7 12:52 Music
drwxr-xr-x  2 root root        4096 Dec 11 18:24 .nano
drwxr-xr-x  2 blue blue        4096 Feb 14 14:50 Pictures
-rw-r--r--  1 blue blue         675 Dec  7 12:42 .profile
drwxr-xr-x  2 blue blue        4096 Dec  7 12:52 Public              
-rw-------  1 blue blue         341 Dec 11 18:15 .recently-used      
-rw-r--r--  1 blue blue           0 Dec  7 13:04 .sudo_as_admin_successful                                                                
drwxr-xr-x  2 blue blue        4096 Dec  7 12:52 Templates           
drwxr-xr-x  2 blue blue        4096 Dec  7 12:52 Videos              
-rwxrwxrwx  1 root root 64424509440 Feb 11 21:50 winpro.raw          
-rw-------  1 blue blue          50 Feb 18 05:54 .Xauthority         
-rw-------  1 blue blue       77929 Feb 18 06:16 .xsession-errors
```
Also here is the output for MaFoElffen:
This is my xml file win10pro (my guest operating system)
As far as screenshots go I don't think I follow you MaFoElfen, if I can't pass the storage over into the Windows guest I see no point in checking Windows for the storage if it doesn't exist to begin with or doing anything related to it in the guest.

```
<domain type='kvm'>
  <name>win10pro</name>
  <uuid>ab7f7c04-cca2-4b4b-b695-a0b00ee64d66</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-vivid'>hvm</type>
    <loader readonly='yes' type='rom'>/usr/share/ovmf/OVMF.fd</loader>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Opteron_G5</model>
    <vendor>AMD</vendor>
    <topology sockets='1' cores='4' threads='1'/>
    <feature policy='require' name='perfctr_core'/>
    <feature policy='require' name='monitor'/>
    <feature policy='require' name='skinit'/>
    <feature policy='require' name='tce'/>
    <feature policy='require' name='mmxext'/>
    <feature policy='require' name='osxsave'/>
    <feature policy='require' name='vme'/>
    <feature policy='require' name='topoext'/>
    <feature policy='require' name='fxsr_opt'/>
    <feature policy='require' name='bmi1'/>
    <feature policy='require' name='ht'/>
    <feature policy='require' name='cr8legacy'/>
    <feature policy='require' name='ibs'/>
    <feature policy='require' name='wdt'/>
    <feature policy='require' name='extapic'/>
    <feature policy='require' name='osvw'/>
    <feature policy='require' name='nodeid_msr'/>
    <feature policy='require' name='perfctr_nb'/>
    <feature policy='require' name='cmp_legacy'/>
    <feature policy='require' name='lwp'/>
    <feature policy='require' name='invtsc'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/blue/winpro.raw'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/media/blue/Storage/StorageVM.raw'/>
      <target dev='vdb' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:c3:77:b5'/>
      <source network='default'/>
      <model type='e1000'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='mouse' bus='usb'/>
    <input type='keyboard' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes' keymap='en-us'/>
    <video>
      <model type='vga' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x02' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

---

### Post by MAFoElffen on 2016-02-18
Could you please go back to that last post and put [ code ] Tags [ /code ] around your output.

Easiest way to do that is go to Edit > Go Advanced ... Highlight the text, then press the " # " icon in the toolbar...
```

<disk type='file' device='disk'>
  <driver name='qemu' type='raw'/>
  <source file='/home/blue/winpro.raw'/>
  <target dev='vda' bus='virtio'/>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
</disk>
<disk type='file' device='disk'>
  <driver name='qemu' type='raw'/>
  <source file='/media/blue/Storage/StorageVM.raw'/>
  <target dev='vdb' bus='virtio'/>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
</disk>

```
You are right... Since it is failing before the start, your VM is not going to see it. /media? What is the physical description (simple human terms) of where StorageVM.raw is located? Is that a mount? (not in fstab...) Just wondering if that mihgt be a mount permissions problem...

Please post the output of (within code tags): 
```

ls -la /home/blue/winpro.raw
ls -la /media/blue/Storage/StorageVM.raw

```

---

### Post by slickymaster on 2016-02-18
@wfacedrive:

Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean and compact.

---

### Post by KillerKelvUK on 2016-02-18
So your /media/blue/ path has an ACL applied to it (noted the + symbol at the end of the permissions identifiers)...the ACL could have be applied by libvirt to acquire ownership so it can manage the pool and guest images but lets check to be sure...please post back the output of 'getfacl /media/blue' as well as 'getfacl [COLOR=#000000][FONT=Ubuntu Mono]/media/blue/Storage/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]StorageVM.raw'.

Also I note that "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]StorageVM.raw" has no search permissions applied i.e. its missing and "x" in the permissions identifiers...not sure if this is the cause but as the libvirt-qemu user isn't the owner of the /media/blue/ path this could be part of the problem.  I think I read you tried a chmod 777 to the file is that right?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2016-02-18
Ouch not 777 on that.

If it was created to be in his home... and is being used as sudo, then fine. If you give a user rights to run non-prvileged vms, then you create in their home and change them as owner... and change the kvm config for user perviledges... not pretty... but that is not what is going on with you.
```

-rwxrwxrwx  1 root root 64424509440 Feb 11 21:50 winpro.raw

```
in the user's home directory, not owned by the user (not really a problem there as you need sudo to run now anyways... and that is fine), and you gave rights to the world. 

Here is mine, to verify that yours should be set as 0600
```

-rw------- 1 root root      197120 Feb 15 16:04 14.1G-01-1.img
-rw------- 1 root root  8590065664 Feb 16 00:12 14.1G-01.img
-rw------- 1 root root  8589934592 Jan 10 14:40 Androidx86.img
-rw------- 1 root root  8589934592 Sep 11  2014 CentOS7.img
-rw------- 1 root root 10737418240 Dec 18  2014 Dyson.img
-rw------- 1 root root  8590159872 Jan 13  2015 Fedora20_Server-S01.img
-rw------- 1 root root  8590045184 Feb 14 09:36 K14.1-01.img
-rw------- 1 root root  8589934592 Dec 31  2014 MAAS-01.img
-rw------- 1 root root  8589934592 Dec 18  2014 OpenIndiana_DK.img
-rw------- 1 root root 10737418240 Dec 20  2014 OpenSolaris.img
-rw------- 1 root root 10737418240 Dec 18  2014 OpenSXCE_Desktop.img
-rw------- 1 root root  8589934592 Sep 11  2014 Ora_R6_Template.img
-rw------- 1 root root  2147483648 Dec 22  2014 ReactOS.img
-rw------- 1 root root  8589934592 Dec 17  2014 rhel5_4-01.img
-rw------- 1 root root  8590086144 Feb 15 15:05 Samba14.1.3.img
-rw------- 1 root root 10737418240 Dec 17  2014 Sol-11_1-01.img
-rw------- 1 root root  6442450944 Aug 16  2014 sol-live.img
-rw------- 1 root root  8589950976 Jan 10  2015 Ubuntu14.1G-client01.img
-rw------- 1 root root  8590045184 Nov 29  2014 Ubuntu14.1-Server01.img
-rw------- 1 root root  8589946880 Jan 11 17:25 UbuntuServer1604o1.img
-rw------- 1 root root  4294967296 Apr  4  2015 yann01-1.img
-rw------- 1 root root  4294967296 Apr  4  2015 yann01-2.img
-rw------- 1 root root  4294967296 Apr  4  2015 yann01-3.img
-rw------- 1 root root  4294967296 Apr  4  2015 yann01-4.img
-rw------- 1 root root  4294967296 Apr  4  2015 yann01.img
-rw------- 1 root root  8589934592 Dec 17  2014 Zentyal_Server_4-5.img
-rw------- 1 root root  8589934592 Jan 14 01:43 ZfsTest-1.img
-rw------- 1 root root  8589934592 Jan 14 01:43 ZfsTest-2.img
-rw------- 1 root root  8589934592 Jan 14 01:43 ZfsTest.img

```

Here is what will get you back... 
```

sudo chown root:root /home/blue/winpro.raw
sudo chmod 0600 /home/blue/winpro.raw
sudo chmod 0600 /media/blue/Storage/StorageVM.raw

```
and what will fix a bug you seem to be affected by... that affects KVM on some ubuntu hosts...
```

sudo apt-get install apparmor-profiles apparmor-utils
sudo aa-complain /usr/lib/libvirt/virt-aa-helper

```

---

### Post by MAFoElffen on 2016-02-18
So here is a test with a VM with distributed Virtial disks... Meaning the last disk of the VM is not in the default image directory. Rather it is in my user directory on my KVM Host server...

The 2 additional disks are mounted in fstab to directory in my home directory... So same permissions as I stated above. root is the owner. But had manually define and tell it where is was using virsh edit. (That is beyond what virt-manager can do... it loses track of anything outside of the default storage pool... remote or local)

---

### Post by wfacedrive on 2016-02-26
Again sorry for the delay.  First off, thanks slickymaster!  Second,  KillerKelvUK here is the output of what you requested for getfacl  /media/blue' as well as 'getfacl [COLOR=#000000][FONT=Ubuntu Mono]/media/blue/Storage/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]StorageVM.raw'[/FONT][/COLOR]:

```

# file: media/blue
# owner: root
# group: root
user::rwx
user:blue:r-x
group::---
mask::r-x
other::---

```

...and the second line...
```

# file: media/blue/Storage/StorageVM.raw
# owner: root
# group: root
user::rw-
group::rw-
other::r--

```

As far as I know I set the StorageVM.raw to 777 but I could be wrong.
But since MAFoElffen recommended I keep everything in 600 I changed it just now.

I see you used virsh edit to define your drive MAFoElffen.  Since I have posted my XML could you possibly show me what line of code to edit to tell virt-manager to see this second internal drive?  Then virt-manager can see my raw image file and that should solve my issue.  
I also set things to complain like you asked MAFoElffen lol.
Speaking of complaining is it bad practice to use the && command when using multiple lines of code?  (Ex: sudo apt-get update && sudo apt-get upgrade)

Thanks, and any further help is appreciated!

---

### Post by wfacedrive on 2016-02-26
Also for KillerKelvUK, here is the new output from the code you asked for since I changed permission to 600:
```

# file: media/blue
# owner: root
# group: root
user::rwx                                                            
user:blue:r-x                                                        
group::---                                                           
mask::r-x                                                            
other::---    

```

and StorageVM.raw...

```

# file: media/blue/Storage/StorageVM.raw
# owner: root
# group: root
user::rw-
group::---
other::---

```

---

### Post by MAFoElffen on 2016-02-26
Which image name do you consider as being your second drive?

Look at post #12...

I use that... but be "aware". If the first command returns errors... You want to be able to <Cntrl><C> out of it before the second part starts.

---

### Post by wfacedrive on 2016-03-09
I still have no idea why I can't just import StorageVM.raw into my virtual machine via virt-manager.  Yes, I did create the raw image using command line but at the same time should there not be a simple way to add this to an existing VM?  Here is the output that was requested earlier also:

```

ls -la /home/blue/winpro.raw
-rw------- 1 root root 64424509440 Feb 11 21:50 /home/blue/winpro.raw

ls -la /media/blue/Storage/StorageVM.raw
-rw------- 1 root root 1014444452864 Feb 14 13:52 /media/blue/Storage/StorageVM.raw


```

This is my secondary pc so unfortunately I'm not on it daily so it's hard for me to keep up to date with these posts.  Can this not be manually added using virsh?  Or some other means?

Also StorageVM.raw is a raw file stored on a second hard drive that is inside my desktop.  I have 2 hard drives.  The first hard drive is 128gb and has my Linux OS and the Windows VM.  The second hard drive is a 2tb hard drive.  This drive has on it StorageVM.raw which has all my games, pictures, ect. on it.  I want to be able to attach this RAW image to my existing virtual machine for extra storage.  I didn't create this originally in virt-manager but it has worked previously in a virtual machine using a script file.  The script file no longer works as I have tweaked the OS for virt-manager so I no longer have access to this RAW file.  Is there a way to clone this drive so that Virt-manager can see it or make a copy even?  I just want the data from the raw file.  If there is any other method to do this I would love to know.
Thanks

---

### Post by MAFoElffen on 2016-03-09
You said you normally use virt-manager right? 

So-- For a test, in virt-manager, with the VM selected > go View > Details > Add stoarge > SCSI, qcow2... and select the path on the drive you want it to live.

Start the VM > use fdisk to partition it. > then use Disk to format it. Mount it. Make sure you can copy and read from it. If so, then copy your data to it. The test would be to let virt-manager make all the connections for that VM.

Now we get into details and splitting hairs. Then is the format... Raw format has better performance than qcow2. Raw can be used by any hypervisor, or at least ported to such. So why did I recommend that instead of raw.Qcow2 can dynamically grow the image file and take snapshots. (you described the data you want to keep on it...) Yo could certainly do the same with it being in Raw format.

EDIT-- The previous test I did for you, I had the test vm in my image directory. I created a VM storage (image) disk inside Virt-manager wihich you said you did, but virt manager, when it creates, only creates in that defualt directory... I moved it to my home directory, which is where yours was. Then I went and used Virsh edit to edit the xml for that vm and changed the path to add that disk image, in my home directory, on that server... all worked fine. 

Note: I did another test where that VM mounted a VM shared directory from my Nework Shared Storage (different physical machine). created another virtual disk image manaully onto that share. Added it manaully on that same vm using virsh edit (xml) as a network shaed resource.. Then I added that share to the fstab of that VM. Again, everything worked okay.

EDIT2-- So with the above tests... I am not there. I have seem your output and everything should work as you posted and the matching tests I did. I few things that did not work in those tests? You probably need to heat those also. I could create a virtual image anywhere with virsh <> Not so with virt-manager. I could only create in whatever was the default image directory in preferences. I could only boot a could not I could not access Virtual disks from multiple machines, with that file being a ntwork resource ... i.e. your cannot access an image from a KVM server and a client's home directory on their machine, without that sevrer or a vm mounting that file on the clients machine. Even though you rn the VM from the client, the client's local home, is remote to the KVM server (in my environment-- 4 network hyperivsor servers. Guests are run from clients machines... Some VM's are stored in Network storage.)

---

### Post by wfacedrive on 2016-03-18
Sadly I nuked my system and decided to start from scratch with a bigger SSD and a different setup (may try ESXi or straight dual-boot) I found I had too many problems with the KVM setup with virt-manager and converted my .raw file to an .iso so that I may have access to it again.  Sorry for the wasted time, just want to start enjoying my desktop again.

---

### Post by MAFoElffen on 2016-03-18
So you didn't try what I suggested in post #21 before letting go?

LOL, okay... Do some research first. Be prepared. I do KVM, Xen (Citrix), ESXi (VSphere). LXC, Docker, Hyper-V...

ESXi takes some resources to get started. ESXi is a true bare-metal hypervisor in the literal sense-- meaning it is it's own OS with integrated hypervisor. It is neither Windows nor Linux. Being such, some things it does it's own way. Admin is done remotely. Hardware that it installs on is what they have pre-approved as being suitable. That way they can control the quality of performance that they expect and will stand behind.


Admin is mainly remotely through the VSphere client. The free ESXi does have some limitations in the Virtual Hardware that it supports. Some things are only in the paid licenses. That is just a quick summary. But if you thin you are having a challenge now... Just saying.

---

### Post by wfacedrive on 2016-04-02
Not trying to revive an old thread but I found the answer I needed. Also gave ESX-i a shot and found it was limited for what I wanted to accomplish.  Also found that Xen was nice but required a kernel recompile where KVM it's optional. So I brought my KVM setup back and after roughly 3 days of digging for answers (and a long document showing all my progress) I think I figured it out.

I nuked my system so obviously I don't have the original raw file I was trying to transfer, but I created a new qcow2 file instead as suggested by MAFoElffen for my storage needs but was still receiving the Error 1. However, this should work regardless the file.

From what I could gather Error 1 was basically saying virt-manager was wanting permissions.  Specifically root permissions to access my second internal HDD. My first impression was that I could just chown the created .qcow2 file to root and that would give virt-manager the permission it needed.  This didn't work.  I then tried setting my username seeing as I am part of the group libvirtd to give permission to the file.  This also didn't work. Then I started digging around in config files and found it.

**To fix permission denied on second internal HDD**

(Not sure if this is a permenant fix but this worked)

```
sudo nano /etc/libvirt/qemu.conf
```

Uncomment user/group to work as root.
Then restart libvirt-bin.

user = "root"
group = "root"

```
service libvirt-bin restart

```

That's it.  Fixed my problem.  Again, not sure if this is the RIGHT way to fix it as I'm still learning but this did the trick for me.  Also have no idea how to mark something as solved.

Thanks!

---

### Post by MAFoElffen on 2016-04-03
Congratulations on resolving your issue.

Two things--
First, You said you did a lot of digging, researching to find ideas and answers. Where did you find that idea? A document somewhere? Just curious to so my own research a little deeper on that...

Second, it would really help others who might have the same or similar problem, if you would come back and mark this thread as 'Solved." That way, they can find your answer to what helped. Easy to do and only takes a few seconds. Go to any page of this thread and select the "Thread Tools" link that is to the top left of the top=most post. > Select "Mark as Solved."

---

### Post by wfacedrive on 2016-04-03
Thanks for the heads up!  Also I found the information somewhere I least expected after hours of digging.  Here's the link > [https://github.com/jedi4ever/veewee/issues/996](https://github.com/jedi4ever/veewee/issues/996)  For some reason this worked.  Also I may post later on the actual document with all my notes I took for setting up my kvm in 'buntu from scratch.  Who knows, maybe it can be improved on and maybe it will help someone else out.  Thanks for the help everyone!

---

