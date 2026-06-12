---
title: "Ubuntu 20.04 on Raspberry Pi - Network Configuration using Netplan"
date: 2020-07-08
forum: Server Platforms
---

### Post by m-dw on 2020-07-08
I've got my Pi up and running headless, using the default settings. It has inherited the settings from network-config file (in the system-boot partition) in a file called /etc/netplan/50-cloud-init.yaml. I would like to use netplan directly using /etc/netplan/01-netcfg.yaml.

Is it simply a case of creating a correctly formed 01-netcfg.yaml, or do I also have to create the file /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg to disable the default configuration?

---

### Post by m-dw on 2020-07-09
In the interests of science, I will try it and report back.

---

### Post by LHammonds on 2020-07-10
The [cloud-init](https://cloudinit.readthedocs.io/en/latest/) is installed by default when using the live installer.  I am small-time and have no [use for it](https://www.quora.com/What-is-cloud-init-and-when-would-you-use-it) so I either use the legacy installer (which is the Debian-based installer and apparently won't exist after 20.04) or simply remove cloud-init if you do not intend on using it.

LHammonds

---

### Post by m-dw on 2020-07-10
In this case it was very useful (I don't have a mini-HDMI cable) so I was grateful for its presence in the Pi image. It got me up-and-running so I could SSH into the address assigned by DHCP.


 And the answer is: "Yes, all it needs is a correctly formed 01-netcfg.yaml"

```
  System information as of Fri Jul 10 17:38:32 BST 2020

  System load:  0.0                Processes:                126
  Usage of /:   19.4% of 14.29GB   Users logged in:          0
  Memory usage: 14%                IPv4 address for vlan100: 192.168.254.4
  Swap usage:   0%                 IPv4 address for vlan200: 192.168.0.4
  Temperature:  68.2 C

```

---

### Post by dyoms on 2020-07-10
i think when you created another network configuration inside the netplan directory, it will automatically be used when you do "sudo netplan apply" command and the default configuration will be left as it is.

---

### Post by m-dw on 2020-07-13
I think you are partially correct. cloud-init is ignored completely, and the network configuration it created was deleted when I ran "sudo netplan apply". Cloud-init is not invoked on reboot.

---

