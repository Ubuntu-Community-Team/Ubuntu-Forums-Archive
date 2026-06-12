---
title: "Trying to launch an ubuntu-cloud image in a vm, but Im getting this error."
date: 2022-12-29
forum: Virtualisation
---

### Post by tech1000 on 2022-12-29
[FONT=Source Sans Pro][COLOR=#22231f]Starting serial terminal on interface serial0. [/COLOR][/FONT]

[FONT=Source Sans Pro][COLOR=#22231f]The issue: It stays on this screen. As if the os is not initializing.[/COLOR][/FONT]

[FONT=Source Sans Pro][COLOR=#22231f]The proxmox server is nested through vmware vm. [/COLOR][/FONT]

[FONT=Source Sans Pro][COLOR=#22231f]I have also enabled virtualization[/COLOR][/FONT][COLOR=#22231F][FONT=&amp]

[/FONT][/COLOR][COLOR=#22231F][FONT=&amp]ubuntu-20.04-minimal-cloudimg-amd64.img

Steps I took: 

[/FONT][/COLOR][COLOR=#22231F][FONT=&amp]create 100 --memory 2048 --balloon 1 --core 3 --name ubuntu-cloud --net0 virtio,bridge=vmbr0 --serial0 socket --vga serial0 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm:-100disk-0

[/FONT][/COLOR][COLOR=#22231F][FONT=&amp]Then initialized and mounted a cloudinit drive.[/FONT][/COLOR][COLOR=#22231F][FONT=&amp]

[/FONT][/COLOR]

---

### Post by howefield on 2022-12-30
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by MAFoElffen on 2022-12-30
What URL are you getting your cloud images from? I don't see, in your 'Domain config' pointing to any cloud config image to setup your user and password on the first boot...

I use this to initialize my dailys to test
```

sudo virt-install \
  --name lunar-server-cloudimg-amd64 \
  --memory 1024 \
  --disk /data/KVM-VM/lunar-server-cloudimg-amd64.img,device=disk,bus=virtio \
  --disk /data/ISO/cloud-init.iso,device=cdrom \
  --os-type linux \
  --os-variant ubuntu22.04 \
  --virt-type kvm \
  --graphics none \
  --network network=default,model=virtio \
  --import

```
And see attached screenshot...

On the VM first run initialization, it will come up directly in the terminal window. On subsequent, I'll connect with a viewer window, which will connect as serial... There will be a square (cursor) in the upper left of the screen. I will click on it with my mouse, then press <Enter>... That then the screen initializes and it will ask me to login. (That's how serial consoles usually work.)

The second screenshot is it viewed as a regular guest with spice/qxl as a graphical viewed guest, instead of viewed as serial.

---

