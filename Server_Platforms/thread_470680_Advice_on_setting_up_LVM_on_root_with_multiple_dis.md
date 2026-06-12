---
title: "Advice on setting up LVM on /root with multiple disks"
date: 2007-06-11
forum: Server Platforms
---

### Post by brago on 2007-06-11
Hi there,
I tried to search through the forum without luck for the answer on my question, if this is a double post, please advice me tn where to look :)

I'm setting 7.04 server on my computer and I got the advice to use LVM to not have to bother on what ends up on what disk and be able to easily add disks in the future. The computer is intented as a server and is the former desktop PC now converted to a server.

My idea was basically to not use several partitions for different things on the server, but to only have a SWAP-partition and then all the rest in the same partition, i.e. the "/root". I ran the partition part of the installation but I could only add partitions on one disk to the logical volume. Then I followed a guide on how to format the additional drives to be used with LVM and add that to the logical volume, but I got stuck when I needed to unmount the /root partition to be able to extend the logical volume with the additional drive(s). Is this possible? I tried to boot from the desktop-CD to see if there was a LVM manager on that disk to help me but I was lost there to.

Do you understand my issue?
Is this possible to achieve?
And if so, how should I do it?

Thanks
Stefan

---

### Post by ikonia on 2007-06-11
1.) Home desktop hardware isn't normally suited for LVM due to crappy disk controllers - but you can use them.
2.) your idea of storing everything in /root sort of defeats the object of LVM.
3.) The desktop editition doesn't ship with LVM I believe you have to use the server edition.

---

### Post by keithweddell on 2007-06-11
LVM works perfectly well but you need the Alternate Install CD - at least in releases up to Edgy.  Don't know about Feisty.

Not sure what you are trying to achieve by storing everything under root but you should be able to make multiple disks appear as a single partition if that's what you want.  You might need to think about the consequences if one of those disks crashes.


Keith

---

### Post by brago on 2007-06-11
Hi there, thanks for the input.

The installation is the server edition, only used the desktop live-CD to try if I could play around with the LVM set up. The server is used privatly for a gallery-website, media-file storage mt-daapd server etc. No commercial stuff at all and not that big of a deal. ;)

I have no idea how much disk space is needed for the root stuff, e.g. /etc, /var, /bin /whatever. What I am trying to achieve is that I do not have a "/root" partition that is neither to large nor to litte. And also to not have to bother what disk have space left so where can I store new files. It seemed so much easier to only have one partition and only place the new files under a place in the file system and not care about where /music, /html /video /win_backup etc are. 

Why is it wrong to have only one partition?

I understand there will be consequences if a disk crashes, but there will be consequences if the wrong disk crashes without LVM to. So I try to keep backup of important things anyway.

Thanks
Stefan

---

