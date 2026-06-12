---
title: "Switched BIOS to Secure Boot and now get 'fail to install' target error"
date: 2015-03-21
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-03-21
Following up on some UEFI testing with new 3TB SATAIII hdd, Windows 10 installed and chose "Replace vivid vervet with ubuntu mate" option after booting USB iso stick in UEFI mode and get the error message from Ubiquity:

My logical next choice will be "Ok"

This:  [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1434871](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1434871)   is a duplicate of
[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1252255](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1252255) whcih they just let fall off the edge of the earth...

  I am certain it has something to do with secure boot enabled.

Now I see what grahammecanical was talking about.

Regards..

---

### Post by grahammechanical on 2015-03-22
Was secure boot enabled when Ubuntu was installed? I do not have a boot system with secure boot so I do not get the signed kernel. So, I imagine if we turn secure boot off then Ubiquity will not install a signed kernel and therefore turning secure boot back on would stop Ubuntu from loading? But this is not something I can test personally.

Boot Repair might fix it by re-installing a signed kernel. Looking again at your screenshot, I ask, is there an efi partition for those efi files to go in? It seems that an attempt is being made to put them in / and I do not think that is right.

Regards.

---

### Post by ventrical on 2015-03-22
> **grahammechanical said:**
> Was secure boot enabled when Ubuntu was installed? I do not have a boot system with secure boot so I do not get the signed kernel. So, I imagine if we turn secure boot off then Ubiquity will not install a signed kernel and therefore turning secure boot back on would stop Ubuntu from loading? But this is not something I can test personally.

Boot Repair might fix it by re-installing a signed kernel. Looking again at your screenshot, I ask, is there an efi partition for those efi files to go in? It seems that an attempt is being made to put them in / and I do not think that is right.

Regards.

Yes .. Secure  boot was enabled. I did it manually as an experiment and that is where the 'fail to install' report subsequently came from. However , it will install in UEFI with secure boot off. I used daily-live/current ubuntu-mate amd64.iso for test.

Regards.

edit:

I guess I might as well do it right. I will wipe current Windows 10 install and re-install with SecureBoot enabled, then , rertry the experiment and test if I can install Ubuntu. I know a lot of this ground has been covered but I think it needs be gone through again.

btw... I was making reference as to another post you made in another foums about how new users end up with bricked or broken systems when using UEFI and secure boot options.

---

### Post by grahammechanical on 2015-03-22
> [COLOR=#000000][INDENT]btw... I was making reference as to another post you made in another foums about how new users end up with bricked or broken systems when using UEFI and secure boot options.[/INDENT]


[/COLOR]


I thought that was what you were doing. I have difficulty in advising these people except to repeat the creed from the wiki page. As I did with you. I like to have a clear understanding of the situation without making assumptions.

Ubuntu was supposed to have fix installing with secure boot on but who knows? Some UEFI system have been modified to only load a Windows OS. So, who knows if other modifications have been done to use secure boot to cause problems.

Although, I should think that the motherboard you are using pre-dates that kind of thing. Anyway practical experience is very useful when giving advice. So, I am following your experiments.

Regards.

---

### Post by ventrical on 2015-03-23
> **grahammechanical said:**
> 

Although, I should think that the motherboard you are using pre-dates that kind of thing. Anyway practical experience is very useful when giving advice. So, I am following your experiments.

Regards.

It's a 2013 MSi mobo. It has all the bells and whistles.  I bought the board bare metal with nothing installed so there is no O.E.M. serial number .. etc..

  The only thing not included was the TPM module. I'm not worried about that though.

 Back to work ... :)

---

### Post by oldfred on 2015-03-26
Finally back to my UEFI machine.

Installed Vivid to sdb. It still installs grub to sda even when sdb specified. And overwrites my existing ubuntu folder with my 14.04 Ubuntu efi files. 

Also it now mounts efi partition with 0077 which means we cannot even look at the efi partition. Most systems require UEFI fixes and edits in the efi partition.

 14.04 fstab entry defaults
drwxr-xr-x 3 root root     4096 Dec 31  1969 efi
drwxr-xr-x 5 root root     4096 Mar 24 12:08 grub
15.04 fstab entry umask=0077
drwx------ 3 root root     4096 Dec 31  1969 efi
drwxr-xr-x 5 root root     4096 Mar 26 13:52 grub

I changed back to defaults and then it seemed to be ok.

Also did prove that you can change the name in UEFI. Did this for both trusty & vivid and now have separate folders in efi partition. Just all are in sda, none in my sdb efi partition.
      
 #GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="trusty"

And just did a reinstall to sdb, (but it installed to sda). I will change UUID in fstab to sdb's efi partition and reinstall to sdb and see if it then works.
       sudo grub-install /dev/sdb
    


```
 BootOrder: 0004,0003,0000,0001,0002,000C,0010,0011
Boot0000* ubuntu    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Windows Boot Manager    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File( \EFI\UBUNTU\SHIMX64.EFI)
Boot0002* UEFI OS    ACPI(a0341d0,0)PCI(1f,2)03120a000000ffff0000HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)..BO
Boot0003* [COLOR=#ff0000]vivid[/COLOR]    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\VIVID\SHIMX64.EFI)
Boot0004* [COLOR=#ff0000]trusty[/COLOR]    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\trusty\shimx64.efi)


```

---

