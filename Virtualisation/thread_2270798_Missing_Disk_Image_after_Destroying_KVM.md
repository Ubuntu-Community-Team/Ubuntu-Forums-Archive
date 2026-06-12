---
title: "Missing Disk Image after Destroying KVM"
date: 2015-03-25
forum: Virtualisation
---

### Post by motobeats on 2015-03-25
[COLOR=#333333][FONT=UbuntuRegular]I am using virsh to manage my KVMs on Ubuntu 14.04. I store my disk path targets (.IMG files) on an LV and mount it manually.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I, of course, forgot to mount this LV after a restart but virsh was still able to start my KVM. Surprising, but ok.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]While the KVM was running I mounted the LV. Everything was still ok. Then when I destroyed the KVM my disk image disappeared.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]How did my disk path target (disk image) disappear? Any way to recover it?[/FONT][/COLOR]

---

### Post by Doug S on 2015-03-29
> **motobeats said:**
> [COLOR=#333333][FONT=UbuntuRegular]I, of course, forgot to mount this LV after a restart but virsh was still able to start my KVM. Surprising, but ok.[/FONT][/COLOR]That is odd. I always forget to mount the drive where I keep my VM's, but when I try to start with "virsh start" I get an error.```
doug@s15:~/temp$ virsh start desk_dev
error: Failed to start domain desk_dev
error: Failed to open file '/media/newhd/desk_dev.img': No such file or directory
```> **motobeats said:**
> [COLOR=#333333][FONT=UbuntuRegular]While the KVM was running I mounted the LV. Everything was still ok. Then when I destroyed the KVM my disk image disappeared.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]How did my disk path target (disk image) disappear? Any way to recover it?[/FONT][/COLOR]I don't know how it disappeared or how the VM started in the first place.

---

### Post by motobeats on 2015-04-09
Doug, 

I have gotten more comfortable with the KVM process and working with file systems (both new to me) and looking back at this, I don't know how much you can trust what I reported (I bet the post time was very early in the morning).

In tuning my KVM creation process I was creating a lot of machines and so I think I might have done some duplication which when combined with the mount mistake really confused me. Here is my best guess at a revision of the events.

1. Forgot to mount the dev holding my other .img files
2. Created a KVM
3. Realized my mistake and mounted the forgotten dev to the same folder (thus hiding the currently running img).
4. Destroyed the KVM
5. Looked for the img in the now hidden (by the mount) folder.

In short, user error.

---

