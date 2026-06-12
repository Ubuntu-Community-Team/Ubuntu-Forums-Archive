---
title: "Autoinstall+raid user-data yaml"
date: 2023-08-04
forum: Server Platforms
---

### Post by smithontoast on 2023-08-04
Hi Folks,

I hope this is the right section, I was torn between the ubuntu install section and the server section of the forum however as the install seemed to be pretty desktop centric I opted for this.

I have reached a point with a hardware refresh that (sadly) I can no longer use preseed as the nics are to new for the netboot kernel and it is not recognised so I have spent the week working on bringing myself up to date, sadly the autoinstall documentation is quite sparse [https://ubuntu.com/server/docs/install/autoinstall-reference](https://ubuntu.com/server/docs/install/autoinstall-reference) and I have gone through the 3 - 4 years wrth of test your autoinstall files threads and I can find no answers.

The goal.

To have a working storage config to achieve.

EFI partitions sda1/sdb2
Swap 2GB sda2/sdb2 (raid1 /dev/md1)
Root file system sda3/sdb3 (raid1 /dev/md2)

However I can find no combination of methods to get this to work and wondered if anyone has had any similar experiences or has an example of a working raid 1 config with no LVM?

with preseed it is trivial

```
d-i partman-auto/disk string /dev/sda /dev/sdb
d-i partman-auto/expert_recipe      string multiraid :: \
    256   512    512   free       $bootable{ } method{ efi } format{ } . \
    1024  10000  -1    raid       method{ raid } . \
    4096  4096   4096  linux-swap method{ raid } format{ } .
d-i partman-auto-raid/recipe string     \
    1 2 0 ext4 / /dev/sda2#/dev/sdb2.   \
    1 2 0 swap - /dev/sda3#/dev/sdb3 .

```


However with autoinstall yaml (user-data) I cant get it to work, here is what I have:

```
storage:
  config:
    - {type: disk, id: disk-sda, match: {path: "/dev/sda"}}
    - {type: disk, id: disk-sdb, match: {path: "/dev/sdb"}}
    - {type: partition, id: sda1, device: disk-sda, size: 512M}
    - {type: partition, id: sdb1, device: disk-sdb, size: 512M}
    - {type: partition, id: sda2, device: disk-sda, size: -1}
    - {type: partition, id: sdb2, device: disk-sdb, size: -1}
    - {type: raid, id: raid-root, name: md0, raidlevel: 1, devices: [sda2, sdb2]}
    - {type: format, id: format-efi-sda1, volume: sda1, fstype: fat32}
    - {type: format, id: format-efi-sdb1, volume: sdb1, fstype: fat32}
    - {type: format, id: format-root, volume: raid-root, fstype: ext4}
    - {type: mount, id: mount-efi-sda1, device: format-efi-sda1, path: /boot/efi}
    - {type: mount, id: mount-root, device: format-root, path: /}

```

the install goes through without issue however what I actually get is:

```
[COLOR=#39C026][FONT=Menlo]**ubuntu@test1**[COLOR=#000000]:[/COLOR][COLOR=#5620F4]**~**[/COLOR][COLOR=#000000]$ df -h[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Filesystem                         Size  Used Avail Use% Mounted on[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]udev                               7.7G     0  7.7G   0% /dev[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs                              1.6G  1.4M  1.6G   1% /run[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/mapper/ubuntu--vg-ubuntu--lv   98G  6.7G   87G   8% /[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs                              7.8G     0  7.8G   0% /dev/shm[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs                              5.0M     0  5.0M   0% /run/lock[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs                              7.8G     0  7.8G   0% /sys/fs/cgroup[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdb2                          2.0G  109M  1.7G   6% /boot[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdb1                          1.1G  6.1M  1.1G   1% /boot/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop0                          64M   64M     0 100% /snap/core20/1828[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop1                          50M   50M     0 100% /snap/snapd/18357[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop2                          92M   92M     0 100% /snap/lxd/24061[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]tmpfs                              1.6G     0  1.6G   0% /run/user/1000[/FONT][/COLOR]
[COLOR=#39C026][FONT=Menlo]**ubuntu@test1**[COLOR=#000000]:[/COLOR][COLOR=#5620F4]**~**[/COLOR][COLOR=#000000]$ lsblk[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]loop0                       7:0    0  63.3M  1 loop /snap/core20/1828[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]loop1                       7:1    0  49.9M  1 loop /snap/snapd/18357[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]loop2                       7:2    0  91.9M  1 loop /snap/lxd/24061[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]sda                         8:0    0 447.1G  0 disk [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]sdb                         8:16   0 447.1G  0 disk [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9500;&#9472;sdb1                      8:17   0   1.1G  0 part /boot/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9500;&#9472;sdb2                      8:18   0     2G  0 part /boot[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9492;&#9472;sdb3                      8:19   0 444.1G  0 part [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   100G  0 lvm  /[/FONT][/COLOR]

```

I also tried to split it out a bit more incase something was being missed:

```
storage:
  config:
    - id: disk-sda
      type: disk
      ptable: gpt
      path: /dev/sda
      wipe: superblock-recursive
    - id: disk-sdb
      type: disk
      ptable: gpt
      path: /dev/sdb
      wipe: superblock-recursive
    - id: partition-sda1
      type: partition
      device: disk-sda
      number: 1
      size: 512M
      flag: boot
    - id: partition-sdb1
      type: partition
      device: disk-sdb
      number: 1
      size: 512M
      flag: boot
    - id: partition-sda2
      type: partition
      device: disk-sda
      number: 2
      size: -1
    - id: partition-sdb2
      type: partition
      device: disk-sdb
      number: 2
      size: -1
    - id: raid-root
      type: raid
      raidlevel: 1
      devices: [partition-sda2, partition-sdb2]
    - id: format-partition-sda1
      type: format
      fstype: fat32
      label: efi
      volume: partition-sda1
    - id: format-partition-sdb1
      type: format
      fstype: fat32
      label: efi
      volume: partition-sdb1
    - id: format-raid-root
      type: format
      fstype: ext4
      label: root
      volume: raid-root
    - id: root-mount
      type: mount
      path: /
      device: format-raid-root
      options: errors=remount-ro
      passno: 1
    - id: boot-mount
      type: mount
      path: /boot/efi
      device: format-partition-sda1
      passno: 1

```

Exactly the same issue.

It defaults to sdb which is a bit odd to start with but reading the autoinstall docs I kind of understand why at least, if however I ONLY replace the storage section to target sda instead that works fine to target a single disk with no LVM which validates the rest of the yaml/autoinstall config I suppose, single disk target method for reference below:

```
[COLOR=#000000][FONT=Menlo]  [/FONT][/COLOR][COLOR=#D1D2D3][FONT=Monaco]storage:[/FONT][/COLOR]   config:
   - id: disk-sda
     type: disk
     ptable: gpt
     path: /dev/sda
     name: osdisk
     wipe: superblock-recursive
   - id: partition-sda1
     type: partition
     device: disk-sda
     number: 1
     size: 512M
     flag: boot
     grub_device: true
   - id: partition-sda2
     type: partition
     device: disk-sda
     number: 2
     size: 100G
   - id: format-partition-sda1
     type: format
     fstype: fat32
     label: efi
     volume: partition-sda1
   - id: format-partition-sda2
     type: format
     fstype: ext4
     label: root
     volume: partition-sda2
   - id: root-mount
     type: mount
     path: /
     device: format-partition-sda2
     options: errors=remount-ro
     passno: 1
   - id: boot-mount
     type: mount
     path: /boot/efi
     device: format-partition-sda1
     passno: 1
```

rest of yaml for reference excluding storage:

```
[COLOR=#000000][FONT=Menlo]autoinstall:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  version: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  refresh-installer:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      update: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      channel: 'stable'[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  user-data:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      disable_root: false[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  identity:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      hostname: test1.local[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      username: ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      password: $6$<redacted>
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  locale: en_US.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  keyboard:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    layout: us[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  disable_root: false[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  timezone: Europe/London[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  ssh:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    allow-pw: true[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    install-server: true[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  apt:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    preserve_sources_list: false[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    primary:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    - arches: amd64[/FONT][/COLOR]
[COLOR=#CF7DFF][FONT=Menlo][COLOR=#000000]      uri: [/COLOR]<local mirror redacted have tested with public also no difference>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    - arches: [default][/FONT][/COLOR]
[COLOR=#CF7DFF][FONT=Menlo][COLOR=#000000]      uri: [/COLOR]http://ports.ubuntu.com/ubuntu-ports[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  packages:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    - build-essential[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  package_update: true[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  package_upgrade: true[/FONT][/COLOR]
[COLOR=#38B9C7][FONT=Menlo]  #Network[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  network:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    version: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    ethernets:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]      enp1s0f0:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        match:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]              macaddress: <redacted>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        addresses:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]          - <redacted>/30[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        gateway4: <redacted>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        nameservers:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]             addresses:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]               - 8.8.8.8[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]               - 1.1.1.1[/FONT][/COLOR]

```



I also tried using early commands to create the mdadm raid arrays and then target the arrays directly but I guess apart from the fact that should not be necessary the changes to the partition table at that stage in the install forces a crash/error and partprobe does not work as expected in the preinstall and demands a reboot (which obviously cannot happen)

any and all suggestions very welcome, if not I hope some snippets of my yaml files help someone else some day, there are simply not enough functional examples out there right now.

---

