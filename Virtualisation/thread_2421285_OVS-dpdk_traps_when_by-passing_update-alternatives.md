---
title: "OVS-dpdk traps when by-passing update-alternatives"
date: 2019-06-19
forum: Virtualisation
---

### Post by georg-kunz on 2019-06-19
Hi all,

I am running OVS with DPDK in a Docker container - quite successfully actually. Until now, I have been using two separate images: one with DPDK and one without DPDK. Now, for the sake of simplicity, I'd like to just maintain a single image which has both the openvswitch-switch and openvswitch-switch-dpdk packages installed. Typically, this is not a problem and the specific version of OVS can be selected by means of update-alternatives.

However, I cannot use update-alternatives in the container because the container's filesystem is read only. So, my idea was to call the target binary to which the ovs-vswitchd symlink points directly: either 

/usr/lib/openvswitch-switch/ovs-vswitchd
or
/usr/lib/openvswitch-switch-dpdk/ovs-vswitchd-dpdk

**Problem**: Something seems to go wrong as the dpdk binary starts up nicely, however, it traps and crashed after about 30s. In the kernel log of the host machine, I see such entries:

[FONT=courier new][22219.308349] traps: revalidator82[3578] general protection ip:7f2907df58f0 sp:7f28e67fb8a0 error:0 in libc-2.27.so[7f2907db5000+1e7000][/FONT]

Please note that this does **not **happen, when using a container image in which the dpdk binary was selected using update-alternatives beforehand.

**Question**: For some reason it seems not to be possible to by-pass the update-alternatives mechanism by calling the target binary directly. Can somebody shed some light on why this is the case? Any idea show to solve this?

Thank you.
Georg

---

