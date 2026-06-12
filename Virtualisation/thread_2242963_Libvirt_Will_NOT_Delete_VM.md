---
title: "Libvirt Will NOT Delete VM"
date: 2014-09-05
forum: Virtualisation
---

### Post by redger on 2014-09-05
I created a kvm-qemu guest machine using "virsh define <filename>" passing a file created using "virsh domxml-from-native <filename>" which all worked ok

Then I wanted to work with the VM
(a) Edit the VM definition using Virt-Manager and using "Virsh edit"  both of which worked ... EXCEPT a restart of libvirt-bin .. or a reboot .... would restore the VM definition to its' pre-edit state !!!!
(b) eventually I tired of that VM and deleted it. Oh oh ... as soon as libvirt restart (via "sudo service libvirt-bin restart" or a reboot) .. the VM was reinstated !!! WTF !
(c) Eventually I went all out and (i) used Virsh to destroy and undefine the VM (ii) stop libvirt (iii) deleted the log files from /var/log/libivrt/qemu (iv) deleted the apparmor files from /etc/apparmor.d/libvirt (v) scanned the entire disk for the VM's uuid - none found (vi) verified that libvirt has actually removed the vm definition from /etc/libvirt/qemu - which it had

Then I restarted libvirt .. and .....
The VM is still there !! I cannot remove it no matter what I do (worth noting that the xml files, apparmor files and logs are all gone - but virt-managerand "virsh list --all" continue to show the VM)

HELP !! How can I get rid of this wart on my machine ?

Please don't ask for more sacrifices ... .tried that already ... didn't work ! :)

---

### Post by TheFu on 2014-09-06
Delete the VM from /var/lib/libivrt/images - assuming it is a default.
I use virt-manager for all the stuff you are doing. It handles 95% of the settings nicely for the casual KVM user. Much easier and works remotely over built-in ssh connections. 

Might need to check if the storage is not local for permissions - NFS can have this issue with non-root.

---

### Post by redger on 2014-09-09
thanks Fu,
I've looked in those directories and there are no files rleated to the VM in question (included a search for all hidden files)

I'm absolutely stuck on this one .... the VM remains in the libvirt list(s) ..... seems to have a "ghost" life all of its own, continually resurrected.

I set out using Virt-Manager ... but a little omore challenging in my case since I;m using VGA passthrough so either need root permissions or to mess with fill and memory permissions in interesting ways, so settled on direct Qemu command for VM requiring vga passthrough and Virt-Manager for everything else. In the meantime I seem to have created this religious icon which is continually resurrected ...... with no obvious source

---

### Post by TheFu on 2014-09-09
> **redger said:**
> thanks Fu,
I've looked in those directories and there are no files rleated to the VM in question (included a search for all hidden files)

Did you search for the specific NAMED file --- as root?  The directories are usually not available to non-root accounts. If another userid can see the file, they can learn everything.

> **redger said:**
> I'm absolutely stuck on this one .... the VM remains in the libvirt list(s) ..... seems to have a "ghost" life all of its own, continually resurrected.  I've never seen this ... well ... except when I'd mount other storage over a directory structure AFTER the file was already loaded and hence hidden.  Does that make sense? I can try to explain better if needed.  Output from 'df -h' would help determine if that is happening here.

> **redger said:**
> I set out using Virt-Manager ... but a little omore challenging in my case since I;m using VGA passthrough so either need root permissions or to mess with fill and memory permissions in interesting ways, so settled on direct Qemu command for VM requiring vga passthrough and Virt-Manager for everything else. In the meantime I seem to have created this religious icon which is continually resurrected ...... with no obvious source

VGA-passthru is definitely NOT normal-user-stuff.  Worth leading with that tidbit of information might be helpful - always.  **df -h** please and the full-path-to-the img file would be helpful too. Sorry - dind't re-read any prior messages if it is already provided. I've slept since then.

Good thing we know that all religious things are just a hoax, imaginary, no more real than the Easter bunny, Santa Claus, or [Jesus images in grilled cheese]("https://en.wikipedia.org/wiki/Perceptions_of_religious_imagery_in_natural_phenomena") sandwiches ... er ... unless you actually believe in that stuff.  My imaginary friend "Bob" says I'm mistaken. ;)

---

### Post by redger on 2014-09-19
thanks Fu,
yes, I scanned as "root" .... nothing

