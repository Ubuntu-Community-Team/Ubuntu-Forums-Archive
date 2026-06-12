---
title: "Boot Ubuntu Cloud image on arm64v8 host"
date: 2018-12-12
forum: Ubuntu Cloud and Juju
---

### Post by apoz on 2018-12-12
Hi, 

I'm having some trouble booting Ubuntu cloud prebuilt image over qemu-kvm on a Arm64v8 server.
The VM boots into UEFI shell, but I'm not able to find where the Image should be booted from.
Some information:
* The image I'm trying to boot is ubuntu-16.04-server-cloudimg-amd64-uefi1.img (just renamed)
* I made some iso file with basic cloud-init configuration
* The script I use to create the VM is the following:
```
virt-install \
  --virt-type=kvm \
  --graphics none \
  --autostart \
  --arch aarch64 \
  --name "ubuntu-1" \
  --memory "16384" \
  --machine virt \
  --vcpus "4" \
  --boot uefi \
  --os-type linux \
  --disk path=/ubuntu-1/ubuntu-1.img,device=disk,bus=virtio \
  --disk path=/ubuntu-1/cloud-init/cloud.img,device=cdrom \
  --network bridge=br_cli,model=virtio \
  --import
```

* The bridge is already available in the machine


Then, the VM gets booted into the following menu:
```

UEFI Interactive Shell v2.1
EDK II
UEFI v2.60 (EDK II, 0x00010000)
Mapping table
      FS0: Alias(s):HD1p:;BLK4:
          VenHw(837DCA9E-E874-4D82-B29A-23FE0E23D1E2,003C000A00000000)/HD(15,GPT,8D969F68-5A0D-4326-A274-51238E44DCB1,0x2800,0x35000)
     BLK6: Alias(s):
          VenHw(F9B94AE2-8BA6-409B-9D56-B9B417F53CB3)
     BLK0: Alias(s):
          VenHw(8047DB4B-7E9C-4C0C-8EBC-DFBBAACACE8F)
     BLK1: Alias(s):
          VenHw(837DCA9E-E874-4D82-B29A-23FE0E23D1E2,003C000A00000000)
     BLK2: Alias(s):
          VenHw(837DCA9E-E874-4D82-B29A-23FE0E23D1E2,003C000A00000000)/HD(1,GPT,E1207878-06B2-46BC-9F37-50641B00EEB8,0x37800,0x42E7DF)
     BLK3: Alias(s):
          VenHw(837DCA9E-E874-4D82-B29A-23FE0E23D1E2,003C000A00000000)/HD(14,GPT,6174B15D-E999-459C-B7B0-43B4FFB5A8C7,0x800,0x2000)
     BLK5: Alias(s):
          VenHw(837DCA9E-E874-4D82-B29A-23FE0E23D1E2,003E000A00000000)/Scsi(0x0,0x0)




Press ESC in 2 seconds to skip startup.nsh or any other key to continue.
```

Then I know (because of some posts about similar issues) I have to look for the grubx64.efi file, but when I select it from FS0 I get the following error:
```
Shell> FS0:\EFI\BOOT\grubx64.efi
Command Error Status: Unsupported
```

I am not able to find any file under the BLKX blocks. Is it normal??
```
BLK2:\> ls
ls: File Not Found - 'BLK2:\'
```


I'd appreciate if anyone can provide some hint so I can boot those cloud images.

Thanks!

---

