---
title: "install of Guest Additions not working"
date: 2014-11-12
forum: Virtualisation
---

### Post by a-you on 2014-11-12
I have virtualbox 4.3.10_Ubuntu r93012 and have a virtual machine from bitnami with a WordPress stack. But I don't know how to copy/move files form the host (ubuntu studio 14.4 64 bit) to the vm (I want to try a WordPress theme that I downloaded). Apparently in order to enable any sort of sharing between the machines I need Guest Additions installed on the vm. I've tried following the bitnami instructions, did get the Guest Additions .iso to mount, though not from the vm's "Devices" menu, rather I could mount it with (in the vm, mounting read-only)

```
sudo mount /dev/cdrom /mnt/cdrom
```

But when I try to run

```
sudo sh ./VBoxLinuxAdditions.run --nox11
```

I get an error that the kernel headers can't be located. In fact it reports that it can't locate dkml nor build-essential. I do have those installed, though on the host---that is, on my computer. I even installed the headers on my computer, with synaptic, though that seemed irrelevant to me; and it didn't help.

To me this seems like a catch-22: how am I supposed to get those needed files installed on the virtual machine if I have no way to transfer anything to it??

Or am I supposed to be able to access the internet from within the virtual machine? Because that doesn't seem to be possible either, else I just don't know how to do it.

If anybody can give any pointers I'd much appreciate it. I've searched far and wide, but every tip just says to run that shell script and presto, it's done. Thanks much in advance!!!

I should add that virtualbox and the guest additions package I installed from the ubuntu repositories.

---

### Post by a-you on 2014-11-12
Whew, it's working. Funny thing too: I had opened ports in UFW according to a tutorial somewhere (don't know now though) that would, I thought, allow the virtual machine to have total access/be accessed, but simply turning off the firewall altogether solved it.

---

