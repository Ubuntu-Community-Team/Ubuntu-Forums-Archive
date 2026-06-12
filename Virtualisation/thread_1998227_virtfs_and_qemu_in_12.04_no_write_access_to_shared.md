---
title: "virtfs and qemu in 12.04: no write access to shared folder"
date: 2012-06-06
forum: Virtualisation
---

### Post by wiggykvm on 2012-06-06
Hi,

I'm struggling with shared folders between a 64bit "Precise"-host and a 64bit "Precise"-VM under qemu-kvm. I've followed the usual guides, managed the usual pitfalls (install linux-image-extra-virtual so I get all the 9p kernel modules, reconfigure apparmor so guest access is allowed and so on) and get to the point where I can mount a shared folder inside the guest and read all files on it. The only problem is writing, meaning I can't create new files or change existing files inside the guest (works fine on the host). All I get is "permission denied", but neither on the host nor on the guest are there any useful messages in the log files explaining where the problem is. Changing file and folder permissions does not help, either.

After a while of googeling, I found this:
[https://bugzilla.redhat.com/show_bug.cgi?id=819594](https://bugzilla.redhat.com/show_bug.cgi?id=819594)

This is for RedHat, but describes exactly the problem I am having. Reading that post, this seems like a bug, but maybe there's a workaround in Ubuntu? Or am I doing something wrong? In the post it is mentioned that the command line argument security_model=passthrough for KVM should help, but looking at the libvirtd-logfiles, that is already there in my case and does not help.

More details on my setup:
part of the XML definition of the KVM:
```

<filesystem type='mount' accessmode='passthrough'> 
  <source dir='/shared'/> 
  <target dir='shared'/>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
</filesystem>

```I've tried "squash" as accessmode, but that didn't help.

Apparmor on the host is disabled for libvirtd by doing:
```
ln -s /etc/apparmor.d/usr.sbin.libvirtd /etc/apparmor.d/disable/
```The share is mounted in the guest by doing this:
```
mount -t 9p -otrans=virtio,version=9p2000.L shared mount-destination
```Permissions for the shared folder on the host were set to 777, bt that also did not help.

Any ideas?

Best regards,
Wiggy

---

### Post by dalvlexa on 2012-08-27
Hei!
Same thing here, cannot write to shared folder from guest OS - permission denied:
Ubuntu Precise x64 host, Ubuntu Precise x64 guest
Added filesystem with default parameters in virt-manager (and tried every other parameter possibility in the XML)
Mounted with mount -t 9p -otrans=virtio,rw,sync,version=9p2000.L,msize=262144 syspool_fs /mnt/syspool_fs
I have no idea what option msize does, except that it does improve performance when copying from the shared folder in the guest OS. Tried with or without this option, no changes.
Changed permissions to host to 777 nobody:nogroup, that didn't help.

Edit: also apparmor is disabled and removed all together.

Ideas anybody?

Thank you!

---

### Post by bricet on 2012-10-08
I have the same problem on my Ubuntu 12.04 desktop. Any way to solve this write issue on the filesystem, since August ?


Edit : actually, it seems I have finally it working using (with virt-manager, too lazy to see what it corresponds to) Mapped/Path/Default settings when creating the filesystem virtual hardware ...

---

