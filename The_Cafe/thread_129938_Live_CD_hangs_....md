---
title: "Live CD hangs ..."
date: 2006-02-15
forum: The Cafe
---

### Post by najevi on 2006-02-15
I've got myself into trouble here. Ubuntu breezy installed on HDD but no longer able to boot succesfully into it.

I was saving various details about a problem to a text file in $HOME and that is the ONLY file that I am interested in recovering from the HDD before a clean reinstal of ubuntu - assuming a reinstall is the only remedy for my current woes!

So I tried to use the LiveCD to at least get to a desktop annd open a Terminal window. I imagine that I might be able to find and mount the partition that is on the HDD. Trouble is Live CD hangs at either "User Setup 56%" or "Display Setup 65%"

Right now I have boot from a CDROM to DSL (Damn Small Linux) and so I have a desktop and terminal windows to work with.

If anyone online right now can PM me with advice as to how to find and mount the HDD partitions I'd certainly appreciate it. I don't have an Instant Messenger application under DSL so would have to make do with forum PM-ing.

Regards,

---

### Post by mstlyevil on 2006-02-15
[QUOTE=najevi]I've got myself into trouble here. Ubuntu breezy installed on HDD but no longer able to boot succesfully into it.

I was saving various details about a problem to a text file in $HOME and that is the ONLY file that I am interested in recovering from the HDD before a clean reinstal of ubuntu - assuming a reinstall is the only remedy for my current woes!

So I tried to use the LiveCD to at least get to a desktop annd open a Terminal window. I imagine that I might be able to find and mount the partition that is on the HDD. Trouble is Live CD hangs at either "User Setup 56%" or "Display Setup 65%"

Right now I have boot from a CDROM to DSL (Damn Small Linux) and so I have a desktop and terminal windows to work with.

If anyone online right now can PM me with advice as to how to find and mount the HDD partitions I'd certainly appreciate it. I don't have an Instant Messenger application under DSL so would have to make do with forum PM-ing.

Regards,[/QUOTE]

It could be a corrupted live cd or you do not have enough RAM depending on how much RAM you have installed.

---

### Post by najevi on 2006-02-15
[QUOTE=mstlyevil]It could be a corrupted live cd or you do not have enough RAM depending on how much RAM you have installed.[/QUOTE]

Yes, RAM could be it - I have 256+128=380MB

Either way I have a unix OS running now (DSL) and so any advice as to how i can find, mount then browse the partitions on my HDD would be appreciated.

---

### Post by codejunkie on 2006-02-15
[QUOTE=najevi]Yes, RAM could be it - I have 256+128=380MB

Either way I have a unix OS running now (DSL) and so any advice as to how i can find, mount then browse the partitions on my HDD would be appreciated.[/QUOTE]
su to root run ```
fdisk -l
``` find your ubuntu partition info there for example mine is **/dev/hdb2** then ```
mkdir /mnt/ubuntu
```
and last ```
mount /dev/hdb2 /mnt/ubuntu
```

---

### Post by najevi on 2006-02-15
Thanks for the instructions - I could not guess the su password to succefsully follow them.

What I did remember is that just before ubuntu boot I can hit ESC to bring up GRUB and from that menu select a recovery boot mode. After that all I needed to do was exit the # prompt and the OS booted as usual.

Have saved my debug notes and now plan to back up /home before restarting to boot normally.

... I am not 100% sure yet but I suspect that the stall during boot of ubuntu previously (whether boot from HDD or boot from Live CD) may have been due to the network cable being disconnected. I can reproduce this when booting from HDD but have not tried when booting from Live CD.

... you live and you learn!

---

