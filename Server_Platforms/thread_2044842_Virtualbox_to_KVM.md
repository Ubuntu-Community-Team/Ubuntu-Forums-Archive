---
title: "Virtualbox to KVM"
date: 2012-08-20
forum: Server Platforms
---

### Post by LordVaderXIII on 2012-08-20
Hi There

Im trying to migrate my Server from Virtualbox to KVM I have converted the hdd to raw and now trying to get it to boot with no luck. I constantly get blue screens. 

I have attached some pics of my setup in Virtualbox any help would be appreciated.

Im using this command:

sudo virt-install --connect qemu:///system -n machinename -r 3096 --vnc --import --vcpus=4 --os-type windows --os-variant win2k3 --disk path=/home/user/machinename.img,bus="ide" --arch x86_64

---

