---
title: "KVM libvirt network creation failure"
date: 2012-04-25
forum: Virtualisation
---

### Post by sean abbott on 2012-04-25
I'm trying to create a KVM virtual machine.  No matter which method I use (virtmanager, virsh) I get the following error: 

error: Failed to start network default
error: cannot disable /proc/sys/net/ipv6/conf/virbr0/accept_ra: No such file or directory

I've looked through the code, and this reaches back to the libvirtmod, where in dtatypes.h it has the following lines:  define VIR_IS_CONNECT(obj)    ((obj) && (obj)->magic==VIR_CONNECT_MAGIC)

And at this point my knowledge of c fails me...I have not idea what that line is doing.  Basically, though, it's checking to see if an ipv6 file exists, and it does not, and it refuses to create the network without it.

I was going to try disabling ipv6, and see if that would prevent libvirt from attempting to create that virbr0 interface in the ipv6 subdirectory of /proc/sys/net (because that directory doesn't exist), but adding the net.ipv6.<can't recall at the moment> to sysctl, but sysctl says it doesn't know what I'm talking about with the option (I triple checked it in the past when I was working on this)

It's failing because /proc/sys/net/ipv6 does not exist. 
1)  Is that standard for ubuntu?
2)  If it is, do I file a bug report with ubuntu or with libvirt?

Or is there anything else I can do to try and solve this?

---

