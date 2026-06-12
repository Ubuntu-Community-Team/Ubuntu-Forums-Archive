---
title: "PCI-E passthrough: pci-stub/bind says no such device"
date: 2014-11-23
forum: Virtualisation
---

### Post by rms2 on 2014-11-23
so im trying to bind my second radeon card to pci-stub, as per instructions for setting up GPU passthrough in [here]("http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM"), but once i get to binding the card to pci-stub, it tells me it isnt there. this is what im putting in, and what i get out:
> 
echo "1002 5a16" > /sys/bus/pci/drivers/pci-stub/new_id
echo "0000:02:00.0" > "/sys/bus/pci/drivers/radeon/unbind"
echo "0000:02:00.0" > "/sys/bus/pci/drivers/pci-stub/bind"
bash: echo: write error: No such device


i modified some of the path as some of the ones in the documentation dont seem to exist on my system, however according to my file manager /sys/bus/pci/drivers/pci-stub/bind definately exists. im trying to give my windows vm a HD6450 so i can actually use it for things, but its proving difficult thus far.

---

### Post by rms2 on 2014-12-02
damn, over a week and no replies?

---

### Post by froyomuffin on 2014-12-13
Two actually. :P

I just tried it manually and the binding worked for me.

I don't think the error you're having is related to whether /sys/bus/pci/drivers/pci-stub/bind exists but rather if the device you're trying to bind/unbind is available for that action. I tried doing the unbind step twice and that message popped up the second time through.

Now, I'm going to guess that the issue you're having is that the device in question is bound to a different driver than radeon when you run those commands. Can you confirm which driver it is bound to via lspci -vnn?

---

