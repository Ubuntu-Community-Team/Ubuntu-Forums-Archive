---
title: "Question: How can I add physical disks to KVM guest VMs?"
date: 2013-11-23
forum: Virtualisation
---

### Post by iamtim on 2013-11-23
I have read varying advice on whether to use block devices, how to mount the disks in the host. Some say I can do it in virt-manager, others say I have to edit XML. I'm baffled.

What I want: I have a VM running on my host, planning to turn it into DMZ ftp server for shipping and sharing files. Want data on separate 1T HDD, to physically separate it from host HDD (a 128GB SSD, which doesn't have any real space anyway.)

Running Ubuntu 13.10 64-bit server host and guests with remote virt-manager via SSH from Mint laptop.

Tips? Ideas? URLs for good advice?

---

### Post by KillerKelvUK on 2013-11-26
So I run my host server from a mSATA SSD and then have a guest which has exclusive block devices assigned that assembles my raid 10 from these blocks and servers out a file share over samba.  I use Virt-Manager but don't believe there is a way to accomplish this level of guest specification in that tool.  I used the CLI and virsh edit and followed this little nugget...[http://ronaldevers.nl/2012/10/14/adding-a-physical-disk-kvm-libvirt.html](http://ronaldevers.nl/2012/10/14/adding-a-physical-disk-kvm-libvirt.html).  Interesting however once you've done this Virt-Manager reflects the new configuration in it GUI...

---

### Post by iamtim on 2013-11-27
Nice. Great advice. I'll try this over the holiday weekend.

---

