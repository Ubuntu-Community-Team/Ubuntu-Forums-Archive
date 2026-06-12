---
title: "[SOLVED] KVM VM &amp;quot;could not open disk image&amp;quot;"
date: 2008-04-13
forum: Virtualisation
---

### Post by kg4ozx on 2008-04-13
I am using Ubuntu 8.04.

I have been using the documentation at the link below:

[https://help.ubuntu.com/community/KVM?highlight=(KVM)#head-753d9db1a09c7f2e984566e0e53ac6e1f619216b](https://help.ubuntu.com/community/KVM?highlight=(KVM)#head-753d9db1a09c7f2e984566e0e53ac6e1f619216b)

I haven't gotten very far, though. When I issue the command :
```

 kvm -no-acpi -m 384 -cdrom /winxpsp2.iso -boot d -hda windows.img

```

I get the error message *"qemu: could not open disk image windows.img"*

I have tried creating other guests with no success. The windows.img file is located in my home folder. 

I'm new to virtualization, so I appreciate the help!

Thanks for your help!

---

### Post by chewearn on 2008-04-14
From your command:
> kvm -no-acpi -m 384 -cdrom /winxpsp2.iso -boot d **-hda **windows.imgDelete the item in bold.
> kvm -no-acpi -m 384 -cdrom /winxpsp2.iso -boot d windows.img

---

### Post by kg4ozx on 2008-04-14
Thanks for the reply. Unfortunately this gave the same result. 

I've checked permissions, I just can't seem to figure out why it won't open windows.img

Thanks!

---

### Post by ericy on 2008-04-14
Copy & paste the following line to your console and see what happens:

ls windows.img

----
If it shows "No such file or directory", then it means you have a spelling problem with your "windows.img" (Maybe you used a capital "W")

---

### Post by kg4ozx on 2008-04-14
Actually I figured it out. Turns out that the syntax from the how-to I posted earlier didn't work for me. (Of course, YMMV)

I used the syntax from [http://maconstuff.blogspot.com/2006_06_01_archive.html](http://maconstuff.blogspot.com/2006_06_01_archive.html)

```
qemu -boot d -hda windows.img -cdrom /dev/cdrom -m 256 -localtime
```

This worked for the install, but was slow. I launch my VM using 

```
kvm -boot c -hda windows.img -m 256 -localtime
```

Now it works like a charm. I will mark this as solved!

Thanks for all the suggestions!

---

### Post by jeantasse on 2008-04-25
Ubuntu 8.04 By the way, i tried that, it was to long so i quit, but right after trying with qemu i did it again with kvm and it worked.

1st: qemu -m 256 -cdrom /dev/cdrom -boot d server1.img ....was too long but then...

2: kvm -m 256 -cdrom /dev/cdrom -boot d server1.img .... and it booted without the error message

---

### Post by kg4ozx on 2008-04-25
Can you elaborate on the "error message" or what is "too long"? It could help someone down the road.

Thanks!

---

### Post by jwatte on 2009-06-11
I think by "too long" he meant "too slow."

Btw, I still have this problem. The image is right there, in the directory. It still won't boot. I created it with qemu-img -f qcow2. I could boot to install Windows. Now, when I try to re-start it, it doesn't work:

[FONT="Courier New"]# **ls -l wxp_build.img**
-rw-r--r-- 1 root root 1338777653 2009-06-11 11:43 wxp_build.img
# **qemu-img info wxp_build.img**
image: wxp_build.img
file format: qcow2
virtual size: 20G (21474836480 bytes)
disk size: 1.2G
cluster_size: 4096
Snapshot list:
ID        TAG                 VM SIZE                DATE       VM CLOCK
1         freshboot.vm           111M 2009-06-11 11:41:47   01:06:21.963
# **kvm -m 1536M -hda wxp_build.img -usb -usbdevice tablet -vnc :1 -net nic,model=virtio -net user**
qemu: could not open disk image wxp_build.img
#[/FONT]

---

### Post by jwatte on 2009-06-11
Soo... I solved it. It seemed to have something to do with the snapshot in the image.
I actually tried loading it with kvm -loadvm freshboot.vm wxp_build.img, but that still didn't work.
When I stripped the snapshot by using "**qemu-img convert**" with appropriate options, it would then boot from the newly created (converted) image.

---

