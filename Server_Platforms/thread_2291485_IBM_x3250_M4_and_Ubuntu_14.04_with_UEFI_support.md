---
title: "IBM x3250 M4 and Ubuntu 14.04 with UEFI support"
date: 2015-08-20
forum: Server Platforms
---

### Post by Drenriza on 2015-08-20
I am trying to install Bbuntu 14.04 lts with UEFI support on a IBM x3250 M4 server.

The installation process goes just fine, and Ubuntu creates a UEFI partition. But when i then reboot the machine and the IBM boot manager tries to boot Ubuntu,
it fails. Just saying "Boot ubuntu, failed." Not super informative.

The path the IBM boot manager looks at is
```
HD(1,GPT,9899318E-BD86-4-581-B851-6DCC82F5AF92,0x800,0x100000)/\EFI\ubuntu\shimx64.efi
```

Under the partition process i selected **use entire disk** without lvm support.

Anyone who has an idea for what i can do? Do i need to download a special UEFI Ubuntu .iso that isint the standard .iso file or something in that regard?

I have looked at just disabling UEFI for the IBM x3250 M4 server, but i cant see in system setup that i can do that.

I have also tried Ubuntu 12.04 LTS as seen here
[http://www.ubuntu.com/certification/hardware/201203-10653/](http://www.ubuntu.com/certification/hardware/201203-10653/)

same problem as 14.04 LTS

All ideas / feedback are most welcome.

Thanks in advance.

---

