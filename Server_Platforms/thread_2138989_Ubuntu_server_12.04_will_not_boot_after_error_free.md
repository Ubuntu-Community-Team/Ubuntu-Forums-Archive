---
title: "Ubuntu server 12.04 will not boot after error free install"
date: 2013-04-25
forum: Server Platforms
---

### Post by sangsterthegangster on 2013-04-25
Hello, Im an intern trying to install ubuntu 12.04 on a single node of a Dell Poweredge C6100.

I've installed Ubuntu twice already and both have failed to boot; even with seemigly smooth installs.

I feel it might be a grub issue since it does not load either. After all the bios stuff loads it just sits there with a blinking cursor and never does anything. I installed grub to the correct location; Which was the raid setup (somthing like /dev/mapper/isw_bgibiaahbd_Volume0P1). So I'm allitle confused as to why that would be happining.

I double checked the boot options in the bios and even the raid controller's setup. Every thing seems in order.

The only thing that seems to be out of orders is my install usb stops being readable while it loads the install components. But then I just tell the Install to load to scan for ISOs ( I put one on the usb) and the install works great from there. Don't think that really matters, just trying to give as much info as I can.  

Does anybody have any ideas as to why the node will not boot?

Thanks

---

### Post by tripp98 on 2013-05-05
reburn the usb installer or burn to cd and install from there.  if the install is failing blank screen will result.

how many drives do you have what is total size of raid.  are you installing to a disk or to the disk array?

---

