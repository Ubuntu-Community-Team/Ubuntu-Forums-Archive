---
title: "how do i break Raid"
date: 2021-11-28
forum: Server Platforms
---

### Post by tross9 on 2021-11-28
I need to break my raid and use one of the drives in another system. 
    sdb and sdc are mirrored file share drives and are not the boot drive.

I used mdadm -f /dev/md127 -r /dev/sdc1 
    which worked but fdisk -l still shows the raid is still active ( autodetect)
when i try rebooting without sdc1 it hangs i have to reattach sdc1 to  get the system to boot.

i know i'm missing a step but what step(s)

also.
one possible problem is i'm not 100% sure which physical drive is sdc1.  
   is there a command  to indicate which sata connection the drives use.

 TIA Tim

---

### Post by blackmoses2003 on 2021-11-29
The following quote is from the man [page]("https://linux.die.net/man/8/mdadm")
> mdadm /dev/md0 -f /dev/hda1 -r /dev/hda1
will firstly mark /dev/hda1 as faulty in /dev/md0 and will then remove it from the array[B][B][B]

So, accordingly, I think the command should have been
[/B][/B][/B]
```
[COLOR=#000000]mdadm /dev/md127 -f /dev/sdc1 [/COLOR][COLOR=#000000]-r /dev/sdc1[/COLOR]
```[COLOR=#000000]

Wish you the best

[/COLOR]

---

### Post by blackmoses2003 on 2021-11-29
> [COLOR=#000000]is there a command to indicate which sata connection the drives use.[/COLOR]

As suggested by this [thread]("https://unix.stackexchange.com/a/502674") you could try
```
[COLOR=#232629][FONT=ui-monospace]ls -l /dev/disk/by-id/[/FONT][/COLOR]
```

---

### Post by tross9 on 2021-11-29
[COLOR=#000000]blackmoses2003, 
   i did use the command you posted, i should have mentioned that I was writing the command from memory and was probably not 100% correct.

    but it appears that i was not pulling the correct HD.  the [/COLOR][COLOR=#232629][FONT=ui-monospace]ls -l /dev/disk/by-id/  helped , thanks for this command[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]      
 note: when I did pull the correct drive I needed to enter setup (bios F2) to get pasted the missing drive error. 

 it is booting but it still shows the mirror as active but degraded.   (clean, degraded)
   as long it being degraded does not corrupt the disk, it might be ok, because I'll be putting sdc1 back into the box ( mdadm --add...) in a month or two when I'm finished with the drive in the other system.
     
       

again thanks.[/COLOR]

---

