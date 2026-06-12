---
title: "KVM - Cannot access shared host folder from guest"
date: 2023-09-07
forum: Virtualisation
---

### Post by drumboog on 2023-09-07
Hi,
I have an Ubuntu 22.04 host running KVM.  A guest is also running Ubuntu 22.04.  I have configured a folder to be shared with the following configuration on the host:

```
<filesystem type="mount" accessmode="passthrough">
  <driver type="virtiofs"/>
  <binary path="/usr/lib/qemu/virtiofsd"/>
  <source dir="/mnt/data"/>
  <target dir="/data"/>
  <alias name="fs0"/>
  <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
</filesystem>
```

This has been working fine, but today I've begun having problems connecting to the shared folder.  I can mount the drive from the guest with this command:

```
sudo mount -t virtiofs /data /mnt/data
```

However, attempting to navigate to the folder results in an error:

```
-bash: cd: data: Connection refused
```

Attempting to view permissions on the folder also results in an error:

```
$ ls -al
ls: cannot access 'data': Connection refused
total 8
drwxr-xr-x  3 root root 4096 Sep  7 22:53 .
drwxr-xr-x 20 root root 4096 Aug 24 22:03 ..
d?????????  ? ?    ?       ?            ? data
```

---

### Post by MAFoElffen on 2023-09-08
I find it easier to just do network shares between the Host and VM, but...

On yours:
```

<filesystem type="mount" accessmode="passthrough">
  <driver type="virtiofs"/>
  <binary path="/usr/lib/qemu/virtiofsd"/>
  <source dir="/mnt/data"/>
  <target dir="/data"/>
  <alias name="fs0"/>
  <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
</filesystem>

```
What happens if you change it to this
```

<filesystem type="mount" accessmode="passthrough">
  <driver type="virtiofs" queue='1024' />
  <binary path="/usr/lib/qemu/virtiofsd"/>
  <source dir="/mnt/data"/>
  <target dir="/data"/>
  <alias name="fs0"/>
  <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
</filesystem>

```
... adding "quote="1024" to the driver line, which is the only way I've seen a working virtiofs share work... 

Then ensure that in this line:
```

  <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>

```
That the combined address noted there, is unique to anything other PCIe address in the Domain XML...

The usually fstab line looks like this:
```

target_directory_tag            /data       virtiofs     defaults 0 0

```
Where is the XMl for your VHost-User memory Backend setup? Look for a "<memoryBacking>" Tag within the <domain> tag... Which is tied to the virtiofs device definition for it to work.

I'm curious if it is actually mounted or halfway there... Or maybe the memory access causing that,,, and that those problems may be why it is getting access problems. Just guessing on that.

Does it show up in the output of 
```

mount | grep -e 'virtiofs'

```

---

### Post by deadflowr on 2023-09-09
Is it supposed to be quote or queue?

---

### Post by MAFoElffen on 2023-09-09
Looking here at LibVirt.org, for reference "queue": [https://libvirt.org/kbase/virtiofs.html](https://libvirt.org/kbase/virtiofs.html)

---

### Post by txfinds55 on 2023-09-10
[COLOR=#1F1F1F][FONT=&quot]There are a few reasons why you might not be able to access a shared host folder from a KVM guest. Here are some things to check:[/FONT][/COLOR]

[LIST]
[*]Make sure that the shared folder is mounted on the guest. You can do this by opening a terminal and running the following command:
[/LIST]
mount

[COLOR=#1F1F1F][FONT=&quot]This will list all of the mounted filesystems, including the shared host folder. If the shared host folder is not listed, then it is not mounted. To mount the shared host folder, you can use the following command:[/FONT][/COLOR]
mount -t hostfs host_folder_path guest_folder_path


[LIST]
[*]Make sure that the permissions on the shared host folder are correct. The guest user must have read and write permissions to the shared host folder. You can check the permissions on the shared host folder by running the following command:
[/LIST]
ls -l host_folder_path


[LIST]
[*]Make sure that the network is configured correctly. The guest must be able to access the host machine on the network. You can check the network configuration on the guest by running the following command:
[/LIST]
ifconfig

[COLOR=#1F1F1F][FONT=&quot]If you have checked all of these things and you are still unable to access the shared host folder from the guest, then you may need to consult the documentation for your KVM hypervisor.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]Here are some additional things to check:[/FONT][/COLOR]

[LIST]
[*]The guest machine must be running a supported operating system. Not all operating systems are supported for shared folders with KVM.
[*]The shared folder must be accessible to the guest user. The guest user must have the appropriate permissions to access the shared folder.
[*]The shared folder must be mounted on the guest machine. The guest machine must be able to see the shared folder in order to access it.
[*]The network connection between the host machine and the guest machine must be working properly. The guest machine must be able to reach the host machine in order to access the shared folder.
[/LIST]
[COLOR=#1F1F1F][FONT=&quot]If you have checked all of these things and you are still unable to access the shared host folder from the guest, then you may need to contact the support for your KVM hypervisor.[/FONT][/COLOR]

---

### Post by fmoor on 2023-09-11
This is bug in qemu [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/2033957](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/2033957)

---

### Post by drumboog on 2023-09-12
Thanks for your help, I'm moving it to a network share between the host and guest instead.

---

