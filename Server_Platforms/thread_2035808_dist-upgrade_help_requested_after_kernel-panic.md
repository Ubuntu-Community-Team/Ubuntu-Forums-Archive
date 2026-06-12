---
title: "dist-upgrade help requested after kernel-panic"
date: 2012-07-31
forum: Server Platforms
---

### Post by xkaliburx on 2012-07-31
I have 5 webservers and we just failed our PCI complaince.  The primary culprit was apache which is running the Apache/2.2.14 (Ubuntu) version.  I was looking twords the day's end, saw a post where someone simply added the oneiric disto to the sources.list.  I added that, did an upgrade, 300+ meg came through, but not apache.  So I followed up with an apt-get dist-upgrade which then took some time a few more packages and then done.  I rebooted and was greeted with a kernel panic;
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)

So looking around others have seen this and simply booted off an old kernel.  I did that and things came back and running fine.  But, /etc/issue still shows 10.04LTS which was the existing one.

An apt-get dist-upgrade now shows;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Looking at the souces.list, I still show all the lucid ones also, so I commented out the single  oneiric.

Looking at the grub.cfg I see;

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-41-server' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 572b9a32-f419-40dc-b81b-e7bade8ef4cb
        linux   /vmlinuz-2.6.32-41-server root=/dev/mapper/cfs2-root ro   quiet
}
menuentry 'Ubuntu, with Linux 2.6.32-22-server' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 572b9a32-f419-40dc-b81b-e7bade8ef4cb
        linux   /vmlinuz-2.6.32-22-server root=/dev/mapper/cfs2-root ro   quiet
[COLOR="Lime"]        initrd  /initrd.img-2.6.32-22-server[/COLOR]
}

So the 2 questions that come out of this are;
1.  How do I upgrade the distribution version now?  apt-get update and dist-upgrade show nothing new at all.  Should I change the sources.list all up to the new one.
2.  Can I use the new kernel, just adding the lime initrd that is not listed (is that the reason for the kernel panic)

Thanks

---

