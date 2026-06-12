---
title: "VirtualBox Crashes When Attaching a CD/DVD"
date: 2017-04-21
forum: Virtualisation
---

### Post by Eldon_McGuinness on 2017-04-21
I'm having an issue with VirtualBox with 17.04. I did not have this issue with 16.10. When ever I try to attach an ISO of a CD/DVD the VirtualBox application immediately closes. I was able to get around this by using the cli tool VBoxManage. In my case I was trying to setup a simple Windows 7 x64 VM.

```
VBoxManage storageattach "vmname" --storagectl SATA --port 1 --device 0 --type dvddrive --medium "/mnt/drive/some.iso"
```

---

### Post by martins1966 on 2017-04-26
I have the same problem. Using the GUI interface, virtualbox immediately closes when I' click on the option to select the folder where the ISO is located.

Using UbuntuGnome 17.04 now. I had no problems while using 16.04 with Unity.

---

### Post by howefield on 2017-04-26
Thread moved to the "*Virtualisation*" forum.

---

