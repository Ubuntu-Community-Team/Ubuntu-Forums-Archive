---
title: "Cannot successfully install vmware tools"
date: 2017-02-19
forum: Virtualisation
---

### Post by rashhashan on 2017-02-19
I have tried to follow [this]("https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525") guide as well as many others to no avail. There is simply nothing in the cdrom image.. It is empty. I have repaired and reinstalled the VMware tools as well. What am i doing wrong?[IMG]http://imgur.com/a/DHBGs[/IMG]

---

### Post by ODTech on 2017-02-20
> **rashhashan said:**
> I have tried to follow [this]("https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525") guide as well as many others to no avail. There is simply nothing in the cdrom image.. It is empty. I have repaired and reinstalled the VMware tools as well. What am i doing wrong?[IMG]http://imgur.com/a/DHBGs[/IMG]

I had the same issue during my brief experience with VMWare before i switched to kvm.

Download the iso directly from here
[HTML]https://my.vmware.com/web/vmware/details?productId=491&downloadGroup=VMTOOLS1000[/HTML]

I will assume you know your way around fairly well so i'll just write the command to mount the iso image. If you need more help just post back.

```
sudo mount -o loop <iso file name> <mount point>
```

Now it will show up as a cd image an you can just install the appropriate package.

---

### Post by rashhashan on 2017-02-20
> **ODTech said:**
> I had the same issue during my brief experience with VMWare before i switched to kvm.

Download the iso directly from here
[HTML]https://my.vmware.com/web/vmware/details?productId=491&downloadGroup=VMTOOLS1000[/HTML]

I will assume you know your way around fairly well so i'll just write the command to mount the iso image. If you need more help just post back.

```
sudo mount -o loop <iso file name> <mount point>
```

Now it will show up as a cd image an you can just install the appropriate package.

That's the thing, I don't know my way around

---

