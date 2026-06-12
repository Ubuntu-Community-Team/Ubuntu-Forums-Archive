---
title: "MAAS 1.7 and Windows Server 2012"
date: 2014-12-11
forum: Ubuntu Cloud and Juju
---

### Post by raph4 on 2014-12-11
Hi all,

Since MAAS 1.7, in order to make Windows 2012 available to nodes, you need to create an TAR.GZ custom image, and upload it through API.
I know now what are the API commands in order to upload the image. But one question remains : How to create this Image ?

Until now, I was using this walkthrough : [http://wiki.cloudbase.it/maas#preparing_the_windows_images](http://wiki.cloudbase.it/maas#preparing_the_windows_images) . But now it's no more compatible.

Can you help me please ?

Thanks.

---

### Post by jpe on 2014-12-12
Hi raph

I created the tar.gz image that way:

Part 1 - install and Sysprep Windows:
followed the instructions from 
[https://github.com/cloudbase/windows-openstack-imaging-tools](https://github.com/cloudbase/windows-openstack-imaging-tools) 
-> How to create a Windows template image on KVM


Part 2 - create the tarred image:
on the KVM host (Proxmox VE 3.3) I created the tarred image:

$ modprobe nbd max_part=8
$ qemu-nbd --connect=/dev/nbd0 /var/lib/vz/images/100/vm-100-disk-1.qcow2
$ dd if=/dev/nbd0 of=/var/lib/vz/windows-server-2012-r2.dd
$ qemu-nbd --disconnect /dev/nbd0

$ cd /var/lib/vz/
$ tar cvzf windows-server-2012-r2.tar.gz windows-server-2012-r2.dd

Part 3 - upload to MAAS:
maas root boot-resources create name=windows/win2012r2 title="Windows Server 2012 R2" architecture=amd64/generic filetype=ddtgz [email]content@=/home/ubuntu/windows-server-2012-r2.tar.gz[/email]

The result is a Generated image in MAAS but actually th ePXE boot failes.
Where did you get the information about uploading the image to MAAS?

Regards

---

### Post by raph4 on 2014-12-16
Hi and thanks for your answer.
My goal is to deploy OSes on bare-metal (Client computers and rack servers), not on VMs of any kind. Do I still have to create my image on a KVM (or anything else) host ?

And about where I find this intel, Google is my friend on this one ;-)

---

### Post by raph4 on 2014-12-31
> **jpe said:**
> Hi raph

I created the tar.gz image that way:

Part 1 - install and Sysprep Windows:
followed the instructions from 
[https://github.com/cloudbase/windows-openstack-imaging-tools](https://github.com/cloudbase/windows-openstack-imaging-tools) 
-> How to create a Windows template image on KVM


Part 2 - create the tarred image:
on the KVM host (Proxmox VE 3.3) I created the tarred image:

$ modprobe nbd max_part=8
$ qemu-nbd --connect=/dev/nbd0 /var/lib/vz/images/100/vm-100-disk-1.qcow2
$ dd if=/dev/nbd0 of=/var/lib/vz/windows-server-2012-r2.dd
$ qemu-nbd --disconnect /dev/nbd0

$ cd /var/lib/vz/
$ tar cvzf windows-server-2012-r2.tar.gz windows-server-2012-r2.dd

Part 3 - upload to MAAS:
maas root boot-resources create name=windows/win2012r2 title="Windows Server 2012 R2" architecture=amd64/generic filetype=ddtgz [EMAIL="content@=/home/ubuntu/windows-server-2012-r2.tar.gz"]content@=/home/ubuntu/windows-server-2012-r2.tar.gz[/EMAIL]

The result is a Generated image in MAAS but actually th ePXE boot failes.
Where did you get the information about uploading the image to MAAS?

Regards
Hi and thanks for your Intel.

I've tried exactly what you've said, and now I come with a 5Go image which i try to submit to MAAS.

When i do that, Postgres hangs and gives this message : 

> 
lo_lseek result out of range for large object descriptor 0
current transaction is aborted, commands ignored until end of transation block


It seems to be related to the way that postgres stores "large files".

Can you help me please ?

---

