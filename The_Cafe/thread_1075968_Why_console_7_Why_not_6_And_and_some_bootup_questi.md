---
title: "Why console 7? Why not 6? And and some bootup questions."
date: 2009-02-20
forum: The Cafe
---

### Post by dragos240 on 2009-02-20
Okay, so after a bit or research of trying to find out how to get into display :0, whatever that was, found that the graphics in ubuntu run under console 7, why not the 6th? Or the fifth? And also i found on console 8 that it displays the system bootup messages i see each time i boot up. Also i found out how to exit gdm (finally). I went into the console 1, and used "sudo /etc/init.d/gdm stop". Okay now for the bootup questions. Sometimes i look inside grub, and i see that i boots the kernel, then the UUID (whatever that is), then the vmlinuz (virtual machine linux?). And then quiet (?). What are these things, what does the linux kernel do? What is the vmlinuz, what is the UUID? And what is the "quiet". What do all of these do?

---

### Post by maybeway36 on 2009-02-20
vmlinuz: this is the filename of the Linux kernel.
UUID: identifier for the hard disk partition, so Linux knows where to boot. I was once able to boot openSUSE with the Ubuntu kernel as a last resort by changing this.
quiet: GRUB doesn't spit out messages at you about what it's doing.

---

### Post by dragos240 on 2009-02-20
> **maybeway36 said:**
> vmlinuz: this is the filename of the Linux kernel.
UUID: identifier for the hard disk partition, so Linux knows where to boot. I was once able to boot openSUSE with the Ubuntu kernel as a last resort by changing this.
quiet: GRUB doesn't spit out messages at you about what it's doing.

I thought the linux kernel was the thing where it said kernel before it.

---

### Post by FuturePilot on 2009-02-20
I think traditionally X has always run on tty 7.

The UUID is a unique number assigned to each partition on your hard drive. In Grub this number is part of the path to the kernel. Ubuntu uses the dev-by-uuid method instead of using the actual device numbers, i.e. /dev/sda1. If you run ```
sudo blkid
``` in a terminal you will see the UUID for all of your partitions.
vmlinuz is the kernel itself. The kernel is responsible for talking to the hardware.
"quiet" just tells the kernel to hide all the verbose output of the boot process. If you remove the "quiet splash" parameters you will see a ton of text fly across the screen at boot up.

I hope this helps answer your questions. :)

---

### Post by dragos240 on 2009-02-20
> **FuturePilot said:**
> I think traditionally X has always run on tty 7.

The UUID is a unique number assigned to each partition on your hard drive. In Grub this number is part of the path to the kernel. Ubuntu uses the dev-by-uuid method instead of using the actual device numbers, i.e. /dev/sda1. If you run ```
sudo blkid
``` in a terminal you will see the UUID for all of your partitions.
vmlinuz is the kernel itself. The kernel is responsible for talking to the hardware.
"quiet" just tells the kernel to hide all the verbose output of the boot process. If you remove the "quiet splash" parameters you will see a ton of text fly across the screen at boot up.

I hope this helps answer your questions. :)

Thanks! Also, i've hard that you can boot partitions by using
```

(hd0,0)

```

Why can't ubuntu use that?

Oh and what is the initrd.img?

---

### Post by FuturePilot on 2009-02-20
> **dragos240 said:**
> Thanks! Also, i've hard that you can boot partitions by using
```

(hd0,0)

```

Why can't ubuntu use that?

Oh and what is the initrd.img?

You can boot like that from the Grub command mode. At the Grub screen you can press "C" and enter the command mode. the command is not specific to the OS, it's part of Grub.

initrd.img is also part of the kernel. It is actually a ramdisk image.

---

### Post by days_of_ruin on 2009-02-20
What I would like to know is why fullscreen games mess up on every console
BUT 7?

---

### Post by Kingsley on 2009-02-20
I've always wondered about tty 7 too, though Fedora switched to tty 1 in Fedora 10.

---

### Post by gletob on 2009-02-20
> **days_of_ruin said:**
> What I would like to know is why fullscreen games mess up on every console
BUT 7?

Because 7 is the only place there is an X server running:lolflag:

---

### Post by jpkotta on 2009-02-21
> **FuturePilot said:**
> You can boot like that from the Grub command mode. At the Grub screen you can press "C" and enter the command mode. the command is not specific to the OS, it's part of Grub.

initrd.img is also part of the kernel. It is actually a ramdisk image.

To elaborate: 

Grub *always* uses (hd0,0) notation, it's Grub's only way for identifying hard drives.  

The initrd is a small userspace image that the kernel initially boots with.  It exists so things that are better implemented in userspace but are necessary for booting can be implemented in userspace and used at boot-time.  The most common example is to build most drivers as modules, and put only the ones needed for booting in the initrd.

> **days_of_ruin said:**
> What I would like to know is why fullscreen games mess up on every console
BUT 7?

How are you starting your games?

---

### Post by wmcbrine on 2009-02-22
My first Linux, Slackware 3.0 in 1996, X was on virtual console 7.

As to why, I think someone just thought one day, "OK, we have this neat feature called virtual consoles. How many should we give the user? How about six? That sounds like a good number. And then X can be on the next one." And it was so. And no one's ever seen fit to change it (well, once in a while, but usually not), because a) it doesn't much matter, and b) we're used to it.

---

### Post by dragos240 on 2009-02-22
by the way, whats the "ro" after the kernel mean.

---

### Post by Barrucadu on 2009-02-22
> **dragos240 said:**
> by the way, whats the "ro" after the kernel mean.

"read-only". it mounts the root filesystem as read only while booting, and it is then remounted read-write somewhere in the initscripts (I think)

---

### Post by dragos240 on 2009-02-22
> **Barrucadu said:**
> "read-only". it mounts the root filesystem as read only while booting, and it is then remounted read-write somewhere in the initscripts (I think)

thanks.

---

### Post by jnw222 on 2009-02-22
xorg can run on any tty, providing it exists, like i once painfully ran it on /dev/tty12

---

### Post by dragos240 on 2009-02-22
> **jnw222 said:**
> xorg can run on any tty, providing it exists, like i once painfully ran it on /dev/tty12

Oof, what happened? Slowness followed by bugs?

---

### Post by maybeway36 on 2009-02-22
Another trick I like to do (as root):
```
echo Hello world>/dev/tty12
```
Then press Ctrl+Alt+F12 and you will probably know what to expect there :)

---

### Post by dragos240 on 2009-02-22
> **maybeway36 said:**
> Another trick I like to do (as root):
```
echo Hello world>/dev/tty12
```Then press Ctrl+Alt+F12 and you will probably know what to expect there :)

A simple hello world message. Of course :p

---

