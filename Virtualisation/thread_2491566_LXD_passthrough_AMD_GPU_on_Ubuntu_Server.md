---
title: "LXD passthrough AMD GPU on Ubuntu Server"
date: 2023-10-13
forum: Virtualisation
---

### Post by carljoans on 2023-10-13
I have seen only posts all over the web about using an Nvidia card (even Intel) with an LXD VM, but nothing about using an AMD card on a headless host.
I'm using the LXD Web UI:
[LIST]
[*]Allow GPU devices in LXD (Under Configuration > Device usage) 
[*]I create a simple VM with desktop, no special settings. 
[*]Starts fine 
[*]I add this to the instance config under devices: 
[/LIST]
[HTML]gpu:
  type: gpu
  pci: '0000:09:00.0'
[/HTML]

The VM just fails to start after adding the GPU config. Any help/suggestions is welcome.

---

### Post by MAFoElffen on 2023-10-13
On the Host:

[LIST=1]
[*]Do you have another GPU to use on your host, beside the one you are trying to pass through??? (very important, unless the host is headless) 
[*]Did you turn on iommu to create iommu groups? 
[*]Did you blacklist the amdgpu driver from being loaded so that it wasn't claimed by the host? 
[/LIST]
If, so, show me the verification of, via the output, posted within CODE Tags... ("Show me the data")

---

### Post by carljoans on 2023-10-15
Thanks. I have done none of those things.
1. The host is headless.
2. Will look this up and do that. 
3. Will also look this up and do that.
I actually saw some of these things while searching for an answer, but all the posts seemed outdated. Hopefully I can find something recent that I can successfully follow.

---

### Post by carljoans on 2023-10-15
Problem solved.
1 and 2 wasn't an issue for me. I found an answer to 3 here even though this was dealing with an Nvidia gpu:
[https://discuss.linuxcontainers.org/t/gpu-passthrough-failed-for-lxc-lxd-virtual-machine/13105/5](https://discuss.linuxcontainers.org/t/gpu-passthrough-failed-for-lxc-lxd-virtual-machine/13105/5)

```

sudo nano /etc/modprobe.d
# add these lines to the file:
blacklist amdgpu
blacklist radeon
# save
sudo update-initramfs -u
sudo reboot

```

As mentioned before, I've seen the stuff before in searches but just needed some confirmation of the steps I needed to take since LXD and/or the host and/or hardware/bios activation could have taken care of some steps already.
Thanks again.

---

### Post by MAFoElffen on 2023-10-15
LOL. Yes, a lot out there is outdated. You have to look at the dates of when things were written.

If you search on my username here, and IOMMU or passthrough you will find some current posts, which I think the last was on amdgu... within the last month or two. 

I'm currently going round and round with the upstream Intel Support Engineers on the Intel XE drivers being broken for passthroughs. Big crashes on the newer kernels. Ugh.

---

