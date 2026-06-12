---
title: "Could not find kernal image: /casper/vmlinuz"
date: 2014-06-22
forum: Virtualisation
---

### Post by TJSL on 2014-06-22
(may also apply to "Could not find kernel image: /install/vmlinuz")

I am using Packer upstream of Vagrant to build virtual machines. However, this problem may also be appearing with respect to USB installations. Upon boot, parameters are passed to the system to identify the location of the kernal image. If this path is incorrect or the file does not exist, you may receive an error: "Could not find kernal image: /casper/vmlinuz" You can verify that  /casper/vmlinuz exists by opening the ISO in Archive Manager. In my case, the path provided to the boot command was wrong (/casper/vmlinuz.efi, not /casper/vmlinuz, in my case)(see corrected boot command below). Although this code was copied from the packer json configuration file, I am assuming a similar boot parameter is provided by preseed during USB installation. (please note that my virtual machine is still failing downstream at Busybox initramfs promt, but this solution at least addressed the problem with finding the kernel image. 

      "boot_command": [
        "<esc><esc><esc><enter><wait5>",
        "/casper/vmlinuz.efi noapic preseed/url=http://{{ .HTTPIP }}:{{ .HTTPPort }}/preseed.cfg <wait>",
        "debian-installer=en_US auto locale=en_US kbd-chooser/method=us <wait>",
        "hostname={{ .Name }} <wait>",
        "fb=false debconf/frontend=noninteractive <wait>",
        "keyboard-configuration/modelcode=SKIP keyboard-configuration/layout=USA keyboard-configuration/variant=USA console-setup/ask_detect=false <wait>",
        "initrd=/casper/initrd.lz -- <enter><wait>"
      ],

---

