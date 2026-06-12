---
title: "[KVM] PCI GPUs have the same device ids. Why? How to change the ids?"
date: 2015-08-29
forum: Virtualisation
---

### Post by manvir2 on 2015-08-29
I've got two R9 280's installed in my system. In Ubuntu when I run ```
lspci -nn
``` both the cards have the same device id.


Example Output:
```
01:00.0 Example GPU 1 [8080:aa68]
04:00.0 Example GPU 2 [8080:aa68]

```
Notice the device ids "8080:aa69" are the same. So my question is why are the ids the same? I'm trying to pass through one of the cards to kvm but both get passed because the ids are the same. So what could I do to solve this?
I've tried ```
setpci
``` but it doesn't change the id. I've also tried ```
echo "8080 aa68" > /sys/bus/pci/drivers/radeon/new_id"
``` but then I get a error ```
new_id file exists
``` if there is no way to the the device id then how can I only passe one card to kvm?

Update: If I do this echo 0000:04:00.0 > /sys/bus/pci/devices/0000:04:00.0/driver/unbind then my system freezes

---

### Post by KillerKelvUK on 2015-08-29
Never had the issue so have no first hand experience resolving but the passthru guru has posted about it on his blog with suggested fixes...

[http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html)

---

