---
title: "Seeking manual setup share-folder"
date: 2022-07-21
forum: Virtualisation
---

### Post by satimis on 2022-07-21
Hi all,

KVM/QEMU

Where can I find document/manual re setup share-folder between Ubuntu 20.04 host and Windows guest or Linux guest.  The share-folder will be automatically mounted at booting the guest.

Thanks

Regards

---

### Post by #&amp;thj^% on 2022-07-21
The documentation on sharing a KVM host's directory with the KVM guests (Linux) is available here on the virt-manager website. 
Basic setup: [https://www.linux-kvm.org/page/9p_virtio](https://www.linux-kvm.org/page/9p_virtio)
Take your time, more on sharing with samba: [https://web.archive.org/web/20160102195151/http://www.linux-kvm.com/content/tip-how-you-can-share-files-your-linux-host-windows-guest-using-samba](https://web.archive.org/web/20160102195151/http://www.linux-kvm.com/content/tip-how-you-can-share-files-your-linux-host-windows-guest-using-samba).
You will get other offered ideas or suggestions as well.

---

### Post by satimis on 2022-07-22
> **1fallen said:**
> The documentation on sharing a KVM host's directory with the KVM guests (Linux) is available here on the virt-manager website. 
Basic setup: [https://www.linux-kvm.org/page/9p_virtio](https://www.linux-kvm.org/page/9p_virtio)
Take your time, more on sharing with samba: [https://web.archive.org/web/20160102195151/http://www.linux-kvm.com/content/tip-how-you-can-share-files-your-linux-host-windows-guest-using-samba](https://web.archive.org/web/20160102195151/http://www.linux-kvm.com/content/tip-how-you-can-share-files-your-linux-host-windows-guest-using-samba).
You will get other offered ideas or suggestions as well.
Hi,

Thanks for your reply and links.

What I can't resolve is whether I don't need doing anything on the host similar to the host of VirtualBox?  Just setup the share-folder on the guests?

Where is KVM forum for support?

Regards

---

### Post by ajgreeny on 2022-07-22
Not sure there is a devoted forum for KVM/QEMU and I personally don't bother with s sharing folder or anything like that as I simply SSH connect from the guest to host.

I am not sure how that is done from Windows guests as I have given up Windows about 17 years ago, and the few times I have looked at it as a guest in KVM/QEMU it has been simply to do that; look at it rather than actually use it for anything.

SSH between guest and host works exactly as it does between any other two computers, ie, it's quick and simple.

---

### Post by #&amp;thj^% on 2022-07-22
> **ajgreeny said:**
> Not sure there is a devoted forum for KVM/QEMU and I personally don't bother with s sharing folder or anything like that as I simply SSH connect from the guest to host.

I am not sure how that is done from Windows guests as I have given up Windows about 17 years ago, and the few times I have looked at it as a guest in KVM/QEMU it has been simply to do that; look at it rather than actually use it for anything.

SSH between guest and host works exactly as it does between any other two computers, ie, it's quick and simple.

^^^^^^^^^^^^Yep and a big +1

---

### Post by satimis on 2022-07-22
Hi all,

In the past I ran SSH sharing files amongst PCs.  But now Windows guest and Ubuntu host are in the same PC.

On VirtualBox Virt2 on Windows VM can retrieve files from Linux hosts with Drag&Drop, but not the other way round.  I don't know whether it works on KVM?

Also I'm searching for another solution additional to SSH.  Windows guest and Linux host are in the same PC although we can regards them as 2 PCs  

Regards

---

### Post by ajgreeny on 2022-07-24
Whether different machines or the same machine on the same LAN makes no difference when using SSH; you can connect just as easily from guest to host.

I'm sure it must be possible to connect in the other direction but as I always use the default NAT networking on my guests I have never bothered to figure out how, or even if, it can be done so easily.

---

