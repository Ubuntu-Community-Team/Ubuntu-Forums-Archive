---
title: "autoinstall not reading cloud-config data"
date: 2022-03-08
forum: Server Platforms
---

### Post by kmcgregor-cow on 2022-03-08
I had set up the Packer (1.7.10) system found at [https://github.com/vmware-samples/packer-examples-for-vsphere](https://github.com/vmware-samples/packer-examples-for-vsphere) and pretty much got it working (subiquity crashes near the end of the build, but that's another story). I modified the config for Ubuntu 20.04.4 to use 'bios' firmware instead of 'efi-secure', so I've had to change the boot_command like so:
boot_command = [
    "<esc><wait2><enter><wait2><f6><esc><wait>",
    "autoinstall ${local.data_source_command}<wait5><enter>"
  //  "<esc><wait>",
  //  "linux /casper/vmlinuz --- autoinstall ${local.data_source_command}",
  //  "<enter><wait>",
  //  "initrd /casper/initrd",
  //  "<enter><wait>",
  //  "boot",
  //  "<enter>"
  ]

The commented-out portion was the original which worked for the efi-secure firmware. When the Ubuntu Server installation screen comes up, the build system types
autoinstall ds="nocloud-net;seedfrom=http://<IP>:<PORT>/"
after the "---", where IP and PORT are the same as what worked for the efi-secure firmware. What happens after the boot, though, is that the Ubuntu installer shortly ends up with the usual interactive install, ignoring the autoinstall data.

Is there a log somewhere which would indicate where this is going wrong? I can't tell if I botched the command line, if it can't contact the HTTP server, or there is a problem with, well, anything else. It definitely worked for the efi-secure firmware and the previous boot_command strings.

---

### Post by MAFoElffen on 2022-03-09
Question: Where do you have the Array variable named "local.data_source_command" defined and what is it defined as?

---

