---
title: "Ubuntu 22.02 Autoinstall errors"
date: 2022-06-16
forum: Server Platforms
---

### Post by scott-ehas on 2022-06-16
Ubuntu's new unattended install method does not perform an autoinstall when loading from pxeboot.  This auto install was taken from a manual install, and I've tried the default as well.  The nginx logs show the user-data, vendor-data, and meta-data files are being grabbed from the pxe boot without issues. This is my pxe configuration, user-data configuration, and I get the following errors in the installer logs.  

subiquity-server-debug.log:2022-06-16 13:10:26,784 ERROR root:39 finish: subiquity/Refresh/check_for_update: FAIL: cancelled
subiquity-server-debug.log:2022-06-16 13:10:26,784 ERROR root:39 finish: subiquity/Refresh/check_for_update: FAIL: cancelled
subiquity-server-debug.log:2022-06-16 13:10:26,786 ERROR root:39 finish: subiquity/Refresh/check_for_update: FAIL: cancelled
subiquity-server-debug.log:2022-06-16 13:10:26,787 ERROR root:39 finish: subiquity/Refresh/check_for_update: FAIL: cancelled

#
MENU TITLE Template Ubuntu22


DEFAULT default
TIMEOUT 1
LABEL default
  MENU LABEL default
  KERNEL linux/vmlinuz/Ubuntu22_x86_64 #Taken form ISO
  INITRD linux/initrd/Ubuntu22_x86_64 #Taken from ISO
  APPEND ip=dhcp url=http://172.27.0.3/ubuntu/ubuntu-22.04-live-server-amd64.iso autoinstall ds=nocloud-net;s=http://placeholder.com/queue/tmp/ks/ac:1f:6b:83:d3:3c/

cat /var/log/installer/autoinstall-user-data
#cloud-config
autoinstall:
  apt:
    disable_components: []
    geoip: true
    preserve_sources_list: false
    primary:
    - arches:
      - amd64
      - i386
      uri: [http://mirrors.gigenet.com/ubuntuarchive](http://mirrors.gigenet.com/ubuntuarchive)
    - arches:
      - default
      uri: [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)
  drivers:
    install: false
  identity:
    hostname: demo-01
    password: ------------
    realname: ubuntu
    username: ubuntu
  kernel:
    package: linux-generic
  keyboard:
    layout: us
    toggle: null
    variant: ''
  locale: en_US.UTF-8
  network:
    ethernets:
      ens1f0:
        critical: true
        dhcp-identifier: mac
        dhcp4: true
        nameservers:
          addresses:
          - 8.8.8.8
      ens1f1:
        dhcp4: true
    version: 2
  ssh:
    allow-pw: true
    authorized-keys: []
    install-server: true
  storage:
    config:
    - ptable: gpt
      serial: INTEL_SSDSC2BB120G4_PHWL441301X6120LGN
      wwn: '0x55cd2e404c409ee0'
      path: /dev/sda
      wipe: superblock-recursive
      preserve: false
      name: ''
      grub_device: true
      type: disk
      id: disk-sda
    - device: disk-sda
      size: 1048576
      flag: bios_grub
      number: 1
      preserve: false
      grub_device: false
      type: partition
      id: partition-0
    - device: disk-sda
      size: 120030494720
      wipe: superblock
      flag: ''
      number: 2
      preserve: false
      grub_device: false
      type: partition
      id: partition-1
    - fstype: ext4
      volume: partition-1
      preserve: false
      type: format
      id: format-0
    - path: /
      device: format-0
      type: mount
      id: mount-0
  updates: security
  version: 1

---

