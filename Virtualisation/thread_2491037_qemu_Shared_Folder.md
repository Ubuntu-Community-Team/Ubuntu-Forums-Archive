---
title: "qemu Shared Folder"
date: 2023-09-23
forum: Virtualisation
---

### Post by Quarkrad on 2023-09-23
I am trying to share a folder on my ubuntu 22.04 host and a folder on my ubuntu 22.04 qemu vm.  On my host I have created /home/dad/vmhost and on the vm created /home/dad/hostshare

I have been following various gui (youtube) and text instructions.  I get to the point on the vm where I type:

**sudo mount -t 9p -o trans=virtio /sharepoint hostshare**

when I enter that command I get:

**mount: /home/dad/hostshare: bad option; for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program.**

Any advice appreciated.

---

### Post by Dennis N on 2023-09-23
No advice on mounting, but you could just connect to the host with ssh, access a folder there, and copy or past files. That's how I share files between a vm and host.

---

### Post by ajgreeny on 2023-09-23
Here's how I've been doing it for some time now.
[https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)

You need to do all the setting up as shown in that webpage and it should then work faultlessly for you as it does for me.
I haven't bothered with mounting the folder in the VM's /etc/fstab file but simply mount it when I need it then unmount when I've finished using it.

---

### Post by #&amp;thj^% on 2023-09-23
> **ajgreeny said:**
> 
I haven't bothered with mounting the folder in the VM's /etc/fstab file but simply mount it when I need it then unmount when I've finished using it.

+1
easy peasy, and goes with my K.I.S.S habits.

---

### Post by MAFoElffen on 2023-09-24
-1 :
Why?

virtiofs is still broken: [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/2033957](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/2033957)

They came up with a patch, tested, works, and built the fixed package... but it is still in Proposed. So, at least for "now", you won't get it unless you enable the Proposed Repo.

I do NFS network shares between my hosts and VM's.

---

### Post by ajgreeny on 2023-09-24
My version of virtiofs is obviously not broken, and I can confirm that I am using all the packages from the default jammy repos with no proposed repos enabled. I wonder what I am doing differently that gives me this success where others are having problems.

I set everything up exactly as shown in that link in my last post #3 and it has never let me down so far.

---

### Post by tea for one on 2023-09-24
+1 with ajgreeny and this tutorial [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/)

Ubuntu 22.04 host
Ubuntu 23.04 guest

Using [COLOR="#0000FF"]qemu-system-x86:amd64 1:6.2+dfsg-2ubuntu6.12 1:6.2+dfsg-2ubuntu6.13[/COLOR]

However, the bug report is dated 02 September 2023 and the package above was upgraded on my system on 06 September 2023

I first tried this sharing method a few months ago and never experienced any problem

---

### Post by #&amp;thj^% on 2023-09-24
Yep no problems here as well, even with:
```
apt policy virtiofsd
virtiofsd:
  Installed: 1.7.0-3
  Candidate: 1.7.0-3
  Version table:
 *** 1.7.0-3 500
        500 http://archive.ubuntu.com/ubuntu mantic/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ajgreeny on 2023-11-17
I am still mounting the shared virtiofs I have setup in my Ubuntu VMs using a manual mount command ```
sudo mount -t virtiofs Host /Host
``` with /Host as the mountpoint and my shared virtiofs named Host.
I said in my previous post #3 that I have not bothered using fstab to mount the virtiofs but I have decided to now try doing so.
Can anyone tell me the required line in /etc/fstab to do this as all I've tried has failed in spite of searching everywhere I can think of.

---

### Post by ajgreeny on 2024-04-03
Just in case anyone sees my query about using fstab in post #9 and prefers to add the mount at boot, here is the needed entry for /etc/fstab
```
Host /Host virtiofs defaults 0 0
```
this again with my shared virtiofs named Host and /Host as the mountpoint of my shared virtiofs.

---

