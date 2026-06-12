---
title: "VM Player update 10.10 to 11.04 grub rescue"
date: 2012-03-25
forum: Virtualisation
---

### Post by bxdobs on 2012-03-25
I have just updated from ubuntu 10.10 to 11.04 ... all went well until the VM session restarted ... the first issue was the screen came up with a grub prompt ... searching around online the solution was to do the following:

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

The VM booted into 11.04 ... the next instruction was to:

sudo grub-install /dev/sda1
sudo update-grub

[http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/](http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/)

The VM now boots into grub rescue ... most posts I see suggest that the only way to fix this is to do a fresh install from a CD copy of this version of LINUX ... I have already spent 2 days on this project and still don't know where to go from here.

---

### Post by dcstar on 2012-03-26
> **bxdobs said:**
> I have just updated from ubuntu 10.10 to 11.04 ... all went well until the VM session restarted ... the first issue was the screen came up with a grub prompt ... searching around online the solution was to do the following:

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

The VM booted into 11.04 ... the next instruction was to:

sudo grub-install /dev/sda1
sudo update-grub

[http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/](http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/)

The VM now boots into grub rescue ... most posts I see suggest that the only way to fix this is to do a fresh install from a CD copy of this version of LINUX ... I have already spent 2 days on this project and still don't know where to go from here.

Version updates are always problematical, it is always better to do fresh installs (and why you would bother to "update" to that old version when 12.04 is imminent is baffling). This is most likely not a VM issue, it is just a standard Ubuntu boot issue.

The only other thing to do is to manually boot it to the Ubuntu system, then:

```
sudo dpkg-reconfigure grub-pc
```
And select the offered drive for the boot loader.

---

