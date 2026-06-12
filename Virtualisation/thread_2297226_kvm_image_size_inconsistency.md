---
title: "kvm image size inconsistency"
date: 2015-10-01
forum: Virtualisation
---

### Post by jfishman2 on 2015-10-01
I have looked all over the internet and this forum but I can not find the answer to this question.

Why does the .img file and guest os report a huge difference in size?


I have installed a fresh version of KVM on ubuntu-14.04.3-server-amd64.iso. The method I used to install the KVM was selecting it as an option during the server install process. Then using virt-manager, I created a VM with an image size of 15GB for the guest OS. The guest OS is also ubuntu-14.04.3-server-amd64.iso.
 
If I go into the directory where the .img is created and issue the following command:ls -l -h  

It shows the following output -rw------- 1 libvirt-qemu kvm   15G Oct  1 17:59 test.img 

During the install process on the guest, the disk size also reflects the fact that it is a 15GB disk. However, after the guest has finished installing, it reports a size of 6.65 GB (df -h):confused:. During the guest install I have tried selecting the option of "use entire disk" without LVM and with LVM.

If I bump the size of the .img up to 50GB then I only lose 3GB of disk in the guest os and it reports a size of 47GB

I need to have a reasonable sized VM of around 15 GB and I do not want to burn up a massive amount of HD by having to create 50 GB .img files.

How do I make the guest OS show an image size of 15 GB to reflect the same size as the .img file?

---

### Post by TheFu on 2015-10-02
Please post the copy/paste output of the commands you ran. We are familar with that and it removes any misinterpretations. Also, please use "code tags" so things line up.

From inside the VM:
```
lvs
df -i
df -h
swapon -s
free -m
```

From outside the VM:
```
sudo ls -l /var/lib/libvirt/images/
qemu-img info /path/to/image/file.img
```

It is possible that a swap partition has been created and may have been created inside the same "image" file. Also, you didn't say the format of the image file - so will use sparse allocations which grow and shrink as necessary.

For example:
```
# qemu-img info cent18.qcow2
image: cent18.qcow2
file format: qcow2
virtual size: 9.0G (9663676416 bytes)
disk size: 1.3G
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: false
```
and
```
# qemu-img info ubudesk.img 
image: ubudesk.img
file format: raw
virtual size: 14G (15401484288 bytes)
disk size: 14G
```

---

