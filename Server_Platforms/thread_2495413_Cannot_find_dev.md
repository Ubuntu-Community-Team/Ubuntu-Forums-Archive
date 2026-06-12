---
title: "Cannot find /dev"
date: 2024-02-17
forum: Server Platforms
---

### Post by Heeter on 2024-02-17
Hi all,

I need help, How can I boot from this?

[IMG]https://i.postimg.cc/vZyD0JZ3/rpviewer-1.png[/IMG]


Any help will be greatly appreciated, Please and thank you

Totally stuck

---

### Post by MAFoElffen on 2024-02-17
Did you check the disk for errors via smartmontools? Next would be to use the rescue menu to do a fsck on the mounts in the fstab...

After you try those 2 first, then we'll dive deeper.

---

### Post by Heeter on 2024-02-18
Hi Thank you MAFoElffen.

I use IDRAC to monitor this Dell, I HDDs are functioning properly.

By rescue menu, would you mean using the Live USB method?

Regards

---

### Post by Heeter on 2024-02-18
I figured out that I am able to boot from a live desktop ubuntu usb. I ran:

```

sudo fsck -f /dev/sdb4

```

Says can't do fsck because it is mounted, I ran:
```

sudo umount sdb4

```

But it doesn't help, stays mounted.

---

### Post by The Cog on 2024-02-18
That would be **[FONT=Courier New]sudo umount /dev/sdb4[/FONT]** - you have to give the full path.
Oh, wait. If it's an LVM partition then you need to fsck the LVM srive, not the raw partition. That would probably be /dev/mapper/<something>, I think. I'mnot really familiar with LVM.

---

### Post by MAFoElffen on 2024-02-18
Well... first you would need to do this in a terminal session from a Desktop LiveUSB...
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model

```
To help you figure out which is the actual installed OS disk and partition, and what is the associated with the LiveUSB.

That makes sense right?

I forgot you were using iDRAC, and that I gave instruction on how to install through that...

The Grub2 Menu doesn't "show" whe you boot the installed server image? I edit my /etc/default/grub files to force them to "show" on boot, even if for 1-2 seconds. That is a good measure in case something like this happens. When we get this going for you agai, remind me and I'll tell you how to do that.

---

### Post by Heeter on 2024-02-18
Hey Guys thank for the Help, really appreciate it!!

This is from the LIVE Desktop

Trying to umount sda3:

Still shows as mounted, don't think that I have the correct command

[IMG]https://i.postimg.cc/YScn8gXj/rpviewer-4.png[/IMG]

 This is what I have so far:

[IMG]https://i.postimg.cc/Fzq13995/rpviewer-3.png[/IMG]

---

### Post by Heeter on 2024-02-18
Hello Guys,

I am going through the motions to reinstall OS from fresh, I have my backups of data that I will be using.

Thank you for helping out guys

---

