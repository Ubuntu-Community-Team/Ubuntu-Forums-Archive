---
title: "KVM-thin and LVM"
date: 2018-04-13
forum: Virtualisation
---

### Post by kcallis on 2018-04-13
A couple of days ago, I was using Proxmox and for the most part, things were well. After a power outage, I could not reach the interface, and ever after I re-installed proxmox and still no joy. Not a problem, it was just time to go back to my root and so I installed Ubuntu Sever 17.10. At the point I decided that I would replicate the LVM layout from proxmox, and have the following available. There is a root partition which I have allocated 200G (although Proxmox only did 100G), swap was 8G, and then there was the remainder that was called DATA (raw partition) which was the remainder of the drive. So I have been stuck in moving forward since I how how to create the root and swap, but I have no idea how to utilize KVM-Thin to make the DATA so that my images can stored on the DATA partition. 

Also, when I create a image, how do I do I force is over to the raw partition? For that matter, although of topic, it is possible to put containter (lxc) and docker images on the raw partition? Any pointers would be greatly appreciated.

K

---

### Post by TheFu on 2018-04-13
Servers should run LTS releases without a very, very, good reason. Support for 17.10 ends in June, which is pretty soon.  OTOH, if you will be wiping and moving to 18.04 in a few months, then it is probably the best choice. Most server admins need more than 6-9 months of security patch support, so we stick with LTS releases only.

There are multiple types of storage pools available:
[https://libvirt.org/storage.html#StorageBackendLogical](https://libvirt.org/storage.html#StorageBackendLogical) 

[https://ubuntuforums.org/showthread.php?t=2152051](https://ubuntuforums.org/showthread.php?t=2152051) post #5 has steps, but they might not be what you need.

I don't use containers through libvirt and have only played with them, so can't help with that. Sorry.

---

