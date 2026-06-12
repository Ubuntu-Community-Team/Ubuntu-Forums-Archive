---
title: "HP prolient dl360 g4p Only Seeing 3.5 Gig of 4 Gig Ram (only in Linux)"
date: 2013-08-14
forum: Server Platforms
---

### Post by count0nz on 2013-08-14
I have a Strange issue with my HP Prolient Server

Here's some of the Steps i've taken to try to resolve this issue.

(Btw this problem only Exists in Linux. FreeBSD and Windows 2008 Both show 4Gig ram.)
Tryed 12.04 LTS (installed), 13.10, Centos 5.8,  6.4

Thanks ... maby a Bois upgrade may fix it.. But its just odd that only Linux has this issue.

Ahhh I noticed this in the dmesg log...

 WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 447MB of RAM.
Did some Googleing... and.. then Checked the Advanced Settings in the Bios..
(cache System Rom (OFF) -- Bingo 3.9Gig ram Avalabe :)



root@proliant:~# uname -a
Linux proliant 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:48:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

[Edit1] -- I also updated to the Latest Firmware as of 2007. no change
Edit2)  -- I Installed 3.10 Kernel ...  no change.
```

-- Installed Memory -- (from Ilo) --


Memory Modules present at POST

DIMM 01 : 512 MB 400 MHz 
DIMM 02 : 512 MB 400 MHz 
DIMM 03 : 512 MB 400 MHz 
DIMM 04 : 512 MB 400 MHz 
DIMM 05 : 1024 MB 400 MHz 
DIMM 06 : 1024 MB 400 MHz 

----------------------------------------

root@proliant:~# dmidecode | sed -n '/^Memory Device$/,/^$/p'
Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: 1
        Locator: DIMM 01
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 400 MHz

Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: 1
        Locator: DIMM 02
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 400 MHz

Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: 2
        Locator: DIMM 03
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 400 MHz

Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 512 MB
        Form Factor: DIMM
        Set: 2
        Locator: DIMM 04
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 400 MHz

Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: 3
        Locator: DIMM 05
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 400 MHz

Memory Device
        Array Handle: 0x1000
        Error Information Handle: Not Provided
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: 3
        Locator: DIMM 06
        Bank Locator: Not Specified
        Type: DDR
        Type Detail: Synchronous
        Speed: 400 MHz
-----------------------------------

```

---

### Post by tgalati4 on 2013-08-15
When you run memtest from the GRUB menu, how much RAM shows up?

What is the output of:

```
free
```

Since this is an older server, it's possible that your motherboard chipset has some limitations with newer Linux kernels.  Try a LiveCD of 10.04 and see if there is a RAM difference.
Look for the latest BIOS and load that into your server, it could be a BIOS bug.

Clean out the machine and rearrange the RAM chips.

---

### Post by count0nz on 2013-08-15
Thanks for your Reply.. Like i Said in my Main Post. I Fixed it.. by disabling Rom Shadowing..
Didn't even notice that before... but odd that it didn't effect FreeBSD etc. But Happy now. Back to Ubuntu :)

---

