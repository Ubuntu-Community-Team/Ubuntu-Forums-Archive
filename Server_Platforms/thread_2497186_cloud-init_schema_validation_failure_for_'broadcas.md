---
title: "cloud-init schema validation failure for: 'broadcast'"
date: 2024-04-26
forum: Server Platforms
---

### Post by rayhvh on 2024-04-26
[COLOR=#000000][FONT=&quot][FONT=&quot]When installing the LTS of ubuntu 24.04,
I am getting the :"cloud-init schema validation failure for: 'broadcast'' error.
from the 'extract_autoinstall' function.
however when running: cloud-init schema -c /var/lib/cloud/instance/cloud-config.txt
I am getting a valid return.

[IMG]https://bugs.launchpad.net/ubuntu/+source/cloud-init/+bug/2063813/+attachment/5770840/+files/MicrosoftTeams-image%20%2822%29.png[/IMG]
My identical cloud-init configuration applied to 22.04 successfully.
I am not trying to do anything custom to the broadcast address.
This is my cloud init:
#cloud-config
chpasswd:
  expire: false
  list:
  - installer:$somereallylonghashpassword
write_files:
- path: /etc/ssh/sshd_not_to_be_run
  content: ""
autoinstall:
  version: 1
  proxy: [http://172.16.100.2:3142/](http://172.16.100.2:3142/)
  apt:
    preserve_sources_list: false
    primary:
    - arches:
      - default
      uri: [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/)
    disable_suites: [backports]
    disable_components: [multiverse]
  storage:
    layout:
      name: direct
      match:
        path: $WSBOOTDEV
  ssh:
    install-server: true
    allow-pw: true
  debconf-selections: |
    popularity-contest popularity-contest/participate boolean false
  network:
    ethernets:
      $bootif:
        addresses:
        - 127.0.0.2/24
        match:
          macaddress: 22:22:33:44:55:66
        nameservers:
          addresses:
          - 172.16.100.3
        routes:
        - to: default
          via: 127.0.0.1
        accept-ra: false
    version: 2
  early-commands:
  - |
      FIRSTPCI=$({ cd /dev/disk/by-path/
        ls | grep nvme | head -1
        ls | grep sas | head -1
        ls | grep scsi | grep -v usb | head -1
        ls | grep ata | head -1
      } | head -1)
      WSBOOTDEV="$(readlink -f /dev/disk/by-path/$FIRSTPCI)"
      sed -i "s|\$WSBOOTDEV|$WSBOOTDEV|" /autoinstall.yaml
  updates: all
  late-commands:
  - rm /target/etc/apt/apt.conf.d/*proxy* /target/etc/systemd/system/snapd.service.d/*proxy*
  - sed -i -E 's/^#?PermitRootLogin [[:alpha:]]+-password/PermitRootLogin yes/' /target/etc/ssh/sshd_config
  - sed -i -E 's/^(GRUB_CMDLINE_LINUX_DEFAULT=)"(.+)"$/\1"\2 ipv6.autoconf=0"/g' /target/etc/default/grub
  - curtin in-target --target /target update-grub2
  user-data:
    users: []
    hostname: NLDW3-3-03-15
    chpasswd:
      expire: false
      list:
      - root:$somereallylonghashpassword
    timezone: Europe/Amsterdam



[/FONT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][/FONT][/COLOR]

---

### Post by rayhvh on 2024-04-26
[COLOR=#000000][FONT=&quot]related to:[/FONT][/COLOR]
[https://bugs.launchpad.net/ubuntu/+source/cloud-init/+bug/2056460](https://bugs.launchpad.net/ubuntu/+source/cloud-init/+bug/2056460)
[https://bugs.launchpad.net/subiquity/+bug/2062988](https://bugs.launchpad.net/subiquity/+bug/2062988)

---

