---
title: "uefi ubuntu boot entry missing after grub upgrade"
date: 2014-08-18
forum: Server Platforms
---

### Post by fgerardi on 2014-08-18
Hi,

I have recently upgraded one of my ubuntu servers (12.04 LTS). 
In the list of packages to be upgraded grub was also present.
After the upgrade the ubuntu boot entry is missing from the list presented by the command "efibootmgr".

I tried to issue the command "grub-install --bootloader-id ubuntu /dev/sda" and also the command "efibootmgr --create --label "ubuntu" --loader "\EFI\ubuntu\grubx64.efi"" but both commands failed to insert an entry in the uefi boot list.

I am aware of a rescue procedure using the ubuntu installation cd but this would be very time consuming as I need to be in front of the server (I generally manage the servers from remote) and I need to repeat the complete rescue procedure for all the server.

As I didn't reboot the server yet do you know a procedure to create the right ubuntu boot entry?

Thanks in advance

---

