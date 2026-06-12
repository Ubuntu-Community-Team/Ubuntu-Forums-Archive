---
title: "Macvtap broken after power shortage"
date: 2015-07-30
forum: Virtualisation
---

### Post by borre2 on 2015-07-30
I have an Ubuntu server hosting VM (also Ubuntu server) with kvm. Their networking was configured to use bridged mode and everything worked fine until accidental power shortage. Host machine still works fine with networking and all but VM won't start. Trying to start the virtual machine gives me following error.


```
error: Failed to start domain mymachine
error: error creating macvtap type of interface attach to eth0: Device or resource busy

```

Error comes immediately (with virt-manager or virsh) and that makes me think that maybe macvtap -driver is somehow corrupted by the power shortage. I really hope that my VM image is not corrupted - that would be the worst scenario. But since error comes so fast I've figured that the problem is in the host. I don't think there is anything wrong with the network card since host works - I can SSH into it, ping works etc. 


All the configuration that I did to /etc/network/interfaces is still same as before - when everything worked. I've tried ip link thing like this (don't remember where I picked it). 

```
sudo ip link add link eth0 name macvtap0 type macvtap

```
Running the previous command gives me this error. 

```
RTNETLINK answers: Device or resource busy
```


I don't fully understand (as you've probably figured out by now :-)) the concepts of networking in kvm environment and since I haven't found anything useful after intensive googling, I'm completely lost. Is macvtap is broken somehow? If so, how can I fix it?

---

### Post by dik232 on 2015-10-29
Did you figure this out?

I've just had a power outage (whole street) and am seeing the same thing. Not just with VMs that were running but with VMs that haven't run for weeks

---

### Post by dik232 on 2015-10-31
Problem solved - typo in my /etc/network/interfaces

Is there anyway to move this post down to the bottom where no one will read it? :oops:

---

