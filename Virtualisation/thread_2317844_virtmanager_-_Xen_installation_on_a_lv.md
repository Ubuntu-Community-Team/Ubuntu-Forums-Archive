---
title: "virtmanager - Xen installation on a lv"
date: 2016-03-20
forum: Virtualisation
---

### Post by warhammer73 on 2016-03-20
Hello,

in the past I created xen-domus via sen-tools like these:
[FONT=Helvetica]xen-create-image --hostname file_srv --lvm=server_vm_vg   --size=10GB --fs=ext3 --swap=512MB --memory=256MB --ip=192.168.2.241   --gateway==192.168.2.1 --netmask=255.255.255.0 --install-method=debootstrap --force --role=udev
-> After that I have an virtual machine with the filesystem in server_vm_vg, this command creates automatically an lv.

I didn't find a way to use an "raw" lv as storage for an xen vm.

Any ideas?

Thanks![/FONT]

---

### Post by MAFoElffen on 2016-03-21
Quoted from [Xen-Tools.org]("http://xen-tools.org/software/xen-tools/examples.html"):
> 
[SIZE=4]_[COLOR=#6E6E6E][FONT=trebuchet ms]**Loopback Images**[/FONT][/COLOR]_[/SIZE]
[COLOR=#6E6E6E][FONT=trebuchet ms]Using loopback images is very straightfoward, all you need to do to prepare is have a directory within which your new Xen guests will be located. This directory should be specified upon the commandline when invoking xen-create-image.
Specifying the directory upon the command line would look like this:
```

xen-create-image --hostname=test.my.flat \
  --ip=192.168.1.1 \
  --dir=/home/xen \
  --dist=sarge \

```
(**Note:** we didn't specify the installation method, or the Debian mirror to use here - we assume those are specified in the configuration file of/etc/xen-tools/xen-tools.conf.)
Once this command has finished you'll be left with the following layout:
```

/home/xen/
`-- domains
    `-- test.my.flat
    |-- disk.img
    `-- swap.img

2 directories, 2 files

```
Here you can see that there is a new sub-directory created calledtest.my.flat, which was the hostname of the new instance we created, and inside that we have two loopback images.
If you're creating several loopback domains you will soon exhaust the default number of loopback devices. [Increase the number of loop devices for Xen]("http://xen-tools.org/software/xen-tools/faq.html#5").
[/FONT][/COLOR]
But that is answering your post content, which uses the xen-tools toolstack... 

If I went by your thread title, which refers to virt-manager, then via the create new, you could create an image and it would default to /var/lib/libvirt/images, via using the libvirt toolstack. The libvirt toolstack does not create to lv.

---

### Post by warhammer73 on 2016-03-21
So it's not possible to use an LV instead of an image with virtmanager?
Thats crap. :(

---

### Post by MAFoElffen on 2016-03-23
Sort-of a yes and a no at the same time...

It's is sort of a not-pure work-around kind of affair, in the sense that if you want to use an lv for Xen DomU, then you can only create it the usual CLI method of creating it with lvcreate. Then in virt-manager, when you create new, then when you get to storage, you choose "Select managed or other existing storage." Then enter the path to the LVM volume to the text field or choose browser path to the LV that you set up earlier. Then you continue to select your other options within virt-manager. You can change your VM settings from within virt-manager to change or tweak it.

The "no" part of that, is you cannot create an LV storage volume from within virt-manager. You can create image files of various formats (raw, etc.), which in Xen doc's is referred to as using a loopback block-device file system.The only formay I saw supported was raw format with an .img extension. But... if you read carefully, if also has support for blktap: AIO, qcow and qcow2 formats. 

Those loopback and blktap formats are very portable, but not as robust nor as flexible as using LV's. Still, I like using virt-manager for management. Bteween CLI tools and virt-manager, there are a lot of things you can do to mold the environment of a guest.

---

