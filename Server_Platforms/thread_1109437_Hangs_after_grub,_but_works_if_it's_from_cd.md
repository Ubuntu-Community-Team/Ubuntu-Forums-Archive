---
title: "Hangs after grub, but works if it's from cd"
date: 2009-03-28
forum: Server Platforms
---

### Post by tthet on 2009-03-28
I there everyone.

Sorry if post as already been aswered but i haven't seen this issue on any of my searchs.

Oh and do apologize for my spelling don't often write english.

Ok, to the problem at hand...

I have 4 disks in RAID1 and one IDE for system, it's hardware raid.

I've installed perfectly the server and it workd if RAID is disconnected or if ... well i'll explain better...

a)  Boot from IDE ( it is set as first disk and second to cd-rom in boot order ), it goes into grub, 3 seconds latter jumps to option 0 and hangs with clinking cursor

b)  Boot from IDE go into grub options->console...
    check disks and boot is on hd0,1 wich is known as correct...
    edit boot option 0 and is using uuid
    back to grub console and do the right steps to boot
    grub> root (hd0,1)
    grub> kernel /boot/vmlinuz(...) root=/dev/sde2 ro (...)
    i know its sde2 because of installation disk options
    and it reboots on pressing enter

c)  boot from cd and selected "boot from first disk" (or something like this)
    it starts grub, 3 seconds latter system starts flawlessly
    one of the first messages states (hd0,1) ext3 (...)

d)  boot from cd and selected "boot from first disk" (or something like this)
    it starts grub, edited options and are the same as disk boot
    went to grub console
    grub> root (hd
    pressing tab and tryin the diferent 5 options 1-5,
    it shows me that my system is at hd4,1
    startled
    selected boot option 0 and
    one of the first messages states (hd0,1) ext3 (...)

I'm no expert, more of a newbie with some knowledge but this is just crazy, don't know what to do or found anyone who knows...

Lokking for the right answer...

I'me thisking of two, one i can do, the other don't know how or if it is the best one...

a)   I can do
     trade the motherboard for a new one and pray

b)   don't know how or if it is good solution
     find a way to automaticly boot grub as if from cd


Tanks in advanced

---

### Post by tthet on 2009-03-29
No thoughts or answers?

No one as an idea or did i not explain the problem well?

I'm really in a pitch...

Thanks for your time

---

### Post by mhgsys on 2009-03-29
You can recover grub with your live cd.

Bootup a live cd, open a terminal and do the following.

```
sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```

find /boot/grub/stage1

```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```

root (hd?,?)

```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```

setup (hd0)

```
Finally exit the grub shell
```

quit

```

Hopes this helps for you

---

### Post by tthet on 2009-03-29
Thanks mhgsys...

but already done that and still nothing... good advice anyways...

even with super grub disk i can't do a thing, it only works if it boots from install cd option "boot from first hard disk"...

i'm thinking on changing mobo

---