Output from df -h
```
Filesystem                                    Size  Used Avail Use% Mounted on
/dev/sda3                                      30G  5.3G   23G  19% /
none                                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                          7.7G  4.0K  7.7G   1% /dev
tmpfs                                         1.6G  1.4M  1.6G   1% /run
none                                          5.0M  4.0K  5.0M   1% /run/lock
none                                          7.8G  156K  7.8G   1% /run/shm
none                                          100M   24K  100M   1% /run/user
/dev/sda4                                      30G  3.9G   25G  14% /home
/dev/sda2                                     181M   81M   87M  49% /boot
/dev/sdb1                                     485M   85M  372M  19% /mnt/wd2t_01_boot_01
/dev/sdb2                                      30G  6.9G   22G  25% /mnt/wd2t_02_root_01
/dev/sdb3                                      30G   26G  2.9G  90% /mnt/wd2t_03_home_01
/dev/sdb5                                     486M  196M  261M  43% /mnt/wd2t_04_boot_02
/dev/sdb6                                      30G  4.9G   24G  17% /mnt/wd2t_05_root_02
/dev/sdb7                                      30G  5.6G   23G  20% /mnt/wd2t_06_home_02
/dev/mapper/wd2t--lvm--data-programming_data   99G   41G   53G  44% /mnt/programming_data
/dev/mapper/wd2t--lvm--data-lxc_images         79G   34G   42G  45% /mnt/lxc_images

```

And from the "find"  (the VM is called "xxxxx-finsafe") from base directory
```
myname@virt-host:/$ sudo find -P -iname *myvm*
[sudo] password for myname: 
./run/udev/links/\x2fwd2t-lvm-data\x2fubuntu_myvm_kvm
./run/udev/links/\x2fmapper\x2fwd2t--lvm--data-ubuntu_myvm_kvm
./run/udev/links/\x2fdisk\x2fby-id\x2fdm-name-wd2t--lvm--data-ubuntu_myvm_kvm
./home/myname/Programs/qemu/temp_qemu_myvm.txt
./home/myname/Programs/qemu/qemu_ubuntu_myvm_command.sh
./home/myname/Programs/qemu/libvirt_uuid_ubuntu_myvm_to_kill.txt
./home/myname/Programs/qemu/libvirt_qemu_ubuntu_myvm_a.sh
./home/myname/Programs/qemu/spice_ubuntu_myvm_command.sh
./home/myname/Programs/qemu/temp_qemu_myvm.xml
./var/log/libvirt/qemu/ubuntu-myvm-a.log
./var/log/libvirt/qemu/ubuntu-myvm.log
./var/log/libvirt/qemu/ubuntu-myvm-a.log.1
./dev/wd2t-lvm-data/ubuntu_myvm_kvm
./dev/disk/by-id/dm-name-wd2t--lvm--data-ubuntu_myvm_kvm
./dev/mapper/wd2t--lvm--data-ubuntu_myvm_kvm
./etc/libvirt/qemu/ubuntu-myvm-a.xml
myname@virt-host:/$ 
```

VGA passthrough is working well, very close to bare metal performance AND now running via libvirt without elevated privileges. Just this wierd anomaly ... who'd have thunk

Apparently your imaginary friend is better than mine (mine's deserted me). Thanks for your help

---

### Post by TheFu on 2014-09-19
Perhaps this is a stupid question, but why search for *myvm* when the name for it is "xxxxx-finsafe"?
Also - is there any chance you've setup LVM passthru for the storage or are using network-based storage - iscsi, nfs, aoe?

The xml file for the VM must point to the storage. Did you check there first?  /etc/libvirt/qemu/ has them in a default config (not using lxc).

---

### Post by redger on 2014-09-19
hi Fu,
the search was appropriate ... I changed names to protect the guilty ;)
The VM storage is all on LVM, and the VM pointed correctly to the storage, yes
I even removed the log files from /var/log/libvirt/qemu/   (./var/log/libvirt/qemu/ubuntu-myvm.log)
and then restarted libvirt ... it's back !
Interestingly ... if I start the "phantom" from libvirt (either virsh or virt-manager) it fails with an apparmor error (makes sense since the prpfile has been removed) ... and creates a new log file. And there's nothing useful in the libvirt log.

All very wierd. Does you imaginary friend have any advice ?

---

### Post by TheFu on 2014-09-19
I can't understand. Bob isn't helping either.

We seem to be going around in a circle on LVM/storage - it is possible to provide an LVM partition or some other whole partition directly to the VM - did you do that?   There are about 5 different ways to provide storage for a VM. Exactly, which does the VM XML file say is being used?

Log files don't matter.

I don't know what a prpfile is. Please clarify.

I think we're gonna find that you weren't dumping the XML file for the VM and reading all the storage stanzas. At least that's what it looks like from here - tonight. ;)

```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 2     Win7Ult                        running
 3     lubuntu                        running

$ virsh dumpxml Win7Ult > /tmp/w7.xml
```

The resulting storage from w7.xml is: <devices>
```
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw' cache='none'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <alias name='ide0-1-0'/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source file='/Data/1TB/Other/VMs/Win7ult/Win7Ult-os.img'/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source file='/Data/1TB/Other/VMs/Win7ult/Win7Ult-Data2.img'/>
      <target dev='vdb' bus='virtio'/>
      <alias name='virtio-disk1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </disk>

```

There are 3 storage devices connected. 
* CDROM/DVD
* OS/Apps
* Data

```
$ du -sh  /Data/1TB/Other/VMs/Win7ult/Win7Ult-*.img

132G    /Data/1TB/Other/VMs/Win7ult/Win7Ult-Data2.img
49G     /Data/1TB/Other/VMs/Win7ult/Win7Ult-os.img
```
The exact files specified exist in the location specified for the OS/Apps and Data. Yes, that is a Windows7 Ultimate install - it does TV recording for me using 4 ATSC tuners.  I'm using fast spinning storage for this application - other VMs are on slower stuff.

---

### Post by redger on 2014-09-19
Interestingly, your point about dumping the xml was woth a thought. I can dump it ... even if I can't find the source file anywhere

yes, all my VM storage is located on LVM managed space. KVM-Qemu based VMs are each allocated an LVM partition (for performance and manageability reasons).
This was a "simple" VM, no fancy passthrough options on this one.

I'm not concerned about making the xml work ... I can easily make them work (and more :) ..... what I can't do in this case is successfull remove the VM definition
```
virsh dumpxml myvm
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>myvm</name>
  <uuid>eb605725-41e9-4617-96ee-11a52c93b87f</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='i686' machine='q35'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <controller type='sata' index='0'/>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='dmi-to-pci-bridge'/>
    <controller type='pci' index='2' model='pci-bridge'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='sdl'/>
    <video>
      <model type='vmvga' vram='9216' heads='1'/>
    </video>
    <memballoon model='virtio'/>
  </devices>
  <qemu:commandline>
    <qemu:arg value='\ -name'/>
    <qemu:arg value='myvm'/>
    <qemu:arg value='\ -cpu'/>
    <qemu:arg value='host'/>
    <qemu:arg value='-rtc'/>
    <qemu:arg value='base=localtime'/>
    <qemu:arg value='\ -boot'/>
    <qemu:arg value='menu=on,order=c'/>
    <qemu:arg value='\ -smp'/>
    <qemu:arg value='1,sockets=1,cores=1,threads=1'/>
    <qemu:arg value='\ -bios'/>
    <qemu:arg value='/usr/share/qemu/bios.bin'/>
    <qemu:arg value='\ -usbdevice'/>
    <qemu:arg value='tablet'/>
    <qemu:arg value='\ -spice'/>
    <qemu:arg value='port=5903,disable-ticketing,addr=127.0.0.1'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='virtio-serial-pci'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='virtserialport,chardev=spicechannel0,name=com.redhat.spice.0'/>
    <qemu:arg value='\ -chardev'/>
    <qemu:arg value='spicevmc,id=spicechannel0,name=vdagent'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='ioh3420,bus=pcie.0,addr=1c.1,multifunction=on,port=2,chassis=2,id=root.2'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='ich9-intel-hda,bus=root.2'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='hda-duplex,bus=hda.0'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='ahci,bus=pcie.0,id=ahci'/>
    <qemu:arg value='\ -net'/>
    <qemu:arg value='nic,macaddr=00:00:00:0a:xx:xx,model=virtio'/>
    <qemu:arg value='\ -net'/>
    <qemu:arg value='user'/>
    <qemu:arg value='\ -drive'/>
    <qemu:arg value='file=/dev/wd2t-lvm-data/ubuntu_kvm,id=disk1,format=raw,if=virtio'/>
    <qemu:arg value='\ -drive'/>
    <qemu:arg value='file=/mnt/programming_data/isos/kubuntu-14.04.1-trusty-desktop-amd64.iso,id=isocd1'/>
    <qemu:arg value='\ -device'/>
    <qemu:arg value='ide-cd,bus=ahci.1,drive=isocd1'/>
  </qemu:commandline>
</domain>
```

PS I protected the guilty again (very minor edit)

I hope you (and Bob) continue to find this entertaining ;) It isn';t boring for me, but imagine it might be for you

---

### Post by TheFu on 2014-09-20
/dev/wd2t-lvm-data/ubuntu_kvm

That is using direct device access via LVM. Unplug that drive.

That's what Bob says. ;)

---

### Post by redger on 2014-09-21
hmmmm .... that partition was deleted some time ago .... ad the space re-used for lxc_images ie. it's long gone, so I can't even take it off-line. The kubuntu image has been moved, VM undefined, libvirt stopped, offending VM log file removed, libvirt started .... VM resurrected - same problem :(
I even re-assured myself once again that all the definitions (including apparmor profile) are gone ....

is Bob feeling ok ? I think I need to lie down

---

### Post by TheFu on 2014-09-21
That is where the VM is. It cannot be anywhere else.

I'd backup anything else from that LV, remove the LV. Then recreate a new LV with a different name and move the LXC stuff back as desired.

Deleting log files doesn't mean anything.
What kubuntu image? 
What does the libvirt storage pool list contain?

Please show exact, unaltered commands going forward.

So - it has been another week - solved?

---

